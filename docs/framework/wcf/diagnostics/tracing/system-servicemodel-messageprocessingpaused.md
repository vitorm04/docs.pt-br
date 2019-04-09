---
title: System.ServiceModel.MessageProcessingPaused
ms.date: 03/30/2017
ms.assetid: 36b5302a-93cc-478a-9bb2-8a1601fba1df
ms.openlocfilehash: ac1dacef94d6446aa407e4a390b9561d033af1bb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59087463"
---
# <a name="systemservicemodelmessageprocessingpaused"></a><span data-ttu-id="c8fac-102">System.ServiceModel.MessageProcessingPaused</span><span class="sxs-lookup"><span data-stu-id="c8fac-102">System.ServiceModel.MessageProcessingPaused</span></span>
<span data-ttu-id="c8fac-103">System.ServiceModel.MessageProcessingPaused</span><span class="sxs-lookup"><span data-stu-id="c8fac-103">System.ServiceModel.MessageProcessingPaused</span></span>  
  
## <a name="description"></a><span data-ttu-id="c8fac-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="c8fac-104">Description</span></span>  
 <span data-ttu-id="c8fac-105">Os threads foram trocados durante o processamento de uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="c8fac-105">The threads were switched while processing a message.</span></span>  
  
 <span data-ttu-id="c8fac-106">Processamento de mensagens pode ser pausado pelos seguintes motivos:</span><span class="sxs-lookup"><span data-stu-id="c8fac-106">Message processing can be paused by the following reasons:</span></span>  
  
-   <span data-ttu-id="c8fac-107">ConcurrencyMode é único ou reentrante e o serviço está processando outra mensagem.</span><span class="sxs-lookup"><span data-stu-id="c8fac-107">ConcurrencyMode is single or reentrant, and the service is processing another message.</span></span>  
  
-   <span data-ttu-id="c8fac-108">Transação está habilitada e o serviço está processando outra transação.</span><span class="sxs-lookup"><span data-stu-id="c8fac-108">Transaction is enabled and the service is processing another transaction.</span></span>  
  
-   <span data-ttu-id="c8fac-109">Contexto de sincronização não é atual.</span><span class="sxs-lookup"><span data-stu-id="c8fac-109">Synchronization context is not current.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8fac-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c8fac-110">See also</span></span>

- [<span data-ttu-id="c8fac-111">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="c8fac-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="c8fac-112">Utilizando o rastreamento para solucionar problemas em seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="c8fac-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="c8fac-113">Administração e diagnósticos</span><span class="sxs-lookup"><span data-stu-id="c8fac-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
