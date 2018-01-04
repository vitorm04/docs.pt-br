---
title: System.ServiceModel.Channels.PeerFlooderReceiveMessageQuotaExceeded
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b8371d0a-843e-440b-b86a-6996db131cb0
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 136baabc0760826aa9ba76dc19862c9c4b60e16e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="systemservicemodelchannelspeerflooderreceivemessagequotaexceeded"></a><span data-ttu-id="aa418-102">System.ServiceModel.Channels.PeerFlooderReceiveMessageQuotaExceeded</span><span class="sxs-lookup"><span data-stu-id="aa418-102">System.ServiceModel.Channels.PeerFlooderReceiveMessageQuotaExceeded</span></span>
<span data-ttu-id="aa418-103">A taxa de entrada de recebimento de mensagens é muito alta.</span><span class="sxs-lookup"><span data-stu-id="aa418-103">The inbound receive rate of messages is too high.</span></span>  
  
## <a name="description"></a><span data-ttu-id="aa418-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="aa418-104">Description</span></span>  
 <span data-ttu-id="aa418-105">Este rastreamento ocorre ao tentar processar as mensagens de entrada.</span><span class="sxs-lookup"><span data-stu-id="aa418-105">This trace occurs when attempting to process inbound messages.</span></span> <span data-ttu-id="aa418-106">Uma mensagem não pôde ser encaminhada para um vizinho específico porque a cota definida para esse vizinho foi excedida.</span><span class="sxs-lookup"><span data-stu-id="aa418-106">A message could not be forwarded to a specific neighbor because the quota set for that neighbor has been exceeded.</span></span> <span data-ttu-id="aa418-107">Isso ocorre quando um vizinho não responder Falha ao limpar uma lista de pendências de mensagens pendentes para vizinho.</span><span class="sxs-lookup"><span data-stu-id="aa418-107">This occurs when an unresponsive neighbor fails to clear a backlog of messages pending for that neighbor.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="aa418-108">Solução de problemas</span><span class="sxs-lookup"><span data-stu-id="aa418-108">Troubleshooting</span></span>  
 <span data-ttu-id="aa418-109">Reduza a taxa na qual as mensagens são enviadas dentro da malha.</span><span class="sxs-lookup"><span data-stu-id="aa418-109">Reduce the rate at which messages are sent within the mesh.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa418-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="aa418-110">See Also</span></span>  
 [<span data-ttu-id="aa418-111">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="aa418-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="aa418-112">Usando o rastreamento para solucionar problemas do seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="aa418-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="aa418-113">Administração e diagnósticos</span><span class="sxs-lookup"><span data-stu-id="aa418-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
