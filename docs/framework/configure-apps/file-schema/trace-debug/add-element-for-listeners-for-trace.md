---
title: Elemento <add> para <listeners> para <trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/add
helpviewer_keywords:
- initializeData attribute
- <add> element for <listeners>
- add element for <listeners>
ms.assetid: 81e804a3-ef11-4d39-bbde-bfa012c179e2
ms.openlocfilehash: d89a77107e7aff65b007a69c23af34771146570c
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697330"
---
# <a name="add-element-for-listeners-for-trace"></a><span data-ttu-id="a02f7-102">\<add > elemento para > \<listeners para \<trace ></span><span class="sxs-lookup"><span data-stu-id="a02f7-102">\<add> Element for \<listeners> for \<trace></span></span>
<span data-ttu-id="a02f7-103">Adiciona um ouvinte à coleção de **ouvintes** .</span><span class="sxs-lookup"><span data-stu-id="a02f7-103">Adds a listener to the **Listeners** collection.</span></span>  
  
[<span data-ttu-id="a02f7-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="a02f7-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="a02f7-105">&nbsp; @ no__t-1[ **\<System. Diagnostics >** ](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="a02f7-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>  
<span data-ttu-id="a02f7-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<trace >** ](trace-element.md)</span><span class="sxs-lookup"><span data-stu-id="a02f7-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<trace>**](trace-element.md)</span></span>  
<span data-ttu-id="a02f7-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5[ **\<listeners >** ](listeners-element-for-trace.md)</span><span class="sxs-lookup"><span data-stu-id="a02f7-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-trace.md)</span></span>  
<span data-ttu-id="a02f7-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Adicionar >**</span><span class="sxs-lookup"><span data-stu-id="a02f7-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a02f7-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a02f7-109">Syntax</span></span>  
  
