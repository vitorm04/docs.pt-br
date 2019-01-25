---
title: System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed
ms.date: 03/30/2017
ms.assetid: d75d39da-7502-4a6a-91b9-eaa05b8e24d5
ms.openlocfilehash: ade49ceb86a401cd27a9381b1ea5d0c1ad624548
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54623086"
---
# <a name="systemservicemodelchannelsmsmqmoveordeleteattemptfailed"></a><span data-ttu-id="0e36d-102">System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed</span><span class="sxs-lookup"><span data-stu-id="0e36d-102">System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed</span></span>
<span data-ttu-id="0e36d-103">Não é possível mover ou excluir a mensagem.</span><span class="sxs-lookup"><span data-stu-id="0e36d-103">Cannot move or delete message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="0e36d-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="0e36d-104">Description</span></span>  
 <span data-ttu-id="0e36d-105">O rastreamento indica que ocorreu uma falha ao tentar mover, excluir ou rejeitar uma mensagem MSMQ.</span><span class="sxs-lookup"><span data-stu-id="0e36d-105">The trace indicates that a failure occurred when attempting to move, delete, or reject an MSMQ message.</span></span>  
  
 <span data-ttu-id="0e36d-106">Mensagens MSMQ são utilizadas pelo Windows Communication Foundation (WCF) (quando usado com o NetMsmqBinding ou o MsmqIntegrationBinding). Este rastreamento está relacionado ao valor escolhido o `ReceiveErrorHandling` propriedade no NetMsmqBinding ou MsmqIntegrationBinding.</span><span class="sxs-lookup"><span data-stu-id="0e36d-106">MSMQ messages are employed by Windows Communication Foundation (WCF) (when used with either the NetMsmqBinding or the MsmqIntegrationBinding).This trace is related to the chosen value of the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding.</span></span>  
  
 <span data-ttu-id="0e36d-107">Esse rastreamento não é uma indicação de uma falha geral no sistema.</span><span class="sxs-lookup"><span data-stu-id="0e36d-107">This trace is not indicative of an overall system failure.</span></span> <span data-ttu-id="0e36d-108">No entanto, ele indica que o escolhido suspeitas falhou para uma mensagem de disposição de mensagem.</span><span class="sxs-lookup"><span data-stu-id="0e36d-108">However, it indicates that the chosen poison message disposition failed for a message.</span></span> <span data-ttu-id="0e36d-109">Ver [tratamento de mensagens suspeitas](https://go.microsoft.com/fwlink/?LinkID=99546) para obter mais detalhes sobre quando as mensagens se tornarão suspeitas e como configurar seu serviço para tratá-las adequadamente.</span><span class="sxs-lookup"><span data-stu-id="0e36d-109">See [Poison-Message Handling](https://go.microsoft.com/fwlink/?LinkID=99546) for more details on when messages become poison and how to configure your service to handle them appropriately.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e36d-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0e36d-110">See also</span></span>
- [<span data-ttu-id="0e36d-111">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="0e36d-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="0e36d-112">Usando o rastreamento para solucionar problemas do seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="0e36d-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="0e36d-113">Administração e diagnósticos</span><span class="sxs-lookup"><span data-stu-id="0e36d-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
