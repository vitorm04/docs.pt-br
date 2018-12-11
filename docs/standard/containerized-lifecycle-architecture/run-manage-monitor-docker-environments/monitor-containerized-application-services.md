---
title: Monitorar os serviços de aplicativo em contêineres
description: Containerized Docker Application Lifecycle with Microsoft Platform and Tools (Ciclo de vida de aplicativo do Docker em contêineres com a plataforma e as ferramentas da Microsoft)
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: 5630bfcc3173def670e2fa780d28024799b7c2a1
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53153911"
---
# <a name="monitor-containerized-application-services"></a>Monitorar os serviços de aplicativo em contêineres

É essencial para aplicativos dividida em vários contêineres e microsserviços ter uma maneira de monitorar e analisar o comportamento do aplicativo.

## <a name="microsoft-application-insights"></a>Microsoft Application Insights

[Application Insights](https://docs.microsoft.com/azure/application-insights/app-insights-overview) é um serviço de análise extensível que monitora seu aplicativo ativo. Ele ajuda a detectar e diagnosticar problemas de desempenho e entender o que os usuários realmente fazem com seu aplicativo. Ele é projetado para desenvolvedores, com a intenção de ajudá-lo a melhorar continuamente o desempenho e a usabilidade de seus aplicativos ou serviços. Application Insights funciona com o autônomo e de web/serviços de aplicativos em uma ampla variedade de plataformas, como .NET, Java, Node. js e muitas outras plataformas, hospedados localmente ou na nuvem.

### <a name="analyzing-docker-apps-in-qa-environments-using-application-insights"></a>Análise de aplicativos do Docker em ambientes de controle de qualidade usando o Application Insights

Pois ela pertence ao Docker, você pode criar um gráfico eventos de ciclo de vida e contadores de desempenho de contêineres de Docker no Application Insights. Você só precisa executar o [imagem do Docker do aplicativo Insights](https://hub.docker.com/r/microsoft/applicationinsights/) como um contêiner em seu host e ele exibirá os contadores de desempenho para o host, bem como para as imagens do Docker. Essa imagem do Docker do Application Insights (Figura 6 - 1) ajuda você a monitorar seus aplicativos em contêineres por meio da coleta de telemetria sobre o desempenho e a atividade do seu host do Docker (ou seja, suas VMs do Linux), contêineres do Docker e os aplicativos em execução dentro deles.

![exemplo](./media/image1.png)

Figura 6-1: Monitoramento de contêineres e hosts do Docker do Application Insights

Quando você executa o [imagem do Docker do aplicativo Insights](https://hub.docker.com/r/microsoft/applicationinsights/) no host do Docker, que você beneficie dos seguintes:

-   Telemetria sobre todos os contêineres em execução no host de ciclo de vida — Iniciar, parar e assim por diante.

-   Contadores de desempenho para todos os contêineres: CPU, memória, uso de rede e muito mais.

-   Se você instalou o também [SDK do Application Insights](https://docs.microsoft.com/azure/application-insights/app-insights-asp-net) nos aplicativos em execução nos contêineres, toda a telemetria desses aplicativos terá propriedades adicionais que identificam o contêiner e o computador host. Portanto, por exemplo, se você tiver instâncias de um aplicativo em execução em mais de um host, você facilmente poderá filtrar a telemetria do aplicativo pelo host.

### <a name="setting-up-application-insights-to-monitor-docker-applications-and-docker-hosts"></a>Configurando o Application Insights para monitorar aplicativos do Docker e hosts do Docker

Para criar um recurso do Application Insights, siga as instruções nos artigos apresentados na lista a seguir. Portal do Azure criará o script necessário para você.

-   **Monitore aplicativos do Docker no Application Insights:**  [https://docs.microsoft.com/azure/application-insights/app-insights-docker](https://docs.microsoft.com/azure/application-insights/app-insights-docker)

-   **Imagem do Docker de Insights de aplicativo no Hub do Docker e do Github:**  
[https://hub.docker.com/r/microsoft/applicationinsights/](https://hub.docker.com/r/microsoft/applicationinsights/) e <https://github.com/Microsoft/ApplicationInsights-Docker>

-   **Configure o Application Insights para ASP.NET:**  
[https://docs.microsoft.com/azure/application-insights/app-insights-asp-net](https://docs.microsoft.com/azure/application-insights/app-insights-asp-net)

-   **Application Insights para páginas da web:**  
<https://docs.microsoft.com/azure/application-insights/app-insights-javascript>

## <a name="microsoft-operations-management-suite"></a>Microsoft Operations Management Suite

[Operations Management Suite](https://microsoft.com/oms) é uma solução de gerenciamento de TI simplificado que fornece o log analytics, automação, backup e recuperação de site. Com base em [consultas](https://blogs.technet.microsoft.com/msoms/2016/01/21/easy-microsoft-operations-management-suite-search-queries/) no Operations Management Suite, você pode gerar [alertas](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-monitoring-alerts) e defina a correção via [automação do Azure](https://docs.microsoft.com/azure/automation/). Ele também integra-se perfeitamente com suas soluções de gerenciamento existentes para fornecer uma única exibição de painel de controle. Operations Management Suite ajuda você a gerenciar e proteger suas instalações e infraestrutura de nuvem.

### <a name="operations-management-suitehttpsmicrosoftcomoms-container-solution-for-docker"></a>[Operations Management Suite](https://microsoft.com/oms) solução de contêiner do Docker

Além de fornecer serviços importantes por conta própria, a solução de contêiner do Operations Management Suite pode gerenciar e monitorar hosts do Docker e contêineres mostrando informações sobre onde seus contêineres e hosts de contêiner estão, quais contêineres estão em execução ou com falha e os logs de daemon e o contêiner do Docker enviados ao *stdout* e *stderr*. Ele também mostra as métricas de desempenho como CPU, memória, rede e armazenamento para o contêiner e os hosts para ajudar você a solucionar problemas e encontrar os contêineres vizinhos barulhentos.

![](./media/image2.png)

Figura 6-2: Informações sobre contêineres do Docker mostrado pelo Operations Management Suite

O Application Insights e Operations Management Suite enfocam monitorar as atividades; No entanto, Application Insights se concentra mais nos aplicativos próprios graças ao seu SDK em execução dentro do aplicativo de monitoramento. No entanto, Operations Management Suite concentra-se muito mais na infraestrutura em torno de hosts, além de oferecer uma análise profunda em logs em grande escala, fornecendo um sistema muito flexível de pesquisa/consulta controlada por dados.

Como Operations Management Suite é implementado como um serviço baseado em nuvem, você pode colocá-lo em funcionamento rapidamente com investimento mínimo nos serviços de infraestrutura. Novos recursos são entregues automaticamente, evitando contínuos com manutenção e custos de atualização.

Usando a solução de contêiner do Operations Management Suite, você pode fazer o seguinte:

-   Centralizar e correlacionar milhões de logs de contêineres do Docker em escala

-   Obter informações sobre todos os hosts de contêiner em um único local

-   Saber quais contêineres estão em execução, qual imagem estiverem em execução e onde elas estão em execução

-   Diagnosticar rapidamente os contêineres de "vizinho barulhento" que podem causar problemas em hosts de contêiner

-   Veja uma trilha de auditoria para ações em contêineres

-   Solucionar problemas exibindo e pesquisando logs centralizados sem comunicação remota para os hosts do Docker

-   Encontrar contêineres que podem ser "vizinhos barulhentos" e o consumo de recursos em excesso em um host

-   Exibir centralizadas de CPU, memória, armazenamento e informações de uso e desempenho de rede para contêineres

-   Gerar testar contêineres do Docker com a automação do Azure

Você pode ver informações sobre o desempenho executando consultas como tipo = Perf, conforme mostrado na Figura 6-3.

![DockerPerfMetricsView](./media/image3.png){width="5.78625in" height="3.25in"}

Figura 6-3: Métricas de desempenho de hosts do Docker mostrados pelo Operations Management Suite

Salvar consultas também é um recurso padrão do Operations Management Suite e pode ajudar a manter você considerar úteis e descobrir tendências no seu sistema de consultas.

**Obter mais informações** para encontrar informações sobre como instalar e configurar o Docker solução de contêiner no [Operations Management Suite](https://microsoft.com/oms), acesse <https://docs.microsoft.com/azure/log-analytics/log-analytics-containers>.

>[!div class="step-by-step"]
>[Anterior](manage-production-docker-environments.md)
>[Próximo](../key-takeaways/index.md)