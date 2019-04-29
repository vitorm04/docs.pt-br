---
title: Fluxo de trabalho de DevOps de aplicativos do Docker com as ferramentas da Microsoft
description: Em contêineres Docker ciclo de vida do fluxo de trabalho Microsoft Platform e ferramentas de DevOps com ferramentas da Microsoft
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/15/2019
ms.openlocfilehash: 80acd58d08900da8e79f6b7388da3b10f9e4e566
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61795285"
---
# <a name="docker-application-devops-workflow-with-microsoft-tools"></a>Fluxo de trabalho de DevOps de aplicativos do Docker com as ferramentas da Microsoft

*Serviços de DevOps do Azure, Microsoft Visual Studio, Team Foundation Server e do Azure Monitor fornecem que um ecossistema abrangente para desenvolvimento e operações de TI que proporcionam à sua equipe as ferramentas para gerenciar projetos e rapidamente compilar, testar e implantar em contêineres aplicativos.*

Com o Visual Studio e serviços do Azure DevOps na nuvem, juntamente com o Team Foundation Server local, as equipes de desenvolvimento produtiva podem criar, testar e liberar aplicativos em contêineres que direcionam o Windows ou Linux.

Ferramentas da Microsoft podem automatizar o pipeline para implementações específicas de aplicativos em contêineres — Docker, .NET Core ou qualquer combinação com outras plataformas — desde compilações globais e CI (integração contínua) e testes com serviços de DevOps do Azure ou a equipe Foundation Server, a CD (implantação contínua) para ambientes do Docker (desenvolvimento, preparo, produção) e para transmitir informações de análise sobre os serviços para a equipe de desenvolvimento por meio do Azure Monitor. Cada confirmação de código pode iniciar uma compilação (CI) e implantar automaticamente os serviços em ambientes em contêineres específicos (CD).

Os desenvolvedores e testadores podem provisionar ambientes de desenvolvimento e teste semelhante à produção com rapidez e facilidade baseados no Docker usando modelos no Microsoft Azure.

A complexidade do desenvolvimento de aplicativos em contêineres aumenta de maneira estável dependendo das necessidades de complexidade e escalabilidade do negócio. Um bom exemplo dessa complexidade são os aplicativos baseados em arquiteturas de microsserviços. Para ter êxito nesse ambiente, o projeto precisa automatizar todo o ciclo de vida — não apenas a compilação e implantação, mas ele também deve gerenciar versões junto com a coleta de telemetria. Serviços de DevOps do Azure e o Azure oferecem os seguintes recursos:

- Gerenciamento de código de origem de DevOps Services/Team Foundation Server do Azure (baseado em Git ou Team Foundation Version Control), planejamento Agile (Agile, Scrum e CMMI têm suporte), CI, gerenciamento de versão e outras ferramentas para equipes Agile.

- Team Foundation Server e serviços de DevOps do Azure incluem um ecossistema avançado e crescente de extensões de primeiro e terceiro com a qual você facilmente pode construir um CI, de compilação, teste, entrega e gerenciamento pipeline para microsserviços da versão.

- Execute testes automatizados como parte de seu pipeline de compilação nos serviços de DevOps do Azure.

- Serviços de DevOps do Azure pode aumentar o DevOps ciclo de vida com a entrega em vários ambientes, não apenas para ambientes de produção, mas também para teste, incluindo um / experimentação de B [versões canário](https://martinfowler.com/bliki/CanaryRelease.html)e assim por diante.

- As organizações podem provisionar facilmente contêineres do Docker de imagens privadas armazenadas no registro de contêiner do Azure juntamente com as dependências em componentes do Azure (dados, PaaS, etc.) usando modelos do Azure Resource Manager com as ferramentas já estiver familiarizados com.

>[!div class="step-by-step"]
>[Anterior](../design-develop-containerized-apps/build-aspnet-core-applications-linux-containers-aks-kubernetes.md)
>[Próximo](docker-application-outer-loop-devops-workflow.md)
