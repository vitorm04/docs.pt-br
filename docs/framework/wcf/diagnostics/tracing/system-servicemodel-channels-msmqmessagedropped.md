---
title: System.ServiceModel.Channels.MsmqMessageDropped
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8b6e644d-fa68-4be7-abe9-3659671a37c1
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f2f905c345db89e909920334a7dbb524095bc46b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="systemservicemodelchannelsmsmqmessagedropped"></a><span data-ttu-id="dd782-102">System.ServiceModel.Channels.MsmqMessageDropped</span><span class="sxs-lookup"><span data-stu-id="dd782-102">System.ServiceModel.Channels.MsmqMessageDropped</span></span>
<span data-ttu-id="dd782-103">A mensagem foi descartada MSMQ.</span><span class="sxs-lookup"><span data-stu-id="dd782-103">MSMQ dropped the message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="dd782-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="dd782-104">Description</span></span>  
 <span data-ttu-id="dd782-105">O rastreamento indica que uma mensagem MSMQ foi descartada.</span><span class="sxs-lookup"><span data-stu-id="dd782-105">The trace indicates that an MSMQ message was dropped.</span></span> <span data-ttu-id="dd782-106">Mensagens MSMQ podem ser descartadas quando [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] (usado com o NetMsmqBinding ou MsmqIntegrationBinding) não pode processá-los.</span><span class="sxs-lookup"><span data-stu-id="dd782-106">MSMQ messages can be dropped when [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] (used with either the NetMsmqBinding or MsmqIntegrationBinding) is unable to process them.</span></span> <span data-ttu-id="dd782-107">Essas mensagens são denominadas mensagens suspeitas.</span><span class="sxs-lookup"><span data-stu-id="dd782-107">Such messages are referred to as poison messages.</span></span>  
  
 <span data-ttu-id="dd782-108">Uma mensagem suspeita será removida quando o `ReceiveErrorHandling` no NetMsmqBinding ou MsmqIntegrationBinding estiver definida como `Drop`.</span><span class="sxs-lookup"><span data-stu-id="dd782-108">A poison message is dropped when the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding is set to `Drop`.</span></span> <span data-ttu-id="dd782-109">Uma mensagem descartada é removida da fila e não é recuperável.</span><span class="sxs-lookup"><span data-stu-id="dd782-109">A dropped message is removed from the queue and is no longer recoverable.</span></span>  
  
 <span data-ttu-id="dd782-110">Consulte [manipulação de mensagens suspeitas](http://go.microsoft.com/fwlink/?LinkID=99546) para obter mais detalhes sobre quando as mensagens são suspeitas e como configurar seu serviço para tratar de maneira adequada.</span><span class="sxs-lookup"><span data-stu-id="dd782-110">See [Poison-Message Handling](http://go.microsoft.com/fwlink/?LinkID=99546) for more details on when messages become poison and how to configure your service to handle them appropriately.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd782-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dd782-111">See Also</span></span>  
 [<span data-ttu-id="dd782-112">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="dd782-112">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="dd782-113">Usando o rastreamento para solucionar problemas do seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="dd782-113">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="dd782-114">Administração e diagnósticos</span><span class="sxs-lookup"><span data-stu-id="dd782-114">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)  
 [<span data-ttu-id="dd782-115">Tratamento de mensagens suspeitas</span><span class="sxs-lookup"><span data-stu-id="dd782-115">Poison-Message Handling</span></span>](http://go.microsoft.com/fwlink/?LinkID=99546)
