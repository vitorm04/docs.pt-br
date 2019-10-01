---
title: Elemento <filter> para <add> para <listeners> para <source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#filter
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/add/filter
helpviewer_keywords:
- initializeData attribute
- <filter> element for <add> for <listeners> for <source>
- filter element for <add> for <listeners> for <source>
ms.assetid: 15808b80-4579-4c25-b385-178cfdf154ba
ms.openlocfilehash: ec288685f47c8a35e2371c31d359b604a4967196
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697172"
---
# <a name="filter-element-for-add-for-listeners-for-source"></a><span data-ttu-id="f3a27-102">\<filter > o elemento para @no__t > @no__t > para @no__t 3source ></span><span class="sxs-lookup"><span data-stu-id="f3a27-102">\<filter> Element for \<add> for \<listeners> for \<source></span></span>
<span data-ttu-id="f3a27-103">Adiciona um filtro a um ouvinte na coleção `Listeners` de uma origem de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="f3a27-103">Adds a filter to a listener in the `Listeners` collection for a trace source.</span></span>  
  
[<span data-ttu-id="f3a27-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="f3a27-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="f3a27-105">&nbsp; @ no__t-1[ **\<System. Diagnostics >** ](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="f3a27-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>  
<span data-ttu-id="f3a27-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<sources >** ](sources-element.md)</span><span class="sxs-lookup"><span data-stu-id="f3a27-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)</span></span>  
<span data-ttu-id="f3a27-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5[ **\<source >** ](source-element.md)</span><span class="sxs-lookup"><span data-stu-id="f3a27-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<source>**](source-element.md)</span></span>  
<span data-ttu-id="f3a27-108">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 @ no__t-7[ **&nbsp;0listeners >** ](listeners-element-for-source.md)</span><span class="sxs-lookup"><span data-stu-id="f3a27-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-source.md)</span></span>  
<span data-ttu-id="f3a27-109">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 @ no__t-7 @ no__t-8 @ no__t-9[ **&nbsp;2Add >** ](add-element-for-listeners-for-source.md)</span><span class="sxs-lookup"><span data-stu-id="f3a27-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-element-for-listeners-for-source.md)</span></span>  
<span data-ttu-id="f3a27-110">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 @ no__t-7 @ no__t-8 @ no__t-9 @ no__t-10 @ no__t-11 **&nbsp;3filter >**</span><span class="sxs-lookup"><span data-stu-id="f3a27-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filter>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3a27-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f3a27-111">Syntax</span></span>  
  
