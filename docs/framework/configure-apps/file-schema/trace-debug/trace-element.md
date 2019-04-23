---
title: Elemento <trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace
- http://schemas.microsoft.com/.NetConfiguration/v2.0#trace
helpviewer_keywords:
- <trace> element
- listeners
- trace element
- trace listener, <trace> element
ms.assetid: 7931c942-63c1-47c3-a045-9d9de3cacdbf
ms.openlocfilehash: 5faf352dce2a459a999b3cf54209f6bd9793bde0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59073787"
---
# <a name="trace-element"></a><span data-ttu-id="61b08-102">\<rastreamento > elemento</span><span class="sxs-lookup"><span data-stu-id="61b08-102">\<trace> Element</span></span>
<span data-ttu-id="61b08-103">Contém os ouvintes que coletam, armazenam e roteiam mensagens de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="61b08-103">Contains listeners that collect, store, and route tracing messages.</span></span>  
  
 <span data-ttu-id="61b08-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="61b08-104">\<configuration></span></span>  
<span data-ttu-id="61b08-105">\<system.diagnostics></span><span class="sxs-lookup"><span data-stu-id="61b08-105">\<system.diagnostics></span></span>  
<span data-ttu-id="61b08-106">\<trace></span><span class="sxs-lookup"><span data-stu-id="61b08-106">\<trace></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61b08-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="61b08-107">Syntax</span></span>  
  
