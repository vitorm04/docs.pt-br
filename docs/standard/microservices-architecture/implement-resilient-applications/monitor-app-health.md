---
title: Monitoramento de integridade
description: Explore uma maneira de implementar o monitoramento de integridade.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/16/2018
ms.openlocfilehash: 666b55608ca4e5d18448e1a0b4a1735f3e856474
ms.sourcegitcommit: 542aa405b295955eb055765f33723cb8b588d0d0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2019
ms.locfileid: "54362477"
---
# <a name="health-monitoring"></a><span data-ttu-id="1580a-103">Monitoramento de integridade</span><span class="sxs-lookup"><span data-stu-id="1580a-103">Health monitoring</span></span>

<span data-ttu-id="1580a-104">O monitoramento de integridade pode permitir informações quase em tempo real sobre o estado de seus contêineres e microsserviços.</span><span class="sxs-lookup"><span data-stu-id="1580a-104">Health monitoring can allow near-real-time information about the state of your containers and microservices.</span></span> <span data-ttu-id="1580a-105">O monitoramento de integridade é fundamental para vários aspectos da operação de microsserviços e é especialmente importante quando orquestradores executam upgrades parciais de aplicativo em fases, conforme explicado posteriormente.</span><span class="sxs-lookup"><span data-stu-id="1580a-105">Health monitoring is critical to multiple aspects of operating microservices and is especially important when orchestrators perform partial application upgrades in phases, as explained later.</span></span>

<span data-ttu-id="1580a-106">Aplicativos baseados em microsserviços geralmente usam pulsações ou verificações de integridade para habilitar seus monitores de desempenho, agendadores e orquestradores a controlar a variedade de serviços.</span><span class="sxs-lookup"><span data-stu-id="1580a-106">Microservices-based applications often use heartbeats or health checks to enable their performance monitors, schedulers, and orchestrators to keep track of the multitude of services.</span></span> <span data-ttu-id="1580a-107">Se os serviços não puderem enviar algum tipo de sinal "Estou ativo", seja sob demanda ou conforme um agendamento, seu aplicativo poderá enfrentar riscos quando você implantar atualizações ou poderá simplesmente detectar falhas tarde demais e não conseguir interromper falhas em cascata que possam levar a grandes interrupções.</span><span class="sxs-lookup"><span data-stu-id="1580a-107">If services cannot send some sort of “I’m alive” signal, either on demand or on a schedule, your application might face risks when you deploy updates, or it might just detect failures too late and not be able to stop cascading failures that can end up in major outages.</span></span>

<span data-ttu-id="1580a-108">No modelo comum, serviços enviam relatórios sobre o status, e essas informações são agregadas para fornecer uma exibição geral do estado de integridade do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1580a-108">In the typical model, services send reports about their status, and that information is aggregated to provide an overall view of the state of health of your application.</span></span> <span data-ttu-id="1580a-109">Se você estiver usando um orquestrador, poderá fornecer informações de integridade para o cluster do orquestrador para que o cluster possa atuar adequadamente.</span><span class="sxs-lookup"><span data-stu-id="1580a-109">If you're using an orchestrator, you can provide health information to your orchestrator’s cluster, so that the cluster can act accordingly.</span></span> <span data-ttu-id="1580a-110">Se você investir em relatórios de integridade de alta qualidade personalizados para seu aplicativo, poderá detectar e corrigir problemas do aplicativo em execução com muito mais facilidade.</span><span class="sxs-lookup"><span data-stu-id="1580a-110">If you invest in high-quality health reporting that's customized for your application, you can detect and fix issues for your running application much more easily.</span></span>

## <a name="implement-health-checks-in-aspnet-core-services"></a><span data-ttu-id="1580a-111">Implementar verificações de integridade nos serviços do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="1580a-111">Implement health checks in ASP.NET Core services</span></span>

