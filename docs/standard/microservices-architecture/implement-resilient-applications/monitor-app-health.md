---
title: Monitoramento de integridade
description: "Arquitetura de Microservices .NET para aplicativos .NET em contêineres | Monitoramento de integridade"
keywords: "Docker, Microsserviços, ASP.NET, Contêiner"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: cbbad72f06bcaa882bc50083d9103b0872f51754
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="health-monitoring"></a><span data-ttu-id="c1b23-104">Monitoramento de integridade</span><span class="sxs-lookup"><span data-stu-id="c1b23-104">Health monitoring</span></span>

<span data-ttu-id="c1b23-105">Monitoramento de integridade pode permitir que informações quase em tempo real sobre o estado de seus contêineres e microservices.</span><span class="sxs-lookup"><span data-stu-id="c1b23-105">Health monitoring can allow near-real-time information about the state of your containers and microservices.</span></span> <span data-ttu-id="c1b23-106">Monitoramento de integridade é fundamental para vários aspectos da operação microservices e é especialmente importante quando orchestrators executar atualizações de aplicativo parcial em fases, conforme explicado posteriormente.</span><span class="sxs-lookup"><span data-stu-id="c1b23-106">Health monitoring is critical to multiple aspects of operating microservices and is especially important when orchestrators perform partial application upgrades in phases, as explained later.</span></span>

<span data-ttu-id="c1b23-107">Aplicativos baseados em Microservices geralmente usam pulsações ou verificações de integridade para habilitar seus monitores de desempenho, agendadores e orchestrators controlar a variedade de serviços.</span><span class="sxs-lookup"><span data-stu-id="c1b23-107">Microservices-based applications often use heartbeats or health checks to enable their performance monitors, schedulers, and orchestrators to keep track of the multitude of services.</span></span> <span data-ttu-id="c1b23-108">Se os serviços não podem enviar algum tipo de sinal "Estou alive", sob demanda ou em um agendamento, seu aplicativo poderá enfrentar riscos quando você implantar atualizações, ou pode simplesmente detectar falhas muito tarde e não conseguir interromper falhas em cascata que podem terminar em interrupções principais.</span><span class="sxs-lookup"><span data-stu-id="c1b23-108">If services cannot send some sort of “I’m alive” signal, either on demand or on a schedule, your application might face risks when you deploy updates, or it might simply detect failures too late and not be able to stop cascading failures that can end up in major outages.</span></span>

<span data-ttu-id="c1b23-109">No modelo comum, serviços de enviar relatórios sobre o status e que informações são agregadas para fornecer uma visão geral do estado de integridade de seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c1b23-109">In the typical model, services send reports about their status, and that information is aggregated to provide an overall view of the state of health of your application.</span></span> <span data-ttu-id="c1b23-110">Se você estiver usando um orquestrador, você pode fornecer informações de integridade para o cluster do orchestrator, para que o cluster possa atuar adequadamente.</span><span class="sxs-lookup"><span data-stu-id="c1b23-110">If you are using an orchestrator, you can provide health information to your orchestrator’s cluster, so that the cluster can act accordingly.</span></span> <span data-ttu-id="c1b23-111">Se investir em relatórios de integridade de alta qualidade que é personalizado para seu aplicativo, você pode detectar e corrigir problemas do seu aplicativo em execução muito mais facilmente.</span><span class="sxs-lookup"><span data-stu-id="c1b23-111">If you invest in high-quality health reporting that is customized for your application, you can detect and fix issues for your running application much more easily.</span></span>

## <a name="implementing-health-checks-in-aspnet-core-services"></a><span data-ttu-id="c1b23-112">Implementação de integridade verifica no ASP.NET Core services</span><span class="sxs-lookup"><span data-stu-id="c1b23-112">Implementing health checks in ASP.NET Core services</span></span>

<span data-ttu-id="c1b23-113">Ao desenvolver um aplicativo de microsserviço ou da web do ASP.NET Core, você pode usar uma biblioteca de chamada HealthChecks da equipe do ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="c1b23-113">When developing an ASP.NET Core microservice or web application, you can use a library named HealthChecks from the ASP.NET team.</span></span> <span data-ttu-id="c1b23-114">(A partir de maio de 2017, uma versão mais recente está disponível no GitHub).</span><span class="sxs-lookup"><span data-stu-id="c1b23-114">(As of May 2017, an early release is available on GitHub).</span></span>

