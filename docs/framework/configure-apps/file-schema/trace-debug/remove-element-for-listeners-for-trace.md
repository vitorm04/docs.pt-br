---
title: <remove> Elemento para <listeners> para <trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/remove
helpviewer_keywords:
- remove element
- <remove> element
ms.assetid: 9a5cd1b5-be1a-485f-8f0c-2890ad3ef3e0
ms.openlocfilehash: 01b797e1fb62d32e9f0d44c54b803dd969615361
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91173829"
---
# <a name="remove-element-for-listeners-for-trace"></a><span data-ttu-id="05d9e-102">\<remove> Elemento para \<listeners> para \<trace></span><span class="sxs-lookup"><span data-stu-id="05d9e-102">\<remove> Element for \<listeners> for \<trace></span></span>

<span data-ttu-id="05d9e-103">Remove um ouvinte da coleção **Listeners** .</span><span class="sxs-lookup"><span data-stu-id="05d9e-103">Removes a listener from the **Listeners** collection.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<trace>**](trace-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-trace.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**

## <a name="syntax"></a><span data-ttu-id="05d9e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="05d9e-104">Syntax</span></span>  
  
```xml  
<remove name="listener name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="05d9e-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="05d9e-105">Attributes and Elements</span></span>  

 <span data-ttu-id="05d9e-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="05d9e-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="05d9e-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="05d9e-107">Attributes</span></span>  
  
|<span data-ttu-id="05d9e-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="05d9e-108">Attribute</span></span>|<span data-ttu-id="05d9e-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="05d9e-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="05d9e-110">**name**</span><span class="sxs-lookup"><span data-stu-id="05d9e-110">**name**</span></span>|<span data-ttu-id="05d9e-111">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="05d9e-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="05d9e-112">O nome do ouvinte a ser removido da coleção de **ouvintes** .</span><span class="sxs-lookup"><span data-stu-id="05d9e-112">The name of the listener to remove from the **Listeners** collection.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="05d9e-113">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="05d9e-113">Child Elements</span></span>  

 <span data-ttu-id="05d9e-114">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="05d9e-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="05d9e-115">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="05d9e-115">Parent Elements</span></span>  
  
|<span data-ttu-id="05d9e-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="05d9e-116">Element</span></span>|<span data-ttu-id="05d9e-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="05d9e-117">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="05d9e-118">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="05d9e-118">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`listeners`|<span data-ttu-id="05d9e-119">Especifica um ouvinte que coleta, armazena e roteia mensagens.</span><span class="sxs-lookup"><span data-stu-id="05d9e-119">Specifies a listener that collects, stores, and routes messages.</span></span> <span data-ttu-id="05d9e-120">Os ouvintes direcionam a saída de rastreamento para um destino apropriado.</span><span class="sxs-lookup"><span data-stu-id="05d9e-120">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="05d9e-121">Especifica os ouvintes de rastreamento que coletam, armazenam e roteiam mensagens e o nível em que uma opção de rastreamento é definida.</span><span class="sxs-lookup"><span data-stu-id="05d9e-121">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`trace`|<span data-ttu-id="05d9e-122">Configura o serviço de rastreamento do ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="05d9e-122">Configures the ASP.NET trace service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="05d9e-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="05d9e-123">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="05d9e-124">Remover o <xref:System.Diagnostics.DefaultTraceListener> da `Listeners` coleção altera o comportamento dos <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> métodos,, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType> <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType> e <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="05d9e-124">Removing the <xref:System.Diagnostics.DefaultTraceListener> from the `Listeners` collection alters the behavior of the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>, and <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="05d9e-125">Chamar um `Assert` `Fail` método ou normalmente resulta na exibição de uma caixa de mensagem, no entanto, a caixa de mensagem não será exibida se o <xref:System.Diagnostics.DefaultTraceListener> não estiver na `Listeners` coleção.</span><span class="sxs-lookup"><span data-stu-id="05d9e-125">Calling an `Assert` or `Fail` method normally results in the display of a message box, however the message box is not displayed if the <xref:System.Diagnostics.DefaultTraceListener> is not in the `Listeners` collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="05d9e-126">Exemplo</span><span class="sxs-lookup"><span data-stu-id="05d9e-126">Example</span></span>  

 <span data-ttu-id="05d9e-127">O exemplo a seguir mostra como remover o ouvinte de rastreamento padrão da coleção de **ouvintes** de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="05d9e-127">The following example shows how to remove the default trace listener from the trace **Listeners** collection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="05d9e-128">Confira também</span><span class="sxs-lookup"><span data-stu-id="05d9e-128">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- [<span data-ttu-id="05d9e-129">Esquema de configurações de rastreamento e depuração</span><span class="sxs-lookup"><span data-stu-id="05d9e-129">Trace and Debug Settings Schema</span></span>](index.md)
