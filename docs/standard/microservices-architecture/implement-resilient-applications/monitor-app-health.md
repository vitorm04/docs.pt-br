---
title: Monitoramento de integridade
description: Explore uma maneira de implementar o monitoramento de integridade.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 01/07/2019
ms.openlocfilehash: 90beb8073cd169b0a68dc0025d8cd815ccb5a308
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/26/2019
ms.locfileid: "58464002"
---
# <a name="health-monitoring"></a><span data-ttu-id="688e7-103">Monitoramento de integridade</span><span class="sxs-lookup"><span data-stu-id="688e7-103">Health monitoring</span></span>

<span data-ttu-id="688e7-104">O monitoramento de integridade pode permitir informações quase em tempo real sobre o estado de seus contêineres e microsserviços.</span><span class="sxs-lookup"><span data-stu-id="688e7-104">Health monitoring can allow near-real-time information about the state of your containers and microservices.</span></span> <span data-ttu-id="688e7-105">O monitoramento de integridade é fundamental para vários aspectos da operação de microsserviços e é especialmente importante quando orquestradores executam upgrades parciais de aplicativo em fases, conforme explicado posteriormente.</span><span class="sxs-lookup"><span data-stu-id="688e7-105">Health monitoring is critical to multiple aspects of operating microservices and is especially important when orchestrators perform partial application upgrades in phases, as explained later.</span></span>

<span data-ttu-id="688e7-106">Aplicativos baseados em microsserviços geralmente usam pulsações ou verificações de integridade para habilitar seus monitores de desempenho, agendadores e orquestradores a controlar a variedade de serviços.</span><span class="sxs-lookup"><span data-stu-id="688e7-106">Microservices-based applications often use heartbeats or health checks to enable their performance monitors, schedulers, and orchestrators to keep track of the multitude of services.</span></span> <span data-ttu-id="688e7-107">Se os serviços não puderem enviar algum tipo de sinal "Estou ativo", seja sob demanda ou conforme um agendamento, seu aplicativo poderá enfrentar riscos quando você implantar atualizações ou poderá simplesmente detectar falhas tarde demais e não conseguir interromper falhas em cascata que possam levar a grandes interrupções.</span><span class="sxs-lookup"><span data-stu-id="688e7-107">If services cannot send some sort of “I’m alive” signal, either on demand or on a schedule, your application might face risks when you deploy updates, or it might just detect failures too late and not be able to stop cascading failures that can end up in major outages.</span></span>

<span data-ttu-id="688e7-108">No modelo comum, serviços enviam relatórios sobre o status, e essas informações são agregadas para fornecer uma exibição geral do estado de integridade do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="688e7-108">In the typical model, services send reports about their status, and that information is aggregated to provide an overall view of the state of health of your application.</span></span> <span data-ttu-id="688e7-109">Se você estiver usando um orquestrador, poderá fornecer informações de integridade para o cluster do orquestrador para que o cluster possa atuar adequadamente.</span><span class="sxs-lookup"><span data-stu-id="688e7-109">If you're using an orchestrator, you can provide health information to your orchestrator’s cluster, so that the cluster can act accordingly.</span></span> <span data-ttu-id="688e7-110">Se você investir em relatórios de integridade de alta qualidade personalizados para seu aplicativo, poderá detectar e corrigir problemas do aplicativo em execução com muito mais facilidade.</span><span class="sxs-lookup"><span data-stu-id="688e7-110">If you invest in high-quality health reporting that's customized for your application, you can detect and fix issues for your running application much more easily.</span></span>

## <a name="implement-health-checks-in-aspnet-core-services"></a><span data-ttu-id="688e7-111">Implementar verificações de integridade nos serviços do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="688e7-111">Implement health checks in ASP.NET Core services</span></span>

<span data-ttu-id="688e7-112">Ao desenvolver um microsserviço ou um aplicativo Web ASP.NET Core, você pode usar a funcionalidade interna de verificações de integridade que foi lançada no ASP.NET Core 2.2.</span><span class="sxs-lookup"><span data-stu-id="688e7-112">When developing an ASP.NET Core microservice or web application, you can use the built-in health checks feature that was released in ASP .NET Core 2.2.</span></span> <span data-ttu-id="688e7-113">Assim como muitas funcionalidades do ASP.NET Core, as verificações de integridade são fornecidas com um conjunto de serviços e um middleware.</span><span class="sxs-lookup"><span data-stu-id="688e7-113">Like many ASP.NET Core features, health checks come with a set of services and a middleware.</span></span>