<span data-ttu-id="c1b23-115">Essa biblioteca é fácil de usar e fornece recursos que permitem que você valide se qualquer recurso externo específico necessário para seu aplicativo (como um banco de dados do SQL Server ou a API remota) está funcionando corretamente.</span><span class="sxs-lookup"><span data-stu-id="c1b23-115">This library is easy to use and provides features that let you validate that any specific external resource needed for your application (like a SQL Server database or remote API) is working properly.</span></span> <span data-ttu-id="c1b23-116">Quando você usa essa biblioteca, você também pode decidir o que significa que o recurso esteja íntegro, como explicaremos mais tarde.</span><span class="sxs-lookup"><span data-stu-id="c1b23-116">When you use this library, you can also decide what it means that the resource is healthy, as we explain later.</span></span>

<span data-ttu-id="c1b23-117">Para usar essa biblioteca, você precisa primeiro usar a biblioteca em sua microservices.</span><span class="sxs-lookup"><span data-stu-id="c1b23-117">In order to use this library, you need to first use the library in your microservices.</span></span> <span data-ttu-id="c1b23-118">Em segundo lugar, é necessário um aplicativo front-end que consulta para os relatórios de integridade.</span><span class="sxs-lookup"><span data-stu-id="c1b23-118">Second, you need a front-end application that queries for the health reports.</span></span> <span data-ttu-id="c1b23-119">Aplicativo front-end pode ser um aplicativo de relatório personalizado, ou pode ser um orchestrator em si pode reagir de acordo para os estados de integridade.</span><span class="sxs-lookup"><span data-stu-id="c1b23-119">That front end application could be a custom reporting application, or it could be an orchestrator itself that can react accordingly to the health states.</span></span>

### <a name="using-the-healthchecks-library-in-your-back-end-aspnet-microservices"></a><span data-ttu-id="c1b23-120">Usando a biblioteca de HealthChecks em seu back-end ASP.NET microservices</span><span class="sxs-lookup"><span data-stu-id="c1b23-120">Using the HealthChecks library in your back end ASP.NET microservices</span></span>

<span data-ttu-id="c1b23-121">Você pode ver como a biblioteca de HealthChecks é usada no aplicativo de exemplo eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="c1b23-121">You can see how the HealthChecks library is used in the eShopOnContainers sample application.</span></span> <span data-ttu-id="c1b23-122">Para começar, você precisa definir o que constitui um status de integridade para cada microsserviço.</span><span class="sxs-lookup"><span data-stu-id="c1b23-122">To begin, you need to define what constitutes a healthy status for each microservice.</span></span> <span data-ttu-id="c1b23-123">O aplicativo de exemplo, os microservices estão funcionando se a API de microsserviço está acessível por meio de HTTP e se seu banco de dados do SQL Server relacionado também está disponível.</span><span class="sxs-lookup"><span data-stu-id="c1b23-123">In the sample application, the microservices are healthy if the microservice API is accessible via HTTP and if its related SQL Server database is also available.</span></span>

<span data-ttu-id="c1b23-124">No futuro, você poderá instalar a biblioteca de HealthChecks como um pacote do NuGet.</span><span class="sxs-lookup"><span data-stu-id="c1b23-124">In the future, you will be able to install the HealthChecks library as a NuGet package.</span></span> <span data-ttu-id="c1b23-125">Mas a redação deste artigo, você precisa baixar e compilar o código como parte de sua solução.</span><span class="sxs-lookup"><span data-stu-id="c1b23-125">But as of this writing, you need to download and compile the code as part of your solution.</span></span> <span data-ttu-id="c1b23-126">Clone de código disponível em https://github.com/aspnet/HealthChecks e copie as seguintes pastas para sua solução.</span><span class="sxs-lookup"><span data-stu-id="c1b23-126">Clone the code available at https://github.com/aspnet/HealthChecks and copy the following folders to your solution.</span></span>

  - <span data-ttu-id="c1b23-127">src/comum</span><span class="sxs-lookup"><span data-stu-id="c1b23-127">src/common</span></span>
  - <span data-ttu-id="c1b23-128">src/Microsoft.AspNetCore.HealthChecks</span><span class="sxs-lookup"><span data-stu-id="c1b23-128">src/Microsoft.AspNetCore.HealthChecks</span></span>
  - <span data-ttu-id="c1b23-129">src/Microsoft.Extensions.HealthChecks</span><span class="sxs-lookup"><span data-stu-id="c1b23-129">src/Microsoft.Extensions.HealthChecks</span></span>
  - <span data-ttu-id="c1b23-130">src/Microsoft.Extensions.HealthChecks.SqlServer</span><span class="sxs-lookup"><span data-stu-id="c1b23-130">src/Microsoft.Extensions.HealthChecks.SqlServer</span></span>

