---
title: "Como testar se dois objetos são iguais (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- variables [Visual Basic], reference
- Is operator [Visual Basic], comparing objects
- reference variables [Visual Basic]
- variables [Visual Basic], referring to same object
- objects [Visual Basic], variables referring to same
- Visual Basic code, operators
ms.assetid: f760e828-8704-4256-bc2d-c22a4c93b524
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 76f5c19386cce84207f80d217326d2e3babf4e44
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-test-whether-two-objects-are-the-same-visual-basic"></a><span data-ttu-id="56d27-102">Como testar se dois objetos são iguais (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="56d27-102">How to: Test Whether Two Objects Are the Same (Visual Basic)</span></span>
<span data-ttu-id="56d27-103">Se você tiver duas variáveis que se referem a objetos, você pode usar o `Is` ou `IsNot` operador, ou ambos, para determinar se eles se referem à mesma instância.</span><span class="sxs-lookup"><span data-stu-id="56d27-103">If you have two variables that refer to objects, you can use either the `Is` or `IsNot` operator, or both, to determine whether they refer to the same instance.</span></span>  
  
### <a name="to-test-whether-two-objects-are-the-same"></a><span data-ttu-id="56d27-104">Para testar se dois objetos são iguais</span><span class="sxs-lookup"><span data-stu-id="56d27-104">To test whether two objects are the same</span></span>  
  
-   <span data-ttu-id="56d27-105">Use o [operador Is](../../../../visual-basic/language-reference/operators/is-operator.md) ou [operador IsNot](../../../../visual-basic/language-reference/operators/isnot-operator.md) com as duas variáveis como operandos.</span><span class="sxs-lookup"><span data-stu-id="56d27-105">Use the [Is Operator](../../../../visual-basic/language-reference/operators/is-operator.md) or the [IsNot Operator](../../../../visual-basic/language-reference/operators/isnot-operator.md) with the two variables as operands.</span></span>  
  
     [!code-vb[VbVbalrOperators#69](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-test-whether-two-objects-are-the-same_1.vb)]  
  
 <span data-ttu-id="56d27-106">Convém levar a uma determinada ação dependendo se dois objetos se referem à mesma instância.</span><span class="sxs-lookup"><span data-stu-id="56d27-106">You might want to take a certain action depending on whether two objects refer to the same instance.</span></span> <span data-ttu-id="56d27-107">O exemplo anterior compara controle `c` contra o controle ativo no formulário `f`.</span><span class="sxs-lookup"><span data-stu-id="56d27-107">The preceding example compares control `c` against the active control on form `f`.</span></span> <span data-ttu-id="56d27-108">Se não há nenhum controle ativo, ou se houver uma, mas não é a mesma instância do controle como `c`, em seguida, o `If` instrução falhará e o procedimento retornará sem processamento adicional.</span><span class="sxs-lookup"><span data-stu-id="56d27-108">If there is no active control, or if there is one but it is not the same control instance as `c`, then the `If` statement fails and the procedure returns without further processing.</span></span>  
  
 <span data-ttu-id="56d27-109">Se você usar `Is` ou `IsNot` é uma questão de conveniência pessoal para você.</span><span class="sxs-lookup"><span data-stu-id="56d27-109">Whether you use `Is` or `IsNot` is a matter of personal convenience to you.</span></span> <span data-ttu-id="56d27-110">Um pode ser mais fácil de ler que o outro em uma determinada expressão.</span><span class="sxs-lookup"><span data-stu-id="56d27-110">One might be easier to read than the other in a given expression.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56d27-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="56d27-111">See Also</span></span>  
 [<span data-ttu-id="56d27-112">Operadores de comparação no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="56d27-112">Comparison Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
