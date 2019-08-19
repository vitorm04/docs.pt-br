---
title: Quando implantar contêineres do Windows no serviço de contêiner do Azure (ou seja, kubernetes)
description: Modernizar aplicativos .NET existentes com contêineres de nuvem e Windows do Azure | Quando implantar contêineres do Windows no serviço de contêiner do Azure (ou seja, kubernetes)
ms.date: 04/30/2018
ms.openlocfilehash: 903082deba635dd0dfc22d0186fbc589f8d05b92
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2019
ms.locfileid: "69577939"
---
# <a name="when-to-deploy-windows-containers-to-azure-container-service-that-is-kubernetes"></a>Quando implantar contêineres do Windows no serviço de contêiner do Azure (ou seja, kubernetes)

O serviço de contêiner do Azure otimiza a configuração de ferramentas e tecnologias populares de software livre especificamente para o Azure. Você Obtém uma solução aberta que oferece portabilidade para seus contêineres e para a configuração do aplicativo. Você seleciona o tamanho, o número de hosts e as ferramentas do Orchestrator. O serviço de contêiner do Azure lida com a infraestrutura para você.

Se você já estiver trabalhando com orquestradores de software livre como kubernetes, Docker Swarm ou DC/so, não será necessário alterar suas práticas de gerenciamento existentes para mover cargas de trabalho de contêiner para a nuvem. Use as ferramentas de gerenciamento de aplicativos com as quais você já está familiarizado e conecte-se por meio dos pontos de extremidade da API padrão para o orquestrador de sua escolha.

Todos esses orquestradores são ambientes maduros se você estiver usando contêineres do Docker do Linux, mas só poderá estar em estado de visualização para contêineres do Windows.

Por exemplo, no kubernetes, o suporte para contêineres é nativo (cidadão de primeira classe). portanto, usar contêineres do Windows no kubernetes também é eficaz (em versão prévia no ACS a partir do início 2018).

Observação importante: A versão evoluida e "mais PaaS" do ACS (serviço de contêiner do Azure) para kubernetes é AKS (serviço kubernetes do Azure). no entanto, os contêineres do Windows ainda não têm suporte a partir do segundo trimestre 2018, mas haverá suporte em breve.

>[!div class="step-by-step"]
>[Anterior](when-to-deploy-windows-containers-to-azure-container-instances-ACI.md)
>[Próximo](choosing-azure-compute-options-for-container-based-applications.md)
