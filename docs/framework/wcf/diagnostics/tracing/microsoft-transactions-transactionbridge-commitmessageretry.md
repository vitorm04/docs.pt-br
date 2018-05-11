---
title: Microsoft.Transactions.TransactionBridge.CommitMessageRetry
ms.date: 03/30/2017
ms.assetid: 4abe01f0-6398-4fba-b2f3-c054b7f7e971
ms.openlocfilehash: f1092dd335be793fb3d2212b7b9398cc69d2f79f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="microsofttransactionstransactionbridgecommitmessageretry"></a><span data-ttu-id="0fb0b-102">Microsoft.Transactions.TransactionBridge.CommitMessageRetry</span><span class="sxs-lookup"><span data-stu-id="0fb0b-102">Microsoft.Transactions.TransactionBridge.CommitMessageRetry</span></span>
<span data-ttu-id="0fb0b-103">Uma tentativa de mensagem de confirmação foi enviada a um participante sem resposta.</span><span class="sxs-lookup"><span data-stu-id="0fb0b-103">A commit message retry was sent to an unresponsive participant.</span></span>  
  
## <a name="description"></a><span data-ttu-id="0fb0b-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="0fb0b-104">Description</span></span>  
 <span data-ttu-id="0fb0b-105">Rastreado se o Gerenciador de transações local necessário reenviar uma mensagem de confirmação a um participante subordinado porque não recebeu uma resposta em uma determinada quantidade de tempo.</span><span class="sxs-lookup"><span data-stu-id="0fb0b-105">Traced if the local Transaction Manager needed to resend a Commit message to a subordinate participant because it did not receive a response in a given amount of time.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="0fb0b-106">Solução de problemas</span><span class="sxs-lookup"><span data-stu-id="0fb0b-106">Troubleshooting</span></span>  
 <span data-ttu-id="0fb0b-107">Investigue os possível problemas na rede ou produto que evitar que sejam entregues em tempo de resposta.</span><span class="sxs-lookup"><span data-stu-id="0fb0b-107">Investigate potential network or product issues that prevent the response from being delivered on time.</span></span>  <span data-ttu-id="0fb0b-108">Se muitas dessas mensagens são vistas, ele pode indicar problemas de infraestrutura ou tempos de resposta anormalmente longo.</span><span class="sxs-lookup"><span data-stu-id="0fb0b-108">If many of these messages are seen, it can indicate infrastructure problems or abnormally long response times.</span></span> <span data-ttu-id="0fb0b-109">Os dois problemas reduzirá drasticamente a taxa de transferência de transações no sistema.</span><span class="sxs-lookup"><span data-stu-id="0fb0b-109">Both issues will drastically reduce the throughput of transactions within the system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0fb0b-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0fb0b-110">See Also</span></span>  
 [<span data-ttu-id="0fb0b-111">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="0fb0b-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="0fb0b-112">Usando o rastreamento para solucionar problemas do seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="0fb0b-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="0fb0b-113">Administração e diagnósticos</span><span class="sxs-lookup"><span data-stu-id="0fb0b-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
