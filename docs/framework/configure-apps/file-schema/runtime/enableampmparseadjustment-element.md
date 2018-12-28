---
title: '&lt;EnableAmPmParseAdjustment&gt; elemento'
ms.date: 03/30/2017
ms.assetid: fda998a5-f538-4f8b-a18c-ee7f35e16938
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cf56a2720ab407d05b8356280913445c15a17020
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/19/2018
ms.locfileid: "53611068"
---
# <a name="ltenableampmparseadjustmentgt-element"></a><span data-ttu-id="44eda-102">&lt;EnableAmPmParseAdjustment&gt; elemento</span><span class="sxs-lookup"><span data-stu-id="44eda-102">&lt;EnableAmPmParseAdjustment&gt; Element</span></span>
<span data-ttu-id="44eda-103">Determina se a data e hora de métodos de análise usam um conjunto de regras ajustado para analisar cadeias de caracteres de data que contêm um dia, mês, hora e designador AM/PM.</span><span class="sxs-lookup"><span data-stu-id="44eda-103">Determines whether date and time parsing methods use an adjusted set of rules to parse date strings that contain a day, month, hour, and AM/PM designator.</span></span>  
  
 <span data-ttu-id="44eda-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="44eda-104">\<configuration></span></span>  
 <span data-ttu-id="44eda-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="44eda-105">\<runtime></span></span>  
<span data-ttu-id="44eda-106">\<EnableAmPmParseAdjustment ></span><span class="sxs-lookup"><span data-stu-id="44eda-106">\<EnableAmPmParseAdjustment></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44eda-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="44eda-107">Syntax</span></span>  
  
