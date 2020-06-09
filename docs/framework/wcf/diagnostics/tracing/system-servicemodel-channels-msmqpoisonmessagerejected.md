---
title: System.ServiceModel.Channels.MsmqPoisonMessageRejected
ms.date: 03/30/2017
ms.assetid: 0e64b9bd-1f12-43df-a189-d7be3c2bace1
ms.openlocfilehash: f0e49fcfa13bb9932a88a4e79d617343c080bb3c
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598366"
---
# <a name="systemservicemodelchannelsmsmqpoisonmessagerejected"></a><span data-ttu-id="59092-102">System.ServiceModel.Channels.MsmqPoisonMessageRejected</span><span class="sxs-lookup"><span data-stu-id="59092-102">System.ServiceModel.Channels.MsmqPoisonMessageRejected</span></span>
<span data-ttu-id="59092-103">Mensagem suspeita rejeitada.</span><span class="sxs-lookup"><span data-stu-id="59092-103">Poison message rejected.</span></span>  
  
## <a name="description"></a><span data-ttu-id="59092-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="59092-104">Description</span></span>  

 <span data-ttu-id="59092-105">O rastreamento indica que uma mensagem suspeita foi encontrada e subsequentemente rejeitada.</span><span class="sxs-lookup"><span data-stu-id="59092-105">The trace indicates that a poison message was encountered and subsequently rejected.</span></span> <span data-ttu-id="59092-106">Isso ocorre quando a `ReceiveErrorHandling` propriedade em NetMsmqBinding ou MsmqIntegrationBinding é definida como `Reject` .</span><span class="sxs-lookup"><span data-stu-id="59092-106">This occurs when the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding is set to `Reject`.</span></span> <span data-ttu-id="59092-107">Uma mensagem rejeitada é entregue de volta para a [fila de mensagens mortas](../../feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md)do remetente.</span><span class="sxs-lookup"><span data-stu-id="59092-107">A rejected message is delivered back to the sender’s [Dead-Letter Queue](../../feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md).</span></span>  
  
 <span data-ttu-id="59092-108">Para obter mais informações sobre quando as mensagens se tornam suspeitas e como configurar seu serviço para tratá-las adequadamente, consulte [manipulação de mensagens suspeitas](../../feature-details/poison-message-handling.md).</span><span class="sxs-lookup"><span data-stu-id="59092-108">For more information on when messages become poison and how to configure your service to handle them appropriately, see [Poison-Message Handling](../../feature-details/poison-message-handling.md).</span></span> <span data-ttu-id="59092-109">Para obter mais informações sobre o que uma mensagem rejeitada significa no MSMQ, consulte [MQMarkMessageRejected](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85)).</span><span class="sxs-lookup"><span data-stu-id="59092-109">For more information on what a rejected message means in MSMQ, see [MQMarkMessageRejected](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59092-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="59092-110">See also</span></span>

- [<span data-ttu-id="59092-111">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="59092-111">Tracing</span></span>](index.md)
- [<span data-ttu-id="59092-112">Utilizando o rastreamento para solucionar problemas em seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="59092-112">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="59092-113">Administração e diagnóstico</span><span class="sxs-lookup"><span data-stu-id="59092-113">Administration and Diagnostics</span></span>](../index.md)
- [<span data-ttu-id="59092-114">Manipulação de mensagens suspeitas</span><span class="sxs-lookup"><span data-stu-id="59092-114">Poison-Message Handling</span></span>](../../feature-details/poison-message-handling.md)
- <span data-ttu-id="59092-115">[MQMarkMessageRejected](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85))</span><span class="sxs-lookup"><span data-stu-id="59092-115">[MQMarkMessageRejected](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85))</span></span>
