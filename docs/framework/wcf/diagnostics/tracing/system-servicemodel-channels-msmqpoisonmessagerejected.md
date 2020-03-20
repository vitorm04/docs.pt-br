---
title: System.ServiceModel.Channels.MsmqPoisonMessageRejected
ms.date: 03/30/2017
ms.assetid: 0e64b9bd-1f12-43df-a189-d7be3c2bace1
ms.openlocfilehash: 6b0e6e3ebcf5d414e9dbbcecd09ba2e8bb3ddd3a
ms.sourcegitcommit: 515469828d0f040e01bde01df6b8e4eb43630b06
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78674811"
---
# <a name="systemservicemodelchannelsmsmqpoisonmessagerejected"></a><span data-ttu-id="be579-102">System.ServiceModel.Channels.MsmqPoisonMessageRejected</span><span class="sxs-lookup"><span data-stu-id="be579-102">System.ServiceModel.Channels.MsmqPoisonMessageRejected</span></span>
<span data-ttu-id="be579-103">Mensagem venenosa rejeitada.</span><span class="sxs-lookup"><span data-stu-id="be579-103">Poison message rejected.</span></span>  
  
## <a name="description"></a><span data-ttu-id="be579-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="be579-104">Description</span></span>  

 <span data-ttu-id="be579-105">O rastro indica que uma mensagem venenosa foi encontrada e posteriormente rejeitada.</span><span class="sxs-lookup"><span data-stu-id="be579-105">The trace indicates that a poison message was encountered and subsequently rejected.</span></span> <span data-ttu-id="be579-106">Isso ocorre `ReceiveErrorHandling` quando a propriedade no NetMsmqBinding ou MsmqIntegrationBinding é definida como `Reject`.</span><span class="sxs-lookup"><span data-stu-id="be579-106">This occurs when the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding is set to `Reject`.</span></span> <span data-ttu-id="be579-107">Uma mensagem rejeitada é entregue de volta à fila de [letras mortas](../../feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md)do remetente .</span><span class="sxs-lookup"><span data-stu-id="be579-107">A rejected message is delivered back to the sender’s [Dead-Letter Queue](../../feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md).</span></span>  
  
 <span data-ttu-id="be579-108">Para obter mais informações sobre quando as mensagens se tornam venenosas e como configurar seu serviço para manuseá-las adequadamente, consulte [Poison-Message Handling](../../feature-details/poison-message-handling.md).</span><span class="sxs-lookup"><span data-stu-id="be579-108">For more information on when messages become poison and how to configure your service to handle them appropriately, see [Poison-Message Handling](../../feature-details/poison-message-handling.md).</span></span> <span data-ttu-id="be579-109">Para obter mais informações sobre o que significa uma mensagem rejeitada no MSMQ, consulte [MQMarkMessageReject .](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85))</span><span class="sxs-lookup"><span data-stu-id="be579-109">For more information on what a rejected message means in MSMQ, see [MQMarkMessageRejected](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be579-110">Confira também</span><span class="sxs-lookup"><span data-stu-id="be579-110">See also</span></span>

- [<span data-ttu-id="be579-111">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="be579-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="be579-112">Utilizando o rastreamento para solucionar problemas em seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="be579-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="be579-113">Administração e Diagnósticos</span><span class="sxs-lookup"><span data-stu-id="be579-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
- [<span data-ttu-id="be579-114">Manuseio de mensagens venenosas</span><span class="sxs-lookup"><span data-stu-id="be579-114">Poison-Message Handling</span></span>](../../feature-details/poison-message-handling.md)
- <span data-ttu-id="be579-115">[MQMarkMessageRejeitado](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85))</span><span class="sxs-lookup"><span data-stu-id="be579-115">[MQMarkMessageRejected](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85))</span></span>
