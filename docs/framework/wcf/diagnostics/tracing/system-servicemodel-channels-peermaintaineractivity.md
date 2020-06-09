---
title: System.ServiceModel.Channels.PeerMaintainerActivity
ms.date: 03/30/2017
ms.assetid: ef28d086-d7fb-4e81-82e9-45a54647783b
ms.openlocfilehash: ce97eaa2ad5c9dbd5f4d6f81186960c489eb4b85
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596071"
---
# <a name="systemservicemodelchannelspeermaintaineractivity"></a><span data-ttu-id="dbc58-102">System.ServiceModel.Channels.PeerMaintainerActivity</span><span class="sxs-lookup"><span data-stu-id="dbc58-102">System.ServiceModel.Channels.PeerMaintainerActivity</span></span>
<span data-ttu-id="dbc58-103">O módulo PeerMaintainer está executando uma operação específica (detalhes contidos no corpo da mensagem de rastreamento).</span><span class="sxs-lookup"><span data-stu-id="dbc58-103">The PeerMaintainer module is performing a specific operation (details contained within the trace message body).</span></span>  
  
## <a name="description"></a><span data-ttu-id="dbc58-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="dbc58-104">Description</span></span>  
 <span data-ttu-id="dbc58-105">Esse rastreamento ocorre durante várias operações de PeerMaintainer.</span><span class="sxs-lookup"><span data-stu-id="dbc58-105">This trace occurs during various PeerMaintainer operations.</span></span>  
  
 <span data-ttu-id="dbc58-106">PeerMaintainer é um componente interno do PeerNode.</span><span class="sxs-lookup"><span data-stu-id="dbc58-106">PeerMaintainer is an internal component of PeerNode.</span></span> <span data-ttu-id="dbc58-107">A cada minuto, ou a cada 32 mensagens recebidas, ele envia uma mensagem LinkUtility para seus vizinhos com estatísticas sobre quantas mensagens são trocadas e quantos são úteis (não duplicados, não violados).</span><span class="sxs-lookup"><span data-stu-id="dbc58-107">Every minute, or every 32 messages received, it sends a LinkUtility message to its neighbors with statistics about how many messages are exchanged and how many are useful (non-duplicates, untampered).</span></span> <span data-ttu-id="dbc58-108">Isso ajuda a determinar o utilitário de link de um vizinho específico.</span><span class="sxs-lookup"><span data-stu-id="dbc58-108">This helps determine a particular neighbor's Link Utility.</span></span> <span data-ttu-id="dbc58-109">Aproximadamente a cada cinco minutos, o mantenedor verifica a integridade das conexões vizinhas.</span><span class="sxs-lookup"><span data-stu-id="dbc58-109">Approximately every five minutes, the maintainer checks the health of neighbor connections.</span></span> <span data-ttu-id="dbc58-110">Se o número de conexões vizinhas exceder o valor ideal, o mantenedor removerá as conexões menos úteis.</span><span class="sxs-lookup"><span data-stu-id="dbc58-110">If the number of neighbor connections exceeds the ideal amount, the maintainer prunes off the least useful connections.</span></span> <span data-ttu-id="dbc58-111">Se não houver conexões suficientes, o mantenedor adquirirá novas conexões.</span><span class="sxs-lookup"><span data-stu-id="dbc58-111">If there are not enough connections, the maintainer acquires new connections.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbc58-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dbc58-112">See also</span></span>

- [<span data-ttu-id="dbc58-113">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="dbc58-113">Tracing</span></span>](index.md)
- [<span data-ttu-id="dbc58-114">Utilizando o rastreamento para solucionar problemas em seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="dbc58-114">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="dbc58-115">Administração e diagnóstico</span><span class="sxs-lookup"><span data-stu-id="dbc58-115">Administration and Diagnostics</span></span>](../index.md)
