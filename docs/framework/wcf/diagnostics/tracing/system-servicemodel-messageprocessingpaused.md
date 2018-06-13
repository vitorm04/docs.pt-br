---
title: System.ServiceModel.MessageProcessingPaused
ms.date: 03/30/2017
ms.assetid: 36b5302a-93cc-478a-9bb2-8a1601fba1df
ms.openlocfilehash: 6fb1463b811d985f54b9a99e59d1280eaa040256
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33482808"
---
# <a name="systemservicemodelmessageprocessingpaused"></a><span data-ttu-id="0a77e-102">System.ServiceModel.MessageProcessingPaused</span><span class="sxs-lookup"><span data-stu-id="0a77e-102">System.ServiceModel.MessageProcessingPaused</span></span>
<span data-ttu-id="0a77e-103">System.ServiceModel.MessageProcessingPaused</span><span class="sxs-lookup"><span data-stu-id="0a77e-103">System.ServiceModel.MessageProcessingPaused</span></span>  
  
## <a name="description"></a><span data-ttu-id="0a77e-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="0a77e-104">Description</span></span>  
 <span data-ttu-id="0a77e-105">Os threads foram alternados ao processar uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="0a77e-105">The threads were switched while processing a message.</span></span>  
  
 <span data-ttu-id="0a77e-106">Processamento de mensagens pode ser pausado pelos seguintes motivos:</span><span class="sxs-lookup"><span data-stu-id="0a77e-106">Message processing can be paused by the following reasons:</span></span>  
  
-   <span data-ttu-id="0a77e-107">ConcurrencyMode é único ou reentrante e o serviço está processando outra mensagem.</span><span class="sxs-lookup"><span data-stu-id="0a77e-107">ConcurrencyMode is single or reentrant, and the service is processing another message.</span></span>  
  
-   <span data-ttu-id="0a77e-108">Transação está habilitada e o serviço está processando outra transação.</span><span class="sxs-lookup"><span data-stu-id="0a77e-108">Transaction is enabled and the service is processing another transaction.</span></span>  
  
-   <span data-ttu-id="0a77e-109">Contexto de sincronização não é atual.</span><span class="sxs-lookup"><span data-stu-id="0a77e-109">Synchronization context is not current.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a77e-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0a77e-110">See Also</span></span>  
 [<span data-ttu-id="0a77e-111">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="0a77e-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="0a77e-112">Usando o rastreamento para solucionar problemas do seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="0a77e-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="0a77e-113">Administração e diagnósticos</span><span class="sxs-lookup"><span data-stu-id="0a77e-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
