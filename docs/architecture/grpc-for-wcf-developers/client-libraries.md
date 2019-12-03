---
title: Criar bibliotecas de cliente do gRPC-gRPC para desenvolvedores do WCF
description: Discussão de bibliotecas/pacotes de cliente compartilhado para serviços gRPCs.
ms.date: 09/02/2019
ms.openlocfilehash: bb58cb3cda4b0cbb3a5d34129961349bcb0093e9
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74711451"
---
# <a name="create-grpc-client-libraries"></a><span data-ttu-id="4afc8-103">Criar bibliotecas de cliente do gRPC</span><span class="sxs-lookup"><span data-stu-id="4afc8-103">Create gRPC client libraries</span></span>

<span data-ttu-id="4afc8-104">Não é necessário distribuir bibliotecas de cliente para um aplicativo gRPC.</span><span class="sxs-lookup"><span data-stu-id="4afc8-104">It isn't necessary to distribute client libraries for a gRPC application.</span></span> <span data-ttu-id="4afc8-105">Você pode criar uma biblioteca compartilhada de arquivos de `.proto` dentro de sua organização e outras equipes podem usar esses arquivos para gerar o código do cliente em seus próprios projetos.</span><span class="sxs-lookup"><span data-stu-id="4afc8-105">You can create a shared library of `.proto` files within your organization, and other teams can use those files to generate client code in their own projects.</span></span> <span data-ttu-id="4afc8-106">Mas se você tiver um repositório do NuGet privado e muitas outras equipes estiverem usando o .NET Core, você poderá criar e publicar pacotes NuGet do cliente como parte do seu projeto de serviço.</span><span class="sxs-lookup"><span data-stu-id="4afc8-106">But if you have a private NuGet repository and many other teams are using .NET Core, you can create and publish client NuGet packages as part of your service project.</span></span> <span data-ttu-id="4afc8-107">Isso pode ser uma boa maneira de compartilhar e promover seu serviço.</span><span class="sxs-lookup"><span data-stu-id="4afc8-107">This can be a good way of sharing and promoting your service.</span></span>

<span data-ttu-id="4afc8-108">Uma vantagem de distribuir uma biblioteca de cliente é que você pode aprimorar as classes gRPC e Protobuf geradas com métodos e propriedades "conveniência" úteis.</span><span class="sxs-lookup"><span data-stu-id="4afc8-108">One advantage of distributing a client library is that you can enhance the generated gRPC and Protobuf classes with helpful "convenience" methods and properties.</span></span> <span data-ttu-id="4afc8-109">No código do cliente, como no servidor, todas as classes são declaradas como `partial`, portanto, você pode estendê-las sem editar o código gerado.</span><span class="sxs-lookup"><span data-stu-id="4afc8-109">In the client code, as in the server, all the classes are declared as `partial`, so you can extend them without editing the generated code.</span></span> <span data-ttu-id="4afc8-110">Isso significa que é fácil adicionar construtores, métodos e propriedades calculadas aos tipos básicos.</span><span class="sxs-lookup"><span data-stu-id="4afc8-110">This means it's easy to add constructors, methods, and calculated properties to the basic types.</span></span>

> [!CAUTION]
> <span data-ttu-id="4afc8-111">Você não deve usar código personalizado para fornecer funcionalidade essencial.</span><span class="sxs-lookup"><span data-stu-id="4afc8-111">You shouldn't use custom code to provide essential functionality.</span></span> <span data-ttu-id="4afc8-112">Você não deseja restringir essa funcionalidade essencial às equipes do .NET que usam a biblioteca compartilhada e não fornecê-la a equipes que usam outras linguagens ou plataformas, como Python ou Java.</span><span class="sxs-lookup"><span data-stu-id="4afc8-112">You don't want to restrict that essential functionality to .NET teams that use the shared library, and not provide it to teams that use other languages or platforms, such as Python or Java.</span></span>

