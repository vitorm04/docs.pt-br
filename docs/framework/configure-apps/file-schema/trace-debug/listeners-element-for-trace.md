---
title: Elemento <listeners> para <trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners
helpviewer_keywords:
- <listeners> element
- listeners element
ms.assetid: 1394c2c3-6304-46db-87c1-8e8b16f5ad5b
ms.openlocfilehash: 84b67532825372e7f69d86e1ef6060f4263587eb
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699350"
---
# <a name="listeners-element-for-trace"></a><span data-ttu-id="f582d-102">\<listeners > elemento para \<trace ></span><span class="sxs-lookup"><span data-stu-id="f582d-102">\<listeners> Element for \<trace></span></span>
<span data-ttu-id="f582d-103">Especifica um ouvinte que coleta, armazena e roteia mensagens.</span><span class="sxs-lookup"><span data-stu-id="f582d-103">Specifies a listener that collects, stores, and routes messages.</span></span> <span data-ttu-id="f582d-104">Os ouvintes direcionam a saída de rastreamento para um destino apropriado.</span><span class="sxs-lookup"><span data-stu-id="f582d-104">Listeners direct the tracing output to an appropriate target.</span></span>  
  
[<span data-ttu-id="f582d-105"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="f582d-105">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="f582d-106">&nbsp; @ no__t-1[ **\<System. Diagnostics >** ](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="f582d-106">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>  
<span data-ttu-id="f582d-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<trace >** ](trace-element.md)</span><span class="sxs-lookup"><span data-stu-id="f582d-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<trace>**](trace-element.md)</span></span>  
<span data-ttu-id="f582d-108">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 **\<listeners >**</span><span class="sxs-lookup"><span data-stu-id="f582d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<listeners>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f582d-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f582d-109">Syntax</span></span>  
  
```xml  
<listeners>   
  <add>...</add>  
  <clear/>  
  <remove ... />  
</listeners>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f582d-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="f582d-110">Attributes and Elements</span></span>  
 <span data-ttu-id="f582d-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="f582d-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f582d-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="f582d-112">Attributes</span></span>  
 <span data-ttu-id="f582d-113">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="f582d-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f582d-114">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="f582d-114">Child Elements</span></span>  
  
|<span data-ttu-id="f582d-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="f582d-115">Element</span></span>|<span data-ttu-id="f582d-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="f582d-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f582d-117">\<add></span><span class="sxs-lookup"><span data-stu-id="f582d-117">\<add></span></span>](add-element-for-listeners-for-trace.md)|<span data-ttu-id="f582d-118">Adiciona um ouvinte na coleção `Listeners`.</span><span class="sxs-lookup"><span data-stu-id="f582d-118">Adds a listener to the `Listeners` collection.</span></span>|  
|[<span data-ttu-id="f582d-119">\<clear></span><span class="sxs-lookup"><span data-stu-id="f582d-119">\<clear></span></span>](clear-element-for-listeners-for-trace.md)|<span data-ttu-id="f582d-120">Limpa a coleção `Listeners` do rastreamento.</span><span class="sxs-lookup"><span data-stu-id="f582d-120">Clears the `Listeners` collection for trace.</span></span>|  
|[<span data-ttu-id="f582d-121">\<remove></span><span class="sxs-lookup"><span data-stu-id="f582d-121">\<remove></span></span>](remove-element-for-listeners-for-trace.md)|<span data-ttu-id="f582d-122">Remove um ouvinte da coleção `Listeners`.</span><span class="sxs-lookup"><span data-stu-id="f582d-122">Removes a listener from the `Listeners` collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f582d-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="f582d-123">Parent Elements</span></span>  
  
|<span data-ttu-id="f582d-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="f582d-124">Element</span></span>|<span data-ttu-id="f582d-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="f582d-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="f582d-126">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f582d-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="f582d-127">Especifica o elemento raiz para a seção de configuração ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="f582d-127">Specifies the root element for the ASP.NET configuration section.</span></span>|  
|`trace`|<span data-ttu-id="f582d-128">Contém os ouvintes que coletam, armazenam e roteiam mensagens de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="f582d-128">Contains listeners that collect, store, and route tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f582d-129">Comentários</span><span class="sxs-lookup"><span data-stu-id="f582d-129">Remarks</span></span>  
 <span data-ttu-id="f582d-130">As classes <xref:System.Diagnostics.Debug> e <xref:System.Diagnostics.Trace> compartilham a mesma coleção de **ouvintes** .</span><span class="sxs-lookup"><span data-stu-id="f582d-130">The <xref:System.Diagnostics.Debug> and <xref:System.Diagnostics.Trace> classes share the same **Listeners** collection.</span></span> <span data-ttu-id="f582d-131">Se você adicionar um objeto de ouvinte à coleção em uma dessas classes, a outra classe usará o mesmo ouvinte.</span><span class="sxs-lookup"><span data-stu-id="f582d-131">If you add a listener object to the collection in one of these classes, the other class uses the same listener.</span></span> <span data-ttu-id="f582d-132">As classes de ouvinte fornecidas com o .NET Framework derivam da classe <xref:System.Diagnostics.TraceListener>.</span><span class="sxs-lookup"><span data-stu-id="f582d-132">The listener classes shipped with the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="f582d-133">Arquivo de Configuração</span><span class="sxs-lookup"><span data-stu-id="f582d-133">Configuration File</span></span>  
 <span data-ttu-id="f582d-134">Esse elemento pode ser usado no arquivo de configuração da máquina (Machine. config) e no arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f582d-134">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f582d-135">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f582d-135">Example</span></span>  
 <span data-ttu-id="f582d-136">O exemplo a seguir mostra como usar o elemento **\<listeners >** para adicionar os ouvintes `MyListener` e `MyEventListener` à coleção de **ouvintes** .</span><span class="sxs-lookup"><span data-stu-id="f582d-136">The following example shows how to use the **\<listeners>** element to add the listeners `MyListener` and `MyEventListener` to the **Listeners** collection.</span></span> <span data-ttu-id="f582d-137">`MyListener` cria um arquivo chamado `MyListener.log` e grava a saída no arquivo.</span><span class="sxs-lookup"><span data-stu-id="f582d-137">`MyListener` creates a file called `MyListener.log` and writes the output to the file.</span></span> <span data-ttu-id="f582d-138">`MyEventListener` cria uma entrada no log de eventos.</span><span class="sxs-lookup"><span data-stu-id="f582d-138">`MyEventListener` creates an entry in the event log.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <trace autoflush="true" indentsize="0">  
      <listeners>  
        <add name="myListener"   
          type="System.Diagnostics.TextWriterTraceListener,   
            system, version=1.0.3300.0, Culture=neutral,   
            PublicKeyToken=b77a5c561934e089"   
          initializeData="c:\myListener.log" />  
        <add name="MyEventListener"  
          type="System.Diagnostics.EventLogTraceListener,   
            system, version=1.0.3300.0, Culture=neutral,   
            PublicKeyToken=b77a5c561934e089"  
          initializeData="MyConfigEventLog"/>  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f582d-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f582d-139">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="f582d-140">Esquema de configurações de rastreamento e depuração</span><span class="sxs-lookup"><span data-stu-id="f582d-140">Trace and Debug Settings Schema</span></span>](index.md)
