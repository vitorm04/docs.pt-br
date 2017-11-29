---
title: System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d75d39da-7502-4a6a-91b9-eaa05b8e24d5
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4cecacdcc9ec1155fbb374bb763f6858da6ccc57
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="systemservicemodelchannelsmsmqmoveordeleteattemptfailed"></a><span data-ttu-id="285c5-102">System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed</span><span class="sxs-lookup"><span data-stu-id="285c5-102">System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed</span></span>
<span data-ttu-id="285c5-103">Não é possível mover ou excluir a mensagem.</span><span class="sxs-lookup"><span data-stu-id="285c5-103">Cannot move or delete message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="285c5-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="285c5-104">Description</span></span>  
 <span data-ttu-id="285c5-105">O rastreamento indica que ocorreu uma falha ao tentar mover, excluir ou rejeitar uma mensagem MSMQ.</span><span class="sxs-lookup"><span data-stu-id="285c5-105">The trace indicates that a failure occurred when attempting to move, delete, or reject an MSMQ message.</span></span>  
  
 <span data-ttu-id="285c5-106">Mensagens MSMQ são usadas pelo [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] (quando usado com o NetMsmqBinding ou MsmqIntegrationBinding). Este rastreamento está relacionado ao valor escolhido o `ReceiveErrorHandling` propriedade no NetMsmqBinding ou MsmqIntegrationBinding.</span><span class="sxs-lookup"><span data-stu-id="285c5-106">MSMQ messages are employed by [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] (when used with either the NetMsmqBinding or the MsmqIntegrationBinding).This trace is related to the chosen value of the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding.</span></span>  
  
 <span data-ttu-id="285c5-107">Este rastreamento não é uma indicação de uma falha geral no sistema.</span><span class="sxs-lookup"><span data-stu-id="285c5-107">This trace is not indicative of an overall system failure.</span></span> <span data-ttu-id="285c5-108">No entanto, ele indica escolhido suspeitas disposição de mensagem falhou para uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="285c5-108">However, it indicates that the chosen poison message disposition failed for a message.</span></span> <span data-ttu-id="285c5-109">Consulte [manipulação de mensagens suspeitas](http://go.microsoft.com/fwlink/?LinkID=99546) para obter mais detalhes sobre quando as mensagens são suspeitas e como configurar seu serviço para tratar de maneira adequada.</span><span class="sxs-lookup"><span data-stu-id="285c5-109">See [Poison-Message Handling](http://go.microsoft.com/fwlink/?LinkID=99546) for more details on when messages become poison and how to configure your service to handle them appropriately.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="285c5-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="285c5-110">See Also</span></span>  
 [<span data-ttu-id="285c5-111">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="285c5-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="285c5-112">Usando o rastreamento para solucionar problemas de seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="285c5-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 <span data-ttu-id="285c5-113">[Administration and Diagnostics](../../../../../docs/framework/wcf/diagnostics/index.md) (Administração e diagnósticos)</span><span class="sxs-lookup"><span data-stu-id="285c5-113">[Administration and Diagnostics](../../../../../docs/framework/wcf/diagnostics/index.md)</span></span>
