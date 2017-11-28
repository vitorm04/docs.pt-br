---
title: "Operador | (Referência de C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: '|_CSharpKeyword'
helpviewer_keywords:
- bitwise OR operator [C#]
- '| operator [C#]'
- binary operator (|) [C#]
ms.assetid: 82d6bb78-54c8-40bf-b679-531180ddaf70
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 374adc30e6937a68d67bfae152f2546c854b829b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a><span data-ttu-id="56dab-102">Operador | (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="56dab-102">| Operator (C# Reference)</span></span>
<span data-ttu-id="56dab-103">Os operadores binários `|` são predefinidos para os tipos integrais e `bool`.</span><span class="sxs-lookup"><span data-stu-id="56dab-103">Binary `|` operators are predefined for the integral types and `bool`.</span></span> <span data-ttu-id="56dab-104">Para tipos integrais, o `|` computa o OR bit a bit de seus operandos.</span><span class="sxs-lookup"><span data-stu-id="56dab-104">For integral types, `|` computes the bitwise OR of its operands.</span></span> <span data-ttu-id="56dab-105">Para operandos `bool`, o `|` computa o OR lógico de seus operandos; ou seja, o resultado será `false` se e somente se, ambos seus operandos forem `false`.</span><span class="sxs-lookup"><span data-stu-id="56dab-105">For `bool` operands, `|` computes the logical OR of its operands; that is, the result is `false` if and only if both its operands are `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="56dab-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="56dab-106">Remarks</span></span>  
 <span data-ttu-id="56dab-107">Os tipos definidos pelo usuário podem sobrecarregar o operador `|` (consulte [operador](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="56dab-107">User-defined types can overload the `|` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="56dab-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="56dab-108">Example</span></span>  
 [!code-csharp[csRefOperators#31](../../../csharp/language-reference/operators/codesnippet/CSharp/or-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="56dab-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="56dab-109">See Also</span></span>  
 [<span data-ttu-id="56dab-110">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="56dab-110">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="56dab-111">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="56dab-111">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="56dab-112">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="56dab-112">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
