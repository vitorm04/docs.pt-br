---
title: Monitoramento da integridade
description: Explore uma maneira de implementar o monitoramento de integridade.
ms.date: 03/02/2020
ms.openlocfilehash: 88354ae0ae59dbfbe40dbe1b25320f8f93d042ce
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2020
ms.locfileid: "80988850"
---
# <a name="health-monitoring"></a>Monitoramento da integridade

O monitoramento de integridade pode permitir informações quase em tempo real sobre o estado de seus contêineres e microsserviços. O monitoramento de integridade é fundamental para vários aspectos da operação de microsserviços e é especialmente importante quando orquestradores executam upgrades parciais de aplicativo em fases, conforme explicado posteriormente.

Aplicativos baseados em microsserviços geralmente usam pulsações ou verificações de integridade para habilitar seus monitores de desempenho, agendadores e orquestradores a controlar a variedade de serviços. Se os serviços não puderem enviar algum tipo de sinal de "estou vivo", seja sob demanda ou em um cronograma, seu aplicativo pode enfrentar riscos quando você implantar atualizações, ou pode apenas detectar falhas tarde demais e não ser capaz de parar falhas em cascata que podem acabar em grandes paralisações.

No modelo comum, serviços enviam relatórios sobre o status, e essas informações são agregadas para fornecer uma exibição geral do estado de integridade do seu aplicativo. Se você estiver usando um orquestrador, você pode fornecer informações de saúde para o cluster do seu orquestrador, para que o cluster possa agir de acordo. Se você investir em relatórios de integridade de alta qualidade personalizados para seu aplicativo, poderá detectar e corrigir problemas do aplicativo em execução com muito mais facilidade.

## <a name="implement-health-checks-in-aspnet-core-services"></a>Implementar verificações de integridade nos serviços do ASP.NET Core

