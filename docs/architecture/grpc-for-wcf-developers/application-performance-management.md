---
title: Gerenciamento de desempenho de aplicativos-gRPC para desenvolvedores do WCF
description: Registro em log, métricas e rastreamento para aplicativos ASP.NET Core gRPC.
ms.date: 09/02/2019
ms.openlocfilehash: 2b6a30ab68cb6e2fdc81c59e7faef81064b948c1
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73968174"
---
# <a name="application-performance-management"></a>Gerenciamento de desempenho de aplicativos

Em ambientes de produção modernos como o kubernetes, é muito importante poder monitorar os aplicativos para garantir que eles estejam sendo executados de forma ideal. Preocupações como registro em log e métrica nunca foram mais importantes. ASP.NET Core, incluindo gRPC, tem suporte de primeira classe para produzir e gerenciar mensagens de log e dados de métrica, bem como dados de *rastreamento* . Esta seção irá explorar essas áreas em mais detalhes.

## <a name="logging-vs-metrics"></a>Registrando em log vs métricas

Antes de examinar os detalhes da implementação, é necessário entender a diferença entre registro em log e métricas.

O registro em log se preocupa com mensagens de texto que registram informações detalhadas sobre as coisas ocorridas no sistema. As mensagens de log podem incluir dados de exceção como rastreamentos de pilha ou dados estruturados que fornecem contexto sobre a mensagem. A saída de log é normalmente gravada em um repositório de texto pesquisável.

As métricas referem-se a dados numéricos que são projetados para serem agregados e apresentados usando gráficos em um painel que fornece uma visão da integridade geral e do desempenho de um aplicativo. Os dados de métricas também podem ser usados para disparar alertas automatizados quando um limite é excedido. A lista a seguir mostra alguns exemplos de dados de métricas:

- Tempo necessário para processar solicitações.
- O número de solicitações por segundo manipuladas por uma instância de um serviço.
- O número de solicitações com falha em uma instância.

## <a name="logging-in-aspnet-core-grpc"></a>Fazendo logon ASP.NET Core gRPC

