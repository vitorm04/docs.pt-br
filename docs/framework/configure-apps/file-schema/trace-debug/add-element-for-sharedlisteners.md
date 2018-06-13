---
title: '&lt;Adicionar&gt; elemento para &lt;sharedListeners&gt;'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sharedListeners/add
helpviewer_keywords:
- initializeData attribute
- <add> element for <sharedListeners>
- add element for <sharedListeners>
ms.assetid: 1595e1bc-2492-421f-8384-7f382eb8eb57
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 27d83ba706b4d93b4ac5426bf5bae59b4bfc0d9a
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32752605"
---
# <a name="ltaddgt-element-for-ltsharedlistenersgt"></a><span data-ttu-id="98308-102">&lt;Adicionar&gt; elemento para &lt;sharedListeners&gt;</span><span class="sxs-lookup"><span data-stu-id="98308-102">&lt;add&gt; Element for &lt;sharedListeners&gt;</span></span>
<span data-ttu-id="98308-103">Adiciona um ouvinte na coleção `sharedListeners`.</span><span class="sxs-lookup"><span data-stu-id="98308-103">Adds a listener to the `sharedListeners` collection.</span></span> <span data-ttu-id="98308-104">`sharedListeners` é uma coleção de ouvintes que quaisquer [ \<fonte >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/source-element.md) ou [ \<rastreamento >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/trace-element.md) podem fazer referência.</span><span class="sxs-lookup"><span data-stu-id="98308-104">`sharedListeners` is a collection of listeners that any [\<source>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/source-element.md) or [\<trace>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/trace-element.md) can reference.</span></span>  <span data-ttu-id="98308-105">Por padrão, ouvintes no `sharedListeners` coleção não são colocados em um `Listeners` coleção.</span><span class="sxs-lookup"><span data-stu-id="98308-105">By default, listeners in the `sharedListeners` collection are not placed in a `Listeners` collection.</span></span> <span data-ttu-id="98308-106">Eles devem ser adicionados por nome para o [ \<fonte >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/source-element.md) ou [ \<rastreamento >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/trace-element.md).</span><span class="sxs-lookup"><span data-stu-id="98308-106">They must be added by name to the [\<source>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/source-element.md) or [\<trace>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/trace-element.md).</span></span> <span data-ttu-id="98308-107">Não é possível obter os ouvintes de `sharedListeners` coleção no código em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="98308-107">It is not possible to get the listeners in the `sharedListeners` collection in code at run time.</span></span>  
  
 <span data-ttu-id="98308-108">\<configuration></span><span class="sxs-lookup"><span data-stu-id="98308-108">\<configuration></span></span>  
<span data-ttu-id="98308-109">\<System. Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="98308-109">\<system.diagnostics></span></span>  
<span data-ttu-id="98308-110">\<sharedListeners > elemento</span><span class="sxs-lookup"><span data-stu-id="98308-110">\<sharedListeners> Element</span></span>  
<span data-ttu-id="98308-111">\<add></span><span class="sxs-lookup"><span data-stu-id="98308-111">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98308-112">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="98308-112">Syntax</span></span>  
  
