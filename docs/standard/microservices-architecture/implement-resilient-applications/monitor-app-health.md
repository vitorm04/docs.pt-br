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
# <a name="health-monitoring"></a>Monitoramento de integridade

Monitoramento de integridade pode permitir que informações quase em tempo real sobre o estado de seus contêineres e microservices. Monitoramento de integridade é fundamental para vários aspectos da operação microservices e é especialmente importante quando orchestrators executar atualizações de aplicativo parcial em fases, conforme explicado posteriormente.

Aplicativos baseados em Microservices geralmente usam pulsações ou verificações de integridade para habilitar seus monitores de desempenho, agendadores e orchestrators controlar a variedade de serviços. Se os serviços não podem enviar algum tipo de sinal "Estou alive", sob demanda ou em um agendamento, seu aplicativo poderá enfrentar riscos quando você implantar atualizações, ou pode simplesmente detectar falhas muito tarde e não conseguir interromper falhas em cascata que podem terminar em interrupções principais.

No modelo comum, serviços de enviar relatórios sobre o status e que informações são agregadas para fornecer uma visão geral do estado de integridade de seu aplicativo. Se você estiver usando um orquestrador, você pode fornecer informações de integridade para o cluster do orchestrator, para que o cluster possa atuar adequadamente. Se investir em relatórios de integridade de alta qualidade que é personalizado para seu aplicativo, você pode detectar e corrigir problemas do seu aplicativo em execução muito mais facilmente.

## <a name="implementing-health-checks-in-aspnet-core-services"></a>Implementação de integridade verifica no ASP.NET Core services

Ao desenvolver um aplicativo de microsserviço ou da web do ASP.NET Core, você pode usar uma biblioteca de chamada HealthChecks da equipe do ASP.NET. (A partir de maio de 2017, uma versão mais recente está disponível no GitHub).

Essa biblioteca é fácil de usar e fornece recursos que permitem que você valide se qualquer recurso externo específico necessário para seu aplicativo (como um banco de dados do SQL Server ou a API remota) está funcionando corretamente. Quando você usa essa biblioteca, você também pode decidir o que significa que o recurso esteja íntegro, como explicaremos mais tarde.

Para usar essa biblioteca, você precisa primeiro usar a biblioteca em sua microservices. Em segundo lugar, é necessário um aplicativo front-end que consulta para os relatórios de integridade. Aplicativo front-end pode ser um aplicativo de relatório personalizado, ou pode ser um orchestrator em si pode reagir de acordo para os estados de integridade.

### <a name="using-the-healthchecks-library-in-your-back-end-aspnet-microservices"></a>Usando a biblioteca de HealthChecks em seu back-end ASP.NET microservices

Você pode ver como a biblioteca de HealthChecks é usada no aplicativo de exemplo eShopOnContainers. Para começar, você precisa definir o que constitui um status de integridade para cada microsserviço. O aplicativo de exemplo, os microservices estão funcionando se a API de microsserviço está acessível por meio de HTTP e se seu banco de dados do SQL Server relacionado também está disponível.

No futuro, você poderá instalar a biblioteca de HealthChecks como um pacote do NuGet. Mas a redação deste artigo, você precisa baixar e compilar o código como parte de sua solução. Clone de código disponível em https://github.com/aspnet/HealthChecks e copie as seguintes pastas para sua solução.

  - src/comum
  - src/Microsoft.AspNetCore.HealthChecks
  - src/Microsoft.Extensions.HealthChecks
  - src/Microsoft.Extensions.HealthChecks.SqlServer

Você também pode usar verificações adicionais, como aquelas para o Azure (Microsoft.Extensions.HealthChecks.AzureStorage), mas como esta versão do eShopOnContainers não tem nenhuma dependência no Azure, não é necessário. As verificações de integridade do ASP.NET, não é necessário porque eShopOnContainers é baseado no ASP.NET Core.

Figura 10-6 mostra a biblioteca HealthChecks no Visual Studio, pronto para ser usado como um bloco de construção por qualquer microservices.

![](./media/image6.png)

**Figura 10-6**. Código-fonte biblioteca ASP.NET Core HealthChecks em uma solução do Visual Studio

Conforme apresentada anteriormente, a primeira coisa a fazer em cada projeto de microsserviço é adicionar uma referência para as três bibliotecas de HealthChecks. Depois disso, você deve adicionar as ações de verificação de integridade que você deseja executar no que microsserviço. Essas ações são basicamente as dependências em outros bancos de dados ou microservices (HttpUrlCheck) (atualmente SqlCheck\* para bancos de dados do SQL Server). Adicionar a ação dentro da classe de inicialização de cada microsserviço ASP.NET ou um aplicativo web ASP.NET.

