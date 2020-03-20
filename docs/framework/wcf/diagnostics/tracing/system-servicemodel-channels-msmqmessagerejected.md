---
title: System.ServiceModel.Channels.MsmqMessageRejected
ms.date: 03/30/2017
ms.assetid: 9b7c10a7-2af6-44a2-8b1a-90bba0c7cf26
ms.openlocfilehash: 8f783dcd4b966ed89c24d724918a3923c5a2d0b1
ms.sourcegitcommit: 515469828d0f040e01bde01df6b8e4eb43630b06
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78674768"
---
# <a name="systemservicemodelchannelsmsmqmessagerejected"></a><span data-ttu-id="fd814-102">System.ServiceModel.Channels.MsmqMessageRejected</span><span class="sxs-lookup"><span data-stu-id="fd814-102">System.ServiceModel.Channels.MsmqMessageRejected</span></span>
<span data-ttu-id="fd814-103">A MSMQ rejeitou a mensagem.</span><span class="sxs-lookup"><span data-stu-id="fd814-103">MSMQ rejected the message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="fd814-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="fd814-104">Description</span></span>  
 <span data-ttu-id="fd814-105">Este rastreamento indica que uma mensagem MSMQ foi rejeitada.</span><span class="sxs-lookup"><span data-stu-id="fd814-105">This trace indicates that an MSMQ message was rejected.</span></span>  
  
 <span data-ttu-id="fd814-106">As mensagens MSMQ podem ser rejeitadas quando o Windows Communication Foundation (WCF) (usado com o NetMsmqBinding ou o MsmqIntegrationBinding) não puder processá-las.</span><span class="sxs-lookup"><span data-stu-id="fd814-106">MSMQ messages can be rejected when Windows Communication Foundation (WCF) (used with either the NetMsmqBinding or MsmqIntegrationBinding) is unable to process them.</span></span> <span data-ttu-id="fd814-107">Essas mensagens são referidas como mensagens venenosas.</span><span class="sxs-lookup"><span data-stu-id="fd814-107">Such messages are referred to as poison messages.</span></span> <span data-ttu-id="fd814-108">Uma mensagem venenosa é `ReceiveErrorHandling` rejeitada quando a propriedade no NetMsmqBinding ou `Reject`MsmqIntegrationBinding é definida como .</span><span class="sxs-lookup"><span data-stu-id="fd814-108">A poison message is rejected when the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding is set to `Reject`.</span></span> <span data-ttu-id="fd814-109">Uma mensagem rejeitada é entregue de volta à fila de [letras mortas](https://docs.microsoft.com/dotnet/framework/wcf/feature-details/using-dead-letter-queues-to-handle-message-transfer-failures)do remetente .</span><span class="sxs-lookup"><span data-stu-id="fd814-109">A rejected message is delivered back to the sender’s [Dead-Letter Queue](https://docs.microsoft.com/dotnet/framework/wcf/feature-details/using-dead-letter-queues-to-handle-message-transfer-failures).</span></span>  
  
 <span data-ttu-id="fd814-110">Para obter mais informações sobre quando as mensagens se tornam venenosas e como configurar seu serviço para manuseá-las adequadamente, consulte [Poison-Message Handling](../../feature-details/poison-message-handling.md).</span><span class="sxs-lookup"><span data-stu-id="fd814-110">For more information on when messages become poison and how to configure your service to handle them appropriately, see [Poison-Message Handling](../../feature-details/poison-message-handling.md).</span></span>  
  
 <span data-ttu-id="fd814-111">Para obter mais informações sobre o que significa uma mensagem rejeitada no MSMQ, consulte [MQMarkMessageReject .](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85))</span><span class="sxs-lookup"><span data-stu-id="fd814-111">For more information on what a rejected message means in MSMQ, see [MQMarkMessageRejected](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd814-112">Confira também</span><span class="sxs-lookup"><span data-stu-id="fd814-112">See also</span></span>

- [<span data-ttu-id="fd814-113">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="fd814-113">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="fd814-114">Utilizando o rastreamento para solucionar problemas em seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="fd814-114">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="fd814-115">Administração e Diagnósticos</span><span class="sxs-lookup"><span data-stu-id="fd814-115">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
- [<span data-ttu-id="fd814-116">Manuseio de mensagens venenosas</span><span class="sxs-lookup"><span data-stu-id="fd814-116">Poison-Message Handling</span></span>](../../feature-details/poison-message-handling.md)
- <span data-ttu-id="fd814-117">[MQMarkMessageRejeitado](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85))</span><span class="sxs-lookup"><span data-stu-id="fd814-117">[MQMarkMessageRejected](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85))</span></span>
