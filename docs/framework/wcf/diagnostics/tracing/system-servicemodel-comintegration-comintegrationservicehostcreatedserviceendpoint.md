---
title: System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed
ms.date: 03/30/2017
ms.assetid: d75d39da-7502-4a6a-91b9-eaa05b8e24d5
ms.openlocfilehash: 8b81cdcaf74aca044260495867b2c4f1de517682
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84593744"
---
# <a name="systemservicemodelchannelsmsmqmoveordeleteattemptfailed"></a><span data-ttu-id="cfc2b-102">System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed</span><span class="sxs-lookup"><span data-stu-id="cfc2b-102">System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed</span></span>
<span data-ttu-id="cfc2b-103">Não é possível mover ou excluir a mensagem.</span><span class="sxs-lookup"><span data-stu-id="cfc2b-103">Cannot move or delete message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="cfc2b-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="cfc2b-104">Description</span></span>  
 <span data-ttu-id="cfc2b-105">O rastreamento indica que uma falha ocorreu ao tentar mover, excluir ou rejeitar uma mensagem MSMQ.</span><span class="sxs-lookup"><span data-stu-id="cfc2b-105">The trace indicates that a failure occurred when attempting to move, delete, or reject an MSMQ message.</span></span>  
  
 <span data-ttu-id="cfc2b-106">As mensagens MSMQ são empregadas por Windows Communication Foundation (WCF) (quando usadas com NetMsmqBinding ou MsmqIntegrationBinding). Esse rastreamento está relacionado ao valor escolhido da `ReceiveErrorHandling` propriedade em NetMsmqBinding ou MsmqIntegrationBinding.</span><span class="sxs-lookup"><span data-stu-id="cfc2b-106">MSMQ messages are employed by Windows Communication Foundation (WCF) (when used with either the NetMsmqBinding or the MsmqIntegrationBinding).This trace is related to the chosen value of the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding.</span></span>  
  
 <span data-ttu-id="cfc2b-107">Esse rastreamento não indica uma falha geral do sistema.</span><span class="sxs-lookup"><span data-stu-id="cfc2b-107">This trace is not indicative of an overall system failure.</span></span> <span data-ttu-id="cfc2b-108">No entanto, isso indica que a disposição de mensagem suspeita escolhida falhou para uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="cfc2b-108">However, it indicates that the chosen poison message disposition failed for a message.</span></span> <span data-ttu-id="cfc2b-109">Para obter mais informações sobre quando as mensagens se tornam suspeitas e como configurar seu serviço para tratá-las adequadamente, consulte [manipulação de mensagens suspeitas](../../feature-details/poison-message-handling.md).</span><span class="sxs-lookup"><span data-stu-id="cfc2b-109">For more information on when messages become poison and how to configure your service to handle them appropriately, see [Poison-Message Handling](../../feature-details/poison-message-handling.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfc2b-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cfc2b-110">See also</span></span>

- [<span data-ttu-id="cfc2b-111">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="cfc2b-111">Tracing</span></span>](index.md)
- [<span data-ttu-id="cfc2b-112">Utilizando o rastreamento para solucionar problemas em seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="cfc2b-112">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="cfc2b-113">Administração e diagnóstico</span><span class="sxs-lookup"><span data-stu-id="cfc2b-113">Administration and Diagnostics</span></span>](../index.md)
