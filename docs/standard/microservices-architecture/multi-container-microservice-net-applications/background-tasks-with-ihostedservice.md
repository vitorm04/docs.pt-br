---
title: "Implementar tarefas em segundo plano em microsserviços com IHostedService e a classe BackgroundService"
description: "Arquitetura de microsserviços .NET para aplicativos .NET em contêineres | Implementar tarefas em segundo plano em microsserviços com IHostedService e a classe BackgroundService"
keywords: "Docker, Microsserviços, ASP.NET, Contêiner"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/11/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: d60a4590682b79a9f8ac57afee09884b7edd1f98
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="implement-background-tasks-in-microservices-with-ihostedservice-and-the-backgroundservice-class"></a><span data-ttu-id="466d8-104">Implementar tarefas em segundo plano em microsserviços com IHostedService e a classe BackgroundService</span><span class="sxs-lookup"><span data-stu-id="466d8-104">Implement background tasks in microservices with IHostedService and the BackgroundService class</span></span>

<span data-ttu-id="466d8-105">Tarefas em segundo plano e trabalhos agendados são algo que talvez você precise implementar, eventualmente, em um aplicativo baseado em microsserviço em ou em qualquer tipo de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="466d8-105">Background tasks and scheduled jobs are something you might need to implement, eventually, in a microservice based application or in any kind of application.</span></span> <span data-ttu-id="466d8-106">A diferença ao usar uma arquitetura de microsserviços é que você pode implementar um único processo/contêiner de microsserviço para hospedar essas tarefas em segundo plano para que você possa expandir/reduzir conforme necessário ou até mesmo garantir que sejam executadas como uma única instância daquele processo de microsserviço/contêiner.</span><span class="sxs-lookup"><span data-stu-id="466d8-106">The difference when using a microservices architecture is that you can implement a single microservice process/container for hosting these background tasks so you can scale it down/up as you need or you can even make sure that it runs a single instance of that microservice process/container.</span></span>

<span data-ttu-id="466d8-107">De um ponto de vista genérico, no .NET Core, chamamos esses tipos de tarefas de Serviços Hospedados, porque são serviços/lógica que você hospeda em seu host/aplicativo/microsserviço.</span><span class="sxs-lookup"><span data-stu-id="466d8-107">From a generic point of view, in .NET Core we called these type of tasks Hosted Services, because they are services/logic that you host within your host/application/microservice.</span></span> <span data-ttu-id="466d8-108">Observe que, neste caso, o serviço hospedado simplesmente significa uma classe com a lógica de tarefa em segundo plano.</span><span class="sxs-lookup"><span data-stu-id="466d8-108">Note that in this case, the hosted service simply means a class with the background task logic.</span></span>

<span data-ttu-id="466d8-109">Desde o .NET Core 2.0, a estrutura fornece uma nova interface chamada <xref:Microsoft.Extensions.Hosting.IHostedService>, ajudando você a implementar serviços hospedados facilmente.</span><span class="sxs-lookup"><span data-stu-id="466d8-109">Since .NET Core 2.0, the framework provides a new interface named <xref:Microsoft.Extensions.Hosting.IHostedService> helping you to easily implement hosted services.</span></span> <span data-ttu-id="466d8-110">A ideia básica é que você pode registrar várias tarefas de segundo plano (serviços hospedados), que são executadas em segundo plano enquanto o host da Web ou o host está em execução, conforme mostra a imagem abaixo.</span><span class="sxs-lookup"><span data-stu-id="466d8-110">The basic idea is that you can register multiple background tasks (hosted services), that run in the background while your web host or host is running, as shown in the image below.</span></span>

![](./media/image26.png)

<span data-ttu-id="466d8-111">**Figura 8-25.**</span><span class="sxs-lookup"><span data-stu-id="466d8-111">**Figure 8-25.**</span></span> <span data-ttu-id="466d8-112">Usando IHostedService em WebHost versus um Host</span><span class="sxs-lookup"><span data-stu-id="466d8-112">Using IHostedService in a WebHost vs. a Host</span></span>

