---
title: System.ServiceModel.Channels.MsmqMessageDropped
ms.date: 03/30/2017
ms.assetid: 8b6e644d-fa68-4be7-abe9-3659671a37c1
ms.openlocfilehash: 4b016f53a75d9527a5cd1bbadacacd650b7f35b0
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601889"
---
# <a name="systemservicemodelchannelsmsmqmessagedropped"></a><span data-ttu-id="ef597-102">System.ServiceModel.Channels.MsmqMessageDropped</span><span class="sxs-lookup"><span data-stu-id="ef597-102">System.ServiceModel.Channels.MsmqMessageDropped</span></span>
<span data-ttu-id="ef597-103">O MSMQ removeu a mensagem.</span><span class="sxs-lookup"><span data-stu-id="ef597-103">MSMQ dropped the message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="ef597-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="ef597-104">Description</span></span>  
 <span data-ttu-id="ef597-105">O rastreamento indica que uma mensagem MSMQ foi descartada.</span><span class="sxs-lookup"><span data-stu-id="ef597-105">The trace indicates that an MSMQ message was dropped.</span></span> <span data-ttu-id="ef597-106">As mensagens MSMQ podem ser descartadas quando Windows Communication Foundation (WCF) (usado com o NetMsmqBinding ou MsmqIntegrationBinding) não puder processá-las.</span><span class="sxs-lookup"><span data-stu-id="ef597-106">MSMQ messages can be dropped when Windows Communication Foundation (WCF) (used with either the NetMsmqBinding or MsmqIntegrationBinding) is unable to process them.</span></span> <span data-ttu-id="ef597-107">Essas mensagens são chamadas de mensagens suspeitas.</span><span class="sxs-lookup"><span data-stu-id="ef597-107">Such messages are referred to as poison messages.</span></span>  
  
 <span data-ttu-id="ef597-108">Uma mensagem suspeita é descartada quando a `ReceiveErrorHandling` propriedade em NetMsmqBinding ou MsmqIntegrationBinding é definida como `Drop` .</span><span class="sxs-lookup"><span data-stu-id="ef597-108">A poison message is dropped when the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding is set to `Drop`.</span></span> <span data-ttu-id="ef597-109">Uma mensagem descartada é removida da fila e não é mais recuperável.</span><span class="sxs-lookup"><span data-stu-id="ef597-109">A dropped message is removed from the queue and is no longer recoverable.</span></span>  
  
 <span data-ttu-id="ef597-110">Para obter mais informações sobre quando as mensagens se tornam suspeitas e como configurar seu serviço para tratá-las adequadamente, consulte [manipulação de mensagens suspeitas](../../feature-details/poison-message-handling.md).</span><span class="sxs-lookup"><span data-stu-id="ef597-110">For more information on when messages become poison and how to configure your service to handle them appropriately, see [Poison-Message Handling](../../feature-details/poison-message-handling.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef597-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ef597-111">See also</span></span>

- [<span data-ttu-id="ef597-112">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="ef597-112">Tracing</span></span>](index.md)
- [<span data-ttu-id="ef597-113">Utilizando o rastreamento para solucionar problemas em seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="ef597-113">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="ef597-114">Administração e diagnóstico</span><span class="sxs-lookup"><span data-stu-id="ef597-114">Administration and Diagnostics</span></span>](../index.md)
- [<span data-ttu-id="ef597-115">Manipulação de mensagens suspeitas</span><span class="sxs-lookup"><span data-stu-id="ef597-115">Poison-Message Handling</span></span>](../../feature-details/poison-message-handling.md)
