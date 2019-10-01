---
title: Palavra-chave char – Referência de C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- char
- char_CSharpKeyword
helpviewer_keywords:
- char data type [C#]
ms.assetid: b51cf4fb-124c-4067-af48-afbac122b228
ms.openlocfilehash: 63f8871926e8c279678c59a2256bef46b2ff514e
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698782"
---
# <a name="char-c-reference"></a><span data-ttu-id="32e03-102">char (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="32e03-102">char (C# Reference)</span></span>

<span data-ttu-id="32e03-103">A palavra-chave `char` é usada para declarar uma instância da estrutura <xref:System.Char?displayProperty=nameWithType> que o .NET Framework usa para representar um caractere Unicode.</span><span class="sxs-lookup"><span data-stu-id="32e03-103">The `char` keyword is used to declare an instance of the <xref:System.Char?displayProperty=nameWithType> structure that the .NET Framework uses to represent a Unicode character.</span></span> <span data-ttu-id="32e03-104">O valor de um objeto `Char` é um valor numérico de 16 bits (ordinal).</span><span class="sxs-lookup"><span data-stu-id="32e03-104">The value of a `Char` object is a 16-bit numeric (ordinal) value.</span></span>

 <span data-ttu-id="32e03-105">Os caracteres Unicode são usados para representar a maioria dos idiomas escritos em todo o mundo.</span><span class="sxs-lookup"><span data-stu-id="32e03-105">Unicode characters are used to represent most of the written languages throughout the world.</span></span>

|<span data-ttu-id="32e03-106">Tipo</span><span class="sxs-lookup"><span data-stu-id="32e03-106">Type</span></span>|<span data-ttu-id="32e03-107">Intervalo</span><span class="sxs-lookup"><span data-stu-id="32e03-107">Range</span></span>|<span data-ttu-id="32e03-108">Size</span><span class="sxs-lookup"><span data-stu-id="32e03-108">Size</span></span>|<span data-ttu-id="32e03-109">Tipo .NET</span><span class="sxs-lookup"><span data-stu-id="32e03-109">.NET type</span></span>|
|----------|-----------|----------|-------------------------|
|`char`|<span data-ttu-id="32e03-110">U+0000 a U+FFFF</span><span class="sxs-lookup"><span data-stu-id="32e03-110">U+0000 to U+FFFF</span></span>|<span data-ttu-id="32e03-111">Caractere Unicode de 16 bits</span><span class="sxs-lookup"><span data-stu-id="32e03-111">Unicode 16-bit character</span></span>|<xref:System.Char?displayProperty=nameWithType>|

## <a name="literals"></a><span data-ttu-id="32e03-112">Literais</span><span class="sxs-lookup"><span data-stu-id="32e03-112">Literals</span></span>

<span data-ttu-id="32e03-113">As constantes de tipo `char` podem ser escritas como literais de caracteres, sequência de escape hexadecimal ou como representação Unicode.</span><span class="sxs-lookup"><span data-stu-id="32e03-113">Constants of the `char` type can be written as character literals, hexadecimal escape sequence, or Unicode representation.</span></span> <span data-ttu-id="32e03-114">Você também pode converter os códigos de caracteres integrais.</span><span class="sxs-lookup"><span data-stu-id="32e03-114">You can also cast the integral character codes.</span></span> <span data-ttu-id="32e03-115">No exemplo a seguir, os quatro elementos de uma matriz de `char` são inicializados com o mesmo caractere `X`:</span><span class="sxs-lookup"><span data-stu-id="32e03-115">In the following example, the four elements of an array of `char` are initialized with the same character `X`:</span></span>

[!code-csharp[csrefKeywordsTypes#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#19)]

## <a name="conversions"></a><span data-ttu-id="32e03-116">Conversões</span><span class="sxs-lookup"><span data-stu-id="32e03-116">Conversions</span></span>

<span data-ttu-id="32e03-117">Um `char` pode ser implicitamente convertido em [ushort](../builtin-types/integral-numeric-types.md), [int](../builtin-types/integral-numeric-types.md), [uint](../builtin-types/integral-numeric-types.md), [double](../builtin-types/floating-point-numeric-types.md) ou [decimal](../builtin-types/floating-point-numeric-types.md).</span><span class="sxs-lookup"><span data-stu-id="32e03-117">A `char` can be implicitly converted to [ushort](../builtin-types/integral-numeric-types.md), [int](../builtin-types/integral-numeric-types.md), [uint](../builtin-types/integral-numeric-types.md), [double](../builtin-types/floating-point-numeric-types.md), or [decimal](../builtin-types/floating-point-numeric-types.md).</span></span> <span data-ttu-id="32e03-118">No entanto, não há conversões implícitas de outros tipos para o tipo `char`.</span><span class="sxs-lookup"><span data-stu-id="32e03-118">However, there are no implicit conversions from other types to the `char` type.</span></span>

<span data-ttu-id="32e03-119">O tipo <xref:System.Char?displayProperty=nameWithType> fornece vários métodos estáticos para trabalhar com valores `char`.</span><span class="sxs-lookup"><span data-stu-id="32e03-119">The <xref:System.Char?displayProperty=nameWithType> type provides several static methods for working with `char` values.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="32e03-120">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="32e03-120">C# language specification</span></span>  

<span data-ttu-id="32e03-121">Para obter mais informações, veja [Tipos integrais](~/_csharplang/spec/types.md#integral-types) na [Especificação da Linguagem C#](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="32e03-121">For more information, see [Integral types](~/_csharplang/spec/types.md#integral-types) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="32e03-122">A especificação da linguagem é a fonte definitiva para a sintaxe e o uso de C#.</span><span class="sxs-lookup"><span data-stu-id="32e03-122">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="32e03-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="32e03-123">See also</span></span>

- <xref:System.Char>
- [<span data-ttu-id="32e03-124">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="32e03-124">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="32e03-125">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="32e03-125">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="32e03-126">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="32e03-126">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="32e03-127">Tipos integrais</span><span class="sxs-lookup"><span data-stu-id="32e03-127">Integral types</span></span>](../builtin-types/integral-numeric-types.md)
- [<span data-ttu-id="32e03-128">Tabela de tipos internos</span><span class="sxs-lookup"><span data-stu-id="32e03-128">Built-In Types Table</span></span>](./built-in-types-table.md)
- [<span data-ttu-id="32e03-129">Tabela de conversões numéricas implícitas</span><span class="sxs-lookup"><span data-stu-id="32e03-129">Implicit Numeric Conversions Table</span></span>](./implicit-numeric-conversions-table.md)
- [<span data-ttu-id="32e03-130">Tabela de conversões numéricas explícitas</span><span class="sxs-lookup"><span data-stu-id="32e03-130">Explicit Numeric Conversions Table</span></span>](./explicit-numeric-conversions-table.md)
- [<span data-ttu-id="32e03-131">Cadeias de Caracteres</span><span class="sxs-lookup"><span data-stu-id="32e03-131">Strings</span></span>](../../programming-guide/strings/index.md)