```xml  
<trace autoflush="true|false"   
       indentsize="indent value"  
       useGlobalLock="true| false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="61b08-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="61b08-108">Attributes and Elements</span></span>  
 <span data-ttu-id="61b08-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="61b08-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="61b08-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="61b08-110">Attributes</span></span>  
  
|<span data-ttu-id="61b08-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="61b08-111">Attribute</span></span>|<span data-ttu-id="61b08-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="61b08-112">Description</span></span>|  
|---------------|-----------------|  
|`autoflush`|<span data-ttu-id="61b08-113">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="61b08-113">Optional attribute.</span></span><br /><br /> <span data-ttu-id="61b08-114">Especifica se os ouvintes de rastreamento automaticamente liberar o buffer de saída após cada operação de gravação.</span><span class="sxs-lookup"><span data-stu-id="61b08-114">Specifies whether the trace listeners automatically flush the output buffer after every write operation.</span></span>|  
|`indentsize`|<span data-ttu-id="61b08-115">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="61b08-115">Optional attribute.</span></span><br /><br /> <span data-ttu-id="61b08-116">Especifica o número de espaços para recuar.</span><span class="sxs-lookup"><span data-stu-id="61b08-116">Specifies the number of spaces to indent.</span></span>|  
|`useGlobalLock`|<span data-ttu-id="61b08-117">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="61b08-117">Optional attribute.</span></span><br /><br /> <span data-ttu-id="61b08-118">Indica se o bloqueio global deve ser usado.</span><span class="sxs-lookup"><span data-stu-id="61b08-118">Indicates whether the global lock should be used.</span></span>|  
  
## <a name="autoflush-attribute"></a><span data-ttu-id="61b08-119">autoflush atributo</span><span class="sxs-lookup"><span data-stu-id="61b08-119">autoflush Attribute</span></span>  
  
|<span data-ttu-id="61b08-120">Valor</span><span class="sxs-lookup"><span data-stu-id="61b08-120">Value</span></span>|<span data-ttu-id="61b08-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="61b08-121">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="61b08-122">Não libera o buffer de saída automaticamente.</span><span class="sxs-lookup"><span data-stu-id="61b08-122">Does not automatically flush the output buffer.</span></span> <span data-ttu-id="61b08-123">Esse é o padrão.</span><span class="sxs-lookup"><span data-stu-id="61b08-123">This is the default.</span></span>|  
|`true`|<span data-ttu-id="61b08-124">Automaticamente libera o buffer de saída.</span><span class="sxs-lookup"><span data-stu-id="61b08-124">Automatically flushes the output buffer.</span></span>|  
  
## <a name="usegloballock-attribute"></a><span data-ttu-id="61b08-125">useGlobalLock atributo</span><span class="sxs-lookup"><span data-stu-id="61b08-125">useGlobalLock Attribute</span></span>  
  
|<span data-ttu-id="61b08-126">Valor</span><span class="sxs-lookup"><span data-stu-id="61b08-126">Value</span></span>|<span data-ttu-id="61b08-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="61b08-127">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="61b08-128">Não usa o bloqueio global, se o ouvinte é thread-safe; Caso contrário, usará o bloqueio global.</span><span class="sxs-lookup"><span data-stu-id="61b08-128">Does not use the global lock if the listener is thread safe; otherwise, uses the global lock.</span></span>|  
|`true`|<span data-ttu-id="61b08-129">Usa o bloqueio global, independentemente se o ouvinte é thread-safe.</span><span class="sxs-lookup"><span data-stu-id="61b08-129">Uses the global lock regardless of whether the listener is thread safe.</span></span> <span data-ttu-id="61b08-130">Esse é o padrão.</span><span class="sxs-lookup"><span data-stu-id="61b08-130">This is the default.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="61b08-131">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="61b08-131">Child Elements</span></span>  
  
|<span data-ttu-id="61b08-132">Elemento</span><span class="sxs-lookup"><span data-stu-id="61b08-132">Element</span></span>|<span data-ttu-id="61b08-133">Descrição</span><span class="sxs-lookup"><span data-stu-id="61b08-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="61b08-134">\<listeners></span><span class="sxs-lookup"><span data-stu-id="61b08-134">\<listeners></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/listeners-element-for-trace.md)|<span data-ttu-id="61b08-135">Especifica um ouvinte que coleta, armazena e encaminha mensagens.</span><span class="sxs-lookup"><span data-stu-id="61b08-135">Specifies a listener that collects, stores, and routes messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="61b08-136">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="61b08-136">Parent Elements</span></span>  
  
|<span data-ttu-id="61b08-137">Elemento</span><span class="sxs-lookup"><span data-stu-id="61b08-137">Element</span></span>|<span data-ttu-id="61b08-138">Descrição</span><span class="sxs-lookup"><span data-stu-id="61b08-138">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="61b08-139">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="61b08-139">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="61b08-140">Especifica os ouvintes de rastreamento que coletam, armazenam e roteiam mensagens e o nível em que uma opção de rastreamento é definida.</span><span class="sxs-lookup"><span data-stu-id="61b08-140">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="61b08-141">Exemplo</span><span class="sxs-lookup"><span data-stu-id="61b08-141">Example</span></span>  
 <span data-ttu-id="61b08-142">O exemplo a seguir mostra como usar o `<trace>` elemento para adicionar o ouvinte `MyListener` para o `Listeners` coleção.</span><span class="sxs-lookup"><span data-stu-id="61b08-142">The following example shows how to use the `<trace>` element to add the listener `MyListener` to the `Listeners` collection.</span></span> <span data-ttu-id="61b08-143">`MyListener` cria um arquivo chamado `MyListener.log` e grava a saída para o arquivo.</span><span class="sxs-lookup"><span data-stu-id="61b08-143">`MyListener` creates a file that is named `MyListener.log` and writes the output to the file.</span></span> <span data-ttu-id="61b08-144">O `useGlobalLock` atributo é definido como `false`, que faz com que o bloqueio global não deve ser usado se o ouvinte de rastreamento é thread-safe.</span><span class="sxs-lookup"><span data-stu-id="61b08-144">The `useGlobalLock` attribute is set to `false`, which causes the global lock not to be used if the trace listener is thread safe.</span></span> <span data-ttu-id="61b08-145">O `autoflush` atributo é definido como `true`, que faz com que o ouvinte de rastreamento gravar o arquivo independentemente se o <xref:System.Diagnostics.Trace.Flush%2A?displayProperty=nameWithType> método é chamado.</span><span class="sxs-lookup"><span data-stu-id="61b08-145">The `autoflush` attribute is set to `true`, which causes the trace listener to write to the file regardless of whether the <xref:System.Diagnostics.Trace.Flush%2A?displayProperty=nameWithType> method is called.</span></span> <span data-ttu-id="61b08-146">O `indentsize` atributo é definido como 0 (zero), que faz com que o ouvinte recuar os espaços de zero quando o <xref:System.Diagnostics.Trace.Indent%2A?displayProperty=nameWithType> método é chamado.</span><span class="sxs-lookup"><span data-stu-id="61b08-146">The `indentsize` attribute is set to 0 (zero), which causes the listener to indent zero spaces when the <xref:System.Diagnostics.Trace.Indent%2A?displayProperty=nameWithType> method is called.</span></span>  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <trace useGlobalLock="false" autoflush="true" indentsize="0">  
         <listeners>  
            <add name="myListener" type="System.Diagnostics.TextWriterTraceListener, system version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" initializeData="c:\myListener.log" />  
         </listeners>  
      </trace>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="61b08-147">Consulte também</span><span class="sxs-lookup"><span data-stu-id="61b08-147">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- [<span data-ttu-id="61b08-148">Esquema de configurações de rastreamento e depuração</span><span class="sxs-lookup"><span data-stu-id="61b08-148">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
