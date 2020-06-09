---
title: Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing
ms.date: 03/30/2017
ms.assetid: 10ef3876-6f8e-4d4e-8444-f47847b64795
ms.openlocfilehash: 31fb8d466c76c7490aa80dfcab089332af4036a2
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84589126"
---
# <a name="microsofttransactionstransactionbridgedurableparticipantreplaywhilepreparing"></a><span data-ttu-id="44b02-102">Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing</span><span class="sxs-lookup"><span data-stu-id="44b02-102">Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing</span></span>
<span data-ttu-id="44b02-103">O serviço de protocolo WS-AT recebeu uma mensagem de reprodução de um participante durável, que não respondeu à preparação.</span><span class="sxs-lookup"><span data-stu-id="44b02-103">The WS-AT protocol service received a Replay message from a durable participant, which did not respond to Prepare.</span></span> <span data-ttu-id="44b02-104">Consequentemente, a transação foi anulada.</span><span class="sxs-lookup"><span data-stu-id="44b02-104">Consequently, the transaction was aborted.</span></span>  
  
## <a name="description"></a><span data-ttu-id="44b02-105">Descrição</span><span class="sxs-lookup"><span data-stu-id="44b02-105">Description</span></span>  
 <span data-ttu-id="44b02-106">Rastreado se uma mensagem de reprodução for recebida enquanto um participante durável ainda estiver se preparando.</span><span class="sxs-lookup"><span data-stu-id="44b02-106">Traced if a Replay message is received while a Durable participant is still Preparing.</span></span> <span data-ttu-id="44b02-107">Esta é uma mensagem ilegal para esse Estado e a transação será anulada.</span><span class="sxs-lookup"><span data-stu-id="44b02-107">This is an illegal message for this state and the transaction is going to be aborted.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="44b02-108">Solução de problemas</span><span class="sxs-lookup"><span data-stu-id="44b02-108">Troubleshooting</span></span>

<span data-ttu-id="44b02-109">Receber esse erro pode indicar que um participante durável (incluindo TransactionManagers subordinados) se recuperou de uma falha; no entanto, não há certeza do resultado da transação e solicita seu status.</span><span class="sxs-lookup"><span data-stu-id="44b02-109">Receiving this error can indicate that a Durable participant (including Subordinate TransactionManagers) has recovered from failure; however, it is unsure of the transaction outcome and requests its status.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44b02-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="44b02-110">See also</span></span>

- [<span data-ttu-id="44b02-111">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="44b02-111">Tracing</span></span>](index.md)
- [<span data-ttu-id="44b02-112">Utilizando o rastreamento para solucionar problemas em seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="44b02-112">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="44b02-113">Administração e diagnóstico</span><span class="sxs-lookup"><span data-stu-id="44b02-113">Administration and Diagnostics</span></span>](../index.md)
