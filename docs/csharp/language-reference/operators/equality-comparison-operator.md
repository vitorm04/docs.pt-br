---
title: Operador == (Referência de C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ==_CSharpKeyword
helpviewer_keywords:
- == operator [C#]
- equality operator [C#]
ms.assetid: 34c6b597-caa2-4855-a7cd-38ecdd11bd07
caps.latest.revision: 14
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ca22846325968519a1f7625461867c0d83a1a9f5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a><span data-ttu-id="7f099-102">Operador == (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="7f099-102">== Operator (C# Reference)</span></span>
<span data-ttu-id="7f099-103">Para tipos de valor predefinidos, o operador de igualdade (`==`) retornará true se os valores dos seus operandos forem iguais; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="7f099-103">For predefined value types, the equality operator (`==`) returns true if the values of its operands are equal, `false` otherwise.</span></span> <span data-ttu-id="7f099-104">Para tipos de referência diferentes de [cadeia de caracteres](../../../csharp/language-reference/keywords/string.md), o `==` retornará `true` se seus dois operandos se referirem ao mesmo objeto.</span><span class="sxs-lookup"><span data-stu-id="7f099-104">For reference types other than [string](../../../csharp/language-reference/keywords/string.md), `==` returns `true` if its two operands refer to the same object.</span></span> <span data-ttu-id="7f099-105">Para o tipo `string`, o `==` compara os valores das cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="7f099-105">For the `string` type, `==` compares the values of the strings.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7f099-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="7f099-106">Remarks</span></span>  
 <span data-ttu-id="7f099-107">Os tipos de valor definidos pelo usuário podem sobrecarregar o operador `==` (consulte [operador](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="7f099-107">User-defined value types can overload the `==` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="7f099-108">Os tipos de referência definidos pelo usuário também podem fazer isso, embora o `==` se comporte, por padrão, conforme descrito acima para os tipos de referência predefinidos e definidos pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="7f099-108">So can user-defined reference types, although by default `==` behaves as described above for both predefined and user-defined reference types.</span></span> <span data-ttu-id="7f099-109">Se `==` estiver sobrecarregado, [!=](../../../csharp/language-reference/operators/not-equal-operator.md) também deverá estar sobrecarregado.</span><span class="sxs-lookup"><span data-stu-id="7f099-109">If `==` is overloaded, [!=](../../../csharp/language-reference/operators/not-equal-operator.md) must also be overloaded.</span></span> <span data-ttu-id="7f099-110">As operações em tipos integrais geralmente são permitidas na enumeração.</span><span class="sxs-lookup"><span data-stu-id="7f099-110">Operations on integral types are generally allowed on enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7f099-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7f099-111">Example</span></span>  
 [!code-csharp[csRefOperators#36](../../../csharp/language-reference/operators/codesnippet/CSharp/equality-comparison-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="7f099-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7f099-112">See Also</span></span>  
 [<span data-ttu-id="7f099-113">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="7f099-113">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="7f099-114">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="7f099-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="7f099-115">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="7f099-115">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
