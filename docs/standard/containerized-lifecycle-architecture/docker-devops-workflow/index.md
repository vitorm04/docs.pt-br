---
title: Fluxo de trabalho de DevOps de aplicativos do Docker com as ferramentas da Microsoft
description: Em contêineres Docker ciclo de vida do fluxo de trabalho Microsoft Platform e ferramentas de DevOps com ferramentas da Microsoft
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 11/23/2018
ms.openlocfilehash: a2d88dda9f3560675fcb6826960c6e76fa7daf92
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/13/2019
ms.locfileid: "56219069"
---
# <a name="docker-application-devops-workflow-with-microsoft-tools"></a>Fluxo de trabalho de DevOps de aplicativos do Docker com as ferramentas da Microsoft

Microsoft Visual Studio, o serviços de DevOps do Azure, o Team Foundation Server e o Application Insights fornecem um ecossistema abrangente para desenvolvimento e operações de TI que proporcionam à sua equipe as ferramentas para gerenciar projetos e rapidamente criar, testar e implantar aplicativos em contêineres.

Com o Visual Studio e serviços do Azure DevOps na nuvem, juntamente com o Team Foundation Server local, as equipes de desenvolvimento produtiva podem criar, testar e liberar aplicativos em contêineres direcionados para qualquer plataforma (Windows ou Linux).

Ferramentas da Microsoft podem automatizar o pipeline para implementações específicas de aplicativos em contêineres — Docker, .NET Core ou qualquer combinação com outras plataformas — desde compilações globais e CI (integração contínua) e testes com serviços de DevOps do Azure ou a equipe Foundation Server, a CD (implantação contínua) para ambientes do Docker (desenvolvimento, preparo, produção) e para transmitir informações de análise sobre os serviços para a equipe de desenvolvimento por meio do Application Insights. Cada confirmação de código pode iniciar uma compilação (CI) e implantar automaticamente os serviços em ambientes em contêineres específicos (CD).

Os desenvolvedores e testadores podem provisionar ambientes de desenvolvimento e teste semelhante à produção com rapidez e facilidade baseados no Docker usando modelos no Microsoft Azure.

A complexidade do desenvolvimento de aplicativos em contêineres aumenta de maneira estável dependendo das necessidades de complexidade e escalabilidade do negócio. Um bom exemplo disso são os aplicativos baseados em arquiteturas de microsserviços. Para ter êxito nesse ambiente, o projeto precisa automatizar todo o ciclo de vida — não apenas a compilação e implantação, mas ele também deve gerenciar versões junto com a coleta de telemetria. Serviços de DevOps do Azure e o Azure oferecem os seguintes recursos:

-   Gerenciamento de código de origem de DevOps Services/Team Foundation Server do Azure (baseado em Git ou Team Foundation Version Control), planejamento Agile (Agile, Scrum e CMMI têm suporte), CI, gerenciamento de versão e outras ferramentas para equipes Agile.

-   Azure DevOps Services/Team Foundation Server incluem um ecossistema avançado e crescente de extensões de primeiro e terceiro com a qual você facilmente pode construir um CI, de compilação, teste, entrega e gerenciamento pipeline para microsserviços da versão.

-   Execute testes automatizados como parte de seu pipeline de compilação nos serviços de DevOps do Azure.

-   Serviços de DevOps do Azure pode aumentar o DevOps ciclo de vida com a entrega em vários ambientes, não apenas para ambientes de produção, mas também para teste, incluindo um / experimentação de B [versões canário](https://martinfowler.com/bliki/CanaryRelease.html)e assim por diante.

-   As organizações podem provisionar facilmente contêineres do Docker com base em imagens privadas armazenadas no Registro de Contêiner do Azure juntamente com as dependências em componentes do Azure (Dados, PaaS, etc.) usando modelos do Azure Resource Manager com ferramentas com a qual elas já estão familiarizadas a trabalhar.

>[!div class="step-by-step"]
>[Anterior](../design-develop-containerized-apps/build-aspnet-core-applications-linux-containers-aks-kubernetes.md)
>[Próximo](docker-application-outer-loop-devops-workflow.md)