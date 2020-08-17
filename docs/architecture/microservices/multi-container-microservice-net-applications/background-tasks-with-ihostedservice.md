---
title: Implementar tarefas em segundo plano em microsserviços com IHostedService e a classe BackgroundService
description: Arquitetura de microsserviços do .NET para aplicativos .NET em contêineres | Compreenda as novas opções para usar IHostedService e BackgroundService para implementar tarefas em segundo plano em microsserviços do .NET Core.
ms.date: 08/14/2020
ms.openlocfilehash: 4ab215f2196cd2e66b116465c3a582a9846c8066
ms.sourcegitcommit: 0100be20fcf23f61dab672deced70059ed71bb2e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88267991"
---
# <a name="implement-background-tasks-in-microservices-with-ihostedservice-and-the-backgroundservice-class"></a><span data-ttu-id="99fc6-103">Implementar tarefas em segundo plano em microsserviços com IHostedService e a classe BackgroundService</span><span class="sxs-lookup"><span data-stu-id="99fc6-103">Implement background tasks in microservices with IHostedService and the BackgroundService class</span></span>

<span data-ttu-id="99fc6-104">Tarefas em segundo plano e trabalhos agendados são algo que talvez você precise usar em qualquer aplicativo, seja ou não após o padrão de arquitetura de microserviços.</span><span class="sxs-lookup"><span data-stu-id="99fc6-104">Background tasks and scheduled jobs are something you might need to use in any application, whether or not it follows the microservices architecture pattern.</span></span> <span data-ttu-id="99fc6-105">A diferença ao usar uma arquitetura de microserviços é que você pode implementar a tarefa em segundo plano em um processo/contêiner separado para hospedagem, de modo que você possa dimensioná-la verticalmente com base em sua necessidade.</span><span class="sxs-lookup"><span data-stu-id="99fc6-105">The difference when using a microservices architecture is that you can implement the background task in a separate process/container for hosting so you can scale it down/up based on your need.</span></span>

<span data-ttu-id="99fc6-106">De um ponto de vista genérico, no .NET Core, chamamos esses tipos de tarefas de *Serviços Hospedados*, porque são serviços/lógica que você hospeda em seu host/aplicativo/microsserviço.</span><span class="sxs-lookup"><span data-stu-id="99fc6-106">From a generic point of view, in .NET Core we called these type of tasks *Hosted Services*, because they are services/logic that you host within your host/application/microservice.</span></span> <span data-ttu-id="99fc6-107">Observe que, neste caso, o serviço hospedado simplesmente significa uma classe com a lógica de tarefa em segundo plano.</span><span class="sxs-lookup"><span data-stu-id="99fc6-107">Note that in this case, the hosted service simply means a class with the background task logic.</span></span>

<span data-ttu-id="99fc6-108">Desde o .NET Core 2.0, a estrutura fornece uma nova interface chamada <xref:Microsoft.Extensions.Hosting.IHostedService>, ajudando você a implementar serviços hospedados facilmente.</span><span class="sxs-lookup"><span data-stu-id="99fc6-108">Since .NET Core 2.0, the framework provides a new interface named <xref:Microsoft.Extensions.Hosting.IHostedService> helping you to easily implement hosted services.</span></span> <span data-ttu-id="99fc6-109">A ideia básica é que você pode registrar várias tarefas em segundo plano (serviços hospedados) que são executadas em segundo plano enquanto o host ou o servidor Web está em execução, conforme mostrado na imagem 6-26.</span><span class="sxs-lookup"><span data-stu-id="99fc6-109">The basic idea is that you can register multiple background tasks (hosted services) that run in the background while your web host or host is running, as shown in the image 6-26.</span></span>

![Diagrama comparando ASP.NET Core IWebHost e o .NET Core IHost.](./media/background-tasks-with-ihostedservice/ihosted-service-webhost-vs-host.png)

