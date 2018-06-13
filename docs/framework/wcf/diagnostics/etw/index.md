---
title: Rastreamento analítico com ETW
ms.date: 03/30/2017
helpviewer_keywords:
- diagnostics [WCF], analytic tracing
- administration [WCF], analytic tracing
- analytic tracing [WCF]
ms.assetid: 1d518e47-a38d-41e8-93d7-8c3b361f6a56
ms.openlocfilehash: 210418b8a8765a1fc59658e9df57c92ce087c95f
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33809258"
---
# <a name="analytic-tracing-with-etw"></a><span data-ttu-id="15d20-102">Rastreamento analítico com ETW</span><span class="sxs-lookup"><span data-stu-id="15d20-102">Analytic Tracing with ETW</span></span>
<span data-ttu-id="15d20-103">Rastreamento analítico do Windows Communication Foundation (WCF) oferece uma maneira de capturar informações de diagnóstico durante a execução de um serviço WCF.</span><span class="sxs-lookup"><span data-stu-id="15d20-103">Windows Communication Foundation (WCF) analytic tracing offers a way to capture diagnostic information during the execution of a WCF service.</span></span> <span data-ttu-id="15d20-104">Eventos de rastreamento analítico do WCF são emitidos nos pontos-chave na pilha do WCF para permitir a solução de problemas de serviços do WCF em um ambiente de produção.</span><span class="sxs-lookup"><span data-stu-id="15d20-104">WCF analytic tracing events are emitted at key points in the WCF stack to allow troubleshooting of WCF services in a production environment.</span></span> <span data-ttu-id="15d20-105">Rastreamento analítico para serviços WCF tem um impacto mínimo sobre o desempenho de um produto de servidor que hospeda [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] dos serviços WCF como esses eventos são emitidos com muita eficiência em uma sessão de rastreamento de eventos para Windows (ETW).</span><span class="sxs-lookup"><span data-stu-id="15d20-105">Analytic tracing for WCF services has minimal impact on the performance of a product server that hosts [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] WCF services as these events are very efficiently emitted to an Event Tracing for Windows (ETW) session.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="15d20-106">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="15d20-106">In This Section</span></span>  
 [<span data-ttu-id="15d20-107">Visão geral de rastreamento analítico</span><span class="sxs-lookup"><span data-stu-id="15d20-107">Analytic Tracing Overview</span></span>](../../../../../docs/framework/wcf/diagnostics/etw/analytic-tracing-overview.md)  
 <span data-ttu-id="15d20-108">Discute como rastreamento analítico do WCF funciona no [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="15d20-108">Discusses how WCF analytic tracing works in [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)].</span></span>  
  
 [<span data-ttu-id="15d20-109">Rastreamento analítico habilitado dinamicamente</span><span class="sxs-lookup"><span data-stu-id="15d20-109">Dynamically Enabling Analytic Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/etw/dynamically-enabling-analytic-tracing.md)  
 <span data-ttu-id="15d20-110">Descreve como habilitar ou desabilitar o rastreamento dinamicamente com o ETW.</span><span class="sxs-lookup"><span data-stu-id="15d20-110">Discusses how to enable or disable tracing dynamically using ETW.</span></span>  
  
 [<span data-ttu-id="15d20-111">Configurando o rastreamento de fluxo de mensagem</span><span class="sxs-lookup"><span data-stu-id="15d20-111">Configuring Message Flow Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/etw/configuring-message-flow-tracing.md)  
 <span data-ttu-id="15d20-112">Descreve como configurar o rastreamento de fluxo de mensagem.</span><span class="sxs-lookup"><span data-stu-id="15d20-112">Describes how to configure message flow tracing.</span></span>  
  
 [<span data-ttu-id="15d20-113">Referência de evento de rastreamento analítico</span><span class="sxs-lookup"><span data-stu-id="15d20-113">Analytic Trace Event Reference</span></span>](../../../../../docs/framework/wcf/diagnostics/etw/analytic-trace-event-reference.md)  
 <span data-ttu-id="15d20-114">Mostra uma tabela de IDs de eventos com níveis de evento, mensagens de eventos e as palavras-chave.</span><span class="sxs-lookup"><span data-stu-id="15d20-114">Shows a table of event IDs with their event levels, event messages and keywords.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15d20-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="15d20-115">See Also</span></span>  
 [<span data-ttu-id="15d20-116">Serviços do WCF e Rastreamento de Eventos para Windows</span><span class="sxs-lookup"><span data-stu-id="15d20-116">WCF Services and Event Tracing for Windows</span></span>](../../../../../docs/framework/wcf/samples/wcf-services-and-event-tracing-for-windows.md)  
 [<span data-ttu-id="15d20-117">Acompanhamento de eventos de rastreamento de evento no Windows</span><span class="sxs-lookup"><span data-stu-id="15d20-117">Tracking Events into Event Tracing in Windows</span></span>](../../../../../docs/framework/windows-workflow-foundation/samples/tracking-events-into-event-tracing-in-windows.md)