<span data-ttu-id="466d8-113">Observe a diferença entre `WebHost` e `Host`.</span><span class="sxs-lookup"><span data-stu-id="466d8-113">Note the difference made between `WebHost` and `Host`.</span></span> <span data-ttu-id="466d8-114">Um `WebHost` (classe base implementando `IWebHost`) no ASP.NET Core 2.0 é o artefato de infraestrutura que você usa para fornecer recursos de servidor HTTP ao seu processo, como se você estivesse implementando um aplicativo Web MVC ou um serviço de API da Web.</span><span class="sxs-lookup"><span data-stu-id="466d8-114">A `WebHost` (base class implementing `IWebHost`) in ASP.NET Core 2.0 is the infrastructure artifact you use to provide HTTP server features to your process, such as if you are implementing an MVC web app or Web API service.</span></span> <span data-ttu-id="466d8-115">Ele fornece todos os benefícios da nova infraestrutura no ASP.NET Core, permitindo que você use a injeção de dependência, insira middleware no pipeline HTTP etc. e use com precisão esses `IHostedServices` para tarefas em segundo plano.</span><span class="sxs-lookup"><span data-stu-id="466d8-115">It provides all the new infrastructure goodness in ASP.NET Core, enabling you to use dependency injection, insert middlewares in the HTTP pipeline, etc. and precisely use these `IHostedServices` for background tasks.</span></span>

<span data-ttu-id="466d8-116">Um `Host` (classe base implementando `IHost`), no entanto, é algo novo no .NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="466d8-116">A `Host` (base class implementing `IHost`), however, is something new in .NET Core 2.1.</span></span> <span data-ttu-id="466d8-117">Basicamente, um `Host` permite que você tenha uma infraestrutura semelhante àquela que você tem com `WebHost` (injeção de dependência, serviços hospedados etc.), mas, nesse caso, você quer apenas ter um processo simples e mais leve como o host, sem nada relacionado ao MVC, à API da Web ou aos recursos de servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="466d8-117">Basically, a `Host` allows you to have a similar infrastructure than what you have with `WebHost` (dependency injection, hosted services, etc.), but in this case, you just want to have a simple and lighter process as the host, with nothing related to MVC, Web API or HTTP server features.</span></span>

<span data-ttu-id="466d8-118">Portanto, você pode escolher e criar um processo de host especializado com IHost para lidar com os serviços hospedados e nada mais, como um microsserviço feito apenas para hospedar o `IHostedServices` ou você pode, como alternativa, estender um ASP.NET Core `WebHost` existente, como um aplicativo MVC ou API da Web do ASP.NET Core existente.</span><span class="sxs-lookup"><span data-stu-id="466d8-118">Therefore, you can choose and either create a specialized host-process with IHost to handle the hosted services and nothing else, such a microservice made just for hosting the `IHostedServices`, or you can alternatevely extend an existing ASP.NET Core `WebHost`, such as an existing ASP.NET Core Web API or MVC app.</span></span> 

<span data-ttu-id="466d8-119">Cada abordagem tem vantagens e desvantagens, dependendo de suas necessidades de negócios e escalabilidade.</span><span class="sxs-lookup"><span data-stu-id="466d8-119">Each approach has pros and cons depending on your business and scalability needs.</span></span> <span data-ttu-id="466d8-120">O resultado é basicamente que se as suas tarefas em segundo plano não tiverem nenhuma relação com HTTP (IWebHost), você deverá usar um IHost, quando disponível no .NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="466d8-120">The bottom line is basically that if your background tasks have nothing to do with HTTP (IWebHost) you should use and IHost, when available in .NET Core 2.1.</span></span>

## <a name="registering-hosted-services-in-your-webhost-or-host"></a><span data-ttu-id="466d8-121">Registro de serviços hospedados em seu WebHost ou Host</span><span class="sxs-lookup"><span data-stu-id="466d8-121">Registering hosted services in your WebHost or Host</span></span>

<span data-ttu-id="466d8-122">Vamos analisar detalhadamente a interface `IHostedService`, já que seu uso é muito semelhante em um `WebHost` ou em um `Host`.</span><span class="sxs-lookup"><span data-stu-id="466d8-122">Let’s drill down further on the `IHostedService` interface since its usage is pretty similar in a `WebHost` or in a `Host`.</span></span> 

<span data-ttu-id="466d8-123">SignalR é um exemplo de um artefato usando serviços hospedados, mas você também pode usá-lo para itens muito mais simples, como:</span><span class="sxs-lookup"><span data-stu-id="466d8-123">SignalR is one example of an artifact using hosted services, but you can also use it for much simpler things like:</span></span>

