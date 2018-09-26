---
title: '&lt;System. Diagnostics&gt; elemento'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.diagnostics
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics
helpviewer_keywords:
- <system.diagnostics> element
- system.diagnostics element
ms.assetid: 3f348f42-fa72-4ff2-aa1c-bb9eecad4bb2
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 35fe167beb53c27aa511e08507415a26b1749ca2
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47193220"
---
# <a name="ltsystemdiagnosticsgt-element"></a><span data-ttu-id="b8ce5-102">&lt;System. Diagnostics&gt; elemento</span><span class="sxs-lookup"><span data-stu-id="b8ce5-102">&lt;system.diagnostics&gt; Element</span></span>
<span data-ttu-id="b8ce5-103">Especifica os ouvintes de rastreamento que coletam, armazenam e roteiam mensagens e o nível em que uma opção de rastreamento é definida.</span><span class="sxs-lookup"><span data-stu-id="b8ce5-103">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>  
  
 <span data-ttu-id="b8ce5-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="b8ce5-104">\<configuration></span></span>  
<span data-ttu-id="b8ce5-105">\<System. Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="b8ce5-105">\<system.diagnostics></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8ce5-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b8ce5-106">Syntax</span></span>  
  
```xml  
<system.diagnostics>   
</system.diagnostics>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b8ce5-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="b8ce5-107">Attributes and Elements</span></span>  
 <span data-ttu-id="b8ce5-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="b8ce5-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b8ce5-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="b8ce5-109">Attributes</span></span>  
 <span data-ttu-id="b8ce5-110">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="b8ce5-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b8ce5-111">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="b8ce5-111">Child Elements</span></span>  
  
|<span data-ttu-id="b8ce5-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="b8ce5-112">Element</span></span>|<span data-ttu-id="b8ce5-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="b8ce5-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b8ce5-114">\<assert></span><span class="sxs-lookup"><span data-stu-id="b8ce5-114">\<assert></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/assert-element.md)|<span data-ttu-id="b8ce5-115">Especifica se uma caixa de mensagem deve ser exibida ao chamar o método <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>; também especifica o nome do arquivo no qual as mensagens serão gravadas.</span><span class="sxs-lookup"><span data-stu-id="b8ce5-115">Specifies whether to display a message box when you call the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> method; also specifies the name of the file to write messages to.</span></span>|  
|[<span data-ttu-id="b8ce5-116">\<performanceCounters></span><span class="sxs-lookup"><span data-stu-id="b8ce5-116">\<performanceCounters></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/performancecounters-element.md)|<span data-ttu-id="b8ce5-117">Especifica o tamanho da memória global compartilhada por contadores de desempenho.</span><span class="sxs-lookup"><span data-stu-id="b8ce5-117">Specifies the size of the global memory shared by performance counters.</span></span>|  
|[<span data-ttu-id="b8ce5-118">\<sharedListeners></span><span class="sxs-lookup"><span data-stu-id="b8ce5-118">\<sharedListeners></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md)|<span data-ttu-id="b8ce5-119">Contém os ouvintes que podem ser referenciados por qualquer elemento de origem ou de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="b8ce5-119">Contains listeners that any source or trace element can reference.</span></span> <span data-ttu-id="b8ce5-120">Ouvintes identificados como ouvintes compartilhados podem ser adicionados à fontes ou rastreamentos por nome.</span><span class="sxs-lookup"><span data-stu-id="b8ce5-120">Listeners identified as shared listeners can be added to sources or traces by name.</span></span>|  
|[<span data-ttu-id="b8ce5-121">\<sources></span><span class="sxs-lookup"><span data-stu-id="b8ce5-121">\<sources></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sources-element.md)|<span data-ttu-id="b8ce5-122">Especifica as origens de rastreamento que iniciam as mensagens de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="b8ce5-122">Specifies trace sources that initiate tracing messages.</span></span>|  
|[<span data-ttu-id="b8ce5-123">\<switches></span><span class="sxs-lookup"><span data-stu-id="b8ce5-123">\<switches></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/switches-element.md)|<span data-ttu-id="b8ce5-124">Contém opções de rastreamento e os níveis de onde as opções de rastreamento são definidas.</span><span class="sxs-lookup"><span data-stu-id="b8ce5-124">Contains trace switches and the levels where the trace switches are set.</span></span>|  
|[<span data-ttu-id="b8ce5-125">\<trace></span><span class="sxs-lookup"><span data-stu-id="b8ce5-125">\<trace></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/trace-element.md)|<span data-ttu-id="b8ce5-126">Contém os ouvintes que coletam, armazenam e roteiam mensagens de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="b8ce5-126">Contains listeners that collect, store, and route tracing messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b8ce5-127">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="b8ce5-127">Parent Elements</span></span>  
  
|<span data-ttu-id="b8ce5-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="b8ce5-128">Element</span></span>|<span data-ttu-id="b8ce5-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="b8ce5-129">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="b8ce5-130">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b8ce5-130">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="b8ce5-131">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b8ce5-131">Example</span></span>  
 <span data-ttu-id="b8ce5-132">O exemplo a seguir mostra como inserir uma opção de rastreamento e um ouvinte de rastreamento dentro do  **\<System. Diagnostics >** elemento.</span><span class="sxs-lookup"><span data-stu-id="b8ce5-132">The following example shows how to embed a trace switch and a trace listener inside the **\<system.diagnostics>** element.</span></span> <span data-ttu-id="b8ce5-133">O `General` opção de rastreamento é definida como o <xref:System.Diagnostics.TraceLevel> nível.</span><span class="sxs-lookup"><span data-stu-id="b8ce5-133">The `General` trace switch is set to the <xref:System.Diagnostics.TraceLevel> level.</span></span> <span data-ttu-id="b8ce5-134">O ouvinte de rastreamento `myListener` cria um arquivo chamado `MyListener.log` e grava a saída para o arquivo.</span><span class="sxs-lookup"><span data-stu-id="b8ce5-134">The trace listener `myListener` creates a file called `MyListener.log` and writes the output to the file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b8ce5-135">No .NET Framework versão 2.0, você pode usar o texto para especificar o valor de uma opção.</span><span class="sxs-lookup"><span data-stu-id="b8ce5-135">In the .NET Framework version 2.0, you can use text to specify the value for a switch.</span></span> <span data-ttu-id="b8ce5-136">Por exemplo, você pode especificar `true` para um <xref:System.Diagnostics.BooleanSwitch> ou use o texto que representa um valor de enumeração como `Error` para um <xref:System.Diagnostics.TraceSwitch>.</span><span class="sxs-lookup"><span data-stu-id="b8ce5-136">For example, you can specify `true` for a <xref:System.Diagnostics.BooleanSwitch> or use the text representing an enumeration value such as `Error` for a <xref:System.Diagnostics.TraceSwitch>.</span></span> <span data-ttu-id="b8ce5-137">A linha `<add name="myTraceSwitch" value="Error" />` é equivalente a `<add name="myTraceSwitch" value="1" />`.</span><span class="sxs-lookup"><span data-stu-id="b8ce5-137">The line `<add name="myTraceSwitch" value="Error" />` is equivalent to `<add name="myTraceSwitch" value="1" />`.</span></span>  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <switches>  
         <add name="General" value="4" />  
      </switches>  
      <trace autoflush="true" indentsize="2">  
         <listeners>  
            <add name="myListener" type="System.Diagnostics.TextWriterTraceListener, System, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" initializeData="MyListener.log" traceOutputOptions="ProcessId, LogicalOperationStack, Timestamp, ThreadId, Callstack, DateTime" />  
         </listeners>  
      </trace>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b8ce5-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b8ce5-138">See Also</span></span>  
 <xref:System.Diagnostics.Trace>  
 <xref:System.Diagnostics.Debug>  
 [<span data-ttu-id="b8ce5-139">Esquema de configurações de rastreamento e depuração</span><span class="sxs-lookup"><span data-stu-id="b8ce5-139">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
