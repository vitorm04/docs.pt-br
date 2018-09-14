---
title: System.ServiceModel.Channels.MsmqMessageRejected
ms.date: 03/30/2017
ms.assetid: 9b7c10a7-2af6-44a2-8b1a-90bba0c7cf26
ms.openlocfilehash: 0addf987eac62c750a3c418e1b1c431d3f9bc1b0
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45533445"
---
# <a name="systemservicemodelchannelsmsmqmessagerejected"></a><span data-ttu-id="ef78f-102">System.ServiceModel.Channels.MsmqMessageRejected</span><span class="sxs-lookup"><span data-stu-id="ef78f-102">System.ServiceModel.Channels.MsmqMessageRejected</span></span>
<span data-ttu-id="ef78f-103">MSMQ rejeitadas a mensagem.</span><span class="sxs-lookup"><span data-stu-id="ef78f-103">MSMQ rejected the message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="ef78f-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="ef78f-104">Description</span></span>  
 <span data-ttu-id="ef78f-105">Este rastreamento indica que uma mensagem MSMQ foi rejeitada.</span><span class="sxs-lookup"><span data-stu-id="ef78f-105">This trace indicates that an MSMQ message was rejected.</span></span>  
  
 <span data-ttu-id="ef78f-106">Mensagens do MSMQ podem ser rejeitadas quando o Windows Communication Foundation (WCF) (usado com o NetMsmqBinding ou MsmqIntegrationBinding) não pode processá-los.</span><span class="sxs-lookup"><span data-stu-id="ef78f-106">MSMQ messages can be rejected when Windows Communication Foundation (WCF) (used with either the NetMsmqBinding or MsmqIntegrationBinding) is unable to process them.</span></span> <span data-ttu-id="ef78f-107">Essas mensagens são denominadas mensagens suspeitas.</span><span class="sxs-lookup"><span data-stu-id="ef78f-107">Such messages are referred to as poison messages.</span></span> <span data-ttu-id="ef78f-108">Uma mensagem suspeita é rejeitada quando o `ReceiveErrorHandling` sobre o NetMsmqBinding ou MsmqIntegrationBinding estiver definida como `Reject`.</span><span class="sxs-lookup"><span data-stu-id="ef78f-108">A poison message is rejected when the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding is set to `Reject`.</span></span> <span data-ttu-id="ef78f-109">Uma mensagem rejeitada é entregue para o remetente [fila de inatividade](https://go.microsoft.com/fwlink/?LinkID=99544).</span><span class="sxs-lookup"><span data-stu-id="ef78f-109">A rejected message is delivered back to the sender’s [Dead-Letter Queue](https://go.microsoft.com/fwlink/?LinkID=99544).</span></span>  
  
 <span data-ttu-id="ef78f-110">Ver [tratamento de mensagens suspeitas](https://go.microsoft.com/fwlink/?LinkID=99546) para obter mais detalhes sobre quando as mensagens se tornarão suspeitas e como configurar seu serviço para tratá-las adequadamente.</span><span class="sxs-lookup"><span data-stu-id="ef78f-110">See [Poison-Message Handling](https://go.microsoft.com/fwlink/?LinkID=99546) for more details on when messages become poison and how to configure your service to handle them appropriately.</span></span>  
  
 <span data-ttu-id="ef78f-111">Ver [MQMarkMessageRejected](https://go.microsoft.com/fwlink/?LinkID=99548) para obter mais detalhes sobre o que significa que uma mensagem rejeitada no MSMQ.</span><span class="sxs-lookup"><span data-stu-id="ef78f-111">See [MQMarkMessageRejected](https://go.microsoft.com/fwlink/?LinkID=99548) for more details on what a rejected message means in MSMQ.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef78f-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ef78f-112">See Also</span></span>  
 [<span data-ttu-id="ef78f-113">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="ef78f-113">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="ef78f-114">Usando o rastreamento para solucionar problemas do seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="ef78f-114">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="ef78f-115">Administração e diagnósticos</span><span class="sxs-lookup"><span data-stu-id="ef78f-115">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)  
 [<span data-ttu-id="ef78f-116">Manipulação de mensagens suspeitas</span><span class="sxs-lookup"><span data-stu-id="ef78f-116">Poison-Message Handling</span></span>](https://go.microsoft.com/fwlink/?LinkID=99546)  
 [<span data-ttu-id="ef78f-117">MQMarkMessageRejected</span><span class="sxs-lookup"><span data-stu-id="ef78f-117">MQMarkMessageRejected</span></span>](https://go.microsoft.com/fwlink/?LinkID=99548)
