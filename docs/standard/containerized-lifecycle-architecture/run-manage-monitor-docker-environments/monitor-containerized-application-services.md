---
title: Monitorar serviços de aplicativos em contêineres
description: Saiba mais alguns aspectos fundamentais do monitoramento de arquiteturas de contêiner
ms.date: 02/15/2019
ms.openlocfilehash: e14553d510751d8a75020a1b6beb9fd7bc29596e
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65641214"
---
# <a name="monitor-containerized-application-services"></a>Monitorar serviços de aplicativos em contêineres

É essencial para aplicativos dividida em vários contêineres e microsserviços ter uma maneira de monitorar e analisar o comportamento de todo o aplicativo.

## <a name="azure-monitor"></a>Azure Monitor

[O Azure Monitor](https://azure.microsoft.com/services/monitor/) é um serviço de análise extensível que monitora seu aplicativo ativo. Ele ajuda a detectar e diagnosticar problemas de desempenho e entender o que os usuários realmente fazem com seu aplicativo. Ele é projetado para desenvolvedores, com a intenção de ajudá-lo a melhorar continuamente o desempenho e a usabilidade de seus aplicativos ou serviços. O Azure Monitor funciona com autônomo e de web/serviços aplicativos em uma ampla variedade de plataformas, como .NET, Java, Node. js e muitas outras plataformas, hospedados localmente ou na nuvem.

### <a name="additional-resources"></a>Recursos adicionais

- **Visão geral do Monitor do Azure** \
  <https://docs.microsoft.com/azure/azure-monitor/overview>

- **O que é o Application Insights?** \
  <https://docs.microsoft.com/azure/azure-monitor/app/app-insights-overview>

- **O que é monitorar métricas do Azure?** \
  <https://docs.microsoft.com/azure/azure-monitor/platform/data-platform-metrics>

- **Solução de monitoramento de contêiner no Azure Monitor** \
  <https://docs.microsoft.com/azure/azure-monitor/insights/containers>

## <a name="security-and-backup-services"></a>Serviços de backup e de segurança

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

- **Recursos locais**. Com o [uma nuvem híbrida realmente consistente](https://azure.microsoft.com/resources/truly-consistent-hybrid-cloud-with-microsoft-azure/).

>[!div class="step-by-step"]
>[Anterior](manage-production-docker-environments.md)
>[Próximo](../key-takeaways/index.md)