<span data-ttu-id="c1b23-131">Você também pode usar verificações adicionais, como aquelas para o Azure (Microsoft.Extensions.HealthChecks.AzureStorage), mas como esta versão do eShopOnContainers não tem nenhuma dependência no Azure, não é necessário.</span><span class="sxs-lookup"><span data-stu-id="c1b23-131">You could also use additional checks like the ones for Azure (Microsoft.Extensions.HealthChecks.AzureStorage), but since this version of eShopOnContainers does not have any dependency on Azure, you do not need it.</span></span> <span data-ttu-id="c1b23-132">As verificações de integridade do ASP.NET, não é necessário porque eShopOnContainers é baseado no ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="c1b23-132">You do not need the ASP.NET health checks, because eShopOnContainers is based on ASP.NET Core.</span></span>

<span data-ttu-id="c1b23-133">Figura 10-6 mostra a biblioteca HealthChecks no Visual Studio, pronto para ser usado como um bloco de construção por qualquer microservices.</span><span class="sxs-lookup"><span data-stu-id="c1b23-133">Figure 10-6 shows the HealthChecks library in Visual Studio, ready to be used as a building block by any microservices.</span></span>

![](./media/image6.png)

<span data-ttu-id="c1b23-134">**Figura 10-6**.</span><span class="sxs-lookup"><span data-stu-id="c1b23-134">**Figure 10-6**.</span></span> <span data-ttu-id="c1b23-135">Código-fonte biblioteca ASP.NET Core HealthChecks em uma solução do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c1b23-135">ASP.NET Core HealthChecks library source code in a Visual Studio solution</span></span>

<span data-ttu-id="c1b23-136">Conforme apresentada anteriormente, a primeira coisa a fazer em cada projeto de microsserviço é adicionar uma referência para as três bibliotecas de HealthChecks.</span><span class="sxs-lookup"><span data-stu-id="c1b23-136">As introduced earlier, the first thing to do in each microservice project is to add a reference to the three HealthChecks libraries.</span></span> <span data-ttu-id="c1b23-137">Depois disso, você deve adicionar as ações de verificação de integridade que você deseja executar no que microsserviço.</span><span class="sxs-lookup"><span data-stu-id="c1b23-137">After that, you add the health check actions that you want to perform in that microservice.</span></span> <span data-ttu-id="c1b23-138">Essas ações são basicamente as dependências em outros bancos de dados ou microservices (HttpUrlCheck) (atualmente SqlCheck\* para bancos de dados do SQL Server).</span><span class="sxs-lookup"><span data-stu-id="c1b23-138">These actions are basically dependencies on other microservices (HttpUrlCheck) or databases (currently SqlCheck\* for SQL Server databases).</span></span> <span data-ttu-id="c1b23-139">Adicionar a ação dentro da classe de inicialização de cada microsserviço ASP.NET ou um aplicativo web ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="c1b23-139">You add the action within the Startup class of each ASP.NET microservice or ASP.NET web application.</span></span>

<span data-ttu-id="c1b23-140">Cada serviço ou aplicativo web deve ser configurado com a adição de todas as suas dependências HTTP ou o banco de dados como um método AddHealthCheck.</span><span class="sxs-lookup"><span data-stu-id="c1b23-140">Each service or web application should be configured by adding all its HTTP or database dependencies as one AddHealthCheck method.</span></span> <span data-ttu-id="c1b23-141">Por exemplo, o aplicativo web MVC eShopOnContainers depende de muitos serviços, portanto, tem vários métodos de AddCheck adicionados para as verificações de integridade.</span><span class="sxs-lookup"><span data-stu-id="c1b23-141">For example, the MVC web application from eShopOnContainers depends on many services, therefore has several AddCheck methods added to the health checks.</span></span>

<span data-ttu-id="c1b23-142">Por exemplo, no código a seguir você pode ver como o catálogo microsserviço adiciona uma dependência em seu banco de dados do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="c1b23-142">For instance, in the following code you can see how the catalog microservice adds a dependency on its SQL Server database.</span></span>

```csharp
// Startup.cs from Catalog.api microservice
//
public class Startup
{
    public void ConfigureServices(IServiceCollection services)
    {
        // Add framework services
        services.AddHealthChecks(checks =>
        {
            checks.AddSqlCheck("CatalogDb", Configuration["ConnectionString"]);
        });
        // Other services
    }
}
```

<span data-ttu-id="c1b23-143">No entanto, o aplicativo web MVC do eShopOnContainers tem várias dependências nos outros a microservices.</span><span class="sxs-lookup"><span data-stu-id="c1b23-143">However, the MVC web application of eShopOnContainers has multiple dependencies on the rest of the microservices.</span></span> <span data-ttu-id="c1b23-144">Portanto, ele chama um método AddUrlCheck para cada microsserviço, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="c1b23-144">Therefore, it calls one AddUrlCheck method for each microservice, as shown in the following example:</span></span>

