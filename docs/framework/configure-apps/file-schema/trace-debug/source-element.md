---
title: '&lt;origem&gt; elemento'
ms.date: 09/29/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source
- http://schemas.microsoft.com/.NetConfiguration/v2.0#source
helpviewer_keywords:
- <source> element
- source element
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 818324077322fffb40a192c9197efde6e8ff7591
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47088939"
---
# <a name="ltsourcegt-element"></a><span data-ttu-id="c6e59-102">&lt;origem&gt; elemento</span><span class="sxs-lookup"><span data-stu-id="c6e59-102">&lt;source&gt; Element</span></span>
<span data-ttu-id="c6e59-103">Especifica uma origem de rastreamento que inicia as mensagens de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="c6e59-103">Specifies a trace source that initiates tracing messages.</span></span>  
  
 <span data-ttu-id="c6e59-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="c6e59-104">\<configuration></span></span>  
<span data-ttu-id="c6e59-105">\<System. Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="c6e59-105">\<system.diagnostics></span></span>  
<span data-ttu-id="c6e59-106">\<fontes ></span><span class="sxs-lookup"><span data-stu-id="c6e59-106">\<sources></span></span>  
<span data-ttu-id="c6e59-107">\<origem ></span><span class="sxs-lookup"><span data-stu-id="c6e59-107">\<source></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6e59-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c6e59-108">Syntax</span></span>  
  
```xml  
<source>   
  <listeners>...</listeners>  
</source>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c6e59-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="c6e59-109">Attributes and Elements</span></span>  
 <span data-ttu-id="c6e59-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="c6e59-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c6e59-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="c6e59-111">Attributes</span></span>  
  
|<span data-ttu-id="c6e59-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="c6e59-112">Attribute</span></span>|<span data-ttu-id="c6e59-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="c6e59-113">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="c6e59-114">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="c6e59-114">Optional attribute.</span></span><br /><br /> <span data-ttu-id="c6e59-115">Especifica o nome da origem de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="c6e59-115">Specifies the name of the trace source.</span></span>|  
|`switchName`|<span data-ttu-id="c6e59-116">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="c6e59-116">Optional attribute.</span></span><br /><br /> <span data-ttu-id="c6e59-117">Especifica o nome de uma instância de comutador de rastreamento no aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c6e59-117">Specifies the name of a trace switch instance in the application.</span></span> <span data-ttu-id="c6e59-118">Se a opção não for identificada em um `<switches>` elemento, o valor Especifica o nível para o comutador.</span><span class="sxs-lookup"><span data-stu-id="c6e59-118">If the switch is not identified in a `<switches>` element, the value specifies the level for the switch.</span></span>|  
|`switchType`|<span data-ttu-id="c6e59-119">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="c6e59-119">Optional attribute.</span></span><br /><br /> <span data-ttu-id="c6e59-120">Especifica o tipo de opção de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="c6e59-120">Specifies the type of the trace switch.</span></span> <span data-ttu-id="c6e59-121">Se estiver presente, o tipo deve ser um nome de classe válido e não pode ser uma cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="c6e59-121">If present, the type must be a valid class name and cannot be an empty string.</span></span>|  
|`extraAttribute`|<span data-ttu-id="c6e59-122">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="c6e59-122">Optional attribute.</span></span><br /><br /> <span data-ttu-id="c6e59-123">Especifica o valor para um atributo específico de fonte de rastreamento identificado pelo <xref:System.Diagnostics.TraceSource.GetSupportedAttributes%2A> método para essa origem de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="c6e59-123">Specifies the value for a trace source-specific attribute identified by the <xref:System.Diagnostics.TraceSource.GetSupportedAttributes%2A> method for that trace source.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c6e59-124">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="c6e59-124">Child Elements</span></span>  
  
|<span data-ttu-id="c6e59-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="c6e59-125">Element</span></span>|<span data-ttu-id="c6e59-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="c6e59-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c6e59-127">\<listeners></span><span class="sxs-lookup"><span data-stu-id="c6e59-127">\<listeners></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/listeners-element-for-source.md)|<span data-ttu-id="c6e59-128">Contém os ouvintes que coletam, armazenam e roteiam mensagens.</span><span class="sxs-lookup"><span data-stu-id="c6e59-128">Contains listeners that collect, store, and route messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c6e59-129">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="c6e59-129">Parent Elements</span></span>  
  
|<span data-ttu-id="c6e59-130">Elemento</span><span class="sxs-lookup"><span data-stu-id="c6e59-130">Element</span></span>|<span data-ttu-id="c6e59-131">Descrição</span><span class="sxs-lookup"><span data-stu-id="c6e59-131">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="c6e59-132">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c6e59-132">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="c6e59-133">Especifica os ouvintes de rastreamento que coletam, armazenam e roteiam mensagens e o nível em que uma opção de rastreamento é definida.</span><span class="sxs-lookup"><span data-stu-id="c6e59-133">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="c6e59-134">Contém as origens de rastreamento que iniciam as mensagens de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="c6e59-134">Contains trace sources that initiate tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c6e59-135">Comentários</span><span class="sxs-lookup"><span data-stu-id="c6e59-135">Remarks</span></span>  
 <span data-ttu-id="c6e59-136">Esse elemento pode ser usado no arquivo de configuração de máquina (Machine. config) e o arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c6e59-136">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c6e59-137">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c6e59-137">Example</span></span>  
 <span data-ttu-id="c6e59-138">O exemplo a seguir mostra como usar o `<source>` elemento para adicionar a origem de rastreamento `mySource` e para definir o nível para a alternância de origem chamado `sourceSwitch`.</span><span class="sxs-lookup"><span data-stu-id="c6e59-138">The following example shows how to use the `<source>` element to add the trace source `mySource` and to set the level for the source switch named `sourceSwitch`.</span></span> <span data-ttu-id="c6e59-139">Um ouvinte de rastreamento do console é adicionado, que grava informações de rastreamento no console.</span><span class="sxs-lookup"><span data-stu-id="c6e59-139">A console trace listener is added that writes trace information to the console.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="mySource" switchName="sourceSwitch" switchType="System.Diagnostics.SourceSwitch"  >  
        <listeners>  
          <add name="console" type="System.Diagnostics.ConsoleTraceListener" >  
            <filter type="System.Diagnostics.EventTypeFilter" initializeData="Error" />  
          </add>  
          <remove name="Default" />  
        </listeners>  
      </source>  
    </sources>  
        <switches>  
           <add name="sourceSwitch" value="Warning" />  
        </switches>    
  </system.diagnostics>   
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c6e59-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c6e59-140">See Also</span></span>  
 [<span data-ttu-id="c6e59-141">Esquema de configurações de rastreamento e depuração</span><span class="sxs-lookup"><span data-stu-id="c6e59-141">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)  
 [<span data-ttu-id="c6e59-142">Opções de rastreamento</span><span class="sxs-lookup"><span data-stu-id="c6e59-142">Trace Switches</span></span>](../../../../../docs/framework/debug-trace-profile/trace-switches.md)
