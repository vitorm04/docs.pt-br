---
title: Monitorar serviços de aplicativos em contêineres
description: Containerized Docker Application Lifecycle with Microsoft Platform and Tools (Ciclo de vida de aplicativo do Docker em contêineres com a plataforma e as ferramentas da Microsoft)
ms.prod: .net
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: b3ffa6c230176e1de6269ed0b30d05711ff78704
ms.sourcegitcommit: 9a4fe1a1c37b26532654b4bbe22d702237950009
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="monitor-containerized-application-services"></a>Monitorar serviços de aplicativos em contêineres

É importante para aplicativos dividido em vários contêineres e microservices para ter uma maneira de monitorar e analisar o comportamento do aplicativo.

## <a name="microsoft-application-insights"></a>Microsoft Application Insights

[Application Insights](https://docs.microsoft.com/azure/application-insights/app-insights-overview) é um serviço de análise extensível que monitora seus aplicativos em tempo real. Ele ajuda a detectar e diagnosticar problemas de desempenho e a entender o que os usuários, na verdade, fazem com seu aplicativo. Ele foi projetado para desenvolvedores, com a intenção de ajudá-lo a melhorar continuamente o desempenho e a usabilidade dos seus serviços ou aplicativos. Application Insights trabalha com web/serviços e autônomo aplicativos em uma ampla variedade de plataformas, como .NET, Java, Node. js e muitas outras plataformas, hospedado no local ou na nuvem.

### <a name="analyzing-docker-apps-in-qa-environments-using-application-insights"></a>Analisando Docker aplicativos em ambientes de controle de qualidade usando o Application Insights

Relacionada com o Docker, você pode listar os eventos de ciclo de vida e contadores de desempenho de contêineres do Docker no Application Insights. Você só precisa executar o [imagem Application Insights Docker](https://hub.docker.com/r/microsoft/applicationinsights/) como um contêiner no seu host e será exibir contadores de desempenho para o host, bem como para as outras imagens do Docker. Esta imagem de aplicativo Insights Docker (Figura 6 - 1) ajuda você a monitorar os aplicativos em contêineres por coletar telemetria sobre o desempenho e a atividade do seu host (ou seja, suas VMs do Linux) do Docker, contêineres do Docker e os aplicativos em execução dentro deles.

![exemplo](./media/image1.png)

Figura 6-1: Application Insights monitoramento contêineres e hosts de Docker

Quando você executa o [imagem Application Insights Docker](https://hub.docker.com/r/microsoft/applicationinsights/) no host do Docker, você se beneficiar com o seguinte:

-   Telemetria sobre todos os contêineres em execução no host de ciclo de vida – Iniciar, parar e assim por diante.

-   Contadores de desempenho para todos os contêineres: CPU, memória, o uso de rede e muito mais.

-   Se você instalou o também [SDK do Application Insights](https://docs.microsoft.com/azure/application-insights/app-insights-asp-net) dos aplicativos em execução nos contêineres, telemetria desses aplicativos terão propriedades adicionais que identifica a máquina host e o contêiner. Portanto, por exemplo, se você tiver instâncias de um aplicativo em execução em mais de um host, você facilmente poderá filtrar a telemetria do seu aplicativo pelo host.

### <a name="setting-up-application-insights-to-monitor-docker-applications-and-docker-hosts"></a>Configurar o Application Insights para monitorar aplicativos do Docker e hosts de Docker

Para criar um recurso do Application Insights, siga as instruções nos artigos apresentados na lista a seguir. Portal do Azure criará o script necessário para você.

-   **Monitore aplicativos de Docker no Application Insights:**  [https://docs.microsoft.com/azure/application-insights/app-insights-docker](https://docs.microsoft.com/azure/application-insights/app-insights-docker)

-   **Imagem de Docker Insights do aplicativo no Hub do Docker e Github:**  
[https://hub.docker.com/r/microsoft/applicationinsights/](https://hub.docker.com/r/microsoft/applicationinsights/) e <https://github.com/Microsoft/ApplicationInsights-Docker>

-   **Configure o Application Insights para ASP.NET:**  
[https://docs.microsoft.com/azure/application-insights/app-insights-asp-net](https://docs.microsoft.com/azure/application-insights/app-insights-asp-net)

-   **Application Insights para páginas da web:**  
<https://docs.microsoft.com/azure/application-insights/app-insights-javascript>

## <a name="microsoft-operations-management-suite"></a>Microsoft Operations Management Suite

[Operations Management Suite](http://microsoft.com/oms) é uma solução de gerenciamento de TI simplificada que fornece análise de logs, automação, backup e recuperação de site. Com base em [consultas](https://blogs.technet.microsoft.com/msoms/2016/01/21/easy-microsoft-operations-management-suite-search-queries/) no Operations Management Suite, você pode gerar [alertas](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-monitoring-alerts) e defina correção via [automação do Azure](https://docs.microsoft.com/azure/automation/). Ele também integra-se perfeitamente com suas soluções existentes de gerenciamento para fornecer uma única exibição de painel de controle. Operations Management Suite ajuda você a gerenciar e proteger seus locais e infraestrutura de nuvem.

### <a name="operations-management-suitehttpmicrosoftcomoms-container-solution-for-docker"></a>[Operations Management Suite](http://microsoft.com/oms) solução de contêiner para Docker

Além de fornecer serviços importantes por conta própria, a solução de contêiner do Operations Management Suite pode gerenciar e monitorar o hosts de Docker e contêineres, mostrando informações sobre onde seus contêineres e hosts de contêiner são, quais contêineres estão em execução ou com falha e logs de daemon e o contêiner do Docker enviado ao *stdout* e *stderr*. Ele também mostra as métricas de desempenho como CPU, memória, rede e armazenamento para o contêiner e os hosts para ajudar você a solucionar problemas e encontrar os contêineres vizinhos barulhentos.

![](./media/image2.png)

Figura 6-2: informações sobre contêineres do Docker mostrado pelo Operations Management Suite

Application Insights e Operations Management Suite se concentrar no monitoramento de atividades; No entanto, Application Insights concentra-se mais sobre como monitorar os próprios aplicativos graças ao seu SDK em execução dentro do aplicativo. No entanto, Operations Management Suite enfoca muito mais a infraestrutura de hosts, além de oferecer uma análise detalhada em logs em escala, proporcionando um sistema muito flexível de pesquisa/consulta controlada por dados.

Como o Operations Management Suite é implementado como um serviço baseado em nuvem, você pode colocá-lo em funcionamento rapidamente com investimento mínimo nos serviços de infraestrutura. Novos recursos são entregues automaticamente, economizando de manutenção contínua e custos de atualização.

Usando a solução de contêiner do Operations Management Suite, você pode fazer o seguinte:

-   Centralizar e correlacionar milhões de registros de contêineres do Docker em escala

-   Ver informações sobre todos os hosts de contêiner em um único local

-   Saber quais contêineres estão em execução, que imagem que está sendo executado e onde eles estão executando

-   Diagnosticar rapidamente os contêineres de "vizinho barulhento" que podem causar problemas em hosts de contêiner

-   Consulte uma trilha de auditoria para ações em contêineres

-   Solucionar problemas exibindo e pesquisando logs centralizados sem remoto para os hosts de Docker

-   Localizar contêineres que podem ser "vizinhos ruídos" e o consumo de recursos em excesso em um host

-   Exibir centralizado de CPU, memória, armazenamento e informações de uso e desempenho de rede para contêineres

-   Gerar testar contêineres do Docker com automação do Azure

Você pode ver informações sobre o desempenho executando consultas como tipo = Perf, conforme mostrado na Figura 6-3.

![DockerPerfMetricsView](./media/image3.png){width="5.78625in" height="3.25in"}

Figura 6-3: métricas de desempenho dos hosts de Docker mostrados pelo Operations Management Suite

Salvar consultas também é um recurso padrão do Operations Management Suite e pode ajudar a manter as consultas que você tenha achado útil e descobre tendências em seu sistema.

**Obter mais informações** para encontrar informações sobre como instalar e configurar o Docker solução contêiner [Operations Management Suite](http://microsoft.com/oms), vá para <https://docs.microsoft.com/azure/log-analytics/log-analytics-containers>.

>[!div class="step-by-step"]
[Anterior] (gerenciar-produção-docker-environments.md) [Avançar] (... /Key-takeaways/index.MD)
