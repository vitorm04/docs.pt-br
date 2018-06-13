---
title: Operador IsFalse (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.isfalse
helpviewer_keywords:
- AndAlso operator [Visual Basic]
- IsFalse operator [Visual Basic]
ms.assetid: 37fc9dbf-e5cc-4570-b93f-7213447974df
ms.openlocfilehash: e84b2162eb0763725f05bc52d5c4223d7c430b81
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33600039"
---
# <a name="isfalse-operator-visual-basic"></a><span data-ttu-id="555ac-102">Operador IsFalse (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="555ac-102">IsFalse Operator (Visual Basic)</span></span>
<span data-ttu-id="555ac-103">Determina se uma expressão é `False`.</span><span class="sxs-lookup"><span data-stu-id="555ac-103">Determines whether an expression is `False`.</span></span>  
  
 <span data-ttu-id="555ac-104">Não é possível chamar `IsFalse` explicitamente no seu código, mas o Visual Basic compilador pode usá-lo para gerar código de `AndAlso` cláusulas.</span><span class="sxs-lookup"><span data-stu-id="555ac-104">You cannot call `IsFalse` explicitly in your code, but the Visual Basic compiler can use it to generate code from `AndAlso` clauses.</span></span> <span data-ttu-id="555ac-105">Se você definir uma classe ou estrutura e, em seguida, usar uma variável do tipo em um `AndAlso` cláusula, você deve definir `IsFalse` nessa classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="555ac-105">If you define a class or structure and then use a variable of that type in an `AndAlso` clause, you must define `IsFalse` on that class or structure.</span></span>  
  
 <span data-ttu-id="555ac-106">O compilador considera o `IsFalse` e `IsTrue` operadores como um *par correspondente*.</span><span class="sxs-lookup"><span data-stu-id="555ac-106">The compiler considers the `IsFalse` and `IsTrue` operators as a *matched pair*.</span></span> <span data-ttu-id="555ac-107">Isso significa que se você definir um deles, você deve também definir o outro.</span><span class="sxs-lookup"><span data-stu-id="555ac-107">This means that if you define one of them, you must also define the other one.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="555ac-108">O `IsFalse` operador pode ser *sobrecarregado*, o que significa que uma classe ou estrutura pode redefinir seu comportamento quando seu operando tem o tipo de classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="555ac-108">The `IsFalse` operator can be *overloaded*, which means that a class or structure can redefine its behavior when its operand has the type of that class or structure.</span></span> <span data-ttu-id="555ac-109">Se seu código usa esse operador em uma classe ou estrutura, certifique-se de que compreender o comportamento redefinido.</span><span class="sxs-lookup"><span data-stu-id="555ac-109">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="555ac-110">Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="555ac-110">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="555ac-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="555ac-111">Example</span></span>  
 <span data-ttu-id="555ac-112">O exemplo de código a seguir define o contorno de uma estrutura que inclui as definições para o `IsFalse` e `IsTrue` operadores.</span><span class="sxs-lookup"><span data-stu-id="555ac-112">The following code example defines the outline of a structure that includes definitions for the `IsFalse` and `IsTrue` operators.</span></span>  
  
 [!code-vb[VbVbalrOperators#28](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/isfalse-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="555ac-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="555ac-113">See Also</span></span>  
 [<span data-ttu-id="555ac-114">Operador IsTrue</span><span class="sxs-lookup"><span data-stu-id="555ac-114">IsTrue Operator</span></span>](../../../visual-basic/language-reference/operators/istrue-operator.md)  
 [<span data-ttu-id="555ac-115">Como definir um operador</span><span class="sxs-lookup"><span data-stu-id="555ac-115">How to: Define an Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)  
 [<span data-ttu-id="555ac-116">Operador AndAlso</span><span class="sxs-lookup"><span data-stu-id="555ac-116">AndAlso Operator</span></span>](../../../visual-basic/language-reference/operators/andalso-operator.md)
