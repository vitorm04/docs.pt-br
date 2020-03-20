---
title: Elemento <add> para <sharedListeners>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sharedListeners/add
helpviewer_keywords:
- initializeData attribute
- <add> element for <sharedListeners>
- add element for <sharedListeners>
ms.assetid: 1595e1bc-2492-421f-8384-7f382eb8eb57
ms.openlocfilehash: 5588892ec75a791eda1eb043936c0af95e79354e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153601"
---
# <a name="add-element-for-sharedlisteners"></a><span data-ttu-id="9c896-102">\<adicionar> \<Elemento para> de ouvintes compartilhados</span><span class="sxs-lookup"><span data-stu-id="9c896-102">\<add> Element for \<sharedListeners></span></span>
<span data-ttu-id="9c896-103">Adiciona um ouvinte na coleção `sharedListeners`.</span><span class="sxs-lookup"><span data-stu-id="9c896-103">Adds a listener to the `sharedListeners` collection.</span></span> <span data-ttu-id="9c896-104">`sharedListeners`é uma coleção de [ \<](source-element.md) ouvintes que qualquer fonte>ou [ \<traçar>](trace-element.md) pode referenciar.</span><span class="sxs-lookup"><span data-stu-id="9c896-104">`sharedListeners` is a collection of listeners that any [\<source>](source-element.md) or [\<trace>](trace-element.md) can reference.</span></span>  <span data-ttu-id="9c896-105">Por padrão, os `sharedListeners` ouvintes da `Listeners` coleção não são colocados em uma coleção.</span><span class="sxs-lookup"><span data-stu-id="9c896-105">By default, listeners in the `sharedListeners` collection are not placed in a `Listeners` collection.</span></span> <span data-ttu-id="9c896-106">Eles devem ser adicionados [ \<](source-element.md) pelo nome à fonte>ou [ \<traçar>](trace-element.md).</span><span class="sxs-lookup"><span data-stu-id="9c896-106">They must be added by name to the [\<source>](source-element.md) or [\<trace>](trace-element.md).</span></span> <span data-ttu-id="9c896-107">Não é possível obter os `sharedListeners` ouvintes da coleção em código em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="9c896-107">It is not possible to get the listeners in the `sharedListeners` collection in code at run time.</span></span>  

<span data-ttu-id="9c896-108">[**\<>de configuração**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="9c896-108">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="9c896-109">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="9c896-109">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>\
<span data-ttu-id="9c896-110">&nbsp;&nbsp;&nbsp;&nbsp;[**\<>de ouvintes compartilhados**](sharedlisteners-element.md)</span><span class="sxs-lookup"><span data-stu-id="9c896-110">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sharedListeners>**](sharedlisteners-element.md)</span></span>\
<span data-ttu-id="9c896-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<adicionar>**</span><span class="sxs-lookup"><span data-stu-id="9c896-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>

## <a name="syntax"></a><span data-ttu-id="9c896-112">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9c896-112">Syntax</span></span>  
  
```xml  
<add name="name"
  type="TraceListenerClassName, Version, Culture, PublicKeyToken"  
  initializeData="data"
  traceOutputOptions = "None"
/>  
```
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9c896-113">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="9c896-113">Attributes and Elements</span></span>  
 <span data-ttu-id="9c896-114">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="9c896-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9c896-115">Atributos</span><span class="sxs-lookup"><span data-stu-id="9c896-115">Attributes</span></span>  
  
