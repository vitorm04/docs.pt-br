---
title: Eventos ETW no CLR
ms.date: 03/30/2017
helpviewer_keywords:
- CLR ETW events
- ETW, common language runtime
- ETW, CLR events
ms.assetid: ef2b31c3-7426-43e7-9924-92339b96556d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 951941af2568e72fe093860801bd2595b3037e41
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428167"
---
# <a name="clr-etw-events"></a><span data-ttu-id="03388-102">Eventos ETW no CLR</span><span class="sxs-lookup"><span data-stu-id="03388-102">CLR ETW Events</span></span>
<span data-ttu-id="03388-103">Os tópicos desta seção descrevem os eventos ETW (rastreamento de eventos para Windows).</span><span class="sxs-lookup"><span data-stu-id="03388-103">The topics in this section describe event tracing for Windows (ETW) events.</span></span> <span data-ttu-id="03388-104">Cada evento tem uma palavra-chave e um nível associados, que são descritos no tópico [Palavras-chave e níveis CLR ETW](clr-etw-keywords-and-levels.md).</span><span class="sxs-lookup"><span data-stu-id="03388-104">Each event has an associated keyword and level, which are described in the [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md) topic.</span></span> <span data-ttu-id="03388-105">O CLR tem dois provedores para os eventos:</span><span class="sxs-lookup"><span data-stu-id="03388-105">The CLR has two providers for the events:</span></span>  
  
- <span data-ttu-id="03388-106">O provedor de runtime, que aciona eventos, dependendo de quais palavras-chave (categorias de eventos) são habilitadas.</span><span class="sxs-lookup"><span data-stu-id="03388-106">The runtime provider, which raises events depending on which keywords (categories of events) are enabled.</span></span> <span data-ttu-id="03388-107">O GUID do provedor de runtime CLR é e13c0d23-ccbc-4e12-931b-d9cc2eee27e4.</span><span class="sxs-lookup"><span data-stu-id="03388-107">The CLR runtime provider GUID is e13c0d23-ccbc-4e12-931b-d9cc2eee27e4.</span></span>  
  