<span data-ttu-id="99fc6-111">**Figura 6-26**.</span><span class="sxs-lookup"><span data-stu-id="99fc6-111">**Figure 6-26**.</span></span> <span data-ttu-id="99fc6-112">Usando IHostedService em WebHost versus um Host</span><span class="sxs-lookup"><span data-stu-id="99fc6-112">Using IHostedService in a WebHost vs. a Host</span></span>

<span data-ttu-id="99fc6-113">Suporte a ASP.NET Core 1. x e 2. x `IWebHost` para processos em segundo plano em aplicativos Web.</span><span class="sxs-lookup"><span data-stu-id="99fc6-113">ASP.NET Core 1.x and 2.x support `IWebHost` for background processes in web apps.</span></span> <span data-ttu-id="99fc6-114">O .NET Core 2,1 e versões posteriores dão suporte a `IHost` processos em segundo plano com aplicativos de console simples.</span><span class="sxs-lookup"><span data-stu-id="99fc6-114">.NET Core 2.1 and later versions support `IHost` for background processes with plain console apps.</span></span> <span data-ttu-id="99fc6-115">Observe a diferença entre `WebHost` e `Host`.</span><span class="sxs-lookup"><span data-stu-id="99fc6-115">Note the difference made between `WebHost` and `Host`.</span></span>

<span data-ttu-id="99fc6-116">R `WebHost` (classe base implementando `IWebHost` ) no ASP.NET Core 2,0 é o artefato de infraestrutura que você usa para fornecer recursos de servidor http para seu processo, como quando você está implementando um aplicativo Web MVC ou serviço de API Web.</span><span class="sxs-lookup"><span data-stu-id="99fc6-116">A `WebHost` (base class implementing `IWebHost`) in ASP.NET Core 2.0 is the infrastructure artifact you use to provide HTTP server features to your process, such as when you're implementing an MVC web app or Web API service.</span></span> <span data-ttu-id="99fc6-117">Ele fornece toda a nova qualidade de infraestrutura no ASP.NET Core, permitindo que você use a injeção de dependência, insira middleware no pipeline de solicitação e semelhante.</span><span class="sxs-lookup"><span data-stu-id="99fc6-117">It provides all the new infrastructure goodness in ASP.NET Core, enabling you to use dependency injection, insert middlewares in the request pipeline, and similar.</span></span> <span data-ttu-id="99fc6-118">O `WebHost` usa esses mesmos `IHostedServices` para tarefas em segundo plano.</span><span class="sxs-lookup"><span data-stu-id="99fc6-118">The `WebHost` uses these very same `IHostedServices` for background tasks.</span></span>

<span data-ttu-id="99fc6-119">Um `Host` (classe base que implementa `IHost`) foi introduzido no .NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="99fc6-119">A `Host` (base class implementing `IHost`) was introduced in .NET Core 2.1.</span></span> <span data-ttu-id="99fc6-120">Basicamente, um `Host` permite que você tenha uma infraestrutura semelhante àquela que você tem com `WebHost` (injeção de dependência, serviços hospedados etc.), mas, nesse caso, você quer apenas ter um processo simples e mais leve como o host, sem nada relacionado ao MVC, à API da Web ou aos recursos de servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="99fc6-120">Basically, a `Host` allows you to have a similar infrastructure than what you have with `WebHost` (dependency injection, hosted services, etc.), but in this case, you just want to have a simple and lighter process as the host, with nothing related to MVC, Web API or HTTP server features.</span></span>

<span data-ttu-id="99fc6-121">Portanto, você pode escolher e criar um processo de host especializado com `IHost` o para lidar com os serviços hospedados e nada mais, como um microserviço feito apenas para hospedar o `IHostedServices` , ou então você pode estender uma ASP.NET Core existente `WebHost` , como uma API Web existente ASP.NET Core ou um aplicativo MVC.</span><span class="sxs-lookup"><span data-stu-id="99fc6-121">Therefore, you can choose and either create a specialized host-process with `IHost` to handle the hosted services and nothing else, such a microservice made just for hosting the `IHostedServices`, or you can alternatively extend an existing ASP.NET Core `WebHost`, such as an existing ASP.NET Core Web API or MVC app.</span></span>

