---
title: Elemento <source>
ms.date: 09/29/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source
- http://schemas.microsoft.com/.NetConfiguration/v2.0#source
helpviewer_keywords:
- <source> element
- source element
ms.openlocfilehash: 8860f5d3ed7ee0c04d1e8afd7614f3f73b470808
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59186544"
---
# <a name="source-element"></a><span data-ttu-id="bef03-102">\<origem > elemento</span><span class="sxs-lookup"><span data-stu-id="bef03-102">\<source> Element</span></span>
<span data-ttu-id="bef03-103">Especifica uma origem de rastreamento que inicia as mensagens de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="bef03-103">Specifies a trace source that initiates tracing messages.</span></span>  
  
 <span data-ttu-id="bef03-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="bef03-104">\<configuration></span></span>  
<span data-ttu-id="bef03-105">\<system.diagnostics></span><span class="sxs-lookup"><span data-stu-id="bef03-105">\<system.diagnostics></span></span>  
<span data-ttu-id="bef03-106">\<sources></span><span class="sxs-lookup"><span data-stu-id="bef03-106">\<sources></span></span>  
<span data-ttu-id="bef03-107">\<origem ></span><span class="sxs-lookup"><span data-stu-id="bef03-107">\<source></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bef03-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bef03-108">Syntax</span></span>  
  
```xml  
<source>   
  <listeners>...</listeners>  
</source>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bef03-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="bef03-109">Attributes and Elements</span></span>  
 <span data-ttu-id="bef03-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="bef03-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bef03-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="bef03-111">Attributes</span></span>  
  
|<span data-ttu-id="bef03-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="bef03-112">Attribute</span></span>|<span data-ttu-id="bef03-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="bef03-113">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="bef03-114">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="bef03-114">Optional attribute.</span></span><br /><br /> <span data-ttu-id="bef03-115">Especifica o nome da origem de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="bef03-115">Specifies the name of the trace source.</span></span>|  
|`switchName`|<span data-ttu-id="bef03-116">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="bef03-116">Optional attribute.</span></span><br /><br /> <span data-ttu-id="bef03-117">Especifica o nome de uma instância de comutador de rastreamento no aplicativo.</span><span class="sxs-lookup"><span data-stu-id="bef03-117">Specifies the name of a trace switch instance in the application.</span></span> <span data-ttu-id="bef03-118">Se a opção não for identificada em um `<switches>` elemento, o valor Especifica o nível para o comutador.</span><span class="sxs-lookup"><span data-stu-id="bef03-118">If the switch is not identified in a `<switches>` element, the value specifies the level for the switch.</span></span>|  
|`switchType`|<span data-ttu-id="bef03-119">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="bef03-119">Optional attribute.</span></span><br /><br /> <span data-ttu-id="bef03-120">Especifica o tipo de opção de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="bef03-120">Specifies the type of the trace switch.</span></span> <span data-ttu-id="bef03-121">Se estiver presente, o tipo deve ser um nome de classe válido e não pode ser uma cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="bef03-121">If present, the type must be a valid class name and cannot be an empty string.</span></span>|  
|`extraAttribute`|<span data-ttu-id="bef03-122">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="bef03-122">Optional attribute.</span></span><br /><br /> <span data-ttu-id="bef03-123">Especifica o valor para um atributo específico de fonte de rastreamento identificado pelo <xref:System.Diagnostics.TraceSource.GetSupportedAttributes%2A> método para essa origem de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="bef03-123">Specifies the value for a trace source-specific attribute identified by the <xref:System.Diagnostics.TraceSource.GetSupportedAttributes%2A> method for that trace source.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bef03-124">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="bef03-124">Child Elements</span></span>  
  
|<span data-ttu-id="bef03-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="bef03-125">Element</span></span>|<span data-ttu-id="bef03-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="bef03-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bef03-127">\<listeners></span><span class="sxs-lookup"><span data-stu-id="bef03-127">\<listeners></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/listeners-element-for-source.md)|<span data-ttu-id="bef03-128">Contém os ouvintes que coletam, armazenam e roteiam mensagens.</span><span class="sxs-lookup"><span data-stu-id="bef03-128">Contains listeners that collect, store, and route messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="bef03-129">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="bef03-129">Parent Elements</span></span>  
  
|<span data-ttu-id="bef03-130">Elemento</span><span class="sxs-lookup"><span data-stu-id="bef03-130">Element</span></span>|<span data-ttu-id="bef03-131">Descrição</span><span class="sxs-lookup"><span data-stu-id="bef03-131">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="bef03-132">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="bef03-132">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="bef03-133">Especifica os ouvintes de rastreamento que coletam, armazenam e roteiam mensagens e o nível em que uma opção de rastreamento é definida.</span><span class="sxs-lookup"><span data-stu-id="bef03-133">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="bef03-134">Contém as origens de rastreamento que iniciam as mensagens de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="bef03-134">Contains trace sources that initiate tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bef03-135">Comentários</span><span class="sxs-lookup"><span data-stu-id="bef03-135">Remarks</span></span>  
 <span data-ttu-id="bef03-136">Esse elemento pode ser usado no arquivo de configuração de máquina (Machine. config) e o arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="bef03-136">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bef03-137">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bef03-137">Example</span></span>  
 <span data-ttu-id="bef03-138">O exemplo a seguir mostra como usar o `<source>` elemento para adicionar a origem de rastreamento `mySource` e para definir o nível para a alternância de origem chamado `sourceSwitch`.</span><span class="sxs-lookup"><span data-stu-id="bef03-138">The following example shows how to use the `<source>` element to add the trace source `mySource` and to set the level for the source switch named `sourceSwitch`.</span></span> <span data-ttu-id="bef03-139">Um ouvinte de rastreamento do console é adicionado, que grava informações de rastreamento no console.</span><span class="sxs-lookup"><span data-stu-id="bef03-139">A console trace listener is added that writes trace information to the console.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="bef03-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bef03-140">See also</span></span>

- [<span data-ttu-id="bef03-141">Esquema de configurações de rastreamento e depuração</span><span class="sxs-lookup"><span data-stu-id="bef03-141">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
- [<span data-ttu-id="bef03-142">Opções de rastreamento</span><span class="sxs-lookup"><span data-stu-id="bef03-142">Trace Switches</span></span>](../../../../../docs/framework/debug-trace-profile/trace-switches.md)
