---
title: Tecnologias da Microsoft em aplicativos em nuvem devops pronto
description: "Arquitetura de Microservices .NET para aplicativos .NET em contêineres | Tecnologias da Microsoft em aplicativos prontos para nuvem DevOps"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.openlocfilehash: a7ce240ee89321f79b10a701cd26fa84b6006f83
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="microsoft-technologies-in-cloud-devops-ready-applications"></a>Tecnologias da Microsoft em aplicativos em nuvem devops pronto

A lista a seguir descreve as ferramentas, tecnologias e soluções que são reconhecidas como os requisitos para aplicativos de nuvem DevOps pronto. Você pode adotar aplicativos prontos para nuvem DevOps seletivamente ou gradualmente, dependendo de suas prioridades.

-   **Infraestrutura de nuvem**: A infraestrutura que fornece a plataforma de computação, sistema operacional, rede e armazenamento. Microsoft Azure está posicionado nesse nível.

-   **Tempo de execução**: essa camada fornece o ambiente para o aplicativo seja executado. Se você estiver usando contêineres, essa camada geralmente é baseada em [mecanismo do Docker](https://docs.docker.com/engine/), em execução em hosts Linux ou em hosts do Windows. ([Contêineres do Windows](https://docs.microsoft.com/virtualization/windowscontainers/about/) têm suporte começando com o Windows Server 2016. Contêineres do Windows é a melhor escolha para aplicativos existentes do .NET Framework que são executados no Windows.)

-   **Gerenciado nuvem**: quando você escolher uma opção de nuvem gerenciado, você pode evitar a despesa e complexidade do gerenciamento e os patches de sistema operacional subjacentes infraestrutura, máquinas virtuais, de suporte e configuração de rede. Se você optar por migrar usando IaaS, você é responsável para todas as tarefas e os custos associados. Uma opção de nuvem gerenciado, você pode gerenciar apenas os aplicativos e serviços que você desenvolve. O provedor de serviços de nuvem normalmente gerencia todo o resto. Exemplos de serviços de nuvem gerenciados no Azure [banco de dados do SQL Azure](https://azure.microsoft.com/services/sql-database), [Cache Redis do Azure](https://azure.microsoft.com/services/cache/), [o banco de dados do Azure Cosmos](https://azure.microsoft.com/services/cosmos-db/), [armazenamento do Azure](https://azure.microsoft.com/services/storage/), [Banco de dados do azure para MySQL](https://azure.microsoft.com/services/mysql/), [banco de dados do Azure para PostgreSQL](https://azure.microsoft.com/services/postgresql/), [Active Directory do Azure](https://azure.microsoft.com/services/active-directory/)e os serviços de computação como gerenciados [escalas de VM define](https://azure.microsoft.com/services/virtual-machine-scale-sets/), [Azure Service Fabric](https://azure.microsoft.com/services/service-fabric/), [do serviço de aplicativo do Azure](https://azure.microsoft.com/services/app-service/), e [serviço de contêiner do Azure](https://azure.microsoft.com/services/container-service/).

-   **Desenvolvimento de aplicativos**: você pode escolher entre vários idiomas quando você criar aplicativos que são executados em contêineres. Este guia, vamos nos concentrar em [.NET](https://www.microsoft.com/net), mas, você pode desenvolver aplicativos baseados no contêiner por meio de outras linguagens, como Node.js, Python, Java/Spring ou GoLang.

-   **Monitoramento de telemetria, registro em log e auditoria**: A capacidade de auditoria e monitorar aplicativos e contêineres que estão em execução na nuvem é essencial para qualquer aplicativo de nuvem DevOps pronto. [Informações de aplicativo do Azure](https://azure.microsoft.com/services/application-insights/) e [Microsoft Operations Management Suite](https://www.microsoft.com/cloud-platform/operations-management-suite) são as principais ferramentas da Microsoft que fornecem monitoramento e auditoria para aplicativos de nuvem DevOps pronto.

-   **Provisionamento**: ferramentas de automação ajudarão-lo a provisionar a infraestrutura e implantar um aplicativo em vários ambientes (produção, teste, preparação). Você pode usar ferramentas como o Chef e Puppet para gerenciar o ambiente e a configuração de um aplicativo. Essa camada também pode ser implementada por meio de abordagens mais simples e mais diretas. Por exemplo, você pode implantar diretamente usando a interface de linha de comando do Azure (Azure CLI) ferramentas e, em seguida, usar a implantação contínua e pipelines de gerenciamento de versão [do Visual Studio Team Services](https://www.visualstudio.com/team-services/).

-   **Ciclo de vida do aplicativo**: [do Visual Studio Team Services](https://www.visualstudio.com/team-services/) e outras ferramentas, como Jenkins, são servidores de automação de compilação que ajudarão-lo a implementam pipelines CI/CD, incluindo o gerenciamento de versão.

As próximas seções deste capítulo e o passo a passo relacionado, concentre-se especificamente nos detalhes sobre a camada de tempo de execução (contêineres do Windows). O guia descreve as maneiras que você pode implantar VMs de contêineres do Windows no Windows Server 2016 (e versões posteriores). Ele também aborda as camadas de orchestrator mais avançadas, como o Azure Service Fabric, Kubernetes e serviço de contêiner do Azure. Configurar camadas orchestrator é um requisito fundamental para modernizar existente do .NET Framework (Windows) aplicativos como aplicativos prontos para nuvem DevOps.

## <a name="monolithic-applications-can-be-cloud-devops-ready"></a>Aplicativos monolíticos *pode* estar pronta para a nuvem DevOps

É importante destacar que monolítico aplicativos (que não são baseados em microservices) *pode* ser aplicativos prontos para nuvem DevOps. Você pode criar e operar monolíticos aplicativos que aproveitam a modelo de computação usando uma combinação de contêineres, fornecimento contínuo e DevOps em nuvem. Se um aplicativo monolítico existente é adequado para suas metas de negócios, você pode modernizá-lo e torná-la pronta para a nuvem DevOps.

Da mesma forma, se monolítico aplicativos podem ser aplicativos prontos para nuvem DevOps, outras arquiteturas mais complexas como aplicativos de N camadas também podem ser modernizadas como aplicativos prontos para nuvem DevOps.

>[!div class="step-by-step"]
[Anterior](reasons-to-lift-and-shift-existing-net-apps-to-cloud-devops-ready-applications.md)
[Próximo](what-about-cloud-optimized-applications.md)