```xml  
<add name="name"   
  type="TraceListenerClassName, Version, Culture, PublicKeyToken"  
  initializeData="data"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="98308-113">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="98308-113">Attributes and Elements</span></span>  
 <span data-ttu-id="98308-114">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="98308-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="98308-115">Atributos</span><span class="sxs-lookup"><span data-stu-id="98308-115">Attributes</span></span>  
  
|<span data-ttu-id="98308-116">Atributo</span><span class="sxs-lookup"><span data-stu-id="98308-116">Attribute</span></span>|<span data-ttu-id="98308-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="98308-117">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="98308-118">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="98308-118">Required attribute.</span></span><br /><br /> <span data-ttu-id="98308-119">Especifica o nome do ouvinte que é usado para adicionar o ouvinte de compartilhado para um `Listeners` coleção.</span><span class="sxs-lookup"><span data-stu-id="98308-119">Specifies the name of the listener that is used to add the shared listener to a `Listeners` collection.</span></span>|  
|`type`|<span data-ttu-id="98308-120">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="98308-120">Required attribute.</span></span><br /><br /> <span data-ttu-id="98308-121">Especifica o tipo de ouvinte.</span><span class="sxs-lookup"><span data-stu-id="98308-121">Specifies the type of the listener.</span></span> <span data-ttu-id="98308-122">Você deve usar uma cadeia de caracteres que atenda aos requisitos especificados em [especificando nomes de tipo totalmente qualificados](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="98308-122">You must use a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="98308-123">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="98308-123">Optional attribute.</span></span><br /><br /> <span data-ttu-id="98308-124">A cadeia de caracteres passada para o construtor para a classe especificada.</span><span class="sxs-lookup"><span data-stu-id="98308-124">The string passed to the constructor for the specified class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="98308-125">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="98308-125">Child Elements</span></span>  
  
|<span data-ttu-id="98308-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="98308-126">Element</span></span>|<span data-ttu-id="98308-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="98308-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="98308-128">\<filter></span><span class="sxs-lookup"><span data-stu-id="98308-128">\<filter></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/filter-element-for-add-for-sharedlisteners.md)|<span data-ttu-id="98308-129">Adiciona um filtro a um ouvinte na coleção `sharedListeners`.</span><span class="sxs-lookup"><span data-stu-id="98308-129">Adds a filter to a listener in the `sharedListeners` collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="98308-130">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="98308-130">Parent Elements</span></span>  
  
|<span data-ttu-id="98308-131">Elemento</span><span class="sxs-lookup"><span data-stu-id="98308-131">Element</span></span>|<span data-ttu-id="98308-132">Descrição</span><span class="sxs-lookup"><span data-stu-id="98308-132">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="98308-133">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="98308-133">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="98308-134">Especifica os ouvintes de rastreamento que coletam, armazenam e roteiam mensagens e o nível em que uma opção de rastreamento é definida.</span><span class="sxs-lookup"><span data-stu-id="98308-134">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sharedListeners`|<span data-ttu-id="98308-135">Uma coleção de ouvintes que podem referenciar qualquer origem ou o elemento de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="98308-135">A collection of listeners that any source or trace element can reference.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="98308-136">Comentários</span><span class="sxs-lookup"><span data-stu-id="98308-136">Remarks</span></span>  
 <span data-ttu-id="98308-137">As classes de ouvinte fornecidas com o .NET Framework derivam de <xref:System.Diagnostics.TraceListener> classe.</span><span class="sxs-lookup"><span data-stu-id="98308-137">The listener classes shipped with the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span> <span data-ttu-id="98308-138">O valor para o `name` atributo é usado para adicionar o ouvinte compartilhado para um `Listeners` coleção para um rastreamento ou uma origem de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="98308-138">The value for the `name` attribute is used to add the shared listener to a `Listeners` collection for either a trace or a trace source.</span></span> <span data-ttu-id="98308-139">O valor para o `initializeData` atributo depende do tipo de ouvinte que você criar.</span><span class="sxs-lookup"><span data-stu-id="98308-139">The value for the `initializeData` attribute depends on the type of listener you create.</span></span> <span data-ttu-id="98308-140">Nem todos os ouvintes de rastreamento requerem que você especifique `initializeData`.</span><span class="sxs-lookup"><span data-stu-id="98308-140">Not all trace listeners require that you specify `initializeData`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="98308-141">Quando você usa o `initializeData` atributo, você pode obter o compilador aviso "o atributo 'initializeData' não é declarado".</span><span class="sxs-lookup"><span data-stu-id="98308-141">When you use the `initializeData` attribute, you may get the compiler warning "The 'initializeData' attribute is not declared."</span></span> <span data-ttu-id="98308-142">Este aviso ocorre porque as definições de configuração são validadas em relação a classe base abstrata <xref:System.Diagnostics.TraceListener>, que não reconhece o `initializeData` atributo.</span><span class="sxs-lookup"><span data-stu-id="98308-142">This warning occurs because the configuration settings are validated against the abstract base class <xref:System.Diagnostics.TraceListener>, which does not recognize the `initializeData` attribute.</span></span> <span data-ttu-id="98308-143">Normalmente, você pode ignorar este aviso para implementações de ouvinte de rastreamento que tem um construtor que usa um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="98308-143">Typically, you can ignore this warning for trace listener implementations that have a constructor that takes a parameter.</span></span>  
  
 <span data-ttu-id="98308-144">A tabela a seguir mostra os ouvintes de rastreamento que são incluídos com o .NET Framework e descreve o valor de suas `initializeData` atributos.</span><span class="sxs-lookup"><span data-stu-id="98308-144">The following table shows the trace listeners that are included with the .NET Framework and describes the value of their `initializeData` attributes.</span></span>  
  
