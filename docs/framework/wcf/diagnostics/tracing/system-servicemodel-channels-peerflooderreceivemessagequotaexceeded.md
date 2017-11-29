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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2931eec5646b44eea19d70b11eb43c056b0ee0e2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="systemservicemodelchannelspeerflooderreceivemessagequotaexceeded"></a><span data-ttu-id="c6d90-102">System.ServiceModel.Channels.PeerFlooderReceiveMessageQuotaExceeded</span><span class="sxs-lookup"><span data-stu-id="c6d90-102">System.ServiceModel.Channels.PeerFlooderReceiveMessageQuotaExceeded</span></span>
<span data-ttu-id="c6d90-103">A taxa de entrada de recebimento de mensagens é muito alta.</span><span class="sxs-lookup"><span data-stu-id="c6d90-103">The inbound receive rate of messages is too high.</span></span>  
  
## <a name="description"></a><span data-ttu-id="c6d90-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="c6d90-104">Description</span></span>  
 <span data-ttu-id="c6d90-105">Este rastreamento ocorre ao tentar processar as mensagens de entrada.</span><span class="sxs-lookup"><span data-stu-id="c6d90-105">This trace occurs when attempting to process inbound messages.</span></span> <span data-ttu-id="c6d90-106">Uma mensagem não pôde ser encaminhada para um vizinho específico porque a cota definida para esse vizinho foi excedida.</span><span class="sxs-lookup"><span data-stu-id="c6d90-106">A message could not be forwarded to a specific neighbor because the quota set for that neighbor has been exceeded.</span></span> <span data-ttu-id="c6d90-107">Isso ocorre quando um vizinho não responder Falha ao limpar uma lista de pendências de mensagens pendentes para vizinho.</span><span class="sxs-lookup"><span data-stu-id="c6d90-107">This occurs when an unresponsive neighbor fails to clear a backlog of messages pending for that neighbor.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="c6d90-108">Solução de problemas</span><span class="sxs-lookup"><span data-stu-id="c6d90-108">Troubleshooting</span></span>  
 <span data-ttu-id="c6d90-109">Reduza a taxa na qual as mensagens são enviadas dentro da malha.</span><span class="sxs-lookup"><span data-stu-id="c6d90-109">Reduce the rate at which messages are sent within the mesh.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6d90-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c6d90-110">See Also</span></span>  
 [<span data-ttu-id="c6d90-111">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="c6d90-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="c6d90-112">Usando o rastreamento para solucionar problemas de seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="c6d90-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 <span data-ttu-id="c6d90-113">[Administration and Diagnostics](../../../../../docs/framework/wcf/diagnostics/index.md) (Administração e diagnósticos)</span><span class="sxs-lookup"><span data-stu-id="c6d90-113">[Administration and Diagnostics](../../../../../docs/framework/wcf/diagnostics/index.md)</span></span>
