---
title: <add>Elemento para <listeners> para<trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/add
helpviewer_keywords:
- initializeData attribute
- <add> element for <listeners>
- add element for <listeners>
ms.assetid: 81e804a3-ef11-4d39-bbde-bfa012c179e2
ms.openlocfilehash: d4ff919991ab1505b2845a225706d32cc1e57d0a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920564"
---
# <a name="add-element-for-listeners-for-trace"></a><span data-ttu-id="6a9d4-102">\<Adicionar > elemento para \<ouvintes > para \<o rastreamento ></span><span class="sxs-lookup"><span data-stu-id="6a9d4-102">\<add> Element for \<listeners> for \<trace></span></span>
<span data-ttu-id="6a9d4-103">Adiciona um ouvinte à coleção de ouvintes.</span><span class="sxs-lookup"><span data-stu-id="6a9d4-103">Adds a listener to the **Listeners** collection.</span></span>  
  
 <span data-ttu-id="6a9d4-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="6a9d4-104">\<configuration></span></span>  
<span data-ttu-id="6a9d4-105">\<System. Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="6a9d4-105">\<system.diagnostics></span></span>  
<span data-ttu-id="6a9d4-106">\<> de rastreamento</span><span class="sxs-lookup"><span data-stu-id="6a9d4-106">\<trace></span></span>  
<span data-ttu-id="6a9d4-107">\<listeners></span><span class="sxs-lookup"><span data-stu-id="6a9d4-107">\<listeners></span></span>  
<span data-ttu-id="6a9d4-108">\<add></span><span class="sxs-lookup"><span data-stu-id="6a9d4-108">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a9d4-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6a9d4-109">Syntax</span></span>  
  