-   <span data-ttu-id="466d8-124">Uma tarefa em segundo plano sondando um banco de dados em busca de alterações.</span><span class="sxs-lookup"><span data-stu-id="466d8-124">A background task polling a database looking for changes.</span></span>
-   <span data-ttu-id="466d8-125">Uma tarefa agendada atualizando algum cache periodicamente.</span><span class="sxs-lookup"><span data-stu-id="466d8-125">A scheduled task updating some cache periodically.</span></span>
-   <span data-ttu-id="466d8-126">Uma implementação de QueueBackgroundWorkItem que permite que uma tarefa seja executada em um thread em segundo plano.</span><span class="sxs-lookup"><span data-stu-id="466d8-126">An implementation of QueueBackgroundWorkItem that allows a task to be executed on a background thread.</span></span>
-   <span data-ttu-id="466d8-127">Processamento de mensagens de uma fila de mensagens em segundo plano de um aplicativo Web enquanto se compartilham serviços comuns como `ILogger`.</span><span class="sxs-lookup"><span data-stu-id="466d8-127">Processing messages from a message queue in the background of a web app while sharing common services such as `ILogger`.</span></span>
-   <span data-ttu-id="466d8-128">Uma tarefa em segundo plano iniciada com `Task.Run()`.</span><span class="sxs-lookup"><span data-stu-id="466d8-128">A background task started with `Task.Run()`.</span></span>

<span data-ttu-id="466d8-129">Você pode basicamente descarregar qualquer uma dessas ações para uma tarefa em segundo plano com base em IHostedService.</span><span class="sxs-lookup"><span data-stu-id="466d8-129">You can basically offload any of those actions to a background task based on IHostedService.</span></span>

<span data-ttu-id="466d8-130">A maneira como você adiciona um ou vários `IHostedServices` em seu `WebHost` ou `Host` é registrando-os por meio de DI (injeção de dependência) padrão em um ASP.NET Core `WebHost` (ou em um `Host` no .NET Core 2.1).</span><span class="sxs-lookup"><span data-stu-id="466d8-130">The way you add one or multiple `IHostedServices` into your `WebHost` or `Host` is by registering them up through the standard DI (dependency injection) in an ASP.NET Core `WebHost` (or in a `Host` in .NET Core 2.1).</span></span> <span data-ttu-id="466d8-131">Basicamente, você deve registrar os serviços hospedados no método `ConfigureServices()` familiar da classe `Startup`, como no código a seguir de um WebHost ASP.NET típico.</span><span class="sxs-lookup"><span data-stu-id="466d8-131">Basically, you have to register the hosted services within the familiar `ConfigureServices()` method of the `Startup` class, as in the following code from a typical ASP.NET WebHost.</span></span> 

```csharp
public IServiceProvider ConfigureServices(IServiceCollection services)
{            
    //Other DI registrations;

    // Register Hosted Services
    services.AddSingleton<IHostedService, GracePeriodManagerService>();
    services.AddSingleton<IHostedService, MyHostedServiceB>();
    services.AddSingleton<IHostedService, MyHostedServiceC>();
    //...
}
```

<span data-ttu-id="466d8-132">Nesse código, o serviço hospedado `GracePeriodManagerService` é o código real do microsserviço de negócios de Ordenação em eShopOnContainers, enquanto os outros dois são apenas dois exemplos adicionais.</span><span class="sxs-lookup"><span data-stu-id="466d8-132">In that code, the `GracePeriodManagerService` hosted service is real code from the Ordering business microservice in eShopOnContainers, while the other two are just two additional samples.</span></span>

<span data-ttu-id="466d8-133">A execução da tarefa em segundo plano `IHostedService` é coordenada com o tempo de vida do aplicativo (ou seja, host ou microsserviço).</span><span class="sxs-lookup"><span data-stu-id="466d8-133">The `IHostedService` background task execution is coordinated with the lifetime of the application (host or microservice, for that matter).</span></span> <span data-ttu-id="466d8-134">Você registra tarefas quando o aplicativo é iniciado e você tem a oportunidade de fazer alguma ação normal ou limpeza quando o aplicativo está sendo desligado.</span><span class="sxs-lookup"><span data-stu-id="466d8-134">You register tasks when the application starts and you have the opportunity to do some graceful action or clean-up when the application is shutting down.</span></span>

