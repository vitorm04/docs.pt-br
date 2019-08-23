---
title: Elemento <EnableAmPmParseAdjustment>
ms.date: 03/30/2017
ms.assetid: fda998a5-f538-4f8b-a18c-ee7f35e16938
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 46cf37ee800c05eb7fe12e8491ad3b2130c3a04d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920818"
---
# <a name="enableampmparseadjustment-element"></a><span data-ttu-id="73e44-102">\<Elemento de > EnableAmPmParseAdjustment</span><span class="sxs-lookup"><span data-stu-id="73e44-102">\<EnableAmPmParseAdjustment> Element</span></span>
<span data-ttu-id="73e44-103">Determina se os métodos de análise de data e hora usam um conjunto ajustado de regras para analisar as cadeias de caracteres de data que contêm um designador de dia, mês, hora e AM/PM.</span><span class="sxs-lookup"><span data-stu-id="73e44-103">Determines whether date and time parsing methods use an adjusted set of rules to parse date strings that contain a day, month, hour, and AM/PM designator.</span></span>  
  
 <span data-ttu-id="73e44-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="73e44-104">\<configuration></span></span>  
 <span data-ttu-id="73e44-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="73e44-105">\<runtime></span></span>  
<span data-ttu-id="73e44-106">\<EnableAmPmParseAdjustment></span><span class="sxs-lookup"><span data-stu-id="73e44-106">\<EnableAmPmParseAdjustment></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73e44-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="73e44-107">Syntax</span></span>  
  