```xml  
<add name="name"   
     type="trace listener class name, Version, Culture, PublicKeyToken"  
     initializeData="data"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a02f7-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="a02f7-110">Attributes and Elements</span></span>  
 <span data-ttu-id="a02f7-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="a02f7-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a02f7-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="a02f7-112">Attributes</span></span>  
  
|<span data-ttu-id="a02f7-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="a02f7-113">Attribute</span></span>|<span data-ttu-id="a02f7-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="a02f7-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a02f7-115">**type**</span><span class="sxs-lookup"><span data-stu-id="a02f7-115">**type**</span></span>|<span data-ttu-id="a02f7-116">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="a02f7-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="a02f7-117">Especifica o tipo do ouvinte.</span><span class="sxs-lookup"><span data-stu-id="a02f7-117">Specifies the type of the listener.</span></span> <span data-ttu-id="a02f7-118">Você deve usar uma cadeia de caracteres que atenda aos requisitos especificados na [especificação de nomes de tipo totalmente qualificados](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="a02f7-118">You must use a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|<span data-ttu-id="a02f7-119">**initializeData**</span><span class="sxs-lookup"><span data-stu-id="a02f7-119">**initializeData**</span></span>|<span data-ttu-id="a02f7-120">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="a02f7-120">Optional attribute.</span></span><br /><br /> <span data-ttu-id="a02f7-121">A cadeia de caracteres passada para o construtor para a classe especificada.</span><span class="sxs-lookup"><span data-stu-id="a02f7-121">The string passed to the constructor for the specified class.</span></span>|  
|<span data-ttu-id="a02f7-122">**name**</span><span class="sxs-lookup"><span data-stu-id="a02f7-122">**name**</span></span>|<span data-ttu-id="a02f7-123">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="a02f7-123">Optional attribute.</span></span><br /><br /> <span data-ttu-id="a02f7-124">Especifica o nome do ouvinte.</span><span class="sxs-lookup"><span data-stu-id="a02f7-124">Specifies the name of the listener.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a02f7-125">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="a02f7-125">Child Elements</span></span>  
  
|<span data-ttu-id="a02f7-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="a02f7-126">Element</span></span>|<span data-ttu-id="a02f7-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="a02f7-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a02f7-128">\<filter></span><span class="sxs-lookup"><span data-stu-id="a02f7-128">\<filter></span></span>](filter-element-for-add-for-listeners-for-trace.md)|<span data-ttu-id="a02f7-129">Adiciona um filtro a um ouvinte na coleção `Listeners` para um rastreamento.</span><span class="sxs-lookup"><span data-stu-id="a02f7-129">Adds a filter to a listener in the `Listeners` collection for a trace.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a02f7-130">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="a02f7-130">Parent Elements</span></span>  
  
|<span data-ttu-id="a02f7-131">Elemento</span><span class="sxs-lookup"><span data-stu-id="a02f7-131">Element</span></span>|<span data-ttu-id="a02f7-132">Descrição</span><span class="sxs-lookup"><span data-stu-id="a02f7-132">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="a02f7-133">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a02f7-133">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`listeners`|<span data-ttu-id="a02f7-134">Especifica um ouvinte que coleta, armazena e roteia mensagens.</span><span class="sxs-lookup"><span data-stu-id="a02f7-134">Specifies a listener that collects, stores, and routes messages.</span></span> <span data-ttu-id="a02f7-135">Os ouvintes direcionam a saída de rastreamento para um destino apropriado.</span><span class="sxs-lookup"><span data-stu-id="a02f7-135">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="a02f7-136">Especifica o elemento raiz para a seção de configuração ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="a02f7-136">Specifies the root element for the ASP.NET configuration section.</span></span>|  
|`trace`|<span data-ttu-id="a02f7-137">Contém os ouvintes que coletam, armazenam e roteiam mensagens de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="a02f7-137">Contains listeners that collect, store, and route tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a02f7-138">Comentários</span><span class="sxs-lookup"><span data-stu-id="a02f7-138">Remarks</span></span>  
 <span data-ttu-id="a02f7-139">As classes <xref:System.Diagnostics.Debug> e <xref:System.Diagnostics.Trace> compartilham a mesma coleção de **ouvintes** .</span><span class="sxs-lookup"><span data-stu-id="a02f7-139">The <xref:System.Diagnostics.Debug> and <xref:System.Diagnostics.Trace> classes share the same **Listeners** collection.</span></span> <span data-ttu-id="a02f7-140">Se você adicionar um objeto de ouvinte à coleção em uma dessas classes, a outra classe usará o mesmo ouvinte.</span><span class="sxs-lookup"><span data-stu-id="a02f7-140">If you add a listener object to the collection in one of these classes, the other class uses the same listener.</span></span> <span data-ttu-id="a02f7-141">As classes de ouvinte derivam do <xref:System.Diagnostics.TraceListener>.</span><span class="sxs-lookup"><span data-stu-id="a02f7-141">The listener classes derive from the <xref:System.Diagnostics.TraceListener>.</span></span>  
  
 <span data-ttu-id="a02f7-142">Se você não especificar o atributo `name` do ouvinte de rastreamento, o <xref:System.Diagnostics.TraceListener.Name%2A> do ouvinte de rastreamento assume como padrão uma cadeia de caracteres vazia ("").</span><span class="sxs-lookup"><span data-stu-id="a02f7-142">If you do not specify the `name` attribute of the trace listener, the <xref:System.Diagnostics.TraceListener.Name%2A> of the trace listener defaults to an empty string ("").</span></span> <span data-ttu-id="a02f7-143">Se seu aplicativo tiver apenas um ouvinte, você poderá adicioná-lo sem especificar um nome e removê-lo especificando uma cadeia de caracteres vazia para o nome.</span><span class="sxs-lookup"><span data-stu-id="a02f7-143">If your application has only one listener, you can add it without specifying a name, and remove it by specifying an empty string for the name.</span></span> <span data-ttu-id="a02f7-144">No entanto, se seu aplicativo tiver mais de um ouvinte, você deverá especificar nomes exclusivos para cada ouvinte de rastreamento, o que permite identificar e gerenciar ouvintes de rastreamento individuais nas coleções <xref:System.Diagnostics.Debug.Listeners%2A> e <xref:System.Diagnostics.Trace.Listeners%2A>.</span><span class="sxs-lookup"><span data-stu-id="a02f7-144">However, if your application has more than one listener, you should specify unique names for each trace listener, which allows you to identify and manage individual trace listeners within the <xref:System.Diagnostics.Debug.Listeners%2A> and <xref:System.Diagnostics.Trace.Listeners%2A> collections.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a02f7-145">Adicionar mais de um ouvinte de rastreamento do mesmo tipo e com o mesmo nome resulta em apenas um ouvinte de rastreamento desse tipo e nome que estão sendo adicionados à coleção `Listeners`.</span><span class="sxs-lookup"><span data-stu-id="a02f7-145">Adding more than one trace listener of the same type and with the same name results in only one trace listener of that type and name being added to the `Listeners` collection.</span></span> <span data-ttu-id="a02f7-146">No entanto, você pode adicionar programaticamente vários ouvintes idênticos à coleção `Listeners`.</span><span class="sxs-lookup"><span data-stu-id="a02f7-146">However, you can programmatically add multiple identical listeners to the `Listeners` collection.</span></span>  
  
 <span data-ttu-id="a02f7-147">O valor do atributo **initializeData** depende do tipo de ouvinte que você criar.</span><span class="sxs-lookup"><span data-stu-id="a02f7-147">The value for the **initializeData** attribute depends on the type of listener you create.</span></span> <span data-ttu-id="a02f7-148">Nem todos os ouvintes de rastreamento exigem que você especifique **initializeData**.</span><span class="sxs-lookup"><span data-stu-id="a02f7-148">Not all trace listeners require that you specify **initializeData**.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a02f7-149">Ao usar o atributo `initializeData`, você pode obter o aviso do compilador "o atributo ' initializeData ' não está declarado".</span><span class="sxs-lookup"><span data-stu-id="a02f7-149">When you use the `initializeData` attribute, you may get the compiler warning "The 'initializeData' attribute is not declared."</span></span> <span data-ttu-id="a02f7-150">Esse aviso ocorre porque as definições de configuração são validadas em relação à classe base abstrata <xref:System.Diagnostics.TraceListener>, que não reconhece o atributo `initializeData`.</span><span class="sxs-lookup"><span data-stu-id="a02f7-150">This warning occurs because the configuration settings are validated against the abstract base class <xref:System.Diagnostics.TraceListener>, which does not recognize the `initializeData` attribute.</span></span> <span data-ttu-id="a02f7-151">Normalmente, você pode ignorar esse aviso para implementações de ouvinte de rastreamento que têm um construtor que usa um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="a02f7-151">Typically, you can ignore this warning for trace listener implementations that have a constructor that takes a parameter.</span></span>  
  
 <span data-ttu-id="a02f7-152">A tabela a seguir mostra os ouvintes de rastreamento que estão incluídos com o .NET Framework e descreve o valor de seus atributos **initializeData** .</span><span class="sxs-lookup"><span data-stu-id="a02f7-152">The following table shows the trace listeners that are included with the .NET Framework and describes the value of their **initializeData** attributes.</span></span>  
  
|<span data-ttu-id="a02f7-153">Classe de ouvinte de rastreamento</span><span class="sxs-lookup"><span data-stu-id="a02f7-153">Trace listener class</span></span>|<span data-ttu-id="a02f7-154">valor do atributo initializeData</span><span class="sxs-lookup"><span data-stu-id="a02f7-154">initializeData attribute value</span></span>|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>|<span data-ttu-id="a02f7-155">O valor `useErrorStream` para o Construtor <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A>.</span><span class="sxs-lookup"><span data-stu-id="a02f7-155">The `useErrorStream` value for the <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> constructor.</span></span>  <span data-ttu-id="a02f7-156">Defina o atributo `initializeData` como "`true`" para gravar rastreamento e depurar saída para <xref:System.Console.Error%2A?displayProperty=nameWithType>; "`false`" para gravar em <xref:System.Console.Out%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a02f7-156">Set the `initializeData` attribute to "`true`" to write trace and debug output to <xref:System.Console.Error%2A?displayProperty=nameWithType>; "`false`" to write to <xref:System.Console.Out%2A?displayProperty=nameWithType>.</span></span>|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>|<span data-ttu-id="a02f7-157">O nome do arquivo no qual o <xref:System.Diagnostics.DelimitedListTraceListener> é gravado.</span><span class="sxs-lookup"><span data-stu-id="a02f7-157">The name of the file the <xref:System.Diagnostics.DelimitedListTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|<span data-ttu-id="a02f7-158">O nome do nome de uma origem de log de eventos existente.</span><span class="sxs-lookup"><span data-stu-id="a02f7-158">The name of the name of an existing event log source.</span></span>|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|<span data-ttu-id="a02f7-159">O nome do arquivo no qual o <xref:System.Diagnostics.EventSchemaTraceListener> grava.</span><span class="sxs-lookup"><span data-stu-id="a02f7-159">The name of the file that the <xref:System.Diagnostics.EventSchemaTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="a02f7-160">O nome do arquivo no qual o <xref:System.Diagnostics.TextWriterTraceListener> grava.</span><span class="sxs-lookup"><span data-stu-id="a02f7-160">The name of the file that the <xref:System.Diagnostics.TextWriterTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="a02f7-161">O nome do arquivo no qual o <xref:System.Diagnostics.XmlWriterTraceListener> grava.</span><span class="sxs-lookup"><span data-stu-id="a02f7-161">The name of the file that the <xref:System.Diagnostics.XmlWriterTraceListener> writes to.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="a02f7-162">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a02f7-162">Example</span></span>  
 <span data-ttu-id="a02f7-163">O exemplo a seguir mostra como usar elementos **de > de @no__t 1add** para adicionar os ouvintes `MyListener` e `MyEventListener` à coleção de **ouvintes** .</span><span class="sxs-lookup"><span data-stu-id="a02f7-163">The following example shows how to use **\<add>** elements to add the listeners `MyListener` and `MyEventListener` to the **Listeners** collection.</span></span> <span data-ttu-id="a02f7-164">`MyListener` cria um arquivo chamado `MyListener.log` e grava a saída no arquivo.</span><span class="sxs-lookup"><span data-stu-id="a02f7-164">`MyListener` creates a file called `MyListener.log` and writes the output to the file.</span></span> <span data-ttu-id="a02f7-165">`MyEventListener` cria uma entrada no log de eventos.</span><span class="sxs-lookup"><span data-stu-id="a02f7-165">`MyEventListener` creates an entry in the event log.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a02f7-166">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a02f7-166">See also</span></span>

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.Debug>
- <xref:System.Diagnostics.EventLogTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- [<span data-ttu-id="a02f7-167">Esquema de configurações de rastreamento e depuração</span><span class="sxs-lookup"><span data-stu-id="a02f7-167">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="a02f7-168">Ouvintes de rastreamento</span><span class="sxs-lookup"><span data-stu-id="a02f7-168">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
