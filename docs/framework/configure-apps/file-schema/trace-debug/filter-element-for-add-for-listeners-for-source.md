---
title: <filter>Elemento <add> para <listeners> para para<source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#filter
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/add/filter
helpviewer_keywords:
- initializeData attribute
- <filter> element for <add> for <listeners> for <source>
- filter element for <add> for <listeners> for <source>
ms.assetid: 15808b80-4579-4c25-b385-178cfdf154ba
ms.openlocfilehash: 0cb668782de263d5f784691f46cb8b74541d942b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153510"
---
# <a name="filter-element-for-add-for-listeners-for-source"></a><span data-ttu-id="81f33-102">\<filtrar> \<Elemento \<para adicionar \<> para os ouvintes> para> de origem</span><span class="sxs-lookup"><span data-stu-id="81f33-102">\<filter> Element for \<add> for \<listeners> for \<source></span></span>
<span data-ttu-id="81f33-103">Adiciona um filtro a um ouvinte na coleção `Listeners` de uma origem de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="81f33-103">Adds a filter to a listener in the `Listeners` collection for a trace source.</span></span>  

<span data-ttu-id="81f33-104">[**\<>de configuração**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="81f33-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="81f33-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="81f33-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>\
<span data-ttu-id="81f33-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<fontes>**](sources-element.md)</span><span class="sxs-lookup"><span data-stu-id="81f33-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)</span></span>\
<span data-ttu-id="81f33-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>fonte**](source-element.md)</span><span class="sxs-lookup"><span data-stu-id="81f33-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<source>**](source-element.md)</span></span>\
<span data-ttu-id="81f33-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<ouvintes>**](listeners-element-for-source.md)</span><span class="sxs-lookup"><span data-stu-id="81f33-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-source.md)</span></span>\
<span data-ttu-id="81f33-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<adicionar>**](add-element-for-listeners-for-source.md)</span><span class="sxs-lookup"><span data-stu-id="81f33-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-element-for-listeners-for-source.md)</span></span>\
<span data-ttu-id="81f33-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>de filtro**</span><span class="sxs-lookup"><span data-stu-id="81f33-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filter>**</span></span>

## <a name="syntax"></a><span data-ttu-id="81f33-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="81f33-111">Syntax</span></span>  
  
