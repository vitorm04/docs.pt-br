---
title: System.ServiceModel.Channels.PeerMaintainerActivity
ms.date: 03/30/2017
ms.assetid: ef28d086-d7fb-4e81-82e9-45a54647783b
ms.openlocfilehash: a7f353b00796c845f5686ca2926bbe7effe09e3e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33480578"
---
# <a name="systemservicemodelchannelspeermaintaineractivity"></a><span data-ttu-id="866a2-102">System.ServiceModel.Channels.PeerMaintainerActivity</span><span class="sxs-lookup"><span data-stu-id="866a2-102">System.ServiceModel.Channels.PeerMaintainerActivity</span></span>
<span data-ttu-id="866a2-103">O módulo PeerMaintainer está executando uma operação específica (contidos no corpo da mensagem de rastreamento para obter detalhes).</span><span class="sxs-lookup"><span data-stu-id="866a2-103">The PeerMaintainer module is performing a specific operation (details contained within the trace message body).</span></span>  
  
## <a name="description"></a><span data-ttu-id="866a2-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="866a2-104">Description</span></span>  
 <span data-ttu-id="866a2-105">Este rastreamento ocorre durante a várias operações PeerMaintainer.</span><span class="sxs-lookup"><span data-stu-id="866a2-105">This trace occurs during various PeerMaintainer operations.</span></span>  
  
 <span data-ttu-id="866a2-106">PeerMaintainer é um componente interno de PeerNode.</span><span class="sxs-lookup"><span data-stu-id="866a2-106">PeerMaintainer is an internal component of PeerNode.</span></span> <span data-ttu-id="866a2-107">A cada minuto, ou cada 32 mensagens recebidas, ele envia uma mensagem LinkUtility para seus vizinhos com estatísticas sobre quantas mensagens são trocadas e quantas são úteis (não-duplicatas, tratamento).</span><span class="sxs-lookup"><span data-stu-id="866a2-107">Every minute, or every 32 messages received, it sends a LinkUtility message to its neighbors with statistics about how many messages are exchanged and how many are useful (non-duplicates, untampered).</span></span> <span data-ttu-id="866a2-108">Isso ajuda a determinar o utilitário de Link de um vizinho específico.</span><span class="sxs-lookup"><span data-stu-id="866a2-108">This helps determine a particular neighbor's Link Utility.</span></span> <span data-ttu-id="866a2-109">Aproximadamente a cada cinco minutos, o mantenedor verifica a integridade de conexões vizinhas.</span><span class="sxs-lookup"><span data-stu-id="866a2-109">Approximately every five minutes, the maintainer checks the health of neighbor connections.</span></span> <span data-ttu-id="866a2-110">Se o número de conexões vizinhas excede a quantidade ideal, o mantenedor remove desativar as conexões menos úteis.</span><span class="sxs-lookup"><span data-stu-id="866a2-110">If the number of neighbor connections exceeds the ideal amount, the maintainer prunes off the least useful connections.</span></span> <span data-ttu-id="866a2-111">Se não há conexões suficientes, o mantenedor adquire novas conexões.</span><span class="sxs-lookup"><span data-stu-id="866a2-111">If there are not enough connections, the maintainer acquires new connections.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="866a2-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="866a2-112">See Also</span></span>  
 [<span data-ttu-id="866a2-113">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="866a2-113">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="866a2-114">Usando o rastreamento para solucionar problemas do seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="866a2-114">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="866a2-115">Administração e diagnósticos</span><span class="sxs-lookup"><span data-stu-id="866a2-115">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
