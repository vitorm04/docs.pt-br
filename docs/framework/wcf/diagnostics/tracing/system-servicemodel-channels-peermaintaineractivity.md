---
title: System.ServiceModel.Channels.PeerMaintainerActivity
ms.date: 03/30/2017
ms.assetid: ef28d086-d7fb-4e81-82e9-45a54647783b
ms.openlocfilehash: 4c352ad4ac4ffee5d12c054590ef994bab0ba757
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54642575"
---
# <a name="systemservicemodelchannelspeermaintaineractivity"></a><span data-ttu-id="6d109-102">System.ServiceModel.Channels.PeerMaintainerActivity</span><span class="sxs-lookup"><span data-stu-id="6d109-102">System.ServiceModel.Channels.PeerMaintainerActivity</span></span>
<span data-ttu-id="6d109-103">O módulo PeerMaintainer está executando uma operação específica (contidos no corpo da mensagem de rastreamento para obter detalhes).</span><span class="sxs-lookup"><span data-stu-id="6d109-103">The PeerMaintainer module is performing a specific operation (details contained within the trace message body).</span></span>  
  
## <a name="description"></a><span data-ttu-id="6d109-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="6d109-104">Description</span></span>  
 <span data-ttu-id="6d109-105">Este rastreamento ocorre durante as várias operações de PeerMaintainer.</span><span class="sxs-lookup"><span data-stu-id="6d109-105">This trace occurs during various PeerMaintainer operations.</span></span>  
  
 <span data-ttu-id="6d109-106">PeerMaintainer é um componente interno de PeerNode.</span><span class="sxs-lookup"><span data-stu-id="6d109-106">PeerMaintainer is an internal component of PeerNode.</span></span> <span data-ttu-id="6d109-107">A cada minuto, ou cada 32 mensagens recebidas, ele envia uma mensagem de LinkUtility para seus vizinhos com estatísticas sobre quantas mensagens são trocadas e quantos são úteis (não-duplicatas, tratamento).</span><span class="sxs-lookup"><span data-stu-id="6d109-107">Every minute, or every 32 messages received, it sends a LinkUtility message to its neighbors with statistics about how many messages are exchanged and how many are useful (non-duplicates, untampered).</span></span> <span data-ttu-id="6d109-108">Isso ajuda a determinar o utilitário de Link de um vizinho específico.</span><span class="sxs-lookup"><span data-stu-id="6d109-108">This helps determine a particular neighbor's Link Utility.</span></span> <span data-ttu-id="6d109-109">Aproximadamente a cada cinco minutos, o mantenedor verifica a integridade das conexões de vizinho.</span><span class="sxs-lookup"><span data-stu-id="6d109-109">Approximately every five minutes, the maintainer checks the health of neighbor connections.</span></span> <span data-ttu-id="6d109-110">Se o número de conexões de vizinho exceder a quantidade ideal, o mantenedor remove desativar as conexões menos úteis.</span><span class="sxs-lookup"><span data-stu-id="6d109-110">If the number of neighbor connections exceeds the ideal amount, the maintainer prunes off the least useful connections.</span></span> <span data-ttu-id="6d109-111">Se não há conexões suficientes, o mantenedor adquire novas conexões.</span><span class="sxs-lookup"><span data-stu-id="6d109-111">If there are not enough connections, the maintainer acquires new connections.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d109-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6d109-112">See also</span></span>
- [<span data-ttu-id="6d109-113">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="6d109-113">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="6d109-114">Usando o rastreamento para solucionar problemas do seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="6d109-114">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="6d109-115">Administração e diagnósticos</span><span class="sxs-lookup"><span data-stu-id="6d109-115">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