<span data-ttu-id="4afc8-113">Verifique se o máximo de equipes possível pode acessar o serviço gRPC.</span><span class="sxs-lookup"><span data-stu-id="4afc8-113">Ensure that as many teams as possible can access your gRPC service.</span></span> <span data-ttu-id="4afc8-114">A melhor maneira de fazer isso é compartilhar `.proto` arquivos para que os desenvolvedores possam gerar seus próprios clientes.</span><span class="sxs-lookup"><span data-stu-id="4afc8-114">The best way to do this is to share `.proto` files so developers can generate their own clients.</span></span> <span data-ttu-id="4afc8-115">Isso é particularmente verdadeiro em um ambiente de várias plataformas, em que equipes diferentes frequentemente usam estruturas e linguagens de programação diferentes, ou onde sua API é acessível externamente.</span><span class="sxs-lookup"><span data-stu-id="4afc8-115">This is particularly true in a multi-platform environment, where different teams frequently use different programming languages and frameworks, or where your API is externally accessible.</span></span>

## <a name="useful-extensions"></a><span data-ttu-id="4afc8-116">Extensões úteis</span><span class="sxs-lookup"><span data-stu-id="4afc8-116">Useful extensions</span></span>

<span data-ttu-id="4afc8-117">Há duas interfaces comumente usadas no .NET para lidar com fluxos de objetos: <xref:System.Collections.Generic.IEnumerable%601> e <xref:System.IObservable%601>.</span><span class="sxs-lookup"><span data-stu-id="4afc8-117">There are two commonly used interfaces in .NET for dealing with streams of objects: <xref:System.Collections.Generic.IEnumerable%601> and <xref:System.IObservable%601>.</span></span> <span data-ttu-id="4afc8-118">A partir do .NET Core 3,0 C# e 8,0, há uma interface <xref:System.Collections.Generic.IAsyncEnumerable%601> para processar fluxos de forma assíncrona e uma sintaxe de `await foreach` para usar a interface.</span><span class="sxs-lookup"><span data-stu-id="4afc8-118">Starting with .NET Core 3.0 and C# 8.0, there's an <xref:System.Collections.Generic.IAsyncEnumerable%601> interface for processing streams asynchronously, and an `await foreach` syntax for using the interface.</span></span> <span data-ttu-id="4afc8-119">Esta seção apresenta código reutilizável para aplicar essas interfaces a fluxos de gRPC.</span><span class="sxs-lookup"><span data-stu-id="4afc8-119">This section presents reusable code for applying these interfaces to gRPC streams.</span></span>

<span data-ttu-id="4afc8-120">Com as bibliotecas de cliente do .NET Core gRPC, há um método de extensão `ReadAllAsync` para `IAsyncStreamReader<T>` que cria uma interface `IAsyncEnumerable<T>`.</span><span class="sxs-lookup"><span data-stu-id="4afc8-120">With the .NET Core gRPC client libraries, there's a `ReadAllAsync` extension method for `IAsyncStreamReader<T>` that creates an `IAsyncEnumerable<T>` interface.</span></span> <span data-ttu-id="4afc8-121">Para os desenvolvedores que usam a programação reativa, um método de extensão equivalente para criar uma interface de `IObservable<T>` pode ser semelhante ao exemplo na seção a seguir.</span><span class="sxs-lookup"><span data-stu-id="4afc8-121">For developers using reactive programming, an equivalent extension method to create an `IObservable<T>` interface might look like the example in the following section.</span></span>

### <a name="iobservable"></a><span data-ttu-id="4afc8-122">IObservable</span><span class="sxs-lookup"><span data-stu-id="4afc8-122">IObservable</span></span>

<span data-ttu-id="4afc8-123">A interface `IObservable<T>` é o inverso "reativo" de `IEnumerable<T>`.</span><span class="sxs-lookup"><span data-stu-id="4afc8-123">The `IObservable<T>` interface is the "reactive" inverse of `IEnumerable<T>`.</span></span> <span data-ttu-id="4afc8-124">Em vez de extrair itens de um fluxo, a abordagem reativa permite que o fluxo Envie itens por push para um assinante.</span><span class="sxs-lookup"><span data-stu-id="4afc8-124">Rather than pulling items from a stream, the reactive approach lets the stream push items to a subscriber.</span></span> <span data-ttu-id="4afc8-125">Isso é muito semelhante aos fluxos de gRPC, e é fácil encapsular uma interface de `IObservable<T>` em uma interface de `IAsyncStreamReader<T>`.</span><span class="sxs-lookup"><span data-stu-id="4afc8-125">This is very similar to gRPC streams, and it's easy to wrap an `IObservable<T>` interface around an `IAsyncStreamReader<T>` interface.</span></span>

