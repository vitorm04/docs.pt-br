---
title: Microsoft.Transactions.TransactionBridge.PreparedMessageRetry
ms.date: 03/30/2017
ms.assetid: 2194292d-bf5f-4aef-9336-cd3c4795cb71
ms.openlocfilehash: 50dd3070525bbc6d36956b25dee587ec7864d3ff
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594303"
---
# <a name="microsofttransactionstransactionbridgepreparedmessageretry"></a><span data-ttu-id="1ae64-102">Microsoft.Transactions.TransactionBridge.PreparedMessageRetry</span><span class="sxs-lookup"><span data-stu-id="1ae64-102">Microsoft.Transactions.TransactionBridge.PreparedMessageRetry</span></span>
<span data-ttu-id="1ae64-103">Uma nova tentativa de mensagem preparada foi enviada a um coordenador sem resposta.</span><span class="sxs-lookup"><span data-stu-id="1ae64-103">A prepared message retry was sent to an unresponsive coordinator.</span></span>  
  
## <a name="description"></a><span data-ttu-id="1ae64-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="1ae64-104">Description</span></span>  
 <span data-ttu-id="1ae64-105">Rastreado se o Gerenciador de transações local precisar reenviar uma mensagem preparada para um coordenador superior porque ele não recebeu uma resposta em um determinado período/</span><span class="sxs-lookup"><span data-stu-id="1ae64-105">Traced if the local Transaction Manager needed to resend a Prepared message to a superior coordinator because it did not receive a response in a given amount of time/</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="1ae64-106">Solução de problemas</span><span class="sxs-lookup"><span data-stu-id="1ae64-106">Troubleshooting</span></span>  
 <span data-ttu-id="1ae64-107">Investigue possíveis problemas de rede ou de produtos que impedem que a resposta seja entregue no prazo.</span><span class="sxs-lookup"><span data-stu-id="1ae64-107">Investigate potential network or product issues that prevent the response from being delivered on time.</span></span>  <span data-ttu-id="1ae64-108">Se muitas dessas mensagens forem vistas, isso poderá indicar problemas de infraestrutura ou tempos de resposta muito longos.</span><span class="sxs-lookup"><span data-stu-id="1ae64-108">If many of these messages are seen, it can indicate infrastructure problems or abnormally long response times.</span></span> <span data-ttu-id="1ae64-109">Os dois problemas reduzem drasticamente a taxa de transferência das transações no sistema.</span><span class="sxs-lookup"><span data-stu-id="1ae64-109">Both issues will drastically reduce the throughput of transactions within the system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ae64-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1ae64-110">See also</span></span>

- [<span data-ttu-id="1ae64-111">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="1ae64-111">Tracing</span></span>](index.md)
- [<span data-ttu-id="1ae64-112">Utilizando o rastreamento para solucionar problemas em seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="1ae64-112">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="1ae64-113">Administração e diagnóstico</span><span class="sxs-lookup"><span data-stu-id="1ae64-113">Administration and Diagnostics</span></span>](../index.md)
