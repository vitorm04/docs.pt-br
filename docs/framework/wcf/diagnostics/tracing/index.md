---
title: Rastreamento
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2649eae2-dbf8-421c-9cfb-cfa9e01de87f
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 75870850a7df01d255d3512dde2a550e2a6c205a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="tracing"></a><span data-ttu-id="19694-102">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="19694-102">Tracing</span></span>
[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]<span data-ttu-id="19694-103">Fornece dados de diagnóstico e de instrumentação do aplicativo para análise e monitoramento de falhas.</span><span class="sxs-lookup"><span data-stu-id="19694-103"> provides application instrumentation and diagnostic data for fault monitoring and analysis.</span></span> <span data-ttu-id="19694-104">Você pode usar o rastreamento em vez de um depurador para entender como um aplicativo está funcionando, ou por que ele falha.</span><span class="sxs-lookup"><span data-stu-id="19694-104">You can use tracing instead of a debugger to understand how an application is behaving, or why it faults.</span></span> <span data-ttu-id="19694-105">Você também pode correlacionar processamento e falhas em componentes para fornecer uma experiência de ponta a ponta.</span><span class="sxs-lookup"><span data-stu-id="19694-105">You can also correlate faults and processing across components to provide an end-to-end experience.</span></span>  
  
 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]<span data-ttu-id="19694-106">gera os seguintes dados para o rastreamento de diagnóstico:</span><span class="sxs-lookup"><span data-stu-id="19694-106"> outputs the following data for diagnostic tracing:</span></span>  
  
-   <span data-ttu-id="19694-107">Rastreamentos para as etapas do processo em todos os componentes de aplicativos, como chamadas de operação, código de exceções, avisos e outros eventos de processamento significativo."</span><span class="sxs-lookup"><span data-stu-id="19694-107">Traces for process milestones across all components of the applications, such as operation calls, code exceptions, warnings and other significant processing events."</span></span>  
  
-   <span data-ttu-id="19694-108">Eventos de erro do Windows quando o recurso de rastreamento de falhas.</span><span class="sxs-lookup"><span data-stu-id="19694-108">Windows error events when the tracing feature malfunctions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="19694-109">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="19694-109">In This Section</span></span>  
 [<span data-ttu-id="19694-110">Configurando o rastreamento</span><span class="sxs-lookup"><span data-stu-id="19694-110">Configuring Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)  
  
 <span data-ttu-id="19694-111">Este tópico descreve como você pode configurar o rastreamento em níveis diferentes de acordo com suas necessidades específicas.</span><span class="sxs-lookup"><span data-stu-id="19694-111">This topic describes how you can configure tracing at different levels to suit your specific need.</span></span>  
  
 [<span data-ttu-id="19694-112">Rastreamento ponta a ponta</span><span class="sxs-lookup"><span data-stu-id="19694-112">End-to-End Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing.md)  
  
 <span data-ttu-id="19694-113">Esta seção descreve como você pode usar o rastreamento de atividade e a propagação de correlação de ponta a ponta para auxiliar a depuração.</span><span class="sxs-lookup"><span data-stu-id="19694-113">This section describes how you can use Activity Tracing and Propagation for end-to-end correlation to assist debugging.</span></span>  
  
 [<span data-ttu-id="19694-114">Usando o rastreamento para solucionar problemas do seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="19694-114">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
  
 <span data-ttu-id="19694-115">Esta seção descreve como você pode usar o rastreamento para depurar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="19694-115">This section describes how you can use tracing to debug your application.</span></span>  
  
 [<span data-ttu-id="19694-116">Questões de segurança e dicas úteis para rastreamento</span><span class="sxs-lookup"><span data-stu-id="19694-116">Security Concerns and Useful Tips for Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/security-concerns-and-useful-tips-for-tracing.md)  
  
 <span data-ttu-id="19694-117">Este tópico descreve como proteger informações confidenciais sejam expostas, bem como dicas úteis ao usar WebHost.</span><span class="sxs-lookup"><span data-stu-id="19694-117">This topic describes how you can protect sensitive information from being exposed, as well as useful tips when using WebHost.</span></span>  
  
 [<span data-ttu-id="19694-118">Referência de rastreamentos</span><span class="sxs-lookup"><span data-stu-id="19694-118">Traces Reference</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/traces-reference.md)  
  
 <span data-ttu-id="19694-119">Este tópico lista todos os rastreamentos gerados pelo [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="19694-119">This topic lists all the traces generated by [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19694-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="19694-120">See Also</span></span>  
 [<span data-ttu-id="19694-121">Ferramenta Visualizador de rastreamento de serviço (SvcTraceViewer.exe)</span><span class="sxs-lookup"><span data-stu-id="19694-121">Service Trace Viewer Tool (SvcTraceViewer.exe)</span></span>](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)