<span data-ttu-id="466d8-135">Sem usar `IHostedService`, você sempre pode iniciar um thread em segundo plano para executar qualquer tarefa.</span><span class="sxs-lookup"><span data-stu-id="466d8-135">Without using `IHostedService`, you could always start a background thread to run any task.</span></span> <span data-ttu-id="466d8-136">A diferença está precisamente no tempo de desligamento do aplicativo quando esse thread seria simplesmente seria interrompido sem a oportunidade de executar as ações de limpeza normais.</span><span class="sxs-lookup"><span data-stu-id="466d8-136">The difference is precisely at the app’s shutdown time when that thread would simply be killed without having the opportunity to run graceful clean-up actions.</span></span>


## <a name="the-ihostedservice-interface"></a><span data-ttu-id="466d8-137">A interface IHostedService</span><span class="sxs-lookup"><span data-stu-id="466d8-137">The IHostedService interface</span></span>

<span data-ttu-id="466d8-138">Quando você registra um `IHostedService`, o .NET Core chamará os métodos `StartAsync()` e `StopAsync()` de seu tipo `IHostedService` durante o início e a parada do aplicativo, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="466d8-138">When you register an `IHostedService`, .NET Core will call the `StartAsync()` and `StopAsync()` methods of your `IHostedService` type during application start and stop respectively.</span></span> <span data-ttu-id="466d8-139">Especificamente, o início é chamado depois que o servidor foi iniciado e `IApplicationLifetime.ApplicationStarted` foi disparado.</span><span class="sxs-lookup"><span data-stu-id="466d8-139">Specifically, start is called after the server has started and `IApplicationLifetime.ApplicationStarted` is triggered.</span></span>

<span data-ttu-id="466d8-140">O `IHostedService`, conforme definido no .NET Core, tem a seguinte aparência.</span><span class="sxs-lookup"><span data-stu-id="466d8-140">The `IHostedService` as defined in .NET Core, looks like the following.</span></span>

```csharp
namespace Microsoft.Extensions.Hosting
{
    //
    // Summary:
    //     Defines methods for objects that are managed by the host.
    public interface IHostedService
    {
        //
        // Summary:
        // Triggered when the application host is ready to start the service.
        Task StartAsync(CancellationToken cancellationToken);
        //
        // Summary:
        // Triggered when the application host is performing a graceful shutdown.
        Task StopAsync(CancellationToken cancellationToken);
    }
}
```
<span data-ttu-id="466d8-141">Como você pode imaginar, é possível criar várias implementações de IHostedService e registrá-las no método `ConfigureService()` no contêiner de ID, como mostrado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="466d8-141">As you can imagine, you can create multiple implementations of IHostedService and register them at the `ConfigureService()` method into the DI container, as shown previously.</span></span> <span data-ttu-id="466d8-142">Todos esses serviços hospedados serão iniciados e interrompidos junto com o aplicativo/microsserviço.</span><span class="sxs-lookup"><span data-stu-id="466d8-142">All those hosted services will be started and stopped along with the application/microservice.</span></span>

<span data-ttu-id="466d8-143">Como desenvolvedor, você é responsável por lidar com a ação de parada ou seus serviços quando o método `StopAsync()` é disparado pelo host.</span><span class="sxs-lookup"><span data-stu-id="466d8-143">As a developer, you are responsible for handling the stopping action or your services when `StopAsync()` method is triggered by the host.</span></span>

## <a name="implementing-ihostedservice-with-a-custom-hosted-service-class-deriving-from-the-backgroundservice-base-class"></a><span data-ttu-id="466d8-144">Implementando IHostedService com uma classe de serviço hospedado personalizado derivado da classe base BackgroundService</span><span class="sxs-lookup"><span data-stu-id="466d8-144">Implementing IHostedService with a custom hosted service class deriving from the BackgroundService base class</span></span>

<span data-ttu-id="466d8-145">Vá em frente e crie sua classe de serviço hospedado personalizada do zero e implemente o `IHostedService`, como você precisa fazer ao usar o .NET Core 2.0.</span><span class="sxs-lookup"><span data-stu-id="466d8-145">You could go ahead and create you custom hosted service class from scratch and implement the `IHostedService`, as you need to do when using .NET Core 2.0.</span></span> 

