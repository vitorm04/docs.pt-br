---
title: Eventos ETW no Common Language Runtime
ms.date: 03/30/2017
helpviewer_keywords:
- CLR ETW events
- ETW, common language runtime
- ETW, CLR events
ms.assetid: 5bb9b6a2-7b57-4aea-8809-32b28bc73e88
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d59416ea2d9a2d7b001421271b9907bb3e84c086
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "44037666"
---
# <a name="etw-events-in-the-common-language-runtime"></a><span data-ttu-id="464bc-102">Eventos ETW no Common Language Runtime</span><span class="sxs-lookup"><span data-stu-id="464bc-102">ETW Events in the Common Language Runtime</span></span>
<span data-ttu-id="464bc-103">O CLR (Common Language Runtime) fornece informações úteis de diagnóstico ETW (rastreamento de eventos para Windows) por meio de uma grande variedade de eventos de depuração e criação de perfil.</span><span class="sxs-lookup"><span data-stu-id="464bc-103">The common language runtime (CLR) provides useful event tracing for Windows (ETW) diagnostic information through a large variety of debugging and profiling events.</span></span> <span data-ttu-id="464bc-104">Os eventos CLR ETW aproveitam o sistema de rastreamento ETW do Windows para ampliar o suporte existente de depuração e criação de perfil fornecido pelo Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="464bc-104">CLR ETW events leverage the Windows ETW tracing system to augment the existing profiling and debugging support provided by the common language runtime.</span></span>  
  
 <span data-ttu-id="464bc-105">Mais informações sobre o ETW estão disponíveis no artigo [Melhorar o ajuste de depuração e desempenho com o ETW](https://go.microsoft.com/fwlink/?LinkID=161142) no MSDN.</span><span class="sxs-lookup"><span data-stu-id="464bc-105">More information about ETW is available in the article [Improve Debugging and Performance Tuning with ETW](https://go.microsoft.com/fwlink/?LinkID=161142) on MSDN.</span></span> <span data-ttu-id="464bc-106">Informações sobre o XPerf podem ser encontradas na entrada [Windows Performance Toolkit – XPerf](https://go.microsoft.com/fwlink/?LinkID=161144) no blog NTDebugging.</span><span class="sxs-lookup"><span data-stu-id="464bc-106">Information about Xperf can be found in the entry [Windows Performance Toolkit - Xperf](https://go.microsoft.com/fwlink/?LinkID=161144) in the NTDebugging blog.</span></span>  
  
 <span data-ttu-id="464bc-107">O [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] ou posterior é necessário para todos os eventos descritos nos tópicos de eventos.</span><span class="sxs-lookup"><span data-stu-id="464bc-107">The [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] or later is required for all the events described in the event topics.</span></span> <span data-ttu-id="464bc-108">O sistema operacional Windows Vista é o cliente com suporte mínimo e o Windows Server 2008 é o servidor com suporte mínimo.</span><span class="sxs-lookup"><span data-stu-id="464bc-108">The Windows Vista operating system is the minimum supported client, and Windows Server 2008 is the minimum supported server.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="464bc-109">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="464bc-109">In This Section</span></span>  
 [<span data-ttu-id="464bc-110">Controlando o log no .NET Framework</span><span class="sxs-lookup"><span data-stu-id="464bc-110">Controlling .NET Framework Logging</span></span>](../../../docs/framework/performance/controlling-logging.md)  
 <span data-ttu-id="464bc-111">Descreve as ferramentas e os comandos para capturar e exibir eventos ETW.</span><span class="sxs-lookup"><span data-stu-id="464bc-111">Describes the tools and commands for capturing and viewing ETW events.</span></span>  
  
 [<span data-ttu-id="464bc-112">Provedores CLR ETW</span><span class="sxs-lookup"><span data-stu-id="464bc-112">CLR ETW Providers</span></span>](../../../docs/framework/performance/clr-etw-providers.md)  
 <span data-ttu-id="464bc-113">Fornece informações sobre o tempo de execução e os provedores de encerramento e como usá-los para a coleta de dados ETW.</span><span class="sxs-lookup"><span data-stu-id="464bc-113">Provides information about the runtime and rundown providers, and how you can use them for ETW data collection.</span></span>  
  
 [<span data-ttu-id="464bc-114">Palavras-chave e níveis CLR ETW</span><span class="sxs-lookup"><span data-stu-id="464bc-114">CLR ETW Keywords and Levels</span></span>](../../../docs/framework/performance/clr-etw-keywords-and-levels.md)  
 <span data-ttu-id="464bc-115">Descreve as palavras-chave para os provedores de Tempo de Execução e Encerramento que permitem a filtragem de eventos por categoria.</span><span class="sxs-lookup"><span data-stu-id="464bc-115">Describes the keywords for the Runtime and Rundown providers that enable the filtering of events by category.</span></span>  
  
 [<span data-ttu-id="464bc-116">Eventos de CLR ETW</span><span class="sxs-lookup"><span data-stu-id="464bc-116">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)  
 <span data-ttu-id="464bc-117">Fornece informações detalhadas sobre eventos CLR ETW, suas palavras-chave, níveis e dados de evento.</span><span class="sxs-lookup"><span data-stu-id="464bc-117">Provides detailed information about CLR ETW events, their keywords, levels, and event data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="464bc-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="464bc-118">See Also</span></span>  
 [<span data-ttu-id="464bc-119">Eventos ETW no .NET Framework</span><span class="sxs-lookup"><span data-stu-id="464bc-119">ETW Events in the .NET Framework</span></span>](../../../docs/framework/performance/etw-events.md)
