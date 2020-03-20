---
title: <clear>Elemento <listeners> para para<source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/clear
helpviewer_keywords:
- <clear> element for <listeners> for <source>
- clear element for <listeners> for <source>
ms.assetid: 76796bb2-9c0b-4526-8135-8bf18b16d8d9
ms.openlocfilehash: 7f9ddd93d27c3619119702c82c9e8752dab1af7b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153575"
---
# <a name="clear-element-for-listeners-for-source"></a><span data-ttu-id="2989e-102">\<elemento> \<claro para \<os ouvintes> para> fonte</span><span class="sxs-lookup"><span data-stu-id="2989e-102">\<clear> Element for \<listeners> for \<source></span></span>
<span data-ttu-id="2989e-103">Limpa a coleção `Listeners` de uma origem de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="2989e-103">Clears the `Listeners` collection for a trace source.</span></span>  

<span data-ttu-id="2989e-104">[**\<>de configuração**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="2989e-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="2989e-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="2989e-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>\
<span data-ttu-id="2989e-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<fontes>**](sources-element.md)</span><span class="sxs-lookup"><span data-stu-id="2989e-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)</span></span>\
<span data-ttu-id="2989e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>fonte**](source-element.md)</span><span class="sxs-lookup"><span data-stu-id="2989e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<source>**](source-element.md)</span></span>\
<span data-ttu-id="2989e-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<ouvintes>**](listeners-element-for-source.md)</span><span class="sxs-lookup"><span data-stu-id="2989e-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-source.md)</span></span>\
<span data-ttu-id="2989e-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<claro>**</span><span class="sxs-lookup"><span data-stu-id="2989e-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>

## <a name="syntax"></a><span data-ttu-id="2989e-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2989e-110">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2989e-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="2989e-111">Attributes and Elements</span></span>  
 <span data-ttu-id="2989e-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="2989e-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2989e-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="2989e-113">Attributes</span></span>  
 <span data-ttu-id="2989e-114">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="2989e-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="2989e-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="2989e-115">Child Elements</span></span>  
 <span data-ttu-id="2989e-116">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="2989e-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2989e-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="2989e-117">Parent Elements</span></span>  
  
|<span data-ttu-id="2989e-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="2989e-118">Element</span></span>|<span data-ttu-id="2989e-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="2989e-119">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="2989e-120">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2989e-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="2989e-121">Especifica os ouvintes de rastreamento que coletam, armazenam e roteiam mensagens e o nível em que uma opção de rastreamento é definida.</span><span class="sxs-lookup"><span data-stu-id="2989e-121">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="2989e-122">Contém as origens de rastreamento que iniciam as mensagens de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="2989e-122">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="2989e-123">Especifica uma origem de rastreamento que inicia as mensagens de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="2989e-123">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="2989e-124">Especifica os ouvintes que coletam, armazenam e encaminham mensagens.</span><span class="sxs-lookup"><span data-stu-id="2989e-124">Specifies listeners that collect, store, and route messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2989e-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="2989e-125">Remarks</span></span>  
 <span data-ttu-id="2989e-126">O `<clear>` elemento remove todos `Listeners` os ouvintes da coleção <xref:System.Diagnostics.DefaultTraceListener>para uma fonte de rastreamento, incluindo o .</span><span class="sxs-lookup"><span data-stu-id="2989e-126">The `<clear>` element removes all listeners from the `Listeners` collection for a trace source, including the <xref:System.Diagnostics.DefaultTraceListener>.</span></span> <span data-ttu-id="2989e-127">Você pode `<clear>` usar o `<add>` elemento antes de usar o elemento para ter certeza de que não há outros ouvintes ativos na coleção.</span><span class="sxs-lookup"><span data-stu-id="2989e-127">You can use the `<clear>` element before using the `<add>` element to be certain there are no other active listeners in the collection.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="2989e-128">Arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="2989e-128">Configuration File</span></span>  
 <span data-ttu-id="2989e-129">Esse elemento pode ser usado no arquivo de configuração da máquina (Machine.config) e no arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2989e-129">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2989e-130">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2989e-130">Example</span></span>  
 <span data-ttu-id="2989e-131">O exemplo a seguir `<clear>` mostra como `<add>` usar o elemento `console` `textListener` antes `Listeners` de usar os `TraceSourceApp`elementos para adicionar os ouvintes e à coleção para a fonte de rastreamento .</span><span class="sxs-lookup"><span data-stu-id="2989e-131">The following example shows how to use the `<clear>` element before using the `<add>` elements to add the listeners `console` and `textListener` to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2989e-132">Confira também</span><span class="sxs-lookup"><span data-stu-id="2989e-132">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="2989e-133">Esquema de configurações de rastreamento e depuração</span><span class="sxs-lookup"><span data-stu-id="2989e-133">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="2989e-134">Ouvintes de rastreamento</span><span class="sxs-lookup"><span data-stu-id="2989e-134">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