Cada serviço ou aplicativo web deve ser configurado com a adição de todas as suas dependências HTTP ou o banco de dados como um método AddHealthCheck. Por exemplo, o aplicativo web MVC eShopOnContainers depende de muitos serviços, portanto, tem vários métodos de AddCheck adicionados para as verificações de integridade.

Por exemplo, no código a seguir você pode ver como o catálogo microsserviço adiciona uma dependência em seu banco de dados do SQL Server.

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

No entanto, o aplicativo web MVC do eShopOnContainers tem várias dependências nos outros a microservices. Portanto, ele chama um método AddUrlCheck para cada microsserviço, conforme mostrado no exemplo a seguir:

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

Assim, um microsserviço não fornecerá um status "Íntegro" até que todas as suas verificações também estão íntegros.

Se o microsserviço não tem uma dependência em um serviço ou no SQL Server, você deve adicionar apenas uma verificação de Healthy("Ok"). O código a seguir é do eShopOnContainers basket.api microsserviço. (O carrinho microsserviço usa o cache Redis, mas a biblioteca ainda não inclui um provedor de verificação de integridade do Redis.)

```csharp
services.AddHealthChecks(checks =>
{
    checks.AddValueTaskCheck("HTTP Endpoint", () => new
        ValueTask<IHealthCheckResult>(HealthCheckResult.Healthy("Ok")));
});
```

Para um serviço ou aplicativo web para expor o ponto de extremidade de verificação de integridade, ele deverá habilitar o UseHealthChecks (\[*url\_para\_integridade\_verifica*\]) extensão método. Esse método passa no WebHostBuilder nível no principal método de classe de programa do ASP.NET Core web ou serviço de aplicativo, logo após UseKestrel conforme mostrado no código a seguir.

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

O processo funciona da seguinte maneira: cada microsserviço expõe /hc o ponto de extremidade. Esse ponto de extremidade é criado pela biblioteca HealthChecks middleware ASP.NET Core. Quando esse ponto de extremidade é invocado, ele executa todas as verificações de integridade são configuradas no método AddHealthChecks na classe de inicialização.

O método UseHealthChecks espera uma porta ou um caminho. Essa porta ou o caminho é o ponto de extremidade a ser usado para verificar o estado de integridade do serviço. Por exemplo, o catálogo microsserviço usa /hc o caminho.

### <a name="caching-health-check-responses"></a>Cache de respostas de verificação de integridade

Desde que você não deseja causar uma negação de serviço (DoS) nos serviços ou simplesmente não desejar afetar o desempenho do serviço Verificando recursos com muita frequência, você pode armazenar em cache a retornar e configurar uma duração de cache para cada verificação de integridade.

Por padrão, a duração do cache internamente é definida como 5 minutos, mas você pode alterar essa duração do cache em cada verificação de integridade, como no código a seguir:

```csharp
checks.AddUrlCheck(Configuration["CatalogUrl"],1); // 1 min as cache duration
```

### <a name="querying-your-microservices-to-report-about-their-health-status"></a>Consultando o microservices para relatório sobre seu status de integridade

Quando você tiver configurado as verificações de integridade, conforme descrito aqui, quando o microsserviço estiver em execução no Docker, diretamente pode verificar em um navegador se está íntegro. (Isso requer que você está publicando a porta do contêiner fora do host do Docker, para que possa acessar o contêiner por meio de localhost ou o IP de host externo do Docker.) Figura 10-7 mostra uma solicitação em um navegador e as respostas correspondentes.

![](./media/image7.png)

**Figura 10-7**. Verificando o status de integridade de um único serviço em um navegador

No teste, você pode ver que o microsserviço catalog.api (em execução na porta 5101) esteja íntegro, retornando status HTTP 200 e informações de status em JSON. Isso também significa que internamente o serviço também marcada a integridade de sua dependência do banco de dados do SQL Server e que a verificação de integridade foi apresentou íntegro.

## <a name="using-watchdogs"></a>Usando watchdogs

Um watchdog é um serviço separado que pode assistir a integridade e a carga em serviços e a integridade de relatório sobre o microservices consultando-se com a biblioteca de HealthChecks apresentada anteriormente. Isso pode ajudar a evitar erros que não seriam detectados com base no modo de exibição de um único serviço. Watchdogs também são um bom lugar para código de host que pode realizar ações de correção para condições conhecidas sem interação do usuário.

O exemplo de eShopOnContainers contém uma página da web que exibe os relatórios de verificação de integridade de exemplo, conforme mostrado na Figura 10-8. Este é o watchdog mais simples, você pode ter, desde que ela simplesmente é mostra o estado dos aplicativos web e microservices eShopOnContainers. Geralmente um watchdog também executa ações quando ele detecta estados não íntegro.

