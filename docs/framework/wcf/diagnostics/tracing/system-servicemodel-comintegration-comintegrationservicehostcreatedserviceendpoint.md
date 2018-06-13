---
title: System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed
ms.date: 03/30/2017
ms.assetid: d75d39da-7502-4a6a-91b9-eaa05b8e24d5
ms.openlocfilehash: 0a28eec659b48d5add4c53bc8c16972892e65099
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33487900"
---
# <a name="systemservicemodelchannelsmsmqmoveordeleteattemptfailed"></a><span data-ttu-id="542bd-102">System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed</span><span class="sxs-lookup"><span data-stu-id="542bd-102">System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed</span></span>
<span data-ttu-id="542bd-103">Não é possível mover ou excluir a mensagem.</span><span class="sxs-lookup"><span data-stu-id="542bd-103">Cannot move or delete message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="542bd-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="542bd-104">Description</span></span>  
 <span data-ttu-id="542bd-105">O rastreamento indica que ocorreu uma falha ao tentar mover, excluir ou rejeitar uma mensagem MSMQ.</span><span class="sxs-lookup"><span data-stu-id="542bd-105">The trace indicates that a failure occurred when attempting to move, delete, or reject an MSMQ message.</span></span>  
  
 <span data-ttu-id="542bd-106">Mensagens MSMQ são utilizadas pelo Windows Communication Foundation (WCF) (quando usado com o NetMsmqBinding ou MsmqIntegrationBinding). Este rastreamento está relacionado ao valor escolhido o `ReceiveErrorHandling` propriedade no NetMsmqBinding ou MsmqIntegrationBinding.</span><span class="sxs-lookup"><span data-stu-id="542bd-106">MSMQ messages are employed by Windows Communication Foundation (WCF) (when used with either the NetMsmqBinding or the MsmqIntegrationBinding).This trace is related to the chosen value of the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding.</span></span>  
  
 <span data-ttu-id="542bd-107">Este rastreamento não é uma indicação de uma falha geral no sistema.</span><span class="sxs-lookup"><span data-stu-id="542bd-107">This trace is not indicative of an overall system failure.</span></span> <span data-ttu-id="542bd-108">No entanto, ele indica escolhido suspeitas disposição de mensagem falhou para uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="542bd-108">However, it indicates that the chosen poison message disposition failed for a message.</span></span> <span data-ttu-id="542bd-109">Consulte [manipulação de mensagens suspeitas](http://go.microsoft.com/fwlink/?LinkID=99546) para obter mais detalhes sobre quando as mensagens são suspeitas e como configurar seu serviço para tratar de maneira adequada.</span><span class="sxs-lookup"><span data-stu-id="542bd-109">See [Poison-Message Handling](http://go.microsoft.com/fwlink/?LinkID=99546) for more details on when messages become poison and how to configure your service to handle them appropriately.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="542bd-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="542bd-110">See Also</span></span>  
 [<span data-ttu-id="542bd-111">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="542bd-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="542bd-112">Usando o rastreamento para solucionar problemas do seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="542bd-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="542bd-113">Administração e diagnósticos</span><span class="sxs-lookup"><span data-stu-id="542bd-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
