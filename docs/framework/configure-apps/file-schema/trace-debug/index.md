---
title: Esquema de configurações de rastreamento e depuração
ms.date: 03/30/2017
helpviewer_keywords:
- tracing [.NET Framework], trace and debug settings schema
- configuration schema [.NET Framework], trace and debug settings
- configuration settings [.NET Framework], tracing
- schema configuration settings
- configuration settings [.NET Framework], debugging
- trace listeners, trace and debug settings schema
- configuration sections [.NET Framework]
- elements [.NET Framework], trace and debug settings
ms.assetid: 277ca5f6-e1c4-41b6-a47f-3a67ce5b94ac
ms.openlocfilehash: 037d08b33e9aa6a64d236b36ebcf821b604b03df
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "69927127"
---
# <a name="trace-and-debug-settings-schema"></a><span data-ttu-id="249a6-102">Esquema de configurações de rastreamento e depuração</span><span class="sxs-lookup"><span data-stu-id="249a6-102">Trace and Debug Settings Schema</span></span>
<span data-ttu-id="249a6-103">As configurações de rastreamento e depuração especificam ouvintes de rastreamento que coletam, armazenam e roteiam mensagens e o nível em que uma opção de rastreamento é definida.</span><span class="sxs-lookup"><span data-stu-id="249a6-103">Trace and debug settings specify trace listeners that collect, store, and route messages, and the level where a trace switch is set.</span></span>  
  
 <span data-ttu-id="249a6-104">A tabela a seguir descreve a função de cada elemento de configurações de rastreamento e depuração.</span><span class="sxs-lookup"><span data-stu-id="249a6-104">The following table describes the function of each trace and debug settings element.</span></span>  
  