<span data-ttu-id="688e7-114">O middleware e os serviços de verificação de integridade são fáceis de usar e fornecem funcionalidades que permitem validar se algum recurso externo necessário para seu aplicativo (como um banco de dados do SQL Server ou uma API remota) está funcionando corretamente.</span><span class="sxs-lookup"><span data-stu-id="688e7-114">Health check services and middleware are easy to use and provide capabilities that let you validate if any external resource needed for your application (like a SQL Server database or a remote API) is working properly.</span></span> <span data-ttu-id="688e7-115">Quando você usa essa funcionalidade, também pode decidir o que significa se o recurso está íntegro, como explicaremos mais adiante.</span><span class="sxs-lookup"><span data-stu-id="688e7-115">When you use this feature, you can also decide what it means that the resource is healthy, as we explain later.</span></span>

<span data-ttu-id="688e7-116">Para usar essa funcionalidade com eficiência, você precisará primeiro configurar serviços em seus microsserviços.</span><span class="sxs-lookup"><span data-stu-id="688e7-116">To use this feature effectively, you need to first configure services in your microservices.</span></span> <span data-ttu-id="688e7-117">Em segundo lugar, é necessário um aplicativo de front-end que consulte os relatórios de integridade.</span><span class="sxs-lookup"><span data-stu-id="688e7-117">Second, you need a front-end application that queries for the health reports.</span></span> <span data-ttu-id="688e7-118">O aplicativo de front-end pode ser um aplicativo de relatório personalizado ou um orquestrador em si que pode reagir de acordo com os estados de integridade.</span><span class="sxs-lookup"><span data-stu-id="688e7-118">That front-end application could be a custom reporting application, or it could be an orchestrator itself that can react accordingly to the health states.</span></span>

### <a name="use-the-healthchecks-feature-in-your-back-end-aspnet-microservices"></a><span data-ttu-id="688e7-119">Usar a funcionalidade HealthChecks nos microsserviços de back-end do ASP.NET</span><span class="sxs-lookup"><span data-stu-id="688e7-119">Use the HealthChecks feature in your back-end ASP.NET microservices</span></span>

<span data-ttu-id="688e7-120">Nesta seção, você aprenderá como a funcionalidade HealthChecks é usada em um aplicativo de API Web de exemplo do ASP.NET Core 2.2.</span><span class="sxs-lookup"><span data-stu-id="688e7-120">In this section, you will learn how the HealthChecks feature is used in a sample ASP.NET Core 2.2 Web API application.</span></span> <span data-ttu-id="688e7-121">A implementação dessa funcionalidade em microsserviços de grande escala, como o eShopOnContainers, é explicada na próxima seção.</span><span class="sxs-lookup"><span data-stu-id="688e7-121">Implementation of this feature in a large scale microservices like the eShopOnContainers is explained in the later section.</span></span> <span data-ttu-id="688e7-122">Para começar, você precisa definir o que constitui o status íntegro para cada microsserviço.</span><span class="sxs-lookup"><span data-stu-id="688e7-122">To begin, you need to define what constitutes a healthy status for each microservice.</span></span> <span data-ttu-id="688e7-123">No aplicativo de exemplo, os microsserviços estão íntegros se a API de microsserviços é acessível por meio de HTTP e se o banco de dados do SQL Server relacionado também está disponível.</span><span class="sxs-lookup"><span data-stu-id="688e7-123">In the sample application, the microservices are healthy if the microservice API is accessible via HTTP and its related SQL Server database is also available.</span></span>

<span data-ttu-id="688e7-124">No .NET Core 2.2, com as APIs internas, você pode configurar os serviços, adicionar uma Verificação de Integridade ao microsserviço e ao banco de dados do SQL Server dependente desta forma:</span><span class="sxs-lookup"><span data-stu-id="688e7-124">In .NET Core 2.2, with the built-in APIs, you can configure the services, add a Health Check for the microservice and its dependent SQL Server database in this way:</span></span>

```csharp
// Startup.cs from .NET Core 2.2 Web Api sample
//
public void ConfigureServices(IServiceCollection services)
{
    //...
    // Registers required services for health checks
    services.AddHealthChecks()
    // Add a health check for a SQL database
    .AddCheck("MyDatabase", new SqlConnectionHealthCheck(Configuration["ConnectionStrings:DefaultConnection"]));
}
```

<span data-ttu-id="688e7-125">No código anterior, o método `services.AddHealthChecks()` configura uma verificação básica de HTTP que retorna um código de status **200** com “Íntegro”.</span><span class="sxs-lookup"><span data-stu-id="688e7-125">In the previous code, the `services.AddHealthChecks()` method configures a basic HTTP check that returns a status code **200** with “Healthy”.</span></span>  <span data-ttu-id="688e7-126">Além disso, o método de extensão `AddCheck()` configura uma `SqlConnectionHealthCheck` personalizada que verifica a integridade do Banco de Dados SQL relacionado.</span><span class="sxs-lookup"><span data-stu-id="688e7-126">Further, the `AddCheck()` extension method configures a custom `SqlConnectionHealthCheck` that checks the related SQL Database’s health.</span></span>

