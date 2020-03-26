---
title: Tecnologias da Microsoft em aplicativos otimizados para nuvem
description: Modernizar os aplicativos .NET existentes com contêineres Azure Cloud e Windows | Tecnologias da Microsoft em aplicativos otimizados para nuvem
ms.date: 04/28/2018
ms.openlocfilehash: c5222ba13258f9c8a40ca3b9ce240aeb9f41da63
ms.sourcegitcommit: 34dc3c0d0d0a1cc418abff259d9daa8078d00b81
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2020
ms.locfileid: "79546504"
---
# <a name="microsoft-technologies-in-cloud-optimized-applications"></a>Tecnologias da Microsoft em aplicativos otimizados para nuvem

A lista a seguir descreve as ferramentas, tecnologias e soluções que são reconhecidas como requisitos para aplicativos otimizados para nuvem. Você pode adotar elementos otimizados para nuvem de forma seletiva ou gradual, dependendo de suas prioridades.

- **Infraestrutura em nuvem**: A infra-estrutura que fornece a plataforma de computação, sistema operacional, rede e armazenamento. O Microsoft Azure está posicionado neste nível.

- **Tempo de execução**: Esta camada fornece o ambiente para que o aplicativo seja executado. Se você estiver usando contêineres, essa camada geralmente é baseada no [Docker Engine](https://docs.docker.com/engine/), executando em hosts Linux ou em hosts windows. ([Os contêineres do Windows](https://docs.microsoft.com/virtualization/windowscontainers/about/) são suportados a partir do Windows Server 2016. O Windows Containers é a melhor escolha para aplicativos .NET Framework existentes que são executados no Windows.)

- **Nuvem gerenciada**: Quando você escolhe uma opção de nuvem gerenciada, você pode evitar a despesa e a complexidade de gerenciar e suportar a infra-estrutura subjacente, VMs, patches de sO e configuração de rede. Se você optar por migrar usando iaaS, você é responsável por todas essas tarefas e pelos custos associados. Em uma opção de nuvem gerenciada, você gerencia apenas os aplicativos e serviços que desenvolve. O provedor de serviços em nuvem normalmente gerencia todo o resto. Exemplos de serviços gerenciados em nuvem no Azure incluem Banco de [Dados Azure SQL,](https://azure.microsoft.com/services/sql-database) [Azure Redis Cache,](https://azure.microsoft.com/services/cache/) [Azure Cosmos DB,](https://azure.microsoft.com/services/cosmos-db/) [Azure Storage,](https://azure.microsoft.com/services/storage/) [Azure Database for MySQL,](https://azure.microsoft.com/services/mysql/) [Azure Database for PostgreSQL,](https://azure.microsoft.com/services/postgresql/) [Azure Active Directory,](https://azure.microsoft.com/services/active-directory/)e serviços de computação gerenciados como [conjuntos de escala VM,](https://azure.microsoft.com/services/virtual-machine-scale-sets/) [Azure App Service](https://azure.microsoft.com/services/app-service/)e [Azure Kubernetes Service](https://azure.microsoft.com/services/container-service/).

- **Desenvolvimento de aplicativos**: Você pode escolher entre muitos idiomas ao criar aplicativos executados em contêineres. Este guia se concentra no [.NET,](https://dotnet.microsoft.com)mas, você pode desenvolver aplicativos baseados em contêineres usando outras linguagens, como Node.js, Python, Spring/Java ou Go.

- **Monitoramento, telemetria, registro e auditoria**: A capacidade de monitorar e auditar aplicativos e contêineres que estão sendo executados na nuvem é fundamental para qualquer aplicativo otimizado para nuvem. [O Azure Application Insights](https://azure.microsoft.com/services/application-insights/) e o [Microsoft Operations Management Suite](https://www.microsoft.com/cloud-platform/operations-management-suite) são as principais ferramentas da Microsoft que fornecem monitoramento e auditoria para aplicativos otimizados para nuvem.

- **Provisionamento**: Ferramentas de automação ajudam você a provisionar a infra-estrutura e implantar um aplicativo em vários ambientes (produção, teste, estadiamento). Você pode usar ferramentas como Chef e Puppet para gerenciar a configuração e o ambiente de um aplicativo. Essa camada também pode ser implementada usando abordagens mais simples e diretas. Por exemplo, você pode implantar diretamente usando ferramentas de interface de linha de comando Azure (Azure CLI) e, em seguida, usar os pipelines de gerenciamento de implantação e liberação contínua sustais no [Azure DevOps Services](https://azure.microsoft.com/services/devops/).

- **Ciclo de vida do aplicativo**: [Azure DevOps Services](https://azure.microsoft.com/services/devops/) e outras ferramentas, como jenkins, são servidores de automação construídos que ajudam a implementar pipelines de CI/CD, incluindo o gerenciamento de lançamentos.

As próximas seções deste capítulo e os passoados relacionados, concentram-se especificamente em detalhes sobre a camada de tempo de execução (Windows Containers). A orientação descreve como você pode implantar contêineres windows no Windows Server 2016 (e versões posteriores) VMs e Azure Container Instances. Também abrange plataformas PaaS mais avançadas, como o Azure App Service e o orquestrador, como o Azure Kubernetes Service.

## <a name="monolithic-applications-can-be-cloud-optimized"></a>Aplicações monolíticas *podem* ser otimizadas para nuvem

É importante destacar que aplicações monolíticas (aplicativos que não são baseados em microserviços) *podem* ser aplicativos otimizados para nuvem. Você pode construir e operar aplicações monolíticas que aproveitam o modelo de computação em nuvem usando uma combinação de contêineres, entrega contínua e DevOps. Se uma aplicação monolítica existente for a certa para seus objetivos de negócios, você pode modernizá-la e torná-la otimizada para a nuvem.

Da mesma forma, se os aplicativos monolíticos podem ser aplicativos otimizados para nuvem, outras arquiteturas mais complexas, como aplicativos N-Tier, também podem ser modernizadas como aplicativos otimizados para nuvem.

>[!div class="step-by-step"]
>[Próximo](reasons-to-modernize-existing-net-apps-to-cloud-optimized-applications.md)
>[anterior](what-about-cloud-native-applications.md)