```csharp
// Startup.cs from the MVC web app
public class Startup
{
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddMvc();
        services.Configure<AppSettings>(Configuration);
        services.AddHealthChecks(checks =>
        {
            checks.AddUrlCheck(Configuration["CatalogUrl"]);
            checks.AddUrlCheck(Configuration["OrderingUrl"]);
            checks.AddUrlCheck(Configuration["BasketUrl"]);
            checks.AddUrlCheck(Configuration["IdentityUrl"]);
        });
    }
}
```

<span data-ttu-id="c1b23-145">Assim, um microsserviço não fornecerá um status "Íntegro" até que todas as suas verificações também estão íntegros.</span><span class="sxs-lookup"><span data-stu-id="c1b23-145">Thus, a microservice will not provide a “healthy” status until all its checks are healthy as well.</span></span>

<span data-ttu-id="c1b23-146">Se o microsserviço não tem uma dependência em um serviço ou no SQL Server, você deve adicionar apenas uma verificação de Healthy("Ok").</span><span class="sxs-lookup"><span data-stu-id="c1b23-146">If the microservice does not have a dependency on a service or on SQL Server, you should just add a Healthy("Ok") check.</span></span> <span data-ttu-id="c1b23-147">O código a seguir é do eShopOnContainers basket.api microsserviço.</span><span class="sxs-lookup"><span data-stu-id="c1b23-147">The following code is from the eShopOnContainers basket.api microservice.</span></span> <span data-ttu-id="c1b23-148">(O carrinho microsserviço usa o cache Redis, mas a biblioteca ainda não inclui um provedor de verificação de integridade do Redis.)</span><span class="sxs-lookup"><span data-stu-id="c1b23-148">(The basket microservice uses the Redis cache, but the library does not yet include a Redis health check provider.)</span></span>

```csharp
services.AddHealthChecks(checks =>
{
    checks.AddValueTaskCheck("HTTP Endpoint", () => new
        ValueTask<IHealthCheckResult>(HealthCheckResult.Healthy("Ok")));
});
```

<span data-ttu-id="c1b23-149">Para um serviço ou aplicativo web para expor o ponto de extremidade de verificação de integridade, ele deverá habilitar o UseHealthChecks (\[*url\_para\_integridade\_verifica*\]) extensão método.</span><span class="sxs-lookup"><span data-stu-id="c1b23-149">For a service or web application to expose the health check endpoint, it has to enable the UseHealthChecks(\[*url\_for\_health\_checks*\]) extension method.</span></span> <span data-ttu-id="c1b23-150">Esse método passa no WebHostBuilder nível no principal método de classe de programa do ASP.NET Core web ou serviço de aplicativo, logo após UseKestrel conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="c1b23-150">This method goes at the WebHostBuilder level in the main method of the Program class of your ASP.NET Core service or web application, right after UseKestrel as shown in the code below.</span></span>

```csharp
namespace Microsoft.eShopOnContainers.WebMVC
{
    public class Program
    {
        public static void Main(string[] args)
        {
            var host = new WebHostBuilder()
                .UseKestrel()
                .UseHealthChecks("/hc")
                .UseContentRoot(Directory.GetCurrentDirectory())
                .UseIISIntegration()
                .UseStartup<Startup>()
                .Build();
            host.Run();
        }
    }
}
```

<span data-ttu-id="c1b23-151">O processo funciona da seguinte maneira: cada microsserviço expõe /hc o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="c1b23-151">The process works like this: each microservice exposes the endpoint /hc.</span></span> <span data-ttu-id="c1b23-152">Esse ponto de extremidade é criado pela biblioteca HealthChecks middleware ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="c1b23-152">That endpoint is created by the HealthChecks library ASP.NET Core middleware.</span></span> <span data-ttu-id="c1b23-153">Quando esse ponto de extremidade é invocado, ele executa todas as verificações de integridade são configuradas no método AddHealthChecks na classe de inicialização.</span><span class="sxs-lookup"><span data-stu-id="c1b23-153">When that endpoint is invoked, it runs all the health checks that are configured in the AddHealthChecks method in the Startup class.</span></span>

