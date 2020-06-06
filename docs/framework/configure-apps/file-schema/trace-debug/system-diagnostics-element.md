---
title: <elemento> System. Diagnostics
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.diagnostics
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics
helpviewer_keywords:
- <system.diagnostics> element
- system.diagnostics element
ms.assetid: 3f348f42-fa72-4ff2-aa1c-bb9eecad4bb2
ms.openlocfilehash: 4f831592d7d178276b1625e1ef7d8512085342af
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153201"
---
# <a name="systemdiagnostics-element"></a><span data-ttu-id="f23e9-102">Elemento \<system.diagnostics></span><span class="sxs-lookup"><span data-stu-id="f23e9-102">\<system.diagnostics> Element</span></span>
<span data-ttu-id="f23e9-103">Especifica os ouvintes de rastreamento que coletam, armazenam e roteiam mensagens e o nível em que uma opção de rastreamento é definida.</span><span class="sxs-lookup"><span data-stu-id="f23e9-103">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;**\<system.diagnostics>**  
  
## <a name="syntax"></a><span data-ttu-id="f23e9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f23e9-104">Syntax</span></span>  
  
```xml  
<system.diagnostics>
</system.diagnostics>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f23e9-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="f23e9-105">Attributes and Elements</span></span>  
 <span data-ttu-id="f23e9-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="f23e9-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f23e9-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="f23e9-107">Attributes</span></span>  
 <span data-ttu-id="f23e9-108">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="f23e9-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f23e9-109">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="f23e9-109">Child Elements</span></span>  
  
|<span data-ttu-id="f23e9-110">Elemento</span><span class="sxs-lookup"><span data-stu-id="f23e9-110">Element</span></span>|<span data-ttu-id="f23e9-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="f23e9-111">Description</span></span>|  
|-------------|-----------------|  
|[\<assert>](assert-element.md)|<span data-ttu-id="f23e9-112">Especifica se uma caixa de mensagem deve ser exibida ao chamar o método <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>; também especifica o nome do arquivo no qual as mensagens serão gravadas.</span><span class="sxs-lookup"><span data-stu-id="f23e9-112">Specifies whether to display a message box when you call the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> method; also specifies the name of the file to write messages to.</span></span>|  
|[\<performanceCounters>](performancecounters-element.md)|<span data-ttu-id="f23e9-113">Especifica o tamanho da memória global compartilhada por contadores de desempenho.</span><span class="sxs-lookup"><span data-stu-id="f23e9-113">Specifies the size of the global memory shared by performance counters.</span></span>|  
|[\<sharedListeners>](sharedlisteners-element.md)|<span data-ttu-id="f23e9-114">Contém os ouvintes que podem ser referenciados por qualquer elemento de origem ou de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="f23e9-114">Contains listeners that any source or trace element can reference.</span></span> <span data-ttu-id="f23e9-115">Os ouvintes identificados como ouvintes compartilhados podem ser adicionados a fontes ou rastreamentos por nome.</span><span class="sxs-lookup"><span data-stu-id="f23e9-115">Listeners identified as shared listeners can be added to sources or traces by name.</span></span>|  
|[\<sources>](sources-element.md)|<span data-ttu-id="f23e9-116">Especifica fontes de rastreamento que iniciam mensagens de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="f23e9-116">Specifies trace sources that initiate tracing messages.</span></span>|  
|[\<switches>](switches-element.md)|<span data-ttu-id="f23e9-117">Contém opções de rastreamento e os níveis em que as opções de rastreamento são definidas.</span><span class="sxs-lookup"><span data-stu-id="f23e9-117">Contains trace switches and the levels where the trace switches are set.</span></span>|  
|[\<trace>](trace-element.md)|<span data-ttu-id="f23e9-118">Contém os ouvintes que coletam, armazenam e roteiam mensagens de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="f23e9-118">Contains listeners that collect, store, and route tracing messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f23e9-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="f23e9-119">Parent Elements</span></span>  
  
|<span data-ttu-id="f23e9-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="f23e9-120">Element</span></span>|<span data-ttu-id="f23e9-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="f23e9-121">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="f23e9-122">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f23e9-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="f23e9-123">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f23e9-123">Example</span></span>  
 <span data-ttu-id="f23e9-124">O exemplo a seguir mostra como inserir uma opção de rastreamento e um ouvinte de rastreamento dentro do **\<system.diagnostics>** elemento.</span><span class="sxs-lookup"><span data-stu-id="f23e9-124">The following example shows how to embed a trace switch and a trace listener inside the **\<system.diagnostics>** element.</span></span> <span data-ttu-id="f23e9-125">A `General` opção de rastreamento é definida para o <xref:System.Diagnostics.TraceLevel> nível.</span><span class="sxs-lookup"><span data-stu-id="f23e9-125">The `General` trace switch is set to the <xref:System.Diagnostics.TraceLevel> level.</span></span> <span data-ttu-id="f23e9-126">O ouvinte de rastreamento `myListener` cria um arquivo chamado `MyListener.log` e grava a saída no arquivo.</span><span class="sxs-lookup"><span data-stu-id="f23e9-126">The trace listener `myListener` creates a file called `MyListener.log` and writes the output to the file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f23e9-127">No .NET Framework versão 2.0, você pode usar o texto para especificar o valor de uma opção.</span><span class="sxs-lookup"><span data-stu-id="f23e9-127">In the .NET Framework version 2.0, you can use text to specify the value for a switch.</span></span> <span data-ttu-id="f23e9-128">Por exemplo, você pode especificar `true` para um <xref:System.Diagnostics.BooleanSwitch> ou usar o texto que representa um valor de enumeração, como `Error` para um <xref:System.Diagnostics.TraceSwitch> .</span><span class="sxs-lookup"><span data-stu-id="f23e9-128">For example, you can specify `true` for a <xref:System.Diagnostics.BooleanSwitch> or use the text representing an enumeration value such as `Error` for a <xref:System.Diagnostics.TraceSwitch>.</span></span> <span data-ttu-id="f23e9-129">A linha `<add name="myTraceSwitch" value="Error" />` é equivalente a `<add name="myTraceSwitch" value="1" />`.</span><span class="sxs-lookup"><span data-stu-id="f23e9-129">The line `<add name="myTraceSwitch" value="Error" />` is equivalent to `<add name="myTraceSwitch" value="1" />`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f23e9-130">Confira também</span><span class="sxs-lookup"><span data-stu-id="f23e9-130">See also</span></span>

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.Debug>
- [<span data-ttu-id="f23e9-131">Esquema de configurações de rastreamento e depuração</span><span class="sxs-lookup"><span data-stu-id="f23e9-131">Trace and Debug Settings Schema</span></span>](index.md)
