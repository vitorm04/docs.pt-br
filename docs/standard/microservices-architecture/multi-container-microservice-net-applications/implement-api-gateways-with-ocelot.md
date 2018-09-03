---
title: Implementação de Gateways de API com o Ocelot
description: Saiba como implementar Gateways de API com o Ocelot e como usar o Ocelot em um ambiente baseado em contêiner.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 07/03/2018
ms.openlocfilehash: dbb3fdb27175a86291d3a942ff168a5aae787c0c
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43453069"
---
# <a name="implementing-api-gateways-with-ocelot"></a>Implementação de Gateways de API com o Ocelot

O aplicativo de microsserviço de referência [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) está usando o [Ocelot](https://github.com/ThreeMammals/Ocelot) porque ele é um Gateway de API simples e leve que pode ser implantado em qualquer lugar, juntamente com os microsserviços/contêineres como nos ambientes a seguir usados pelo eShopOnContainers.

- Host do docker, no computador de desenvolvimento local, localmente ou na nuvem.
- Cluster do Kubernetes, localmente ou em nuvem gerenciada, como o AKS (Serviço de Kubernetes do Azure).
- Cluster do Service Fabric, localmente ou na nuvem.
- Malha do Service Fabric, como PaaS/sem servidor no Azure.

## <a name="architect-and-design-your-api-gateways"></a>Arquitetar e projetar seus Gateways de API

O diagrama de arquitetura a seguir mostra como os Gateways de API são implementados com o Ocelot no eShopOnContainers.

![Diagrama de arquitetura do eShopOnContainers, mostrando aplicativos clientes, microsserviços e os Gateways de API entre eles](./media/image28.png)

**Figura 8-27.** Arquitetura do eShopOnContainers com Gateways de API

Esse diagrama mostra como todo o aplicativo é implantado em um único host do Docker ou computador de desenvolvimento com o "Docker for Windows" ou o "Docker for Mac". No entanto, implantar em qualquer orquestrador seria muito semelhante, mas qualquer contêiner no diagrama poderia ser expandido no orquestrador. 

Além disso, os ativos de infraestrutura, como bancos de dados, cache e agentes de mensagens devem ser descarregados do orquestrador e implantados em sistemas altamente disponíveis para a infraestrutura, como o Banco de Dados SQL do Azure, o Azure Cosmos DB, o Redis do Azure, o Barramento de Serviço do Azure ou qualquer solução de cluster de HA local.

Como você também pode observar no diagrama, a presença de vários Gateways de API permite que várias equipes de desenvolvimento sejam autônomas (nesse caso, recursos de marketing em relação a recursos de compras) ao desenvolver e implantar seus microsserviços além de seus próprios Gateways de API relacionados. 

Se você tivesse um único Gateway de API monolítico, isso significaria um único ponto a ser atualizado por várias equipes de desenvolvimento, o que poderia vincular todos os microsserviços com uma única parte do aplicativo.

Avançado bastante no design, às vezes, um Gateway de API refinado também pode ser limitado a um único microsserviço de negócios, dependendo da arquitetura escolhida. Ter os limites de API do Gateway determinados pela empresa ou domínio ajudará a obter um melhor design. 

Por exemplo, a granularidade refinada na camada do Gateway de API pode ser útil principalmente para aplicativos de interface do usuário compostos, mais avançados e baseados em microsserviços, porque o conceito de Gateway de API refinado é semelhante ao de serviço de composição de interface do usuário. 

Para obter mais informações sobre os serviços de composição de interface do usuário, confira [Criando interface do usuário de composição baseada em microsserviços](https://docs.microsoft.com/dotnet/standard/microservices-architecture/architect-microservice-container-applications/microservice-based-composite-ui-shape-layout).

Como principal vantagem para muitos aplicativos de médio e grande porte, o uso de um produto de Gateway de API personalizado costuma ser uma boa abordagem, mas não como um único agregador monolítico ou um Gateway de API personalizado central exclusivo, a menos que esse Gateway de API permita várias áreas de configuração independentes para as diversas equipes de desenvolvimento que criam microsserviços autônomos.

### <a name="sample-microservicescontainers-to-reroute-through-the-api-gateways"></a>Microsserviços/contêineres de amostra a serem reencaminhados por meio dos Gateways de API

Por exemplo, o `eShopOnContainers` tem cerca de seis tipos de microsserviços internos que precisam ser publicados por meio dos Gateways de API, conforme é mostrado na imagem a seguir.
 
![](./media/image29.png)

**Figura 8-28.** Pastas do microsserviço na solução eShopOnContainers no Visual Studio

Sobre o serviço de identidade, no design, ele fica fora do reencaminhamento do Gateway de API porque é o único interesse paralelo no sistema, mas com o Ocelot também é possível incluí-lo como parte das listas de reencaminhamento.

Todos esses serviços são implementados atualmente como serviços da API Web ASP.NET Core, como você pode observar no código. Vamos nos concentrar em um dos microsserviços, como o código do microsserviço Catálogo.

![](./media/image30.png)

**Figura 8-29.** Microsserviço de API Web de exemplo (microsserviço Catálogo)

Você pode ver que o microsserviço Catálogo é um projeto de API Web ASP.NET Core típico com vários controladores e métodos como no código a seguir.

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
A solicitação HTTP terminará executando esse tipo de código C# acessando o banco de dados de microsserviço além de qualquer ação adicional.

Em relação à URL do microsserviço, quando os contêineres são implantados no computador de desenvolvimento local (host do Docker local), cada contêiner do microsserviço tem sempre uma porta interna, geralmente a porta 80, especificada em seu dockerfile, como no dockerfile a seguir:

```
FROM microsoft/aspnetcore:2.0.5 AS base
WORKDIR /app
EXPOSE 80
```

A porta 80, mostrada no código é interna no host do Docker, portanto, não pode ser acessada por aplicativos clientes. Os aplicativos clientes podem acessar apenas as portas externas (se houver) publicadas durante a implantação de `docker-compose`.

Essas portas externas não devem ser publicadas durante a implantação em um ambiente de produção. Esse é exatamente o motivo para usar o Gateway de API, ou seja, para evitar a comunicação direta entre os aplicativos clientes e os microsserviços.

No entanto, durante o desenvolvimento, é necessário acessar o microsserviço/contêiner diretamente e executá-lo por meio do Swagger. É por isso que no eShopOnContainers as portas externas são especificadas mesmo quando elas não precisam ser usadas pelo Gateway de API ou por aplicativos clientes.

Aqui está um exemplo do arquivo `docker-compose.override.yml` para o microsserviço de catálogo:

```
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

Você pode ver como na configuração do docker-compose.override.yml a porta interna do contêiner de catálogo é a porta 80, mas a porta para acesso externo é a 5101. Mas essa porta não deve ser usada pelo aplicativo quando um Gateway de API é usado, apenas para depurar, executar e testar somente o microsserviço Catálogo.

Normalmente, não se implanta com o docker-compose em um ambiente de produção porque o ambiente de implantação de produção certo para microsserviços é um orquestrador como o Kubernetes ou o Service Fabric. Ao implantar nesses ambientes, use arquivos de configuração diferentes nos quais você não publica diretamente nenhuma porta externa para os microsserviços, mas sempre usa o proxy reverso do Gateway de API.

Execute o microsserviço de catálogo no host do Docker local seja executando a solução eShopOnContainers completa por meio do Visual Studio (ela executará todos os serviços nos arquivos docker-compose) ou apenas iniciando o microsserviço de catálogo com o seguinte comando docker-compose no CMD ou no PowerShell, localizado na pasta onde o `docker-compose.yml` e o docker-compose.override.yml estão localizados.

```
docker-compose run --service-ports catalog.api
```

Esse comando executa apenas o contêiner de serviço catalog.api e as dependências especificadas no docker-compose.yml. Nesse caso, o contêiner do SQL Server e o contêiner do RabbitMQ.

Em seguida, você pode acessar diretamente o microsserviço Catálogo e ver seus métodos na interface do usuário do Swagger, acessando diretamente por essa porta "externa", nesse caso, a `http://localhost:5101`. 

![](./media/image31.png)

**Figura 8-30.** Testando o microsserviço Catálogo com sua interface do usuário do Swagger

Neste ponto, você pode definir um ponto de interrupção no código C# no Visual Studio, testar o microsserviço com os métodos expostos na interface do usuário do Swagger e, por fim, limpar tudo com o comando `docker-compose down`.

No entanto, essa comunicação de acesso direto com o microsserviço, nesse caso, pela porta 5101 externa, é exatamente o que você deseja evitar em seu aplicativo. E você pode evitar isso definindo o nível adicional de indireção do Gateway de API (o Ocelot, neste caso). Dessa forma, o aplicativo cliente não acessará o microsserviço diretamente.

## <a name="implementing-your-api-gateways-with-ocelot"></a>Implementando Gateways de API com o Ocelot

O Ocelot é basicamente um conjunto de middleware que você pode aplicar em uma ordem específica.

O Ocelot foi projetado para funcionar apenas com o ASP.NET Core. Ele é direcionado ao netstandard2.0, portanto, pode ser usado em qualquer local com suporte para o .NET Standard 2.0, incluindo o tempo de execução do .NET Core 2.0 e o tempo de execução do .NET Framework 4.6.1 e superiores.

Instale o Ocelot e suas dependências no projeto ASP.NET Core com o [pacote NuGet do Ocelot](https://www.nuget.org/packages/Ocelot/), por meio do Visual Studio.

```
Install-Package Ocelot
```

No eShopOnContainers, a implementação do Gateway de API é um projeto simples de WebHost do ASP.NET Core, além disso, o middleware do Ocelot lida com todos os recursos do Gateway de API, conforme é mostrado na imagem a seguir:

![](./media/image32.png)

**Figura 8-31.** Projeto base OcelotApiGw no eShopOnContainers

Este projeto de WebHost do ASP.NET Core é composto por dois arquivos simples, o `Program.cs` e `Startup.cs`.

O Program.cs precisa apenas criar e configurar o BuildWebHost típico do ASP.NET Core. 

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

O ponto importante para Ocelot é o arquivo `configuration.json` que você precisa fornecer para o construtor pelo método `AddJsonFile()`. Esse `configuration.json` é onde você especifica todos os reencaminhamentos do Gateway de API, o que significa os pontos de extremidade externos com portas específicas e os pontos de extremidade internos correlacionados, geralmente usando portas diferentes.

```
{
    "ReRoutes": [],
    "GlobalConfiguration": {}
}
```

Há duas seções para a configuração. Uma matriz de reencaminhamento e um GlobalConfiguration. Os reencaminhamentos são os objetos que dizem ao Ocelot como tratar uma solicitação de upstream. A configuração Global permite substituições das configurações específicas de reencaminhamento. Ela é útil quando não se deseja gerenciar muita configurações específicas de reencaminhamento.

Aqui está um exemplo simplificado do arquivo de [configuração de reencaminhamento](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/ApiGateways/Web.Bff.Shopping/apigw/configuration.json) de um dos Gateways de API do eShopOnContainers.

```
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

A funcionalidade principal de um Gateway de API Ocelot é obter solicitações HTTP de entrada e encaminhá-las para um serviço downstream, simultaneamente à outra solicitação HTTP. O Ocelot descreve o encaminhamento de uma solicitação para outra como um reencaminhamento.

Por exemplo, vamos nos concentrar em um dos reencaminhamentos no configuration.json mencionado acima, a configuração do microsserviço Cesta.

```
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

O DownstreamPathTemplate, o esquema e o DownstreamHostAndPorts compõem a URL interna do microsserviço ao qual essa solicitação será encaminhada. 

A porta é a porta interna usada pelo serviço. Ao usar contêineres, é a porta especificada no dockerfile.

O `Host` é um nome de serviço que depende da resolução de nomes de serviço que você está usando. Quando o docker-compose é usado, os serviços de nomes são fornecidos pelo Host do Docker, que está usando os nomes de serviço fornecidos nos arquivos docker-compose. Quando é usado um orquestrador, como o Kubernetes ou o Service Fabric, esse nome deve ser resolvido pelo DNS ou pela resolução de nomes fornecida por cada orquestrador.

DownstreamHostAndPorts é uma matriz que contém o host e a porta de todos os serviços downstream para os quais você deseja encaminhar solicitações. Normalmente, ela conterá apenas uma entrada, mas, às vezes, convém balancear a carga de solicitações para os serviços downstream e, para isso, o Ocelot permite que você adicione mais de uma entrada e, em seguida, selecione um balanceador de carga. Mas se você estiver usando o Azure e algum orquestrador, provavelmente, será melhor balancear a carga com a infraestrutura de nuvem e do orquestrador.

O UpstreamPathTemplate é a URL que o Ocelot usará para identificar qual DownstreamPathTemplate será usado para uma determinada solicitação do cliente. Por fim, o UpstreamHttpMethod é usado para que Ocelot possa distinguir entre diferentes solicitações (GET, POST, PUT) para a mesma URL.

Neste ponto, você poderia usar um único Gateway de API do Ocelot (WebHost do ASP.NET Core), com um ou [vários arquivos configuration.json mesclados](http://ocelot.readthedocs.io/en/latest/features/configuration.html#merging-configuration-files), ou armazenar a [configuração em um repositório KV Consul](http://ocelot.readthedocs.io/en/latest/features/configuration.html#store-configuration-in-consul). 

Mas, conforme apresentado nas seções de arquitetura e design, se você realmente deseja usar microsserviços autônomos, talvez seja melhor dividir esse único Gateway de API monolítico em vários Gateways de API e/ou BFFs (back-end para front-end). Para isso, vamos ver como implementar essa abordagem com contêineres do Docker.

### <a name="using-a-single-docker-container-image-to-run-multiple-different-api-gateway--bff-container-types"></a>Usando uma única imagem de contêiner do Docker para executar o vários Gateway de API diferentes ou tipos de BFF contêineres 

O design no eShopOnContainers implementa uma única imagem de contêiner do Docker com o Gateway de API Ocelot, mas, em seguida, ao implantar no Docker, ele cria contêineres/serviços diferentes para cada tipo de Gateway de API/BFF, fornecendo um arquivo configuration.json diferente para cada contêiner.

![](./media/image33.png)

**Figura 8-32.** Reutilizando uma única imagem do Docker do Ocelot em vários tipos de Gateway de API

No eShopOnContainers, a "imagem genérica do Docker do Gateway de API" é criada com o projeto chamado 'OcelotApiGw' e a imagem de nome "eshop/ocelotapigw" que é especificada no arquivo docker-compose.yml. Em seguida, ao implantar no Docker, haverá quatro contêineres de Gateway de API criados com essa mesma imagem do Docker, conforme é mostrado na seguinte extração do arquivo docker-compose.yml.

```
PARTIAL DOCKER-COMPOSE.YML

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

Além disso, como você pode ver no arquivo docker-compose.override.yml, a única diferença entre esses contêineres de Gateway de API é o arquivo de configuração do Ocelot, que é diferente para cada contêiner de serviço e é especificado no tempo de execução por meio de um volume do Docker, conforme é mostrado no seguinte arquivo docker-compose.override.yml.

```
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

Devido ao código anterior e, como é mostrado no Gerenciador do Visual Studio abaixo, o único arquivo necessário para definir cada Gateway de API de negócios/BFF é apenas um arquivo configuration.json, porque os quatro Gateways de API são baseados na mesma imagem do Docker.

![](./media/image34.png)

**Figura 8-33.** O único arquivo necessário para definir cada Gateway de API/BFF com o Ocelot é um arquivo de configuração 

Dividindo o Gateway de API em vários Gateways de API, diferentes equipes de desenvolvimento concentrando-se em diferentes subconjuntos de microsserviços podem gerenciar seus próprios Gateways de API usando arquivos de configuração do Ocelot independentes. Além disso, ao mesmo tempo, elas podem reutilizar a mesma imagem do Docker do Ocelot. 

Agora, se você executar o eShopOnContainers com os Gateways de API (incluídos por padrão no VS quando uma solução eShopOnContainers-ServicesAndWebApps.sln é aberta ou quando o "docker-compose up" é executado), as rotas de exemplo a seguir serão executadas. 

Por exemplo, ao visitar a URL upstream http://localhost:5202/api/v1/c/catalog/items/2/ atendida pelo Gateway de API webshoppingapigw, você obterá o resultado da URL downstream interna http://catalog.api/api/v1/2 dentro do host do Docker, como no navegador a seguir.

![](./media/image35.png)

**Figura 8-34.** Acessando um microsserviço por meio de uma URL fornecida pelo Gateway de API 

Por motivos de teste ou depuração, se você quiser acessar diretamente o contêiner do Docker do Catálogo (somente no ambiente de desenvolvimento) sem passar pelo Gateway de API, como 'catalog.api' é uma resolução de DNS interna do host do Docker (descoberta de serviço manipulada pelos nomes de serviço do docker-compose), a única maneira de acessar diretamente o contêiner será por meio da porta externa publicada em docker-compose.override.yml, que é fornecida apenas para testes de desenvolvimento, como http://localhost:5101/api/v1/Catalog/items/1 no navegador a seguir.

![](./media/image36.png)

**Figura 8-35.** Acesso direto a um microsserviço para fins de teste 

Mas o aplicativo está configurado para acessar todos os microsserviços por meio dos Gateways de API, não pela porta direta "atalhos". 

### <a name="the-gateway-aggregation-pattern-in-eshoponcontainers"></a>O padrão de agregação do Gateway em eShopOnContainers

Conforme apresentado anteriormente, uma maneira flexível de implementar a agregação de solicitações é com os serviços personalizados, por código. Você também pode implementar a agregação de solicitação com o recurso de agregação de solicitação no Ocelot, mas talvez essa opção não seja flexível o suficiente. Portanto, a maneira selecionada de implementar a agregação em eShopOnContainers é com um serviços da API Web ASP.NET Core explícitos para cada agregador. 

De acordo com essa abordagem, o diagrama de composição do Gateway de API é na realidade um pouco mais amplo ao considerar os serviços do agregador que não são mostrados no diagrama de arquitetura global simplificado mostrado anteriormente. 

No diagrama a seguir, você também poderá ver como os serviços do agregador funcionam com seus Gateways de API relacionados.

![](./media/image37.png)

**Figura 8-36.** Arquitetura de eShopOnContainers com serviços do agregador

A imagem a seguir está mais ampliada para que você possa observar como os aplicativos clientes poderiam ser melhorados para a área de negócios "Compras", reduzindo o excesso de comunicação com microsserviços ao usar esses serviços do agregador no realm dos Gateways de API. 

 ![](./media/image38.png)

**Figura 8-37.** Visão ampliada do agregador de serviços

Você pode observar como a complexidade aumenta quando o diagrama mostra as possíveis solicitações provenientes dos Gateways de API. Apesar disso, veja como as setas em azul seriam simplificadas, da perspectiva dos aplicativos clientes, ao usar o padrão de agregador reduzindo o excesso de comunicação e a latência na comunicação, por fim, melhorando significativamente a experiência do usuário para os aplicativos remotos ( aplicativos móveis e SPA), principalmente. 

A área de negócios e de microsserviços de "Marketing" é um caso de uso muito simples, portanto, não há necessidade de usar agregadores, mas, se fosse necessário, também seria possível.

### <a name="authentication-and-authorization-in-ocelot-api-gateways"></a>Autenticação e autorização em Gateways de API do Ocelot

Em um Gateway de API do Ocelot, você pode usar o serviço de autenticação, como um serviço de API Web ASP.NET Core, usando [IdentityServer](http://identityserver.io/) e fornecendo o token de autenticação dentro ou fora do Gateway de API.

Como o eShopOnContainers está usando vários Gateways de API com limites baseados em BFF e em áreas de negócios, o serviço de identidade/autenticação é deixado de fora dos Gateways de API, conforme está realçado em amarelo no diagrama a seguir.

 ![](./media/image39.png)

**Figura 8-38.** A posição do serviço de identidade em eShopOnContainers

No entanto, o Ocelot também dá suporte para o uso do microsserviço de identidade/autenticação dentro do limite do Gateway de API, como nesse outro diagrama.

 ![](./media/image40.png)

**Figura 8-39.** Autenticação no Gateway de API do Ocelot

Como o aplicativo eShopOnContainers dividiu o Gateway de API em vários Gateways de API de BFF (back-end para front-end) e de áreas de negócios, outra opção seria criar um Gateway de API adicional para interesses paralelos. Essa opção seria razoável em uma arquitetura de microsserviço bem mais complexa com vários microsserviços de interesses paralelos. Como há apenas um interesse paralelo no eShopOnContainers, foi decidido apenas lidar com o serviço de segurança fora do realm do Gateway de API, para simplificar.

Em qualquer caso, se o aplicativo estiver protegido no nível do Gateway de API, o módulo de autenticação do Gateway de API do Ocelot será acessado primeiro quando houver uma tentativa de usar qualquer microsserviço protegido. Isso redireciona a solicitação HTTP para acessar o microsserviço de identidade ou de autenticação para obter o token de acesso que permitirá acessar os serviços protegidos com o access_token.

É a maneira de proteger com autenticação qualquer serviço no nível do Gateway de API é definir o AuthenticationProviderKey em suas configurações relacionadas no configuration.json.

```
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

Quando o Ocelot for executado, ele examinará os reencaminhamentos AuthenticationOptions.AuthenticationProviderKey e verificará se há um provedor de autenticação registrado com a chave especificada. Se não houver, o Ocelot não será iniciado. Se houver, o reencaminhamento usará esse provedor quando for executado.

Como o WebHost do Ocelot é configurado com o `authenticationProviderKey = "IdentityApiKey"`, ele exigirá a autenticação sempre que esse serviço tiver alguma solicitação sem nenhum token de autenticação. 

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
```

Em seguida, você também precisará definir a autorização com o atributo [Authorize] nos recursos a serem acessados, como os microsserviços, como no seguinte controlador do microsserviço Cesta.

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

Os ValidAudiences como "cesta" são correlacionados à audiência definida em cada microsserviço com `AddJwtBearer()` no ConfigureServices() da classe de inicialização, como no código a seguir.

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

Como próxima etapa, se você tentar acessar qualquer microsserviço protegido, como o Cesta, com uma URL de reencaminhamento baseada no Gateway de API, como http://localhost:5202/api/v1/b/basket/1, ocorrerá um erro 401 Não Autorizado, a menos que você forneça um token válido. Por outro lado, se uma URL de reencaminhamento for autenticada, o Ocelot invocará qualquer esquema downstream associado a ela (a URL interna do microsserviço).

**Autorização na camada de reencaminhamento do Ocelot.**  O Ocelot dá suporte a autorização baseada em declarações avaliada após a autenticação. Você pode definir a autorização em um nível de rota adicionando o código a seguir na configuração de reencaminhamento. 

```
"RouteClaimsRequirement": {
    "UserType": "employee"
}
```

Nesse exemplo, quando o middleware de autorização for chamado, o Ocelot descobrirá se o usuário tem o tipo de declaração 'UserType' no token e se o valor dessa declaração é 'employee'. Se não for, o usuário não será autorizado e a resposta será 403 Proibido. 

## <a name="using-kubernetes-ingress-plus-ocelot-api-gateways"></a>Usando a entrada do Kubernetes e os Gateways de API do Ocelot

Ao usar o Kubernetes (como em um cluster do Serviço de Kubernetes do Azure), geralmente se unifica todas as solicitações HTTP por meio da [camada de entrada do Kubernetes](https://kubernetes.io/docs/concepts/services-networking/ingress/) com base no *Nginx*. 

No Kubernetes, se você não usar nenhuma abordagem de entrada, seus serviços e pods terão IPs que apenas poderão ser encaminhados pela rede de cluster. 

Mas se você usar uma abordagem de entrada, haverá uma camada intermediária entre a Internet e seus serviços (incluindo seus Gateways de API), atuando como um proxy reverso.

Como uma definição, uma entrada é uma coleção de regras que permitem que conexões de entrada acessem os serviços de cluster. Uma entrada é configurada para fornecer aos serviços URLs acessadas externamente, balancear a carga do tráfego, terminação SSL e muito mais. Os usuários solicitam a entrada postando o recurso de entrada no servidor de API.

Em eShopOnContainers, ao desenvolver localmente e usar apenas o computador de desenvolvimento como o host do Docker, você não está usando nenhuma entrada, mas apenas vários Gateways de API. 

No entanto, ao direcionar a um ambiente de "produção" baseado no Kubernetes, o eShopOnCOntainers está usando uma entrada na frente dos gateways de API. Dessa forma, os clientes ainda chamam a mesma URL base, mas as solicitações são encaminhadas para vários Gateways de API ou BFFs. 

Observe que os Gateways de API são front-ends ou fachadas que mostram somente os serviços, mas não os aplicativos Web que normalmente estão fora de seu escopo. Além disso, os Gateways de API podem ocultar determinados microsserviços internos. 

A entrada, no entanto, está apenas redirecionando solicitações HTTP, mas não está tentando ocultar nenhum microsserviço ou aplicativo Web.

A arquitetura ideal é uma camada Nginx de entrada no Kubernetes na frente dos aplicativos Web além de vários Gateways de API/BFF do Ocelot, conforme é mostrado no diagrama a seguir.

 ![](./media/image41.png)

**Figura 8-40.** A camada de entrada em eShopOnContainers, quando implantada no Kubernetes

Quando você implanta o eShopOnContainers no Kubernetes, ele expõe apenas alguns serviços ou pontos de extremidade via _entrada_, ou seja, basicamente, a seguinte lista de pós-fixados nas URLs:

-   `/` para o aplicativo Web cliente SPA
-   `/webmvc` para o aplicativo Web cliente MVC
-   `/webstatus` para o aplicativo Web cliente mostrando o status e as verificações de integridade
-   `/webshoppingapigw` para os processos de negócios Web BFF e de compras
-   `/webmarketingapigw` para os processos de negócios Web BFF e de marketing
-   `/mobileshoppingapigw` para os processos de negócios móveis BFF e de compras
-   `/mobilemarketingapigw` para os processos de negócios móveis BFF e de marketing

Ao implantar no Kubernetes, cada Gateway de API do Ocelot está usando um arquivo “configuration.json” diferente para cada _pod_ que executa os Gateways de API. Esses arquivos de “configuration.json” são fornecidos ao montar (originalmente com o script deploy.ps1) um volume criado com base em um _mapa de configuração_ do Kubernetes chamado 'ocelot'. Cada contêiner monta seu arquivo de configuração relacionado na pasta do contêiner chamada `/app/configuration`.

Nos arquivos de código-fonte do eShopOnContainers, os arquivos “configuration.json” originais podem ser encontrados na pasta `k8s/ocelot/`. Há um arquivo para cada BFF/APIGateway.


## <a name="additional-cross-cutting-features-in-an-ocelot-api-gateway"></a>Recursos de interesses paralelos adicionais em um Gateway de API do Ocelot

Há outros recursos importantes que podem ser pesquisados e usados ao usar um Gateway de API do Ocelot, descritos nos links a seguir.

-   **Descoberta de serviço no lado do cliente integrando o Ocelot ao Consul ou ao Eureka** 
    [*http://ocelot.readthedocs.io/en/latest/features/servicediscovery.html*](http://ocelot.readthedocs.io/en/latest/features/servicediscovery.html)

-   **Cache na camada do Gateway de API** 
    [*http://ocelot.readthedocs.io/en/latest/features/caching.html*](http://ocelot.readthedocs.io/en/latest/features/caching.html)

-   **Registro em log na camada do Gateway de API** 
    [*http://ocelot.readthedocs.io/en/latest/features/logging.html*](http://ocelot.readthedocs.io/en/latest/features/logging.html)

-   **Qualidade de Serviço (repetições e disjuntores) na camada do Gateway de API** 
    [*http://ocelot.readthedocs.io/en/latest/features/qualityofservice.html*](http://ocelot.readthedocs.io/en/latest/features/qualityofservice.html)

-   **Limitação de taxa** 
    [*http://ocelot.readthedocs.io/en/latest/features/ratelimiting.html*](http://ocelot.readthedocs.io/en/latest/features/ratelimiting.html )




>[!div class="step-by-step"]
[Anterior] (background-tasks-with-ihostedservice.md) [Próximo] (../microservice-ddd-cqrs-patterns/index.md)
