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
ms.openlocfilehash: 0c7665898f8c625c2d07b67ea6c7fe25113fddd8
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699484"
---
# <a name="add-element-for-sharedlisteners"></a><span data-ttu-id="698f3-102">\<add > elemento para \<sharedListeners ></span><span class="sxs-lookup"><span data-stu-id="698f3-102">\<add> Element for \<sharedListeners></span></span>
<span data-ttu-id="698f3-103">Adiciona um ouvinte na coleção `sharedListeners`.</span><span class="sxs-lookup"><span data-stu-id="698f3-103">Adds a listener to the `sharedListeners` collection.</span></span> <span data-ttu-id="698f3-104">`sharedListeners` é uma coleção de ouvintes que qualquer [\<source >](source-element.md) ou [\<trace >](trace-element.md) pode referenciar.</span><span class="sxs-lookup"><span data-stu-id="698f3-104">`sharedListeners` is a collection of listeners that any [\<source>](source-element.md) or [\<trace>](trace-element.md) can reference.</span></span>  <span data-ttu-id="698f3-105">Por padrão, os ouvintes na coleção `sharedListeners` não são colocados em uma coleção `Listeners`.</span><span class="sxs-lookup"><span data-stu-id="698f3-105">By default, listeners in the `sharedListeners` collection are not placed in a `Listeners` collection.</span></span> <span data-ttu-id="698f3-106">Eles devem ser adicionados pelo nome para o [> \<source](source-element.md) ou [\<trace >](trace-element.md).</span><span class="sxs-lookup"><span data-stu-id="698f3-106">They must be added by name to the [\<source>](source-element.md) or [\<trace>](trace-element.md).</span></span> <span data-ttu-id="698f3-107">Não é possível obter os ouvintes na coleção `sharedListeners` no código em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="698f3-107">It is not possible to get the listeners in the `sharedListeners` collection in code at run time.</span></span>  
  
[<span data-ttu-id="698f3-108"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="698f3-108">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="698f3-109">&nbsp; @ no__t-1[ **\<System. Diagnostics >** ](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="698f3-109">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>  
<span data-ttu-id="698f3-110">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<sharedListeners >** ](sharedlisteners-element.md)</span><span class="sxs-lookup"><span data-stu-id="698f3-110">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sharedListeners>**](sharedlisteners-element.md)</span></span>  
<span data-ttu-id="698f3-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Adicionar >**</span><span class="sxs-lookup"><span data-stu-id="698f3-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="698f3-112">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="698f3-112">Syntax</span></span>  
  
```xml  
<add name="name"   
  type="TraceListenerClassName, Version, Culture, PublicKeyToken"  
  initializeData="data"
  traceOutputOptions = "None"
/>  
```
  
## <a name="attributes-and-elements"></a><span data-ttu-id="698f3-113">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="698f3-113">Attributes and Elements</span></span>  
 <span data-ttu-id="698f3-114">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="698f3-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="698f3-115">Atributos</span><span class="sxs-lookup"><span data-stu-id="698f3-115">Attributes</span></span>  
  
