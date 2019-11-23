---
title: < elemento > System. Diagnostics
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.diagnostics
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics
helpviewer_keywords:
- <system.diagnostics> element
- system.diagnostics element
ms.assetid: 3f348f42-fa72-4ff2-aa1c-bb9eecad4bb2
ms.openlocfilehash: dc05c46cb1ba74baceaaeadc2959a6889faf19c9
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699191"
---
# <a name="systemdiagnostics-element"></a><span data-ttu-id="27385-102">\<elemento > System. Diagnostics</span><span class="sxs-lookup"><span data-stu-id="27385-102">\<system.diagnostics> Element</span></span>
<span data-ttu-id="27385-103">Especifica os ouvintes de rastreamento que coletam, armazenam e roteiam mensagens e o nível em que uma opção de rastreamento é definida.</span><span class="sxs-lookup"><span data-stu-id="27385-103">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>  
  
[<span data-ttu-id="27385-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="27385-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="27385-105">&nbsp;&nbsp; **\<System. diagnostics >**</span><span class="sxs-lookup"><span data-stu-id="27385-105">&nbsp;&nbsp;**\<system.diagnostics>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27385-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="27385-106">Syntax</span></span>  
  
```xml  
<system.diagnostics>   
</system.diagnostics>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="27385-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="27385-107">Attributes and Elements</span></span>  
 <span data-ttu-id="27385-108">As seções a seguir descrevem os atributos, bem como os elementos filhos e pais.</span><span class="sxs-lookup"><span data-stu-id="27385-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="27385-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="27385-109">Attributes</span></span>  
 <span data-ttu-id="27385-110">None.</span><span class="sxs-lookup"><span data-stu-id="27385-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="27385-111">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="27385-111">Child Elements</span></span>  
  
|<span data-ttu-id="27385-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="27385-112">Element</span></span>|<span data-ttu-id="27385-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="27385-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="27385-114">\<assert></span><span class="sxs-lookup"><span data-stu-id="27385-114">\<assert></span></span>](assert-element.md)|<span data-ttu-id="27385-115">Especifica se uma caixa de mensagem deve ser exibida ao chamar o método <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>; também especifica o nome do arquivo no qual as mensagens serão gravadas.</span><span class="sxs-lookup"><span data-stu-id="27385-115">Specifies whether to display a message box when you call the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> method; also specifies the name of the file to write messages to.</span></span>|  
|[<span data-ttu-id="27385-116">\<performanceCounters></span><span class="sxs-lookup"><span data-stu-id="27385-116">\<performanceCounters></span></span>](performancecounters-element.md)|<span data-ttu-id="27385-117">Especifica o tamanho da memória global compartilhada por contadores de desempenho.</span><span class="sxs-lookup"><span data-stu-id="27385-117">Specifies the size of the global memory shared by performance counters.</span></span>|  
|[<span data-ttu-id="27385-118">\<sharedListeners></span><span class="sxs-lookup"><span data-stu-id="27385-118">\<sharedListeners></span></span>](sharedlisteners-element.md)|<span data-ttu-id="27385-119">Contém os ouvintes que podem ser referenciados por qualquer elemento de origem ou de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="27385-119">Contains listeners that any source or trace element can reference.</span></span> <span data-ttu-id="27385-120">Os ouvintes identificados como ouvintes compartilhados podem ser adicionados a fontes ou rastreamentos por nome.</span><span class="sxs-lookup"><span data-stu-id="27385-120">Listeners identified as shared listeners can be added to sources or traces by name.</span></span>|  
|[<span data-ttu-id="27385-121">\<sources></span><span class="sxs-lookup"><span data-stu-id="27385-121">\<sources></span></span>](sources-element.md)|<span data-ttu-id="27385-122">Especifica fontes de rastreamento que iniciam mensagens de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="27385-122">Specifies trace sources that initiate tracing messages.</span></span>|  
|[<span data-ttu-id="27385-123">\<switches></span><span class="sxs-lookup"><span data-stu-id="27385-123">\<switches></span></span>](switches-element.md)|<span data-ttu-id="27385-124">Contém opções de rastreamento e os níveis em que as opções de rastreamento são definidas.</span><span class="sxs-lookup"><span data-stu-id="27385-124">Contains trace switches and the levels where the trace switches are set.</span></span>|  
|[<span data-ttu-id="27385-125">\<trace></span><span class="sxs-lookup"><span data-stu-id="27385-125">\<trace></span></span>](trace-element.md)|<span data-ttu-id="27385-126">Contém os ouvintes que coletam, armazenam e roteiam mensagens de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="27385-126">Contains listeners that collect, store, and route tracing messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="27385-127">Elementos Pai</span><span class="sxs-lookup"><span data-stu-id="27385-127">Parent Elements</span></span>  
  
|<span data-ttu-id="27385-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="27385-128">Element</span></span>|<span data-ttu-id="27385-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="27385-129">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="27385-130">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="27385-130">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="27385-131">{1&gt;Exemplo&lt;1}</span><span class="sxs-lookup"><span data-stu-id="27385-131">Example</span></span>  
 <span data-ttu-id="27385-132">O exemplo a seguir mostra como inserir uma opção de rastreamento e um ouvinte de rastreamento dentro do elemento **\<System. diagnostics >** .</span><span class="sxs-lookup"><span data-stu-id="27385-132">The following example shows how to embed a trace switch and a trace listener inside the **\<system.diagnostics>** element.</span></span> <span data-ttu-id="27385-133">A opção de rastreamento de `General` é definida como o nível de <xref:System.Diagnostics.TraceLevel>.</span><span class="sxs-lookup"><span data-stu-id="27385-133">The `General` trace switch is set to the <xref:System.Diagnostics.TraceLevel> level.</span></span> <span data-ttu-id="27385-134">O ouvinte de rastreamento `myListener` cria um arquivo chamado `MyListener.log` e grava a saída no arquivo.</span><span class="sxs-lookup"><span data-stu-id="27385-134">The trace listener `myListener` creates a file called `MyListener.log` and writes the output to the file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="27385-135">No .NET Framework versão 2.0, você pode usar o texto para especificar o valor de uma opção.</span><span class="sxs-lookup"><span data-stu-id="27385-135">In the .NET Framework version 2.0, you can use text to specify the value for a switch.</span></span> <span data-ttu-id="27385-136">Por exemplo, você pode especificar `true` para um <xref:System.Diagnostics.BooleanSwitch> ou usar o texto que representa um valor de enumeração, como `Error` para um <xref:System.Diagnostics.TraceSwitch>.</span><span class="sxs-lookup"><span data-stu-id="27385-136">For example, you can specify `true` for a <xref:System.Diagnostics.BooleanSwitch> or use the text representing an enumeration value such as `Error` for a <xref:System.Diagnostics.TraceSwitch>.</span></span> <span data-ttu-id="27385-137">A linha `<add name="myTraceSwitch" value="Error" />` é equivalente a `<add name="myTraceSwitch" value="1" />`.</span><span class="sxs-lookup"><span data-stu-id="27385-137">The line `<add name="myTraceSwitch" value="Error" />` is equivalent to `<add name="myTraceSwitch" value="1" />`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="27385-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="27385-138">See also</span></span>

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.Debug>
- [<span data-ttu-id="27385-139">Esquema de configurações de rastreamento e depuração</span><span class="sxs-lookup"><span data-stu-id="27385-139">Trace and Debug Settings Schema</span></span>](index.md)
