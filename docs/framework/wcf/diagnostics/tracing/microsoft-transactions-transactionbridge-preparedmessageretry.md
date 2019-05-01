---
title: Microsoft.Transactions.TransactionBridge.PreparedMessageRetry
ms.date: 03/30/2017
ms.assetid: 2194292d-bf5f-4aef-9336-cd3c4795cb71
ms.openlocfilehash: d8acdb2f94e752860025ee2963aa78682b43b079
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61997887"
---
# <a name="microsofttransactionstransactionbridgepreparedmessageretry"></a><span data-ttu-id="0ad11-102">Microsoft.Transactions.TransactionBridge.PreparedMessageRetry</span><span class="sxs-lookup"><span data-stu-id="0ad11-102">Microsoft.Transactions.TransactionBridge.PreparedMessageRetry</span></span>
<span data-ttu-id="0ad11-103">Uma tentativa de mensagem preparada foi enviada a um coordenador não responder.</span><span class="sxs-lookup"><span data-stu-id="0ad11-103">A prepared message retry was sent to an unresponsive coordinator.</span></span>  
  
## <a name="description"></a><span data-ttu-id="0ad11-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ad11-104">Description</span></span>  
 <span data-ttu-id="0ad11-105">Rastreados se o Gerenciador de transações local necessário reenviar uma mensagem preparada para um coordenador superior porque não recebeu uma resposta em uma determinada quantidade de tempo /</span><span class="sxs-lookup"><span data-stu-id="0ad11-105">Traced if the local Transaction Manager needed to resend a Prepared message to a superior coordinator because it did not receive a response in a given amount of time/</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="0ad11-106">Solução de problemas</span><span class="sxs-lookup"><span data-stu-id="0ad11-106">Troubleshooting</span></span>  
 <span data-ttu-id="0ad11-107">Investigar os potencial rede ou problemas do produto que evitar que sejam entregues em tempo de resposta.</span><span class="sxs-lookup"><span data-stu-id="0ad11-107">Investigate potential network or product issues that prevent the response from being delivered on time.</span></span>  <span data-ttu-id="0ad11-108">Se muitas dessas mensagens são vistas, isso pode indicar problemas de infraestrutura ou tempos de resposta anormalmente longo.</span><span class="sxs-lookup"><span data-stu-id="0ad11-108">If many of these messages are seen, it can indicate infrastructure problems or abnormally long response times.</span></span> <span data-ttu-id="0ad11-109">Os dois problemas reduzirá drasticamente a taxa de transferência de transações no sistema.</span><span class="sxs-lookup"><span data-stu-id="0ad11-109">Both issues will drastically reduce the throughput of transactions within the system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ad11-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ad11-110">See also</span></span>

- [<span data-ttu-id="0ad11-111">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="0ad11-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="0ad11-112">Usando o rastreamento para solucionar problemas do seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="0ad11-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="0ad11-113">Administração e diagnósticos</span><span class="sxs-lookup"><span data-stu-id="0ad11-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
