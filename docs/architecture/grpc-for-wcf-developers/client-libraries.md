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
# <a name="create-grpc-client-libraries"></a><span data-ttu-id="11ab2-103">Crie bibliotecas de clientes gRPC</span><span class="sxs-lookup"><span data-stu-id="11ab2-103">Create gRPC client libraries</span></span>

<span data-ttu-id="11ab2-104">Não é necessário distribuir bibliotecas de clientes para um aplicativo gRPC.</span><span class="sxs-lookup"><span data-stu-id="11ab2-104">It isn't necessary to distribute client libraries for a gRPC application.</span></span> <span data-ttu-id="11ab2-105">Você pode criar uma `.proto` biblioteca compartilhada de arquivos dentro de sua organização, e outras equipes podem usar esses arquivos para gerar código cliente em seus próprios projetos.</span><span class="sxs-lookup"><span data-stu-id="11ab2-105">You can create a shared library of `.proto` files within your organization, and other teams can use those files to generate client code in their own projects.</span></span> <span data-ttu-id="11ab2-106">Mas se você tem um repositório NuGet privado e muitas outras equipes estão usando o .NET Core, você pode criar e publicar pacotes nuGet do cliente como parte do seu projeto de serviço.</span><span class="sxs-lookup"><span data-stu-id="11ab2-106">But if you have a private NuGet repository and many other teams are using .NET Core, you can create and publish client NuGet packages as part of your service project.</span></span> <span data-ttu-id="11ab2-107">Essa pode ser uma boa maneira de compartilhar e promover o seu serviço.</span><span class="sxs-lookup"><span data-stu-id="11ab2-107">This can be a good way of sharing and promoting your service.</span></span>

<span data-ttu-id="11ab2-108">Uma vantagem de distribuir uma biblioteca de clientes é que você pode melhorar as classes gRPC e Protobuf geradas com métodos e propriedades úteis de "conveniência".</span><span class="sxs-lookup"><span data-stu-id="11ab2-108">One advantage of distributing a client library is that you can enhance the generated gRPC and Protobuf classes with helpful "convenience" methods and properties.</span></span> <span data-ttu-id="11ab2-109">No código do cliente, como no servidor, todas `partial`as classes são declaradas como , para que você possa ampliá-las sem editar o código gerado.</span><span class="sxs-lookup"><span data-stu-id="11ab2-109">In the client code, as in the server, all the classes are declared as `partial`, so you can extend them without editing the generated code.</span></span> <span data-ttu-id="11ab2-110">Isso significa que é fácil adicionar construtores, métodos e propriedades calculadas aos tipos básicos.</span><span class="sxs-lookup"><span data-stu-id="11ab2-110">This means it's easy to add constructors, methods, and calculated properties to the basic types.</span></span>

> [!CAUTION]
> <span data-ttu-id="11ab2-111">Você não deve usar código personalizado para fornecer funcionalidade essencial.</span><span class="sxs-lookup"><span data-stu-id="11ab2-111">You shouldn't use custom code to provide essential functionality.</span></span> <span data-ttu-id="11ab2-112">Você não quer restringir essa funcionalidade essencial para equipes .NET que usam a biblioteca compartilhada e não fornecê-la a equipes que usam outras linguagens ou plataformas, como Python ou Java.</span><span class="sxs-lookup"><span data-stu-id="11ab2-112">You don't want to restrict that essential functionality to .NET teams that use the shared library, and not provide it to teams that use other languages or platforms, such as Python or Java.</span></span>

