---
title: System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed
ms.date: 03/30/2017
ms.assetid: d75d39da-7502-4a6a-91b9-eaa05b8e24d5
ms.openlocfilehash: 7e7bd48d206456af6a5a8662516c4d9c82b3ed2f
ms.sourcegitcommit: f513a91160b3fec289dd06646d0d6f81f8fcf910
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46007081"
---
# <a name="systemservicemodelchannelsmsmqmoveordeleteattemptfailed"></a><span data-ttu-id="6003b-102">System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed</span><span class="sxs-lookup"><span data-stu-id="6003b-102">System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed</span></span>
<span data-ttu-id="6003b-103">Não é possível mover ou excluir a mensagem.</span><span class="sxs-lookup"><span data-stu-id="6003b-103">Cannot move or delete message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="6003b-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="6003b-104">Description</span></span>  
 <span data-ttu-id="6003b-105">O rastreamento indica que ocorreu uma falha ao tentar mover, excluir ou rejeitar uma mensagem MSMQ.</span><span class="sxs-lookup"><span data-stu-id="6003b-105">The trace indicates that a failure occurred when attempting to move, delete, or reject an MSMQ message.</span></span>  
  
 <span data-ttu-id="6003b-106">Mensagens MSMQ são utilizadas pelo Windows Communication Foundation (WCF) (quando usado com o NetMsmqBinding ou o MsmqIntegrationBinding). Este rastreamento está relacionado ao valor escolhido o `ReceiveErrorHandling` propriedade no NetMsmqBinding ou MsmqIntegrationBinding.</span><span class="sxs-lookup"><span data-stu-id="6003b-106">MSMQ messages are employed by Windows Communication Foundation (WCF) (when used with either the NetMsmqBinding or the MsmqIntegrationBinding).This trace is related to the chosen value of the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding.</span></span>  
  
 <span data-ttu-id="6003b-107">Esse rastreamento não é uma indicação de uma falha geral no sistema.</span><span class="sxs-lookup"><span data-stu-id="6003b-107">This trace is not indicative of an overall system failure.</span></span> <span data-ttu-id="6003b-108">No entanto, ele indica que o escolhido suspeitas falhou para uma mensagem de disposição de mensagem.</span><span class="sxs-lookup"><span data-stu-id="6003b-108">However, it indicates that the chosen poison message disposition failed for a message.</span></span> <span data-ttu-id="6003b-109">Ver [tratamento de mensagens suspeitas](https://go.microsoft.com/fwlink/?LinkID=99546) para obter mais detalhes sobre quando as mensagens se tornarão suspeitas e como configurar seu serviço para tratá-las adequadamente.</span><span class="sxs-lookup"><span data-stu-id="6003b-109">See [Poison-Message Handling](https://go.microsoft.com/fwlink/?LinkID=99546) for more details on when messages become poison and how to configure your service to handle them appropriately.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6003b-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6003b-110">See Also</span></span>  
 [<span data-ttu-id="6003b-111">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="6003b-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="6003b-112">Usando o rastreamento para solucionar problemas do seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="6003b-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="6003b-113">Administração e diagnósticos</span><span class="sxs-lookup"><span data-stu-id="6003b-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
