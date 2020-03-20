---
title: <add>Elemento <listeners> para para<source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/add
helpviewer_keywords:
- initializeData attribute
- add element for <listeners> for <source>
- <add> element for <listeners> for <source>
ms.assetid: 4ce36ac1-81ef-48e8-b8b2-b5a5b0e2adcb
ms.openlocfilehash: 883eef32172c5a7f900197995b4c57c3d5a84e19
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153679"
---
# <a name="add-element-for-listeners-for-source"></a><span data-ttu-id="831bb-102">\<adicionar> \<Element para \<ouvintes> para> de origem</span><span class="sxs-lookup"><span data-stu-id="831bb-102">\<add> Element for \<listeners> for \<source></span></span>
<span data-ttu-id="831bb-103">Adiciona um ouvinte na coleção `Listeners` de uma origem de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="831bb-103">Adds a listener to the `Listeners` collection for a trace source.</span></span>  

<span data-ttu-id="831bb-104">[**\<>de configuração**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="831bb-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="831bb-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="831bb-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>\
<span data-ttu-id="831bb-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<fontes>**](sources-element.md)</span><span class="sxs-lookup"><span data-stu-id="831bb-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)</span></span>\
<span data-ttu-id="831bb-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>fonte**](source-element.md)</span><span class="sxs-lookup"><span data-stu-id="831bb-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<source>**](source-element.md)</span></span>\
<span data-ttu-id="831bb-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<ouvintes>**](listeners-element-for-source.md)</span><span class="sxs-lookup"><span data-stu-id="831bb-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-source.md)</span></span>\
<span data-ttu-id="831bb-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<adicionar>**</span><span class="sxs-lookup"><span data-stu-id="831bb-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>

## <a name="syntax"></a><span data-ttu-id="831bb-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="831bb-110">Syntax</span></span>  
  
