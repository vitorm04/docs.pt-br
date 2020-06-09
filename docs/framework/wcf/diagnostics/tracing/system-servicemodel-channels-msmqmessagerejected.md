---
title: System.ServiceModel.Channels.MsmqMessageRejected
ms.date: 03/30/2017
ms.assetid: 9b7c10a7-2af6-44a2-8b1a-90bba0c7cf26
ms.openlocfilehash: c388a9dc3569e20639de09abc5f4941b73c561ad
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84578045"
---
# <a name="systemservicemodelchannelsmsmqmessagerejected"></a><span data-ttu-id="489e5-102">System.ServiceModel.Channels.MsmqMessageRejected</span><span class="sxs-lookup"><span data-stu-id="489e5-102">System.ServiceModel.Channels.MsmqMessageRejected</span></span>
<span data-ttu-id="489e5-103">O MSMQ rejeitou a mensagem.</span><span class="sxs-lookup"><span data-stu-id="489e5-103">MSMQ rejected the message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="489e5-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="489e5-104">Description</span></span>  
 <span data-ttu-id="489e5-105">Esse rastreamento indica que uma mensagem MSMQ foi rejeitada.</span><span class="sxs-lookup"><span data-stu-id="489e5-105">This trace indicates that an MSMQ message was rejected.</span></span>  
  
 <span data-ttu-id="489e5-106">As mensagens MSMQ podem ser rejeitadas quando Windows Communication Foundation (WCF) (usado com o NetMsmqBinding ou MsmqIntegrationBinding) não puder processá-las.</span><span class="sxs-lookup"><span data-stu-id="489e5-106">MSMQ messages can be rejected when Windows Communication Foundation (WCF) (used with either the NetMsmqBinding or MsmqIntegrationBinding) is unable to process them.</span></span> <span data-ttu-id="489e5-107">Essas mensagens são chamadas de mensagens suspeitas.</span><span class="sxs-lookup"><span data-stu-id="489e5-107">Such messages are referred to as poison messages.</span></span> <span data-ttu-id="489e5-108">Uma mensagem suspeita é rejeitada quando a `ReceiveErrorHandling` propriedade em NetMsmqBinding ou MsmqIntegrationBinding é definida como `Reject` .</span><span class="sxs-lookup"><span data-stu-id="489e5-108">A poison message is rejected when the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding is set to `Reject`.</span></span> <span data-ttu-id="489e5-109">Uma mensagem rejeitada é entregue de volta para a [fila de mensagens mortas](https://docs.microsoft.com/dotnet/framework/wcf/feature-details/using-dead-letter-queues-to-handle-message-transfer-failures)do remetente.</span><span class="sxs-lookup"><span data-stu-id="489e5-109">A rejected message is delivered back to the sender’s [Dead-Letter Queue](https://docs.microsoft.com/dotnet/framework/wcf/feature-details/using-dead-letter-queues-to-handle-message-transfer-failures).</span></span>  
  
 <span data-ttu-id="489e5-110">Para obter mais informações sobre quando as mensagens se tornam suspeitas e como configurar seu serviço para tratá-las adequadamente, consulte [manipulação de mensagens suspeitas](../../feature-details/poison-message-handling.md).</span><span class="sxs-lookup"><span data-stu-id="489e5-110">For more information on when messages become poison and how to configure your service to handle them appropriately, see [Poison-Message Handling](../../feature-details/poison-message-handling.md).</span></span>  
  
 <span data-ttu-id="489e5-111">Para obter mais informações sobre o que uma mensagem rejeitada significa no MSMQ, consulte [MQMarkMessageRejected](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85)).</span><span class="sxs-lookup"><span data-stu-id="489e5-111">For more information on what a rejected message means in MSMQ, see [MQMarkMessageRejected](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="489e5-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="489e5-112">See also</span></span>

- [<span data-ttu-id="489e5-113">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="489e5-113">Tracing</span></span>](index.md)
- [<span data-ttu-id="489e5-114">Utilizando o rastreamento para solucionar problemas em seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="489e5-114">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="489e5-115">Administração e diagnóstico</span><span class="sxs-lookup"><span data-stu-id="489e5-115">Administration and Diagnostics</span></span>](../index.md)
- [<span data-ttu-id="489e5-116">Manipulação de mensagens suspeitas</span><span class="sxs-lookup"><span data-stu-id="489e5-116">Poison-Message Handling</span></span>](../../feature-details/poison-message-handling.md)
- <span data-ttu-id="489e5-117">[MQMarkMessageRejected](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85))</span><span class="sxs-lookup"><span data-stu-id="489e5-117">[MQMarkMessageRejected](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85))</span></span>
