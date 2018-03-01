---
title: '&lt;Limpar&gt; elemento para &lt;ouvintes&gt; para &lt;rastreamento&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/clear
helpviewer_keywords:
- clear element for <listeners> for <trace>
- <clear> element for <listeners> for <trace>
ms.assetid: b44732a8-271f-4a06-ba9e-fe3298d6f192
caps.latest.revision: 
author: mcleblanc
ms.author: markl
manager: markl
ms.workload:
- dotnet
ms.openlocfilehash: b2739cc5eaa6a1e43c06849e1b00f7ac8bd531e7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltcleargt-element-for-ltlistenersgt-for-lttracegt"></a><span data-ttu-id="c400d-102">&lt;Limpar&gt; elemento para &lt;ouvintes&gt; para &lt;rastreamento&gt;</span><span class="sxs-lookup"><span data-stu-id="c400d-102">&lt;clear&gt; Element for &lt;listeners&gt; for &lt;trace&gt;</span></span>
<span data-ttu-id="c400d-103">Limpa a coleção `Listeners` do rastreamento.</span><span class="sxs-lookup"><span data-stu-id="c400d-103">Clears the `Listeners` collection for trace.</span></span>  
  
 <span data-ttu-id="c400d-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="c400d-104">\<configuration></span></span>  
<span data-ttu-id="c400d-105">\<System. Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="c400d-105">\<system.diagnostics></span></span>  
<span data-ttu-id="c400d-106">\<rastreamento ></span><span class="sxs-lookup"><span data-stu-id="c400d-106">\<trace></span></span>  
<span data-ttu-id="c400d-107">\<ouvintes ></span><span class="sxs-lookup"><span data-stu-id="c400d-107">\<listeners></span></span>  
<span data-ttu-id="c400d-108">\<Limpar ></span><span class="sxs-lookup"><span data-stu-id="c400d-108">\<clear></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c400d-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c400d-109">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c400d-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="c400d-110">Attributes and Elements</span></span>  
 <span data-ttu-id="c400d-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="c400d-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c400d-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="c400d-112">Attributes</span></span>  
 <span data-ttu-id="c400d-113">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="c400d-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c400d-114">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="c400d-114">Child Elements</span></span>  
 <span data-ttu-id="c400d-115">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="c400d-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c400d-116">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="c400d-116">Parent Elements</span></span>  
  
|<span data-ttu-id="c400d-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="c400d-117">Element</span></span>|<span data-ttu-id="c400d-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="c400d-118">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="c400d-119">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c400d-119">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="c400d-120">Especifica os ouvintes de rastreamento que coletam, armazenam e roteiam mensagens e o nível em que uma opção de rastreamento é definida.</span><span class="sxs-lookup"><span data-stu-id="c400d-120">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`trace`|<span data-ttu-id="c400d-121">Contém os ouvintes que coletam, armazenam e roteiam mensagens de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="c400d-121">Contains listeners that collect, store, and route tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="c400d-122">Contém os ouvintes que coletarem, armazenam e rotear mensagens.</span><span class="sxs-lookup"><span data-stu-id="c400d-122">Contains listeners that collect, store, and route messages.</span></span> <span data-ttu-id="c400d-123">Os ouvintes direcionam a saída de rastreamento para um destino satisfatório.</span><span class="sxs-lookup"><span data-stu-id="c400d-123">Listeners direct the tracing output to an appropriate target.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c400d-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="c400d-124">Remarks</span></span>  
 <span data-ttu-id="c400d-125">O `<clear>` elemento remove todos os ouvintes do `Listeners` coleta de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="c400d-125">The `<clear>` element removes all listeners from the `Listeners` collection for trace.</span></span> <span data-ttu-id="c400d-126">Você pode usar o `<clear>` elemento antes de usar o `<add>` elemento para ter certeza de que não há nenhum outros ouvintes ativos na coleção.</span><span class="sxs-lookup"><span data-stu-id="c400d-126">You can use the `<clear>` element before using the `<add>` element to be certain there are no other active listeners in the collection.</span></span>  
  
 <span data-ttu-id="c400d-127">Você pode limpar o `Listeners` coleção programaticamente, chamando o <xref:System.Diagnostics.TraceListenerCollection.Clear%2A> método no <xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=nameWithType> propriedade (`System.Diagnostics.Trace.Listeners.Clear()`).</span><span class="sxs-lookup"><span data-stu-id="c400d-127">You can clear the `Listeners` collection programmatically by calling the <xref:System.Diagnostics.TraceListenerCollection.Clear%2A> method on the <xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=nameWithType> property (`System.Diagnostics.Trace.Listeners.Clear()`).</span></span>  
  
 <span data-ttu-id="c400d-128">Esse elemento pode ser usado no arquivo de configuração de máquina (Machine. config) e o arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c400d-128">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c400d-129">O `<clear>` elemento remove o <xref:System.Diagnostics.DefaultTraceListener> do `Listeners` coleção, alterando o comportamento do <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>, e <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> métodos.</span><span class="sxs-lookup"><span data-stu-id="c400d-129">The `<clear>` element removes the <xref:System.Diagnostics.DefaultTraceListener> from the `Listeners` collection, altering the behavior of the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>, and <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="c400d-130">Chamando um `Assert` ou `Fail` método normalmente resulta na exibição de uma caixa de mensagem.</span><span class="sxs-lookup"><span data-stu-id="c400d-130">Calling an `Assert` or `Fail` method normally results in the display of a message box.</span></span> <span data-ttu-id="c400d-131">No entanto, a caixa de mensagem não será exibida se o <xref:System.Diagnostics.DefaultTraceListener> não está no `Listeners` coleção.</span><span class="sxs-lookup"><span data-stu-id="c400d-131">However, the message box is not displayed if the <xref:System.Diagnostics.DefaultTraceListener> is not in the `Listeners` collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c400d-132">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c400d-132">Example</span></span>  
 <span data-ttu-id="c400d-133">O exemplo a seguir mostra como usar o `<clear>` elemento antes de usar o `<add>` elemento para adicionar o ouvinte `console` para o `Listeners` coleta de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="c400d-133">The following example shows how to use the `<clear>` element before using the `<add>` element to add the listener `console` to the `Listeners` collection for trace.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <trace autoflush="false" indentsize="4">  
      <listeners>  
        <clear/>  
        <add name="console"   
          type="System.Diagnostics.ConsoleTraceListener" >  
          <filter type="System.Diagnostics.EventTypeFilter"   
            initializeData="Error" />  
        </add>  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration>   
```  
  
## <a name="see-also"></a><span data-ttu-id="c400d-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c400d-134">See Also</span></span>  
 <xref:System.Diagnostics.Trace.Listeners%2A>  
 <xref:System.Diagnostics.Trace>  
 <xref:System.Diagnostics.Debug>  
 <xref:System.Diagnostics.TraceSource>  
 [<span data-ttu-id="c400d-135">Esquema de configurações de rastreamento e depuração</span><span class="sxs-lookup"><span data-stu-id="c400d-135">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)  
 [<span data-ttu-id="c400d-136">\<remove></span><span class="sxs-lookup"><span data-stu-id="c400d-136">\<remove></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/remove-element-for-listeners-for-trace.md)  
 [<span data-ttu-id="c400d-137">Ouvintes de rastreamento</span><span class="sxs-lookup"><span data-stu-id="c400d-137">Trace Listeners</span></span>](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
