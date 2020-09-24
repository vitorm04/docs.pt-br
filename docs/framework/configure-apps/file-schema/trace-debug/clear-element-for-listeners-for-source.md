---
title: <clear> Elemento para <listeners> para <source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/clear
helpviewer_keywords:
- <clear> element for <listeners> for <source>
- clear element for <listeners> for <source>
ms.assetid: 76796bb2-9c0b-4526-8135-8bf18b16d8d9
ms.openlocfilehash: d3e76496c82b508feabf8a46cf7bce7e3d54e8cf
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91149277"
---
# <a name="clear-element-for-listeners-for-source"></a><span data-ttu-id="3db33-102">\<clear> Elemento para \<listeners> para \<source></span><span class="sxs-lookup"><span data-stu-id="3db33-102">\<clear> Element for \<listeners> for \<source></span></span>

<span data-ttu-id="3db33-103">Limpa a coleção `Listeners` de uma origem de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="3db33-103">Clears the `Listeners` collection for a trace source.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<source>**](source-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-source.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**

## <a name="syntax"></a><span data-ttu-id="3db33-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="3db33-104">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3db33-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="3db33-105">Attributes and Elements</span></span>  

 <span data-ttu-id="3db33-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="3db33-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3db33-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="3db33-107">Attributes</span></span>  

 <span data-ttu-id="3db33-108">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="3db33-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="3db33-109">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="3db33-109">Child Elements</span></span>  

 <span data-ttu-id="3db33-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="3db33-110">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3db33-111">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="3db33-111">Parent Elements</span></span>  
  
|<span data-ttu-id="3db33-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="3db33-112">Element</span></span>|<span data-ttu-id="3db33-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="3db33-113">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="3db33-114">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3db33-114">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="3db33-115">Especifica os ouvintes de rastreamento que coletam, armazenam e roteiam mensagens e o nível em que uma opção de rastreamento é definida.</span><span class="sxs-lookup"><span data-stu-id="3db33-115">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="3db33-116">Contém as origens de rastreamento que iniciam as mensagens de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="3db33-116">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="3db33-117">Especifica uma origem de rastreamento que inicia as mensagens de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="3db33-117">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="3db33-118">Especifica os ouvintes que coletam, armazenam e roteiam mensagens.</span><span class="sxs-lookup"><span data-stu-id="3db33-118">Specifies listeners that collect, store, and route messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3db33-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="3db33-119">Remarks</span></span>  

 <span data-ttu-id="3db33-120">O `<clear>` elemento remove todos os ouvintes da `Listeners` coleção para uma origem de rastreamento, incluindo o <xref:System.Diagnostics.DefaultTraceListener> .</span><span class="sxs-lookup"><span data-stu-id="3db33-120">The `<clear>` element removes all listeners from the `Listeners` collection for a trace source, including the <xref:System.Diagnostics.DefaultTraceListener>.</span></span> <span data-ttu-id="3db33-121">Você pode usar o `<clear>` elemento antes de usar o `<add>` elemento para ter certeza de que não há outros ouvintes ativos na coleção.</span><span class="sxs-lookup"><span data-stu-id="3db33-121">You can use the `<clear>` element before using the `<add>` element to be certain there are no other active listeners in the collection.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="3db33-122">Arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="3db33-122">Configuration File</span></span>  

 <span data-ttu-id="3db33-123">Esse elemento pode ser usado no arquivo de configuração da máquina (Machine.config) e no arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3db33-123">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3db33-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3db33-124">Example</span></span>  

 <span data-ttu-id="3db33-125">O exemplo a seguir mostra como usar o `<clear>` elemento antes de usar os `<add>` elementos para adicionar os ouvintes `console` e a `textListener` `Listeners` coleção para a origem do rastreamento `TraceSourceApp` .</span><span class="sxs-lookup"><span data-stu-id="3db33-125">The following example shows how to use the `<clear>` element before using the `<add>` elements to add the listeners `console` and `textListener` to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3db33-126">Confira também</span><span class="sxs-lookup"><span data-stu-id="3db33-126">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="3db33-127">Esquema de configurações de rastreamento e depuração</span><span class="sxs-lookup"><span data-stu-id="3db33-127">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="3db33-128">Ouvintes de rastreamento</span><span class="sxs-lookup"><span data-stu-id="3db33-128">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