<span data-ttu-id="c1b23-154">O método UseHealthChecks espera uma porta ou um caminho.</span><span class="sxs-lookup"><span data-stu-id="c1b23-154">The UseHealthChecks method expects a port or a path.</span></span> <span data-ttu-id="c1b23-155">Essa porta ou o caminho é o ponto de extremidade a ser usado para verificar o estado de integridade do serviço.</span><span class="sxs-lookup"><span data-stu-id="c1b23-155">That port or path is the endpoint to use to check the health state of the service.</span></span> <span data-ttu-id="c1b23-156">Por exemplo, o catálogo microsserviço usa /hc o caminho.</span><span class="sxs-lookup"><span data-stu-id="c1b23-156">For instance, the catalog microservice uses the path /hc.</span></span>

### <a name="caching-health-check-responses"></a><span data-ttu-id="c1b23-157">Cache de respostas de verificação de integridade</span><span class="sxs-lookup"><span data-stu-id="c1b23-157">Caching health check responses</span></span>

<span data-ttu-id="c1b23-158">Desde que você não deseja causar uma negação de serviço (DoS) nos serviços ou simplesmente não desejar afetar o desempenho do serviço Verificando recursos com muita frequência, você pode armazenar em cache a retornar e configurar uma duração de cache para cada verificação de integridade.</span><span class="sxs-lookup"><span data-stu-id="c1b23-158">Since you do not want to cause a Denial of Service (DoS) in your services, or you simply do not want to impact service performance by checking resources too frequently, you can cache the returns and configure a cache duration for each health check.</span></span>

<span data-ttu-id="c1b23-159">Por padrão, a duração do cache internamente é definida como 5 minutos, mas você pode alterar essa duração do cache em cada verificação de integridade, como no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="c1b23-159">By default, the cache duration is internally set to 5 minutes, but you can change that cache duration on each health check, as in the following code:</span></span>

```csharp
checks.AddUrlCheck(Configuration["CatalogUrl"],1); // 1 min as cache duration
```

### <a name="querying-your-microservices-to-report-about-their-health-status"></a><span data-ttu-id="c1b23-160">Consultando o microservices para relatório sobre seu status de integridade</span><span class="sxs-lookup"><span data-stu-id="c1b23-160">Querying your microservices to report about their health status</span></span>

<span data-ttu-id="c1b23-161">Quando você tiver configurado as verificações de integridade, conforme descrito aqui, quando o microsserviço estiver em execução no Docker, diretamente pode verificar em um navegador se está íntegro.</span><span class="sxs-lookup"><span data-stu-id="c1b23-161">When you have configured health checks as described here, once the microservice is running in Docker, you can directly check from a browser if it is healthy.</span></span> <span data-ttu-id="c1b23-162">(Isso requer que você está publicando a porta do contêiner fora do host do Docker, para que possa acessar o contêiner por meio de localhost ou o IP de host externo do Docker.) Figura 10-7 mostra uma solicitação em um navegador e as respostas correspondentes.</span><span class="sxs-lookup"><span data-stu-id="c1b23-162">(This does require that you are publishing the container port out of the Docker host, so you can access the container through localhost or through the external Docker host IP.) Figure 10-7 shows a request in a browser and the corresponding response.</span></span>

![](./media/image7.png)

<span data-ttu-id="c1b23-163">**Figura 10-7**.</span><span class="sxs-lookup"><span data-stu-id="c1b23-163">**Figure 10-7**.</span></span> <span data-ttu-id="c1b23-164">Verificando o status de integridade de um único serviço em um navegador</span><span class="sxs-lookup"><span data-stu-id="c1b23-164">Checking health status of a single service from a browser</span></span>

<span data-ttu-id="c1b23-165">No teste, você pode ver que o microsserviço catalog.api (em execução na porta 5101) esteja íntegro, retornando status HTTP 200 e informações de status em JSON.</span><span class="sxs-lookup"><span data-stu-id="c1b23-165">In that test, you can see that the catalog.api microservice (running on port 5101) is healthy, returning HTTP status 200 and status information in JSON.</span></span> <span data-ttu-id="c1b23-166">Isso também significa que internamente o serviço também marcada a integridade de sua dependência do banco de dados do SQL Server e que a verificação de integridade foi apresentou íntegro.</span><span class="sxs-lookup"><span data-stu-id="c1b23-166">It also means that internally the service also checked the health of its SQL Server database dependency and that health check was reported itself as healthy.</span></span>

## <a name="using-watchdogs"></a><span data-ttu-id="c1b23-167">Usando watchdogs</span><span class="sxs-lookup"><span data-stu-id="c1b23-167">Using watchdogs</span></span>

