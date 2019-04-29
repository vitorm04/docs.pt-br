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
ms.openlocfilehash: cb7520518497b244be8be3751ca8a3063a02717a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61788005"
---
# <a name="clr-etw-events"></a><span data-ttu-id="a306f-102">Eventos ETW no CLR</span><span class="sxs-lookup"><span data-stu-id="a306f-102">CLR ETW Events</span></span>
<span data-ttu-id="a306f-103">Os tópicos desta seção descrevem os eventos ETW (rastreamento de eventos para Windows).</span><span class="sxs-lookup"><span data-stu-id="a306f-103">The topics in this section describe event tracing for Windows (ETW) events.</span></span> <span data-ttu-id="a306f-104">Cada evento tem uma palavra-chave e um nível associados, que são descritos no tópico [Palavras-chave e níveis CLR ETW](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).</span><span class="sxs-lookup"><span data-stu-id="a306f-104">Each event has an associated keyword and level, which are described in the [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md) topic.</span></span> <span data-ttu-id="a306f-105">O CLR tem dois provedores para os eventos:</span><span class="sxs-lookup"><span data-stu-id="a306f-105">The CLR has two providers for the events:</span></span>  
  
- <span data-ttu-id="a306f-106">O provedor de tempo de execução, que aciona eventos, dependendo de quais palavras-chave (categorias de eventos) são habilitadas.</span><span class="sxs-lookup"><span data-stu-id="a306f-106">The runtime provider, which raises events depending on which keywords (categories of events) are enabled.</span></span> <span data-ttu-id="a306f-107">O GUID do provedor de tempo de execução CLR é e13c0d23-ccbc-4e12-931b-d9cc2eee27e4.</span><span class="sxs-lookup"><span data-stu-id="a306f-107">The CLR runtime provider GUID is e13c0d23-ccbc-4e12-931b-d9cc2eee27e4.</span></span>  
  
