---
title: palavra-chave C# Char-referência
ms.custom: seodec18
ms.date: 10/22/2019
f1_keywords:
- char
- char_CSharpKeyword
helpviewer_keywords:
- char data type [C#]
ms.assetid: b51cf4fb-124c-4067-af48-afbac122b228
ms.openlocfilehash: 1b9f8d1bb205a6cbfe521830a11bd8878ccde991
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72771795"
---
# <a name="char-c-reference"></a><span data-ttu-id="a5093-102">Char (C# referência)</span><span class="sxs-lookup"><span data-stu-id="a5093-102">char (C# reference)</span></span>

<span data-ttu-id="a5093-103">A palavra-chave Type de `char` é um alias para o tipo de estrutura .NET <xref:System.Char?displayProperty=nameWithType> que representa um caractere Unicode UTF-16:</span><span class="sxs-lookup"><span data-stu-id="a5093-103">The `char` type keyword is an alias for the .NET <xref:System.Char?displayProperty=nameWithType> structure type that represents a Unicode UTF-16 character:</span></span>

|<span data-ttu-id="a5093-104">Digite</span><span class="sxs-lookup"><span data-stu-id="a5093-104">Type</span></span>|<span data-ttu-id="a5093-105">Intervalo</span><span class="sxs-lookup"><span data-stu-id="a5093-105">Range</span></span>|<span data-ttu-id="a5093-106">Tamanho</span><span class="sxs-lookup"><span data-stu-id="a5093-106">Size</span></span>|<span data-ttu-id="a5093-107">Tipo .NET</span><span class="sxs-lookup"><span data-stu-id="a5093-107">.NET type</span></span>|
|----------|-----------|----------|-------------------------|
|`char`|<span data-ttu-id="a5093-108">U+0000 a U+FFFF</span><span class="sxs-lookup"><span data-stu-id="a5093-108">U+0000 to U+FFFF</span></span>|<span data-ttu-id="a5093-109">16 bits</span><span class="sxs-lookup"><span data-stu-id="a5093-109">16 bit</span></span>|<xref:System.Char?displayProperty=nameWithType>|

## <a name="literals"></a><span data-ttu-id="a5093-110">Literais</span><span class="sxs-lookup"><span data-stu-id="a5093-110">Literals</span></span>

<span data-ttu-id="a5093-111">As constantes de tipo `char` podem ser escritas como literais de caracteres, sequência de escape hexadecimal ou como representação Unicode.</span><span class="sxs-lookup"><span data-stu-id="a5093-111">Constants of the `char` type can be written as character literals, hexadecimal escape sequence, or Unicode representation.</span></span> <span data-ttu-id="a5093-112">Você também pode converter um código de caractere integral no valor de `char` correspondente.</span><span class="sxs-lookup"><span data-stu-id="a5093-112">You can also cast an integral character code into the corresponding `char` value.</span></span> <span data-ttu-id="a5093-113">No exemplo a seguir, os quatro elementos de uma matriz de `char` são inicializados com o mesmo caractere `X`:</span><span class="sxs-lookup"><span data-stu-id="a5093-113">In the following example, the four elements of an array of `char` are initialized with the same character `X`:</span></span>

[!code-csharp[csrefKeywordsTypes#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#19)]

## <a name="conversions"></a><span data-ttu-id="a5093-114">Conversões</span><span class="sxs-lookup"><span data-stu-id="a5093-114">Conversions</span></span>

<span data-ttu-id="a5093-115">O tipo de `char` é implicitamente conversível para os seguintes tipos [integral](../builtin-types/integral-numeric-types.md) : `ushort`, `int`, `uint`, `long` e `ulong`.</span><span class="sxs-lookup"><span data-stu-id="a5093-115">The `char` type is implicitly convertible to the following [integral](../builtin-types/integral-numeric-types.md) types: `ushort`, `int`, `uint`, `long`, and `ulong`.</span></span> <span data-ttu-id="a5093-116">Ele também é implicitamente conversível para os tipos numéricos de [ponto flutuante](../builtin-types/floating-point-numeric-types.md) internos: `float`, `double` e `decimal`.</span><span class="sxs-lookup"><span data-stu-id="a5093-116">It's also implicitly convertible to the built-in [floating-point](../builtin-types/floating-point-numeric-types.md) numeric types: `float`, `double`, and `decimal`.</span></span> <span data-ttu-id="a5093-117">Ele é explicitamente conversível para `sbyte`, `byte` e `short` tipos integrais.</span><span class="sxs-lookup"><span data-stu-id="a5093-117">It's explicitly convertible to `sbyte`, `byte`, and `short` integral types.</span></span>

<span data-ttu-id="a5093-118">Não há conversões implícitas de outros tipos para o tipo de `char`.</span><span class="sxs-lookup"><span data-stu-id="a5093-118">There are no implicit conversions from other types to the `char` type.</span></span> <span data-ttu-id="a5093-119">No entanto, qualquer tipo [integral](../builtin-types/integral-numeric-types.md) ou numérico [de ponto flutuante](../builtin-types/floating-point-numeric-types.md) é explicitamente conversível para `char`.</span><span class="sxs-lookup"><span data-stu-id="a5093-119">However, any [integral](../builtin-types/integral-numeric-types.md) or [floating-point](../builtin-types/floating-point-numeric-types.md) numeric type is explicitly convertible to `char`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="a5093-120">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="a5093-120">C# language specification</span></span>

<span data-ttu-id="a5093-121">Para obter mais informações, consulte a seção [tipos integrais](~/_csharplang/spec/types.md#integral-types) da [ C# especificação da linguagem](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="a5093-121">For more information, see the [Integral types](~/_csharplang/spec/types.md#integral-types) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a5093-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a5093-122">See also</span></span>

- [<span data-ttu-id="a5093-123">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="a5093-123">C# reference</span></span>](../index.md)
- [<span data-ttu-id="a5093-124">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="a5093-124">C# keywords</span></span>](./index.md)
- [<span data-ttu-id="a5093-125">Tabela de tipos internos</span><span class="sxs-lookup"><span data-stu-id="a5093-125">Built-in types table</span></span>](./built-in-types-table.md)
- [<span data-ttu-id="a5093-126">Cadeias de Caracteres</span><span class="sxs-lookup"><span data-stu-id="a5093-126">Strings</span></span>](../../programming-guide/strings/index.md)
- <xref:System.Char?displayProperty=nameWithType>