|<span data-ttu-id="698f3-116">Atributo</span><span class="sxs-lookup"><span data-stu-id="698f3-116">Attribute</span></span>|<span data-ttu-id="698f3-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="698f3-117">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="698f3-118">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="698f3-118">Required attribute.</span></span><br /><br /> <span data-ttu-id="698f3-119">Especifica o nome do ouvinte que é usado para adicionar o ouvinte compartilhado a uma coleção `Listeners`.</span><span class="sxs-lookup"><span data-stu-id="698f3-119">Specifies the name of the listener that is used to add the shared listener to a `Listeners` collection.</span></span>|  
|`type`|<span data-ttu-id="698f3-120">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="698f3-120">Required attribute.</span></span><br /><br /> <span data-ttu-id="698f3-121">Especifica o tipo do ouvinte.</span><span class="sxs-lookup"><span data-stu-id="698f3-121">Specifies the type of the listener.</span></span> <span data-ttu-id="698f3-122">Você deve usar uma cadeia de caracteres que atenda aos requisitos especificados na [especificação de nomes de tipo totalmente qualificados](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="698f3-122">You must use a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="698f3-123">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="698f3-123">Optional attribute.</span></span><br /><br /> <span data-ttu-id="698f3-124">A cadeia de caracteres passada para o construtor para a classe especificada.</span><span class="sxs-lookup"><span data-stu-id="698f3-124">The string passed to the constructor for the specified class.</span></span>|  
|`traceOutputOptions`|<span data-ttu-id="698f3-125">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="698f3-125">Optional attribute.</span></span><br/><br/><span data-ttu-id="698f3-126">A representação de cadeia de caracteres de um ou mais membros de enumeração <xref:System.Diagnostics.TraceOptions> que indicam os dados a serem gravados na saída do rastreamento.</span><span class="sxs-lookup"><span data-stu-id="698f3-126">The string representation of one or more <xref:System.Diagnostics.TraceOptions> enumeration members that indicates the data to be written to the trace output.</span></span> <span data-ttu-id="698f3-127">Vários itens são separados por vírgulas.</span><span class="sxs-lookup"><span data-stu-id="698f3-127">Multiple items are separated by commas.</span></span> <span data-ttu-id="698f3-128">O valor padrão é "None".</span><span class="sxs-lookup"><span data-stu-id="698f3-128">The default value is "None".</span></span>|

### <a name="child-elements"></a><span data-ttu-id="698f3-129">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="698f3-129">Child Elements</span></span>  
  
|<span data-ttu-id="698f3-130">Elemento</span><span class="sxs-lookup"><span data-stu-id="698f3-130">Element</span></span>|<span data-ttu-id="698f3-131">Descrição</span><span class="sxs-lookup"><span data-stu-id="698f3-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="698f3-132">\<filter></span><span class="sxs-lookup"><span data-stu-id="698f3-132">\<filter></span></span>](filter-element-for-add-for-sharedlisteners.md)|<span data-ttu-id="698f3-133">Adiciona um filtro a um ouvinte na coleção `sharedListeners`.</span><span class="sxs-lookup"><span data-stu-id="698f3-133">Adds a filter to a listener in the `sharedListeners` collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="698f3-134">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="698f3-134">Parent Elements</span></span>  
  
|<span data-ttu-id="698f3-135">Elemento</span><span class="sxs-lookup"><span data-stu-id="698f3-135">Element</span></span>|<span data-ttu-id="698f3-136">Descrição</span><span class="sxs-lookup"><span data-stu-id="698f3-136">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="698f3-137">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="698f3-137">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="698f3-138">Especifica os ouvintes de rastreamento que coletam, armazenam e roteiam mensagens e o nível em que uma opção de rastreamento é definida.</span><span class="sxs-lookup"><span data-stu-id="698f3-138">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sharedListeners`|<span data-ttu-id="698f3-139">Uma coleção de ouvintes que qualquer elemento de origem ou de rastreamento pode referenciar.</span><span class="sxs-lookup"><span data-stu-id="698f3-139">A collection of listeners that any source or trace element can reference.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="698f3-140">Comentários</span><span class="sxs-lookup"><span data-stu-id="698f3-140">Remarks</span></span>  
 <span data-ttu-id="698f3-141">As classes de ouvinte fornecidas com o .NET Framework derivam da classe <xref:System.Diagnostics.TraceListener>.</span><span class="sxs-lookup"><span data-stu-id="698f3-141">The listener classes shipped with the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span> <span data-ttu-id="698f3-142">O valor do atributo `name` é usado para adicionar o ouvinte compartilhado a uma coleção de `Listeners` para um rastreamento ou uma origem de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="698f3-142">The value for the `name` attribute is used to add the shared listener to a `Listeners` collection for either a trace or a trace source.</span></span> <span data-ttu-id="698f3-143">O valor do atributo `initializeData` depende do tipo de ouvinte que você criar.</span><span class="sxs-lookup"><span data-stu-id="698f3-143">The value for the `initializeData` attribute depends on the type of listener you create.</span></span> <span data-ttu-id="698f3-144">Nem todos os ouvintes de rastreamento exigem que você especifique `initializeData`.</span><span class="sxs-lookup"><span data-stu-id="698f3-144">Not all trace listeners require that you specify `initializeData`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="698f3-145">Ao usar o atributo `initializeData`, você pode obter o aviso do compilador "o atributo ' initializeData ' não está declarado".</span><span class="sxs-lookup"><span data-stu-id="698f3-145">When you use the `initializeData` attribute, you may get the compiler warning "The 'initializeData' attribute is not declared."</span></span> <span data-ttu-id="698f3-146">Esse aviso ocorre porque as definições de configuração são validadas em relação à classe base abstrata <xref:System.Diagnostics.TraceListener>, que não reconhece o atributo `initializeData`.</span><span class="sxs-lookup"><span data-stu-id="698f3-146">This warning occurs because the configuration settings are validated against the abstract base class <xref:System.Diagnostics.TraceListener>, which does not recognize the `initializeData` attribute.</span></span> <span data-ttu-id="698f3-147">Normalmente, você pode ignorar esse aviso para implementações de ouvinte de rastreamento que têm um construtor que usa um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="698f3-147">Typically, you can ignore this warning for trace listener implementations that have a constructor that takes a parameter.</span></span>  
  
 <span data-ttu-id="698f3-148">A tabela a seguir mostra os ouvintes de rastreamento que estão incluídos com o .NET Framework e descreve o valor de seus atributos `initializeData`.</span><span class="sxs-lookup"><span data-stu-id="698f3-148">The following table shows the trace listeners that are included with the .NET Framework and describes the value of their `initializeData` attributes.</span></span>  
  
|<span data-ttu-id="698f3-149">Classe de ouvinte de rastreamento</span><span class="sxs-lookup"><span data-stu-id="698f3-149">Trace listener class</span></span>|<span data-ttu-id="698f3-150">valor do atributo initializeData</span><span class="sxs-lookup"><span data-stu-id="698f3-150">initializeData attribute value</span></span>|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener>|<span data-ttu-id="698f3-151">O valor `useErrorStream` para o Construtor <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A>.</span><span class="sxs-lookup"><span data-stu-id="698f3-151">The `useErrorStream` value for the <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> constructor.</span></span>  <span data-ttu-id="698f3-152">Defina o atributo `initializeData` como "`true`" para gravar rastreamento e depurar saída para o fluxo de erro padrão; Defina-o como "`false`" para gravar no fluxo de saída padrão.</span><span class="sxs-lookup"><span data-stu-id="698f3-152">Set the `initializeData` attribute to "`true`" to write trace and debug output to the standard error stream; set it to "`false`" to write to the standard output stream.</span></span>|  
|<xref:System.Diagnostics.DelimitedListTraceListener>|<span data-ttu-id="698f3-153">O nome do arquivo no qual o <xref:System.Diagnostics.DelimitedListTraceListener> é gravado.</span><span class="sxs-lookup"><span data-stu-id="698f3-153">The name of the file the <xref:System.Diagnostics.DelimitedListTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|<span data-ttu-id="698f3-154">O nome da origem de um log de eventos existente.</span><span class="sxs-lookup"><span data-stu-id="698f3-154">The name of an existing event log source.</span></span>|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|<span data-ttu-id="698f3-155">O nome do arquivo no qual o <xref:System.Diagnostics.EventSchemaTraceListener> grava.</span><span class="sxs-lookup"><span data-stu-id="698f3-155">The name of the file that the <xref:System.Diagnostics.EventSchemaTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="698f3-156">O nome do arquivo no qual o <xref:System.Diagnostics.TextWriterTraceListener> grava.</span><span class="sxs-lookup"><span data-stu-id="698f3-156">The name of the file that the <xref:System.Diagnostics.TextWriterTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.XmlWriterTraceListener>|<span data-ttu-id="698f3-157">O nome do arquivo no qual o <xref:System.Diagnostics.XmlWriterTraceListener> grava.</span><span class="sxs-lookup"><span data-stu-id="698f3-157">The name of the file that the <xref:System.Diagnostics.XmlWriterTraceListener> writes to.</span></span>|  
  
## <a name="configuration-file"></a><span data-ttu-id="698f3-158">Arquivo de Configuração</span><span class="sxs-lookup"><span data-stu-id="698f3-158">Configuration File</span></span>  
 <span data-ttu-id="698f3-159">Esse elemento pode ser usado no arquivo de configuração da máquina (Machine. config) e no arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="698f3-159">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="698f3-160">Exemplo</span><span class="sxs-lookup"><span data-stu-id="698f3-160">Example</span></span>  
 <span data-ttu-id="698f3-161">O exemplo a seguir mostra como usar elementos `<add>` para adicionar o <xref:System.Diagnostics.TextWriterTraceListener> @ no__t-2 à coleção `sharedListeners`.</span><span class="sxs-lookup"><span data-stu-id="698f3-161">The following example shows how to use `<add>` elements to add the <xref:System.Diagnostics.TextWriterTraceListener>`textListener` to the `sharedListeners` collection.</span></span>   <span data-ttu-id="698f3-162">`textListener` é adicionado pelo nome à coleção de `Listeners` para a fonte de rastreamento `TraceSourceApp`.</span><span class="sxs-lookup"><span data-stu-id="698f3-162">`textListener` is added by name to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span> <span data-ttu-id="698f3-163">O ouvinte `textListener` grava a saída de rastreamento no arquivo myListener. log.</span><span class="sxs-lookup"><span data-stu-id="698f3-163">The `textListener` listener writes trace output to the file myListener.log.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="698f3-164">Consulte também</span><span class="sxs-lookup"><span data-stu-id="698f3-164">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="698f3-165">Esquema de configurações de rastreamento e depuração</span><span class="sxs-lookup"><span data-stu-id="698f3-165">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="698f3-166">Ouvintes de rastreamento</span><span class="sxs-lookup"><span data-stu-id="698f3-166">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
