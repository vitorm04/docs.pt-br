---
title: Quando implantar os contêineres do Windows no Azure Container Service (isto é, Kubernetes)
description: Modernizar os aplicativos .NET existentes com contêineres Azure Cloud e Windows | Quando implantar os contêineres do Windows no Azure Container Service (isto é, Kubernetes)
ms.date: 04/30/2018
ms.openlocfilehash: 3ff51a70d4e158b831155ab4992ec32f5d98cedb
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2020
ms.locfileid: "80987758"
---
# <a name="when-to-deploy-windows-containers-to-azure-container-service-that-is-kubernetes"></a>Quando implantar os contêineres do Windows no Azure Container Service (isto é, Kubernetes)

O Azure Container Service otimiza a configuração de ferramentas e tecnologias de código aberto populares especificamente para o Azure. Você recebe uma solução aberta que oferece portabilidade tanto para seus contêineres quanto para a configuração do seu aplicativo. Você seleciona o tamanho, o número de hosts e as ferramentas de orquestrador. O Azure Container Service lida com a infra-estrutura para você.

Se você já está trabalhando com orquestradores de código aberto como Kubernetes, Docker Swarm ou DC/OS, você não precisa alterar suas práticas de gerenciamento existentes para mover cargas de trabalho de contêineres para a nuvem. Use as ferramentas de gerenciamento de aplicativos com as que você já está familiarizado e conecte-se através dos pontos finais padrão da API para o orquestrador de sua escolha.

Todos esses orquestradores são ambientes maduros se você estiver usando contêineres Linux Docker, mas pode estar apenas no estado de visualização para contêineres windows.

Por exemplo, em Kubernetes, o suporte para contêineres é nativo (cidadão de primeira classe), então usar o Windows Containers no Kubernetes também é eficaz (em visualização em ACS a partir do início de 2018).

Nota importante: A versão evoluída e "mais PaaS" do ACS (Azure Container Service) para Kubernetes é AKS (Azure Kubernetes Service), no entanto, os Contêineres Windows ainda não são suportados a partir do 2º trimestre de 2018, mas serão suportados em breve.

>[!div class="step-by-step"]
>[Próximo](when-to-deploy-windows-containers-to-azure-container-instances-ACI.md)
>[anterior](choosing-azure-compute-options-for-container-based-applications.md)
