---
title: System.ServiceModel.Channels.PeerMaintainerActivity
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ef28d086-d7fb-4e81-82e9-45a54647783b
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f3cde90bf5e9c57ff54378eaaf970aec219871a7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="systemservicemodelchannelspeermaintaineractivity"></a><span data-ttu-id="20c8a-102">System.ServiceModel.Channels.PeerMaintainerActivity</span><span class="sxs-lookup"><span data-stu-id="20c8a-102">System.ServiceModel.Channels.PeerMaintainerActivity</span></span>
<span data-ttu-id="20c8a-103">O módulo PeerMaintainer está executando uma operação específica (contidos no corpo da mensagem de rastreamento para obter detalhes).</span><span class="sxs-lookup"><span data-stu-id="20c8a-103">The PeerMaintainer module is performing a specific operation (details contained within the trace message body).</span></span>  
  
## <a name="description"></a><span data-ttu-id="20c8a-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="20c8a-104">Description</span></span>  
 <span data-ttu-id="20c8a-105">Este rastreamento ocorre durante a várias operações PeerMaintainer.</span><span class="sxs-lookup"><span data-stu-id="20c8a-105">This trace occurs during various PeerMaintainer operations.</span></span>  
  
 <span data-ttu-id="20c8a-106">PeerMaintainer é um componente interno de PeerNode.</span><span class="sxs-lookup"><span data-stu-id="20c8a-106">PeerMaintainer is an internal component of PeerNode.</span></span> <span data-ttu-id="20c8a-107">A cada minuto, ou cada 32 mensagens recebidas, ele envia uma mensagem LinkUtility para seus vizinhos com estatísticas sobre quantas mensagens são trocadas e quantas são úteis (não-duplicatas, tratamento).</span><span class="sxs-lookup"><span data-stu-id="20c8a-107">Every minute, or every 32 messages received, it sends a LinkUtility message to its neighbors with statistics about how many messages are exchanged and how many are useful (non-duplicates, untampered).</span></span> <span data-ttu-id="20c8a-108">Isso ajuda a determinar o utilitário de Link de um vizinho específico.</span><span class="sxs-lookup"><span data-stu-id="20c8a-108">This helps determine a particular neighbor's Link Utility.</span></span> <span data-ttu-id="20c8a-109">Aproximadamente a cada cinco minutos, o mantenedor verifica a integridade de conexões vizinhas.</span><span class="sxs-lookup"><span data-stu-id="20c8a-109">Approximately every five minutes, the maintainer checks the health of neighbor connections.</span></span> <span data-ttu-id="20c8a-110">Se o número de conexões vizinhas excede a quantidade ideal, o mantenedor remove desativar as conexões menos úteis.</span><span class="sxs-lookup"><span data-stu-id="20c8a-110">If the number of neighbor connections exceeds the ideal amount, the maintainer prunes off the least useful connections.</span></span> <span data-ttu-id="20c8a-111">Se não há conexões suficientes, o mantenedor adquire novas conexões.</span><span class="sxs-lookup"><span data-stu-id="20c8a-111">If there are not enough connections, the maintainer acquires new connections.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20c8a-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="20c8a-112">See Also</span></span>  
 [<span data-ttu-id="20c8a-113">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="20c8a-113">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="20c8a-114">Usando o rastreamento para solucionar problemas de seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="20c8a-114">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 <span data-ttu-id="20c8a-115">[Administration and Diagnostics](../../../../../docs/framework/wcf/diagnostics/index.md) (Administração e diagnósticos)</span><span class="sxs-lookup"><span data-stu-id="20c8a-115">[Administration and Diagnostics](../../../../../docs/framework/wcf/diagnostics/index.md)</span></span>
