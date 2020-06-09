---
title: Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure
ms.date: 03/30/2017
ms.assetid: 3a4ead79-8550-4037-84e3-fd70ff56e001
ms.openlocfilehash: 1819a269a6775c8541f38f4aa5d733002e3c1e9f
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599667"
---
# <a name="microsofttransactionstransactionbridgeregisterparticipantfailure"></a><span data-ttu-id="2d2b5-102">Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure</span><span class="sxs-lookup"><span data-stu-id="2d2b5-102">Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure</span></span>
<span data-ttu-id="2d2b5-103">Falha do serviço de protocolo WS-AT ao registrar um participante para um protocolo de controle.</span><span class="sxs-lookup"><span data-stu-id="2d2b5-103">The WS-AT protocol service failed to register a participant for a control protocol.</span></span>  
  
## <a name="description"></a><span data-ttu-id="2d2b5-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="2d2b5-104">Description</span></span>  
 <span data-ttu-id="2d2b5-105">Rastreado se o MSDTC detectar uma solicitação de registro inválida.</span><span class="sxs-lookup"><span data-stu-id="2d2b5-105">Traced if MSDTC detects an invalid Registration request.</span></span> <span data-ttu-id="2d2b5-106">Isso pode ser causado por várias solicitações de registro de conclusão e erros internos.</span><span class="sxs-lookup"><span data-stu-id="2d2b5-106">This can be caused by  multiple Completion registration requests and internal errors.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="2d2b5-107">Solução de problemas</span><span class="sxs-lookup"><span data-stu-id="2d2b5-107">Troubleshooting</span></span>  
 <span data-ttu-id="2d2b5-108">Não tente se registrar para conclusão mais de uma vez.</span><span class="sxs-lookup"><span data-stu-id="2d2b5-108">Do not try to Register for Completion more than once.</span></span>  <span data-ttu-id="2d2b5-109">Além disso, inspecione a cadeia de caracteres de status na mensagem de rastreamento para determinar se existe algum item acionável.</span><span class="sxs-lookup"><span data-stu-id="2d2b5-109">Also, inspect the status string within the trace message to determine if any actionable item exists.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d2b5-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2d2b5-110">See also</span></span>

- [<span data-ttu-id="2d2b5-111">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="2d2b5-111">Tracing</span></span>](index.md)
- [<span data-ttu-id="2d2b5-112">Utilizando o rastreamento para solucionar problemas em seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="2d2b5-112">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="2d2b5-113">Administração e diagnóstico</span><span class="sxs-lookup"><span data-stu-id="2d2b5-113">Administration and Diagnostics</span></span>](../index.md)