<span data-ttu-id="99fc6-122">Cada abordagem tem vantagens e desvantagens, dependendo de suas necessidades de negócios e escalabilidade.</span><span class="sxs-lookup"><span data-stu-id="99fc6-122">Each approach has pros and cons depending on your business and scalability needs.</span></span> <span data-ttu-id="99fc6-123">A linha inferior é basicamente que se as tarefas em segundo plano não têm nada a ver com HTTP ( `IWebHost` ), você deve usar `IHost` .</span><span class="sxs-lookup"><span data-stu-id="99fc6-123">The bottom line is basically that if your background tasks have nothing to do with HTTP (`IWebHost`) you should use `IHost`.</span></span>

## <a name="registering-hosted-services-in-your-webhost-or-host"></a><span data-ttu-id="99fc6-124">Registro de serviços hospedados em seu WebHost ou Host</span><span class="sxs-lookup"><span data-stu-id="99fc6-124">Registering hosted services in your WebHost or Host</span></span>

<span data-ttu-id="99fc6-125">Vamos detalhar mais detalhadamente a `IHostedService` interface, pois seu uso é bastante semelhante em um `WebHost` ou em um `Host` .</span><span class="sxs-lookup"><span data-stu-id="99fc6-125">Let's drill down further on the `IHostedService` interface since its usage is pretty similar in a `WebHost` or in a `Host`.</span></span>

<span data-ttu-id="99fc6-126">SignalR é um exemplo de um artefato usando serviços hospedados, mas você também pode usá-lo para itens muito mais simples, como:</span><span class="sxs-lookup"><span data-stu-id="99fc6-126">SignalR is one example of an artifact using hosted services, but you can also use it for much simpler things like:</span></span>

- <span data-ttu-id="99fc6-127">Uma tarefa em segundo plano sondando um banco de dados em busca de alterações.</span><span class="sxs-lookup"><span data-stu-id="99fc6-127">A background task polling a database looking for changes.</span></span>
- <span data-ttu-id="99fc6-128">Uma tarefa agendada atualizando algum cache periodicamente.</span><span class="sxs-lookup"><span data-stu-id="99fc6-128">A scheduled task updating some cache periodically.</span></span>
- <span data-ttu-id="99fc6-129">Uma implementação de QueueBackgroundWorkItem que permite que uma tarefa seja executada em um thread em segundo plano.</span><span class="sxs-lookup"><span data-stu-id="99fc6-129">An implementation of QueueBackgroundWorkItem that allows a task to be executed on a background thread.</span></span>
- <span data-ttu-id="99fc6-130">Processamento de mensagens de uma fila de mensagens em segundo plano de um aplicativo Web enquanto se compartilham serviços comuns como `ILogger`.</span><span class="sxs-lookup"><span data-stu-id="99fc6-130">Processing messages from a message queue in the background of a web app while sharing common services such as `ILogger`.</span></span>
- <span data-ttu-id="99fc6-131">Uma tarefa em segundo plano iniciada com `Task.Run()`.</span><span class="sxs-lookup"><span data-stu-id="99fc6-131">A background task started with `Task.Run()`.</span></span>

<span data-ttu-id="99fc6-132">Basicamente, você pode descarregar qualquer uma dessas ações em uma tarefa em segundo plano que implementa o `IHostedService` .</span><span class="sxs-lookup"><span data-stu-id="99fc6-132">You can basically offload any of those actions to a background task that implements `IHostedService`.</span></span>