<span data-ttu-id="688e7-127">O método `AddCheck()` adiciona uma nova verificação de integridade com um nome especificado e a implementação do tipo `IHealthCheck`.</span><span class="sxs-lookup"><span data-stu-id="688e7-127">The `AddCheck()` method adds a new health check with a specified name and the implementation of type `IHealthCheck`.</span></span> <span data-ttu-id="688e7-128">Adicione várias Verificações de Integridade usando o método AddCheck, de modo que um microsserviço não forneça um status “íntegro” até que todas as suas verificações estejam íntegras.</span><span class="sxs-lookup"><span data-stu-id="688e7-128">You can add multiple Health Checks using AddCheck method, so a microservice won't provide a “healthy” status until all its checks are healthy.</span></span>

<span data-ttu-id="688e7-129">`SqlConnectionHealthCheck` é uma classe personalizada que implementa `IHealthCheck`, que usa uma cadeia de conexão como um parâmetro de construtor e executa uma consulta simples para verificar se a conexão com o Banco de Dados SQL foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="688e7-129">`SqlConnectionHealthCheck` is a custom class that implements `IHealthCheck`, which takes a connection string as a constructor parameter and executes a simple query to check if the connection to the SQL database is successful.</span></span> <span data-ttu-id="688e7-130">Ela retornara `HealthCheckResult.Healthy()` se a consulta for executada com êxito e um `FailureStatus` com a exceção real em caso de falha.</span><span class="sxs-lookup"><span data-stu-id="688e7-130">It returns `HealthCheckResult.Healthy()` if the query was executed successfully and a `FailureStatus` with the actual exception when it fails.</span></span>

```csharp
// Sample SQL Connection Health Check
public class SqlConnectionHealthCheck : IHealthCheck
{
    private static readonly string DefaultTestQuery = "Select 1";

    public string ConnectionString { get; }

    public string TestQuery { get; }

    public SqlConnectionHealthCheck(string connectionString)
        : this(connectionString, testQuery: DefaultTestQuery)
    {
    }

    public SqlConnectionHealthCheck(string connectionString, string testQuery)
    {
        ConnectionString = connectionString ?? throw new ArgumentNullException(nameof(connectionString));
        TestQuery = testQuery;
    }

    public async Task<HealthCheckResult> CheckHealthAsync(HealthCheckContext context, CancellationToken cancellationToken = default(CancellationToken))
    {
        using (var connection = new SqlConnection(ConnectionString))
        {
            try
            {
                await connection.OpenAsync(cancellationToken);

                if (TestQuery != null)
                {
                    var command = connection.CreateCommand();
                    command.CommandText = TestQuery;

                    await command.ExecuteNonQueryAsync(cancellationToken);
                }
            }
            catch (DbException ex)
            {
                return new HealthCheckResult(status: context.Registration.FailureStatus, exception: ex);
            }
        }

        return HealthCheckResult.Healthy();
    }
}
```

<span data-ttu-id="688e7-131">Observe que, no código anterior, `Select 1` é a consulta usada para verificar a Integridade do banco de dados.</span><span class="sxs-lookup"><span data-stu-id="688e7-131">Note that in the previous code, `Select 1` is the query used to check the Health of the database.</span></span> <span data-ttu-id="688e7-132">Para monitorar a disponibilidade de seus microsserviços, orquestradores como Kubernetes e Service Fabric realizam verificações de integridade periodicamente enviando solicitações para testar os microsserviços.</span><span class="sxs-lookup"><span data-stu-id="688e7-132">To monitor the availability of your microservices, orchestrators like Kubernetes and Service Fabric periodically perform health checks by sending requests to test the microservices.</span></span> <span data-ttu-id="688e7-133">É importante manter suas consultas de banco de dados eficientes para que essas operações sejam rápidas e não resultem em uma maior utilização de recursos.</span><span class="sxs-lookup"><span data-stu-id="688e7-133">It's important to keep your database queries efficient so that these operations are quick and don’t result in a higher utilization of resources.</span></span>

<span data-ttu-id="688e7-134">Por fim, crie um middleware que responde ao caminho da URL “/hc”:</span><span class="sxs-lookup"><span data-stu-id="688e7-134">Finally, create a middleware that responds to the url path “/hc”:</span></span>

```csharp
// Startup.cs from .NET Core 2.2 Web Api sample
//
public void Configure(IApplicationBuilder app, IHostingEnvironment env)
{
    //…
    app.UseHealthChecks("/hc");
    //…
} 
```

<span data-ttu-id="688e7-135">Quando o ponto de extremidade `<yourmicroservice>/hc` é invocado, ele executa todas as verificações de integridade configuradas no método `AddHealthChecks()` na classe de Inicialização e mostra o resultado.</span><span class="sxs-lookup"><span data-stu-id="688e7-135">When the endpoint `<yourmicroservice>/hc` is invoked, it runs all the health checks that are configured in the `AddHealthChecks()` method in the Startup class and shows the result.</span></span>