<span data-ttu-id="11ab2-113">Certifique-se de que o maior número possível de equipes possa acessar seu serviço gRPC.</span><span class="sxs-lookup"><span data-stu-id="11ab2-113">Ensure that as many teams as possible can access your gRPC service.</span></span> <span data-ttu-id="11ab2-114">A melhor maneira de fazer `.proto` isso é compartilhar arquivos para que os desenvolvedores possam gerar seus próprios clientes.</span><span class="sxs-lookup"><span data-stu-id="11ab2-114">The best way to do this is to share `.proto` files so developers can generate their own clients.</span></span> <span data-ttu-id="11ab2-115">Isso é particularmente verdadeiro em um ambiente multiplataforma, onde diferentes equipes frequentemente usam diferentes linguagens e frameworks de programação, ou onde sua API é acessível externamente.</span><span class="sxs-lookup"><span data-stu-id="11ab2-115">This is particularly true in a multi-platform environment, where different teams frequently use different programming languages and frameworks, or where your API is externally accessible.</span></span>

## <a name="useful-extensions"></a><span data-ttu-id="11ab2-116">Extensões úteis</span><span class="sxs-lookup"><span data-stu-id="11ab2-116">Useful extensions</span></span>

<span data-ttu-id="11ab2-117">Existem duas interfaces comumente usadas no .NET para <xref:System.Collections.Generic.IEnumerable%601> <xref:System.IObservable%601>lidar com fluxos de objetos: e .</span><span class="sxs-lookup"><span data-stu-id="11ab2-117">There are two commonly used interfaces in .NET for dealing with streams of objects: <xref:System.Collections.Generic.IEnumerable%601> and <xref:System.IObservable%601>.</span></span> <span data-ttu-id="11ab2-118">Começando com .NET Core 3.0 e C# 8.0, há uma <xref:System.Collections.Generic.IAsyncEnumerable%601> interface para processamento `await foreach` de fluxos assíncronamente e uma sintaxe para usar a interface.</span><span class="sxs-lookup"><span data-stu-id="11ab2-118">Starting with .NET Core 3.0 and C# 8.0, there's an <xref:System.Collections.Generic.IAsyncEnumerable%601> interface for processing streams asynchronously, and an `await foreach` syntax for using the interface.</span></span> <span data-ttu-id="11ab2-119">Esta seção apresenta código reutilizável para a aplicação dessas interfaces em fluxos gRPC.</span><span class="sxs-lookup"><span data-stu-id="11ab2-119">This section presents reusable code for applying these interfaces to gRPC streams.</span></span>

<span data-ttu-id="11ab2-120">Com as bibliotecas de clientes .NET Core `ReadAllAsync` gRPC, há um método de extensão para `IAsyncStreamReader<T>` isso criar uma `IAsyncEnumerable<T>` interface.</span><span class="sxs-lookup"><span data-stu-id="11ab2-120">With the .NET Core gRPC client libraries, there's a `ReadAllAsync` extension method for `IAsyncStreamReader<T>` that creates an `IAsyncEnumerable<T>` interface.</span></span> <span data-ttu-id="11ab2-121">Para desenvolvedores que usam programação reativa, um `IObservable<T>` método de extensão equivalente para criar uma interface pode parecer o exemplo na seção a seguir.</span><span class="sxs-lookup"><span data-stu-id="11ab2-121">For developers using reactive programming, an equivalent extension method to create an `IObservable<T>` interface might look like the example in the following section.</span></span>

### <a name="iobservable"></a><span data-ttu-id="11ab2-122">Iobservable</span><span class="sxs-lookup"><span data-stu-id="11ab2-122">IObservable</span></span>

<span data-ttu-id="11ab2-123">A `IObservable<T>` interface é o inverso `IEnumerable<T>`"reativo" de .</span><span class="sxs-lookup"><span data-stu-id="11ab2-123">The `IObservable<T>` interface is the "reactive" inverse of `IEnumerable<T>`.</span></span> <span data-ttu-id="11ab2-124">Em vez de puxar itens de um fluxo, a abordagem reativa permite que o fluxo empurre itens para um assinante.</span><span class="sxs-lookup"><span data-stu-id="11ab2-124">Rather than pulling items from a stream, the reactive approach lets the stream push items to a subscriber.</span></span> <span data-ttu-id="11ab2-125">Isso é muito semelhante aos fluxos gRPC, `IObservable<T>` e é `IAsyncStreamReader<T>` fácil envolver uma interface em torno de uma interface.</span><span class="sxs-lookup"><span data-stu-id="11ab2-125">This is very similar to gRPC streams, and it's easy to wrap an `IObservable<T>` interface around an `IAsyncStreamReader<T>` interface.</span></span>

