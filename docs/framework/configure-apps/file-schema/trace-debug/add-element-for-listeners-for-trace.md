---
title: '&lt;Adicione&gt; elemento para &lt;ouvintes&gt; para &lt;rastreamento&gt;'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/add
helpviewer_keywords:
- initializeData attribute
- <add> element for <listeners>
- add element for <listeners>
ms.assetid: 81e804a3-ef11-4d39-bbde-bfa012c179e2
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 3a5dfffa7892cb0cec837a2492e1a4ecdfe60be0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54520965"
---
# <a name="ltaddgt-element-for-ltlistenersgt-for-lttracegt"></a><span data-ttu-id="9d795-102">&lt;Adicione&gt; elemento para &lt;ouvintes&gt; para &lt;rastreamento&gt;</span><span class="sxs-lookup"><span data-stu-id="9d795-102">&lt;add&gt; Element for &lt;listeners&gt; for &lt;trace&gt;</span></span>
<span data-ttu-id="9d795-103">Adiciona um ouvinte para o **ouvintes** coleção.</span><span class="sxs-lookup"><span data-stu-id="9d795-103">Adds a listener to the **Listeners** collection.</span></span>  
  
 <span data-ttu-id="9d795-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="9d795-104">\<configuration></span></span>  
<span data-ttu-id="9d795-105">\<system.diagnostics></span><span class="sxs-lookup"><span data-stu-id="9d795-105">\<system.diagnostics></span></span>  
<span data-ttu-id="9d795-106">\<trace></span><span class="sxs-lookup"><span data-stu-id="9d795-106">\<trace></span></span>  
<span data-ttu-id="9d795-107">\<listeners></span><span class="sxs-lookup"><span data-stu-id="9d795-107">\<listeners></span></span>  
<span data-ttu-id="9d795-108">\<add></span><span class="sxs-lookup"><span data-stu-id="9d795-108">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d795-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9d795-109">Syntax</span></span>  
  