|<span data-ttu-id="9c896-116">Atributo</span><span class="sxs-lookup"><span data-stu-id="9c896-116">Attribute</span></span>|<span data-ttu-id="9c896-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="9c896-117">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="9c896-118">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="9c896-118">Required attribute.</span></span><br /><br /> <span data-ttu-id="9c896-119">Especifica o nome do ouvinte que é usado para adicionar `Listeners` o ouvinte compartilhado a uma coleção.</span><span class="sxs-lookup"><span data-stu-id="9c896-119">Specifies the name of the listener that is used to add the shared listener to a `Listeners` collection.</span></span>|  
|`type`|<span data-ttu-id="9c896-120">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="9c896-120">Required attribute.</span></span><br /><br /> <span data-ttu-id="9c896-121">Especifica o tipo do ouvinte.</span><span class="sxs-lookup"><span data-stu-id="9c896-121">Specifies the type of the listener.</span></span> <span data-ttu-id="9c896-122">Você deve usar uma string que atenda aos requisitos especificados na [Especificação de nomes de tipo totalmente qualificados](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="9c896-122">You must use a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="9c896-123">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="9c896-123">Optional attribute.</span></span><br /><br /> <span data-ttu-id="9c896-124">A seqüência passou para o construtor para a classe especificada.</span><span class="sxs-lookup"><span data-stu-id="9c896-124">The string passed to the constructor for the specified class.</span></span>|  
|`traceOutputOptions`|<span data-ttu-id="9c896-125">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="9c896-125">Optional attribute.</span></span><br/><br/><span data-ttu-id="9c896-126">A representação de <xref:System.Diagnostics.TraceOptions> seqüência de um ou mais membros de enumeração que indica os dados a serem gravados na saída de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="9c896-126">The string representation of one or more <xref:System.Diagnostics.TraceOptions> enumeration members that indicates the data to be written to the trace output.</span></span> <span data-ttu-id="9c896-127">Vários itens são separados por commas.</span><span class="sxs-lookup"><span data-stu-id="9c896-127">Multiple items are separated by commas.</span></span> <span data-ttu-id="9c896-128">O valor padrão é "Nenhum".</span><span class="sxs-lookup"><span data-stu-id="9c896-128">The default value is "None".</span></span>|

### <a name="child-elements"></a><span data-ttu-id="9c896-129">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="9c896-129">Child Elements</span></span>  
  
|<span data-ttu-id="9c896-130">Elemento</span><span class="sxs-lookup"><span data-stu-id="9c896-130">Element</span></span>|<span data-ttu-id="9c896-131">Descrição</span><span class="sxs-lookup"><span data-stu-id="9c896-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9c896-132">\<>de filtro</span><span class="sxs-lookup"><span data-stu-id="9c896-132">\<filter></span></span>](filter-element-for-add-for-sharedlisteners.md)|<span data-ttu-id="9c896-133">Adiciona um filtro a um ouvinte na coleção `sharedListeners`.</span><span class="sxs-lookup"><span data-stu-id="9c896-133">Adds a filter to a listener in the `sharedListeners` collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9c896-134">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="9c896-134">Parent Elements</span></span>  
  
|<span data-ttu-id="9c896-135">Elemento</span><span class="sxs-lookup"><span data-stu-id="9c896-135">Element</span></span>|<span data-ttu-id="9c896-136">Descrição</span><span class="sxs-lookup"><span data-stu-id="9c896-136">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="9c896-137">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9c896-137">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="9c896-138">Especifica os ouvintes de rastreamento que coletam, armazenam e roteiam mensagens e o nível em que uma opção de rastreamento é definida.</span><span class="sxs-lookup"><span data-stu-id="9c896-138">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sharedListeners`|<span data-ttu-id="9c896-139">Uma coleção de ouvintes que qualquer fonte ou elemento de rastreamento pode referenciar.</span><span class="sxs-lookup"><span data-stu-id="9c896-139">A collection of listeners that any source or trace element can reference.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9c896-140">Comentários</span><span class="sxs-lookup"><span data-stu-id="9c896-140">Remarks</span></span>  
 <span data-ttu-id="9c896-141">As classes de ouvinte enviadas com o <xref:System.Diagnostics.TraceListener> Quadro .NET derivam da classe.</span><span class="sxs-lookup"><span data-stu-id="9c896-141">The listener classes shipped with the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span> <span data-ttu-id="9c896-142">O valor `name` para o atributo é usado para `Listeners` adicionar o ouvinte compartilhado a uma coleção para um traço ou uma fonte de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="9c896-142">The value for the `name` attribute is used to add the shared listener to a `Listeners` collection for either a trace or a trace source.</span></span> <span data-ttu-id="9c896-143">O valor `initializeData` para o atributo depende do tipo de ouvinte que você cria.</span><span class="sxs-lookup"><span data-stu-id="9c896-143">The value for the `initializeData` attribute depends on the type of listener you create.</span></span> <span data-ttu-id="9c896-144">Nem todos os ouvintes `initializeData`de rastreamento exigem que você especifique .</span><span class="sxs-lookup"><span data-stu-id="9c896-144">Not all trace listeners require that you specify `initializeData`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9c896-145">Quando você `initializeData` usa o atributo, você pode obter o aviso do compilador "O atributo 'initializeData' não é declarado."</span><span class="sxs-lookup"><span data-stu-id="9c896-145">When you use the `initializeData` attribute, you may get the compiler warning "The 'initializeData' attribute is not declared."</span></span> <span data-ttu-id="9c896-146">Esse aviso ocorre porque as configurações são <xref:System.Diagnostics.TraceListener>validadas em `initializeData` relação à classe base abstrata, que não reconhece o atributo.</span><span class="sxs-lookup"><span data-stu-id="9c896-146">This warning occurs because the configuration settings are validated against the abstract base class <xref:System.Diagnostics.TraceListener>, which does not recognize the `initializeData` attribute.</span></span> <span data-ttu-id="9c896-147">Normalmente, você pode ignorar este aviso para implementações de ouvintes de rastreamento que tenham um construtor que leva um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="9c896-147">Typically, you can ignore this warning for trace listener implementations that have a constructor that takes a parameter.</span></span>  
  
 <span data-ttu-id="9c896-148">A tabela a seguir mostra os ouvintes de rastreamento que estão `initializeData` incluídos no Quadro .NET e descreve o valor de seus atributos.</span><span class="sxs-lookup"><span data-stu-id="9c896-148">The following table shows the trace listeners that are included with the .NET Framework and describes the value of their `initializeData` attributes.</span></span>  
  