### <a name="healthchecks-implementation-in-eshoponcontainers"></a><span data-ttu-id="688e7-136">Implementação de HealthChecks no eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="688e7-136">HealthChecks implementation in eShopOnContainers</span></span>

<span data-ttu-id="688e7-137">Os microsserviços do eShopOnContainers dependem de vários serviços para realizar suas tarefas.</span><span class="sxs-lookup"><span data-stu-id="688e7-137">Microservices in eShopOnContainers rely on multiple services to perform its task.</span></span> <span data-ttu-id="688e7-138">Por exemplo, o microsserviço `Catalog.API` do eShopOnContainers depende de muitos serviços, como Armazenamento de Blobs do Azure, SQL Server e RabbitMQ.</span><span class="sxs-lookup"><span data-stu-id="688e7-138">For example, the `Catalog.API` microservice from eShopOnContainers depends on many services, such as Azure Blob Storage, SQL Server, and RabbitMQ.</span></span> <span data-ttu-id="688e7-139">Portanto, ele tem várias verificações de integridade adicionadas usando o método `AddCheck()`.</span><span class="sxs-lookup"><span data-stu-id="688e7-139">Therefore, it has several health checks added using the `AddCheck()` method.</span></span> <span data-ttu-id="688e7-140">Para cada serviço dependente, uma implementação de `IHealthCheck` personalizada que define seu respectivo status da integridade precisa ser adicionada.</span><span class="sxs-lookup"><span data-stu-id="688e7-140">For every dependent service, a custom `IHealthCheck` implementation that defines its respective health status needs to be added.</span></span>

<span data-ttu-id="688e7-141">O projeto de software livre [AspNetCore.Diagnostics.HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks) resolve esse problema fornecendo implementações de verificação de integridade personalizadas para cada um desses serviços corporativos baseados no .NET Core 2.2.</span><span class="sxs-lookup"><span data-stu-id="688e7-141">The open-source project [AspNetCore.Diagnostics.HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks) solves this problem by providing custom health check implementations for each of these enterprise services that are built on top of .NET Core 2.2.</span></span> <span data-ttu-id="688e7-142">Cada verificação de integridade está disponível como um pacote NuGet individual que pode ser adicionado ao projeto com facilidade.</span><span class="sxs-lookup"><span data-stu-id="688e7-142">Each health check is available as an individual NuGet package that can be easily added to the project.</span></span> <span data-ttu-id="688e7-143">O eShopOnContainers usa essas implementações amplamente em todos os seus microsserviços.</span><span class="sxs-lookup"><span data-stu-id="688e7-143">eShopOnContainers use them extensively in all its microservices.</span></span>

<span data-ttu-id="688e7-144">Por exemplo, no microsserviço `Catalog.API`, os seguintes pacotes NuGet foram adicionados:</span><span class="sxs-lookup"><span data-stu-id="688e7-144">For instance, in the `Catalog.API` microservice, the following NuGet packages were added:</span></span>

![Exibição do Gerenciador de Soluções do projeto Catalog.API, em que os pacotes NuGet AspNetCore.Diagnostics.HealthChecks são referenciados](./media/image6.png)

<span data-ttu-id="688e7-146">**Figura 8-7**.</span><span class="sxs-lookup"><span data-stu-id="688e7-146">**Figure 8-7**.</span></span> <span data-ttu-id="688e7-147">Verificações de Integridade personalizadas implementadas em Catalog.API usando AspNetCore.Diagnostics.HealthChecks</span><span class="sxs-lookup"><span data-stu-id="688e7-147">Custom Health Checks implemented in Catalog.API using AspNetCore.Diagnostics.HealthChecks</span></span>

<span data-ttu-id="688e7-148">No seguinte código, as implementações de verificação de integridade são adicionadas a cada serviço dependente e, em seguida, o middleware é configurado:</span><span class="sxs-lookup"><span data-stu-id="688e7-148">In the following code, the health check implementations are added for each dependent service and then the middleware is configured:</span></span>

