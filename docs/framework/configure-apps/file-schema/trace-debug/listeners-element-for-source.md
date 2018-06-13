---
title: '&lt;ouvintes de&gt; elemento para &lt;fonte&gt;'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners
helpviewer_keywords:
- listeners element for <source>
- <listeners> element for <source>
ms.assetid: a2991f43-b4d3-4614-a8e7-da392de9697f
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: a711b8d6bfd5b6d73d3240cb84810841bdc5a2b6
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32746833"
---
# <a name="ltlistenersgt-element-for-ltsourcegt"></a><span data-ttu-id="d26b6-102">&lt;ouvintes de&gt; elemento para &lt;fonte&gt;</span><span class="sxs-lookup"><span data-stu-id="d26b6-102">&lt;listeners&gt; Element for &lt;source&gt;</span></span>
<span data-ttu-id="d26b6-103">Adiciona ou remove ouvintes no <xref:System.Diagnostics.TraceSource.Listeners%2A> coleção para um <xref:System.Diagnostics.TraceSource>.</span><span class="sxs-lookup"><span data-stu-id="d26b6-103">Adds or removes listeners in the <xref:System.Diagnostics.TraceSource.Listeners%2A> collection for a <xref:System.Diagnostics.TraceSource>.</span></span> <span data-ttu-id="d26b6-104">Um ouvinte direciona a saída de rastreamento para um destino apropriado, como um log, uma janela ou um arquivo de texto.</span><span class="sxs-lookup"><span data-stu-id="d26b6-104">A listener directs the tracing output to an appropriate target, such as a log, window, or text file.</span></span>  
  
 <span data-ttu-id="d26b6-105">\<configuration></span><span class="sxs-lookup"><span data-stu-id="d26b6-105">\<configuration></span></span>  
<span data-ttu-id="d26b6-106">\<System. Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="d26b6-106">\<system.diagnostics></span></span>  
<span data-ttu-id="d26b6-107">\<fontes ></span><span class="sxs-lookup"><span data-stu-id="d26b6-107">\<sources></span></span>  
<span data-ttu-id="d26b6-108">\<origem ></span><span class="sxs-lookup"><span data-stu-id="d26b6-108">\<source></span></span>  
<span data-ttu-id="d26b6-109">\<ouvintes > elemento</span><span class="sxs-lookup"><span data-stu-id="d26b6-109">\<listeners> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d26b6-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d26b6-110">Syntax</span></span>  
  
```xml  
<listeners>   
  <add>...</add>  
  <remove ... />  
  <clear/>  
</listeners>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d26b6-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="d26b6-111">Attributes and Elements</span></span>  
 <span data-ttu-id="d26b6-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="d26b6-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d26b6-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="d26b6-113">Attributes</span></span>  
 <span data-ttu-id="d26b6-114">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="d26b6-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d26b6-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="d26b6-115">Child Elements</span></span>  
  
|<span data-ttu-id="d26b6-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="d26b6-116">Element</span></span>|<span data-ttu-id="d26b6-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="d26b6-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d26b6-118">\<add></span><span class="sxs-lookup"><span data-stu-id="d26b6-118">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-listeners-for-source.md)|<span data-ttu-id="d26b6-119">Adiciona um ouvinte na coleção `Listeners`.</span><span class="sxs-lookup"><span data-stu-id="d26b6-119">Adds a listener to the `Listeners` collection.</span></span>|  
|[<span data-ttu-id="d26b6-120">\<remove></span><span class="sxs-lookup"><span data-stu-id="d26b6-120">\<remove></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/remove-element-for-listeners-for-source.md)|<span data-ttu-id="d26b6-121">Remove um ouvinte do `Listeners` coleção.</span><span class="sxs-lookup"><span data-stu-id="d26b6-121">Removes a listener from the `Listeners` collection.</span></span>|  
|[<span data-ttu-id="d26b6-122">\<clear></span><span class="sxs-lookup"><span data-stu-id="d26b6-122">\<clear></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/clear-element-for-listeners-for-source.md)|<span data-ttu-id="d26b6-123">Limpa a coleção `Listeners` de uma origem de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="d26b6-123">Clears the `Listeners` collection for a trace source.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d26b6-124">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="d26b6-124">Parent Elements</span></span>  
  
|<span data-ttu-id="d26b6-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="d26b6-125">Element</span></span>|<span data-ttu-id="d26b6-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="d26b6-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="d26b6-127">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d26b6-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="d26b6-128">Especifica os ouvintes de rastreamento que coletam, armazenam e roteiam mensagens e o nível em que uma opção de rastreamento é definida.</span><span class="sxs-lookup"><span data-stu-id="d26b6-128">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="d26b6-129">Contém as origens de rastreamento que iniciam as mensagens de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="d26b6-129">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="d26b6-130">Especifica uma origem de rastreamento que inicia as mensagens de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="d26b6-130">Specifies a trace source that initiates tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d26b6-131">Comentários</span><span class="sxs-lookup"><span data-stu-id="d26b6-131">Remarks</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="d26b6-132">Arquivo de Configuração</span><span class="sxs-lookup"><span data-stu-id="d26b6-132">Configuration File</span></span>  
 <span data-ttu-id="d26b6-133">Esse elemento pode ser usado no arquivo de configuração de máquina (Machine. config) e o arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d26b6-133">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d26b6-134">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d26b6-134">Example</span></span>  
 <span data-ttu-id="d26b6-135">O exemplo a seguir mostra como usar o `<listeners>` elemento para adicionar um ouvinte de rastreamento do console para o `mySource` origem e remover o ouvinte de rastreamento padrão.</span><span class="sxs-lookup"><span data-stu-id="d26b6-135">The following example shows how to use the `<listeners>` element to add a console trace listener to the `mySource` source and to remove the default trace listener.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d26b6-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d26b6-136">See Also</span></span>  
 <xref:System.Diagnostics.TraceListener>  
 [<span data-ttu-id="d26b6-137">Esquema de configurações de rastreamento e depuração</span><span class="sxs-lookup"><span data-stu-id="d26b6-137">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)  
 [<span data-ttu-id="d26b6-138">Ouvintes de rastreamento</span><span class="sxs-lookup"><span data-stu-id="d26b6-138">Trace Listeners</span></span>](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
