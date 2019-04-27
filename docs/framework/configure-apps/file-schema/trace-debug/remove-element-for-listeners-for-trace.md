---
title: <remove> Elemento para <listeners> para <trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/remove
helpviewer_keywords:
- remove element
- <remove> element
ms.assetid: 9a5cd1b5-be1a-485f-8f0c-2890ad3ef3e0
ms.openlocfilehash: adf00394bc0bfe808836e74214003cd2078204e4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61673674"
---
# <a name="remove-element-for-listeners-for-trace"></a><span data-ttu-id="4f814-102">\<Remover > elemento para \<ouvintes > para \<rastreamento ></span><span class="sxs-lookup"><span data-stu-id="4f814-102">\<remove> Element for \<listeners> for \<trace></span></span>
<span data-ttu-id="4f814-103">Remove um ouvinte dos **ouvintes** coleção.</span><span class="sxs-lookup"><span data-stu-id="4f814-103">Removes a listener from the **Listeners** collection.</span></span>  
  
 <span data-ttu-id="4f814-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="4f814-104">\<configuration></span></span>  
<span data-ttu-id="4f814-105">\<system.diagnostics></span><span class="sxs-lookup"><span data-stu-id="4f814-105">\<system.diagnostics></span></span>  
<span data-ttu-id="4f814-106">\<trace></span><span class="sxs-lookup"><span data-stu-id="4f814-106">\<trace></span></span>  
<span data-ttu-id="4f814-107">\<listeners></span><span class="sxs-lookup"><span data-stu-id="4f814-107">\<listeners></span></span>  
<span data-ttu-id="4f814-108">\<remove></span><span class="sxs-lookup"><span data-stu-id="4f814-108">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f814-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4f814-109">Syntax</span></span>  
  
```xml  
<remove name="listener name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4f814-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="4f814-110">Attributes and Elements</span></span>  
 <span data-ttu-id="4f814-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="4f814-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4f814-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="4f814-112">Attributes</span></span>  
  
|<span data-ttu-id="4f814-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="4f814-113">Attribute</span></span>|<span data-ttu-id="4f814-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="4f814-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4f814-115">**name**</span><span class="sxs-lookup"><span data-stu-id="4f814-115">**name**</span></span>|<span data-ttu-id="4f814-116">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="4f814-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="4f814-117">O nome do ouvinte para remover o **ouvintes** coleção.</span><span class="sxs-lookup"><span data-stu-id="4f814-117">The name of the listener to remove from the **Listeners** collection.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4f814-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="4f814-118">Child Elements</span></span>  
 <span data-ttu-id="4f814-119">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="4f814-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4f814-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="4f814-120">Parent Elements</span></span>  
  
|<span data-ttu-id="4f814-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="4f814-121">Element</span></span>|<span data-ttu-id="4f814-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="4f814-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="4f814-123">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4f814-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`listeners`|<span data-ttu-id="4f814-124">Especifica um ouvinte que coleta, armazena e encaminha mensagens.</span><span class="sxs-lookup"><span data-stu-id="4f814-124">Specifies a listener that collects, stores, and routes messages.</span></span> <span data-ttu-id="4f814-125">Os ouvintes direcionam a saída de rastreamento para um destino apropriado.</span><span class="sxs-lookup"><span data-stu-id="4f814-125">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="4f814-126">Especifica os ouvintes de rastreamento que coletam, armazenam e roteiam mensagens e o nível em que uma opção de rastreamento é definida.</span><span class="sxs-lookup"><span data-stu-id="4f814-126">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`trace`|<span data-ttu-id="4f814-127">Configura o serviço de rastreamento do ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="4f814-127">Configures the ASP.NET trace service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4f814-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="4f814-128">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4f814-129">Removendo o <xref:System.Diagnostics.DefaultTraceListener> do `Listeners` coleção altera o comportamento das <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>, e <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> métodos.</span><span class="sxs-lookup"><span data-stu-id="4f814-129">Removing the <xref:System.Diagnostics.DefaultTraceListener> from the `Listeners` collection alters the behavior of the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>, and <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="4f814-130">Chamar um `Assert` ou `Fail` método normalmente resulta na exibição de uma caixa de mensagem, no entanto, a caixa de mensagem não será exibida se o <xref:System.Diagnostics.DefaultTraceListener> não está no `Listeners` coleção.</span><span class="sxs-lookup"><span data-stu-id="4f814-130">Calling an `Assert` or `Fail` method normally results in the display of a message box, however the message box is not displayed if the <xref:System.Diagnostics.DefaultTraceListener> is not in the `Listeners` collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4f814-131">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4f814-131">Example</span></span>  
 <span data-ttu-id="4f814-132">O exemplo a seguir mostra como remover o ouvinte de rastreamento padrão do rastreamento **ouvintes** coleção.</span><span class="sxs-lookup"><span data-stu-id="4f814-132">The following example shows how to remove the default trace listener from the trace **Listeners** collection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4f814-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4f814-133">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- [<span data-ttu-id="4f814-134">Esquema de configurações de rastreamento e depuração</span><span class="sxs-lookup"><span data-stu-id="4f814-134">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
