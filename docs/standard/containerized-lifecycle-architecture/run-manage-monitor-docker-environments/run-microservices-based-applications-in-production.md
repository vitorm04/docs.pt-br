---
title: Executar aplicativos compostos e microsserviços em ambientes de produção
description: Conheça os principais componentes para executar aplicativos baseados em contêiner na produção
ms.date: 02/15/2019
ms.openlocfilehash: 69df3d39a00b91cbe59c96e5fcab841a60943bcc
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65644974"
---
# <a name="run-composed-and-microservices-based-applications-in-production-environments"></a>Executar aplicativos compostos e microsserviços em ambientes de produção

Aplicativos compostos por vários microsserviços precisam ser implantados em clusters do orchestrator para simplificar a complexidade de implantação e torná-lo viável de um ponto de vista de TI. Sem um cluster do orquestrador, seria difícil de implantar e dimensionar um aplicativo de microsserviços complexos.

## <a name="introduction-to-orchestrators-schedulers-and-container-clusters"></a>Introdução aos clusters de contêiner, agendadores e orquestradores

Anteriormente, este livro eletrônico *clusters* e *agendadores* foram introduzidos como parte da discussão sobre arquitetura de software e desenvolvimento. Kubernetes e Service Fabric são exemplos de clusters do Docker. Ambos esses orquestradores podem executar como parte da infra-estrutura fornecida pelo serviço de Kubernetes do Microsoft Azure.

Quando aplicativos são escalados horizontalmente em vários sistemas de host, a capacidade de gerenciar cada sistema de host e abstraem a complexidade da plataforma subjacente se torna atraente. É exatamente isso que fornecem os orquestradores e agendadores. Aqui, vamos dar uma rápida olhada neles:

- **Agendadores**. "Planejamento" refere-se à capacidade de um administrador para carregar um arquivo de serviço para um sistema de host que estabelece como executar um contêiner específico. Iniciar contêineres em um cluster do Docker tende a ser conhecido como agendamento. Embora o agendamento refere-se ao ato de carregar a definição de serviço, em um sentido mais geral, específico agendadores são responsáveis por vinculando ao sistema de inicialização do host para gerenciar os serviços em qualquer capacidade necessária.

   Agendador do cluster tem vários objetivos: usando os recursos de cluster com eficiência, trabalhando com restrições de posicionamento de fornecido pelo usuário, agendar aplicativos rapidamente para não deixá-los em um estado pendente, com um grau de "integridade", sendo robusto para erros, e sempre estarão disponíveis.

- **Orquestradores**. Plataformas de estendem os recursos de gerenciamento de ciclo de vida para cargas de trabalho de complexos, com vários contêineres implantados em um cluster de hosts. Abstraindo a infraestrutura de host, as ferramentas de orquestração dar aos usuários uma maneira de tratar de todo o cluster como um destino de implantação única.

   O processo de orquestração envolve ferramentas e uma plataforma que pode automatizar todos os aspectos do gerenciamento de aplicativos de posicionamento inicial ou a implantação por contêiner; movendo contêineres para hosts diferentes, dependendo do desempenho; ou integridade do seu host controle de versão e atualizações sem interrupção e funções que dão suporte ao failover; e dimensionamento de monitoramento de integridade e muito mais.

   Orquestração é um termo abrangente que se refere ao contêiner de agendamento, gerenciamento de cluster e, possivelmente, o provisionamento de hosts adicionais.

Os recursos fornecidos pelo orquestradores e agendadores são complexos para desenvolver e criar do zero, portanto, você normalmente usaria oferecidas por fornecedores de soluções de orquestração.

>[!div class="step-by-step"]
>[Anterior](index.md)
>[Próximo](manage-production-docker-environments.md)
