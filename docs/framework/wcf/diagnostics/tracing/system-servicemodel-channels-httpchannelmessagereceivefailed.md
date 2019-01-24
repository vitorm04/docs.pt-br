---
title: System.ServiceModel.Channels.HttpChannelMessageReceiveFailed
ms.date: 03/30/2017
ms.assetid: 9eb311da-fdcc-4dd3-9d85-05b3280dfdda
ms.openlocfilehash: 22730ef8a0c0b4706f9e267fef251014a70a58fb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54720165"
---
# <a name="systemservicemodelchannelshttpchannelmessagereceivefailed"></a><span data-ttu-id="b1bf2-102">System.ServiceModel.Channels.HttpChannelMessageReceiveFailed</span><span class="sxs-lookup"><span data-stu-id="b1bf2-102">System.ServiceModel.Channels.HttpChannelMessageReceiveFailed</span></span>
<span data-ttu-id="b1bf2-103">Falha ao receber uma mensagem por um canal HTTP.</span><span class="sxs-lookup"><span data-stu-id="b1bf2-103">Failed to receive a message over an HTTP channel.</span></span>  
  
## <a name="description"></a><span data-ttu-id="b1bf2-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="b1bf2-104">Description</span></span>  
 <span data-ttu-id="b1bf2-105">Este rastreamento pode ser emitido como um aviso ou erro.</span><span class="sxs-lookup"><span data-stu-id="b1bf2-105">This trace can be emitted as a warning or an error.</span></span> <span data-ttu-id="b1bf2-106">Em ambos os casos, o rastreamento será emitido quando um ouvinte compatível não for encontrado para uma solicitação HTTP de entrada e a solicitação HTTP é descartada.</span><span class="sxs-lookup"><span data-stu-id="b1bf2-106">In both cases, the trace is emitted when a compatible listener is not found for an incoming HTTP request and the HTTP request is discarded.</span></span> <span data-ttu-id="b1bf2-107">Isso pode acontecer porque o verbo HTTP da solicitação não foi reconhecido por qualquer ouvinte HTTP, ou porque nenhum ouvinte estava escutando no endereço a solicitação foi direcionada para.</span><span class="sxs-lookup"><span data-stu-id="b1bf2-107">This could happen because the request’s HTTP verb was not recognized by any HTTP listener, or because no listener was listening on the address the request was targeted for.</span></span> <span data-ttu-id="b1bf2-108">O rastreamento é emitido como um aviso no caso de auto-hospedado e como um erro quando o serviço está hospedado no IIS.</span><span class="sxs-lookup"><span data-stu-id="b1bf2-108">The trace is emitted as a warning in the self-hosted case, and as an error when the service is hosted in IIS.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1bf2-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b1bf2-109">See also</span></span>
- [<span data-ttu-id="b1bf2-110">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="b1bf2-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="b1bf2-111">Usando o rastreamento para solucionar problemas do seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="b1bf2-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="b1bf2-112">Administração e diagnósticos</span><span class="sxs-lookup"><span data-stu-id="b1bf2-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
