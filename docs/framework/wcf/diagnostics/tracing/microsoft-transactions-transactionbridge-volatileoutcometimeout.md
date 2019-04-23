---
title: Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout
ms.date: 03/30/2017
ms.assetid: 2dbe34c5-57c7-4b64-9257-63021911d03c
ms.openlocfilehash: 22992b4dfad4b4867adda0fcbbd8ecc5eb67d87e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59160134"
---
# <a name="microsofttransactionstransactionbridgevolatileoutcometimeout"></a><span data-ttu-id="ad8a0-102">Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout</span><span class="sxs-lookup"><span data-stu-id="ad8a0-102">Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout</span></span>
<span data-ttu-id="ad8a0-103">O serviço de protocolo WS-AT atingiu o tempo limite aguardando uma resposta a uma mensagem de resultado de um participante volátil.</span><span class="sxs-lookup"><span data-stu-id="ad8a0-103">The WS-AT protocol service timed out waiting for a response to an outcome message from a volatile participant.</span></span> <span data-ttu-id="ad8a0-104">O resultado da transação pode estar em dúvida se o participante de retornar.</span><span class="sxs-lookup"><span data-stu-id="ad8a0-104">The transaction outcome may be in doubt if the participant returns.</span></span>  
  
## <a name="description"></a><span data-ttu-id="ad8a0-105">Descrição</span><span class="sxs-lookup"><span data-stu-id="ad8a0-105">Description</span></span>  
 <span data-ttu-id="ad8a0-106">Rastreada quando um participante volátil decidiu confirmar ou anular, mas não respondeu a uma solicitação de confirmação ou reversão dentro de um determinado período de tempo.</span><span class="sxs-lookup"><span data-stu-id="ad8a0-106">Traced when a Volatile participant has decided to Commit or Abort but has not responded to a Commit or Rollback request within a given amount of time.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="ad8a0-107">Solução de problemas</span><span class="sxs-lookup"><span data-stu-id="ad8a0-107">Troubleshooting</span></span>  
 <span data-ttu-id="ad8a0-108">Certifique-se de que todos os participantes voláteis sejam capazes de responder em determinado período de tempo.</span><span class="sxs-lookup"><span data-stu-id="ad8a0-108">Ensure that all Volatile participants are able to respond within the given amount of time.</span></span> <span data-ttu-id="ad8a0-109">Período o padrão é 180 segundos.</span><span class="sxs-lookup"><span data-stu-id="ad8a0-109">The default time period is 180 seconds.</span></span>  <span data-ttu-id="ad8a0-110">Se isso for insuficiente, aumente o `VolatileOutcomeDelay` política de timer para WS-AT.</span><span class="sxs-lookup"><span data-stu-id="ad8a0-110">If this is insufficient, increase the `VolatileOutcomeDelay` timer policy for WS-AT.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad8a0-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ad8a0-111">See also</span></span>

- [<span data-ttu-id="ad8a0-112">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="ad8a0-112">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="ad8a0-113">Usando o rastreamento para solucionar problemas do seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="ad8a0-113">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="ad8a0-114">Administração e diagnósticos</span><span class="sxs-lookup"><span data-stu-id="ad8a0-114">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