<span data-ttu-id="11ab2-126">Este código é `IAsyncEnumerable<T>` mais longo que o código, porque C# não tem suporte interno para trabalhar com observáveis.</span><span class="sxs-lookup"><span data-stu-id="11ab2-126">This code is longer than the `IAsyncEnumerable<T>` code, because C# doesn't have built-in support for working with observables.</span></span> <span data-ttu-id="11ab2-127">Você tem que criar a classe de implementação manualmente.</span><span class="sxs-lookup"><span data-stu-id="11ab2-127">You have to create the implementation class manually.</span></span> <span data-ttu-id="11ab2-128">É uma classe genérica, porém, então uma única implementação funciona em todos os tipos.</span><span class="sxs-lookup"><span data-stu-id="11ab2-128">It's a generic class, though, so a single implementation works across all types.</span></span>

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
> <span data-ttu-id="11ab2-129">Essa implementação observável permite que o `Subscribe` método seja chamado apenas uma vez, porque ter vários assinantes tentando ler a partir do fluxo resultaria em caos.</span><span class="sxs-lookup"><span data-stu-id="11ab2-129">This observable implementation allows the `Subscribe` method to be called only once, because having multiple subscribers trying to read from the stream would result in chaos.</span></span> <span data-ttu-id="11ab2-130">Existem operadores, `Replay` como no [System.Reactive.Linq,](https://www.nuget.org/packages/System.Reactive.Linq)que permitem o buffering e o compartilhamento repetível de observáveis, que podem ser usados com essa implementação.</span><span class="sxs-lookup"><span data-stu-id="11ab2-130">There are operators, such as `Replay` in the [System.Reactive.Linq](https://www.nuget.org/packages/System.Reactive.Linq), that enable buffering and repeatable sharing of observables, which can be used with this implementation.</span></span>

<span data-ttu-id="11ab2-131">A `GrpcStreamSubscription` classe lida com a `IAsyncStreamReader`enumeração do:</span><span class="sxs-lookup"><span data-stu-id="11ab2-131">The `GrpcStreamSubscription` class handles the enumeration of the `IAsyncStreamReader`:</span></span>

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

<span data-ttu-id="11ab2-132">Tudo o que é necessário agora é um método de extensão simples para criar o observável a partir do leitor de fluxo.</span><span class="sxs-lookup"><span data-stu-id="11ab2-132">All that is required now is a simple extension method to create the observable from the stream reader.</span></span>

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

## <a name="summary"></a><span data-ttu-id="11ab2-133">Resumo</span><span class="sxs-lookup"><span data-stu-id="11ab2-133">Summary</span></span>

<span data-ttu-id="11ab2-134">Os `IAsyncEnumerable` `IObservable` modelos e modelos são formas bem suportadas e bem documentadas de lidar com fluxos assíncronos de dados em .NET.</span><span class="sxs-lookup"><span data-stu-id="11ab2-134">The `IAsyncEnumerable` and `IObservable` models are both well-supported and well-documented ways of dealing with asynchronous streams of data in .NET.</span></span> <span data-ttu-id="11ab2-135">os fluxos gRPC mapeiam bem ambos os paradigmas, oferecendo estreita integração com o .NET Core e estilos de programação reativos e assíncronos.</span><span class="sxs-lookup"><span data-stu-id="11ab2-135">gRPC streams map well to both paradigms, offering close integration with .NET Core, and reactive and asynchronous programming styles.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="11ab2-136">[Próximo](streaming-versus-repeated.md)
>[anterior](security.md)</span><span class="sxs-lookup"><span data-stu-id="11ab2-136">[Previous](streaming-versus-repeated.md)
[Next](security.md)</span></span>