<span data-ttu-id="466d8-146">No entanto, já que a maioria das tarefas em segundo plano terá necessidades semelhantes sobre o gerenciamento de tokens de cancelamento e outras operações típicas, o .NET Core 2.1 fornecerá uma classe base abstrata muito conveniente da qual você pode derivar, chamada BackgroundService.</span><span class="sxs-lookup"><span data-stu-id="466d8-146">However, since most background tasks will have similar needs in regard to the cancellation tokens management and other tipical operations, .NET Core 2.1 will be providing a very convenient abstract base class you can derive from, named BackgroundService.</span></span>

<span data-ttu-id="466d8-147">Essa classe fornece o trabalho principal necessário para configurar a tarefa em segundo plano.</span><span class="sxs-lookup"><span data-stu-id="466d8-147">That class provides the main work needed to set up the background task.</span></span> <span data-ttu-id="466d8-148">Observe que essa classe virá na biblioteca do .NET Core 2.1 para que não seja necessário gravá-la.</span><span class="sxs-lookup"><span data-stu-id="466d8-148">Note that this class will come in the .NET Core 2.1 library so you don’t need to write it.</span></span>

<span data-ttu-id="466d8-149">No entanto, do momento da redação deste artigo, o .NET Core 2.1 não havia sido liberado.</span><span class="sxs-lookup"><span data-stu-id="466d8-149">However, as of the time of this writing, .NET Core 2.1 has not been released.</span></span> <span data-ttu-id="466d8-150">Portanto, no eShopOnContainers que está usando atualmente o .NET Core 2.0, estamos apenas temporariamente incorporando aquela classe do repositório de software livre do .NET Core 2.1 (sem necessidade de qualquer licença do proprietária que não seja a licença de software livre) porque ele é compatível com a interface IHostedService atual no .NET Core 2.0.</span><span class="sxs-lookup"><span data-stu-id="466d8-150">Therefore, in eShopOnContainers which is currently using .NET Core 2.0, we are just temporally incorporating that class from the .NET Core 2.1 open-source repo (no need of any proprietary license other than the open-source license) because it is compatible with the current IHostedService interface in .NET Core 2.0.</span></span> <span data-ttu-id="466d8-151">Quando .NET Core 2.1 for liberado, você precisará apenas apontar para o pacote do NuGet correto.</span><span class="sxs-lookup"><span data-stu-id="466d8-151">When .NET Core 2.1 is released, you’ll just need to point to the right NuGet package.</span></span>

<span data-ttu-id="466d8-152">O próximo código de erro é a classe base abstrata BackgroundService conforme implementada no .NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="466d8-152">The next code is the abstract BackgroundService base class as implemented in .NET Core 2.1.</span></span>

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