```xml  
<add name="name"   
     type="trace listener class name, Version, Culture, PublicKeyToken"  
     initializeData="data"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6a9d4-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="6a9d4-110">Attributes and Elements</span></span>  
 <span data-ttu-id="6a9d4-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="6a9d4-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6a9d4-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="6a9d4-112">Attributes</span></span>  
  
|<span data-ttu-id="6a9d4-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="6a9d4-113">Attribute</span></span>|<span data-ttu-id="6a9d4-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="6a9d4-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6a9d4-115">**type**</span><span class="sxs-lookup"><span data-stu-id="6a9d4-115">**type**</span></span>|<span data-ttu-id="6a9d4-116">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="6a9d4-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="6a9d4-117">Especifica o tipo do ouvinte.</span><span class="sxs-lookup"><span data-stu-id="6a9d4-117">Specifies the type of the listener.</span></span> <span data-ttu-id="6a9d4-118">Você deve usar uma cadeia de caracteres que atenda aos requisitos especificados na [especificação de nomes de tipo totalmente qualificados](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="6a9d4-118">You must use a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|<span data-ttu-id="6a9d4-119">**initializeData**</span><span class="sxs-lookup"><span data-stu-id="6a9d4-119">**initializeData**</span></span>|<span data-ttu-id="6a9d4-120">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="6a9d4-120">Optional attribute.</span></span><br /><br /> <span data-ttu-id="6a9d4-121">A cadeia de caracteres passada para o construtor para a classe especificada.</span><span class="sxs-lookup"><span data-stu-id="6a9d4-121">The string passed to the constructor for the specified class.</span></span>|  
|<span data-ttu-id="6a9d4-122">**name**</span><span class="sxs-lookup"><span data-stu-id="6a9d4-122">**name**</span></span>|<span data-ttu-id="6a9d4-123">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="6a9d4-123">Optional attribute.</span></span><br /><br /> <span data-ttu-id="6a9d4-124">Especifica o nome do ouvinte.</span><span class="sxs-lookup"><span data-stu-id="6a9d4-124">Specifies the name of the listener.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6a9d4-125">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="6a9d4-125">Child Elements</span></span>  
  
|<span data-ttu-id="6a9d4-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="6a9d4-126">Element</span></span>|<span data-ttu-id="6a9d4-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="6a9d4-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6a9d4-128">\<filter></span><span class="sxs-lookup"><span data-stu-id="6a9d4-128">\<filter></span></span>](filter-element-for-add-for-listeners-for-trace.md)|<span data-ttu-id="6a9d4-129">Adiciona um filtro a um ouvinte na `Listeners` coleção de um rastreamento.</span><span class="sxs-lookup"><span data-stu-id="6a9d4-129">Adds a filter to a listener in the `Listeners` collection for a trace.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6a9d4-130">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="6a9d4-130">Parent Elements</span></span>  
  
|<span data-ttu-id="6a9d4-131">Elemento</span><span class="sxs-lookup"><span data-stu-id="6a9d4-131">Element</span></span>|<span data-ttu-id="6a9d4-132">Descrição</span><span class="sxs-lookup"><span data-stu-id="6a9d4-132">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="6a9d4-133">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6a9d4-133">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`listeners`|<span data-ttu-id="6a9d4-134">Especifica um ouvinte que coleta, armazena e roteia mensagens.</span><span class="sxs-lookup"><span data-stu-id="6a9d4-134">Specifies a listener that collects, stores, and routes messages.</span></span> <span data-ttu-id="6a9d4-135">Os ouvintes direcionam a saída de rastreamento para um destino apropriado.</span><span class="sxs-lookup"><span data-stu-id="6a9d4-135">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="6a9d4-136">Especifica o elemento raiz para a seção de configuração ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="6a9d4-136">Specifies the root element for the ASP.NET configuration section.</span></span>|  
|`trace`|<span data-ttu-id="6a9d4-137">Contém os ouvintes que coletam, armazenam e roteiam mensagens de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="6a9d4-137">Contains listeners that collect, store, and route tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6a9d4-138">Comentários</span><span class="sxs-lookup"><span data-stu-id="6a9d4-138">Remarks</span></span>  
 <span data-ttu-id="6a9d4-139">As <xref:System.Diagnostics.Debug> classes <xref:System.Diagnostics.Trace> e compartilham a mesma coleção de ouvintes.</span><span class="sxs-lookup"><span data-stu-id="6a9d4-139">The <xref:System.Diagnostics.Debug> and <xref:System.Diagnostics.Trace> classes share the same **Listeners** collection.</span></span> <span data-ttu-id="6a9d4-140">Se você adicionar um objeto de ouvinte à coleção em uma dessas classes, a outra classe usará o mesmo ouvinte.</span><span class="sxs-lookup"><span data-stu-id="6a9d4-140">If you add a listener object to the collection in one of these classes, the other class uses the same listener.</span></span> <span data-ttu-id="6a9d4-141">As classes de ouvinte derivam de <xref:System.Diagnostics.TraceListener>.</span><span class="sxs-lookup"><span data-stu-id="6a9d4-141">The listener classes derive from the <xref:System.Diagnostics.TraceListener>.</span></span>  
  
 <span data-ttu-id="6a9d4-142">Se você não especificar o `name` atributo do ouvinte de rastreamento, o <xref:System.Diagnostics.TraceListener.Name%2A> do ouvinte de rastreamento assume como padrão uma cadeia de caracteres vazia ("").</span><span class="sxs-lookup"><span data-stu-id="6a9d4-142">If you do not specify the `name` attribute of the trace listener, the <xref:System.Diagnostics.TraceListener.Name%2A> of the trace listener defaults to an empty string ("").</span></span> <span data-ttu-id="6a9d4-143">Se seu aplicativo tiver apenas um ouvinte, você poderá adicioná-lo sem especificar um nome e removê-lo especificando uma cadeia de caracteres vazia para o nome.</span><span class="sxs-lookup"><span data-stu-id="6a9d4-143">If your application has only one listener, you can add it without specifying a name, and remove it by specifying an empty string for the name.</span></span> <span data-ttu-id="6a9d4-144">No entanto, se seu aplicativo tiver mais de um ouvinte, você deverá especificar nomes exclusivos para cada ouvinte de rastreamento, o que permite identificar e gerenciar ouvintes <xref:System.Diagnostics.Debug.Listeners%2A> de <xref:System.Diagnostics.Trace.Listeners%2A> rastreamento individuais nas coleções e.</span><span class="sxs-lookup"><span data-stu-id="6a9d4-144">However, if your application has more than one listener, you should specify unique names for each trace listener, which allows you to identify and manage individual trace listeners within the <xref:System.Diagnostics.Debug.Listeners%2A> and <xref:System.Diagnostics.Trace.Listeners%2A> collections.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6a9d4-145">Adicionar mais de um ouvinte de rastreamento do mesmo tipo e com o mesmo nome resulta em apenas um ouvinte de rastreamento desse tipo e nome que estão `Listeners` sendo adicionados à coleção.</span><span class="sxs-lookup"><span data-stu-id="6a9d4-145">Adding more than one trace listener of the same type and with the same name results in only one trace listener of that type and name being added to the `Listeners` collection.</span></span> <span data-ttu-id="6a9d4-146">No entanto, você pode adicionar programaticamente vários ouvintes idênticos à `Listeners` coleção.</span><span class="sxs-lookup"><span data-stu-id="6a9d4-146">However, you can programmatically add multiple identical listeners to the `Listeners` collection.</span></span>  
  
 <span data-ttu-id="6a9d4-147">O valor do atributo **initializeData** depende do tipo de ouvinte que você criar.</span><span class="sxs-lookup"><span data-stu-id="6a9d4-147">The value for the **initializeData** attribute depends on the type of listener you create.</span></span> <span data-ttu-id="6a9d4-148">Nem todos os ouvintes de rastreamento exigem que você especifique **initializeData**.</span><span class="sxs-lookup"><span data-stu-id="6a9d4-148">Not all trace listeners require that you specify **initializeData**.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6a9d4-149">Ao usar o `initializeData` atributo, você pode obter o aviso do compilador "o atributo ' initializeData ' não está declarado."</span><span class="sxs-lookup"><span data-stu-id="6a9d4-149">When you use the `initializeData` attribute, you may get the compiler warning "The 'initializeData' attribute is not declared."</span></span> <span data-ttu-id="6a9d4-150">Esse aviso ocorre porque as definições de configuração são validadas em relação à <xref:System.Diagnostics.TraceListener>classe base abstrata, que não `initializeData` reconhece o atributo.</span><span class="sxs-lookup"><span data-stu-id="6a9d4-150">This warning occurs because the configuration settings are validated against the abstract base class <xref:System.Diagnostics.TraceListener>, which does not recognize the `initializeData` attribute.</span></span> <span data-ttu-id="6a9d4-151">Normalmente, você pode ignorar esse aviso para implementações de ouvinte de rastreamento que têm um construtor que usa um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="6a9d4-151">Typically, you can ignore this warning for trace listener implementations that have a constructor that takes a parameter.</span></span>  
  
 <span data-ttu-id="6a9d4-152">A tabela a seguir mostra os ouvintes de rastreamento que estão incluídos com o .NET Framework e descreve o valor de seus atributos **initializeData** .</span><span class="sxs-lookup"><span data-stu-id="6a9d4-152">The following table shows the trace listeners that are included with the .NET Framework and describes the value of their **initializeData** attributes.</span></span>  
  
|<span data-ttu-id="6a9d4-153">Classe de ouvinte de rastreamento</span><span class="sxs-lookup"><span data-stu-id="6a9d4-153">Trace listener class</span></span>|<span data-ttu-id="6a9d4-154">valor do atributo initializeData</span><span class="sxs-lookup"><span data-stu-id="6a9d4-154">initializeData attribute value</span></span>|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>|<span data-ttu-id="6a9d4-155">O `useErrorStream` valor<xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> do construtor.</span><span class="sxs-lookup"><span data-stu-id="6a9d4-155">The `useErrorStream` value for the <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> constructor.</span></span>  <span data-ttu-id="6a9d4-156">Defina o `initializeData` atributo como "`true`" para gravar rastreamento e depurar saída para <xref:System.Console.Error%2A?displayProperty=nameWithType>; "`false`" para <xref:System.Console.Out%2A?displayProperty=nameWithType>gravar.</span><span class="sxs-lookup"><span data-stu-id="6a9d4-156">Set the `initializeData` attribute to "`true`" to write trace and debug output to <xref:System.Console.Error%2A?displayProperty=nameWithType>; "`false`" to write to <xref:System.Console.Out%2A?displayProperty=nameWithType>.</span></span>|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>|<span data-ttu-id="6a9d4-157">O nome do arquivo no qual o <xref:System.Diagnostics.DelimitedListTraceListener> é gravado.</span><span class="sxs-lookup"><span data-stu-id="6a9d4-157">The name of the file the <xref:System.Diagnostics.DelimitedListTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|<span data-ttu-id="6a9d4-158">O nome do nome de uma origem de log de eventos existente.</span><span class="sxs-lookup"><span data-stu-id="6a9d4-158">The name of the name of an existing event log source.</span></span>|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|<span data-ttu-id="6a9d4-159">O nome do arquivo no qual as <xref:System.Diagnostics.EventSchemaTraceListener> gravações são gravadas.</span><span class="sxs-lookup"><span data-stu-id="6a9d4-159">The name of the file that the <xref:System.Diagnostics.EventSchemaTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="6a9d4-160">O nome do arquivo no qual as <xref:System.Diagnostics.TextWriterTraceListener> gravações são gravadas.</span><span class="sxs-lookup"><span data-stu-id="6a9d4-160">The name of the file that the <xref:System.Diagnostics.TextWriterTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="6a9d4-161">O nome do arquivo no qual as <xref:System.Diagnostics.XmlWriterTraceListener> gravações são gravadas.</span><span class="sxs-lookup"><span data-stu-id="6a9d4-161">The name of the file that the <xref:System.Diagnostics.XmlWriterTraceListener> writes to.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="6a9d4-162">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6a9d4-162">Example</span></span>  
 <span data-ttu-id="6a9d4-163">O exemplo a seguir mostra como usar  **\<Adicionar >** elementos `MyListener` para adicionar os ouvintes e `MyEventListener` a coleção de **ouvintes** .</span><span class="sxs-lookup"><span data-stu-id="6a9d4-163">The following example shows how to use **\<add>** elements to add the listeners `MyListener` and `MyEventListener` to the **Listeners** collection.</span></span> <span data-ttu-id="6a9d4-164">`MyListener`Cria um arquivo chamado `MyListener.log` e grava a saída no arquivo.</span><span class="sxs-lookup"><span data-stu-id="6a9d4-164">`MyListener` creates a file called `MyListener.log` and writes the output to the file.</span></span> <span data-ttu-id="6a9d4-165">`MyEventListener`Cria uma entrada no log de eventos.</span><span class="sxs-lookup"><span data-stu-id="6a9d4-165">`MyEventListener` creates an entry in the event log.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6a9d4-166">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6a9d4-166">See also</span></span>

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.Debug>
- <xref:System.Diagnostics.EventLogTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- [<span data-ttu-id="6a9d4-167">Esquema de configurações de rastreamento e depuração</span><span class="sxs-lookup"><span data-stu-id="6a9d4-167">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="6a9d4-168">Ouvintes de rastreamento</span><span class="sxs-lookup"><span data-stu-id="6a9d4-168">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
