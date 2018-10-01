---
title: Operador != (Referência de C#)
ms.date: 07/20/2015
f1_keywords:
- '!=_CSharpKeyword'
helpviewer_keywords:
- inequality operator (!=) [C#]
- not equals operator (!=) [C#]
- '!= operator [C#]'
ms.assetid: eeff7a4e-ad6f-462d-9f8d-49e9b91c6c97
ms.openlocfilehash: e974ffb1b25944e24fca23864dc7e932ec1876d5
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47455468"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="bb787-102">Operador != (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="bb787-102">!= Operator (C# Reference)</span></span>
<span data-ttu-id="bb787-103">O operador de desigualdade (`!=`) retornará false se seus operandos forem iguais; caso contrário, true.</span><span class="sxs-lookup"><span data-stu-id="bb787-103">The inequality operator (`!=`) returns false if its operands are equal, true otherwise.</span></span> <span data-ttu-id="bb787-104">Os operadores de desigualdade são predefinidos para todos os tipos, incluindo cadeia de caracteres e objeto.</span><span class="sxs-lookup"><span data-stu-id="bb787-104">Inequality operators are predefined for all types, including string and object.</span></span> <span data-ttu-id="bb787-105">Os tipos definidos pelo usuário podem sobrecarregar o operador `!=`.</span><span class="sxs-lookup"><span data-stu-id="bb787-105">User-defined types can overload the `!=` operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bb787-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="bb787-106">Remarks</span></span>  
 <span data-ttu-id="bb787-107">Para tipos de valor predefinidos, o operador de desigualdade (`!=`) retornará true se os valores dos seus operandos forem diferentes; caso contrário, false.</span><span class="sxs-lookup"><span data-stu-id="bb787-107">For predefined value types, the inequality operator (`!=`) returns true if the values of its operands are different, false otherwise.</span></span> <span data-ttu-id="bb787-108">Para tipos de referência diferentes de `string`, o `!=` retornará true se seus dois operandos se referirem a objetos diferentes.</span><span class="sxs-lookup"><span data-stu-id="bb787-108">For reference types other than `string`, `!=` returns true if its two operands refer to different objects.</span></span> <span data-ttu-id="bb787-109">Para o tipo `string`, o `!=` compara os valores das cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="bb787-109">For the `string` type, `!=` compares the values of the strings.</span></span>  
  
 <span data-ttu-id="bb787-110">Os tipos de valor definidos pelo usuário podem sobrecarregar o operador `!=` (consulte [operador](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="bb787-110">User-defined value types can overload the `!=` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="bb787-111">Os tipos de referência definidos pelo usuário também podem fazer isso, embora o `!=` se comporte, por padrão, conforme descrito acima para os tipos de referência predefinidos e definidos pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="bb787-111">So can user-defined reference types, although by default `!=` behaves as described above for both predefined and user-defined reference types.</span></span> <span data-ttu-id="bb787-112">Se `!=` estiver sobrecarregado, [==](../../../csharp/language-reference/operators/equality-comparison-operator.md) também deverá estar sobrecarregado.</span><span class="sxs-lookup"><span data-stu-id="bb787-112">If `!=` is overloaded, [==](../../../csharp/language-reference/operators/equality-comparison-operator.md) must also be overloaded.</span></span> <span data-ttu-id="bb787-113">As operações em tipos integrais geralmente são permitidas na enumeração.</span><span class="sxs-lookup"><span data-stu-id="bb787-113">Operations on integral types are generally allowed on enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bb787-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bb787-114">Example</span></span>  
 [!code-csharp[csRefOperators#33](../../../csharp/language-reference/operators/codesnippet/CSharp/not-equal-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="bb787-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bb787-115">See Also</span></span>

- [<span data-ttu-id="bb787-116">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="bb787-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="bb787-117">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="bb787-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="bb787-118">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="bb787-118">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