```csharp
// Startup.cs from Catalog.api microservice
//
public static IServiceCollection AddCustomHealthCheck(this IServiceCollection services, IConfiguration configuration)
{
    var accountName = configuration.GetValue<string>("AzureStorageAccountName");
    var accountKey = configuration.GetValue<string>("AzureStorageAccountKey");

    var hcBuilder = services.AddHealthChecks();

    hcBuilder
        .AddSqlServer(
            configuration["ConnectionString"],
            name: "CatalogDB-check",
            tags: new string[] { "catalogdb" });

    if (!string.IsNullOrEmpty(accountName) && !string.IsNullOrEmpty(accountKey))
    {
        hcBuilder
            .AddAzureBlobStorage(
                $"DefaultEndpointsProtocol=https;AccountName={accountName};AccountKey={accountKey};EndpointSuffix=core.windows.net",
                name: "catalog-storage-check",
                tags: new string[] { "catalogstorage" });
    }
    if (configuration.GetValue<bool>("AzureServiceBusEnabled"))
    {
        hcBuilder
            .AddAzureServiceBusTopic(
                configuration["EventBusConnection"],
                topicName: "eshop_event_bus",
                name: "catalog-servicebus-check",
                tags: new string[] { "servicebus" });
    }
    else
    {
        hcBuilder
            .AddRabbitMQ(
                $"amqp://{configuration["EventBusConnection"]}",
                name: "catalog-rabbitmqbus-check",
                tags: new string[] { "rabbitmqbus" });
    }

    return services;
}
```

<span data-ttu-id="688e7-149">Por fim, adicionamos o middleware de HealthCheck para escutar no ponto de extremidade “/hc”:</span><span class="sxs-lookup"><span data-stu-id="688e7-149">Finally, we add the HealthCheck middleware to listen to “/hc” endpoint:</span></span>

```csharp
// HealthCheck middleware
app.UseHealthChecks("/hc", new HealthCheckOptions()
{
    Predicate = _ => true,
    ResponseWriter = UIResponseWriter.WriteHealthCheckUIResponse
});
}
```

### <a name="query-your-microservices-to-report-about-their-health-status"></a><span data-ttu-id="688e7-150">Consultar os microsserviços para relatar o status de integridade</span><span class="sxs-lookup"><span data-stu-id="688e7-150">Query your microservices to report about their health status</span></span>

<span data-ttu-id="688e7-151">Depois de configurar as verificações de integridade, como descrito neste artigo e colocar o microsserviço em execução no Docker, você poderá verificar diretamente se ele está íntegro usando um navegador.</span><span class="sxs-lookup"><span data-stu-id="688e7-151">When you've configured health checks as described in this article and you have the microservice running in Docker, you can directly check from a browser if it's healthy.</span></span> <span data-ttu-id="688e7-152">É necessário publicar a porta do contêiner no host do Docker, para que você possa acessar o contêiner por meio do IP externo do host do Docker ou por meio de `localhost`, como mostra a Figura 8-8.</span><span class="sxs-lookup"><span data-stu-id="688e7-152">You have to publish the container port in the Docker host, so you can access the container through the external Docker host IP or through `localhost`, as shown in figure 8-8.</span></span>

![Exibição do navegador da resposta JSON retornada por uma verificação de integridade](./media/image7.png)

<span data-ttu-id="688e7-154">**Figura 8-8**.</span><span class="sxs-lookup"><span data-stu-id="688e7-154">**Figure 8-8**.</span></span> <span data-ttu-id="688e7-155">Verificando o status da integridade de um único serviço em um navegador</span><span class="sxs-lookup"><span data-stu-id="688e7-155">Checking health status of a single service from a browser</span></span>

<span data-ttu-id="688e7-156">Nesse teste, você pode ver que o microsserviço `Catalog.API` (em execução na porta 5101) está íntegro, retornando o status HTTP 200 e informações de status em JSON.</span><span class="sxs-lookup"><span data-stu-id="688e7-156">In that test, you can see that the `Catalog.API` microservice (running on port 5101) is healthy, returning HTTP status 200 and status information in JSON.</span></span> <span data-ttu-id="688e7-157">O serviço também verificou a integridade de sua dependência do banco de dados do SQL Server e do RabbitMQ e, portanto, a verificação de integridade relatou a si própria como íntegra.</span><span class="sxs-lookup"><span data-stu-id="688e7-157">The service also checked the health of its SQL Server database dependency and RabbitMQ, so the health check reported itself as healthy.</span></span>

## <a name="use-watchdogs"></a><span data-ttu-id="688e7-158">Usar watchdogs</span><span class="sxs-lookup"><span data-stu-id="688e7-158">Use watchdogs</span></span>

<span data-ttu-id="688e7-159">Um watchdog é um serviço separado que pode inspecionar a integridade e a carga entre serviços e relatar a integridade dos microsserviços consultando a biblioteca `HealthChecks` já apresentada.</span><span class="sxs-lookup"><span data-stu-id="688e7-159">A watchdog is a separate service that can watch health and load across services, and report health about the microservices by querying with the `HealthChecks` library introduced earlier.</span></span> <span data-ttu-id="688e7-160">Isso pode ajudar a evitar erros que não seriam detectados com base no modo de exibição de um único serviço.</span><span class="sxs-lookup"><span data-stu-id="688e7-160">This can help prevent errors that would not be detected based on the view of a single service.</span></span> <span data-ttu-id="688e7-161">Watchdogs também são um bom lugar para hospedar código que pode realizar ações de correção para condições conhecidas sem interação do usuário.</span><span class="sxs-lookup"><span data-stu-id="688e7-161">Watchdogs also are a good place to host code that can perform remediation actions for known conditions without user interaction.</span></span>

