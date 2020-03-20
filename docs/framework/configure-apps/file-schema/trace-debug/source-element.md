---
title: Elemento <source>
ms.date: 09/29/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source
- http://schemas.microsoft.com/.NetConfiguration/v2.0#source
helpviewer_keywords:
- <source> element
- source element
ms.openlocfilehash: 417722ce2f3865350158413307495e3ab435d386
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153289"
---
# <a name="source-element"></a><span data-ttu-id="024f3-102">\<origem> Elemento</span><span class="sxs-lookup"><span data-stu-id="024f3-102">\<source> Element</span></span>
<span data-ttu-id="024f3-103">Especifica uma origem de rastreamento que inicia as mensagens de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="024f3-103">Specifies a trace source that initiates tracing messages.</span></span>  

<span data-ttu-id="024f3-104">[**\<>de configuração**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="024f3-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="024f3-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="024f3-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>\
<span data-ttu-id="024f3-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<fontes>**](sources-element.md)</span><span class="sxs-lookup"><span data-stu-id="024f3-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)</span></span>\
<span data-ttu-id="024f3-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>fonte**</span><span class="sxs-lookup"><span data-stu-id="024f3-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<source>**</span></span>

## <a name="syntax"></a><span data-ttu-id="024f3-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="024f3-108">Syntax</span></span>  
  
```xml  
<source>
  <listeners>...</listeners>  
</source>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="024f3-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="024f3-109">Attributes and Elements</span></span>  
 <span data-ttu-id="024f3-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="024f3-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="024f3-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="024f3-111">Attributes</span></span>  
  
|<span data-ttu-id="024f3-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="024f3-112">Attribute</span></span>|<span data-ttu-id="024f3-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="024f3-113">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="024f3-114">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="024f3-114">Optional attribute.</span></span><br /><br /> <span data-ttu-id="024f3-115">Especifica o nome da fonte de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="024f3-115">Specifies the name of the trace source.</span></span>|  
|`switchName`|<span data-ttu-id="024f3-116">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="024f3-116">Optional attribute.</span></span><br /><br /> <span data-ttu-id="024f3-117">Especifica o nome de uma instância de switch de rastreamento no aplicativo.</span><span class="sxs-lookup"><span data-stu-id="024f3-117">Specifies the name of a trace switch instance in the application.</span></span> <span data-ttu-id="024f3-118">Se o switch não `<switches>` for identificado em um elemento, o valor especificará o nível do switch.</span><span class="sxs-lookup"><span data-stu-id="024f3-118">If the switch is not identified in a `<switches>` element, the value specifies the level for the switch.</span></span>|  
|`switchType`|<span data-ttu-id="024f3-119">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="024f3-119">Optional attribute.</span></span><br /><br /> <span data-ttu-id="024f3-120">Especifica o tipo do interruptor de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="024f3-120">Specifies the type of the trace switch.</span></span> <span data-ttu-id="024f3-121">Se estiver presente, o tipo deve ser um nome de classe válido e não pode ser uma seqüência de string vazia.</span><span class="sxs-lookup"><span data-stu-id="024f3-121">If present, the type must be a valid class name and cannot be an empty string.</span></span>|  
|`extraAttribute`|<span data-ttu-id="024f3-122">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="024f3-122">Optional attribute.</span></span><br /><br /> <span data-ttu-id="024f3-123">Especifica o valor de um atributo específico <xref:System.Diagnostics.TraceSource.GetSupportedAttributes%2A> da origem de rastreamento identificado pelo método para essa fonte de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="024f3-123">Specifies the value for a trace source-specific attribute identified by the <xref:System.Diagnostics.TraceSource.GetSupportedAttributes%2A> method for that trace source.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="024f3-124">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="024f3-124">Child Elements</span></span>  
  
|<span data-ttu-id="024f3-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="024f3-125">Element</span></span>|<span data-ttu-id="024f3-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="024f3-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="024f3-127">\<ouvintes></span><span class="sxs-lookup"><span data-stu-id="024f3-127">\<listeners></span></span>](listeners-element-for-source.md)|<span data-ttu-id="024f3-128">Contém ouvintes que coletam, armazenam e encaminham mensagens.</span><span class="sxs-lookup"><span data-stu-id="024f3-128">Contains listeners that collect, store, and route messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="024f3-129">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="024f3-129">Parent Elements</span></span>  
  
|<span data-ttu-id="024f3-130">Elemento</span><span class="sxs-lookup"><span data-stu-id="024f3-130">Element</span></span>|<span data-ttu-id="024f3-131">Descrição</span><span class="sxs-lookup"><span data-stu-id="024f3-131">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="024f3-132">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="024f3-132">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="024f3-133">Especifica os ouvintes de rastreamento que coletam, armazenam e roteiam mensagens e o nível em que uma opção de rastreamento é definida.</span><span class="sxs-lookup"><span data-stu-id="024f3-133">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="024f3-134">Contém as origens de rastreamento que iniciam as mensagens de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="024f3-134">Contains trace sources that initiate tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="024f3-135">Comentários</span><span class="sxs-lookup"><span data-stu-id="024f3-135">Remarks</span></span>  
 <span data-ttu-id="024f3-136">Esse elemento pode ser usado no arquivo de configuração da máquina (Machine.config) e no arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="024f3-136">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="024f3-137">Exemplo</span><span class="sxs-lookup"><span data-stu-id="024f3-137">Example</span></span>  
 <span data-ttu-id="024f3-138">O exemplo a seguir `<source>` mostra como usar `mySource` o elemento para adicionar a `sourceSwitch`fonte de rastreamento e definir o nível para o switch de origem chamado .</span><span class="sxs-lookup"><span data-stu-id="024f3-138">The following example shows how to use the `<source>` element to add the trace source `mySource` and to set the level for the source switch named `sourceSwitch`.</span></span> <span data-ttu-id="024f3-139">Um ouvinte de rastreamento de console é adicionado que grava informações de rastreamento para o console.</span><span class="sxs-lookup"><span data-stu-id="024f3-139">A console trace listener is added that writes trace information to the console.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="024f3-140">Confira também</span><span class="sxs-lookup"><span data-stu-id="024f3-140">See also</span></span>

- [<span data-ttu-id="024f3-141">Esquema de configurações de rastreamento e depuração</span><span class="sxs-lookup"><span data-stu-id="024f3-141">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="024f3-142">Opções de rastreamento</span><span class="sxs-lookup"><span data-stu-id="024f3-142">Trace Switches</span></span>](../../../debug-trace-profile/trace-switches.md)
