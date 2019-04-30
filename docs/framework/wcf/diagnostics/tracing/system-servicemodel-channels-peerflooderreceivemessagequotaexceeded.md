---
title: System.ServiceModel.Channels.PeerFlooderReceiveMessageQuotaExceeded
ms.date: 03/30/2017
ms.assetid: b8371d0a-843e-440b-b86a-6996db131cb0
ms.openlocfilehash: 0ca3d198ce225221348ac7b405ea91ad215cd298
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61950638"
---
# <a name="systemservicemodelchannelspeerflooderreceivemessagequotaexceeded"></a><span data-ttu-id="696e5-102">System.ServiceModel.Channels.PeerFlooderReceiveMessageQuotaExceeded</span><span class="sxs-lookup"><span data-stu-id="696e5-102">System.ServiceModel.Channels.PeerFlooderReceiveMessageQuotaExceeded</span></span>
<span data-ttu-id="696e5-103">A taxa de entrada de recebimento de mensagens é muito alta.</span><span class="sxs-lookup"><span data-stu-id="696e5-103">The inbound receive rate of messages is too high.</span></span>  
  
## <a name="description"></a><span data-ttu-id="696e5-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="696e5-104">Description</span></span>  
 <span data-ttu-id="696e5-105">Este rastreamento ocorre ao tentar processar as mensagens de entrada.</span><span class="sxs-lookup"><span data-stu-id="696e5-105">This trace occurs when attempting to process inbound messages.</span></span> <span data-ttu-id="696e5-106">Uma mensagem não pôde ser encaminhada para um vizinho específico porque a cota definida para aquele vizinho foi excedida.</span><span class="sxs-lookup"><span data-stu-id="696e5-106">A message could not be forwarded to a specific neighbor because the quota set for that neighbor has been exceeded.</span></span> <span data-ttu-id="696e5-107">Isso ocorre quando um vizinho sem resposta Falha ao limpar uma lista de pendências de mensagens pendentes para aquele vizinho.</span><span class="sxs-lookup"><span data-stu-id="696e5-107">This occurs when an unresponsive neighbor fails to clear a backlog of messages pending for that neighbor.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="696e5-108">Solução de problemas</span><span class="sxs-lookup"><span data-stu-id="696e5-108">Troubleshooting</span></span>  
 <span data-ttu-id="696e5-109">Reduza a taxa na qual as mensagens são enviadas dentro da malha.</span><span class="sxs-lookup"><span data-stu-id="696e5-109">Reduce the rate at which messages are sent within the mesh.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="696e5-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="696e5-110">See also</span></span>

- [<span data-ttu-id="696e5-111">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="696e5-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="696e5-112">Usando o rastreamento para solucionar problemas do seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="696e5-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="696e5-113">Administração e diagnósticos</span><span class="sxs-lookup"><span data-stu-id="696e5-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
