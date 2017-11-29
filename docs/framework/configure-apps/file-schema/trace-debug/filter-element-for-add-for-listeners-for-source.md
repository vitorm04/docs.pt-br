---
title: '&lt;filtro&gt; elemento para &lt;adicionar&gt; para &lt;ouvintes&gt; para &lt;fonte&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#filter
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/add/filter
helpviewer_keywords:
- initializeData attribute
- <filter> element for <add> for <listeners> for <source>
- filter element for <add> for <listeners> for <source>
ms.assetid: 15808b80-4579-4c25-b385-178cfdf154ba
caps.latest.revision: "7"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 3b02f97caeef2a560682e5746c6c24986d5a3ad2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ltfiltergt-element-for-ltaddgt-for-ltlistenersgt-for-ltsourcegt"></a><span data-ttu-id="6c27d-102">&lt;filtro&gt; elemento para &lt;adicionar&gt; para &lt;ouvintes&gt; para &lt;fonte&gt;</span><span class="sxs-lookup"><span data-stu-id="6c27d-102">&lt;filter&gt; Element for &lt;add&gt; for &lt;listeners&gt; for &lt;source&gt;</span></span>
<span data-ttu-id="6c27d-103">Adiciona um filtro a um ouvinte na coleção `Listeners` de uma origem de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="6c27d-103">Adds a filter to a listener in the `Listeners` collection for a trace source.</span></span>  
  
 <span data-ttu-id="6c27d-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="6c27d-104">\<configuration></span></span>  
<span data-ttu-id="6c27d-105">\<System. Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="6c27d-105">\<system.diagnostics></span></span>  
<span data-ttu-id="6c27d-106">\<fontes ></span><span class="sxs-lookup"><span data-stu-id="6c27d-106">\<sources></span></span>  
<span data-ttu-id="6c27d-107">\<origem ></span><span class="sxs-lookup"><span data-stu-id="6c27d-107">\<source></span></span>  
<span data-ttu-id="6c27d-108">\<ouvintes ></span><span class="sxs-lookup"><span data-stu-id="6c27d-108">\<listeners></span></span>  
<span data-ttu-id="6c27d-109">\<add></span><span class="sxs-lookup"><span data-stu-id="6c27d-109">\<add></span></span>  
<span data-ttu-id="6c27d-110">\<Filtro ></span><span class="sxs-lookup"><span data-stu-id="6c27d-110">\<filter></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c27d-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6c27d-111">Syntax</span></span>  
  
