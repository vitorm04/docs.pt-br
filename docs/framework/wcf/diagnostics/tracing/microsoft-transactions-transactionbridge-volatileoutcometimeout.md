---
title: Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2dbe34c5-57c7-4b64-9257-63021911d03c
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1385995165308cb1c2f2e6bd6c8a800a88b7b79e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="microsofttransactionstransactionbridgevolatileoutcometimeout"></a><span data-ttu-id="d824d-102">Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout</span><span class="sxs-lookup"><span data-stu-id="d824d-102">Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout</span></span>
<span data-ttu-id="d824d-103">O serviço de protocolo WS-AT atingiu o tempo limite aguardando uma resposta a uma mensagem de resultado de um participante volátil.</span><span class="sxs-lookup"><span data-stu-id="d824d-103">The WS-AT protocol service timed out waiting for a response to an outcome message from a volatile participant.</span></span> <span data-ttu-id="d824d-104">O resultado da transação pode ser em dúvida se o participante retornar.</span><span class="sxs-lookup"><span data-stu-id="d824d-104">The transaction outcome may be in doubt if the participant returns.</span></span>  
  
## <a name="description"></a><span data-ttu-id="d824d-105">Descrição</span><span class="sxs-lookup"><span data-stu-id="d824d-105">Description</span></span>  
 <span data-ttu-id="d824d-106">Rastreada quando um participante volátil decidiu confirmação ou anulação, mas não respondeu a uma solicitação de confirmação ou reversão em um determinado período de tempo.</span><span class="sxs-lookup"><span data-stu-id="d824d-106">Traced when a Volatile participant has decided to Commit or Abort but has not responded to a Commit or Rollback request within a given amount of time.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="d824d-107">Solução de problemas</span><span class="sxs-lookup"><span data-stu-id="d824d-107">Troubleshooting</span></span>  
 <span data-ttu-id="d824d-108">Certifique-se de que todos os participantes voláteis são capazes de responder dentro de determinado período de tempo.</span><span class="sxs-lookup"><span data-stu-id="d824d-108">Ensure that all Volatile participants are able to respond within the given amount of time.</span></span> <span data-ttu-id="d824d-109">Período o padrão é 180 segundos.</span><span class="sxs-lookup"><span data-stu-id="d824d-109">The default time period is 180 seconds.</span></span>  <span data-ttu-id="d824d-110">Se isso for insuficiente, aumente o `VolatileOutcomeDelay` política de timer para WS-AT.</span><span class="sxs-lookup"><span data-stu-id="d824d-110">If this is insufficient, increase the `VolatileOutcomeDelay` timer policy for WS-AT.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d824d-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d824d-111">See Also</span></span>  
 [<span data-ttu-id="d824d-112">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="d824d-112">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="d824d-113">Usando o rastreamento para solucionar problemas do seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="d824d-113">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="d824d-114">Administração e diagnósticos</span><span class="sxs-lookup"><span data-stu-id="d824d-114">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
