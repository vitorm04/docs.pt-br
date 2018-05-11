---
title: '&lt;filtro&gt; elemento para &lt;adicionar&gt; para &lt;ouvintes&gt; para &lt;rastreamento&gt;'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/add/filter
helpviewer_keywords:
- initializeData attribute
- filter element for <add> for <listeners> for <trace>
- <filter> element for <add> for <listeners> for <trace>
ms.assetid: eb9c18f5-dfa8-47c5-b91b-e4b93e76e1cc
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 095212f73adb906d9d80db747c331c436c1cf846
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltfiltergt-element-for-ltaddgt-for-ltlistenersgt-for-lttracegt"></a><span data-ttu-id="a063d-102">&lt;filtro&gt; elemento para &lt;adicionar&gt; para &lt;ouvintes&gt; para &lt;rastreamento&gt;</span><span class="sxs-lookup"><span data-stu-id="a063d-102">&lt;filter&gt; Element for &lt;add&gt; for &lt;listeners&gt; for &lt;trace&gt;</span></span>
<span data-ttu-id="a063d-103">Adiciona um filtro a um ouvinte no `Listeners` coleção para um rastreamento.</span><span class="sxs-lookup"><span data-stu-id="a063d-103">Adds a filter to a listener in the `Listeners` collection for a trace.</span></span>  
  
 <span data-ttu-id="a063d-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="a063d-104">\<configuration></span></span>  
<span data-ttu-id="a063d-105">\<System. Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="a063d-105">\<system.diagnostics></span></span>  
<span data-ttu-id="a063d-106">\<rastreamento ></span><span class="sxs-lookup"><span data-stu-id="a063d-106">\<trace></span></span>  
<span data-ttu-id="a063d-107">\<ouvintes ></span><span class="sxs-lookup"><span data-stu-id="a063d-107">\<listeners></span></span>  
<span data-ttu-id="a063d-108">\<add></span><span class="sxs-lookup"><span data-stu-id="a063d-108">\<add></span></span>  
<span data-ttu-id="a063d-109">\<Filtro ></span><span class="sxs-lookup"><span data-stu-id="a063d-109">\<filter></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a063d-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a063d-110">Syntax</span></span>  
  
