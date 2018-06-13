---
title: Monitoramento de integridade
description: Arquitetura de microsserviços do .NET para aplicativos .NET em contêineres | Monitoramento de integridade
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/11/2017
ms.openlocfilehash: 81c4fc7662212bb3c6586a590d87e731220b7b7c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33578866"
---
# <a name="health-monitoring"></a>Monitoramento de integridade

O monitoramento de integridade pode permitir informações quase em tempo real sobre o estado de seus contêineres e microsserviços. O monitoramento de integridade é fundamental para vários aspectos da operação de microsserviços e é especialmente importante quando orquestradores executam upgrades parciais de aplicativo em fases, conforme explicado posteriormente.

Aplicativos baseados em microsserviços geralmente usam pulsações ou verificações de integridade para habilitar seus monitores de desempenho, agendadores e orquestradores a controlar a variedade de serviços. Se os serviços não puderem enviar algum tipo de sinal "Estou vivo", seja sob demanda ou conforme um agendamento, seu aplicativo poderá enfrentar riscos quando você implantar atualizações, ou poderá simplesmente detectar falhas tarde demais e não conseguir interromper falhas em cascata que podem terminar em grandes interrupções.

No modelo comum, serviços enviam relatórios sobre o status, e essas informações são agregadas para fornecer uma exibição geral do estado de integridade do seu aplicativo. Se você estiver usando um orquestrador, poderá fornecer informações de integridade para o cluster do orquestrador para que o cluster possa atuar adequadamente. Se você investir em relatórios de integridade de alta qualidade personalizados para seu aplicativo, poderá detectar e corrigir problemas do seu aplicativo em execução muito mais facilmente.

## <a name="implementing-health-checks-in-aspnet-core-services"></a>Implementação de verificações de integridade nos serviços do ASP.NET Core

