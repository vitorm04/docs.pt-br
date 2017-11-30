---
title: Microsoft.Transactions.TransactionBridge.ReplayMessageRetry
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e5b820ae-504d-405a-926a-9effa41d2369
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9e7e87c379c84829934a929ec27bd5dacde3931f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="microsofttransactionstransactionbridgereplaymessageretry"></a><span data-ttu-id="a03bb-102">Microsoft.Transactions.TransactionBridge.ReplayMessageRetry</span><span class="sxs-lookup"><span data-stu-id="a03bb-102">Microsoft.Transactions.TransactionBridge.ReplayMessageRetry</span></span>
<span data-ttu-id="a03bb-103">Uma mensagem de repetição foi enviada a um coordenador que não responde.</span><span class="sxs-lookup"><span data-stu-id="a03bb-103">A replay message retry was sent to an unresponsive coordinator.</span></span>  
  
## <a name="description"></a><span data-ttu-id="a03bb-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="a03bb-104">Description</span></span>  
 <span data-ttu-id="a03bb-105">Rastreado se o Gerenciador de transações local necessário reenviar uma mensagem de repetição para um coordenador superior porque não recebeu uma resposta em uma determinada quantidade de tempo.</span><span class="sxs-lookup"><span data-stu-id="a03bb-105">Traced if the local Transaction Manager needed to resend a Replay message to a superior coordinator because it did not receive a response in a given amount of time.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="a03bb-106">Solução de problemas</span><span class="sxs-lookup"><span data-stu-id="a03bb-106">Troubleshooting</span></span>  
 <span data-ttu-id="a03bb-107">Investigue os possível problemas na rede ou produto que evitar que sejam entregues em tempo de resposta.</span><span class="sxs-lookup"><span data-stu-id="a03bb-107">Investigate potential network or product issues that prevent the response from being delivered on time.</span></span>  <span data-ttu-id="a03bb-108">Se muitas dessas mensagens são vistas, ele pode indicar problemas de infraestrutura ou tempos de resposta anormalmente longo.</span><span class="sxs-lookup"><span data-stu-id="a03bb-108">If many of these messages are seen, it can indicate infrastructure problems or abnormally long response times.</span></span> <span data-ttu-id="a03bb-109">Os dois problemas reduzirá drasticamente a taxa de transferência de transações no sistema.</span><span class="sxs-lookup"><span data-stu-id="a03bb-109">Both issues will drastically reduce the throughput of transactions within the system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a03bb-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a03bb-110">See Also</span></span>  
 [<span data-ttu-id="a03bb-111">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="a03bb-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="a03bb-112">Usando o rastreamento para solucionar problemas de seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="a03bb-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 <span data-ttu-id="a03bb-113">[Administration and Diagnostics](../../../../../docs/framework/wcf/diagnostics/index.md) (Administração e diagnósticos)</span><span class="sxs-lookup"><span data-stu-id="a03bb-113">[Administration and Diagnostics](../../../../../docs/framework/wcf/diagnostics/index.md)</span></span>
