---
title: '&lt;filtro&gt; elemento para &lt;adicione&gt; para &lt;ouvintes&gt; para &lt;fonte&gt;'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#filter
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/add/filter
helpviewer_keywords:
- initializeData attribute
- <filter> element for <add> for <listeners> for <source>
- filter element for <add> for <listeners> for <source>
ms.assetid: 15808b80-4579-4c25-b385-178cfdf154ba
ms.openlocfilehash: 76aecf0b97a1b203d790dc34d83bc01ea1de5236
ms.sourcegitcommit: b351b0781a035616c90c68ccae6dd60aae66a953
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/26/2019
ms.locfileid: "55083282"
---
# <a name="ltfiltergt-element-for-ltaddgt-for-ltlistenersgt-for-ltsourcegt"></a><span data-ttu-id="df40b-102">&lt;filtro&gt; elemento para &lt;adicione&gt; para &lt;ouvintes&gt; para &lt;fonte&gt;</span><span class="sxs-lookup"><span data-stu-id="df40b-102">&lt;filter&gt; Element for &lt;add&gt; for &lt;listeners&gt; for &lt;source&gt;</span></span>
<span data-ttu-id="df40b-103">Adiciona um filtro a um ouvinte na coleção `Listeners` de uma origem de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="df40b-103">Adds a filter to a listener in the `Listeners` collection for a trace source.</span></span>  
  
 <span data-ttu-id="df40b-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="df40b-104">\<configuration></span></span>  
<span data-ttu-id="df40b-105">\<system.diagnostics></span><span class="sxs-lookup"><span data-stu-id="df40b-105">\<system.diagnostics></span></span>  
<span data-ttu-id="df40b-106">\<sources></span><span class="sxs-lookup"><span data-stu-id="df40b-106">\<sources></span></span>  
<span data-ttu-id="df40b-107">\<origem ></span><span class="sxs-lookup"><span data-stu-id="df40b-107">\<source></span></span>  
<span data-ttu-id="df40b-108">\<listeners></span><span class="sxs-lookup"><span data-stu-id="df40b-108">\<listeners></span></span>  
<span data-ttu-id="df40b-109">\<add></span><span class="sxs-lookup"><span data-stu-id="df40b-109">\<add></span></span>  
<span data-ttu-id="df40b-110">\<filter></span><span class="sxs-lookup"><span data-stu-id="df40b-110">\<filter></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df40b-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="df40b-111">Syntax</span></span>  
  
