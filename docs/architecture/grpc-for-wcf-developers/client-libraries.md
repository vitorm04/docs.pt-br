---
title: Criar bibliotecas de cliente do gRPC-gRPC para desenvolvedores do WCF
description: Discussão de bibliotecas/pacotes de cliente compartilhado para serviços gRPCs.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 44a749c888528ca244f41b5b88354d7ed1db4190
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184585"
---
# <a name="create-grpc-client-libraries"></a><span data-ttu-id="97b16-103">Criar bibliotecas de cliente do gRPC</span><span class="sxs-lookup"><span data-stu-id="97b16-103">Create gRPC client libraries</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="97b16-104">Não é necessário distribuir bibliotecas de cliente para um aplicativo gPRC.</span><span class="sxs-lookup"><span data-stu-id="97b16-104">It isn't necessary to distribute client libraries for a gPRC application.</span></span> <span data-ttu-id="97b16-105">Você pode criar uma biblioteca compartilhada de `.proto` arquivos em sua organização e outras equipes podem usar esses arquivos para gerar o código do cliente em seus próprios projetos.</span><span class="sxs-lookup"><span data-stu-id="97b16-105">You can create a shared library of `.proto` files within your organization, and other teams can use those files to generate client code in their own projects.</span></span> <span data-ttu-id="97b16-106">Mas se você tiver um repositório do NuGet privado e muitas outras equipes estiverem usando o .NET Core, criar e publicar pacotes NuGet do cliente como parte do seu projeto de serviço pode ser uma boa maneira de compartilhar e promover seu serviço.</span><span class="sxs-lookup"><span data-stu-id="97b16-106">But if you have a private NuGet repository and many other teams are using .NET Core, creating and publishing client NuGet packages as part of your service project may be a good way of sharing and promoting your service.</span></span>

<span data-ttu-id="97b16-107">Uma vantagem de distribuir uma biblioteca de cliente é que você pode aprimorar as classes gRPC e Protobuf geradas com métodos e propriedades "conveniência" úteis.</span><span class="sxs-lookup"><span data-stu-id="97b16-107">One advantage of distributing a client library is that you can enhance the generated gRPC and Protobuf classes with helpful "convenience" methods and properties.</span></span> <span data-ttu-id="97b16-108">No código do cliente, como no servidor, todas as classes são declaradas `partial` como para que você possa estendê-las sem editar o código gerado.</span><span class="sxs-lookup"><span data-stu-id="97b16-108">In the client code, as in the server, all the classes are declared as `partial` so you can extend them without editing the generated code.</span></span> <span data-ttu-id="97b16-109">Isso significa que é fácil adicionar construtores, métodos, Propriedades calculadas e muito mais aos tipos básicos.</span><span class="sxs-lookup"><span data-stu-id="97b16-109">This means it's easy to add constructors, methods, calculated properties, and more to the basic types.</span></span>

> [!CAUTION]
> <span data-ttu-id="97b16-110">Você **não** deve usar o código personalizado para fornecer funcionalidade essencial, pois isso significaria que a funcionalidade seria restrita às equipes do .NET usando a biblioteca compartilhada e não às equipes que usam outras linguagens ou plataformas como Python ou Java.</span><span class="sxs-lookup"><span data-stu-id="97b16-110">You should **not** use custom code to provide essential functionality, as this would mean that functionality would be restricted to .NET teams using the shared library, and not to teams using other languages or platforms such as Python or Java.</span></span>

<span data-ttu-id="97b16-111">Em um ambiente de várias plataformas em que equipes diferentes frequentemente usam estruturas e linguagens de programação diferentes, ou onde sua API está acessível externamente, `.proto` simplesmente compartilhar arquivos para que os desenvolvedores possam gerar seus próprios clientes é a melhor maneira de Verifique se o máximo de equipes possível pode acessar o serviço gRPC.</span><span class="sxs-lookup"><span data-stu-id="97b16-111">In a multi-platform environment where different teams frequently use different programming languages and frameworks, or where your API is externally accessible, simply sharing `.proto` files so developers can generate their own clients is the best way to ensure as many teams as possible can access your gRPC service.</span></span>

## <a name="useful-extensions"></a><span data-ttu-id="97b16-112">Extensões úteis</span><span class="sxs-lookup"><span data-stu-id="97b16-112">Useful extensions</span></span>

<span data-ttu-id="97b16-113">Há duas interfaces comumente usadas no .net para lidar com fluxos de objetos: <xref:System.Collections.Generic.IEnumerable%601> e. <xref:System.IObservable%601></span><span class="sxs-lookup"><span data-stu-id="97b16-113">There are two commonly used interfaces in .NET for dealing with streams of objects: <xref:System.Collections.Generic.IEnumerable%601> and <xref:System.IObservable%601>.</span></span> <span data-ttu-id="97b16-114">A partir do .NET Core 3,0 C# e 8,0, há uma <xref:System.Collections.Generic.IAsyncEnumerable%601> interface para processar fluxos de forma assíncrona `await foreach` e uma sintaxe para usar a interface.</span><span class="sxs-lookup"><span data-stu-id="97b16-114">Starting with .NET Core 3.0 and C# 8.0, there's an <xref:System.Collections.Generic.IAsyncEnumerable%601> interface for processing streams asynchronously, and an `await foreach` syntax for using the interface.</span></span> <span data-ttu-id="97b16-115">Esta seção apresenta código reutilizável para aplicar essas interfaces a fluxos de gRPC.</span><span class="sxs-lookup"><span data-stu-id="97b16-115">This section presents reusable code for applying these interfaces to gRPC streams.</span></span>

