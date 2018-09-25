---
title: '&lt;Adicione&gt; elemento para &lt;ouvintes&gt; para &lt;fonte&gt;'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/add
helpviewer_keywords:
- initializeData attribute
- add element for <listeners> for <source>
- <add> element for <listeners> for <source>
ms.assetid: 4ce36ac1-81ef-48e8-b8b2-b5a5b0e2adcb
author: mcleblanc
ms.author: markl
ms.openlocfilehash: c0ab15f6eca8b20653530583016eb849273c4ce1
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47072015"
---
# <a name="ltaddgt-element-for-ltlistenersgt-for-ltsourcegt"></a><span data-ttu-id="55e9a-102">&lt;Adicione&gt; elemento para &lt;ouvintes&gt; para &lt;fonte&gt;</span><span class="sxs-lookup"><span data-stu-id="55e9a-102">&lt;add&gt; Element for &lt;listeners&gt; for &lt;source&gt;</span></span>
<span data-ttu-id="55e9a-103">Adiciona um ouvinte na coleção `Listeners` de uma origem de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="55e9a-103">Adds a listener to the `Listeners` collection for a trace source.</span></span>  
  
 <span data-ttu-id="55e9a-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="55e9a-104">\<configuration></span></span>  
<span data-ttu-id="55e9a-105">\<System. Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="55e9a-105">\<system.diagnostics></span></span>  
<span data-ttu-id="55e9a-106">\<fontes ></span><span class="sxs-lookup"><span data-stu-id="55e9a-106">\<sources></span></span>  
<span data-ttu-id="55e9a-107">\<origem ></span><span class="sxs-lookup"><span data-stu-id="55e9a-107">\<source></span></span>  
<span data-ttu-id="55e9a-108">\<ouvintes ></span><span class="sxs-lookup"><span data-stu-id="55e9a-108">\<listeners></span></span>  
<span data-ttu-id="55e9a-109">\<add></span><span class="sxs-lookup"><span data-stu-id="55e9a-109">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55e9a-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="55e9a-110">Syntax</span></span>  
  
