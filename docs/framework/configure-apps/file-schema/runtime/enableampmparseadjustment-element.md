---
title: Elemento <EnableAmPmParseAdjustment>
ms.date: 03/30/2017
ms.assetid: fda998a5-f538-4f8b-a18c-ee7f35e16938
ms.openlocfilehash: f935f213e1bca8dac7a5401970bc6183575e2301
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91167223"
---
# <a name="enableampmparseadjustment-element"></a><span data-ttu-id="23798-102">Elemento \<EnableAmPmParseAdjustment></span><span class="sxs-lookup"><span data-stu-id="23798-102">\<EnableAmPmParseAdjustment> Element</span></span>

<span data-ttu-id="23798-103">Determina se os métodos de análise de data e hora usam um conjunto ajustado de regras para analisar as cadeias de caracteres de data que contêm um designador de dia, mês, hora e AM/PM.</span><span class="sxs-lookup"><span data-stu-id="23798-103">Determines whether date and time parsing methods use an adjusted set of rules to parse date strings that contain a day, month, hour, and AM/PM designator.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<EnableAmPmParseAdjustment>**  
  
## <a name="syntax"></a><span data-ttu-id="23798-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="23798-104">Syntax</span></span>  
  
```xml  
<EnableAmPmParseAdjustment enabled="0"|"1" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="23798-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="23798-105">Attributes and Elements</span></span>  

 <span data-ttu-id="23798-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="23798-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="23798-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="23798-107">Attributes</span></span>  
  
|<span data-ttu-id="23798-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="23798-108">Attribute</span></span>|<span data-ttu-id="23798-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="23798-109">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="23798-110">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="23798-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="23798-111">Especifica se os métodos de análise de data e hora usam um conjunto ajustado de regras para analisar cadeias de caracteres de data que contêm apenas um designador de dia, mês, hora e AM/PM.</span><span class="sxs-lookup"><span data-stu-id="23798-111">Specifies whether date and time parsing methods use an adjusted set of rules to parse date strings that contain only a day, month, hour, and AM/PM designator.</span></span>|  
  
### <a name="enabled-attribute"></a><span data-ttu-id="23798-112">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="23798-112">enabled Attribute</span></span>  
  
|<span data-ttu-id="23798-113">Valor</span><span class="sxs-lookup"><span data-stu-id="23798-113">Value</span></span>|<span data-ttu-id="23798-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="23798-114">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="23798-115">0</span><span class="sxs-lookup"><span data-stu-id="23798-115">0</span></span>|<span data-ttu-id="23798-116">Os métodos de análise de data e hora não usam regras ajustadas para a análise de cadeias de caracteres de data que contêm apenas um designador de dia, mês, hora e AM/PM.</span><span class="sxs-lookup"><span data-stu-id="23798-116">Date and time parsing methods do not use adjusted rules for parsing date strings that contain only a day, month, hour, and AM/PM designator.</span></span>|  
|<span data-ttu-id="23798-117">1</span><span class="sxs-lookup"><span data-stu-id="23798-117">1</span></span>|<span data-ttu-id="23798-118">Os métodos de análise de data e hora usam regras ajustadas para a análise de cadeias de caracteres de data que contêm apenas um designador de dia, mês, hora e AM/PM.</span><span class="sxs-lookup"><span data-stu-id="23798-118">Date and time parsing methods use adjusted rules for parsing date strings that contain only a day, month, hour, and AM/PM designator.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="23798-119">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="23798-119">Child Elements</span></span>  

 <span data-ttu-id="23798-120">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="23798-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="23798-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="23798-121">Parent Elements</span></span>  
  
|<span data-ttu-id="23798-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="23798-122">Element</span></span>|<span data-ttu-id="23798-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="23798-123">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="23798-124">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="23798-124">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="23798-125">Contém informações sobre opções de inicialização do runtime.</span><span class="sxs-lookup"><span data-stu-id="23798-125">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="23798-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="23798-126">Remarks</span></span>  

 <span data-ttu-id="23798-127">O `<EnableAmPmParseAdjustment>` elemento controla como os métodos a seguir analisam uma cadeia de caracteres de data que contém um dia e mês numéricos seguidos por uma hora e um designador AM/PM (como "4/10 6 am"):</span><span class="sxs-lookup"><span data-stu-id="23798-127">The `<EnableAmPmParseAdjustment>` element controls how the following methods parse a date string that contains a numeric day and month followed by an hour and an AM/PM designator (such as "4/10 6 AM"):</span></span>  
  
- <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>  
  
- <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType>  
  
- <xref:System.DateTime.TryParse%2A?displayProperty=nameWithType>  
  
- <xref:System.DateTimeOffset.TryParse%2A?displayProperty=nameWithType>  
  
- <xref:System.Convert.ToDateTime%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="23798-128">Nenhum outro padrão é afetado.</span><span class="sxs-lookup"><span data-stu-id="23798-128">No other patterns are affected.</span></span>  
  
 <span data-ttu-id="23798-129">O `<EnableAmPmParseAdjustment>` elemento não tem nenhum efeito nos  <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType> métodos,,  <xref:System.DateTime.TryParseExact%2A?displayProperty=nameWithType> <xref:System.DateTimeOffset.ParseExact%2A?displayProperty=nameWithType> e <xref:System.DateTimeOffset.TryParseExact%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="23798-129">The `<EnableAmPmParseAdjustment>` element has no effect on the  <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType>,  <xref:System.DateTime.TryParseExact%2A?displayProperty=nameWithType>, <xref:System.DateTimeOffset.ParseExact%2A?displayProperty=nameWithType>, and <xref:System.DateTimeOffset.TryParseExact%2A?displayProperty=nameWithType> methods.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="23798-130">No .NET Core e .NET Native, as regras de análise de AM/PM ajustadas são habilitadas por padrão.</span><span class="sxs-lookup"><span data-stu-id="23798-130">In .NET Core and .NET Native, the adjusted AM/PM parsing rules are enabled by default.</span></span>  
  
 <span data-ttu-id="23798-131">Se a regra de ajuste de análise não estiver habilitada, o primeiro dígito da cadeia de caracteres será interpretado como a hora do relógio de 12 horas e o restante da cadeia de caracteres, exceto o designador AM/PM, será ignorado.</span><span class="sxs-lookup"><span data-stu-id="23798-131">If the parsing adjustment rule is not enabled, the first digit of the string is interpreted as the hour of the 12-hour clock, and the remainder of the string except for the AM/PM designator is ignored.</span></span> <span data-ttu-id="23798-132">A data e a hora retornadas pelo método de análise consiste na data atual e na hora do dia extraídas da cadeia de caracteres de data.</span><span class="sxs-lookup"><span data-stu-id="23798-132">The date and time returned by the parsing method consists of the current date and the hour of the day extracted from the date string.</span></span>  
  
 <span data-ttu-id="23798-133">Se a regra de ajuste de análise estiver habilitada, o método de análise interpretará o dia e o mês como pertencentes ao ano atual e interpretará a hora como a hora do relógio de 12 horas.</span><span class="sxs-lookup"><span data-stu-id="23798-133">If the parsing adjustment rule is enabled, parsing method interpret the day and month as belonging to the current year, and interpret the time as the hour of the 12-hour clock.</span></span>  
  
 <span data-ttu-id="23798-134">A tabela a seguir ilustra a diferença no <xref:System.DateTime> valor quando o <xref:System.DateTime.Parse%28System.String%29?displayProperty=nameWithType> método é usado para analisar a cadeia de caracteres "" 4/10 6 am "com a `<EnableAmPmParseAdjustment>` Propriedade do elemento `enabled` definida como" 0 "ou" 1 ".</span><span class="sxs-lookup"><span data-stu-id="23798-134">The following table illustrates the difference in the <xref:System.DateTime> value when the <xref:System.DateTime.Parse%28System.String%29?displayProperty=nameWithType> method is used to parse the string ""4/10 6 AM" with the `<EnableAmPmParseAdjustment>` element's `enabled` property  set to "0" or "1".</span></span> <span data-ttu-id="23798-135">Ele assume que a data de hoje é 5 de janeiro de 2017 e exibe a data como se ela fosse formatada usando a cadeia de caracteres de formato "G" da cultura especificada.</span><span class="sxs-lookup"><span data-stu-id="23798-135">It assumes that today's date is January 5, 2017, and displays the date as if it is formatted using the specified culture's "G" format string.</span></span>  
  
|<span data-ttu-id="23798-136">Nome da cultura</span><span class="sxs-lookup"><span data-stu-id="23798-136">Culture name</span></span>|<span data-ttu-id="23798-137">habilitado = "0"</span><span class="sxs-lookup"><span data-stu-id="23798-137">enabled="0"</span></span>|<span data-ttu-id="23798-138">habilitado = "1"</span><span class="sxs-lookup"><span data-stu-id="23798-138">enabled="1"</span></span>|  
|------------------|------------------|------------------|  
|<span data-ttu-id="23798-139">en-US</span><span class="sxs-lookup"><span data-stu-id="23798-139">en-US</span></span>|<span data-ttu-id="23798-140">1/5/2017 4:00:00 AM</span><span class="sxs-lookup"><span data-stu-id="23798-140">1/5/2017 4:00:00 AM</span></span>|<span data-ttu-id="23798-141">4/10/2017 6:00:00 AM</span><span class="sxs-lookup"><span data-stu-id="23798-141">4/10/2017 6:00:00 AM</span></span>|  
|<span data-ttu-id="23798-142">en-GB</span><span class="sxs-lookup"><span data-stu-id="23798-142">en-GB</span></span>|<span data-ttu-id="23798-143">5/1/2017 6:00:00</span><span class="sxs-lookup"><span data-stu-id="23798-143">5/1/2017 6:00:00</span></span>|<span data-ttu-id="23798-144">10/4/2017 6:00:00</span><span class="sxs-lookup"><span data-stu-id="23798-144">10/4/2017 6:00:00</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="23798-145">Confira também</span><span class="sxs-lookup"><span data-stu-id="23798-145">See also</span></span>

- [<span data-ttu-id="23798-146">\<runtime> Elementos</span><span class="sxs-lookup"><span data-stu-id="23798-146">\<runtime> Element</span></span>](runtime-element.md)
- [<span data-ttu-id="23798-147">\<configuration> Elementos</span><span class="sxs-lookup"><span data-stu-id="23798-147">\<configuration> Element</span></span>](../configuration-element.md)