```xml  
<EnableAmPmParseAdjustment enabled="0"|"1" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="73e44-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="73e44-108">Attributes and Elements</span></span>  
 <span data-ttu-id="73e44-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="73e44-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="73e44-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="73e44-110">Attributes</span></span>  
  
|<span data-ttu-id="73e44-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="73e44-111">Attribute</span></span>|<span data-ttu-id="73e44-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="73e44-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="73e44-113">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="73e44-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="73e44-114">Especifica se os métodos de análise de data e hora usam um conjunto ajustado de regras para analisar cadeias de caracteres de data que contêm apenas um designador de dia, mês, hora e AM/PM.</span><span class="sxs-lookup"><span data-stu-id="73e44-114">Specifies whether date and time parsing methods use an adjusted set of rules to parse date strings that contain only a day, month, hour, and AM/PM designator.</span></span>|  
  
### <a name="enabled-attribute"></a><span data-ttu-id="73e44-115">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="73e44-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="73e44-116">Valor</span><span class="sxs-lookup"><span data-stu-id="73e44-116">Value</span></span>|<span data-ttu-id="73e44-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="73e44-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="73e44-118">0</span><span class="sxs-lookup"><span data-stu-id="73e44-118">0</span></span>|<span data-ttu-id="73e44-119">Os métodos de análise de data e hora não usam regras ajustadas para a análise de cadeias de caracteres de data que contêm apenas um designador de dia, mês, hora e AM/PM.</span><span class="sxs-lookup"><span data-stu-id="73e44-119">Date and time parsing methods do not use adjusted rules for parsing date strings that contain only a day, month, hour, and AM/PM designator.</span></span>|  
|<span data-ttu-id="73e44-120">1</span><span class="sxs-lookup"><span data-stu-id="73e44-120">1</span></span>|<span data-ttu-id="73e44-121">Os métodos de análise de data e hora usam regras ajustadas para a análise de cadeias de caracteres de data que contêm apenas um designador de dia, mês, hora e AM/PM.</span><span class="sxs-lookup"><span data-stu-id="73e44-121">Date and time parsing methods use adjusted rules for parsing date strings that contain only a day, month, hour, and AM/PM designator.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="73e44-122">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="73e44-122">Child Elements</span></span>  
 <span data-ttu-id="73e44-123">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="73e44-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="73e44-124">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="73e44-124">Parent Elements</span></span>  
  
|<span data-ttu-id="73e44-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="73e44-125">Element</span></span>|<span data-ttu-id="73e44-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="73e44-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="73e44-127">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="73e44-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="73e44-128">Contém informações sobre opções de inicialização do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="73e44-128">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="73e44-129">Comentários</span><span class="sxs-lookup"><span data-stu-id="73e44-129">Remarks</span></span>  
 <span data-ttu-id="73e44-130">O `<EnableAmPmParseAdjustment>` elemento controla como os métodos a seguir analisam uma cadeia de caracteres de data que contém um dia e mês numéricos seguidos por uma hora e um designador AM/PM (como "4/10 6 am"):</span><span class="sxs-lookup"><span data-stu-id="73e44-130">The `<EnableAmPmParseAdjustment>` element controls how the following methods parse a date string that contains a numeric day and month followed by an hour and an AM/PM designator (such as "4/10 6 AM"):</span></span>  
  
- <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>  
  
- <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType>  
  
- <xref:System.DateTime.TryParse%2A?displayProperty=nameWithType>  
  
- <xref:System.DateTimeOffset.TryParse%2A?displayProperty=nameWithType>  
  
- <xref:System.Convert.ToDateTime%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="73e44-131">Nenhum outro padrão é afetado.</span><span class="sxs-lookup"><span data-stu-id="73e44-131">No other patterns are affected.</span></span>  
  
 <span data-ttu-id="73e44-132">O `<EnableAmPmParseAdjustment>` elemento não tem nenhum efeito <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType>nos métodos <xref:System.DateTime.TryParseExact%2A?displayProperty=nameWithType>, <xref:System.DateTimeOffset.ParseExact%2A?displayProperty=nameWithType>, e <xref:System.DateTimeOffset.TryParseExact%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="73e44-132">The `<EnableAmPmParseAdjustment>` element has no effect on the  <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType>,  <xref:System.DateTime.TryParseExact%2A?displayProperty=nameWithType>, <xref:System.DateTimeOffset.ParseExact%2A?displayProperty=nameWithType>, and <xref:System.DateTimeOffset.TryParseExact%2A?displayProperty=nameWithType> methods.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="73e44-133">No .NET Core e .NET Native, as regras de análise de AM/PM ajustadas são habilitadas por padrão.</span><span class="sxs-lookup"><span data-stu-id="73e44-133">In .NET Core and .NET Native, the adjusted AM/PM parsing rules are enabled by default.</span></span>  
  
 <span data-ttu-id="73e44-134">Se a regra de ajuste de análise não estiver habilitada, o primeiro dígito da cadeia de caracteres será interpretado como a hora do relógio de 12 horas e o restante da cadeia de caracteres, exceto o designador AM/PM, será ignorado.</span><span class="sxs-lookup"><span data-stu-id="73e44-134">If the parsing adjustment rule is not enabled, the first digit of the string is interpreted as the hour of the 12-hour clock, and the remainder of the string except for the AM/PM designator is ignored.</span></span> <span data-ttu-id="73e44-135">A data e a hora retornadas pelo método de análise consiste na data atual e na hora do dia extraídas da cadeia de caracteres de data.</span><span class="sxs-lookup"><span data-stu-id="73e44-135">The date and time returned by the parsing method consists of the current date and the hour of the day extracted from the date string.</span></span>  
  
 <span data-ttu-id="73e44-136">Se a regra de ajuste de análise estiver habilitada, o método de análise interpretará o dia e o mês como pertencentes ao ano atual e interpretará a hora como a hora do relógio de 12 horas.</span><span class="sxs-lookup"><span data-stu-id="73e44-136">If the parsing adjustment rule is enabled, parsing method interpret the day and month as belonging to the current year, and interpret the time as the hour of the 12-hour clock.</span></span>  
  
 <span data-ttu-id="73e44-137">A tabela a seguir ilustra a diferença no <xref:System.DateTime> valor quando o <xref:System.DateTime.Parse%28System.String%29?displayProperty=nameWithType> método é usado para analisar a cadeia de caracteres "" 4/10 6 am " `<EnableAmPmParseAdjustment>` com a `enabled` Propriedade do elemento definida como" 0 "ou" 1 ".</span><span class="sxs-lookup"><span data-stu-id="73e44-137">The following table illustrates the difference in the <xref:System.DateTime> value when the <xref:System.DateTime.Parse%28System.String%29?displayProperty=nameWithType> method is used to parse the string ""4/10 6 AM" with the `<EnableAmPmParseAdjustment>` element's `enabled` property  set to "0" or "1".</span></span> <span data-ttu-id="73e44-138">Ele assume que a data de hoje é 5 de janeiro de 2017 e exibe a data como se ela fosse formatada usando a cadeia de caracteres de formato "G" da cultura especificada.</span><span class="sxs-lookup"><span data-stu-id="73e44-138">It assumes that today's date is January 5, 2017, and displays the date as if it is formatted using the specified culture's "G" format string.</span></span>  
  
|<span data-ttu-id="73e44-139">Nome da cultura</span><span class="sxs-lookup"><span data-stu-id="73e44-139">Culture name</span></span>|<span data-ttu-id="73e44-140">enabled="0"</span><span class="sxs-lookup"><span data-stu-id="73e44-140">enabled="0"</span></span>|<span data-ttu-id="73e44-141">enabled="1"</span><span class="sxs-lookup"><span data-stu-id="73e44-141">enabled="1"</span></span>|  
|------------------|------------------|------------------|  
|<span data-ttu-id="73e44-142">en-US</span><span class="sxs-lookup"><span data-stu-id="73e44-142">en-US</span></span>|<span data-ttu-id="73e44-143">1/5/2017 4:00:00 AM</span><span class="sxs-lookup"><span data-stu-id="73e44-143">1/5/2017 4:00:00 AM</span></span>|<span data-ttu-id="73e44-144">4/10/2017 6:00:00 AM</span><span class="sxs-lookup"><span data-stu-id="73e44-144">4/10/2017 6:00:00 AM</span></span>|  
|<span data-ttu-id="73e44-145">en-GB</span><span class="sxs-lookup"><span data-stu-id="73e44-145">en-GB</span></span>|<span data-ttu-id="73e44-146">5/1/2017 6:00:00</span><span class="sxs-lookup"><span data-stu-id="73e44-146">5/1/2017 6:00:00</span></span>|<span data-ttu-id="73e44-147">10/4/2017 6:00:00</span><span class="sxs-lookup"><span data-stu-id="73e44-147">10/4/2017 6:00:00</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="73e44-148">Consulte também</span><span class="sxs-lookup"><span data-stu-id="73e44-148">See also</span></span>

- [<span data-ttu-id="73e44-149">\<Elemento de > de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="73e44-149">\<runtime> Element</span></span>](runtime-element.md)
- [<span data-ttu-id="73e44-150">Elemento \<configuration></span><span class="sxs-lookup"><span data-stu-id="73e44-150">\<configuration> Element</span></span>](../configuration-element.md)
