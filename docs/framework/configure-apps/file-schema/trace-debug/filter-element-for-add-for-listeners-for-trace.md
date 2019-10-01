---
title: Elemento <filter> para <add> para <listeners> para <trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/add/filter
helpviewer_keywords:
- initializeData attribute
- filter element for <add> for <listeners> for <trace>
- <filter> element for <add> for <listeners> for <trace>
ms.assetid: eb9c18f5-dfa8-47c5-b91b-e4b93e76e1cc
ms.openlocfilehash: f6b1ec99c5aab8e85df7f1920aca32f49a5be066
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699361"
---
# <a name="filter-element-for-add-for-listeners-for-trace"></a><span data-ttu-id="aabc0-102">\<filter > o elemento para @no__t > @no__t > para @no__t 3trace ></span><span class="sxs-lookup"><span data-stu-id="aabc0-102">\<filter> Element for \<add> for \<listeners> for \<trace></span></span>
<span data-ttu-id="aabc0-103">Adiciona um filtro a um ouvinte na coleção `Listeners` para um rastreamento.</span><span class="sxs-lookup"><span data-stu-id="aabc0-103">Adds a filter to a listener in the `Listeners` collection for a trace.</span></span>  
  
[<span data-ttu-id="aabc0-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="aabc0-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="aabc0-105">&nbsp; @ no__t-1[ **\<System. Diagnostics >** ](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="aabc0-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>  
<span data-ttu-id="aabc0-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<trace >** ](trace-element.md)</span><span class="sxs-lookup"><span data-stu-id="aabc0-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<trace>**](trace-element.md)</span></span>  
<span data-ttu-id="aabc0-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5[ **\<listeners >** ](listeners-element-for-trace.md)</span><span class="sxs-lookup"><span data-stu-id="aabc0-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-trace.md)</span></span>  
<span data-ttu-id="aabc0-108">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 @ no__t-7[ **&nbsp;0add >** ](add-element-for-listeners-for-trace.md)</span><span class="sxs-lookup"><span data-stu-id="aabc0-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-element-for-listeners-for-trace.md)</span></span>  
<span data-ttu-id="aabc0-109">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 @ no__t-7 @ no__t-8 @ no__t-9 **&nbsp;1filter >**</span><span class="sxs-lookup"><span data-stu-id="aabc0-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filter>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aabc0-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="aabc0-110">Syntax</span></span>  
  
