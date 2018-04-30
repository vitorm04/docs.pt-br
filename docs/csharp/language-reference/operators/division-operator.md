---
title: Operador / (Referência de C#)
ms.date: 04/04/2018
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /_CSharpKeyword
helpviewer_keywords:
- / operator [C#]
- division operator [C#]
ms.assetid: d155e496-678f-4efa-bebe-2bd08da2c5af
caps.latest.revision: 21
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 5b17d122e3e3f75012e084903b6f8975fb53d46c
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
---
# <a name="-operator-c-reference"></a><span data-ttu-id="a9421-102">Operador / (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="a9421-102">/ Operator (C# Reference)</span></span>
<span data-ttu-id="a9421-103">O operador de divisão (`/`) divide o primeiro operando pelo segundo.</span><span class="sxs-lookup"><span data-stu-id="a9421-103">The division operator (`/`) divides its first operand by its second operand.</span></span> <span data-ttu-id="a9421-104">Todos os tipos numéricos têm operadores de divisão predefinidos.</span><span class="sxs-lookup"><span data-stu-id="a9421-104">All numeric types have predefined division operators.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="a9421-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="a9421-105">Remarks</span></span>  
 <span data-ttu-id="a9421-106">Os tipos definidos pelo usuário podem sobrecarregar o operador `/` (consulte [operador](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="a9421-106">User-defined types can overload the `/` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="a9421-107">Uma sobrecarga do operador `/` sobrecarrega implicitamente o [operador /=](division-assignment-operator.md).</span><span class="sxs-lookup"><span data-stu-id="a9421-107">An overload of the `/` operator implicitly overloads the [/= operator](division-assignment-operator.md).</span></span>  
  
 <span data-ttu-id="a9421-108">Quando você divide dois números inteiros, o resultado sempre é um número inteiro.</span><span class="sxs-lookup"><span data-stu-id="a9421-108">When you divide two integers, the result is always an integer.</span></span> <span data-ttu-id="a9421-109">Por exemplo, o resultado do 7/3 é 2.</span><span class="sxs-lookup"><span data-stu-id="a9421-109">For example, the result of 7 / 3 is 2.</span></span> <span data-ttu-id="a9421-110">Não deve ser confundido com a divisão pelo piso, pois o operador `/` é arredondado no sentido de zero: -7/3 é -2.</span><span class="sxs-lookup"><span data-stu-id="a9421-110">This is not to be confused with floored division, as the `/` operator rounds towards zero: -7 / 3 is -2.</span></span>  
  
 <span data-ttu-id="a9421-111">Para obter um quociente como um número racional, use os tipos `float`, `double` ou `decimal`.</span><span class="sxs-lookup"><span data-stu-id="a9421-111">To obtain a quotient as a rational number, use the `float`, `double`, or `decimal` types.</span></span> <span data-ttu-id="a9421-112">Há várias maneiras de converter entre [tipos numéricos internos](../../../csharp/language-reference/keywords/reference-tables-for-types.md).</span><span class="sxs-lookup"><span data-stu-id="a9421-112">There are many ways to convert between [built in numeric types](../../../csharp/language-reference/keywords/reference-tables-for-types.md).</span></span>  
  
 <span data-ttu-id="a9421-113">Para determinar o resto, use o [operador de resto](../../../csharp/language-reference/operators/remainder-operator.md) `%`.</span><span class="sxs-lookup"><span data-stu-id="a9421-113">To determine the remainder, use the [remainder operator](../../../csharp/language-reference/operators/remainder-operator.md) `%`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a9421-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a9421-114">Example</span></span>  
 [!code-csharp[csRefOperators#42](../../../csharp/language-reference/operators/codesnippet/CSharp/division-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="a9421-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a9421-115">See Also</span></span>  
 [<span data-ttu-id="a9421-116">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="a9421-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="a9421-117">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="a9421-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="a9421-118">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="a9421-118">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
