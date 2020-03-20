---
title: <filter>Elemento <add> para <listeners> para para<trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/add/filter
helpviewer_keywords:
- initializeData attribute
- filter element for <add> for <listeners> for <trace>
- <filter> element for <add> for <listeners> for <trace>
ms.assetid: eb9c18f5-dfa8-47c5-b91b-e4b93e76e1cc
ms.openlocfilehash: b6c2c2bf7fe953a75f9d8129039ef33b4d8a3f56
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153460"
---
# <a name="filter-element-for-add-for-listeners-for-trace"></a><span data-ttu-id="bb243-102">\<filtrar> \<Element \<para adicionar \<> para ouvintes> para rastrear></span><span class="sxs-lookup"><span data-stu-id="bb243-102">\<filter> Element for \<add> for \<listeners> for \<trace></span></span>
<span data-ttu-id="bb243-103">Adiciona um filtro a um `Listeners` ouvinte na coleção para um rastreamento.</span><span class="sxs-lookup"><span data-stu-id="bb243-103">Adds a filter to a listener in the `Listeners` collection for a trace.</span></span>  

<span data-ttu-id="bb243-104">[**\<>de configuração**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="bb243-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="bb243-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="bb243-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>\
<span data-ttu-id="bb243-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<traçar>**](trace-element.md)</span><span class="sxs-lookup"><span data-stu-id="bb243-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<trace>**](trace-element.md)</span></span>\
<span data-ttu-id="bb243-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<ouvintes>**](listeners-element-for-trace.md)</span><span class="sxs-lookup"><span data-stu-id="bb243-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-trace.md)</span></span>\
<span data-ttu-id="bb243-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<adicionar>**](add-element-for-listeners-for-trace.md)</span><span class="sxs-lookup"><span data-stu-id="bb243-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-element-for-listeners-for-trace.md)</span></span>\
<span data-ttu-id="bb243-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>de filtro**</span><span class="sxs-lookup"><span data-stu-id="bb243-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filter>**</span></span>

## <a name="syntax"></a><span data-ttu-id="bb243-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bb243-110">Syntax</span></span>  
  
```xml  
<filter
  type="traceFilterClassName"
  initializeData="data" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bb243-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="bb243-111">Attributes and Elements</span></span>  
 <span data-ttu-id="bb243-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="bb243-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bb243-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="bb243-113">Attributes</span></span>  
  
|<span data-ttu-id="bb243-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="bb243-114">Attribute</span></span>|<span data-ttu-id="bb243-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="bb243-115">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="bb243-116">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="bb243-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="bb243-117">Especifica o tipo do filtro, que <xref:System.Diagnostics.TraceFilter> deve herdar da classe.</span><span class="sxs-lookup"><span data-stu-id="bb243-117">Specifies the type of the filter, which should inherit from the <xref:System.Diagnostics.TraceFilter> class.</span></span> <span data-ttu-id="bb243-118">Você pode usar o nome qualificado do tipo, que corresponde <xref:System.Type.FullName%2A> à propriedade do tipo, ou pode usar o nome do <xref:System.Type.AssemblyQualifiedName%2A> tipo totalmente qualificado, incluindo as informações de montagem, que correspondem à propriedade.</span><span class="sxs-lookup"><span data-stu-id="bb243-118">You can use the namespace-qualified name of the type, which corresponds to the type's <xref:System.Type.FullName%2A> property, or you can use the fully qualified type name including the assembly information, which corresponds to the <xref:System.Type.AssemblyQualifiedName%2A> property.</span></span> <span data-ttu-id="bb243-119">Para obter informações sobre nomes de tipo totalmente qualificados, consulte [Especificando nomes de tipo totalmente qualificados](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="bb243-119">For information about fully qualified type names, see [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="bb243-120">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="bb243-120">Optional attribute.</span></span><br /><br /> <span data-ttu-id="bb243-121">A seqüência passou para o construtor para a classe de filtro especificada.</span><span class="sxs-lookup"><span data-stu-id="bb243-121">The string passed to the constructor for the specified filter class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bb243-122">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="bb243-122">Child Elements</span></span>  
 <span data-ttu-id="bb243-123">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="bb243-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bb243-124">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="bb243-124">Parent Elements</span></span>  
  
|<span data-ttu-id="bb243-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="bb243-125">Element</span></span>|<span data-ttu-id="bb243-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="bb243-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="bb243-127">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="bb243-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="bb243-128">Especifica os ouvintes de rastreamento que coletam, armazenam e roteiam mensagens e o nível em que uma opção de rastreamento é definida.</span><span class="sxs-lookup"><span data-stu-id="bb243-128">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`trace`|<span data-ttu-id="bb243-129">Contém os ouvintes que coletam, armazenam e roteiam mensagens de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="bb243-129">Contains listeners that collect, store, and route tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="bb243-130">Contém ouvintes que coletam, armazenam e encaminham mensagens.</span><span class="sxs-lookup"><span data-stu-id="bb243-130">Contains listeners that collect, store, and route messages.</span></span> <span data-ttu-id="bb243-131">Os ouvintes direcionam a saída de rastreamento para um alvo apropriado.</span><span class="sxs-lookup"><span data-stu-id="bb243-131">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`add`|<span data-ttu-id="bb243-132">Adiciona um ouvinte na coleção `Listeners`.</span><span class="sxs-lookup"><span data-stu-id="bb243-132">Adds a listener to the `Listeners` collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bb243-133">Comentários</span><span class="sxs-lookup"><span data-stu-id="bb243-133">Remarks</span></span>  
 <span data-ttu-id="bb243-134">O `<filter>` elemento deve ser `<add>` contido em um elemento para um ouvinte de rastreamento que especifique o tipo do ouvinte, não apenas o nome de um ouvinte definido em um [ \<>de Ouvintes compartilhados ](sharedlisteners-element.md).</span><span class="sxs-lookup"><span data-stu-id="bb243-134">The `<filter>` element must be contained in an `<add>` element for a trace listener that specifies the type of the listener, not just the name of a listener defined in a [\<sharedListeners>](sharedlisteners-element.md).</span></span> <span data-ttu-id="bb243-135">Se o ouvinte for definido em um [ \<>de Ouvintes compartilhados, ](sharedlisteners-element.md)o filtro para esse ouvinte deve ser definido nesse elemento.</span><span class="sxs-lookup"><span data-stu-id="bb243-135">If the listener is defined in a [\<sharedListeners>](sharedlisteners-element.md), the filter for that listener must be defined in that element.</span></span>  
  
 <span data-ttu-id="bb243-136">Esse elemento pode ser usado no arquivo de configuração da máquina (Machine.config) e no arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="bb243-136">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bb243-137">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bb243-137">Example</span></span>  
 <span data-ttu-id="bb243-138">O exemplo a seguir `<filter>` mostra como usar o elemento `console` para `Listeners` adicionar um filtro ao ouvinte `Error`na coleção para rastreamento, especificando o nível de evento do filtro como .</span><span class="sxs-lookup"><span data-stu-id="bb243-138">The following example shows how to use the `<filter>` element to add a filter to the listener `console` in the `Listeners` collection for trace, specifying the filter event level as `Error`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="bb243-139">Confira também</span><span class="sxs-lookup"><span data-stu-id="bb243-139">See also</span></span>

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.TraceListener.Filter%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.TraceFilter>
- [<span data-ttu-id="bb243-140">Esquema de configurações de rastreamento e depuração</span><span class="sxs-lookup"><span data-stu-id="bb243-140">Trace and Debug Settings Schema</span></span>](index.md)
