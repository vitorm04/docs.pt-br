---
title: Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing
ms.date: 03/30/2017
ms.assetid: 10ef3876-6f8e-4d4e-8444-f47847b64795
ms.openlocfilehash: 93354fbdd0c1726280526ca07a8b3dd1c57c8a25
ms.sourcegitcommit: 2d42b7ae4252cfe1232777f501ea9ac97df31b63
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2019
ms.locfileid: "67486765"
---
# <a name="microsofttransactionstransactionbridgedurableparticipantreplaywhilepreparing"></a><span data-ttu-id="376e9-102">Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing</span><span class="sxs-lookup"><span data-stu-id="376e9-102">Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing</span></span>
<span data-ttu-id="376e9-103">O serviço de protocolo WS-AT recebeu uma mensagem de repetição de um participante durável, que não respondeu à preparação.</span><span class="sxs-lookup"><span data-stu-id="376e9-103">The WS-AT protocol service received a Replay message from a durable participant, which did not respond to Prepare.</span></span> <span data-ttu-id="376e9-104">Consequentemente, a transação foi anulada.</span><span class="sxs-lookup"><span data-stu-id="376e9-104">Consequently, the transaction was aborted.</span></span>  
  
## <a name="description"></a><span data-ttu-id="376e9-105">Descrição</span><span class="sxs-lookup"><span data-stu-id="376e9-105">Description</span></span>  
 <span data-ttu-id="376e9-106">Rastreados se uma mensagem de repetição é recebida enquanto ainda está se preparando um participante durável.</span><span class="sxs-lookup"><span data-stu-id="376e9-106">Traced if a Replay message is received while a Durable participant is still Preparing.</span></span> <span data-ttu-id="376e9-107">Esta é uma mensagem ilegal para este estado e a transação será anulada.</span><span class="sxs-lookup"><span data-stu-id="376e9-107">This is an illegal message for this state and the transaction is going to be aborted.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="376e9-108">Solução de problemas</span><span class="sxs-lookup"><span data-stu-id="376e9-108">Troubleshooting</span></span>

<span data-ttu-id="376e9-109">Recebendo esse erro pode indicar que um participante durável (incluindo TransactionManagers subordinado) se recuperou de falha; No entanto, ele não tem certo de que o resultado da transação e solicita seu status.</span><span class="sxs-lookup"><span data-stu-id="376e9-109">Receiving this error can indicate that a Durable participant (including Subordinate TransactionManagers) has recovered from failure; however, it is unsure of the transaction outcome and requests its status.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="376e9-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="376e9-110">See also</span></span>

- [<span data-ttu-id="376e9-111">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="376e9-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="376e9-112">Usando o rastreamento para solucionar problemas do seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="376e9-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="376e9-113">Administração e diagnósticos</span><span class="sxs-lookup"><span data-stu-id="376e9-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
