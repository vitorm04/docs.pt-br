---
title: <add>Elemento para <listeners> para<source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/add
helpviewer_keywords:
- initializeData attribute
- add element for <listeners> for <source>
- <add> element for <listeners> for <source>
ms.assetid: 4ce36ac1-81ef-48e8-b8b2-b5a5b0e2adcb
ms.openlocfilehash: 883eef32172c5a7f900197995b4c57c3d5a84e19
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153679"
---
# <a name="add-element-for-listeners-for-source"></a><span data-ttu-id="ed4aa-102">\<add>Elemento para \<listeners> para\<source></span><span class="sxs-lookup"><span data-stu-id="ed4aa-102">\<add> Element for \<listeners> for \<source></span></span>
<span data-ttu-id="ed4aa-103">Adiciona um ouvinte na coleção `Listeners` de uma origem de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="ed4aa-103">Adds a listener to the `Listeners` collection for a trace source.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<source>**](source-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-source.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

## <a name="syntax"></a><span data-ttu-id="ed4aa-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ed4aa-104">Syntax</span></span>  
  
```xml  
<add name="name"
  type="TraceListenerClassName, Version, Culture, PublicKeyToken"  
  initializeData="data"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ed4aa-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="ed4aa-105">Attributes and Elements</span></span>  
 <span data-ttu-id="ed4aa-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="ed4aa-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ed4aa-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="ed4aa-107">Attributes</span></span>  
  
|<span data-ttu-id="ed4aa-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="ed4aa-108">Attribute</span></span>|<span data-ttu-id="ed4aa-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="ed4aa-109">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="ed4aa-110">Atributo obrigatório, a menos que você esteja fazendo referência a um ouvinte na `sharedListeners` coleção; nesse caso, você só precisa fazer referência a ele por nome (consulte o [exemplo](#example)).</span><span class="sxs-lookup"><span data-stu-id="ed4aa-110">Required attribute, unless you're referencing a listener in the `sharedListeners` collection, in which case you only need to refer to it by name (see the [Example](#example)).</span></span><br /><br /> <span data-ttu-id="ed4aa-111">Especifica o tipo do ouvinte.</span><span class="sxs-lookup"><span data-stu-id="ed4aa-111">Specifies the type of the listener.</span></span> <span data-ttu-id="ed4aa-112">Você deve usar uma cadeia de caracteres que atenda aos requisitos especificados na [especificação de nomes de tipo totalmente qualificados](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="ed4aa-112">You must use a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="ed4aa-113">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="ed4aa-113">Optional attribute.</span></span><br /><br /> <span data-ttu-id="ed4aa-114">A cadeia de caracteres passada para o construtor para a classe especificada.</span><span class="sxs-lookup"><span data-stu-id="ed4aa-114">The string passed to the constructor for the specified class.</span></span> <span data-ttu-id="ed4aa-115">Um <xref:System.Configuration.ConfigurationException> será gerado se a classe não tiver um construtor que usa uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="ed4aa-115">A <xref:System.Configuration.ConfigurationException> is thrown if the class does not have a constructor that takes a string.</span></span>|  
|`name`|<span data-ttu-id="ed4aa-116">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="ed4aa-116">Optional attribute.</span></span><br /><br /> <span data-ttu-id="ed4aa-117">Especifica o nome do ouvinte.</span><span class="sxs-lookup"><span data-stu-id="ed4aa-117">Specifies the name of the listener.</span></span>|  
|`traceOutputOptions`|<span data-ttu-id="ed4aa-118">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="ed4aa-118">Optional attribute.</span></span><br /><br /> <span data-ttu-id="ed4aa-119">Especifica o <xref:System.Diagnostics.TraceListener.TraceOutputOptions%2A> valor da propriedade para o ouvinte de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="ed4aa-119">Specifies the <xref:System.Diagnostics.TraceListener.TraceOutputOptions%2A> property value for the trace listener.</span></span>|  
|<span data-ttu-id="ed4aa-120">[atributos personalizados]</span><span class="sxs-lookup"><span data-stu-id="ed4aa-120">[custom attributes]</span></span>|<span data-ttu-id="ed4aa-121">Atributos opcionais.</span><span class="sxs-lookup"><span data-stu-id="ed4aa-121">Optional attributes.</span></span><br /><br /> <span data-ttu-id="ed4aa-122">Especifica o valor para atributos específicos do ouvinte identificados pelo <xref:System.Diagnostics.TraceListener.GetSupportedAttributes%2A> método para esse ouvinte.</span><span class="sxs-lookup"><span data-stu-id="ed4aa-122">Specifies the value for listener-specific attributes identified by the <xref:System.Diagnostics.TraceListener.GetSupportedAttributes%2A> method for that listener.</span></span> <span data-ttu-id="ed4aa-123"><xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A>é um exemplo de um atributo extra exclusivo para a <xref:System.Diagnostics.DelimitedListTraceListener> classe.</span><span class="sxs-lookup"><span data-stu-id="ed4aa-123"><xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A> is an example of an extra attribute unique to the <xref:System.Diagnostics.DelimitedListTraceListener> class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ed4aa-124">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="ed4aa-124">Child Elements</span></span>  
  
|<span data-ttu-id="ed4aa-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="ed4aa-125">Element</span></span>|<span data-ttu-id="ed4aa-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="ed4aa-126">Description</span></span>|  
|-------------|-----------------|  
|[\<filter>](filter-element-for-add-for-listeners-for-source.md)|<span data-ttu-id="ed4aa-127">Adiciona um filtro a um ouvinte na coleção `Listeners` de uma origem de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="ed4aa-127">Adds a filter to a listener in the `Listeners` collection for a trace source.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ed4aa-128">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="ed4aa-128">Parent Elements</span></span>  
  
|<span data-ttu-id="ed4aa-129">Elemento</span><span class="sxs-lookup"><span data-stu-id="ed4aa-129">Element</span></span>|<span data-ttu-id="ed4aa-130">Descrição</span><span class="sxs-lookup"><span data-stu-id="ed4aa-130">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="ed4aa-131">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ed4aa-131">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="ed4aa-132">Especifica os ouvintes de rastreamento que coletam, armazenam e roteiam mensagens e o nível em que uma opção de rastreamento é definida.</span><span class="sxs-lookup"><span data-stu-id="ed4aa-132">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="ed4aa-133">Contém as origens de rastreamento que iniciam as mensagens de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="ed4aa-133">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="ed4aa-134">Especifica uma origem de rastreamento que inicia as mensagens de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="ed4aa-134">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="ed4aa-135">Especifica os ouvintes que coletam, armazenam e roteiam mensagens.</span><span class="sxs-lookup"><span data-stu-id="ed4aa-135">Specifies listeners that collect, store, and route messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ed4aa-136">Comentários</span><span class="sxs-lookup"><span data-stu-id="ed4aa-136">Remarks</span></span>  
 <span data-ttu-id="ed4aa-137">As classes de ouvinte fornecidas com o .NET Framework derivam da <xref:System.Diagnostics.TraceListener> classe.</span><span class="sxs-lookup"><span data-stu-id="ed4aa-137">The listener classes shipped with the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span>  
  
 <span data-ttu-id="ed4aa-138">Se você não especificar o `name` atributo do ouvinte de rastreamento, a <xref:System.Diagnostics.TraceListener.Name%2A> Propriedade do ouvinte de rastreamento será padronizada como uma cadeia de caracteres vazia ("").</span><span class="sxs-lookup"><span data-stu-id="ed4aa-138">If you do not specify the `name` attribute of the trace listener, the <xref:System.Diagnostics.TraceListener.Name%2A> property of the trace listener defaults to an empty string ("").</span></span> <span data-ttu-id="ed4aa-139">Se seu aplicativo tiver apenas um ouvinte, você poderá adicioná-lo sem especificar um nome, e poderá removê-lo especificando uma cadeia de caracteres vazia para o nome.</span><span class="sxs-lookup"><span data-stu-id="ed4aa-139">If your application has only one listener, you can add it without specifying a name, and you can remove it by specifying an empty string for the name.</span></span> <span data-ttu-id="ed4aa-140">No entanto, se seu aplicativo tiver mais de um ouvinte, você deverá especificar um nome exclusivo para cada ouvinte de rastreamento, que permite identificar e gerenciar ouvintes de rastreamento individuais na <xref:System.Diagnostics.TraceSource.Listeners%2A?displayProperty=nameWithType> coleção.</span><span class="sxs-lookup"><span data-stu-id="ed4aa-140">However, if your application has more than one listener, you should specify a unique name for each trace listener, which allows you to identify and manage individual trace listeners in the <xref:System.Diagnostics.TraceSource.Listeners%2A?displayProperty=nameWithType> collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ed4aa-141">Adicionar mais de um ouvinte de rastreamento do mesmo tipo e com o mesmo nome resulta em apenas um ouvinte de rastreamento desse tipo e nome que estão sendo adicionados à `Listeners` coleção.</span><span class="sxs-lookup"><span data-stu-id="ed4aa-141">Adding more than one trace listener of the same type and with the same name results in only one trace listener of that type and name being added to the `Listeners` collection.</span></span> <span data-ttu-id="ed4aa-142">No entanto, você pode adicionar programaticamente vários ouvintes idênticos à `Listeners` coleção.</span><span class="sxs-lookup"><span data-stu-id="ed4aa-142">However, you can programmatically add multiple identical listeners to the `Listeners` collection.</span></span>  
  
 <span data-ttu-id="ed4aa-143">O valor para o `initializeData` atributo depende do tipo de ouvinte que você criar.</span><span class="sxs-lookup"><span data-stu-id="ed4aa-143">The value for the `initializeData` attribute depends on the type of listener you create.</span></span> <span data-ttu-id="ed4aa-144">Nem todos os ouvintes de rastreamento exigem que você especifique `initializeData` .</span><span class="sxs-lookup"><span data-stu-id="ed4aa-144">Not all trace listeners require that you specify `initializeData`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ed4aa-145">Ao usar o `initializeData` atributo, você pode obter o aviso do compilador "o atributo ' initializeData ' não está declarado."</span><span class="sxs-lookup"><span data-stu-id="ed4aa-145">When you use the `initializeData` attribute, you may get the compiler warning "The 'initializeData' attribute is not declared."</span></span> <span data-ttu-id="ed4aa-146">Esse aviso ocorre porque as definições de configuração são validadas em relação à classe base abstrata <xref:System.Diagnostics.TraceListener> , que não reconhece o `initializeData` atributo.</span><span class="sxs-lookup"><span data-stu-id="ed4aa-146">This warning occurs because the configuration settings are validated against the abstract base class <xref:System.Diagnostics.TraceListener>, which does not recognize the `initializeData` attribute.</span></span> <span data-ttu-id="ed4aa-147">Normalmente, você pode ignorar esse aviso para implementações de ouvinte de rastreamento que têm um construtor que usa um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="ed4aa-147">Typically, you can ignore this warning for trace listener implementations that have a constructor that takes a parameter.</span></span>  
  
 <span data-ttu-id="ed4aa-148">A tabela a seguir mostra os ouvintes de rastreamento que estão incluídos com o .NET Framework e descreve o valor de seus `initializeData` atributos.</span><span class="sxs-lookup"><span data-stu-id="ed4aa-148">The following table shows the trace listeners that are included with the .NET Framework and describes the value of their `initializeData` attributes.</span></span>  
  
|<span data-ttu-id="ed4aa-149">Classe de ouvinte de rastreamento</span><span class="sxs-lookup"><span data-stu-id="ed4aa-149">Trace listener class</span></span>|<span data-ttu-id="ed4aa-150">valor do atributo initializeData</span><span class="sxs-lookup"><span data-stu-id="ed4aa-150">initializeData attribute value</span></span>|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>|<span data-ttu-id="ed4aa-151">O `useErrorStream` valor do <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> Construtor.</span><span class="sxs-lookup"><span data-stu-id="ed4aa-151">The `useErrorStream` value for the <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> constructor.</span></span>  <span data-ttu-id="ed4aa-152">Defina o `initializeData` atributo como " `true` " para gravar rastreamento e depurar saída para o fluxo de erro padrão; defina-o como " `false` " para gravar no fluxo de saída padrão.</span><span class="sxs-lookup"><span data-stu-id="ed4aa-152">Set the `initializeData` attribute to "`true`" to write trace and debug output to the standard error stream; set it to "`false`" to write to the standard output stream.</span></span>|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>|<span data-ttu-id="ed4aa-153">O nome do arquivo no qual o <xref:System.Diagnostics.DelimitedListTraceListener> é gravado.</span><span class="sxs-lookup"><span data-stu-id="ed4aa-153">The name of the file the <xref:System.Diagnostics.DelimitedListTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|<span data-ttu-id="ed4aa-154">O nome da origem de um log de eventos existente.</span><span class="sxs-lookup"><span data-stu-id="ed4aa-154">The name of an existing event log source.</span></span>|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|<span data-ttu-id="ed4aa-155">O nome do arquivo no qual as <xref:System.Diagnostics.EventSchemaTraceListener> gravações são gravadas.</span><span class="sxs-lookup"><span data-stu-id="ed4aa-155">The name of the file that the <xref:System.Diagnostics.EventSchemaTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="ed4aa-156">O nome do arquivo no qual as <xref:System.Diagnostics.TextWriterTraceListener> gravações são gravadas.</span><span class="sxs-lookup"><span data-stu-id="ed4aa-156">The name of the file that the <xref:System.Diagnostics.TextWriterTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="ed4aa-157">O nome do arquivo no qual as <xref:System.Diagnostics.XmlWriterTraceListener> gravações são gravadas.</span><span class="sxs-lookup"><span data-stu-id="ed4aa-157">The name of the file that the <xref:System.Diagnostics.XmlWriterTraceListener> writes to.</span></span>|  
  
## <a name="configuration-file"></a><span data-ttu-id="ed4aa-158">Arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="ed4aa-158">Configuration File</span></span>  
 <span data-ttu-id="ed4aa-159">Esse elemento pode ser usado no arquivo de configuração da máquina (Machine. config) e no arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ed4aa-159">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ed4aa-160">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ed4aa-160">Example</span></span>  
 <span data-ttu-id="ed4aa-161">O exemplo a seguir mostra como usar `<add>` elementos para adicionar os ouvintes `console` e `textListener` à `Listeners` coleção para a origem do rastreamento `TraceSourceApp` .</span><span class="sxs-lookup"><span data-stu-id="ed4aa-161">The following example shows how to use `<add>` elements to add the listeners `console` and `textListener` to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span> <span data-ttu-id="ed4aa-162">O `textListener` ouvinte grava a saída de rastreamento no arquivo myListener. log.</span><span class="sxs-lookup"><span data-stu-id="ed4aa-162">The `textListener` listener writes trace output to the file myListener.log.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ed4aa-163">Confira também</span><span class="sxs-lookup"><span data-stu-id="ed4aa-163">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="ed4aa-164">Esquema de configurações de rastreamento e depuração</span><span class="sxs-lookup"><span data-stu-id="ed4aa-164">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="ed4aa-165">Ouvintes de rastreamento</span><span class="sxs-lookup"><span data-stu-id="ed4aa-165">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