```xml  
<add name="name"
  type="TraceListenerClassName, Version, Culture, PublicKeyToken"  
  initializeData="data"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="831bb-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="831bb-111">Attributes and Elements</span></span>  
 <span data-ttu-id="831bb-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="831bb-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="831bb-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="831bb-113">Attributes</span></span>  
  
|<span data-ttu-id="831bb-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="831bb-114">Attribute</span></span>|<span data-ttu-id="831bb-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="831bb-115">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="831bb-116">Atributo necessário, a menos que você `sharedListeners` esteja fazendo referência a um ouvinte na coleção, nesse caso você só precisa se referir a ele pelo nome (veja o [Exemplo](#example)).</span><span class="sxs-lookup"><span data-stu-id="831bb-116">Required attribute, unless you're referencing a listener in the `sharedListeners` collection, in which case you only need to refer to it by name (see the [Example](#example)).</span></span><br /><br /> <span data-ttu-id="831bb-117">Especifica o tipo do ouvinte.</span><span class="sxs-lookup"><span data-stu-id="831bb-117">Specifies the type of the listener.</span></span> <span data-ttu-id="831bb-118">Você deve usar uma string que atenda aos requisitos especificados na [Especificação de nomes de tipo totalmente qualificados](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="831bb-118">You must use a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="831bb-119">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="831bb-119">Optional attribute.</span></span><br /><br /> <span data-ttu-id="831bb-120">A seqüência passou para o construtor para a classe especificada.</span><span class="sxs-lookup"><span data-stu-id="831bb-120">The string passed to the constructor for the specified class.</span></span> <span data-ttu-id="831bb-121">A <xref:System.Configuration.ConfigurationException> é jogado se a classe não tem um construtor que leva uma corda.</span><span class="sxs-lookup"><span data-stu-id="831bb-121">A <xref:System.Configuration.ConfigurationException> is thrown if the class does not have a constructor that takes a string.</span></span>|  
|`name`|<span data-ttu-id="831bb-122">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="831bb-122">Optional attribute.</span></span><br /><br /> <span data-ttu-id="831bb-123">Especifica o nome do ouvinte.</span><span class="sxs-lookup"><span data-stu-id="831bb-123">Specifies the name of the listener.</span></span>|  
|`traceOutputOptions`|<span data-ttu-id="831bb-124">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="831bb-124">Optional attribute.</span></span><br /><br /> <span data-ttu-id="831bb-125">Especifica o <xref:System.Diagnostics.TraceListener.TraceOutputOptions%2A> valor da propriedade para o ouvinte de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="831bb-125">Specifies the <xref:System.Diagnostics.TraceListener.TraceOutputOptions%2A> property value for the trace listener.</span></span>|  
|<span data-ttu-id="831bb-126">[atributos personalizados]</span><span class="sxs-lookup"><span data-stu-id="831bb-126">[custom attributes]</span></span>|<span data-ttu-id="831bb-127">Atributos opcionais.</span><span class="sxs-lookup"><span data-stu-id="831bb-127">Optional attributes.</span></span><br /><br /> <span data-ttu-id="831bb-128">Especifica o valor para atributos específicos <xref:System.Diagnostics.TraceListener.GetSupportedAttributes%2A> do ouvinte identificados pelo método para esse ouvinte.</span><span class="sxs-lookup"><span data-stu-id="831bb-128">Specifies the value for listener-specific attributes identified by the <xref:System.Diagnostics.TraceListener.GetSupportedAttributes%2A> method for that listener.</span></span> <span data-ttu-id="831bb-129"><xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A>é um exemplo de um <xref:System.Diagnostics.DelimitedListTraceListener> atributo extra único para a classe.</span><span class="sxs-lookup"><span data-stu-id="831bb-129"><xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A> is an example of an extra attribute unique to the <xref:System.Diagnostics.DelimitedListTraceListener> class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="831bb-130">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="831bb-130">Child Elements</span></span>  
  
|<span data-ttu-id="831bb-131">Elemento</span><span class="sxs-lookup"><span data-stu-id="831bb-131">Element</span></span>|<span data-ttu-id="831bb-132">Descrição</span><span class="sxs-lookup"><span data-stu-id="831bb-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="831bb-133">\<>de filtro</span><span class="sxs-lookup"><span data-stu-id="831bb-133">\<filter></span></span>](filter-element-for-add-for-listeners-for-source.md)|<span data-ttu-id="831bb-134">Adiciona um filtro a um ouvinte na coleção `Listeners` de uma origem de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="831bb-134">Adds a filter to a listener in the `Listeners` collection for a trace source.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="831bb-135">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="831bb-135">Parent Elements</span></span>  
  
|<span data-ttu-id="831bb-136">Elemento</span><span class="sxs-lookup"><span data-stu-id="831bb-136">Element</span></span>|<span data-ttu-id="831bb-137">Descrição</span><span class="sxs-lookup"><span data-stu-id="831bb-137">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="831bb-138">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="831bb-138">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="831bb-139">Especifica os ouvintes de rastreamento que coletam, armazenam e roteiam mensagens e o nível em que uma opção de rastreamento é definida.</span><span class="sxs-lookup"><span data-stu-id="831bb-139">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="831bb-140">Contém as origens de rastreamento que iniciam as mensagens de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="831bb-140">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="831bb-141">Especifica uma origem de rastreamento que inicia as mensagens de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="831bb-141">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="831bb-142">Especifica os ouvintes que coletam, armazenam e encaminham mensagens.</span><span class="sxs-lookup"><span data-stu-id="831bb-142">Specifies listeners that collect, store, and route messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="831bb-143">Comentários</span><span class="sxs-lookup"><span data-stu-id="831bb-143">Remarks</span></span>  
 <span data-ttu-id="831bb-144">As classes de ouvinte enviadas com o <xref:System.Diagnostics.TraceListener> Quadro .NET derivam da classe.</span><span class="sxs-lookup"><span data-stu-id="831bb-144">The listener classes shipped with the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span>  
  
 <span data-ttu-id="831bb-145">Se você não `name` especificar o atributo <xref:System.Diagnostics.TraceListener.Name%2A> do ouvinte de rastreamento, a propriedade do ouvinte de rastreamento será padrão para uma seqüência de string vazia ("").</span><span class="sxs-lookup"><span data-stu-id="831bb-145">If you do not specify the `name` attribute of the trace listener, the <xref:System.Diagnostics.TraceListener.Name%2A> property of the trace listener defaults to an empty string ("").</span></span> <span data-ttu-id="831bb-146">Se o aplicativo tiver apenas um ouvinte, você pode adicioná-lo sem especificar um nome e removê-lo especificando uma seqüência de string vazia para o nome.</span><span class="sxs-lookup"><span data-stu-id="831bb-146">If your application has only one listener, you can add it without specifying a name, and you can remove it by specifying an empty string for the name.</span></span> <span data-ttu-id="831bb-147">No entanto, se o seu aplicativo tiver mais de um ouvinte, você deve especificar um nome <xref:System.Diagnostics.TraceSource.Listeners%2A?displayProperty=nameWithType> único para cada ouvinte de rastreamento, o que permite identificar e gerenciar ouvintes de rastreamento individuais na coleção.</span><span class="sxs-lookup"><span data-stu-id="831bb-147">However, if your application has more than one listener, you should specify a unique name for each trace listener, which allows you to identify and manage individual trace listeners in the <xref:System.Diagnostics.TraceSource.Listeners%2A?displayProperty=nameWithType> collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="831bb-148">Adicionar mais de um ouvinte de rastreamento do mesmo tipo e com o mesmo nome resulta `Listeners` em apenas um ouvinte de rastreamento desse tipo e nome sendo adicionado à coleção.</span><span class="sxs-lookup"><span data-stu-id="831bb-148">Adding more than one trace listener of the same type and with the same name results in only one trace listener of that type and name being added to the `Listeners` collection.</span></span> <span data-ttu-id="831bb-149">No entanto, você pode adicionar programáticamente vários ouvintes idênticos à `Listeners` coleção.</span><span class="sxs-lookup"><span data-stu-id="831bb-149">However, you can programmatically add multiple identical listeners to the `Listeners` collection.</span></span>  
  
 <span data-ttu-id="831bb-150">O valor `initializeData` para o atributo depende do tipo de ouvinte que você cria.</span><span class="sxs-lookup"><span data-stu-id="831bb-150">The value for the `initializeData` attribute depends on the type of listener you create.</span></span> <span data-ttu-id="831bb-151">Nem todos os ouvintes `initializeData`de rastreamento exigem que você especifique .</span><span class="sxs-lookup"><span data-stu-id="831bb-151">Not all trace listeners require that you specify `initializeData`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="831bb-152">Quando você `initializeData` usa o atributo, você pode obter o aviso do compilador "O atributo 'initializeData' não é declarado."</span><span class="sxs-lookup"><span data-stu-id="831bb-152">When you use the `initializeData` attribute, you may get the compiler warning "The 'initializeData' attribute is not declared."</span></span> <span data-ttu-id="831bb-153">Esse aviso ocorre porque as configurações são <xref:System.Diagnostics.TraceListener>validadas em `initializeData` relação à classe base abstrata, que não reconhece o atributo.</span><span class="sxs-lookup"><span data-stu-id="831bb-153">This warning occurs because the configuration settings are validated against the abstract base class <xref:System.Diagnostics.TraceListener>, which does not recognize the `initializeData` attribute.</span></span> <span data-ttu-id="831bb-154">Normalmente, você pode ignorar este aviso para implementações de ouvintes de rastreamento que tenham um construtor que leva um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="831bb-154">Typically, you can ignore this warning for trace listener implementations that have a constructor that takes a parameter.</span></span>  
  
 <span data-ttu-id="831bb-155">A tabela a seguir mostra os ouvintes de rastreamento que estão `initializeData` incluídos no Quadro .NET e descreve o valor de seus atributos.</span><span class="sxs-lookup"><span data-stu-id="831bb-155">The following table shows the trace listeners that are included with the .NET Framework and describes the value of their `initializeData` attributes.</span></span>  
  
|<span data-ttu-id="831bb-156">Classe de ouvinte de rastreamento</span><span class="sxs-lookup"><span data-stu-id="831bb-156">Trace listener class</span></span>|<span data-ttu-id="831bb-157">inicializarvalor do atributoData</span><span class="sxs-lookup"><span data-stu-id="831bb-157">initializeData attribute value</span></span>|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>|<span data-ttu-id="831bb-158">O `useErrorStream` valor <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> para o construtor.</span><span class="sxs-lookup"><span data-stu-id="831bb-158">The `useErrorStream` value for the <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> constructor.</span></span>  <span data-ttu-id="831bb-159">Defina `initializeData` o`true`atributo como " " para gravar a saída de rastreamento e depuração para o fluxo de erro padrão; configurá-lo`false`para " " para escrever para o fluxo de saída padrão.</span><span class="sxs-lookup"><span data-stu-id="831bb-159">Set the `initializeData` attribute to "`true`" to write trace and debug output to the standard error stream; set it to "`false`" to write to the standard output stream.</span></span>|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>|<span data-ttu-id="831bb-160">O nome do arquivo no qual o <xref:System.Diagnostics.DelimitedListTraceListener> é gravado.</span><span class="sxs-lookup"><span data-stu-id="831bb-160">The name of the file the <xref:System.Diagnostics.DelimitedListTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|<span data-ttu-id="831bb-161">O nome da origem de um log de eventos existente.</span><span class="sxs-lookup"><span data-stu-id="831bb-161">The name of an existing event log source.</span></span>|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|<span data-ttu-id="831bb-162">O nome do arquivo <xref:System.Diagnostics.EventSchemaTraceListener> para o que ele escreve.</span><span class="sxs-lookup"><span data-stu-id="831bb-162">The name of the file that the <xref:System.Diagnostics.EventSchemaTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="831bb-163">O nome do arquivo <xref:System.Diagnostics.TextWriterTraceListener> para o que ele escreve.</span><span class="sxs-lookup"><span data-stu-id="831bb-163">The name of the file that the <xref:System.Diagnostics.TextWriterTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="831bb-164">O nome do arquivo <xref:System.Diagnostics.XmlWriterTraceListener> para o que ele escreve.</span><span class="sxs-lookup"><span data-stu-id="831bb-164">The name of the file that the <xref:System.Diagnostics.XmlWriterTraceListener> writes to.</span></span>|  
  
## <a name="configuration-file"></a><span data-ttu-id="831bb-165">Arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="831bb-165">Configuration File</span></span>  
 <span data-ttu-id="831bb-166">Esse elemento pode ser usado no arquivo de configuração da máquina (Machine.config) e no arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="831bb-166">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="831bb-167">Exemplo</span><span class="sxs-lookup"><span data-stu-id="831bb-167">Example</span></span>  
 <span data-ttu-id="831bb-168">O exemplo a seguir `<add>` mostra como `console` usar `textListener` elementos para adicionar os ouvintes e à `Listeners` coleção para a fonte `TraceSourceApp`de rastreamento .</span><span class="sxs-lookup"><span data-stu-id="831bb-168">The following example shows how to use `<add>` elements to add the listeners `console` and `textListener` to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span> <span data-ttu-id="831bb-169">O `textListener` ouvinte grava a saída de rastreamento para o arquivo myListener.log.</span><span class="sxs-lookup"><span data-stu-id="831bb-169">The `textListener` listener writes trace output to the file myListener.log.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="831bb-170">Confira também</span><span class="sxs-lookup"><span data-stu-id="831bb-170">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="831bb-171">Esquema de configurações de rastreamento e depuração</span><span class="sxs-lookup"><span data-stu-id="831bb-171">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="831bb-172">Ouvintes de rastreamento</span><span class="sxs-lookup"><span data-stu-id="831bb-172">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