|<span data-ttu-id="249a6-105">Elemento</span><span class="sxs-lookup"><span data-stu-id="249a6-105">Element</span></span>|<span data-ttu-id="249a6-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="249a6-106">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-element-for-listeners-for-source.md)|<span data-ttu-id="249a6-107">Adiciona um ouvinte na coleção `Listeners` de uma origem de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="249a6-107">Adds a listener to the `Listeners` collection for a trace source.</span></span>|  
|[\<add>](add-element-for-listeners-for-trace.md)|<span data-ttu-id="249a6-108">Adiciona um ouvinte na coleção `Listeners`.</span><span class="sxs-lookup"><span data-stu-id="249a6-108">Adds a listener to the `Listeners` collection.</span></span>|  
|[\<add>](add-element-for-sharedlisteners.md)|<span data-ttu-id="249a6-109">Adiciona um ouvinte na coleção `sharedListeners`.</span><span class="sxs-lookup"><span data-stu-id="249a6-109">Adds a listener to the `sharedListeners` collection.</span></span>|  
|[\<add>](add-element-for-switches.md)|<span data-ttu-id="249a6-110">Especifica o nível em que uma opção de rastreamento é definida.</span><span class="sxs-lookup"><span data-stu-id="249a6-110">Specifies the level where a trace switch is set.</span></span>|  
|[\<assert>](assert-element.md)|<span data-ttu-id="249a6-111">Especifica se uma caixa de mensagem deve ser exibida ao chamar o método <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>; também especifica o nome do arquivo no qual as mensagens serão gravadas.</span><span class="sxs-lookup"><span data-stu-id="249a6-111">Specifies whether to display a message box when you call the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> method; also specifies the name of the file to write messages to.</span></span>|  
|[\<clear>](clear-element-for-listeners-for-source.md)|<span data-ttu-id="249a6-112">Limpa a coleção `Listeners` de uma origem de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="249a6-112">Clears the `Listeners` collection for a trace source.</span></span>|  
|[\<clear>](clear-element-for-listeners-for-trace.md)|<span data-ttu-id="249a6-113">Limpa a coleção `Listeners` do rastreamento.</span><span class="sxs-lookup"><span data-stu-id="249a6-113">Clears the `Listeners` collection for trace.</span></span>|  
|[\<filter>](filter-element-for-add-for-listeners-for-source.md)|<span data-ttu-id="249a6-114">Adiciona um filtro a um ouvinte na coleção `Listeners` de uma origem de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="249a6-114">Adds a filter to a listener in the `Listeners` collection for a trace source.</span></span>|  
|[\<filter>](filter-element-for-add-for-listeners-for-trace.md)|<span data-ttu-id="249a6-115">Adiciona um filtro a um ouvinte na coleção `Listeners` do rastreamento.</span><span class="sxs-lookup"><span data-stu-id="249a6-115">Adds a filter to a listener in the `Listeners` collection for trace.</span></span>|  
|[\<filter>](filter-element-for-add-for-sharedlisteners.md)|<span data-ttu-id="249a6-116">Adiciona um filtro a um ouvinte na coleção `sharedListeners`.</span><span class="sxs-lookup"><span data-stu-id="249a6-116">Adds a filter to a listener in the `sharedListeners` collection.</span></span>|  
|[\<listeners>](listeners-element-for-source.md)|<span data-ttu-id="249a6-117">Especifica os ouvintes da coleção `Listeners` de uma origem de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="249a6-117">Specifies listeners for the `Listeners` collection for a trace source.</span></span>|  
|[\<listeners>](listeners-element-for-trace.md)|<span data-ttu-id="249a6-118">Especifica os ouvintes da coleção `Listeners` do rastreamento.</span><span class="sxs-lookup"><span data-stu-id="249a6-118">Specifies listeners for the `Listeners` collection for trace.</span></span>|  
|[\<performanceCounters>](performancecounters-element.md)|<span data-ttu-id="249a6-119">Especifica o tamanho da memória global compartilhada por contadores de desempenho.</span><span class="sxs-lookup"><span data-stu-id="249a6-119">Specifies the size of the global memory shared by performance counters.</span></span>|  
|[\<remove>](remove-element-for-listeners-for-trace.md)|<span data-ttu-id="249a6-120">Remove um ouvinte da coleção `Listeners` do rastreamento.</span><span class="sxs-lookup"><span data-stu-id="249a6-120">Removes a listener from the `Listeners` collection for trace.</span></span>|  
|[\<remove>](remove-element-for-listeners-for-source.md)|<span data-ttu-id="249a6-121">Remove um ouvinte da coleção `Listeners` de uma origem de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="249a6-121">Removes a listener from the `Listeners` collection for a trace source.</span></span>|  
|[\<sharedListeners>](sharedlisteners-element.md)|<span data-ttu-id="249a6-122">Contém os ouvintes que podem ser referenciados por qualquer elemento de origem ou de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="249a6-122">Contains listeners that any source or trace element can reference.</span></span>|  
|[\<sources>](sources-element.md)|<span data-ttu-id="249a6-123">Contém as origens de rastreamento que iniciam as mensagens de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="249a6-123">Contains trace sources that initiate tracing messages.</span></span>|  
|[\<source>](source-element.md)|<span data-ttu-id="249a6-124">Especifica uma origem de rastreamento que inicia as mensagens de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="249a6-124">Specifies a trace source that initiates tracing messages.</span></span>|  
|[\<switches>](switches-element.md)|<span data-ttu-id="249a6-125">Contém opções de rastreamento e o nível em que as opções de rastreamento são definidas.</span><span class="sxs-lookup"><span data-stu-id="249a6-125">Contains trace switches and the level where the trace switches are set.</span></span>|  
|[\<system.diagnostics>](system-diagnostics-element.md)|<span data-ttu-id="249a6-126">Especifica os ouvintes de rastreamento que coletam, armazenam e roteiam mensagens e o nível em que uma opção de rastreamento é definida.</span><span class="sxs-lookup"><span data-stu-id="249a6-126">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|[\<trace>](trace-element.md)|<span data-ttu-id="249a6-127">Contém os ouvintes que coletam, armazenam e roteiam mensagens de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="249a6-127">Contains listeners that collect, store, and route tracing messages.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="249a6-128">Confira também</span><span class="sxs-lookup"><span data-stu-id="249a6-128">See also</span></span>

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.Debug>
- [<span data-ttu-id="249a6-129">Esquema do arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="249a6-129">Configuration File Schema</span></span>](../index.md)