<span data-ttu-id="4afc8-126">Esse código é maior do que o código de `IAsyncEnumerable<T>` C# , porque o não tem suporte interno para trabalhar com observáveis.</span><span class="sxs-lookup"><span data-stu-id="4afc8-126">This code is longer than the `IAsyncEnumerable<T>` code, because C# doesn't have built-in support for working with observables.</span></span> <span data-ttu-id="4afc8-127">Você precisa criar a classe de implementação manualmente.</span><span class="sxs-lookup"><span data-stu-id="4afc8-127">You have to create the implementation class manually.</span></span> <span data-ttu-id="4afc8-128">No entanto, é uma classe genérica, portanto, uma única implementação funciona em todos os tipos.</span><span class="sxs-lookup"><span data-stu-id="4afc8-128">It's a generic class, though, so a single implementation works across all types.</span></span>

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
> <span data-ttu-id="4afc8-129">Essa implementação observável permite que o método `Subscribe` seja chamado apenas uma vez, porque ter vários assinantes tentando ler a partir do fluxo resultaria em caos.</span><span class="sxs-lookup"><span data-stu-id="4afc8-129">This observable implementation allows the `Subscribe` method to be called only once, because having multiple subscribers trying to read from the stream would result in chaos.</span></span> <span data-ttu-id="4afc8-130">Há operadores, como `Replay` no [sistema. Reactive. Linq](https://www.nuget.org/packages/System.Reactive.Linq), que habilitam o armazenamento em buffer e o compartilhamento reproduzível de observáveis, que podem ser usados com essa implementação.</span><span class="sxs-lookup"><span data-stu-id="4afc8-130">There are operators, such as `Replay` in the [System.Reactive.Linq](https://www.nuget.org/packages/System.Reactive.Linq), that enable buffering and repeatable sharing of observables, which can be used with this implementation.</span></span>

<span data-ttu-id="4afc8-131">A classe `GrpcStreamSubscription` manipula a enumeração do `IAsyncStreamReader`:</span><span class="sxs-lookup"><span data-stu-id="4afc8-131">The `GrpcStreamSubscription` class handles the enumeration of the `IAsyncStreamReader`:</span></span>

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

<span data-ttu-id="4afc8-132">Tudo o que é necessário agora é um método de extensão simples para criar o observável do leitor de fluxo.</span><span class="sxs-lookup"><span data-stu-id="4afc8-132">All that is required now is a simple extension method to create the observable from the stream reader.</span></span>

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

## <a name="summary"></a><span data-ttu-id="4afc8-133">Resumo</span><span class="sxs-lookup"><span data-stu-id="4afc8-133">Summary</span></span>

<span data-ttu-id="4afc8-134">Os modelos `IAsyncEnumerable` e `IObservable` são as maneiras bem suportadas e bem documentadas de lidar com fluxos de dados assíncronos no .NET.</span><span class="sxs-lookup"><span data-stu-id="4afc8-134">The `IAsyncEnumerable` and `IObservable` models are both well-supported and well-documented ways of dealing with asynchronous streams of data in .NET.</span></span> <span data-ttu-id="4afc8-135">o gRPC streams mapeia bem para ambos os paradigmas, oferecendo integração próxima com o .NET Core e estilos de programação reativos e assíncronos.</span><span class="sxs-lookup"><span data-stu-id="4afc8-135">gRPC streams map well to both paradigms, offering close integration with .NET Core, and reactive and asynchronous programming styles.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="4afc8-136">[Anterior](streaming-versus-repeated.md)
>[Próximo](security.md)</span><span class="sxs-lookup"><span data-stu-id="4afc8-136">[Previous](streaming-versus-repeated.md)
[Next](security.md)</span></span>
