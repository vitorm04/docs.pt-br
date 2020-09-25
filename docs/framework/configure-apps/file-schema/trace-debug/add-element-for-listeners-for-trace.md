---
title: <add> Elemento para <listeners> para <trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/add
helpviewer_keywords:
- initializeData attribute
- <add> element for <listeners>
- add element for <listeners>
ms.assetid: 81e804a3-ef11-4d39-bbde-bfa012c179e2
ms.openlocfilehash: da5c0ccae08a32c324a1633b5a7ff7592efa6e2d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91174037"
---
# <a name="add-element-for-listeners-for-trace"></a><span data-ttu-id="81d3c-102">\<add> Elemento para \<listeners> para \<trace></span><span class="sxs-lookup"><span data-stu-id="81d3c-102">\<add> Element for \<listeners> for \<trace></span></span>

<span data-ttu-id="81d3c-103">Adiciona um ouvinte à coleção de **ouvintes** .</span><span class="sxs-lookup"><span data-stu-id="81d3c-103">Adds a listener to the **Listeners** collection.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<trace>**](trace-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-trace.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

## <a name="syntax"></a><span data-ttu-id="81d3c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="81d3c-104">Syntax</span></span>  
  
```xml  
<add name="name"
     type="trace listener class name, Version, Culture, PublicKeyToken"  
     initializeData="data"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="81d3c-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="81d3c-105">Attributes and Elements</span></span>  

 <span data-ttu-id="81d3c-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="81d3c-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="81d3c-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="81d3c-107">Attributes</span></span>  
  
|<span data-ttu-id="81d3c-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="81d3c-108">Attribute</span></span>|<span data-ttu-id="81d3c-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="81d3c-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="81d3c-110">**tipo**</span><span class="sxs-lookup"><span data-stu-id="81d3c-110">**type**</span></span>|<span data-ttu-id="81d3c-111">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="81d3c-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="81d3c-112">Especifica o tipo do ouvinte.</span><span class="sxs-lookup"><span data-stu-id="81d3c-112">Specifies the type of the listener.</span></span> <span data-ttu-id="81d3c-113">Você deve usar uma cadeia de caracteres que atenda aos requisitos especificados na [especificação de nomes de tipo totalmente qualificados](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="81d3c-113">You must use a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|<span data-ttu-id="81d3c-114">**initializeData**</span><span class="sxs-lookup"><span data-stu-id="81d3c-114">**initializeData**</span></span>|<span data-ttu-id="81d3c-115">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="81d3c-115">Optional attribute.</span></span><br /><br /> <span data-ttu-id="81d3c-116">A cadeia de caracteres passada para o construtor para a classe especificada.</span><span class="sxs-lookup"><span data-stu-id="81d3c-116">The string passed to the constructor for the specified class.</span></span>|  
|<span data-ttu-id="81d3c-117">**name**</span><span class="sxs-lookup"><span data-stu-id="81d3c-117">**name**</span></span>|<span data-ttu-id="81d3c-118">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="81d3c-118">Optional attribute.</span></span><br /><br /> <span data-ttu-id="81d3c-119">Especifica o nome do ouvinte.</span><span class="sxs-lookup"><span data-stu-id="81d3c-119">Specifies the name of the listener.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="81d3c-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="81d3c-120">Child Elements</span></span>  
  
|<span data-ttu-id="81d3c-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="81d3c-121">Element</span></span>|<span data-ttu-id="81d3c-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="81d3c-122">Description</span></span>|  
|-------------|-----------------|  
|[\<filter>](filter-element-for-add-for-listeners-for-trace.md)|<span data-ttu-id="81d3c-123">Adiciona um filtro a um ouvinte na `Listeners` coleção de um rastreamento.</span><span class="sxs-lookup"><span data-stu-id="81d3c-123">Adds a filter to a listener in the `Listeners` collection for a trace.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="81d3c-124">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="81d3c-124">Parent Elements</span></span>  
  
|<span data-ttu-id="81d3c-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="81d3c-125">Element</span></span>|<span data-ttu-id="81d3c-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="81d3c-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="81d3c-127">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="81d3c-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`listeners`|<span data-ttu-id="81d3c-128">Especifica um ouvinte que coleta, armazena e roteia mensagens.</span><span class="sxs-lookup"><span data-stu-id="81d3c-128">Specifies a listener that collects, stores, and routes messages.</span></span> <span data-ttu-id="81d3c-129">Os ouvintes direcionam a saída de rastreamento para um destino apropriado.</span><span class="sxs-lookup"><span data-stu-id="81d3c-129">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="81d3c-130">Especifica o elemento raiz para a seção de configuração ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="81d3c-130">Specifies the root element for the ASP.NET configuration section.</span></span>|  
|`trace`|<span data-ttu-id="81d3c-131">Contém os ouvintes que coletam, armazenam e roteiam mensagens de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="81d3c-131">Contains listeners that collect, store, and route tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="81d3c-132">Comentários</span><span class="sxs-lookup"><span data-stu-id="81d3c-132">Remarks</span></span>  

 <span data-ttu-id="81d3c-133">As <xref:System.Diagnostics.Debug> <xref:System.Diagnostics.Trace> classes e compartilham a mesma coleção de **ouvintes** .</span><span class="sxs-lookup"><span data-stu-id="81d3c-133">The <xref:System.Diagnostics.Debug> and <xref:System.Diagnostics.Trace> classes share the same **Listeners** collection.</span></span> <span data-ttu-id="81d3c-134">Se você adicionar um objeto de ouvinte à coleção em uma dessas classes, a outra classe usará o mesmo ouvinte.</span><span class="sxs-lookup"><span data-stu-id="81d3c-134">If you add a listener object to the collection in one of these classes, the other class uses the same listener.</span></span> <span data-ttu-id="81d3c-135">As classes de ouvinte derivam de <xref:System.Diagnostics.TraceListener> .</span><span class="sxs-lookup"><span data-stu-id="81d3c-135">The listener classes derive from the <xref:System.Diagnostics.TraceListener>.</span></span>  
  
 <span data-ttu-id="81d3c-136">Se você não especificar o `name` atributo do ouvinte de rastreamento, o <xref:System.Diagnostics.TraceListener.Name%2A> do ouvinte de rastreamento assume como padrão uma cadeia de caracteres vazia ("").</span><span class="sxs-lookup"><span data-stu-id="81d3c-136">If you do not specify the `name` attribute of the trace listener, the <xref:System.Diagnostics.TraceListener.Name%2A> of the trace listener defaults to an empty string ("").</span></span> <span data-ttu-id="81d3c-137">Se seu aplicativo tiver apenas um ouvinte, você poderá adicioná-lo sem especificar um nome e removê-lo especificando uma cadeia de caracteres vazia para o nome.</span><span class="sxs-lookup"><span data-stu-id="81d3c-137">If your application has only one listener, you can add it without specifying a name, and remove it by specifying an empty string for the name.</span></span> <span data-ttu-id="81d3c-138">No entanto, se seu aplicativo tiver mais de um ouvinte, você deverá especificar nomes exclusivos para cada ouvinte de rastreamento, o que permite identificar e gerenciar ouvintes de rastreamento individuais nas <xref:System.Diagnostics.Debug.Listeners%2A> <xref:System.Diagnostics.Trace.Listeners%2A> coleções e.</span><span class="sxs-lookup"><span data-stu-id="81d3c-138">However, if your application has more than one listener, you should specify unique names for each trace listener, which allows you to identify and manage individual trace listeners within the <xref:System.Diagnostics.Debug.Listeners%2A> and <xref:System.Diagnostics.Trace.Listeners%2A> collections.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="81d3c-139">Adicionar mais de um ouvinte de rastreamento do mesmo tipo e com o mesmo nome resulta em apenas um ouvinte de rastreamento desse tipo e nome que estão sendo adicionados à `Listeners` coleção.</span><span class="sxs-lookup"><span data-stu-id="81d3c-139">Adding more than one trace listener of the same type and with the same name results in only one trace listener of that type and name being added to the `Listeners` collection.</span></span> <span data-ttu-id="81d3c-140">No entanto, você pode adicionar programaticamente vários ouvintes idênticos à `Listeners` coleção.</span><span class="sxs-lookup"><span data-stu-id="81d3c-140">However, you can programmatically add multiple identical listeners to the `Listeners` collection.</span></span>  
  
 <span data-ttu-id="81d3c-141">O valor do atributo **initializeData** depende do tipo de ouvinte que você criar.</span><span class="sxs-lookup"><span data-stu-id="81d3c-141">The value for the **initializeData** attribute depends on the type of listener you create.</span></span> <span data-ttu-id="81d3c-142">Nem todos os ouvintes de rastreamento exigem que você especifique **initializeData**.</span><span class="sxs-lookup"><span data-stu-id="81d3c-142">Not all trace listeners require that you specify **initializeData**.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="81d3c-143">Ao usar o `initializeData` atributo, você pode obter o aviso do compilador "o atributo ' initializeData ' não está declarado."</span><span class="sxs-lookup"><span data-stu-id="81d3c-143">When you use the `initializeData` attribute, you may get the compiler warning "The 'initializeData' attribute is not declared."</span></span> <span data-ttu-id="81d3c-144">Esse aviso ocorre porque as definições de configuração são validadas em relação à classe base abstrata <xref:System.Diagnostics.TraceListener> , que não reconhece o `initializeData` atributo.</span><span class="sxs-lookup"><span data-stu-id="81d3c-144">This warning occurs because the configuration settings are validated against the abstract base class <xref:System.Diagnostics.TraceListener>, which does not recognize the `initializeData` attribute.</span></span> <span data-ttu-id="81d3c-145">Normalmente, você pode ignorar esse aviso para implementações de ouvinte de rastreamento que têm um construtor que usa um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="81d3c-145">Typically, you can ignore this warning for trace listener implementations that have a constructor that takes a parameter.</span></span>  
  
 <span data-ttu-id="81d3c-146">A tabela a seguir mostra os ouvintes de rastreamento que estão incluídos com o .NET Framework e descreve o valor de seus atributos **initializeData** .</span><span class="sxs-lookup"><span data-stu-id="81d3c-146">The following table shows the trace listeners that are included with the .NET Framework and describes the value of their **initializeData** attributes.</span></span>  
  
|<span data-ttu-id="81d3c-147">Classe de ouvinte de rastreamento</span><span class="sxs-lookup"><span data-stu-id="81d3c-147">Trace listener class</span></span>|<span data-ttu-id="81d3c-148">valor do atributo initializeData</span><span class="sxs-lookup"><span data-stu-id="81d3c-148">initializeData attribute value</span></span>|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>|<span data-ttu-id="81d3c-149">O `useErrorStream` valor do <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> Construtor.</span><span class="sxs-lookup"><span data-stu-id="81d3c-149">The `useErrorStream` value for the <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> constructor.</span></span>  <span data-ttu-id="81d3c-150">Defina o `initializeData` atributo como " `true` " para gravar rastreamento e depurar saída para <xref:System.Console.Error%2A?displayProperty=nameWithType> ; " `false` " para gravar <xref:System.Console.Out%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="81d3c-150">Set the `initializeData` attribute to "`true`" to write trace and debug output to <xref:System.Console.Error%2A?displayProperty=nameWithType>; "`false`" to write to <xref:System.Console.Out%2A?displayProperty=nameWithType>.</span></span>|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>|<span data-ttu-id="81d3c-151">O nome do arquivo no qual o <xref:System.Diagnostics.DelimitedListTraceListener> é gravado.</span><span class="sxs-lookup"><span data-stu-id="81d3c-151">The name of the file the <xref:System.Diagnostics.DelimitedListTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|<span data-ttu-id="81d3c-152">O nome do nome de uma origem de log de eventos existente.</span><span class="sxs-lookup"><span data-stu-id="81d3c-152">The name of the name of an existing event log source.</span></span>|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|<span data-ttu-id="81d3c-153">O nome do arquivo no qual as <xref:System.Diagnostics.EventSchemaTraceListener> gravações são gravadas.</span><span class="sxs-lookup"><span data-stu-id="81d3c-153">The name of the file that the <xref:System.Diagnostics.EventSchemaTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="81d3c-154">O nome do arquivo no qual as <xref:System.Diagnostics.TextWriterTraceListener> gravações são gravadas.</span><span class="sxs-lookup"><span data-stu-id="81d3c-154">The name of the file that the <xref:System.Diagnostics.TextWriterTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="81d3c-155">O nome do arquivo no qual as <xref:System.Diagnostics.XmlWriterTraceListener> gravações são gravadas.</span><span class="sxs-lookup"><span data-stu-id="81d3c-155">The name of the file that the <xref:System.Diagnostics.XmlWriterTraceListener> writes to.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="81d3c-156">Exemplo</span><span class="sxs-lookup"><span data-stu-id="81d3c-156">Example</span></span>  

 <span data-ttu-id="81d3c-157">O exemplo a seguir mostra como usar **\<add>** elementos para adicionar os ouvintes `MyListener` e a `MyEventListener` coleção de **ouvintes** .</span><span class="sxs-lookup"><span data-stu-id="81d3c-157">The following example shows how to use **\<add>** elements to add the listeners `MyListener` and `MyEventListener` to the **Listeners** collection.</span></span> <span data-ttu-id="81d3c-158">`MyListener` Cria um arquivo chamado `MyListener.log` e grava a saída no arquivo.</span><span class="sxs-lookup"><span data-stu-id="81d3c-158">`MyListener` creates a file called `MyListener.log` and writes the output to the file.</span></span> <span data-ttu-id="81d3c-159">`MyEventListener` Cria uma entrada no log de eventos.</span><span class="sxs-lookup"><span data-stu-id="81d3c-159">`MyEventListener` creates an entry in the event log.</span></span>  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <trace autoflush="true" indentsize="0">  
         <listeners>  
            <add name="myListener" type="System.Diagnostics.TextWriterTraceListener, system, version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" initializeData="c:\myListener.log" />  
            <add name="MyEventListener"  
                 type="System.Diagnostics.EventLogTraceListener, system, version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"                 initializeData="MyConfigEventLog"/>  
            <add name="configConsoleListener"  
                 type="System.Diagnostics.ConsoleTraceListener, system, version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"/>  
         </listeners>  
      </trace>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="81d3c-160">Veja também</span><span class="sxs-lookup"><span data-stu-id="81d3c-160">See also</span></span>

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.Debug>
- <xref:System.Diagnostics.EventLogTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- [<span data-ttu-id="81d3c-161">Esquema de configurações de rastreamento e depuração</span><span class="sxs-lookup"><span data-stu-id="81d3c-161">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="81d3c-162">Ouvintes de rastreamento</span><span class="sxs-lookup"><span data-stu-id="81d3c-162">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
