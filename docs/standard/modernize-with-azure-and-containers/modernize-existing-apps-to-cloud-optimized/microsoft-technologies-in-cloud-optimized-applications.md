---
title: Tecnologias da Microsoft em aplicativos otimizados para a nuvem
description: Modernizar aplicativos .NET existentes com contêineres do Windows e de nuvem do Azure | Tecnologias da Microsoft em aplicativos otimizados para a nuvem
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/28/2018
ms.openlocfilehash: 21ba318c3a59175dadde86ff247c6e41e7f85c0b
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64627275"
---
# <a name="microsoft-technologies-in-cloud-optimized-applications"></a>Tecnologias da Microsoft em aplicativos otimizados para a nuvem

A lista a seguir descreve as ferramentas, tecnologias e soluções que são reconhecidas como requisitos para aplicativos otimizados para a nuvem. Você pode adotar elementos otimizada para a nuvem seletivamente ou gradualmente, dependendo de suas prioridades.

- **Infraestrutura de nuvem**: A infraestrutura que fornece a plataforma de computação, sistema operacional, rede e armazenamento. Microsoft Azure é posicionado nesse nível.

- **Tempo de execução**: Essa camada fornece o ambiente para a execução do aplicativo. Se você estiver usando contêineres, essa camada geralmente se baseia no [mecanismo do Docker](https://docs.docker.com/engine/), em execução em hosts Linux ou em hosts do Windows. ([Contêineres do Windows](https://docs.microsoft.com/virtualization/windowscontainers/about/) são suportados começando com o Windows Server 2016. Contêineres do Windows é a melhor opção para aplicativos existentes do .NET Framework que são executados no Windows).

- **Gerenciado nuvem**: Quando você escolhe uma opção de nuvem gerenciado, você pode evitar os gastos e a complexidade de gerenciar e dar suporte aos patches de sistema operacional subjacentes infraestrutura, máquinas virtuais e configuração de rede. Se você optar por migrar usando IaaS, será responsável por todas essas tarefas e os custos associados. Uma opção de nuvem gerenciado, você pode gerenciar apenas os aplicativos e serviços que você desenvolve. O provedor de serviços de nuvem normalmente gerencia todo o resto. Exemplos de serviços de nuvem gerenciado no Azure [banco de dados SQL](https://azure.microsoft.com/services/sql-database), [Cache Redis do Azure](https://azure.microsoft.com/services/cache/), [do Azure Cosmos DB](https://azure.microsoft.com/services/cosmos-db/), [armazenamento do Azure](https://azure.microsoft.com/services/storage/), [Banco de dados do azure para MySQL](https://azure.microsoft.com/services/mysql/), [banco de dados do Azure para PostgreSQL](https://azure.microsoft.com/services/postgresql/), [Azure Active Directory](https://azure.microsoft.com/services/active-directory/)e gerenciadas, como os serviços de computação [de dimensionamento de VM define](https://azure.microsoft.com/services/virtual-machine-scale-sets/), [do Azure Service Fabric](https://azure.microsoft.com/services/service-fabric/), [serviço de aplicativo do Azure](https://azure.microsoft.com/services/app-service/), e [serviço Kubernetes do Azure](https://azure.microsoft.com/services/container-service/).

- **Desenvolvimento de aplicativos**: Muitas linguagens podem ser escolhidos de quando você compila aplicativos que são executados em contêineres. Este guia enfoca [.NET](https://www.microsoft.com/net), mas você pode desenvolver aplicativos baseados em contêiner usando outras linguagens, como o Node. js, Python, Spring/Java, ou ir.

- **Monitoramento, telemetria, registro e auditoria**: A capacidade de aplicativos de monitoramento e a auditoria e contêineres que estão em execução na nuvem é essencial para qualquer aplicativo otimizada para a nuvem. [O Azure Application Insights](https://azure.microsoft.com/services/application-insights/) e [Microsoft Operations Management Suite](https://www.microsoft.com/cloud-platform/operations-management-suite) são as principais ferramentas da Microsoft que fornecem monitoramento e auditoria para aplicativos otimizados para a nuvem.

- **Provisionamento**: Ferramentas de automação de ajudam você a provisionar a infraestrutura e implantar um aplicativo em vários ambientes (produção, teste, preparação). Você pode usar ferramentas como o Chef e Puppet para gerenciar a configuração de um aplicativo e o ambiente. Essa camada também pode ser implementada usando as abordagens mais simples e diretas. Por exemplo, você pode implantar diretamente por meio de interface de linha de comando do Azure (CLI do Azure) de ferramentas e, em seguida, usar a implantação contínua e liberar pipelines de gerenciamento no [serviços do Azure DevOps](https://azure.microsoft.com/services/devops/).

- **Ciclo de vida do aplicativo**: [Os serviços do Azure DevOps](https://azure.microsoft.com/services/devops/) e outras ferramentas, como Jenkins, são servidores de automação criada que ajudam você a implementar pipelines de CI/CD, incluindo o gerenciamento de versão.

As próximas seções deste capítulo e a passo a passo relacionados, concentre-se especificamente em detalhes sobre a camada de tempo de execução (contêineres do Windows). As diretrizes descrevem as maneiras que você pode implantar VMs de contêineres do Windows no Windows Server 2016 (e versões posteriores) e instâncias de contêiner do Azure. Ele também aborda a plataformas de PaaS mais avançadas, como o serviço de aplicativo do Azure e o orchestrator, como o Azure Service Fabric e serviço Kubernetes do Azure.

## <a name="monolithic-applications-can-be-cloud-optimized"></a>Aplicativos monolíticos *pode* ser otimizada para a nuvem

É importante destacar que os aplicativos (aplicativos que não são baseados em microsserviços) monolítico *pode* ser aplicativos otimizados para a nuvem. Você pode criar e operar aplicativos monolíticos que tiram proveito da nuvem do modelo de computação usando uma combinação de contêineres, entrega contínua e DevOps. Se um aplicativo monolítico existente é adequado para suas metas de negócios, você pode modernizá-lo e torná-lo otimizada para a nuvem.

Da mesma forma, se os aplicativos monolíticos podem ser aplicativos otimizados para a nuvem, outras arquiteturas mais complexas, como aplicativos de N camadas também podem ser modernizadas como aplicativos otimizados para a nuvem.

>[!div class="step-by-step"]
>[Anterior](reasons-to-modernize-existing-net-apps-to-cloud-optimized-applications.md)
>[Próximo](what-about-cloud-native-applications.md)