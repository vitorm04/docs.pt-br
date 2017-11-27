---
title: '&lt;EnableAmPmParseAdjustment&gt; elemento'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fda998a5-f538-4f8b-a18c-ee7f35e16938
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 44bd6297142b6f29d93e9a3bebdb89d32d4bf46a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ltenableampmparseadjustmentgt-element"></a><span data-ttu-id="7fa9b-102">&lt;EnableAmPmParseAdjustment&gt; elemento</span><span class="sxs-lookup"><span data-stu-id="7fa9b-102">&lt;EnableAmPmParseAdjustment&gt; Element</span></span>
<span data-ttu-id="7fa9b-103">Determina se a data e hora métodos usam um conjunto de regras de ajustada para analisar cadeias de caracteres de data que contêm um dia, mês, hora e designator AM/PM.</span><span class="sxs-lookup"><span data-stu-id="7fa9b-103">Determines whether date and time parsing methods use an adjusted set of rules to parse date strings that contain a day, month, hour, and AM/PM designator.</span></span>  
  
 <span data-ttu-id="7fa9b-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="7fa9b-104">\<configuration></span></span>  
 <span data-ttu-id="7fa9b-105">\<tempo de execução ></span><span class="sxs-lookup"><span data-stu-id="7fa9b-105">\<runtime></span></span>  
<span data-ttu-id="7fa9b-106">\<EnableAmPmParseAdjustment ></span><span class="sxs-lookup"><span data-stu-id="7fa9b-106">\<EnableAmPmParseAdjustment></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7fa9b-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7fa9b-107">Syntax</span></span>  
  
