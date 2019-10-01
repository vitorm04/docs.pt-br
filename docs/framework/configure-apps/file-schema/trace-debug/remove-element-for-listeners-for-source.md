---
title: Elemento <remove> para <listeners> para <source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/remove
helpviewer_keywords:
- remove element for <listeners> for <source>
- <remove> element for <listeners> for <source>
ms.assetid: 3ff6b578-273d-407f-b07f-8251f1f9f5d0
ms.openlocfilehash: 4a11308278f755ec8271477352d91d8797d105c5
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699492"
---
# <a name="remove-element-for-listeners-for-source"></a><span data-ttu-id="517df-102">\<remove > elemento para > \<listeners para \<source ></span><span class="sxs-lookup"><span data-stu-id="517df-102">\<remove> Element for \<listeners> for \<source></span></span>
<span data-ttu-id="517df-103">Remove um ouvinte da coleção `Listeners` de uma origem de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="517df-103">Removes a listener from the `Listeners` collection for a trace source.</span></span>  
  
[<span data-ttu-id="517df-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="517df-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="517df-105">&nbsp; @ no__t-1[ **\<System. Diagnostics >** ](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="517df-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>  
<span data-ttu-id="517df-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<sources >** ](sources-element.md)</span><span class="sxs-lookup"><span data-stu-id="517df-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)</span></span>  
<span data-ttu-id="517df-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5[ **\<source >** ](source-element.md)</span><span class="sxs-lookup"><span data-stu-id="517df-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<source>**](source-element.md)</span></span>  
<span data-ttu-id="517df-108">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 @ no__t-7[ **&nbsp;0listeners >** ](listeners-element-for-source.md)</span><span class="sxs-lookup"><span data-stu-id="517df-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-source.md)</span></span>  
<span data-ttu-id="517df-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<remove>**</span><span class="sxs-lookup"><span data-stu-id="517df-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="517df-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="517df-110">Syntax</span></span>  
  
```xml  
<remove name="listenerName" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="517df-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="517df-111">Attributes and Elements</span></span>  
 <span data-ttu-id="517df-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="517df-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="517df-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="517df-113">Attributes</span></span>  
  
|<span data-ttu-id="517df-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="517df-114">Attribute</span></span>|<span data-ttu-id="517df-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="517df-115">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="517df-116">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="517df-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="517df-117">O nome do ouvinte a ser removido da coleção `Listeners`.</span><span class="sxs-lookup"><span data-stu-id="517df-117">The name of the listener to remove from the `Listeners` collection.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="517df-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="517df-118">Child Elements</span></span>  
 <span data-ttu-id="517df-119">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="517df-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="517df-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="517df-120">Parent Elements</span></span>  
  
|<span data-ttu-id="517df-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="517df-121">Element</span></span>|<span data-ttu-id="517df-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="517df-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="517df-123">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="517df-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="517df-124">Especifica os ouvintes de rastreamento que coletam, armazenam e roteiam mensagens e o nível em que uma opção de rastreamento é definida.</span><span class="sxs-lookup"><span data-stu-id="517df-124">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="517df-125">Contém as origens de rastreamento que iniciam as mensagens de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="517df-125">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="517df-126">Especifica uma origem de rastreamento que inicia as mensagens de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="517df-126">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="517df-127">Especifica os ouvintes que coletam, armazenam e roteiam mensagens.</span><span class="sxs-lookup"><span data-stu-id="517df-127">Specifies listeners that collect, store, and route messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="517df-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="517df-128">Remarks</span></span>  
 <span data-ttu-id="517df-129">O elemento `<remove>` remove um ouvinte especificado da coleção `Listeners` para uma origem de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="517df-129">The `<remove>` element removes a specified listener from the `Listeners` collection for a trace source.</span></span>  
  
 <span data-ttu-id="517df-130">Você pode remover um elemento da coleção `Listeners` de uma fonte de rastreamento programaticamente chamando o método <xref:System.Diagnostics.TraceListenerCollection.Remove%2A> na propriedade <xref:System.Diagnostics.TraceSource.Listeners%2A> da instância <xref:System.Diagnostics.TraceSource>.</span><span class="sxs-lookup"><span data-stu-id="517df-130">You can remove an element from the `Listeners` collection for a trace source programmatically by calling the <xref:System.Diagnostics.TraceListenerCollection.Remove%2A> method on the <xref:System.Diagnostics.TraceSource.Listeners%2A> property of the <xref:System.Diagnostics.TraceSource> instance.</span></span>  
  
 <span data-ttu-id="517df-131">Esse elemento pode ser usado no arquivo de configuração da máquina (Machine. config) e no arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="517df-131">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="517df-132">Exemplo</span><span class="sxs-lookup"><span data-stu-id="517df-132">Example</span></span>  
 <span data-ttu-id="517df-133">O exemplo a seguir mostra como usar o elemento `<remove>` antes de usar o elemento `<add>` para adicionar o ouvinte `console` à coleção `Listeners` para a fonte de rastreamento `TraceSourceApp`.</span><span class="sxs-lookup"><span data-stu-id="517df-133">The following example shows how to use the `<remove>` element before using the `<add>` element to add the listener `console` to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="517df-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="517df-134">See also</span></span>

- <xref:System.Diagnostics.TraceSource.Listeners%2A>
- <xref:System.Diagnostics.TraceSource>
- [<span data-ttu-id="517df-135">Esquema de configurações de rastreamento e depuração</span><span class="sxs-lookup"><span data-stu-id="517df-135">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="517df-136">\<clear></span><span class="sxs-lookup"><span data-stu-id="517df-136">\<clear></span></span>](clear-element-for-listeners-for-source.md)
- [<span data-ttu-id="517df-137">Ouvintes de rastreamento</span><span class="sxs-lookup"><span data-stu-id="517df-137">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
