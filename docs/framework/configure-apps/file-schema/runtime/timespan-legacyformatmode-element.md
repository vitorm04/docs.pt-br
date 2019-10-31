---
title: Elemento <TimeSpan_LegacyFormatMode>
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- <TimeSpan_LegacyFormatMode> element
- TimeSpan_LegacyFormatMode element
ms.assetid: 865e7207-d050-4442-b574-57ea29d5e2d6
ms.openlocfilehash: c835e1bcef7bbfdc990c8db177eafed4ec6bb30c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73115208"
---
# <a name="timespan_legacyformatmode-element"></a><span data-ttu-id="76819-102">\<elemento de > TimeSpan_LegacyFormatMode</span><span class="sxs-lookup"><span data-stu-id="76819-102">\<TimeSpan_LegacyFormatMode> Element</span></span>

<span data-ttu-id="76819-103">Determina se o tempo de execução preserva o comportamento herdado nas operações de formatação com <xref:System.TimeSpan?displayProperty=nameWithType> valores.</span><span class="sxs-lookup"><span data-stu-id="76819-103">Determines whether the runtime preserves legacy behavior in formatting operations with <xref:System.TimeSpan?displayProperty=nameWithType> values.</span></span>

<span data-ttu-id="76819-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="76819-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="76819-105">&nbsp; &nbsp;[ **\<runtime >** ](runtime-element.md) </span><span class="sxs-lookup"><span data-stu-id="76819-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="76819-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<TimeSpan_LegacyFormatMode >**</span><span class="sxs-lookup"><span data-stu-id="76819-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<TimeSpan_LegacyFormatMode>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="76819-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="76819-107">Syntax</span></span>