- <span data-ttu-id="a306f-108">O provedor de encerramento, que tem usos de finalidade especial.</span><span class="sxs-lookup"><span data-stu-id="a306f-108">The rundown provider, which has special-purpose uses.</span></span> <span data-ttu-id="a306f-109">O GUID do provedor de encerramento CLR é a669021c-c450-4609-a035-5af59af4df18.</span><span class="sxs-lookup"><span data-stu-id="a306f-109">The CLR rundown provider GUID is a669021c-c450-4609-a035-5af59af4df18.</span></span>  
  
 <span data-ttu-id="a306f-110">Para obter mais informações sobre os provedores, consulte [Provedores CLR ETW](../../../docs/framework/performance/clr-etw-providers.md).</span><span class="sxs-lookup"><span data-stu-id="a306f-110">For more information about the providers, see [CLR ETW Providers](../../../docs/framework/performance/clr-etw-providers.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a306f-111">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="a306f-111">In This Section</span></span>  
 [<span data-ttu-id="a306f-112">Eventos de informações de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="a306f-112">Runtime Information Events</span></span>](../../../docs/framework/performance/runtime-information-etw-events.md)  
 <span data-ttu-id="a306f-113">Captura informações sobre o tempo de execução, incluindo a SKU, o número de versão, a maneira pela qual o tempo de execução foi ativado, os parâmetros de linha de comando com os quais ele foi iniciado, o GUID (se aplicável) e outras informações relevantes.</span><span class="sxs-lookup"><span data-stu-id="a306f-113">Captures information about the runtime, including the SKU, version number, the manner in which the runtime was activated, the command-line parameters it was started with, the GUID (if applicable), and other relevant information.</span></span>  
  
 [<span data-ttu-id="a306f-114">Evento Exception Thrown_V1</span><span class="sxs-lookup"><span data-stu-id="a306f-114">Exception Thrown_V1 Event</span></span>](../../../docs/framework/performance/exception-thrown-v1-etw-event.md)  
 <span data-ttu-id="a306f-115">Captura informações sobre as exceções geradas.</span><span class="sxs-lookup"><span data-stu-id="a306f-115">Captures information about exceptions that are thrown.</span></span>  
  
 [<span data-ttu-id="a306f-116">Eventos de contenção</span><span class="sxs-lookup"><span data-stu-id="a306f-116">Contention Events</span></span>](../../../docs/framework/performance/contention-etw-events.md)  
 <span data-ttu-id="a306f-117">Captura informações sobre a contenção de bloqueios do monitor ou bloqueios nativos usados pelo tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="a306f-117">Captures information about contention for monitor locks or native locks that the runtime uses.</span></span>  
  
 [<span data-ttu-id="a306f-118">Eventos de pool de threads</span><span class="sxs-lookup"><span data-stu-id="a306f-118">Thread Pool Events</span></span>](../../../docs/framework/performance/thread-pool-etw-events.md)  
 <span data-ttu-id="a306f-119">Captura informações sobre pools de threads de trabalho e pools de threads de E/S.</span><span class="sxs-lookup"><span data-stu-id="a306f-119">Captures information about worker thread pools and I/O thread pools.</span></span>  
  
 [<span data-ttu-id="a306f-120">Eventos de carregador</span><span class="sxs-lookup"><span data-stu-id="a306f-120">Loader Events</span></span>](../../../docs/framework/performance/loader-etw-events.md)  
 <span data-ttu-id="a306f-121">Captura informações sobre o carregamento e descarregamento de domínios do aplicativo, assemblies e módulos.</span><span class="sxs-lookup"><span data-stu-id="a306f-121">Captures information about loading and unloading application domains, assemblies, and modules.</span></span>  
  
 [<span data-ttu-id="a306f-122">Eventos de método</span><span class="sxs-lookup"><span data-stu-id="a306f-122">Method Events</span></span>](../../../docs/framework/performance/method-etw-events.md)  
 <span data-ttu-id="a306f-123">Captura informações sobre métodos CLR para a resolução de símbolo.</span><span class="sxs-lookup"><span data-stu-id="a306f-123">Captures information about CLR methods for symbol resolution.</span></span>  
  
 [<span data-ttu-id="a306f-124">Eventos de coleta de lixo</span><span class="sxs-lookup"><span data-stu-id="a306f-124">Garbage Collection Events</span></span>](../../../docs/framework/performance/garbage-collection-etw-events.md)  
 <span data-ttu-id="a306f-125">Captura informações referentes à coleta de lixo, para ajudar no diagnóstico e na depuração.</span><span class="sxs-lookup"><span data-stu-id="a306f-125">Captures information pertaining to garbage collection, to help in diagnostics and debugging.</span></span>  
  
 [<span data-ttu-id="a306f-126">Eventos de rastreamento JIT</span><span class="sxs-lookup"><span data-stu-id="a306f-126">JIT Tracing Events</span></span>](../../../docs/framework/performance/jit-tracing-etw-events.md)  
 <span data-ttu-id="a306f-127">Captura informações sobre chamadas inlining e tail JIT (Just-In-Time).</span><span class="sxs-lookup"><span data-stu-id="a306f-127">Captures information about just-in-time (JIT) inlining and tail calls.</span></span>  
  
 [<span data-ttu-id="a306f-128">Eventos de interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="a306f-128">Interop Events</span></span>](../../../docs/framework/performance/interop-etw-events.md)  
 <span data-ttu-id="a306f-129">Captura informações sobre a geração e o cache de stub da MSIL (Microsoft Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="a306f-129">Captures information about Microsoft intermediate language (MSIL) stub generation and caching.</span></span>  
  
 [<span data-ttu-id="a306f-130">Eventos de ARM</span><span class="sxs-lookup"><span data-stu-id="a306f-130">ARM Events</span></span>](../../../docs/framework/performance/application-domain-resource-monitoring-arm-etw-events.md)  
 <span data-ttu-id="a306f-131">Captura informações de diagnóstico detalhadas sobre o estado de um domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a306f-131">Captures detailed diagnostic information about the state of an application domain.</span></span>  
  
 [<span data-ttu-id="a306f-132">Eventos de segurança</span><span class="sxs-lookup"><span data-stu-id="a306f-132">Security Events</span></span>](../../../docs/framework/performance/security-etw-events.md)  
 <span data-ttu-id="a306f-133">Captura informações sobre o nome forte e a verificação do Authenticode.</span><span class="sxs-lookup"><span data-stu-id="a306f-133">Captures information about strong name and Authenticode verification.</span></span>  
  
 [<span data-ttu-id="a306f-134">Evento de pilha</span><span class="sxs-lookup"><span data-stu-id="a306f-134">Stack Event</span></span>](../../../docs/framework/performance/stack-etw-event.md)  
 <span data-ttu-id="a306f-135">Captura informações que são usadas com outros eventos para gerar rastreamentos de pilha depois que um evento é acionado.</span><span class="sxs-lookup"><span data-stu-id="a306f-135">Captures information that is used with other events to generate stack traces after an event is raised.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a306f-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a306f-136">See also</span></span>

- [<span data-ttu-id="a306f-137">Melhorar a depuração e ajuste de desempenho com o ETW</span><span class="sxs-lookup"><span data-stu-id="a306f-137">Improve Debugging And Performance Tuning With ETW</span></span>](https://go.microsoft.com/fwlink/?LinkId=179696)
- [<span data-ttu-id="a306f-138">Blog de desempenho do Windows</span><span class="sxs-lookup"><span data-stu-id="a306f-138">Windows Performance Blog</span></span>](https://go.microsoft.com/fwlink/?LinkId=179509)
- [<span data-ttu-id="a306f-139">Controlando o log no .NET Framework</span><span class="sxs-lookup"><span data-stu-id="a306f-139">Controlling .NET Framework Logging</span></span>](../../../docs/framework/performance/controlling-logging.md)
- [<span data-ttu-id="a306f-140">Provedores CLR ETW</span><span class="sxs-lookup"><span data-stu-id="a306f-140">CLR ETW Providers</span></span>](../../../docs/framework/performance/clr-etw-providers.md)
- [<span data-ttu-id="a306f-141">Palavras-chave e níveis CLR ETW</span><span class="sxs-lookup"><span data-stu-id="a306f-141">CLR ETW Keywords and Levels</span></span>](../../../docs/framework/performance/clr-etw-keywords-and-levels.md)
- [<span data-ttu-id="a306f-142">Eventos ETW no Common Language Runtime</span><span class="sxs-lookup"><span data-stu-id="a306f-142">ETW Events in the Common Language Runtime</span></span>](../../../docs/framework/performance/etw-events-in-the-common-language-runtime.md)