<span data-ttu-id="466d8-153">Ao derivar da classe base abstrata anterior, graças àquela implementação herdada, você só precisa implementar o método `ExecuteAsync()` em sua própria classe de serviço hospedado personalizada, como no seguinte código simplificado eShopOnContainers que está sondando um banco de dados e publicando eventos de integração no Barramento de Eventos quando necessário.</span><span class="sxs-lookup"><span data-stu-id="466d8-153">When deriving from the previous abstract base class, thanks to that inherited implementation, you just need to implement the `ExecuteAsync()` method in your own custom hosted service class, as in the following simplified code from eShopOnContainers which is polling a database and publishing integration events into the Event Bus when needed.</span></span>

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
            //Constructor’s parameters validations...       
        }

        protected override async Task ExecuteAsync(CancellationToken stoppingToken)
        {
            _logger.LogDebug($"GracePeriodManagerService is starting.");

            stoppingToken.Register(() => 
                    _logger.LogDebug($" GracePeriod background task is stopping."));

            while (!stoppingToken.IsCancellationRequested)
            {
                _logger.LogDebug($"GracePeriod task doing background work.");

                // This eShopOnContainers method is quering a database table 
                // and publishing events into the Event Bus (RabbitMS / ServiceBus)
                CheckConfirmedGracePeriodOrders();

                await Task.Delay(_settings.CheckUpdateTime, stoppingToken);
            }
            
            _logger.LogDebug($"GracePeriod background task is stopping.");

        }

        protected override async Task StopAsync (CancellationToken stoppingToken)
        {
               // Run your graceful clean-up actions
        }
}
```

<span data-ttu-id="466d8-154">Neste caso específico para eShopOnContainers, que está executando um método de aplicativo que está consultando uma tabela de banco de dados procurando pedidos com um estado específico e ao aplicar as alterações, ele está publicando eventos de integração por meio de um barramento de evento (sob ele, pode estar usando RabbitMQ ou Barramento de Serviço do Azure).</span><span class="sxs-lookup"><span data-stu-id="466d8-154">In this specific case for eShopOnContainers, it is executing an application method which is quering a database table looking for orders with a specific state and when applying changes, it is publishing integration events through the event bus (underneath it can be using RabbitMQ or Azure Service Bus).</span></span> 

<span data-ttu-id="466d8-155">Obviamente, você pode executar qualquer outra tarefa em segundo plano de negócios em vez disso.</span><span class="sxs-lookup"><span data-stu-id="466d8-155">Of course, you could run any other business background task, instead.</span></span>

<span data-ttu-id="466d8-156">Por padrão, o token de cancelamento é definido com um tempo limite de 5 segundos, embora você possa alterar esse valor ao criar seu `WebHost` usando a extensão `UseShutdownTimeout` do `IWebHostBuilder`.</span><span class="sxs-lookup"><span data-stu-id="466d8-156">By default, the cancellation token is set with a 5 second timeout, although you can change that value when building your `WebHost` using the `UseShutdownTimeout` extension of the `IWebHostBuilder`.</span></span> <span data-ttu-id="466d8-157">Isso significa que o nosso serviço deve cancelar dentro de 5 segundos, caso contrário, ele será encerrado mais abruptamente.</span><span class="sxs-lookup"><span data-stu-id="466d8-157">This means that our service is expected to cancel within 5 seconds otherwise it will be more abruptly killed.</span></span>

<span data-ttu-id="466d8-158">O código a seguir alteraria esse tempo para 10 segundos.</span><span class="sxs-lookup"><span data-stu-id="466d8-158">The following code would be changing that time to 10 seconds.</span></span>

```csharp
WebHost.CreateDefaultBuilder(args)
    .UseShutdownTimeout(TimeSpan.FromSeconds(10))
    ...
