---
title: Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout
ms.date: 03/30/2017
ms.assetid: 2dbe34c5-57c7-4b64-9257-63021911d03c
ms.openlocfilehash: dd2a0b67ec140aa2e6fe1abad8e85c0206abd8ea
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84579015"
---
# <a name="microsofttransactionstransactionbridgevolatileoutcometimeout"></a><span data-ttu-id="14edc-102">Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout</span><span class="sxs-lookup"><span data-stu-id="14edc-102">Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout</span></span>
<span data-ttu-id="14edc-103">O tempo limite do serviço de protocolo WS-AT expirou ao aguardar uma resposta a uma mensagem de resultado de um participante volátil.</span><span class="sxs-lookup"><span data-stu-id="14edc-103">The WS-AT protocol service timed out waiting for a response to an outcome message from a volatile participant.</span></span> <span data-ttu-id="14edc-104">O resultado da transação pode estar em dúvida se o participante retornar.</span><span class="sxs-lookup"><span data-stu-id="14edc-104">The transaction outcome may be in doubt if the participant returns.</span></span>  
  
## <a name="description"></a><span data-ttu-id="14edc-105">Descrição</span><span class="sxs-lookup"><span data-stu-id="14edc-105">Description</span></span>  
 <span data-ttu-id="14edc-106">Rastreado quando um participante volátil decidiu confirmar ou anular, mas não respondeu a uma solicitação de confirmação ou reversão em um determinado período de tempo.</span><span class="sxs-lookup"><span data-stu-id="14edc-106">Traced when a Volatile participant has decided to Commit or Abort but has not responded to a Commit or Rollback request within a given amount of time.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="14edc-107">Solução de problemas</span><span class="sxs-lookup"><span data-stu-id="14edc-107">Troubleshooting</span></span>  
 <span data-ttu-id="14edc-108">Certifique-se de que todos os participantes voláteis sejam capazes de responder dentro do período determinado.</span><span class="sxs-lookup"><span data-stu-id="14edc-108">Ensure that all Volatile participants are able to respond within the given amount of time.</span></span> <span data-ttu-id="14edc-109">O período de tempo padrão é de 180 segundos.</span><span class="sxs-lookup"><span data-stu-id="14edc-109">The default time period is 180 seconds.</span></span>  <span data-ttu-id="14edc-110">Se isso for insuficiente, aumente a `VolatileOutcomeDelay` política de temporizador para WS-AT.</span><span class="sxs-lookup"><span data-stu-id="14edc-110">If this is insufficient, increase the `VolatileOutcomeDelay` timer policy for WS-AT.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14edc-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="14edc-111">See also</span></span>

- [<span data-ttu-id="14edc-112">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="14edc-112">Tracing</span></span>](index.md)
- [<span data-ttu-id="14edc-113">Utilizando o rastreamento para solucionar problemas em seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="14edc-113">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="14edc-114">Administração e diagnóstico</span><span class="sxs-lookup"><span data-stu-id="14edc-114">Administration and Diagnostics</span></span>](../index.md)
