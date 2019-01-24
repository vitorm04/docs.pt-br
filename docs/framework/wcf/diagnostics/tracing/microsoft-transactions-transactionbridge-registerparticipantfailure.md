---
title: Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure
ms.date: 03/30/2017
ms.assetid: 3a4ead79-8550-4037-84e3-fd70ff56e001
ms.openlocfilehash: b94c017f6ed3a76a6bc5ed2cb970877ad18ef9ea
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54610416"
---
# <a name="microsofttransactionstransactionbridgeregisterparticipantfailure"></a><span data-ttu-id="c6c0a-102">Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure</span><span class="sxs-lookup"><span data-stu-id="c6c0a-102">Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure</span></span>
<span data-ttu-id="c6c0a-103">O serviço de protocolo WS-AT Falha ao registrar um participante para um protocolo de controle.</span><span class="sxs-lookup"><span data-stu-id="c6c0a-103">The WS-AT protocol service failed to register a participant for a control protocol.</span></span>  
  
## <a name="description"></a><span data-ttu-id="c6c0a-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="c6c0a-104">Description</span></span>  
 <span data-ttu-id="c6c0a-105">Rastreados se MSDTC detectar uma solicitação de registro inválido.</span><span class="sxs-lookup"><span data-stu-id="c6c0a-105">Traced if MSDTC detects an invalid Registration request.</span></span> <span data-ttu-id="c6c0a-106">Isso pode ser causado por várias solicitações de registro de conclusão e erros internos.</span><span class="sxs-lookup"><span data-stu-id="c6c0a-106">This can be caused by  multiple Completion registration requests and internal errors.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="c6c0a-107">Solução de problemas</span><span class="sxs-lookup"><span data-stu-id="c6c0a-107">Troubleshooting</span></span>  
 <span data-ttu-id="c6c0a-108">Não tente registrar-se para a conclusão mais de uma vez.</span><span class="sxs-lookup"><span data-stu-id="c6c0a-108">Do not try to Register for Completion more than once.</span></span>  <span data-ttu-id="c6c0a-109">Além disso, inspecione a cadeia de caracteres de status dentro da mensagem de rastreamento para determinar se há qualquer item acionável.</span><span class="sxs-lookup"><span data-stu-id="c6c0a-109">Also, inspect the status string within the trace message to determine if any actionable item exists.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6c0a-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c6c0a-110">See also</span></span>
- [<span data-ttu-id="c6c0a-111">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="c6c0a-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="c6c0a-112">Usando o rastreamento para solucionar problemas do seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="c6c0a-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="c6c0a-113">Administração e diagnósticos</span><span class="sxs-lookup"><span data-stu-id="c6c0a-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
