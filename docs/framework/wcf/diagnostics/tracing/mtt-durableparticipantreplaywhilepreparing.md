---
title: Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing
ms.date: 03/30/2017
ms.assetid: 10ef3876-6f8e-4d4e-8444-f47847b64795
ms.openlocfilehash: f5d74d73cc43b500d3920ca03905f4eb7543619a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59075529"
---
# <a name="microsofttransactionstransactionbridgedurableparticipantreplaywhilepreparing"></a><span data-ttu-id="1a95c-102">Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing</span><span class="sxs-lookup"><span data-stu-id="1a95c-102">Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing</span></span>
<span data-ttu-id="1a95c-103">O serviço de protocolo WS-AT recebeu uma mensagem de repetição de um participante durável, que não respondeu à preparação.</span><span class="sxs-lookup"><span data-stu-id="1a95c-103">The WS-AT protocol service received a Replay message from a durable participant, which did not respond to Prepare.</span></span> <span data-ttu-id="1a95c-104">Consequentemente, a transação foi anulada.</span><span class="sxs-lookup"><span data-stu-id="1a95c-104">Consequently, the transaction was aborted.</span></span>  
  
## <a name="description"></a><span data-ttu-id="1a95c-105">Descrição</span><span class="sxs-lookup"><span data-stu-id="1a95c-105">Description</span></span>  
 <span data-ttu-id="1a95c-106">Rastreados se uma mensagem de repetição é recebida enquanto ainda está se preparando um participante durável.</span><span class="sxs-lookup"><span data-stu-id="1a95c-106">Traced if a Replay message is received while a Durable participant is still Preparing.</span></span> <span data-ttu-id="1a95c-107">Esta é uma mensagem ilegal para este estado e a transação será anulada.</span><span class="sxs-lookup"><span data-stu-id="1a95c-107">This is an illegal message for this state and the transaction is going to be aborted.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="1a95c-108">Solução de problemas</span><span class="sxs-lookup"><span data-stu-id="1a95c-108">Troubleshooting</span></span>  
 <span data-ttu-id="1a95c-109">Recebendo esse erro pode indiate que um participante durável (incluindo TransactionManagers subordinado) se recuperou de falha, no entanto, ele não tem certo do resultado da transação e seu status da solicitação.</span><span class="sxs-lookup"><span data-stu-id="1a95c-109">Receiving this error can indiate that a Durable participant (including Subordinate TransactionManagers) has recovered from failure, however it is unsure of the transaction outcome and request its status.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a95c-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1a95c-110">See also</span></span>

- [<span data-ttu-id="1a95c-111">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="1a95c-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="1a95c-112">Usando o rastreamento para solucionar problemas do seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="1a95c-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="1a95c-113">Administração e diagnósticos</span><span class="sxs-lookup"><span data-stu-id="1a95c-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
