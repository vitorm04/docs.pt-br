---
title: Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3a4ead79-8550-4037-84e3-fd70ff56e001
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2e3cbe9443f32ec9752198646e96cc1012d7343c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="microsofttransactionstransactionbridgeregisterparticipantfailure"></a><span data-ttu-id="e12ab-102">Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure</span><span class="sxs-lookup"><span data-stu-id="e12ab-102">Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure</span></span>
<span data-ttu-id="e12ab-103">Falha do serviço de protocolo WS-AT ao registrar um participante para um protocolo de controle.</span><span class="sxs-lookup"><span data-stu-id="e12ab-103">The WS-AT protocol service failed to register a participant for a control protocol.</span></span>  
  
## <a name="description"></a><span data-ttu-id="e12ab-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="e12ab-104">Description</span></span>  
 <span data-ttu-id="e12ab-105">Rastreadas se MSDTC detecta uma solicitação de registro inválida.</span><span class="sxs-lookup"><span data-stu-id="e12ab-105">Traced if MSDTC detects an invalid Registration request.</span></span> <span data-ttu-id="e12ab-106">Isso pode ser causado por várias solicitações de registro de conclusão e erros internos.</span><span class="sxs-lookup"><span data-stu-id="e12ab-106">This can be caused by  multiple Completion registration requests and internal errors.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="e12ab-107">Solução de problemas</span><span class="sxs-lookup"><span data-stu-id="e12ab-107">Troubleshooting</span></span>  
 <span data-ttu-id="e12ab-108">Não tente registrar-se para conclusão mais de uma vez.</span><span class="sxs-lookup"><span data-stu-id="e12ab-108">Do not try to Register for Completion more than once.</span></span>  <span data-ttu-id="e12ab-109">Além disso, verifique a cadeia de caracteres de status dentro da mensagem de rastreamento para determinar se há qualquer item acionável.</span><span class="sxs-lookup"><span data-stu-id="e12ab-109">Also, inspect the status string within the trace message to determine if any actionable item exists.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e12ab-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e12ab-110">See Also</span></span>  
 [<span data-ttu-id="e12ab-111">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="e12ab-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="e12ab-112">Usando o rastreamento para solucionar problemas de seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="e12ab-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 <span data-ttu-id="e12ab-113">[Administration and Diagnostics](../../../../../docs/framework/wcf/diagnostics/index.md) (Administração e diagnósticos)</span><span class="sxs-lookup"><span data-stu-id="e12ab-113">[Administration and Diagnostics](../../../../../docs/framework/wcf/diagnostics/index.md)</span></span>
