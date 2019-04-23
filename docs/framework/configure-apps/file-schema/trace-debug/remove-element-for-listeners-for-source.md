---
title: <remove> Elemento para <listeners> para <source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/remove
helpviewer_keywords:
- remove element for <listeners> for <source>
- <remove> element for <listeners> for <source>
ms.assetid: 3ff6b578-273d-407f-b07f-8251f1f9f5d0
ms.openlocfilehash: 4809c471deb51e0560b438b5a2c8849daad34ca0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59120127"
---
# <a name="remove-element-for-listeners-for-source"></a><span data-ttu-id="8b206-102">\<Remover > elemento para \<ouvintes > para \<origem ></span><span class="sxs-lookup"><span data-stu-id="8b206-102">\<remove> Element for \<listeners> for \<source></span></span>
<span data-ttu-id="8b206-103">Remove um ouvinte da coleção `Listeners` de uma origem de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="8b206-103">Removes a listener from the `Listeners` collection for a trace source.</span></span>  
  
 <span data-ttu-id="8b206-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="8b206-104">\<configuration></span></span>  
<span data-ttu-id="8b206-105">\<system.diagnostics></span><span class="sxs-lookup"><span data-stu-id="8b206-105">\<system.diagnostics></span></span>  
<span data-ttu-id="8b206-106">\<sources></span><span class="sxs-lookup"><span data-stu-id="8b206-106">\<sources></span></span>  
<span data-ttu-id="8b206-107">\<origem ></span><span class="sxs-lookup"><span data-stu-id="8b206-107">\<source></span></span>  
<span data-ttu-id="8b206-108">\<listeners></span><span class="sxs-lookup"><span data-stu-id="8b206-108">\<listeners></span></span>  
<span data-ttu-id="8b206-109">\<remove></span><span class="sxs-lookup"><span data-stu-id="8b206-109">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b206-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8b206-110">Syntax</span></span>  
  
```xml  
<remove name="listenerName" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8b206-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="8b206-111">Attributes and Elements</span></span>  
 <span data-ttu-id="8b206-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="8b206-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8b206-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="8b206-113">Attributes</span></span>  
  
|<span data-ttu-id="8b206-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="8b206-114">Attribute</span></span>|<span data-ttu-id="8b206-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="8b206-115">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="8b206-116">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="8b206-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="8b206-117">O nome do ouvinte para remover o `Listeners` coleção.</span><span class="sxs-lookup"><span data-stu-id="8b206-117">The name of the listener to remove from the `Listeners` collection.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8b206-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="8b206-118">Child Elements</span></span>  
 <span data-ttu-id="8b206-119">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="8b206-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8b206-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="8b206-120">Parent Elements</span></span>  
  
|<span data-ttu-id="8b206-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="8b206-121">Element</span></span>|<span data-ttu-id="8b206-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="8b206-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="8b206-123">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8b206-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="8b206-124">Especifica os ouvintes de rastreamento que coletam, armazenam e roteiam mensagens e o nível em que uma opção de rastreamento é definida.</span><span class="sxs-lookup"><span data-stu-id="8b206-124">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="8b206-125">Contém as origens de rastreamento que iniciam as mensagens de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="8b206-125">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="8b206-126">Especifica uma origem de rastreamento que inicia as mensagens de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="8b206-126">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="8b206-127">Especifica os ouvintes que coletam, armazenam e roteiam mensagens.</span><span class="sxs-lookup"><span data-stu-id="8b206-127">Specifies listeners that collect, store, and route messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8b206-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="8b206-128">Remarks</span></span>  
 <span data-ttu-id="8b206-129">O `<remove>` elemento remove um ouvinte especificado do `Listeners` coleção para uma origem de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="8b206-129">The `<remove>` element removes a specified listener from the `Listeners` collection for a trace source.</span></span>  
  
 <span data-ttu-id="8b206-130">Você pode remover um elemento a `Listeners` coleção para uma origem de rastreamento programaticamente, chamando o <xref:System.Diagnostics.TraceListenerCollection.Remove%2A> método na <xref:System.Diagnostics.TraceSource.Listeners%2A> propriedade do <xref:System.Diagnostics.TraceSource> instância.</span><span class="sxs-lookup"><span data-stu-id="8b206-130">You can remove an element from the `Listeners` collection for a trace source programmatically by calling the <xref:System.Diagnostics.TraceListenerCollection.Remove%2A> method on the <xref:System.Diagnostics.TraceSource.Listeners%2A> property of the <xref:System.Diagnostics.TraceSource> instance.</span></span>  
  
 <span data-ttu-id="8b206-131">Esse elemento pode ser usado no arquivo de configuração de máquina (Machine. config) e o arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8b206-131">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8b206-132">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8b206-132">Example</span></span>  
 <span data-ttu-id="8b206-133">O exemplo a seguir mostra como usar o `<remove>` elemento antes de usar o `<add>` elemento para adicionar o ouvinte `console` para o `Listeners` coleção para a origem de rastreamento `TraceSourceApp`.</span><span class="sxs-lookup"><span data-stu-id="8b206-133">The following example shows how to use the `<remove>` element before using the `<add>` element to add the listener `console` to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="TraceSourceApp" switchName="sourceSwitch"   
         switchType="System.Diagnostics.SourceSwitch" >  
         <listeners>  
           <remove name="Default"/>  
           <add name="console"   
             type="System.Diagnostics.ConsoleTraceListener" />  
         </listeners>  
      </source>  
    </sources>  
  </system.diagnostics>  
</configuration>   
```  
  
## <a name="see-also"></a><span data-ttu-id="8b206-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8b206-134">See also</span></span>

- <xref:System.Diagnostics.TraceSource.Listeners%2A>
- <xref:System.Diagnostics.TraceSource>
- [<span data-ttu-id="8b206-135">Esquema de configurações de rastreamento e depuração</span><span class="sxs-lookup"><span data-stu-id="8b206-135">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
- [<span data-ttu-id="8b206-136">\<clear></span><span class="sxs-lookup"><span data-stu-id="8b206-136">\<clear></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/clear-element-for-listeners-for-source.md)
- [<span data-ttu-id="8b206-137">Ouvintes de rastreamento</span><span class="sxs-lookup"><span data-stu-id="8b206-137">Trace Listeners</span></span>](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
