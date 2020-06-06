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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153601"
---
# <a name="add-element-for-sharedlisteners"></a><span data-ttu-id="6cfdb-102">Elemento \<add> para \<sharedListeners></span><span class="sxs-lookup"><span data-stu-id="6cfdb-102">\<add> Element for \<sharedListeners></span></span>
<span data-ttu-id="6cfdb-103">Adiciona um ouvinte na coleção `sharedListeners`.</span><span class="sxs-lookup"><span data-stu-id="6cfdb-103">Adds a listener to the `sharedListeners` collection.</span></span> <span data-ttu-id="6cfdb-104">`sharedListeners`é uma coleção de ouvintes que qualquer [\<source>](source-element.md) ou [\<trace>](trace-element.md) pode referenciar.</span><span class="sxs-lookup"><span data-stu-id="6cfdb-104">`sharedListeners` is a collection of listeners that any [\<source>](source-element.md) or [\<trace>](trace-element.md) can reference.</span></span>  <span data-ttu-id="6cfdb-105">Por padrão, os ouvintes na `sharedListeners` coleção não são colocados em uma `Listeners` coleção.</span><span class="sxs-lookup"><span data-stu-id="6cfdb-105">By default, listeners in the `sharedListeners` collection are not placed in a `Listeners` collection.</span></span> <span data-ttu-id="6cfdb-106">Eles devem ser adicionados pelo nome ao [\<source>](source-element.md) ou ao [\<trace>](trace-element.md) .</span><span class="sxs-lookup"><span data-stu-id="6cfdb-106">They must be added by name to the [\<source>](source-element.md) or [\<trace>](trace-element.md).</span></span> <span data-ttu-id="6cfdb-107">Não é possível obter os ouvintes na `sharedListeners` coleção no código em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="6cfdb-107">It is not possible to get the listeners in the `sharedListeners` collection in code at run time.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sharedListeners>**](sharedlisteners-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

## <a name="syntax"></a><span data-ttu-id="6cfdb-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6cfdb-108">Syntax</span></span>  
  
```xml  
<add name="name"
  type="TraceListenerClassName, Version, Culture, PublicKeyToken"  
  initializeData="data"
  traceOutputOptions = "None"
/>  
```
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6cfdb-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="6cfdb-109">Attributes and Elements</span></span>  
 <span data-ttu-id="6cfdb-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="6cfdb-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6cfdb-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="6cfdb-111">Attributes</span></span>  
  
|<span data-ttu-id="6cfdb-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="6cfdb-112">Attribute</span></span>|<span data-ttu-id="6cfdb-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="6cfdb-113">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="6cfdb-114">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="6cfdb-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="6cfdb-115">Especifica o nome do ouvinte que é usado para adicionar o ouvinte compartilhado a uma `Listeners` coleção.</span><span class="sxs-lookup"><span data-stu-id="6cfdb-115">Specifies the name of the listener that is used to add the shared listener to a `Listeners` collection.</span></span>|  
|`type`|<span data-ttu-id="6cfdb-116">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="6cfdb-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="6cfdb-117">Especifica o tipo do ouvinte.</span><span class="sxs-lookup"><span data-stu-id="6cfdb-117">Specifies the type of the listener.</span></span> <span data-ttu-id="6cfdb-118">Você deve usar uma cadeia de caracteres que atenda aos requisitos especificados na [especificação de nomes de tipo totalmente qualificados](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="6cfdb-118">You must use a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="6cfdb-119">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="6cfdb-119">Optional attribute.</span></span><br /><br /> <span data-ttu-id="6cfdb-120">A cadeia de caracteres passada para o construtor para a classe especificada.</span><span class="sxs-lookup"><span data-stu-id="6cfdb-120">The string passed to the constructor for the specified class.</span></span>|  
|`traceOutputOptions`|<span data-ttu-id="6cfdb-121">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="6cfdb-121">Optional attribute.</span></span><br/><br/><span data-ttu-id="6cfdb-122">A representação de cadeia de caracteres de um ou mais <xref:System.Diagnostics.TraceOptions> membros de enumeração que indica os dados a serem gravados na saída do rastreamento.</span><span class="sxs-lookup"><span data-stu-id="6cfdb-122">The string representation of one or more <xref:System.Diagnostics.TraceOptions> enumeration members that indicates the data to be written to the trace output.</span></span> <span data-ttu-id="6cfdb-123">Vários itens são separados por vírgulas.</span><span class="sxs-lookup"><span data-stu-id="6cfdb-123">Multiple items are separated by commas.</span></span> <span data-ttu-id="6cfdb-124">O valor padrão é "None".</span><span class="sxs-lookup"><span data-stu-id="6cfdb-124">The default value is "None".</span></span>|

### <a name="child-elements"></a><span data-ttu-id="6cfdb-125">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="6cfdb-125">Child Elements</span></span>  
  
|<span data-ttu-id="6cfdb-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="6cfdb-126">Element</span></span>|<span data-ttu-id="6cfdb-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="6cfdb-127">Description</span></span>|  
|-------------|-----------------|  
|[\<filter>](filter-element-for-add-for-sharedlisteners.md)|<span data-ttu-id="6cfdb-128">Adiciona um filtro a um ouvinte na coleção `sharedListeners`.</span><span class="sxs-lookup"><span data-stu-id="6cfdb-128">Adds a filter to a listener in the `sharedListeners` collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6cfdb-129">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="6cfdb-129">Parent Elements</span></span>  
  
|<span data-ttu-id="6cfdb-130">Elemento</span><span class="sxs-lookup"><span data-stu-id="6cfdb-130">Element</span></span>|<span data-ttu-id="6cfdb-131">Descrição</span><span class="sxs-lookup"><span data-stu-id="6cfdb-131">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="6cfdb-132">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6cfdb-132">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="6cfdb-133">Especifica os ouvintes de rastreamento que coletam, armazenam e roteiam mensagens e o nível em que uma opção de rastreamento é definida.</span><span class="sxs-lookup"><span data-stu-id="6cfdb-133">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sharedListeners`|<span data-ttu-id="6cfdb-134">Uma coleção de ouvintes que qualquer elemento de origem ou de rastreamento pode referenciar.</span><span class="sxs-lookup"><span data-stu-id="6cfdb-134">A collection of listeners that any source or trace element can reference.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6cfdb-135">Comentários</span><span class="sxs-lookup"><span data-stu-id="6cfdb-135">Remarks</span></span>  
 <span data-ttu-id="6cfdb-136">As classes de ouvinte fornecidas com o .NET Framework derivam da <xref:System.Diagnostics.TraceListener> classe.</span><span class="sxs-lookup"><span data-stu-id="6cfdb-136">The listener classes shipped with the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span> <span data-ttu-id="6cfdb-137">O valor para o `name` atributo é usado para adicionar o ouvinte compartilhado a uma `Listeners` coleção para um rastreamento ou uma origem de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="6cfdb-137">The value for the `name` attribute is used to add the shared listener to a `Listeners` collection for either a trace or a trace source.</span></span> <span data-ttu-id="6cfdb-138">O valor para o `initializeData` atributo depende do tipo de ouvinte que você criar.</span><span class="sxs-lookup"><span data-stu-id="6cfdb-138">The value for the `initializeData` attribute depends on the type of listener you create.</span></span> <span data-ttu-id="6cfdb-139">Nem todos os ouvintes de rastreamento exigem que você especifique `initializeData` .</span><span class="sxs-lookup"><span data-stu-id="6cfdb-139">Not all trace listeners require that you specify `initializeData`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6cfdb-140">Ao usar o `initializeData` atributo, você pode obter o aviso do compilador "o atributo ' initializeData ' não está declarado."</span><span class="sxs-lookup"><span data-stu-id="6cfdb-140">When you use the `initializeData` attribute, you may get the compiler warning "The 'initializeData' attribute is not declared."</span></span> <span data-ttu-id="6cfdb-141">Esse aviso ocorre porque as definições de configuração são validadas em relação à classe base abstrata <xref:System.Diagnostics.TraceListener> , que não reconhece o `initializeData` atributo.</span><span class="sxs-lookup"><span data-stu-id="6cfdb-141">This warning occurs because the configuration settings are validated against the abstract base class <xref:System.Diagnostics.TraceListener>, which does not recognize the `initializeData` attribute.</span></span> <span data-ttu-id="6cfdb-142">Normalmente, você pode ignorar esse aviso para implementações de ouvinte de rastreamento que têm um construtor que usa um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="6cfdb-142">Typically, you can ignore this warning for trace listener implementations that have a constructor that takes a parameter.</span></span>  
  
 <span data-ttu-id="6cfdb-143">A tabela a seguir mostra os ouvintes de rastreamento que estão incluídos com o .NET Framework e descreve o valor de seus `initializeData` atributos.</span><span class="sxs-lookup"><span data-stu-id="6cfdb-143">The following table shows the trace listeners that are included with the .NET Framework and describes the value of their `initializeData` attributes.</span></span>  
  
|<span data-ttu-id="6cfdb-144">Classe de ouvinte de rastreamento</span><span class="sxs-lookup"><span data-stu-id="6cfdb-144">Trace listener class</span></span>|<span data-ttu-id="6cfdb-145">valor do atributo initializeData</span><span class="sxs-lookup"><span data-stu-id="6cfdb-145">initializeData attribute value</span></span>|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener>|<span data-ttu-id="6cfdb-146">O `useErrorStream` valor do <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> Construtor.</span><span class="sxs-lookup"><span data-stu-id="6cfdb-146">The `useErrorStream` value for the <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> constructor.</span></span>  <span data-ttu-id="6cfdb-147">Defina o `initializeData` atributo como " `true` " para gravar rastreamento e depurar saída para o fluxo de erro padrão; defina-o como " `false` " para gravar no fluxo de saída padrão.</span><span class="sxs-lookup"><span data-stu-id="6cfdb-147">Set the `initializeData` attribute to "`true`" to write trace and debug output to the standard error stream; set it to "`false`" to write to the standard output stream.</span></span>|  
|<xref:System.Diagnostics.DelimitedListTraceListener>|<span data-ttu-id="6cfdb-148">O nome do arquivo no qual o <xref:System.Diagnostics.DelimitedListTraceListener> é gravado.</span><span class="sxs-lookup"><span data-stu-id="6cfdb-148">The name of the file the <xref:System.Diagnostics.DelimitedListTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|<span data-ttu-id="6cfdb-149">O nome da origem de um log de eventos existente.</span><span class="sxs-lookup"><span data-stu-id="6cfdb-149">The name of an existing event log source.</span></span>|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|<span data-ttu-id="6cfdb-150">O nome do arquivo no qual as <xref:System.Diagnostics.EventSchemaTraceListener> gravações são gravadas.</span><span class="sxs-lookup"><span data-stu-id="6cfdb-150">The name of the file that the <xref:System.Diagnostics.EventSchemaTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="6cfdb-151">O nome do arquivo no qual as <xref:System.Diagnostics.TextWriterTraceListener> gravações são gravadas.</span><span class="sxs-lookup"><span data-stu-id="6cfdb-151">The name of the file that the <xref:System.Diagnostics.TextWriterTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.XmlWriterTraceListener>|<span data-ttu-id="6cfdb-152">O nome do arquivo no qual as <xref:System.Diagnostics.XmlWriterTraceListener> gravações são gravadas.</span><span class="sxs-lookup"><span data-stu-id="6cfdb-152">The name of the file that the <xref:System.Diagnostics.XmlWriterTraceListener> writes to.</span></span>|  
  
## <a name="configuration-file"></a><span data-ttu-id="6cfdb-153">Arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="6cfdb-153">Configuration File</span></span>  
 <span data-ttu-id="6cfdb-154">Esse elemento pode ser usado no arquivo de configuração da máquina (Machine. config) e no arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6cfdb-154">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6cfdb-155">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6cfdb-155">Example</span></span>  
 <span data-ttu-id="6cfdb-156">O exemplo a seguir mostra como usar `<add>` elementos para adicionar o <xref:System.Diagnostics.TextWriterTraceListener> `textListener` à `sharedListeners` coleção.</span><span class="sxs-lookup"><span data-stu-id="6cfdb-156">The following example shows how to use `<add>` elements to add the <xref:System.Diagnostics.TextWriterTraceListener>`textListener` to the `sharedListeners` collection.</span></span>   <span data-ttu-id="6cfdb-157">`textListener`é adicionado pelo nome à `Listeners` coleção para a origem do rastreamento `TraceSourceApp` .</span><span class="sxs-lookup"><span data-stu-id="6cfdb-157">`textListener` is added by name to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span> <span data-ttu-id="6cfdb-158">O `textListener` ouvinte grava a saída de rastreamento no arquivo myListener. log.</span><span class="sxs-lookup"><span data-stu-id="6cfdb-158">The `textListener` listener writes trace output to the file myListener.log.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6cfdb-159">Confira também</span><span class="sxs-lookup"><span data-stu-id="6cfdb-159">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="6cfdb-160">Esquema de configurações de rastreamento e depuração</span><span class="sxs-lookup"><span data-stu-id="6cfdb-160">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="6cfdb-161">Ouvintes de rastreamento</span><span class="sxs-lookup"><span data-stu-id="6cfdb-161">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
