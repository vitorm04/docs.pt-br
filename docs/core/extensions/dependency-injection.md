---
title: Injeção de dependência no .NET
description: Saiba como o .NET implementa a injeção de dependência e como usá-la.
author: IEvangelist
ms.author: dapine
ms.date: 10/28/2020
ms.topic: overview
ms.openlocfilehash: 2199f51ab13bedd50af747ce33ceee7b6eaefd8f
ms.sourcegitcommit: b1442669f1982d3a1cb18ea35b5acfb0fc7d93e4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93063143"
---
# <a name="dependency-injection-in-net"></a><span data-ttu-id="0d85a-103">Injeção de dependência no .NET</span><span class="sxs-lookup"><span data-stu-id="0d85a-103">Dependency injection in .NET</span></span>

<span data-ttu-id="0d85a-104">O .NET dá suporte ao padrão de design de software de injeção de dependência (DI), que é uma técnica para obter [inversão de controle (IOC)](../../architecture/modern-web-apps-azure/architectural-principles.md#dependency-inversion) entre classes e suas dependências.</span><span class="sxs-lookup"><span data-stu-id="0d85a-104">.NET supports the dependency injection (DI) software design pattern, which is a technique for achieving [Inversion of Control (IoC)](../../architecture/modern-web-apps-azure/architectural-principles.md#dependency-inversion) between classes and their dependencies.</span></span> <span data-ttu-id="0d85a-105">A injeção de dependência no .NET é um [cidadão de primeira classe](https://en.wikipedia.org/wiki/First-class_citizen), juntamente com configuração, registro em log e o padrão de opções.</span><span class="sxs-lookup"><span data-stu-id="0d85a-105">Dependency injection in .NET is a [first-class citizen](https://en.wikipedia.org/wiki/First-class_citizen), along with configuration, logging, and the options pattern.</span></span>

<span data-ttu-id="0d85a-106">Uma *dependência* é um objeto do qual outro objeto depende.</span><span class="sxs-lookup"><span data-stu-id="0d85a-106">A *dependency* is an object that another object depends on.</span></span> <span data-ttu-id="0d85a-107">Examine a seguinte `MessageWriter` classe com um `Write` método de que outras classes dependem:</span><span class="sxs-lookup"><span data-stu-id="0d85a-107">Examine the following `MessageWriter` class with a `Write` method that other classes depend on:</span></span>

```csharp
public class MessageWriter
{
    public void Write(string message)
    {
        Console.WriteLine($"MessageWriter.Write(message: \"{message}\")");
    }
}
```

<span data-ttu-id="0d85a-108">Uma classe pode criar uma instância da `MessageWriter` classe para fazer uso de seu `Write` método.</span><span class="sxs-lookup"><span data-stu-id="0d85a-108">A class can create an instance of the `MessageWriter` class to make use of its `Write` method.</span></span> <span data-ttu-id="0d85a-109">No exemplo a seguir, a `MessageWriter` classe é uma dependência da `Worker` classe:</span><span class="sxs-lookup"><span data-stu-id="0d85a-109">In the following example, the `MessageWriter` class is a dependency of the `Worker` class:</span></span>

```csharp
public class Worker : BackgroundService
{
    private readonly MessageWriter _messageWriter = new MessageWriter();

    protected override async Task ExecuteAsync(CancellationToken stoppingToken)
    {
        while (!stoppingToken.IsCancellationRequested)
        {
            _messageWriter.Write($"Worker running at: {DateTimeOffset.Now}");
            await Task.Delay(1000, stoppingToken);
        }
    }
}
```

<span data-ttu-id="0d85a-110">A classe cria e depende diretamente da `MessageWriter` classe.</span><span class="sxs-lookup"><span data-stu-id="0d85a-110">The class creates and directly depends on the `MessageWriter` class.</span></span> <span data-ttu-id="0d85a-111">As dependências embutidas em código, como no exemplo anterior, são problemáticas e devem ser evitadas pelos seguintes motivos:</span><span class="sxs-lookup"><span data-stu-id="0d85a-111">Hard-coded dependencies, such as in the previous example, are problematic and should be avoided for the following reasons:</span></span>

- <span data-ttu-id="0d85a-112">Para substituir `MessageWriter` por uma implementação diferente, a `MessageService` classe deve ser modificada.</span><span class="sxs-lookup"><span data-stu-id="0d85a-112">To replace `MessageWriter` with a different implementation, the `MessageService` class must be modified.</span></span>
- <span data-ttu-id="0d85a-113">Se `MessageWriter` tiver dependências, elas também deverão ser configuradas pela `MessageService` classe.</span><span class="sxs-lookup"><span data-stu-id="0d85a-113">If `MessageWriter` has dependencies, they must also be configured by the `MessageService` class.</span></span> <span data-ttu-id="0d85a-114">Em um projeto grande com várias classes dependendo da `MessageWriter`, o código de configuração fica pulverizado por todo o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0d85a-114">In a large project with multiple classes depending on `MessageWriter`, the configuration code becomes scattered across the app.</span></span>
- <span data-ttu-id="0d85a-115">É difícil testar a unidade dessa implementação.</span><span class="sxs-lookup"><span data-stu-id="0d85a-115">This implementation is difficult to unit test.</span></span> <span data-ttu-id="0d85a-116">O aplicativo deve usar uma simulação ou stub da classe `MessageWriter`, o que não é possível com essa abordagem.</span><span class="sxs-lookup"><span data-stu-id="0d85a-116">The app should use a mock or stub `MessageWriter` class, which isn't possible with this approach.</span></span>

<span data-ttu-id="0d85a-117">Injeção de dependência trata desses problemas da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="0d85a-117">Dependency injection addresses these problems through:</span></span>

- <span data-ttu-id="0d85a-118">O uso de uma interface ou classe base para abstrair a implementação da dependência.</span><span class="sxs-lookup"><span data-stu-id="0d85a-118">The use of an interface or base class to abstract the dependency implementation.</span></span>
- <span data-ttu-id="0d85a-119">Registrando a dependência em um contêiner de serviço.</span><span class="sxs-lookup"><span data-stu-id="0d85a-119">Registration of the dependency in a service container.</span></span> <span data-ttu-id="0d85a-120">O .NET fornece um contêiner de serviço interno, <xref:System.IServiceProvider> .</span><span class="sxs-lookup"><span data-stu-id="0d85a-120">.NET provides a built-in service container, <xref:System.IServiceProvider>.</span></span> <span data-ttu-id="0d85a-121">Normalmente, os serviços são registrados na inicialização do aplicativo e anexados a um <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection> .</span><span class="sxs-lookup"><span data-stu-id="0d85a-121">Services are typically registered at the app's start-up, and appended to an <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection>.</span></span> <span data-ttu-id="0d85a-122">Depois que todos os serviços forem adicionados, você usará <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionContainerBuilderExtensions.BuildServiceProvider%2A> para criar o contêiner de serviço.</span><span class="sxs-lookup"><span data-stu-id="0d85a-122">Once all services are added, you use <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionContainerBuilderExtensions.BuildServiceProvider%2A> to create the service container.</span></span>
- <span data-ttu-id="0d85a-123">*Injeção* do serviço no construtor da classe na qual ele é usado.</span><span class="sxs-lookup"><span data-stu-id="0d85a-123">*Injection* of the service into the constructor of the class where it's used.</span></span> <span data-ttu-id="0d85a-124">A estrutura assume a responsabilidade de criar uma instância da dependência e de descartá-la quando não for mais necessária.</span><span class="sxs-lookup"><span data-stu-id="0d85a-124">The framework takes on the responsibility of creating an instance of the dependency and disposing of it when it's no longer needed.</span></span>

<span data-ttu-id="0d85a-125">Por exemplo, a `IMessageWriter` interface define o `Write` método:</span><span class="sxs-lookup"><span data-stu-id="0d85a-125">As an example, the `IMessageWriter` interface defines the `Write` method:</span></span>

:::code language="csharp" source="snippets/configuration/dependency-injection/IMessageWriter.cs":::

<span data-ttu-id="0d85a-126">Essa interface é implementada por um tipo concreto, `MessageWriter`:</span><span class="sxs-lookup"><span data-stu-id="0d85a-126">This interface is implemented by a concrete type, `MessageWriter`:</span></span>

:::code language="csharp" source="snippets/configuration/dependency-injection/MessageWriter.cs":::

<span data-ttu-id="0d85a-127">O código de exemplo registra o `IMessageWriter` serviço com o tipo concreto `MessageWriter` .</span><span class="sxs-lookup"><span data-stu-id="0d85a-127">The sample code registers the `IMessageWriter` service with the concrete type `MessageWriter`.</span></span> <span data-ttu-id="0d85a-128">O <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionServiceExtensions.AddScoped%2A> método registra o serviço com um tempo de vida de escopo, o tempo de vida de uma única solicitação.</span><span class="sxs-lookup"><span data-stu-id="0d85a-128">The <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionServiceExtensions.AddScoped%2A> method registers the service with a scoped lifetime, the lifetime of a single request.</span></span> <span data-ttu-id="0d85a-129">Descreveremos posteriormente neste tópico os [tempos de vida do serviço](#service-lifetimes).</span><span class="sxs-lookup"><span data-stu-id="0d85a-129">[Service lifetimes](#service-lifetimes) are described later in this topic.</span></span>

:::code language="csharp" source="snippets/configuration/dependency-injection/Program.cs" highlight="16":::

<span data-ttu-id="0d85a-130">No aplicativo de exemplo, o `IMessageWriter` serviço é solicitado e usado para chamar o `Write` método:</span><span class="sxs-lookup"><span data-stu-id="0d85a-130">In the sample app, the `IMessageWriter` service is requested and used to call the `Write` method:</span></span>

:::code language="csharp" source="snippets/configuration/dependency-injection/Worker.cs":::

<span data-ttu-id="0d85a-131">Usando o padrão DI, o serviço de trabalho:</span><span class="sxs-lookup"><span data-stu-id="0d85a-131">By using the DI pattern, the worker service:</span></span>

- <span data-ttu-id="0d85a-132">Não usa o tipo concreto `MessageWriter` , apenas a `IMessageWriter` interface que o implementa.</span><span class="sxs-lookup"><span data-stu-id="0d85a-132">Doesn't use the concrete type `MessageWriter`, only the `IMessageWriter` interface that implements it.</span></span> <span data-ttu-id="0d85a-133">Isso facilita a alteração da implementação que o controlador usa sem modificar o controlador.</span><span class="sxs-lookup"><span data-stu-id="0d85a-133">That makes it easy to change the implementation that the controller uses without modifying the controller.</span></span>
- <span data-ttu-id="0d85a-134">Não cria uma instância do `MessageWriter` , ela é criada pelo contêiner de di.</span><span class="sxs-lookup"><span data-stu-id="0d85a-134">Doesn't create an instance of `MessageWriter`, it's created by the DI container.</span></span>

<span data-ttu-id="0d85a-135">A implementação da `IMessageWriter` interface pode ser aprimorada usando a API de registro em log interna:</span><span class="sxs-lookup"><span data-stu-id="0d85a-135">The implementation of the `IMessageWriter` interface can be improved by using the built-in logging API:</span></span>

:::code language="csharp" source="snippets/configuration/dependency-injection/LoggingMessageWriter.cs":::

<span data-ttu-id="0d85a-136">O `ConfigureServices` método atualizado registra a nova `IMessageWriter` implementação:</span><span class="sxs-lookup"><span data-stu-id="0d85a-136">The updated `ConfigureServices` method registers the new `IMessageWriter` implementation:</span></span>

```csharp
static IHostBuilder CreateHostBuilder(string[] args) =>
    Host.CreateDefaultBuilder(args)
        .ConfigureServices((_, services) =>
            services.AddHostedService<Worker>()
                    .AddScoped<IMessageWriter, LoggingMessageWriter>());
```

<span data-ttu-id="0d85a-137">`LoggingMessageWriter` depende de <xref:Microsoft.Extensions.Logging.ILogger%601> , que ele solicita no construtor.</span><span class="sxs-lookup"><span data-stu-id="0d85a-137">`LoggingMessageWriter` depends on <xref:Microsoft.Extensions.Logging.ILogger%601>, which it requests in the constructor.</span></span> <span data-ttu-id="0d85a-138">`ILogger<TCategoryName>` é um [serviço fornecido pelo Framework](#framework-provided-services).</span><span class="sxs-lookup"><span data-stu-id="0d85a-138">`ILogger<TCategoryName>` is a [framework-provided service](#framework-provided-services).</span></span>

<span data-ttu-id="0d85a-139">Não é incomum usar a injeção de dependência de uma maneira encadeada.</span><span class="sxs-lookup"><span data-stu-id="0d85a-139">It's not unusual to use dependency injection in a chained fashion.</span></span> <span data-ttu-id="0d85a-140">Por sua vez, cada dependência solicitada solicita suas próprias dependências.</span><span class="sxs-lookup"><span data-stu-id="0d85a-140">Each requested dependency in turn requests its own dependencies.</span></span> <span data-ttu-id="0d85a-141">O contêiner resolve as dependências no grafo e retorna o serviço totalmente resolvido.</span><span class="sxs-lookup"><span data-stu-id="0d85a-141">The container resolves the dependencies in the graph and returns the fully resolved service.</span></span> <span data-ttu-id="0d85a-142">O conjunto de dependências que precisa ser resolvido normalmente é chamado de *árvore de dependência* , *grafo de dependência* ou *grafo de objeto* .</span><span class="sxs-lookup"><span data-stu-id="0d85a-142">The collective set of dependencies that must be resolved is typically referred to as a *dependency tree* , *dependency graph* , or *object graph* .</span></span>

<span data-ttu-id="0d85a-143">O contêiner resolve aproveitando `ILogger<TCategoryName>` os [tipos abertos (genéricos)](/dotnet/csharp/language-reference/language-specification/types#open-and-closed-types), eliminando a necessidade de registrar cada [tipo construído (genérico)](/dotnet/csharp/language-reference/language-specification/types#constructed-types).</span><span class="sxs-lookup"><span data-stu-id="0d85a-143">The container resolves `ILogger<TCategoryName>` by taking advantage of [(generic) open types](/dotnet/csharp/language-reference/language-specification/types#open-and-closed-types), eliminating the need to register every [(generic) constructed type](/dotnet/csharp/language-reference/language-specification/types#constructed-types).</span></span>

<span data-ttu-id="0d85a-144">Na terminologia de injeção de dependência, um serviço:</span><span class="sxs-lookup"><span data-stu-id="0d85a-144">In dependency injection terminology, a service:</span></span>

- <span data-ttu-id="0d85a-145">Normalmente é um objeto que fornece um serviço para outros objetos, como o `IMessageWriter` serviço.</span><span class="sxs-lookup"><span data-stu-id="0d85a-145">Is typically an object that provides a service to other objects, such as the `IMessageWriter` service.</span></span>
- <span data-ttu-id="0d85a-146">O não está relacionado a um serviço Web, embora o serviço possa usar um serviço Web.</span><span class="sxs-lookup"><span data-stu-id="0d85a-146">Is not related to a web service, although the service may use a web service.</span></span>

<span data-ttu-id="0d85a-147">A estrutura fornece um sistema de registro em log robusto.</span><span class="sxs-lookup"><span data-stu-id="0d85a-147">The framework provides a robust logging system.</span></span> <span data-ttu-id="0d85a-148">As `IMessageWriter` implementações mostradas nos exemplos anteriores foram escritas para demonstrar a di básica, não para implementar o registro em log.</span><span class="sxs-lookup"><span data-stu-id="0d85a-148">The `IMessageWriter` implementations shown in the preceding examples were written to demonstrate basic DI, not to implement logging.</span></span> <span data-ttu-id="0d85a-149">A maioria dos aplicativos não deve precisar gravar agentes.</span><span class="sxs-lookup"><span data-stu-id="0d85a-149">Most apps shouldn't need to write loggers.</span></span> <span data-ttu-id="0d85a-150">O código a seguir demonstra como usar o log padrão, que requer que apenas o seja `Worker` registrado no `ConfigureServices` como um serviço hospedado <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionHostedServiceExtensions.AddHostedService%2A> :</span><span class="sxs-lookup"><span data-stu-id="0d85a-150">The following code demonstrates using the default logging, which only requires the `Worker` to be registered in `ConfigureServices` as a hosted service <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionHostedServiceExtensions.AddHostedService%2A>:</span></span>

```csharp
public class Worker : BackgroundService
{
    private readonly ILogger<Worker> _logger;

    public Worker(ILogger<Worker> logger) =>
        _logger = logger;

    protected override async Task ExecuteAsync(CancellationToken stoppingToken)
    {
        while (!stoppingToken.IsCancellationRequested)
        {
            _logger.LogInformation("Worker running at: {time}", DateTimeOffset.Now);
            await Task.Delay(1000, stoppingToken);
        }
    }
}
```

<span data-ttu-id="0d85a-151">Usando o código anterior, não há necessidade de atualizar `ConfigureServices` , porque o registro em log é fornecido pela estrutura.</span><span class="sxs-lookup"><span data-stu-id="0d85a-151">Using the preceding code, there is no need to update `ConfigureServices`, because logging is provided by the framework.</span></span>

## <a name="register-groups-of-services-with-extension-methods"></a><span data-ttu-id="0d85a-152">Registrar grupos de serviços com métodos de extensão</span><span class="sxs-lookup"><span data-stu-id="0d85a-152">Register groups of services with extension methods</span></span>

<span data-ttu-id="0d85a-153">O Microsoft Extensions usa uma Convenção para registrar um grupo de serviços relacionados.</span><span class="sxs-lookup"><span data-stu-id="0d85a-153">Microsoft Extensions uses a convention for registering a group of related services.</span></span> <span data-ttu-id="0d85a-154">A Convenção é usar um método de `Add{GROUP_NAME}` extensão único para registrar todos os serviços exigidos por um recurso de estrutura.</span><span class="sxs-lookup"><span data-stu-id="0d85a-154">The convention is to use a single `Add{GROUP_NAME}` extension method to register all of the services required by a framework feature.</span></span> <span data-ttu-id="0d85a-155">Por exemplo, o <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.AddOptions%2A> método de extensão registra todos os serviços necessários para usar as opções.</span><span class="sxs-lookup"><span data-stu-id="0d85a-155">For example, the <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.AddOptions%2A> extension method registers all of the services required for using options.</span></span>

## <a name="framework-provided-services"></a><span data-ttu-id="0d85a-156">Serviços fornecidos pela estrutura</span><span class="sxs-lookup"><span data-stu-id="0d85a-156">Framework-provided services</span></span>

<span data-ttu-id="0d85a-157">O `ConfigureServices` método registra os serviços que o aplicativo usa, incluindo recursos de plataforma.</span><span class="sxs-lookup"><span data-stu-id="0d85a-157">The `ConfigureServices` method registers services that the app uses, including platform features.</span></span> <span data-ttu-id="0d85a-158">Inicialmente, o `IServiceCollection` fornecido para o `ConfigureServices` tem serviços definidos pela estrutura, dependendo de [como o host foi configurado](generic-host.md#host-configuration).</span><span class="sxs-lookup"><span data-stu-id="0d85a-158">Initially, the `IServiceCollection` provided to `ConfigureServices` has services defined by the framework depending on [how the host was configured](generic-host.md#host-configuration).</span></span> <span data-ttu-id="0d85a-159">Para aplicativos baseados nos modelos .NET, a estrutura registra centenas de serviços.</span><span class="sxs-lookup"><span data-stu-id="0d85a-159">For apps based on the .NET templates, the framework registers hundreds of services.</span></span>

<span data-ttu-id="0d85a-160">A tabela a seguir lista uma pequena amostra desses serviços registrados no Framework:</span><span class="sxs-lookup"><span data-stu-id="0d85a-160">The following table lists a small sample of these framework-registered services:</span></span>

| <span data-ttu-id="0d85a-161">Tipo de Serviço</span><span class="sxs-lookup"><span data-stu-id="0d85a-161">Service Type</span></span>                                                                       | <span data-ttu-id="0d85a-162">Tempo de vida</span><span class="sxs-lookup"><span data-stu-id="0d85a-162">Lifetime</span></span>  |
|------------------------------------------------------------------------------------|-----------|
| <xref:Microsoft.Extensions.Hosting.IHostApplicationLifetime>                       | <span data-ttu-id="0d85a-163">Singleton</span><span class="sxs-lookup"><span data-stu-id="0d85a-163">Singleton</span></span> |
| <xref:Microsoft.Extensions.Logging.ILogger%601?displayProperty=fullName>           | <span data-ttu-id="0d85a-164">Singleton</span><span class="sxs-lookup"><span data-stu-id="0d85a-164">Singleton</span></span> |
| <xref:Microsoft.Extensions.Logging.ILoggerFactory?displayProperty=fullName>        | <span data-ttu-id="0d85a-165">Singleton</span><span class="sxs-lookup"><span data-stu-id="0d85a-165">Singleton</span></span> |
| <xref:Microsoft.Extensions.ObjectPool.ObjectPoolProvider?displayProperty=fullName> | <span data-ttu-id="0d85a-166">Singleton</span><span class="sxs-lookup"><span data-stu-id="0d85a-166">Singleton</span></span> |
| <xref:Microsoft.Extensions.Options.IConfigureOptions%601?displayProperty=fullName> | <span data-ttu-id="0d85a-167">Transitório</span><span class="sxs-lookup"><span data-stu-id="0d85a-167">Transient</span></span> |
| <xref:Microsoft.Extensions.Options.IOptions%601?displayProperty=fullName>          | <span data-ttu-id="0d85a-168">Singleton</span><span class="sxs-lookup"><span data-stu-id="0d85a-168">Singleton</span></span> |
| <xref:System.Diagnostics.DiagnosticListener?displayProperty=fullName>              | <span data-ttu-id="0d85a-169">Singleton</span><span class="sxs-lookup"><span data-stu-id="0d85a-169">Singleton</span></span> |
| <xref:System.Diagnostics.DiagnosticSource?displayProperty=fullName>                | <span data-ttu-id="0d85a-170">Singleton</span><span class="sxs-lookup"><span data-stu-id="0d85a-170">Singleton</span></span> |

## <a name="service-lifetimes"></a><span data-ttu-id="0d85a-171">Tempos de vida do serviço</span><span class="sxs-lookup"><span data-stu-id="0d85a-171">Service lifetimes</span></span>

<span data-ttu-id="0d85a-172">Os serviços podem ser registrados com um dos seguintes tempos de vida:</span><span class="sxs-lookup"><span data-stu-id="0d85a-172">Services can be registered with one of the following lifetimes:</span></span>

- <span data-ttu-id="0d85a-173">Transitório</span><span class="sxs-lookup"><span data-stu-id="0d85a-173">Transient</span></span>
- <span data-ttu-id="0d85a-174">Com escopo</span><span class="sxs-lookup"><span data-stu-id="0d85a-174">Scoped</span></span>
- <span data-ttu-id="0d85a-175">Singleton</span><span class="sxs-lookup"><span data-stu-id="0d85a-175">Singleton</span></span>

<span data-ttu-id="0d85a-176">As seções a seguir descrevem cada um dos tempos de vida anteriores.</span><span class="sxs-lookup"><span data-stu-id="0d85a-176">The following sections describe each of the preceding lifetimes.</span></span> <span data-ttu-id="0d85a-177">Escolha um tempo de vida apropriado para cada serviço registrado.</span><span class="sxs-lookup"><span data-stu-id="0d85a-177">Choose an appropriate lifetime for each registered service.</span></span>

### <a name="transient"></a><span data-ttu-id="0d85a-178">Transitório</span><span class="sxs-lookup"><span data-stu-id="0d85a-178">Transient</span></span>

<span data-ttu-id="0d85a-179">Serviços temporários de tempo de vida são criados cada vez que são solicitados pelo contêiner de serviço.</span><span class="sxs-lookup"><span data-stu-id="0d85a-179">Transient lifetime services are created each time they're requested from the service container.</span></span> <span data-ttu-id="0d85a-180">Esse tempo de vida funciona melhor para serviços leves e sem estado.</span><span class="sxs-lookup"><span data-stu-id="0d85a-180">This lifetime works best for lightweight, stateless services.</span></span> <span data-ttu-id="0d85a-181">Registre serviços transitórios com <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionServiceExtensions.AddTransient%2A> .</span><span class="sxs-lookup"><span data-stu-id="0d85a-181">Register transient services with <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionServiceExtensions.AddTransient%2A>.</span></span>

<span data-ttu-id="0d85a-182">Em aplicativos que processam solicitações, os serviços transitórios são descartados no final da solicitação.</span><span class="sxs-lookup"><span data-stu-id="0d85a-182">In apps that process requests, transient services are disposed at the end of the request.</span></span>

### <a name="scoped"></a><span data-ttu-id="0d85a-183">Com escopo</span><span class="sxs-lookup"><span data-stu-id="0d85a-183">Scoped</span></span>

<span data-ttu-id="0d85a-184">Para aplicativos Web, um tempo de vida com escopo indica que os serviços são criados uma vez por solicitação do cliente (conexão).</span><span class="sxs-lookup"><span data-stu-id="0d85a-184">For web applications a scoped lifetime indicates that services are created once per client request (connection).</span></span> <span data-ttu-id="0d85a-185">Registre os serviços com escopo com <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionServiceExtensions.AddScoped%2A> .</span><span class="sxs-lookup"><span data-stu-id="0d85a-185">Register scoped services with <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionServiceExtensions.AddScoped%2A>.</span></span>

<span data-ttu-id="0d85a-186">Em aplicativos que processam solicitações, os serviços com escopo são descartados no final da solicitação.</span><span class="sxs-lookup"><span data-stu-id="0d85a-186">In apps that process requests, scoped services are disposed at the end of the request.</span></span>

<span data-ttu-id="0d85a-187">Ao usar Entity Framework Core, o <xref:Microsoft.Extensions.DependencyInjection.EntityFrameworkServiceCollectionExtensions.AddDbContext%2A> método de extensão registra os `DbContext` tipos com um tempo de vida com escopo definido por padrão.</span><span class="sxs-lookup"><span data-stu-id="0d85a-187">When using Entity Framework Core, the <xref:Microsoft.Extensions.DependencyInjection.EntityFrameworkServiceCollectionExtensions.AddDbContext%2A> extension method registers `DbContext` types with a scoped lifetime by default.</span></span>

> [!NOTE]
> <span data-ttu-id="0d85a-188">**Não resolva** um serviço com escopo de um singleton e tenha cuidado para não fazê-lo indiretamente, por exemplo, por meio de um serviço transitório.</span><span class="sxs-lookup"><span data-stu-id="0d85a-188">Do \* **not** _ resolve a scoped service from a singleton and be careful not to do so indirectly, for example, through a transient service.</span></span> <span data-ttu-id="0d85a-189">Pode fazer com que o serviço tenha um estado incorreto durante o processamento das solicitações seguintes.</span><span class="sxs-lookup"><span data-stu-id="0d85a-189">It may cause the service to have incorrect state when processing subsequent requests.</span></span> <span data-ttu-id="0d85a-190">Não há problema em:</span><span class="sxs-lookup"><span data-stu-id="0d85a-190">It's fine to:</span></span>
>
> - <span data-ttu-id="0d85a-191">Resolva um serviço singleton de um serviço com escopo ou transitório.</span><span class="sxs-lookup"><span data-stu-id="0d85a-191">Resolve a singleton service from a scoped or transient service.</span></span>
> - <span data-ttu-id="0d85a-192">Resolva um serviço com escopo de outro serviço com escopo ou transitório.</span><span class="sxs-lookup"><span data-stu-id="0d85a-192">Resolve a scoped service from another scoped or transient service.</span></span>

<span data-ttu-id="0d85a-193">Por padrão, no ambiente de desenvolvimento, a resolução de um serviço de outro serviço com um tempo de vida maior gera uma exceção.</span><span class="sxs-lookup"><span data-stu-id="0d85a-193">By default, in the development environment, resolving a service from another service with a longer lifetime throws an exception.</span></span> <span data-ttu-id="0d85a-194">Para obter mais informações, confira [Validação de escopo](#scope-validation).</span><span class="sxs-lookup"><span data-stu-id="0d85a-194">For more information, see [Scope validation](#scope-validation).</span></span>

### <a name="singleton"></a><span data-ttu-id="0d85a-195">Singleton</span><span class="sxs-lookup"><span data-stu-id="0d85a-195">Singleton</span></span>

<span data-ttu-id="0d85a-196">Os serviços de vida útil singleton são criados:</span><span class="sxs-lookup"><span data-stu-id="0d85a-196">Singleton lifetime services are created either:</span></span>

- <span data-ttu-id="0d85a-197">Na primeira vez que forem solicitadas.</span><span class="sxs-lookup"><span data-stu-id="0d85a-197">The first time they're requested.</span></span>
- <span data-ttu-id="0d85a-198">Pelo desenvolvedor, ao fornecer uma instância de implementação diretamente para o contêiner.</span><span class="sxs-lookup"><span data-stu-id="0d85a-198">By the developer, when providing an implementation instance directly to the container.</span></span> <span data-ttu-id="0d85a-199">Essa abordagem raramente é necessária.</span><span class="sxs-lookup"><span data-stu-id="0d85a-199">This approach is rarely needed.</span></span>

<span data-ttu-id="0d85a-200">Cada solicitação subsequente da implementação do serviço do contêiner de injeção de dependência usa a mesma instância.</span><span class="sxs-lookup"><span data-stu-id="0d85a-200">Every subsequent request of the service implementation from the dependency injection container uses the same instance.</span></span> <span data-ttu-id="0d85a-201">Se o aplicativo exigir um comportamento singleton, permita que o contêiner de serviço gerencie o tempo de vida do serviço.</span><span class="sxs-lookup"><span data-stu-id="0d85a-201">If the app requires singleton behavior, allow the service container to manage the service's lifetime.</span></span> <span data-ttu-id="0d85a-202">Não implemente o padrão de design singleton e forneça código para descartar o singleton.</span><span class="sxs-lookup"><span data-stu-id="0d85a-202">Don't implement the singleton design pattern and provide code to dispose of the singleton.</span></span> <span data-ttu-id="0d85a-203">Os serviços nunca devem ser descartados pelo código que resolveu o serviço do contêiner.</span><span class="sxs-lookup"><span data-stu-id="0d85a-203">Services should never be disposed by code that resolved the service from the container.</span></span> <span data-ttu-id="0d85a-204">Se um tipo ou fábrica for registrado como um singleton, o contêiner descartará o singleton automaticamente.</span><span class="sxs-lookup"><span data-stu-id="0d85a-204">If a type or factory is registered as a singleton, the container disposes the singleton automatically.</span></span>

<span data-ttu-id="0d85a-205">Registre os serviços singleton com <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionServiceExtensions.AddSingleton%2A> .</span><span class="sxs-lookup"><span data-stu-id="0d85a-205">Register singleton services with <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionServiceExtensions.AddSingleton%2A>.</span></span> <span data-ttu-id="0d85a-206">Os serviços singleton devem ser thread-safe e geralmente são usados em serviços sem estado.</span><span class="sxs-lookup"><span data-stu-id="0d85a-206">Singleton services must be thread safe and are often used in stateless services.</span></span>

<span data-ttu-id="0d85a-207">Em aplicativos que processam solicitações, os serviços singleton são descartados quando o <xref:Microsoft.Extensions.DependencyInjection.ServiceProvider> é Descartado no desligamento do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0d85a-207">In apps that process requests, singleton services are disposed when the <xref:Microsoft.Extensions.DependencyInjection.ServiceProvider> is disposed on application shutdown.</span></span> <span data-ttu-id="0d85a-208">Como a memória não é liberada até que o aplicativo seja desligado, considere o uso de memória com um serviço singleton.</span><span class="sxs-lookup"><span data-stu-id="0d85a-208">Because memory is not released until the app is shut down, consider memory use with a singleton service.</span></span>

> [!WARNING]
> <span data-ttu-id="0d85a-209">_*_Não_*_ resolva um serviço com escopo de um singleton.</span><span class="sxs-lookup"><span data-stu-id="0d85a-209">Do _*_not_*_ resolve a scoped service from a singleton.</span></span> <span data-ttu-id="0d85a-210">Pode fazer com que o serviço tenha um estado incorreto durante o processamento das solicitações seguintes.</span><span class="sxs-lookup"><span data-stu-id="0d85a-210">It may cause the service to have incorrect state when processing subsequent requests.</span></span> <span data-ttu-id="0d85a-211">É bom resolver um serviço singleton de um serviço com escopo ou transitório.</span><span class="sxs-lookup"><span data-stu-id="0d85a-211">It's fine to resolve a singleton service from a scoped or transient service.</span></span>

## <a name="service-registration-methods"></a><span data-ttu-id="0d85a-212">Métodos de registro do serviço</span><span class="sxs-lookup"><span data-stu-id="0d85a-212">Service registration methods</span></span>

<span data-ttu-id="0d85a-213">A estrutura fornece métodos de extensão de registro de serviço que são úteis em cenários específicos:</span><span class="sxs-lookup"><span data-stu-id="0d85a-213">The framework provides service registration extension methods that are useful in specific scenarios:</span></span>

| <span data-ttu-id="0d85a-214">Método</span><span class="sxs-lookup"><span data-stu-id="0d85a-214">Method</span></span> | <span data-ttu-id="0d85a-215">Automática</span><span class="sxs-lookup"><span data-stu-id="0d85a-215">Automatic</span></span><br><span data-ttu-id="0d85a-216">objeto</span><span class="sxs-lookup"><span data-stu-id="0d85a-216">object</span></span><br><span data-ttu-id="0d85a-217">descarte</span><span class="sxs-lookup"><span data-stu-id="0d85a-217">disposal</span></span> | <span data-ttu-id="0d85a-218">Vários</span><span class="sxs-lookup"><span data-stu-id="0d85a-218">Multiple</span></span><br><span data-ttu-id="0d85a-219">implementações</span><span class="sxs-lookup"><span data-stu-id="0d85a-219">implementations</span></span> | <span data-ttu-id="0d85a-220">Passar argumentos</span><span class="sxs-lookup"><span data-stu-id="0d85a-220">Pass args</span></span> |
|--|:-:|:-:|:-:|
| `Add{LIFETIME}<{SERVICE}, {IMPLEMENTATION}>()`<br><br><span data-ttu-id="0d85a-221">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="0d85a-221">Example:</span></span><br><br>`services.AddSingleton<IMyDep, MyDep>();` | <span data-ttu-id="0d85a-222">Sim</span><span class="sxs-lookup"><span data-stu-id="0d85a-222">Yes</span></span> | <span data-ttu-id="0d85a-223">Sim</span><span class="sxs-lookup"><span data-stu-id="0d85a-223">Yes</span></span> | <span data-ttu-id="0d85a-224">Não</span><span class="sxs-lookup"><span data-stu-id="0d85a-224">No</span></span> |
| `Add{LIFETIME}<{SERVICE}>(sp => new {IMPLEMENTATION})`<br><br><span data-ttu-id="0d85a-225">Exemplos:</span><span class="sxs-lookup"><span data-stu-id="0d85a-225">Examples:</span></span><br><br>`services.AddSingleton<IMyDep>(sp => new MyDep());`<br>`services.AddSingleton<IMyDep>(sp => new MyDep(99));` | <span data-ttu-id="0d85a-226">Sim</span><span class="sxs-lookup"><span data-stu-id="0d85a-226">Yes</span></span> | <span data-ttu-id="0d85a-227">Sim</span><span class="sxs-lookup"><span data-stu-id="0d85a-227">Yes</span></span> | <span data-ttu-id="0d85a-228">Sim</span><span class="sxs-lookup"><span data-stu-id="0d85a-228">Yes</span></span> |
| `Add{LIFETIME}<{IMPLEMENTATION}>()`<br><br><span data-ttu-id="0d85a-229">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="0d85a-229">Example:</span></span><br><br>`services.AddSingleton<MyDep>();` | <span data-ttu-id="0d85a-230">Sim</span><span class="sxs-lookup"><span data-stu-id="0d85a-230">Yes</span></span> | <span data-ttu-id="0d85a-231">Não</span><span class="sxs-lookup"><span data-stu-id="0d85a-231">No</span></span> | <span data-ttu-id="0d85a-232">Não</span><span class="sxs-lookup"><span data-stu-id="0d85a-232">No</span></span> |
| `AddSingleton<{SERVICE}>(new {IMPLEMENTATION})`<br><br><span data-ttu-id="0d85a-233">Exemplos:</span><span class="sxs-lookup"><span data-stu-id="0d85a-233">Examples:</span></span><br><br>`services.AddSingleton<IMyDep>(new MyDep());`<br>`services.AddSingleton<IMyDep>(new MyDep(99));` | <span data-ttu-id="0d85a-234">Não</span><span class="sxs-lookup"><span data-stu-id="0d85a-234">No</span></span> | <span data-ttu-id="0d85a-235">Sim</span><span class="sxs-lookup"><span data-stu-id="0d85a-235">Yes</span></span> | <span data-ttu-id="0d85a-236">Sim</span><span class="sxs-lookup"><span data-stu-id="0d85a-236">Yes</span></span> |
| `AddSingleton(new {IMPLEMENTATION})`<br><br><span data-ttu-id="0d85a-237">Exemplos:</span><span class="sxs-lookup"><span data-stu-id="0d85a-237">Examples:</span></span><br><br>`services.AddSingleton(new MyDep());`<br>`services.AddSingleton(new MyDep(99));` | <span data-ttu-id="0d85a-238">Não</span><span class="sxs-lookup"><span data-stu-id="0d85a-238">No</span></span> | <span data-ttu-id="0d85a-239">Não</span><span class="sxs-lookup"><span data-stu-id="0d85a-239">No</span></span> | <span data-ttu-id="0d85a-240">Sim</span><span class="sxs-lookup"><span data-stu-id="0d85a-240">Yes</span></span> |

<span data-ttu-id="0d85a-241">Para obter mais informações sobre o descarte de tipos, consulte a seção [Descarte de serviços](dependency-injection-guidelines.md#disposal-of-services).</span><span class="sxs-lookup"><span data-stu-id="0d85a-241">For more information on type disposal, see the [Disposal of services](dependency-injection-guidelines.md#disposal-of-services) section.</span></span>

<span data-ttu-id="0d85a-242">O registro de um serviço com apenas um tipo de implementação é equivalente ao registro desse serviço com a mesma implementação e tipo de serviço.</span><span class="sxs-lookup"><span data-stu-id="0d85a-242">Registering a service with only an implementation type is equivalent to registering that service with the same implementation and service type.</span></span> <span data-ttu-id="0d85a-243">É por isso que várias implementações de um serviço não podem ser registradas usando os métodos que não usam um tipo de serviço explícito.</span><span class="sxs-lookup"><span data-stu-id="0d85a-243">This is why multiple implementations of a service cannot be registered using the methods that don't take an explicit service type.</span></span> <span data-ttu-id="0d85a-244">Esses métodos podem registrar vários _instances \* de um serviço, mas todos terão o mesmo tipo de *implementação* .</span><span class="sxs-lookup"><span data-stu-id="0d85a-244">These methods can register multiple _instances\* of a service, but they will all have the same *implementation* type.</span></span>

<span data-ttu-id="0d85a-245">Qualquer um dos métodos de registro de serviço acima pode ser usado para registrar várias instâncias de serviço do mesmo tipo de serviço.</span><span class="sxs-lookup"><span data-stu-id="0d85a-245">Any of the above service registration methods can be used to register multiple service instances of the same service type.</span></span> <span data-ttu-id="0d85a-246">No exemplo a seguir, `AddSingleton` é chamado duas vezes com `IMessageWriter` como o tipo de serviço.</span><span class="sxs-lookup"><span data-stu-id="0d85a-246">In the following example, `AddSingleton` is called twice with `IMessageWriter` as the service type.</span></span> <span data-ttu-id="0d85a-247">A segunda chamada para `AddSingleton` substitui a anterior quando resolvida como `IMessageWriter` e a adiciona à anterior quando vários serviços são resolvidos por meio de `IEnumerable<IMessageWriter>` .</span><span class="sxs-lookup"><span data-stu-id="0d85a-247">The second call to `AddSingleton` overrides the previous one when resolved as `IMessageWriter` and adds to the previous one when multiple services are resolved via `IEnumerable<IMessageWriter>`.</span></span> <span data-ttu-id="0d85a-248">Os serviços aparecem na ordem em que foram registrados quando resolvidos por meio de `IEnumerable<{SERVICE}>` .</span><span class="sxs-lookup"><span data-stu-id="0d85a-248">Services appear in the order they were registered when resolved via `IEnumerable<{SERVICE}>`.</span></span>

:::code language="csharp" source="snippets/configuration/console-di-ienumerable/Program.cs" highlight="19-24":::

<span data-ttu-id="0d85a-249">O código-fonte de exemplo anterior registra duas implementações do `IMessageWriter` .</span><span class="sxs-lookup"><span data-stu-id="0d85a-249">The preceding sample source code registers two implementations of the `IMessageWriter`.</span></span>

:::code language="csharp" source="snippets/configuration/console-di-ienumerable/ExampleService.cs" highlight="9-18":::

<span data-ttu-id="0d85a-250">O `ExampleService` define dois parâmetros de Construtor; um único `IMessageWriter` e um `IEnumerable<IMessageWriter>` .</span><span class="sxs-lookup"><span data-stu-id="0d85a-250">The `ExampleService` defines two constructor parameters; a single `IMessageWriter`, and an `IEnumerable<IMessageWriter>`.</span></span> <span data-ttu-id="0d85a-251">O único `IMessageWriter` é o último implementação a ser registrado, enquanto que `IEnumerable<IMessageWriter>` representa todas as implementações registradas.</span><span class="sxs-lookup"><span data-stu-id="0d85a-251">The single `IMessageWriter` is the last implemenation to have been registered, whereas the `IEnumerable<IMessageWriter>` represents all registered implementations.</span></span>

<span data-ttu-id="0d85a-252">A estrutura também fornece `TryAdd{LIFETIME}` métodos de extensão, que registram o serviço somente se ainda não houver uma implementação registrada.</span><span class="sxs-lookup"><span data-stu-id="0d85a-252">The framework also provides `TryAdd{LIFETIME}` extension methods, which register the service only if there isn't already an implementation registered.</span></span>

<span data-ttu-id="0d85a-253">No exemplo a seguir, a chamada para `AddSingleton` registra `ConsoleMessageWriter` como uma implementação para `IMessageWriter` .</span><span class="sxs-lookup"><span data-stu-id="0d85a-253">In the following example, the call to `AddSingleton` registers `ConsoleMessageWriter` as an implementation for `IMessageWriter`.</span></span> <span data-ttu-id="0d85a-254">A chamada para `TryAddSingleton` não tem efeito porque `IMessageWriter` já tem uma implementação registrada:</span><span class="sxs-lookup"><span data-stu-id="0d85a-254">The call to `TryAddSingleton` has no effect because `IMessageWriter` already has a registered implementation:</span></span>

```csharp
services.AddSingleton<IMessageWriter, ConsoleMessageWriter>();
services.TryAddSingleton<IMessageWriter, LoggingMessageWriter>();
```

<span data-ttu-id="0d85a-255">O `TryAddSingleton` não tem efeito, pois já foi adicionado e o "try" falhará.</span><span class="sxs-lookup"><span data-stu-id="0d85a-255">The `TryAddSingleton` has no effect, as it was already added and the "try" will fail.</span></span> <span data-ttu-id="0d85a-256">O `ExampleService` declararia o seguinte:</span><span class="sxs-lookup"><span data-stu-id="0d85a-256">The `ExampleService` would assert the following:</span></span>

```csharp
public class ExampleService
{
    public ExampleService(
        IMessageWriter messageWriter,
        IEnumerable<IMessageWriter> messageWriters)
    {
        Trace.Assert(messageWriter is ConsoleMessageWriter);
        Trace.Assert(messageWriters.Single() is ConsoleMessageWriter);
    }
}
```

<span data-ttu-id="0d85a-257">Para obter mais informações, consulte:</span><span class="sxs-lookup"><span data-stu-id="0d85a-257">For more information, see:</span></span>

- <xref:Microsoft.Extensions.DependencyInjection.Extensions.ServiceCollectionDescriptorExtensions.TryAdd%2A>
- <xref:Microsoft.Extensions.DependencyInjection.Extensions.ServiceCollectionDescriptorExtensions.TryAddTransient%2A>
- <xref:Microsoft.Extensions.DependencyInjection.Extensions.ServiceCollectionDescriptorExtensions.TryAddScoped%2A>
- <xref:Microsoft.Extensions.DependencyInjection.Extensions.ServiceCollectionDescriptorExtensions.TryAddSingleton%2A>

<span data-ttu-id="0d85a-258">Os métodos [TryAddEnumerable (Service Descriptor)](xref:Microsoft.Extensions.DependencyInjection.Extensions.ServiceCollectionDescriptorExtensions.TryAddEnumerable%2A) registram o serviço somente se ainda não houver uma implementação *do mesmo tipo* .</span><span class="sxs-lookup"><span data-stu-id="0d85a-258">The [TryAddEnumerable(ServiceDescriptor)](xref:Microsoft.Extensions.DependencyInjection.Extensions.ServiceCollectionDescriptorExtensions.TryAddEnumerable%2A) methods register the service only if there isn't already an implementation *of the same type* .</span></span> <span data-ttu-id="0d85a-259">Vários serviços são resolvidos via `IEnumerable<{SERVICE}>`.</span><span class="sxs-lookup"><span data-stu-id="0d85a-259">Multiple services are resolved via `IEnumerable<{SERVICE}>`.</span></span> <span data-ttu-id="0d85a-260">Ao registrar serviços, adicione uma instância se um dos mesmos tipos ainda não tiver sido adicionado.</span><span class="sxs-lookup"><span data-stu-id="0d85a-260">When registering services, add an instance if one of the same types hasn't already been added.</span></span> <span data-ttu-id="0d85a-261">Os autores de biblioteca usam `TryAddEnumerable` para evitar o registro de várias cópias de uma implementação no contêiner.</span><span class="sxs-lookup"><span data-stu-id="0d85a-261">Library authors use `TryAddEnumerable` to avoid registering multiple copies of an implementation in the container.</span></span>

<span data-ttu-id="0d85a-262">No exemplo a seguir, a primeira chamada para `TryAddEnumerable` registra `MessageWriter` como uma implementação para `IMessageWriter1` .</span><span class="sxs-lookup"><span data-stu-id="0d85a-262">In the following example, the first call to `TryAddEnumerable` registers `MessageWriter` as an implementation for `IMessageWriter1`.</span></span> <span data-ttu-id="0d85a-263">A segunda chamada é registrada `MessageWriter` para `IMessageWriter2` .</span><span class="sxs-lookup"><span data-stu-id="0d85a-263">The second call registers `MessageWriter` for `IMessageWriter2`.</span></span> <span data-ttu-id="0d85a-264">A terceira chamada não tem nenhum efeito porque `IMessageWriter1` já tem uma implementação registrada de `MessageWriter` :</span><span class="sxs-lookup"><span data-stu-id="0d85a-264">The third call has no effect because `IMessageWriter1` already has a registered implementation of `MessageWriter`:</span></span>

```csharp
public interface IMessageWriter1 { }
public interface IMessageWriter2 { }

public class MessageWriter : IMessageWriter1, IMessageWriter2
{
}

services.TryAddEnumerable(ServiceDescriptor.Singleton<IMessageWriter1, MessageWriter>());
services.TryAddEnumerable(ServiceDescriptor.Singleton<IMessageWriter2, MessageWriter>());
services.TryAddEnumerable(ServiceDescriptor.Singleton<IMessageWriter1, MessageWriter>());
```

<span data-ttu-id="0d85a-265">O registro de serviço geralmente é independente de ordem, exceto ao registrar várias implementações do mesmo tipo.</span><span class="sxs-lookup"><span data-stu-id="0d85a-265">Service registration is generally order independent except when registering multiple implementations of the same type.</span></span>

<span data-ttu-id="0d85a-266">`IServiceCollection` é uma coleção de <xref:Microsoft.Extensions.DependencyInjection.ServiceDescriptor> objetos.</span><span class="sxs-lookup"><span data-stu-id="0d85a-266">`IServiceCollection` is a collection of <xref:Microsoft.Extensions.DependencyInjection.ServiceDescriptor> objects.</span></span> <span data-ttu-id="0d85a-267">O exemplo a seguir mostra como registrar um serviço criando e adicionando um `ServiceDescriptor` :</span><span class="sxs-lookup"><span data-stu-id="0d85a-267">The following example shows how to register a service by creating and adding a `ServiceDescriptor`:</span></span>

```csharp
string secretKey = Configuration["SecretKey"];
var descriptor = new ServiceDescriptor(
    typeof(IMessageWriter),
    _ => new DefaultMessageWriter(secretKey),
    ServiceLifetime.Transient);

services.Add(descriptor);
```

<span data-ttu-id="0d85a-268">Os `Add{LIFETIME}` métodos internos usam a mesma abordagem.</span><span class="sxs-lookup"><span data-stu-id="0d85a-268">The built-in `Add{LIFETIME}` methods use the same approach.</span></span> <span data-ttu-id="0d85a-269">Por exemplo, consulte o [código-fonte de Addscoped](https://github.com/dotnet/extensions/blob/v3.1.8/src/DependencyInjection/DI.Abstractions/src/ServiceCollectionServiceExtensions.cs#L216-L237).</span><span class="sxs-lookup"><span data-stu-id="0d85a-269">For example, see the [AddScoped source code](https://github.com/dotnet/extensions/blob/v3.1.8/src/DependencyInjection/DI.Abstractions/src/ServiceCollectionServiceExtensions.cs#L216-L237).</span></span>

### <a name="constructor-injection-behavior"></a><span data-ttu-id="0d85a-270">Comportamento da injeção de construtor</span><span class="sxs-lookup"><span data-stu-id="0d85a-270">Constructor injection behavior</span></span>

<span data-ttu-id="0d85a-271">Os serviços podem ser resolvidos usando:</span><span class="sxs-lookup"><span data-stu-id="0d85a-271">Services can be resolved by using:</span></span>

- <xref:System.IServiceProvider>
- <span data-ttu-id="0d85a-272"><xref:Microsoft.Extensions.DependencyInjection.ActivatorUtilities>:</span><span class="sxs-lookup"><span data-stu-id="0d85a-272"><xref:Microsoft.Extensions.DependencyInjection.ActivatorUtilities>:</span></span>
  - <span data-ttu-id="0d85a-273">Cria objetos que não estão registrados no contêiner.</span><span class="sxs-lookup"><span data-stu-id="0d85a-273">Creates objects that aren't registered in the container.</span></span>
  - <span data-ttu-id="0d85a-274">Usado com alguns recursos de estrutura.</span><span class="sxs-lookup"><span data-stu-id="0d85a-274">Used with some framework features.</span></span>

<span data-ttu-id="0d85a-275">Os construtores podem aceitar argumentos que não são fornecidos pela injeção de dependência, mas que precisam atribuir valores padrão.</span><span class="sxs-lookup"><span data-stu-id="0d85a-275">Constructors can accept arguments that aren't provided by dependency injection, but the arguments must assign default values.</span></span>

<span data-ttu-id="0d85a-276">Quando os serviços são resolvidos por `IServiceProvider` ou `ActivatorUtilities`, a injeção do construtor exige um construtor *público* .</span><span class="sxs-lookup"><span data-stu-id="0d85a-276">When services are resolved by `IServiceProvider` or `ActivatorUtilities`, constructor injection requires a *public* constructor.</span></span>

<span data-ttu-id="0d85a-277">Quando os serviços são resolvidos por `ActivatorUtilities`, a injeção de construtor exige a existência de apenas de um construtor aplicável.</span><span class="sxs-lookup"><span data-stu-id="0d85a-277">When services are resolved by `ActivatorUtilities`, constructor injection requires that only one applicable constructor exists.</span></span> <span data-ttu-id="0d85a-278">Há suporte para sobrecargas de construtor, mas somente uma sobrecarga pode existir, cujos argumentos podem ser todos atendidos pela injeção de dependência.</span><span class="sxs-lookup"><span data-stu-id="0d85a-278">Constructor overloads are supported, but only one overload can exist whose arguments can all be fulfilled by dependency injection.</span></span>

## <a name="scope-validation"></a><span data-ttu-id="0d85a-279">Validação de escopo</span><span class="sxs-lookup"><span data-stu-id="0d85a-279">Scope validation</span></span>

<span data-ttu-id="0d85a-280">Quando o aplicativo é executado no `Development` ambiente e chama [CreateDefaultBuilder](generic-host.md#default-builder-settings) para criar o host, o provedor de serviço padrão executa verificações para verificar se:</span><span class="sxs-lookup"><span data-stu-id="0d85a-280">When the app runs in the `Development` environment and calls [CreateDefaultBuilder](generic-host.md#default-builder-settings) to build the host, the default service provider performs checks to verify that:</span></span>

- <span data-ttu-id="0d85a-281">Os serviços com escopo não são resolvidos do provedor de serviços raiz.</span><span class="sxs-lookup"><span data-stu-id="0d85a-281">Scoped services aren't resolved from the root service provider.</span></span>
- <span data-ttu-id="0d85a-282">Os serviços com escopo não são injetados em singletons.</span><span class="sxs-lookup"><span data-stu-id="0d85a-282">Scoped services aren't injected into singletons.</span></span>

<span data-ttu-id="0d85a-283">O provedor de serviços raiz é criado quando <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionContainerBuilderExtensions.BuildServiceProvider%2A> é chamado.</span><span class="sxs-lookup"><span data-stu-id="0d85a-283">The root service provider is created when <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionContainerBuilderExtensions.BuildServiceProvider%2A> is called.</span></span> <span data-ttu-id="0d85a-284">O tempo de vida do provedor de serviço raiz corresponde ao tempo de vida do aplicativo quando o provedor começa com o aplicativo e é Descartado quando o aplicativo é desligado.</span><span class="sxs-lookup"><span data-stu-id="0d85a-284">The root service provider's lifetime corresponds to the app's lifetime when the provider starts with the app and is disposed when the app shuts down.</span></span>

<span data-ttu-id="0d85a-285">Os serviços com escopo são descartados pelo contêiner que os criou.</span><span class="sxs-lookup"><span data-stu-id="0d85a-285">Scoped services are disposed by the container that created them.</span></span> <span data-ttu-id="0d85a-286">Se um serviço com escopo for criado no contêiner raiz, o tempo de vida do serviço será efetivamente promovido para singleton porque é descartado apenas pelo contêiner raiz quando o aplicativo é desligado.</span><span class="sxs-lookup"><span data-stu-id="0d85a-286">If a scoped service is created in the root container, the service's lifetime is effectively promoted to singleton because it's only disposed by the root container when the app shuts down.</span></span> <span data-ttu-id="0d85a-287">A validação dos escopos de serviço detecta essas situações quando `BuildServiceProvider` é chamado.</span><span class="sxs-lookup"><span data-stu-id="0d85a-287">Validating service scopes catches these situations when `BuildServiceProvider` is called.</span></span>

## <a name="see-also"></a><span data-ttu-id="0d85a-288">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0d85a-288">See also</span></span>

- [<span data-ttu-id="0d85a-289">Usar injeção de dependência no .NET</span><span class="sxs-lookup"><span data-stu-id="0d85a-289">Use dependency injection in .NET</span></span>](dependency-injection-usage.md)
- [<span data-ttu-id="0d85a-290">Diretrizes de injeção de dependência</span><span class="sxs-lookup"><span data-stu-id="0d85a-290">Dependency injection guidelines</span></span>](dependency-injection-guidelines.md)
- [<span data-ttu-id="0d85a-291">Injeção de dependência no ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="0d85a-291">Dependency injection in ASP.NET Core</span></span>](/aspnet/core/fundamentals/dependency-injection)
- [<span data-ttu-id="0d85a-292">Padrões de conferência NDC para desenvolvimento de aplicativo de DI</span><span class="sxs-lookup"><span data-stu-id="0d85a-292">NDC Conference Patterns for DI app development</span></span>](https://www.youtube.com/watch?v=x-C-CNBVTaY)
- [<span data-ttu-id="0d85a-293">Princípio de dependências explícitas</span><span class="sxs-lookup"><span data-stu-id="0d85a-293">Explicit dependencies principle</span></span>](../../architecture/modern-web-apps-azure/architectural-principles.md#explicit-dependencies)
- [<span data-ttu-id="0d85a-294">Inversão de contêineres de controle e padrão de injeção de dependência (Martin Fowler)</span><span class="sxs-lookup"><span data-stu-id="0d85a-294">Inversion of control containers and the dependency injection pattern (Martin Fowler)</span></span>](https://www.martinfowler.com/articles/injection.html)
- <span data-ttu-id="0d85a-295">Os bugs de injeção de erros devem ser criados no repositório [github.com/dotnet/Extensions](https://github.com/dotnet/extensions/issues)</span><span class="sxs-lookup"><span data-stu-id="0d85a-295">DI bugs should be created in the [github.com/dotnet/extensions](https://github.com/dotnet/extensions/issues) repo</span></span>