<span data-ttu-id="c1b23-168">Um watchdog é um serviço separado que pode assistir a integridade e a carga em serviços e a integridade de relatório sobre o microservices consultando-se com a biblioteca de HealthChecks apresentada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="c1b23-168">A watchdog is a separate service that can watch health and load across services, and report health about the microservices by querying with the HealthChecks library introduced earlier.</span></span> <span data-ttu-id="c1b23-169">Isso pode ajudar a evitar erros que não seriam detectados com base no modo de exibição de um único serviço.</span><span class="sxs-lookup"><span data-stu-id="c1b23-169">This can help prevent errors that would not be detected based on the view of a single service.</span></span> <span data-ttu-id="c1b23-170">Watchdogs também são um bom lugar para código de host que pode realizar ações de correção para condições conhecidas sem interação do usuário.</span><span class="sxs-lookup"><span data-stu-id="c1b23-170">Watchdogs also are a good place to host code that can perform remediation actions for known conditions without user interaction.</span></span>

<span data-ttu-id="c1b23-171">O exemplo de eShopOnContainers contém uma página da web que exibe os relatórios de verificação de integridade de exemplo, conforme mostrado na Figura 10-8.</span><span class="sxs-lookup"><span data-stu-id="c1b23-171">The eShopOnContainers sample contains a web page that displays sample health check reports, as shown in Figure 10-8.</span></span> <span data-ttu-id="c1b23-172">Este é o watchdog mais simples, você pode ter, desde que ela simplesmente é mostra o estado dos aplicativos web e microservices eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="c1b23-172">This is the simplest watchdog you could have, since all it does is shows the state of the microservices and web applications in eShopOnContainers.</span></span> <span data-ttu-id="c1b23-173">Geralmente um watchdog também executa ações quando ele detecta estados não íntegro.</span><span class="sxs-lookup"><span data-stu-id="c1b23-173">Usually a watchdog also takes actions when it detects unhealthy states.</span></span>

![](./media/image8.png)

<span data-ttu-id="c1b23-174">**Figura 10-8**.</span><span class="sxs-lookup"><span data-stu-id="c1b23-174">**Figure 10-8**.</span></span> <span data-ttu-id="c1b23-175">Relatório de verificação de integridade de exemplo no eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="c1b23-175">Sample health check report in eShopOnContainers</span></span>

<span data-ttu-id="c1b23-176">Em resumo, o middleware ASP.NET da biblioteca do ASP.NET Core HealthChecks fornece um ponto de extremidade de verificação de integridade único para cada microsserviço.</span><span class="sxs-lookup"><span data-stu-id="c1b23-176">In summary, the ASP.NET middleware of the ASP.NET Core HealthChecks library provides a single health check endpoint for each microservice.</span></span> <span data-ttu-id="c1b23-177">Isso será executar todas as verificações de integridade definidas dentro dela e retorna um estado de integridade geral dependendo todas essas verificações.</span><span class="sxs-lookup"><span data-stu-id="c1b23-177">This will execute all the health checks defined within it and return an overall health state depending on all those checks.</span></span>

<span data-ttu-id="c1b23-178">A biblioteca de HealthChecks é extensível via novas verificações de integridade dos futuros recursos externos.</span><span class="sxs-lookup"><span data-stu-id="c1b23-178">The HealthChecks library is extensible through new health checks of future external resources.</span></span> <span data-ttu-id="c1b23-179">Por exemplo, esperamos que no futuro a biblioteca terá verificações de integridade para o cache Redis em outros bancos de dados.</span><span class="sxs-lookup"><span data-stu-id="c1b23-179">For example, we expect that in the future the library will have health checks for Redis cache and for other databases.</span></span> <span data-ttu-id="c1b23-180">A biblioteca permite relatório por várias dependências de aplicativo ou serviço de integridade, e você pode executar as ações com base nessas verificações de integridade.</span><span class="sxs-lookup"><span data-stu-id="c1b23-180">The library allows health reporting by multiple service or application dependencies, and you can then take actions based on those health checks.</span></span>

## <a name="health-checks-when-using-orchestrators"></a><span data-ttu-id="c1b23-181">Verificações de integridade ao usar orchestrators</span><span class="sxs-lookup"><span data-stu-id="c1b23-181">Health checks when using orchestrators</span></span>

<span data-ttu-id="c1b23-182">Para monitorar a disponibilidade de seu microservices, orchestrators como o Docker Swarm, Kubernetes e do Service Fabric periodicamente realiza verificações de integridade, enviando solicitações para testar o microservices.</span><span class="sxs-lookup"><span data-stu-id="c1b23-182">To monitor the availability of your microservices, orchestrators like Docker Swarm, Kubernetes, and Service Fabric periodically perform health checks by sending requests to test the microservices.</span></span> <span data-ttu-id="c1b23-183">Quando um orquestrador determina que um contêiner de serviço/não está íntegro, que ele interrompe a rotear solicitações para essa instância.</span><span class="sxs-lookup"><span data-stu-id="c1b23-183">When an orchestrator determines that a service/container is unhealthy, it stops routing requests to that instance.</span></span> <span data-ttu-id="c1b23-184">Ele também geralmente cria uma nova instância do contêiner.</span><span class="sxs-lookup"><span data-stu-id="c1b23-184">It also usually creates a new instance of that container.</span></span>

