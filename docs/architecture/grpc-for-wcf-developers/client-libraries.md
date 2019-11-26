---
title: Criar bibliotecas de cliente do gRPC-gRPC para desenvolvedores do WCF
description: Discussão de bibliotecas/pacotes de cliente compartilhado para serviços gRPCs.
ms.date: 09/02/2019
ms.openlocfilehash: 2135fe8b24a2311a31cb2bed191d290b1112bc66
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73967882"
---
# <a name="create-grpc-client-libraries"></a>Criar bibliotecas de cliente do gRPC

Não é necessário distribuir bibliotecas de cliente para um aplicativo gRPC. Você pode criar uma biblioteca compartilhada de arquivos de `.proto` dentro de sua organização e outras equipes podem usar esses arquivos para gerar o código do cliente em seus próprios projetos. Mas se você tiver um repositório do NuGet privado e muitas outras equipes estiverem usando o .NET Core, criar e publicar pacotes NuGet do cliente como parte do seu projeto de serviço pode ser uma boa maneira de compartilhar e promover seu serviço.

Uma vantagem de distribuir uma biblioteca de cliente é que você pode aprimorar as classes gRPC e Protobuf geradas com métodos e propriedades "conveniência" úteis. No código do cliente, como no servidor, todas as classes são declaradas como `partial` para que você possa estendê-las sem editar o código gerado. Isso significa que é fácil adicionar construtores, métodos, Propriedades calculadas e muito mais aos tipos básicos.

> [!CAUTION]
> Você **não** deve usar o código personalizado para fornecer funcionalidade essencial, pois isso significaria que a funcionalidade seria restrita às equipes do .NET usando a biblioteca compartilhada e não às equipes que usam outras linguagens ou plataformas como Python ou Java.

Em um ambiente de várias plataformas em que equipes diferentes frequentemente usam estruturas e linguagens de programação diferentes, ou onde sua API está acessível externamente, basta compartilhar `.proto` arquivos para que os desenvolvedores possam gerar seus próprios clientes é a melhor maneira de garantir que o máximo possível de equipes possam acessar o serviço gRPC.

## <a name="useful-extensions"></a>Extensões úteis

Há duas interfaces comumente usadas no .NET para lidar com fluxos de objetos: <xref:System.Collections.Generic.IEnumerable%601> e <xref:System.IObservable%601>. A partir do .NET Core 3,0 C# e 8,0, há uma interface <xref:System.Collections.Generic.IAsyncEnumerable%601> para processar fluxos de forma assíncrona e uma sintaxe de `await foreach` para usar a interface. Esta seção apresenta código reutilizável para aplicar essas interfaces a fluxos de gRPC.

Com as bibliotecas de cliente do .NET Core gRPC, há um método de extensão `ReadAllAsync` para `IAsyncStreamReader<T>` que cria uma `IAsyncEnumerable<T>`. Para os desenvolvedores que usam a programação reativa, um método de extensão equivalente para criar um `IObservable<T>` pode ser semelhante a este.

### <a name="iobservable"></a>IObservable

A interface `IObservable<T>` é o inverso "reativo" de `IEnumerable<T>`. Em vez de extrair itens de um fluxo, a abordagem reativa permite que o fluxo Envie itens por push para um assinante. Isso é muito semelhante aos fluxos de gRPC, e é fácil encapsular um `IObservable<T>` em um `IAsyncStreamReader<T>`.

Esse código é maior do que o código de C# `IAsyncEnumerable<T>` porque o não tem suporte interno para trabalhar com observáveis, portanto, a classe de implementação deve ser criada manualmente. No entanto, é uma classe genérica, portanto, uma única implementação funcionará em todos os tipos.

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
> Essa implementação observável só permite que o método `Subscribe` seja chamado uma vez, pois ter vários assinantes tentando ler a partir do fluxo resultaria em caos. Há operadores como `Replay` no [sistema. Reactive. Linq](https://www.nuget.org/packages/System.Reactive.Linq) que habilita o armazenamento em buffer e o compartilhamento repetível de observáveis, que podem ser usados com essa implementação.

A classe `GrpcStreamSubscription` manipula a enumeração do `IAsyncStreamReader`.

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

Tudo o que é necessário agora é um método de extensão simples para criar o observável do leitor de fluxo.

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

Os modelos `IAsyncEnumerable` e `IObservable` são as maneiras bem suportadas e bem documentadas de lidar com fluxos de dados assíncronos no .NET. o gRPC streams mapeia bem para ambos os paradigmas, oferecendo uma integração próxima com o .NET Core Framework moderno e os estilos de programação reativos/assíncronos.

>[!div class="step-by-step"]
>[Anterior](streaming-versus-repeated.md)
>[Próximo](security.md)
