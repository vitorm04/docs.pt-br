---
title: System.ServiceModel.Channels.MsmqPoisonMessageRejected
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0e64b9bd-1f12-43df-a189-d7be3c2bace1
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 28924f04dc83387f49c2369c2598c028f9b8d4bb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="systemservicemodelchannelsmsmqpoisonmessagerejected"></a><span data-ttu-id="7ab12-102">System.ServiceModel.Channels.MsmqPoisonMessageRejected</span><span class="sxs-lookup"><span data-stu-id="7ab12-102">System.ServiceModel.Channels.MsmqPoisonMessageRejected</span></span>
<span data-ttu-id="7ab12-103">Mensagem de inviabilização recusada.</span><span class="sxs-lookup"><span data-stu-id="7ab12-103">Poison message rejected.</span></span>  
  
## <a name="description"></a><span data-ttu-id="7ab12-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="7ab12-104">Description</span></span>  
 <span data-ttu-id="7ab12-105">O rastreamento indica que uma mensagem suspeita foi encontrada e subsequentemente rejeitada.</span><span class="sxs-lookup"><span data-stu-id="7ab12-105">The trace indicates that a poison message was encountered and subsequently rejected.</span></span> <span data-ttu-id="7ab12-106">Isso ocorre quando o `ReceiveErrorHandling` no NetMsmqBinding ou MsmqIntegrationBinding estiver definida como `Reject`.</span><span class="sxs-lookup"><span data-stu-id="7ab12-106">This occurs when the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding is set to `Reject`.</span></span> <span data-ttu-id="7ab12-107">Uma mensagem rejeitada é fornecida para o remetente [fila de mensagens mortas](http://go.microsoft.com/fwlink/?LinkId=99544).</span><span class="sxs-lookup"><span data-stu-id="7ab12-107">A rejected message is delivered back to the sender’s [Dead-Letter Queue](http://go.microsoft.com/fwlink/?LinkId=99544).</span></span>  
  
 <span data-ttu-id="7ab12-108">Consulte [manipulação de mensagens suspeitas](http://go.microsoft.com/fwlink/?LinkId=99546) para obter mais detalhes sobre quando as mensagens são suspeitas e como configurar seu serviço para tratar de maneira adequada.</span><span class="sxs-lookup"><span data-stu-id="7ab12-108">See [Poison-Message Handling](http://go.microsoft.com/fwlink/?LinkId=99546) for more details on when messages become poison and how to configure your service to handle them appropriately.</span></span> <span data-ttu-id="7ab12-109">Consulte [MQMarkMessageRejected](http://go.microsoft.com/fwlink/?LinkId=99548) para obter mais detalhes sobre o que significa que uma mensagem rejeitada no MSMQ.</span><span class="sxs-lookup"><span data-stu-id="7ab12-109">See [MQMarkMessageRejected](http://go.microsoft.com/fwlink/?LinkId=99548) for more details on what a rejected message means in MSMQ.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ab12-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7ab12-110">See Also</span></span>  
 [<span data-ttu-id="7ab12-111">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="7ab12-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="7ab12-112">Usando o rastreamento para solucionar problemas do seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="7ab12-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="7ab12-113">Administração e diagnósticos</span><span class="sxs-lookup"><span data-stu-id="7ab12-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)  
 [<span data-ttu-id="7ab12-114">Tratamento de mensagens suspeitas</span><span class="sxs-lookup"><span data-stu-id="7ab12-114">Poison-Message Handling</span></span>](http://go.microsoft.com/fwlink/?LinkId=99546)  
 [<span data-ttu-id="7ab12-115">MQMarkMessageRejected</span><span class="sxs-lookup"><span data-stu-id="7ab12-115">MQMarkMessageRejected</span></span>](http://go.microsoft.com/fwlink/?LinkId=99548)