Ao desenvolver um ASP.NET microserviço Core ou aplicativo web, você pode usar o recurso de verificação de saúde incorporado que foi lançado no ASP .NET Core 2.2 ([Microsoft.Extensions.Diagnostics.HealthChecks](https://www.nuget.org/packages/Microsoft.Extensions.Diagnostics.HealthChecks)). Assim como muitas funcionalidades do ASP.NET Core, as verificações de integridade são fornecidas com um conjunto de serviços e um middleware.

O middleware e os serviços de verificação de integridade são fáceis de usar e fornecem funcionalidades que permitem validar se algum recurso externo necessário para seu aplicativo (como um banco de dados do SQL Server ou uma API remota) está funcionando corretamente. Quando você usa essa funcionalidade, também pode decidir o que significa se o recurso está íntegro, como explicaremos mais adiante.

Para usar essa funcionalidade com eficiência, você precisará primeiro configurar serviços em seus microsserviços. Em segundo lugar, é necessário um aplicativo de front-end que consulte os relatórios de integridade. O aplicativo de front-end pode ser um aplicativo de relatório personalizado ou um orquestrador em si que pode reagir de acordo com os estados de integridade.

### <a name="use-the-healthchecks-feature-in-your-back-end-aspnet-microservices"></a>Usar a funcionalidade HealthChecks nos microsserviços de back-end do ASP.NET

Nesta seção, você aprenderá como implementar o recurso HealthChecks em uma amostra ASP.NET aplicativo de API da Web Core 3.1 ao usar o pacote [Microsoft.Extensions.Diagnostics.HealthChecks.](https://www.nuget.org/packages/Microsoft.Extensions.Diagnostics.HealthChecks) A implementação desse recurso em microserviços em larga escala, como o eShopOnContainers, é explicada na próxima seção.

Para começar, você precisa definir o que constitui o status íntegro para cada microsserviço. Na aplicação da amostra, definimos que o microserviço é saudável se sua API estiver acessível via HTTP e seu banco de dados SQL Server relacionado também estiver disponível.

No .NET Core 3.1, com as APIs incorporadas, você pode configurar os serviços, adicionar uma Verificação de Saúde para o microserviço e seu banco de dados SQL Server dependente desta forma:

```csharp
// Startup.cs from .NET Core 3.1 Web API sample
//
public void ConfigureServices(IServiceCollection services)
{
    //...
    // Registers required services for health checks
    services.AddHealthChecks()
        // Add a health check for a SQL Server database
        .AddCheck(
            "OrderingDB-check",
            new SqlConnectionHealthCheck(Configuration["ConnectionString"]),
            HealthStatus.Unhealthy,
            new string[] { "orderingdb" });
}
```

No código anterior, `services.AddHealthChecks()` o método configura uma verificação HTTP básica que retorna um código de status **200** com "Saudável".  Além disso, o `AddCheck()` método `SqlConnectionHealthCheck` de extensão configura um costume que verifica a saúde do Banco de Dados SQL relacionado.

O método `AddCheck()` adiciona uma nova verificação de integridade com um nome especificado e a implementação do tipo `IHealthCheck`. Você pode adicionar várias verificações de saúde usando o método AddCheck, para que um microserviço não forneça um status "saudável" até que todas as suas verificações estejam saudáveis.

`SqlConnectionHealthCheck` é uma classe personalizada que implementa `IHealthCheck`, que usa uma cadeia de conexão como um parâmetro de construtor e executa uma consulta simples para verificar se a conexão com o Banco de Dados SQL foi bem-sucedida. Ela retornara `HealthCheckResult.Healthy()` se a consulta for executada com êxito e um `FailureStatus` com a exceção real em caso de falha.

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

Observe que, no código anterior, `Select 1` é a consulta usada para verificar a Integridade do banco de dados. Para monitorar a disponibilidade de seus microsserviços, orquestradores como kubernetes realizam periodicamente verificações de saúde enviando solicitações para testar os microsserviços. É importante manter suas consultas de banco de dados eficientes para que essas operações sejam rápidas e não resultem em uma maior utilização de recursos.

Finalmente, adicione um middleware que responda ao caminho `/hc`da url:

```csharp
// Startup.cs from .NET Core 3.1 Web Api sample
//
public void Configure(IApplicationBuilder app, IHostingEnvironment env)
{
    //…
    app.UseEndpoints(endpoints =>
    {
        //...
        endpoints.MapHealthChecks("/hc");
        //...
    });
    //…
}
```

Quando o ponto de extremidade `<yourmicroservice>/hc` é invocado, ele executa todas as verificações de integridade configuradas no método `AddHealthChecks()` na classe de Inicialização e mostra o resultado.

### <a name="healthchecks-implementation-in-eshoponcontainers"></a>Implementação de HealthChecks no eShopOnContainers

Os microsserviços do eShopOnContainers dependem de vários serviços para realizar suas tarefas. Por exemplo, o microsserviço `Catalog.API` do eShopOnContainers depende de muitos serviços, como Armazenamento de Blobs do Azure, SQL Server e RabbitMQ. Portanto, ele tem várias verificações de integridade adicionadas usando o método `AddCheck()`. Para cada serviço dependente, uma implementação personalizada `IHealthCheck` que define seu respectivo estado de saúde precisaria ser adicionada.

O projeto de código aberto [AspNetCore.Diagnostics.HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks) resolve esse problema fornecendo implementações personalizadas de verificação de saúde para cada um desses serviços corporativos, que são construídos em cima do .NET Core 3.1. Cada verificação de integridade está disponível como um pacote NuGet individual que pode ser adicionado ao projeto com facilidade. O eShopOnContainers os utiliza extensivamente em todos os seus microserviços.

Por exemplo, no microsserviço `Catalog.API`, os seguintes pacotes NuGet foram adicionados:

![Captura de tela dos pacotes AspNetCore.Diagnostics.HealthChecks NuGet.](./media/monitor-app-health/aspnet-core-diagnostics-health-checks.png)

**Figura 8-7**. Verificações de Integridade personalizadas implementadas em Catalog.API usando AspNetCore.Diagnostics.HealthChecks

No seguinte código, as implementações de verificação de integridade são adicionadas a cada serviço dependente e, em seguida, o middleware é configurado:

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

Por fim, adicione o middleware HealthCheck para ouvir o ponto final "/hc":

```csharp
// HealthCheck middleware
app.UseHealthChecks("/hc", new HealthCheckOptions()
{
    Predicate = _ => true,
    ResponseWriter = UIResponseWriter.WriteHealthCheckUIResponse
});
}
```

### <a name="query-your-microservices-to-report-about-their-health-status"></a>Consultar os microsserviços para relatar o status de integridade

Depois de configurar as verificações de integridade, como descrito neste artigo e colocar o microsserviço em execução no Docker, você poderá verificar diretamente se ele está íntegro usando um navegador. É necessário publicar a porta do contêiner no host do Docker, para que você possa acessar o contêiner por meio do IP externo do host do Docker ou por meio de `localhost`, como mostra a Figura 8-8.

![Captura de tela da resposta JSON retornada por um exame de saúde.](./media/monitor-app-health/health-check-json-response.png)

**Figura 8-8**. Verificando o status da integridade de um único serviço em um navegador

Nesse teste, você pode ver que o microsserviço `Catalog.API` (em execução na porta 5101) está íntegro, retornando o status HTTP 200 e informações de status em JSON. O serviço também verificou a integridade de sua dependência do banco de dados do SQL Server e do RabbitMQ e, portanto, a verificação de integridade relatou a si própria como íntegra.

## <a name="use-watchdogs"></a>Usar watchdogs

Um watchdog é um serviço separado que pode inspecionar a integridade e a carga entre serviços e relatar a integridade dos microsserviços consultando a biblioteca `HealthChecks` já apresentada. Isso pode ajudar a evitar erros que não seriam detectados com base no modo de exibição de um único serviço. Os watchdogs também são um bom local para hospedar os códigos que podem realizar ações de correção para condições conhecidas sem qualquer interação com o usuário.

O exemplo de eShopOnContainers contém uma página da Web que exibe os relatórios de verificação de integridade de exemplo, como mostra a Figura 8-9. Este é o watchdog mais simples que você pode ter, pois ele mostra simplesmente o estado dos aplicativos Web e dos microsserviços no eShopOnContainers. Geralmente, um watchdog também executa ações quando detecta estados não íntegro.

Uma boa notícia é que [AspNetCore.Diagnostics.HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks) também fornece o pacote NuGet [AspNetCore.HealthChecks.UI](https://www.nuget.org/packages/AspNetCore.HealthChecks.UI/), que pode ser usado para exibir os resultados da verificação de integridade dos URIs configurados.

![Captura de tela do Health Checks UI eShopOnContainers status de saúde.](./media/monitor-app-health/health-check-status-ui.png)

**Figura 8-9**. Relatório de verificação de integridade de exemplo em eShopOnContainers

Em resumo, este serviço de cão de guarda consulta o ponto final "/hc" de cada microserviço. Isso executará todas as verificações de integridade definidas dentro dele e retornará um estado de integridade geral dependendo todas essas verificações. A HealthChecksUI é fácil de ser consumida com algumas entradas de configuração e duas linhas de código que precisam ser adicionadas no Startup.cs do serviço de watchdog.

Arquivo de configuração de exemplo para interface do usuário da verificação de integridade:

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

Arquivo Startup.cs que adiciona HealthChecksUI:

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
    app.UseHealthChecksUI(config=> config.UIPath = "/hc-ui");
    //…
}
```

## <a name="health-checks-when-using-orchestrators"></a>Verificações de integridade ao usar orquestradores

Para monitorar a disponibilidade de seus microsserviços, orquestradores como Kubernetes e Service Fabric realizam verificações de integridade periodicamente enviando solicitações para testar os microsserviços. Quando um orquestrador determina que um serviço/contêiner não está íntegro, ele para de rotear solicitações para aquela instância. Ele também geralmente cria uma nova instância do contêiner.

Por exemplo, a maioria dos orquestradores pode usar verificações de integridade para gerenciar implantações de tempo de inatividade zero. Somente quando o status de um serviço/contêiner é alterado para íntegro o orquestrador começa a rotear o tráfego para instâncias de serviço/contêiner.

O monitoramento de integridade é especialmente importante quando um orquestrador executa uma atualização do aplicativo. Alguns orquestradores (como o Azure Service Fabric) atualizam os serviços em fases, por exemplo, podem atualizar um quinto da superfície de cluster para cada upgrade de aplicativo. O conjunto de nós que é atualizado ao mesmo tempo é mencionado como um *domínio de atualização*. Depois de cada domínio de atualização ter sido atualizado e estar disponível para os usuários, esse domínio de atualização deverá passar por verificações de integridade antes que a implantação passe para o próximo domínio de atualização.

Outro aspecto da integridade do serviço são os relatórios de métrica do serviço. Este é uma funcionalidade avançada do modelo de integridade de alguns orquestradores, como o Service Fabric. As métricas são importantes ao usar um orquestrador, pois elas são usadas para equilibrar o uso de recursos. As métricas também podem ser um indicador de integridade do sistema. Por exemplo, você pode ter um aplicativo com muitos microsserviços, e cada instância relata uma métrica de RPS (solicitações por segundo). Se um serviço estiver usando mais recursos (memória, processador etc.) que outro, o orquestrador poderá mover instâncias de serviço do cluster para tentar manter até mesmo a utilização de recursos.

Observe que o Azure Service Fabric fornece seu próprio [modelo de monitoramento de integridade](/azure/service-fabric/service-fabric-health-introduction), que é mais avançado do que as verificações de integridade simples.

## <a name="advanced-monitoring-visualization-analysis-and-alerts"></a>Monitoramento avançado: visualização, análise e alertas

A parte final do monitoramento é visualizar o fluxo de eventos, informar sobre o desempenho do serviço e alertar ao detectar um problema. Você pode usar diferentes soluções para esse aspecto do monitoramento.

Você pode usar aplicativos personalizados simples que mostram o estado dos serviços, como a página personalizada mostrada na explicação do [AspNetCore.Diagnostics.HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks). Ou você pode usar ferramentas mais avançadas, como o [Azure Monitor](https://azure.microsoft.com/services/monitor/) para gerar alertas com base em fluxo de eventos.

Por fim, se você estiver armazenando todos os fluxos de eventos, poderá usar o Microsoft Power BI ou uma solução de terceiros, como o Kibana ou o Splunk, para visualizar os dados.

## <a name="additional-resources"></a>Recursos adicionais

- **HealthChecks and HealthChecks UI for ASP.NET Core** \
  <https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks>

- **Introdução ao monitoramento de saúde do Tecido de Serviço** \
  [https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction](/azure/service-fabric/service-fabric-health-introduction)

- **Azure Monitor** \
  <https://azure.microsoft.com/services/monitor/>

>[!div class="step-by-step"]
>[Próximo](implement-circuit-breaker-pattern.md)
>[anterior](../secure-net-microservices-web-applications/index.md)
