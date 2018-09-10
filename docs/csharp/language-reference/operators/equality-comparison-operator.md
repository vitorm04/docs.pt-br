---
title: Operador == (Referência de C#)
ms.date: 07/20/2015
f1_keywords:
- ==_CSharpKeyword
helpviewer_keywords:
- == operator [C#]
- equality operator [C#]
ms.assetid: 34c6b597-caa2-4855-a7cd-38ecdd11bd07
ms.openlocfilehash: d9d7dcf3b38939e681fb51d6c674151cee78b3d0
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43779151"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="a93b9-102">Operador == (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="a93b9-102">== Operator (C# Reference)</span></span>
<span data-ttu-id="a93b9-103">Para tipos de valor predefinidos, o operador de igualdade (`==`) retornará true se os valores dos seus operandos forem iguais; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="a93b9-103">For predefined value types, the equality operator (`==`) returns true if the values of its operands are equal, `false` otherwise.</span></span> <span data-ttu-id="a93b9-104">Para tipos de referência diferentes de [cadeia de caracteres](../../../csharp/language-reference/keywords/string.md), o `==` retornará `true` se seus dois operandos se referirem ao mesmo objeto.</span><span class="sxs-lookup"><span data-stu-id="a93b9-104">For reference types other than [string](../../../csharp/language-reference/keywords/string.md), `==` returns `true` if its two operands refer to the same object.</span></span> <span data-ttu-id="a93b9-105">Para o tipo `string`, o `==` compara os valores das cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="a93b9-105">For the `string` type, `==` compares the values of the strings.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a93b9-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="a93b9-106">Remarks</span></span>  
 <span data-ttu-id="a93b9-107">Os tipos de valor definidos pelo usuário podem sobrecarregar o operador `==` (consulte [operador](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="a93b9-107">User-defined value types can overload the `==` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="a93b9-108">Os tipos de referência definidos pelo usuário também podem fazer isso, embora o `==` se comporte, por padrão, conforme descrito acima para os tipos de referência predefinidos e definidos pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="a93b9-108">So can user-defined reference types, although by default `==` behaves as described above for both predefined and user-defined reference types.</span></span> <span data-ttu-id="a93b9-109">Se `==` estiver sobrecarregado, [!=](../../../csharp/language-reference/operators/not-equal-operator.md) também deverá estar sobrecarregado.</span><span class="sxs-lookup"><span data-stu-id="a93b9-109">If `==` is overloaded, [!=](../../../csharp/language-reference/operators/not-equal-operator.md) must also be overloaded.</span></span> <span data-ttu-id="a93b9-110">As operações em tipos integrais geralmente são permitidas na enumeração.</span><span class="sxs-lookup"><span data-stu-id="a93b9-110">Operations on integral types are generally allowed on enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a93b9-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a93b9-111">Example</span></span>  
 [!code-csharp[csRefOperators#36](../../../csharp/language-reference/operators/codesnippet/CSharp/equality-comparison-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="a93b9-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a93b9-112">See Also</span></span>

- [<span data-ttu-id="a93b9-113">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="a93b9-113">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="a93b9-114">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="a93b9-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="a93b9-115">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="a93b9-115">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
