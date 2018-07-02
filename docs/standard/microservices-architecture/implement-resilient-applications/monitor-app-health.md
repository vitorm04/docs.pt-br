---
title: Monitoramento de integridade
description: Arquitetura de microsserviços do .NET para aplicativos .NET em contêineres | Monitoramento de integridade
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/11/2017
ms.openlocfilehash: 62d4e9a26710a5c4b191287bf76192972f7e991b
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37106535"
---
# <a name="health-monitoring"></a><span data-ttu-id="10cd1-103">Monitoramento de integridade</span><span class="sxs-lookup"><span data-stu-id="10cd1-103">Health monitoring</span></span>

<span data-ttu-id="10cd1-104">O monitoramento de integridade pode permitir informações quase em tempo real sobre o estado de seus contêineres e microsserviços.</span><span class="sxs-lookup"><span data-stu-id="10cd1-104">Health monitoring can allow near-real-time information about the state of your containers and microservices.</span></span> <span data-ttu-id="10cd1-105">O monitoramento de integridade é fundamental para vários aspectos da operação de microsserviços e é especialmente importante quando orquestradores executam upgrades parciais de aplicativo em fases, conforme explicado posteriormente.</span><span class="sxs-lookup"><span data-stu-id="10cd1-105">Health monitoring is critical to multiple aspects of operating microservices and is especially important when orchestrators perform partial application upgrades in phases, as explained later.</span></span>

<span data-ttu-id="10cd1-106">Aplicativos baseados em microsserviços geralmente usam pulsações ou verificações de integridade para habilitar seus monitores de desempenho, agendadores e orquestradores a controlar a variedade de serviços.</span><span class="sxs-lookup"><span data-stu-id="10cd1-106">Microservices-based applications often use heartbeats or health checks to enable their performance monitors, schedulers, and orchestrators to keep track of the multitude of services.</span></span> <span data-ttu-id="10cd1-107">Se os serviços não puderem enviar algum tipo de sinal "Estou vivo", seja sob demanda ou conforme um agendamento, seu aplicativo poderá enfrentar riscos quando você implantar atualizações, ou poderá simplesmente detectar falhas tarde demais e não conseguir interromper falhas em cascata que podem terminar em grandes interrupções.</span><span class="sxs-lookup"><span data-stu-id="10cd1-107">If services cannot send some sort of “I’m alive” signal, either on demand or on a schedule, your application might face risks when you deploy updates, or it might simply detect failures too late and not be able to stop cascading failures that can end up in major outages.</span></span>

<span data-ttu-id="10cd1-108">No modelo comum, serviços enviam relatórios sobre o status, e essas informações são agregadas para fornecer uma exibição geral do estado de integridade do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="10cd1-108">In the typical model, services send reports about their status, and that information is aggregated to provide an overall view of the state of health of your application.</span></span> <span data-ttu-id="10cd1-109">Se você estiver usando um orquestrador, poderá fornecer informações de integridade para o cluster do orquestrador para que o cluster possa atuar adequadamente.</span><span class="sxs-lookup"><span data-stu-id="10cd1-109">If you are using an orchestrator, you can provide health information to your orchestrator’s cluster, so that the cluster can act accordingly.</span></span> <span data-ttu-id="10cd1-110">Se você investir em relatórios de integridade de alta qualidade personalizados para seu aplicativo, poderá detectar e corrigir problemas do seu aplicativo em execução muito mais facilmente.</span><span class="sxs-lookup"><span data-stu-id="10cd1-110">If you invest in high-quality health reporting that is customized for your application, you can detect and fix issues for your running application much more easily.</span></span>

## <a name="implementing-health-checks-in-aspnet-core-services"></a><span data-ttu-id="10cd1-111">Implementação de verificações de integridade nos serviços do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="10cd1-111">Implementing health checks in ASP.NET Core services</span></span>

