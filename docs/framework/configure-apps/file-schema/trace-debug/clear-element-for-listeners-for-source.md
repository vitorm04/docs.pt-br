---
title: '&lt;Limpar&gt; elemento para &lt;ouvintes&gt; para &lt;fonte&gt;'
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
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/clear
helpviewer_keywords:
- <clear> element for <listeners> for <source>
- clear element for <listeners> for <source>
ms.assetid: 76796bb2-9c0b-4526-8135-8bf18b16d8d9
caps.latest.revision: 
author: mcleblanc
ms.author: markl
manager: markl
ms.workload:
- dotnet
ms.openlocfilehash: 3cc809a6e896119c5d31c700f3e2ced171da9f7c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltcleargt-element-for-ltlistenersgt-for-ltsourcegt"></a><span data-ttu-id="5ca79-102">&lt;Limpar&gt; elemento para &lt;ouvintes&gt; para &lt;fonte&gt;</span><span class="sxs-lookup"><span data-stu-id="5ca79-102">&lt;clear&gt; Element for &lt;listeners&gt; for &lt;source&gt;</span></span>
<span data-ttu-id="5ca79-103">Limpa a coleção `Listeners` de uma origem de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="5ca79-103">Clears the `Listeners` collection for a trace source.</span></span>  
  
 <span data-ttu-id="5ca79-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="5ca79-104">\<configuration></span></span>  
<span data-ttu-id="5ca79-105">\<System. Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="5ca79-105">\<system.diagnostics></span></span>  
<span data-ttu-id="5ca79-106">\<fontes ></span><span class="sxs-lookup"><span data-stu-id="5ca79-106">\<sources></span></span>  
<span data-ttu-id="5ca79-107">\<origem ></span><span class="sxs-lookup"><span data-stu-id="5ca79-107">\<source></span></span>  
<span data-ttu-id="5ca79-108">\<ouvintes ></span><span class="sxs-lookup"><span data-stu-id="5ca79-108">\<listeners></span></span>  
<span data-ttu-id="5ca79-109">\<Limpar ></span><span class="sxs-lookup"><span data-stu-id="5ca79-109">\<clear></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ca79-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5ca79-110">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5ca79-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="5ca79-111">Attributes and Elements</span></span>  
 <span data-ttu-id="5ca79-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="5ca79-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5ca79-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="5ca79-113">Attributes</span></span>  
 <span data-ttu-id="5ca79-114">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="5ca79-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5ca79-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="5ca79-115">Child Elements</span></span>  
 <span data-ttu-id="5ca79-116">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="5ca79-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5ca79-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="5ca79-117">Parent Elements</span></span>  
  
|<span data-ttu-id="5ca79-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="5ca79-118">Element</span></span>|<span data-ttu-id="5ca79-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="5ca79-119">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="5ca79-120">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5ca79-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="5ca79-121">Especifica os ouvintes de rastreamento que coletam, armazenam e roteiam mensagens e o nível em que uma opção de rastreamento é definida.</span><span class="sxs-lookup"><span data-stu-id="5ca79-121">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="5ca79-122">Contém as origens de rastreamento que iniciam as mensagens de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="5ca79-122">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="5ca79-123">Especifica uma origem de rastreamento que inicia as mensagens de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="5ca79-123">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="5ca79-124">Especifica os ouvintes que coletarem, armazenam e rotear mensagens.</span><span class="sxs-lookup"><span data-stu-id="5ca79-124">Specifies listeners that collect, store, and route messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5ca79-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="5ca79-125">Remarks</span></span>  
 <span data-ttu-id="5ca79-126">O `<clear>` elemento remove todos os ouvintes do `Listeners` coleção para uma origem de rastreamento, incluindo o <xref:System.Diagnostics.DefaultTraceListener>.</span><span class="sxs-lookup"><span data-stu-id="5ca79-126">The `<clear>` element removes all listeners from the `Listeners` collection for a trace source, including the <xref:System.Diagnostics.DefaultTraceListener>.</span></span> <span data-ttu-id="5ca79-127">Você pode usar o `<clear>` elemento antes de usar o `<add>` elemento para ter certeza de que não há nenhum outros ouvintes ativos na coleção.</span><span class="sxs-lookup"><span data-stu-id="5ca79-127">You can use the `<clear>` element before using the `<add>` element to be certain there are no other active listeners in the collection.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="5ca79-128">Arquivo de Configuração</span><span class="sxs-lookup"><span data-stu-id="5ca79-128">Configuration File</span></span>  
 <span data-ttu-id="5ca79-129">Esse elemento pode ser usado no arquivo de configuração de máquina (Machine. config) e o arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5ca79-129">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5ca79-130">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5ca79-130">Example</span></span>  
 <span data-ttu-id="5ca79-131">O exemplo a seguir mostra como usar o `<clear>` elemento antes de usar o `<add>` elementos para adicionar os ouvintes `console` e `textListener` para o `Listeners` coleção para a origem de rastreamento `TraceSourceApp`.</span><span class="sxs-lookup"><span data-stu-id="5ca79-131">The following example shows how to use the `<clear>` element before using the `<add>` elements to add the listeners `console` and `textListener` to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5ca79-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5ca79-132">See Also</span></span>  
 <xref:System.Diagnostics.TraceSource>  
 <xref:System.Diagnostics.TraceListener>  
 [<span data-ttu-id="5ca79-133">Esquema de configurações de rastreamento e depuração</span><span class="sxs-lookup"><span data-stu-id="5ca79-133">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)  
 [<span data-ttu-id="5ca79-134">Ouvintes de rastreamento</span><span class="sxs-lookup"><span data-stu-id="5ca79-134">Trace Listeners</span></span>](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
