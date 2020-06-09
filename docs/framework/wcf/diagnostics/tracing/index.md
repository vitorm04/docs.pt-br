---
title: Rastreamento
ms.date: 03/30/2017
ms.assetid: 2649eae2-dbf8-421c-9cfb-cfa9e01de87f
ms.openlocfilehash: 569a97dc21a434cd711ad4c735f828df588f3af7
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84578975"
---
# <a name="tracing"></a><span data-ttu-id="4da3f-102">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="4da3f-102">Tracing</span></span>
<span data-ttu-id="4da3f-103">O Windows Communication Foundation (WCF) fornece dados de diagnóstico e instrumentação de aplicativos para monitoramento e análise de falhas.</span><span class="sxs-lookup"><span data-stu-id="4da3f-103">Windows Communication Foundation (WCF) provides application instrumentation and diagnostic data for fault monitoring and analysis.</span></span> <span data-ttu-id="4da3f-104">Você pode usar o rastreamento em vez de um depurador para entender como um aplicativo está se comportando, ou por que ele falha.</span><span class="sxs-lookup"><span data-stu-id="4da3f-104">You can use tracing instead of a debugger to understand how an application is behaving, or why it faults.</span></span> <span data-ttu-id="4da3f-105">Você também pode correlacionar as falhas e o processamento entre os componentes para fornecer uma experiência de ponta a ponta.</span><span class="sxs-lookup"><span data-stu-id="4da3f-105">You can also correlate faults and processing across components to provide an end-to-end experience.</span></span>  
  
 <span data-ttu-id="4da3f-106">O WCF gera os seguintes dados para o rastreamento de diagnóstico:</span><span class="sxs-lookup"><span data-stu-id="4da3f-106">WCF outputs the following data for diagnostic tracing:</span></span>  
  
- <span data-ttu-id="4da3f-107">Rastreamentos de etapas de processo em todos os componentes dos aplicativos, como chamadas de operação, exceções de código, avisos e outros eventos de processamento significativos. "</span><span class="sxs-lookup"><span data-stu-id="4da3f-107">Traces for process milestones across all components of the applications, such as operation calls, code exceptions, warnings and other significant processing events."</span></span>  
  
- <span data-ttu-id="4da3f-108">Eventos de erro do Windows quando o recurso de rastreamento não funciona.</span><span class="sxs-lookup"><span data-stu-id="4da3f-108">Windows error events when the tracing feature malfunctions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4da3f-109">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="4da3f-109">In This Section</span></span>  
 [<span data-ttu-id="4da3f-110">Configurando o rastreamento</span><span class="sxs-lookup"><span data-stu-id="4da3f-110">Configuring Tracing</span></span>](configuring-tracing.md)  
  
 <span data-ttu-id="4da3f-111">Este tópico descreve como você pode configurar o rastreamento em diferentes níveis para se adequar à sua necessidade específica.</span><span class="sxs-lookup"><span data-stu-id="4da3f-111">This topic describes how you can configure tracing at different levels to suit your specific need.</span></span>  
  
 [<span data-ttu-id="4da3f-112">Rastreamento de ponta a ponta</span><span class="sxs-lookup"><span data-stu-id="4da3f-112">End-to-End Tracing</span></span>](end-to-end-tracing.md)  
  
 <span data-ttu-id="4da3f-113">Esta seção descreve como você pode usar o rastreamento de atividade e a propagação para correlação de ponta a ponta para auxiliar na depuração.</span><span class="sxs-lookup"><span data-stu-id="4da3f-113">This section describes how you can use Activity Tracing and Propagation for end-to-end correlation to assist debugging.</span></span>  
  
 [<span data-ttu-id="4da3f-114">Utilizando o rastreamento para solucionar problemas em seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="4da3f-114">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)  
  
 <span data-ttu-id="4da3f-115">Esta seção descreve como você pode usar o rastreamento para depurar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4da3f-115">This section describes how you can use tracing to debug your application.</span></span>  
  
 [<span data-ttu-id="4da3f-116">Preocupações de segurança e dicas úteis para rastreamento</span><span class="sxs-lookup"><span data-stu-id="4da3f-116">Security Concerns and Useful Tips for Tracing</span></span>](security-concerns-and-useful-tips-for-tracing.md)  
  
 <span data-ttu-id="4da3f-117">Este tópico descreve como você pode proteger informações confidenciais de serem expostas, bem como dicas úteis ao usar o webhost.</span><span class="sxs-lookup"><span data-stu-id="4da3f-117">This topic describes how you can protect sensitive information from being exposed, as well as useful tips when using WebHost.</span></span>  
  
 [<span data-ttu-id="4da3f-118">Referência de rastreamentos</span><span class="sxs-lookup"><span data-stu-id="4da3f-118">Traces Reference</span></span>](traces-reference.md)  
  
 <span data-ttu-id="4da3f-119">Este tópico lista todos os rastreamentos gerados pelo WCF.</span><span class="sxs-lookup"><span data-stu-id="4da3f-119">This topic lists all the traces generated by WCF.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4da3f-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4da3f-120">See also</span></span>

- [<span data-ttu-id="4da3f-121">Ferramenta Visualizador de rastreamento de serviço (SvcTraceViewer.exe)</span><span class="sxs-lookup"><span data-stu-id="4da3f-121">Service Trace Viewer Tool (SvcTraceViewer.exe)</span></span>](../../service-trace-viewer-tool-svctraceviewer-exe.md)
