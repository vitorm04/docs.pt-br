---
title: Elemento <listeners> para <trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners
helpviewer_keywords:
- <listeners> element
- listeners element
ms.assetid: 1394c2c3-6304-46db-87c1-8e8b16f5ad5b
ms.openlocfilehash: e4550d4c4cd9ff37c5937ad366cccf91387c0e3f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927014"
---
# <a name="listeners-element-for-trace"></a><span data-ttu-id="9a2cd-102">\<elemento de > de ouvintes para > de \<rastreamento</span><span class="sxs-lookup"><span data-stu-id="9a2cd-102">\<listeners> Element for \<trace></span></span>
<span data-ttu-id="9a2cd-103">Especifica um ouvinte que coleta, armazena e roteia mensagens.</span><span class="sxs-lookup"><span data-stu-id="9a2cd-103">Specifies a listener that collects, stores, and routes messages.</span></span> <span data-ttu-id="9a2cd-104">Os ouvintes direcionam a saída de rastreamento para um destino apropriado.</span><span class="sxs-lookup"><span data-stu-id="9a2cd-104">Listeners direct the tracing output to an appropriate target.</span></span>  
  
 <span data-ttu-id="9a2cd-105">\<Elemento de > de configuração</span><span class="sxs-lookup"><span data-stu-id="9a2cd-105">\<configuration> Element</span></span>  
<span data-ttu-id="9a2cd-106">\<Elemento de > System. Diagnostics</span><span class="sxs-lookup"><span data-stu-id="9a2cd-106">\<system.diagnostics> Element</span></span>  
<span data-ttu-id="9a2cd-107">\<Elemento de > de rastreamento</span><span class="sxs-lookup"><span data-stu-id="9a2cd-107">\<trace> Element</span></span>  
<span data-ttu-id="9a2cd-108">\<elemento de > de ouvintes para > de \<rastreamento</span><span class="sxs-lookup"><span data-stu-id="9a2cd-108">\<listeners> Element for \<trace></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a2cd-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9a2cd-109">Syntax</span></span>  
  
```xml  
<listeners>   
  <add>...</add>  
  <clear/>  
  <remove ... />  
</listeners>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9a2cd-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="9a2cd-110">Attributes and Elements</span></span>  
 <span data-ttu-id="9a2cd-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="9a2cd-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9a2cd-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="9a2cd-112">Attributes</span></span>  
 <span data-ttu-id="9a2cd-113">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="9a2cd-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="9a2cd-114">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="9a2cd-114">Child Elements</span></span>  
  
|<span data-ttu-id="9a2cd-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="9a2cd-115">Element</span></span>|<span data-ttu-id="9a2cd-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="9a2cd-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9a2cd-117">\<add></span><span class="sxs-lookup"><span data-stu-id="9a2cd-117">\<add></span></span>](add-element-for-listeners-for-trace.md)|<span data-ttu-id="9a2cd-118">Adiciona um ouvinte na coleção `Listeners`.</span><span class="sxs-lookup"><span data-stu-id="9a2cd-118">Adds a listener to the `Listeners` collection.</span></span>|  
|[<span data-ttu-id="9a2cd-119">\<clear></span><span class="sxs-lookup"><span data-stu-id="9a2cd-119">\<clear></span></span>](clear-element-for-listeners-for-trace.md)|<span data-ttu-id="9a2cd-120">Limpa a coleção `Listeners` do rastreamento.</span><span class="sxs-lookup"><span data-stu-id="9a2cd-120">Clears the `Listeners` collection for trace.</span></span>|  
|[<span data-ttu-id="9a2cd-121">\<remove></span><span class="sxs-lookup"><span data-stu-id="9a2cd-121">\<remove></span></span>](remove-element-for-listeners-for-trace.md)|<span data-ttu-id="9a2cd-122">Remove um ouvinte da `Listeners` coleção.</span><span class="sxs-lookup"><span data-stu-id="9a2cd-122">Removes a listener from the `Listeners` collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9a2cd-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="9a2cd-123">Parent Elements</span></span>  
  
|<span data-ttu-id="9a2cd-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="9a2cd-124">Element</span></span>|<span data-ttu-id="9a2cd-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="9a2cd-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="9a2cd-126">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9a2cd-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="9a2cd-127">Especifica o elemento raiz para a seção de configuração ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="9a2cd-127">Specifies the root element for the ASP.NET configuration section.</span></span>|  
|`trace`|<span data-ttu-id="9a2cd-128">Contém os ouvintes que coletam, armazenam e roteiam mensagens de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="9a2cd-128">Contains listeners that collect, store, and route tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9a2cd-129">Comentários</span><span class="sxs-lookup"><span data-stu-id="9a2cd-129">Remarks</span></span>  
 <span data-ttu-id="9a2cd-130">As <xref:System.Diagnostics.Debug> classes <xref:System.Diagnostics.Trace> e compartilham a mesma coleção de ouvintes.</span><span class="sxs-lookup"><span data-stu-id="9a2cd-130">The <xref:System.Diagnostics.Debug> and <xref:System.Diagnostics.Trace> classes share the same **Listeners** collection.</span></span> <span data-ttu-id="9a2cd-131">Se você adicionar um objeto de ouvinte à coleção em uma dessas classes, a outra classe usará o mesmo ouvinte.</span><span class="sxs-lookup"><span data-stu-id="9a2cd-131">If you add a listener object to the collection in one of these classes, the other class uses the same listener.</span></span> <span data-ttu-id="9a2cd-132">As classes de ouvinte fornecidas com o .NET Framework derivam da <xref:System.Diagnostics.TraceListener> classe.</span><span class="sxs-lookup"><span data-stu-id="9a2cd-132">The listener classes shipped with the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="9a2cd-133">Arquivo de Configuração</span><span class="sxs-lookup"><span data-stu-id="9a2cd-133">Configuration File</span></span>  
 <span data-ttu-id="9a2cd-134">Esse elemento pode ser usado no arquivo de configuração da máquina (Machine. config) e no arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9a2cd-134">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9a2cd-135">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9a2cd-135">Example</span></span>  
 <span data-ttu-id="9a2cd-136">O exemplo a seguir mostra como usar o  **\<elemento >** de ouvintes `MyListener` para adicionar os ouvintes `MyEventListener` e a coleção de **ouvintes** .</span><span class="sxs-lookup"><span data-stu-id="9a2cd-136">The following example shows how to use the **\<listeners>** element to add the listeners `MyListener` and `MyEventListener` to the **Listeners** collection.</span></span> <span data-ttu-id="9a2cd-137">`MyListener`Cria um arquivo chamado `MyListener.log` e grava a saída no arquivo.</span><span class="sxs-lookup"><span data-stu-id="9a2cd-137">`MyListener` creates a file called `MyListener.log` and writes the output to the file.</span></span> <span data-ttu-id="9a2cd-138">`MyEventListener`Cria uma entrada no log de eventos.</span><span class="sxs-lookup"><span data-stu-id="9a2cd-138">`MyEventListener` creates an entry in the event log.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9a2cd-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9a2cd-139">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="9a2cd-140">Esquema de configurações de rastreamento e depuração</span><span class="sxs-lookup"><span data-stu-id="9a2cd-140">Trace and Debug Settings Schema</span></span>](index.md)
