---
title: System.ServiceModel.Channels.MsmqPoisonMessageRejected
ms.date: 03/30/2017
ms.assetid: 0e64b9bd-1f12-43df-a189-d7be3c2bace1
ms.openlocfilehash: 27402017e5e79194578719fd0c921dfc1e047b80
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43407911"
---
# <a name="systemservicemodelchannelsmsmqpoisonmessagerejected"></a><span data-ttu-id="4b8b9-102">System.ServiceModel.Channels.MsmqPoisonMessageRejected</span><span class="sxs-lookup"><span data-stu-id="4b8b9-102">System.ServiceModel.Channels.MsmqPoisonMessageRejected</span></span>
<span data-ttu-id="4b8b9-103">Nezpracovatelná zpráva byla odmítnuta.</span><span class="sxs-lookup"><span data-stu-id="4b8b9-103">Poison message rejected.</span></span>  
  
## <a name="description"></a><span data-ttu-id="4b8b9-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="4b8b9-104">Description</span></span>  
 <span data-ttu-id="4b8b9-105">O rastreamento indica que uma mensagem suspeita foi encontrada e, subsequentemente, foi rejeitada.</span><span class="sxs-lookup"><span data-stu-id="4b8b9-105">The trace indicates that a poison message was encountered and subsequently rejected.</span></span> <span data-ttu-id="4b8b9-106">Isso ocorre quando o `ReceiveErrorHandling` sobre o NetMsmqBinding ou MsmqIntegrationBinding estiver definida como `Reject`.</span><span class="sxs-lookup"><span data-stu-id="4b8b9-106">This occurs when the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding is set to `Reject`.</span></span> <span data-ttu-id="4b8b9-107">Uma mensagem rejeitada é entregue para o remetente [fila de inatividade](https://go.microsoft.com/fwlink/?LinkId=99544).</span><span class="sxs-lookup"><span data-stu-id="4b8b9-107">A rejected message is delivered back to the sender’s [Dead-Letter Queue](https://go.microsoft.com/fwlink/?LinkId=99544).</span></span>  
  
 <span data-ttu-id="4b8b9-108">Ver [tratamento de mensagens suspeitas](https://go.microsoft.com/fwlink/?LinkId=99546) para obter mais detalhes sobre quando as mensagens se tornarão suspeitas e como configurar seu serviço para tratá-las adequadamente.</span><span class="sxs-lookup"><span data-stu-id="4b8b9-108">See [Poison-Message Handling](https://go.microsoft.com/fwlink/?LinkId=99546) for more details on when messages become poison and how to configure your service to handle them appropriately.</span></span> <span data-ttu-id="4b8b9-109">Ver [MQMarkMessageRejected](https://go.microsoft.com/fwlink/?LinkId=99548) para obter mais detalhes sobre o que significa que uma mensagem rejeitada no MSMQ.</span><span class="sxs-lookup"><span data-stu-id="4b8b9-109">See [MQMarkMessageRejected](https://go.microsoft.com/fwlink/?LinkId=99548) for more details on what a rejected message means in MSMQ.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b8b9-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4b8b9-110">See Also</span></span>  
 [<span data-ttu-id="4b8b9-111">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="4b8b9-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="4b8b9-112">Usando o rastreamento para solucionar problemas do seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="4b8b9-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="4b8b9-113">Administração e diagnósticos</span><span class="sxs-lookup"><span data-stu-id="4b8b9-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)  
 [<span data-ttu-id="4b8b9-114">Manipulação de mensagens suspeitas</span><span class="sxs-lookup"><span data-stu-id="4b8b9-114">Poison-Message Handling</span></span>](https://go.microsoft.com/fwlink/?LinkId=99546)  
 [<span data-ttu-id="4b8b9-115">MQMarkMessageRejected</span><span class="sxs-lookup"><span data-stu-id="4b8b9-115">MQMarkMessageRejected</span></span>](https://go.microsoft.com/fwlink/?LinkId=99548)