```xml  
<filter   
  type="traceFilterClassName"   
  initializeData="data" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="df40b-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="df40b-112">Attributes and Elements</span></span>  
 <span data-ttu-id="df40b-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="df40b-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="df40b-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="df40b-114">Attributes</span></span>  
  
|<span data-ttu-id="df40b-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="df40b-115">Attribute</span></span>|<span data-ttu-id="df40b-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="df40b-116">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="df40b-117">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="df40b-117">Required attribute.</span></span><br /><br /> <span data-ttu-id="df40b-118">Especifica o tipo de filtro, que deve herdar a <xref:System.Diagnostics.TraceFilter> classe.</span><span class="sxs-lookup"><span data-stu-id="df40b-118">Specifies the type of the filter, which should inherit from the <xref:System.Diagnostics.TraceFilter> class.</span></span> <span data-ttu-id="df40b-119">Você pode usar o nome qualificado de namespace do tipo, que corresponde ao tipo de <xref:System.Type.FullName%2A> propriedade, ou você pode usar o nome de tipo totalmente qualificado, incluindo as informações de assembly, que correspondem ao <xref:System.Type.AssemblyQualifiedName%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="df40b-119">You can use the namespace-qualified name of the type, which corresponds to the type's <xref:System.Type.FullName%2A> property, or you can use the fully qualified type name including the assembly information, which corresponds to the <xref:System.Type.AssemblyQualifiedName%2A> property.</span></span> <span data-ttu-id="df40b-120">Para obter informações sobre nomes de tipo totalmente qualificado, consulte [especificando nomes de tipo totalmente qualificados](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="df40b-120">For information about fully qualified type names, see [Specifying Fully Qualified Type Names](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="df40b-121">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="df40b-121">Optional attribute.</span></span><br /><br /> <span data-ttu-id="df40b-122">A cadeia de caracteres passada para o construtor para a classe de filtro especificado.</span><span class="sxs-lookup"><span data-stu-id="df40b-122">The string passed to the constructor for the specified filter class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="df40b-123">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="df40b-123">Child Elements</span></span>  
 <span data-ttu-id="df40b-124">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="df40b-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="df40b-125">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="df40b-125">Parent Elements</span></span>  
  
|<span data-ttu-id="df40b-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="df40b-126">Element</span></span>|<span data-ttu-id="df40b-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="df40b-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="df40b-128">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="df40b-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="df40b-129">Especifica os ouvintes de rastreamento que coletam, armazenam e roteiam mensagens e o nível em que uma opção de rastreamento é definida.</span><span class="sxs-lookup"><span data-stu-id="df40b-129">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="df40b-130">Contém as origens de rastreamento que iniciam as mensagens de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="df40b-130">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="df40b-131">Especifica uma origem de rastreamento que inicia as mensagens de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="df40b-131">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="df40b-132">Contém os ouvintes que coletam, armazenam e roteiam mensagens.</span><span class="sxs-lookup"><span data-stu-id="df40b-132">Contains listeners that collect, store, and route messages.</span></span> <span data-ttu-id="df40b-133">Os ouvintes direcionam a saída de rastreamento para um destino apropriado.</span><span class="sxs-lookup"><span data-stu-id="df40b-133">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`add`|<span data-ttu-id="df40b-134">Adiciona um ouvinte na coleção `Listeners` de uma origem de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="df40b-134">Adds a listener to the `Listeners` collection for a trace source.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="df40b-135">Comentários</span><span class="sxs-lookup"><span data-stu-id="df40b-135">Remarks</span></span>  
 <span data-ttu-id="df40b-136">O `<filter>` elemento deve estar contido em um `<add>` elemento para um ouvinte de origem de rastreamento que especifica o tipo do ouvinte, não apenas o nome de um ouvinte definido em um [ \<sharedListeners >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md).</span><span class="sxs-lookup"><span data-stu-id="df40b-136">The `<filter>` element must be contained in an `<add>` element for a trace source listener that specifies the type of the listener, not just the name of a listener defined in a [\<sharedListeners>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md).</span></span> <span data-ttu-id="df40b-137">Se o ouvinte é definido em um [ \<sharedListeners >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md), o filtro para esse ouvinte deve ser definido no elemento.</span><span class="sxs-lookup"><span data-stu-id="df40b-137">If the listener is defined in a [\<sharedListeners>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md), the filter for that listener must be defined in that element.</span></span>  
  
 <span data-ttu-id="df40b-138">Esse elemento pode ser usado no arquivo de configuração de máquina (Machine. config) e o arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="df40b-138">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="df40b-139">Exemplo</span><span class="sxs-lookup"><span data-stu-id="df40b-139">Example</span></span>  
 <span data-ttu-id="df40b-140">O exemplo a seguir mostra como usar o `<filter>` elemento para adicionar um filtro para o ouvinte `console` na `Listeners` coleção para a origem de rastreamento `myTraceSource`, especificando o nível de evento de filtro como `Error`.</span><span class="sxs-lookup"><span data-stu-id="df40b-140">The following example shows how to use the `<filter>` element to add a filter to the listener `console` in the `Listeners` collection for the trace source `myTraceSource`, specifying the filter event level as `Error`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="df40b-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="df40b-141">See also</span></span>
- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.TraceListener.Filter%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.TraceFilter>
- [<span data-ttu-id="df40b-142">Esquema de configurações de rastreamento e depuração</span><span class="sxs-lookup"><span data-stu-id="df40b-142">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
