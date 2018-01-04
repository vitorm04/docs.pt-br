---
title: "Correlação"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 60151f6c-19b7-47af-9cdc-76c2ac95f301
caps.latest.revision: "26"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0a0be008eae45ca5bbe6ca77383bde433931b72e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="correlation"></a><span data-ttu-id="fd8ab-102">Correlação</span><span class="sxs-lookup"><span data-stu-id="fd8ab-102">Correlation</span></span>
<span data-ttu-id="fd8ab-103">Quando os aplicativos de serviço de fluxo de trabalho se comunicam com outros serviços, é importante que as mensagens entre eles são despachadas para a instância de fluxo de trabalho apropriado.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-103">When workflow service applications communicate with other services, it is important that messages between them are dispatched to the appropriate workflow instance.</span></span> <span data-ttu-id="fd8ab-104">Correlação fornece o mecanismo para isso.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-104">Correlation provides the mechanism for this.</span></span> <span data-ttu-id="fd8ab-105">Os tópicos nesta seção fornecem uma visão geral de correlação e como usá-lo em cenários de serviço de fluxo de trabalho diferente.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-105">The topics in this section provide an overview of correlation and how to use it in different workflow service scenarios.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="fd8ab-106">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="fd8ab-106">In This Section</span></span>  
 [<span data-ttu-id="fd8ab-107">Visão geral de correlação</span><span class="sxs-lookup"><span data-stu-id="fd8ab-107">Correlation Overview</span></span>](../../../../docs/framework/wcf/feature-details/correlation-overview.md)  
 <span data-ttu-id="fd8ab-108">Fornece uma visão geral dos tipos de correlação disponível em [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="fd8ab-108">Provides an overview of the types of correlation available in [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].</span></span>  
  
 [<span data-ttu-id="fd8ab-109">Troca de contexto</span><span class="sxs-lookup"><span data-stu-id="fd8ab-109">Context Exchange</span></span>](../../../../docs/framework/wcf/feature-details/context-exchange-correlation.md)  
 <span data-ttu-id="fd8ab-110">Descreve a correlação de intercâmbio de contexto.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-110">Describes context exchange correlation.</span></span>  
  
 [<span data-ttu-id="fd8ab-111">Duplex durável</span><span class="sxs-lookup"><span data-stu-id="fd8ab-111">Durable Duplex</span></span>](../../../../docs/framework/wcf/feature-details/durable-duplex-correlation.md)  
 <span data-ttu-id="fd8ab-112">Descreve a correlação duplex durável.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-112">Describes durable duplex correlation.</span></span>  
  
 [<span data-ttu-id="fd8ab-113">Conteúdo com base</span><span class="sxs-lookup"><span data-stu-id="fd8ab-113">Content Based</span></span>](../../../../docs/framework/wcf/feature-details/content-based-correlation.md)  
 <span data-ttu-id="fd8ab-114">Descreve a correlação baseada em conteúdo.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-114">Describes content-based correlation.</span></span>  
  
 [<span data-ttu-id="fd8ab-115">Solicitação-resposta</span><span class="sxs-lookup"><span data-stu-id="fd8ab-115">Request-Reply</span></span>](../../../../docs/framework/wcf/feature-details/request-reply-correlation.md)  
 <span data-ttu-id="fd8ab-116">Descreve a correlação de solicitação-resposta.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-116">Describes request-reply correlation.</span></span>  
  
 [<span data-ttu-id="fd8ab-117">Correlação de solução de problemas</span><span class="sxs-lookup"><span data-stu-id="fd8ab-117">Troubleshooting Correlation</span></span>](../../../../docs/framework/wcf/feature-details/troubleshooting-correlation.md)  
 <span data-ttu-id="fd8ab-118">Fornece métodos para correlação de solução de problemas.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-118">Provides methods for troubleshooting correlation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd8ab-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fd8ab-119">See Also</span></span>  
 <xref:System.ServiceModel.Activities.CorrelationHandle>  
 <xref:System.ServiceModel.Activities.Send>  
 <xref:System.ServiceModel.Activities.Receive>  
 <xref:System.ServiceModel.CorrelationQuery>  
 [<span data-ttu-id="fd8ab-120">Correlação baseada em conteúdo</span><span class="sxs-lookup"><span data-stu-id="fd8ab-120">Content-Based Correlation</span></span>](../../../../docs/framework/windows-workflow-foundation/samples/content-based-correlation.md)  
 [<span data-ttu-id="fd8ab-121">Calculadora correlacionada</span><span class="sxs-lookup"><span data-stu-id="fd8ab-121">Correlated Calculator</span></span>](../../../../docs/framework/windows-workflow-foundation/samples/correlated-calculator.md)
