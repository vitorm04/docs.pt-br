---
title: Eventos ETW no Common Language Runtime
description: Leia um resumo e exiba links relacionados a eventos de ETW (rastreamento de eventos para Windows) no Common Language Runtime (CLR).
ms.date: 03/30/2017
helpviewer_keywords:
- CLR ETW events
- ETW, common language runtime
- ETW, CLR events
ms.assetid: 5bb9b6a2-7b57-4aea-8809-32b28bc73e88
ms.openlocfilehash: aa422dcb7efbc0f6f7f09e09a6c9e44b40ada86b
ms.sourcegitcommit: 0fa2b7b658bf137e813a7f4d09589d64c148ebf5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/14/2020
ms.locfileid: "86309476"
---
# <a name="etw-events-in-the-common-language-runtime"></a><span data-ttu-id="051fc-103">Eventos ETW no Common Language Runtime</span><span class="sxs-lookup"><span data-stu-id="051fc-103">ETW Events in the Common Language Runtime</span></span>
<span data-ttu-id="051fc-104">O CLR (Common Language Runtime) fornece informações úteis de diagnóstico ETW (rastreamento de eventos para Windows) por meio de uma grande variedade de eventos de depuração e criação de perfil.</span><span class="sxs-lookup"><span data-stu-id="051fc-104">The common language runtime (CLR) provides useful event tracing for Windows (ETW) diagnostic information through a large variety of debugging and profiling events.</span></span> <span data-ttu-id="051fc-105">Os eventos CLR ETW aproveitam o sistema de rastreamento ETW do Windows para ampliar o suporte existente de depuração e criação de perfil fornecido pelo Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="051fc-105">CLR ETW events leverage the Windows ETW tracing system to augment the existing profiling and debugging support provided by the common language runtime.</span></span>  
  
 <span data-ttu-id="051fc-106">Mais informações sobre o ETW estão disponíveis no artigo [melhorar a depuração e o ajuste de desempenho com o ETW](https://docs.microsoft.com/archive/msdn-magazine/2007/april/event-tracing-improve-debugging-and-performance-tuning-with-etw) .</span><span class="sxs-lookup"><span data-stu-id="051fc-106">More information about ETW is available in the [Improve Debugging and Performance Tuning with ETW](https://docs.microsoft.com/archive/msdn-magazine/2007/april/event-tracing-improve-debugging-and-performance-tuning-with-etw) article.</span></span> <span data-ttu-id="051fc-107">Informações sobre o XPerf podem ser encontradas na entrada [Windows Performance Toolkit – XPerf](https://docs.microsoft.com/archive/blogs/ntdebugging/windows-performance-toolkit-xperf) no blog NTDebugging.</span><span class="sxs-lookup"><span data-stu-id="051fc-107">Information about Xperf can be found in the entry [Windows Performance Toolkit - Xperf](https://docs.microsoft.com/archive/blogs/ntdebugging/windows-performance-toolkit-xperf) in the NTDebugging blog.</span></span>  
  
 <span data-ttu-id="051fc-108">O .NET Framework 4 ou posterior é necessário para todos os eventos descritos nos tópicos de evento.</span><span class="sxs-lookup"><span data-stu-id="051fc-108">The .NET Framework 4 or later is required for all the events described in the event topics.</span></span> <span data-ttu-id="051fc-109">O sistema operacional Windows Vista é o cliente com suporte mínimo e o Windows Server 2008 é o servidor com suporte mínimo.</span><span class="sxs-lookup"><span data-stu-id="051fc-109">The Windows Vista operating system is the minimum supported client, and Windows Server 2008 is the minimum supported server.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="051fc-110">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="051fc-110">In This Section</span></span>  
 [<span data-ttu-id="051fc-111">Controlando o registro em log no .NET Framework</span><span class="sxs-lookup"><span data-stu-id="051fc-111">Controlling .NET Framework Logging</span></span>](controlling-logging.md)  
 <span data-ttu-id="051fc-112">Descreve as ferramentas e os comandos para capturar e exibir eventos ETW.</span><span class="sxs-lookup"><span data-stu-id="051fc-112">Describes the tools and commands for capturing and viewing ETW events.</span></span>  
  
 [<span data-ttu-id="051fc-113">Provedores ETW no CLR</span><span class="sxs-lookup"><span data-stu-id="051fc-113">CLR ETW Providers</span></span>](clr-etw-providers.md)  
 <span data-ttu-id="051fc-114">Fornece informações sobre o runtime e os provedores de encerramento e como usá-los para a coleta de dados ETW.</span><span class="sxs-lookup"><span data-stu-id="051fc-114">Provides information about the runtime and rundown providers, and how you can use them for ETW data collection.</span></span>  
  
 [<span data-ttu-id="051fc-115">Palavras-chave e níveis ETW no CLR</span><span class="sxs-lookup"><span data-stu-id="051fc-115">CLR ETW Keywords and Levels</span></span>](clr-etw-keywords-and-levels.md)  
 <span data-ttu-id="051fc-116">Descreve as palavras-chave para os provedores de Runtime e Encerramento que permitem a filtragem de eventos por categoria.</span><span class="sxs-lookup"><span data-stu-id="051fc-116">Describes the keywords for the Runtime and Rundown providers that enable the filtering of events by category.</span></span>  
  
 [<span data-ttu-id="051fc-117">Eventos ETW no CLR</span><span class="sxs-lookup"><span data-stu-id="051fc-117">CLR ETW Events</span></span>](clr-etw-events.md)  
 <span data-ttu-id="051fc-118">Fornece informações detalhadas sobre eventos CLR ETW, suas palavras-chave, níveis e dados de evento.</span><span class="sxs-lookup"><span data-stu-id="051fc-118">Provides detailed information about CLR ETW events, their keywords, levels, and event data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="051fc-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="051fc-119">See also</span></span>

- [<span data-ttu-id="051fc-120">Eventos ETW no .NET Framework</span><span class="sxs-lookup"><span data-stu-id="051fc-120">ETW Events in the .NET Framework</span></span>](etw-events.md)
