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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153289"
---
# <a name="source-element"></a><span data-ttu-id="e454e-102">Elemento \<source></span><span class="sxs-lookup"><span data-stu-id="e454e-102">\<source> Element</span></span>
<span data-ttu-id="e454e-103">Especifica uma origem de rastreamento que inicia as mensagens de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="e454e-103">Specifies a trace source that initiates tracing messages.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<source>**

## <a name="syntax"></a><span data-ttu-id="e454e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e454e-104">Syntax</span></span>  
  
```xml  
<source>
  <listeners>...</listeners>  
</source>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e454e-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="e454e-105">Attributes and Elements</span></span>  
 <span data-ttu-id="e454e-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="e454e-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e454e-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="e454e-107">Attributes</span></span>  
  
|<span data-ttu-id="e454e-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="e454e-108">Attribute</span></span>|<span data-ttu-id="e454e-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="e454e-109">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="e454e-110">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="e454e-110">Optional attribute.</span></span><br /><br /> <span data-ttu-id="e454e-111">Especifica o nome da origem do rastreamento.</span><span class="sxs-lookup"><span data-stu-id="e454e-111">Specifies the name of the trace source.</span></span>|  
|`switchName`|<span data-ttu-id="e454e-112">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="e454e-112">Optional attribute.</span></span><br /><br /> <span data-ttu-id="e454e-113">Especifica o nome de uma instância de opção de rastreamento no aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e454e-113">Specifies the name of a trace switch instance in the application.</span></span> <span data-ttu-id="e454e-114">Se a opção não for identificada em um `<switches>` elemento, o valor especificará o nível para a opção.</span><span class="sxs-lookup"><span data-stu-id="e454e-114">If the switch is not identified in a `<switches>` element, the value specifies the level for the switch.</span></span>|  
|`switchType`|<span data-ttu-id="e454e-115">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="e454e-115">Optional attribute.</span></span><br /><br /> <span data-ttu-id="e454e-116">Especifica o tipo da opção de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="e454e-116">Specifies the type of the trace switch.</span></span> <span data-ttu-id="e454e-117">Se presente, o tipo deve ser um nome de classe válido e não pode ser uma cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="e454e-117">If present, the type must be a valid class name and cannot be an empty string.</span></span>|  
|`extraAttribute`|<span data-ttu-id="e454e-118">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="e454e-118">Optional attribute.</span></span><br /><br /> <span data-ttu-id="e454e-119">Especifica o valor para um atributo específico de origem de rastreamento identificado pelo <xref:System.Diagnostics.TraceSource.GetSupportedAttributes%2A> método para essa origem de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="e454e-119">Specifies the value for a trace source-specific attribute identified by the <xref:System.Diagnostics.TraceSource.GetSupportedAttributes%2A> method for that trace source.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e454e-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="e454e-120">Child Elements</span></span>  
  
|<span data-ttu-id="e454e-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="e454e-121">Element</span></span>|<span data-ttu-id="e454e-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="e454e-122">Description</span></span>|  
|-------------|-----------------|  
|[\<listeners>](listeners-element-for-source.md)|<span data-ttu-id="e454e-123">Contém ouvintes que coletam, armazenam e roteiam mensagens.</span><span class="sxs-lookup"><span data-stu-id="e454e-123">Contains listeners that collect, store, and route messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e454e-124">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="e454e-124">Parent Elements</span></span>  
  
|<span data-ttu-id="e454e-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="e454e-125">Element</span></span>|<span data-ttu-id="e454e-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="e454e-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="e454e-127">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e454e-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="e454e-128">Especifica os ouvintes de rastreamento que coletam, armazenam e roteiam mensagens e o nível em que uma opção de rastreamento é definida.</span><span class="sxs-lookup"><span data-stu-id="e454e-128">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="e454e-129">Contém as origens de rastreamento que iniciam as mensagens de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="e454e-129">Contains trace sources that initiate tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e454e-130">Comentários</span><span class="sxs-lookup"><span data-stu-id="e454e-130">Remarks</span></span>  
 <span data-ttu-id="e454e-131">Esse elemento pode ser usado no arquivo de configuração da máquina (Machine. config) e no arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e454e-131">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e454e-132">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e454e-132">Example</span></span>  
 <span data-ttu-id="e454e-133">O exemplo a seguir mostra como usar o `<source>` elemento para adicionar a origem de rastreamento `mySource` e definir o nível para a opção de origem denominada `sourceSwitch` .</span><span class="sxs-lookup"><span data-stu-id="e454e-133">The following example shows how to use the `<source>` element to add the trace source `mySource` and to set the level for the source switch named `sourceSwitch`.</span></span> <span data-ttu-id="e454e-134">Um ouvinte de rastreamento de console é adicionado que grava informações de rastreamento no console do.</span><span class="sxs-lookup"><span data-stu-id="e454e-134">A console trace listener is added that writes trace information to the console.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e454e-135">Confira também</span><span class="sxs-lookup"><span data-stu-id="e454e-135">See also</span></span>

- [<span data-ttu-id="e454e-136">Esquema de configurações de rastreamento e depuração</span><span class="sxs-lookup"><span data-stu-id="e454e-136">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="e454e-137">Opções de rastreamento</span><span class="sxs-lookup"><span data-stu-id="e454e-137">Trace Switches</span></span>](../../../debug-trace-profile/trace-switches.md)
