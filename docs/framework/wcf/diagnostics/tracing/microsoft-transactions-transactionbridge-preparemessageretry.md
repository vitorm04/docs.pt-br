---
title: Microsoft.Transactions.TransactionBridge.PrepareMessageRetry
ms.date: 03/30/2017
ms.assetid: ada4baa5-b60d-46b8-ad46-4d69f8d8a9fa
ms.openlocfilehash: f168cb24d87f3159a1ea41003c2ffa7041ce8c09
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54710437"
---
# <a name="microsofttransactionstransactionbridgepreparemessageretry"></a><span data-ttu-id="629ee-102">Microsoft.Transactions.TransactionBridge.PrepareMessageRetry</span><span class="sxs-lookup"><span data-stu-id="629ee-102">Microsoft.Transactions.TransactionBridge.PrepareMessageRetry</span></span>
<span data-ttu-id="629ee-103">Uma tentativa de preparação de mensagem foi enviada a um participante sem resposta.</span><span class="sxs-lookup"><span data-stu-id="629ee-103">A prepare message retry was sent to an unresponsive participant.</span></span>  
  
## <a name="description"></a><span data-ttu-id="629ee-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="629ee-104">Description</span></span>  
 <span data-ttu-id="629ee-105">Rastreados se o Gerenciador de transações local necessário reenviar uma mensagem de preparação para um participante subordinado porque não recebeu uma resposta em uma determinada quantidade de tempo.</span><span class="sxs-lookup"><span data-stu-id="629ee-105">Traced if the local Transaction Manager needed to resend a Prepare message to a subordinate participant because it did not receive a response in a given amount of time.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="629ee-106">Solução de problemas</span><span class="sxs-lookup"><span data-stu-id="629ee-106">Troubleshooting</span></span>  
 <span data-ttu-id="629ee-107">Investigar os potencial rede ou problemas do produto que evitar que sejam entregues em tempo de resposta.</span><span class="sxs-lookup"><span data-stu-id="629ee-107">Investigate potential network or product issues that prevent the response from being delivered on time.</span></span>  <span data-ttu-id="629ee-108">Se muitas dessas mensagens são vistas, isso pode indicar problemas de infraestrutura ou tempos de resposta anormalmente longo.</span><span class="sxs-lookup"><span data-stu-id="629ee-108">If many of these messages are seen, it can indicate infrastructure problems or abnormally long response times.</span></span> <span data-ttu-id="629ee-109">Os dois problemas podem reduzir drasticamente a taxa de transferência de transações no sistema.</span><span class="sxs-lookup"><span data-stu-id="629ee-109">Both issues can drastically reduce the throughput of transactions within the system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="629ee-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="629ee-110">See also</span></span>
- [<span data-ttu-id="629ee-111">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="629ee-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="629ee-112">Usando o rastreamento para solucionar problemas do seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="629ee-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="629ee-113">Administração e diagnósticos</span><span class="sxs-lookup"><span data-stu-id="629ee-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
