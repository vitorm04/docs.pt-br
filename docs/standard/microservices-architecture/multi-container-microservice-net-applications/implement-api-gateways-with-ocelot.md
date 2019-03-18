---
title: Implementação de Gateways de API com o Ocelot
description: Saiba como implementar Gateways de API com o Ocelot e como usar o Ocelot em um ambiente baseado em contêiner.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/02/2018
ms.openlocfilehash: 404f19f55b3be1e4be161543556bb2619f164b9b
ms.sourcegitcommit: 16aefeb2d265e69c0d80967580365fabf0c5d39a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2019
ms.locfileid: "57846097"
---
# <a name="implement-api-gateways-with-ocelot"></a><span data-ttu-id="471cf-103">Implementar Gateways de API com o Ocelot</span><span class="sxs-lookup"><span data-stu-id="471cf-103">Implement API Gateways with Ocelot</span></span>

<span data-ttu-id="471cf-104">Os aplicativos de microsserviço de referência [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) usam o [Ocelot](https://github.com/ThreeMammals/Ocelot), um Gateway de API simples e leve que pode ser implantado em qualquer lugar, juntamente com microsserviços/contêineres, como nos ambientes a seguir usados pelo eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="471cf-104">The reference microservice application [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) is using [Ocelot](https://github.com/ThreeMammals/Ocelot), a simple and lightweight API Gateway that you can deploy anywhere along with your microservices/containers, such as in any of the following environments used by eShopOnContainers.</span></span>

- <span data-ttu-id="471cf-105">Host do docker, no computador de desenvolvimento local, localmente ou na nuvem.</span><span class="sxs-lookup"><span data-stu-id="471cf-105">Docker host, in your local dev PC, on-premises or in the cloud.</span></span>
- <span data-ttu-id="471cf-106">Cluster do Kubernetes, localmente ou em nuvem gerenciada, como o AKS (Serviço de Kubernetes do Azure).</span><span class="sxs-lookup"><span data-stu-id="471cf-106">Kubernetes cluster, on-premises or in managed cloud such as Azure Kubernetes Service (AKS).</span></span>
- <span data-ttu-id="471cf-107">Cluster do Service Fabric, localmente ou na nuvem.</span><span class="sxs-lookup"><span data-stu-id="471cf-107">Service Fabric cluster, on-premises or in the cloud.</span></span>
- <span data-ttu-id="471cf-108">Malha do Service Fabric, como PaaS/sem servidor no Azure.</span><span class="sxs-lookup"><span data-stu-id="471cf-108">Service Fabric mesh, as PaaS/Serverless in Azure.</span></span>

## <a name="architect-and-design-your-api-gateways"></a><span data-ttu-id="471cf-109">Arquitetar e projetar seus Gateways de API</span><span class="sxs-lookup"><span data-stu-id="471cf-109">Architect and design your API Gateways</span></span>

<span data-ttu-id="471cf-110">O diagrama de arquitetura a seguir mostra como os Gateways de API são implementados com o Ocelot no eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="471cf-110">The following architecture diagram shows how API Gateways are implemented with Ocelot in eShopOnContainers.</span></span>

![Diagrama de arquitetura do eShopOnContainers, mostrando aplicativos clientes, microsserviços e os Gateways de API entre eles](./media/image28.png)

<span data-ttu-id="471cf-112">**Figura 6-28**.</span><span class="sxs-lookup"><span data-stu-id="471cf-112">**Figure 6-28**.</span></span> <span data-ttu-id="471cf-113">Arquitetura do eShopOnContainers com Gateways de API</span><span class="sxs-lookup"><span data-stu-id="471cf-113">eShopOnContainers architecture with API Gateways</span></span>

<span data-ttu-id="471cf-114">Esse diagrama mostra como todo o aplicativo é implantado em um único host do Docker ou computador de desenvolvimento com o "Docker for Windows" ou o "Docker for Mac".</span><span class="sxs-lookup"><span data-stu-id="471cf-114">That diagram shows how the whole application is deployed into a single Docker host or development PC with “Docker for Windows” or “Docker for Mac”.</span></span> <span data-ttu-id="471cf-115">No entanto, implantar em qualquer orquestrador seria muito semelhante, mas qualquer contêiner no diagrama poderia ser expandido no orquestrador.</span><span class="sxs-lookup"><span data-stu-id="471cf-115">However, deploying into any orchestrator would be pretty similar but any container in the diagram could be scaled-out in the orchestrator.</span></span>

<span data-ttu-id="471cf-116">Além disso, os ativos de infraestrutura, como bancos de dados, cache e agentes de mensagens devem ser descarregados do orquestrador e implantados em sistemas altamente disponíveis para a infraestrutura, como o Banco de Dados SQL do Azure, o Azure Cosmos DB, o Redis do Azure, o Barramento de Serviço do Azure ou qualquer solução de cluster de HA local.</span><span class="sxs-lookup"><span data-stu-id="471cf-116">In addition, the infrastructure assets such as databases, cache, and message brokers should be offloaded from the orchestrator and deployed into high available systems for infrastructure, like Azure SQL Database, Azure Cosmos DB, Azure Redis, Azure Service Bus, or any HA clustering solution on-premises.</span></span>

<span data-ttu-id="471cf-117">Como você também pode observar no diagrama, a presença de vários Gateways de API permite que várias equipes de desenvolvimento sejam autônomas (nesse caso, recursos de marketing em relação a recursos de compras) ao desenvolver e implantar seus microsserviços além de seus próprios Gateways de API relacionados.</span><span class="sxs-lookup"><span data-stu-id="471cf-117">As you can also notice in the diagram, having several API Gateways allows multiple development teams to be autonomous (in this case Marketing features vs. Shopping features) when developing and deploying their microservices plus their own related API Gateways.</span></span>

<span data-ttu-id="471cf-118">Se você tivesse um único Gateway de API monolítico, isso significaria um único ponto a ser atualizado por várias equipes de desenvolvimento, o que poderia vincular todos os microsserviços com uma única parte do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="471cf-118">If you had a single monolithic API Gateway that would mean a single point to be updated by several development teams, which could couple all the microservices with a single part of the application.</span></span>

<span data-ttu-id="471cf-119">Avançado bastante no design, às vezes, um Gateway de API refinado também pode ser limitado a um único microsserviço de negócios, dependendo da arquitetura escolhida.</span><span class="sxs-lookup"><span data-stu-id="471cf-119">Going much further in the design, sometimes a fine-grained API Gateway can also be limited to a single business microservice depending on the chosen architecture.</span></span> <span data-ttu-id="471cf-120">Ter os limites de API do Gateway determinados pela empresa ou domínio ajudará a obter um melhor design.</span><span class="sxs-lookup"><span data-stu-id="471cf-120">Having the API Gateway’s boundaries dictated by the business or domain will help you to get a better design.</span></span>

<span data-ttu-id="471cf-121">Por exemplo, a granularidade refinada na camada do Gateway de API pode ser útil principalmente para aplicativos de interface do usuário compostos, mais avançados e baseados em microsserviços, porque o conceito de Gateway de API refinado é semelhante ao de serviço de composição de interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="471cf-121">For instance, fine granularity in the API Gateway tier can be especially useful for more advanced composite UI applications that are based on microservices, because the concept of a fine-grained API Gateway is similar to a UI composition service.</span></span>

<span data-ttu-id="471cf-122">Apresentamos mais detalhes na seção anterior [Criando uma interface do usuário composta baseada em microsserviços](../architect-microservice-container-applications/microservice-based-composite-ui-shape-layout.md).</span><span class="sxs-lookup"><span data-stu-id="471cf-122">We delve into more details in the previous section [Creating composite UI based on microservices](../architect-microservice-container-applications/microservice-based-composite-ui-shape-layout.md).</span></span>

<span data-ttu-id="471cf-123">Como principal vantagem para muitos aplicativos de médio e grande porte, o uso de um produto de Gateway de API personalizado costuma ser uma boa abordagem, mas não como um único agregador monolítico ou um Gateway de API personalizado central exclusivo, a menos que esse Gateway de API permita várias áreas de configuração independentes para as diversas equipes de desenvolvimento que criam microsserviços autônomos.</span><span class="sxs-lookup"><span data-stu-id="471cf-123">As key takeaway, for many medium- and large-size applications, using a custom-built API Gateway product is usually a good approach, but not as a single monolithic aggregator or unique central custom API Gateway unless that API Gateway allows multiple independent configuration areas for the several development teams creating autonomous microservices.</span></span>

### <a name="sample-microservicescontainers-to-re-route-through-the-api-gateways"></a><span data-ttu-id="471cf-124">Microsserviços/contêineres de exemplo a serem reencaminhados por meio dos Gateways de API</span><span class="sxs-lookup"><span data-stu-id="471cf-124">Sample microservices/containers to re-route through the API Gateways</span></span>

<span data-ttu-id="471cf-125">Por exemplo, o eShopOnContainers tem cerca de seis tipos de microsserviços internos que precisam ser publicados por meio dos Gateways de API, conforme mostrado na imagem a seguir.</span><span class="sxs-lookup"><span data-stu-id="471cf-125">As an example, eShopOnContainers has around six internal microservice-types that have to be published through the API Gateways, as shown in the following image.</span></span>

![Somente os microsserviços Cesta, Catálogo, Localização, Marketing, Pedidos e Pagamento são publicados por meio do gateway de API.](./media/image29.png)

<span data-ttu-id="471cf-127">**Figura 6-29**.</span><span class="sxs-lookup"><span data-stu-id="471cf-127">**Figure 6-29**.</span></span> <span data-ttu-id="471cf-128">Pastas do microsserviço na solução eShopOnContainers no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="471cf-128">Microservice folders in eShopOnContainers solution in Visual Studio</span></span>

<span data-ttu-id="471cf-129">Sobre o serviço de Identidade, no design, ele fica fora do roteamento do Gateway de API porque é o único interesse paralelo no sistema, embora com o Ocelot também seja possível incluí-lo como parte das listas de reencaminhamento.</span><span class="sxs-lookup"><span data-stu-id="471cf-129">About the Identity service, in the design it's left out of the API Gateway routing because it's the only cross-cutting concern in the system, although with Ocelot it's also possible to include it as part of the rerouting lists.</span></span>

<span data-ttu-id="471cf-130">Todos esses serviços são implementados atualmente como serviços de API Web do ASP.NET Core, como você pode observar no código.</span><span class="sxs-lookup"><span data-stu-id="471cf-130">All those services are currently implemented as ASP.NET Core Web API services, as you can tell from the code.</span></span> <span data-ttu-id="471cf-131">Vamos nos concentrar em um dos microsserviços, como o código do microsserviço Catálogo.</span><span class="sxs-lookup"><span data-stu-id="471cf-131">Let’s focus on one of the microservices like the Catalog microservice code.</span></span>

![Exibição do Gerenciador de Soluções do projeto Catalog.API.](./media/image30.png)

<span data-ttu-id="471cf-133">**Figura 6-30**.</span><span class="sxs-lookup"><span data-stu-id="471cf-133">**Figure 6-30**.</span></span> <span data-ttu-id="471cf-134">Microsserviço de API Web de exemplo (microsserviço Catálogo)</span><span class="sxs-lookup"><span data-stu-id="471cf-134">Sample Web API microservice (Catalog microservice)</span></span>

<span data-ttu-id="471cf-135">Você pode ver que o microsserviço Catálogo é um projeto de API Web ASP.NET Core típico com vários controladores e métodos como no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="471cf-135">You can see that the Catalog microservice is a typical ASP.NET Core Web API project with several controllers and methods like in the following code.</span></span>

```csharp
[HttpGet]
[Route("items/{id:int}")]
[ProducesResponseType((int)HttpStatusCode.BadRequest)]
[ProducesResponseType((int)HttpStatusCode.NotFound)]
[ProducesResponseType(typeof(CatalogItem),(int)HttpStatusCode.OK)]
public async Task<IActionResult> GetItemById(int id)
{
    if (id <= 0)
    {
        return BadRequest();
    }
    var item = await _catalogContext.CatalogItems.
                                          SingleOrDefaultAsync(ci => ci.Id == id);
    //…

    if (item != null)
    {
        return Ok(item);
    }
    return NotFound();
}
```
<span data-ttu-id="471cf-136">A solicitação HTTP acabará executando esse tipo de código C# acessando o banco de dados de microsserviço e qualquer ação adicional necessária.</span><span class="sxs-lookup"><span data-stu-id="471cf-136">The HTTP request will end up running that kind of C# code accessing the microservice database and any additional required action.</span></span>

<span data-ttu-id="471cf-137">Em relação à URL do microsserviço, quando os contêineres são implantados no computador de desenvolvimento local (host do Docker local), cada contêiner do microsserviço tem sempre uma porta interna (geralmente, a porta 80) especificada em seu Dockerfile, como no seguinte Dockerfile:</span><span class="sxs-lookup"><span data-stu-id="471cf-137">Regarding the microservice URL, when the containers are deployed in your local development PC (local Docker host), each microservice’s container has always an internal port (usually port 80) specified in its dockerfile, as in the following dockerfile:</span></span>

```Dockerfile
FROM microsoft/aspnetcore:2.0.5 AS base
WORKDIR /app
EXPOSE 80
```

<span data-ttu-id="471cf-138">A porta 80 mostrada no código é interna no host do Docker e, portanto, não pode ser acessada por aplicativos cliente.</span><span class="sxs-lookup"><span data-stu-id="471cf-138">The port 80 shown in the code is internal within the Docker host, so it can't be reached by client apps.</span></span>

<span data-ttu-id="471cf-139">Os aplicativos cliente poderão acessar apenas as portas externas (se houver) publicadas durante a implantação com `docker-compose`.</span><span class="sxs-lookup"><span data-stu-id="471cf-139">Client apps can access only the external ports (if any) published when deploying with `docker-compose`.</span></span>

<span data-ttu-id="471cf-140">Essas portas externas não devem ser publicadas durante a implantação em um ambiente de produção.</span><span class="sxs-lookup"><span data-stu-id="471cf-140">Those external ports shouldn't be published when deploying to a production environment.</span></span> <span data-ttu-id="471cf-141">Esse é exatamente o motivo para usar o Gateway de API, ou seja, para evitar a comunicação direta entre os aplicativos clientes e os microsserviços.</span><span class="sxs-lookup"><span data-stu-id="471cf-141">This is precisely why you want to use the API Gateway, to avoid the direct communication between the client apps and the microservices.</span></span>

<span data-ttu-id="471cf-142">No entanto, durante o desenvolvimento, é necessário acessar o microsserviço/contêiner diretamente e executá-lo por meio do Swagger.</span><span class="sxs-lookup"><span data-stu-id="471cf-142">However, when developing, you want to access the microservice/container directly and run it through Swagger.</span></span> <span data-ttu-id="471cf-143">É por isso que no eShopOnContainers as portas externas são especificadas mesmo quando elas não precisam ser usadas pelo Gateway de API ou por aplicativos clientes.</span><span class="sxs-lookup"><span data-stu-id="471cf-143">That’s why in eShopOnContainers, the external ports are still specified even when they won’t be used by the API Gateway or the client apps.</span></span>

<span data-ttu-id="471cf-144">Aqui está um exemplo do arquivo `docker-compose.override.yml` para o microsserviço de catálogo:</span><span class="sxs-lookup"><span data-stu-id="471cf-144">Here’s an example of the `docker-compose.override.yml` file for the Catalog microservice:</span></span>

```yml
catalog.api:
  environment:
    - ASPNETCORE_ENVIRONMENT=Development
    - ASPNETCORE_URLS=http://0.0.0.0:80
    - ConnectionString=YOUR_VALUE
    - ... Other Environment Variables
  ports:
    - "5101:80"   # Important: In a production environment you should remove the external port (5101) kept here for microservice debugging purposes.
                  # The API Gateway redirects and access through the internal port (80).
```

<span data-ttu-id="471cf-145">Você pode ver como na configuração do docker-compose.override.yml a porta interna do contêiner de catálogo é a porta 80, mas a porta para acesso externo é a 5101.</span><span class="sxs-lookup"><span data-stu-id="471cf-145">You can see how in the docker-compose.override.yml configuration the internal port for the Catalog container is port 80, but the port for external access is 5101.</span></span> <span data-ttu-id="471cf-146">Mas essa porta não deve ser usada pelo aplicativo quando um Gateway de API é usado, apenas para depurar, executar e testar somente o microsserviço Catálogo.</span><span class="sxs-lookup"><span data-stu-id="471cf-146">But this port shouldn’t be used by the application when using an API Gateway, only to debug, run and test just the Catalog microservice.</span></span>

<span data-ttu-id="471cf-147">Normalmente, não se implanta com o docker-compose em um ambiente de produção porque o ambiente de implantação de produção certo para microsserviços é um orquestrador como o Kubernetes ou o Service Fabric.</span><span class="sxs-lookup"><span data-stu-id="471cf-147">Normally, you won’t be deploying with docker-compose into a production environment because the right production deployment environment for microservices is an orchestrator like Kubernetes or Service Fabric.</span></span> <span data-ttu-id="471cf-148">Ao implantar nesses ambientes, use arquivos de configuração diferentes nos quais você não publica diretamente nenhuma porta externa para os microsserviços, mas sempre usa o proxy reverso do Gateway de API.</span><span class="sxs-lookup"><span data-stu-id="471cf-148">When deploying to those environments you use different configuration files where you won’t publish directly any external port for the microservices but, you'll always use the reverse proxy from the API Gateway.</span></span>

<span data-ttu-id="471cf-149">Execute o microsserviço de catálogo no host do Docker local seja executando a solução eShopOnContainers completa por meio do Visual Studio (ela executará todos os serviços nos arquivos docker-compose) ou apenas iniciando o microsserviço de catálogo com o seguinte comando docker-compose no CMD ou no PowerShell, localizado na pasta onde o `docker-compose.yml` e o docker-compose.override.yml estão localizados.</span><span class="sxs-lookup"><span data-stu-id="471cf-149">Run the catalog microservice in your local Docker host either by running the full eShopOnContainers solution from Visual Studio (it’ll run all the services in the docker-compose files) or just starting the Catalog microservice with the following docker-compose command in CMD or PowerShell positioned at the folder where the `docker-compose.yml` and docker-compose.override.yml are placed.</span></span>

```console
docker-compose run --service-ports catalog.api
```

<span data-ttu-id="471cf-150">Esse comando executa apenas o contêiner de serviço catalog.api e as dependências especificadas no docker-compose.yml.</span><span class="sxs-lookup"><span data-stu-id="471cf-150">This command only runs the catalog.api service container plus dependencies that are specified in the docker-compose.yml.</span></span> <span data-ttu-id="471cf-151">Nesse caso, o contêiner do SQL Server e o contêiner do RabbitMQ.</span><span class="sxs-lookup"><span data-stu-id="471cf-151">In this case, the SQL Server container and RabbitMQ container.</span></span>

<span data-ttu-id="471cf-152">Em seguida, você pode acessar diretamente o microsserviço de Catálogo e ver seus métodos por meio da interface do usuário do Swagger, acessando-o diretamente por essa porta “externa”, nesse caso, `http://localhost:5101/swagger`:</span><span class="sxs-lookup"><span data-stu-id="471cf-152">Then, you can directly access the Catalog microservice and see its methods through the Swagger UI accessing directly through that “external” port, in this case `http://localhost:5101/swagger`:</span></span>

![Exibição do navegador da idade da interface do usuário do Swagger para a API REST de Catalog.API.](./media/image31.png)

<span data-ttu-id="471cf-154">**Figura 6-31**.</span><span class="sxs-lookup"><span data-stu-id="471cf-154">**Figure 6-31**.</span></span> <span data-ttu-id="471cf-155">Testando o microsserviço Catálogo com sua interface do usuário do Swagger</span><span class="sxs-lookup"><span data-stu-id="471cf-155">Testing the Catalog microservice with its Swagger UI</span></span>

<span data-ttu-id="471cf-156">Neste ponto, você pode definir um ponto de interrupção no código C# no Visual Studio, testar o microsserviço com os métodos expostos na interface do usuário do Swagger e, por fim, limpar tudo com o comando `docker-compose down`.</span><span class="sxs-lookup"><span data-stu-id="471cf-156">At this point, you could set a breakpoint in C# code in Visual Studio, test the microservice with the methods exposed in Swagger UI, and finally clean-up everything with the `docker-compose down` command.</span></span>

<span data-ttu-id="471cf-157">No entanto, a comunicação de acesso direto com o microsserviço, nesse caso, pela porta 5101 externa, é exatamente o que você deseja evitar em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="471cf-157">However, direct-access communication to the microservice, in this case through the external port 5101, is precisely what you want to avoid in your application.</span></span> <span data-ttu-id="471cf-158">E você pode evitar isso definindo o nível adicional de indireção do Gateway de API (o Ocelot, neste caso).</span><span class="sxs-lookup"><span data-stu-id="471cf-158">And you can avoid that by setting the additional level of indirection of the API Gateway (Ocelot, in this case).</span></span> <span data-ttu-id="471cf-159">Dessa forma, o aplicativo cliente não acessará o microsserviço diretamente.</span><span class="sxs-lookup"><span data-stu-id="471cf-159">That way, the client app won’t directly access the microservice.</span></span>

## <a name="implementing-your-api-gateways-with-ocelot"></a><span data-ttu-id="471cf-160">Implementando Gateways de API com o Ocelot</span><span class="sxs-lookup"><span data-stu-id="471cf-160">Implementing your API Gateways with Ocelot</span></span>

<span data-ttu-id="471cf-161">O Ocelot é basicamente um conjunto de middleware que você pode aplicar em uma ordem específica.</span><span class="sxs-lookup"><span data-stu-id="471cf-161">Ocelot is basically a set of middlewares that you can apply in a specific order.</span></span>

<span data-ttu-id="471cf-162">O Ocelot foi projetado para funcionar apenas com o ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="471cf-162">Ocelot is designed to work with ASP.NET Core only.</span></span> <span data-ttu-id="471cf-163">Ele é direcionado ao netstandard2.0, portanto, pode ser usado em qualquer local com suporte para o .NET Standard 2.0, incluindo o tempo de execução do .NET Core 2.0 e o tempo de execução do .NET Framework 4.6.1 e superiores.</span><span class="sxs-lookup"><span data-stu-id="471cf-163">It targets netstandard2.0 so it can be used anywhere .NET Standard 2.0 is supported, including .NET Core 2.0 runtime and .NET Framework 4.6.1 runtime and up.</span></span>

<span data-ttu-id="471cf-164">Instale o Ocelot e suas dependências no projeto ASP.NET Core com o [pacote NuGet do Ocelot](https://www.nuget.org/packages/Ocelot/), por meio do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="471cf-164">You install Ocelot and its dependencies in your ASP.NET Core project with [Ocelot's NuGet package](https://www.nuget.org/packages/Ocelot/), from Visual Studio.</span></span>

```powershell
Install-Package Ocelot
```

<span data-ttu-id="471cf-165">No eShopOnContainers, a implementação do Gateway de API é um projeto simples de WebHost do ASP.NET Core, além disso, o middleware do Ocelot lida com todos os recursos do Gateway de API, conforme é mostrado na imagem a seguir:</span><span class="sxs-lookup"><span data-stu-id="471cf-165">In eShopOnContainers, its API Gateway implementation is a simple ASP.NET Core WebHost project, and Ocelot’s middlewares handle all the API Gateway features, as shown in the following image:</span></span>

![Exibição do Gerenciador de Soluções do projeto de gateway de API do Ocelot.](./media/image32.png)

<span data-ttu-id="471cf-167">**Figura 6-32**.</span><span class="sxs-lookup"><span data-stu-id="471cf-167">**Figure 6-32**.</span></span> <span data-ttu-id="471cf-168">Projeto base OcelotApiGw no eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="471cf-168">The OcelotApiGw base project in eShopOnContainers</span></span>

<span data-ttu-id="471cf-169">Basicamente, este projeto WebHost do ASP.NET Core é criado com dois arquivos simples: `Program.cs` e `Startup.cs`.</span><span class="sxs-lookup"><span data-stu-id="471cf-169">This ASP.NET Core WebHost project is basically built with two simple files:  `Program.cs` and `Startup.cs`.</span></span>

<span data-ttu-id="471cf-170">O Program.cs precisa apenas criar e configurar o BuildWebHost típico do ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="471cf-170">The Program.cs just needs to create and configure the typical ASP.NET Core BuildWebHost.</span></span>

```csharp
namespace OcelotApiGw
{
    public class Program
    {
        public static void Main(string[] args)
        {
            BuildWebHost(args).Run();
        }

        public static IWebHost BuildWebHost(string[] args)
        {
            var builder = WebHost.CreateDefaultBuilder(args);

            builder.ConfigureServices(s => s.AddSingleton(builder))
                    .ConfigureAppConfiguration(
                          ic => ic.AddJsonFile(Path.Combine("configuration",
                                                            "configuration.json")))
                    .UseStartup<Startup>();
            var host = builder.Build();
            return host;
        }
    }
}
```

<span data-ttu-id="471cf-171">O ponto importante para Ocelot é o arquivo `configuration.json` que você precisa fornecer para o construtor pelo método `AddJsonFile()`.</span><span class="sxs-lookup"><span data-stu-id="471cf-171">The important point here for Ocelot is the `configuration.json` file that you must provide to the builder through the `AddJsonFile()` method.</span></span> <span data-ttu-id="471cf-172">Esse `configuration.json` é onde você especifica todos os reencaminhamentos do Gateway de API, o que significa os pontos de extremidade externos com portas específicas e os pontos de extremidade internos correlacionados, geralmente usando portas diferentes.</span><span class="sxs-lookup"><span data-stu-id="471cf-172">That `configuration.json` is where you specify all the API Gateway ReRoutes, meaning the external endpoints with specific ports and the correlated internal endpoints, usually using different ports.</span></span>

```json
{
    "ReRoutes": [],
    "GlobalConfiguration": {}
}
```

<span data-ttu-id="471cf-173">Há duas seções para a configuração.</span><span class="sxs-lookup"><span data-stu-id="471cf-173">There are two sections to the configuration.</span></span> <span data-ttu-id="471cf-174">Uma matriz de reencaminhamento e um GlobalConfiguration.</span><span class="sxs-lookup"><span data-stu-id="471cf-174">An array of Re-Routes and a GlobalConfiguration.</span></span> <span data-ttu-id="471cf-175">Os reencaminhamentos são os objetos que dizem ao Ocelot como tratar uma solicitação de upstream.</span><span class="sxs-lookup"><span data-stu-id="471cf-175">The Re-Routes are the objects that tell Ocelot how to treat an upstream request.</span></span> <span data-ttu-id="471cf-176">A configuração Global permite substituições das configurações específicas de reencaminhamento.</span><span class="sxs-lookup"><span data-stu-id="471cf-176">The Global configuration allows overrides of Re-Route specific settings.</span></span> <span data-ttu-id="471cf-177">Ela é útil quando não se deseja gerenciar muita configurações específicas de reencaminhamento.</span><span class="sxs-lookup"><span data-stu-id="471cf-177">It’s useful if you don’t want to manage lots of Re-Route specific settings.</span></span>

<span data-ttu-id="471cf-178">Veja a seguir um exemplo simplificado do [arquivo de configuração de Reencaminhamento](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/ApiGateways/Web.Bff.Shopping/apigw/configuration.json) de um dos Gateways de API do eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="471cf-178">Here’s a simplified example of [ReRoute configuration file](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/ApiGateways/Web.Bff.Shopping/apigw/configuration.json) from one of the API Gateways from eShopOnContainers.</span></span>

```json
{
  "ReRoutes": [
    {
      "DownstreamPathTemplate": "/api/{version}/{everything}",
      "DownstreamScheme": "http",
      "DownstreamHostAndPorts": [
        {
          "Host": "catalog.api",
          "Port": 80
        }
      ],
      "UpstreamPathTemplate": "/api/{version}/c/{everything}",
      "UpstreamHttpMethod": [ "POST", "PUT", "GET" ]
    },
    {
      "DownstreamPathTemplate": "/api/{version}/{everything}",
      "DownstreamScheme": "http",
      "DownstreamHostAndPorts": [
        {
          "Host": "basket.api",
          "Port": 80
        }
      ],
      "UpstreamPathTemplate": "/api/{version}/b/{everything}",
      "UpstreamHttpMethod": [ "POST", "PUT", "GET" ],
      "AuthenticationOptions": {
        "AuthenticationProviderKey": "IdentityApiKey",
        "AllowedScopes": []
      }
    }

  ],
    "GlobalConfiguration": {
      "RequestIdKey": "OcRequestId",
      "AdministrationPath": "/administration"
    }
  }
```

<span data-ttu-id="471cf-179">A funcionalidade principal de um Gateway de API Ocelot é obter solicitações HTTP de entrada e encaminhá-las para um serviço downstream, simultaneamente à outra solicitação HTTP.</span><span class="sxs-lookup"><span data-stu-id="471cf-179">The main functionality of an Ocelot API Gateway is to take incoming HTTP requests and forward them on to a downstream service, currently as another HTTP request.</span></span> <span data-ttu-id="471cf-180">O Ocelot descreve o encaminhamento de uma solicitação para outra como um reencaminhamento.</span><span class="sxs-lookup"><span data-stu-id="471cf-180">Ocelot’s describes the routing of one request to another as a Re-Route.</span></span>

<span data-ttu-id="471cf-181">Por exemplo, vamos nos concentrar em um dos reencaminhamentos no configuration.json mencionado acima, a configuração do microsserviço Cesta.</span><span class="sxs-lookup"><span data-stu-id="471cf-181">For instance, let’s focus on one of the Re-Routes in the configuration.json from above, the configuration for the Basket microservice.</span></span>

```json
{
      "DownstreamPathTemplate": "/api/{version}/{everything}",
      "DownstreamScheme": "http",
      "DownstreamHostAndPorts": [
        {
          "Host": "basket.api",
          "Port": 80
        }
      ],
      "UpstreamPathTemplate": "/api/{version}/b/{everything}",
      "UpstreamHttpMethod": [ "POST", "PUT", "GET" ],
      "AuthenticationOptions": {
        "AuthenticationProviderKey": "IdentityApiKey",
        "AllowedScopes": []
      }
}
```

<span data-ttu-id="471cf-182">O DownstreamPathTemplate, o esquema e o DownstreamHostAndPorts compõem a URL interna do microsserviço ao qual essa solicitação será encaminhada.</span><span class="sxs-lookup"><span data-stu-id="471cf-182">The DownstreamPathTemplate, Scheme, and DownstreamHostAndPorts make the internal microservice URL that this request will be forwarded to.</span></span>

<span data-ttu-id="471cf-183">A porta é a porta interna usada pelo serviço.</span><span class="sxs-lookup"><span data-stu-id="471cf-183">The port is the internal port used by the service.</span></span> <span data-ttu-id="471cf-184">Ao usar contêineres, é a porta especificada no dockerfile.</span><span class="sxs-lookup"><span data-stu-id="471cf-184">When using containers, the port specified at its dockerfile.</span></span>

<span data-ttu-id="471cf-185">O `Host` é um nome de serviço que depende da resolução de nomes de serviço que você está usando.</span><span class="sxs-lookup"><span data-stu-id="471cf-185">The `Host` is a service name that depends on the service name resolution you are using.</span></span> <span data-ttu-id="471cf-186">Quando o docker-compose é usado, os serviços de nomes são fornecidos pelo Host do Docker, que está usando os nomes de serviço fornecidos nos arquivos docker-compose.</span><span class="sxs-lookup"><span data-stu-id="471cf-186">When using docker-compose, the services names are provided by the Docker Host, which is using the service names provided in the docker-compose files.</span></span> <span data-ttu-id="471cf-187">Quando é usado um orquestrador, como o Kubernetes ou o Service Fabric, esse nome deve ser resolvido pelo DNS ou pela resolução de nomes fornecida por cada orquestrador.</span><span class="sxs-lookup"><span data-stu-id="471cf-187">If using an orchestrator like Kubernetes or Service Fabric, that name should be resolved by the DNS or name resolution provided by each orchestrator.</span></span>

<span data-ttu-id="471cf-188">DownstreamHostAndPorts é uma matriz que contém o host e a porta de todos os serviços downstream para os quais você deseja encaminhar solicitações.</span><span class="sxs-lookup"><span data-stu-id="471cf-188">DownstreamHostAndPorts is an array that contains the host and port of any downstream services that you wish to forward requests to.</span></span> <span data-ttu-id="471cf-189">Normalmente, ela conterá apenas uma entrada, mas, às vezes, convém balancear a carga de solicitações para os serviços downstream e, para isso, o Ocelot permite que você adicione mais de uma entrada e, em seguida, selecione um balanceador de carga.</span><span class="sxs-lookup"><span data-stu-id="471cf-189">Usually this will just contain one entry but sometimes you might want to load balance requests to your downstream services and Ocelot lets you add more than one entry and then select a load balancer.</span></span> <span data-ttu-id="471cf-190">Mas se você estiver usando o Azure e algum orquestrador, provavelmente, será melhor balancear a carga com a infraestrutura de nuvem e do orquestrador.</span><span class="sxs-lookup"><span data-stu-id="471cf-190">But if using Azure and any orchestrator it is probably a better idea to load balance with the cloud and orchestrator infrastructure.</span></span>

<span data-ttu-id="471cf-191">O UpstreamPathTemplate é a URL que o Ocelot usará para identificar qual DownstreamPathTemplate será usado para uma determinada solicitação do cliente.</span><span class="sxs-lookup"><span data-stu-id="471cf-191">The UpstreamPathTemplate is the URL that Ocelot will use to identify which DownstreamPathTemplate to use for a given request from the client.</span></span> <span data-ttu-id="471cf-192">Por fim, o UpstreamHttpMethod é usado para que Ocelot possa distinguir entre diferentes solicitações (GET, POST, PUT) para a mesma URL.</span><span class="sxs-lookup"><span data-stu-id="471cf-192">Finally, the UpstreamHttpMethod is used so Ocelot can distinguish between different requests (GET, POST, PUT) to the same URL.</span></span>

<span data-ttu-id="471cf-193">Neste ponto, você poderia usar um único Gateway de API do Ocelot (WebHost do ASP.NET Core), com um ou [vários arquivos configuration.json mesclados](https://ocelot.readthedocs.io/en/latest/features/configuration.html#merging-configuration-files), ou armazenar a [configuração em um repositório KV Consul](https://ocelot.readthedocs.io/en/latest/features/configuration.html#store-configuration-in-consul).</span><span class="sxs-lookup"><span data-stu-id="471cf-193">At this point, you could have a single Ocelot API Gateway (ASP.NET Core WebHost) using one or [multiple merged configuration.json files](https://ocelot.readthedocs.io/en/latest/features/configuration.html#merging-configuration-files) or you can also store the [configuration in a Consul KV store](https://ocelot.readthedocs.io/en/latest/features/configuration.html#store-configuration-in-consul).</span></span>

<span data-ttu-id="471cf-194">Mas, conforme apresentado nas seções de arquitetura e design, se você realmente deseja usar microsserviços autônomos, talvez seja melhor dividir esse único Gateway de API monolítico em vários Gateways de API e/ou BFFs (back-end para front-end).</span><span class="sxs-lookup"><span data-stu-id="471cf-194">But as introduced in the architecture and design sections, if you really want to have autonomous microservices, it might be better to split that single monolithic API Gateway into multiple API Gateways and/or BFF (Backend for Frontend).</span></span> <span data-ttu-id="471cf-195">Para isso, vamos ver como implementar essa abordagem com contêineres do Docker.</span><span class="sxs-lookup"><span data-stu-id="471cf-195">For that purpose, let’s see how to implement that approach with Docker containers.</span></span>

### <a name="using-a-single-docker-container-image-to-run-multiple-different-api-gateway--bff-container-types"></a><span data-ttu-id="471cf-196">Usando uma única imagem de contêiner do Docker para executar o vários Gateway de API diferentes ou tipos de BFF contêineres</span><span class="sxs-lookup"><span data-stu-id="471cf-196">Using a single Docker container image to run multiple different API Gateway / BFF container types</span></span>

<span data-ttu-id="471cf-197">No eShopOnContainers, estamos usando uma única imagem de contêiner do Docker com o Gateway de API do Ocelot, mas, em seguida, em tempo de execução, criamos serviços/contêineres diferentes para cada tipo de Gateway de API/BFF fornecendo um arquivo configuration.json diferente, usando um volume do Docker para acessar uma pasta de computador diferente para cada serviço.</span><span class="sxs-lookup"><span data-stu-id="471cf-197">In eShopOnContainers we’re using a single Docker container image with the Ocelot API Gateway but then, at run time, we create different services/containers for each type of API-Gateway/BFF by providing a different configuration.json file, using a docker volume to access a different PC folder for each service.</span></span>

![Uma única imagem do Docker para o gateway de API do Ocelot é usada para todos os quatro gateways de API](./media/image33.png)

<span data-ttu-id="471cf-199">**Figura 6-33**.</span><span class="sxs-lookup"><span data-stu-id="471cf-199">**Figure 6-33**.</span></span> <span data-ttu-id="471cf-200">Reutilizando uma única imagem do Docker do Ocelot em vários tipos de Gateway de API</span><span class="sxs-lookup"><span data-stu-id="471cf-200">Re-using a single Ocelot Docker image across multiple API Gateway types</span></span>

<span data-ttu-id="471cf-201">No eShopOnContainers, a "imagem genérica do Docker do Gateway de API" é criada com o projeto chamado 'OcelotApiGw' e a imagem de nome "eshop/ocelotapigw" que é especificada no arquivo docker-compose.yml.</span><span class="sxs-lookup"><span data-stu-id="471cf-201">In eShopOnContainers, the “Generic Ocelot API Gateway Docker Image” is created with the project named 'OcelotApiGw' and the image name “eshop/ocelotapigw” that is specified in the docker-compose.yml file.</span></span> <span data-ttu-id="471cf-202">Em seguida, ao implantar no Docker, haverá quatro contêineres de Gateway de API criados com essa mesma imagem do Docker, conforme é mostrado na seguinte extração do arquivo docker-compose.yml.</span><span class="sxs-lookup"><span data-stu-id="471cf-202">Then, when deploying to Docker, there will be four API-Gateway containers created from that same Docker image, as shown in the following extract from the docker-compose.yml file.</span></span>

```yml
  mobileshoppingapigw:
    image: eshop/ocelotapigw:${TAG:-latest}
    build:
      context: .
      dockerfile: src/ApiGateways/ApiGw-Base/Dockerfile

  mobilemarketingapigw:
    image: eshop/ocelotapigw:${TAG:-latest}
    build:
      context: .
      dockerfile: src/ApiGateways/ApiGw-Base/Dockerfile

  webshoppingapigw:
    image: eshop/ocelotapigw:${TAG:-latest}
    build:
      context: .
      dockerfile: src/ApiGateways/ApiGw-Base/Dockerfile

  webmarketingapigw:
    image: eshop/ocelotapigw:${TAG:-latest}
    build:
      context: .
      dockerfile: src/ApiGateways/ApiGw-Base/Dockerfile
```

<span data-ttu-id="471cf-203">Além disso, como você pode ver no arquivo docker-compose.override.yml a seguir, a única diferença entre esses contêineres de Gateway de API é o arquivo de configuração do Ocelot, que é diferente para cada contêiner de serviço e é especificado em tempo de execução por meio de um volume do Docker.</span><span class="sxs-lookup"><span data-stu-id="471cf-203">Additionally, as you can see in the following docker-compose.override.yml file, the only difference between those API Gateway containers is the Ocelot configuration file, which is different for each service container and it's specified at runtime through a Docker volume.</span></span>

```yml
mobileshoppingapigw:
  environment:
    - ASPNETCORE_ENVIRONMENT=Development
    - IdentityUrl=http://identity.api
  ports:
    - "5200:80"
  volumes:
    - ./src/ApiGateways/Mobile.Bff.Shopping/apigw:/app/configuration

mobilemarketingapigw:
  environment:
    - ASPNETCORE_ENVIRONMENT=Development
    - IdentityUrl=http://identity.api
  ports:
    - "5201:80"
  volumes:
    - ./src/ApiGateways/Mobile.Bff.Marketing/apigw:/app/configuration

webshoppingapigw:
  environment:
    - ASPNETCORE_ENVIRONMENT=Development
    - IdentityUrl=http://identity.api
  ports:
    - "5202:80"
  volumes:
    - ./src/ApiGateways/Web.Bff.Shopping/apigw:/app/configuration

webmarketingapigw:
  environment:
    - ASPNETCORE_ENVIRONMENT=Development
    - IdentityUrl=http://identity.api
  ports:
    - "5203:80"
  volumes:
    - ./src/ApiGateways/Web.Bff.Marketing/apigw:/app/configuration
```

<span data-ttu-id="471cf-204">Devido ao código anterior e, como é mostrado no Gerenciador do Visual Studio abaixo, o único arquivo necessário para definir cada Gateway de API de negócios/BFF é apenas um arquivo configuration.json, porque os quatro Gateways de API são baseados na mesma imagem do Docker.</span><span class="sxs-lookup"><span data-stu-id="471cf-204">Because of that previous code, and as shown in the Visual Studio Explorer below, the only file needed to define each specific business/BFF API Gateway is just a configuration.json file, because the four API Gateways are based on the same Docker image.</span></span>

![A única diferença entre todos os gateways de API é um arquivo configuration.json em cada um deles.](./media/image34.png)

<span data-ttu-id="471cf-206">**Figura 6-34**.</span><span class="sxs-lookup"><span data-stu-id="471cf-206">**Figure 6-34**.</span></span> <span data-ttu-id="471cf-207">O único arquivo necessário para definir cada Gateway de API/BFF com o Ocelot é um arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="471cf-207">The only file needed to define each API Gateway / BFF with Ocelot is a configuration file</span></span>

<span data-ttu-id="471cf-208">Dividindo o Gateway de API em vários Gateways de API, diferentes equipes de desenvolvimento concentrando-se em diferentes subconjuntos de microsserviços podem gerenciar seus próprios Gateways de API usando arquivos de configuração do Ocelot independentes.</span><span class="sxs-lookup"><span data-stu-id="471cf-208">By splitting the API Gateway into multiple API Gateways, different development teams focusing on different subsets of microservices can manage their own API Gateways by using independent Ocelot configuration files.</span></span> <span data-ttu-id="471cf-209">Além disso, ao mesmo tempo, elas podem reutilizar a mesma imagem do Docker do Ocelot.</span><span class="sxs-lookup"><span data-stu-id="471cf-209">Plus, at the same time they can reuse the same Ocelot Docker image.</span></span>

<span data-ttu-id="471cf-210">Agora, se você executar o eShopOnContainers com os Gateways de API (incluídos por padrão no VS quando uma solução eShopOnContainers-ServicesAndWebApps.sln é aberta ou quando o "docker-compose up" é executado), as rotas de exemplo a seguir serão executadas.</span><span class="sxs-lookup"><span data-stu-id="471cf-210">Now, if you run eShopOnContainers with the API Gateways (included by default in VS when opening eShopOnContainers-ServicesAndWebApps.sln solution or if running “docker-compose up”), the following sample routes will be performed.</span></span>

<span data-ttu-id="471cf-211">Por exemplo, ao visitar a URL upstream `http://localhost:5202/api/v1/c/catalog/items/2/` atendida pelo Gateway de API webshoppingapigw, você obterá o mesmo resultado da URL Downstream interna `http://catalog.api/api/v1/2` dentro do host do Docker, como no navegador a seguir.</span><span class="sxs-lookup"><span data-stu-id="471cf-211">For instance, when visiting the upstream URL `http://localhost:5202/api/v1/c/catalog/items/2/` served by the webshoppingapigw API Gateway, you get the same result from the internal Downstream URL `http://catalog.api/api/v1/2` within the Docker host, as in the following browser.</span></span>

![Exibição do navegador de uma resposta de Catalog.api passando pelo gateway de API.](./media/image35.png)

<span data-ttu-id="471cf-213">**Figura 6-35**.</span><span class="sxs-lookup"><span data-stu-id="471cf-213">**Figure 6-35**.</span></span> <span data-ttu-id="471cf-214">Acessando um microsserviço por meio de uma URL fornecida pelo Gateway de API</span><span class="sxs-lookup"><span data-stu-id="471cf-214">Accessing a microservice through a URL provided by the API Gateway</span></span>

<span data-ttu-id="471cf-215">Por motivos de teste ou depuração, se você quiser acessar diretamente o contêiner do Docker do Catálogo (somente no ambiente de desenvolvimento) sem passar pelo Gateway de API, como 'catalog.api' é uma resolução de DNS interna do host do Docker (descoberta de serviço manipulada pelos nomes de serviço do docker-compose), a única maneira de acessar diretamente o contêiner será por meio da porta externa publicada em docker-compose.override.yml, que é fornecida apenas para testes de desenvolvimento, como `http://localhost:5101/api/v1/Catalog/items/1` no navegador a seguir.</span><span class="sxs-lookup"><span data-stu-id="471cf-215">Because of testing or debugging reasons, if you wanted to directly access to the Catalog Docker container (only at the development environment) without passing through the API Gateway, since 'catalog.api' is a DNS resolution internal to the Docker host (service discovery handled by docker-compose service names), the only way to directly access the container is through the external port published in the docker-compose.override.yml, which is provided only for development tests, such as `http://localhost:5101/api/v1/Catalog/items/1` in the following browser.</span></span>

![Exibição do navegador de uma resposta de Catalog.api passando diretamente para o Catalog.api, idêntica àquela que passa pelo gateway de API.](./media/image36.png)

<span data-ttu-id="471cf-217">**Figura 6-36**.</span><span class="sxs-lookup"><span data-stu-id="471cf-217">**Figure 6-36**.</span></span> <span data-ttu-id="471cf-218">Acesso direto a um microsserviço para fins de teste</span><span class="sxs-lookup"><span data-stu-id="471cf-218">Direct access to a microservice for testing purposes</span></span>

<span data-ttu-id="471cf-219">Mas o aplicativo está configurado para acessar todos os microsserviços por meio dos Gateways de API, não pela porta direta "atalhos".</span><span class="sxs-lookup"><span data-stu-id="471cf-219">But the application is configured so it accesses all the microservices through the API Gateways, not though the direct port “shortcuts”.</span></span>

### <a name="the-gateway-aggregation-pattern-in-eshoponcontainers"></a><span data-ttu-id="471cf-220">O padrão de agregação do Gateway em eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="471cf-220">The Gateway aggregation pattern in eShopOnContainers</span></span>

<span data-ttu-id="471cf-221">Conforme apresentado anteriormente, uma maneira flexível de implementar a agregação de solicitações é com os serviços personalizados, por código.</span><span class="sxs-lookup"><span data-stu-id="471cf-221">As introduced previously, a flexible way to implement requests aggregation is with custom services, by code.</span></span> <span data-ttu-id="471cf-222">Você também pode implementar a agregação de solicitação com a [funcionalidade de Agregação de Solicitação no Ocelot](https://ocelot.readthedocs.io/en/latest/features/requestaggregation.html#request-aggregation), mas talvez essa opção não seja flexível o suficiente.</span><span class="sxs-lookup"><span data-stu-id="471cf-222">You could also implement request aggregation with the [Request Aggregation feature in Ocelot](https://ocelot.readthedocs.io/en/latest/features/requestaggregation.html#request-aggregation), but it might not be as flexible as you need.</span></span> <span data-ttu-id="471cf-223">Portanto, a maneira selecionada de implementar a agregação em eShopOnContainers é com um serviços da API Web ASP.NET Core explícitos para cada agregador.</span><span class="sxs-lookup"><span data-stu-id="471cf-223">Therefore, the selected way to implement aggregation in eShopOnContainers is with an explicit ASP.NET Core Web API services for each aggregator.</span></span>

<span data-ttu-id="471cf-224">De acordo com essa abordagem, o diagrama de composição do Gateway de API é, na realidade, um pouco mais amplo ao considerar os serviços de agregador que não são mostrados no diagrama de arquitetura global simplificado mostrado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="471cf-224">According to that approach, the API Gateway composition diagram is in reality a bit more extended when considering the aggregator services that are not shown in the simplified global architecture diagram shown previously.</span></span>

<span data-ttu-id="471cf-225">No diagrama a seguir, você também poderá ver como os serviços do agregador funcionam com seus Gateways de API relacionados.</span><span class="sxs-lookup"><span data-stu-id="471cf-225">In the following diagram, you can also see how the aggregator services work with their related API Gateways.</span></span>

![Arquitetura de eShopOnContainers, mostrando os serviços de agregador.](./media/image37.png)

<span data-ttu-id="471cf-227">**Figura 6-37**.</span><span class="sxs-lookup"><span data-stu-id="471cf-227">**Figure 6-37**.</span></span> <span data-ttu-id="471cf-228">Arquitetura de eShopOnContainers com serviços do agregador</span><span class="sxs-lookup"><span data-stu-id="471cf-228">eShopOnContainers architecture with aggregator services</span></span>

<span data-ttu-id="471cf-229">Ampliando ainda mais, na área de negócios “Compras” na imagem a seguir, você pode ver que o número de chamadas entre os aplicativos cliente e os microsserviços é reduzido ao usar os serviços de agregador nos Gateways de API.</span><span class="sxs-lookup"><span data-stu-id="471cf-229">Zooming in further, on the “Shopping” business area in the following image, you can see that chattiness between the client apps and the microservices is reduced when using the aggregator services in the API Gateways.</span></span>

![Ampliação da arquitetura de eShopOnContainers, mostrando os serviços de agregador, que "reúne" uma resposta "unindo" a resposta de vários microsserviços para reduzir o número de chamadas com o cliente final.](./media/image38.png)

<span data-ttu-id="471cf-231">**Figura 6-38**.</span><span class="sxs-lookup"><span data-stu-id="471cf-231">**Figure 6-38**.</span></span> <span data-ttu-id="471cf-232">Visão ampliada do agregador de serviços</span><span class="sxs-lookup"><span data-stu-id="471cf-232">Zoom in vision of the Aggregator services</span></span>

<span data-ttu-id="471cf-233">Você pode observar como a complexidade aumenta quando o diagrama mostra as possíveis solicitações provenientes dos Gateways de API.</span><span class="sxs-lookup"><span data-stu-id="471cf-233">You can notice how when the diagram shows the possible requests coming from the API Gateways it can get pretty complex.</span></span> <span data-ttu-id="471cf-234">Apesar disso, veja como as setas em azul seriam simplificadas, da perspectiva dos aplicativos clientes, ao usar o padrão de agregador reduzindo o excesso de comunicação e a latência na comunicação, por fim, melhorando significativamente a experiência do usuário para os aplicativos remotos ( aplicativos móveis e SPA), principalmente.</span><span class="sxs-lookup"><span data-stu-id="471cf-234">Although you can see how the arrows in blue would be simplified, from a client apps perspective, when using the aggregator pattern by reducing chattiness and latency in the communication, ultimately significantly improving the user experience for the remote apps (mobile and SPA apps), especially.</span></span>

<span data-ttu-id="471cf-235">A área de negócios e de microsserviços de "Marketing" é um caso de uso muito simples, portanto, não há necessidade de usar agregadores, mas, se fosse necessário, também seria possível.</span><span class="sxs-lookup"><span data-stu-id="471cf-235">In the case of the “Marketing” business area and microservices, it is a very simple use case so there was no need to use aggregators, but it could also be possible, if needed.</span></span>

### <a name="authentication-and-authorization-in-ocelot-api-gateways"></a><span data-ttu-id="471cf-236">Autenticação e autorização em Gateways de API do Ocelot</span><span class="sxs-lookup"><span data-stu-id="471cf-236">Authentication and authorization in Ocelot API Gateways</span></span>

<span data-ttu-id="471cf-237">Em um Gateway de API do Ocelot, você pode usar o serviço de autenticação, como um serviço de API Web ASP.NET Core, usando [IdentityServer](https://identityserver.io/) e fornecendo o token de autenticação dentro ou fora do Gateway de API.</span><span class="sxs-lookup"><span data-stu-id="471cf-237">In an Ocelot API Gateway you can sit the authentication service, such as an ASP.NET Core Web API service using [IdentityServer](https://identityserver.io/) providing the auth token, either out or inside the API Gateway.</span></span>

<span data-ttu-id="471cf-238">Como o eShopOnContainers está usando vários Gateways de API com limites baseados em BFF e em áreas de negócios, o serviço de identidade/autenticação é deixado de fora dos Gateways de API, conforme está realçado em amarelo no diagrama a seguir.</span><span class="sxs-lookup"><span data-stu-id="471cf-238">Since eShopOnContainers is using multiple API Gateways with boundaries based on BFF and business areas, the Identity/Auth service is left out of the API Gateways, as highlighted in yellow in the following diagram.</span></span>

![Diagrama da arquitetura de eShopOnContainers mostrando o microsserviço de Identidade abaixo do gateway de API.](./media/image39.png)

<span data-ttu-id="471cf-240">**Figura 6-39**.</span><span class="sxs-lookup"><span data-stu-id="471cf-240">**Figure 6-39**.</span></span> <span data-ttu-id="471cf-241">A posição do serviço de identidade em eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="471cf-241">Position of the Identity service in eShopOnContainers</span></span>

<span data-ttu-id="471cf-242">No entanto, o Ocelot também dá suporte ao uso do microsserviço de Identidade/Autenticação dentro do limite do Gateway de API, como neste outro diagrama.</span><span class="sxs-lookup"><span data-stu-id="471cf-242">However, Ocelot also supports sitting the Identity/Auth microservice within the API Gateway boundary, as in this other diagram.</span></span>

![Autenticação com o Microsserviço de identidade abaixo do AG (gateway de API): 1) o AG solicita um token de autenticação do microsserviço de identidade, 2) o microsserviço de identidade retorna um token para o AG, 3-4) solicitações do AG nos microsserviços usando o token de autenticação.](./media/image40.png)

<span data-ttu-id="471cf-244">**Figura 6-40**.</span><span class="sxs-lookup"><span data-stu-id="471cf-244">**Figure 6-40**.</span></span> <span data-ttu-id="471cf-245">Autenticação no Ocelot</span><span class="sxs-lookup"><span data-stu-id="471cf-245">Authentication in Ocelot</span></span>

<span data-ttu-id="471cf-246">Como o aplicativo eShopOnContainers dividiu o Gateway de API em vários Gateways de API de BFF (back-end para front-end) e de áreas de negócios, outra opção seria criar um Gateway de API adicional para interesses paralelos.</span><span class="sxs-lookup"><span data-stu-id="471cf-246">Because eShopOnContainers application has split the API Gateway into multiple BFF (Backend for Frontend) and business areas API Gateways, another option would had been to create an additional API Gateway for cross-cutting concerns.</span></span> <span data-ttu-id="471cf-247">Essa opção seria razoável em uma arquitetura de microsserviço bem mais complexa com vários microsserviços de interesses paralelos.</span><span class="sxs-lookup"><span data-stu-id="471cf-247">That choice would be fair in a more complex microservice based architecture with multiple cross-cutting concerns microservices.</span></span> <span data-ttu-id="471cf-248">Como há apenas um interesse paralelo no eShopOnContainers, foi decidido apenas lidar com o serviço de segurança fora do realm do Gateway de API, para simplificar.</span><span class="sxs-lookup"><span data-stu-id="471cf-248">Since there's only one cross-cutting concern in eShopOnContainers, it was decided to just handle the security service out of the API Gateway realm, for simplicity’s sake.</span></span>

<span data-ttu-id="471cf-249">Em qualquer caso, se o aplicativo estiver protegido no nível do Gateway de API, o módulo de autenticação do Gateway de API do Ocelot será acessado primeiro quando houver uma tentativa de usar qualquer microsserviço protegido.</span><span class="sxs-lookup"><span data-stu-id="471cf-249">In any case, if the app is secured at the API Gateway level, the authentication module of the Ocelot API Gateway is visited at first when trying to use any secured microservice.</span></span> <span data-ttu-id="471cf-250">Isso redireciona a solicitação HTTP para acessar o microsserviço de identidade ou de autenticação para obter o token de acesso que permitirá acessar os serviços protegidos com o access_token.</span><span class="sxs-lookup"><span data-stu-id="471cf-250">That re-directs the HTTP request to visit the Identity or auth microservice to get the access token so you can visit the protected services with the access_token.</span></span>

<span data-ttu-id="471cf-251">É a maneira de proteger com autenticação qualquer serviço no nível do Gateway de API é definir o AuthenticationProviderKey em suas configurações relacionadas no configuration.json.</span><span class="sxs-lookup"><span data-stu-id="471cf-251">The way you secure with authentication any service at the API Gateway level is by setting the AuthenticationProviderKey in its related settings at the configuration.json.</span></span>

```json
    {
      "DownstreamPathTemplate": "/api/{version}/{everything}",
      "DownstreamScheme": "http",
      "DownstreamHostAndPorts": [
        {
          "Host": "basket.api",
          "Port": 80
        }
      ],
      "UpstreamPathTemplate": "/api/{version}/b/{everything}",
      "UpstreamHttpMethod": [],
      "AuthenticationOptions": {
        "AuthenticationProviderKey": "IdentityApiKey",
        "AllowedScopes": []
      }
    }
```

<span data-ttu-id="471cf-252">Quando o Ocelot for executado, ele examinará os reencaminhamentos AuthenticationOptions.AuthenticationProviderKey e verificará se há um provedor de autenticação registrado com a chave especificada.</span><span class="sxs-lookup"><span data-stu-id="471cf-252">When Ocelot runs, it will look at the Re-Routes AuthenticationOptions.AuthenticationProviderKey and check that there is an Authentication Provider registered with the given key.</span></span> <span data-ttu-id="471cf-253">Se não houver, o Ocelot não será iniciado.</span><span class="sxs-lookup"><span data-stu-id="471cf-253">If there isn't, then Ocelot will not start up.</span></span> <span data-ttu-id="471cf-254">Se houver, o reencaminhamento usará esse provedor quando for executado.</span><span class="sxs-lookup"><span data-stu-id="471cf-254">If there is, then the ReRoute will use that provider when it executes.</span></span>

<span data-ttu-id="471cf-255">Como o WebHost do Ocelot é configurado com o `authenticationProviderKey = "IdentityApiKey"`, ele exigirá a autenticação sempre que esse serviço tiver alguma solicitação sem nenhum token de autenticação.</span><span class="sxs-lookup"><span data-stu-id="471cf-255">Because the Ocelot WebHost is configured with the `authenticationProviderKey = "IdentityApiKey"`, that will require authentication whenever that service has any requests without any auth token.</span></span>

```csharp
namespace OcelotApiGw
{
    public class Startup
    {
        private readonly IConfiguration _cfg;

        public Startup(IConfiguration configuration) => _cfg = configuration;

        public void ConfigureServices(IServiceCollection services)
        {
            var identityUrl = _cfg.GetValue<string>("IdentityUrl");
            var authenticationProviderKey = "IdentityApiKey";
                         //…
            services.AddAuthentication()
                .AddJwtBearer(authenticationProviderKey, x =>
                {
                    x.Authority = identityUrl;
                    x.RequireHttpsMetadata = false;
                    x.TokenValidationParameters = new Microsoft.IdentityModel.Tokens.TokenValidationParameters()
                    {
                        ValidAudiences = new[] { "orders", "basket", "locations", "marketing", "mobileshoppingagg", "webshoppingagg" }
                    };
                });
            //...
        }
    }
}
```

<span data-ttu-id="471cf-256">Em seguida, você também precisará definir a autorização com o atributo [Authorize] nos recursos a serem acessados, como os microsserviços, como no seguinte controlador do microsserviço Cesta.</span><span class="sxs-lookup"><span data-stu-id="471cf-256">Then, you also need to set authorization with the [Authorize] attribute on any resource to be accessed like the microservices, such as in the following Basket microservice controller.</span></span>

```csharp
namespace Microsoft.eShopOnContainers.Services.Basket.API.Controllers
{
    [Route("api/v1/[controller]")]
    [Authorize]
    public class BasketController : Controller
    {
      //...
    }
}
```

<span data-ttu-id="471cf-257">Os ValidAudiences como "cesta" são correlacionados à audiência definida em cada microsserviço com `AddJwtBearer()` no ConfigureServices() da classe de inicialização, como no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="471cf-257">The ValidAudiences such as “basket” are correlated with the audience defined in each microservice with `AddJwtBearer()` at the ConfigureServices() of the Startup class, such as in the code below.</span></span>

```csharp
// prevent from mapping "sub" claim to nameidentifier.
JwtSecurityTokenHandler.DefaultInboundClaimTypeMap.Clear();

var identityUrl = Configuration.GetValue<string>("IdentityUrl");

services.AddAuthentication(options =>
{
    options.DefaultAuthenticateScheme = JwtBearerDefaults.AuthenticationScheme;
    options.DefaultChallengeScheme = JwtBearerDefaults.AuthenticationScheme;

}).AddJwtBearer(options =>
{
    options.Authority = identityUrl;
    options.RequireHttpsMetadata = false;
    options.Audience = "basket";
});
```

<span data-ttu-id="471cf-258">Se você tentar acessar qualquer microsserviço protegido, como o microsserviço de Cesta, com uma URL de Reencaminhamento baseada no Gateway de API como `http://localhost:5202/api/v1/b/basket/1`, ocorrerá um erro 401 Não Autorizado, a menos que você forneça um token válido.</span><span class="sxs-lookup"><span data-stu-id="471cf-258">If you try to access any secured microservice, like the Basket microservice with a Re-Route URL based on the API Gateway like `http://localhost:5202/api/v1/b/basket/1`, then you’ll get a 401 Unauthorized unless you provide a valid token.</span></span> <span data-ttu-id="471cf-259">Por outro lado, se uma URL de reencaminhamento for autenticada, o Ocelot invocará qualquer esquema downstream associado a ela (a URL interna do microsserviço).</span><span class="sxs-lookup"><span data-stu-id="471cf-259">On the other hand, if a Re-Route URL is authenticated, Ocelot will invoke whatever downstream scheme is associated with it (the internal microservice URL).</span></span>

<span data-ttu-id="471cf-260">**Autorização na camada de Reencaminhamento do Ocelot.**</span><span class="sxs-lookup"><span data-stu-id="471cf-260">**Authorization at Ocelot’s ReRoutes tier.**</span></span>  <span data-ttu-id="471cf-261">O Ocelot dá suporte a autorização baseada em declarações avaliada após a autenticação.</span><span class="sxs-lookup"><span data-stu-id="471cf-261">Ocelot supports claims-based authorization evaluated after the authentication.</span></span> <span data-ttu-id="471cf-262">Defina a autorização em um nível de rota adicionando as linhas a seguir à configuração de Reencaminhamento.</span><span class="sxs-lookup"><span data-stu-id="471cf-262">You set the authorization at a route level by adding the following lines to the ReRoute configuration.</span></span>

```json
"RouteClaimsRequirement": {
    "UserType": "employee"
}
```

<span data-ttu-id="471cf-263">Nesse exemplo, quando o middleware de autorização for chamado, o Ocelot descobrirá se o usuário tem o tipo de declaração 'UserType' no token e se o valor dessa declaração é 'employee'.</span><span class="sxs-lookup"><span data-stu-id="471cf-263">In that example, when the authorization middleware is called, Ocelot will find if the user has the claim type 'UserType' in the token and if the value of that claim is 'employee'.</span></span> <span data-ttu-id="471cf-264">Se não for, o usuário não será autorizado e a resposta será 403 Proibido.</span><span class="sxs-lookup"><span data-stu-id="471cf-264">If it isn’t, then the user will not be authorized and the response will be 403 forbidden.</span></span>

## <a name="using-kubernetes-ingress-plus-ocelot-api-gateways"></a><span data-ttu-id="471cf-265">Usando a entrada do Kubernetes e os Gateways de API do Ocelot</span><span class="sxs-lookup"><span data-stu-id="471cf-265">Using Kubernetes Ingress plus Ocelot API Gateways</span></span>

<span data-ttu-id="471cf-266">Ao usar o Kubernetes (como em um cluster do Serviço de Kubernetes do Azure), você geralmente unifica todas as solicitações HTTP por meio da [camada de Entrada do Kubernetes](https://kubernetes.io/docs/concepts/services-networking/ingress/) com base no *Nginx*.</span><span class="sxs-lookup"><span data-stu-id="471cf-266">When using Kubernetes (like in an Azure Kubernetes Service cluster), you usually unify all the HTTP requests through the [Kubernetes Ingress tier](https://kubernetes.io/docs/concepts/services-networking/ingress/) based on *Nginx*.</span></span>

<span data-ttu-id="471cf-267">No Kubernetes, se você não usar qualquer abordagem de entrada, os seus serviços e pods terão IPs que poderão ser encaminhados apenas pela rede de cluster.</span><span class="sxs-lookup"><span data-stu-id="471cf-267">In Kubernetes, if you don’t use any ingress approach, then your services and pods have IPs only routable by the cluster network.</span></span>

<span data-ttu-id="471cf-268">Mas se você usar uma abordagem de entrada, haverá uma camada intermediária entre a Internet e seus serviços (incluindo seus Gateways de API), atuando como um proxy reverso.</span><span class="sxs-lookup"><span data-stu-id="471cf-268">But if you use an ingress approach, you'll have a middle tier between the Internet and your services (including your API Gateways), acting as a reverse proxy.</span></span>

<span data-ttu-id="471cf-269">Como uma definição, uma entrada é uma coleção de regras que permitem que conexões de entrada acessem os serviços de cluster.</span><span class="sxs-lookup"><span data-stu-id="471cf-269">As a definition, an Ingress is a collection of rules that allow inbound connections to reach the cluster services.</span></span> <span data-ttu-id="471cf-270">Uma entrada é geralmente configurada para fornecer aos serviços URLs acessadas externamente, balancear a carga do tráfego, terminação SSL e muito mais.</span><span class="sxs-lookup"><span data-stu-id="471cf-270">An ingress is usually configured to provide services externally reachable URLs, load balance traffic, SSL termination and more.</span></span> <span data-ttu-id="471cf-271">Os usuários solicitam a entrada postando o recurso de entrada no servidor de API.</span><span class="sxs-lookup"><span data-stu-id="471cf-271">Users request ingress by POSTing the Ingress resource to the API server.</span></span>

<span data-ttu-id="471cf-272">Em eShopOnContainers, ao desenvolver localmente e usar apenas o computador de desenvolvimento como o host do Docker, você não está usando nenhuma entrada, mas apenas vários Gateways de API.</span><span class="sxs-lookup"><span data-stu-id="471cf-272">In eShopOnContainers, when developing locally and using just your development machine as the Docker host, you are not using any ingress but only the multiple API Gateways.</span></span>

<span data-ttu-id="471cf-273">No entanto, ao direcionar a um ambiente de "produção" baseado no Kubernetes, o eShopOnContainers está usando uma entrada na frente dos gateways de API.</span><span class="sxs-lookup"><span data-stu-id="471cf-273">However, when targeting a “production” environment based on Kubernetes, eShopOnContainers is using an ingress in front of the API gateways.</span></span> <span data-ttu-id="471cf-274">Dessa forma, os clientes ainda chamam a mesma URL base, mas as solicitações são encaminhadas para vários Gateways de API ou BFFs.</span><span class="sxs-lookup"><span data-stu-id="471cf-274">That way, the clients still call the same base URL but the requests are routed to multiple API Gateways or BFF.</span></span>

<span data-ttu-id="471cf-275">Observe que os Gateways de API são front-ends ou fachadas que mostram somente os serviços, mas não os aplicativos Web que normalmente estão fora de seu escopo.</span><span class="sxs-lookup"><span data-stu-id="471cf-275">Note that API Gateways are front-ends or façades surfacing only the services but not the web applications that are usually out of their scope.</span></span> <span data-ttu-id="471cf-276">Além disso, os Gateways de API podem ocultar determinados microsserviços internos.</span><span class="sxs-lookup"><span data-stu-id="471cf-276">In addition, the API Gateways might hide certain internal microservices.</span></span>

<span data-ttu-id="471cf-277">A entrada, no entanto, está apenas redirecionando solicitações HTTP, mas não está tentando ocultar nenhum microsserviço ou aplicativo Web.</span><span class="sxs-lookup"><span data-stu-id="471cf-277">The ingress, however, is just redirecting HTTP requests but not trying to hide any microservice or web app.</span></span>

<span data-ttu-id="471cf-278">A arquitetura ideal é uma camada Nginx de entrada no Kubernetes na frente dos aplicativos Web além de vários Gateways de API/BFF do Ocelot, conforme é mostrado no diagrama a seguir.</span><span class="sxs-lookup"><span data-stu-id="471cf-278">Having an ingress Nginx tier in Kubernetes in front of the web applications plus the several Ocelot API Gateways / BFF is the ideal architecture, as shown in the following diagram.</span></span>

![Uma Entrada do Kubernetes funciona como um proxy reverso para todo o tráfego para o aplicativo, incluindo os aplicativos Web, que geralmente estão fora do escopo do gateway de API.](./media/image41.png)

<span data-ttu-id="471cf-280">**Figura 6-41**.</span><span class="sxs-lookup"><span data-stu-id="471cf-280">**Figure 6-41**.</span></span> <span data-ttu-id="471cf-281">A camada de entrada em eShopOnContainers, quando implantada no Kubernetes</span><span class="sxs-lookup"><span data-stu-id="471cf-281">The ingress tier in eShopOnContainers when deployed into Kubernetes</span></span>

<span data-ttu-id="471cf-282">Quando você implanta o eShopOnContainers no Kubernetes, ele expõe apenas alguns serviços ou pontos de extremidade via _entrada_, ou seja, basicamente, a seguinte lista de pós-fixados nas URLs:</span><span class="sxs-lookup"><span data-stu-id="471cf-282">When you deploy eShopOnContainers into Kubernetes, it exposes just a few services or endpoints via _ingress_, basically the following list of postfixes on the URLs:</span></span>

- <span data-ttu-id="471cf-283">`/` para o aplicativo Web cliente SPA</span><span class="sxs-lookup"><span data-stu-id="471cf-283">`/` for the client SPA web application</span></span>
- <span data-ttu-id="471cf-284">`/webmvc` para o aplicativo Web cliente MVC</span><span class="sxs-lookup"><span data-stu-id="471cf-284">`/webmvc` for the client MVC web application</span></span>
- <span data-ttu-id="471cf-285">`/webstatus` para o aplicativo Web cliente mostrando o status e as verificações de integridade</span><span class="sxs-lookup"><span data-stu-id="471cf-285">`/webstatus` for the client web app showing the status/healthchecks</span></span>
- <span data-ttu-id="471cf-286">`/webshoppingapigw` para os processos de negócios Web BFF e de compras</span><span class="sxs-lookup"><span data-stu-id="471cf-286">`/webshoppingapigw` for the web BFF and shopping business processes</span></span>
- <span data-ttu-id="471cf-287">`/webmarketingapigw` para os processos de negócios Web BFF e de marketing</span><span class="sxs-lookup"><span data-stu-id="471cf-287">`/webmarketingapigw` for the web BFF and marketing business processes</span></span>
- <span data-ttu-id="471cf-288">`/mobileshoppingapigw` para os processos de negócios móveis BFF e de compras</span><span class="sxs-lookup"><span data-stu-id="471cf-288">`/mobileshoppingapigw` for the mobile BFF and shopping business processes</span></span>
- <span data-ttu-id="471cf-289">`/mobilemarketingapigw` para os processos de negócios móveis BFF e de marketing</span><span class="sxs-lookup"><span data-stu-id="471cf-289">`/mobilemarketingapigw` for the mobile BFF and marketing business processes</span></span>

<span data-ttu-id="471cf-290">Ao implantar no Kubernetes, cada Gateway de API do Ocelot está usando um arquivo “configuration.json” diferente para cada _pod_ que executa os Gateways de API.</span><span class="sxs-lookup"><span data-stu-id="471cf-290">When deploying to Kubernetes, each Ocelot API Gateway is using a different “configuration.json” file for each _pod_ running the API Gateways.</span></span> <span data-ttu-id="471cf-291">Esses arquivos de "configuration.json" são fornecidos pela montagem (originalmente com o script deploy.ps1) de um volume criado com base em um _mapa de configuração_ do Kubernetes chamado 'ocelot'.</span><span class="sxs-lookup"><span data-stu-id="471cf-291">Those “configuration.json” files are provided by mounting (originally with the deploy.ps1 script) a volume created based on a Kubernetes _config map_ named ‘ocelot’.</span></span> <span data-ttu-id="471cf-292">Cada contêiner monta seu arquivo de configuração relacionado na pasta do contêiner chamada `/app/configuration`.</span><span class="sxs-lookup"><span data-stu-id="471cf-292">Each container mounts its related configuration file in the container’s folder named `/app/configuration`.</span></span>

<span data-ttu-id="471cf-293">Nos arquivos de código-fonte do eShopOnContainers, os arquivos “configuration.json” originais podem ser encontrados na pasta `k8s/ocelot/`.</span><span class="sxs-lookup"><span data-stu-id="471cf-293">In the source code files of eShopOnContainers, the original “configuration.json” files can be found within the `k8s/ocelot/` folder.</span></span> <span data-ttu-id="471cf-294">Há um arquivo para cada BFF/APIGateway.</span><span class="sxs-lookup"><span data-stu-id="471cf-294">There’s one file for each BFF/APIGateway.</span></span>

## <a name="additional-cross-cutting-features-in-an-ocelot-api-gateway"></a><span data-ttu-id="471cf-295">Recursos de interesses paralelos adicionais em um Gateway de API do Ocelot</span><span class="sxs-lookup"><span data-stu-id="471cf-295">Additional cross-cutting features in an Ocelot API Gateway</span></span>

<span data-ttu-id="471cf-296">Há outros recursos importantes que podem ser pesquisados e usados ao usar um Gateway de API do Ocelot, descritos nos links a seguir.</span><span class="sxs-lookup"><span data-stu-id="471cf-296">There are other important features to research and use, when using an Ocelot API Gateway, described in the following links.</span></span>

- <span data-ttu-id="471cf-297">**Descoberta de serviço no lado do cliente integrando o Ocelot ao Consul ou ao Eureka** \\</span><span class="sxs-lookup"><span data-stu-id="471cf-297">**Service discovery in the client side integrating Ocelot with Consul or Eureka** \\</span></span>
  [*https://ocelot.readthedocs.io/en/latest/features/servicediscovery.html*](https://ocelot.readthedocs.io/en/latest/features/servicediscovery.html)

- <span data-ttu-id="471cf-298">**Cache na camada do Gateway de API** \\</span><span class="sxs-lookup"><span data-stu-id="471cf-298">**Caching at the API Gateway tier** \\</span></span>
  [*https://ocelot.readthedocs.io/en/latest/features/caching.html*](https://ocelot.readthedocs.io/en/latest/features/caching.html)

- <span data-ttu-id="471cf-299">**Log na camada do Gateway de API** \\</span><span class="sxs-lookup"><span data-stu-id="471cf-299">**Logging at the API Gateway tier** \\</span></span>
  [*https://ocelot.readthedocs.io/en/latest/features/logging.html*](https://ocelot.readthedocs.io/en/latest/features/logging.html)

- <span data-ttu-id="471cf-300">**Qualidade de Serviço (repetições e disjuntores) na camada do Gateway de API** \\</span><span class="sxs-lookup"><span data-stu-id="471cf-300">**Quality of Service (Retries and Circuit breakers) at the API Gateway tier** \\</span></span>
  [*https://ocelot.readthedocs.io/en/latest/features/qualityofservice.html*](https://ocelot.readthedocs.io/en/latest/features/qualityofservice.html)

- <span data-ttu-id="471cf-301">**Limitação de taxa** \\</span><span class="sxs-lookup"><span data-stu-id="471cf-301">**Rate limiting** \\</span></span>
  [*https://ocelot.readthedocs.io/en/latest/features/ratelimiting.html*](https://ocelot.readthedocs.io/en/latest/features/ratelimiting.html )

> [!div class="step-by-step"]
> <span data-ttu-id="471cf-302">[Anterior](background-tasks-with-ihostedservice.md)
> [Próximo](../microservice-ddd-cqrs-patterns/index.md)</span><span class="sxs-lookup"><span data-stu-id="471cf-302">[Previous](background-tasks-with-ihostedservice.md)
[Next](../microservice-ddd-cqrs-patterns/index.md)</span></span>
