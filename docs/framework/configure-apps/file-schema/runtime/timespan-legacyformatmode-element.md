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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f16a2bbd2470b4aec9e95ab67ccb0e736c4c6d02
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920682"
---
# <a name="timespan_legacyformatmode-element"></a><span data-ttu-id="11996-102">\<Elemento de > TimeSpan_LegacyFormatMode</span><span class="sxs-lookup"><span data-stu-id="11996-102">\<TimeSpan_LegacyFormatMode> Element</span></span>

<span data-ttu-id="11996-103">Determina se o tempo de execução preserva o comportamento herdado nas operações <xref:System.TimeSpan?displayProperty=nameWithType> de formatação com valores.</span><span class="sxs-lookup"><span data-stu-id="11996-103">Determines whether the runtime preserves legacy behavior in formatting operations with <xref:System.TimeSpan?displayProperty=nameWithType> values.</span></span>

<span data-ttu-id="11996-104">\<> de configuração </span><span class="sxs-lookup"><span data-stu-id="11996-104">\<configuration></span></span>\
<span data-ttu-id="11996-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="11996-105">\<runtime></span></span>\
<span data-ttu-id="11996-106">\<TimeSpan_LegacyFormatMode></span><span class="sxs-lookup"><span data-stu-id="11996-106">\<TimeSpan_LegacyFormatMode></span></span>

## <a name="syntax"></a><span data-ttu-id="11996-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="11996-107">Syntax</span></span>

