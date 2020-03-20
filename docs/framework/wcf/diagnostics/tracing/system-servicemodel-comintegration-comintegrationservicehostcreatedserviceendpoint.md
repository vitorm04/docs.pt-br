---
title: System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed
ms.date: 03/30/2017
ms.assetid: d75d39da-7502-4a6a-91b9-eaa05b8e24d5
ms.openlocfilehash: f89dd1373d67714046f8cb958582c3a5dea04456
ms.sourcegitcommit: 515469828d0f040e01bde01df6b8e4eb43630b06
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78674784"
---
# <a name="systemservicemodelchannelsmsmqmoveordeleteattemptfailed"></a><span data-ttu-id="b3251-102">System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed</span><span class="sxs-lookup"><span data-stu-id="b3251-102">System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed</span></span>
<span data-ttu-id="b3251-103">Não é possível mover ou excluir mensagem.</span><span class="sxs-lookup"><span data-stu-id="b3251-103">Cannot move or delete message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="b3251-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="b3251-104">Description</span></span>  
 <span data-ttu-id="b3251-105">O rastreamento indica que ocorreu uma falha ao tentar mover, excluir ou rejeitar uma mensagem MSMQ.</span><span class="sxs-lookup"><span data-stu-id="b3251-105">The trace indicates that a failure occurred when attempting to move, delete, or reject an MSMQ message.</span></span>  
  
 <span data-ttu-id="b3251-106">As mensagens MSMQ são empregadas pela Windows Communication Foundation (WCF) (quando usadas com o NetMsmqBinding ou o MsmqIntegrationBinding). Este traço está relacionado com `ReceiveErrorHandling` o valor escolhido da propriedade no NetMsmqBinding ou MsmqIntegrationBinding.</span><span class="sxs-lookup"><span data-stu-id="b3251-106">MSMQ messages are employed by Windows Communication Foundation (WCF) (when used with either the NetMsmqBinding or the MsmqIntegrationBinding).This trace is related to the chosen value of the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding.</span></span>  
  
 <span data-ttu-id="b3251-107">Este traço não indica uma falha geral do sistema.</span><span class="sxs-lookup"><span data-stu-id="b3251-107">This trace is not indicative of an overall system failure.</span></span> <span data-ttu-id="b3251-108">No entanto, indica que a disposição da mensagem venenosa escolhida falhou para uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="b3251-108">However, it indicates that the chosen poison message disposition failed for a message.</span></span> <span data-ttu-id="b3251-109">Para obter mais informações sobre quando as mensagens se tornam venenosas e como configurar seu serviço para manuseá-las adequadamente, consulte [Poison-Message Handling](../../feature-details/poison-message-handling.md).</span><span class="sxs-lookup"><span data-stu-id="b3251-109">For more information on when messages become poison and how to configure your service to handle them appropriately, see [Poison-Message Handling](../../feature-details/poison-message-handling.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3251-110">Confira também</span><span class="sxs-lookup"><span data-stu-id="b3251-110">See also</span></span>

- [<span data-ttu-id="b3251-111">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="b3251-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="b3251-112">Utilizando o rastreamento para solucionar problemas em seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="b3251-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="b3251-113">Administração e Diagnósticos</span><span class="sxs-lookup"><span data-stu-id="b3251-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
