---
title: Elemento <sharedListeners>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#sharedListeners
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sharedListeners
helpviewer_keywords:
- <sharedListeners> element
- listeners
- shared listeners
- trace listeners, <sharedListeners> element
- sharedListeners element
ms.assetid: de200534-19dd-4156-86cf-c50521802c4c
ms.openlocfilehash: b419ecf451b79808e545525c7b8761175f390200
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699299"
---
# <a name="sharedlisteners-element"></a><span data-ttu-id="dd9c0-102">\<sharedListeners > elemento</span><span class="sxs-lookup"><span data-stu-id="dd9c0-102">\<sharedListeners> Element</span></span>
<span data-ttu-id="dd9c0-103">Contém os ouvintes que podem ser referenciados por qualquer elemento de origem ou de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="dd9c0-103">Contains listeners that any source or trace element can reference.</span></span>  <span data-ttu-id="dd9c0-104">Esses ouvintes não recebem nenhum rastreamento por padrão e não é possível recuperar esses ouvintes em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="dd9c0-104">These listeners do not receive any traces by default, and it is not possible to retrieve these listeners at run time.</span></span> <span data-ttu-id="dd9c0-105">Os ouvintes identificados como ouvintes compartilhados podem ser adicionados a fontes ou rastreamentos por nome.</span><span class="sxs-lookup"><span data-stu-id="dd9c0-105">Listeners identified as shared listeners can be added to sources or traces by name.</span></span>  
  
[<span data-ttu-id="dd9c0-106"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="dd9c0-106">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="dd9c0-107">&nbsp; @ no__t-1[ **\<System. Diagnostics >** ](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="dd9c0-107">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>  
<span data-ttu-id="dd9c0-108">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 **\<sharedListeners >**</span><span class="sxs-lookup"><span data-stu-id="dd9c0-108">&nbsp;&nbsp;&nbsp;&nbsp;**\<sharedListeners>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd9c0-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="dd9c0-109">Syntax</span></span>  
  
```xml  
<sharedListeners>   
  <add>...</add>  
</sharedListeners>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dd9c0-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="dd9c0-110">Attributes and Elements</span></span>  
 <span data-ttu-id="dd9c0-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="dd9c0-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dd9c0-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="dd9c0-112">Attributes</span></span>  
 <span data-ttu-id="dd9c0-113">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="dd9c0-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="dd9c0-114">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="dd9c0-114">Child Elements</span></span>  
  
|<span data-ttu-id="dd9c0-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="dd9c0-115">Element</span></span>|<span data-ttu-id="dd9c0-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="dd9c0-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dd9c0-117">\<add></span><span class="sxs-lookup"><span data-stu-id="dd9c0-117">\<add></span></span>](add-element-for-listeners-for-trace.md)|<span data-ttu-id="dd9c0-118">Adiciona um ouvinte na coleção `sharedListeners`.</span><span class="sxs-lookup"><span data-stu-id="dd9c0-118">Adds a listener to the `sharedListeners` collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="dd9c0-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="dd9c0-119">Parent Elements</span></span>  
  
|<span data-ttu-id="dd9c0-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="dd9c0-120">Element</span></span>|<span data-ttu-id="dd9c0-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="dd9c0-121">Description</span></span>|  
|-------------|-----------------|  
|`Configuration`|<span data-ttu-id="dd9c0-122">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="dd9c0-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="dd9c0-123">Especifica o elemento raiz para a seção de configuração ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="dd9c0-123">Specifies the root element for the ASP.NET configuration section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dd9c0-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="dd9c0-124">Remarks</span></span>  
 <span data-ttu-id="dd9c0-125">A adição de um ouvinte à coleção de ouvintes compartilhados não o torna um ouvinte ativo.</span><span class="sxs-lookup"><span data-stu-id="dd9c0-125">Adding a listener to the shared listeners collection does not make it an active listener.</span></span> <span data-ttu-id="dd9c0-126">Ele ainda deve ser adicionado a uma origem de rastreamento ou a um rastreamento adicionando-o à coleção `Listeners` para esse elemento Trace.</span><span class="sxs-lookup"><span data-stu-id="dd9c0-126">It must still be added to a trace source or a trace by adding it to the `Listeners` collection for that trace element.</span></span> <span data-ttu-id="dd9c0-127">As classes de ouvinte no .NET Framework derivam da classe <xref:System.Diagnostics.TraceListener>.</span><span class="sxs-lookup"><span data-stu-id="dd9c0-127">The listener classes in the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span>  
  
 <span data-ttu-id="dd9c0-128">Esse elemento pode ser usado no arquivo de configuração da máquina (Machine. config) e no arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="dd9c0-128">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dd9c0-129">Exemplo</span><span class="sxs-lookup"><span data-stu-id="dd9c0-129">Example</span></span>  
 <span data-ttu-id="dd9c0-130">O exemplo a seguir mostra como usar o elemento `<sharedListeners>` para adicionar o ouvinte `console` à coleção `Listeners` para as classes <xref:System.Diagnostics.TraceSource> e <xref:System.Diagnostics.Trace>.</span><span class="sxs-lookup"><span data-stu-id="dd9c0-130">The following example shows how to use the `<sharedListeners>` element to add the listener `console` to the `Listeners` collection for both the <xref:System.Diagnostics.TraceSource> and <xref:System.Diagnostics.Trace> classes.</span></span> <span data-ttu-id="dd9c0-131">O ouvinte de rastreamento do console grava informações de rastreamento no console por meio de chamadas para <xref:System.Diagnostics.TraceSource> ou <xref:System.Diagnostics.Trace>.</span><span class="sxs-lookup"><span data-stu-id="dd9c0-131">The console trace listener writes trace information to the console through calls to either <xref:System.Diagnostics.TraceSource> or <xref:System.Diagnostics.Trace>.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sharedListeners>  
      <add name="console" type="System.Diagnostics.ConsoleTraceListener" >  
        <filter type="System.Diagnostics.EventTypeFilter"  
          initializeData="Warning" />  
      </add>  
    </sharedListeners>  
    <sources>  
      <source name="mySource" switchName="sourceSwitch"  >  
        <listeners>  
          <add name="console" />  
        </listeners>  
      </source>  
    </sources>  
    <switches>  
      <add name="sourceSwitch" value="Verbose"/>  
    </switches>  
    <trace>  
      <listeners>  
        <add name="console" />  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="dd9c0-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dd9c0-132">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="dd9c0-133">Esquema de configurações de rastreamento e depuração</span><span class="sxs-lookup"><span data-stu-id="dd9c0-133">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="dd9c0-134">Ouvintes de rastreamento</span><span class="sxs-lookup"><span data-stu-id="dd9c0-134">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
