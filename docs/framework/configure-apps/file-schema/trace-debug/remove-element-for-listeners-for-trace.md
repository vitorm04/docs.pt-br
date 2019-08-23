---
title: <remove>Elemento para <listeners> para<trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/remove
helpviewer_keywords:
- remove element
- <remove> element
ms.assetid: 9a5cd1b5-be1a-485f-8f0c-2890ad3ef3e0
ms.openlocfilehash: 0c5c9efb8a22d26ea5d4467f9628af5935d6dbad
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920485"
---
# <a name="remove-element-for-listeners-for-trace"></a><span data-ttu-id="e1f8c-102">\<remover o elemento > \<para ouvintes > \<para rastreamento ></span><span class="sxs-lookup"><span data-stu-id="e1f8c-102">\<remove> Element for \<listeners> for \<trace></span></span>
<span data-ttu-id="e1f8c-103">Remove um ouvinte da coleção Listeners.</span><span class="sxs-lookup"><span data-stu-id="e1f8c-103">Removes a listener from the **Listeners** collection.</span></span>  
  
 <span data-ttu-id="e1f8c-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="e1f8c-104">\<configuration></span></span>  
<span data-ttu-id="e1f8c-105">\<System. Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="e1f8c-105">\<system.diagnostics></span></span>  
<span data-ttu-id="e1f8c-106">\<> de rastreamento</span><span class="sxs-lookup"><span data-stu-id="e1f8c-106">\<trace></span></span>  
<span data-ttu-id="e1f8c-107">\<listeners></span><span class="sxs-lookup"><span data-stu-id="e1f8c-107">\<listeners></span></span>  
<span data-ttu-id="e1f8c-108">\<remove></span><span class="sxs-lookup"><span data-stu-id="e1f8c-108">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1f8c-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e1f8c-109">Syntax</span></span>  
  
```xml  
<remove name="listener name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e1f8c-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="e1f8c-110">Attributes and Elements</span></span>  
 <span data-ttu-id="e1f8c-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="e1f8c-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e1f8c-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="e1f8c-112">Attributes</span></span>  
  
|<span data-ttu-id="e1f8c-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="e1f8c-113">Attribute</span></span>|<span data-ttu-id="e1f8c-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="e1f8c-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e1f8c-115">**name**</span><span class="sxs-lookup"><span data-stu-id="e1f8c-115">**name**</span></span>|<span data-ttu-id="e1f8c-116">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="e1f8c-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="e1f8c-117">O nome do ouvinte a ser removido da coleção de ouvintes.</span><span class="sxs-lookup"><span data-stu-id="e1f8c-117">The name of the listener to remove from the **Listeners** collection.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e1f8c-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="e1f8c-118">Child Elements</span></span>  
 <span data-ttu-id="e1f8c-119">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="e1f8c-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e1f8c-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="e1f8c-120">Parent Elements</span></span>  
  
|<span data-ttu-id="e1f8c-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="e1f8c-121">Element</span></span>|<span data-ttu-id="e1f8c-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="e1f8c-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="e1f8c-123">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e1f8c-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`listeners`|<span data-ttu-id="e1f8c-124">Especifica um ouvinte que coleta, armazena e roteia mensagens.</span><span class="sxs-lookup"><span data-stu-id="e1f8c-124">Specifies a listener that collects, stores, and routes messages.</span></span> <span data-ttu-id="e1f8c-125">Os ouvintes direcionam a saída de rastreamento para um destino apropriado.</span><span class="sxs-lookup"><span data-stu-id="e1f8c-125">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="e1f8c-126">Especifica os ouvintes de rastreamento que coletam, armazenam e roteiam mensagens e o nível em que uma opção de rastreamento é definida.</span><span class="sxs-lookup"><span data-stu-id="e1f8c-126">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`trace`|<span data-ttu-id="e1f8c-127">Configura o serviço de rastreamento do ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="e1f8c-127">Configures the ASP.NET trace service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e1f8c-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="e1f8c-128">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e1f8c-129">Remover o <xref:System.Diagnostics.DefaultTraceListener> <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>da coleção altera o<xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>comportamento dos métodos,, e <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType>. `Listeners`</span><span class="sxs-lookup"><span data-stu-id="e1f8c-129">Removing the <xref:System.Diagnostics.DefaultTraceListener> from the `Listeners` collection alters the behavior of the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>, and <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="e1f8c-130">Chamar um `Assert` método `Fail` ou normalmente resulta na exibição de uma caixa de mensagem, no entanto, a caixa de mensagem não <xref:System.Diagnostics.DefaultTraceListener> será exibida se `Listeners` o não estiver na coleção.</span><span class="sxs-lookup"><span data-stu-id="e1f8c-130">Calling an `Assert` or `Fail` method normally results in the display of a message box, however the message box is not displayed if the <xref:System.Diagnostics.DefaultTraceListener> is not in the `Listeners` collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e1f8c-131">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e1f8c-131">Example</span></span>  
 <span data-ttu-id="e1f8c-132">O exemplo a seguir mostra como remover o ouvinte de rastreamento padrão da coleção de ouvintes de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="e1f8c-132">The following example shows how to remove the default trace listener from the trace **Listeners** collection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e1f8c-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e1f8c-133">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- [<span data-ttu-id="e1f8c-134">Esquema de configurações de rastreamento e depuração</span><span class="sxs-lookup"><span data-stu-id="e1f8c-134">Trace and Debug Settings Schema</span></span>](index.md)
