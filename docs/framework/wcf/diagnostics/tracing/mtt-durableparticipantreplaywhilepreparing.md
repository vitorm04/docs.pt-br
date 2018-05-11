---
title: Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing
ms.date: 03/30/2017
ms.assetid: 10ef3876-6f8e-4d4e-8444-f47847b64795
ms.openlocfilehash: fe88e70ab4955305d78baa1158cd73a93ba2ed2c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="microsofttransactionstransactionbridgedurableparticipantreplaywhilepreparing"></a><span data-ttu-id="2c579-102">Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing</span><span class="sxs-lookup"><span data-stu-id="2c579-102">Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing</span></span>
<span data-ttu-id="2c579-103">O serviço de protocolo WS-AT recebeu uma mensagem de repetição de um participante permanente, não respondeu à preparação.</span><span class="sxs-lookup"><span data-stu-id="2c579-103">The WS-AT protocol service received a Replay message from a durable participant, which did not respond to Prepare.</span></span> <span data-ttu-id="2c579-104">Consequentemente, a transação foi anulada.</span><span class="sxs-lookup"><span data-stu-id="2c579-104">Consequently, the transaction was aborted.</span></span>  
  
## <a name="description"></a><span data-ttu-id="2c579-105">Descrição</span><span class="sxs-lookup"><span data-stu-id="2c579-105">Description</span></span>  
 <span data-ttu-id="2c579-106">Rastreados se uma mensagem de repetição é recebida enquanto ainda está se preparando um participante permanente.</span><span class="sxs-lookup"><span data-stu-id="2c579-106">Traced if a Replay message is received while a Durable participant is still Preparing.</span></span> <span data-ttu-id="2c579-107">Esta é uma mensagem ilegal para este estado e a transação será anulada.</span><span class="sxs-lookup"><span data-stu-id="2c579-107">This is an illegal message for this state and the transaction is going to be aborted.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="2c579-108">Solução de problemas</span><span class="sxs-lookup"><span data-stu-id="2c579-108">Troubleshooting</span></span>  
 <span data-ttu-id="2c579-109">Recebendo esse erro pode indiate que um participante permanente (incluindo TransactionManagers subordinada) foi recuperado após falha, no entanto, é seguro sobre o resultado da transação e o status da solicitação.</span><span class="sxs-lookup"><span data-stu-id="2c579-109">Receiving this error can indiate that a Durable participant (including Subordinate TransactionManagers) has recovered from failure, however it is unsure of the transaction outcome and request its status.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c579-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2c579-110">See Also</span></span>  
 [<span data-ttu-id="2c579-111">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="2c579-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="2c579-112">Usando o rastreamento para solucionar problemas do seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="2c579-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="2c579-113">Administração e diagnósticos</span><span class="sxs-lookup"><span data-stu-id="2c579-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
