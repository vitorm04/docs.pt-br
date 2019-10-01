---
title: Elemento <add> para <listeners> para <source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/add
helpviewer_keywords:
- initializeData attribute
- add element for <listeners> for <source>
- <add> element for <listeners> for <source>
ms.assetid: 4ce36ac1-81ef-48e8-b8b2-b5a5b0e2adcb
ms.openlocfilehash: 0818d7ec248b210f215759069b9f69a3e29637f5
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699398"
---
# <a name="add-element-for-listeners-for-source"></a><span data-ttu-id="6c28c-102">\<add > elemento para > \<listeners para \<source ></span><span class="sxs-lookup"><span data-stu-id="6c28c-102">\<add> Element for \<listeners> for \<source></span></span>
<span data-ttu-id="6c28c-103">Adiciona um ouvinte na coleção `Listeners` de uma origem de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="6c28c-103">Adds a listener to the `Listeners` collection for a trace source.</span></span>  
  
[<span data-ttu-id="6c28c-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="6c28c-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="6c28c-105">&nbsp; @ no__t-1[ **\<System. Diagnostics >** ](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="6c28c-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>  
<span data-ttu-id="6c28c-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<sources >** ](sources-element.md)</span><span class="sxs-lookup"><span data-stu-id="6c28c-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)</span></span>  
<span data-ttu-id="6c28c-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5[ **\<source >** ](source-element.md)</span><span class="sxs-lookup"><span data-stu-id="6c28c-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<source>**](source-element.md)</span></span>  
<span data-ttu-id="6c28c-108">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 @ no__t-7[ **&nbsp;0listeners >** ](listeners-element-for-source.md)</span><span class="sxs-lookup"><span data-stu-id="6c28c-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-source.md)</span></span>  
<span data-ttu-id="6c28c-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<add>**</span><span class="sxs-lookup"><span data-stu-id="6c28c-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c28c-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6c28c-110">Syntax</span></span>  
  
