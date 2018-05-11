---
title: Tecnologias da Microsoft em aplicativos com otimização de nuvem
description: Modernizar aplicativos existentes do .NET com contêineres do Windows e de nuvem do Azure | Tecnologias da Microsoft em aplicativos com otimização de nuvem
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/28/2018
ms.openlocfilehash: ece366ee3918124bb60e367d3c7447c1d4555c72
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/10/2018
---
# <a name="microsoft-technologies-in-cloud-optimized-applications"></a>Tecnologias da Microsoft em aplicativos com otimização de nuvem

A lista a seguir descreve as ferramentas, tecnologias e soluções que são reconhecidas como os requisitos para aplicativos otimizada para a nuvem. Você pode adotar otimizada para a nuvem elementos seletivamente ou gradualmente, dependendo de suas prioridades.

-   **Infraestrutura de nuvem**: A infraestrutura que fornece a plataforma de computação, sistema operacional, rede e armazenamento. Microsoft Azure está posicionado nesse nível.

-   **Tempo de execução**: essa camada fornece o ambiente para o aplicativo seja executado. Se você estiver usando contêineres, essa camada geralmente é baseada em [mecanismo do Docker](https://docs.docker.com/engine/), em execução em hosts Linux ou em hosts do Windows. ([Contêineres do Windows](https://docs.microsoft.com/virtualization/windowscontainers/about/) têm suporte começando com o Windows Server 2016. Contêineres do Windows é a melhor escolha para aplicativos existentes do .NET Framework que são executados no Windows.)

-   **Gerenciado nuvem**: quando você escolher uma opção de nuvem gerenciado, você pode evitar a despesa e complexidade do gerenciamento e os patches de sistema operacional subjacentes infraestrutura, máquinas virtuais, de suporte e configuração de rede. Se você optar por migrar usando IaaS, você é responsável para todas as tarefas e os custos associados. Uma opção de nuvem gerenciado, você pode gerenciar apenas os aplicativos e serviços que você desenvolve. O provedor de serviços de nuvem normalmente gerencia todo o resto. Exemplos de serviços de nuvem gerenciados no Azure [banco de dados do SQL Azure](https://azure.microsoft.com/services/sql-database), [Cache Redis do Azure](https://azure.microsoft.com/services/cache/), [o banco de dados do Azure Cosmos](https://azure.microsoft.com/services/cosmos-db/), [armazenamento do Azure](https://azure.microsoft.com/services/storage/), [Banco de dados do azure para MySQL](https://azure.microsoft.com/services/mysql/), [banco de dados do Azure para PostgreSQL](https://azure.microsoft.com/services/postgresql/), [Active Directory do Azure](https://azure.microsoft.com/services/active-directory/)e os serviços de computação como gerenciados [escalas de VM define](https://azure.microsoft.com/services/virtual-machine-scale-sets/), [Azure Service Fabric](https://azure.microsoft.com/services/service-fabric/), [do serviço de aplicativo do Azure](https://azure.microsoft.com/services/app-service/), e [o serviço do Azure Kubernetes](https://azure.microsoft.com/services/container-service/).

-   **Desenvolvimento de aplicativos**: você pode escolher entre vários idiomas quando você criar aplicativos que são executados em contêineres. Este guia se concentra em [.NET](https://www.microsoft.com/net), mas você pode desenvolver aplicativos baseados no contêiner por meio de outras linguagens, como Node.js, Python, Spring/Java, ou vá.

-   **Monitoramento de telemetria, registro em log e auditoria**: A capacidade de auditoria e monitorar aplicativos e contêineres que estão em execução na nuvem é essencial para qualquer aplicativo otimizada para a nuvem. [Informações de aplicativo do Azure](https://azure.microsoft.com/services/application-insights/) e [Microsoft Operations Management Suite](https://www.microsoft.com/cloud-platform/operations-management-suite) são as principais ferramentas da Microsoft que fornecem monitoramento e auditoria para aplicativos otimizada para a nuvem.

-   **Provisionamento**: ferramentas de automação ajudarão-lo a provisionar a infraestrutura e implantar um aplicativo em vários ambientes (produção, teste, preparação). Você pode usar ferramentas como o Chef e Puppet para gerenciar o ambiente e a configuração de um aplicativo. Essa camada também pode ser implementada por meio de abordagens mais simples e mais diretas. Por exemplo, você pode implantar diretamente usando a interface de linha de comando do Azure (Azure CLI) ferramentas e, em seguida, usar a implantação contínua e pipelines de gerenciamento de versão [do Visual Studio Team Services](https://www.visualstudio.com/team-services/).

-   **Ciclo de vida do aplicativo**: [do Visual Studio Team Services](https://www.visualstudio.com/team-services/) e outras ferramentas, como Jenkins, são servidores de automação criada que ajudarão-lo a implementar pipelines CI/CD, incluindo o gerenciamento de versão.

As próximas seções deste capítulo e o passo a passo relacionado, concentre-se especificamente nos detalhes sobre a camada de tempo de execução (contêineres do Windows). O guia descreve as maneiras como você pode implantar contêineres do Windows no Windows Server 2016 (e versões posteriores) VMs e instâncias de contêiner do Azure. Ele também aborda plataformas mais avançadas de PaaS como o serviço de aplicativo do Azure e o orchestrator como Kubernetes o serviço do Azure e o Azure Service Fabric.

## <a name="monolithic-applications-can-be-cloud-optimized"></a>Aplicativos monolíticos *pode* ser otimizada para a nuvem

É importante destacar que monolítico aplicativos (que não são baseados em microservices) *pode* ser otimizada para a nuvem de aplicativos. Você pode criar e operar monolíticos aplicativos que aproveitam a modelo de computação usando uma combinação de contêineres, fornecimento contínuo e DevOps em nuvem. Se um aplicativo monolítico existente é adequado para suas metas de negócios, você pode modernizá-lo e torná-lo otimizada para a nuvem.

Da mesma forma, se monolítico aplicativos podem ser aplicativos otimizada para a nuvem, outras arquiteturas mais complexas como aplicativos de N camadas podem ser modernizadas como aplicativos otimizada para a nuvem.

>[!div class="step-by-step"]
[Anterior](reasons-to-modernize-existing-net-apps-to-cloud-optimized-applications.md)
[Próximo](what-about-cloud-native-applications.md)
