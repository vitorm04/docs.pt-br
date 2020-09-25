---
title: <filter> Elemento para <add> para <sharedListeners>
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
ms.openlocfilehash: e140148a342e31d6ade7def8849d8a7738301704
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91173920"
---
# <a name="filter-element-for-add-for-sharedlisteners"></a><span data-ttu-id="e847c-102">\<filter> Elemento para \<add> para \<sharedListeners></span><span class="sxs-lookup"><span data-stu-id="e847c-102">\<filter> Element for \<add> for \<sharedListeners></span></span>

<span data-ttu-id="e847c-103">Adiciona um filtro a um ouvinte na coleção `sharedListeners`.</span><span class="sxs-lookup"><span data-stu-id="e847c-103">Adds a filter to a listener in the `sharedListeners` collection.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sharedListeners>**](sharedlisteners-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-element-for-sharedlisteners.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filter>**

## <a name="syntax"></a><span data-ttu-id="e847c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e847c-104">Syntax</span></span>  
  
```xml  
<filter type="System.Diagnostics.EventTypeFilter"
  initializeData="Warning" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e847c-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="e847c-105">Attributes and Elements</span></span>  

 <span data-ttu-id="e847c-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="e847c-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e847c-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="e847c-107">Attributes</span></span>  
  
|<span data-ttu-id="e847c-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="e847c-108">Attribute</span></span>|<span data-ttu-id="e847c-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="e847c-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e847c-110">**tipo**</span><span class="sxs-lookup"><span data-stu-id="e847c-110">**type**</span></span>|<span data-ttu-id="e847c-111">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="e847c-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="e847c-112">Especifica o tipo do filtro.</span><span class="sxs-lookup"><span data-stu-id="e847c-112">Specifies the type of the filter.</span></span> <span data-ttu-id="e847c-113">Você pode usar apenas o nome completo do tipo (no formato da <xref:System.Type.FullName%2A?displayProperty=nameWithType> Propriedade) ou pode usar o nome do tipo totalmente qualificado, incluindo as informações do assembly (no formato da <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType> Propriedade).</span><span class="sxs-lookup"><span data-stu-id="e847c-113">You can use only the full name of the type (in the format of the <xref:System.Type.FullName%2A?displayProperty=nameWithType> property), or you can use the fully qualified type name including the assembly information (in the format of the <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType> property).</span></span> <span data-ttu-id="e847c-114">Para obter informações sobre como criar um nome de tipo totalmente qualificado, consulte [especificando nomes de tipo totalmente qualificados](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="e847c-114">For information on creating a fully qualified type name, see [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|<span data-ttu-id="e847c-115">**initializeData**</span><span class="sxs-lookup"><span data-stu-id="e847c-115">**initializeData**</span></span>|<span data-ttu-id="e847c-116">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="e847c-116">Optional attribute.</span></span><br /><br /> <span data-ttu-id="e847c-117">A cadeia de caracteres passada para o construtor para a classe especificada.</span><span class="sxs-lookup"><span data-stu-id="e847c-117">The string passed to the constructor for the specified class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e847c-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="e847c-118">Child Elements</span></span>  

 <span data-ttu-id="e847c-119">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="e847c-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e847c-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="e847c-120">Parent Elements</span></span>  
  
|<span data-ttu-id="e847c-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="e847c-121">Element</span></span>|<span data-ttu-id="e847c-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="e847c-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="e847c-123">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e847c-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="e847c-124">Especifica os ouvintes de rastreamento que coletam, armazenam e roteiam mensagens e o nível em que uma opção de rastreamento é definida.</span><span class="sxs-lookup"><span data-stu-id="e847c-124">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sharedListeners`|<span data-ttu-id="e847c-125">Uma coleção de ouvintes que qualquer elemento de origem ou de rastreamento pode referenciar.</span><span class="sxs-lookup"><span data-stu-id="e847c-125">A collection of listeners that any source or trace element can reference.</span></span>|  
|`add`|<span data-ttu-id="e847c-126">Adiciona um ouvinte à coleção **sharedListeners** .</span><span class="sxs-lookup"><span data-stu-id="e847c-126">Adds a listener to the **sharedListeners** collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e847c-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="e847c-127">Remarks</span></span>  

 <span data-ttu-id="e847c-128">Se um ouvinte for definido em um `<add>` elemento do `<sharedListeners>` elemento, o filtro desse ouvinte deverá ser definido em um `<filter>` elemento que seja filho do `<add>` elemento.</span><span class="sxs-lookup"><span data-stu-id="e847c-128">If a listener is defined in an `<add>` element of the `<sharedListeners>` element, the filter for that listener should be defined in a `<filter>` element that is a child of the `<add>` element.</span></span>  
  
 <span data-ttu-id="e847c-129">Esse elemento pode ser usado no arquivo de configuração da máquina (Machine.config) e no arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e847c-129">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e847c-130">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e847c-130">Example</span></span>  

 <span data-ttu-id="e847c-131">O exemplo a seguir mostra como usar o `<filter>` elemento para adicionar um filtro ao ouvinte de rastreamento `console` na `sharedListeners` coleção.</span><span class="sxs-lookup"><span data-stu-id="e847c-131">The following example shows how to use the `<filter>` element to add a filter to the trace listener `console` in the `sharedListeners` collection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e847c-132">Confira também</span><span class="sxs-lookup"><span data-stu-id="e847c-132">See also</span></span>

- <xref:System.Diagnostics.TraceFilter>
- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.TraceSource>
- [<span data-ttu-id="e847c-133">Esquema de configurações de rastreamento e depuração</span><span class="sxs-lookup"><span data-stu-id="e847c-133">Trace and Debug Settings Schema</span></span>](index.md)
