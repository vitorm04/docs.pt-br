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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 33d05eaa94ec0efdf6d18d03d9d38bda6f0c9eb7
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="systemservicemodelmessageprocessingpaused"></a><span data-ttu-id="a1c42-102">System.ServiceModel.MessageProcessingPaused</span><span class="sxs-lookup"><span data-stu-id="a1c42-102">System.ServiceModel.MessageProcessingPaused</span></span>
<span data-ttu-id="a1c42-103">System.ServiceModel.MessageProcessingPaused</span><span class="sxs-lookup"><span data-stu-id="a1c42-103">System.ServiceModel.MessageProcessingPaused</span></span>  
  
## <a name="description"></a><span data-ttu-id="a1c42-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="a1c42-104">Description</span></span>  
 <span data-ttu-id="a1c42-105">Os threads foram alternados ao processar uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="a1c42-105">The threads were switched while processing a message.</span></span>  
  
 <span data-ttu-id="a1c42-106">Processamento de mensagens pode ser pausado pelos seguintes motivos:</span><span class="sxs-lookup"><span data-stu-id="a1c42-106">Message processing can be paused by the following reasons:</span></span>  
  
-   <span data-ttu-id="a1c42-107">ConcurrencyMode é único ou reentrante e o serviço está processando outra mensagem.</span><span class="sxs-lookup"><span data-stu-id="a1c42-107">ConcurrencyMode is single or reentrant, and the service is processing another message.</span></span>  
  
-   <span data-ttu-id="a1c42-108">Transação está habilitada e o serviço está processando outra transação.</span><span class="sxs-lookup"><span data-stu-id="a1c42-108">Transaction is enabled and the service is processing another transaction.</span></span>  
  
-   <span data-ttu-id="a1c42-109">Contexto de sincronização não é atual.</span><span class="sxs-lookup"><span data-stu-id="a1c42-109">Synchronization context is not current.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1c42-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a1c42-110">See Also</span></span>  
 [<span data-ttu-id="a1c42-111">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="a1c42-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="a1c42-112">Usando o rastreamento para solucionar problemas de seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="a1c42-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 <span data-ttu-id="a1c42-113">[Administration and Diagnostics](../../../../../docs/framework/wcf/diagnostics/index.md) (Administração e diagnósticos)</span><span class="sxs-lookup"><span data-stu-id="a1c42-113">[Administration and Diagnostics](../../../../../docs/framework/wcf/diagnostics/index.md)</span></span>