```xml  
<filter   
  type="traceFilterClassName"   
  initializeData="data" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6c27d-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="6c27d-112">Attributes and Elements</span></span>  
 <span data-ttu-id="6c27d-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="6c27d-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6c27d-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="6c27d-114">Attributes</span></span>  
  
|<span data-ttu-id="6c27d-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="6c27d-115">Attribute</span></span>|<span data-ttu-id="6c27d-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="6c27d-116">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="6c27d-117">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="6c27d-117">Required attribute.</span></span><br /><br /> <span data-ttu-id="6c27d-118">Especifica o tipo de filtro, que deve herdar do <xref:System.Diagnostics.TraceFilter> classe.</span><span class="sxs-lookup"><span data-stu-id="6c27d-118">Specifies the type of the filter, which should inherit from the <xref:System.Diagnostics.TraceFilter> class.</span></span> <span data-ttu-id="6c27d-119">Você pode usar o nome qualificado de namespace do tipo, que corresponde ao tipo de <xref:System.Type.FullName%2A> propriedade, ou você pode usar o nome de tipo totalmente qualificado, incluindo as informações de assembly, que corresponde do <xref:System.Type.AssemblyQualifiedName%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="6c27d-119">You can use the namespace-qualified name of the type, which corresponds to the type's <xref:System.Type.FullName%2A> property, or you can use the fully qualified type name including the assembly information, which corresponds to the <xref:System.Type.AssemblyQualifiedName%2A> property.</span></span> <span data-ttu-id="6c27d-120">Para obter informações sobre nomes de tipo totalmente qualificado, consulte [especificando nomes de tipo totalmente qualificados](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="6c27d-120">For information about fully qualified type names, see [Specifying Fully Qualified Type Names](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="6c27d-121">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="6c27d-121">Optional attribute.</span></span><br /><br /> <span data-ttu-id="6c27d-122">A cadeia de caracteres transmitido ao construtor da classe de filtro especificado.</span><span class="sxs-lookup"><span data-stu-id="6c27d-122">The string passed to the constructor for the specified filter class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6c27d-123">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="6c27d-123">Child Elements</span></span>  
 <span data-ttu-id="6c27d-124">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="6c27d-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6c27d-125">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="6c27d-125">Parent Elements</span></span>  
  
|<span data-ttu-id="6c27d-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="6c27d-126">Element</span></span>|<span data-ttu-id="6c27d-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="6c27d-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="6c27d-128">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6c27d-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="6c27d-129">Especifica os ouvintes de rastreamento que coletam, armazenam e roteiam mensagens e o nível em que uma opção de rastreamento é definida.</span><span class="sxs-lookup"><span data-stu-id="6c27d-129">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="6c27d-130">Contém as origens de rastreamento que iniciam as mensagens de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="6c27d-130">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="6c27d-131">Especifica uma origem de rastreamento que inicia as mensagens de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="6c27d-131">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="6c27d-132">Contém os ouvintes que coletarem, armazenam e rotear mensagens.</span><span class="sxs-lookup"><span data-stu-id="6c27d-132">Contains listeners that collect, store, and route messages.</span></span> <span data-ttu-id="6c27d-133">Os ouvintes direcionam a saída de rastreamento para um destino satisfatório.</span><span class="sxs-lookup"><span data-stu-id="6c27d-133">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`add`|<span data-ttu-id="6c27d-134">Adiciona um ouvinte na coleção `Listeners` de uma origem de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="6c27d-134">Adds a listener to the `Listeners` collection for a trace source.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6c27d-135">Comentários</span><span class="sxs-lookup"><span data-stu-id="6c27d-135">Remarks</span></span>  
 <span data-ttu-id="6c27d-136">O `<filter>` elemento deve estar contido em um `<add>` elemento para um ouvinte de origem de rastreamento que especifica o tipo do ouvinte, não apenas o nome de um ouvinte definido um [ \<sharedListeners >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md).</span><span class="sxs-lookup"><span data-stu-id="6c27d-136">The `<filter>` element must be contained in an `<add>` element for a trace source listener that specifies the type of the listener, not just the name of a listener defined in a [\<sharedListeners>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md).</span></span> <span data-ttu-id="6c27d-137">Se o ouvinte é definido em um [ \<sharedListeners >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md), o filtro para esse ouvinte deve ser definido no elemento.</span><span class="sxs-lookup"><span data-stu-id="6c27d-137">If the listener is defined in a [\<sharedListeners>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md), the filter for that listener must be defined in that element.</span></span>  
  
 <span data-ttu-id="6c27d-138">Esse elemento pode ser usado no arquivo de configuração de máquina (Machine. config) e o arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6c27d-138">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6c27d-139">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6c27d-139">Example</span></span>  
 <span data-ttu-id="6c27d-140">O exemplo a seguir mostra como usar o `<filter>` elemento para adicionar um filtro para o ouvinte `console` no `Listeners` coleção para a origem de rastreamento `myTraceSource`, especificando o nível de evento de filtro como `Error`.</span><span class="sxs-lookup"><span data-stu-id="6c27d-140">The following example shows how to use the `<filter>` element to add a filter to the listener `console` in the `Listeners` collection for the trace source `myTraceSource`, specifying the filter event level as `Error`.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="myTraceSource" switchName="SourceSwitch"   
        switchType="System.Diagnostics.SourceSwitch"  >  
        <listeners>  
          <add name="console"   
            type="System.Diagnostics.ConsoleTraceListener" >  
            <filter type="System.Diagnostics.EventTypeFilter"   
              initializeData="Error" />  
          </add>  
          <remove name="Default" />  
        </listeners>  
      </source>  
    </sources>  
    <switches>  
      <add name="SourceSwitch" value="Warning" />  
    </switches>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6c27d-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6c27d-141">See Also</span></span>  
 <xref:System.Diagnostics.TraceSource>  
 <xref:System.Diagnostics.TraceListener>  
 <xref:System.Diagnostics.TraceListener.Filter%2A?displayProperty=nameWithType>  
 <xref:System.Diagnostics.TraceFilter>  
 [<span data-ttu-id="6c27d-142">Esquema de configurações de rastreamento e depuração</span><span class="sxs-lookup"><span data-stu-id="6c27d-142">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
