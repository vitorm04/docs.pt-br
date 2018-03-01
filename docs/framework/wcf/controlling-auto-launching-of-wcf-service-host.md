---
title: "Controlando a auto inicialização do host de serviço do WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- WcfOptions
ms.assetid: 6abe5d34-519b-4cef-8f02-3c0a7f125585
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 65daceac9b865f3e8224c709d672344606905d9f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="controlling-auto-launching-of-wcf-service-host"></a><span data-ttu-id="82526-102">Controlando a auto inicialização do host de serviço do WCF</span><span class="sxs-lookup"><span data-stu-id="82526-102">Controlling Auto-launching of WCF Service Host</span></span>
<span data-ttu-id="82526-103">Você pode controlar a capacidade de inicialização automática do [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] (WcfSvcHost.exe) de Host de serviço para um [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] projeto de biblioteca de serviço, ao depurar outro projeto na mesma [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] solução que contém vários projetos.</span><span class="sxs-lookup"><span data-stu-id="82526-103">You can control the auto-launching capability of [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] Service Host (WcfSvcHost.exe) for a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Service Library project, when you debug another project in the same [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] solution containing multiple projects.</span></span>  
  
 <span data-ttu-id="82526-104">Para fazer isso, clique com botão direito do [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] projeto de serviço no **Solution Explorer**, escolha **propriedades**e clique em **WCF opções** guia. O **iniciar ao depurar outro projeto na mesma solução o Host de serviço de WCF** caixa de seleção é habilitada por padrão.</span><span class="sxs-lookup"><span data-stu-id="82526-104">To do so, right-click the [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Service Project in **Solution Explorer**, choose **Properties**, and click **WCF Options** tab. The **Start WCF Service Host when debugging another project in the same solution** check box is enabled by default.</span></span> <span data-ttu-id="82526-105">Você pode desmarcar a caixa de forma que [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Host de serviço para este projeto específico não é iniciado quando o outro projeto é depurado na mesma solução.</span><span class="sxs-lookup"><span data-stu-id="82526-105">You can clear the box so that [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Service Host for this specific project is not launched when another project is debugged in the same solution.</span></span>  
  
 <span data-ttu-id="82526-106">Esse comportamento não afeta a depuração F5 ou funcionalidades adicionar referência de serviço para este projeto.</span><span class="sxs-lookup"><span data-stu-id="82526-106">This behavior does not affect the F5 debugging, or Add Service Reference functionalities for this project.</span></span>  
  
 <span data-ttu-id="82526-107">Essa opção está disponível para os projetos a seguir:</span><span class="sxs-lookup"><span data-stu-id="82526-107">This option is available to the following projects:</span></span>  
  
-   [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]<span data-ttu-id="82526-108">Projeto de biblioteca de serviço.</span><span class="sxs-lookup"><span data-stu-id="82526-108"> Service Library Project.</span></span>  
  
-   <span data-ttu-id="82526-109">Projeto de biblioteca de serviço de fluxo de trabalho sequencial.</span><span class="sxs-lookup"><span data-stu-id="82526-109">Sequential Workflow Service Library Project.</span></span>  
  
-   <span data-ttu-id="82526-110">Projeto de biblioteca de serviço de fluxo de trabalho de máquina de estado.</span><span class="sxs-lookup"><span data-stu-id="82526-110">State Machine Workflow Service Library Project.</span></span>  
  
-   <span data-ttu-id="82526-111">Projeto de biblioteca de serviço de distribuição.</span><span class="sxs-lookup"><span data-stu-id="82526-111">Syndication Service Library Project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82526-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="82526-112">See Also</span></span>  
 [<span data-ttu-id="82526-113">Host de serviço do WCF (WcfSvcHost.exe)</span><span class="sxs-lookup"><span data-stu-id="82526-113">WCF Service Host (WcfSvcHost.exe)</span></span>](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)