<span data-ttu-id="99fc6-133">A maneira como você adiciona um ou vários `IHostedServices` em seu `WebHost` ou `Host` está registrando-os por meio do <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionHostedServiceExtensions.AddHostedService%2A>   método de extensão em um ASP.NET Core `WebHost` (ou em um `Host` no .NET Core 2,1 e posterior).</span><span class="sxs-lookup"><span data-stu-id="99fc6-133">The way you add one or multiple `IHostedServices` into your `WebHost` or `Host` is by registering them up through the <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionHostedServiceExtensions.AddHostedService%2A> extension method in an ASP.NET Core `WebHost` (or in a `Host` in .NET Core 2.1 and above).</span></span> <span data-ttu-id="99fc6-134">Basicamente, você deve registrar os serviços hospedados no método `ConfigureServices()` familiar da classe `Startup`, como no código a seguir de um WebHost ASP.NET típico.</span><span class="sxs-lookup"><span data-stu-id="99fc6-134">Basically, you have to register the hosted services within the familiar `ConfigureServices()` method of the `Startup` class, as in the following code from a typical ASP.NET WebHost.</span></span>

```csharp
public IServiceProvider ConfigureServices(IServiceCollection services)
{
    //Other DI registrations;

    // Register Hosted Services
    services.AddHostedService<GracePeriodManagerService>();
    services.AddHostedService<MyHostedServiceB>();
    services.AddHostedService<MyHostedServiceC>();
    //...
}
```

<span data-ttu-id="99fc6-135">Nesse código, o serviço hospedado `GracePeriodManagerService` é o código real do microsserviço de negócios de Ordenação em eShopOnContainers, enquanto os outros dois são apenas dois exemplos adicionais.</span><span class="sxs-lookup"><span data-stu-id="99fc6-135">In that code, the `GracePeriodManagerService` hosted service is real code from the Ordering business microservice in eShopOnContainers, while the other two are just two additional samples.</span></span>

<span data-ttu-id="99fc6-136">A execução da tarefa em segundo plano `IHostedService` é coordenada com o tempo de vida do aplicativo (ou seja, host ou microsserviço).</span><span class="sxs-lookup"><span data-stu-id="99fc6-136">The `IHostedService` background task execution is coordinated with the lifetime of the application (host or microservice, for that matter).</span></span> <span data-ttu-id="99fc6-137">Você registra tarefas quando o aplicativo é iniciado e você tem a oportunidade de fazer alguma ação normal ou limpeza quando o aplicativo está sendo desligado.</span><span class="sxs-lookup"><span data-stu-id="99fc6-137">You register tasks when the application starts and you have the opportunity to do some graceful action or clean-up when the application is shutting down.</span></span>

<span data-ttu-id="99fc6-138">Sem usar `IHostedService`, você sempre pode iniciar um thread em segundo plano para executar qualquer tarefa.</span><span class="sxs-lookup"><span data-stu-id="99fc6-138">Without using `IHostedService`, you could always start a background thread to run any task.</span></span> <span data-ttu-id="99fc6-139">A diferença é precisamente no tempo de desligamento do aplicativo quando esse thread simplesmente fosse encerrado sem a oportunidade de executar ações de limpeza normais.</span><span class="sxs-lookup"><span data-stu-id="99fc6-139">The difference is precisely at the app's shutdown time when that thread would simply be killed without having the opportunity to run graceful clean-up actions.</span></span>

## <a name="the-ihostedservice-interface"></a><span data-ttu-id="99fc6-140">A interface IHostedService</span><span class="sxs-lookup"><span data-stu-id="99fc6-140">The IHostedService interface</span></span>

