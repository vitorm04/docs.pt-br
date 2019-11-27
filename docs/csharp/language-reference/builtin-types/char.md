---
title: tipo de caractere C# -referência
ms.date: 11/22/2019
f1_keywords:
- char
- char_CSharpKeyword
helpviewer_keywords:
- char data type [C#]
ms.assetid: b51cf4fb-124c-4067-af48-afbac122b228
ms.openlocfilehash: 3b2eec4f0e17aa329fe3865fb3ef453ee030c6a7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74451160"
---
# <a name="char-c-reference"></a><span data-ttu-id="f8c64-102">Char (C# referência)</span><span class="sxs-lookup"><span data-stu-id="f8c64-102">char (C# reference)</span></span>

<span data-ttu-id="f8c64-103">A palavra-chave Type de `char` é um alias para o tipo de estrutura .NET <xref:System.Char?displayProperty=nameWithType> que representa um caractere Unicode UTF-16.</span><span class="sxs-lookup"><span data-stu-id="f8c64-103">The `char` type keyword is an alias for the .NET <xref:System.Char?displayProperty=nameWithType> structure type that represents a Unicode UTF-16 character.</span></span>

|<span data-ttu-id="f8c64-104">Tipo</span><span class="sxs-lookup"><span data-stu-id="f8c64-104">Type</span></span>|<span data-ttu-id="f8c64-105">Intervalo</span><span class="sxs-lookup"><span data-stu-id="f8c64-105">Range</span></span>|<span data-ttu-id="f8c64-106">Tamanho</span><span class="sxs-lookup"><span data-stu-id="f8c64-106">Size</span></span>|<span data-ttu-id="f8c64-107">Tipo .NET</span><span class="sxs-lookup"><span data-stu-id="f8c64-107">.NET type</span></span>|
|----------|-----------|----------|-------------------------|
|`char`|<span data-ttu-id="f8c64-108">U+0000 a U+FFFF</span><span class="sxs-lookup"><span data-stu-id="f8c64-108">U+0000 to U+FFFF</span></span>|<span data-ttu-id="f8c64-109">16 bits</span><span class="sxs-lookup"><span data-stu-id="f8c64-109">16 bit</span></span>|<xref:System.Char?displayProperty=nameWithType>|

<span data-ttu-id="f8c64-110">O tipo de [cadeia de caracteres](reference-types.md#the-string-type) representa o texto como uma sequência de valores de `char`.</span><span class="sxs-lookup"><span data-stu-id="f8c64-110">The [string](reference-types.md#the-string-type) type represents text as a sequence of `char` values.</span></span>

## <a name="literals"></a><span data-ttu-id="f8c64-111">{1&gt;Literais&lt;1}</span><span class="sxs-lookup"><span data-stu-id="f8c64-111">Literals</span></span>

<span data-ttu-id="f8c64-112">Você pode especificar um valor de `char` com:</span><span class="sxs-lookup"><span data-stu-id="f8c64-112">You can specify a `char` value with:</span></span>

- <span data-ttu-id="f8c64-113">um literal de caractere.</span><span class="sxs-lookup"><span data-stu-id="f8c64-113">a character literal.</span></span>
- <span data-ttu-id="f8c64-114">uma sequência de escape Unicode, que é `\u` seguida pela representação hexadecimal de quatro símbolos de um código de caractere.</span><span class="sxs-lookup"><span data-stu-id="f8c64-114">a Unicode escape sequence, which is `\u` followed by the four-symbol hexadecimal representation of a character code.</span></span>
- <span data-ttu-id="f8c64-115">uma sequência de escape hexadecimal, que é `\x` seguida pela representação hexadecimal de um código de caractere.</span><span class="sxs-lookup"><span data-stu-id="f8c64-115">a hexadecimal escape sequence, which is `\x` followed by the hexadecimal representation of a character code.</span></span>

[!code-csharp-interactive[char literals](~/samples/csharp/language-reference/builtin-types/CharType.cs#Literals)]

<span data-ttu-id="f8c64-116">Como mostra o exemplo anterior, você também pode converter o valor de um código de caractere no valor de `char` correspondente.</span><span class="sxs-lookup"><span data-stu-id="f8c64-116">As the preceding example shows, you also can cast the value of a character code into the corresponding `char` value.</span></span>

> [!NOTE]
> <span data-ttu-id="f8c64-117">No caso de uma sequência de escape Unicode, você deve especificar todos os quatro dígitos hexadecimais.</span><span class="sxs-lookup"><span data-stu-id="f8c64-117">In the case of a Unicode escape sequence, you must specify all four hexadecimal digits.</span></span> <span data-ttu-id="f8c64-118">Ou seja, `\u006A` é uma sequência de escape válida, enquanto `\u06A` e `\u6A` não são válidos.</span><span class="sxs-lookup"><span data-stu-id="f8c64-118">That is, `\u006A` is a valid escape sequence, while `\u06A` and `\u6A` are not valid.</span></span>
>
> <span data-ttu-id="f8c64-119">No caso de uma sequência de escape hexadecimal, você pode omitir os zeros à esquerda.</span><span class="sxs-lookup"><span data-stu-id="f8c64-119">In the case of a hexadecimal escape sequence, you can omit the leading zeros.</span></span> <span data-ttu-id="f8c64-120">Ou seja, as sequências de escape `\x006A`, `\x06A`e `\x6A` são válidas e correspondem ao mesmo caractere.</span><span class="sxs-lookup"><span data-stu-id="f8c64-120">That is, the `\x006A`, `\x06A`, and `\x6A` escape sequences are valid and correspond to the same character.</span></span>

## <a name="conversions"></a><span data-ttu-id="f8c64-121">Conversões</span><span class="sxs-lookup"><span data-stu-id="f8c64-121">Conversions</span></span>

<span data-ttu-id="f8c64-122">O tipo de `char` é implicitamente conversível para os seguintes tipos [integral](integral-numeric-types.md) : `ushort`, `int`, `uint`, `long`e `ulong`.</span><span class="sxs-lookup"><span data-stu-id="f8c64-122">The `char` type is implicitly convertible to the following [integral](integral-numeric-types.md) types: `ushort`, `int`, `uint`, `long`, and `ulong`.</span></span> <span data-ttu-id="f8c64-123">Ele também é implicitamente conversível para os tipos numéricos de [ponto flutuante](floating-point-numeric-types.md) internos: `float`, `double`e `decimal`.</span><span class="sxs-lookup"><span data-stu-id="f8c64-123">It's also implicitly convertible to the built-in [floating-point](floating-point-numeric-types.md) numeric types: `float`, `double`, and `decimal`.</span></span> <span data-ttu-id="f8c64-124">Ele é explicitamente conversível para `sbyte`, `byte`e `short` tipos integrais.</span><span class="sxs-lookup"><span data-stu-id="f8c64-124">It's explicitly convertible to `sbyte`, `byte`, and `short` integral types.</span></span>

<span data-ttu-id="f8c64-125">Não há conversões implícitas de outros tipos para o tipo de `char`.</span><span class="sxs-lookup"><span data-stu-id="f8c64-125">There are no implicit conversions from other types to the `char` type.</span></span> <span data-ttu-id="f8c64-126">No entanto, qualquer tipo [integral](integral-numeric-types.md) ou numérico [de ponto flutuante](floating-point-numeric-types.md) é explicitamente conversível para `char`.</span><span class="sxs-lookup"><span data-stu-id="f8c64-126">However, any [integral](integral-numeric-types.md) or [floating-point](floating-point-numeric-types.md) numeric type is explicitly convertible to `char`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="f8c64-127">especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="f8c64-127">C# language specification</span></span>

<span data-ttu-id="f8c64-128">Para obter mais informações, consulte a seção [tipos integrais](~/_csharplang/spec/types.md#integral-types) da [ C# especificação da linguagem](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="f8c64-128">For more information, see the [Integral types](~/_csharplang/spec/types.md#integral-types) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f8c64-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f8c64-129">See also</span></span>

- [<span data-ttu-id="f8c64-130">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="f8c64-130">C# reference</span></span>](../index.md)
- [<span data-ttu-id="f8c64-131">Tabela de tipos internos</span><span class="sxs-lookup"><span data-stu-id="f8c64-131">Built-in types table</span></span>](../keywords/built-in-types-table.md)
- [<span data-ttu-id="f8c64-132">Cadeias de Caracteres</span><span class="sxs-lookup"><span data-stu-id="f8c64-132">Strings</span></span>](../../programming-guide/strings/index.md)
