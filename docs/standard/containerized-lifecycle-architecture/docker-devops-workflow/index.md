---
title: Fluxo de trabalho de DevOps de aplicativos do Docker com as ferramentas da Microsoft
description: Ciclo de vida de aplicativo do Docker em contêineres com a plataforma e as ferramentas da Microsoft, fluxo de trabalho de DevOps e ferramentas da Microsoft
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: b4a88725de78f59c62aac1bd33764db6b2e0887e
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="docker-application-devops-workflow-with-microsoft-tools"></a>Fluxo de trabalho de DevOps de aplicativos do Docker com as ferramentas da Microsoft

O Microsoft Visual Studio, Visual Studio Team Services, Team Foundation Server e Application Insights fornecem um ecossistema abrangente para desenvolvimento e operações de TI que proporcionam à sua equipe as ferramentas para gerenciar projetos e compilar, testar e implantar aplicativos em contêineres com rapidez.

Com o Visual Studio e o Visual Studio Team Services na nuvem, juntamente com o Team Foundation Server local, as equipes de desenvolvimento podem compilar, testar e liberar aplicativos em contêineres direcionados para qualquer plataforma (Windows ou Linux) de forma produtiva.

As ferramentas da Microsoft podem automatizar o pipeline para implementações específicas de aplicativos em contêineres — Docker, .NET Core ou qualquer combinação com outras plataformas — desde compilações globais e CI (Integração Contínua) e testes com o Visual Studio Team Services ou Team Foundation Server, até CD (Implantação Contínua) para ambientes do Docker (Desenvolvimento, Preparo, Produção) e para transmitir informações de análise sobre os serviços para a equipe de desenvolvimento por meio do Application Insights. Cada confirmação de código pode iniciar uma compilação (CI) e implantar automaticamente os serviços em ambientes em contêineres específicos (CD).

Os desenvolvedores e testadores podem provisionar ambientes de desenvolvimento e teste semelhante à produção com rapidez e facilidade baseados no Docker usando modelos no Microsoft Azure.

A complexidade do desenvolvimento de aplicativos em contêineres aumenta de maneira estável dependendo das necessidades de complexidade e escalabilidade do negócio. Um bom exemplo disso são os aplicativos baseados em arquiteturas de microsserviços. Para ter êxito nesse ambiente, o projeto precisa automatizar todo o ciclo de vida — não apenas o build e a implantação, mas também deve gerenciar versões junto com a coleta de telemetria. O Visual Studio Team Services e o Azure oferecem os seguintes recursos:

-   O gerenciamento de código-fonte do Visual Studio Team Services/Team Foundation Server (baseado no Git ou Controle de Versão do Team Foundation), planejamento do Agile (Agile, Scrum e CMMI têm suporte), CI, Release Management e outras ferramentas para equipes Agile.

-   O Visual Studio Team Services/Team Foundation Server inclui um ecossistema avançado e crescente de extensões internas e de terceiros com as quais você pode facilmente construir um CI, compilar, testar, entregar e gerenciar versões com pipeline para microsserviços.

-   Execute testes automatizados como parte de seu pipeline de build no Visual Studio Team Services.

-   O Visual Studio Team Services pode aprimorar o ciclo de vida de DevOps com distribuição para vários ambientes, não apenas para ambientes de produção, mas também para teste, incluindo experimentação A/B, [versões canário](https://martinfowler.com/bliki/CanaryRelease.html) e assim por diante.

-   As organizações podem provisionar facilmente contêineres do Docker com base em imagens privadas armazenadas no Registro de Contêiner do Azure juntamente com as dependências em componentes do Azure (Dados, PaaS, etc.) usando modelos do Azure Resource Manager com ferramentas com a qual elas já estão familiarizadas a trabalhar.


>[!div class="step-by-step"]
[Previous] (../design-develop-containerized-apps/set-up-windows-containers-with-powershell.md) [Next] (docker-application-outer-loop-devops-workflow.md)