```xml  
<EnableAmPmParseAdjustment enabled="0"|"1" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7fa9b-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="7fa9b-108">Attributes and Elements</span></span>  
 <span data-ttu-id="7fa9b-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="7fa9b-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7fa9b-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="7fa9b-110">Attributes</span></span>  
  
|<span data-ttu-id="7fa9b-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="7fa9b-111">Attribute</span></span>|<span data-ttu-id="7fa9b-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="7fa9b-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="7fa9b-113">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="7fa9b-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="7fa9b-114">Especifica se a data e hora métodos usarem um conjunto de regras de ajustada para analisar cadeias de caracteres de data que contêm somente um dia, mês, hora e designator AM/PM.</span><span class="sxs-lookup"><span data-stu-id="7fa9b-114">Specifies whether date and time parsing methods use an adjusted set of rules to parse date strings that contain only a day, month, hour, and AM/PM designator.</span></span>|  
  
### <a name="enabled-attribute"></a><span data-ttu-id="7fa9b-115">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="7fa9b-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="7fa9b-116">Valor</span><span class="sxs-lookup"><span data-stu-id="7fa9b-116">Value</span></span>|<span data-ttu-id="7fa9b-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="7fa9b-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="7fa9b-118">0</span><span class="sxs-lookup"><span data-stu-id="7fa9b-118">0</span></span>|<span data-ttu-id="7fa9b-119">Data e hora métodos não usar regras ajustadas para analisar cadeias de caracteres que contêm apenas um dia, mês, hora e designator AM/PM.</span><span class="sxs-lookup"><span data-stu-id="7fa9b-119">Date and time parsing methods do not use adjusted rules for parsing date strings that contain only a day, month, hour, and AM/PM designator.</span></span>|  
|<span data-ttu-id="7fa9b-120">1</span><span class="sxs-lookup"><span data-stu-id="7fa9b-120">1</span></span>|<span data-ttu-id="7fa9b-121">Data e hora métodos usam regras ajustadas para analisar cadeias de caracteres que contêm apenas um dia, mês, hora e designator AM/PM.</span><span class="sxs-lookup"><span data-stu-id="7fa9b-121">Date and time parsing methods use adjusted rules for parsing date strings that contain only a day, month, hour, and AM/PM designator.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7fa9b-122">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="7fa9b-122">Child Elements</span></span>  
 <span data-ttu-id="7fa9b-123">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="7fa9b-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7fa9b-124">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="7fa9b-124">Parent Elements</span></span>  
  
|<span data-ttu-id="7fa9b-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="7fa9b-125">Element</span></span>|<span data-ttu-id="7fa9b-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="7fa9b-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="7fa9b-127">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7fa9b-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="7fa9b-128">Contém informações sobre opções de inicialização do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="7fa9b-128">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7fa9b-129">Comentários</span><span class="sxs-lookup"><span data-stu-id="7fa9b-129">Remarks</span></span>  
 <span data-ttu-id="7fa9b-130">O `<EnableAmPmParseAdjustment>` elemento controla como os métodos a seguir analisar uma cadeia de caracteres de data que contém um dia numérico e seguido por um designador de AM/PM (por exemplo, "6 de 4 a 10 AM") e uma hora do mês:</span><span class="sxs-lookup"><span data-stu-id="7fa9b-130">The `<EnableAmPmParseAdjustment>` element controls how the following methods parse a date string that contains a numeric day and month followed by an hour and an AM/PM designator (such as "4/10 6 AM"):</span></span>  
  
-   <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>  
  
-   <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType>  
  
-   <xref:System.DateTime.TryParse%2A?displayProperty=nameWithType>  
  
-   <xref:System.DateTimeOffset.TryParse%2A?displayProperty=nameWithType>  
  
-   <xref:System.Convert.ToDateTime%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="7fa9b-131">Não há outros padrões são afetados.</span><span class="sxs-lookup"><span data-stu-id="7fa9b-131">No other patterns are affected.</span></span>  
  
 <span data-ttu-id="7fa9b-132">O `<EnableAmPmParseAdjustment>` elemento não tem nenhum efeito o <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType>, <xref:System.DateTime.TryParseExact%2A?displayProperty=nameWithType>, <xref:System.DateTimeOffset.ParseExact%2A?displayProperty=nameWithType>, e <xref:System.DateTimeOffset.TryParseExact%2A?displayProperty=nameWithType> métodos.</span><span class="sxs-lookup"><span data-stu-id="7fa9b-132">The `<EnableAmPmParseAdjustment>` element has no effect on the  <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType>,  <xref:System.DateTime.TryParseExact%2A?displayProperty=nameWithType>, <xref:System.DateTimeOffset.ParseExact%2A?displayProperty=nameWithType>, and <xref:System.DateTimeOffset.TryParseExact%2A?displayProperty=nameWithType> methods.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7fa9b-133">No .NET Core e .NET nativo, as regras de análise de AM/PM ajustadas são habilitadas por padrão.</span><span class="sxs-lookup"><span data-stu-id="7fa9b-133">In .NET Core and .NET Native, the adjusted AM/PM parsing rules are enabled by default.</span></span>  
  
 <span data-ttu-id="7fa9b-134">Se a regra de ajuste a análise não estiver habilitada, o primeiro dígito da cadeia de caracteres é interpretado como a hora do relógio de 12 horas, e o restante da cadeia de caracteres, exceto o designador de AM/PM é ignorado.</span><span class="sxs-lookup"><span data-stu-id="7fa9b-134">If the parsing adjustment rule is not enabled, the first digit of the string is interpreted as the hour of the 12-hour clock, and the remainder of the string except for the AM/PM designator is ignored.</span></span> <span data-ttu-id="7fa9b-135">A data e hora retornada pelo método de análise consiste a data atual e a hora do dia extraído da cadeia de caracteres de data.</span><span class="sxs-lookup"><span data-stu-id="7fa9b-135">The date and time returned by the parsing method consists of the current date and the hour of the day extracted from the date string.</span></span>  
  
 <span data-ttu-id="7fa9b-136">Se a regra de ajuste a análise está habilitada, análise do método interpretar o dia e mês como pertencentes ao ano atual e interpretar a hora como a hora do relógio de 12 horas.</span><span class="sxs-lookup"><span data-stu-id="7fa9b-136">If the parsing adjustment rule is enabled, parsing method interpret the day and month as belonging to the current year, and interpret the time as the hour of the 12-hour clock.</span></span>  
  
 <span data-ttu-id="7fa9b-137">A tabela a seguir ilustra a diferença no <xref:System.DateTime> valor quando o <xref:System.DateTime.Parse%28System.String%29?displayProperty=nameWithType> método é usado para analisar a cadeia de caracteres "" 4/10 6 AM"com o `<EnableAmPmParseAdjustment>` do elemento `enabled` propriedade definida como"0"ou"1".</span><span class="sxs-lookup"><span data-stu-id="7fa9b-137">The following table illustrates the difference in the <xref:System.DateTime> value when the <xref:System.DateTime.Parse%28System.String%29?displayProperty=nameWithType> method is used to parse the string ""4/10 6 AM" with the `<EnableAmPmParseAdjustment>` element's `enabled` property  set to "0" or "1".</span></span> <span data-ttu-id="7fa9b-138">Ele pressupõe que a data de hoje é 5 de janeiro de 2017 e exibe a data em que ele é formatado usando a cadeia de caracteres do formato da cultura especificada "G".</span><span class="sxs-lookup"><span data-stu-id="7fa9b-138">It assumes that today's date is January 5, 2017, and displays the date as if it is formatted using the specified culture's "G" format string.</span></span>  
  
|<span data-ttu-id="7fa9b-139">Nome da cultura</span><span class="sxs-lookup"><span data-stu-id="7fa9b-139">Culture name</span></span>|<span data-ttu-id="7fa9b-140">ativado = "0"</span><span class="sxs-lookup"><span data-stu-id="7fa9b-140">enabled="0"</span></span>|<span data-ttu-id="7fa9b-141">ativado = "1"</span><span class="sxs-lookup"><span data-stu-id="7fa9b-141">enabled="1"</span></span>|  
|------------------|------------------|------------------|  
|<span data-ttu-id="7fa9b-142">pt-BR</span><span class="sxs-lookup"><span data-stu-id="7fa9b-142">en-US</span></span>|<span data-ttu-id="7fa9b-143">1/5/2017 4:00:00 AM</span><span class="sxs-lookup"><span data-stu-id="7fa9b-143">1/5/2017 4:00:00 AM</span></span>|<span data-ttu-id="7fa9b-144">10/4/2017 6:00:00 AM</span><span class="sxs-lookup"><span data-stu-id="7fa9b-144">4/10/2017 6:00:00 AM</span></span>|  
|<span data-ttu-id="7fa9b-145">en-GB</span><span class="sxs-lookup"><span data-stu-id="7fa9b-145">en-GB</span></span>|<span data-ttu-id="7fa9b-146">5/1/2017 6:00:00</span><span class="sxs-lookup"><span data-stu-id="7fa9b-146">5/1/2017 6:00:00</span></span>|<span data-ttu-id="7fa9b-147">10/4/2017 6:00:00</span><span class="sxs-lookup"><span data-stu-id="7fa9b-147">10/4/2017 6:00:00</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7fa9b-148">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7fa9b-148">See Also</span></span>  
 [<span data-ttu-id="7fa9b-149">\<tempo de execução > elemento</span><span class="sxs-lookup"><span data-stu-id="7fa9b-149">\<runtime> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md)  
 [<span data-ttu-id="7fa9b-150">Elemento \<configuration></span><span class="sxs-lookup"><span data-stu-id="7fa9b-150">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)
