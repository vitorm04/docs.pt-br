---
title: Elemento <filter> para <add> para <sharedListeners>
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
ms.openlocfilehash: 4e92f80e9f6069b5fa70501e13a55d5a6fe95e7a
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697319"
---
# <a name="filter-element-for-add-for-sharedlisteners"></a><span data-ttu-id="8d0bd-102">\<filter > elemento para > \<add para \<sharedListeners ></span><span class="sxs-lookup"><span data-stu-id="8d0bd-102">\<filter> Element for \<add> for \<sharedListeners></span></span>
<span data-ttu-id="8d0bd-103">Adiciona um filtro a um ouvinte na coleção `sharedListeners`.</span><span class="sxs-lookup"><span data-stu-id="8d0bd-103">Adds a filter to a listener in the `sharedListeners` collection.</span></span>  
  
[<span data-ttu-id="8d0bd-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="8d0bd-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="8d0bd-105">&nbsp; @ no__t-1[ **\<System. Diagnostics >** ](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="8d0bd-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>  
<span data-ttu-id="8d0bd-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<sharedListeners >** ](sharedlisteners-element.md)</span><span class="sxs-lookup"><span data-stu-id="8d0bd-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sharedListeners>**](sharedlisteners-element.md)</span></span>  
<span data-ttu-id="8d0bd-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5[ **\<add >** ](add-element-for-sharedlisteners.md)</span><span class="sxs-lookup"><span data-stu-id="8d0bd-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-element-for-sharedlisteners.md)</span></span>  
<span data-ttu-id="8d0bd-108">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 @ no__t-7 **\<filter >**</span><span class="sxs-lookup"><span data-stu-id="8d0bd-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filter>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d0bd-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8d0bd-109">Syntax</span></span>  
  
```xml  
<filter type="System.Diagnostics.EventTypeFilter"   
  initializeData="Warning" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8d0bd-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="8d0bd-110">Attributes and Elements</span></span>  
 <span data-ttu-id="8d0bd-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="8d0bd-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8d0bd-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="8d0bd-112">Attributes</span></span>  
  
|<span data-ttu-id="8d0bd-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="8d0bd-113">Attribute</span></span>|<span data-ttu-id="8d0bd-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="8d0bd-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8d0bd-115">**type**</span><span class="sxs-lookup"><span data-stu-id="8d0bd-115">**type**</span></span>|<span data-ttu-id="8d0bd-116">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="8d0bd-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="8d0bd-117">Especifica o tipo do filtro.</span><span class="sxs-lookup"><span data-stu-id="8d0bd-117">Specifies the type of the filter.</span></span> <span data-ttu-id="8d0bd-118">Você pode usar apenas o nome completo do tipo (no formato da propriedade <xref:System.Type.FullName%2A?displayProperty=nameWithType>) ou pode usar o nome do tipo totalmente qualificado, incluindo as informações do assembly (no formato da propriedade <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType>).</span><span class="sxs-lookup"><span data-stu-id="8d0bd-118">You can use only the full name of the type (in the format of the <xref:System.Type.FullName%2A?displayProperty=nameWithType> property), or you can use the fully qualified type name including the assembly information (in the format of the <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType> property).</span></span> <span data-ttu-id="8d0bd-119">Para obter informações sobre como criar um nome de tipo totalmente qualificado, consulte [especificando nomes de tipo totalmente qualificados](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="8d0bd-119">For information on creating a fully qualified type name, see [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|<span data-ttu-id="8d0bd-120">**initializeData**</span><span class="sxs-lookup"><span data-stu-id="8d0bd-120">**initializeData**</span></span>|<span data-ttu-id="8d0bd-121">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="8d0bd-121">Optional attribute.</span></span><br /><br /> <span data-ttu-id="8d0bd-122">A cadeia de caracteres passada para o construtor para a classe especificada.</span><span class="sxs-lookup"><span data-stu-id="8d0bd-122">The string passed to the constructor for the specified class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8d0bd-123">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="8d0bd-123">Child Elements</span></span>  
 <span data-ttu-id="8d0bd-124">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="8d0bd-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8d0bd-125">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="8d0bd-125">Parent Elements</span></span>  
  
|<span data-ttu-id="8d0bd-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="8d0bd-126">Element</span></span>|<span data-ttu-id="8d0bd-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="8d0bd-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="8d0bd-128">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8d0bd-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="8d0bd-129">Especifica os ouvintes de rastreamento que coletam, armazenam e roteiam mensagens e o nível em que uma opção de rastreamento é definida.</span><span class="sxs-lookup"><span data-stu-id="8d0bd-129">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sharedListeners`|<span data-ttu-id="8d0bd-130">Uma coleção de ouvintes que qualquer elemento de origem ou de rastreamento pode referenciar.</span><span class="sxs-lookup"><span data-stu-id="8d0bd-130">A collection of listeners that any source or trace element can reference.</span></span>|  
|`add`|<span data-ttu-id="8d0bd-131">Adiciona um ouvinte à coleção **sharedListeners** .</span><span class="sxs-lookup"><span data-stu-id="8d0bd-131">Adds a listener to the **sharedListeners** collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8d0bd-132">Comentários</span><span class="sxs-lookup"><span data-stu-id="8d0bd-132">Remarks</span></span>  
 <span data-ttu-id="8d0bd-133">Se um ouvinte for definido em um elemento `<add>` do elemento `<sharedListeners>`, o filtro desse ouvinte deverá ser definido em um elemento `<filter>` que seja filho do elemento `<add>`.</span><span class="sxs-lookup"><span data-stu-id="8d0bd-133">If a listener is defined in an `<add>` element of the `<sharedListeners>` element, the filter for that listener should be defined in a `<filter>` element that is a child of the `<add>` element.</span></span>  
  
 <span data-ttu-id="8d0bd-134">Esse elemento pode ser usado no arquivo de configuração da máquina (Machine. config) e no arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8d0bd-134">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8d0bd-135">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8d0bd-135">Example</span></span>  
 <span data-ttu-id="8d0bd-136">O exemplo a seguir mostra como usar o elemento `<filter>` para adicionar um filtro ao ouvinte de rastreamento `console` na coleção `sharedListeners`.</span><span class="sxs-lookup"><span data-stu-id="8d0bd-136">The following example shows how to use the `<filter>` element to add a filter to the trace listener `console` in the `sharedListeners` collection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8d0bd-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8d0bd-137">See also</span></span>

- <xref:System.Diagnostics.TraceFilter>
- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.TraceSource>
- [<span data-ttu-id="8d0bd-138">Esquema de configurações de rastreamento e depuração</span><span class="sxs-lookup"><span data-stu-id="8d0bd-138">Trace and Debug Settings Schema</span></span>](index.md)
