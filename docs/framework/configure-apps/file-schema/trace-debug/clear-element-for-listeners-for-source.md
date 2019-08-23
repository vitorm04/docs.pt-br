---
title: <clear>Elemento para <listeners> para<source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/clear
helpviewer_keywords:
- <clear> element for <listeners> for <source>
- clear element for <listeners> for <source>
ms.assetid: 76796bb2-9c0b-4526-8135-8bf18b16d8d9
ms.openlocfilehash: 768d51a74b4c31d1250d2f5d6517f760f886e0a0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920543"
---
# <a name="clear-element-for-listeners-for-source"></a><span data-ttu-id="8710f-102">\<limpar > elemento para \<ouvintes > para \<a fonte ></span><span class="sxs-lookup"><span data-stu-id="8710f-102">\<clear> Element for \<listeners> for \<source></span></span>
<span data-ttu-id="8710f-103">Limpa a coleção `Listeners` de uma origem de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="8710f-103">Clears the `Listeners` collection for a trace source.</span></span>  
  
 <span data-ttu-id="8710f-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="8710f-104">\<configuration></span></span>  
<span data-ttu-id="8710f-105">\<System. Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="8710f-105">\<system.diagnostics></span></span>  
<span data-ttu-id="8710f-106">\<fontes ></span><span class="sxs-lookup"><span data-stu-id="8710f-106">\<sources></span></span>  
<span data-ttu-id="8710f-107">\<> de origem</span><span class="sxs-lookup"><span data-stu-id="8710f-107">\<source></span></span>  
<span data-ttu-id="8710f-108">\<listeners></span><span class="sxs-lookup"><span data-stu-id="8710f-108">\<listeners></span></span>  
<span data-ttu-id="8710f-109">\<clear></span><span class="sxs-lookup"><span data-stu-id="8710f-109">\<clear></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8710f-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8710f-110">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8710f-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="8710f-111">Attributes and Elements</span></span>  
 <span data-ttu-id="8710f-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="8710f-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8710f-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="8710f-113">Attributes</span></span>  
 <span data-ttu-id="8710f-114">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="8710f-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="8710f-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="8710f-115">Child Elements</span></span>  
 <span data-ttu-id="8710f-116">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="8710f-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8710f-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="8710f-117">Parent Elements</span></span>  
  
|<span data-ttu-id="8710f-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="8710f-118">Element</span></span>|<span data-ttu-id="8710f-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="8710f-119">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="8710f-120">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8710f-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="8710f-121">Especifica os ouvintes de rastreamento que coletam, armazenam e roteiam mensagens e o nível em que uma opção de rastreamento é definida.</span><span class="sxs-lookup"><span data-stu-id="8710f-121">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="8710f-122">Contém as origens de rastreamento que iniciam as mensagens de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="8710f-122">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="8710f-123">Especifica uma origem de rastreamento que inicia as mensagens de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="8710f-123">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="8710f-124">Especifica os ouvintes que coletam, armazenam e roteiam mensagens.</span><span class="sxs-lookup"><span data-stu-id="8710f-124">Specifies listeners that collect, store, and route messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8710f-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="8710f-125">Remarks</span></span>  
 <span data-ttu-id="8710f-126">O `<clear>` elemento remove todos os ouvintes `Listeners` da coleção para uma origem de rastreamento, incluindo <xref:System.Diagnostics.DefaultTraceListener>o.</span><span class="sxs-lookup"><span data-stu-id="8710f-126">The `<clear>` element removes all listeners from the `Listeners` collection for a trace source, including the <xref:System.Diagnostics.DefaultTraceListener>.</span></span> <span data-ttu-id="8710f-127">Você pode usar o `<clear>` elemento antes de usar `<add>` o elemento para ter certeza de que não há outros ouvintes ativos na coleção.</span><span class="sxs-lookup"><span data-stu-id="8710f-127">You can use the `<clear>` element before using the `<add>` element to be certain there are no other active listeners in the collection.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="8710f-128">Arquivo de Configuração</span><span class="sxs-lookup"><span data-stu-id="8710f-128">Configuration File</span></span>  
 <span data-ttu-id="8710f-129">Esse elemento pode ser usado no arquivo de configuração da máquina (Machine. config) e no arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8710f-129">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8710f-130">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8710f-130">Example</span></span>  
 <span data-ttu-id="8710f-131">O exemplo a seguir mostra como usar o `<clear>` elemento antes de usar `<add>` os elementos `console` para adicionar os `Listeners` ouvintes `textListener` e a coleção para a origem `TraceSourceApp`do rastreamento.</span><span class="sxs-lookup"><span data-stu-id="8710f-131">The following example shows how to use the `<clear>` element before using the `<add>` elements to add the listeners `console` and `textListener` to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
       <source name="TraceSourceApp" switchName="sourceSwitch"   
         switchType="System.Diagnostics.SourceSwitch">  
        <listeners>  
          <clear/>  
          <add name="console"   
            type="System.Diagnostics.ConsoleTraceListener"/>  
          <add name="textListener"/>  
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
  
## <a name="see-also"></a><span data-ttu-id="8710f-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8710f-132">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="8710f-133">Esquema de configurações de rastreamento e depuração</span><span class="sxs-lookup"><span data-stu-id="8710f-133">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="8710f-134">Ouvintes de rastreamento</span><span class="sxs-lookup"><span data-stu-id="8710f-134">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
