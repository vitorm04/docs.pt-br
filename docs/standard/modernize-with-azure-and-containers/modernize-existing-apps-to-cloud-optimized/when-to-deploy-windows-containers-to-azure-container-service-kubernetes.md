---
title: Quando implantar contêineres do Windows para serviço de contêiner do Azure (ou seja, Kubernetes)
description: Modernizar aplicativos existentes do .NET com contêineres do Windows e de nuvem do Azure | Quando implantar contêineres do Windows para serviço de contêiner do Azure (ou seja, Kubernetes)
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/30/2018
ms.openlocfilehash: b7f106e2b79a2c6bb24733debf7f4828505d66a6
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/10/2018
---
# <a name="when-to-deploy-windows-containers-to-azure-container-service-that-is-kubernetes"></a>Quando implantar contêineres do Windows para serviço de contêiner do Azure (ou seja, Kubernetes)

Serviço de contêiner do Azure otimiza a configuração de tecnologias e ferramentas de código aberto populares especificamente para o Azure. Você obtém uma solução aberta que oferece portabilidade para seus contêineres e sua configuração de aplicativo. Você seleciona o tamanho, o número de hosts e as ferramentas do orchestrator. Serviço de contêiner do Azure lida com a infraestrutura para você.

Se você já estiver trabalhando com código-fonte aberto orchestrators como Kubernetes, Docker Swarm ou DC/sistema operacional, você não precisa alterar suas práticas de gerenciamento existente para mover cargas de trabalho do contêiner para a nuvem. Use as ferramentas de gerenciamento de aplicativo que você já estiver familiarizado com e conectar-se por meio de pontos de extremidade de API padrão para o orquestrador de sua escolha.

Todos esses orchestrators são ambientes maduras, se você estiver usando contêineres do Docker do Linux, mas só pode estar em estado de visualização para contêineres do Windows.

Por exemplo, em Kubernetes, o suporte para contêineres é nativo (cidadão de primeira classe), portanto, usar contêineres do Windows em Kubernetes também é efetivo (em visualização no ACS a partir do início 2018).

Observação importante: O evoluído e "mais PaaS" versão do ACS (serviço de contêiner do Azure) para Kubernetes é AKS (serviço de Kubernetes do Azure), no entanto, os contêineres do Windows ainda não há suporte para a partir de Q2 2018, mas terá suporte em breve.

>[!div class="step-by-step"]
[Anterior](when-to-deploy-windows-containers-to-service-fabric.md)
[Próximo](choosing-azure-compute-options-for-container-based-applications.md)
