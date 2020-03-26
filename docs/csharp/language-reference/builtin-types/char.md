---
title: tipo char - referência C#
ms.date: 11/22/2019
f1_keywords:
- char
- char_CSharpKeyword
helpviewer_keywords:
- char data type [C#]
ms.assetid: b51cf4fb-124c-4067-af48-afbac122b228
ms.openlocfilehash: 8727e47e13082e8550fb174c92139dfd5c17ec36
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80134336"
---
# <a name="char-c-reference"></a><span data-ttu-id="d0ed3-102">char (referência C#)</span><span class="sxs-lookup"><span data-stu-id="d0ed3-102">char (C# reference)</span></span>

<span data-ttu-id="d0ed3-103">A `char` palavra-chave tipo é um <xref:System.Char?displayProperty=nameWithType> alias para o tipo de estrutura .NET que representa um caractere Unicode UTF-16.</span><span class="sxs-lookup"><span data-stu-id="d0ed3-103">The `char` type keyword is an alias for the .NET <xref:System.Char?displayProperty=nameWithType> structure type that represents a Unicode UTF-16 character.</span></span>

|<span data-ttu-id="d0ed3-104">Type</span><span class="sxs-lookup"><span data-stu-id="d0ed3-104">Type</span></span>|<span data-ttu-id="d0ed3-105">Intervalo</span><span class="sxs-lookup"><span data-stu-id="d0ed3-105">Range</span></span>|<span data-ttu-id="d0ed3-106">Tamanho</span><span class="sxs-lookup"><span data-stu-id="d0ed3-106">Size</span></span>|<span data-ttu-id="d0ed3-107">Tipo .NET</span><span class="sxs-lookup"><span data-stu-id="d0ed3-107">.NET type</span></span>|
|----------|-----------|----------|-------------------------|
|`char`|<span data-ttu-id="d0ed3-108">U+0000 a U+FFFF</span><span class="sxs-lookup"><span data-stu-id="d0ed3-108">U+0000 to U+FFFF</span></span>|<span data-ttu-id="d0ed3-109">16 bits</span><span class="sxs-lookup"><span data-stu-id="d0ed3-109">16 bit</span></span>|<xref:System.Char?displayProperty=nameWithType>|

<span data-ttu-id="d0ed3-110">O valor padrão `char` do `\0`tipo é, ou seja, U+0000.</span><span class="sxs-lookup"><span data-stu-id="d0ed3-110">The default value of the `char` type is `\0`, that is, U+0000.</span></span>

<span data-ttu-id="d0ed3-111">O tipo [de string](reference-types.md#the-string-type) representa `char` o texto como uma seqüência de valores.</span><span class="sxs-lookup"><span data-stu-id="d0ed3-111">The [string](reference-types.md#the-string-type) type represents text as a sequence of `char` values.</span></span>

## <a name="literals"></a><span data-ttu-id="d0ed3-112">Literais</span><span class="sxs-lookup"><span data-stu-id="d0ed3-112">Literals</span></span>

<span data-ttu-id="d0ed3-113">Você pode `char` especificar um valor com:</span><span class="sxs-lookup"><span data-stu-id="d0ed3-113">You can specify a `char` value with:</span></span>

- <span data-ttu-id="d0ed3-114">um personagem literal.</span><span class="sxs-lookup"><span data-stu-id="d0ed3-114">a character literal.</span></span>
- <span data-ttu-id="d0ed3-115">uma seqüência de `\u` fuga Unicode, que é seguida pela representação hexadecimal de quatro símbolos de um código de caractere.</span><span class="sxs-lookup"><span data-stu-id="d0ed3-115">a Unicode escape sequence, which is `\u` followed by the four-symbol hexadecimal representation of a character code.</span></span>
- <span data-ttu-id="d0ed3-116">uma seqüência de fuga hexadecimal, que é `\x` seguida pela representação hexadecimal de um código de caractere.</span><span class="sxs-lookup"><span data-stu-id="d0ed3-116">a hexadecimal escape sequence, which is `\x` followed by the hexadecimal representation of a character code.</span></span>

[!code-csharp-interactive[char literals](snippets/CharType.cs#Literals)]

<span data-ttu-id="d0ed3-117">Como o exemplo anterior mostra, você também pode lançar `char` o valor de um código de caractere no valor correspondente.</span><span class="sxs-lookup"><span data-stu-id="d0ed3-117">As the preceding example shows, you also can cast the value of a character code into the corresponding `char` value.</span></span>

> [!NOTE]
> <span data-ttu-id="d0ed3-118">No caso de uma seqüência de fuga Unicode, você deve especificar todos os quatro dígitos hexadecimais.</span><span class="sxs-lookup"><span data-stu-id="d0ed3-118">In the case of a Unicode escape sequence, you must specify all four hexadecimal digits.</span></span> <span data-ttu-id="d0ed3-119">Ou seja, `\u006A` é uma sequência `\u06A` `\u6A` de fuga válida, enquanto e não são válidos.</span><span class="sxs-lookup"><span data-stu-id="d0ed3-119">That is, `\u006A` is a valid escape sequence, while `\u06A` and `\u6A` are not valid.</span></span>
>
> <span data-ttu-id="d0ed3-120">No caso de uma seqüência de fuga hexadecimal, você pode omiti-lo os zeros principais.</span><span class="sxs-lookup"><span data-stu-id="d0ed3-120">In the case of a hexadecimal escape sequence, you can omit the leading zeros.</span></span> <span data-ttu-id="d0ed3-121">Ou seja, `\x006A` `\x06A`as `\x6A` seqüências de fuga são válidas e correspondem ao mesmo caractere.</span><span class="sxs-lookup"><span data-stu-id="d0ed3-121">That is, the `\x006A`, `\x06A`, and `\x6A` escape sequences are valid and correspond to the same character.</span></span>

## <a name="conversions"></a><span data-ttu-id="d0ed3-122">Conversões</span><span class="sxs-lookup"><span data-stu-id="d0ed3-122">Conversions</span></span>

<span data-ttu-id="d0ed3-123">O `char` tipo é implicitamente conversível `int`para `uint` `long`os `ulong`seguintes tipos [integrais:](integral-numeric-types.md) `ushort`, , , e . .</span><span class="sxs-lookup"><span data-stu-id="d0ed3-123">The `char` type is implicitly convertible to the following [integral](integral-numeric-types.md) types: `ushort`, `int`, `uint`, `long`, and `ulong`.</span></span> <span data-ttu-id="d0ed3-124">Também é implicitamente conversível para os tipos numéricos `double`de `decimal` [ponto flutuante](floating-point-numeric-types.md) embutidos: `float`, e .</span><span class="sxs-lookup"><span data-stu-id="d0ed3-124">It's also implicitly convertible to the built-in [floating-point](floating-point-numeric-types.md) numeric types: `float`, `double`, and `decimal`.</span></span> <span data-ttu-id="d0ed3-125">É explicitamente conversível `sbyte`para, `byte` `short` e tipos integrais.</span><span class="sxs-lookup"><span data-stu-id="d0ed3-125">It's explicitly convertible to `sbyte`, `byte`, and `short` integral types.</span></span>

<span data-ttu-id="d0ed3-126">Não há conversões implícitas de `char` outros tipos para o tipo.</span><span class="sxs-lookup"><span data-stu-id="d0ed3-126">There are no implicit conversions from other types to the `char` type.</span></span> <span data-ttu-id="d0ed3-127">No entanto, qualquer tipo numérico [integral](integral-numeric-types.md) `char`ou de ponto [flutuante](floating-point-numeric-types.md) é explicitamente conversível para .</span><span class="sxs-lookup"><span data-stu-id="d0ed3-127">However, any [integral](integral-numeric-types.md) or [floating-point](floating-point-numeric-types.md) numeric type is explicitly convertible to `char`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="d0ed3-128">especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="d0ed3-128">C# language specification</span></span>

<span data-ttu-id="d0ed3-129">Para obter mais informações, consulte a seção [Tipos Integrais](~/_csharplang/spec/types.md#integral-types) da especificação do [idioma C#.](~/_csharplang/spec/introduction.md)</span><span class="sxs-lookup"><span data-stu-id="d0ed3-129">For more information, see the [Integral types](~/_csharplang/spec/types.md#integral-types) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d0ed3-130">Confira também</span><span class="sxs-lookup"><span data-stu-id="d0ed3-130">See also</span></span>

- [<span data-ttu-id="d0ed3-131">Referência do C#</span><span class="sxs-lookup"><span data-stu-id="d0ed3-131">C# reference</span></span>](../index.md)
- [<span data-ttu-id="d0ed3-132">Tipos de valor</span><span class="sxs-lookup"><span data-stu-id="d0ed3-132">Value types</span></span>](value-types.md)
- [<span data-ttu-id="d0ed3-133">Cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="d0ed3-133">Strings</span></span>](../../programming-guide/strings/index.md)
- <xref:System.Text.Rune?displayProperty=nameWithType>
- [<span data-ttu-id="d0ed3-134">Codificação de caracteres no .NET</span><span class="sxs-lookup"><span data-stu-id="d0ed3-134">Character encoding in .NET</span></span>](../../../standard/base-types/character-encoding-introduction.md)
