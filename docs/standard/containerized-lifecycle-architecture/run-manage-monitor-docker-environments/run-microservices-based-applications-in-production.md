---
title: Executar aplicativos compostos e baseados em microsserviços em ambientes de produção
description: Containerized Docker Application Lifecycle with Microsoft Platform and Tools (Ciclo de vida de aplicativo do Docker em contêineres com a plataforma e as ferramentas da Microsoft)
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: 18e6cb1fb5f496b66c89cb8e009a67894b8a76ad
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48580281"
---
# <a name="run-composed-and-microservices-based-applications-in-production-environments"></a>Executar aplicativos compostos e baseados em microsserviços em ambientes de produção

Aplicativos compostos por vários microsserviços precisam ser implantados em clusters do orchestrator para simplificar a complexidade de implantação e torná-lo viável de um ponto de vista de TI. Sem um cluster do orquestrador, seria muito difícil de implantar e escalar horizontalmente um aplicativo de microsserviços complexos.

## <a name="introduction-to-orchestrators-schedulers-and-container-clusters"></a>Introdução aos clusters de contêiner, agendadores e orquestradores

Anteriormente neste livro eletrônico, apresentamos *clusters* e *agendadores* como parte da discussão sobre arquitetura de software e desenvolvimento. Exemplos de clusters do Docker são Docker Swarm e o sistema de operacional de Datacenter do Mesosphere (DC/OS). Ambos podem executar como parte da infra-estrutura fornecida pelo serviço de contêiner do Microsoft Azure.

Quando aplicativos são escalados horizontalmente em vários sistemas de host, a capacidade de gerenciar cada sistema de host e abstraem a complexidade da plataforma subjacente se torna atraente. É exatamente isso que fornecem os orquestradores e agendadores. Aqui, vamos dar uma rápida olhada neles:

- **Agendadores**. "Planejamento" refere-se à capacidade de um administrador para carregar um arquivo de serviço para um sistema de host que estabelece como executar um contêiner específico. Iniciar contêineres em um cluster do Docker tende a ser conhecido como agendamento. Embora o agendamento refere-se ao ato de carregar a definição de serviço, em um sentido mais geral, específico agendadores são responsáveis por vinculando ao sistema de inicialização do host para gerenciar os serviços em qualquer capacidade necessária.

   Agendador do cluster tem vários objetivos: usando os recursos de cluster com eficiência, trabalhando com restrições de posicionamento de fornecido pelo usuário, agendar aplicativos rapidamente para não deixá-los em um estado pendente, com um grau de "integridade", sendo robusto para erros, e sempre estarão disponíveis.

- **Orquestração**. Plataformas de estendem os recursos de gerenciamento de ciclo de vida para cargas de trabalho de complexos, vários contêineres implantados em um cluster de hosts. Abstraindo a infraestrutura de host, as ferramentas de orquestração dar aos usuários uma maneira de tratar de todo o cluster como um destino de implantação única.

   O processo de orquestração envolve ferramentas e uma plataforma que pode automatizar todos os aspectos do gerenciamento de aplicativos de posicionamento inicial ou a implantação por contêiner; movendo contêineres para hosts diferentes, dependendo do desempenho; ou integridade do seu host controle de versão e atualizações sem interrupção e funções que dão suporte ao failover; e dimensionamento de monitoramento de integridade e muito mais.

   Orquestração é um termo abrangente que se refere ao contêiner de agendamento, gerenciamento de cluster e, possivelmente, o provisionamento de hosts adicionais.

Os recursos fornecidos pelo orquestradores e agendadores são muito complexos para desenvolver e criar do zero e, portanto, você geralmente desejam fazer uso de orquestração soluções oferecidas pelos fornecedores.


>[!div class="step-by-step"]
[Anterior](index.md)
[Próximo](manage-production-docker-environments.md)