<span data-ttu-id="c1b23-185">Por exemplo, orchestrators a maioria das podem usar verificações de integridade para gerenciar implantações de tempo de inatividade zero.</span><span class="sxs-lookup"><span data-stu-id="c1b23-185">For instance, most orchestrators can use health checks to manage zero-downtime deployments.</span></span> <span data-ttu-id="c1b23-186">Somente quando o status de um contêiner do serviço é alterado para íntegro o orchestrator iniciar rotear o tráfego para instâncias de contêiner do serviço.</span><span class="sxs-lookup"><span data-stu-id="c1b23-186">Only when the status of a service/container changes to healthy will the orchestrator start routing traffic to service/container instances.</span></span>

<span data-ttu-id="c1b23-187">Monitoramento de integridade é especialmente importante quando um orquestrador executa uma atualização do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c1b23-187">Health monitoring is especially important when an orchestrator performs an application upgrade.</span></span> <span data-ttu-id="c1b23-188">Alguns orchestrators (como o Azure Service Fabric) atualizar serviços em fases — por exemplo, eles podem atualizar um quinto da superfície de cluster para cada atualização de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c1b23-188">Some orchestrators (like Azure Service Fabric) update services in phases—for example, they might update one-fifth of the cluster surface for each application upgrade.</span></span> <span data-ttu-id="c1b23-189">O conjunto de nós que é atualizado ao mesmo tempo é referido como uma *domínio de atualização*.</span><span class="sxs-lookup"><span data-stu-id="c1b23-189">The set of nodes that is upgraded at the same time is referred to as an *upgrade domain*.</span></span> <span data-ttu-id="c1b23-190">Depois de cada domínio de atualização foi atualizado e está disponível para usuários, esse domínio de atualização deve passar verificações de integridade antes que a implantação é movido para o próximo domínio de atualização.</span><span class="sxs-lookup"><span data-stu-id="c1b23-190">After each upgrade domain has been upgraded and is available to users, that upgrade domain must pass health checks before the deployment moves to the next upgrade domain.</span></span>

<span data-ttu-id="c1b23-191">Métricas do serviço de relatórios é outro aspecto da integridade do serviço.</span><span class="sxs-lookup"><span data-stu-id="c1b23-191">Another aspect of service health is reporting metrics from the service.</span></span> <span data-ttu-id="c1b23-192">Este é um recurso avançado do modelo de integridade de alguns orchestrators, como o Service Fabric.</span><span class="sxs-lookup"><span data-stu-id="c1b23-192">This is an advanced capability of the health model of some orchestrators, like Service Fabric.</span></span> <span data-ttu-id="c1b23-193">Métricas são importantes ao usar um orquestrador porque eles são usados para equilibrar o uso de recursos.</span><span class="sxs-lookup"><span data-stu-id="c1b23-193">Metrics are important when using an orchestrator because they are used to balance resource usage.</span></span> <span data-ttu-id="c1b23-194">Métricas também podem ser um indicador de integridade do sistema.</span><span class="sxs-lookup"><span data-stu-id="c1b23-194">Metrics also can be an indicator of system health.</span></span> <span data-ttu-id="c1b23-195">Por exemplo, você pode ter um aplicativo que tem muitas microservices, e cada instância informa uma métrica de solicitações por segundo (RPS).</span><span class="sxs-lookup"><span data-stu-id="c1b23-195">For example, you might have an application that has many microservices, and each instance reports a requests-per-second (RPS) metric.</span></span> <span data-ttu-id="c1b23-196">Se um serviço estiver usando mais recursos (memória, processador, etc.) que outro serviço, o orchestrator pode mover instâncias de serviço do cluster para tentar manter até mesmo a utilização de recursos.</span><span class="sxs-lookup"><span data-stu-id="c1b23-196">If one service is using more resources (memory, processor, etc.) than another service, the orchestrator could move service instances around in the cluster to try to maintain even resource utilization.</span></span>

<span data-ttu-id="c1b23-197">Observe que se você estiver usando o Azure Service Fabric, ele fornece seu próprio [modelo de monitoramento de integridade](https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction), que é mais avançada do que as verificações de integridade simples.</span><span class="sxs-lookup"><span data-stu-id="c1b23-197">Note that if you are using Azure Service Fabric, it provides its own [Health Monitoring model](https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction), which is more advanced than simple health checks.</span></span>

