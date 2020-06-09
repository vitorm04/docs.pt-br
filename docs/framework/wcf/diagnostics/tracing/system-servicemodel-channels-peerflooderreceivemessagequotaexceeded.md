---
title: System.ServiceModel.Channels.PeerFlooderReceiveMessageQuotaExceeded
ms.date: 03/30/2017
ms.assetid: b8371d0a-843e-440b-b86a-6996db131cb0
ms.openlocfilehash: 93afa0b495e20c02c58ac1fa75c31715eaa0e8dc
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596084"
---
# <a name="systemservicemodelchannelspeerflooderreceivemessagequotaexceeded"></a><span data-ttu-id="33149-102">System.ServiceModel.Channels.PeerFlooderReceiveMessageQuotaExceeded</span><span class="sxs-lookup"><span data-stu-id="33149-102">System.ServiceModel.Channels.PeerFlooderReceiveMessageQuotaExceeded</span></span>
<span data-ttu-id="33149-103">A taxa de recebimento de mensagens de entrada é muito alta.</span><span class="sxs-lookup"><span data-stu-id="33149-103">The inbound receive rate of messages is too high.</span></span>  
  
## <a name="description"></a><span data-ttu-id="33149-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="33149-104">Description</span></span>  
 <span data-ttu-id="33149-105">Esse rastreamento ocorre ao tentar processar mensagens de entrada.</span><span class="sxs-lookup"><span data-stu-id="33149-105">This trace occurs when attempting to process inbound messages.</span></span> <span data-ttu-id="33149-106">Uma mensagem não pôde ser encaminhada para um vizinho específico porque o conjunto de cotas para esse vizinho foi excedido.</span><span class="sxs-lookup"><span data-stu-id="33149-106">A message could not be forwarded to a specific neighbor because the quota set for that neighbor has been exceeded.</span></span> <span data-ttu-id="33149-107">Isso ocorre quando um vizinho sem resposta falha ao limpar uma pendência de mensagens pendentes para esse vizinho.</span><span class="sxs-lookup"><span data-stu-id="33149-107">This occurs when an unresponsive neighbor fails to clear a backlog of messages pending for that neighbor.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="33149-108">Solução de problemas</span><span class="sxs-lookup"><span data-stu-id="33149-108">Troubleshooting</span></span>  
 <span data-ttu-id="33149-109">Reduza a taxa em que as mensagens são enviadas dentro da malha.</span><span class="sxs-lookup"><span data-stu-id="33149-109">Reduce the rate at which messages are sent within the mesh.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33149-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="33149-110">See also</span></span>

- [<span data-ttu-id="33149-111">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="33149-111">Tracing</span></span>](index.md)
- [<span data-ttu-id="33149-112">Utilizando o rastreamento para solucionar problemas em seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="33149-112">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="33149-113">Administração e diagnóstico</span><span class="sxs-lookup"><span data-stu-id="33149-113">Administration and Diagnostics</span></span>](../index.md)
