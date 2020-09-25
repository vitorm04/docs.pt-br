---
title: <filter>Elemento para <add> para para <listeners><trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/add/filter
helpviewer_keywords:
- initializeData attribute
- filter element for <add> for <listeners> for <trace>
- <filter> element for <add> for <listeners> for <trace>
ms.assetid: eb9c18f5-dfa8-47c5-b91b-e4b93e76e1cc
ms.openlocfilehash: d856fc742bc2dca51095ce0866dcbfdaadadf64d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91176104"
---
# <a name="filter-element-for-add-for-listeners-for-trace"></a><span data-ttu-id="a8029-102">\<filter>Elemento para \<add> para para \<listeners>\<trace></span><span class="sxs-lookup"><span data-stu-id="a8029-102">\<filter> Element for \<add> for \<listeners> for \<trace></span></span>

<span data-ttu-id="a8029-103">Adiciona um filtro a um ouvinte na `Listeners` coleção de um rastreamento.</span><span class="sxs-lookup"><span data-stu-id="a8029-103">Adds a filter to a listener in the `Listeners` collection for a trace.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<trace>**](trace-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-trace.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-element-for-listeners-for-trace.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filter>**

## <a name="syntax"></a><span data-ttu-id="a8029-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a8029-104">Syntax</span></span>  
  
```xml  
<filter
  type="traceFilterClassName"
  initializeData="data" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a8029-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="a8029-105">Attributes and Elements</span></span>  

 <span data-ttu-id="a8029-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="a8029-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a8029-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="a8029-107">Attributes</span></span>  
  
|<span data-ttu-id="a8029-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="a8029-108">Attribute</span></span>|<span data-ttu-id="a8029-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="a8029-109">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="a8029-110">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="a8029-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="a8029-111">Especifica o tipo do filtro, que deve herdar da <xref:System.Diagnostics.TraceFilter> classe.</span><span class="sxs-lookup"><span data-stu-id="a8029-111">Specifies the type of the filter, which should inherit from the <xref:System.Diagnostics.TraceFilter> class.</span></span> <span data-ttu-id="a8029-112">Você pode usar o nome qualificado de namespace do tipo, que corresponde à propriedade do tipo <xref:System.Type.FullName%2A> , ou pode usar o nome de tipo totalmente qualificado, incluindo as informações de assembly, que correspondem à <xref:System.Type.AssemblyQualifiedName%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="a8029-112">You can use the namespace-qualified name of the type, which corresponds to the type's <xref:System.Type.FullName%2A> property, or you can use the fully qualified type name including the assembly information, which corresponds to the <xref:System.Type.AssemblyQualifiedName%2A> property.</span></span> <span data-ttu-id="a8029-113">Para obter informações sobre nomes de tipo totalmente qualificados, consulte [especificando nomes de tipo totalmente qualificados](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="a8029-113">For information about fully qualified type names, see [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="a8029-114">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="a8029-114">Optional attribute.</span></span><br /><br /> <span data-ttu-id="a8029-115">A cadeia de caracteres passada para o construtor da classe de filtro especificada.</span><span class="sxs-lookup"><span data-stu-id="a8029-115">The string passed to the constructor for the specified filter class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a8029-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="a8029-116">Child Elements</span></span>  

 <span data-ttu-id="a8029-117">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="a8029-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a8029-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="a8029-118">Parent Elements</span></span>  
  
|<span data-ttu-id="a8029-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="a8029-119">Element</span></span>|<span data-ttu-id="a8029-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="a8029-120">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="a8029-121">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a8029-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="a8029-122">Especifica os ouvintes de rastreamento que coletam, armazenam e roteiam mensagens e o nível em que uma opção de rastreamento é definida.</span><span class="sxs-lookup"><span data-stu-id="a8029-122">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`trace`|<span data-ttu-id="a8029-123">Contém os ouvintes que coletam, armazenam e roteiam mensagens de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="a8029-123">Contains listeners that collect, store, and route tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="a8029-124">Contém ouvintes que coletam, armazenam e roteiam mensagens.</span><span class="sxs-lookup"><span data-stu-id="a8029-124">Contains listeners that collect, store, and route messages.</span></span> <span data-ttu-id="a8029-125">Os ouvintes direcionam a saída de rastreamento para um destino apropriado.</span><span class="sxs-lookup"><span data-stu-id="a8029-125">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`add`|<span data-ttu-id="a8029-126">Adiciona um ouvinte na coleção `Listeners`.</span><span class="sxs-lookup"><span data-stu-id="a8029-126">Adds a listener to the `Listeners` collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a8029-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="a8029-127">Remarks</span></span>  

 <span data-ttu-id="a8029-128">O `<filter>` elemento deve estar contido em um `<add>` elemento para um ouvinte de rastreamento que especifica o tipo do ouvinte, não apenas o nome de um ouvinte definido em um [\<sharedListeners>](sharedlisteners-element.md) .</span><span class="sxs-lookup"><span data-stu-id="a8029-128">The `<filter>` element must be contained in an `<add>` element for a trace listener that specifies the type of the listener, not just the name of a listener defined in a [\<sharedListeners>](sharedlisteners-element.md).</span></span> <span data-ttu-id="a8029-129">Se o ouvinte for definido em um [\<sharedListeners>](sharedlisteners-element.md) , o filtro para esse ouvinte deverá ser definido nesse elemento.</span><span class="sxs-lookup"><span data-stu-id="a8029-129">If the listener is defined in a [\<sharedListeners>](sharedlisteners-element.md), the filter for that listener must be defined in that element.</span></span>  
  
 <span data-ttu-id="a8029-130">Esse elemento pode ser usado no arquivo de configuração da máquina (Machine.config) e no arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a8029-130">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a8029-131">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a8029-131">Example</span></span>  

 <span data-ttu-id="a8029-132">O exemplo a seguir mostra como usar o `<filter>` elemento para adicionar um filtro ao ouvinte `console` na `Listeners` coleção para rastreamento, especificando o nível de evento de filtro como `Error` .</span><span class="sxs-lookup"><span data-stu-id="a8029-132">The following example shows how to use the `<filter>` element to add a filter to the listener `console` in the `Listeners` collection for trace, specifying the filter event level as `Error`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a8029-133">Confira também</span><span class="sxs-lookup"><span data-stu-id="a8029-133">See also</span></span>

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.TraceListener.Filter%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.TraceFilter>
- [<span data-ttu-id="a8029-134">Esquema de configurações de rastreamento e depuração</span><span class="sxs-lookup"><span data-stu-id="a8029-134">Trace and Debug Settings Schema</span></span>](index.md)