## <a name="advanced-monitoring-visualization-analysis-and-alerts"></a><span data-ttu-id="c1b23-198">Monitoramento avançado: visualização, análise e alertas</span><span class="sxs-lookup"><span data-stu-id="c1b23-198">Advanced monitoring: visualization, analysis, and alerts</span></span>

<span data-ttu-id="c1b23-199">A parte final do monitoramento está visualizando o fluxo de eventos, relatórios sobre o desempenho do serviço e alertas quando é detectado um problema.</span><span class="sxs-lookup"><span data-stu-id="c1b23-199">The final part of monitoring is visualizing the event stream, reporting on service performance, and alerting when an issue is detected.</span></span> <span data-ttu-id="c1b23-200">Você pode usar diferentes soluções para esse aspecto do monitoramento.</span><span class="sxs-lookup"><span data-stu-id="c1b23-200">You can use different solutions for this aspect of monitoring.</span></span>

<span data-ttu-id="c1b23-201">Você pode usar simples aplicativos personalizados que mostra o estado de seus serviços, como a página personalizada mostramos quando explicamos [ASP.NET Core HealthChecks](https://github.com/aspnet/HealthChecks).</span><span class="sxs-lookup"><span data-stu-id="c1b23-201">You can use simple custom applications showing the state of your services, like the custom page we showed when we explained [ASP.NET Core HealthChecks](https://github.com/aspnet/HealthChecks).</span></span> <span data-ttu-id="c1b23-202">Ou você pode usar as ferramentas mais avançadas, como informações de aplicativo do Azure e Operations Management Suite para gerar alertas com base em fluxo de eventos.</span><span class="sxs-lookup"><span data-stu-id="c1b23-202">Or you could use more advanced tools like Azure Application Insights and Operations Management Suite to raise alerts based on the stream of events.</span></span>

<span data-ttu-id="c1b23-203">Por fim, se você estava armazenando os fluxos de eventos, você pode usar Microsoft Power BI ou uma solução de terceiros como Kibana ou Splunk para visualizar os dados.</span><span class="sxs-lookup"><span data-stu-id="c1b23-203">Finally, if you were storing all the event streams, you can use Microsoft Power BI or a third-party solution like Kibana or Splunk to visualize the data.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="c1b23-204">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="c1b23-204">Additional resources</span></span>

-   <span data-ttu-id="c1b23-205">**ASP.NET Core HealthChecks** (versão inicial) [ *https://github.com/aspnet/HealthChecks/*](https://github.com/aspnet/HealthChecks/)</span><span class="sxs-lookup"><span data-stu-id="c1b23-205">**ASP.NET Core HealthChecks** (early release) [*https://github.com/aspnet/HealthChecks/*](https://github.com/aspnet/HealthChecks/)</span></span>

-   <span data-ttu-id="c1b23-206">**Introdução ao monitoramento de integridade do Service Fabric**
    [*https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction*](https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction)</span><span class="sxs-lookup"><span data-stu-id="c1b23-206">**Introduction to Service Fabric health monitoring**
[*https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction*](https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction)</span></span>

-   <span data-ttu-id="c1b23-207">**Aplicativo do Azure Insights**
    [*https://azure.microsoft.com/services/application-insights/*](https://azure.microsoft.com/services/application-insights/)</span><span class="sxs-lookup"><span data-stu-id="c1b23-207">**Azure Application Insights**
[*https://azure.microsoft.com/services/application-insights/*](https://azure.microsoft.com/services/application-insights/)</span></span>

-   <span data-ttu-id="c1b23-208">**Microsoft Operations Management Suite**
    [*https://www.microsoft.com/en-us/cloud-platform/operations-management-suite*](https://www.microsoft.com/en-us/cloud-platform/operations-management-suite)</span><span class="sxs-lookup"><span data-stu-id="c1b23-208">**Microsoft Operations Management Suite**
[*https://www.microsoft.com/en-us/cloud-platform/operations-management-suite*](https://www.microsoft.com/en-us/cloud-platform/operations-management-suite)</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="c1b23-209">[Anterior] (implementar-circuito-separador-pattern.md) [Avançar] (... /Secure-NET-microservices-Web-Applications/Index.MD)</span><span class="sxs-lookup"><span data-stu-id="c1b23-209">[Previous] (implement-circuit-breaker-pattern.md) [Next] (../secure-net-microservices-web-applications/index.md)</span></span>
