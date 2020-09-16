---
title: System.ServiceModel.Channels.MsmqPoisonMessageRejected
ms.date: 03/30/2017
ms.assetid: 0e64b9bd-1f12-43df-a189-d7be3c2bace1
ms.openlocfilehash: c5401bae1d8e7f61939d8de321353f59f412f966
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90535327"
---
# <a name="systemservicemodelchannelsmsmqpoisonmessagerejected"></a><span data-ttu-id="58446-102">System.ServiceModel.Channels.MsmqPoisonMessageRejected</span><span class="sxs-lookup"><span data-stu-id="58446-102">System.ServiceModel.Channels.MsmqPoisonMessageRejected</span></span>
<span data-ttu-id="58446-103">Mensagem suspeita rejeitada.</span><span class="sxs-lookup"><span data-stu-id="58446-103">Poison message rejected.</span></span>  
  
## <a name="description"></a><span data-ttu-id="58446-104">Description</span><span class="sxs-lookup"><span data-stu-id="58446-104">Description</span></span>  

 <span data-ttu-id="58446-105">O rastreamento indica que uma mensagem suspeita foi encontrada e subsequentemente rejeitada.</span><span class="sxs-lookup"><span data-stu-id="58446-105">The trace indicates that a poison message was encountered and subsequently rejected.</span></span> <span data-ttu-id="58446-106">Isso ocorre quando a `ReceiveErrorHandling` propriedade em NetMsmqBinding ou MsmqIntegrationBinding é definida como `Reject` .</span><span class="sxs-lookup"><span data-stu-id="58446-106">This occurs when the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding is set to `Reject`.</span></span> <span data-ttu-id="58446-107">Uma mensagem rejeitada é entregue de volta para a [fila de mensagens mortas](../../feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md)do remetente.</span><span class="sxs-lookup"><span data-stu-id="58446-107">A rejected message is delivered back to the sender’s [Dead-Letter Queue](../../feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md).</span></span>  
  
 <span data-ttu-id="58446-108">Para obter mais informações sobre quando as mensagens se tornam suspeitas e como configurar seu serviço para tratá-las adequadamente, consulte [manipulação de mensagens suspeitas](../../feature-details/poison-message-handling.md).</span><span class="sxs-lookup"><span data-stu-id="58446-108">For more information on when messages become poison and how to configure your service to handle them appropriately, see [Poison-Message Handling](../../feature-details/poison-message-handling.md).</span></span> <span data-ttu-id="58446-109">Para obter mais informações sobre o que uma mensagem rejeitada significa no MSMQ, consulte [MQMarkMessageRejected](/previous-versions/windows/desktop/msmq/ms707071(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="58446-109">For more information on what a rejected message means in MSMQ, see [MQMarkMessageRejected](/previous-versions/windows/desktop/msmq/ms707071(v=vs.85)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58446-110">Confira também</span><span class="sxs-lookup"><span data-stu-id="58446-110">See also</span></span>

- [<span data-ttu-id="58446-111">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="58446-111">Tracing</span></span>](index.md)
- [<span data-ttu-id="58446-112">Utilizando o rastreamento para solucionar problemas em seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="58446-112">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="58446-113">Administração e diagnóstico</span><span class="sxs-lookup"><span data-stu-id="58446-113">Administration and Diagnostics</span></span>](../index.md)
- [<span data-ttu-id="58446-114">Manipulação de mensagens suspeitas</span><span class="sxs-lookup"><span data-stu-id="58446-114">Poison-Message Handling</span></span>](../../feature-details/poison-message-handling.md)
- <span data-ttu-id="58446-115">[MQMarkMessageRejected](/previous-versions/windows/desktop/msmq/ms707071(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="58446-115">[MQMarkMessageRejected](/previous-versions/windows/desktop/msmq/ms707071(v=vs.85))</span></span>
