---
title: System.ServiceModel.Channels.MsmqMessageRejected
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9b7c10a7-2af6-44a2-8b1a-90bba0c7cf26
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ecbbd8bc0e798388f994432ea2d3f25396f7de97
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="systemservicemodelchannelsmsmqmessagerejected"></a><span data-ttu-id="47660-102">System.ServiceModel.Channels.MsmqMessageRejected</span><span class="sxs-lookup"><span data-stu-id="47660-102">System.ServiceModel.Channels.MsmqMessageRejected</span></span>
<span data-ttu-id="47660-103">MSMQ rejeitou a mensagem.</span><span class="sxs-lookup"><span data-stu-id="47660-103">MSMQ rejected the message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="47660-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="47660-104">Description</span></span>  
 <span data-ttu-id="47660-105">Este rastreamento indica que uma mensagem MSMQ foi rejeitada.</span><span class="sxs-lookup"><span data-stu-id="47660-105">This trace indicates that an MSMQ message was rejected.</span></span>  
  
 <span data-ttu-id="47660-106">As mensagens MSMQ podem ser rejeitada quando [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] (usado com o NetMsmqBinding ou MsmqIntegrationBinding) não pode processá-los.</span><span class="sxs-lookup"><span data-stu-id="47660-106">MSMQ messages can be rejected when [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] (used with either the NetMsmqBinding or MsmqIntegrationBinding) is unable to process them.</span></span> <span data-ttu-id="47660-107">Essas mensagens são denominadas mensagens suspeitas.</span><span class="sxs-lookup"><span data-stu-id="47660-107">Such messages are referred to as poison messages.</span></span> <span data-ttu-id="47660-108">Uma mensagem suspeita é rejeitada quando o `ReceiveErrorHandling` no NetMsmqBinding ou MsmqIntegrationBinding estiver definida como `Reject`.</span><span class="sxs-lookup"><span data-stu-id="47660-108">A poison message is rejected when the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding is set to `Reject`.</span></span> <span data-ttu-id="47660-109">Uma mensagem rejeitada é fornecida para o remetente [fila de mensagens mortas](http://go.microsoft.com/fwlink/?LinkID=99544).</span><span class="sxs-lookup"><span data-stu-id="47660-109">A rejected message is delivered back to the sender’s [Dead-Letter Queue](http://go.microsoft.com/fwlink/?LinkID=99544).</span></span>  
  
 <span data-ttu-id="47660-110">Consulte [manipulação de mensagens suspeitas](http://go.microsoft.com/fwlink/?LinkID=99546) para obter mais detalhes sobre quando as mensagens são suspeitas e como configurar seu serviço para tratar de maneira adequada.</span><span class="sxs-lookup"><span data-stu-id="47660-110">See [Poison-Message Handling](http://go.microsoft.com/fwlink/?LinkID=99546) for more details on when messages become poison and how to configure your service to handle them appropriately.</span></span>  
  
 <span data-ttu-id="47660-111">Consulte [MQMarkMessageRejected](http://go.microsoft.com/fwlink/?LinkID=99548) para obter mais detalhes sobre o que significa que uma mensagem rejeitada no MSMQ.</span><span class="sxs-lookup"><span data-stu-id="47660-111">See [MQMarkMessageRejected](http://go.microsoft.com/fwlink/?LinkID=99548) for more details on what a rejected message means in MSMQ.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47660-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="47660-112">See Also</span></span>  
 [<span data-ttu-id="47660-113">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="47660-113">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="47660-114">Usando o rastreamento para solucionar problemas de seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="47660-114">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 <span data-ttu-id="47660-115">[Administration and Diagnostics](../../../../../docs/framework/wcf/diagnostics/index.md) (Administração e diagnósticos)</span><span class="sxs-lookup"><span data-stu-id="47660-115">[Administration and Diagnostics](../../../../../docs/framework/wcf/diagnostics/index.md)</span></span>  
 [<span data-ttu-id="47660-116">Tratamento de mensagens suspeitas</span><span class="sxs-lookup"><span data-stu-id="47660-116">Poison-Message Handling</span></span>](http://go.microsoft.com/fwlink/?LinkID=99546)  
 [<span data-ttu-id="47660-117">MQMarkMessageRejected</span><span class="sxs-lookup"><span data-stu-id="47660-117">MQMarkMessageRejected</span></span>](http://go.microsoft.com/fwlink/?LinkID=99548)
