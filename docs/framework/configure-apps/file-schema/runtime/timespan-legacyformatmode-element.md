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
ms.openlocfilehash: 9d9eedf52f5d711412e4549e39e6ea23abb68ff3
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73968900"
---
# <a name="timespan_legacyformatmode-element"></a><span data-ttu-id="acdaa-102">Elemento \<TimeSpan_LegacyFormatMode></span><span class="sxs-lookup"><span data-stu-id="acdaa-102">\<TimeSpan_LegacyFormatMode> Element</span></span>

<span data-ttu-id="acdaa-103">Determina se o tempo de execução preserva o comportamento herdado nas operações de formatação com <xref:System.TimeSpan?displayProperty=nameWithType> valores.</span><span class="sxs-lookup"><span data-stu-id="acdaa-103">Determines whether the runtime preserves legacy behavior in formatting operations with <xref:System.TimeSpan?displayProperty=nameWithType> values.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<TimeSpan_LegacyFormatMode>**  

## <a name="syntax"></a><span data-ttu-id="acdaa-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="acdaa-104">Syntax</span></span>

```xml
<TimeSpan_LegacyFormatMode
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="acdaa-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="acdaa-105">Attributes and Elements</span></span>

<span data-ttu-id="acdaa-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="acdaa-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="acdaa-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="acdaa-107">Attributes</span></span>

|<span data-ttu-id="acdaa-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="acdaa-108">Attribute</span></span>|<span data-ttu-id="acdaa-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="acdaa-109">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="acdaa-110">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="acdaa-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="acdaa-111">Especifica se o tempo de execução usa comportamento de formatação herdado com <xref:System.TimeSpan?displayProperty=nameWithType> valores.</span><span class="sxs-lookup"><span data-stu-id="acdaa-111">Specifies whether the runtime uses legacy formatting behavior with <xref:System.TimeSpan?displayProperty=nameWithType> values.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="acdaa-112">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="acdaa-112">enabled Attribute</span></span>

|<span data-ttu-id="acdaa-113">Valor</span><span class="sxs-lookup"><span data-stu-id="acdaa-113">Value</span></span>|<span data-ttu-id="acdaa-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="acdaa-114">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="acdaa-115">O tempo de execução não restaura o comportamento de formatação herdado.</span><span class="sxs-lookup"><span data-stu-id="acdaa-115">The runtime does not restore legacy formatting behavior.</span></span>|
|`true`|<span data-ttu-id="acdaa-116">O tempo de execução restaura o comportamento de formatação herdado.</span><span class="sxs-lookup"><span data-stu-id="acdaa-116">The runtime restores legacy formatting behavior.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="acdaa-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="acdaa-117">Child Elements</span></span>

<span data-ttu-id="acdaa-118">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="acdaa-118">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="acdaa-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="acdaa-119">Parent Elements</span></span>

|<span data-ttu-id="acdaa-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="acdaa-120">Element</span></span>|<span data-ttu-id="acdaa-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="acdaa-121">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="acdaa-122">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="acdaa-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="acdaa-123">Contém informações sobre opções de inicialização do runtime.</span><span class="sxs-lookup"><span data-stu-id="acdaa-123">Contains information about runtime initialization options.</span></span>|

## <a name="remarks"></a><span data-ttu-id="acdaa-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="acdaa-124">Remarks</span></span>

<span data-ttu-id="acdaa-125">Começando com o .NET Framework 4, a <xref:System.TimeSpan?displayProperty=nameWithType> estrutura implementa a <xref:System.IFormattable> interface e dá suporte a operações de formatação com cadeias de caracteres de formato padrão e personalizadas.</span><span class="sxs-lookup"><span data-stu-id="acdaa-125">Starting with the .NET Framework 4, the <xref:System.TimeSpan?displayProperty=nameWithType> structure implements the <xref:System.IFormattable> interface and supports formatting operations with standard and custom format strings.</span></span> <span data-ttu-id="acdaa-126">Se um método de análise encontrar um especificador de formato sem suporte ou uma cadeia de caracteres de formato, ele lançará um <xref:System.FormatException> .</span><span class="sxs-lookup"><span data-stu-id="acdaa-126">If a parsing method encounters an unsupported format specifier or format string, it throws a <xref:System.FormatException>.</span></span>

<span data-ttu-id="acdaa-127">Nas versões anteriores do .NET Framework, a <xref:System.TimeSpan> estrutura não implementou <xref:System.IFormattable> e não oferecia suporte a cadeias de caracteres de formato.</span><span class="sxs-lookup"><span data-stu-id="acdaa-127">In previous versions of the .NET Framework, the <xref:System.TimeSpan> structure did not implement <xref:System.IFormattable> and did not support format strings.</span></span> <span data-ttu-id="acdaa-128">No entanto, muitos desenvolvedores assumiram erroneamente que <xref:System.TimeSpan> davam suporte a um conjunto de cadeias de caracteres de formato e os usaram em [operações de formatação composta](../../../../standard/base-types/composite-formatting.md) com métodos como <xref:System.String.Format%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="acdaa-128">However, many developers mistakenly assumed that <xref:System.TimeSpan> did support a set of format strings and used them in [composite formatting operations](../../../../standard/base-types/composite-formatting.md) with methods such as <xref:System.String.Format%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="acdaa-129">Normalmente, se um tipo implementa <xref:System.IFormattable> e dá suporte a cadeias de caracteres de formato, as chamadas para métodos de formatação com cadeias de caracteres de formato sem suporte geralmente lançam um <xref:System.FormatException> .</span><span class="sxs-lookup"><span data-stu-id="acdaa-129">Ordinarily, if a type implements <xref:System.IFormattable> and supports format strings, calls to formatting methods with unsupported format strings usually throw a <xref:System.FormatException>.</span></span> <span data-ttu-id="acdaa-130">No entanto, como <xref:System.TimeSpan> o não foi implementado <xref:System.IFormattable> , o Runtime ignorou a cadeia de caracteres de formato e, em vez disso, chamou o <xref:System.TimeSpan.ToString?displayProperty=nameWithType> método.</span><span class="sxs-lookup"><span data-stu-id="acdaa-130">However, because <xref:System.TimeSpan> did not implement <xref:System.IFormattable>, the runtime ignored the format string and instead called the <xref:System.TimeSpan.ToString?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="acdaa-131">Isso significa que, embora as cadeias de caracteres de formato não tenham efeito sobre a operação de formatação, sua presença não resultou em um <xref:System.FormatException> .</span><span class="sxs-lookup"><span data-stu-id="acdaa-131">This means that, although the format strings had no effect on the formatting operation, their presence did not result in a <xref:System.FormatException>.</span></span>

<span data-ttu-id="acdaa-132">Para casos em que o código herdado passa um método de formatação composto e uma cadeia de caracteres de formato inválida, e esse código não pode ser recompilado, você pode usar o `<TimeSpan_LegacyFormatMode>` elemento para restaurar o comportamento herdado <xref:System.TimeSpan> .</span><span class="sxs-lookup"><span data-stu-id="acdaa-132">For cases in which legacy code passes a composite formatting method and an invalid format string, and that code cannot be recompiled, you can use the `<TimeSpan_LegacyFormatMode>` element to restore the legacy <xref:System.TimeSpan> behavior.</span></span> <span data-ttu-id="acdaa-133">Quando você define o `enabled` atributo desse elemento como `true` , o método de formatação composta resulta em uma chamada para <xref:System.TimeSpan.ToString?displayProperty=nameWithType> em vez de <xref:System.TimeSpan.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> e um <xref:System.FormatException> não é gerado.</span><span class="sxs-lookup"><span data-stu-id="acdaa-133">When you set the `enabled` attribute of this element to `true`, the composite formatting method results in a call to <xref:System.TimeSpan.ToString?displayProperty=nameWithType> rather than <xref:System.TimeSpan.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>, and a <xref:System.FormatException> is not thrown.</span></span>

## <a name="example"></a><span data-ttu-id="acdaa-134">Exemplo</span><span class="sxs-lookup"><span data-stu-id="acdaa-134">Example</span></span>

<span data-ttu-id="acdaa-135">O exemplo a seguir instancia um <xref:System.TimeSpan> objeto e tenta formatá-lo com o <xref:System.String.Format%28System.String%2CSystem.Object%29?displayProperty=nameWithType> método usando uma cadeia de caracteres de formato padrão sem suporte.</span><span class="sxs-lookup"><span data-stu-id="acdaa-135">The following example instantiates a <xref:System.TimeSpan> object and attempts to format it with the <xref:System.String.Format%28System.String%2CSystem.Object%29?displayProperty=nameWithType> method by using an unsupported standard format string.</span></span>

[!code-csharp[TimeSpan.BreakingChanges#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/timespan.breakingchanges/cs/legacyformatmode1.cs#1)]
[!code-vb[TimeSpan.BreakingChanges#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/timespan.breakingchanges/vb/legacyformatmode1.vb#1)]

<span data-ttu-id="acdaa-136">Quando você executa o exemplo no .NET Framework 3,5 ou em uma versão anterior, ele exibe a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="acdaa-136">When you run the example on the .NET Framework 3.5 or on an earlier version, it displays the following output:</span></span>

```console
12:30:45
```

<span data-ttu-id="acdaa-137">Isso difere de acordo com a saída se você executar o exemplo na versão .NET Framework 4 ou posterior:</span><span class="sxs-lookup"><span data-stu-id="acdaa-137">This differs markedly from the output if you run the example on the .NET Framework 4 or later version:</span></span>

```console
Invalid Format
```

<span data-ttu-id="acdaa-138">No entanto, se você adicionar o seguinte arquivo de configuração ao diretório do exemplo e, em seguida, executar o exemplo na versão .NET Framework 4 ou posterior, a saída será idêntica à produzida pelo exemplo quando for executada em .NET Framework 3,5.</span><span class="sxs-lookup"><span data-stu-id="acdaa-138">However, if you add the following configuration file to the example's directory and then run the example on the .NET Framework 4 or later version, the output is identical to that produced by the example when it is run on .NET Framework 3.5.</span></span>

```xml
<?xml version ="1.0"?>
<configuration>
   <runtime>
      <TimeSpan_LegacyFormatMode enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="acdaa-139">Confira também</span><span class="sxs-lookup"><span data-stu-id="acdaa-139">See also</span></span>

- [<span data-ttu-id="acdaa-140">Esquema de configurações do runtime</span><span class="sxs-lookup"><span data-stu-id="acdaa-140">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="acdaa-141">Esquema do arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="acdaa-141">Configuration File Schema</span></span>](../index.md)
