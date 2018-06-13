---
title: explicit (Referência de C#)
ms.date: 07/20/2015
f1_keywords:
- explicit_CSharpKeyword
- explicit
helpviewer_keywords:
- explicit keyword [C#]
ms.assetid: cfb8f42a-e411-4db2-af9b-796b05644846
ms.openlocfilehash: c8a05aef3318eb34242ed1268ea26663592e4d1b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33216471"
---
# <a name="explicit-c-reference"></a><span data-ttu-id="ceecf-102">explicit (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="ceecf-102">explicit (C# Reference)</span></span>
<span data-ttu-id="ceecf-103">A palavra-chave `explicit` declara um operador de conversão de tipo definido pelo usuário que deve ser invocado com uma conversão.</span><span class="sxs-lookup"><span data-stu-id="ceecf-103">The `explicit` keyword declares a user-defined type conversion operator that must be invoked with a cast.</span></span> <span data-ttu-id="ceecf-104">Por exemplo, esse operador converte de uma classe chamada Fahrenheit para uma classe chamada Celsius:</span><span class="sxs-lookup"><span data-stu-id="ceecf-104">For example, this operator converts from a class called Fahrenheit to a class called Celsius:</span></span>  
  
 [!code-csharp[csrefKeywordsConversion#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/explicit_1.cs)]  
  
 <span data-ttu-id="ceecf-105">Esse operador de conversão pode ser invocado assim:</span><span class="sxs-lookup"><span data-stu-id="ceecf-105">This conversion operator can be invoked like this:</span></span>  
  
 [!code-csharp[csrefKeywordsConversion#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/explicit_2.cs)]  
  
 <span data-ttu-id="ceecf-106">O operador de conversão converte de um tipo de origem para um tipo de destino.</span><span class="sxs-lookup"><span data-stu-id="ceecf-106">The conversion operator converts from a source type to a target type.</span></span> <span data-ttu-id="ceecf-107">O tipo de origem fornece o operador de conversão.</span><span class="sxs-lookup"><span data-stu-id="ceecf-107">The source type provides the conversion operator.</span></span> <span data-ttu-id="ceecf-108">Ao contrário da conversão implícita, os operadores de conversão explícita devem ser invocados por meio de uma conversão.</span><span class="sxs-lookup"><span data-stu-id="ceecf-108">Unlike implicit conversion, explicit conversion operators must be invoked by means of a cast.</span></span> <span data-ttu-id="ceecf-109">Se uma operação de conversão pode causar exceções ou perda de informações, você deve marcá-la como `explicit`.</span><span class="sxs-lookup"><span data-stu-id="ceecf-109">If a conversion operation can cause exceptions or lose information, you should mark it `explicit`.</span></span> <span data-ttu-id="ceecf-110">Isso impede que o compilador invoque silenciosamente a operação de conversão com consequências possivelmente imprevisíveis.</span><span class="sxs-lookup"><span data-stu-id="ceecf-110">This prevents the compiler from silently invoking the conversion operation with possibly unforeseen consequences.</span></span>  
  
 <span data-ttu-id="ceecf-111">A omissão da conversão resulta no erro em tempo de compilação CS0266.</span><span class="sxs-lookup"><span data-stu-id="ceecf-111">Omitting the cast results in compile-time error CS0266.</span></span>  
  
 <span data-ttu-id="ceecf-112">Para obter mais informações, consulte [Usando Operadores de Conversão](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md).</span><span class="sxs-lookup"><span data-stu-id="ceecf-112">For more information, see [Using Conversion Operators](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ceecf-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ceecf-113">Example</span></span>  
 <span data-ttu-id="ceecf-114">O exemplo a seguir fornece uma classe `Fahrenheit` e uma classe `Celsius` e cada uma delas fornece um operador de conversão explícita para a outra classe.</span><span class="sxs-lookup"><span data-stu-id="ceecf-114">The following example provides a `Fahrenheit` and a `Celsius` class, each of which provides an explicit conversion operator to the other class.</span></span>  
  
 [!code-csharp[csrefKeywordsConversion#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/explicit_3.cs)]  
  
## <a name="example"></a><span data-ttu-id="ceecf-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ceecf-115">Example</span></span>  
 <span data-ttu-id="ceecf-116">O exemplo a seguir define um struct `Digit`, que representa um único dígito decimal.</span><span class="sxs-lookup"><span data-stu-id="ceecf-116">The following example defines a struct, `Digit`, that represents a single decimal digit.</span></span> <span data-ttu-id="ceecf-117">Um operador é definido para conversões de `byte` para `Digit`, mas como nem todos os bytes podem ser convertidos para um `Digit`, a conversão é explícita.</span><span class="sxs-lookup"><span data-stu-id="ceecf-117">An operator is defined for conversions from `byte` to `Digit`, but because not all bytes can be converted to a `Digit`, the conversion is explicit.</span></span>  
  
 [!code-csharp[csrefKeywordsConversion#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/explicit_4.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="ceecf-118">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="ceecf-118">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ceecf-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ceecf-119">See Also</span></span>  
 [<span data-ttu-id="ceecf-120">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="ceecf-120">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="ceecf-121">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="ceecf-121">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="ceecf-122">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="ceecf-122">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="ceecf-123">implicit</span><span class="sxs-lookup"><span data-stu-id="ceecf-123">implicit</span></span>](../../../csharp/language-reference/keywords/implicit.md)  
 [<span data-ttu-id="ceecf-124">operator (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="ceecf-124">operator (C# Reference)</span></span>](../../../csharp/language-reference/keywords/operator.md)  
 [<span data-ttu-id="ceecf-125">Como implementar conversões definidas pelo usuário entre structs</span><span class="sxs-lookup"><span data-stu-id="ceecf-125">How to: Implement User-Defined Conversions Between Structs</span></span>](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)  
 [<span data-ttu-id="ceecf-126">Conversões explícitas encadeadas definidas pelo usuário em C#</span><span class="sxs-lookup"><span data-stu-id="ceecf-126">Chained user-defined explicit conversions in C#</span></span>](https://blogs.msdn.microsoft.com/ericlippert/2007/04/16/chained-user-defined-explicit-conversions-in-c/)
