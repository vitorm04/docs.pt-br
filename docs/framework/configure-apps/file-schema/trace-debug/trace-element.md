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
ms.openlocfilehash: 617b42a0be2be272a78b33be997cce632d1c6dcb
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91198919"
---
# <a name="trace-element"></a><span data-ttu-id="f087a-102">Elemento \<trace></span><span class="sxs-lookup"><span data-stu-id="f087a-102">\<trace> Element</span></span>

<span data-ttu-id="f087a-103">Contém os ouvintes que coletam, armazenam e roteiam mensagens de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="f087a-103">Contains listeners that collect, store, and route tracing messages.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<trace>**  
  
## <a name="syntax"></a><span data-ttu-id="f087a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f087a-104">Syntax</span></span>  
  
```xml  
<trace autoflush="true|false"
       indentsize="indent value"  
       useGlobalLock="true| false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f087a-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="f087a-105">Attributes and Elements</span></span>  

 <span data-ttu-id="f087a-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="f087a-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f087a-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="f087a-107">Attributes</span></span>  
  
|<span data-ttu-id="f087a-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="f087a-108">Attribute</span></span>|<span data-ttu-id="f087a-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="f087a-109">Description</span></span>|  
|---------------|-----------------|  
|`autoflush`|<span data-ttu-id="f087a-110">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="f087a-110">Optional attribute.</span></span><br /><br /> <span data-ttu-id="f087a-111">Especifica se os ouvintes de rastreamento liberam automaticamente o buffer de saída após cada operação de gravação.</span><span class="sxs-lookup"><span data-stu-id="f087a-111">Specifies whether the trace listeners automatically flush the output buffer after every write operation.</span></span>|  
|`indentsize`|<span data-ttu-id="f087a-112">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="f087a-112">Optional attribute.</span></span><br /><br /> <span data-ttu-id="f087a-113">Especifica o número de espaços a serem recuados.</span><span class="sxs-lookup"><span data-stu-id="f087a-113">Specifies the number of spaces to indent.</span></span>|  
|`useGlobalLock`|<span data-ttu-id="f087a-114">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="f087a-114">Optional attribute.</span></span><br /><br /> <span data-ttu-id="f087a-115">Indica se o bloqueio global deve ser usado.</span><span class="sxs-lookup"><span data-stu-id="f087a-115">Indicates whether the global lock should be used.</span></span>|  
  
## <a name="autoflush-attribute"></a><span data-ttu-id="f087a-116">Atributo autoflush</span><span class="sxs-lookup"><span data-stu-id="f087a-116">autoflush Attribute</span></span>  
  
|<span data-ttu-id="f087a-117">Valor</span><span class="sxs-lookup"><span data-stu-id="f087a-117">Value</span></span>|<span data-ttu-id="f087a-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="f087a-118">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="f087a-119">Não libera automaticamente o buffer de saída.</span><span class="sxs-lookup"><span data-stu-id="f087a-119">Does not automatically flush the output buffer.</span></span> <span data-ttu-id="f087a-120">Esse é o padrão.</span><span class="sxs-lookup"><span data-stu-id="f087a-120">This is the default.</span></span>|  
|`true`|<span data-ttu-id="f087a-121">Libera automaticamente o buffer de saída.</span><span class="sxs-lookup"><span data-stu-id="f087a-121">Automatically flushes the output buffer.</span></span>|  
  
## <a name="usegloballock-attribute"></a><span data-ttu-id="f087a-122">Atributo useGlobalLock</span><span class="sxs-lookup"><span data-stu-id="f087a-122">useGlobalLock Attribute</span></span>  
  
|<span data-ttu-id="f087a-123">Valor</span><span class="sxs-lookup"><span data-stu-id="f087a-123">Value</span></span>|<span data-ttu-id="f087a-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="f087a-124">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="f087a-125">Não usará o bloqueio global se o ouvinte for thread-safe; caso contrário, o usará o bloqueio global.</span><span class="sxs-lookup"><span data-stu-id="f087a-125">Does not use the global lock if the listener is thread safe; otherwise, uses the global lock.</span></span>|  
|`true`|<span data-ttu-id="f087a-126">Usa o bloqueio global independentemente de o ouvinte ser thread-safe.</span><span class="sxs-lookup"><span data-stu-id="f087a-126">Uses the global lock regardless of whether the listener is thread safe.</span></span> <span data-ttu-id="f087a-127">Esse é o padrão.</span><span class="sxs-lookup"><span data-stu-id="f087a-127">This is the default.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f087a-128">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="f087a-128">Child Elements</span></span>  
  
|<span data-ttu-id="f087a-129">Elemento</span><span class="sxs-lookup"><span data-stu-id="f087a-129">Element</span></span>|<span data-ttu-id="f087a-130">Descrição</span><span class="sxs-lookup"><span data-stu-id="f087a-130">Description</span></span>|  
|-------------|-----------------|  
|[\<listeners>](listeners-element-for-trace.md)|<span data-ttu-id="f087a-131">Especifica um ouvinte que coleta, armazena e roteia mensagens.</span><span class="sxs-lookup"><span data-stu-id="f087a-131">Specifies a listener that collects, stores, and routes messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f087a-132">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="f087a-132">Parent Elements</span></span>  
  
|<span data-ttu-id="f087a-133">Elemento</span><span class="sxs-lookup"><span data-stu-id="f087a-133">Element</span></span>|<span data-ttu-id="f087a-134">Descrição</span><span class="sxs-lookup"><span data-stu-id="f087a-134">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="f087a-135">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f087a-135">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="f087a-136">Especifica os ouvintes de rastreamento que coletam, armazenam e roteiam mensagens e o nível em que uma opção de rastreamento é definida.</span><span class="sxs-lookup"><span data-stu-id="f087a-136">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="f087a-137">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f087a-137">Example</span></span>  

 <span data-ttu-id="f087a-138">O exemplo a seguir mostra como usar o `<trace>` elemento para adicionar o ouvinte `MyListener` à `Listeners` coleção.</span><span class="sxs-lookup"><span data-stu-id="f087a-138">The following example shows how to use the `<trace>` element to add the listener `MyListener` to the `Listeners` collection.</span></span> <span data-ttu-id="f087a-139">`MyListener` Cria um arquivo chamado `MyListener.log` e grava a saída no arquivo.</span><span class="sxs-lookup"><span data-stu-id="f087a-139">`MyListener` creates a file that is named `MyListener.log` and writes the output to the file.</span></span> <span data-ttu-id="f087a-140">O `useGlobalLock` atributo é definido como `false` , o que faz com que o bloqueio global não seja usado se o ouvinte de rastreamento for thread-safe.</span><span class="sxs-lookup"><span data-stu-id="f087a-140">The `useGlobalLock` attribute is set to `false`, which causes the global lock not to be used if the trace listener is thread safe.</span></span> <span data-ttu-id="f087a-141">O `autoflush` atributo é definido como `true` , o que faz com que o ouvinte de rastreamento grave no arquivo, independentemente de o <xref:System.Diagnostics.Trace.Flush%2A?displayProperty=nameWithType> método ser chamado.</span><span class="sxs-lookup"><span data-stu-id="f087a-141">The `autoflush` attribute is set to `true`, which causes the trace listener to write to the file regardless of whether the <xref:System.Diagnostics.Trace.Flush%2A?displayProperty=nameWithType> method is called.</span></span> <span data-ttu-id="f087a-142">O `indentsize` atributo é definido como 0 (zero), o que faz com que o ouvinte recue zero espaços quando o <xref:System.Diagnostics.Trace.Indent%2A?displayProperty=nameWithType> método é chamado.</span><span class="sxs-lookup"><span data-stu-id="f087a-142">The `indentsize` attribute is set to 0 (zero), which causes the listener to indent zero spaces when the <xref:System.Diagnostics.Trace.Indent%2A?displayProperty=nameWithType> method is called.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f087a-143">Veja também</span><span class="sxs-lookup"><span data-stu-id="f087a-143">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- [<span data-ttu-id="f087a-144">Esquema de configurações de rastreamento e depuração</span><span class="sxs-lookup"><span data-stu-id="f087a-144">Trace and Debug Settings Schema</span></span>](index.md)
