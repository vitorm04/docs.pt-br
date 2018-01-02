---
title: '&lt;remover&gt; elemento para &lt;ouvintes&gt; para &lt;rastreamento&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/remove
helpviewer_keywords:
- remove element
- <remove> element
ms.assetid: 9a5cd1b5-be1a-485f-8f0c-2890ad3ef3e0
caps.latest.revision: "12"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 7bc4136fb917ee9b63b7cca26ba1834de21f542e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltremovegt-element-for-ltlistenersgt-for-lttracegt"></a><span data-ttu-id="f8a40-102">&lt;remover&gt; elemento para &lt;ouvintes&gt; para &lt;rastreamento&gt;</span><span class="sxs-lookup"><span data-stu-id="f8a40-102">&lt;remove&gt; Element for &lt;listeners&gt; for &lt;trace&gt;</span></span>
<span data-ttu-id="f8a40-103">Remove um ouvinte do **ouvintes** coleção.</span><span class="sxs-lookup"><span data-stu-id="f8a40-103">Removes a listener from the **Listeners** collection.</span></span>  
  
 <span data-ttu-id="f8a40-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="f8a40-104">\<configuration></span></span>  
<span data-ttu-id="f8a40-105">\<System. Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="f8a40-105">\<system.diagnostics></span></span>  
<span data-ttu-id="f8a40-106">\<rastreamento ></span><span class="sxs-lookup"><span data-stu-id="f8a40-106">\<trace></span></span>  
<span data-ttu-id="f8a40-107">\<ouvintes ></span><span class="sxs-lookup"><span data-stu-id="f8a40-107">\<listeners></span></span>  
<span data-ttu-id="f8a40-108">\<Remover ></span><span class="sxs-lookup"><span data-stu-id="f8a40-108">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8a40-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f8a40-109">Syntax</span></span>  
  
```xml  
<remove name="listener name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f8a40-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="f8a40-110">Attributes and Elements</span></span>  
 <span data-ttu-id="f8a40-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="f8a40-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f8a40-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="f8a40-112">Attributes</span></span>  
  
|<span data-ttu-id="f8a40-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="f8a40-113">Attribute</span></span>|<span data-ttu-id="f8a40-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="f8a40-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f8a40-115">**name**</span><span class="sxs-lookup"><span data-stu-id="f8a40-115">**name**</span></span>|<span data-ttu-id="f8a40-116">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="f8a40-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="f8a40-117">O nome do ouvinte a remova o **ouvintes** coleção.</span><span class="sxs-lookup"><span data-stu-id="f8a40-117">The name of the listener to remove from the **Listeners** collection.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f8a40-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="f8a40-118">Child Elements</span></span>  
 <span data-ttu-id="f8a40-119">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="f8a40-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f8a40-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="f8a40-120">Parent Elements</span></span>  
  
|<span data-ttu-id="f8a40-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="f8a40-121">Element</span></span>|<span data-ttu-id="f8a40-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="f8a40-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="f8a40-123">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f8a40-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`listeners`|<span data-ttu-id="f8a40-124">Especifica um ouvinte que coleta, armazena e roteamento de mensagens.</span><span class="sxs-lookup"><span data-stu-id="f8a40-124">Specifies a listener that collects, stores, and routes messages.</span></span> <span data-ttu-id="f8a40-125">Os ouvintes direcionam a saída de rastreamento para um destino satisfatório.</span><span class="sxs-lookup"><span data-stu-id="f8a40-125">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="f8a40-126">Especifica os ouvintes de rastreamento que coletam, armazenam e roteiam mensagens e o nível em que uma opção de rastreamento é definida.</span><span class="sxs-lookup"><span data-stu-id="f8a40-126">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`trace`|<span data-ttu-id="f8a40-127">Configura o serviço de rastreamento do ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="f8a40-127">Configures the ASP.NET trace service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f8a40-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="f8a40-128">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f8a40-129">Removendo o <xref:System.Diagnostics.DefaultTraceListener> do `Listeners` coleção altera o comportamento do <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>, e <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> métodos.</span><span class="sxs-lookup"><span data-stu-id="f8a40-129">Removing the <xref:System.Diagnostics.DefaultTraceListener> from the `Listeners` collection alters the behavior of the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>, and <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="f8a40-130">Chamando um `Assert` ou `Fail` método normalmente resulta na exibição de uma caixa de mensagem, no entanto, a caixa de mensagem não será exibida se o <xref:System.Diagnostics.DefaultTraceListener> não está no `Listeners` coleção.</span><span class="sxs-lookup"><span data-stu-id="f8a40-130">Calling an `Assert` or `Fail` method normally results in the display of a message box, however the message box is not displayed if the <xref:System.Diagnostics.DefaultTraceListener> is not in the `Listeners` collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f8a40-131">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f8a40-131">Example</span></span>  
 <span data-ttu-id="f8a40-132">O exemplo a seguir mostra como remover o ouvinte de rastreamento padrão do rastreamento **ouvintes** coleção.</span><span class="sxs-lookup"><span data-stu-id="f8a40-132">The following example shows how to remove the default trace listener from the trace **Listeners** collection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f8a40-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f8a40-133">See Also</span></span>  
 <xref:System.Diagnostics.TraceListener>  
 <xref:System.Diagnostics.DefaultTraceListener>  
 <xref:System.Diagnostics.TextWriterTraceListener>  
 <xref:System.Diagnostics.EventLogTraceListener>  
 [<span data-ttu-id="f8a40-134">Esquema de configurações de rastreamento e depuração</span><span class="sxs-lookup"><span data-stu-id="f8a40-134">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
