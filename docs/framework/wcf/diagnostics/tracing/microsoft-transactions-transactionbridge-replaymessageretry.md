---
title: Microsoft.Transactions.TransactionBridge.ReplayMessageRetry
ms.date: 03/30/2017
ms.assetid: e5b820ae-504d-405a-926a-9effa41d2369
ms.openlocfilehash: d000447245d973916dfe0df9af5c46b6fa822e32
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33475124"
---
# <a name="microsofttransactionstransactionbridgereplaymessageretry"></a><span data-ttu-id="de3db-102">Microsoft.Transactions.TransactionBridge.ReplayMessageRetry</span><span class="sxs-lookup"><span data-stu-id="de3db-102">Microsoft.Transactions.TransactionBridge.ReplayMessageRetry</span></span>
<span data-ttu-id="de3db-103">Uma mensagem de repetição foi enviada a um coordenador que não responde.</span><span class="sxs-lookup"><span data-stu-id="de3db-103">A replay message retry was sent to an unresponsive coordinator.</span></span>  
  
## <a name="description"></a><span data-ttu-id="de3db-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="de3db-104">Description</span></span>  
 <span data-ttu-id="de3db-105">Rastreado se o Gerenciador de transações local necessário reenviar uma mensagem de repetição para um coordenador superior porque não recebeu uma resposta em uma determinada quantidade de tempo.</span><span class="sxs-lookup"><span data-stu-id="de3db-105">Traced if the local Transaction Manager needed to resend a Replay message to a superior coordinator because it did not receive a response in a given amount of time.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="de3db-106">Solução de problemas</span><span class="sxs-lookup"><span data-stu-id="de3db-106">Troubleshooting</span></span>  
 <span data-ttu-id="de3db-107">Investigue os possível problemas na rede ou produto que evitar que sejam entregues em tempo de resposta.</span><span class="sxs-lookup"><span data-stu-id="de3db-107">Investigate potential network or product issues that prevent the response from being delivered on time.</span></span>  <span data-ttu-id="de3db-108">Se muitas dessas mensagens são vistas, ele pode indicar problemas de infraestrutura ou tempos de resposta anormalmente longo.</span><span class="sxs-lookup"><span data-stu-id="de3db-108">If many of these messages are seen, it can indicate infrastructure problems or abnormally long response times.</span></span> <span data-ttu-id="de3db-109">Os dois problemas reduzirá drasticamente a taxa de transferência de transações no sistema.</span><span class="sxs-lookup"><span data-stu-id="de3db-109">Both issues will drastically reduce the throughput of transactions within the system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de3db-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="de3db-110">See Also</span></span>  
 [<span data-ttu-id="de3db-111">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="de3db-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="de3db-112">Usando o rastreamento para solucionar problemas do seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="de3db-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="de3db-113">Administração e diagnósticos</span><span class="sxs-lookup"><span data-stu-id="de3db-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
