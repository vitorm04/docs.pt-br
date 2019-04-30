---
title: Quando implantar Contêineres do Windows no Service Fabric
description: Modernizar aplicativos .NET existentes com contêineres do Windows e de nuvem do Azure | Quando implantar contêineres do Windows para o Service Fabric
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/30/2018
ms.openlocfilehash: 01d76f325480c7cf09fef36b02589a602e3ee11e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61973636"
---
# <a name="when-to-deploy-windows-containers-to-service-fabric"></a>Quando implantar Contêineres do Windows no Service Fabric

Aplicativos que são baseados em contêineres do Windows rapidamente precisará usar as plataformas ainda mais afastar das VMs de IaaS. Isso é para alta escalabilidade e melhor escalabilidade automatizada, e obter melhorias significativas em uma experiência de gerenciamento completa para implantações, atualizações, controle de versão, reversões e monitoramento de integridade. Para atingir essas metas com o orchestrator do Azure Service Fabric, disponível na nuvem do Microsoft Azure, mas também no local, ou até mesmo em outra nuvem.

Muitas organizações estão levantar e dos aplicativos monolíticos existentes em contêineres por duas razões:

- Reduções de custos, devido à consolidação e a remoção de hardware existente ou de aplicativos em execução em uma densidade mais alta.

- Um contrato de implantação consistente entre o desenvolvimento e operações.

Buscando reduções de custo é compreensível, e é provável que todas as organizações estão perseguindo esse objetivo. Implantação consistente é mais difícil avaliar, mas é igualmente importante. Um contrato de implantação consistente diz que os desenvolvedores são livres para optar por usar a tecnologia que é ideal para eles, e a equipe de operações obtém uma única maneira de implantar e gerenciar aplicativos. Este contrato alivia a dificuldade de ter operações que lidam com a complexidade das muitas tecnologias diferentes, ou forçar os desenvolvedores trabalhem apenas com determinadas tecnologias. Essencialmente, cada aplicativo está em contêineres em uma imagem de implantação autocontida.

Algumas organizações continuarão Modernizando adicionando microsserviços (aplicativos nativos de nuvem), mas muitas outras organizações parar aqui (aplicativos otimizados para a nuvem). Conforme mostrado na Figura 4 a 8, essas organizações não se moverá para arquiteturas de microsserviços porque eles talvez não precise. Em qualquer caso, já que eles obtém os benefícios que usar contêineres além do Service Fabric fornece uma experiência completa de gerenciamento que inclui a implantação, atualiza, controle de versão, reversões e monitoramento de integridade.

> ![Comparar e Deslocar um aplicativo do Service Fabric](./media/image8.png)
>
> **Figura 4 a 8.** Comparar e Deslocar um aplicativo do Service Fabric

Uma abordagem chave para o Service Fabric é reutilizar o código existente e comparar e deslocar. Portanto, você pode migrar seus aplicativos atuais do .NET Framework, usando os contêineres do Windows e implantá-los para o Service Fabric. Será mais fácil manter vai modernização, eventualmente, adicionando novos microsserviços.

Ao comparar o Service Fabric para outros orquestradores, é importante destacar que o Service Fabric é maduro na execução de serviços e aplicativos baseados em Windows. Execução do Service Fabric serviços baseados em Windows e aplicativos, incluindo o nível 1 de missão crítica de produtos da Microsoft há anos. Ele era o orquestrador primeiro para ter disponibilidade geral para contêineres do Windows. Outros contêineres, como Kubernetes, DC/SO e Docker Swarm, são mais maduros no Linux, mas menos maduro que aplicativos baseados no Service Fabric para Windows e contêineres do Windows.

O objetivo final do Service Fabric é reduzir a complexidade da criação de aplicativos usando uma abordagem de microsserviços. Eventualmente, você deseja um microsserviços para determinados tipos de aplicativos para evitar reformulações dispendiosas. Você pode começar pequeno, dimensionar quando necessário, substituir serviços, adicionar novos serviços e evoluir seu aplicativo com o uso do cliente. Há muitos outros problemas que ainda precisam ser resolvidos para tornar os microsserviços mais acessíveis para a maioria dos desenvolvedores. Se atualmente você estiver apenas levantar e Deslocar um aplicativo com contêineres do Windows, mas você está pensando em Adicionar microsserviços com base em contêineres no futuro, que é o ponto ideal do Service Fabric.

>[!div class="step-by-step"]
>[Anterior](when-to-deploy-windows-containers-to-azure-vms-iaas-cloud.md)
>[Próximo](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)