<span data-ttu-id="688e7-162">O exemplo de eShopOnContainers contém uma página da Web que exibe os relatórios de verificação de integridade de exemplo, como mostra a Figura 8-9.</span><span class="sxs-lookup"><span data-stu-id="688e7-162">The eShopOnContainers sample contains a web page that displays sample health check reports, as shown in Figure 8-9.</span></span> <span data-ttu-id="688e7-163">Este é o watchdog mais simples que você pode ter, pois ele mostra simplesmente o estado dos aplicativos Web e dos microsserviços no eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="688e7-163">This is the simplest watchdog you could have since it only shows the state of the microservices and web applications in eShopOnContainers.</span></span> <span data-ttu-id="688e7-164">Geralmente, um watchdog também executa ações quando detecta estados não íntegro.</span><span class="sxs-lookup"><span data-stu-id="688e7-164">Usually a watchdog also takes actions when it detects unhealthy states.</span></span>

<span data-ttu-id="688e7-165">Uma boa notícia é que [AspNetCore.Diagnostics.HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks) também fornece o pacote NuGet [AspNetCore.HealthChecks.UI](https://www.nuget.org/packages/AspNetCore.HealthChecks.UI/), que pode ser usado para exibir os resultados da verificação de integridade dos URIs configurados.</span><span class="sxs-lookup"><span data-stu-id="688e7-165">Fortunately, [AspNetCore.Diagnostics.HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks) also provides [AspNetCore.HealthChecks.UI](https://www.nuget.org/packages/AspNetCore.HealthChecks.UI/) NuGet package that can be used to display the health check results from the configured URIs.</span></span>

![Exibição no navegador do aplicativo WebStatus mostrando o status da integridade de todos os microsserviços do eShopOnContainers](./media/image8.png)

<span data-ttu-id="688e7-167">**Figura 8-9**.</span><span class="sxs-lookup"><span data-stu-id="688e7-167">**Figure 8-9**.</span></span> <span data-ttu-id="688e7-168">Relatório de verificação de integridade de exemplo em eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="688e7-168">Sample health check report in eShopOnContainers</span></span>

<span data-ttu-id="688e7-169">Em resumo, esse serviço de watchdog consulta o ponto de extremidade "/hc" de cada microsserviço.</span><span class="sxs-lookup"><span data-stu-id="688e7-169">In summary, this watchdog service queries each microservice’s "/hc" endpoint.</span></span> <span data-ttu-id="688e7-170">Isso executará todas as verificações de integridade definidas dentro dele e retornará um estado de integridade geral dependendo todas essas verificações.</span><span class="sxs-lookup"><span data-stu-id="688e7-170">This will execute all the health checks defined within it and return an overall health state depending on all those checks.</span></span> <span data-ttu-id="688e7-171">A HealthChecksUI é fácil de ser consumida com algumas entradas de configuração e duas linhas de código que precisam ser adicionadas no Startup.cs do serviço de watchdog.</span><span class="sxs-lookup"><span data-stu-id="688e7-171">The HealthChecksUI is easy to consume with a few configuration entries and two lines of code that needs to be added into the Startup.cs of the watchdog service.</span></span>

<span data-ttu-id="688e7-172">Arquivo de configuração de exemplo para interface do usuário da verificação de integridade:</span><span class="sxs-lookup"><span data-stu-id="688e7-172">Sample configuration file for health check UI:</span></span>

```json
// Configuration
{
  "HealthChecks-UI": {
    "HealthChecks": [
      {
        "Name": "Ordering HTTP Check",
        "Uri": "http://localhost:5102/hc"
      },
      {
        "Name": "Ordering HTTP Background Check",
        "Uri": "http://localhost:5111/hc"
      },
      //...
    ]}
}
```

<span data-ttu-id="688e7-173">Arquivo Startup.cs que adiciona HealthChecksUI:</span><span class="sxs-lookup"><span data-stu-id="688e7-173">Startup.cs file that adds HealthChecksUI:</span></span>

```csharp
// Startup.cs from WebStatus(Watch Dog) service
//
public void ConfigureServices(IServiceCollection services)
{
    //…
    // Registers required services for health checks
    services.AddHealthChecksUI();
}
//…
public void Configure(IApplicationBuilder app, IHostingEnvironment env)
{
    //…
    app.UseHealthChecksUI(config=> config.UIPath = “/hc-ui”);
    //…
}
```

## <a name="health-checks-when-using-orchestrators"></a><span data-ttu-id="688e7-174">Verificações de integridade ao usar orquestradores</span><span class="sxs-lookup"><span data-stu-id="688e7-174">Health checks when using orchestrators</span></span>

<span data-ttu-id="688e7-175">Para monitorar a disponibilidade de seus microsserviços, orquestradores como Kubernetes e Service Fabric realizam verificações de integridade periodicamente enviando solicitações para testar os microsserviços.</span><span class="sxs-lookup"><span data-stu-id="688e7-175">To monitor the availability of your microservices, orchestrators like Kubernetes and Service Fabric periodically perform health checks by sending requests to test the microservices.</span></span> <span data-ttu-id="688e7-176">Quando um orquestrador determina que um serviço/contêiner não está íntegro, ele para de rotear solicitações para aquela instância.</span><span class="sxs-lookup"><span data-stu-id="688e7-176">When an orchestrator determines that a service/container is unhealthy, it stops routing requests to that instance.</span></span> <span data-ttu-id="688e7-177">Ele também geralmente cria uma nova instância do contêiner.</span><span class="sxs-lookup"><span data-stu-id="688e7-177">It also usually creates a new instance of that container.</span></span>

<span data-ttu-id="688e7-178">Por exemplo, a maioria dos orquestradores pode usar verificações de integridade para gerenciar implantações de tempo de inatividade zero.</span><span class="sxs-lookup"><span data-stu-id="688e7-178">For instance, most orchestrators can use health checks to manage zero-downtime deployments.</span></span> <span data-ttu-id="688e7-179">Somente quando o status de um serviço/contêiner é alterado para íntegro o orquestrador começa a rotear o tráfego para instâncias de serviço/contêiner.</span><span class="sxs-lookup"><span data-stu-id="688e7-179">Only when the status of a service/container changes to healthy will the orchestrator start routing traffic to service/container instances.</span></span>

<span data-ttu-id="688e7-180">O monitoramento de integridade é especialmente importante quando um orquestrador executa uma atualização do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="688e7-180">Health monitoring is especially important when an orchestrator performs an application upgrade.</span></span> <span data-ttu-id="688e7-181">Alguns orquestradores (como o Azure Service Fabric) atualizam os serviços em fases, por exemplo, podem atualizar um quinto da superfície de cluster para cada upgrade de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="688e7-181">Some orchestrators (like Azure Service Fabric) update services in phases—for example, they might update one-fifth of the cluster surface for each application upgrade.</span></span> <span data-ttu-id="688e7-182">O conjunto de nós que é atualizado ao mesmo tempo é mencionado como um *domínio de atualização*.</span><span class="sxs-lookup"><span data-stu-id="688e7-182">The set of nodes that's upgraded at the same time is referred to as an *upgrade domain*.</span></span> <span data-ttu-id="688e7-183">Depois de cada domínio de atualização ter sido atualizado e estar disponível para os usuários, esse domínio de atualização deverá passar por verificações de integridade antes que a implantação passe para o próximo domínio de atualização.</span><span class="sxs-lookup"><span data-stu-id="688e7-183">After each upgrade domain has been upgraded and is available to users, that upgrade domain must pass health checks before the deployment moves to the next upgrade domain.</span></span>

<span data-ttu-id="688e7-184">Outro aspecto da integridade de serviço são as métricas de relatório do serviço.</span><span class="sxs-lookup"><span data-stu-id="688e7-184">Another aspect of service health is reporting metrics from the service.</span></span> <span data-ttu-id="688e7-185">Este é uma funcionalidade avançada do modelo de integridade de alguns orquestradores, como o Service Fabric.</span><span class="sxs-lookup"><span data-stu-id="688e7-185">This is an advanced capability of the health model of some orchestrators, like Service Fabric.</span></span> <span data-ttu-id="688e7-186">As métricas são importantes ao usar um orquestrador, pois elas são usadas para equilibrar o uso de recursos.</span><span class="sxs-lookup"><span data-stu-id="688e7-186">Metrics are important when using an orchestrator because they are used to balance resource usage.</span></span> <span data-ttu-id="688e7-187">As métricas também podem ser um indicador de integridade do sistema.</span><span class="sxs-lookup"><span data-stu-id="688e7-187">Metrics also can be an indicator of system health.</span></span> <span data-ttu-id="688e7-188">Por exemplo, você pode ter um aplicativo com muitos microsserviços, e cada instância relata uma métrica de RPS (solicitações por segundo).</span><span class="sxs-lookup"><span data-stu-id="688e7-188">For example, you might have an application that has many microservices, and each instance reports a requests-per-second (RPS) metric.</span></span> <span data-ttu-id="688e7-189">Se um serviço estiver usando mais recursos (memória, processador etc.) que outro, o orquestrador poderá mover instâncias de serviço do cluster para tentar manter até mesmo a utilização de recursos.</span><span class="sxs-lookup"><span data-stu-id="688e7-189">If one service is using more resources (memory, processor, etc.) than another service, the orchestrator could move service instances around in the cluster to try to maintain even resource utilization.</span></span>

<span data-ttu-id="688e7-190">Observe que o Azure Service Fabric fornece seu próprio [modelo de monitoramento de integridade](/azure/service-fabric/service-fabric-health-introduction), que é mais avançado do que as verificações de integridade simples.</span><span class="sxs-lookup"><span data-stu-id="688e7-190">Note that Azure Service Fabric provides its own [Health Monitoring model](/azure/service-fabric/service-fabric-health-introduction), which is more advanced than simple health checks.</span></span>

## <a name="advanced-monitoring-visualization-analysis-and-alerts"></a><span data-ttu-id="688e7-191">Monitoramento avançado: visualização, análise e alertas</span><span class="sxs-lookup"><span data-stu-id="688e7-191">Advanced monitoring: visualization, analysis, and alerts</span></span>

<span data-ttu-id="688e7-192">A parte final do monitoramento é visualizar o fluxo de eventos, relatar o desempenho do serviço e alertar quando for detectado um problema.</span><span class="sxs-lookup"><span data-stu-id="688e7-192">The final part of monitoring is visualizing the event stream, reporting on service performance, and alerting when an issue is detected.</span></span> <span data-ttu-id="688e7-193">Você pode usar diferentes soluções para esse aspecto do monitoramento.</span><span class="sxs-lookup"><span data-stu-id="688e7-193">You can use different solutions for this aspect of monitoring.</span></span>

<span data-ttu-id="688e7-194">Você pode usar aplicativos personalizados simples que mostram o estado dos serviços, como a página personalizada mostrada na explicação do [AspNetCore.Diagnostics.HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks).</span><span class="sxs-lookup"><span data-stu-id="688e7-194">You can use simple custom applications showing the state of your services, like the custom page shown when explaining the [AspNetCore.Diagnostics.HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks).</span></span> <span data-ttu-id="688e7-195">Ou você pode usar ferramentas mais avançadas, como Azure Application Insights e o Operations Management Suite para gerar alertas com base em fluxo de eventos.</span><span class="sxs-lookup"><span data-stu-id="688e7-195">Or you could use more advanced tools like Azure Application Insights to raise alerts based on the stream of events.</span></span>

<span data-ttu-id="688e7-196">Por fim, se você estiver armazenando todos os fluxos de eventos, poderá usar o Microsoft Power BI ou uma solução de terceiros, como o Kibana ou o Splunk, para visualizar os dados.</span><span class="sxs-lookup"><span data-stu-id="688e7-196">Finally, if you're storing all the event streams, you can use Microsoft Power BI or other solutions like Kibana or Splunk to visualize the data.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="688e7-197">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="688e7-197">Additional resources</span></span>

-   <span data-ttu-id="688e7-198">**HealthChecks e interface do usuário de HealthChecks para o ASP.NET Core**
    [https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks )</span><span class="sxs-lookup"><span data-stu-id="688e7-198">**HealthChecks and HealthChecks UI for ASP.NET Core**
[https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks )</span></span>

-   <span data-ttu-id="688e7-199">**Introdução ao monitoramento de integridade do Service Fabric**
    [https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction](/azure/service-fabric/service-fabric-health-introduction)</span><span class="sxs-lookup"><span data-stu-id="688e7-199">**Introduction to Service Fabric health monitoring**
[https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction](/azure/service-fabric/service-fabric-health-introduction)</span></span>

-   <span data-ttu-id="688e7-200">**Azure Application Insights**
    [https://azure.microsoft.com/services/application-insights/](https://azure.microsoft.com/services/application-insights/)</span><span class="sxs-lookup"><span data-stu-id="688e7-200">**Azure Application Insights**
[https://azure.microsoft.com/services/application-insights/](https://azure.microsoft.com/services/application-insights/)</span></span>

-   <span data-ttu-id="688e7-201">**Microsoft Operations Management Suite**
    [https://www.microsoft.com/en-us/cloud-platform/operations-management-suite](https://www.microsoft.com/en-us/cloud-platform/operations-management-suite)</span><span class="sxs-lookup"><span data-stu-id="688e7-201">**Microsoft Operations Management Suite**
[https://www.microsoft.com/en-us/cloud-platform/operations-management-suite](https://www.microsoft.com/en-us/cloud-platform/operations-management-suite)</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="688e7-202">[Anterior](implement-circuit-breaker-pattern.md)
>[Próximo](../secure-net-microservices-web-applications/index.md)</span><span class="sxs-lookup"><span data-stu-id="688e7-202">[Previous](implement-circuit-breaker-pattern.md)
[Next](../secure-net-microservices-web-applications/index.md)</span></span>