```xml  
<filter
  type="traceFilterClassName"
  initializeData="data" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="81f33-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="81f33-112">Attributes and Elements</span></span>  
 <span data-ttu-id="81f33-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="81f33-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="81f33-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="81f33-114">Attributes</span></span>  
  
|<span data-ttu-id="81f33-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="81f33-115">Attribute</span></span>|<span data-ttu-id="81f33-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="81f33-116">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="81f33-117">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="81f33-117">Required attribute.</span></span><br /><br /> <span data-ttu-id="81f33-118">Especifica o tipo do filtro, que <xref:System.Diagnostics.TraceFilter> deve herdar da classe.</span><span class="sxs-lookup"><span data-stu-id="81f33-118">Specifies the type of the filter, which should inherit from the <xref:System.Diagnostics.TraceFilter> class.</span></span> <span data-ttu-id="81f33-119">Você pode usar o nome qualificado do tipo, que corresponde <xref:System.Type.FullName%2A> à propriedade do tipo, ou pode usar o nome do <xref:System.Type.AssemblyQualifiedName%2A> tipo totalmente qualificado, incluindo as informações de montagem, que correspondem à propriedade.</span><span class="sxs-lookup"><span data-stu-id="81f33-119">You can use the namespace-qualified name of the type, which corresponds to the type's <xref:System.Type.FullName%2A> property, or you can use the fully qualified type name including the assembly information, which corresponds to the <xref:System.Type.AssemblyQualifiedName%2A> property.</span></span> <span data-ttu-id="81f33-120">Para obter informações sobre nomes de tipo totalmente qualificados, consulte [Especificando nomes de tipo totalmente qualificados](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="81f33-120">For information about fully qualified type names, see [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="81f33-121">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="81f33-121">Optional attribute.</span></span><br /><br /> <span data-ttu-id="81f33-122">A seqüência passou para o construtor para a classe de filtro especificada.</span><span class="sxs-lookup"><span data-stu-id="81f33-122">The string passed to the constructor for the specified filter class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="81f33-123">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="81f33-123">Child Elements</span></span>  
 <span data-ttu-id="81f33-124">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="81f33-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="81f33-125">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="81f33-125">Parent Elements</span></span>  
  
|<span data-ttu-id="81f33-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="81f33-126">Element</span></span>|<span data-ttu-id="81f33-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="81f33-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="81f33-128">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="81f33-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="81f33-129">Especifica os ouvintes de rastreamento que coletam, armazenam e roteiam mensagens e o nível em que uma opção de rastreamento é definida.</span><span class="sxs-lookup"><span data-stu-id="81f33-129">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="81f33-130">Contém as origens de rastreamento que iniciam as mensagens de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="81f33-130">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="81f33-131">Especifica uma origem de rastreamento que inicia as mensagens de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="81f33-131">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="81f33-132">Contém ouvintes que coletam, armazenam e encaminham mensagens.</span><span class="sxs-lookup"><span data-stu-id="81f33-132">Contains listeners that collect, store, and route messages.</span></span> <span data-ttu-id="81f33-133">Os ouvintes direcionam a saída de rastreamento para um alvo apropriado.</span><span class="sxs-lookup"><span data-stu-id="81f33-133">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`add`|<span data-ttu-id="81f33-134">Adiciona um ouvinte na coleção `Listeners` de uma origem de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="81f33-134">Adds a listener to the `Listeners` collection for a trace source.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="81f33-135">Comentários</span><span class="sxs-lookup"><span data-stu-id="81f33-135">Remarks</span></span>  
 <span data-ttu-id="81f33-136">O `<filter>` elemento deve ser `<add>` contido em um elemento para um ouvinte de origem de rastreamento que especifique o tipo do ouvinte, não apenas o nome de um ouvinte definido em um [ \<>de ouvintes compartilhados ](sharedlisteners-element.md).</span><span class="sxs-lookup"><span data-stu-id="81f33-136">The `<filter>` element must be contained in an `<add>` element for a trace source listener that specifies the type of the listener, not just the name of a listener defined in a [\<sharedListeners>](sharedlisteners-element.md).</span></span> <span data-ttu-id="81f33-137">Se o ouvinte for definido em um [ \<>de Ouvintes compartilhados, ](sharedlisteners-element.md)o filtro para esse ouvinte deve ser definido nesse elemento.</span><span class="sxs-lookup"><span data-stu-id="81f33-137">If the listener is defined in a [\<sharedListeners>](sharedlisteners-element.md), the filter for that listener must be defined in that element.</span></span>  
  
 <span data-ttu-id="81f33-138">Esse elemento pode ser usado no arquivo de configuração da máquina (Machine.config) e no arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="81f33-138">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="81f33-139">Exemplo</span><span class="sxs-lookup"><span data-stu-id="81f33-139">Example</span></span>  
 <span data-ttu-id="81f33-140">O exemplo a seguir `<filter>` mostra como usar o elemento `console` para `Listeners` adicionar um `myTraceSource`filtro ao ouvinte na `Error`coleção para a origem do rastreamento, especificando o nível de evento do filtro como .</span><span class="sxs-lookup"><span data-stu-id="81f33-140">The following example shows how to use the `<filter>` element to add a filter to the listener `console` in the `Listeners` collection for the trace source `myTraceSource`, specifying the filter event level as `Error`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="81f33-141">Confira também</span><span class="sxs-lookup"><span data-stu-id="81f33-141">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.TraceListener.Filter%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.TraceFilter>
- [<span data-ttu-id="81f33-142">Esquema de configurações de rastreamento e depuração</span><span class="sxs-lookup"><span data-stu-id="81f33-142">Trace and Debug Settings Schema</span></span>](index.md)
