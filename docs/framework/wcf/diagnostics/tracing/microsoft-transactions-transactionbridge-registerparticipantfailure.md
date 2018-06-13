---
title: Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure
ms.date: 03/30/2017
ms.assetid: 3a4ead79-8550-4037-84e3-fd70ff56e001
ms.openlocfilehash: fb5e50e7332269690a200334ef936dd0d5525e9c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33475108"
---
# <a name="microsofttransactionstransactionbridgeregisterparticipantfailure"></a><span data-ttu-id="690a3-102">Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure</span><span class="sxs-lookup"><span data-stu-id="690a3-102">Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure</span></span>
<span data-ttu-id="690a3-103">Falha do serviço de protocolo WS-AT ao registrar um participante para um protocolo de controle.</span><span class="sxs-lookup"><span data-stu-id="690a3-103">The WS-AT protocol service failed to register a participant for a control protocol.</span></span>  
  
## <a name="description"></a><span data-ttu-id="690a3-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="690a3-104">Description</span></span>  
 <span data-ttu-id="690a3-105">Rastreadas se MSDTC detecta uma solicitação de registro inválida.</span><span class="sxs-lookup"><span data-stu-id="690a3-105">Traced if MSDTC detects an invalid Registration request.</span></span> <span data-ttu-id="690a3-106">Isso pode ser causado por várias solicitações de registro de conclusão e erros internos.</span><span class="sxs-lookup"><span data-stu-id="690a3-106">This can be caused by  multiple Completion registration requests and internal errors.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="690a3-107">Solução de problemas</span><span class="sxs-lookup"><span data-stu-id="690a3-107">Troubleshooting</span></span>  
 <span data-ttu-id="690a3-108">Não tente registrar-se para conclusão mais de uma vez.</span><span class="sxs-lookup"><span data-stu-id="690a3-108">Do not try to Register for Completion more than once.</span></span>  <span data-ttu-id="690a3-109">Além disso, verifique a cadeia de caracteres de status dentro da mensagem de rastreamento para determinar se há qualquer item acionável.</span><span class="sxs-lookup"><span data-stu-id="690a3-109">Also, inspect the status string within the trace message to determine if any actionable item exists.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="690a3-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="690a3-110">See Also</span></span>  
 [<span data-ttu-id="690a3-111">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="690a3-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="690a3-112">Usando o rastreamento para solucionar problemas do seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="690a3-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="690a3-113">Administração e diagnósticos</span><span class="sxs-lookup"><span data-stu-id="690a3-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
