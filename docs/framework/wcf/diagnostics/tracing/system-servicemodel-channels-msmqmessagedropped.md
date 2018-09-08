---
title: System.ServiceModel.Channels.MsmqMessageDropped
ms.date: 03/30/2017
ms.assetid: 8b6e644d-fa68-4be7-abe9-3659671a37c1
ms.openlocfilehash: 07bef8b391a03f2c011e1d1a7c7fb4fad908e022
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44205874"
---
# <a name="systemservicemodelchannelsmsmqmessagedropped"></a><span data-ttu-id="a87af-102">System.ServiceModel.Channels.MsmqMessageDropped</span><span class="sxs-lookup"><span data-stu-id="a87af-102">System.ServiceModel.Channels.MsmqMessageDropped</span></span>
<span data-ttu-id="a87af-103">A mensagem descartada do MSMQ.</span><span class="sxs-lookup"><span data-stu-id="a87af-103">MSMQ dropped the message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="a87af-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="a87af-104">Description</span></span>  
 <span data-ttu-id="a87af-105">O rastreamento indica que uma mensagem MSMQ foi descartada.</span><span class="sxs-lookup"><span data-stu-id="a87af-105">The trace indicates that an MSMQ message was dropped.</span></span> <span data-ttu-id="a87af-106">Mensagens MSMQ podem ser descartadas quando o Windows Communication Foundation (WCF) (usado com o NetMsmqBinding ou MsmqIntegrationBinding) não pode processá-los.</span><span class="sxs-lookup"><span data-stu-id="a87af-106">MSMQ messages can be dropped when Windows Communication Foundation (WCF) (used with either the NetMsmqBinding or MsmqIntegrationBinding) is unable to process them.</span></span> <span data-ttu-id="a87af-107">Essas mensagens são denominadas mensagens suspeitas.</span><span class="sxs-lookup"><span data-stu-id="a87af-107">Such messages are referred to as poison messages.</span></span>  
  
 <span data-ttu-id="a87af-108">Uma mensagem suspeita será removida quando o `ReceiveErrorHandling` sobre o NetMsmqBinding ou MsmqIntegrationBinding estiver definida como `Drop`.</span><span class="sxs-lookup"><span data-stu-id="a87af-108">A poison message is dropped when the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding is set to `Drop`.</span></span> <span data-ttu-id="a87af-109">Uma mensagem descartada é removida da fila e não é recuperável.</span><span class="sxs-lookup"><span data-stu-id="a87af-109">A dropped message is removed from the queue and is no longer recoverable.</span></span>  
  
 <span data-ttu-id="a87af-110">Ver [tratamento de mensagens suspeitas](https://go.microsoft.com/fwlink/?LinkID=99546) para obter mais detalhes sobre quando as mensagens se tornarão suspeitas e como configurar seu serviço para tratá-las adequadamente.</span><span class="sxs-lookup"><span data-stu-id="a87af-110">See [Poison-Message Handling](https://go.microsoft.com/fwlink/?LinkID=99546) for more details on when messages become poison and how to configure your service to handle them appropriately.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a87af-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a87af-111">See Also</span></span>  
 [<span data-ttu-id="a87af-112">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="a87af-112">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="a87af-113">Usando o rastreamento para solucionar problemas do seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="a87af-113">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="a87af-114">Administração e diagnósticos</span><span class="sxs-lookup"><span data-stu-id="a87af-114">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)  
 [<span data-ttu-id="a87af-115">Manipulação de mensagens suspeitas</span><span class="sxs-lookup"><span data-stu-id="a87af-115">Poison-Message Handling</span></span>](https://go.microsoft.com/fwlink/?LinkID=99546)
