---
title: Elemento <clear> para <listeners> para <trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/clear
helpviewer_keywords:
- clear element for <listeners> for <trace>
- <clear> element for <listeners> for <trace>
ms.assetid: b44732a8-271f-4a06-ba9e-fe3298d6f192
ms.openlocfilehash: 0361580724351f8f42d058d5e20354e3335bac2f
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699375"
---
# <a name="clear-element-for-listeners-for-trace"></a><span data-ttu-id="78660-102">\<clear > elemento para > \<listeners para \<trace ></span><span class="sxs-lookup"><span data-stu-id="78660-102">\<clear> Element for \<listeners> for \<trace></span></span>
<span data-ttu-id="78660-103">Limpa a coleção `Listeners` do rastreamento.</span><span class="sxs-lookup"><span data-stu-id="78660-103">Clears the `Listeners` collection for trace.</span></span>  
  
[<span data-ttu-id="78660-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="78660-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="78660-105">&nbsp; @ no__t-1[ **\<System. Diagnostics >** ](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="78660-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>  
<span data-ttu-id="78660-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<trace >** ](trace-element.md)</span><span class="sxs-lookup"><span data-stu-id="78660-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<trace>**](trace-element.md)</span></span>  
<span data-ttu-id="78660-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5[ **\<listeners >** ](listeners-element-for-trace.md)</span><span class="sxs-lookup"><span data-stu-id="78660-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-trace.md)</span></span>  
<span data-ttu-id="78660-108">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 @ no__t-7 **\<clear >**</span><span class="sxs-lookup"><span data-stu-id="78660-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78660-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="78660-109">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="78660-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="78660-110">Attributes and Elements</span></span>  
 <span data-ttu-id="78660-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="78660-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="78660-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="78660-112">Attributes</span></span>  
 <span data-ttu-id="78660-113">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="78660-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="78660-114">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="78660-114">Child Elements</span></span>  
 <span data-ttu-id="78660-115">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="78660-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="78660-116">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="78660-116">Parent Elements</span></span>  
  
|<span data-ttu-id="78660-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="78660-117">Element</span></span>|<span data-ttu-id="78660-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="78660-118">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="78660-119">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="78660-119">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="78660-120">Especifica os ouvintes de rastreamento que coletam, armazenam e roteiam mensagens e o nível em que uma opção de rastreamento é definida.</span><span class="sxs-lookup"><span data-stu-id="78660-120">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`trace`|<span data-ttu-id="78660-121">Contém os ouvintes que coletam, armazenam e roteiam mensagens de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="78660-121">Contains listeners that collect, store, and route tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="78660-122">Contém ouvintes que coletam, armazenam e roteiam mensagens.</span><span class="sxs-lookup"><span data-stu-id="78660-122">Contains listeners that collect, store, and route messages.</span></span> <span data-ttu-id="78660-123">Os ouvintes direcionam a saída de rastreamento para um destino apropriado.</span><span class="sxs-lookup"><span data-stu-id="78660-123">Listeners direct the tracing output to an appropriate target.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="78660-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="78660-124">Remarks</span></span>  
 <span data-ttu-id="78660-125">O elemento `<clear>` remove todos os ouvintes da coleção `Listeners` para rastreamento.</span><span class="sxs-lookup"><span data-stu-id="78660-125">The `<clear>` element removes all listeners from the `Listeners` collection for trace.</span></span> <span data-ttu-id="78660-126">Você pode usar o elemento `<clear>` antes de usar o elemento `<add>` para ter certeza de que não há outros ouvintes ativos na coleção.</span><span class="sxs-lookup"><span data-stu-id="78660-126">You can use the `<clear>` element before using the `<add>` element to be certain there are no other active listeners in the collection.</span></span>  
  
 <span data-ttu-id="78660-127">Você pode limpar a coleção `Listeners` programaticamente chamando o método <xref:System.Diagnostics.TraceListenerCollection.Clear%2A> na propriedade <xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=nameWithType> (`System.Diagnostics.Trace.Listeners.Clear()`).</span><span class="sxs-lookup"><span data-stu-id="78660-127">You can clear the `Listeners` collection programmatically by calling the <xref:System.Diagnostics.TraceListenerCollection.Clear%2A> method on the <xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=nameWithType> property (`System.Diagnostics.Trace.Listeners.Clear()`).</span></span>  
  
 <span data-ttu-id="78660-128">Esse elemento pode ser usado no arquivo de configuração da máquina (Machine. config) e no arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="78660-128">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="78660-129">O elemento `<clear>` remove o <xref:System.Diagnostics.DefaultTraceListener> da coleção `Listeners`, alterando o comportamento dos métodos <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType> e <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="78660-129">The `<clear>` element removes the <xref:System.Diagnostics.DefaultTraceListener> from the `Listeners` collection, altering the behavior of the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>, and <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="78660-130">Chamar um método `Assert` ou `Fail` normalmente resulta na exibição de uma caixa de mensagem.</span><span class="sxs-lookup"><span data-stu-id="78660-130">Calling an `Assert` or `Fail` method normally results in the display of a message box.</span></span> <span data-ttu-id="78660-131">No entanto, a caixa de mensagem não será exibida se o <xref:System.Diagnostics.DefaultTraceListener> não estiver na coleção `Listeners`.</span><span class="sxs-lookup"><span data-stu-id="78660-131">However, the message box is not displayed if the <xref:System.Diagnostics.DefaultTraceListener> is not in the `Listeners` collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="78660-132">Exemplo</span><span class="sxs-lookup"><span data-stu-id="78660-132">Example</span></span>  
 <span data-ttu-id="78660-133">O exemplo a seguir mostra como usar o elemento `<clear>` antes de usar o elemento `<add>` para adicionar o ouvinte `console` à coleção `Listeners` para rastreamento.</span><span class="sxs-lookup"><span data-stu-id="78660-133">The following example shows how to use the `<clear>` element before using the `<add>` element to add the listener `console` to the `Listeners` collection for trace.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <trace autoflush="false" indentsize="4">  
      <listeners>  
        <clear/>  
        <add name="console"   
          type="System.Diagnostics.ConsoleTraceListener" >  
          <filter type="System.Diagnostics.EventTypeFilter"   
            initializeData="Error" />  
        </add>  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration>   
```  
  
## <a name="see-also"></a><span data-ttu-id="78660-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="78660-134">See also</span></span>

- <xref:System.Diagnostics.Trace.Listeners%2A>
- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.Debug>
- <xref:System.Diagnostics.TraceSource>
- [<span data-ttu-id="78660-135">Esquema de configurações de rastreamento e depuração</span><span class="sxs-lookup"><span data-stu-id="78660-135">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="78660-136">\<remove></span><span class="sxs-lookup"><span data-stu-id="78660-136">\<remove></span></span>](remove-element-for-listeners-for-trace.md)
- [<span data-ttu-id="78660-137">Ouvintes de rastreamento</span><span class="sxs-lookup"><span data-stu-id="78660-137">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