Ao desenvolver um aplicativo Web ou um microsserviço ASP.NET Core, use uma biblioteca fora de banda (não oficial como parte do ASP.NETCore) chamada `HealthChecks` da equipe do ASP.NET. Ela está disponível neste [repositório GitHub](https://github.com/dotnet-architecture/HealthChecks).

Essa biblioteca é fácil de usar e fornece recursos que permitem que você valide se qualquer recurso externo específico necessário para o seu aplicativo (como um banco de dados do SQL Server ou a API remota) está funcionando corretamente. Quando você usa essa biblioteca, também pode decidir o que significa o recurso estar íntegro, como explicaremos mais adiante.

Para usar essa biblioteca, você precisa primeiro usar a biblioteca em seus microsserviços. Em segundo lugar, é necessário um aplicativo de front-end que consulte os relatórios de integridade. O aplicativo de front-end pode ser um aplicativo de relatório personalizado, ou pode ser um orquestrador em si que pode reagir de acordo para os estados de integridade.

### <a name="using-the-healthchecks-library-in-your-back-end-aspnet-microservices"></a>Usando a biblioteca de HealthChecks em seus microsserviços ASP.NET de back-end

Você pode ver como a biblioteca HealthChecks é usada no aplicativo de exemplo eShopOnContainers. Para começar, você precisa definir o que constitui o status íntegro para cada microsserviço. No aplicativo de exemplo, os microsserviços estão íntegros se a API de microsserviços está acessível por meio de HTTP e se o banco de dados do SQL Server relacionado também está disponível.

No futuro, você poderá instalar a biblioteca de HealthChecks como um pacote do NuGet. Porém, no momento da redação deste artigo, você precisa baixar e compilar o código como parte da sua solução. Clone o código disponível em https://github.com/dotnet-architecture/HealthChecks e copie as seguintes pastas para sua solução:

  - src/common
  - src/Microsoft.AspNetCore.HealthChecks
  - src/Microsoft.Extensions.HealthChecks
  - src/Microsoft.Extensions.HealthChecks.SqlServer

Você também pode usar verificações adicionais, como aquelas para o Azure (Microsoft.Extensions.HealthChecks.AzureStorage), mas como essa versão do eShopOnContainers não tem nenhuma dependência do Azure, não é necessário. Você não precisa de verificações de integridade do ASP.NET, pois o eShopOnContainers está baseado no ASP.NET Core.

A Figura 10-6 mostra a biblioteca HealthChecks no Visual Studio, pronta para ser usada como um bloco de construção por qualquer microsserviço.

![](./media/image6.png)

**Figura 10-6**. Código-fonte da biblioteca HealthChecks do ASP.NET Core em uma solução do Visual Studio

Conforme apresentado anteriormente, a primeira coisa a fazer em cada projeto de microsserviço é adicionar uma referência às três bibliotecas HealthChecks. Depois disso, você adiciona as ações de verificação de integridade que deseja executar naquele microsserviço. Essas ações são basicamente as dependências de outros microsserviços (HttpUrlCheck) ou bancos de dados (atualmente SqlCheck\* para bancos de dados do SQL Server). Você adiciona a ação dentro da classe de Inicialização de cada microsserviço ASP.NET ou aplicativo Web ASP .NET.

Cada serviço ou aplicativo Web deve ser configurado com a adição de todas as suas dependências HTTP ou do banco de dados como um método AddHealthCheck. Por exemplo, o aplicativo Web MVC de eShopOnContainers depende de muitos serviços, portanto, tem vários métodos AddCheck adicionados às verificações de integridade.

Por exemplo, no código a seguir, você pode ver como o microsserviço de catálogo adiciona uma dependência no seu banco de dados do SQL Server.

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

No entanto, o aplicativo Web MVC do eShopOnContainers tem várias dependências de outros microsserviços. Portanto, ele chama um método AddUrlCheck para cada microsserviço, conforme mostra o exemplo a seguir:

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

Assim, um microsserviço não fornecerá um status "íntegro" até que todas as suas verificações também estejam íntegras.

Se o microsserviço não tiver uma dependência de um serviço ou do SQL Server, você deverá adicionar apenas uma verificação de Healthy("Ok"). O código a seguir é do microsserviço basket.api de eShopOnContainers. (O microsserviço de cesta usa o Cache Redis, mas a biblioteca ainda não inclui um provedor de verificação de integridade do Redis.)

```csharp
services.AddHealthChecks(checks =>
{
    checks.AddValueTaskCheck("HTTP Endpoint", () => new
        ValueTask<IHealthCheckResult>(HealthCheckResult.Healthy("Ok")));
});
```

Para um serviço ou aplicativo Web expor o ponto de extremidade de verificação de integridade, ele deverá habilitar o método de extensão UseHealthChecks(\[*url\_for\_health\_checks*\]). Esse método vai no nível do WebHostBuilder no método principal da classe Programa do seu serviço ASP.NET Core ou aplicativo Web, logo após UseKestrel, conforme mostrado no código a seguir.

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

O processo funciona da seguinte maneira: cada microsserviço expõe o ponto de extremidade /hc. Esse ponto de extremidade é criado pela biblioteca HealthChecks do middleware ASP.NET Core. Quando esse ponto de extremidade é invocado, ele executa todas as verificações de integridade configuradas no método AddHealthChecks na classe de Inicialização.

O método UseHealthChecks espera uma porta ou um caminho. Essa porta ou caminho é o ponto de extremidade a ser usado para verificar o estado de integridade do serviço. Por exemplo, o catálogo microsserviço usa o caminho /hc.

### <a name="caching-health-check-responses"></a>Armazenando em cache as respostas de verificação de integridade

Uma vez que você não deseja causar uma DoS (Negação de Serviço) nos seus serviços, ou simplesmente não desejar afetar o desempenho do serviço verificando recursos com muita frequência, você pode armazenar em cache os retornos e configurar uma duração de cache para cada verificação de integridade.

Por padrão, a duração do cache está definida internamente como 5 minutos, mas você pode alterar essa duração do cache em cada verificação de integridade, como no código a seguir:

```csharp
checks.AddUrlCheck(Configuration["CatalogUrl"],1); // 1 min as cache duration
```

### <a name="querying-your-microservices-to-report-about-their-health-status"></a>Consultando seus microsserviços para relatar sobre o status da integridade

Quando você tiver configurado as verificações de integridade, conforme descrito aqui, quando o microsserviço estiver em execução no Docker, você poderá verificar diretamente de um navegador se ele estiver íntegro. (Isso requer que você esteja publicando a porta do contêiner do host do Docker para que possa acessar o contêiner por meio de localhost ou pelo IP de host externo do Docker.) A Figura 10-7 mostra uma solicitação em um navegador e as respostas correspondentes.

![](./media/image7.png)

**Figura 10-7**. Verificando o status da integridade de um único serviço em um navegador

No teste, você pode ver que o microsserviço catalog.api (em execução na porta 5101) está íntegro, retornando o status HTTP 200 e informações de status em JSON. Isso significa, ainda, que o serviço também verificou internamente a integridade de sua dependência do banco de dados do SQL Server e que a verificação de integridade relatou a si própria como íntegra.

## <a name="using-watchdogs"></a>Usando watchdogs

Um watchdog é um serviço separado que pode inspecionar a integridade e a carga entre serviços e relatar a integridade sobre os microsserviços consultando a biblioteca HealthChecks apresentada anteriormente. Isso pode ajudar a evitar erros que não seriam detectados com base no modo de exibição de um único serviço. Watchdogs também são um bom lugar para hospedar código que pode realizar ações de correção para condições conhecidas sem interação do usuário.

O exemplo de eShopOnContainers contém uma página da Web que exibe os relatórios de verificação de integridade de exemplo, conforme mostra a Figura 10-8. Este é o watchdog mais simples que você pode ter, já que ele simplesmente mostra o estado dos aplicativos Web e dos microsserviços em eShopOnContainers. Geralmente, um watchdog também executa ações quando detecta estados não íntegro.

![](./media/image8.png)

**Figura 10-8**. Relatório de verificação de integridade de exemplo em eShopOnContainers

Em resumo, o middleware ASP.NET da biblioteca HealthChecks do ASP.NET Core fornece um ponto de extremidade de verificação de integridade único para cada microsserviço. Isso executará todas as verificações de integridade definidas dentro dele e retornará um estado de integridade geral dependendo todas essas verificações.

A biblioteca HealthChecks é extensível via novas verificações de integridade dos futuros recursos externos. Por exemplo, esperamos que no futuro a biblioteca tenha verificações de integridade para o Cache Redis e para outros bancos de dados. A biblioteca permite relatório de integridade por várias dependências de aplicativo ou serviço, e você pode executar as ações com base nessas verificações de integridade.

## <a name="health-checks-when-using-orchestrators"></a>Verificações de integridade ao usar orquestradores

Para monitorar a disponibilidade de seus microsserviços, orquestradores como Docker Swarm, Kubernetes e Service Fabric periodicamente realizam verificações de integridade enviando solicitações para testar os microsserviços. Quando um orquestrador determina que um serviço/contêiner não está íntegro, ele para de rotear solicitações para aquela instância. Ele também geralmente cria uma nova instância do contêiner.

Por exemplo, a maioria dos orquestradores pode usar verificações de integridade para gerenciar implantações de tempo de inatividade zero. Somente quando o status de um serviço/contêiner é alterado para íntegro o orquestrador começa a rotear o tráfego para instâncias de serviço/contêiner.

O monitoramento de integridade é especialmente importante quando um orquestrador executa uma atualização do aplicativo. Alguns orquestradores (como o Azure Service Fabric) atualizam os serviços em fases, por exemplo, podem atualizar um quinto da superfície de cluster para cada upgrade de aplicativo. O conjunto de nós que é atualizado ao mesmo tempo é referido como um *domínio de atualização*. Depois de cada domínio de atualização ter sido atualizado e estar disponível para os usuários, esse domínio de atualização deverá passar por verificações de integridade antes que a implantação passe para o próximo domínio de atualização.

Outro aspecto da integridade de serviço são as métricas de relatório do serviço. Este é uma funcionalidade avançada do modelo de integridade de alguns orquestradores, como o Service Fabric. As métricas são importantes ao usar um orquestrador, pois elas são usadas para equilibrar o uso de recursos. As métricas também podem ser um indicador de integridade do sistema. Por exemplo, você pode ter um aplicativo com muitos microsserviços, e cada instância relata uma métrica de RPS (solicitações por segundo). Se um serviço estiver usando mais recursos (memória, processador etc.) que outro, o orquestrador poderá mover instâncias de serviço do cluster para tentar manter até mesmo a utilização de recursos.

Observe que se você estiver usando o Azure Service Fabric, ele fornecerá seu próprio [modelo de Monitoramento de Integridade](https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction), que é mais avançada do que simples verificações de integridade.

## <a name="advanced-monitoring-visualization-analysis-and-alerts"></a>Monitoramento avançado: visualização, análise e alertas

A parte final do monitoramento é visualizar o fluxo de eventos, relatar o desempenho do serviço e alertar quando for detectado um problema. Você pode usar diferentes soluções para esse aspecto do monitoramento.

Você pode usar aplicativos personalizados simples que mostrem o estado de seus serviços, como a página personalizada que mostramos ao explicar o [ASP.NET Core HealthChecks](https://github.com/aspnet/HealthChecks). Ou você pode usar as ferramentas mais avançadas, como Azure Application Insights e Operations Management Suite para gerar alertas com base em fluxo de eventos.

Por fim, se você estava armazenando todos os fluxos de eventos, pode usar Microsoft Power BI ou uma solução de terceiros, como Kibana ou Splunk, para visualizar os dados.

## <a name="additional-resources"></a>Recursos adicionais

-   **ASP.NET Core HealthChecks** (versão inicial) [*https://github.com/aspnet/HealthChecks/*](https://github.com/aspnet/HealthChecks/)

-   **Introdução ao monitoramento de integridade do Service Fabric**
    [*https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction*](https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction)

-   **Azure Application Insights**
    [*https://azure.microsoft.com/services/application-insights/*](https://azure.microsoft.com/services/application-insights/)

-   **Microsoft Operations Management Suite**
    [*https://www.microsoft.com/en-us/cloud-platform/operations-management-suite*](https://www.microsoft.com/en-us/cloud-platform/operations-management-suite)

>[!div class="step-by-step"]
[Anterior] (implement-circuit-breaker-pattern.md) [Próximo] (../secure-net-microservices-web-applications/index.md)
