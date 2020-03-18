---
title: Criar bibliotecas de clientes gRPC - gRPC para Desenvolvedores WCF
description: Discussão de bibliotecas/pacotes de clientes compartilhados para serviços gRPC.
ms.date: 09/02/2019
ms.openlocfilehash: bb58cb3cda4b0cbb3a5d34129961349bcb0093e9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79401665"
---
# <a name="create-grpc-client-libraries"></a>Crie bibliotecas de clientes gRPC

Não é necessário distribuir bibliotecas de clientes para um aplicativo gRPC. Você pode criar uma `.proto` biblioteca compartilhada de arquivos dentro de sua organização, e outras equipes podem usar esses arquivos para gerar código cliente em seus próprios projetos. Mas se você tem um repositório NuGet privado e muitas outras equipes estão usando o .NET Core, você pode criar e publicar pacotes nuGet do cliente como parte do seu projeto de serviço. Essa pode ser uma boa maneira de compartilhar e promover o seu serviço.

Uma vantagem de distribuir uma biblioteca de clientes é que você pode melhorar as classes gRPC e Protobuf geradas com métodos e propriedades úteis de "conveniência". No código do cliente, como no servidor, todas `partial`as classes são declaradas como , para que você possa ampliá-las sem editar o código gerado. Isso significa que é fácil adicionar construtores, métodos e propriedades calculadas aos tipos básicos.

> [!CAUTION]
> Você não deve usar código personalizado para fornecer funcionalidade essencial. Você não quer restringir essa funcionalidade essencial para equipes .NET que usam a biblioteca compartilhada e não fornecê-la a equipes que usam outras linguagens ou plataformas, como Python ou Java.

Certifique-se de que o maior número possível de equipes possa acessar seu serviço gRPC. A melhor maneira de fazer `.proto` isso é compartilhar arquivos para que os desenvolvedores possam gerar seus próprios clientes. Isso é particularmente verdadeiro em um ambiente multiplataforma, onde diferentes equipes frequentemente usam diferentes linguagens e frameworks de programação, ou onde sua API é acessível externamente.

## <a name="useful-extensions"></a>Extensões úteis

Existem duas interfaces comumente usadas no .NET para <xref:System.Collections.Generic.IEnumerable%601> <xref:System.IObservable%601>lidar com fluxos de objetos: e . Começando com .NET Core 3.0 e C# 8.0, há uma <xref:System.Collections.Generic.IAsyncEnumerable%601> interface para processamento `await foreach` de fluxos assíncronamente e uma sintaxe para usar a interface. Esta seção apresenta código reutilizável para a aplicação dessas interfaces em fluxos gRPC.

Com as bibliotecas de clientes .NET Core `ReadAllAsync` gRPC, há um método de extensão para `IAsyncStreamReader<T>` isso criar uma `IAsyncEnumerable<T>` interface. Para desenvolvedores que usam programação reativa, um `IObservable<T>` método de extensão equivalente para criar uma interface pode parecer o exemplo na seção a seguir.

### <a name="iobservable"></a>Iobservable

A `IObservable<T>` interface é o inverso `IEnumerable<T>`"reativo" de . Em vez de puxar itens de um fluxo, a abordagem reativa permite que o fluxo empurre itens para um assinante. Isso é muito semelhante aos fluxos gRPC, `IObservable<T>` e é `IAsyncStreamReader<T>` fácil envolver uma interface em torno de uma interface.

Este código é `IAsyncEnumerable<T>` mais longo que o código, porque C# não tem suporte interno para trabalhar com observáveis. Você tem que criar a classe de implementação manualmente. É uma classe genérica, porém, então uma única implementação funciona em todos os tipos.

```csharp
using System;
using System.Diagnostics;
using System.Threading;
using System.Threading.Tasks;

namespace Grpc.Core
{
    public class GrpcStreamObservable<T> : IObservable<T>
    {
        private readonly IAsyncStreamReader<T> _reader;
        private readonly CancellationToken _token;
        private int _used;

        public Observable(IAsyncStreamReader<T> reader, CancellationToken token = default)
        {
            _reader = reader;
            _token = token;
            _used = 0;
        }

        public IDisposable Subscribe(IObserver<T> observer) =>
            Interlocked.Exchange(ref _used, 1) == 0
                ? new GrpcStreamSubscription(_reader, observer, _token)
                : throw new InvalidOperationException("Subscribe can only be called once.");

    }
}
```

> [!IMPORTANT]
> Essa implementação observável permite que o `Subscribe` método seja chamado apenas uma vez, porque ter vários assinantes tentando ler a partir do fluxo resultaria em caos. Existem operadores, `Replay` como no [System.Reactive.Linq,](https://www.nuget.org/packages/System.Reactive.Linq)que permitem o buffering e o compartilhamento repetível de observáveis, que podem ser usados com essa implementação.

A `GrpcStreamSubscription` classe lida com a `IAsyncStreamReader`enumeração do:

```csharp
public class GrpcStreamSubscription : IDisposable
{
    private readonly Task _task;
    private readonly CancellationTokenSource _tokenSource;
    private bool _completed;

    public Subscription(IAsyncStreamReader<T> reader, IObserver<T> observer, CancellationToken token)
    {
        Debug.Assert(reader != null);
        Debug.Assert(observer != null);
        _tokenSource = new CancellationTokenSource();
        token.Register(_tokenSource.Cancel);
        _task = Run(reader, observer, _tokenSource.Token);
    }

    private async Task Run(IAsyncStreamReader<T> reader, IObserver<T> observer, CancellationToken token)
    {
        while (!token.IsCancellationRequested)
        {
            try
            {
                if (!await reader.MoveNext(token)) break;
            }
            catch (RpcException e) when (e.StatusCode == Grpc.Core.StatusCode.NotFound)
            {
                break;
            }
            catch (OperationCanceledException)
            {
                break;
            }
            catch (Exception e)
            {
                observer.OnError(e);
                _completed = true;
                return;
            }

            observer.OnNext(reader.Current);
        }

        _completed = true;
        observer.OnCompleted();
    }

    public void Dispose()
    {
        if (!_completed && !_tokenSource.IsCancellationRequested)
        {
            _tokenSource.Cancel();
        }

        _tokenSource.Dispose();
        _task.Dispose();
    }

}
```

Tudo o que é necessário agora é um método de extensão simples para criar o observável a partir do leitor de fluxo.

```csharp
using System;
using System.Diagnostics;
using System.Threading;
using System.Threading.Tasks;

namespace Grpc.Core
{
    public static class AsyncStreamReaderObservableExtensions
    {
        public static IObservable<T> AsObservable<T>(this IAsyncStreamReader<T> reader) =>
            new GrpcStreamObservable<T>(reader);
    }
}
```

## <a name="summary"></a>Resumo

Os `IAsyncEnumerable` `IObservable` modelos e modelos são formas bem suportadas e bem documentadas de lidar com fluxos assíncronos de dados em .NET. os fluxos gRPC mapeiam bem ambos os paradigmas, oferecendo estreita integração com o .NET Core e estilos de programação reativos e assíncronos.

>[!div class="step-by-step"]
>[Próximo](streaming-versus-repeated.md)
>[anterior](security.md)
