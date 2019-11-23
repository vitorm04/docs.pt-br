---
title: Elemento <listeners> para <source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners
helpviewer_keywords:
- listeners element for <source>
- <listeners> element for <source>
ms.assetid: a2991f43-b4d3-4614-a8e7-da392de9697f
ms.openlocfilehash: d7641611e5d8257b49bc6a6abd0a2fadfde66e91
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697297"
---
# <a name="listeners-element-for-source"></a><span data-ttu-id="986ce-102">Elemento \<Listeners > para \<origem ></span><span class="sxs-lookup"><span data-stu-id="986ce-102">\<listeners> Element for \<source></span></span>
<span data-ttu-id="986ce-103">Adiciona ou remove ouvintes na coleção de <xref:System.Diagnostics.TraceSource.Listeners%2A> para um <xref:System.Diagnostics.TraceSource>.</span><span class="sxs-lookup"><span data-stu-id="986ce-103">Adds or removes listeners in the <xref:System.Diagnostics.TraceSource.Listeners%2A> collection for a <xref:System.Diagnostics.TraceSource>.</span></span> <span data-ttu-id="986ce-104">Um ouvinte direciona a saída de rastreamento para um destino apropriado, como um log, uma janela ou um arquivo de texto.</span><span class="sxs-lookup"><span data-stu-id="986ce-104">A listener directs the tracing output to an appropriate target, such as a log, window, or text file.</span></span>  
  
[<span data-ttu-id="986ce-105"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="986ce-105">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="986ce-106">&nbsp;&nbsp;[ **\<System. Diagnostics >** ](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="986ce-106">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>  
<span data-ttu-id="986ce-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<de fontes >** ](sources-element.md)</span><span class="sxs-lookup"><span data-stu-id="986ce-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)</span></span>  
<span data-ttu-id="986ce-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<[ **fonte** >](source-element.md)</span><span class="sxs-lookup"><span data-stu-id="986ce-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<source>**](source-element.md)</span></span>  
<span data-ttu-id="986ce-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**ouvintes >**</span><span class="sxs-lookup"><span data-stu-id="986ce-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<listeners>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="986ce-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="986ce-110">Syntax</span></span>  
  
```xml  
<listeners>   
  <add>...</add>  
  <remove ... />  
  <clear/>  
</listeners>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="986ce-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="986ce-111">Attributes and Elements</span></span>  
 <span data-ttu-id="986ce-112">As seções a seguir descrevem os atributos, bem como os elementos filhos e pais.</span><span class="sxs-lookup"><span data-stu-id="986ce-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="986ce-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="986ce-113">Attributes</span></span>  
 <span data-ttu-id="986ce-114">None.</span><span class="sxs-lookup"><span data-stu-id="986ce-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="986ce-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="986ce-115">Child Elements</span></span>  
  
|<span data-ttu-id="986ce-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="986ce-116">Element</span></span>|<span data-ttu-id="986ce-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="986ce-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="986ce-118">\<add></span><span class="sxs-lookup"><span data-stu-id="986ce-118">\<add></span></span>](add-element-for-listeners-for-source.md)|<span data-ttu-id="986ce-119">Adiciona um ouvinte na coleção `Listeners`.</span><span class="sxs-lookup"><span data-stu-id="986ce-119">Adds a listener to the `Listeners` collection.</span></span>|  
|[<span data-ttu-id="986ce-120">\<remove></span><span class="sxs-lookup"><span data-stu-id="986ce-120">\<remove></span></span>](remove-element-for-listeners-for-source.md)|<span data-ttu-id="986ce-121">Remove um ouvinte da coleção de `Listeners`.</span><span class="sxs-lookup"><span data-stu-id="986ce-121">Removes a listener from the `Listeners` collection.</span></span>|  
|[<span data-ttu-id="986ce-122">\<clear></span><span class="sxs-lookup"><span data-stu-id="986ce-122">\<clear></span></span>](clear-element-for-listeners-for-source.md)|<span data-ttu-id="986ce-123">Limpa a coleção `Listeners` de uma origem de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="986ce-123">Clears the `Listeners` collection for a trace source.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="986ce-124">Elementos Pai</span><span class="sxs-lookup"><span data-stu-id="986ce-124">Parent Elements</span></span>  
  
|<span data-ttu-id="986ce-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="986ce-125">Element</span></span>|<span data-ttu-id="986ce-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="986ce-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="986ce-127">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="986ce-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="986ce-128">Especifica os ouvintes de rastreamento que coletam, armazenam e roteiam mensagens e o nível em que uma opção de rastreamento é definida.</span><span class="sxs-lookup"><span data-stu-id="986ce-128">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="986ce-129">Contém as origens de rastreamento que iniciam as mensagens de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="986ce-129">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="986ce-130">Especifica uma origem de rastreamento que inicia as mensagens de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="986ce-130">Specifies a trace source that initiates tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="986ce-131">Comentários</span><span class="sxs-lookup"><span data-stu-id="986ce-131">Remarks</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="986ce-132">Arquivo de Configuração</span><span class="sxs-lookup"><span data-stu-id="986ce-132">Configuration File</span></span>  
 <span data-ttu-id="986ce-133">Esse elemento pode ser usado no arquivo de configuração da máquina (Machine. config) e no arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="986ce-133">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="986ce-134">{1&gt;Exemplo&lt;1}</span><span class="sxs-lookup"><span data-stu-id="986ce-134">Example</span></span>  
 <span data-ttu-id="986ce-135">O exemplo a seguir mostra como usar o elemento `<listeners>` para adicionar um ouvinte de rastreamento de console à fonte de `mySource` e remover o ouvinte de rastreamento padrão.</span><span class="sxs-lookup"><span data-stu-id="986ce-135">The following example shows how to use the `<listeners>` element to add a console trace listener to the `mySource` source and to remove the default trace listener.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="mySource" switchName="sourceSwitch"   
        switchType="System.Diagnostics.SourceSwitch">  
        <listeners>  
          <add name="console"   
            type="System.Diagnostics.ConsoleTraceListener">  
            <filter type="System.Diagnostics.EventTypeFilter"   
              initializeData="Error"/>  
          </add>  
          <remove name="Default"/>  
        </listeners>  
      </source>  
    </sources>  
    <switches>  
      <add name="sourceSwitch" value="Warning"/>  
    </switches>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="986ce-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="986ce-136">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="986ce-137">Esquema de configurações de rastreamento e depuração</span><span class="sxs-lookup"><span data-stu-id="986ce-137">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="986ce-138">Ouvintes de rastreamento</span><span class="sxs-lookup"><span data-stu-id="986ce-138">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
