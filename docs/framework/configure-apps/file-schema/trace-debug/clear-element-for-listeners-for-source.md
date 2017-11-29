---
title: '&lt;Limpar&gt; elemento para &lt;ouvintes&gt; para &lt;fonte&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/clear
helpviewer_keywords:
- <clear> element for <listeners> for <source>
- clear element for <listeners> for <source>
ms.assetid: 76796bb2-9c0b-4526-8135-8bf18b16d8d9
caps.latest.revision: "7"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: d5e8518f2ca8a04d91f5bfdd9f6389c741d0278e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ltcleargt-element-for-ltlistenersgt-for-ltsourcegt"></a><span data-ttu-id="e817b-102">&lt;Limpar&gt; elemento para &lt;ouvintes&gt; para &lt;fonte&gt;</span><span class="sxs-lookup"><span data-stu-id="e817b-102">&lt;clear&gt; Element for &lt;listeners&gt; for &lt;source&gt;</span></span>
<span data-ttu-id="e817b-103">Limpa a coleção `Listeners` de uma origem de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="e817b-103">Clears the `Listeners` collection for a trace source.</span></span>  
  
 <span data-ttu-id="e817b-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="e817b-104">\<configuration></span></span>  
<span data-ttu-id="e817b-105">\<System. Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="e817b-105">\<system.diagnostics></span></span>  
<span data-ttu-id="e817b-106">\<fontes ></span><span class="sxs-lookup"><span data-stu-id="e817b-106">\<sources></span></span>  
<span data-ttu-id="e817b-107">\<origem ></span><span class="sxs-lookup"><span data-stu-id="e817b-107">\<source></span></span>  
<span data-ttu-id="e817b-108">\<ouvintes ></span><span class="sxs-lookup"><span data-stu-id="e817b-108">\<listeners></span></span>  
<span data-ttu-id="e817b-109">\<Limpar ></span><span class="sxs-lookup"><span data-stu-id="e817b-109">\<clear></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e817b-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e817b-110">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e817b-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="e817b-111">Attributes and Elements</span></span>  
 <span data-ttu-id="e817b-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="e817b-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e817b-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="e817b-113">Attributes</span></span>  
 <span data-ttu-id="e817b-114">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="e817b-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e817b-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="e817b-115">Child Elements</span></span>  
 <span data-ttu-id="e817b-116">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="e817b-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e817b-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="e817b-117">Parent Elements</span></span>  
  
|<span data-ttu-id="e817b-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="e817b-118">Element</span></span>|<span data-ttu-id="e817b-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="e817b-119">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="e817b-120">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e817b-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="e817b-121">Especifica os ouvintes de rastreamento que coletam, armazenam e roteiam mensagens e o nível em que uma opção de rastreamento é definida.</span><span class="sxs-lookup"><span data-stu-id="e817b-121">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="e817b-122">Contém as origens de rastreamento que iniciam as mensagens de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="e817b-122">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="e817b-123">Especifica uma origem de rastreamento que inicia as mensagens de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="e817b-123">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="e817b-124">Especifica os ouvintes que coletarem, armazenam e rotear mensagens.</span><span class="sxs-lookup"><span data-stu-id="e817b-124">Specifies listeners that collect, store, and route messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e817b-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="e817b-125">Remarks</span></span>  
 <span data-ttu-id="e817b-126">O `<clear>` elemento remove todos os ouvintes do `Listeners` coleção para uma origem de rastreamento, incluindo o <xref:System.Diagnostics.DefaultTraceListener>.</span><span class="sxs-lookup"><span data-stu-id="e817b-126">The `<clear>` element removes all listeners from the `Listeners` collection for a trace source, including the <xref:System.Diagnostics.DefaultTraceListener>.</span></span> <span data-ttu-id="e817b-127">Você pode usar o `<clear>` elemento antes de usar o `<add>` elemento para ter certeza de que não há nenhum outros ouvintes ativos na coleção.</span><span class="sxs-lookup"><span data-stu-id="e817b-127">You can use the `<clear>` element before using the `<add>` element to be certain there are no other active listeners in the collection.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="e817b-128">Arquivo de Configuração</span><span class="sxs-lookup"><span data-stu-id="e817b-128">Configuration File</span></span>  
 <span data-ttu-id="e817b-129">Esse elemento pode ser usado no arquivo de configuração de máquina (Machine. config) e o arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e817b-129">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e817b-130">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e817b-130">Example</span></span>  
 <span data-ttu-id="e817b-131">O exemplo a seguir mostra como usar o `<clear>` elemento antes de usar o `<add>` elementos para adicionar os ouvintes `console` e `textListener` para o `Listeners` coleção para a origem de rastreamento `TraceSourceApp`.</span><span class="sxs-lookup"><span data-stu-id="e817b-131">The following example shows how to use the `<clear>` element before using the `<add>` elements to add the listeners `console` and `textListener` to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
       <source name="TraceSourceApp" switchName="sourceSwitch"   
         switchType="System.Diagnostics.SourceSwitch">  
        <listeners>  
          <clear/>  
          <add name="console"   
            type="System.Diagnostics.ConsoleTraceListener"/>  
          <add name="textListener"/>  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add name="textListener"   
        type="System.Diagnostics.TextWriterTraceListener"   
        initializeData="myListener.log"/>  
    </sharedListeners>  
    <switches>  
      <add name="sourceSwitch" value="Warning"/>  
    </switches>  
  </system.diagnostics>  
</configuration>   
```  
  
## <a name="see-also"></a><span data-ttu-id="e817b-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e817b-132">See Also</span></span>  
 <xref:System.Diagnostics.TraceSource>  
 <xref:System.Diagnostics.TraceListener>  
 [<span data-ttu-id="e817b-133">Esquema de configurações de rastreamento e depuração</span><span class="sxs-lookup"><span data-stu-id="e817b-133">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)  
 [<span data-ttu-id="e817b-134">Ouvintes de rastreamento</span><span class="sxs-lookup"><span data-stu-id="e817b-134">Trace Listeners</span></span>](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
