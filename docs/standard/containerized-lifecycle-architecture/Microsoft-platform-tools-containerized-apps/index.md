---
title: Introdução à plataforma e ferramentas da Microsoft para aplicativos em contêineres
description: Containerized Docker Application Lifecycle with Microsoft Platform and Tools (Ciclo de vida de aplicativo do Docker em contêineres com a plataforma e as ferramentas da Microsoft)
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/21/2017
ms.openlocfilehash: bc13a0c8d6f14b8ea7ea2017009ba074f9a96ab3
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/20/2018
ms.locfileid: "46473292"
---
# <a name="introduction-to-the-microsoft-platform-and-tools-for-containerized-apps"></a>Introdução à plataforma e ferramentas da Microsoft para aplicativos em contêineres


A Figura 3-1 mostra os pilares principais no ciclo de vida de aplicativos do Docker classificados por tipo de trabalho entregue por várias equipes (desenvolvimento de aplicativos, processos de infraestrutura de DevOps e o gerenciamento e operações de TI). Normalmente na empresa, os perfis de "a pessoa" responsável para cada área são diferentes. Suas habilidades também são diferentes.

![](./media/image1.png)

Figura 3-1: principais pilares no ciclo de vida de aplicativos do Docker em contêineres com a plataforma e ferramentas da Microsoft

Um fluxo de trabalho do ciclo de vida do Docker pode ser inicialmente prescritivo com base nas “opções padrão de produto”, tornando mais fácil para os desenvolvedores começar a trabalhar mais rapidamente, porém é fundamental haver uma estrutura aberta nos bastidores para que o fluxo de trabalho seja flexível e tenha a capacidade de ajustar-se aos diferentes contextos de cada organização ou empresa. A infraestrutura de fluxo de trabalho (componentes e produtos) deve ser flexível o suficiente para abranger o ambiente que cada empresa terá no futuro, mesmo sendo capaz de trocar de desenvolvimento ou produtos de DevOps por outros. Essa flexibilidade, a abertura e a ampla variedade de tecnologias na plataforma e infraestrutura são precisamente as prioridades da Microsoft para aplicativos em contêineres do Docker, conforme explicado nos capítulos a seguir.

A Tabela 3-1 demonstra que a intenção do Microsoft DevOps com relação aos aplicativos em contêineres do Docker é fornecer um fluxo de trabalho de DevOps livre para que você possa escolher quais produtos usar para cada fase (da Microsoft ou de terceiros), proporcionando um fluxo de trabalho simplificado que fornece “produtos padrão” já conectados. Dessa forma, você pode começar rapidamente com o fluxo de trabalho de DevOps de nível corporativo para aplicativos do Docker.

Tabela 3-1: fluxo de trabalho de DevOps livre para qualquer tecnologia

| Host | Tecnologias da Microsoft | Terceiros — Conectável ao Azure |
| ---------------------------| ----------------------------------------------------| --------------------------------------------------------------------------------|
| Plataforma para aplicativos do Docker   | • Microsoft Visual Studio e Visual Studio Code<br /> • .NET<br /> • Serviço de Contêiner do Microsoft Azure<br /> • Azure Service Fabric<br /> • Registro de Contêiner do Azure<br /> | • Qualquer editor de código (por exemplo, Sublime)<br /> • Qualquer linguagem (Node.js, Java, Go, etc.)<br /> • Qualquer orquestrador e agendador<br /> • Qualquer registro do Docker<br /> |
| DevOps para aplicativos do Docker     | • Serviços do DevOps do azure<br /> • Microsoft Team Foundation Server<br /> • Serviço de Contêiner do Azure<br /> • Azure Service Fabric<br /> | • GitHub, Git, Subversion, etc.<br /> • Jenkins, Chef, Puppet, Velocity, CircleCI, TravisCI, etc.<br /> • Docker Datacenter, Docker Swarm, Mesos DC/OS, Kubernetes, etc. local<br /> |
| Gerenciamento e monitoramento  | • Operations Management Suite<br /> • Applications Insights<br /> | • Marathon, Chronos, etc.<br />

A plataforma Microsoft e ferramentas para aplicativos em contêineres do Docker, conforme definido na tabela 3-1, incluem os seguintes componentes:

-   **Plataforma para desenvolvimento de aplicativos de Docker** O desenvolvimento de um serviço ou coleção de serviços que compõem um “aplicativo”. A plataforma de desenvolvimento fornece todo o trabalho exigido pelos desenvolvedores antes de efetuar push do código para um repositório de código compartilhado. Os serviços de desenvolvimento, implantados como contêineres, são muito semelhantes ao desenvolvimento dos mesmos aplicativos ou serviços sem o Docker. Você continuar a usar sua linguagem (.NET, Node.js, Go, etc.) e editor favoritos ou um IDE como o Visual Studio ou o Visual Studio Code. No entanto, em vez de considerar o Docker como um destino de implantação, você pode desenvolver seus serviços no ambiente do Docker. Você compila, executa, testa e depura o código em contêineres localmente, fornecendo o ambiente de destino no tempo de desenvolvimento. Ao fornecer o ambiente de destino localmente, os contêineres do Docker configuram o que ajudará a melhorar drasticamente seu ciclo de vida de DevOps. O Visual Studio e o Visual Studio Code têm extensões para integrar com contêineres do Docker em seu processo de desenvolvimento.

-   **DevOps para aplicativos do Docker** os desenvolvedores que criam aplicativos do Docker podem usar os serviços de DevOps do Azure ou qualquer outro produto de terceiros, como o Jenkins criar uma abrangente automatizado gerenciamento de ciclo de vida de aplicativos (ALM).

Com os serviços de DevOps do Azure, os desenvolvedores podem criar voltado para contêiner controlar o DevOps para um processo iterativo rápido que abrange o código-fonte de qualquer lugar (serviços de DevOps do Azure-Git, GitHub, qualquer repositório Git remoto ou Subversion), CI (integração contínua) , testes de unidade interno, inter testes de integração/serviço de contêiner, entrega contínua (CD) e o gerenciamento de liberação (RM). Os desenvolvedores também podem automatizar suas versões de aplicativo do Docker para o Serviço de Contêiner do Azure, desde o desenvolvimento até os ambientes de preparo e produção.
 
-   Gerenciamento e monitoramento da produção de TI.

**Gerenciamento** A equipe de TI pode gerenciar aplicativos de produção e serviços de várias maneiras:

-   **Portal do Azure** Se você estiver usando orquestradores de software livre e o ACS (Serviço de Contêiner do Azure) além de ferramentas de gerenciamento de cluster como o Docker Datacenter e o Mesosphere Marathon, eles podem ajudar a configurar e manter seus ambientes do Docker. Se você estiver usando o Azure Service Fabric, a ferramenta Service Fabric Explorer possibilita visualizar e configurar o cluster.

-   **Ferramentas do Docker** Você pode gerenciar seus aplicativos de contêiner usando ferramentas familiares. Não é necessário alterar suas práticas de gerenciamento existentes do Docker para mover cargas de trabalho do contêiner para a nuvem. Use as ferramentas de gerenciamento de aplicativo com as quais você já está familiarizado e conecte-se por meio de pontos de extremidade de API padrão ao orquestrador de sua escolha. Você também pode usar outras ferramentas de terceiros para gerenciar seus aplicativos do Docker, como Docker Datacenter ou até mesmo as ferramentas do Docker CLI.

-   **Ferramentas de software livre** Como o ACS expõe os pontos de extremidade de API padrão para o mecanismo de orquestração, as ferramentas mais populares são compatíveis com o ACS e, na maioria dos casos, funcionarão de imediato — incluindo visualizadores, monitoramento, ferramentas de linha de comando e até mesmo ferramentas futuras à medida que elas se tornarem disponíveis.

**Monitoramento** Ao executar ambientes de produção, é possível monitorar todos os ângulos usando o seguinte:

-   **OMS (Operations Management Suite)** A “Solução de Contêiner de OMS” pode gerenciar e monitorar os hosts de Docker e contêineres mostrando informações sobre onde seus contêineres e hosts de contêiner estão, quais contêineres estão em execução ou apresentam falha, o daemon do Docker e os logs de contêiner. Ele também mostra as métricas de desempenho como CPU, memória, rede e armazenamento para o contêiner e os hosts para ajudar você a solucionar problemas e encontrar os contêineres vizinhos barulhentos.

-   **Application Insights** Você pode monitorar aplicativos do Docker de produção apenas configurando seu SDK nos seus serviços de forma a obter dados de telemetria dos aplicativos.

Dessa forma, a Microsoft oferece uma base completa para um ciclo de vida de ponta a ponta para aplicativos do Docker em contêineres. No entanto, é *uma coleção de produtos e tecnologias que permitem que você selecione, opcionalmente e se integre a ferramentas e processos existentes*. A flexibilidade de uma abordagem ampla junto com a força da profundidade dos recursos colocam a Microsoft em uma forte posição para desenvolvimento de aplicativos em contêineres do Docker.

>[!div class="step-by-step"]
[Anterior](../Docker-application-lifecycle/containers-foundation-for-devops-collaboration.md)
[Próximo](../design-develop-containerized-apps/index.md)