O ASP.NET Core fornece suporte interno para registro em log, na forma do pacote NuGet [Microsoft. Extensions. Logging](https://www.nuget.org/packages/Microsoft.Extensions.Logging) . As principais partes dessa biblioteca estão incluídas no SDK da Web, portanto, não é necessário instalá-las manualmente. Por padrão, as mensagens de log são gravadas na saída padrão (o "console") e em qualquer depurador anexado. Para gravar logs em armazenamentos de dados externos persistentes, talvez seja necessário importar [pacotes de coletor de log opcionais](https://docs.microsoft.com/aspnet/core/fundamentals/logging/?view=aspnetcore-3.0#third-party-logging-providers).

O ASP.NET Core estrutura gRPC grava mensagens de log de diagnóstico detalhadas para essa estrutura de log para que elas possam ser processadas/armazenadas junto com as próprias mensagens do seu aplicativo.

### <a name="produce-log-messages"></a>Produzir mensagens de log

A extensão de log é automaticamente registrada com o sistema de injeção de dependência ASP.NET Core, para que você possa especificar os agentes como um parâmetro de Construtor em tipos de serviço gRPC.

```csharp
public class StockData : Stocks.StocksBase
{
    private readonly ILogger<StockData> _logger;

    public StockData(ILogger<StockData> logger)
    {
        _logger = logger;
    }
}
```

Muitas mensagens de log em relação a solicitações, exceções etc. são fornecidas pelos componentes ASP.NET Core e gRPC Framework. Adicione suas próprias mensagens de log para fornecer detalhes e contexto sobre a lógica do aplicativo em vez de preocupações de nível inferior.

Para obter mais informações sobre como gravar mensagens de log e destinos e coletores de logs disponíveis, consulte o artigo [log no .NET Core e ASP.NET Core](https://docs.microsoft.com/aspnet/core/fundamentals/logging/?view=aspnetcore-3.0) .

## <a name="metrics-in-aspnet-core-grpc"></a>Métricas no ASP.NET Core gRPC

O tempo de execução do .NET Core fornece um conjunto de componentes para emitir e observar métricas que incluem APIs como as classes <xref:System.Diagnostics.Tracing.EventSource> e <xref:System.Diagnostics.Tracing.EventCounter>. Essas APIs podem ser usadas para emitir dados numéricos básicos que podem ser consumidos por processos externos, como a [ferramenta global dotnet-Counters](https://github.com/dotnet/diagnostics/blob/master/documentation/dotnet-counters-instructions.md)ou o rastreamento de eventos para Windows. Para obter mais informações sobre como usar `EventCounter` em seu próprio código, consulte o tutorial de [introdução do EventCounter](https://github.com/dotnet/corefx/blob/master/src/System.Diagnostics.Tracing/documentation/EventCounterTutorial.md) .

Para métricas mais avançadas e para gravar dados de métrica em uma maior variedade de armazenamentos de dados, há um excelente projeto de código-fonte aberto chamado [métricas de aplicativo](https://www.app-metrics.io). Esse conjunto de bibliotecas fornece um amplo conjunto de tipos para instrumentar seu código. Ele também oferece pacotes para gravar métricas em diferentes tipos de destinos que incluem bancos de dados de série temporal, como Prometheus e InfluxDB, informações de [aplicativo Azure](https://docs.microsoft.com/azure/azure-monitor/app/app-insights-overview)e muito mais. O pacote NuGet [app. Metrics. AspNetCore. Mvc](https://www.nuget.org/packages/App.Metrics.AspNetCore.Mvc/) , inclusive, adiciona um conjunto abrangente de métricas básicas que são geradas automaticamente por meio da integração com o ASP.NET Core Framework, e o site fornece [modelos](https://www.app-metrics.io/samples/grafana/) para exibir essas métricas com a plataforma de visualização [Grafana](https://grafana.com/) .

Para obter mais informações e documentação sobre as métricas de aplicativo, consulte o site do [app-Metrics.Io](https://app-metrics.io) .

### <a name="produce-metrics"></a>Produzir métricas

A maioria das plataformas de métricas dá suporte a cinco tipos básicos de métricas, descritos na tabela a seguir:

| Tipo de métrica | Descrição |
| ----------- | ----------- |
| Contador     | Controla com que frequência algo acontece, como solicitações, erros e assim por diante. |
| Indicadores       | Registra um único valor que muda ao longo do tempo, como conexões ativas. |
| Histograma   | Mede uma distribuição de valores entre limites arbitrários. Por exemplo, um histograma pode acompanhar o tamanho do conjunto de dados, contando quantos registros contidos < 10, quantos 11-100 e 101-1000 e > 1000 registros. |
| Limitados       | Mede a taxa na qual um evento ocorre em vários intervalos de tempo. |
| Temporizador       | Controla a duração de eventos e a taxa na qual ele ocorre, armazenado como um histograma. |

Usando as *métricas de aplicativo*, uma interface `IMetrics` pode ser obtida por meio de injeção de dependência e usada para registrar qualquer uma dessas métricas para um serviço gRPC. O exemplo a seguir mostra como contar o número de solicitações de `Get` feitas ao longo do tempo:

```csharp
public class StockData : Stocks.StocksBase
{
    private static readonly CounterOptions GetRequestCounter = new CounterOptions
    {
        Name = "StockData_Get_Requests",
        MeasurementUnit = Unit.Calls
    };

    private readonly IStockRepository _repository;
    private readonly IMetrics _metrics;

    public StockData(IStockRepository repository, IMetrics metrics)
    {
        _repository = repository;
        _metrics = metrics;
    }

    public override async Task<GetResponse> Get(GetRequest request, ServerCallContext context)
    {
        _metrics.Measure.Counter.Increment(GetRequestCounter);

        // Serve request...
    }
}
```

### <a name="store-and-visualize-metrics-data"></a>Armazenar e Visualizar dados de métricas

A melhor maneira de armazenar dados de métricas está em um banco de dados de série temporal, um armazenamento de dado especializado criado para registrar séries de dados numéricas marcadas com carimbos de data */hora*. Os bancos de dados mais populares são [Prometheus](https://prometheus.io/) e [InfluxDB](https://www.influxdata.com/products/influxdb-overview/). O Microsoft Azure também fornece armazenamento de métricas dedicado por meio do serviço de [Azure monitor](https://docs.microsoft.com/azure/azure-monitor/overview) .

A solução atual para a visualização de dados de métricas é [Grafana](https://grafana.com), que funciona com uma ampla variedade de provedores de armazenamento, incluindo Azure monitor, InfluxDB e Prometheus. A imagem a seguir mostra um painel Grafana de exemplo que exibe as métricas da malha do serviço Linkerd que executa o exemplo StockData:

![Painel do Grafana](media/application-performance-management/grafana-screenshot.png)

### <a name="metrics-based-alerting"></a>Alertas baseados em métricas

A natureza numérica dos dados de métricas significa que ele é ideal para impulsionar sistemas de alerta, notificando os desenvolvedores ou engenheiros de suporte quando um valor cai fora de alguma tolerância definida. Todas as plataformas já mencionadas fornecem suporte para alertas por meio de uma variedade de opções, incluindo emails, mensagens de texto ou visualizações no painel.

## <a name="distributed-tracing"></a>Rastreamento distribuído

O *rastreamento distribuído* é um desenvolvimento relativamente recente no monitoramento, que tem surgido do uso crescente de microserviços e arquiteturas distribuídas. Uma única solicitação de um navegador cliente, aplicativo ou dispositivo pode ser dividida em várias etapas e subsolicitaçãos e envolve o uso de muitos serviços em uma rede. Isso dificulta a correlação de mensagens de log e métricas com a solicitação específica que as disparou. O rastreamento distribuído aplica identificadores a solicitações que permitem que os logs e as métricas sejam correlacionados a uma operação específica. Isso é semelhante ao [rastreamento de ponta a ponta do WCF](https://docs.microsoft.com/dotnet/framework/wcf/diagnostics/tracing/end-to-end-tracing), mas aplicado em várias plataformas.

Embora ainda seja uma área de tecnologia recente, o rastreamento distribuído cresceu rapidamente em popularidade e agora está passando por um processo de padronização. A base de computação nativa da nuvem criou o [padrão de rastreamento aberto](https://opentracing.io), tentando fornecer bibliotecas neutras ao fornecedor para trabalhar com back-ends, como [Jaeger](https://www.jaegertracing.io/) e o [APM elástico](https://www.elastic.co/products/apm). Ao mesmo tempo, o Google criou o [projeto OpenCensus](https://opencensus.io/) para abordar o mesmo conjunto de problemas. Esses dois projetos agora estão sendo mesclados em um novo projeto, [OpenTelemetry](https://opentelemetry.io), que visa ser o padrão futuro do setor.

### <a name="how-distributed-tracing-works"></a>Como funciona o rastreamento distribuído

O rastreamento distribuído baseia-se no conceito de *spans*: operações nomeadas e oportunas que fazem parte de um único *rastreamento*, o que pode envolver o processamento em vários nós de um sistema. Quando uma nova operação é iniciada, um rastreamento é criado com um identificador exclusivo. Para cada suboperação, um Span é criado com seu próprio identificador e identificador de rastreamento. À medida que a solicitação passa pelo sistema, vários componentes podem criar spans *filho* que incluem o identificador de seu *pai*. Um Span tem um *contexto*, que contém os identificadores de rastreamento e de span, bem como dados úteis na forma de pares de chave/valor (chamados de *bagagem*).

### <a name="distributed-tracing-with-diagnosticsource"></a>Rastreamento distribuído com Diagnosticname

O .NET Core tem um módulo interno que mapeia bem para rastreamentos distribuídos e abrange: [diagnosticname](https://github.com/dotnet/corefx/blob/master/src/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md#diagnosticsource-users-guide). Além de fornecer uma maneira simples de produzir e consumir diagnósticos em um processo, o módulo `DiagnosticSource` tem o conceito de uma *atividade*, que é efetivamente uma implementação de um rastreamento distribuído ou um intervalo dentro de um rastreamento. Os elementos internos do módulo cuidam das atividades pai/filho, incluindo a alocação de identificadores. Para obter mais informações sobre como usar o tipo de `Activity`, consulte o [Guia do usuário da atividade no GitHub](https://github.com/dotnet/corefx/blob/master/src/System.Diagnostics.DiagnosticSource/src/ActivityUserGuide.md#activity-user-guide)

Como o Diagnosticname faz parte da estrutura principal, ele tem suporte por vários componentes principais, incluindo <xref:System.Net.Http.HttpClient>, Entity Framework Core e ASP.NET Core, incluindo suporte explícito na estrutura gRPC. Quando ASP.NET Core recebe uma solicitação, ele verifica um par de cabeçalhos HTTP que correspondem ao padrão de [contexto de rastreamento W3C](https://www.w3.org/TR/trace-context) . Se os cabeçalhos forem encontrados, uma atividade será iniciada usando os valores de identidade e o contexto dos cabeçalhos. Se nenhum cabeçalho for encontrado, uma atividade será iniciada com valores de identidade gerados que correspondam ao formato padrão. Qualquer diagnóstico gerado pela estrutura ou pelo código do aplicativo durante o tempo de vida dessa atividade pode ser marcado com os identificadores de rastreamento e span. O suporte a `HttpClient` estende isso mais tarde, verificando se há uma atividade atual em cada solicitação e adicionando automaticamente os cabeçalhos de rastreamento à solicitação de saída.

As bibliotecas de cliente e servidor do ASP.NET Core gRPC incluem suporte explícito para Diagnosticname e atividade, e criarão atividades e aplicarão e usarão informações de cabeçalho automaticamente.

> [!NOTE]
> Tudo isso só acontece se um *ouvinte* estiver consumindo as informações de diagnóstico. Se não houver um ouvinte, nenhum diagnóstico será gravado e nenhuma atividade será criada.

### <a name="add-your-own-diagnosticsources-and-activities"></a>Adicione seu próprio DiagnosticSources e suas atividades

Embora uma boa quantidade de dados seja gerada automaticamente pelo ASP.NET Core, incluindo gRPC, bem como Entity Framework Core e `HttpClient`, talvez você queira adicionar seu próprio diagnóstico ou criar spans explícitos no código do aplicativo. Consulte o [Guia do usuário do diagnosticm](https://github.com/dotnet/corefx/blob/master/src/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md#instrumenting-with-diagnosticsourcediagnosticlistener) e o [Guia do usuário da atividade](https://github.com/dotnet/corefx/blob/master/src/System.Diagnostics.DiagnosticSource/src/ActivityUserGuide.md#activity-usage) para obter detalhes sobre como implementar seu próprio diagnóstico.

### <a name="store-distributed-trace-data"></a>Armazenar dados de rastreamento distribuído

No momento da escrita, o projeto OpenTelemetry ainda está nos estágios iniciais e apenas os pacotes de qualidade alfa estão disponíveis para aplicativos .NET. O projeto OpenTracing oferece bibliotecas mais maduras, mas elas serão substituídas pelas bibliotecas do OpenTelemetry no futuro.

A API OpenTracing é descrita abaixo. Se você preferir usar a API OpenTelemetry mais recente em seu aplicativo, consulte o repositório do [SDK do .net do OpenTelemetry no GitHub](https://github.com/open-telemetry/opentelemetry-dotnet).

#### <a name="use-the-opentracing-package-to-store-distributed-trace-data"></a>Usar o pacote OpenTracing para armazenar dados de rastreamento distribuídos

O [pacote NuGet do OpenTracing](https://www.nuget.org/packages/OpenTracing/) que dá suporte a todos os back-ends compatíveis com OpenTracing (que podem ser usados independentemente do `DiagnosticSource`). Há um pacote adicional do projeto de contribuições da API do OpenTracing, [OpenTracing. contrib. NetCore](https://www.nuget.org/packages/OpenTracing.Contrib.NetCore/), que adiciona um ouvinte `DiagnosticSource` e grava eventos e atividades em um back-end automaticamente. Habilitar esse pacote é tão simples quanto instalá-lo do NuGet e adicioná-lo como um serviço em sua classe de `Startup`.

```csharp
public class Startup
{
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddOpenTracing();
    }
}
```

O pacote OpenTracing é uma camada de abstração e, como tal, requer uma implementação específica de back-end. As implementações da API OpenTracing estão disponíveis para os seguintes back-ends de software livre.

| {1&gt;Nome&lt;1} | Pacote | Site |
| ---- | ------- | -------- |
| Jaeger | [Jaeger](https://www.nuget.org/packages/Jaeger/) | [jaegertracing.io](https://jaegertracing.io) |
| APM elástico | [Elástico. APM. NetCoreAll](https://www.nuget.org/packages/Elastic.Apm.NetCoreAll/) | [elastic.co/products/apm](https://www.elastic.co/products/apm) |

Para obter mais informações sobre a API do OpenTracing para .net, consulte os repositórios [OpenTracing for C# ](https://github.com/opentracing/opentracing-csharp) e [OpenTracing C#contrib/.NET Core](https://github.com/opentracing-contrib/csharp-netcore) no github.

>[!div class="step-by-step"]
>[Anterior](load-balancing.md)
>[Próximo](appendix.md)
