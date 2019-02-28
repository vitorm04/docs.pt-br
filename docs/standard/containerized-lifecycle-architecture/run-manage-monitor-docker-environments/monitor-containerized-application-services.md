---
title: Monitorar os serviços de aplicativo em contêineres
description: Saiba mais alguns aspectos fundamentais do monitoramento de arquiteturas de contêiner
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/15/2019
ms.openlocfilehash: 925db543617deb28590cf6631ebbda3ee96836c4
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56975739"
---
# <a name="monitor-containerized-application-services"></a>Monitorar os serviços de aplicativo em contêineres

É essencial para aplicativos dividida em vários contêineres e microsserviços ter uma maneira de monitorar e analisar o comportamento de todo o aplicativo.

## <a name="microsoft-application-insights"></a>Microsoft Application Insights

[Application Insights](https://docs.microsoft.com/azure/application-insights/app-insights-overview) é um serviço de análise extensível que monitora seu aplicativo ativo. Ele ajuda a detectar e diagnosticar problemas de desempenho e entender o que os usuários realmente fazem com seu aplicativo. Ele é projetado para desenvolvedores, com a intenção de ajudá-lo a melhorar continuamente o desempenho e a usabilidade de seus aplicativos ou serviços. Application Insights funciona com o autônomo e de web/serviços de aplicativos em uma ampla variedade de plataformas, como .NET, Java, Node. js e muitas outras plataformas, hospedados localmente ou na nuvem.

### <a name="analyzing-docker-apps-in-qa-environments-using-application-insights"></a>Análise de aplicativos do Docker em ambientes de controle de qualidade usando o Application Insights

Pois ela pertence ao Docker, você pode criar um gráfico eventos de ciclo de vida e contadores de desempenho de contêineres de Docker no Application Insights. Você só precisa executar o [imagem do Docker do aplicativo Insights](https://hub.docker.com/r/microsoft/applicationinsights/) como um contêiner em seu host e ele exibirá os contadores de desempenho para o host, bem como para as imagens do Docker. Essa imagem do Docker do Application Insights (Figura 6 - 1) ajuda você a monitorar seus aplicativos em contêineres por meio da coleta de telemetria sobre o desempenho e a atividade do seu host do Docker (ou seja, suas VMs do Linux), contêineres do Docker e os aplicativos em execução dentro deles.

![exemplo](./media/image1.png)

**Figura 6-1**. Monitoramento de contêineres e hosts do Docker do Application Insights

Quando você executa o [imagem do Docker do aplicativo Insights](https://hub.docker.com/r/microsoft/applicationinsights/) no host do Docker, que você beneficie dos seguintes:

- Telemetria sobre todos os contêineres em execução no host de ciclo de vida — Iniciar, parar e assim por diante.

- Contadores de desempenho para todos os contêineres: CPU, memória, uso de rede e muito mais.

- Se você instalou o também [SDK do Application Insights](https://docs.microsoft.com/azure/application-insights/app-insights-asp-net) nos aplicativos em execução nos contêineres, toda a telemetria desses aplicativos terá propriedades adicionais que identificam o contêiner e o computador host. Portanto, por exemplo, se você tiver instâncias de um aplicativo em execução em mais de um host, você facilmente poderá filtrar a telemetria do aplicativo pelo host.

### <a name="setting-up-application-insights-to-monitor-docker-applications-and-docker-hosts"></a>Configurando o Application Insights para monitorar aplicativos do Docker e hosts do Docker

Para criar um recurso do Application Insights, siga as instruções nos artigos apresentados na lista a seguir. Portal do Azure criará o script necessário para você.

- **Monitore aplicativos do Docker no Application Insights:** \
  <https://docs.microsoft.com/azure/application-insights/app-insights-docker>

- **Imagem do Docker de Insights de aplicativo no Hub do Docker e do GitHub:** \
  <https://hub.docker.com/r/microsoft/applicationinsights/> e \
  <https://github.com/Microsoft/ApplicationInsights-Docker>

- **Configure o Application Insights para aplicativos web do ASP.NET e ASP.NET Core:** \
  <https://docs.microsoft.com/azure/application-insights/app-insights-asp-net>

- **Application Insights para páginas da web:**  
  <https://docs.microsoft.com/azure/application-insights/app-insights-javascript>

## <a name="security-backup-and-monitoring-services"></a>Serviços de monitoramento, backup e segurança

Há muitas tarefas de suporte com muitos detalhes que você precisa lidar com para garantir que seus aplicativos e infraestrutura estão em condições de entalhe superior para dar suporte às necessidades de negócios e a situação fica mais complicada no realm de microsserviços, portanto, você precisa de uma maneira de tem exibições detalhadas e de alto nível quando você precisa realizar ação.

O Azure tem as ferramentas para gerenciar e fornecer uma exibição unificada de quatro aspectos críticos dos recursos de sua nuvem e locais:

- **Segurança**. Com o [Central de segurança do Azure](https://azure.microsoft.com/services/security-center/).
  - Obtenha visibilidade e controle sobre a segurança de suas máquinas virtuais, aplicativos e cargas de trabalho completos.
  - Centralizar o gerenciamento de suas políticas de segurança e integre ferramentas e processos existentes.
  - Detecte ameaças reais usando análise avançada.

- **Backup**. Com o [o Backup do Azure](https://azure.microsoft.com/services/backup/).
  - Evite interrupções dos negócios onerosas, cumpra metas de conformidade e proteger seus dados contra ransomware e erros humanos.
  - Mantenha seus dados de backup criptografados em trânsito e em repouso.
  - Verifique se o acesso com base na autenticação multifator para evitar uso não autorizado.

- **Monitoramento**. Com o [o monitoramento do Azure](https://azure.microsoft.com/solutions/monitoring/), [Log Analytics](https://azure.microsoft.com/services/log-analytics/), e [Application Insights](https://azure.microsoft.com/services/application-insights/).
  - Obtenha visibilidade completa a integridade e o desempenho de cargas de trabalho do Azure, aplicativos e infraestrutura.
  - Coletar dados de qualquer fonte e obtenha insights avançados em suas máquinas virtuais, contêineres e aplicativos.
  - Encontre informações que você precisa usando consultas interativas e pesquisa de texto completo. 
  - Execute análise de causa raiz com análise avançada, incluindo algoritmos de aprendizado de máquina.

- **Recursos locais**. Com o [uma nuvem híbrida realmente consistente](https://azure.microsoft.com/resources/truly-consistent-hybrid-cloud-with-microsoft-azure/).

>[!div class="step-by-step"]
>[Anterior](manage-production-docker-environments.md)
>[Próximo](../key-takeaways/index.md)
