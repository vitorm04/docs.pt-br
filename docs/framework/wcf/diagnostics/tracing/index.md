---
title: Rastreamento
ms.date: 03/30/2017
ms.assetid: 2649eae2-dbf8-421c-9cfb-cfa9e01de87f
ms.openlocfilehash: 3520d2aca07f988c45d65d5d8113d05292a37638
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64664956"
---
# <a name="tracing"></a><span data-ttu-id="1ac9c-102">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="1ac9c-102">Tracing</span></span>
<span data-ttu-id="1ac9c-103">Windows Communication Foundation (WCF) fornece instrumentação de aplicativos e dados de diagnóstico para análise e monitoramento de falhas.</span><span class="sxs-lookup"><span data-stu-id="1ac9c-103">Windows Communication Foundation (WCF) provides application instrumentation and diagnostic data for fault monitoring and analysis.</span></span> <span data-ttu-id="1ac9c-104">Você pode usar o rastreamento em vez de um depurador para entender como um aplicativo está se comportando ou por que ela faz.</span><span class="sxs-lookup"><span data-stu-id="1ac9c-104">You can use tracing instead of a debugger to understand how an application is behaving, or why it faults.</span></span> <span data-ttu-id="1ac9c-105">Também é possível correlacionar falhas e processamento entre os componentes para fornecer uma experiência de ponta a ponta.</span><span class="sxs-lookup"><span data-stu-id="1ac9c-105">You can also correlate faults and processing across components to provide an end-to-end experience.</span></span>  
  
 <span data-ttu-id="1ac9c-106">O WCF gera os seguintes dados para o rastreamento de diagnóstico:</span><span class="sxs-lookup"><span data-stu-id="1ac9c-106">WCF outputs the following data for diagnostic tracing:</span></span>  
  
- <span data-ttu-id="1ac9c-107">Para as etapas do processo em todos os componentes de aplicativos, como chamadas de operação, os rastreamentos de código exceções, avisos e outros eventos de processamento significativo."</span><span class="sxs-lookup"><span data-stu-id="1ac9c-107">Traces for process milestones across all components of the applications, such as operation calls, code exceptions, warnings and other significant processing events."</span></span>  
  
- <span data-ttu-id="1ac9c-108">Eventos de erro do Windows quando o recurso de rastreamento funciona incorretamente.</span><span class="sxs-lookup"><span data-stu-id="1ac9c-108">Windows error events when the tracing feature malfunctions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1ac9c-109">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="1ac9c-109">In This Section</span></span>  
 [<span data-ttu-id="1ac9c-110">Configurando o rastreamento</span><span class="sxs-lookup"><span data-stu-id="1ac9c-110">Configuring Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)  
  
 <span data-ttu-id="1ac9c-111">Este tópico descreve como você pode configurar o rastreamento em níveis diferentes para atender às suas necessidades específicas.</span><span class="sxs-lookup"><span data-stu-id="1ac9c-111">This topic describes how you can configure tracing at different levels to suit your specific need.</span></span>  
  
 [<span data-ttu-id="1ac9c-112">Rastreamento ponta a ponta</span><span class="sxs-lookup"><span data-stu-id="1ac9c-112">End-to-End Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing.md)  
  
 <span data-ttu-id="1ac9c-113">Esta seção descreve como você pode usar o rastreamento de atividade e de propagação para correlação de ponta a ponta para ajudar na depuração.</span><span class="sxs-lookup"><span data-stu-id="1ac9c-113">This section describes how you can use Activity Tracing and Propagation for end-to-end correlation to assist debugging.</span></span>  
  
 [<span data-ttu-id="1ac9c-114">Usando o rastreamento para solucionar problemas do seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="1ac9c-114">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
  
 <span data-ttu-id="1ac9c-115">Esta seção descreve como você pode usar o rastreamento para depurar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1ac9c-115">This section describes how you can use tracing to debug your application.</span></span>  
  
 [<span data-ttu-id="1ac9c-116">Questões de segurança e dicas úteis para rastreamento</span><span class="sxs-lookup"><span data-stu-id="1ac9c-116">Security Concerns and Useful Tips for Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/security-concerns-and-useful-tips-for-tracing.md)  
  
 <span data-ttu-id="1ac9c-117">Este tópico descreve como você pode proteger informações confidenciais sejam expostas, bem como dicas úteis ao usar o WebHost.</span><span class="sxs-lookup"><span data-stu-id="1ac9c-117">This topic describes how you can protect sensitive information from being exposed, as well as useful tips when using WebHost.</span></span>  
  
 [<span data-ttu-id="1ac9c-118">Referência de rastreamentos</span><span class="sxs-lookup"><span data-stu-id="1ac9c-118">Traces Reference</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/traces-reference.md)  
  
 <span data-ttu-id="1ac9c-119">Este tópico lista todos os rastreamentos gerados pelo WCF.</span><span class="sxs-lookup"><span data-stu-id="1ac9c-119">This topic lists all the traces generated by WCF.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ac9c-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1ac9c-120">See also</span></span>

- [<span data-ttu-id="1ac9c-121">Ferramenta Visualizador de rastreamento de serviço (SvcTraceViewer.exe)</span><span class="sxs-lookup"><span data-stu-id="1ac9c-121">Service Trace Viewer Tool (SvcTraceViewer.exe)</span></span>](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)