```xml  
<add name="name"   
  type="TraceListenerClassName, Version, Culture, PublicKeyToken"  
  initializeData="data"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="55e9a-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="55e9a-111">Attributes and Elements</span></span>  
 <span data-ttu-id="55e9a-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="55e9a-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="55e9a-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="55e9a-113">Attributes</span></span>  
  
|<span data-ttu-id="55e9a-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="55e9a-114">Attribute</span></span>|<span data-ttu-id="55e9a-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="55e9a-115">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="55e9a-116">Com atributo obrigatório, a menos que você está fazendo referência a um ouvinte na `sharedListeners` coleção na qual caso, você só precisa fazer referência a ele por nome (consulte a [exemplo](#example)).</span><span class="sxs-lookup"><span data-stu-id="55e9a-116">Required attribute, unless you're referencing a listener in the `sharedListeners` collection, in which case you only need to refer to it by name (see the [Example](#example)).</span></span><br /><br /> <span data-ttu-id="55e9a-117">Especifica o tipo do ouvinte.</span><span class="sxs-lookup"><span data-stu-id="55e9a-117">Specifies the type of the listener.</span></span> <span data-ttu-id="55e9a-118">Você deve usar uma cadeia de caracteres que atenda aos requisitos especificados em [especificando nomes de tipo totalmente qualificados](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="55e9a-118">You must use a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="55e9a-119">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="55e9a-119">Optional attribute.</span></span><br /><br /> <span data-ttu-id="55e9a-120">A cadeia de caracteres passada para o construtor para a classe especificada.</span><span class="sxs-lookup"><span data-stu-id="55e9a-120">The string passed to the constructor for the specified class.</span></span> <span data-ttu-id="55e9a-121">Um <xref:System.Configuration.ConfigurationException> será gerada se a classe não tem um construtor que aceita uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="55e9a-121">A <xref:System.Configuration.ConfigurationException> is thrown if the class does not have a constructor that takes a string.</span></span>|  
|`name`|<span data-ttu-id="55e9a-122">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="55e9a-122">Optional attribute.</span></span><br /><br /> <span data-ttu-id="55e9a-123">Especifica o nome do ouvinte.</span><span class="sxs-lookup"><span data-stu-id="55e9a-123">Specifies the name of the listener.</span></span>|  
|`traceOutputOptions`|<span data-ttu-id="55e9a-124">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="55e9a-124">Optional attribute.</span></span><br /><br /> <span data-ttu-id="55e9a-125">Especifica o <xref:System.Diagnostics.TraceListener.TraceOutputOptions%2A> valor da propriedade para o ouvinte de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="55e9a-125">Specifies the <xref:System.Diagnostics.TraceListener.TraceOutputOptions%2A> property value for the trace listener.</span></span>|  
|<span data-ttu-id="55e9a-126">[atributos personalizados]</span><span class="sxs-lookup"><span data-stu-id="55e9a-126">[custom attributes]</span></span>|<span data-ttu-id="55e9a-127">Atributos opcionais.</span><span class="sxs-lookup"><span data-stu-id="55e9a-127">Optional attributes.</span></span><br /><br /> <span data-ttu-id="55e9a-128">Especifica o valor para os atributos de ouvinte específico identificado pelo <xref:System.Diagnostics.TraceListener.GetSupportedAttributes%2A> método para esse ouvinte.</span><span class="sxs-lookup"><span data-stu-id="55e9a-128">Specifies the value for listener-specific attributes identified by the <xref:System.Diagnostics.TraceListener.GetSupportedAttributes%2A> method for that listener.</span></span> <span data-ttu-id="55e9a-129"><xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A> é um exemplo de um atributo extra exclusivo para o <xref:System.Diagnostics.DelimitedListTraceListener> classe.</span><span class="sxs-lookup"><span data-stu-id="55e9a-129"><xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A> is an example of an extra attribute unique to the <xref:System.Diagnostics.DelimitedListTraceListener> class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="55e9a-130">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="55e9a-130">Child Elements</span></span>  
  
|<span data-ttu-id="55e9a-131">Elemento</span><span class="sxs-lookup"><span data-stu-id="55e9a-131">Element</span></span>|<span data-ttu-id="55e9a-132">Descrição</span><span class="sxs-lookup"><span data-stu-id="55e9a-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="55e9a-133">\<filter></span><span class="sxs-lookup"><span data-stu-id="55e9a-133">\<filter></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/filter-element-for-add-for-listeners-for-source.md)|<span data-ttu-id="55e9a-134">Adiciona um filtro a um ouvinte na coleção `Listeners` de uma origem de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="55e9a-134">Adds a filter to a listener in the `Listeners` collection for a trace source.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="55e9a-135">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="55e9a-135">Parent Elements</span></span>  
  
|<span data-ttu-id="55e9a-136">Elemento</span><span class="sxs-lookup"><span data-stu-id="55e9a-136">Element</span></span>|<span data-ttu-id="55e9a-137">Descrição</span><span class="sxs-lookup"><span data-stu-id="55e9a-137">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="55e9a-138">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="55e9a-138">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="55e9a-139">Especifica os ouvintes de rastreamento que coletam, armazenam e roteiam mensagens e o nível em que uma opção de rastreamento é definida.</span><span class="sxs-lookup"><span data-stu-id="55e9a-139">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="55e9a-140">Contém as origens de rastreamento que iniciam as mensagens de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="55e9a-140">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="55e9a-141">Especifica uma origem de rastreamento que inicia as mensagens de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="55e9a-141">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="55e9a-142">Especifica os ouvintes que coletam, armazenam e roteiam mensagens.</span><span class="sxs-lookup"><span data-stu-id="55e9a-142">Specifies listeners that collect, store, and route messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="55e9a-143">Comentários</span><span class="sxs-lookup"><span data-stu-id="55e9a-143">Remarks</span></span>  
 <span data-ttu-id="55e9a-144">As classes de ouvinte que acompanham o .NET Framework derivam o <xref:System.Diagnostics.TraceListener> classe.</span><span class="sxs-lookup"><span data-stu-id="55e9a-144">The listener classes shipped with the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span>  
  
 <span data-ttu-id="55e9a-145">Se você não especificar o `name` atributo do ouvinte de rastreamento, o <xref:System.Diagnostics.TraceListener.Name%2A> propriedade do ouvinte de rastreamento padrão é uma cadeia de caracteres vazia ("").</span><span class="sxs-lookup"><span data-stu-id="55e9a-145">If you do not specify the `name` attribute of the trace listener, the <xref:System.Diagnostics.TraceListener.Name%2A> property of the trace listener defaults to an empty string ("").</span></span> <span data-ttu-id="55e9a-146">Se seu aplicativo tiver somente um ouvinte, você pode adicioná-lo sem especificar um nome, e você pode removê-lo especificando uma cadeia de caracteres vazia para o nome.</span><span class="sxs-lookup"><span data-stu-id="55e9a-146">If your application has only one listener, you can add it without specifying a name, and you can remove it by specifying an empty string for the name.</span></span> <span data-ttu-id="55e9a-147">No entanto, se seu aplicativo tiver mais de um ouvinte, você deve especificar um nome exclusivo para cada ouvinte de rastreamento, que permite que você identifique e gerencie os ouvintes de rastreamento individuais a <xref:System.Diagnostics.TraceSource.Listeners%2A?displayProperty=nameWithType> coleção.</span><span class="sxs-lookup"><span data-stu-id="55e9a-147">However, if your application has more than one listener, you should specify a unique name for each trace listener, which allows you to identify and manage individual trace listeners in the <xref:System.Diagnostics.TraceSource.Listeners%2A?displayProperty=nameWithType> collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="55e9a-148">Adicionando mais de um ouvinte de rastreamento do mesmo tipo e com o mesmo nome resultados no ouvinte de rastreamento somente um desse tipo e nomeie o que está sendo adicionado ao `Listeners` coleção.</span><span class="sxs-lookup"><span data-stu-id="55e9a-148">Adding more than one trace listener of the same type and with the same name results in only one trace listener of that type and name being added to the `Listeners` collection.</span></span> <span data-ttu-id="55e9a-149">No entanto, você pode adicionar programaticamente várias escutas idênticas a `Listeners` coleção.</span><span class="sxs-lookup"><span data-stu-id="55e9a-149">However, you can programmatically add multiple identical listeners to the `Listeners` collection.</span></span>  
  
 <span data-ttu-id="55e9a-150">O valor para o `initializeData` atributo depende do tipo de ouvinte que você cria.</span><span class="sxs-lookup"><span data-stu-id="55e9a-150">The value for the `initializeData` attribute depends on the type of listener you create.</span></span> <span data-ttu-id="55e9a-151">Nem todos os ouvintes de rastreamento requerem que você especifique `initializeData`.</span><span class="sxs-lookup"><span data-stu-id="55e9a-151">Not all trace listeners require that you specify `initializeData`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="55e9a-152">Quando você usa o `initializeData` atributo, você pode receber o aviso "o atributo 'initializeData' não é declarado" do compilador</span><span class="sxs-lookup"><span data-stu-id="55e9a-152">When you use the `initializeData` attribute, you may get the compiler warning "The 'initializeData' attribute is not declared."</span></span> <span data-ttu-id="55e9a-153">Este aviso ocorre porque as definições de configuração são validadas em relação a classe base abstrata <xref:System.Diagnostics.TraceListener>, que não reconhece o `initializeData` atributo.</span><span class="sxs-lookup"><span data-stu-id="55e9a-153">This warning occurs because the configuration settings are validated against the abstract base class <xref:System.Diagnostics.TraceListener>, which does not recognize the `initializeData` attribute.</span></span> <span data-ttu-id="55e9a-154">Normalmente, você pode ignorar este aviso para as implementações de ouvinte de rastreamento que tem um construtor que aceita um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="55e9a-154">Typically, you can ignore this warning for trace listener implementations that have a constructor that takes a parameter.</span></span>  
  
 <span data-ttu-id="55e9a-155">A tabela a seguir mostra os ouvintes de rastreamento que são incluídos com o .NET Framework e descreve o valor de suas `initializeData` atributos.</span><span class="sxs-lookup"><span data-stu-id="55e9a-155">The following table shows the trace listeners that are included with the .NET Framework and describes the value of their `initializeData` attributes.</span></span>  
  
|<span data-ttu-id="55e9a-156">Classe de ouvintes de rastreamento</span><span class="sxs-lookup"><span data-stu-id="55e9a-156">Trace listener class</span></span>|<span data-ttu-id="55e9a-157">valor do atributo initializeData</span><span class="sxs-lookup"><span data-stu-id="55e9a-157">initializeData attribute value</span></span>|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>|<span data-ttu-id="55e9a-158">O `useErrorStream` de valor para o <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> construtor.</span><span class="sxs-lookup"><span data-stu-id="55e9a-158">The `useErrorStream` value for the <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> constructor.</span></span>  <span data-ttu-id="55e9a-159">Defina as `initializeData` de atributo para "`true`"gravar saída de rastreamento e depuração para o fluxo de erro padrão; defina-"`false`" para gravar no fluxo de saída padrão.</span><span class="sxs-lookup"><span data-stu-id="55e9a-159">Set the `initializeData` attribute to "`true`" to write trace and debug output to the standard error stream; set it to "`false`" to write to the standard output stream.</span></span>|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>|<span data-ttu-id="55e9a-160">O nome do arquivo no qual o <xref:System.Diagnostics.DelimitedListTraceListener> é gravado.</span><span class="sxs-lookup"><span data-stu-id="55e9a-160">The name of the file the <xref:System.Diagnostics.DelimitedListTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|<span data-ttu-id="55e9a-161">O nome da origem de um log de eventos existente.</span><span class="sxs-lookup"><span data-stu-id="55e9a-161">The name of an existing event log source.</span></span>|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|<span data-ttu-id="55e9a-162">O nome do arquivo que o <xref:System.Diagnostics.EventSchemaTraceListener> grava.</span><span class="sxs-lookup"><span data-stu-id="55e9a-162">The name of the file that the <xref:System.Diagnostics.EventSchemaTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="55e9a-163">O nome do arquivo que o <xref:System.Diagnostics.TextWriterTraceListener> grava.</span><span class="sxs-lookup"><span data-stu-id="55e9a-163">The name of the file that the <xref:System.Diagnostics.TextWriterTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="55e9a-164">O nome do arquivo que o <xref:System.Diagnostics.XmlWriterTraceListener> grava.</span><span class="sxs-lookup"><span data-stu-id="55e9a-164">The name of the file that the <xref:System.Diagnostics.XmlWriterTraceListener> writes to.</span></span>|  
  
## <a name="configuration-file"></a><span data-ttu-id="55e9a-165">Arquivo de Configuração</span><span class="sxs-lookup"><span data-stu-id="55e9a-165">Configuration File</span></span>  
 <span data-ttu-id="55e9a-166">Esse elemento pode ser usado no arquivo de configuração de máquina (Machine. config) e o arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="55e9a-166">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="55e9a-167">Exemplo</span><span class="sxs-lookup"><span data-stu-id="55e9a-167">Example</span></span>  
 <span data-ttu-id="55e9a-168">O exemplo a seguir mostra como usar `<add>` elementos para adicionar os ouvintes `console` e `textListener` para o `Listeners` coleção para a origem de rastreamento `TraceSourceApp`.</span><span class="sxs-lookup"><span data-stu-id="55e9a-168">The following example shows how to use `<add>` elements to add the listeners `console` and `textListener` to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span> <span data-ttu-id="55e9a-169">O `textListener` ouvinte grava a saída de rastreamento para o arquivo myListener.log.</span><span class="sxs-lookup"><span data-stu-id="55e9a-169">The `textListener` listener writes trace output to the file myListener.log.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="TraceSourceApp" switchName="sourceSwitch"   
        switchType="System.Diagnostics.SourceSwitch">  
        <listeners>  
          <add name="console"   
            type="System.Diagnostics.ConsoleTraceListener"/>  
          <add name="textListener"/>  
          <remove name="Default"/>  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add name="textListener"   
        type="System.Diagnostics.TextWriterTraceListener"   
        initializeData="myListener.log"/>  
    </sharedListeners>  
    <switches>  
      <add name="sourceSwitch" value="Warning"/>  
    </switches>  
  </system.diagnostics>  
</configuration>   
```  
  
## <a name="see-also"></a><span data-ttu-id="55e9a-170">Consulte também</span><span class="sxs-lookup"><span data-stu-id="55e9a-170">See Also</span></span>  
 <xref:System.Diagnostics.TraceSource>  
 <xref:System.Diagnostics.TraceListener>  
 [<span data-ttu-id="55e9a-171">Esquema de configurações de rastreamento e depuração</span><span class="sxs-lookup"><span data-stu-id="55e9a-171">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)  
 [<span data-ttu-id="55e9a-172">Ouvintes de rastreamento</span><span class="sxs-lookup"><span data-stu-id="55e9a-172">Trace Listeners</span></span>](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
