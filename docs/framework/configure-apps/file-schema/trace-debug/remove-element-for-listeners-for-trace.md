---
title: Elemento <remove> para <listeners> para <trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/remove
helpviewer_keywords:
- remove element
- <remove> element
ms.assetid: 9a5cd1b5-be1a-485f-8f0c-2890ad3ef3e0
ms.openlocfilehash: 56d1e56514aed98d5f3b9f7363e461af6ac68a8c
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697215"
---
# <a name="remove-element-for-listeners-for-trace"></a><span data-ttu-id="b60d9-102">\<remove > elemento para > \<listeners para \<trace ></span><span class="sxs-lookup"><span data-stu-id="b60d9-102">\<remove> Element for \<listeners> for \<trace></span></span>
<span data-ttu-id="b60d9-103">Remove um ouvinte da coleção **Listeners** .</span><span class="sxs-lookup"><span data-stu-id="b60d9-103">Removes a listener from the **Listeners** collection.</span></span>  
  
[<span data-ttu-id="b60d9-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="b60d9-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="b60d9-105">&nbsp; @ no__t-1[ **\<System. Diagnostics >** ](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="b60d9-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>  
<span data-ttu-id="b60d9-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<trace >** ](trace-element.md)</span><span class="sxs-lookup"><span data-stu-id="b60d9-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<trace>**](trace-element.md)</span></span>  
<span data-ttu-id="b60d9-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5[ **\<listeners >** ](listeners-element-for-trace.md)</span><span class="sxs-lookup"><span data-stu-id="b60d9-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-trace.md)</span></span>  
<span data-ttu-id="b60d9-108">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 @ no__t-7 **\<remove >**</span><span class="sxs-lookup"><span data-stu-id="b60d9-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b60d9-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b60d9-109">Syntax</span></span>  
  
```xml  
<remove name="listener name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b60d9-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="b60d9-110">Attributes and Elements</span></span>  
 <span data-ttu-id="b60d9-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="b60d9-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b60d9-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="b60d9-112">Attributes</span></span>  
  
|<span data-ttu-id="b60d9-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="b60d9-113">Attribute</span></span>|<span data-ttu-id="b60d9-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="b60d9-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b60d9-115">**name**</span><span class="sxs-lookup"><span data-stu-id="b60d9-115">**name**</span></span>|<span data-ttu-id="b60d9-116">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="b60d9-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="b60d9-117">O nome do ouvinte a ser removido da coleção de **ouvintes** .</span><span class="sxs-lookup"><span data-stu-id="b60d9-117">The name of the listener to remove from the **Listeners** collection.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b60d9-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="b60d9-118">Child Elements</span></span>  
 <span data-ttu-id="b60d9-119">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="b60d9-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b60d9-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="b60d9-120">Parent Elements</span></span>  
  
|<span data-ttu-id="b60d9-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="b60d9-121">Element</span></span>|<span data-ttu-id="b60d9-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="b60d9-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="b60d9-123">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b60d9-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`listeners`|<span data-ttu-id="b60d9-124">Especifica um ouvinte que coleta, armazena e roteia mensagens.</span><span class="sxs-lookup"><span data-stu-id="b60d9-124">Specifies a listener that collects, stores, and routes messages.</span></span> <span data-ttu-id="b60d9-125">Os ouvintes direcionam a saída de rastreamento para um destino apropriado.</span><span class="sxs-lookup"><span data-stu-id="b60d9-125">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="b60d9-126">Especifica os ouvintes de rastreamento que coletam, armazenam e roteiam mensagens e o nível em que uma opção de rastreamento é definida.</span><span class="sxs-lookup"><span data-stu-id="b60d9-126">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`trace`|<span data-ttu-id="b60d9-127">Configura o serviço de rastreamento do ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="b60d9-127">Configures the ASP.NET trace service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b60d9-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="b60d9-128">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b60d9-129">Remover o <xref:System.Diagnostics.DefaultTraceListener> da coleção `Listeners` altera o comportamento dos métodos <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType> e <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b60d9-129">Removing the <xref:System.Diagnostics.DefaultTraceListener> from the `Listeners` collection alters the behavior of the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>, and <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="b60d9-130">Chamar um método `Assert` ou `Fail` normalmente resulta na exibição de uma caixa de mensagem, no entanto, a caixa de mensagem não será exibida se o <xref:System.Diagnostics.DefaultTraceListener> não estiver na coleção `Listeners`.</span><span class="sxs-lookup"><span data-stu-id="b60d9-130">Calling an `Assert` or `Fail` method normally results in the display of a message box, however the message box is not displayed if the <xref:System.Diagnostics.DefaultTraceListener> is not in the `Listeners` collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b60d9-131">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b60d9-131">Example</span></span>  
 <span data-ttu-id="b60d9-132">O exemplo a seguir mostra como remover o ouvinte de rastreamento padrão da coleção de **ouvintes** de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="b60d9-132">The following example shows how to remove the default trace listener from the trace **Listeners** collection.</span></span>  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <trace autoflush="true" indentsize="0">  
         <listeners>  
            <remove name="Default" />  
         </listeners>  
      </trace>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b60d9-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b60d9-133">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- [<span data-ttu-id="b60d9-134">Esquema de configurações de rastreamento e depuração</span><span class="sxs-lookup"><span data-stu-id="b60d9-134">Trace and Debug Settings Schema</span></span>](index.md)
