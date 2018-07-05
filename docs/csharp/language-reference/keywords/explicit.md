---
title: Palavra-chave explicit (Referência de C#)
ms.date: 07/20/2015
f1_keywords:
- explicit_CSharpKeyword
- explicit
helpviewer_keywords:
- explicit keyword [C#]
ms.assetid: cfb8f42a-e411-4db2-af9b-796b05644846
ms.openlocfilehash: 66d271fdac0bad356ee0bafc1732e2f410854da1
ms.sourcegitcommit: f9e38d31288fe5962e6be5b0cc286da633482873
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/27/2018
ms.locfileid: "37027935"
---
# <a name="explicit-c-reference"></a><span data-ttu-id="cf191-102">explicit (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="cf191-102">explicit (C# Reference)</span></span>

<span data-ttu-id="cf191-103">A palavra-chave `explicit` declara um operador de conversão de tipo definido pelo usuário que deve ser invocado com uma conversão.</span><span class="sxs-lookup"><span data-stu-id="cf191-103">The `explicit` keyword declares a user-defined type conversion operator that must be invoked with a cast.</span></span> <span data-ttu-id="cf191-104">Por exemplo, esse operador converte de uma classe chamada Fahrenheit para uma classe chamada Celsius:</span><span class="sxs-lookup"><span data-stu-id="cf191-104">For example, this operator converts from a class called Fahrenheit to a class called Celsius:</span></span>

[!code-csharp[csrefKeywordsConversion#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsConversion/CS/csrefKeywordsConversion.cs#2)]

<span data-ttu-id="cf191-105">Esse operador de conversão pode ser invocado assim:</span><span class="sxs-lookup"><span data-stu-id="cf191-105">This conversion operator can be invoked like this:</span></span>

[!code-csharp[csrefKeywordsConversion#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsConversion/CS/csrefKeywordsConversion.cs#3)]

<span data-ttu-id="cf191-106">O operador de conversão converte de um tipo de origem para um tipo de destino.</span><span class="sxs-lookup"><span data-stu-id="cf191-106">The conversion operator converts from a source type to a target type.</span></span> <span data-ttu-id="cf191-107">O tipo de origem fornece o operador de conversão.</span><span class="sxs-lookup"><span data-stu-id="cf191-107">The source type provides the conversion operator.</span></span> <span data-ttu-id="cf191-108">Ao contrário da conversão implícita, os operadores de conversão explícita devem ser invocados por meio de uma conversão.</span><span class="sxs-lookup"><span data-stu-id="cf191-108">Unlike implicit conversion, explicit conversion operators must be invoked by means of a cast.</span></span> <span data-ttu-id="cf191-109">Se uma operação de conversão pode causar exceções ou perda de informações, você deve marcá-la como `explicit`.</span><span class="sxs-lookup"><span data-stu-id="cf191-109">If a conversion operation can cause exceptions or lose information, you should mark it `explicit`.</span></span> <span data-ttu-id="cf191-110">Isso impede que o compilador invoque silenciosamente a operação de conversão com consequências possivelmente imprevisíveis.</span><span class="sxs-lookup"><span data-stu-id="cf191-110">This prevents the compiler from silently invoking the conversion operation with possibly unforeseen consequences.</span></span>

<span data-ttu-id="cf191-111">A omissão da conversão resulta no erro em tempo de compilação CS0266.</span><span class="sxs-lookup"><span data-stu-id="cf191-111">Omitting the cast results in compile-time error CS0266.</span></span>

<span data-ttu-id="cf191-112">Para obter mais informações, consulte [Usando Operadores de Conversão](../../programming-guide/statements-expressions-operators/using-conversion-operators.md).</span><span class="sxs-lookup"><span data-stu-id="cf191-112">For more information, see [Using Conversion Operators](../../programming-guide/statements-expressions-operators/using-conversion-operators.md).</span></span>

## <a name="example"></a><span data-ttu-id="cf191-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="cf191-113">Example</span></span>

<span data-ttu-id="cf191-114">O exemplo a seguir fornece uma classe `Fahrenheit` e uma classe `Celsius` e cada uma delas fornece um operador de conversão explícita para a outra classe.</span><span class="sxs-lookup"><span data-stu-id="cf191-114">The following example provides a `Fahrenheit` and a `Celsius` class, each of which provides an explicit conversion operator to the other class.</span></span>

[!code-csharp[csrefKeywordsConversion#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsConversion/CS/csrefKeywordsConversion.cs#1)]

## <a name="example"></a><span data-ttu-id="cf191-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="cf191-115">Example</span></span>

<span data-ttu-id="cf191-116">O exemplo a seguir define um struct `Digit`, que representa um único dígito decimal.</span><span class="sxs-lookup"><span data-stu-id="cf191-116">The following example defines a struct, `Digit`, that represents a single decimal digit.</span></span> <span data-ttu-id="cf191-117">Um operador é definido para conversões de `byte` para `Digit`, mas como nem todos os bytes podem ser convertidos para um `Digit`, a conversão é explícita.</span><span class="sxs-lookup"><span data-stu-id="cf191-117">An operator is defined for conversions from `byte` to `Digit`, but because not all bytes can be converted to a `Digit`, the conversion is explicit.</span></span>

[!code-csharp[csrefKeywordsConversion#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsConversion/CS/csrefKeywordsConversion.cs#4)]

## <a name="c-language-specification"></a><span data-ttu-id="cf191-118">especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="cf191-118">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="cf191-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cf191-119">See also</span></span>

[<span data-ttu-id="cf191-120">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="cf191-120">C# Reference</span></span>](../index.md)  
[<span data-ttu-id="cf191-121">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="cf191-121">C# Programming Guide</span></span>](../../programming-guide/index.md)  
[<span data-ttu-id="cf191-122">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="cf191-122">C# Keywords</span></span>](index.md)  
[<span data-ttu-id="cf191-123">implicit</span><span class="sxs-lookup"><span data-stu-id="cf191-123">implicit</span></span>](implicit.md)  
[<span data-ttu-id="cf191-124">operator (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="cf191-124">operator (C# Reference)</span></span>](operator.md)  
[<span data-ttu-id="cf191-125">Como implementar conversões definidas pelo usuário entre structs</span><span class="sxs-lookup"><span data-stu-id="cf191-125">How to: Implement User-Defined Conversions Between Structs</span></span>](../../programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)  
[<span data-ttu-id="cf191-126">Conversões explícitas encadeadas definidas pelo usuário em C#</span><span class="sxs-lookup"><span data-stu-id="cf191-126">Chained user-defined explicit conversions in C#</span></span>](https://blogs.msdn.microsoft.com/ericlippert/2007/04/16/chained-user-defined-explicit-conversions-in-c/)  