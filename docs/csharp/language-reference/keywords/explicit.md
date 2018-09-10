---
title: Palavra-chave explicit (Referência de C#)
ms.date: 08/24/2018
f1_keywords:
- explicit_CSharpKeyword
- explicit
helpviewer_keywords:
- explicit keyword [C#]
ms.assetid: cfb8f42a-e411-4db2-af9b-796b05644846
ms.openlocfilehash: 3567a2c5aa549aa3141ed59c3e93e7b07975da70
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43463137"
---
# <a name="explicit-c-reference"></a><span data-ttu-id="cf58f-102">explicit (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="cf58f-102">explicit (C# Reference)</span></span>

<span data-ttu-id="cf58f-103">A palavra-chave `explicit` declara um operador de conversão de tipo definido pelo usuário que deve ser invocado com uma conversão.</span><span class="sxs-lookup"><span data-stu-id="cf58f-103">The `explicit` keyword declares a user-defined type conversion operator that must be invoked with a cast.</span></span>

<span data-ttu-id="cf58f-104">O exemplo a seguir define o operador que converte de uma classe `Fahrenheit` a uma classe `Celsius`.</span><span class="sxs-lookup"><span data-stu-id="cf58f-104">The following example defines the operator that converts from a `Fahrenheit` class to a `Celsius` class.</span></span> <span data-ttu-id="cf58f-105">O operador deve ser definido dentro uma classe `Fahrenheit` ou uma classe `Celsius`:</span><span class="sxs-lookup"><span data-stu-id="cf58f-105">The operator must be defined either inside a `Fahrenheit` class or a `Celsius` class:</span></span>

[!code-csharp[csrefKeywordsConversion#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsConversion/CS/csrefKeywordsConversion.cs#2)]

<span data-ttu-id="cf58f-106">Você invoca o operador de conversão definido com uma conversão, como mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="cf58f-106">You invoke the defined conversion operator with a cast, as the following example shows:</span></span>

[!code-csharp[csrefKeywordsConversion#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsConversion/CS/csrefKeywordsConversion.cs#3)]

<span data-ttu-id="cf58f-107">O operador de conversão converte de um tipo de origem para um tipo de destino.</span><span class="sxs-lookup"><span data-stu-id="cf58f-107">The conversion operator converts from a source type to a target type.</span></span> <span data-ttu-id="cf58f-108">O tipo de origem fornece o operador de conversão.</span><span class="sxs-lookup"><span data-stu-id="cf58f-108">The source type provides the conversion operator.</span></span> <span data-ttu-id="cf58f-109">Ao contrário da conversão implícita, os operadores de conversão explícita devem ser invocados por meio de uma conversão.</span><span class="sxs-lookup"><span data-stu-id="cf58f-109">Unlike implicit conversion, explicit conversion operators must be invoked by means of a cast.</span></span> <span data-ttu-id="cf58f-110">Se uma operação de conversão pode causar exceções ou perda de informações, você deve marcá-la como `explicit`.</span><span class="sxs-lookup"><span data-stu-id="cf58f-110">If a conversion operation can cause exceptions or lose information, you should mark it `explicit`.</span></span> <span data-ttu-id="cf58f-111">Isso impede que o compilador invoque silenciosamente a operação de conversão com consequências possivelmente imprevisíveis.</span><span class="sxs-lookup"><span data-stu-id="cf58f-111">This prevents the compiler from silently invoking the conversion operation with possibly unforeseen consequences.</span></span>

<span data-ttu-id="cf58f-112">A omissão da conversão resulta no erro em tempo de compilação CS0266.</span><span class="sxs-lookup"><span data-stu-id="cf58f-112">Omitting the cast results in compile-time error CS0266.</span></span>

<span data-ttu-id="cf58f-113">Para obter mais informações, consulte [Usando Operadores de Conversão](../../programming-guide/statements-expressions-operators/using-conversion-operators.md).</span><span class="sxs-lookup"><span data-stu-id="cf58f-113">For more information, see [Using Conversion Operators](../../programming-guide/statements-expressions-operators/using-conversion-operators.md).</span></span>

## <a name="example"></a><span data-ttu-id="cf58f-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="cf58f-114">Example</span></span>

<span data-ttu-id="cf58f-115">O exemplo a seguir fornece uma classe `Fahrenheit` e uma classe `Celsius` e cada uma delas fornece um operador de conversão explícita para a outra classe.</span><span class="sxs-lookup"><span data-stu-id="cf58f-115">The following example provides a `Fahrenheit` and a `Celsius` class, each of which provides an explicit conversion operator to the other class.</span></span>

[!code-csharp[csrefKeywordsConversion#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsConversion/CS/csrefKeywordsConversion.cs#1)]

## <a name="example"></a><span data-ttu-id="cf58f-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="cf58f-116">Example</span></span>

<span data-ttu-id="cf58f-117">O exemplo a seguir define um struct `Digit`, que representa um único dígito decimal.</span><span class="sxs-lookup"><span data-stu-id="cf58f-117">The following example defines a struct, `Digit`, that represents a single decimal digit.</span></span> <span data-ttu-id="cf58f-118">Um operador é definido para conversões de `byte` para `Digit`, mas como nem todos os bytes podem ser convertidos para um `Digit`, a conversão é explícita.</span><span class="sxs-lookup"><span data-stu-id="cf58f-118">An operator is defined for conversions from `byte` to `Digit`, but because not all bytes can be converted to a `Digit`, the conversion is explicit.</span></span>

[!code-csharp[csrefKeywordsConversion#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsConversion/CS/csrefKeywordsConversion.cs#4)]

## <a name="c-language-specification"></a><span data-ttu-id="cf58f-119">especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="cf58f-119">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="cf58f-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cf58f-120">See also</span></span>

- [<span data-ttu-id="cf58f-121">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="cf58f-121">C# Reference</span></span>](../index.md)  
- [<span data-ttu-id="cf58f-122">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="cf58f-122">C# Programming Guide</span></span>](../../programming-guide/index.md)  
- [<span data-ttu-id="cf58f-123">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="cf58f-123">C# Keywords</span></span>](index.md)  
- [<span data-ttu-id="cf58f-124">implicit</span><span class="sxs-lookup"><span data-stu-id="cf58f-124">implicit</span></span>](implicit.md)  
- [<span data-ttu-id="cf58f-125">operator (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="cf58f-125">operator (C# Reference)</span></span>](operator.md)  
- [<span data-ttu-id="cf58f-126">Como implementar conversões definidas pelo usuário entre structs</span><span class="sxs-lookup"><span data-stu-id="cf58f-126">How to: Implement User-Defined Conversions Between Structs</span></span>](../../programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)  
- [<span data-ttu-id="cf58f-127">Conversões explícitas encadeadas definidas pelo usuário em C#</span><span class="sxs-lookup"><span data-stu-id="cf58f-127">Chained user-defined explicit conversions in C#</span></span>](https://blogs.msdn.microsoft.com/ericlippert/2007/04/16/chained-user-defined-explicit-conversions-in-c/)  