```xml  
<filter   
  type="traceFilterClassName"   
  initializeData="data" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="aabc0-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="aabc0-111">Attributes and Elements</span></span>  
 <span data-ttu-id="aabc0-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="aabc0-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="aabc0-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="aabc0-113">Attributes</span></span>  
  
|<span data-ttu-id="aabc0-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="aabc0-114">Attribute</span></span>|<span data-ttu-id="aabc0-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="aabc0-115">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="aabc0-116">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="aabc0-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="aabc0-117">Especifica o tipo do filtro, que deve herdar da classe <xref:System.Diagnostics.TraceFilter>.</span><span class="sxs-lookup"><span data-stu-id="aabc0-117">Specifies the type of the filter, which should inherit from the <xref:System.Diagnostics.TraceFilter> class.</span></span> <span data-ttu-id="aabc0-118">Você pode usar o nome qualificado para namespace do tipo, que corresponde à propriedade <xref:System.Type.FullName%2A> do tipo, ou você pode usar o nome de tipo totalmente qualificado, incluindo as informações de assembly, que correspondem à propriedade <xref:System.Type.AssemblyQualifiedName%2A>.</span><span class="sxs-lookup"><span data-stu-id="aabc0-118">You can use the namespace-qualified name of the type, which corresponds to the type's <xref:System.Type.FullName%2A> property, or you can use the fully qualified type name including the assembly information, which corresponds to the <xref:System.Type.AssemblyQualifiedName%2A> property.</span></span> <span data-ttu-id="aabc0-119">Para obter informações sobre nomes de tipo totalmente qualificados, consulte [especificando nomes de tipo totalmente qualificados](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="aabc0-119">For information about fully qualified type names, see [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="aabc0-120">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="aabc0-120">Optional attribute.</span></span><br /><br /> <span data-ttu-id="aabc0-121">A cadeia de caracteres passada para o construtor da classe de filtro especificada.</span><span class="sxs-lookup"><span data-stu-id="aabc0-121">The string passed to the constructor for the specified filter class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="aabc0-122">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="aabc0-122">Child Elements</span></span>  
 <span data-ttu-id="aabc0-123">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="aabc0-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="aabc0-124">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="aabc0-124">Parent Elements</span></span>  
  
|<span data-ttu-id="aabc0-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="aabc0-125">Element</span></span>|<span data-ttu-id="aabc0-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="aabc0-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="aabc0-127">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="aabc0-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="aabc0-128">Especifica os ouvintes de rastreamento que coletam, armazenam e roteiam mensagens e o nível em que uma opção de rastreamento é definida.</span><span class="sxs-lookup"><span data-stu-id="aabc0-128">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`trace`|<span data-ttu-id="aabc0-129">Contém os ouvintes que coletam, armazenam e roteiam mensagens de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="aabc0-129">Contains listeners that collect, store, and route tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="aabc0-130">Contém ouvintes que coletam, armazenam e roteiam mensagens.</span><span class="sxs-lookup"><span data-stu-id="aabc0-130">Contains listeners that collect, store, and route messages.</span></span> <span data-ttu-id="aabc0-131">Os ouvintes direcionam a saída de rastreamento para um destino apropriado.</span><span class="sxs-lookup"><span data-stu-id="aabc0-131">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`add`|<span data-ttu-id="aabc0-132">Adiciona um ouvinte na coleção `Listeners`.</span><span class="sxs-lookup"><span data-stu-id="aabc0-132">Adds a listener to the `Listeners` collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aabc0-133">Comentários</span><span class="sxs-lookup"><span data-stu-id="aabc0-133">Remarks</span></span>  
 <span data-ttu-id="aabc0-134">O elemento `<filter>` deve estar contido em um elemento `<add>` para um ouvinte de rastreamento que especifica o tipo do ouvinte, não apenas o nome de um ouvinte definido em um [> de @no__t 3sharedListeners](sharedlisteners-element.md).</span><span class="sxs-lookup"><span data-stu-id="aabc0-134">The `<filter>` element must be contained in an `<add>` element for a trace listener that specifies the type of the listener, not just the name of a listener defined in a [\<sharedListeners>](sharedlisteners-element.md).</span></span> <span data-ttu-id="aabc0-135">Se o ouvinte for definido em um [> \<sharedListeners](sharedlisteners-element.md), o filtro desse ouvinte deverá ser definido nesse elemento.</span><span class="sxs-lookup"><span data-stu-id="aabc0-135">If the listener is defined in a [\<sharedListeners>](sharedlisteners-element.md), the filter for that listener must be defined in that element.</span></span>  
  
 <span data-ttu-id="aabc0-136">Esse elemento pode ser usado no arquivo de configuração da máquina (Machine. config) e no arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="aabc0-136">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aabc0-137">Exemplo</span><span class="sxs-lookup"><span data-stu-id="aabc0-137">Example</span></span>  
 <span data-ttu-id="aabc0-138">O exemplo a seguir mostra como usar o elemento `<filter>` para adicionar um filtro ao ouvinte `console` na coleção `Listeners` para rastreamento, especificando o nível de evento de filtro como `Error`.</span><span class="sxs-lookup"><span data-stu-id="aabc0-138">The following example shows how to use the `<filter>` element to add a filter to the listener `console` in the `Listeners` collection for trace, specifying the filter event level as `Error`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="aabc0-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="aabc0-139">See also</span></span>

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.TraceListener.Filter%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.TraceFilter>
- [<span data-ttu-id="aabc0-140">Esquema de configurações de rastreamento e depuração</span><span class="sxs-lookup"><span data-stu-id="aabc0-140">Trace and Debug Settings Schema</span></span>](index.md)