- <span data-ttu-id="03388-108">O provedor de encerramento, que tem usos de finalidade especial.</span><span class="sxs-lookup"><span data-stu-id="03388-108">The rundown provider, which has special-purpose uses.</span></span> <span data-ttu-id="03388-109">O GUID do provedor de encerramento CLR é a669021c-c450-4609-a035-5af59af4df18.</span><span class="sxs-lookup"><span data-stu-id="03388-109">The CLR rundown provider GUID is a669021c-c450-4609-a035-5af59af4df18.</span></span>  
  
 <span data-ttu-id="03388-110">Para obter mais informações sobre os provedores, consulte [Provedores CLR ETW](clr-etw-providers.md).</span><span class="sxs-lookup"><span data-stu-id="03388-110">For more information about the providers, see [CLR ETW Providers](clr-etw-providers.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="03388-111">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="03388-111">In This Section</span></span>  
 [<span data-ttu-id="03388-112">Eventos de informações de runtime</span><span class="sxs-lookup"><span data-stu-id="03388-112">Runtime Information Events</span></span>](runtime-information-etw-events.md)  
 <span data-ttu-id="03388-113">Captura informações sobre o runtime, incluindo a SKU, o número de versão, a maneira pela qual o runtime foi ativado, os parâmetros de linha de comando com os quais ele foi iniciado, o GUID (se aplicável) e outras informações relevantes.</span><span class="sxs-lookup"><span data-stu-id="03388-113">Captures information about the runtime, including the SKU, version number, the manner in which the runtime was activated, the command-line parameters it was started with, the GUID (if applicable), and other relevant information.</span></span>  
  
 [<span data-ttu-id="03388-114">Evento Exception Thrown_V1</span><span class="sxs-lookup"><span data-stu-id="03388-114">Exception Thrown_V1 Event</span></span>](exception-thrown-v1-etw-event.md)  
 <span data-ttu-id="03388-115">Captura informações sobre as exceções geradas.</span><span class="sxs-lookup"><span data-stu-id="03388-115">Captures information about exceptions that are thrown.</span></span>  
  
 [<span data-ttu-id="03388-116">Eventos de contenção</span><span class="sxs-lookup"><span data-stu-id="03388-116">Contention Events</span></span>](contention-etw-events.md)  
 <span data-ttu-id="03388-117">Captura informações sobre a contenção de bloqueios do monitor ou bloqueios nativos usados pelo runtime.</span><span class="sxs-lookup"><span data-stu-id="03388-117">Captures information about contention for monitor locks or native locks that the runtime uses.</span></span>  
  
 [<span data-ttu-id="03388-118">Eventos de pool de threads</span><span class="sxs-lookup"><span data-stu-id="03388-118">Thread Pool Events</span></span>](thread-pool-etw-events.md)  
 <span data-ttu-id="03388-119">Captura informações sobre pools de threads de trabalho e pools de threads de E/S.</span><span class="sxs-lookup"><span data-stu-id="03388-119">Captures information about worker thread pools and I/O thread pools.</span></span>  
  
 [<span data-ttu-id="03388-120">Eventos de carregador</span><span class="sxs-lookup"><span data-stu-id="03388-120">Loader Events</span></span>](loader-etw-events.md)  
 <span data-ttu-id="03388-121">Captura informações sobre o carregamento e descarregamento de domínios do aplicativo, assemblies e módulos.</span><span class="sxs-lookup"><span data-stu-id="03388-121">Captures information about loading and unloading application domains, assemblies, and modules.</span></span>  
  
 [<span data-ttu-id="03388-122">Eventos de método</span><span class="sxs-lookup"><span data-stu-id="03388-122">Method Events</span></span>](method-etw-events.md)  
 <span data-ttu-id="03388-123">Captura informações sobre métodos CLR para a resolução de símbolo.</span><span class="sxs-lookup"><span data-stu-id="03388-123">Captures information about CLR methods for symbol resolution.</span></span>  
  
 [<span data-ttu-id="03388-124">Eventos de coleta de lixo</span><span class="sxs-lookup"><span data-stu-id="03388-124">Garbage Collection Events</span></span>](garbage-collection-etw-events.md)  
 <span data-ttu-id="03388-125">Captura informações referentes à coleta de lixo, para ajudar no diagnóstico e na depuração.</span><span class="sxs-lookup"><span data-stu-id="03388-125">Captures information pertaining to garbage collection, to help in diagnostics and debugging.</span></span>  
  
 [<span data-ttu-id="03388-126">Eventos de rastreamento JIT</span><span class="sxs-lookup"><span data-stu-id="03388-126">JIT Tracing Events</span></span>](jit-tracing-etw-events.md)  
 <span data-ttu-id="03388-127">Captura informações sobre chamadas inlining e tail JIT (Just-In-Time).</span><span class="sxs-lookup"><span data-stu-id="03388-127">Captures information about just-in-time (JIT) inlining and tail calls.</span></span>  
  
 [<span data-ttu-id="03388-128">Eventos de interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="03388-128">Interop Events</span></span>](interop-etw-events.md)  
 <span data-ttu-id="03388-129">Captura informações sobre a geração e o cache de stub da MSIL (Microsoft Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="03388-129">Captures information about Microsoft intermediate language (MSIL) stub generation and caching.</span></span>  
  
 [<span data-ttu-id="03388-130">Eventos de ARM</span><span class="sxs-lookup"><span data-stu-id="03388-130">ARM Events</span></span>](application-domain-resource-monitoring-arm-etw-events.md)  
 <span data-ttu-id="03388-131">Captura informações de diagnóstico detalhadas sobre o estado de um domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="03388-131">Captures detailed diagnostic information about the state of an application domain.</span></span>  
  
 [<span data-ttu-id="03388-132">Eventos de segurança</span><span class="sxs-lookup"><span data-stu-id="03388-132">Security Events</span></span>](security-etw-events.md)  
 <span data-ttu-id="03388-133">Captura informações sobre o nome forte e a verificação do Authenticode.</span><span class="sxs-lookup"><span data-stu-id="03388-133">Captures information about strong name and Authenticode verification.</span></span>  
  
 [<span data-ttu-id="03388-134">Evento de pilha</span><span class="sxs-lookup"><span data-stu-id="03388-134">Stack Event</span></span>](stack-etw-event.md)  
 <span data-ttu-id="03388-135">Captura informações que são usadas com outros eventos para gerar rastreamentos de pilha depois que um evento é acionado.</span><span class="sxs-lookup"><span data-stu-id="03388-135">Captures information that is used with other events to generate stack traces after an event is raised.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03388-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="03388-136">See also</span></span>

- [<span data-ttu-id="03388-137">Melhorar a depuração e o ajuste de desempenho com o ETW</span><span class="sxs-lookup"><span data-stu-id="03388-137">Improve Debugging And Performance Tuning With ETW</span></span>](https://docs.microsoft.com/archive/msdn-magazine/2007/april/event-tracing-improve-debugging-and-performance-tuning-with-etw)
- [<span data-ttu-id="03388-138">Blog de desempenho do Windows</span><span class="sxs-lookup"><span data-stu-id="03388-138">Windows Performance Blog</span></span>](https://blogs.msdn.microsoft.com/pigscanfly/tag/xperf/)
- [<span data-ttu-id="03388-139">Controlando o log no .NET Framework</span><span class="sxs-lookup"><span data-stu-id="03388-139">Controlling .NET Framework Logging</span></span>](controlling-logging.md)
- [<span data-ttu-id="03388-140">Provedores CLR ETW</span><span class="sxs-lookup"><span data-stu-id="03388-140">CLR ETW Providers</span></span>](clr-etw-providers.md)
- [<span data-ttu-id="03388-141">Palavras-chave e níveis CLR ETW</span><span class="sxs-lookup"><span data-stu-id="03388-141">CLR ETW Keywords and Levels</span></span>](clr-etw-keywords-and-levels.md)
- [<span data-ttu-id="03388-142">Eventos ETW no Common Language Runtime</span><span class="sxs-lookup"><span data-stu-id="03388-142">ETW Events in the Common Language Runtime</span></span>](etw-events-in-the-common-language-runtime.md)
