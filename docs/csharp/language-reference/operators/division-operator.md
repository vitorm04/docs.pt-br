---
title: Operador / (Referência de C#)
ms.date: 07/20/2015
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
ms.openlocfilehash: 9e12e5c472266ea75d3f572a2091bd0784ea5dcf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a><span data-ttu-id="808e6-102">Operador / (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="808e6-102">/ Operator (C# Reference)</span></span>
<span data-ttu-id="808e6-103">O operador de divisão (`/`) divide o primeiro operando pelo segundo.</span><span class="sxs-lookup"><span data-stu-id="808e6-103">The division operator (`/`) divides its first operand by its second operand.</span></span> <span data-ttu-id="808e6-104">Todos os tipos numéricos têm operadores de divisão predefinidos.</span><span class="sxs-lookup"><span data-stu-id="808e6-104">All numeric types have predefined division operators.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="808e6-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="808e6-105">Remarks</span></span>  
 <span data-ttu-id="808e6-106">Os tipos definidos pelo usuário podem sobrecarregar o operador `/` (consulte [operador](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="808e6-106">User-defined types can overload the `/` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="808e6-107">Uma sobrecarga do operador `/` sobrecarrega implicitamente o [operador /=](division-assignment-operator.md).</span><span class="sxs-lookup"><span data-stu-id="808e6-107">An overload of the `/` operator implicitly overloads the [/= operator](division-assignment-operator.md).</span></span>  
  
 <span data-ttu-id="808e6-108">Quando você divide dois números inteiros, o resultado sempre é um número inteiro.</span><span class="sxs-lookup"><span data-stu-id="808e6-108">When you divide two integers, the result is always an integer.</span></span> <span data-ttu-id="808e6-109">Por exemplo, o resultado do 7/3 é 2.</span><span class="sxs-lookup"><span data-stu-id="808e6-109">For example, the result of 7 / 3 is 2.</span></span> <span data-ttu-id="808e6-110">Para determinar o resto de 7/3, use o operador de resto ([%](../../../csharp/language-reference/operators/modulus-operator.md)).</span><span class="sxs-lookup"><span data-stu-id="808e6-110">To determine the remainder of 7 / 3, use the remainder operator ([%](../../../csharp/language-reference/operators/modulus-operator.md)).</span></span> <span data-ttu-id="808e6-111">Para obter um quociente como um número racional ou fração, dê ao dividendo ou divisor o tipo `float` ou o tipo `double`.</span><span class="sxs-lookup"><span data-stu-id="808e6-111">To obtain a quotient as a rational number or fraction, give the dividend or divisor type `float` or type `double`.</span></span> <span data-ttu-id="808e6-112">Você poderá atribuir o tipo implicitamente se expressar o dividendo ou divisor como um decimal colocando um dígito à direita do ponto decimal, como mostra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="808e6-112">You can assign the type implicitly if you express the dividend or divisor as a decimal by putting a digit to the right side of the decimal point, as the following example shows.</span></span>  
  
## <a name="example"></a><span data-ttu-id="808e6-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="808e6-113">Example</span></span>  
 [!code-csharp[csRefOperators#42](../../../csharp/language-reference/operators/codesnippet/CSharp/division-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="808e6-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="808e6-114">See Also</span></span>  
 [<span data-ttu-id="808e6-115">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="808e6-115">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="808e6-116">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="808e6-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="808e6-117">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="808e6-117">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
