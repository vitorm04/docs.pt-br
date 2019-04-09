---
title: <listeners> elemento para <source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners
helpviewer_keywords:
- listeners element for <source>
- <listeners> element for <source>
ms.assetid: a2991f43-b4d3-4614-a8e7-da392de9697f
ms.openlocfilehash: b15a30fb6d356f92312bf33bc1964c7922ba1383
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59089647"
---
# <a name="listeners-element-for-source"></a><span data-ttu-id="96b38-102">\<ouvintes > elemento para \<origem ></span><span class="sxs-lookup"><span data-stu-id="96b38-102">\<listeners> Element for \<source></span></span>
<span data-ttu-id="96b38-103">Adiciona ou remove os ouvintes na <xref:System.Diagnostics.TraceSource.Listeners%2A> coleção para um <xref:System.Diagnostics.TraceSource>.</span><span class="sxs-lookup"><span data-stu-id="96b38-103">Adds or removes listeners in the <xref:System.Diagnostics.TraceSource.Listeners%2A> collection for a <xref:System.Diagnostics.TraceSource>.</span></span> <span data-ttu-id="96b38-104">Um ouvinte direciona a saída de rastreamento para um destino apropriado, como um log, a janela ou o arquivo de texto.</span><span class="sxs-lookup"><span data-stu-id="96b38-104">A listener directs the tracing output to an appropriate target, such as a log, window, or text file.</span></span>  
  
 <span data-ttu-id="96b38-105">\<configuration></span><span class="sxs-lookup"><span data-stu-id="96b38-105">\<configuration></span></span>  
<span data-ttu-id="96b38-106">\<system.diagnostics></span><span class="sxs-lookup"><span data-stu-id="96b38-106">\<system.diagnostics></span></span>  
<span data-ttu-id="96b38-107">\<sources></span><span class="sxs-lookup"><span data-stu-id="96b38-107">\<sources></span></span>  
<span data-ttu-id="96b38-108">\<origem ></span><span class="sxs-lookup"><span data-stu-id="96b38-108">\<source></span></span>  
<span data-ttu-id="96b38-109">\<ouvintes > elemento</span><span class="sxs-lookup"><span data-stu-id="96b38-109">\<listeners> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96b38-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="96b38-110">Syntax</span></span>  
  
```xml  
<listeners>   
  <add>...</add>  
  <remove ... />  
  <clear/>  
</listeners>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="96b38-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="96b38-111">Attributes and Elements</span></span>  
 <span data-ttu-id="96b38-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="96b38-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="96b38-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="96b38-113">Attributes</span></span>  
 <span data-ttu-id="96b38-114">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="96b38-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="96b38-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="96b38-115">Child Elements</span></span>  
  
|<span data-ttu-id="96b38-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="96b38-116">Element</span></span>|<span data-ttu-id="96b38-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="96b38-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="96b38-118">\<add></span><span class="sxs-lookup"><span data-stu-id="96b38-118">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-listeners-for-source.md)|<span data-ttu-id="96b38-119">Adiciona um ouvinte na coleção `Listeners`.</span><span class="sxs-lookup"><span data-stu-id="96b38-119">Adds a listener to the `Listeners` collection.</span></span>|  
|[<span data-ttu-id="96b38-120">\<remove></span><span class="sxs-lookup"><span data-stu-id="96b38-120">\<remove></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/remove-element-for-listeners-for-source.md)|<span data-ttu-id="96b38-121">Remove um ouvinte do `Listeners` coleção.</span><span class="sxs-lookup"><span data-stu-id="96b38-121">Removes a listener from the `Listeners` collection.</span></span>|  
|[<span data-ttu-id="96b38-122">\<clear></span><span class="sxs-lookup"><span data-stu-id="96b38-122">\<clear></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/clear-element-for-listeners-for-source.md)|<span data-ttu-id="96b38-123">Limpa a coleção `Listeners` de uma origem de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="96b38-123">Clears the `Listeners` collection for a trace source.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="96b38-124">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="96b38-124">Parent Elements</span></span>  
  
|<span data-ttu-id="96b38-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="96b38-125">Element</span></span>|<span data-ttu-id="96b38-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="96b38-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="96b38-127">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="96b38-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="96b38-128">Especifica os ouvintes de rastreamento que coletam, armazenam e roteiam mensagens e o nível em que uma opção de rastreamento é definida.</span><span class="sxs-lookup"><span data-stu-id="96b38-128">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="96b38-129">Contém as origens de rastreamento que iniciam as mensagens de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="96b38-129">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="96b38-130">Especifica uma origem de rastreamento que inicia as mensagens de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="96b38-130">Specifies a trace source that initiates tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="96b38-131">Comentários</span><span class="sxs-lookup"><span data-stu-id="96b38-131">Remarks</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="96b38-132">Arquivo de Configuração</span><span class="sxs-lookup"><span data-stu-id="96b38-132">Configuration File</span></span>  
 <span data-ttu-id="96b38-133">Esse elemento pode ser usado no arquivo de configuração de máquina (Machine. config) e o arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="96b38-133">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="96b38-134">Exemplo</span><span class="sxs-lookup"><span data-stu-id="96b38-134">Example</span></span>  
 <span data-ttu-id="96b38-135">O exemplo a seguir mostra como usar o `<listeners>` elemento para adicionar um ouvinte de rastreamento do console para o `mySource` origem e remover o ouvinte de rastreamento padrão.</span><span class="sxs-lookup"><span data-stu-id="96b38-135">The following example shows how to use the `<listeners>` element to add a console trace listener to the `mySource` source and to remove the default trace listener.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="96b38-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="96b38-136">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="96b38-137">Esquema de configurações de rastreamento e depuração</span><span class="sxs-lookup"><span data-stu-id="96b38-137">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
- [<span data-ttu-id="96b38-138">Ouvintes de rastreamento</span><span class="sxs-lookup"><span data-stu-id="96b38-138">Trace Listeners</span></span>](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