```xml  
<EnableAmPmParseAdjustment enabled="0"|"1" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="44eda-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="44eda-108">Attributes and Elements</span></span>  
 <span data-ttu-id="44eda-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="44eda-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="44eda-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="44eda-110">Attributes</span></span>  
  
|<span data-ttu-id="44eda-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="44eda-111">Attribute</span></span>|<span data-ttu-id="44eda-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="44eda-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="44eda-113">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="44eda-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="44eda-114">Especifica se a data e hora de métodos de análise usam um conjunto de regras ajustado para analisar cadeias de caracteres de data que contêm somente um dia, mês, hora e designador AM/PM.</span><span class="sxs-lookup"><span data-stu-id="44eda-114">Specifies whether date and time parsing methods use an adjusted set of rules to parse date strings that contain only a day, month, hour, and AM/PM designator.</span></span>|  
  
### <a name="enabled-attribute"></a><span data-ttu-id="44eda-115">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="44eda-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="44eda-116">Valor</span><span class="sxs-lookup"><span data-stu-id="44eda-116">Value</span></span>|<span data-ttu-id="44eda-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="44eda-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="44eda-118">0</span><span class="sxs-lookup"><span data-stu-id="44eda-118">0</span></span>|<span data-ttu-id="44eda-119">Data e hora de métodos de análise não usam regras ajustadas para analisar cadeias de caracteres de data que contêm somente um dia, mês, hora e designador AM/PM.</span><span class="sxs-lookup"><span data-stu-id="44eda-119">Date and time parsing methods do not use adjusted rules for parsing date strings that contain only a day, month, hour, and AM/PM designator.</span></span>|  
|<span data-ttu-id="44eda-120">1</span><span class="sxs-lookup"><span data-stu-id="44eda-120">1</span></span>|<span data-ttu-id="44eda-121">Data e hora métodos de análise usam regras ajustadas para analisar cadeias de caracteres de data que contêm somente um dia, mês, hora e designador AM/PM.</span><span class="sxs-lookup"><span data-stu-id="44eda-121">Date and time parsing methods use adjusted rules for parsing date strings that contain only a day, month, hour, and AM/PM designator.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="44eda-122">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="44eda-122">Child Elements</span></span>  
 <span data-ttu-id="44eda-123">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="44eda-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="44eda-124">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="44eda-124">Parent Elements</span></span>  
  
|<span data-ttu-id="44eda-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="44eda-125">Element</span></span>|<span data-ttu-id="44eda-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="44eda-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="44eda-127">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="44eda-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="44eda-128">Contém informações sobre opções de inicialização do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="44eda-128">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="44eda-129">Comentários</span><span class="sxs-lookup"><span data-stu-id="44eda-129">Remarks</span></span>  
 <span data-ttu-id="44eda-130">O `<EnableAmPmParseAdjustment>` elemento controla como os métodos a seguir analisar uma cadeia de caracteres de data que contém um dia numérico e o mês, seguido por uma hora e um designador AM/PM (por exemplo, "10 4 6 AM"):</span><span class="sxs-lookup"><span data-stu-id="44eda-130">The `<EnableAmPmParseAdjustment>` element controls how the following methods parse a date string that contains a numeric day and month followed by an hour and an AM/PM designator (such as "4/10 6 AM"):</span></span>  
  
-   <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>  
  
-   <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType>  
  
-   <xref:System.DateTime.TryParse%2A?displayProperty=nameWithType>  
  
-   <xref:System.DateTimeOffset.TryParse%2A?displayProperty=nameWithType>  
  
-   <xref:System.Convert.ToDateTime%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="44eda-131">Outros padrões não são afetados.</span><span class="sxs-lookup"><span data-stu-id="44eda-131">No other patterns are affected.</span></span>  
  
 <span data-ttu-id="44eda-132">O `<EnableAmPmParseAdjustment>` elemento não tem efeito sobre a <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType>, <xref:System.DateTime.TryParseExact%2A?displayProperty=nameWithType>, <xref:System.DateTimeOffset.ParseExact%2A?displayProperty=nameWithType>, e <xref:System.DateTimeOffset.TryParseExact%2A?displayProperty=nameWithType> métodos.</span><span class="sxs-lookup"><span data-stu-id="44eda-132">The `<EnableAmPmParseAdjustment>` element has no effect on the  <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType>,  <xref:System.DateTime.TryParseExact%2A?displayProperty=nameWithType>, <xref:System.DateTimeOffset.ParseExact%2A?displayProperty=nameWithType>, and <xref:System.DateTimeOffset.TryParseExact%2A?displayProperty=nameWithType> methods.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="44eda-133">No .NET Core e .NET Native, regras de análise ajustadas do AM/PM são habilitadas por padrão.</span><span class="sxs-lookup"><span data-stu-id="44eda-133">In .NET Core and .NET Native, the adjusted AM/PM parsing rules are enabled by default.</span></span>  
  
 <span data-ttu-id="44eda-134">Se a regra de análise de ajuste não estiver habilitada, o primeiro dígito da cadeia de caracteres é interpretado como a hora do relógio de 12 horas, e o restante da cadeia de caracteres, exceto o designador AM/PM é ignorado.</span><span class="sxs-lookup"><span data-stu-id="44eda-134">If the parsing adjustment rule is not enabled, the first digit of the string is interpreted as the hour of the 12-hour clock, and the remainder of the string except for the AM/PM designator is ignored.</span></span> <span data-ttu-id="44eda-135">A data e hora retornado pelo método de análise consiste da data atual e a hora do dia extraído da cadeia de caracteres de data.</span><span class="sxs-lookup"><span data-stu-id="44eda-135">The date and time returned by the parsing method consists of the current date and the hour of the day extracted from the date string.</span></span>  
  
 <span data-ttu-id="44eda-136">Se a regra de análise de ajuste está habilitada, método de análise interpretar o dia e mês como pertencentes ao ano atual e interpretar a hora como a hora do relógio de 12 horas.</span><span class="sxs-lookup"><span data-stu-id="44eda-136">If the parsing adjustment rule is enabled, parsing method interpret the day and month as belonging to the current year, and interpret the time as the hour of the 12-hour clock.</span></span>  
  
 <span data-ttu-id="44eda-137">A tabela a seguir ilustra a diferença no <xref:System.DateTime> valor quando o <xref:System.DateTime.Parse%28System.String%29?displayProperty=nameWithType> método é usado para analisar a cadeia de caracteres "" 4/10 6 AM"com o `<EnableAmPmParseAdjustment>` do elemento `enabled` propriedade definida como"0"ou"1".</span><span class="sxs-lookup"><span data-stu-id="44eda-137">The following table illustrates the difference in the <xref:System.DateTime> value when the <xref:System.DateTime.Parse%28System.String%29?displayProperty=nameWithType> method is used to parse the string ""4/10 6 AM" with the `<EnableAmPmParseAdjustment>` element's `enabled` property  set to "0" or "1".</span></span> <span data-ttu-id="44eda-138">Ele pressupõe que hoje é dia 5 de janeiro de 2017 e exibe a data como se ele é formatado usando a cadeia de caracteres de formato de "G" da cultura especificada.</span><span class="sxs-lookup"><span data-stu-id="44eda-138">It assumes that today's date is January 5, 2017, and displays the date as if it is formatted using the specified culture's "G" format string.</span></span>  
  
|<span data-ttu-id="44eda-139">Nome da cultura</span><span class="sxs-lookup"><span data-stu-id="44eda-139">Culture name</span></span>|<span data-ttu-id="44eda-140">habilitado = "0"</span><span class="sxs-lookup"><span data-stu-id="44eda-140">enabled="0"</span></span>|<span data-ttu-id="44eda-141">habilitado = "1"</span><span class="sxs-lookup"><span data-stu-id="44eda-141">enabled="1"</span></span>|  
|------------------|------------------|------------------|  
|<span data-ttu-id="44eda-142">en-US</span><span class="sxs-lookup"><span data-stu-id="44eda-142">en-US</span></span>|<span data-ttu-id="44eda-143">1/5/2017 4:00:00 AM</span><span class="sxs-lookup"><span data-stu-id="44eda-143">1/5/2017 4:00:00 AM</span></span>|<span data-ttu-id="44eda-144">4/10/2017 6:00:00 AM</span><span class="sxs-lookup"><span data-stu-id="44eda-144">4/10/2017 6:00:00 AM</span></span>|  
|<span data-ttu-id="44eda-145">en-GB</span><span class="sxs-lookup"><span data-stu-id="44eda-145">en-GB</span></span>|<span data-ttu-id="44eda-146">5/1/2017 6:00:00</span><span class="sxs-lookup"><span data-stu-id="44eda-146">5/1/2017 6:00:00</span></span>|<span data-ttu-id="44eda-147">10/4/2017 6:00:00</span><span class="sxs-lookup"><span data-stu-id="44eda-147">10/4/2017 6:00:00</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="44eda-148">Consulte também</span><span class="sxs-lookup"><span data-stu-id="44eda-148">See Also</span></span>  
- [<span data-ttu-id="44eda-149">\<tempo de execução > elemento</span><span class="sxs-lookup"><span data-stu-id="44eda-149">\<runtime> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md)  
- [<span data-ttu-id="44eda-150">Elemento \<configuration></span><span class="sxs-lookup"><span data-stu-id="44eda-150">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)