<span data-ttu-id="97b16-116">Com as bibliotecas de cliente do .NET Core gRPC, há `ReadAllAsync` um método de `IAsyncStreamReader<T>` extensão para o `IAsyncEnumerable<T>`que cria um.</span><span class="sxs-lookup"><span data-stu-id="97b16-116">With the .NET Core gRPC client libraries, there's a `ReadAllAsync` extension method for `IAsyncStreamReader<T>` that creates an `IAsyncEnumerable<T>`.</span></span> <span data-ttu-id="97b16-117">Para os desenvolvedores que usam a programação reativa, um método de extensão `IObservable<T>` equivalente para criar um pode ser semelhante a este.</span><span class="sxs-lookup"><span data-stu-id="97b16-117">For developers using reactive programming, an equivalent extension method to create an `IObservable<T>` might look like this.</span></span>

### <a name="iobservable"></a><span data-ttu-id="97b16-118">IObservable</span><span class="sxs-lookup"><span data-stu-id="97b16-118">IObservable</span></span>

<span data-ttu-id="97b16-119">A `IObservable<T>` interface é o inverso "reativo" `IEnumerable<T>`de.</span><span class="sxs-lookup"><span data-stu-id="97b16-119">The `IObservable<T>` interface is the "reactive" inverse of `IEnumerable<T>`.</span></span> <span data-ttu-id="97b16-120">Em vez de extrair itens de um fluxo, a abordagem reativa permite que o fluxo Envie itens por push para um assinante.</span><span class="sxs-lookup"><span data-stu-id="97b16-120">Rather than pulling items from a stream, the reactive approach lets the stream push items to a subscriber.</span></span> <span data-ttu-id="97b16-121">Isso é muito semelhante aos fluxos de gRPC, e é fácil encapsular `IObservable<T>` `IAsyncStreamReader<T>`um.</span><span class="sxs-lookup"><span data-stu-id="97b16-121">This is very similar to gRPC streams, and it's easy to wrap an `IObservable<T>` around an `IAsyncStreamReader<T>`.</span></span>

<span data-ttu-id="97b16-122">Esse código é maior do que `IAsyncEnumerable<T>` o código C# porque não tem suporte interno para trabalhar com observáveis, portanto, a classe de implementação deve ser criada manualmente.</span><span class="sxs-lookup"><span data-stu-id="97b16-122">This code is longer than the `IAsyncEnumerable<T>` code because C# doesn't have built-in support for working with observables, so the implementation class has to be created manually.</span></span> <span data-ttu-id="97b16-123">No entanto, é uma classe genérica, portanto, uma única implementação funcionará em todos os tipos.</span><span class="sxs-lookup"><span data-stu-id="97b16-123">It's a generic class, though, so a single implementation will work across all types.</span></span>

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
> <span data-ttu-id="97b16-124">Essa implementação observável só permite `Subscribe` que o método seja chamado uma vez, pois ter vários assinantes tentando ler a partir do fluxo resultaria em caos.</span><span class="sxs-lookup"><span data-stu-id="97b16-124">This observable implementation only allows the `Subscribe` method to be called once, as having multiple subscribers trying to read from the stream would result in chaos.</span></span> <span data-ttu-id="97b16-125">Há operadores como `Replay` no [sistema. Reactive. Linq](https://www.nuget.org/packages/System.Reactive.Linq) que habilitam o armazenamento em buffer e o compartilhamento repetível de observáveis, que podem ser usados com essa implementação.</span><span class="sxs-lookup"><span data-stu-id="97b16-125">There are operators such as `Replay` in the [System.Reactive.Linq](https://www.nuget.org/packages/System.Reactive.Linq) that enable buffering and repeatable sharing of observables, which can be used with this implementation.</span></span>

<span data-ttu-id="97b16-126">A `GrpcStreamSubscription` classe manipula a enumeração `IAsyncStreamReader`do.</span><span class="sxs-lookup"><span data-stu-id="97b16-126">The `GrpcStreamSubscription` class handles the enumeration of the `IAsyncStreamReader`.</span></span>

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

<span data-ttu-id="97b16-127">Tudo o que é necessário agora é um método de extensão simples para criar o observável do leitor de fluxo.</span><span class="sxs-lookup"><span data-stu-id="97b16-127">All that is required now is a simple extension method to create the observable from the stream reader.</span></span>

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

## <a name="summary"></a><span data-ttu-id="97b16-128">Resumo</span><span class="sxs-lookup"><span data-stu-id="97b16-128">Summary</span></span>

<span data-ttu-id="97b16-129">Os `IAsyncEnumerable` modelos `IObservable` e são maneiras bem suportadas e bem documentadas de lidar com fluxos de dados assíncronos no .net.</span><span class="sxs-lookup"><span data-stu-id="97b16-129">The `IAsyncEnumerable` and `IObservable` models are both well-supported and well-documented ways of dealing with asynchronous streams of data in .NET.</span></span> <span data-ttu-id="97b16-130">o gRPC streams mapeia bem para ambos os paradigmas, oferecendo uma integração próxima com o .NET Core Framework moderno e os estilos de programação reativos/assíncronos.</span><span class="sxs-lookup"><span data-stu-id="97b16-130">gRPC streams map well to both paradigms, offering close integration with the modern .NET Core framework and reactive/asynchronous programming styles.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="97b16-131">[Anterior](streaming-versus-repeated.md)
>[Próximo](security.md)</span><span class="sxs-lookup"><span data-stu-id="97b16-131">[Previous](streaming-versus-repeated.md)
[Next](security.md)</span></span>