<span data-ttu-id="1580a-112">Ao desenvolver um aplicativo Web ou de microsserviço do ASP.NET Core, você pode usar uma biblioteca fora de banda experimental (não a oficial do ASP.NETCore e agora preterida) chamada *Verificações de Integridade* da equipe do ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="1580a-112">When developing an ASP.NET Core microservice or web application, you can use an experimental out-of-band library (not official as part of ASP.NETCore and now deprecated) named *Health Checks* from the ASP.NET team.</span></span> <span data-ttu-id="1580a-113">Ela está disponível no [repositório do dotnet-architecture do GitHub](https://github.com/dotnet-architecture/HealthChecks).</span><span class="sxs-lookup"><span data-stu-id="1580a-113">It's available at this [dotnet-architecture GitHub repository](https://github.com/dotnet-architecture/HealthChecks).</span></span> <span data-ttu-id="1580a-114">No entanto, a versão oficial da biblioteca *Verificações de Integridade* [foi lançada no ASP.NET Core 2.2](https://github.com/aspnet/Announcements/issues/307) (oficialmente no final de 2018).</span><span class="sxs-lookup"><span data-stu-id="1580a-114">However, the official version of *Health Checks* [will be released in ASP.NET Core 2.2](https://github.com/aspnet/Announcements/issues/307) (Should be officially released by the end of 2018).</span></span>

<span data-ttu-id="1580a-115">Essa biblioteca é fácil de usar e fornece recursos que permitem que você valide se qualquer recurso externo específico necessário para o seu aplicativo (como um banco de dados do SQL Server ou a API remota) está funcionando corretamente.</span><span class="sxs-lookup"><span data-stu-id="1580a-115">This library is easy to use and provides features that let you validate that any specific external resource needed for your application (like a SQL Server database or remote API) is working properly.</span></span> <span data-ttu-id="1580a-116">Quando você usa essa biblioteca, também pode decidir o que significa o recurso estar íntegro, como explicaremos mais adiante.</span><span class="sxs-lookup"><span data-stu-id="1580a-116">When you use this library, you can also decide what it means that the resource is healthy, as we explain later.</span></span>

<span data-ttu-id="1580a-117">Para usar essa biblioteca, você precisa primeiro usar a biblioteca em seus microsserviços.</span><span class="sxs-lookup"><span data-stu-id="1580a-117">In order to use this library, you need to first use the library in your microservices.</span></span> <span data-ttu-id="1580a-118">Em segundo lugar, é necessário um aplicativo de front-end que consulte os relatórios de integridade.</span><span class="sxs-lookup"><span data-stu-id="1580a-118">Second, you need a front-end application that queries for the health reports.</span></span> <span data-ttu-id="1580a-119">O aplicativo de front-end pode ser um aplicativo de relatório personalizado ou um orquestrador em si que pode reagir de acordo com os estados de integridade.</span><span class="sxs-lookup"><span data-stu-id="1580a-119">That front-end application could be a custom reporting application, or it could be an orchestrator itself that can react accordingly to the health states.</span></span>

### <a name="use-the-healthchecks-library-in-your-back-end-aspnet-microservices"></a><span data-ttu-id="1580a-120">Usar a biblioteca HealthChecks em seus microsserviços de back-end do ASP.NET</span><span class="sxs-lookup"><span data-stu-id="1580a-120">Use the HealthChecks library in your back-end ASP.NET microservices</span></span>

<span data-ttu-id="1580a-121">Você pode ver como a biblioteca HealthChecks é usada no aplicativo de exemplo eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="1580a-121">You can see how the HealthChecks library is used in the eShopOnContainers sample application.</span></span> <span data-ttu-id="1580a-122">Para começar, você precisa definir o que constitui o status íntegro para cada microsserviço.</span><span class="sxs-lookup"><span data-stu-id="1580a-122">To begin, you need to define what constitutes a healthy status for each microservice.</span></span> <span data-ttu-id="1580a-123">No aplicativo de exemplo, os microsserviços estão íntegros se a API de microsserviços está acessível por meio de HTTP e se o banco de dados do SQL Server relacionado também está disponível.</span><span class="sxs-lookup"><span data-stu-id="1580a-123">In the sample application, the microservices are healthy if the microservice API is accessible via HTTP and if its related SQL Server database is also available.</span></span>

<span data-ttu-id="1580a-124">No futuro, você poderá instalar a biblioteca HealthChecks como um pacote NuGet.</span><span class="sxs-lookup"><span data-stu-id="1580a-124">In the future, you'll be able to install the HealthChecks library as a NuGet package.</span></span> <span data-ttu-id="1580a-125">Porém, no momento da redação deste artigo, você precisa baixar e compilar o código como parte da sua solução.</span><span class="sxs-lookup"><span data-stu-id="1580a-125">But as of this writing, you need to download and compile the code as part of your solution.</span></span> <span data-ttu-id="1580a-126">Clone o código disponível em <https://github.com/dotnet-architecture/HealthChecks> e copie as seguintes pastas para sua solução:</span><span class="sxs-lookup"><span data-stu-id="1580a-126">Clone the code available at <https://github.com/dotnet-architecture/HealthChecks> and copy the following folders to your solution:</span></span>

- <span data-ttu-id="1580a-127">src/common</span><span class="sxs-lookup"><span data-stu-id="1580a-127">src/common</span></span>
- <span data-ttu-id="1580a-128">src/Microsoft.AspNetCore.HealthChecks</span><span class="sxs-lookup"><span data-stu-id="1580a-128">src/Microsoft.AspNetCore.HealthChecks</span></span>
- <span data-ttu-id="1580a-129">src/Microsoft.Extensions.HealthChecks</span><span class="sxs-lookup"><span data-stu-id="1580a-129">src/Microsoft.Extensions.HealthChecks</span></span>
- <span data-ttu-id="1580a-130">src/Microsoft.Extensions.HealthChecks.SqlServer</span><span class="sxs-lookup"><span data-stu-id="1580a-130">src/Microsoft.Extensions.HealthChecks.SqlServer</span></span>

<span data-ttu-id="1580a-131">Você também pode usar verificações adicionais, como aquelas para o Azure (Microsoft.Extensions.HealthChecks.AzureStorage), mas como essa versão do eShopOnContainers não tem nenhuma dependência do Azure, não é necessário.</span><span class="sxs-lookup"><span data-stu-id="1580a-131">You could also use additional checks like the ones for Azure (Microsoft.Extensions.HealthChecks.AzureStorage), but since this version of eShopOnContainers does not have any dependency on Azure, you do not need it.</span></span> <span data-ttu-id="1580a-132">Você não precisa de verificações de integridade do ASP.NET, pois o eShopOnContainers está baseado no ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="1580a-132">You do not need the ASP.NET health checks, because eShopOnContainers is based on ASP.NET Core.</span></span>

<span data-ttu-id="1580a-133">A Figura 8-7 mostra a biblioteca HealthChecks no Visual Studio, pronta para ser usada como um bloco de construção por qualquer microsserviço.</span><span class="sxs-lookup"><span data-stu-id="1580a-133">Figure 8-7 shows the HealthChecks library in Visual Studio, ready to be used as a building block by any microservices.</span></span>

![Exibição do Gerenciador de Soluções da pasta HealthChecks, mostrando os três projetos.](./media/image6.png)

<span data-ttu-id="1580a-135">**Figura 8-7**.</span><span class="sxs-lookup"><span data-stu-id="1580a-135">**Figure 8-7**.</span></span> <span data-ttu-id="1580a-136">Código-fonte da biblioteca HealthChecks do ASP.NET Core em uma solução do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="1580a-136">ASP.NET Core HealthChecks library source code in a Visual Studio solution</span></span>

<span data-ttu-id="1580a-137">Conforme apresentado anteriormente, a primeira coisa a fazer em cada projeto de microsserviço é adicionar uma referência às três bibliotecas HealthChecks.</span><span class="sxs-lookup"><span data-stu-id="1580a-137">As introduced earlier, the first thing to do in each microservice project is to add a reference to the three HealthChecks libraries.</span></span> <span data-ttu-id="1580a-138">Depois disso, você adiciona as ações de verificação de integridade que deseja executar naquele microsserviço.</span><span class="sxs-lookup"><span data-stu-id="1580a-138">After that, you add the health check actions that you want to perform in that microservice.</span></span> <span data-ttu-id="1580a-139">Essas ações são basicamente as dependências de outros microsserviços (HttpUrlCheck) ou bancos de dados (atualmente SqlCheck\* para bancos de dados do SQL Server).</span><span class="sxs-lookup"><span data-stu-id="1580a-139">These actions are basically dependencies on other microservices (HttpUrlCheck) or databases (currently SqlCheck\* for SQL Server databases).</span></span> <span data-ttu-id="1580a-140">Você adiciona a ação dentro da classe de Inicialização de cada microsserviço ASP.NET ou aplicativo Web ASP .NET.</span><span class="sxs-lookup"><span data-stu-id="1580a-140">You add the action within the Startup class of each ASP.NET microservice or ASP.NET web application.</span></span>

<span data-ttu-id="1580a-141">Cada serviço ou aplicativo Web deve ser configurado com a adição de todas as suas dependências HTTP ou do banco de dados como um método AddHealthCheck.</span><span class="sxs-lookup"><span data-stu-id="1580a-141">Each service or web application should be configured by adding all its HTTP or database dependencies as one AddHealthCheck method.</span></span> <span data-ttu-id="1580a-142">Por exemplo, o aplicativo Web MVC de eShopOnContainers depende de muitos serviços, portanto, tem vários métodos AddCheck adicionados às verificações de integridade.</span><span class="sxs-lookup"><span data-stu-id="1580a-142">For example, the MVC web application from eShopOnContainers depends on many services, therefore has several AddCheck methods added to the health checks.</span></span>

<span data-ttu-id="1580a-143">Por exemplo, no código a seguir (simplificado), veja como o microsserviço de catálogo adiciona uma dependência no banco de dados do SQL Server dele.</span><span class="sxs-lookup"><span data-stu-id="1580a-143">For instance, in the following (simplified) code you can see how the catalog microservice adds a dependency on its SQL Server database.</span></span>

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

<span data-ttu-id="1580a-144">No entanto, o aplicativo Web MVC do eShopOnContainers tem várias dependências de outros microsserviços.</span><span class="sxs-lookup"><span data-stu-id="1580a-144">However, the MVC web application of eShopOnContainers has multiple dependencies on the rest of the microservices.</span></span> <span data-ttu-id="1580a-145">Portanto, ele chama um método AddUrlCheck para cada microsserviço, como mostra o seguinte exemplo (simplificado):</span><span class="sxs-lookup"><span data-stu-id="1580a-145">Therefore, it calls one AddUrlCheck method for each microservice, as shown in the following (simplified) example:</span></span>

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

<span data-ttu-id="1580a-146">Assim, um microsserviço não fornecerá um status "íntegro" até que todas as suas verificações também estejam íntegras.</span><span class="sxs-lookup"><span data-stu-id="1580a-146">Thus, a microservice will not provide a “healthy” status until all its checks are healthy as well.</span></span>

<span data-ttu-id="1580a-147">Se o microsserviço não tiver uma dependência de um serviço ou do SQL Server, você deverá adicionar apenas uma verificação de Healthy("Ok").</span><span class="sxs-lookup"><span data-stu-id="1580a-147">If the microservice does not have a dependency on a service or on SQL Server, you should just add a Healthy("Ok") check.</span></span> <span data-ttu-id="1580a-148">O código a seguir é do microsserviço `basket.api` do eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="1580a-148">The following code is from the eShopOnContainers `basket.api` microservice.</span></span> <span data-ttu-id="1580a-149">(O microsserviço de cesta usa o Cache Redis, mas a biblioteca ainda não inclui um provedor de verificação de integridade do Redis.)</span><span class="sxs-lookup"><span data-stu-id="1580a-149">(The basket microservice uses the Redis cache, but the library does not yet include a Redis health check provider.)</span></span>

```csharp
services.AddHealthChecks(checks =>
{
    checks.AddValueTaskCheck("HTTP Endpoint", () => new
        ValueTask<IHealthCheckResult>(HealthCheckResult.Healthy("Ok")));
});
```

<span data-ttu-id="1580a-150">Para que um serviço ou aplicativo Web exponha o ponto de extremidade de verificação de integridade, ele deverá habilitar o método de extensão `UseHealthChecks([*url_for_health_checks*])`.</span><span class="sxs-lookup"><span data-stu-id="1580a-150">For a service or web application to expose the health check endpoint, it has to enable the `UseHealthChecks([*url_for_health_checks*])` extension method.</span></span> <span data-ttu-id="1580a-151">Esse método age no nível do `WebHostBuilder` no método principal da classe `Program` do aplicativo Web ou serviço do ASP.NET Core, logo após <xref:Microsoft.AspNetCore.WebHost.CreateDefaultBuilder>, como mostra o código simplificado a seguir:</span><span class="sxs-lookup"><span data-stu-id="1580a-151">This method goes at the `WebHostBuilder` level in the main method of the `Program` class of your ASP.NET Core service or web application, right after <xref:Microsoft.AspNetCore.WebHost.CreateDefaultBuilder> as shown in the following simplified code:</span></span>

```csharp
namespace Microsoft.eShopOnContainers.WebMVC
{
    public class Program
    {
        public static void Main(string[] args)
        {
            var host = WebHost.CreateDefaultBuilder(args)
                .UseHealthChecks("/hc")
                .UseContentRoot(Directory.GetCurrentDirectory())
                .UseStartup<Startup>()
                .Build();

            host.Run();
        }
    }
}
```

<span data-ttu-id="1580a-152">O processo funciona desta maneira: cada microsserviço expõe o ponto de extremidade /hc.</span><span class="sxs-lookup"><span data-stu-id="1580a-152">The process works this way: each microservice exposes the endpoint /hc.</span></span> <span data-ttu-id="1580a-153">Esse ponto de extremidade é criado pela biblioteca HealthChecks do middleware ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="1580a-153">That endpoint is created by the HealthChecks library ASP.NET Core middleware.</span></span> <span data-ttu-id="1580a-154">Quando esse ponto de extremidade é invocado, ele executa todas as verificações de integridade configuradas no método AddHealthChecks na classe de Inicialização.</span><span class="sxs-lookup"><span data-stu-id="1580a-154">When that endpoint is invoked, it runs all the health checks that are configured in the AddHealthChecks method in the Startup class.</span></span>

<span data-ttu-id="1580a-155">O método UseHealthChecks espera uma porta ou um caminho.</span><span class="sxs-lookup"><span data-stu-id="1580a-155">The UseHealthChecks method expects a port or a path.</span></span> <span data-ttu-id="1580a-156">Essa porta ou caminho é o ponto de extremidade a ser usado para verificar o estado de integridade do serviço.</span><span class="sxs-lookup"><span data-stu-id="1580a-156">That port or path is the endpoint to use to check the health state of the service.</span></span> <span data-ttu-id="1580a-157">Por exemplo, o catálogo microsserviço usa o caminho /hc.</span><span class="sxs-lookup"><span data-stu-id="1580a-157">For instance, the catalog microservice uses the path /hc.</span></span>

### <a name="cache-health-check-responses"></a><span data-ttu-id="1580a-158">Respostas de verificação de integridade do cache</span><span class="sxs-lookup"><span data-stu-id="1580a-158">Cache health check responses</span></span>

<span data-ttu-id="1580a-159">Uma vez que você não deseja causar uma DoS (Negação de Serviço) nos seus serviços, ou simplesmente não desejar afetar o desempenho do serviço verificando recursos com muita frequência, você pode armazenar em cache os retornos e configurar uma duração de cache para cada verificação de integridade.</span><span class="sxs-lookup"><span data-stu-id="1580a-159">Since you do not want to cause a Denial of Service (DoS) in your services, or you simply do not want to impact service performance by checking resources too frequently, you can cache the returns and configure a cache duration for each health check.</span></span>

<span data-ttu-id="1580a-160">Por padrão, a duração do cache está definida internamente como 5 minutos, mas você pode alterar essa duração do cache em cada verificação de integridade, como no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="1580a-160">By default, the cache duration is internally set to 5 minutes, but you can change that cache duration on each health check, as in the following code:</span></span>

```csharp
checks.AddUrlCheck(Configuration["CatalogUrl"],1); // 1 min as cache duration
```

### <a name="query-your-microservices-to-report-about-their-health-status"></a><span data-ttu-id="1580a-161">Consultar os microsserviços para relatar o status de integridade</span><span class="sxs-lookup"><span data-stu-id="1580a-161">Query your microservices to report about their health status</span></span>

<span data-ttu-id="1580a-162">Depois de configurar as verificações de integridade, como descrito neste artigo e colocar o microsserviço em execução no Docker, você poderá verificar diretamente se ele está íntegro usando um navegador.</span><span class="sxs-lookup"><span data-stu-id="1580a-162">When you've configured health checks as described in this article and you have the microservice running in Docker, you can directly check from a browser if it's healthy.</span></span>

<span data-ttu-id="1580a-163">É necessário publicar a porta do contêiner no host do Docker, para que você possa acessar o contêiner por meio do IP externo do host do Docker ou por meio de `localhost`, como mostra a Figura 8-8.</span><span class="sxs-lookup"><span data-stu-id="1580a-163">You have to publish the container port in the Docker host, so you can access the container through the external Docker host IP or through `localhost`, as shown in figure 8-8.</span></span>

![Exibição do navegador da resposta JSON retornada por uma verificação de integridade](./media/image7.png)

<span data-ttu-id="1580a-165">**Figura 8-8**.</span><span class="sxs-lookup"><span data-stu-id="1580a-165">**Figure 8-8**.</span></span> <span data-ttu-id="1580a-166">Verificando o status da integridade de um único serviço em um navegador</span><span class="sxs-lookup"><span data-stu-id="1580a-166">Checking health status of a single service from a browser</span></span>

<span data-ttu-id="1580a-167">No teste, você pode ver que o microsserviço catalog.api (em execução na porta 5101) está íntegro, retornando o status HTTP 200 e informações de status em JSON.</span><span class="sxs-lookup"><span data-stu-id="1580a-167">In that test, you can see that the catalog.api microservice (running on port 5101) is healthy, returning HTTP status 200 and status information in JSON.</span></span> <span data-ttu-id="1580a-168">Isso significa, ainda, que o serviço também verificou internamente a integridade de sua dependência do banco de dados do SQL Server e que a verificação de integridade relatou a si própria como íntegra.</span><span class="sxs-lookup"><span data-stu-id="1580a-168">It also means that internally the service also checked the health of its SQL Server database dependency and that health check was reported itself as healthy.</span></span>

## <a name="use-watchdogs"></a><span data-ttu-id="1580a-169">Usar watchdogs</span><span class="sxs-lookup"><span data-stu-id="1580a-169">Use watchdogs</span></span>

<span data-ttu-id="1580a-170">Um watchdog é um serviço separado que pode inspecionar a integridade e a carga entre serviços e relatar a integridade dos microsserviços consultando a biblioteca `HealthChecks` já apresentada.</span><span class="sxs-lookup"><span data-stu-id="1580a-170">A watchdog is a separate service that can watch health and load across services, and report health about the microservices by querying with the `HealthChecks` library introduced earlier.</span></span> <span data-ttu-id="1580a-171">Isso pode ajudar a evitar erros que não seriam detectados com base no modo de exibição de um único serviço.</span><span class="sxs-lookup"><span data-stu-id="1580a-171">This can help prevent errors that would not be detected based on the view of a single service.</span></span> <span data-ttu-id="1580a-172">Watchdogs também são um bom lugar para hospedar código que pode realizar ações de correção para condições conhecidas sem interação do usuário.</span><span class="sxs-lookup"><span data-stu-id="1580a-172">Watchdogs also are a good place to host code that can perform remediation actions for known conditions without user interaction.</span></span>

<span data-ttu-id="1580a-173">O exemplo de eShopOnContainers contém uma página da Web que exibe os relatórios de verificação de integridade de exemplo, como mostra a Figura 8-9.</span><span class="sxs-lookup"><span data-stu-id="1580a-173">The eShopOnContainers sample contains a web page that displays sample health check reports, as shown in Figure 8-9.</span></span> <span data-ttu-id="1580a-174">Este é o watchdog mais simples que você pode ter, pois ele mostra simplesmente o estado dos aplicativos Web e dos microsserviços no eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="1580a-174">This is the simplest watchdog you could have since it only shows the state of the microservices and web applications in eShopOnContainers.</span></span> <span data-ttu-id="1580a-175">Geralmente, um watchdog também executa ações quando detecta estados não íntegro.</span><span class="sxs-lookup"><span data-stu-id="1580a-175">Usually a watchdog also takes actions when it detects unhealthy states.</span></span>

![Exibição no navegador do aplicativo WebStatus, mostrando o status de integridade de cinco microsserviços do eShopOnContainers](./media/image8.png)

<span data-ttu-id="1580a-177">**Figura 8-9**.</span><span class="sxs-lookup"><span data-stu-id="1580a-177">**Figure 8-9**.</span></span> <span data-ttu-id="1580a-178">Relatório de verificação de integridade de exemplo em eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="1580a-178">Sample health check report in eShopOnContainers</span></span>

<span data-ttu-id="1580a-179">Em resumo, o middleware ASP.NET da biblioteca HealthChecks do ASP.NET Core fornece um ponto de extremidade de verificação de integridade único para cada microsserviço.</span><span class="sxs-lookup"><span data-stu-id="1580a-179">In summary, the ASP.NET middleware of the ASP.NET Core HealthChecks library provides a single health check endpoint for each microservice.</span></span> <span data-ttu-id="1580a-180">Isso executará todas as verificações de integridade definidas dentro dele e retornará um estado de integridade geral dependendo todas essas verificações.</span><span class="sxs-lookup"><span data-stu-id="1580a-180">This will execute all the health checks defined within it and return an overall health state depending on all those checks.</span></span>

<span data-ttu-id="1580a-181">A biblioteca HealthChecks é extensível via novas verificações de integridade dos futuros recursos externos.</span><span class="sxs-lookup"><span data-stu-id="1580a-181">The HealthChecks library is extensible through new health checks of future external resources.</span></span> <span data-ttu-id="1580a-182">Por exemplo, esperamos que no futuro a biblioteca tenha verificações de integridade para o Cache Redis e para outros bancos de dados.</span><span class="sxs-lookup"><span data-stu-id="1580a-182">For example, we expect that in the future the library will have health checks for Redis cache and for other databases.</span></span> <span data-ttu-id="1580a-183">A biblioteca permite relatório de integridade por várias dependências de aplicativo ou serviço, e você pode executar as ações com base nessas verificações de integridade.</span><span class="sxs-lookup"><span data-stu-id="1580a-183">The library allows health reporting by multiple service or application dependencies, and you can then take actions based on those health checks.</span></span>

## <a name="health-checks-when-using-orchestrators"></a><span data-ttu-id="1580a-184">Verificações de integridade ao usar orquestradores</span><span class="sxs-lookup"><span data-stu-id="1580a-184">Health checks when using orchestrators</span></span>

<span data-ttu-id="1580a-185">Para monitorar a disponibilidade de seus microsserviços, orquestradores como Kubernetes e Service Fabric realizam verificações de integridade periodicamente enviando solicitações para testar os microsserviços.</span><span class="sxs-lookup"><span data-stu-id="1580a-185">To monitor the availability of your microservices, orchestrators like Kubernetes and Service Fabric periodically perform health checks by sending requests to test the microservices.</span></span> <span data-ttu-id="1580a-186">Quando um orquestrador determina que um serviço/contêiner não está íntegro, ele para de rotear solicitações para aquela instância.</span><span class="sxs-lookup"><span data-stu-id="1580a-186">When an orchestrator determines that a service/container is unhealthy, it stops routing requests to that instance.</span></span> <span data-ttu-id="1580a-187">Ele também geralmente cria uma nova instância do contêiner.</span><span class="sxs-lookup"><span data-stu-id="1580a-187">It also usually creates a new instance of that container.</span></span>

<span data-ttu-id="1580a-188">Por exemplo, a maioria dos orquestradores pode usar verificações de integridade para gerenciar implantações de tempo de inatividade zero.</span><span class="sxs-lookup"><span data-stu-id="1580a-188">For instance, most orchestrators can use health checks to manage zero-downtime deployments.</span></span> <span data-ttu-id="1580a-189">Somente quando o status de um serviço/contêiner é alterado para íntegro o orquestrador começa a rotear o tráfego para instâncias de serviço/contêiner.</span><span class="sxs-lookup"><span data-stu-id="1580a-189">Only when the status of a service/container changes to healthy will the orchestrator start routing traffic to service/container instances.</span></span>

<span data-ttu-id="1580a-190">O monitoramento de integridade é especialmente importante quando um orquestrador executa uma atualização do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1580a-190">Health monitoring is especially important when an orchestrator performs an application upgrade.</span></span> <span data-ttu-id="1580a-191">Alguns orquestradores (como o Azure Service Fabric) atualizam os serviços em fases, por exemplo, podem atualizar um quinto da superfície de cluster para cada upgrade de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1580a-191">Some orchestrators (like Azure Service Fabric) update services in phases—for example, they might update one-fifth of the cluster surface for each application upgrade.</span></span> <span data-ttu-id="1580a-192">O conjunto de nós que é atualizado ao mesmo tempo é mencionado como um *domínio de atualização*.</span><span class="sxs-lookup"><span data-stu-id="1580a-192">The set of nodes that's upgraded at the same time is referred to as an *upgrade domain*.</span></span> <span data-ttu-id="1580a-193">Depois de cada domínio de atualização ter sido atualizado e estar disponível para os usuários, esse domínio de atualização deverá passar por verificações de integridade antes que a implantação passe para o próximo domínio de atualização.</span><span class="sxs-lookup"><span data-stu-id="1580a-193">After each upgrade domain has been upgraded and is available to users, that upgrade domain must pass health checks before the deployment moves to the next upgrade domain.</span></span>

<span data-ttu-id="1580a-194">Outro aspecto da integridade de serviço são as métricas de relatório do serviço.</span><span class="sxs-lookup"><span data-stu-id="1580a-194">Another aspect of service health is reporting metrics from the service.</span></span> <span data-ttu-id="1580a-195">Este é uma funcionalidade avançada do modelo de integridade de alguns orquestradores, como o Service Fabric.</span><span class="sxs-lookup"><span data-stu-id="1580a-195">This is an advanced capability of the health model of some orchestrators, like Service Fabric.</span></span> <span data-ttu-id="1580a-196">As métricas são importantes ao usar um orquestrador, pois elas são usadas para equilibrar o uso de recursos.</span><span class="sxs-lookup"><span data-stu-id="1580a-196">Metrics are important when using an orchestrator because they are used to balance resource usage.</span></span> <span data-ttu-id="1580a-197">As métricas também podem ser um indicador de integridade do sistema.</span><span class="sxs-lookup"><span data-stu-id="1580a-197">Metrics also can be an indicator of system health.</span></span> <span data-ttu-id="1580a-198">Por exemplo, você pode ter um aplicativo com muitos microsserviços, e cada instância relata uma métrica de RPS (solicitações por segundo).</span><span class="sxs-lookup"><span data-stu-id="1580a-198">For example, you might have an application that has many microservices, and each instance reports a requests-per-second (RPS) metric.</span></span> <span data-ttu-id="1580a-199">Se um serviço estiver usando mais recursos (memória, processador etc.) que outro, o orquestrador poderá mover instâncias de serviço do cluster para tentar manter até mesmo a utilização de recursos.</span><span class="sxs-lookup"><span data-stu-id="1580a-199">If one service is using more resources (memory, processor, etc.) than another service, the orchestrator could move service instances around in the cluster to try to maintain even resource utilization.</span></span>

<span data-ttu-id="1580a-200">Observe que o Azure Service Fabric fornece seu próprio [modelo de monitoramento de integridade](/azure/service-fabric/service-fabric-health-introduction), que é mais avançado do que as verificações de integridade simples.</span><span class="sxs-lookup"><span data-stu-id="1580a-200">Note that Azure Service Fabric provides its own [Health Monitoring model](/azure/service-fabric/service-fabric-health-introduction), which is more advanced than simple health checks.</span></span>

## <a name="advanced-monitoring-visualization-analysis-and-alerts"></a><span data-ttu-id="1580a-201">Monitoramento avançado: visualização, análise e alertas</span><span class="sxs-lookup"><span data-stu-id="1580a-201">Advanced monitoring: visualization, analysis, and alerts</span></span>

<span data-ttu-id="1580a-202">A parte final do monitoramento é visualizar o fluxo de eventos, relatar o desempenho do serviço e alertar quando for detectado um problema.</span><span class="sxs-lookup"><span data-stu-id="1580a-202">The final part of monitoring is visualizing the event stream, reporting on service performance, and alerting when an issue is detected.</span></span> <span data-ttu-id="1580a-203">Você pode usar diferentes soluções para esse aspecto do monitoramento.</span><span class="sxs-lookup"><span data-stu-id="1580a-203">You can use different solutions for this aspect of monitoring.</span></span>

<span data-ttu-id="1580a-204">Você pode usar aplicativos personalizados simples que mostrem o estado dos serviços, como a página personalizada que mostramos ao explicar o [HealthChecks do ASP.NET Core](https://github.com/dotnet-architecture/HealthChecks).</span><span class="sxs-lookup"><span data-stu-id="1580a-204">You can use simple custom applications showing the state of your services, like the custom page shown when explaining the [ASP.NET Core HealthChecks](https://github.com/dotnet-architecture/HealthChecks).</span></span> <span data-ttu-id="1580a-205">Ou você pode usar ferramentas mais avançadas, como Azure Application Insights e o Operations Management Suite para gerar alertas com base em fluxo de eventos.</span><span class="sxs-lookup"><span data-stu-id="1580a-205">Or you could use more advanced tools like Azure Application Insights to raise alerts based on the stream of events.</span></span>

<span data-ttu-id="1580a-206">Por fim, se você estiver armazenando todos os fluxos de eventos, poderá usar o Microsoft Power BI ou uma solução de terceiros, como o Kibana ou o Splunk, para visualizar os dados.</span><span class="sxs-lookup"><span data-stu-id="1580a-206">Finally, if you're storing all the event streams, you can use Microsoft Power BI or other solutions like Kibana or Splunk to visualize the data.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="1580a-207">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="1580a-207">Additional resources</span></span>

- <span data-ttu-id="1580a-208">**HealthChecks do ASP.NET Core** (versão experimental)\\</span><span class="sxs-lookup"><span data-stu-id="1580a-208">**ASP.NET Core HealthChecks** (experimental release)\\</span></span>
  [*https://github.com/dotnet-architecture/HealthChecks/*](https://github.com/dotnet-architecture/HealthChecks/)

- <span data-ttu-id="1580a-209">**Introdução ao monitoramento de integridade do Service Fabric**\\</span><span class="sxs-lookup"><span data-stu-id="1580a-209">**Introduction to Service Fabric health monitoring**\\</span></span>
  [*https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction*](/azure/service-fabric/service-fabric-health-introduction)

- <span data-ttu-id="1580a-210">**Azure Application Insights**\\</span><span class="sxs-lookup"><span data-stu-id="1580a-210">**Azure Application Insights**\\</span></span>
  [*https://azure.microsoft.com/services/application-insights/*](https://azure.microsoft.com/services/application-insights/)

- <span data-ttu-id="1580a-211">**Microsoft Operations Management Suite**\\</span><span class="sxs-lookup"><span data-stu-id="1580a-211">**Microsoft Operations Management Suite**\\</span></span>
  [*https://www.microsoft.com/cloud-platform/operations-management-suite*](https://www.microsoft.com/cloud-platform/operations-management-suite)

>[!div class="step-by-step"]
><span data-ttu-id="1580a-212">[Anterior](implement-circuit-breaker-pattern.md)
>[Próximo](../secure-net-microservices-web-applications/index.md)</span><span class="sxs-lookup"><span data-stu-id="1580a-212">[Previous](implement-circuit-breaker-pattern.md)
[Next](../secure-net-microservices-web-applications/index.md)</span></span>