```xml  
<filter   
  type="traceFilterClassName"   
  initializeData="data" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f3a27-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="f3a27-112">Attributes and Elements</span></span>  
 <span data-ttu-id="f3a27-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="f3a27-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f3a27-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="f3a27-114">Attributes</span></span>  
  
|<span data-ttu-id="f3a27-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="f3a27-115">Attribute</span></span>|<span data-ttu-id="f3a27-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="f3a27-116">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="f3a27-117">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="f3a27-117">Required attribute.</span></span><br /><br /> <span data-ttu-id="f3a27-118">Especifica o tipo do filtro, que deve herdar da classe <xref:System.Diagnostics.TraceFilter>.</span><span class="sxs-lookup"><span data-stu-id="f3a27-118">Specifies the type of the filter, which should inherit from the <xref:System.Diagnostics.TraceFilter> class.</span></span> <span data-ttu-id="f3a27-119">Você pode usar o nome qualificado para namespace do tipo, que corresponde à propriedade <xref:System.Type.FullName%2A> do tipo, ou você pode usar o nome de tipo totalmente qualificado, incluindo as informações de assembly, que correspondem à propriedade <xref:System.Type.AssemblyQualifiedName%2A>.</span><span class="sxs-lookup"><span data-stu-id="f3a27-119">You can use the namespace-qualified name of the type, which corresponds to the type's <xref:System.Type.FullName%2A> property, or you can use the fully qualified type name including the assembly information, which corresponds to the <xref:System.Type.AssemblyQualifiedName%2A> property.</span></span> <span data-ttu-id="f3a27-120">Para obter informações sobre nomes de tipo totalmente qualificados, consulte [especificando nomes de tipo totalmente qualificados](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="f3a27-120">For information about fully qualified type names, see [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="f3a27-121">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="f3a27-121">Optional attribute.</span></span><br /><br /> <span data-ttu-id="f3a27-122">A cadeia de caracteres passada para o construtor da classe de filtro especificada.</span><span class="sxs-lookup"><span data-stu-id="f3a27-122">The string passed to the constructor for the specified filter class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f3a27-123">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="f3a27-123">Child Elements</span></span>  
 <span data-ttu-id="f3a27-124">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="f3a27-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f3a27-125">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="f3a27-125">Parent Elements</span></span>  
  
|<span data-ttu-id="f3a27-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="f3a27-126">Element</span></span>|<span data-ttu-id="f3a27-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="f3a27-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="f3a27-128">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f3a27-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="f3a27-129">Especifica os ouvintes de rastreamento que coletam, armazenam e roteiam mensagens e o nível em que uma opção de rastreamento é definida.</span><span class="sxs-lookup"><span data-stu-id="f3a27-129">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="f3a27-130">Contém as origens de rastreamento que iniciam as mensagens de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="f3a27-130">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="f3a27-131">Especifica uma origem de rastreamento que inicia as mensagens de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="f3a27-131">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="f3a27-132">Contém ouvintes que coletam, armazenam e roteiam mensagens.</span><span class="sxs-lookup"><span data-stu-id="f3a27-132">Contains listeners that collect, store, and route messages.</span></span> <span data-ttu-id="f3a27-133">Os ouvintes direcionam a saída de rastreamento para um destino apropriado.</span><span class="sxs-lookup"><span data-stu-id="f3a27-133">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`add`|<span data-ttu-id="f3a27-134">Adiciona um ouvinte na coleção `Listeners` de uma origem de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="f3a27-134">Adds a listener to the `Listeners` collection for a trace source.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f3a27-135">Comentários</span><span class="sxs-lookup"><span data-stu-id="f3a27-135">Remarks</span></span>  
 <span data-ttu-id="f3a27-136">O elemento `<filter>` deve estar contido em um elemento `<add>` para um ouvinte de origem de rastreamento que especifica o tipo do ouvinte, não apenas o nome de um ouvinte definido em um [> de @no__t 3sharedListeners](sharedlisteners-element.md).</span><span class="sxs-lookup"><span data-stu-id="f3a27-136">The `<filter>` element must be contained in an `<add>` element for a trace source listener that specifies the type of the listener, not just the name of a listener defined in a [\<sharedListeners>](sharedlisteners-element.md).</span></span> <span data-ttu-id="f3a27-137">Se o ouvinte for definido em um [> \<sharedListeners](sharedlisteners-element.md), o filtro desse ouvinte deverá ser definido nesse elemento.</span><span class="sxs-lookup"><span data-stu-id="f3a27-137">If the listener is defined in a [\<sharedListeners>](sharedlisteners-element.md), the filter for that listener must be defined in that element.</span></span>  
  
 <span data-ttu-id="f3a27-138">Esse elemento pode ser usado no arquivo de configuração da máquina (Machine. config) e no arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f3a27-138">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f3a27-139">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f3a27-139">Example</span></span>  
 <span data-ttu-id="f3a27-140">O exemplo a seguir mostra como usar o elemento `<filter>` para adicionar um filtro ao ouvinte `console` na coleção `Listeners` para a origem de rastreamento `myTraceSource`, especificando o nível de evento de filtro como `Error`.</span><span class="sxs-lookup"><span data-stu-id="f3a27-140">The following example shows how to use the `<filter>` element to add a filter to the listener `console` in the `Listeners` collection for the trace source `myTraceSource`, specifying the filter event level as `Error`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f3a27-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f3a27-141">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.TraceListener.Filter%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.TraceFilter>
- [<span data-ttu-id="f3a27-142">Esquema de configurações de rastreamento e depuração</span><span class="sxs-lookup"><span data-stu-id="f3a27-142">Trace and Debug Settings Schema</span></span>](index.md)
