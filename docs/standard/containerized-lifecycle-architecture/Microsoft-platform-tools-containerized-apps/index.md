---
title: Introdução à plataforma e ferramentas da Microsoft para aplicativos em contêineres
description: Obtenha saber as ofertas da Microsoft para dar suporte ao ciclo de vida de aplicativos de Docker.
ms.date: 02/15/2019
ms.openlocfilehash: 9e7e821370b98fbda9af0ea69c13eaeab2f35acf
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65644902"
---
# <a name="introduction-to-the-microsoft-platform-andtools-for-containerized-apps"></a>Introdução à plataforma Microsoft e ferramentas para aplicativos em contêineres

*Visão: Criar um adaptável, empresarial, em contêineres ciclo de vida do aplicativo que abrange o desenvolvimento, operações de TI e gerenciamento de produção.*

A Figura 3-1 mostra os pilares principais no ciclo de vida de aplicativos do Docker classificados por tipo de trabalho entregue por várias equipes (desenvolvimento de aplicativos, processos de infraestrutura de DevOps e o gerenciamento e operações de TI). Normalmente na empresa, os perfis de "a pessoa" responsável para cada área são diferentes. Suas habilidades também são diferentes.

![Ferramentas da Microsoft. Para a carga de trabalho de Design/desenvolvimento: Mecanismo do docker para Windows, o VS e o VS Code, .NET Core, o serviço de Kubernetes do Azure. Para a carga de trabalho de Build/teste/remessa: DevOps do Azure, Team Foundation Server, Docker CLI, o serviço Kubernetes do Azure. Para a carga de trabalho de execução/Monitor/gerenciar: O Azure Monitor, serviços de Kubernetes do Azure do Portal do Azure, Service Fabric, outros orquestradores.](./media/image1.png)

**Figura 3-1.** Pilares principais no ciclo de vida de aplicativos do Docker em contêineres com ferramentas e plataformas da Microsoft

Um fluxo de trabalho ciclo de vida em contêineres do Docker pode ser inicialmente prescritivo com base em "por opções padrão de produto," tornando mais fácil para os desenvolvedores a começar a usar mais rapidamente, mas é fundamental que nos bastidores deve haver uma estrutura aberta para que ele será um fluxo de trabalho flexível capaz de ajustar-se aos diferentes contextos de cada organização ou empresa. A infraestrutura de fluxo de trabalho (componentes e produtos) deve ser flexível o suficiente para abranger o ambiente que cada empresa terá no futuro, mesmo sendo capaz de trocar de desenvolvimento ou produtos de DevOps por outros. Essa flexibilidade, a abertura e a ampla variedade de tecnologias na plataforma e infraestrutura são precisamente as prioridades da Microsoft para aplicativos em contêineres do Docker, conforme explicado nos capítulos a seguir.

A Tabela 3-1 demonstra que a intenção do Microsoft DevOps com relação aos aplicativos em contêineres do Docker é fornecer um fluxo de trabalho de DevOps livre para que você possa escolher quais produtos usar para cada fase (da Microsoft ou de terceiros), proporcionando um fluxo de trabalho simplificado que fornece “produtos padrão” já conectados. Dessa forma, você pode começar rapidamente com o fluxo de trabalho de DevOps de nível corporativo para aplicativos do Docker.

**Tabela 3-1.** Fluxos de trabalho de DevOps, abra qualquer tecnologia

| Host | Tecnologias da Microsoft | Terceiros — Conectável ao Azure |
| ---------------------------| ----------------------------------------------------| --------------------------------------------------------------------------------|
| Plataforma para aplicativos do Docker   | • Microsoft Visual Studio e Visual Studio Code<br /> • .NET<br /> • Serviço de Contêiner do Microsoft Azure<br /> • Azure Service Fabric<br /> • Registro de Contêiner do Azure<br /> | • Qualquer editor de código (por exemplo, Sublime)<br /> • Qualquer linguagem (Node.js, Java, Go, etc.)<br /> • Qualquer orquestrador e agendador<br /> • Qualquer registro do Docker<br /> |
| DevOps para aplicativos do Docker     | • Serviços do DevOps do azure<br /> • Microsoft Team Foundation Server<br /> • Serviço de Contêiner do Azure<br /> • Azure Service Fabric<br /> | • GitHub, Git, Subversion, etc.<br /> • Jenkins, Chef, Puppet, Velocity, CircleCI, TravisCI, etc.<br /> • Docker Datacenter, Docker Swarm, Mesos DC/OS, Kubernetes, etc. local<br /> |
| Gerenciamento e monitoramento  | • Azure Monitor | • Marathon, Chronos, etc.<br />|

A plataforma Microsoft e ferramentas para aplicativos em contêineres do Docker, conforme definido na tabela 3-1, incluem os seguintes componentes:

- **Plataforma para desenvolvimento de aplicativos de Docker** O desenvolvimento de um serviço ou coleção de serviços que compõem um “aplicativo”. A plataforma de desenvolvimento fornece todo o trabalho exigido pelos desenvolvedores antes de efetuar push do código para um repositório de código compartilhado. Serviços de desenvolvimento, implantados como contêineres, são semelhantes ao desenvolvimento dos mesmos aplicativos ou serviços sem o Docker. Você continuar a usar seu idioma preferencial (.NET, Node. js, Go, etc.) e editor preferido ou IDE como o Visual Studio ou Visual Studio Code. No entanto, em vez de considerar o Docker como um destino de implantação, você pode desenvolver seus serviços no ambiente do Docker. Você compila, executa, testa e depura o código em contêineres localmente, fornecendo o ambiente de destino no tempo de desenvolvimento. Ao fornecer o ambiente de destino localmente, os contêineres do Docker configuram o que ajudará a melhorar drasticamente seu ciclo de vida de DevOps. O Visual Studio e o Visual Studio Code têm extensões para integrar com contêineres do Docker em seu processo de desenvolvimento.

- **DevOps para aplicativos do Docker** os desenvolvedores que criam aplicativos do Docker podem usar [os serviços do Azure DevOps](https://azure.microsoft.com/services/devops/) ou qualquer outro produto de terceiros, como o Jenkins para criar um ciclo de vida do aplicativo automatizado abrangente ALM (gerenciamento).

  Com os serviços de DevOps do Azure, os desenvolvedores podem criar voltado para contêiner controlar o DevOps para um processo iterativo rápido que abrange o código-fonte de qualquer lugar (serviços de DevOps do Azure-Git, GitHub, qualquer repositório Git remoto ou Subversion), CI (integração contínua) , testes de unidade interna, testes de integração simplificaram container/serviço, CD (entrega contínua) e o gerenciamento de liberação (RM). Os desenvolvedores também podem automatizar suas versões de aplicativo do Docker para o Serviço de Contêiner do Azure, desde o desenvolvimento até os ambientes de preparo e produção.

- **Gerenciamento e monitoramento** IT pode gerenciar e monitorar aplicativos de produção e serviços de várias maneiras, a integração de ambas as perspectivas em uma experiência consolidada.

  - **Portal do Azure** se você estiver usando orquestradores de software livre, serviço de Kubernetes do Azure (AKS), Service Fabric e outros orquestradores ajudam a configurar e manter seus ambientes do Docker. Se você estiver usando o Azure Service Fabric, a ferramenta Service Fabric Explorer possibilita visualizar e configurar o cluster.

  - **Ferramentas do Docker** Você pode gerenciar seus aplicativos de contêiner usando ferramentas familiares. Não é necessário alterar suas práticas de gerenciamento existentes do Docker para mover cargas de trabalho do contêiner para a nuvem. Use as ferramentas de gerenciamento de aplicativo com as quais você já está familiarizado e conecte-se por meio de pontos de extremidade de API padrão ao orquestrador de sua escolha. Você também pode usar outras ferramentas de terceiros para gerenciar seus aplicativos do Docker, como Docker Datacenter ou até mesmo as ferramentas do Docker CLI. 

    Mesmo se você estiver familiarizado com os comandos do Linux, você pode gerenciar seus aplicativos de contêiner usando o Microsoft Windows e do PowerShell com uma linha de comando de subsistema do Linux e os produtos (Docker, Kubernetes...) clientes em execução nessa capacidade do subsistema do Linux. Você aprenderá mais sobre como usar essas ferramentas no subsistema do Linux usando o seu SO favorito do Windows Microsoft mais adiante neste livro.

  - **Ferramentas de código-fonte aberto** AKS porque expõe os pontos de extremidade de API padrão para o mecanismo de orquestração, as ferramentas mais populares são compatíveis com o AKS e, na maioria dos casos, funcionarão de imediato — incluindo visualizadores, monitoramento, ferramentas de linha de comando e até mesmo ferramentas futuras como eles se tornam disponíveis.

  - **O Azure Monitor** solução do Azure é para monitorar todos os ângulos de seu ambiente de produção. Você pode monitorar aplicativos do Docker de produção apenas configurando seu SDK nos seus serviços para que você pode obter dados de log gerados pelo sistema de aplicativos.

Dessa forma, a Microsoft oferece uma base completa para um ciclo de vida de ponta a ponta para aplicativos do Docker em contêineres. No entanto, vale *uma coleção de produtos e tecnologias que permitem que você selecione, opcionalmente e integrar com existente, ferramentas e processos*. A flexibilidade de uma abordagem ampla junto com a força da profundidade dos recursos colocam a Microsoft em uma forte posição para desenvolvimento de aplicativos em contêineres do Docker.

>[!div class="step-by-step"]
>[Anterior](../Docker-application-lifecycle/containers-foundation-for-devops-collaboration.md)
>[Próximo](../design-develop-containerized-apps/index.md)
