---
title: System.ServiceModel.Channels.MsmqMessageDropped
ms.date: 03/30/2017
ms.assetid: 8b6e644d-fa68-4be7-abe9-3659671a37c1
ms.openlocfilehash: e80fecf508158dcb53f08b75c8f9486c13e403a4
ms.sourcegitcommit: 515469828d0f040e01bde01df6b8e4eb43630b06
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78674793"
---
# <a name="systemservicemodelchannelsmsmqmessagedropped"></a><span data-ttu-id="28f1e-102">System.ServiceModel.Channels.MsmqMessageDropped</span><span class="sxs-lookup"><span data-stu-id="28f1e-102">System.ServiceModel.Channels.MsmqMessageDropped</span></span>
<span data-ttu-id="28f1e-103">MSMQ deixou cair a mensagem.</span><span class="sxs-lookup"><span data-stu-id="28f1e-103">MSMQ dropped the message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="28f1e-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="28f1e-104">Description</span></span>  
 <span data-ttu-id="28f1e-105">O rastro indica que uma mensagem MSMQ foi descartada.</span><span class="sxs-lookup"><span data-stu-id="28f1e-105">The trace indicates that an MSMQ message was dropped.</span></span> <span data-ttu-id="28f1e-106">As mensagens MSMQ podem ser descartadas quando o Windows Communication Foundation (WCF) (usado com o NetMsmqBinding ou o MsmqIntegrationBinding) não puder processá-las.</span><span class="sxs-lookup"><span data-stu-id="28f1e-106">MSMQ messages can be dropped when Windows Communication Foundation (WCF) (used with either the NetMsmqBinding or MsmqIntegrationBinding) is unable to process them.</span></span> <span data-ttu-id="28f1e-107">Essas mensagens são referidas como mensagens venenosas.</span><span class="sxs-lookup"><span data-stu-id="28f1e-107">Such messages are referred to as poison messages.</span></span>  
  
 <span data-ttu-id="28f1e-108">Uma mensagem venenosa é `ReceiveErrorHandling` descartada quando a propriedade no NetMsmqBinding ou `Drop`MsmqIntegrationBinding é definida como .</span><span class="sxs-lookup"><span data-stu-id="28f1e-108">A poison message is dropped when the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding is set to `Drop`.</span></span> <span data-ttu-id="28f1e-109">Uma mensagem descartada é removida da fila e não pode mais ser recuperável.</span><span class="sxs-lookup"><span data-stu-id="28f1e-109">A dropped message is removed from the queue and is no longer recoverable.</span></span>  
  
 <span data-ttu-id="28f1e-110">Para obter mais informações sobre quando as mensagens se tornam venenosas e como configurar seu serviço para manuseá-las adequadamente, consulte [Poison-Message Handling](../../feature-details/poison-message-handling.md).</span><span class="sxs-lookup"><span data-stu-id="28f1e-110">For more information on when messages become poison and how to configure your service to handle them appropriately, see [Poison-Message Handling](../../feature-details/poison-message-handling.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28f1e-111">Confira também</span><span class="sxs-lookup"><span data-stu-id="28f1e-111">See also</span></span>

- [<span data-ttu-id="28f1e-112">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="28f1e-112">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="28f1e-113">Utilizando o rastreamento para solucionar problemas em seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="28f1e-113">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="28f1e-114">Administração e Diagnósticos</span><span class="sxs-lookup"><span data-stu-id="28f1e-114">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
- [<span data-ttu-id="28f1e-115">Manuseio de mensagens venenosas</span><span class="sxs-lookup"><span data-stu-id="28f1e-115">Poison-Message Handling</span></span>](../../feature-details/poison-message-handling.md)