<span data-ttu-id="99fc6-141">Quando você registra um `IHostedService`, o .NET Core chamará os métodos `StartAsync()` e `StopAsync()` de seu tipo `IHostedService` durante o início e a parada do aplicativo, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="99fc6-141">When you register an `IHostedService`, .NET Core will call the `StartAsync()` and `StopAsync()` methods of your `IHostedService` type during application start and stop respectively.</span></span> <span data-ttu-id="99fc6-142">Para obter mais detalhes, consulte a [interface IHostedService](https://docs.microsoft.com/aspnet/core/fundamentals/host/hosted-services?view=aspnetcore-3.1&tabs=visual-studio#ihostedservice-interface)</span><span class="sxs-lookup"><span data-stu-id="99fc6-142">For more details, refer [IHostedService interface](https://docs.microsoft.com/aspnet/core/fundamentals/host/hosted-services?view=aspnetcore-3.1&tabs=visual-studio#ihostedservice-interface)</span></span>

<span data-ttu-id="99fc6-143">Como você pode imaginar, é possível criar várias implementações de IHostedService e registrá-las no método `ConfigureService()` no contêiner de ID, como mostrado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="99fc6-143">As you can imagine, you can create multiple implementations of IHostedService and register them at the `ConfigureService()` method into the DI container, as shown previously.</span></span> <span data-ttu-id="99fc6-144">Todos esses serviços hospedados serão iniciados e interrompidos junto com o aplicativo/microsserviço.</span><span class="sxs-lookup"><span data-stu-id="99fc6-144">All those hosted services will be started and stopped along with the application/microservice.</span></span>

<span data-ttu-id="99fc6-145">Como desenvolvedor, você é responsável por lidar com a ação de parada de seus serviços quando o método `StopAsync()` é disparado pelo host.</span><span class="sxs-lookup"><span data-stu-id="99fc6-145">As a developer, you are responsible for handling the stopping action of your services when `StopAsync()` method is triggered by the host.</span></span>

## <a name="implementing-ihostedservice-with-a-custom-hosted-service-class-deriving-from-the-backgroundservice-base-class"></a><span data-ttu-id="99fc6-146">Implementando IHostedService com uma classe de serviço hospedado personalizado derivado da classe base BackgroundService</span><span class="sxs-lookup"><span data-stu-id="99fc6-146">Implementing IHostedService with a custom hosted service class deriving from the BackgroundService base class</span></span>

<span data-ttu-id="99fc6-147">Vá em frente e crie sua classe de serviço hospedado personalizada do zero e implemente o `IHostedService`, como você precisa fazer ao usar o .NET Core 2.0.</span><span class="sxs-lookup"><span data-stu-id="99fc6-147">You could go ahead and create your custom hosted service class from scratch and implement the `IHostedService`, as you need to do when using .NET Core 2.0.</span></span>

<span data-ttu-id="99fc6-148">No entanto, como a maioria das tarefas em segundo plano terá necessidades semelhantes em relação ao gerenciamento de tokens de cancelamento e outras operações típicas, há uma classe base abstrata conveniente da qual você pode derivar, chamada `BackgroundService` (disponível no .NET Core 2.1).</span><span class="sxs-lookup"><span data-stu-id="99fc6-148">However, since most background tasks will have similar needs in regard to the cancellation tokens management and other typical operations, there is a convenient abstract base class you can derive from, named `BackgroundService` (available since .NET Core 2.1).</span></span>

<span data-ttu-id="99fc6-149">Essa classe fornece o trabalho principal necessário para configurar a tarefa em segundo plano.</span><span class="sxs-lookup"><span data-stu-id="99fc6-149">That class provides the main work needed to set up the background task.</span></span>

<span data-ttu-id="99fc6-150">O próximo código é a classe base abstrata BackgroundService, conforme implementada no .NET Core.</span><span class="sxs-lookup"><span data-stu-id="99fc6-150">The next code is the abstract BackgroundService base class as implemented in .NET Core.</span></span>

```csharp
// Copyright (c) .NET Foundation. Licensed under the Apache License, Version 2.0.
/// <summary>
/// Base class for implementing a long running <see cref="IHostedService"/>.
/// </summary>
public abstract class BackgroundService : IHostedService, IDisposable
{
    private Task _executingTask;
    private readonly CancellationTokenSource _stoppingCts =
                                                   new CancellationTokenSource();

    protected abstract Task ExecuteAsync(CancellationToken stoppingToken);

    public virtual Task StartAsync(CancellationToken cancellationToken)
    {
        // Store the task we're executing
        _executingTask = ExecuteAsync(_stoppingCts.Token);

        // If the task is completed then return it,
        // this will bubble cancellation and failure to the caller
        if (_executingTask.IsCompleted)
        {
            return _executingTask;
        }

        // Otherwise it's running
        return Task.CompletedTask;
    }

    public virtual async Task StopAsync(CancellationToken cancellationToken)
    {
        // Stop called without start
        if (_executingTask == null)
        {
            return;
        }

        try
        {
            // Signal cancellation to the executing method
            _stoppingCts.Cancel();
        }
        finally
        {
            // Wait until the task completes or the stop token triggers
            await Task.WhenAny(_executingTask, Task.Delay(Timeout.Infinite,
                                                          cancellationToken));
        }

    }

    public virtual void Dispose()
    {
        _stoppingCts.Cancel();
    }
}
```

<span data-ttu-id="99fc6-151">Ao derivar da classe base abstrata anterior, graças àquela implementação herdada, você só precisa implementar o método `ExecuteAsync()` em sua própria classe de serviço hospedado personalizada, como no seguinte código simplificado eShopOnContainers que está sondando um banco de dados e publicando eventos de integração no Barramento de Eventos quando necessário.</span><span class="sxs-lookup"><span data-stu-id="99fc6-151">When deriving from the previous abstract base class, thanks to that inherited implementation, you just need to implement the `ExecuteAsync()` method in your own custom hosted service class, as in the following simplified code from eShopOnContainers which is polling a database and publishing integration events into the Event Bus when needed.</span></span>

```csharp
public class GracePeriodManagerService : BackgroundService
{
    private readonly ILogger<GracePeriodManagerService> _logger;
    private readonly OrderingBackgroundSettings _settings;

    private readonly IEventBus _eventBus;

    public GracePeriodManagerService(IOptions<OrderingBackgroundSettings> settings,
                                     IEventBus eventBus,
                                     ILogger<GracePeriodManagerService> logger)
    {
        // Constructor's parameters validations...
    }

    protected override async Task ExecuteAsync(CancellationToken stoppingToken)
    {
        _logger.LogDebug($"GracePeriodManagerService is starting.");

        stoppingToken.Register(() =>
            _logger.LogDebug($" GracePeriod background task is stopping."));

        while (!stoppingToken.IsCancellationRequested)
        {
            _logger.LogDebug($"GracePeriod task doing background work.");

            // This eShopOnContainers method is querying a database table
            // and publishing events into the Event Bus (RabbitMQ / ServiceBus)
            CheckConfirmedGracePeriodOrders();

            await Task.Delay(_settings.CheckUpdateTime, stoppingToken);
        }

        _logger.LogDebug($"GracePeriod background task is stopping.");
    }

    .../...
}
```

<span data-ttu-id="99fc6-152">Neste caso específico para eShopOnContainers, que está executando um método de aplicativo que está consultando uma tabela de banco de dados procurando pedidos com um estado específico e ao aplicar as alterações, ele está publicando eventos de integração por meio de um barramento de evento (sob ele, pode estar usando RabbitMQ ou Barramento de Serviço do Azure).</span><span class="sxs-lookup"><span data-stu-id="99fc6-152">In this specific case for eShopOnContainers, it's executing an application method that's querying a database table looking for orders with a specific state and when applying changes, it is publishing integration events through the event bus (underneath it can be using RabbitMQ or Azure Service Bus).</span></span>

<span data-ttu-id="99fc6-153">Obviamente, você pode executar qualquer outra tarefa em segundo plano de negócios em vez disso.</span><span class="sxs-lookup"><span data-stu-id="99fc6-153">Of course, you could run any other business background task, instead.</span></span>

<span data-ttu-id="99fc6-154">Por padrão, o token de cancelamento é definido com um tempo limite de 5 segundos, embora você possa alterar esse valor ao compilar o `WebHost` usando a `UseShutdownTimeout` extensão do `IWebHostBuilder` .</span><span class="sxs-lookup"><span data-stu-id="99fc6-154">By default, the cancellation token is set with a 5 seconds timeout, although you can change that value when building your `WebHost` using the `UseShutdownTimeout` extension of the `IWebHostBuilder`.</span></span> <span data-ttu-id="99fc6-155">Isso significa que o nosso serviço deve cancelar dentro de 5 segundos, caso contrário, ele será encerrado mais abruptamente.</span><span class="sxs-lookup"><span data-stu-id="99fc6-155">This means that our service is expected to cancel within 5 seconds otherwise it will be more abruptly killed.</span></span>

<span data-ttu-id="99fc6-156">O código a seguir alteraria esse tempo para 10 segundos.</span><span class="sxs-lookup"><span data-stu-id="99fc6-156">The following code would be changing that time to 10 seconds.</span></span>

```csharp
WebHost.CreateDefaultBuilder(args)
    .UseShutdownTimeout(TimeSpan.FromSeconds(10))
    ...
```

### <a name="summary-class-diagram"></a><span data-ttu-id="99fc6-157">Diagrama de classe de resumo</span><span class="sxs-lookup"><span data-stu-id="99fc6-157">Summary class diagram</span></span>

<span data-ttu-id="99fc6-158">A imagem a seguir mostra um resumo visual das classes e interfaces envolvidas ao implementar IHostedServices.</span><span class="sxs-lookup"><span data-stu-id="99fc6-158">The following image shows a visual summary of the classes and interfaces involved when implementing IHostedServices.</span></span>

![Diagrama mostrando que IWebHost e IHost podem hospedar muitos serviços.](./media/background-tasks-with-ihostedservice/class-diagram-custom-ihostedservice.png)

<span data-ttu-id="99fc6-160">**Figura 6-27**.</span><span class="sxs-lookup"><span data-stu-id="99fc6-160">**Figure 6-27**.</span></span> <span data-ttu-id="99fc6-161">Diagrama de classe mostrando as várias classes e interfaces relacionadas ao IHostedService</span><span class="sxs-lookup"><span data-stu-id="99fc6-161">Class diagram showing the multiple classes and interfaces related to IHostedService</span></span>

<span data-ttu-id="99fc6-162">Diagrama de classe: o IWebHost e o IHost podem hospedar muitos serviços, herdados de BackgroundService, que implementa o IHostedService.</span><span class="sxs-lookup"><span data-stu-id="99fc6-162">Class diagram: IWebHost and IHost can host many services, which inherit from BackgroundService, which implements IHostedService.</span></span>

### <a name="deployment-considerations-and-takeaways"></a><span data-ttu-id="99fc6-163">Pontos importantes e considerações sobre implantação</span><span class="sxs-lookup"><span data-stu-id="99fc6-163">Deployment considerations and takeaways</span></span>

<span data-ttu-id="99fc6-164">É importante observar que a maneira como você implanta o ASP.NET Core `WebHost` ou .NET Core `Host` pode afetar a solução final.</span><span class="sxs-lookup"><span data-stu-id="99fc6-164">It is important to note that the way you deploy your ASP.NET Core `WebHost` or .NET Core `Host` might impact the final solution.</span></span> <span data-ttu-id="99fc6-165">Por exemplo, se você implantar o `WebHost` no IIS ou em um Serviço de Aplicativo do Azure normal, o host poderá desligar devido a reciclagens do pool de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="99fc6-165">For instance, if you deploy your `WebHost` on IIS or a regular Azure App Service, your host can be shut down because of app pool recycles.</span></span> <span data-ttu-id="99fc6-166">Mas se você estiver implantando o host como um contêiner em um orquestrador como kubernetes, poderá controlar o número garantido de instâncias ao vivo do seu host.</span><span class="sxs-lookup"><span data-stu-id="99fc6-166">But if you are deploying your host as a container into an orchestrator like Kubernetes, you can control the assured number of live instances of your host.</span></span> <span data-ttu-id="99fc6-167">Além disso, poderá considerar outras abordagens na nuvem feitas especialmente para esses cenários, como Azure Functions.</span><span class="sxs-lookup"><span data-stu-id="99fc6-167">In addition, you could consider other approaches in the cloud especially made for these scenarios, like Azure Functions.</span></span> <span data-ttu-id="99fc6-168">Por fim, se você precisar que o serviço esteja em execução o tempo todo e estiver implantando em um Windows Server, você poderá usar um Serviço Windows.</span><span class="sxs-lookup"><span data-stu-id="99fc6-168">Finally, if you need the service to be running all the time and are deploying on a Windows Server you could use a Windows Service.</span></span>

<span data-ttu-id="99fc6-169">Mas mesmo para uma `WebHost` implantação em um pool de aplicativos, há cenários como repopular ou liberar o cache na memória do aplicativo que ainda seria aplicável.</span><span class="sxs-lookup"><span data-stu-id="99fc6-169">But even for a `WebHost` deployed into an app pool, there are scenarios like repopulating or flushing application's in-memory cache that would be still applicable.</span></span>

<span data-ttu-id="99fc6-170">A `IHostedService` interface fornece uma maneira conveniente de iniciar tarefas em segundo plano em um aplicativo web ASP.NET Core (no .net core 2,0 e em versões posteriores) ou em qualquer processo/host (a partir do .net core 2,1 com `IHost` ).</span><span class="sxs-lookup"><span data-stu-id="99fc6-170">The `IHostedService` interface provides a convenient way to start background tasks in an ASP.NET Core web application (in .NET Core 2.0 and later versions) or in any process/host (starting in .NET Core 2.1 with `IHost`).</span></span> <span data-ttu-id="99fc6-171">Seu principal benefício é a oportunidade que você obtém com o cancelamento normal para limpar o código das tarefas em segundo plano quando o próprio host está sendo desligado.</span><span class="sxs-lookup"><span data-stu-id="99fc6-171">Its main benefit is the opportunity you get with the graceful cancellation to clean-up the code of your background tasks when the host itself is shutting down.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="99fc6-172">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="99fc6-172">Additional resources</span></span>

- <span data-ttu-id="99fc6-173">**Criando uma tarefa agendada no ASP.NET Core/Standard 2,0** </span><span class="sxs-lookup"><span data-stu-id="99fc6-173">**Building a scheduled task in ASP.NET Core/Standard 2.0** </span></span>\
  <https://blog.maartenballiauw.be/post/2017/08/01/building-a-scheduled-cache-updater-in-aspnet-core-2.html>

- <span data-ttu-id="99fc6-174">**Implementando IHostedService no ASP.NET Core 2,0** </span><span class="sxs-lookup"><span data-stu-id="99fc6-174">**Implementing IHostedService in ASP.NET Core 2.0** </span></span>\
  <https://www.stevejgordon.co.uk/asp-net-core-2-ihostedservice>

- <span data-ttu-id="99fc6-175">**Exemplo de GenericHost usando o ASP.NET Core 2,1** </span><span class="sxs-lookup"><span data-stu-id="99fc6-175">**GenericHost Sample using ASP.NET Core 2.1** </span></span>\
  <https://github.com/aspnet/Hosting/tree/release/2.1/samples/GenericHostSample>

> [!div class="step-by-step"]
> <span data-ttu-id="99fc6-176">[Anterior](test-aspnet-core-services-web-apps.md) 
>  [Avançar](implement-api-gateways-with-ocelot.md)</span><span class="sxs-lookup"><span data-stu-id="99fc6-176">[Previous](test-aspnet-core-services-web-apps.md)
[Next](implement-api-gateways-with-ocelot.md)</span></span>
