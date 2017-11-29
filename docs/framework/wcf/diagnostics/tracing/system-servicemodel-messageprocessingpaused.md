---
title: System.ServiceModel.MessageProcessingPaused
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 36b5302a-93cc-478a-9bb2-8a1601fba1df
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1176af676673e19eb2d8cd54cc4d2d254c7ba324
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="systemservicemodelmessageprocessingpaused"></a><span data-ttu-id="74aff-102">System.ServiceModel.MessageProcessingPaused</span><span class="sxs-lookup"><span data-stu-id="74aff-102">System.ServiceModel.MessageProcessingPaused</span></span>
<span data-ttu-id="74aff-103">System.ServiceModel.MessageProcessingPaused</span><span class="sxs-lookup"><span data-stu-id="74aff-103">System.ServiceModel.MessageProcessingPaused</span></span>  
  
## <a name="description"></a><span data-ttu-id="74aff-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="74aff-104">Description</span></span>  
 <span data-ttu-id="74aff-105">Os threads foram alternados ao processar uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="74aff-105">The threads were switched while processing a message.</span></span>  
  
 <span data-ttu-id="74aff-106">Processamento de mensagens pode ser pausado pelos seguintes motivos:</span><span class="sxs-lookup"><span data-stu-id="74aff-106">Message processing can be paused by the following reasons:</span></span>  
  
-   <span data-ttu-id="74aff-107">ConcurrencyMode é único ou reentrante e o serviço está processando outra mensagem.</span><span class="sxs-lookup"><span data-stu-id="74aff-107">ConcurrencyMode is single or reentrant, and the service is processing another message.</span></span>  
  
-   <span data-ttu-id="74aff-108">Transação está habilitada e o serviço está processando outra transação.</span><span class="sxs-lookup"><span data-stu-id="74aff-108">Transaction is enabled and the service is processing another transaction.</span></span>  
  
-   <span data-ttu-id="74aff-109">Contexto de sincronização não é atual.</span><span class="sxs-lookup"><span data-stu-id="74aff-109">Synchronization context is not current.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74aff-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="74aff-110">See Also</span></span>  
 [<span data-ttu-id="74aff-111">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="74aff-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="74aff-112">Usando o rastreamento para solucionar problemas de seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="74aff-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 <span data-ttu-id="74aff-113">[Administration and Diagnostics](../../../../../docs/framework/wcf/diagnostics/index.md) (Administração e diagnósticos)</span><span class="sxs-lookup"><span data-stu-id="74aff-113">[Administration and Diagnostics](../../../../../docs/framework/wcf/diagnostics/index.md)</span></span>
