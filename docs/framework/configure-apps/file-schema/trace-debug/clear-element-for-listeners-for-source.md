---
title: Elemento <clear> para <listeners> para <source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/clear
helpviewer_keywords:
- <clear> element for <listeners> for <source>
- clear element for <listeners> for <source>
ms.assetid: 76796bb2-9c0b-4526-8135-8bf18b16d8d9
ms.openlocfilehash: 05c20040ef59f4dee6b15bbe0b0369281b532754
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697181"
---
# <a name="clear-element-for-listeners-for-source"></a><span data-ttu-id="55659-102">\<clear > elemento para > \<listeners para \<source ></span><span class="sxs-lookup"><span data-stu-id="55659-102">\<clear> Element for \<listeners> for \<source></span></span>
<span data-ttu-id="55659-103">Limpa a coleção `Listeners` de uma origem de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="55659-103">Clears the `Listeners` collection for a trace source.</span></span>  
  
[<span data-ttu-id="55659-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="55659-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="55659-105">&nbsp; @ no__t-1[ **\<System. Diagnostics >** ](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="55659-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>  
<span data-ttu-id="55659-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<sources >** ](sources-element.md)</span><span class="sxs-lookup"><span data-stu-id="55659-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)</span></span>  
<span data-ttu-id="55659-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5[ **\<source >** ](source-element.md)</span><span class="sxs-lookup"><span data-stu-id="55659-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<source>**](source-element.md)</span></span>  
<span data-ttu-id="55659-108">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 @ no__t-7[ **&nbsp;0listeners >** ](listeners-element-for-source.md)</span><span class="sxs-lookup"><span data-stu-id="55659-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-source.md)</span></span>  
<span data-ttu-id="55659-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<clear>**</span><span class="sxs-lookup"><span data-stu-id="55659-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55659-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="55659-110">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="55659-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="55659-111">Attributes and Elements</span></span>  
 <span data-ttu-id="55659-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="55659-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="55659-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="55659-113">Attributes</span></span>  
 <span data-ttu-id="55659-114">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="55659-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="55659-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="55659-115">Child Elements</span></span>  
 <span data-ttu-id="55659-116">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="55659-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="55659-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="55659-117">Parent Elements</span></span>  
  
|<span data-ttu-id="55659-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="55659-118">Element</span></span>|<span data-ttu-id="55659-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="55659-119">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="55659-120">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="55659-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="55659-121">Especifica os ouvintes de rastreamento que coletam, armazenam e roteiam mensagens e o nível em que uma opção de rastreamento é definida.</span><span class="sxs-lookup"><span data-stu-id="55659-121">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="55659-122">Contém as origens de rastreamento que iniciam as mensagens de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="55659-122">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="55659-123">Especifica uma origem de rastreamento que inicia as mensagens de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="55659-123">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="55659-124">Especifica os ouvintes que coletam, armazenam e roteiam mensagens.</span><span class="sxs-lookup"><span data-stu-id="55659-124">Specifies listeners that collect, store, and route messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="55659-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="55659-125">Remarks</span></span>  
 <span data-ttu-id="55659-126">O elemento `<clear>` remove todos os ouvintes da coleção `Listeners` para uma origem de rastreamento, incluindo o <xref:System.Diagnostics.DefaultTraceListener>.</span><span class="sxs-lookup"><span data-stu-id="55659-126">The `<clear>` element removes all listeners from the `Listeners` collection for a trace source, including the <xref:System.Diagnostics.DefaultTraceListener>.</span></span> <span data-ttu-id="55659-127">Você pode usar o elemento `<clear>` antes de usar o elemento `<add>` para ter certeza de que não há outros ouvintes ativos na coleção.</span><span class="sxs-lookup"><span data-stu-id="55659-127">You can use the `<clear>` element before using the `<add>` element to be certain there are no other active listeners in the collection.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="55659-128">Arquivo de Configuração</span><span class="sxs-lookup"><span data-stu-id="55659-128">Configuration File</span></span>  
 <span data-ttu-id="55659-129">Esse elemento pode ser usado no arquivo de configuração da máquina (Machine. config) e no arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="55659-129">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="55659-130">Exemplo</span><span class="sxs-lookup"><span data-stu-id="55659-130">Example</span></span>  
 <span data-ttu-id="55659-131">O exemplo a seguir mostra como usar o elemento `<clear>` antes de usar os elementos `<add>` para adicionar os ouvintes `console` e `textListener` à coleção `Listeners` para a fonte de rastreamento `TraceSourceApp`.</span><span class="sxs-lookup"><span data-stu-id="55659-131">The following example shows how to use the `<clear>` element before using the `<add>` elements to add the listeners `console` and `textListener` to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="55659-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="55659-132">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="55659-133">Esquema de configurações de rastreamento e depuração</span><span class="sxs-lookup"><span data-stu-id="55659-133">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="55659-134">Ouvintes de rastreamento</span><span class="sxs-lookup"><span data-stu-id="55659-134">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
