---
title: Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout
ms.date: 03/30/2017
ms.assetid: 2dbe34c5-57c7-4b64-9257-63021911d03c
ms.openlocfilehash: fac3682a955ed0caf21fdb1dea48672bf3bdea77
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54704570"
---
# <a name="microsofttransactionstransactionbridgevolatileoutcometimeout"></a><span data-ttu-id="3446a-102">Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout</span><span class="sxs-lookup"><span data-stu-id="3446a-102">Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout</span></span>
<span data-ttu-id="3446a-103">O serviço de protocolo WS-AT atingiu o tempo limite aguardando uma resposta a uma mensagem de resultado de um participante volátil.</span><span class="sxs-lookup"><span data-stu-id="3446a-103">The WS-AT protocol service timed out waiting for a response to an outcome message from a volatile participant.</span></span> <span data-ttu-id="3446a-104">O resultado da transação pode estar em dúvida se o participante de retornar.</span><span class="sxs-lookup"><span data-stu-id="3446a-104">The transaction outcome may be in doubt if the participant returns.</span></span>  
  
## <a name="description"></a><span data-ttu-id="3446a-105">Descrição</span><span class="sxs-lookup"><span data-stu-id="3446a-105">Description</span></span>  
 <span data-ttu-id="3446a-106">Rastreada quando um participante volátil decidiu confirmar ou anular, mas não respondeu a uma solicitação de confirmação ou reversão dentro de um determinado período de tempo.</span><span class="sxs-lookup"><span data-stu-id="3446a-106">Traced when a Volatile participant has decided to Commit or Abort but has not responded to a Commit or Rollback request within a given amount of time.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="3446a-107">Solução de problemas</span><span class="sxs-lookup"><span data-stu-id="3446a-107">Troubleshooting</span></span>  
 <span data-ttu-id="3446a-108">Certifique-se de que todos os participantes voláteis sejam capazes de responder em determinado período de tempo.</span><span class="sxs-lookup"><span data-stu-id="3446a-108">Ensure that all Volatile participants are able to respond within the given amount of time.</span></span> <span data-ttu-id="3446a-109">Período o padrão é 180 segundos.</span><span class="sxs-lookup"><span data-stu-id="3446a-109">The default time period is 180 seconds.</span></span>  <span data-ttu-id="3446a-110">Se isso for insuficiente, aumente o `VolatileOutcomeDelay` política de timer para WS-AT.</span><span class="sxs-lookup"><span data-stu-id="3446a-110">If this is insufficient, increase the `VolatileOutcomeDelay` timer policy for WS-AT.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3446a-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3446a-111">See also</span></span>
- [<span data-ttu-id="3446a-112">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="3446a-112">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="3446a-113">Usando o rastreamento para solucionar problemas do seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="3446a-113">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="3446a-114">Administração e diagnósticos</span><span class="sxs-lookup"><span data-stu-id="3446a-114">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