<span data-ttu-id="10cd1-112">Ao desenvolver um aplicativo Web ou um microsserviço ASP.NET Core, use uma biblioteca fora de banda (não oficial como parte do ASP.NETCore) chamada `HealthChecks` da equipe do ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="10cd1-112">When developing an ASP.NET Core microservice or web application, you can use an out-of-band library (not official as part of ASP.NETCore) named `HealthChecks` from the ASP.NET team.</span></span> <span data-ttu-id="10cd1-113">Ela está disponível neste [repositório GitHub](https://github.com/dotnet-architecture/HealthChecks).</span><span class="sxs-lookup"><span data-stu-id="10cd1-113">It is available at this [GitHub repo](https://github.com/dotnet-architecture/HealthChecks).</span></span>

<span data-ttu-id="10cd1-114">Essa biblioteca é fácil de usar e fornece recursos que permitem que você valide se qualquer recurso externo específico necessário para o seu aplicativo (como um banco de dados do SQL Server ou a API remota) está funcionando corretamente.</span><span class="sxs-lookup"><span data-stu-id="10cd1-114">This library is easy to use and provides features that let you validate that any specific external resource needed for your application (like a SQL Server database or remote API) is working properly.</span></span> <span data-ttu-id="10cd1-115">Quando você usa essa biblioteca, também pode decidir o que significa o recurso estar íntegro, como explicaremos mais adiante.</span><span class="sxs-lookup"><span data-stu-id="10cd1-115">When you use this library, you can also decide what it means that the resource is healthy, as we explain later.</span></span>

<span data-ttu-id="10cd1-116">Para usar essa biblioteca, você precisa primeiro usar a biblioteca em seus microsserviços.</span><span class="sxs-lookup"><span data-stu-id="10cd1-116">In order to use this library, you need to first use the library in your microservices.</span></span> <span data-ttu-id="10cd1-117">Em segundo lugar, é necessário um aplicativo de front-end que consulte os relatórios de integridade.</span><span class="sxs-lookup"><span data-stu-id="10cd1-117">Second, you need a front-end application that queries for the health reports.</span></span> <span data-ttu-id="10cd1-118">O aplicativo de front-end pode ser um aplicativo de relatório personalizado, ou pode ser um orquestrador em si que pode reagir de acordo para os estados de integridade.</span><span class="sxs-lookup"><span data-stu-id="10cd1-118">That front end application could be a custom reporting application, or it could be an orchestrator itself that can react accordingly to the health states.</span></span>

### <a name="using-the-healthchecks-library-in-your-back-end-aspnet-microservices"></a><span data-ttu-id="10cd1-119">Usando a biblioteca de HealthChecks em seus microsserviços ASP.NET de back-end</span><span class="sxs-lookup"><span data-stu-id="10cd1-119">Using the HealthChecks library in your back end ASP.NET microservices</span></span>

<span data-ttu-id="10cd1-120">Você pode ver como a biblioteca HealthChecks é usada no aplicativo de exemplo eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="10cd1-120">You can see how the HealthChecks library is used in the eShopOnContainers sample application.</span></span> <span data-ttu-id="10cd1-121">Para começar, você precisa definir o que constitui o status íntegro para cada microsserviço.</span><span class="sxs-lookup"><span data-stu-id="10cd1-121">To begin, you need to define what constitutes a healthy status for each microservice.</span></span> <span data-ttu-id="10cd1-122">No aplicativo de exemplo, os microsserviços estão íntegros se a API de microsserviços está acessível por meio de HTTP e se o banco de dados do SQL Server relacionado também está disponível.</span><span class="sxs-lookup"><span data-stu-id="10cd1-122">In the sample application, the microservices are healthy if the microservice API is accessible via HTTP and if its related SQL Server database is also available.</span></span>

<span data-ttu-id="10cd1-123">No futuro, você poderá instalar a biblioteca de HealthChecks como um pacote do NuGet.</span><span class="sxs-lookup"><span data-stu-id="10cd1-123">In the future, you will be able to install the HealthChecks library as a NuGet package.</span></span> <span data-ttu-id="10cd1-124">Porém, no momento da redação deste artigo, você precisa baixar e compilar o código como parte da sua solução.</span><span class="sxs-lookup"><span data-stu-id="10cd1-124">But as of this writing, you need to download and compile the code as part of your solution.</span></span> <span data-ttu-id="10cd1-125">Clone o código disponível em https://github.com/dotnet-architecture/HealthChecks e copie as seguintes pastas para sua solução:</span><span class="sxs-lookup"><span data-stu-id="10cd1-125">Clone the code available at https://github.com/dotnet-architecture/HealthChecks and copy the following folders to your solution:</span></span>

  - <span data-ttu-id="10cd1-126">src/common</span><span class="sxs-lookup"><span data-stu-id="10cd1-126">src/common</span></span>
  - <span data-ttu-id="10cd1-127">src/Microsoft.AspNetCore.HealthChecks</span><span class="sxs-lookup"><span data-stu-id="10cd1-127">src/Microsoft.AspNetCore.HealthChecks</span></span>
  - <span data-ttu-id="10cd1-128">src/Microsoft.Extensions.HealthChecks</span><span class="sxs-lookup"><span data-stu-id="10cd1-128">src/Microsoft.Extensions.HealthChecks</span></span>
  - <span data-ttu-id="10cd1-129">src/Microsoft.Extensions.HealthChecks.SqlServer</span><span class="sxs-lookup"><span data-stu-id="10cd1-129">src/Microsoft.Extensions.HealthChecks.SqlServer</span></span>

<span data-ttu-id="10cd1-130">Você também pode usar verificações adicionais, como aquelas para o Azure (Microsoft.Extensions.HealthChecks.AzureStorage), mas como essa versão do eShopOnContainers não tem nenhuma dependência do Azure, não é necessário.</span><span class="sxs-lookup"><span data-stu-id="10cd1-130">You could also use additional checks like the ones for Azure (Microsoft.Extensions.HealthChecks.AzureStorage), but since this version of eShopOnContainers does not have any dependency on Azure, you do not need it.</span></span> <span data-ttu-id="10cd1-131">Você não precisa de verificações de integridade do ASP.NET, pois o eShopOnContainers está baseado no ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="10cd1-131">You do not need the ASP.NET health checks, because eShopOnContainers is based on ASP.NET Core.</span></span>

<span data-ttu-id="10cd1-132">A Figura 10-6 mostra a biblioteca HealthChecks no Visual Studio, pronta para ser usada como um bloco de construção por qualquer microsserviço.</span><span class="sxs-lookup"><span data-stu-id="10cd1-132">Figure 10-6 shows the HealthChecks library in Visual Studio, ready to be used as a building block by any microservices.</span></span>

![](./media/image6.png)

<span data-ttu-id="10cd1-133">**Figura 10-6**.</span><span class="sxs-lookup"><span data-stu-id="10cd1-133">**Figure 10-6**.</span></span> <span data-ttu-id="10cd1-134">Código-fonte da biblioteca HealthChecks do ASP.NET Core em uma solução do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="10cd1-134">ASP.NET Core HealthChecks library source code in a Visual Studio solution</span></span>

<span data-ttu-id="10cd1-135">Conforme apresentado anteriormente, a primeira coisa a fazer em cada projeto de microsserviço é adicionar uma referência às três bibliotecas HealthChecks.</span><span class="sxs-lookup"><span data-stu-id="10cd1-135">As introduced earlier, the first thing to do in each microservice project is to add a reference to the three HealthChecks libraries.</span></span> <span data-ttu-id="10cd1-136">Depois disso, você adiciona as ações de verificação de integridade que deseja executar naquele microsserviço.</span><span class="sxs-lookup"><span data-stu-id="10cd1-136">After that, you add the health check actions that you want to perform in that microservice.</span></span> <span data-ttu-id="10cd1-137">Essas ações são basicamente as dependências de outros microsserviços (HttpUrlCheck) ou bancos de dados (atualmente SqlCheck\* para bancos de dados do SQL Server).</span><span class="sxs-lookup"><span data-stu-id="10cd1-137">These actions are basically dependencies on other microservices (HttpUrlCheck) or databases (currently SqlCheck\* for SQL Server databases).</span></span> <span data-ttu-id="10cd1-138">Você adiciona a ação dentro da classe de Inicialização de cada microsserviço ASP.NET ou aplicativo Web ASP .NET.</span><span class="sxs-lookup"><span data-stu-id="10cd1-138">You add the action within the Startup class of each ASP.NET microservice or ASP.NET web application.</span></span>

<span data-ttu-id="10cd1-139">Cada serviço ou aplicativo Web deve ser configurado com a adição de todas as suas dependências HTTP ou do banco de dados como um método AddHealthCheck.</span><span class="sxs-lookup"><span data-stu-id="10cd1-139">Each service or web application should be configured by adding all its HTTP or database dependencies as one AddHealthCheck method.</span></span> <span data-ttu-id="10cd1-140">Por exemplo, o aplicativo Web MVC de eShopOnContainers depende de muitos serviços, portanto, tem vários métodos AddCheck adicionados às verificações de integridade.</span><span class="sxs-lookup"><span data-stu-id="10cd1-140">For example, the MVC web application from eShopOnContainers depends on many services, therefore has several AddCheck methods added to the health checks.</span></span>

<span data-ttu-id="10cd1-141">Por exemplo, no código a seguir, você pode ver como o microsserviço de catálogo adiciona uma dependência no seu banco de dados do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="10cd1-141">For instance, in the following code you can see how the catalog microservice adds a dependency on its SQL Server database.</span></span>

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

<span data-ttu-id="10cd1-142">No entanto, o aplicativo Web MVC do eShopOnContainers tem várias dependências de outros microsserviços.</span><span class="sxs-lookup"><span data-stu-id="10cd1-142">However, the MVC web application of eShopOnContainers has multiple dependencies on the rest of the microservices.</span></span> <span data-ttu-id="10cd1-143">Portanto, ele chama um método AddUrlCheck para cada microsserviço, conforme mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="10cd1-143">Therefore, it calls one AddUrlCheck method for each microservice, as shown in the following example:</span></span>

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

<span data-ttu-id="10cd1-144">Assim, um microsserviço não fornecerá um status "íntegro" até que todas as suas verificações também estejam íntegras.</span><span class="sxs-lookup"><span data-stu-id="10cd1-144">Thus, a microservice will not provide a “healthy” status until all its checks are healthy as well.</span></span>

<span data-ttu-id="10cd1-145">Se o microsserviço não tiver uma dependência de um serviço ou do SQL Server, você deverá adicionar apenas uma verificação de Healthy("Ok").</span><span class="sxs-lookup"><span data-stu-id="10cd1-145">If the microservice does not have a dependency on a service or on SQL Server, you should just add a Healthy("Ok") check.</span></span> <span data-ttu-id="10cd1-146">O código a seguir é do microsserviço basket.api de eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="10cd1-146">The following code is from the eShopOnContainers basket.api microservice.</span></span> <span data-ttu-id="10cd1-147">(O microsserviço de cesta usa o Cache Redis, mas a biblioteca ainda não inclui um provedor de verificação de integridade do Redis.)</span><span class="sxs-lookup"><span data-stu-id="10cd1-147">(The basket microservice uses the Redis cache, but the library does not yet include a Redis health check provider.)</span></span>

```csharp
services.AddHealthChecks(checks =>
{
    checks.AddValueTaskCheck("HTTP Endpoint", () => new
        ValueTask<IHealthCheckResult>(HealthCheckResult.Healthy("Ok")));
});
```

<span data-ttu-id="10cd1-148">Para um serviço ou aplicativo Web expor o ponto de extremidade de verificação de integridade, ele deverá habilitar o método de extensão UseHealthChecks(\[*url\_for\_health\_checks*\]).</span><span class="sxs-lookup"><span data-stu-id="10cd1-148">For a service or web application to expose the health check endpoint, it has to enable the UseHealthChecks(\[*url\_for\_health\_checks*\]) extension method.</span></span> <span data-ttu-id="10cd1-149">Esse método vai no nível do WebHostBuilder no método principal da classe Programa do seu serviço ASP.NET Core ou aplicativo Web, logo após UseKestrel, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="10cd1-149">This method goes at the WebHostBuilder level in the main method of the Program class of your ASP.NET Core service or web application, right after UseKestrel as shown in the code below.</span></span>

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

<span data-ttu-id="10cd1-150">O processo funciona da seguinte maneira: cada microsserviço expõe o ponto de extremidade /hc.</span><span class="sxs-lookup"><span data-stu-id="10cd1-150">The process works like this: each microservice exposes the endpoint /hc.</span></span> <span data-ttu-id="10cd1-151">Esse ponto de extremidade é criado pela biblioteca HealthChecks do middleware ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="10cd1-151">That endpoint is created by the HealthChecks library ASP.NET Core middleware.</span></span> <span data-ttu-id="10cd1-152">Quando esse ponto de extremidade é invocado, ele executa todas as verificações de integridade configuradas no método AddHealthChecks na classe de Inicialização.</span><span class="sxs-lookup"><span data-stu-id="10cd1-152">When that endpoint is invoked, it runs all the health checks that are configured in the AddHealthChecks method in the Startup class.</span></span>

<span data-ttu-id="10cd1-153">O método UseHealthChecks espera uma porta ou um caminho.</span><span class="sxs-lookup"><span data-stu-id="10cd1-153">The UseHealthChecks method expects a port or a path.</span></span> <span data-ttu-id="10cd1-154">Essa porta ou caminho é o ponto de extremidade a ser usado para verificar o estado de integridade do serviço.</span><span class="sxs-lookup"><span data-stu-id="10cd1-154">That port or path is the endpoint to use to check the health state of the service.</span></span> <span data-ttu-id="10cd1-155">Por exemplo, o catálogo microsserviço usa o caminho /hc.</span><span class="sxs-lookup"><span data-stu-id="10cd1-155">For instance, the catalog microservice uses the path /hc.</span></span>

### <a name="caching-health-check-responses"></a><span data-ttu-id="10cd1-156">Armazenando em cache as respostas de verificação de integridade</span><span class="sxs-lookup"><span data-stu-id="10cd1-156">Caching health check responses</span></span>

<span data-ttu-id="10cd1-157">Uma vez que você não deseja causar uma DoS (Negação de Serviço) nos seus serviços, ou simplesmente não desejar afetar o desempenho do serviço verificando recursos com muita frequência, você pode armazenar em cache os retornos e configurar uma duração de cache para cada verificação de integridade.</span><span class="sxs-lookup"><span data-stu-id="10cd1-157">Since you do not want to cause a Denial of Service (DoS) in your services, or you simply do not want to impact service performance by checking resources too frequently, you can cache the returns and configure a cache duration for each health check.</span></span>

<span data-ttu-id="10cd1-158">Por padrão, a duração do cache está definida internamente como 5 minutos, mas você pode alterar essa duração do cache em cada verificação de integridade, como no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="10cd1-158">By default, the cache duration is internally set to 5 minutes, but you can change that cache duration on each health check, as in the following code:</span></span>

```csharp
checks.AddUrlCheck(Configuration["CatalogUrl"],1); // 1 min as cache duration
```

### <a name="querying-your-microservices-to-report-about-their-health-status"></a><span data-ttu-id="10cd1-159">Consultando seus microsserviços para relatar sobre o status da integridade</span><span class="sxs-lookup"><span data-stu-id="10cd1-159">Querying your microservices to report about their health status</span></span>

<span data-ttu-id="10cd1-160">Quando você tiver configurado as verificações de integridade, conforme descrito aqui, quando o microsserviço estiver em execução no Docker, você poderá verificar diretamente de um navegador se ele estiver íntegro.</span><span class="sxs-lookup"><span data-stu-id="10cd1-160">When you have configured health checks as described here, once the microservice is running in Docker, you can directly check from a browser if it is healthy.</span></span> <span data-ttu-id="10cd1-161">(Isso requer que você esteja publicando a porta do contêiner do host do Docker para que possa acessar o contêiner por meio de localhost ou pelo IP de host externo do Docker.) A Figura 10-7 mostra uma solicitação em um navegador e as respostas correspondentes.</span><span class="sxs-lookup"><span data-stu-id="10cd1-161">(This does require that you are publishing the container port out of the Docker host, so you can access the container through localhost or through the external Docker host IP.) Figure 10-7 shows a request in a browser and the corresponding response.</span></span>

![](./media/image7.png)

<span data-ttu-id="10cd1-162">**Figura 10-7**.</span><span class="sxs-lookup"><span data-stu-id="10cd1-162">**Figure 10-7**.</span></span> <span data-ttu-id="10cd1-163">Verificando o status da integridade de um único serviço em um navegador</span><span class="sxs-lookup"><span data-stu-id="10cd1-163">Checking health status of a single service from a browser</span></span>

<span data-ttu-id="10cd1-164">No teste, você pode ver que o microsserviço catalog.api (em execução na porta 5101) está íntegro, retornando o status HTTP 200 e informações de status em JSON.</span><span class="sxs-lookup"><span data-stu-id="10cd1-164">In that test, you can see that the catalog.api microservice (running on port 5101) is healthy, returning HTTP status 200 and status information in JSON.</span></span> <span data-ttu-id="10cd1-165">Isso significa, ainda, que o serviço também verificou internamente a integridade de sua dependência do banco de dados do SQL Server e que a verificação de integridade relatou a si própria como íntegra.</span><span class="sxs-lookup"><span data-stu-id="10cd1-165">It also means that internally the service also checked the health of its SQL Server database dependency and that health check was reported itself as healthy.</span></span>

## <a name="using-watchdogs"></a><span data-ttu-id="10cd1-166">Usando watchdogs</span><span class="sxs-lookup"><span data-stu-id="10cd1-166">Using watchdogs</span></span>

<span data-ttu-id="10cd1-167">Um watchdog é um serviço separado que pode inspecionar a integridade e a carga entre serviços e relatar a integridade sobre os microsserviços consultando a biblioteca HealthChecks apresentada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="10cd1-167">A watchdog is a separate service that can watch health and load across services, and report health about the microservices by querying with the HealthChecks library introduced earlier.</span></span> <span data-ttu-id="10cd1-168">Isso pode ajudar a evitar erros que não seriam detectados com base no modo de exibição de um único serviço.</span><span class="sxs-lookup"><span data-stu-id="10cd1-168">This can help prevent errors that would not be detected based on the view of a single service.</span></span> <span data-ttu-id="10cd1-169">Watchdogs também são um bom lugar para hospedar código que pode realizar ações de correção para condições conhecidas sem interação do usuário.</span><span class="sxs-lookup"><span data-stu-id="10cd1-169">Watchdogs also are a good place to host code that can perform remediation actions for known conditions without user interaction.</span></span>

<span data-ttu-id="10cd1-170">O exemplo de eShopOnContainers contém uma página da Web que exibe os relatórios de verificação de integridade de exemplo, conforme mostra a Figura 10-8.</span><span class="sxs-lookup"><span data-stu-id="10cd1-170">The eShopOnContainers sample contains a web page that displays sample health check reports, as shown in Figure 10-8.</span></span> <span data-ttu-id="10cd1-171">Este é o watchdog mais simples que você pode ter, já que ele simplesmente mostra o estado dos aplicativos Web e dos microsserviços em eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="10cd1-171">This is the simplest watchdog you could have, since all it does is shows the state of the microservices and web applications in eShopOnContainers.</span></span> <span data-ttu-id="10cd1-172">Geralmente, um watchdog também executa ações quando detecta estados não íntegro.</span><span class="sxs-lookup"><span data-stu-id="10cd1-172">Usually a watchdog also takes actions when it detects unhealthy states.</span></span>

![](./media/image8.png)

<span data-ttu-id="10cd1-173">**Figura 10-8**.</span><span class="sxs-lookup"><span data-stu-id="10cd1-173">**Figure 10-8**.</span></span> <span data-ttu-id="10cd1-174">Relatório de verificação de integridade de exemplo em eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="10cd1-174">Sample health check report in eShopOnContainers</span></span>

<span data-ttu-id="10cd1-175">Em resumo, o middleware ASP.NET da biblioteca HealthChecks do ASP.NET Core fornece um ponto de extremidade de verificação de integridade único para cada microsserviço.</span><span class="sxs-lookup"><span data-stu-id="10cd1-175">In summary, the ASP.NET middleware of the ASP.NET Core HealthChecks library provides a single health check endpoint for each microservice.</span></span> <span data-ttu-id="10cd1-176">Isso executará todas as verificações de integridade definidas dentro dele e retornará um estado de integridade geral dependendo todas essas verificações.</span><span class="sxs-lookup"><span data-stu-id="10cd1-176">This will execute all the health checks defined within it and return an overall health state depending on all those checks.</span></span>

<span data-ttu-id="10cd1-177">A biblioteca HealthChecks é extensível via novas verificações de integridade dos futuros recursos externos.</span><span class="sxs-lookup"><span data-stu-id="10cd1-177">The HealthChecks library is extensible through new health checks of future external resources.</span></span> <span data-ttu-id="10cd1-178">Por exemplo, esperamos que no futuro a biblioteca tenha verificações de integridade para o Cache Redis e para outros bancos de dados.</span><span class="sxs-lookup"><span data-stu-id="10cd1-178">For example, we expect that in the future the library will have health checks for Redis cache and for other databases.</span></span> <span data-ttu-id="10cd1-179">A biblioteca permite relatório de integridade por várias dependências de aplicativo ou serviço, e você pode executar as ações com base nessas verificações de integridade.</span><span class="sxs-lookup"><span data-stu-id="10cd1-179">The library allows health reporting by multiple service or application dependencies, and you can then take actions based on those health checks.</span></span>

## <a name="health-checks-when-using-orchestrators"></a><span data-ttu-id="10cd1-180">Verificações de integridade ao usar orquestradores</span><span class="sxs-lookup"><span data-stu-id="10cd1-180">Health checks when using orchestrators</span></span>

<span data-ttu-id="10cd1-181">Para monitorar a disponibilidade de seus microsserviços, orquestradores como Docker Swarm, Kubernetes e Service Fabric periodicamente realizam verificações de integridade enviando solicitações para testar os microsserviços.</span><span class="sxs-lookup"><span data-stu-id="10cd1-181">To monitor the availability of your microservices, orchestrators like Docker Swarm, Kubernetes, and Service Fabric periodically perform health checks by sending requests to test the microservices.</span></span> <span data-ttu-id="10cd1-182">Quando um orquestrador determina que um serviço/contêiner não está íntegro, ele para de rotear solicitações para aquela instância.</span><span class="sxs-lookup"><span data-stu-id="10cd1-182">When an orchestrator determines that a service/container is unhealthy, it stops routing requests to that instance.</span></span> <span data-ttu-id="10cd1-183">Ele também geralmente cria uma nova instância do contêiner.</span><span class="sxs-lookup"><span data-stu-id="10cd1-183">It also usually creates a new instance of that container.</span></span>

<span data-ttu-id="10cd1-184">Por exemplo, a maioria dos orquestradores pode usar verificações de integridade para gerenciar implantações de tempo de inatividade zero.</span><span class="sxs-lookup"><span data-stu-id="10cd1-184">For instance, most orchestrators can use health checks to manage zero-downtime deployments.</span></span> <span data-ttu-id="10cd1-185">Somente quando o status de um serviço/contêiner é alterado para íntegro o orquestrador começa a rotear o tráfego para instâncias de serviço/contêiner.</span><span class="sxs-lookup"><span data-stu-id="10cd1-185">Only when the status of a service/container changes to healthy will the orchestrator start routing traffic to service/container instances.</span></span>

<span data-ttu-id="10cd1-186">O monitoramento de integridade é especialmente importante quando um orquestrador executa uma atualização do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="10cd1-186">Health monitoring is especially important when an orchestrator performs an application upgrade.</span></span> <span data-ttu-id="10cd1-187">Alguns orquestradores (como o Azure Service Fabric) atualizam os serviços em fases, por exemplo, podem atualizar um quinto da superfície de cluster para cada upgrade de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="10cd1-187">Some orchestrators (like Azure Service Fabric) update services in phases—for example, they might update one-fifth of the cluster surface for each application upgrade.</span></span> <span data-ttu-id="10cd1-188">O conjunto de nós que é atualizado ao mesmo tempo é referido como um *domínio de atualização*.</span><span class="sxs-lookup"><span data-stu-id="10cd1-188">The set of nodes that is upgraded at the same time is referred to as an *upgrade domain*.</span></span> <span data-ttu-id="10cd1-189">Depois de cada domínio de atualização ter sido atualizado e estar disponível para os usuários, esse domínio de atualização deverá passar por verificações de integridade antes que a implantação passe para o próximo domínio de atualização.</span><span class="sxs-lookup"><span data-stu-id="10cd1-189">After each upgrade domain has been upgraded and is available to users, that upgrade domain must pass health checks before the deployment moves to the next upgrade domain.</span></span>

<span data-ttu-id="10cd1-190">Outro aspecto da integridade de serviço são as métricas de relatório do serviço.</span><span class="sxs-lookup"><span data-stu-id="10cd1-190">Another aspect of service health is reporting metrics from the service.</span></span> <span data-ttu-id="10cd1-191">Este é uma funcionalidade avançada do modelo de integridade de alguns orquestradores, como o Service Fabric.</span><span class="sxs-lookup"><span data-stu-id="10cd1-191">This is an advanced capability of the health model of some orchestrators, like Service Fabric.</span></span> <span data-ttu-id="10cd1-192">As métricas são importantes ao usar um orquestrador, pois elas são usadas para equilibrar o uso de recursos.</span><span class="sxs-lookup"><span data-stu-id="10cd1-192">Metrics are important when using an orchestrator because they are used to balance resource usage.</span></span> <span data-ttu-id="10cd1-193">As métricas também podem ser um indicador de integridade do sistema.</span><span class="sxs-lookup"><span data-stu-id="10cd1-193">Metrics also can be an indicator of system health.</span></span> <span data-ttu-id="10cd1-194">Por exemplo, você pode ter um aplicativo com muitos microsserviços, e cada instância relata uma métrica de RPS (solicitações por segundo).</span><span class="sxs-lookup"><span data-stu-id="10cd1-194">For example, you might have an application that has many microservices, and each instance reports a requests-per-second (RPS) metric.</span></span> <span data-ttu-id="10cd1-195">Se um serviço estiver usando mais recursos (memória, processador etc.) que outro, o orquestrador poderá mover instâncias de serviço do cluster para tentar manter até mesmo a utilização de recursos.</span><span class="sxs-lookup"><span data-stu-id="10cd1-195">If one service is using more resources (memory, processor, etc.) than another service, the orchestrator could move service instances around in the cluster to try to maintain even resource utilization.</span></span>

<span data-ttu-id="10cd1-196">Observe que se você estiver usando o Azure Service Fabric, ele fornecerá seu próprio [modelo de Monitoramento de Integridade](https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction), que é mais avançada do que simples verificações de integridade.</span><span class="sxs-lookup"><span data-stu-id="10cd1-196">Note that if you are using Azure Service Fabric, it provides its own [Health Monitoring model](https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction), which is more advanced than simple health checks.</span></span>

## <a name="advanced-monitoring-visualization-analysis-and-alerts"></a><span data-ttu-id="10cd1-197">Monitoramento avançado: visualização, análise e alertas</span><span class="sxs-lookup"><span data-stu-id="10cd1-197">Advanced monitoring: visualization, analysis, and alerts</span></span>

<span data-ttu-id="10cd1-198">A parte final do monitoramento é visualizar o fluxo de eventos, relatar o desempenho do serviço e alertar quando for detectado um problema.</span><span class="sxs-lookup"><span data-stu-id="10cd1-198">The final part of monitoring is visualizing the event stream, reporting on service performance, and alerting when an issue is detected.</span></span> <span data-ttu-id="10cd1-199">Você pode usar diferentes soluções para esse aspecto do monitoramento.</span><span class="sxs-lookup"><span data-stu-id="10cd1-199">You can use different solutions for this aspect of monitoring.</span></span>

<span data-ttu-id="10cd1-200">Você pode usar aplicativos personalizados simples que mostrem o estado de seus serviços, como a página personalizada que mostramos ao explicar o [ASP.NET Core HealthChecks](https://github.com/aspnet/HealthChecks).</span><span class="sxs-lookup"><span data-stu-id="10cd1-200">You can use simple custom applications showing the state of your services, like the custom page we showed when we explained [ASP.NET Core HealthChecks](https://github.com/aspnet/HealthChecks).</span></span> <span data-ttu-id="10cd1-201">Ou você pode usar as ferramentas mais avançadas, como Azure Application Insights e Operations Management Suite para gerar alertas com base em fluxo de eventos.</span><span class="sxs-lookup"><span data-stu-id="10cd1-201">Or you could use more advanced tools like Azure Application Insights and Operations Management Suite to raise alerts based on the stream of events.</span></span>

<span data-ttu-id="10cd1-202">Por fim, se você estava armazenando todos os fluxos de eventos, pode usar Microsoft Power BI ou uma solução de terceiros, como Kibana ou Splunk, para visualizar os dados.</span><span class="sxs-lookup"><span data-stu-id="10cd1-202">Finally, if you were storing all the event streams, you can use Microsoft Power BI or a third-party solution like Kibana or Splunk to visualize the data.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="10cd1-203">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="10cd1-203">Additional resources</span></span>

-   <span data-ttu-id="10cd1-204">**ASP.NET Core HealthChecks** (versão inicial) [*https://github.com/aspnet/HealthChecks/*](https://github.com/aspnet/HealthChecks/)</span><span class="sxs-lookup"><span data-stu-id="10cd1-204">**ASP.NET Core HealthChecks** (early release) [*https://github.com/aspnet/HealthChecks/*](https://github.com/aspnet/HealthChecks/)</span></span>

-   <span data-ttu-id="10cd1-205">**Introdução ao monitoramento de integridade do Service Fabric**
    [*https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction*](https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction)</span><span class="sxs-lookup"><span data-stu-id="10cd1-205">**Introduction to Service Fabric health monitoring**
[*https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction*](https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction)</span></span>

-   <span data-ttu-id="10cd1-206">**Azure Application Insights**
    [*https://azure.microsoft.com/services/application-insights/*](https://azure.microsoft.com/services/application-insights/)</span><span class="sxs-lookup"><span data-stu-id="10cd1-206">**Azure Application Insights**
[*https://azure.microsoft.com/services/application-insights/*](https://azure.microsoft.com/services/application-insights/)</span></span>

-   <span data-ttu-id="10cd1-207">**Microsoft Operations Management Suite**
    [*https://www.microsoft.com/en-us/cloud-platform/operations-management-suite*](https://www.microsoft.com/en-us/cloud-platform/operations-management-suite)</span><span class="sxs-lookup"><span data-stu-id="10cd1-207">**Microsoft Operations Management Suite**
[*https://www.microsoft.com/en-us/cloud-platform/operations-management-suite*](https://www.microsoft.com/en-us/cloud-platform/operations-management-suite)</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="10cd1-208">[Anterior](implement-circuit-breaker-pattern.md)
[Próximo](../secure-net-microservices-web-applications/index.md)</span><span class="sxs-lookup"><span data-stu-id="10cd1-208">[Previous](implement-circuit-breaker-pattern.md)
[Next](../secure-net-microservices-web-applications/index.md)</span></span>
