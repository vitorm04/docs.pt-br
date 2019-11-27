---
title: Como testar se dois objetos são iguais
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], reference
- Is operator [Visual Basic], comparing objects
- reference variables [Visual Basic]
- variables [Visual Basic], referring to same object
- objects [Visual Basic], variables referring to same
- Visual Basic code, operators
ms.assetid: f760e828-8704-4256-bc2d-c22a4c93b524
ms.openlocfilehash: 22e8e1e688d9e3bc3804899103ee78814aac235b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343625"
---
# <a name="how-to-test-whether-two-objects-are-the-same-visual-basic"></a><span data-ttu-id="ba1a3-102">Como testar se dois objetos são iguais (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ba1a3-102">How to: Test Whether Two Objects Are the Same (Visual Basic)</span></span>
<span data-ttu-id="ba1a3-103">Se você tiver duas variáveis que se referem a objetos, poderá usar o operador `Is` ou `IsNot`, ou ambos, para determinar se eles se referem à mesma instância.</span><span class="sxs-lookup"><span data-stu-id="ba1a3-103">If you have two variables that refer to objects, you can use either the `Is` or `IsNot` operator, or both, to determine whether they refer to the same instance.</span></span>  
  
### <a name="to-test-whether-two-objects-are-the-same"></a><span data-ttu-id="ba1a3-104">Para testar se dois objetos são iguais</span><span class="sxs-lookup"><span data-stu-id="ba1a3-104">To test whether two objects are the same</span></span>  
  
- <span data-ttu-id="ba1a3-105">Use o [operador is](../../../../visual-basic/language-reference/operators/is-operator.md) ou o [operador IsNot](../../../../visual-basic/language-reference/operators/isnot-operator.md) com as duas variáveis como operandos.</span><span class="sxs-lookup"><span data-stu-id="ba1a3-105">Use the [Is Operator](../../../../visual-basic/language-reference/operators/is-operator.md) or the [IsNot Operator](../../../../visual-basic/language-reference/operators/isnot-operator.md) with the two variables as operands.</span></span>  
  
     [!code-vb[VbVbalrOperators#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#69)]  
  
 <span data-ttu-id="ba1a3-106">Talvez você queira executar uma determinada ação dependendo se dois objetos se referem à mesma instância.</span><span class="sxs-lookup"><span data-stu-id="ba1a3-106">You might want to take a certain action depending on whether two objects refer to the same instance.</span></span> <span data-ttu-id="ba1a3-107">O exemplo anterior compara o controle `c` com o controle ativo no `f`de formulário.</span><span class="sxs-lookup"><span data-stu-id="ba1a3-107">The preceding example compares control `c` against the active control on form `f`.</span></span> <span data-ttu-id="ba1a3-108">Se não houver nenhum controle ativo, ou se houver um, mas não for a mesma instância de controle que `c`, a instrução `If` falhará e o procedimento retornará sem processamento adicional.</span><span class="sxs-lookup"><span data-stu-id="ba1a3-108">If there is no active control, or if there is one but it is not the same control instance as `c`, then the `If` statement fails and the procedure returns without further processing.</span></span>  
  
 <span data-ttu-id="ba1a3-109">Se você usa `Is` ou `IsNot` é uma questão de conveniência pessoal.</span><span class="sxs-lookup"><span data-stu-id="ba1a3-109">Whether you use `Is` or `IsNot` is a matter of personal convenience to you.</span></span> <span data-ttu-id="ba1a3-110">Uma delas pode ser mais fácil de ler do que a outra em uma determinada expressão.</span><span class="sxs-lookup"><span data-stu-id="ba1a3-110">One might be easier to read than the other in a given expression.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba1a3-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ba1a3-111">See also</span></span>

- [<span data-ttu-id="ba1a3-112">Operadores de comparação no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ba1a3-112">Comparison Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