![](./media/image8.png)

**Figura 10-8**. Relatório de verificação de integridade de exemplo no eShopOnContainers

Em resumo, o middleware ASP.NET da biblioteca do ASP.NET Core HealthChecks fornece um ponto de extremidade de verificação de integridade único para cada microsserviço. Isso será executar todas as verificações de integridade definidas dentro dela e retorna um estado de integridade geral dependendo todas essas verificações.

A biblioteca de HealthChecks é extensível via novas verificações de integridade dos futuros recursos externos. Por exemplo, esperamos que no futuro a biblioteca terá verificações de integridade para o cache Redis em outros bancos de dados. A biblioteca permite relatório por várias dependências de aplicativo ou serviço de integridade, e você pode executar as ações com base nessas verificações de integridade.

## <a name="health-checks-when-using-orchestrators"></a>Verificações de integridade ao usar orchestrators

Para monitorar a disponibilidade de seu microservices, orchestrators como o Docker Swarm, Kubernetes e do Service Fabric periodicamente realiza verificações de integridade, enviando solicitações para testar o microservices. Quando um orquestrador determina que um contêiner de serviço/não está íntegro, que ele interrompe a rotear solicitações para essa instância. Ele também geralmente cria uma nova instância do contêiner.

Por exemplo, orchestrators a maioria das podem usar verificações de integridade para gerenciar implantações de tempo de inatividade zero. Somente quando o status de um contêiner do serviço é alterado para íntegro o orchestrator iniciar rotear o tráfego para instâncias de contêiner do serviço.

Monitoramento de integridade é especialmente importante quando um orquestrador executa uma atualização do aplicativo. Alguns orchestrators (como o Azure Service Fabric) atualizar serviços em fases — por exemplo, eles podem atualizar um quinto da superfície de cluster para cada atualização de aplicativo. O conjunto de nós que é atualizado ao mesmo tempo é referido como uma *domínio de atualização*. Depois de cada domínio de atualização foi atualizado e está disponível para usuários, esse domínio de atualização deve passar verificações de integridade antes que a implantação é movido para o próximo domínio de atualização.

Métricas do serviço de relatórios é outro aspecto da integridade do serviço. Este é um recurso avançado do modelo de integridade de alguns orchestrators, como o Service Fabric. Métricas são importantes ao usar um orquestrador porque eles são usados para equilibrar o uso de recursos. Métricas também podem ser um indicador de integridade do sistema. Por exemplo, você pode ter um aplicativo que tem muitas microservices, e cada instância informa uma métrica de solicitações por segundo (RPS). Se um serviço estiver usando mais recursos (memória, processador, etc.) que outro serviço, o orchestrator pode mover instâncias de serviço do cluster para tentar manter até mesmo a utilização de recursos.

Observe que se você estiver usando o Azure Service Fabric, ele fornece seu próprio [modelo de monitoramento de integridade](https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction), que é mais avançada do que as verificações de integridade simples.

## <a name="advanced-monitoring-visualization-analysis-and-alerts"></a>Monitoramento avançado: visualização, análise e alertas

A parte final do monitoramento está visualizando o fluxo de eventos, relatórios sobre o desempenho do serviço e alertas quando é detectado um problema. Você pode usar diferentes soluções para esse aspecto do monitoramento.

Você pode usar simples aplicativos personalizados que mostra o estado de seus serviços, como a página personalizada mostramos quando explicamos [ASP.NET Core HealthChecks](https://github.com/aspnet/HealthChecks). Ou você pode usar as ferramentas mais avançadas, como informações de aplicativo do Azure e Operations Management Suite para gerar alertas com base em fluxo de eventos.

Por fim, se você estava armazenando os fluxos de eventos, você pode usar Microsoft Power BI ou uma solução de terceiros como Kibana ou Splunk para visualizar os dados.

## <a name="additional-resources"></a>Recursos adicionais

-   **ASP.NET Core HealthChecks** (versão inicial) [ *https://github.com/aspnet/HealthChecks/*](https://github.com/aspnet/HealthChecks/)

-   **Introdução ao monitoramento de integridade do Service Fabric**
    [*https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction*](https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction)

-   **Aplicativo do Azure Insights**
    [*https://azure.microsoft.com/services/application-insights/*](https://azure.microsoft.com/services/application-insights/)

-   **Microsoft Operations Management Suite**
    [*https://www.microsoft.com/en-us/cloud-platform/operations-management-suite*](https://www.microsoft.com/en-us/cloud-platform/operations-management-suite)

>[!div class="step-by-step"]
[Anterior] (implementar-circuito-separador-pattern.md) [Avançar] (... /Secure-NET-microservices-Web-Applications/Index.MD)
