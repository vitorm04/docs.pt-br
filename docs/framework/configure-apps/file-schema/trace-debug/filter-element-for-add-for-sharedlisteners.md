---
title: '&lt;filtro&gt; elemento para &lt;adicionar&gt; para &lt;sharedListeners&gt;'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sharedListeners/add/filter
helpviewer_keywords:
- filter element for <add> for <sharedListeners>
- initializeData attribute
- <filter> element for <add> for <sharedListeners>
- filters, trace listeners
- trace listeners, filters
ms.assetid: 7d4e7faa-2e4e-4379-ac76-f6cd7f2f8fac
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 3bbba1c805c6b300f7cf7b3d9112cde9df7607a8
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltfiltergt-element-for-ltaddgt-for-ltsharedlistenersgt"></a><span data-ttu-id="161eb-102">&lt;filtro&gt; elemento para &lt;adicionar&gt; para &lt;sharedListeners&gt;</span><span class="sxs-lookup"><span data-stu-id="161eb-102">&lt;filter&gt; Element for &lt;add&gt; for &lt;sharedListeners&gt;</span></span>
<span data-ttu-id="161eb-103">Adiciona um filtro a um ouvinte na coleção `sharedListeners`.</span><span class="sxs-lookup"><span data-stu-id="161eb-103">Adds a filter to a listener in the `sharedListeners` collection.</span></span>  
  
 <span data-ttu-id="161eb-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="161eb-104">\<configuration></span></span>  
<span data-ttu-id="161eb-105">\<System. Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="161eb-105">\<system.diagnostics></span></span>  
<span data-ttu-id="161eb-106">\<sharedListeners > elemento</span><span class="sxs-lookup"><span data-stu-id="161eb-106">\<sharedListeners> Element</span></span>  
<span data-ttu-id="161eb-107">\<add></span><span class="sxs-lookup"><span data-stu-id="161eb-107">\<add></span></span>  
<span data-ttu-id="161eb-108">\<Filtro ></span><span class="sxs-lookup"><span data-stu-id="161eb-108">\<filter></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="161eb-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="161eb-109">Syntax</span></span>  
  
```xml  
<filter type="System.Diagnostics.EventTypeFilter"   
  initializeData="Warning" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="161eb-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="161eb-110">Attributes and Elements</span></span>  
 <span data-ttu-id="161eb-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="161eb-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="161eb-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="161eb-112">Attributes</span></span>  
  
|<span data-ttu-id="161eb-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="161eb-113">Attribute</span></span>|<span data-ttu-id="161eb-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="161eb-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="161eb-115">**type**</span><span class="sxs-lookup"><span data-stu-id="161eb-115">**type**</span></span>|<span data-ttu-id="161eb-116">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="161eb-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="161eb-117">Especifica o tipo do filtro.</span><span class="sxs-lookup"><span data-stu-id="161eb-117">Specifies the type of the filter.</span></span> <span data-ttu-id="161eb-118">Você pode usar apenas o nome completo do tipo (no formato do <xref:System.Type.FullName%2A?displayProperty=nameWithType> propriedade), ou você pode usar o nome de tipo totalmente qualificado, incluindo as informações de assembly (no formato de <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType> propriedade).</span><span class="sxs-lookup"><span data-stu-id="161eb-118">You can use only the full name of the type (in the format of the <xref:System.Type.FullName%2A?displayProperty=nameWithType> property), or you can use the fully qualified type name including the assembly information (in the format of the <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType> property).</span></span> <span data-ttu-id="161eb-119">Para obter informações sobre a criação de um nome de tipo totalmente qualificado, consulte [especificando nomes de tipo totalmente qualificados](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="161eb-119">For information on creating a fully qualified type name, see [Specifying Fully Qualified Type Names](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|<span data-ttu-id="161eb-120">**initializeData**</span><span class="sxs-lookup"><span data-stu-id="161eb-120">**initializeData**</span></span>|<span data-ttu-id="161eb-121">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="161eb-121">Optional attribute.</span></span><br /><br /> <span data-ttu-id="161eb-122">A cadeia de caracteres passada para o construtor para a classe especificada.</span><span class="sxs-lookup"><span data-stu-id="161eb-122">The string passed to the constructor for the specified class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="161eb-123">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="161eb-123">Child Elements</span></span>  
 <span data-ttu-id="161eb-124">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="161eb-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="161eb-125">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="161eb-125">Parent Elements</span></span>  
  
|<span data-ttu-id="161eb-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="161eb-126">Element</span></span>|<span data-ttu-id="161eb-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="161eb-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="161eb-128">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="161eb-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="161eb-129">Especifica os ouvintes de rastreamento que coletam, armazenam e roteiam mensagens e o nível em que uma opção de rastreamento é definida.</span><span class="sxs-lookup"><span data-stu-id="161eb-129">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sharedListeners`|<span data-ttu-id="161eb-130">Uma coleção de ouvintes que podem referenciar qualquer origem ou o elemento de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="161eb-130">A collection of listeners that any source or trace element can reference.</span></span>|  
|`add`|<span data-ttu-id="161eb-131">Adiciona um ouvinte para o **sharedListeners** coleção.</span><span class="sxs-lookup"><span data-stu-id="161eb-131">Adds a listener to the **sharedListeners** collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="161eb-132">Comentários</span><span class="sxs-lookup"><span data-stu-id="161eb-132">Remarks</span></span>  
 <span data-ttu-id="161eb-133">Se um ouvinte é definido em um `<add>` elemento do `<sharedListeners>` elemento, o filtro para esse ouvinte deve ser definido em um `<filter>` que é um filho do elemento de `<add>` elemento.</span><span class="sxs-lookup"><span data-stu-id="161eb-133">If a listener is defined in an `<add>` element of the `<sharedListeners>` element, the filter for that listener should be defined in a `<filter>` element that is a child of the `<add>` element.</span></span>  
  
 <span data-ttu-id="161eb-134">Esse elemento pode ser usado no arquivo de configuração de máquina (Machine. config) e o arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="161eb-134">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="161eb-135">Exemplo</span><span class="sxs-lookup"><span data-stu-id="161eb-135">Example</span></span>  
 <span data-ttu-id="161eb-136">O exemplo a seguir mostra como usar o `<filter>` elemento para adicionar um filtro para o ouvinte de rastreamento `console` no `sharedListeners` coleção.</span><span class="sxs-lookup"><span data-stu-id="161eb-136">The following example shows how to use the `<filter>` element to add a filter to the trace listener `console` in the `sharedListeners` collection.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="myTraceSource" >  
        <listeners>  
          <add name="console" />  
          <remove name="Default" />  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add name="console"   
        type="System.Diagnostics.ConsoleTraceListener" >  
        <filter type="System.Diagnostics.EventTypeFilter"   
          initializeData="Error" />  
      </add>  
    </sharedListeners>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="161eb-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="161eb-137">See Also</span></span>  
 <xref:System.Diagnostics.TraceFilter>  
 <xref:System.Diagnostics.TraceListener>  
 <xref:System.Diagnostics.TraceSource>  
 [<span data-ttu-id="161eb-138">Esquema de configurações de rastreamento e depuração</span><span class="sxs-lookup"><span data-stu-id="161eb-138">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
