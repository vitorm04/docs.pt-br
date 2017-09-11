---
title: "Operador != (Referência de C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '!=_CSharpKeyword'
dev_langs:
- CSharp
helpviewer_keywords:
- inequality operator (!=) [C#]
- not equals operator (!=) [C#]
- '!= operator [C#]'
ms.assetid: eeff7a4e-ad6f-462d-9f8d-49e9b91c6c97
caps.latest.revision: 14
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 49c5c9668c6b1169220ee4fa0babf167292a9813
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="-operator-c-reference"></a><span data-ttu-id="5a33b-102">Operador != (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="5a33b-102">!= Operator (C# Reference)</span></span>
<span data-ttu-id="5a33b-103">O operador de desigualdade (`!=`) retornará false se seus operandos forem iguais; caso contrário, true.</span><span class="sxs-lookup"><span data-stu-id="5a33b-103">The inequality operator (`!=`) returns false if its operands are equal, true otherwise.</span></span> <span data-ttu-id="5a33b-104">Os operadores de desigualdade são predefinidos para todos os tipos, incluindo cadeia de caracteres e objeto.</span><span class="sxs-lookup"><span data-stu-id="5a33b-104">Inequality operators are predefined for all types, including string and object.</span></span> <span data-ttu-id="5a33b-105">Os tipos definidos pelo usuário podem sobrecarregar o operador `!=`.</span><span class="sxs-lookup"><span data-stu-id="5a33b-105">User-defined types can overload the `!=` operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5a33b-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="5a33b-106">Remarks</span></span>  
 <span data-ttu-id="5a33b-107">Para tipos de valor predefinidos, o operador de desigualdade (`!=`) retornará true se os valores dos seus operandos forem diferentes; caso contrário, false.</span><span class="sxs-lookup"><span data-stu-id="5a33b-107">For predefined value types, the inequality operator (`!=`) returns true if the values of its operands are different, false otherwise.</span></span> <span data-ttu-id="5a33b-108">Para tipos de referência diferentes de `string`, o `!=` retornará true se seus dois operandos se referirem a objetos diferentes.</span><span class="sxs-lookup"><span data-stu-id="5a33b-108">For reference types other than `string`, `!=` returns true if its two operands refer to different objects.</span></span> <span data-ttu-id="5a33b-109">Para o tipo `string`, o `!=` compara os valores das cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="5a33b-109">For the `string` type, `!=` compares the values of the strings.</span></span>  
  
 <span data-ttu-id="5a33b-110">Os tipos de valor definidos pelo usuário podem sobrecarregar o operador `!=` (consulte [operador](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="5a33b-110">User-defined value types can overload the `!=` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="5a33b-111">Os tipos de referência definidos pelo usuário também podem fazer isso, embora o `!=` se comporte, por padrão, conforme descrito acima para os tipos de referência predefinidos e definidos pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="5a33b-111">So can user-defined reference types, although by default `!=` behaves as described above for both predefined and user-defined reference types.</span></span> <span data-ttu-id="5a33b-112">Se `!=` estiver sobrecarregado, [==](../../../csharp/language-reference/operators/equality-comparison-operator.md) também deverá estar sobrecarregado.</span><span class="sxs-lookup"><span data-stu-id="5a33b-112">If `!=` is overloaded, [==](../../../csharp/language-reference/operators/equality-comparison-operator.md) must also be overloaded.</span></span> <span data-ttu-id="5a33b-113">As operações em tipos integrais geralmente são permitidas na enumeração.</span><span class="sxs-lookup"><span data-stu-id="5a33b-113">Operations on integral types are generally allowed on enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5a33b-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5a33b-114">Example</span></span>  
 <span data-ttu-id="5a33b-115">[!code-cs[csRefOperators#33](../../../csharp/language-reference/operators/codesnippet/CSharp/not-equal-operator_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="5a33b-115">[!code-cs[csRefOperators#33](../../../csharp/language-reference/operators/codesnippet/CSharp/not-equal-operator_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a33b-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5a33b-116">See Also</span></span>  
 <span data-ttu-id="5a33b-117">[Referência de C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="5a33b-117">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="5a33b-118">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="5a33b-118">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="5a33b-119">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="5a33b-119">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)