```xml  
<add name="name"   
  type="TraceListenerClassName, Version, Culture, PublicKeyToken"  
  initializeData="data"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6c28c-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="6c28c-111">Attributes and Elements</span></span>  
 <span data-ttu-id="6c28c-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="6c28c-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6c28c-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="6c28c-113">Attributes</span></span>  
  
|<span data-ttu-id="6c28c-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="6c28c-114">Attribute</span></span>|<span data-ttu-id="6c28c-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="6c28c-115">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="6c28c-116">Atributo obrigatório, a menos que você esteja fazendo referência a um ouvinte na coleção `sharedListeners`; nesse caso, você só precisa fazer referência a ele por nome (consulte o [exemplo](#example)).</span><span class="sxs-lookup"><span data-stu-id="6c28c-116">Required attribute, unless you're referencing a listener in the `sharedListeners` collection, in which case you only need to refer to it by name (see the [Example](#example)).</span></span><br /><br /> <span data-ttu-id="6c28c-117">Especifica o tipo do ouvinte.</span><span class="sxs-lookup"><span data-stu-id="6c28c-117">Specifies the type of the listener.</span></span> <span data-ttu-id="6c28c-118">Você deve usar uma cadeia de caracteres que atenda aos requisitos especificados na [especificação de nomes de tipo totalmente qualificados](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="6c28c-118">You must use a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="6c28c-119">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="6c28c-119">Optional attribute.</span></span><br /><br /> <span data-ttu-id="6c28c-120">A cadeia de caracteres passada para o construtor para a classe especificada.</span><span class="sxs-lookup"><span data-stu-id="6c28c-120">The string passed to the constructor for the specified class.</span></span> <span data-ttu-id="6c28c-121">Um <xref:System.Configuration.ConfigurationException> será gerado se a classe não tiver um construtor que usa uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="6c28c-121">A <xref:System.Configuration.ConfigurationException> is thrown if the class does not have a constructor that takes a string.</span></span>|  
|`name`|<span data-ttu-id="6c28c-122">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="6c28c-122">Optional attribute.</span></span><br /><br /> <span data-ttu-id="6c28c-123">Especifica o nome do ouvinte.</span><span class="sxs-lookup"><span data-stu-id="6c28c-123">Specifies the name of the listener.</span></span>|  
|`traceOutputOptions`|<span data-ttu-id="6c28c-124">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="6c28c-124">Optional attribute.</span></span><br /><br /> <span data-ttu-id="6c28c-125">Especifica o valor da propriedade <xref:System.Diagnostics.TraceListener.TraceOutputOptions%2A> para o ouvinte de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="6c28c-125">Specifies the <xref:System.Diagnostics.TraceListener.TraceOutputOptions%2A> property value for the trace listener.</span></span>|  
|<span data-ttu-id="6c28c-126">[atributos personalizados]</span><span class="sxs-lookup"><span data-stu-id="6c28c-126">[custom attributes]</span></span>|<span data-ttu-id="6c28c-127">Atributos opcionais.</span><span class="sxs-lookup"><span data-stu-id="6c28c-127">Optional attributes.</span></span><br /><br /> <span data-ttu-id="6c28c-128">Especifica o valor para atributos específicos do ouvinte identificados pelo método <xref:System.Diagnostics.TraceListener.GetSupportedAttributes%2A> para esse ouvinte.</span><span class="sxs-lookup"><span data-stu-id="6c28c-128">Specifies the value for listener-specific attributes identified by the <xref:System.Diagnostics.TraceListener.GetSupportedAttributes%2A> method for that listener.</span></span> <span data-ttu-id="6c28c-129"><xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A> é um exemplo de um atributo extra exclusivo para a classe <xref:System.Diagnostics.DelimitedListTraceListener>.</span><span class="sxs-lookup"><span data-stu-id="6c28c-129"><xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A> is an example of an extra attribute unique to the <xref:System.Diagnostics.DelimitedListTraceListener> class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6c28c-130">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="6c28c-130">Child Elements</span></span>  
  
|<span data-ttu-id="6c28c-131">Elemento</span><span class="sxs-lookup"><span data-stu-id="6c28c-131">Element</span></span>|<span data-ttu-id="6c28c-132">Descrição</span><span class="sxs-lookup"><span data-stu-id="6c28c-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6c28c-133">\<filter></span><span class="sxs-lookup"><span data-stu-id="6c28c-133">\<filter></span></span>](filter-element-for-add-for-listeners-for-source.md)|<span data-ttu-id="6c28c-134">Adiciona um filtro a um ouvinte na coleção `Listeners` de uma origem de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="6c28c-134">Adds a filter to a listener in the `Listeners` collection for a trace source.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6c28c-135">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="6c28c-135">Parent Elements</span></span>  
  
|<span data-ttu-id="6c28c-136">Elemento</span><span class="sxs-lookup"><span data-stu-id="6c28c-136">Element</span></span>|<span data-ttu-id="6c28c-137">Descrição</span><span class="sxs-lookup"><span data-stu-id="6c28c-137">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="6c28c-138">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6c28c-138">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="6c28c-139">Especifica os ouvintes de rastreamento que coletam, armazenam e roteiam mensagens e o nível em que uma opção de rastreamento é definida.</span><span class="sxs-lookup"><span data-stu-id="6c28c-139">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="6c28c-140">Contém as origens de rastreamento que iniciam as mensagens de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="6c28c-140">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="6c28c-141">Especifica uma origem de rastreamento que inicia as mensagens de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="6c28c-141">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="6c28c-142">Especifica os ouvintes que coletam, armazenam e roteiam mensagens.</span><span class="sxs-lookup"><span data-stu-id="6c28c-142">Specifies listeners that collect, store, and route messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6c28c-143">Comentários</span><span class="sxs-lookup"><span data-stu-id="6c28c-143">Remarks</span></span>  
 <span data-ttu-id="6c28c-144">As classes de ouvinte fornecidas com o .NET Framework derivam da classe <xref:System.Diagnostics.TraceListener>.</span><span class="sxs-lookup"><span data-stu-id="6c28c-144">The listener classes shipped with the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span>  
  
 <span data-ttu-id="6c28c-145">Se você não especificar o atributo `name` do ouvinte de rastreamento, a propriedade <xref:System.Diagnostics.TraceListener.Name%2A> do ouvinte de rastreamento será padronizada como uma cadeia de caracteres vazia ("").</span><span class="sxs-lookup"><span data-stu-id="6c28c-145">If you do not specify the `name` attribute of the trace listener, the <xref:System.Diagnostics.TraceListener.Name%2A> property of the trace listener defaults to an empty string ("").</span></span> <span data-ttu-id="6c28c-146">Se seu aplicativo tiver apenas um ouvinte, você poderá adicioná-lo sem especificar um nome, e poderá removê-lo especificando uma cadeia de caracteres vazia para o nome.</span><span class="sxs-lookup"><span data-stu-id="6c28c-146">If your application has only one listener, you can add it without specifying a name, and you can remove it by specifying an empty string for the name.</span></span> <span data-ttu-id="6c28c-147">No entanto, se seu aplicativo tiver mais de um ouvinte, você deverá especificar um nome exclusivo para cada ouvinte de rastreamento, que permite identificar e gerenciar ouvintes de rastreamento individuais na coleção <xref:System.Diagnostics.TraceSource.Listeners%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6c28c-147">However, if your application has more than one listener, you should specify a unique name for each trace listener, which allows you to identify and manage individual trace listeners in the <xref:System.Diagnostics.TraceSource.Listeners%2A?displayProperty=nameWithType> collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6c28c-148">Adicionar mais de um ouvinte de rastreamento do mesmo tipo e com o mesmo nome resulta em apenas um ouvinte de rastreamento desse tipo e nome que estão sendo adicionados à coleção `Listeners`.</span><span class="sxs-lookup"><span data-stu-id="6c28c-148">Adding more than one trace listener of the same type and with the same name results in only one trace listener of that type and name being added to the `Listeners` collection.</span></span> <span data-ttu-id="6c28c-149">No entanto, você pode adicionar programaticamente vários ouvintes idênticos à coleção `Listeners`.</span><span class="sxs-lookup"><span data-stu-id="6c28c-149">However, you can programmatically add multiple identical listeners to the `Listeners` collection.</span></span>  
  
 <span data-ttu-id="6c28c-150">O valor do atributo `initializeData` depende do tipo de ouvinte que você criar.</span><span class="sxs-lookup"><span data-stu-id="6c28c-150">The value for the `initializeData` attribute depends on the type of listener you create.</span></span> <span data-ttu-id="6c28c-151">Nem todos os ouvintes de rastreamento exigem que você especifique `initializeData`.</span><span class="sxs-lookup"><span data-stu-id="6c28c-151">Not all trace listeners require that you specify `initializeData`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6c28c-152">Ao usar o atributo `initializeData`, você pode obter o aviso do compilador "o atributo ' initializeData ' não está declarado".</span><span class="sxs-lookup"><span data-stu-id="6c28c-152">When you use the `initializeData` attribute, you may get the compiler warning "The 'initializeData' attribute is not declared."</span></span> <span data-ttu-id="6c28c-153">Esse aviso ocorre porque as definições de configuração são validadas em relação à classe base abstrata <xref:System.Diagnostics.TraceListener>, que não reconhece o atributo `initializeData`.</span><span class="sxs-lookup"><span data-stu-id="6c28c-153">This warning occurs because the configuration settings are validated against the abstract base class <xref:System.Diagnostics.TraceListener>, which does not recognize the `initializeData` attribute.</span></span> <span data-ttu-id="6c28c-154">Normalmente, você pode ignorar esse aviso para implementações de ouvinte de rastreamento que têm um construtor que usa um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="6c28c-154">Typically, you can ignore this warning for trace listener implementations that have a constructor that takes a parameter.</span></span>  
  
 <span data-ttu-id="6c28c-155">A tabela a seguir mostra os ouvintes de rastreamento que estão incluídos com o .NET Framework e descreve o valor de seus atributos `initializeData`.</span><span class="sxs-lookup"><span data-stu-id="6c28c-155">The following table shows the trace listeners that are included with the .NET Framework and describes the value of their `initializeData` attributes.</span></span>  
  
|<span data-ttu-id="6c28c-156">Classe de ouvinte de rastreamento</span><span class="sxs-lookup"><span data-stu-id="6c28c-156">Trace listener class</span></span>|<span data-ttu-id="6c28c-157">valor do atributo initializeData</span><span class="sxs-lookup"><span data-stu-id="6c28c-157">initializeData attribute value</span></span>|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>|<span data-ttu-id="6c28c-158">O valor `useErrorStream` para o Construtor <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A>.</span><span class="sxs-lookup"><span data-stu-id="6c28c-158">The `useErrorStream` value for the <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> constructor.</span></span>  <span data-ttu-id="6c28c-159">Defina o atributo `initializeData` como "`true`" para gravar rastreamento e depurar saída para o fluxo de erro padrão; Defina-o como "`false`" para gravar no fluxo de saída padrão.</span><span class="sxs-lookup"><span data-stu-id="6c28c-159">Set the `initializeData` attribute to "`true`" to write trace and debug output to the standard error stream; set it to "`false`" to write to the standard output stream.</span></span>|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>|<span data-ttu-id="6c28c-160">O nome do arquivo no qual o <xref:System.Diagnostics.DelimitedListTraceListener> é gravado.</span><span class="sxs-lookup"><span data-stu-id="6c28c-160">The name of the file the <xref:System.Diagnostics.DelimitedListTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|<span data-ttu-id="6c28c-161">O nome da origem de um log de eventos existente.</span><span class="sxs-lookup"><span data-stu-id="6c28c-161">The name of an existing event log source.</span></span>|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|<span data-ttu-id="6c28c-162">O nome do arquivo no qual o <xref:System.Diagnostics.EventSchemaTraceListener> grava.</span><span class="sxs-lookup"><span data-stu-id="6c28c-162">The name of the file that the <xref:System.Diagnostics.EventSchemaTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="6c28c-163">O nome do arquivo no qual o <xref:System.Diagnostics.TextWriterTraceListener> grava.</span><span class="sxs-lookup"><span data-stu-id="6c28c-163">The name of the file that the <xref:System.Diagnostics.TextWriterTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="6c28c-164">O nome do arquivo no qual o <xref:System.Diagnostics.XmlWriterTraceListener> grava.</span><span class="sxs-lookup"><span data-stu-id="6c28c-164">The name of the file that the <xref:System.Diagnostics.XmlWriterTraceListener> writes to.</span></span>|  
  
## <a name="configuration-file"></a><span data-ttu-id="6c28c-165">Arquivo de Configuração</span><span class="sxs-lookup"><span data-stu-id="6c28c-165">Configuration File</span></span>  
 <span data-ttu-id="6c28c-166">Esse elemento pode ser usado no arquivo de configuração da máquina (Machine. config) e no arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6c28c-166">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6c28c-167">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6c28c-167">Example</span></span>  
 <span data-ttu-id="6c28c-168">O exemplo a seguir mostra como usar elementos `<add>` para adicionar os ouvintes `console` e `textListener` à coleção `Listeners` para a fonte de rastreamento `TraceSourceApp`.</span><span class="sxs-lookup"><span data-stu-id="6c28c-168">The following example shows how to use `<add>` elements to add the listeners `console` and `textListener` to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span> <span data-ttu-id="6c28c-169">O ouvinte `textListener` grava a saída de rastreamento no arquivo myListener. log.</span><span class="sxs-lookup"><span data-stu-id="6c28c-169">The `textListener` listener writes trace output to the file myListener.log.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6c28c-170">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6c28c-170">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="6c28c-171">Esquema de configurações de rastreamento e depuração</span><span class="sxs-lookup"><span data-stu-id="6c28c-171">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="6c28c-172">Ouvintes de rastreamento</span><span class="sxs-lookup"><span data-stu-id="6c28c-172">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
