---
title: tipo de caractere-referência C#
ms.date: 05/11/2020
f1_keywords:
- char
- char_CSharpKeyword
helpviewer_keywords:
- char data type [C#]
ms.assetid: b51cf4fb-124c-4067-af48-afbac122b228
ms.openlocfilehash: f771626e9777deab30e798559d847615d6124e6d
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83205787"
---
# <a name="char-c-reference"></a><span data-ttu-id="d4ea8-102">Char (referência C#)</span><span class="sxs-lookup"><span data-stu-id="d4ea8-102">char (C# reference)</span></span>

<span data-ttu-id="d4ea8-103">A `char` palavra-chave Type é um alias para o <xref:System.Char?displayProperty=nameWithType> tipo de estrutura .NET que representa um caractere Unicode UTF-16.</span><span class="sxs-lookup"><span data-stu-id="d4ea8-103">The `char` type keyword is an alias for the .NET <xref:System.Char?displayProperty=nameWithType> structure type that represents a Unicode UTF-16 character.</span></span>

|<span data-ttu-id="d4ea8-104">Type</span><span class="sxs-lookup"><span data-stu-id="d4ea8-104">Type</span></span>|<span data-ttu-id="d4ea8-105">Intervalo</span><span class="sxs-lookup"><span data-stu-id="d4ea8-105">Range</span></span>|<span data-ttu-id="d4ea8-106">Tamanho</span><span class="sxs-lookup"><span data-stu-id="d4ea8-106">Size</span></span>|<span data-ttu-id="d4ea8-107">Tipo .NET</span><span class="sxs-lookup"><span data-stu-id="d4ea8-107">.NET type</span></span>|
|----------|-----------|----------|-------------------------|
|`char`|<span data-ttu-id="d4ea8-108">U+0000 a U+FFFF</span><span class="sxs-lookup"><span data-stu-id="d4ea8-108">U+0000 to U+FFFF</span></span>|<span data-ttu-id="d4ea8-109">16 bits</span><span class="sxs-lookup"><span data-stu-id="d4ea8-109">16 bit</span></span>|<xref:System.Char?displayProperty=nameWithType>|

<span data-ttu-id="d4ea8-110">O valor padrão do `char` tipo é `\0` , ou seja, U + 0000.</span><span class="sxs-lookup"><span data-stu-id="d4ea8-110">The default value of the `char` type is `\0`, that is, U+0000.</span></span>

<span data-ttu-id="d4ea8-111">O `char` tipo dá suporte a operadores de [comparação](../operators/comparison-operators.md), [igualdade](../operators/equality-operators.md), [incremento](../operators/arithmetic-operators.md#increment-operator-)e [decréscimo](../operators/arithmetic-operators.md#decrement-operator---) .</span><span class="sxs-lookup"><span data-stu-id="d4ea8-111">The `char` type supports [comparison](../operators/comparison-operators.md), [equality](../operators/equality-operators.md), [increment](../operators/arithmetic-operators.md#increment-operator-), and [decrement](../operators/arithmetic-operators.md#decrement-operator---) operators.</span></span> <span data-ttu-id="d4ea8-112">Além disso, para `char` operandos, os operadores [lógicos](../operators/bitwise-and-shift-operators.md) [aritméticos](../operators/arithmetic-operators.md) e de bit-a-vírgula executam uma operação nos códigos de caracteres correspondentes e produzem o resultado do `int` tipo.</span><span class="sxs-lookup"><span data-stu-id="d4ea8-112">Moreover, for `char` operands, [arithmetic](../operators/arithmetic-operators.md) and [bitwise logical](../operators/bitwise-and-shift-operators.md) operators perform an operation on the corresponding character codes and produce the result of the `int` type.</span></span>

<span data-ttu-id="d4ea8-113">O tipo de [cadeia de caracteres](reference-types.md#the-string-type) representa o texto como uma sequência de `char` valores.</span><span class="sxs-lookup"><span data-stu-id="d4ea8-113">The [string](reference-types.md#the-string-type) type represents text as a sequence of `char` values.</span></span>

## <a name="literals"></a><span data-ttu-id="d4ea8-114">Literais</span><span class="sxs-lookup"><span data-stu-id="d4ea8-114">Literals</span></span>

<span data-ttu-id="d4ea8-115">Você pode especificar um `char` valor com:</span><span class="sxs-lookup"><span data-stu-id="d4ea8-115">You can specify a `char` value with:</span></span>

- <span data-ttu-id="d4ea8-116">um literal de caractere.</span><span class="sxs-lookup"><span data-stu-id="d4ea8-116">a character literal.</span></span>
- <span data-ttu-id="d4ea8-117">uma sequência de escape Unicode, que é `\u` seguida pela representação hexadecimal de quatro símbolos de um código de caractere.</span><span class="sxs-lookup"><span data-stu-id="d4ea8-117">a Unicode escape sequence, which is `\u` followed by the four-symbol hexadecimal representation of a character code.</span></span>
- <span data-ttu-id="d4ea8-118">uma sequência de escape hexadecimal, que é `\x` seguida pela representação hexadecimal de um código de caractere.</span><span class="sxs-lookup"><span data-stu-id="d4ea8-118">a hexadecimal escape sequence, which is `\x` followed by the hexadecimal representation of a character code.</span></span>

[!code-csharp-interactive[char literals](snippets/CharType.cs#Literals)]

<span data-ttu-id="d4ea8-119">Como mostra o exemplo anterior, você também pode converter o valor de um código de caractere no `char` valor correspondente.</span><span class="sxs-lookup"><span data-stu-id="d4ea8-119">As the preceding example shows, you can also cast the value of a character code into the corresponding `char` value.</span></span>

> [!NOTE]
> <span data-ttu-id="d4ea8-120">No caso de uma sequência de escape Unicode, você deve especificar todos os quatro dígitos hexadecimais.</span><span class="sxs-lookup"><span data-stu-id="d4ea8-120">In the case of a Unicode escape sequence, you must specify all four hexadecimal digits.</span></span> <span data-ttu-id="d4ea8-121">Ou seja, `\u006A` é uma sequência de escape válida, enquanto `\u06A` e `\u6A` não são válidas.</span><span class="sxs-lookup"><span data-stu-id="d4ea8-121">That is, `\u006A` is a valid escape sequence, while `\u06A` and `\u6A` are not valid.</span></span>
>
> <span data-ttu-id="d4ea8-122">No caso de uma sequência de escape hexadecimal, você pode omitir os zeros à esquerda.</span><span class="sxs-lookup"><span data-stu-id="d4ea8-122">In the case of a hexadecimal escape sequence, you can omit the leading zeros.</span></span> <span data-ttu-id="d4ea8-123">Ou seja, as `\x006A` `\x06A` `\x6A` sequências de escape, e são válidas e correspondem ao mesmo caractere.</span><span class="sxs-lookup"><span data-stu-id="d4ea8-123">That is, the `\x006A`, `\x06A`, and `\x6A` escape sequences are valid and correspond to the same character.</span></span>

## <a name="conversions"></a><span data-ttu-id="d4ea8-124">Conversões</span><span class="sxs-lookup"><span data-stu-id="d4ea8-124">Conversions</span></span>

<span data-ttu-id="d4ea8-125">O `char` tipo é implicitamente conversível nos seguintes tipos [integral](integral-numeric-types.md) : `ushort` ,,, `int` `uint` `long` e `ulong` .</span><span class="sxs-lookup"><span data-stu-id="d4ea8-125">The `char` type is implicitly convertible to the following [integral](integral-numeric-types.md) types: `ushort`, `int`, `uint`, `long`, and `ulong`.</span></span> <span data-ttu-id="d4ea8-126">Ele também é implicitamente conversível para os tipos numéricos de [ponto flutuante](floating-point-numeric-types.md) internos: `float` , `double` e `decimal` .</span><span class="sxs-lookup"><span data-stu-id="d4ea8-126">It's also implicitly convertible to the built-in [floating-point](floating-point-numeric-types.md) numeric types: `float`, `double`, and `decimal`.</span></span> <span data-ttu-id="d4ea8-127">Ele é explicitamente convertido em `sbyte` , `byte` e `short` tipos integrais.</span><span class="sxs-lookup"><span data-stu-id="d4ea8-127">It's explicitly convertible to `sbyte`, `byte`, and `short` integral types.</span></span>

<span data-ttu-id="d4ea8-128">Não há conversões implícitas de outros tipos para o `char` tipo.</span><span class="sxs-lookup"><span data-stu-id="d4ea8-128">There are no implicit conversions from other types to the `char` type.</span></span> <span data-ttu-id="d4ea8-129">No entanto, qualquer tipo [integral](integral-numeric-types.md) ou numérico [de ponto flutuante](floating-point-numeric-types.md) é explicitamente conversível para `char` .</span><span class="sxs-lookup"><span data-stu-id="d4ea8-129">However, any [integral](integral-numeric-types.md) or [floating-point](floating-point-numeric-types.md) numeric type is explicitly convertible to `char`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="d4ea8-130">especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="d4ea8-130">C# language specification</span></span>

<span data-ttu-id="d4ea8-131">Para obter mais informações, consulte a seção [tipos integrais](~/_csharplang/spec/types.md#integral-types) da [especificação da linguagem C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="d4ea8-131">For more information, see the [Integral types](~/_csharplang/spec/types.md#integral-types) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d4ea8-132">Confira também</span><span class="sxs-lookup"><span data-stu-id="d4ea8-132">See also</span></span>

- [<span data-ttu-id="d4ea8-133">Referência do C#</span><span class="sxs-lookup"><span data-stu-id="d4ea8-133">C# reference</span></span>](../index.md)
- [<span data-ttu-id="d4ea8-134">Tipos de valor</span><span class="sxs-lookup"><span data-stu-id="d4ea8-134">Value types</span></span>](value-types.md)
- [<span data-ttu-id="d4ea8-135">Cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="d4ea8-135">Strings</span></span>](../../programming-guide/strings/index.md)
- <xref:System.Text.Rune?displayProperty=nameWithType>
- [<span data-ttu-id="d4ea8-136">Codificação de caracteres no .NET</span><span class="sxs-lookup"><span data-stu-id="d4ea8-136">Character encoding in .NET</span></span>](../../../standard/base-types/character-encoding-introduction.md)