```

### <a name="summary-class-diagram"></a><span data-ttu-id="466d8-159">Diagrama de classe de resumo</span><span class="sxs-lookup"><span data-stu-id="466d8-159">Summary class diagram</span></span>

<span data-ttu-id="466d8-160">A imagem a seguir 8-26 mostra um resumo visual das classes e interfaces envolvidas na implementação do IHostedServices.</span><span class="sxs-lookup"><span data-stu-id="466d8-160">The following image 8-26 shows a visual summary of the classes and interfaced involved when implementing IHostedServices.</span></span>
 
![](./media/image27.png)

<span data-ttu-id="466d8-161">**Figura 8-26.**</span><span class="sxs-lookup"><span data-stu-id="466d8-161">**Figure 8-26.**</span></span> <span data-ttu-id="466d8-162">Diagrama de classe mostrando as várias classes e interfaces relacionadas ao IHostedService</span><span class="sxs-lookup"><span data-stu-id="466d8-162">Class diagram showing the multiple classes and interfaces related to IHostedService</span></span>

### <a name="deployment-considerations-and-takeaways"></a><span data-ttu-id="466d8-163">Pontos importantes e considerações sobre implantação</span><span class="sxs-lookup"><span data-stu-id="466d8-163">Deployment considerations and takeaways</span></span>

<span data-ttu-id="466d8-164">É importante observar que a maneira como você implanta o ASP.NET Core `WebHost` ou .NET Core `Host` pode afetar a solução final.</span><span class="sxs-lookup"><span data-stu-id="466d8-164">It is important to note that the way you deploy your ASP.NET Core `WebHost` or .NET Core `Host` might impact the final solution.</span></span> <span data-ttu-id="466d8-165">Por exemplo, se você implantar o `WebHost` no IIS ou em um Serviço de Aplicativo do Azure normal, o host poderá desligar devido a reciclagens do pool de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="466d8-165">For instance, if you deploy your `WebHost` on IIS or a regular Azure App Service, your host can be shut down because of app pool recycles.</span></span> <span data-ttu-id="466d8-166">Porém, se você estiver implantando eu host como um contêiner em um orquestrador como Kubernetes ou Service Fabric, poderá controlar o número garantido de instâncias ativas do seu host.</span><span class="sxs-lookup"><span data-stu-id="466d8-166">But if you are deploying your host as a container into an orchestrator like Kubernetes or Service Fabric, you can control the assured number of live instances of your host.</span></span> <span data-ttu-id="466d8-167">Além disso, poderá considerar outras abordagens na nuvem feitas especialmente para esses cenários, como Azure Functions.</span><span class="sxs-lookup"><span data-stu-id="466d8-167">In addition, you could consider other approaches in the cloud especially made for these scenarios, like Azure Functions.</span></span> 

<span data-ttu-id="466d8-168">Porém, mesmo para um `WebHost` implantado em um pool de aplicativos, há cenários como repopulação ou liberação do cache em memória do aplicativo em que isso ainda seria aplicável.</span><span class="sxs-lookup"><span data-stu-id="466d8-168">But even for a `WebHost` deployed into an app pool, there are scenarios like repopulating or flushing application’s in-memory cache, that would be still applicable.</span></span>

<span data-ttu-id="466d8-169">A interface `IHostedService` fornece uma maneira conveniente de iniciar tarefas em segundo plano em um aplicativo Web ASP.NET Core (no .NET Core 2.0) ou em qualquer processo/host (começando com o .NET Core 2.1 com `IHost`).</span><span class="sxs-lookup"><span data-stu-id="466d8-169">The `IHostedService` interface provides a convenient way to start background tasks in an ASP.NET Core web application (in .NET Core 2.0) or in any process/host (starting in .NET Core 2.1 with `IHost`).</span></span> <span data-ttu-id="466d8-170">O principal benefício é a oportunidade que você obtém com o cancelamento normal para o código de limpeza de suas tarefas em segundo plano quando o host em si está sendo desligado.</span><span class="sxs-lookup"><span data-stu-id="466d8-170">Its main benefit is the opportunity you get with the graceful cancellation to clean-up code of your background tasks when the host itself is shutting down.</span></span>


#### <a name="additional-resources"></a><span data-ttu-id="466d8-171">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="466d8-171">Additional resources</span></span>

-   <span data-ttu-id="466d8-172">**Criar uma tarefa agendada no ASP.NET Core/Standard 2.0**</span><span class="sxs-lookup"><span data-stu-id="466d8-172">**Building a scheduled task in ASP.NET Core/Standard 2.0**</span></span> 

    [<span data-ttu-id="466d8-173">*https://blog.maartenballiauw.be/post/2017/08/01/building-a-scheduled-cache-updater-in-aspnet-core-2.html*</span><span class="sxs-lookup"><span data-stu-id="466d8-173">*https://blog.maartenballiauw.be/post/2017/08/01/building-a-scheduled-cache-updater-in-aspnet-core-2.html*</span></span>](https://blog.maartenballiauw.be/post/2017/08/01/building-a-scheduled-cache-updater-in-aspnet-core-2.html)

-   <span data-ttu-id="466d8-174">**Implementando IHostedService no ASP.NET Core 2.0**</span><span class="sxs-lookup"><span data-stu-id="466d8-174">**Implementing IHostedService in ASP.NET Core 2.0**</span></span> 

    [<span data-ttu-id="466d8-175">*https://www.stevejgordon.co.uk/asp-net-core-2-ihostedservice*</span><span class="sxs-lookup"><span data-stu-id="466d8-175">*https://www.stevejgordon.co.uk/asp-net-core-2-ihostedservice*</span></span>](https://www.stevejgordon.co.uk/asp-net-core-2-ihostedservice)

-   <span data-ttu-id="466d8-176">**Exemplos de hospedagem do ASP.NET Core 2.1**</span><span class="sxs-lookup"><span data-stu-id="466d8-176">**ASP.NET Core 2.1 Hosting samples**</span></span> 

    [<span data-ttu-id="466d8-177">*https://github.com/aspnet/Hosting/tree/dev/samples/GenericHostSample*</span><span class="sxs-lookup"><span data-stu-id="466d8-177">*https://github.com/aspnet/Hosting/tree/dev/samples/GenericHostSample*</span></span>](https://github.com/aspnet/Hosting/tree/dev/samples/GenericHostSample)



>[!div class="step-by-step"]
<span data-ttu-id="466d8-178">[Anterior] (test-aspnet-core-services-web-apps.md) [Próximo] (../microservice-ddd-cqrs-patterns/index.md)</span><span class="sxs-lookup"><span data-stu-id="466d8-178">[Previous] (test-aspnet-core-services-web-apps.md) [Next] (../microservice-ddd-cqrs-patterns/index.md)</span></span>
