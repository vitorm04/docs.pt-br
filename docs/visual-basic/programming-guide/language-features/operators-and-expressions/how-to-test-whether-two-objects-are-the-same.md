---
title: "Como: testar se dois objetos são iguais (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- variables [Visual Basic], reference
- Is operator [Visual Basic], comparing objects
- reference variables
- variables [Visual Basic], referring to same object
- objects [Visual Basic], variables referring to same
- Visual Basic code, operators
ms.assetid: f760e828-8704-4256-bc2d-c22a4c93b524
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 1ad28e8de79cc64e945ee638df13591fe69331a9
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-test-whether-two-objects-are-the-same-visual-basic"></a><span data-ttu-id="7eef2-102">Como testar se dois objetos são iguais (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7eef2-102">How to: Test Whether Two Objects Are the Same (Visual Basic)</span></span>
<span data-ttu-id="7eef2-103">Se você tiver duas variáveis que se referem a objetos, você pode usar o `Is` ou `IsNot` operador, ou ambos, para determinar se eles se referem à mesma instância.</span><span class="sxs-lookup"><span data-stu-id="7eef2-103">If you have two variables that refer to objects, you can use either the `Is` or `IsNot` operator, or both, to determine whether they refer to the same instance.</span></span>  
  
### <a name="to-test-whether-two-objects-are-the-same"></a><span data-ttu-id="7eef2-104">Para testar se dois objetos são iguais</span><span class="sxs-lookup"><span data-stu-id="7eef2-104">To test whether two objects are the same</span></span>  
  
-   <span data-ttu-id="7eef2-105">Use o [operador Is](../../../../visual-basic/language-reference/operators/is-operator.md) ou [operador IsNot](../../../../visual-basic/language-reference/operators/isnot-operator.md) com as duas variáveis como operandos.</span><span class="sxs-lookup"><span data-stu-id="7eef2-105">Use the [Is Operator](../../../../visual-basic/language-reference/operators/is-operator.md) or the [IsNot Operator](../../../../visual-basic/language-reference/operators/isnot-operator.md) with the two variables as operands.</span></span>  
  
     <span data-ttu-id="7eef2-106">[!code-vb[VbVbalrOperators&#69;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-test-whether-two-objects-are-the-same_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="7eef2-106">[!code-vb[VbVbalrOperators#69](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-test-whether-two-objects-are-the-same_1.vb)]</span></span>  
  
 <span data-ttu-id="7eef2-107">Você talvez queira levar uma determinada ação dependendo se dois objetos se referem à mesma instância.</span><span class="sxs-lookup"><span data-stu-id="7eef2-107">You might want to take a certain action depending on whether two objects refer to the same instance.</span></span> <span data-ttu-id="7eef2-108">O exemplo anterior compara controle `c` contra o controle ativo no formulário `f`.</span><span class="sxs-lookup"><span data-stu-id="7eef2-108">The preceding example compares control `c` against the active control on form `f`.</span></span> <span data-ttu-id="7eef2-109">Se não há nenhum controle ativo, ou se houver um, mas não é a mesma instância de controle como `c`, o `If` instrução falhará e o procedimento retornará sem processamento adicional.</span><span class="sxs-lookup"><span data-stu-id="7eef2-109">If there is no active control, or if there is one but it is not the same control instance as `c`, then the `If` statement fails and the procedure returns without further processing.</span></span>  
  
 <span data-ttu-id="7eef2-110">Se você usar `Is` ou `IsNot` é uma questão de conveniência pessoal para você.</span><span class="sxs-lookup"><span data-stu-id="7eef2-110">Whether you use `Is` or `IsNot` is a matter of personal convenience to you.</span></span> <span data-ttu-id="7eef2-111">Um pode ser mais fácil de ler do que a outra em uma determinada expressão.</span><span class="sxs-lookup"><span data-stu-id="7eef2-111">One might be easier to read than the other in a given expression.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7eef2-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7eef2-112">See Also</span></span>  
 [<span data-ttu-id="7eef2-113">Operadores de comparação em Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7eef2-113">Comparison Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