|<span data-ttu-id="9c896-149">Classe de ouvinte de rastreamento</span><span class="sxs-lookup"><span data-stu-id="9c896-149">Trace listener class</span></span>|<span data-ttu-id="9c896-150">inicializarvalor do atributoData</span><span class="sxs-lookup"><span data-stu-id="9c896-150">initializeData attribute value</span></span>|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener>|<span data-ttu-id="9c896-151">O `useErrorStream` valor <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> para o construtor.</span><span class="sxs-lookup"><span data-stu-id="9c896-151">The `useErrorStream` value for the <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> constructor.</span></span>  <span data-ttu-id="9c896-152">Defina `initializeData` o`true`atributo como " " para gravar a saída de rastreamento e depuração para o fluxo de erro padrão; configurá-lo`false`para " " para escrever para o fluxo de saída padrão.</span><span class="sxs-lookup"><span data-stu-id="9c896-152">Set the `initializeData` attribute to "`true`" to write trace and debug output to the standard error stream; set it to "`false`" to write to the standard output stream.</span></span>|  
|<xref:System.Diagnostics.DelimitedListTraceListener>|<span data-ttu-id="9c896-153">O nome do arquivo no qual o <xref:System.Diagnostics.DelimitedListTraceListener> é gravado.</span><span class="sxs-lookup"><span data-stu-id="9c896-153">The name of the file the <xref:System.Diagnostics.DelimitedListTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|<span data-ttu-id="9c896-154">O nome da origem de um log de eventos existente.</span><span class="sxs-lookup"><span data-stu-id="9c896-154">The name of an existing event log source.</span></span>|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|<span data-ttu-id="9c896-155">O nome do arquivo <xref:System.Diagnostics.EventSchemaTraceListener> para o que ele escreve.</span><span class="sxs-lookup"><span data-stu-id="9c896-155">The name of the file that the <xref:System.Diagnostics.EventSchemaTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="9c896-156">O nome do arquivo <xref:System.Diagnostics.TextWriterTraceListener> para o que ele escreve.</span><span class="sxs-lookup"><span data-stu-id="9c896-156">The name of the file that the <xref:System.Diagnostics.TextWriterTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.XmlWriterTraceListener>|<span data-ttu-id="9c896-157">O nome do arquivo <xref:System.Diagnostics.XmlWriterTraceListener> para o que ele escreve.</span><span class="sxs-lookup"><span data-stu-id="9c896-157">The name of the file that the <xref:System.Diagnostics.XmlWriterTraceListener> writes to.</span></span>|  
  
## <a name="configuration-file"></a><span data-ttu-id="9c896-158">Arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="9c896-158">Configuration File</span></span>  
 <span data-ttu-id="9c896-159">Esse elemento pode ser usado no arquivo de configuração da máquina (Machine.config) e no arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9c896-159">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9c896-160">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9c896-160">Example</span></span>  
 <span data-ttu-id="9c896-161">O exemplo a seguir `<add>` mostra como <xref:System.Diagnostics.TextWriterTraceListener> `textListener` usar `sharedListeners` elementos para adicionar à coleção.</span><span class="sxs-lookup"><span data-stu-id="9c896-161">The following example shows how to use `<add>` elements to add the <xref:System.Diagnostics.TextWriterTraceListener>`textListener` to the `sharedListeners` collection.</span></span>   <span data-ttu-id="9c896-162">`textListener`é adicionado por `Listeners` nome à coleção `TraceSourceApp`para a fonte de rastreamento .</span><span class="sxs-lookup"><span data-stu-id="9c896-162">`textListener` is added by name to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span> <span data-ttu-id="9c896-163">O `textListener` ouvinte grava a saída de rastreamento para o arquivo myListener.log.</span><span class="sxs-lookup"><span data-stu-id="9c896-163">The `textListener` listener writes trace output to the file myListener.log.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9c896-164">Confira também</span><span class="sxs-lookup"><span data-stu-id="9c896-164">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="9c896-165">Esquema de configurações de rastreamento e depuração</span><span class="sxs-lookup"><span data-stu-id="9c896-165">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="9c896-166">Ouvintes de rastreamento</span><span class="sxs-lookup"><span data-stu-id="9c896-166">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
