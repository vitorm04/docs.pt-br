---
title: "Executar aplicativos compostos e microservices em ambientes de produção"
description: "Ciclo de vida de aplicativo de Docker em contêineres com ferramentas e plataformas da Microsoft"
keywords: "Docker, Microsserviços, ASP.NET, Contêiner"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: e7a2788098aa731699cbb201c7177e7578907673
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="run-composed-and-microservices-based-applications-in-production-environments"></a>Executar aplicativos compostos e microservices em ambientes de produção

Os aplicativos compostos por várias microservices precisam ser implantados em clusters do orchestrator para simplificar a complexidade da implantação e torná-lo viável de um ponto de vista de TI. Sem um cluster do orchestrator, seria muito difícil de implantar e um aplicativo complexo microservices de expansão.

## <a name="introduction-to-orchestrators-schedulers-and-container-clusters"></a>Introdução ao orchestrators agendadores e clusters de contêiner

Anteriormente neste livro eletrônico, apresentamos *clusters* e *agendadores* como parte da discussão no desenvolvimento e arquitetura de software. São exemplos de clusters de Docker Docker Swarm e sistema operacional de Datacenter Mesosphere (controlador de domínio/OS). Ambos podem executar como parte da infraestrutura de fornecido pelo serviço de contêiner do Microsoft Azure.

Quando os aplicativos são expandidos em vários sistemas de host, a capacidade de gerenciar cada sistema host e abstrair a complexidade da plataforma subjacente se torna atraente. É exatamente o que fornecem orchestrators e agendadores. Vamos dar uma olhada rápida-los aqui:

-   **Agendadores*** *"Programação" refere-se à capacidade de um administrador para carregar um arquivo de serviço em um sistema de host que estabelece como executar um contêiner específico. Iniciar contêineres em um cluster de Docker tende a ser conhecido como agendamento. Embora o agendamento refere-se ao ato de carregar a definição de serviço, em termos mais gerais, específico agendadores são responsáveis por conectar ao sistema de inicialização do host para gerenciar os serviços de qualquer capacidade necessária.

Um agendador de cluster tem vários objetivos: usando recursos do cluster com eficiência, trabalhando com restrições de posicionamento fornecido pelo usuário, agendamento aplicativos rapidamente para não deixá-los em um estado pendente, com um grau de "integridade", sendo robusto para erros, e sempre estar disponíveis.

-   **Orquestração*** *plataformas estendem os recursos de gerenciamento de ciclo de vida complexas, multicontainer cargas de trabalho implantadas em um cluster de hosts. Abstraindo a infraestrutura de host, as ferramentas de orquestração dar aos usuários uma maneira de tratar de todo o cluster como um destino de implantação única.

O processo de orquestração envolve ferramentas e uma plataforma que pode automatizar todos os aspectos do gerenciamento de aplicativos de posicionamento inicial ou a implantação por contêiner; contêineres de movimentação para hosts diferentes, dependendo do seu host integridade ou desempenho; controle de versão e as atualizações sem interrupção e funções que oferecem suporte a failover; e dimensionamento de monitoramento de integridade e muito mais.

Orquestração é um termo amplo que se refere ao contêiner de agendamento, gerenciamento de cluster e possivelmente o provisionamento de hosts adicionais.

Os recursos fornecidos pelo orchestrators e agendadores são muito complexos para desenvolver e criar do zero, e, portanto, você geralmente deseja fazer uso das soluções de orquestração oferecidos por fornecedores.


>[!div class="step-by-step"]
[Anterior] (index.md) [Avançar] (gerenciar-produção-docker-environments.md)