```xml  
<filter   
  type="traceFilterClassName"   
  initializeData="data" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a063d-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="a063d-111">Attributes and Elements</span></span>  
 <span data-ttu-id="a063d-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="a063d-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a063d-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="a063d-113">Attributes</span></span>  
  
|<span data-ttu-id="a063d-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="a063d-114">Attribute</span></span>|<span data-ttu-id="a063d-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="a063d-115">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="a063d-116">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="a063d-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="a063d-117">Especifica o tipo de filtro, que deve herdar do <xref:System.Diagnostics.TraceFilter> classe.</span><span class="sxs-lookup"><span data-stu-id="a063d-117">Specifies the type of the filter, which should inherit from the <xref:System.Diagnostics.TraceFilter> class.</span></span> <span data-ttu-id="a063d-118">Você pode usar o nome qualificado de namespace do tipo, que corresponde ao tipo de <xref:System.Type.FullName%2A> propriedade, ou você pode usar o nome de tipo totalmente qualificado, incluindo as informações de assembly, que corresponde do <xref:System.Type.AssemblyQualifiedName%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="a063d-118">You can use the namespace-qualified name of the type, which corresponds to the type's <xref:System.Type.FullName%2A> property, or you can use the fully qualified type name including the assembly information, which corresponds to the <xref:System.Type.AssemblyQualifiedName%2A> property.</span></span> <span data-ttu-id="a063d-119">Para obter informações sobre nomes de tipo totalmente qualificado, consulte [especificando nomes de tipo totalmente qualificados](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="a063d-119">For information about fully qualified type names, see [Specifying Fully Qualified Type Names](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="a063d-120">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="a063d-120">Optional attribute.</span></span><br /><br /> <span data-ttu-id="a063d-121">A cadeia de caracteres transmitido ao construtor da classe de filtro especificado.</span><span class="sxs-lookup"><span data-stu-id="a063d-121">The string passed to the constructor for the specified filter class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a063d-122">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="a063d-122">Child Elements</span></span>  
 <span data-ttu-id="a063d-123">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="a063d-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a063d-124">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="a063d-124">Parent Elements</span></span>  
  
|<span data-ttu-id="a063d-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="a063d-125">Element</span></span>|<span data-ttu-id="a063d-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="a063d-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="a063d-127">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a063d-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="a063d-128">Especifica os ouvintes de rastreamento que coletam, armazenam e roteiam mensagens e o nível em que uma opção de rastreamento é definida.</span><span class="sxs-lookup"><span data-stu-id="a063d-128">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`trace`|<span data-ttu-id="a063d-129">Contém os ouvintes que coletam, armazenam e roteiam mensagens de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="a063d-129">Contains listeners that collect, store, and route tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="a063d-130">Contém os ouvintes que coletarem, armazenam e rotear mensagens.</span><span class="sxs-lookup"><span data-stu-id="a063d-130">Contains listeners that collect, store, and route messages.</span></span> <span data-ttu-id="a063d-131">Os ouvintes direcionam a saída de rastreamento para um destino satisfatório.</span><span class="sxs-lookup"><span data-stu-id="a063d-131">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`add`|<span data-ttu-id="a063d-132">Adiciona um ouvinte na coleção `Listeners`.</span><span class="sxs-lookup"><span data-stu-id="a063d-132">Adds a listener to the `Listeners` collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a063d-133">Comentários</span><span class="sxs-lookup"><span data-stu-id="a063d-133">Remarks</span></span>  
 <span data-ttu-id="a063d-134">O `<filter>` elemento deve estar contido em um `<add>` elemento para um ouvinte de rastreamento que especifica o tipo do ouvinte, não apenas o nome de um ouvinte definido um [ \<sharedListeners >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md).</span><span class="sxs-lookup"><span data-stu-id="a063d-134">The `<filter>` element must be contained in an `<add>` element for a trace listener that specifies the type of the listener, not just the name of a listener defined in a [\<sharedListeners>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md).</span></span> <span data-ttu-id="a063d-135">Se o ouvinte é definido em um [ \<sharedListeners >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md), o filtro para esse ouvinte deve ser definido no elemento.</span><span class="sxs-lookup"><span data-stu-id="a063d-135">If the listener is defined in a [\<sharedListeners>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md), the filter for that listener must be defined in that element.</span></span>  
  
 <span data-ttu-id="a063d-136">Esse elemento pode ser usado no arquivo de configuração de máquina (Machine. config) e o arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a063d-136">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a063d-137">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a063d-137">Example</span></span>  
 <span data-ttu-id="a063d-138">O exemplo a seguir mostra como usar o `<filter>` elemento para adicionar um filtro para o ouvinte `console` no `Listeners` coleta de rastreamento, especificando o nível de evento de filtro como `Error`.</span><span class="sxs-lookup"><span data-stu-id="a063d-138">The following example shows how to use the `<filter>` element to add a filter to the listener `console` in the `Listeners` collection for trace, specifying the filter event level as `Error`.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <trace autoflush="false" indentsize="4">  
      <listeners>  
        <add name="console"   
          type="System.Diagnostics.ConsoleTraceListener" >  
          <filter type="System.Diagnostics.EventTypeFilter"   
            initializeData="Error" />  
        </add>  
        <remove name="Default" />  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a063d-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a063d-139">See Also</span></span>  
 <xref:System.Diagnostics.Trace>  
 <xref:System.Diagnostics.TraceListener>  
 <xref:System.Diagnostics.TraceListener.Filter%2A?displayProperty=nameWithType>  
 <xref:System.Diagnostics.TraceFilter>  
 [<span data-ttu-id="a063d-140">Esquema de configurações de rastreamento e depuração</span><span class="sxs-lookup"><span data-stu-id="a063d-140">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
