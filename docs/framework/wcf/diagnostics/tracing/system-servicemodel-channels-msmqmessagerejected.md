---
title: System.ServiceModel.Channels.MsmqMessageRejected
ms.date: 03/30/2017
ms.assetid: 9b7c10a7-2af6-44a2-8b1a-90bba0c7cf26
ms.openlocfilehash: e602dd7da2a5652ec10e74fa05c73b75afec2ed4
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90551985"
---
# <a name="systemservicemodelchannelsmsmqmessagerejected"></a><span data-ttu-id="00cce-102">System.ServiceModel.Channels.MsmqMessageRejected</span><span class="sxs-lookup"><span data-stu-id="00cce-102">System.ServiceModel.Channels.MsmqMessageRejected</span></span>
<span data-ttu-id="00cce-103">O MSMQ rejeitou a mensagem.</span><span class="sxs-lookup"><span data-stu-id="00cce-103">MSMQ rejected the message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="00cce-104">Description</span><span class="sxs-lookup"><span data-stu-id="00cce-104">Description</span></span>  
 <span data-ttu-id="00cce-105">Esse rastreamento indica que uma mensagem MSMQ foi rejeitada.</span><span class="sxs-lookup"><span data-stu-id="00cce-105">This trace indicates that an MSMQ message was rejected.</span></span>  
  
 <span data-ttu-id="00cce-106">As mensagens MSMQ podem ser rejeitadas quando Windows Communication Foundation (WCF) (usado com o NetMsmqBinding ou MsmqIntegrationBinding) não puder processá-las.</span><span class="sxs-lookup"><span data-stu-id="00cce-106">MSMQ messages can be rejected when Windows Communication Foundation (WCF) (used with either the NetMsmqBinding or MsmqIntegrationBinding) is unable to process them.</span></span> <span data-ttu-id="00cce-107">Essas mensagens são chamadas de mensagens suspeitas.</span><span class="sxs-lookup"><span data-stu-id="00cce-107">Such messages are referred to as poison messages.</span></span> <span data-ttu-id="00cce-108">Uma mensagem suspeita é rejeitada quando a `ReceiveErrorHandling` propriedade em NetMsmqBinding ou MsmqIntegrationBinding é definida como `Reject` .</span><span class="sxs-lookup"><span data-stu-id="00cce-108">A poison message is rejected when the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding is set to `Reject`.</span></span> <span data-ttu-id="00cce-109">Uma mensagem rejeitada é entregue de volta para a [fila de mensagens mortas](../../feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md)do remetente.</span><span class="sxs-lookup"><span data-stu-id="00cce-109">A rejected message is delivered back to the sender’s [Dead-Letter Queue](../../feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md).</span></span>  
  
 <span data-ttu-id="00cce-110">Para obter mais informações sobre quando as mensagens se tornam suspeitas e como configurar seu serviço para tratá-las adequadamente, consulte [manipulação de mensagens suspeitas](../../feature-details/poison-message-handling.md).</span><span class="sxs-lookup"><span data-stu-id="00cce-110">For more information on when messages become poison and how to configure your service to handle them appropriately, see [Poison-Message Handling](../../feature-details/poison-message-handling.md).</span></span>  
  
 <span data-ttu-id="00cce-111">Para obter mais informações sobre o que uma mensagem rejeitada significa no MSMQ, consulte [MQMarkMessageRejected](/previous-versions/windows/desktop/msmq/ms707071(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="00cce-111">For more information on what a rejected message means in MSMQ, see [MQMarkMessageRejected](/previous-versions/windows/desktop/msmq/ms707071(v=vs.85)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00cce-112">Confira também</span><span class="sxs-lookup"><span data-stu-id="00cce-112">See also</span></span>

- [<span data-ttu-id="00cce-113">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="00cce-113">Tracing</span></span>](index.md)
- [<span data-ttu-id="00cce-114">Utilizando o rastreamento para solucionar problemas em seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="00cce-114">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="00cce-115">Administração e diagnóstico</span><span class="sxs-lookup"><span data-stu-id="00cce-115">Administration and Diagnostics</span></span>](../index.md)
- [<span data-ttu-id="00cce-116">Manipulação de mensagens suspeitas</span><span class="sxs-lookup"><span data-stu-id="00cce-116">Poison-Message Handling</span></span>](../../feature-details/poison-message-handling.md)
- <span data-ttu-id="00cce-117">[MQMarkMessageRejected](/previous-versions/windows/desktop/msmq/ms707071(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="00cce-117">[MQMarkMessageRejected](/previous-versions/windows/desktop/msmq/ms707071(v=vs.85))</span></span>