|<span data-ttu-id="98308-145">Classe de ouvinte de rastreamento</span><span class="sxs-lookup"><span data-stu-id="98308-145">Trace listener class</span></span>|<span data-ttu-id="98308-146">valor do atributo initializeData</span><span class="sxs-lookup"><span data-stu-id="98308-146">initializeData attribute value</span></span>|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener>|<span data-ttu-id="98308-147">O `useErrorStream` valor para o <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> construtor.</span><span class="sxs-lookup"><span data-stu-id="98308-147">The `useErrorStream` value for the <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> constructor.</span></span>  <span data-ttu-id="98308-148">Definir o `initializeData` atributo "`true`"gravar saída de rastreamento e depuração para o fluxo de erro padrão; defina-a como"`false`" para gravar o fluxo de saída padrão.</span><span class="sxs-lookup"><span data-stu-id="98308-148">Set the `initializeData` attribute to "`true`" to write trace and debug output to the standard error stream; set it to "`false`" to write to the standard output stream.</span></span>|  
|<xref:System.Diagnostics.DelimitedListTraceListener>|<span data-ttu-id="98308-149">O nome do arquivo no qual o <xref:System.Diagnostics.DelimitedListTraceListener> é gravado.</span><span class="sxs-lookup"><span data-stu-id="98308-149">The name of the file the <xref:System.Diagnostics.DelimitedListTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|<span data-ttu-id="98308-150">O nome da origem de um log de eventos existente.</span><span class="sxs-lookup"><span data-stu-id="98308-150">The name of an existing event log source.</span></span>|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|<span data-ttu-id="98308-151">O nome do arquivo que o <xref:System.Diagnostics.EventSchemaTraceListener> grava.</span><span class="sxs-lookup"><span data-stu-id="98308-151">The name of the file that the <xref:System.Diagnostics.EventSchemaTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="98308-152">O nome do arquivo que o <xref:System.Diagnostics.TextWriterTraceListener> grava.</span><span class="sxs-lookup"><span data-stu-id="98308-152">The name of the file that the <xref:System.Diagnostics.TextWriterTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.XmlWriterTraceListener>|<span data-ttu-id="98308-153">O nome do arquivo que o <xref:System.Diagnostics.XmlWriterTraceListener> grava.</span><span class="sxs-lookup"><span data-stu-id="98308-153">The name of the file that the <xref:System.Diagnostics.XmlWriterTraceListener> writes to.</span></span>|  
  
## <a name="configuration-file"></a><span data-ttu-id="98308-154">Arquivo de Configuração</span><span class="sxs-lookup"><span data-stu-id="98308-154">Configuration File</span></span>  
 <span data-ttu-id="98308-155">Esse elemento pode ser usado no arquivo de configuração de máquina (Machine. config) e o arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="98308-155">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="98308-156">Exemplo</span><span class="sxs-lookup"><span data-stu-id="98308-156">Example</span></span>  
 <span data-ttu-id="98308-157">O exemplo a seguir mostra como usar `<add>` elementos para adicionar o <xref:System.Diagnostics.TextWriterTraceListener> `textListener` para o `sharedListeners` coleção.</span><span class="sxs-lookup"><span data-stu-id="98308-157">The following example shows how to use `<add>` elements to add the <xref:System.Diagnostics.TextWriterTraceListener>`textListener` to the `sharedListeners` collection.</span></span>   <span data-ttu-id="98308-158">`textListener` é adicionada pelo nome para o `Listeners` coleção para a origem de rastreamento `TraceSourceApp`.</span><span class="sxs-lookup"><span data-stu-id="98308-158">`textListener` is added by name to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span> <span data-ttu-id="98308-159">O `textListener` ouvinte grava a saída de rastreamento para o arquivo myListener.log.</span><span class="sxs-lookup"><span data-stu-id="98308-159">The `textListener` listener writes trace output to the file myListener.log.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="98308-160">Consulte também</span><span class="sxs-lookup"><span data-stu-id="98308-160">See Also</span></span>  
 <xref:System.Diagnostics.TraceSource>  
 <xref:System.Diagnostics.TraceListener>  
 [<span data-ttu-id="98308-161">Esquema de configurações de rastreamento e depuração</span><span class="sxs-lookup"><span data-stu-id="98308-161">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)  
 [<span data-ttu-id="98308-162">Ouvintes de rastreamento</span><span class="sxs-lookup"><span data-stu-id="98308-162">Trace Listeners</span></span>](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