```xml
<TimeSpan_LegacyFormatMode
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="76819-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="76819-108">Attributes and Elements</span></span>

<span data-ttu-id="76819-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="76819-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="76819-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="76819-110">Attributes</span></span>

|<span data-ttu-id="76819-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="76819-111">Attribute</span></span>|<span data-ttu-id="76819-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="76819-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="76819-113">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="76819-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="76819-114">Especifica se o tempo de execução usa comportamento de formatação herdado com <xref:System.TimeSpan?displayProperty=nameWithType> valores.</span><span class="sxs-lookup"><span data-stu-id="76819-114">Specifies whether the runtime uses legacy formatting behavior with <xref:System.TimeSpan?displayProperty=nameWithType> values.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="76819-115">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="76819-115">enabled Attribute</span></span>

|<span data-ttu-id="76819-116">Valor</span><span class="sxs-lookup"><span data-stu-id="76819-116">Value</span></span>|<span data-ttu-id="76819-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="76819-117">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="76819-118">O tempo de execução não restaura o comportamento de formatação herdado.</span><span class="sxs-lookup"><span data-stu-id="76819-118">The runtime does not restore legacy formatting behavior.</span></span>|
|`true`|<span data-ttu-id="76819-119">O tempo de execução restaura o comportamento de formatação herdado.</span><span class="sxs-lookup"><span data-stu-id="76819-119">The runtime restores legacy formatting behavior.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="76819-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="76819-120">Child Elements</span></span>

<span data-ttu-id="76819-121">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="76819-121">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="76819-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="76819-122">Parent Elements</span></span>

|<span data-ttu-id="76819-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="76819-123">Element</span></span>|<span data-ttu-id="76819-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="76819-124">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="76819-125">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="76819-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="76819-126">Contém informações sobre opções de inicialização do runtime.</span><span class="sxs-lookup"><span data-stu-id="76819-126">Contains information about runtime initialization options.</span></span>|

## <a name="remarks"></a><span data-ttu-id="76819-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="76819-127">Remarks</span></span>

<span data-ttu-id="76819-128">Começando com o .NET Framework 4, a estrutura de <xref:System.TimeSpan?displayProperty=nameWithType> implementa a interface <xref:System.IFormattable> e dá suporte a operações de formatação com cadeias de caracteres de formato padrão e personalizadas.</span><span class="sxs-lookup"><span data-stu-id="76819-128">Starting with the .NET Framework 4, the <xref:System.TimeSpan?displayProperty=nameWithType> structure implements the <xref:System.IFormattable> interface and supports formatting operations with standard and custom format strings.</span></span> <span data-ttu-id="76819-129">Se um método de análise encontrar um especificador de formato sem suporte ou uma cadeia de caracteres de formato, ele lançará um <xref:System.FormatException>.</span><span class="sxs-lookup"><span data-stu-id="76819-129">If a parsing method encounters an unsupported format specifier or format string, it throws a <xref:System.FormatException>.</span></span>

<span data-ttu-id="76819-130">Nas versões anteriores do .NET Framework, a estrutura de <xref:System.TimeSpan> não implementou <xref:System.IFormattable> e não oferecia suporte a cadeias de caracteres de formato.</span><span class="sxs-lookup"><span data-stu-id="76819-130">In previous versions of the .NET Framework, the <xref:System.TimeSpan> structure did not implement <xref:System.IFormattable> and did not support format strings.</span></span> <span data-ttu-id="76819-131">No entanto, muitos desenvolvedores assumiram erroneamente que <xref:System.TimeSpan> davam suporte a um conjunto de cadeias de caracteres de formato e os usaram em [operações de formatação composta](../../../../standard/base-types/composite-formatting.md) com métodos como <xref:System.String.Format%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="76819-131">However, many developers mistakenly assumed that <xref:System.TimeSpan> did support a set of format strings and used them in [composite formatting operations](../../../../standard/base-types/composite-formatting.md) with methods such as <xref:System.String.Format%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="76819-132">Normalmente, se um tipo implementa <xref:System.IFormattable> e dá suporte a cadeias de caracteres de formato, as chamadas para métodos de formatação com cadeias de caracteres de formato sem suporte geralmente geram um <xref:System.FormatException>.</span><span class="sxs-lookup"><span data-stu-id="76819-132">Ordinarily, if a type implements <xref:System.IFormattable> and supports format strings, calls to formatting methods with unsupported format strings usually throw a <xref:System.FormatException>.</span></span> <span data-ttu-id="76819-133">No entanto, como <xref:System.TimeSpan> não implementou <xref:System.IFormattable>, o tempo de execução ignorou a cadeia de caracteres de formato e, em vez disso, chamou o método <xref:System.TimeSpan.ToString?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="76819-133">However, because <xref:System.TimeSpan> did not implement <xref:System.IFormattable>, the runtime ignored the format string and instead called the <xref:System.TimeSpan.ToString?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="76819-134">Isso significa que, embora as cadeias de caracteres de formato não tenham efeito sobre a operação de formatação, sua presença não resultou em um <xref:System.FormatException>.</span><span class="sxs-lookup"><span data-stu-id="76819-134">This means that, although the format strings had no effect on the formatting operation, their presence did not result in a <xref:System.FormatException>.</span></span>

<span data-ttu-id="76819-135">Para casos em que o código herdado passa um método de formatação composto e uma cadeia de caracteres de formato inválida, e esse código não pode ser recompilado, você pode usar o elemento `<TimeSpan_LegacyFormatMode>` para restaurar o comportamento de <xref:System.TimeSpan> herdado.</span><span class="sxs-lookup"><span data-stu-id="76819-135">For cases in which legacy code passes a composite formatting method and an invalid format string, and that code cannot be recompiled, you can use the `<TimeSpan_LegacyFormatMode>` element to restore the legacy <xref:System.TimeSpan> behavior.</span></span> <span data-ttu-id="76819-136">Quando você define o atributo `enabled` desse elemento como `true`, o método de formatação composta resulta em uma chamada para <xref:System.TimeSpan.ToString?displayProperty=nameWithType> em vez de <xref:System.TimeSpan.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>e uma <xref:System.FormatException> não é gerada.</span><span class="sxs-lookup"><span data-stu-id="76819-136">When you set the `enabled` attribute of this element to `true`, the composite formatting method results in a call to <xref:System.TimeSpan.ToString?displayProperty=nameWithType> rather than <xref:System.TimeSpan.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>, and a <xref:System.FormatException> is not thrown.</span></span>

## <a name="example"></a><span data-ttu-id="76819-137">Exemplo</span><span class="sxs-lookup"><span data-stu-id="76819-137">Example</span></span>

<span data-ttu-id="76819-138">O exemplo a seguir instancia um objeto <xref:System.TimeSpan> e tenta formatá-lo com o método <xref:System.String.Format%28System.String%2CSystem.Object%29?displayProperty=nameWithType> usando uma cadeia de caracteres de formato padrão sem suporte.</span><span class="sxs-lookup"><span data-stu-id="76819-138">The following example instantiates a <xref:System.TimeSpan> object and attempts to format it with the <xref:System.String.Format%28System.String%2CSystem.Object%29?displayProperty=nameWithType> method by using an unsupported standard format string.</span></span>

[!code-csharp[TimeSpan.BreakingChanges#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/timespan.breakingchanges/cs/legacyformatmode1.cs#1)]
[!code-vb[TimeSpan.BreakingChanges#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/timespan.breakingchanges/vb/legacyformatmode1.vb#1)]

<span data-ttu-id="76819-139">Quando você executa o exemplo no .NET Framework 3,5 ou em uma versão anterior, ele exibe a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="76819-139">When you run the example on the .NET Framework 3.5 or on an earlier version, it displays the following output:</span></span>

```
12:30:45
```

<span data-ttu-id="76819-140">Isso difere de acordo com a saída se você executar o exemplo na versão .NET Framework 4 ou posterior:</span><span class="sxs-lookup"><span data-stu-id="76819-140">This differs markedly from the output if you run the example on the .NET Framework 4 or later version:</span></span>

```
Invalid Format
```

<span data-ttu-id="76819-141">No entanto, se você adicionar o seguinte arquivo de configuração ao diretório do exemplo e, em seguida, executar o exemplo na versão .NET Framework 4 ou posterior, a saída será idêntica à produzida pelo exemplo quando for executada em .NET Framework 3,5.</span><span class="sxs-lookup"><span data-stu-id="76819-141">However, if you add the following configuration file to the example's directory and then run the example on the .NET Framework 4 or later version, the output is identical to that produced by the example when it is run on .NET Framework 3.5.</span></span>

```xml
<?xml version ="1.0"?>
<configuration>
   <runtime>
      <TimeSpan_LegacyFormatMode enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="76819-142">Consulte também</span><span class="sxs-lookup"><span data-stu-id="76819-142">See also</span></span>

- [<span data-ttu-id="76819-143">Esquema de configurações do tempo de execução</span><span class="sxs-lookup"><span data-stu-id="76819-143">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="76819-144">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="76819-144">Configuration File Schema</span></span>](../index.md)
