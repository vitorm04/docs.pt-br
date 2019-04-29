---
title: System.ServiceModel.MessageProcessingPaused
ms.date: 03/30/2017
ms.assetid: 36b5302a-93cc-478a-9bb2-8a1601fba1df
ms.openlocfilehash: ac1dacef94d6446aa407e4a390b9561d033af1bb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61927017"
---
# <a name="systemservicemodelmessageprocessingpaused"></a><span data-ttu-id="b338f-102">System.ServiceModel.MessageProcessingPaused</span><span class="sxs-lookup"><span data-stu-id="b338f-102">System.ServiceModel.MessageProcessingPaused</span></span>
<span data-ttu-id="b338f-103">System.ServiceModel.MessageProcessingPaused</span><span class="sxs-lookup"><span data-stu-id="b338f-103">System.ServiceModel.MessageProcessingPaused</span></span>  
  
## <a name="description"></a><span data-ttu-id="b338f-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="b338f-104">Description</span></span>  
 <span data-ttu-id="b338f-105">Os threads foram trocados durante o processamento de uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="b338f-105">The threads were switched while processing a message.</span></span>  
  
 <span data-ttu-id="b338f-106">Processamento de mensagens pode ser pausado pelos seguintes motivos:</span><span class="sxs-lookup"><span data-stu-id="b338f-106">Message processing can be paused by the following reasons:</span></span>  
  
- <span data-ttu-id="b338f-107">ConcurrencyMode é único ou reentrante e o serviço está processando outra mensagem.</span><span class="sxs-lookup"><span data-stu-id="b338f-107">ConcurrencyMode is single or reentrant, and the service is processing another message.</span></span>  
  
- <span data-ttu-id="b338f-108">Transação está habilitada e o serviço está processando outra transação.</span><span class="sxs-lookup"><span data-stu-id="b338f-108">Transaction is enabled and the service is processing another transaction.</span></span>  
  
- <span data-ttu-id="b338f-109">Contexto de sincronização não é atual.</span><span class="sxs-lookup"><span data-stu-id="b338f-109">Synchronization context is not current.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b338f-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b338f-110">See also</span></span>

- [<span data-ttu-id="b338f-111">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="b338f-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="b338f-112">Usando o rastreamento para solucionar problemas do seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="b338f-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="b338f-113">Administração e diagnósticos</span><span class="sxs-lookup"><span data-stu-id="b338f-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