```xml
<TimeSpan_LegacyFormatMode
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="11996-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="11996-108">Attributes and Elements</span></span>

<span data-ttu-id="11996-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="11996-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="11996-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="11996-110">Attributes</span></span>

|<span data-ttu-id="11996-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="11996-111">Attribute</span></span>|<span data-ttu-id="11996-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="11996-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="11996-113">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="11996-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="11996-114">Especifica se o tempo de execução usa comportamento de <xref:System.TimeSpan?displayProperty=nameWithType> formatação herdado com valores.</span><span class="sxs-lookup"><span data-stu-id="11996-114">Specifies whether the runtime uses legacy formatting behavior with <xref:System.TimeSpan?displayProperty=nameWithType> values.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="11996-115">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="11996-115">enabled Attribute</span></span>

|<span data-ttu-id="11996-116">Valor</span><span class="sxs-lookup"><span data-stu-id="11996-116">Value</span></span>|<span data-ttu-id="11996-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="11996-117">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="11996-118">O tempo de execução não restaura o comportamento de formatação herdado.</span><span class="sxs-lookup"><span data-stu-id="11996-118">The runtime does not restore legacy formatting behavior.</span></span>|
|`true`|<span data-ttu-id="11996-119">O tempo de execução restaura o comportamento de formatação herdado.</span><span class="sxs-lookup"><span data-stu-id="11996-119">The runtime restores legacy formatting behavior.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="11996-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="11996-120">Child Elements</span></span>

<span data-ttu-id="11996-121">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="11996-121">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="11996-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="11996-122">Parent Elements</span></span>

|<span data-ttu-id="11996-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="11996-123">Element</span></span>|<span data-ttu-id="11996-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="11996-124">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="11996-125">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="11996-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="11996-126">Contém informações sobre opções de inicialização do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="11996-126">Contains information about runtime initialization options.</span></span>|

## <a name="remarks"></a><span data-ttu-id="11996-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="11996-127">Remarks</span></span>

<span data-ttu-id="11996-128">Começando com o .NET Framework 4, a <xref:System.TimeSpan?displayProperty=nameWithType> estrutura implementa a <xref:System.IFormattable> interface e dá suporte a operações de formatação com cadeias de caracteres de formato padrão e personalizadas.</span><span class="sxs-lookup"><span data-stu-id="11996-128">Starting with the .NET Framework 4, the <xref:System.TimeSpan?displayProperty=nameWithType> structure implements the <xref:System.IFormattable> interface and supports formatting operations with standard and custom format strings.</span></span> <span data-ttu-id="11996-129">Se um método de análise encontrar um especificador de formato sem suporte ou uma cadeia de caracteres de <xref:System.FormatException>formato, ele lançará um.</span><span class="sxs-lookup"><span data-stu-id="11996-129">If a parsing method encounters an unsupported format specifier or format string, it throws a <xref:System.FormatException>.</span></span>

<span data-ttu-id="11996-130">Nas versões anteriores do .NET Framework, a estrutura <xref:System.TimeSpan> não implementou <xref:System.IFormattable> e não oferecia suporte a cadeias de caracteres de formato.</span><span class="sxs-lookup"><span data-stu-id="11996-130">In previous versions of the .NET Framework, the <xref:System.TimeSpan> structure did not implement <xref:System.IFormattable> and did not support format strings.</span></span> <span data-ttu-id="11996-131">No entanto, muitos desenvolvedores assumiram erroneamente <xref:System.TimeSpan> que davam suporte a um conjunto de cadeias de caracteres de formato e os usaram em <xref:System.String.Format%2A?displayProperty=nameWithType> [operações de formatação composta](../../../../standard/base-types/composite-formatting.md) com métodos como.</span><span class="sxs-lookup"><span data-stu-id="11996-131">However, many developers mistakenly assumed that <xref:System.TimeSpan> did support a set of format strings and used them in [composite formatting operations](../../../../standard/base-types/composite-formatting.md) with methods such as <xref:System.String.Format%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="11996-132">Normalmente, se um tipo implementa <xref:System.IFormattable> e dá suporte a cadeias de caracteres de formato, as chamadas para métodos de formatação com <xref:System.FormatException>cadeias de caracteres de formato sem suporte geralmente lançam um.</span><span class="sxs-lookup"><span data-stu-id="11996-132">Ordinarily, if a type implements <xref:System.IFormattable> and supports format strings, calls to formatting methods with unsupported format strings usually throw a <xref:System.FormatException>.</span></span> <span data-ttu-id="11996-133">No entanto <xref:System.TimeSpan> , como o <xref:System.IFormattable>não foi implementado, o Runtime ignorou a cadeia de <xref:System.TimeSpan.ToString?displayProperty=nameWithType> caracteres de formato e, em vez disso, chamou o método.</span><span class="sxs-lookup"><span data-stu-id="11996-133">However, because <xref:System.TimeSpan> did not implement <xref:System.IFormattable>, the runtime ignored the format string and instead called the <xref:System.TimeSpan.ToString?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="11996-134">Isso significa que, embora as cadeias de caracteres de formato não tenham efeito sobre a operação de formatação, sua presença <xref:System.FormatException>não resultou em um.</span><span class="sxs-lookup"><span data-stu-id="11996-134">This means that, although the format strings had no effect on the formatting operation, their presence did not result in a <xref:System.FormatException>.</span></span>

<span data-ttu-id="11996-135">Para casos em que o código herdado passa um método de formatação composto e uma cadeia de caracteres de formato inválida, e esse código não pode ser `<TimeSpan_LegacyFormatMode>` recompilado, você pode <xref:System.TimeSpan> usar o elemento para restaurar o comportamento herdado.</span><span class="sxs-lookup"><span data-stu-id="11996-135">For cases in which legacy code passes a composite formatting method and an invalid format string, and that code cannot be recompiled, you can use the `<TimeSpan_LegacyFormatMode>` element to restore the legacy <xref:System.TimeSpan> behavior.</span></span> <span data-ttu-id="11996-136">Quando você define o `enabled` atributo desse elemento como `true`, o método de formatação composta resulta em uma chamada para <xref:System.TimeSpan.ToString?displayProperty=nameWithType> em vez <xref:System.TimeSpan.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>de e um <xref:System.FormatException> não é gerado.</span><span class="sxs-lookup"><span data-stu-id="11996-136">When you set the `enabled` attribute of this element to `true`, the composite formatting method results in a call to <xref:System.TimeSpan.ToString?displayProperty=nameWithType> rather than <xref:System.TimeSpan.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>, and a <xref:System.FormatException> is not thrown.</span></span>

## <a name="example"></a><span data-ttu-id="11996-137">Exemplo</span><span class="sxs-lookup"><span data-stu-id="11996-137">Example</span></span>

<span data-ttu-id="11996-138">O exemplo a seguir instancia um <xref:System.TimeSpan> objeto e tenta formatá-lo com <xref:System.String.Format%28System.String%2CSystem.Object%29?displayProperty=nameWithType> o método usando uma cadeia de caracteres de formato padrão sem suporte.</span><span class="sxs-lookup"><span data-stu-id="11996-138">The following example instantiates a <xref:System.TimeSpan> object and attempts to format it with the <xref:System.String.Format%28System.String%2CSystem.Object%29?displayProperty=nameWithType> method by using an unsupported standard format string.</span></span>

[!code-csharp[TimeSpan.BreakingChanges#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/timespan.breakingchanges/cs/legacyformatmode1.cs#1)]
[!code-vb[TimeSpan.BreakingChanges#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/timespan.breakingchanges/vb/legacyformatmode1.vb#1)]

<span data-ttu-id="11996-139">Quando você executa o exemplo no .NET Framework 3,5 ou em uma versão anterior, ele exibe a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="11996-139">When you run the example on the .NET Framework 3.5 or on an earlier version, it displays the following output:</span></span>

```
12:30:45
```

<span data-ttu-id="11996-140">Isso difere de acordo com a saída se você executar o exemplo na versão .NET Framework 4 ou posterior:</span><span class="sxs-lookup"><span data-stu-id="11996-140">This differs markedly from the output if you run the example on the .NET Framework 4 or later version:</span></span>

```
Invalid Format
```

<span data-ttu-id="11996-141">No entanto, se você adicionar o seguinte arquivo de configuração ao diretório do exemplo e, em seguida, executar o exemplo na versão .NET Framework 4 ou posterior, a saída será idêntica à produzida pelo exemplo quando for executada em .NET Framework 3,5.</span><span class="sxs-lookup"><span data-stu-id="11996-141">However, if you add the following configuration file to the example's directory and then run the example on the .NET Framework 4 or later version, the output is identical to that produced by the example when it is run on .NET Framework 3.5.</span></span>

```xml
<?xml version ="1.0"?>
<configuration>
   <runtime>
      <TimeSpan_LegacyFormatMode enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="11996-142">Consulte também</span><span class="sxs-lookup"><span data-stu-id="11996-142">See also</span></span>

- [<span data-ttu-id="11996-143">Esquema de configurações do tempo de execução</span><span class="sxs-lookup"><span data-stu-id="11996-143">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="11996-144">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="11996-144">Configuration File Schema</span></span>](../index.md)
