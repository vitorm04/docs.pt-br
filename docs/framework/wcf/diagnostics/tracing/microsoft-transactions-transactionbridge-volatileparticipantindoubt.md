---
title: Microsoft.Transactions.TransactionBridge.VolatileParticipantInDoubt
ms.date: 03/30/2017
ms.assetid: 3e8fc825-9f22-47e7-9c16-d64ef291c932
ms.openlocfilehash: 9434f2f902a50a37fb3efee22fd3b18b33af9129
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61997440"
---
# <a name="microsofttransactionstransactionbridgevolatileparticipantindoubt"></a><span data-ttu-id="4094a-102">Microsoft.Transactions.TransactionBridge.VolatileParticipantInDoubt</span><span class="sxs-lookup"><span data-stu-id="4094a-102">Microsoft.Transactions.TransactionBridge.VolatileParticipantInDoubt</span></span>
<span data-ttu-id="4094a-103">O serviço de protocolo WS-AT recebeu uma mensagem preparada ou de repetição de um participante volátil não reconhecido.</span><span class="sxs-lookup"><span data-stu-id="4094a-103">The WS-AT protocol service received a Prepared or Replay message from an unrecognized volatile participant.</span></span> <span data-ttu-id="4094a-104">Uma falha foi retornado para o participante, declara que o resultado da transação está em dúvida.</span><span class="sxs-lookup"><span data-stu-id="4094a-104">A fault was returned to the participant, declares that the transaction's outcome is in doubt.</span></span>  
  
## <a name="description"></a><span data-ttu-id="4094a-105">Descrição</span><span class="sxs-lookup"><span data-stu-id="4094a-105">Description</span></span>  
 <span data-ttu-id="4094a-106">Rastreada quando o Gerenciador de transações local recebe uma mensagem preparada ou de repetição de uma inscrição volátil que ele já tenha esquecido.</span><span class="sxs-lookup"><span data-stu-id="4094a-106">Traced when the local Transaction Manager receives a Prepared or Replay message from a Volatile enlistment that it has already forgotten.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="4094a-107">Solução de problemas</span><span class="sxs-lookup"><span data-stu-id="4094a-107">Troubleshooting</span></span>  
 <span data-ttu-id="4094a-108">Investigar as causas em potencial com a última mensagens provenientes do participante volátil.</span><span class="sxs-lookup"><span data-stu-id="4094a-108">Investigate potential causes of late messages coming from the Volatile participant.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4094a-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4094a-109">See also</span></span>

- [<span data-ttu-id="4094a-110">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="4094a-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="4094a-111">Usando o rastreamento para solucionar problemas do seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="4094a-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="4094a-112">Administração e diagnósticos</span><span class="sxs-lookup"><span data-stu-id="4094a-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
