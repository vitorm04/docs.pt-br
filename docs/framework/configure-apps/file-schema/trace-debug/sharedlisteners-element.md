---
title: '&lt;sharedListeners&gt; Element'
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
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 3069022287d469704cc7adac40d02ef3c6997b56
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54563036"
---
# <a name="ltsharedlistenersgt-element"></a><span data-ttu-id="8bc94-102">&lt;sharedListeners&gt; Element</span><span class="sxs-lookup"><span data-stu-id="8bc94-102">&lt;sharedListeners&gt; Element</span></span>
<span data-ttu-id="8bc94-103">Contém os ouvintes que podem ser referenciados por qualquer elemento de origem ou de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="8bc94-103">Contains listeners that any source or trace element can reference.</span></span>  <span data-ttu-id="8bc94-104">Esses ouvintes não recebem os rastreamentos por padrão, e não é possível recuperar esses ouvintes em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="8bc94-104">These listeners do not receive any traces by default, and it is not possible to retrieve these listeners at run time.</span></span> <span data-ttu-id="8bc94-105">Ouvintes identificados como ouvintes compartilhados podem ser adicionados à fontes ou rastreamentos por nome.</span><span class="sxs-lookup"><span data-stu-id="8bc94-105">Listeners identified as shared listeners can be added to sources or traces by name.</span></span>  
  
 <span data-ttu-id="8bc94-106">\<configuration></span><span class="sxs-lookup"><span data-stu-id="8bc94-106">\<configuration></span></span>  
<span data-ttu-id="8bc94-107">\<system.diagnostics></span><span class="sxs-lookup"><span data-stu-id="8bc94-107">\<system.diagnostics></span></span>  
<span data-ttu-id="8bc94-108">\<sharedListeners></span><span class="sxs-lookup"><span data-stu-id="8bc94-108">\<sharedListeners></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8bc94-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8bc94-109">Syntax</span></span>  
  
```xml  
<sharedListeners>   
  <add>...</add>  
</sharedListeners>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8bc94-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="8bc94-110">Attributes and Elements</span></span>  
 <span data-ttu-id="8bc94-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="8bc94-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8bc94-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="8bc94-112">Attributes</span></span>  
 <span data-ttu-id="8bc94-113">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="8bc94-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="8bc94-114">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="8bc94-114">Child Elements</span></span>  
  
|<span data-ttu-id="8bc94-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="8bc94-115">Element</span></span>|<span data-ttu-id="8bc94-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="8bc94-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8bc94-117">\<add></span><span class="sxs-lookup"><span data-stu-id="8bc94-117">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-listeners-for-trace.md)|<span data-ttu-id="8bc94-118">Adiciona um ouvinte na coleção `sharedListeners`.</span><span class="sxs-lookup"><span data-stu-id="8bc94-118">Adds a listener to the `sharedListeners` collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8bc94-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="8bc94-119">Parent Elements</span></span>  
  
|<span data-ttu-id="8bc94-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="8bc94-120">Element</span></span>|<span data-ttu-id="8bc94-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="8bc94-121">Description</span></span>|  
|-------------|-----------------|  
|`Configuration`|<span data-ttu-id="8bc94-122">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8bc94-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="8bc94-123">Especifica o elemento raiz para a seção de configuração do ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="8bc94-123">Specifies the root element for the ASP.NET configuration section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8bc94-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="8bc94-124">Remarks</span></span>  
 <span data-ttu-id="8bc94-125">Adicionar um ouvinte à coleção de ouvintes compartilhados não o torna um ouvinte ativo.</span><span class="sxs-lookup"><span data-stu-id="8bc94-125">Adding a listener to the shared listeners collection does not make it an active listener.</span></span> <span data-ttu-id="8bc94-126">Ela ainda deve ser adicionada a uma origem de rastreamento ou um rastreamento adicionando-à `Listeners` coleção para esse elemento de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="8bc94-126">It must still be added to a trace source or a trace by adding it to the `Listeners` collection for that trace element.</span></span> <span data-ttu-id="8bc94-127">As classes de ouvinte no .NET Framework derivam o <xref:System.Diagnostics.TraceListener> classe.</span><span class="sxs-lookup"><span data-stu-id="8bc94-127">The listener classes in the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span>  
  
 <span data-ttu-id="8bc94-128">Esse elemento pode ser usado no arquivo de configuração de máquina (Machine. config) e o arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8bc94-128">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8bc94-129">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8bc94-129">Example</span></span>  
 <span data-ttu-id="8bc94-130">O exemplo a seguir mostra como usar o `<sharedListeners>` elemento para adicionar o ouvinte `console` para o `Listeners` coleção para ambos os <xref:System.Diagnostics.TraceSource> e <xref:System.Diagnostics.Trace> classes.</span><span class="sxs-lookup"><span data-stu-id="8bc94-130">The following example shows how to use the `<sharedListeners>` element to add the listener `console` to the `Listeners` collection for both the <xref:System.Diagnostics.TraceSource> and <xref:System.Diagnostics.Trace> classes.</span></span> <span data-ttu-id="8bc94-131">O ouvinte de rastreamento do console grava informações de rastreamento no console por meio de chamadas para um <xref:System.Diagnostics.TraceSource> ou <xref:System.Diagnostics.Trace>.</span><span class="sxs-lookup"><span data-stu-id="8bc94-131">The console trace listener writes trace information to the console through calls to either <xref:System.Diagnostics.TraceSource> or <xref:System.Diagnostics.Trace>.</span></span>  
  
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
</configuration></system.diagnostics>   
```  
  
## <a name="see-also"></a><span data-ttu-id="8bc94-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8bc94-132">See also</span></span>
- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="8bc94-133">Esquema de configurações de rastreamento e depuração</span><span class="sxs-lookup"><span data-stu-id="8bc94-133">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
- [<span data-ttu-id="8bc94-134">Ouvintes de rastreamento</span><span class="sxs-lookup"><span data-stu-id="8bc94-134">Trace Listeners</span></span>](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