```xml  
<add name="name"   
     type="trace listener class name, Version, Culture, PublicKeyToken"  
     initializeData="data"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9d795-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="9d795-110">Attributes and Elements</span></span>  
 <span data-ttu-id="9d795-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="9d795-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9d795-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="9d795-112">Attributes</span></span>  
  
|<span data-ttu-id="9d795-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="9d795-113">Attribute</span></span>|<span data-ttu-id="9d795-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="9d795-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9d795-115">**type**</span><span class="sxs-lookup"><span data-stu-id="9d795-115">**type**</span></span>|<span data-ttu-id="9d795-116">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="9d795-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="9d795-117">Especifica o tipo do ouvinte.</span><span class="sxs-lookup"><span data-stu-id="9d795-117">Specifies the type of the listener.</span></span> <span data-ttu-id="9d795-118">Você deve usar uma cadeia de caracteres que atenda aos requisitos especificados em [especificando nomes de tipo totalmente qualificados](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="9d795-118">You must use a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|<span data-ttu-id="9d795-119">**initializeData**</span><span class="sxs-lookup"><span data-stu-id="9d795-119">**initializeData**</span></span>|<span data-ttu-id="9d795-120">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="9d795-120">Optional attribute.</span></span><br /><br /> <span data-ttu-id="9d795-121">A cadeia de caracteres passada para o construtor para a classe especificada.</span><span class="sxs-lookup"><span data-stu-id="9d795-121">The string passed to the constructor for the specified class.</span></span>|  
|<span data-ttu-id="9d795-122">**name**</span><span class="sxs-lookup"><span data-stu-id="9d795-122">**name**</span></span>|<span data-ttu-id="9d795-123">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="9d795-123">Optional attribute.</span></span><br /><br /> <span data-ttu-id="9d795-124">Especifica o nome do ouvinte.</span><span class="sxs-lookup"><span data-stu-id="9d795-124">Specifies the name of the listener.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9d795-125">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="9d795-125">Child Elements</span></span>  
  
|<span data-ttu-id="9d795-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="9d795-126">Element</span></span>|<span data-ttu-id="9d795-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="9d795-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9d795-128">\<filter></span><span class="sxs-lookup"><span data-stu-id="9d795-128">\<filter></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/filter-element-for-add-for-listeners-for-trace.md)|<span data-ttu-id="9d795-129">Adiciona um filtro a um ouvinte no `Listeners` coleção para um rastreamento.</span><span class="sxs-lookup"><span data-stu-id="9d795-129">Adds a filter to a listener in the `Listeners` collection for a trace.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9d795-130">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="9d795-130">Parent Elements</span></span>  
  
|<span data-ttu-id="9d795-131">Elemento</span><span class="sxs-lookup"><span data-stu-id="9d795-131">Element</span></span>|<span data-ttu-id="9d795-132">Descrição</span><span class="sxs-lookup"><span data-stu-id="9d795-132">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="9d795-133">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9d795-133">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`listeners`|<span data-ttu-id="9d795-134">Especifica um ouvinte que coleta, armazena e encaminha mensagens.</span><span class="sxs-lookup"><span data-stu-id="9d795-134">Specifies a listener that collects, stores, and routes messages.</span></span> <span data-ttu-id="9d795-135">Os ouvintes direcionam a saída de rastreamento para um destino apropriado.</span><span class="sxs-lookup"><span data-stu-id="9d795-135">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="9d795-136">Especifica o elemento raiz para a seção de configuração do ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="9d795-136">Specifies the root element for the ASP.NET configuration section.</span></span>|  
|`trace`|<span data-ttu-id="9d795-137">Contém os ouvintes que coletam, armazenam e roteiam mensagens de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="9d795-137">Contains listeners that collect, store, and route tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9d795-138">Comentários</span><span class="sxs-lookup"><span data-stu-id="9d795-138">Remarks</span></span>  
 <span data-ttu-id="9d795-139">O <xref:System.Diagnostics.Debug> e <xref:System.Diagnostics.Trace> classes compartilham o mesmo **ouvintes** coleção.</span><span class="sxs-lookup"><span data-stu-id="9d795-139">The <xref:System.Diagnostics.Debug> and <xref:System.Diagnostics.Trace> classes share the same **Listeners** collection.</span></span> <span data-ttu-id="9d795-140">Se você adicionar um objeto de ouvinte à coleção em uma dessas classes, a outra classe usa o mesmo ouvinte.</span><span class="sxs-lookup"><span data-stu-id="9d795-140">If you add a listener object to the collection in one of these classes, the other class uses the same listener.</span></span> <span data-ttu-id="9d795-141">As classes de ouvinte derivam o <xref:System.Diagnostics.TraceListener>.</span><span class="sxs-lookup"><span data-stu-id="9d795-141">The listener classes derive from the <xref:System.Diagnostics.TraceListener>.</span></span>  
  
 <span data-ttu-id="9d795-142">Se você não especificar o `name` atributo do ouvinte de rastreamento, o <xref:System.Diagnostics.TraceListener.Name%2A> dos padrões de ouvinte de rastreamento para uma cadeia de caracteres vazia ("").</span><span class="sxs-lookup"><span data-stu-id="9d795-142">If you do not specify the `name` attribute of the trace listener, the <xref:System.Diagnostics.TraceListener.Name%2A> of the trace listener defaults to an empty string ("").</span></span> <span data-ttu-id="9d795-143">Se seu aplicativo tiver somente um ouvinte, você pode adicioná-lo sem especificar um nome e removê-la, especificando uma cadeia de caracteres vazia para o nome.</span><span class="sxs-lookup"><span data-stu-id="9d795-143">If your application has only one listener, you can add it without specifying a name, and remove it by specifying an empty string for the name.</span></span> <span data-ttu-id="9d795-144">No entanto, se seu aplicativo tiver mais de um ouvinte, você deve especificar nomes exclusivos para cada ouvinte de rastreamento, que permite que você identifique e gerencie os ouvintes de rastreamento individuais dentro de <xref:System.Diagnostics.Debug.Listeners%2A> e <xref:System.Diagnostics.Trace.Listeners%2A> coleções.</span><span class="sxs-lookup"><span data-stu-id="9d795-144">However, if your application has more than one listener, you should specify unique names for each trace listener, which allows you to identify and manage individual trace listeners within the <xref:System.Diagnostics.Debug.Listeners%2A> and <xref:System.Diagnostics.Trace.Listeners%2A> collections.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9d795-145">Adicionando mais de um ouvinte de rastreamento do mesmo tipo e com o mesmo nome resultados no ouvinte de rastreamento somente um desse tipo e nomeie o que está sendo adicionado ao `Listeners` coleção.</span><span class="sxs-lookup"><span data-stu-id="9d795-145">Adding more than one trace listener of the same type and with the same name results in only one trace listener of that type and name being added to the `Listeners` collection.</span></span> <span data-ttu-id="9d795-146">No entanto, você pode adicionar programaticamente várias escutas idênticas a `Listeners` coleção.</span><span class="sxs-lookup"><span data-stu-id="9d795-146">However, you can programmatically add multiple identical listeners to the `Listeners` collection.</span></span>  
  
 <span data-ttu-id="9d795-147">O valor para o **initializeData** atributo depende do tipo de ouvinte que você cria.</span><span class="sxs-lookup"><span data-stu-id="9d795-147">The value for the **initializeData** attribute depends on the type of listener you create.</span></span> <span data-ttu-id="9d795-148">Nem todos os ouvintes de rastreamento requerem que você especifique **initializeData**.</span><span class="sxs-lookup"><span data-stu-id="9d795-148">Not all trace listeners require that you specify **initializeData**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9d795-149">Quando você usa o `initializeData` atributo, você pode receber o aviso "o atributo 'initializeData' não é declarado" do compilador</span><span class="sxs-lookup"><span data-stu-id="9d795-149">When you use the `initializeData` attribute, you may get the compiler warning "The 'initializeData' attribute is not declared."</span></span> <span data-ttu-id="9d795-150">Este aviso ocorre porque as definições de configuração são validadas em relação a classe base abstrata <xref:System.Diagnostics.TraceListener>, que não reconhece o `initializeData` atributo.</span><span class="sxs-lookup"><span data-stu-id="9d795-150">This warning occurs because the configuration settings are validated against the abstract base class <xref:System.Diagnostics.TraceListener>, which does not recognize the `initializeData` attribute.</span></span> <span data-ttu-id="9d795-151">Normalmente, você pode ignorar este aviso para as implementações de ouvinte de rastreamento que tem um construtor que aceita um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="9d795-151">Typically, you can ignore this warning for trace listener implementations that have a constructor that takes a parameter.</span></span>  
  
 <span data-ttu-id="9d795-152">A tabela a seguir mostra os ouvintes de rastreamento que são incluídos com o .NET Framework e descreve o valor de suas **initializeData** atributos.</span><span class="sxs-lookup"><span data-stu-id="9d795-152">The following table shows the trace listeners that are included with the .NET Framework and describes the value of their **initializeData** attributes.</span></span>  
  
|<span data-ttu-id="9d795-153">Classe de ouvintes de rastreamento</span><span class="sxs-lookup"><span data-stu-id="9d795-153">Trace listener class</span></span>|<span data-ttu-id="9d795-154">valor do atributo initializeData</span><span class="sxs-lookup"><span data-stu-id="9d795-154">initializeData attribute value</span></span>|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>|<span data-ttu-id="9d795-155">O `useErrorStream` de valor para o <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> construtor.</span><span class="sxs-lookup"><span data-stu-id="9d795-155">The `useErrorStream` value for the <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> constructor.</span></span>  <span data-ttu-id="9d795-156">Defina as `initializeData` de atributo para "`true`" para gravar o rastreamento e depuração de saída para <xref:System.Console.Error%2A?displayProperty=nameWithType>; "`false`" para gravar <xref:System.Console.Out%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="9d795-156">Set the `initializeData` attribute to "`true`" to write trace and debug output to <xref:System.Console.Error%2A?displayProperty=nameWithType>; "`false`" to write to <xref:System.Console.Out%2A?displayProperty=nameWithType>.</span></span>|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>|<span data-ttu-id="9d795-157">O nome do arquivo no qual o <xref:System.Diagnostics.DelimitedListTraceListener> é gravado.</span><span class="sxs-lookup"><span data-stu-id="9d795-157">The name of the file the <xref:System.Diagnostics.DelimitedListTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|<span data-ttu-id="9d795-158">O nome do nome de uma fonte de log de eventos existente.</span><span class="sxs-lookup"><span data-stu-id="9d795-158">The name of the name of an existing event log source.</span></span>|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|<span data-ttu-id="9d795-159">O nome do arquivo que o <xref:System.Diagnostics.EventSchemaTraceListener> grava.</span><span class="sxs-lookup"><span data-stu-id="9d795-159">The name of the file that the <xref:System.Diagnostics.EventSchemaTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="9d795-160">O nome do arquivo que o <xref:System.Diagnostics.TextWriterTraceListener> grava.</span><span class="sxs-lookup"><span data-stu-id="9d795-160">The name of the file that the <xref:System.Diagnostics.TextWriterTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="9d795-161">O nome do arquivo que o <xref:System.Diagnostics.XmlWriterTraceListener> grava.</span><span class="sxs-lookup"><span data-stu-id="9d795-161">The name of the file that the <xref:System.Diagnostics.XmlWriterTraceListener> writes to.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="9d795-162">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9d795-162">Example</span></span>  
 <span data-ttu-id="9d795-163">O exemplo a seguir mostra como usar  **\<Adicionar >** elementos para adicionar os ouvintes `MyListener` e `MyEventListener` para o **ouvintes** coleção.</span><span class="sxs-lookup"><span data-stu-id="9d795-163">The following example shows how to use **\<add>** elements to add the listeners `MyListener` and `MyEventListener` to the **Listeners** collection.</span></span> <span data-ttu-id="9d795-164">`MyListener` cria um arquivo chamado `MyListener.log` e grava a saída para o arquivo.</span><span class="sxs-lookup"><span data-stu-id="9d795-164">`MyListener` creates a file called `MyListener.log` and writes the output to the file.</span></span> <span data-ttu-id="9d795-165">`MyEventListener` cria uma entrada no log de eventos.</span><span class="sxs-lookup"><span data-stu-id="9d795-165">`MyEventListener` creates an entry in the event log.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9d795-166">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9d795-166">See also</span></span>
- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.Debug>
- <xref:System.Diagnostics.EventLogTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- [<span data-ttu-id="9d795-167">Esquema de configurações de rastreamento e depuração</span><span class="sxs-lookup"><span data-stu-id="9d795-167">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
- [<span data-ttu-id="9d795-168">Ouvintes de rastreamento</span><span class="sxs-lookup"><span data-stu-id="9d795-168">Trace Listeners</span></span>](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
