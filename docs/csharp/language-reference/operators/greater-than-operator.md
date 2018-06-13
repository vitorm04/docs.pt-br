---
title: Operador &gt; (Referência de C#)
ms.date: 07/20/2015
f1_keywords:
- '>_CSharpKeyword'
helpviewer_keywords:
- '> operator [C#]'
- greater than operator (>) [C#]
ms.assetid: 26d3cb69-9c0b-4cc5-858b-5be1abd6659d
ms.openlocfilehash: 1589c5e785b33db6106a0ef0a58202e771db9fa0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33273492"
---
# <a name="gt-operator-c-reference"></a><span data-ttu-id="6d274-102">Operador &gt; (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="6d274-102">&gt; Operator (C# Reference)</span></span>
<span data-ttu-id="6d274-103">Todos os tipos numéricos e de enumeração definem um operador relacional "maior que" (`>`) que retornará `true` se o primeiro operando for maior que o segundo, caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="6d274-103">All numeric and enumeration types define a "greater than" relational operator (`>`) that returns `true` if the first operand is greater than the second, `false` otherwise.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6d274-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="6d274-104">Remarks</span></span>  
 <span data-ttu-id="6d274-105">Os tipos definidos pelo usuário podem sobrecarregar o operador `>` (consulte [operador](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="6d274-105">User-defined types can overload the `>` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="6d274-106">Se `>` estiver sobrecarregado, [<](../../../csharp/language-reference/operators/less-than-operator.md) também deverá estar sobrecarregado.</span><span class="sxs-lookup"><span data-stu-id="6d274-106">If `>` is overloaded, [<](../../../csharp/language-reference/operators/less-than-operator.md) must also be overloaded.</span></span> <span data-ttu-id="6d274-107">Quando um operador binário está sobrecarregado, o operador de atribuição correspondente, se houver, também estará implicitamente sobrecarregado.</span><span class="sxs-lookup"><span data-stu-id="6d274-107">When a binary operator is overloaded, the corresponding assignment operator, if any, is also implicitly overloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6d274-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6d274-108">Example</span></span>  
 [!code-csharp[csRefOperators#29](../../../csharp/language-reference/operators/codesnippet/CSharp/greater-than-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="6d274-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6d274-109">See Also</span></span>  
 [<span data-ttu-id="6d274-110">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="6d274-110">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="6d274-111">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="6d274-111">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="6d274-112">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="6d274-112">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
 [<span data-ttu-id="6d274-113">explicit</span><span class="sxs-lookup"><span data-stu-id="6d274-113">explicit</span></span>](../../../csharp/language-reference/keywords/explicit.md)
