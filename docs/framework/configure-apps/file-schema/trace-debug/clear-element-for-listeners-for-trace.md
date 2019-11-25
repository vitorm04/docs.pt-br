---
title: <clear> elemento para <listeners> para <trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/clear
helpviewer_keywords:
- clear element for <listeners> for <trace>
- <clear> element for <listeners> for <trace>
ms.assetid: b44732a8-271f-4a06-ba9e-fe3298d6f192
ms.openlocfilehash: 049b8e7ed17633c0f34b062915afaf719927dad6
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088923"
---
# <a name="clear-element-for-listeners-for-trace"></a><span data-ttu-id="4c7b4-102">\<limpar > elemento para \<ouvintes > para \<rastreamento ></span><span class="sxs-lookup"><span data-stu-id="4c7b4-102">\<clear> Element for \<listeners> for \<trace></span></span>
<span data-ttu-id="4c7b4-103">Limpa a coleção `Listeners` do rastreamento.</span><span class="sxs-lookup"><span data-stu-id="4c7b4-103">Clears the `Listeners` collection for trace.</span></span>  

<span data-ttu-id="4c7b4-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="4c7b4-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="4c7b4-105">&nbsp;&nbsp;[ **\<System. diagnostics >** ](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="4c7b4-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>\
<span data-ttu-id="4c7b4-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Trace**](trace-element.md) ></span><span class="sxs-lookup"><span data-stu-id="4c7b4-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<trace>**](trace-element.md)</span></span>\
<span data-ttu-id="4c7b4-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<[**ouvintes >** ](listeners-element-for-trace.md)</span><span class="sxs-lookup"><span data-stu-id="4c7b4-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-trace.md)</span></span>\
<span data-ttu-id="4c7b4-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<desmarque >**</span><span class="sxs-lookup"><span data-stu-id="4c7b4-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>

## <a name="syntax"></a><span data-ttu-id="4c7b4-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4c7b4-109">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4c7b4-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="4c7b4-110">Attributes and Elements</span></span>  
 <span data-ttu-id="4c7b4-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="4c7b4-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4c7b4-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="4c7b4-112">Attributes</span></span>  
 <span data-ttu-id="4c7b4-113">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="4c7b4-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="4c7b4-114">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="4c7b4-114">Child Elements</span></span>  
 <span data-ttu-id="4c7b4-115">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="4c7b4-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4c7b4-116">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="4c7b4-116">Parent Elements</span></span>  
  
|<span data-ttu-id="4c7b4-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="4c7b4-117">Element</span></span>|<span data-ttu-id="4c7b4-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="4c7b4-118">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="4c7b4-119">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4c7b4-119">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="4c7b4-120">Especifica os ouvintes de rastreamento que coletam, armazenam e roteiam mensagens e o nível em que uma opção de rastreamento é definida.</span><span class="sxs-lookup"><span data-stu-id="4c7b4-120">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`trace`|<span data-ttu-id="4c7b4-121">Contém os ouvintes que coletam, armazenam e roteiam mensagens de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="4c7b4-121">Contains listeners that collect, store, and route tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="4c7b4-122">Contém ouvintes que coletam, armazenam e roteiam mensagens.</span><span class="sxs-lookup"><span data-stu-id="4c7b4-122">Contains listeners that collect, store, and route messages.</span></span> <span data-ttu-id="4c7b4-123">Os ouvintes direcionam a saída de rastreamento para um destino apropriado.</span><span class="sxs-lookup"><span data-stu-id="4c7b4-123">Listeners direct the tracing output to an appropriate target.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4c7b4-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="4c7b4-124">Remarks</span></span>  
 <span data-ttu-id="4c7b4-125">O elemento `<clear>` remove todos os ouvintes da coleção de `Listeners` para o rastreamento.</span><span class="sxs-lookup"><span data-stu-id="4c7b4-125">The `<clear>` element removes all listeners from the `Listeners` collection for trace.</span></span> <span data-ttu-id="4c7b4-126">Você pode usar o elemento `<clear>` antes de usar o elemento `<add>` para ter certeza de que não há outros ouvintes ativos na coleção.</span><span class="sxs-lookup"><span data-stu-id="4c7b4-126">You can use the `<clear>` element before using the `<add>` element to be certain there are no other active listeners in the collection.</span></span>  
  
 <span data-ttu-id="4c7b4-127">Você pode limpar a coleção de `Listeners` programaticamente chamando o método <xref:System.Diagnostics.TraceListenerCollection.Clear%2A> na propriedade <xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=nameWithType> (`System.Diagnostics.Trace.Listeners.Clear()`).</span><span class="sxs-lookup"><span data-stu-id="4c7b4-127">You can clear the `Listeners` collection programmatically by calling the <xref:System.Diagnostics.TraceListenerCollection.Clear%2A> method on the <xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=nameWithType> property (`System.Diagnostics.Trace.Listeners.Clear()`).</span></span>  
  
 <span data-ttu-id="4c7b4-128">Esse elemento pode ser usado no arquivo de configuração da máquina (Machine. config) e no arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4c7b4-128">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4c7b4-129">O elemento `<clear>` remove o <xref:System.Diagnostics.DefaultTraceListener> da coleção de `Listeners`, alterando o comportamento dos métodos <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>e <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4c7b4-129">The `<clear>` element removes the <xref:System.Diagnostics.DefaultTraceListener> from the `Listeners` collection, altering the behavior of the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>, and <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="4c7b4-130">Chamar um método `Assert` ou `Fail` normalmente resulta na exibição de uma caixa de mensagem.</span><span class="sxs-lookup"><span data-stu-id="4c7b4-130">Calling an `Assert` or `Fail` method normally results in the display of a message box.</span></span> <span data-ttu-id="4c7b4-131">No entanto, a caixa de mensagem não será exibida se o <xref:System.Diagnostics.DefaultTraceListener> não estiver na coleção de `Listeners`.</span><span class="sxs-lookup"><span data-stu-id="4c7b4-131">However, the message box is not displayed if the <xref:System.Diagnostics.DefaultTraceListener> is not in the `Listeners` collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4c7b4-132">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4c7b4-132">Example</span></span>  
 <span data-ttu-id="4c7b4-133">O exemplo a seguir mostra como usar o elemento `<clear>` antes de usar o elemento `<add>` para adicionar o `console` do ouvinte à coleção de `Listeners` para rastreamento.</span><span class="sxs-lookup"><span data-stu-id="4c7b4-133">The following example shows how to use the `<clear>` element before using the `<add>` element to add the listener `console` to the `Listeners` collection for trace.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4c7b4-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4c7b4-134">See also</span></span>

- <xref:System.Diagnostics.Trace.Listeners%2A>
- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.Debug>
- <xref:System.Diagnostics.TraceSource>
- [<span data-ttu-id="4c7b4-135">Esquema de configurações de rastreamento e depuração</span><span class="sxs-lookup"><span data-stu-id="4c7b4-135">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="4c7b4-136">\<remove></span><span class="sxs-lookup"><span data-stu-id="4c7b4-136">\<remove></span></span>](remove-element-for-listeners-for-trace.md)
- [<span data-ttu-id="4c7b4-137">Ouvintes de rastreamento</span><span class="sxs-lookup"><span data-stu-id="4c7b4-137">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
