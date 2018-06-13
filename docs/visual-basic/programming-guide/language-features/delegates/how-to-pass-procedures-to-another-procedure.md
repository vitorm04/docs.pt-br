---
title: Como passar procedimentos para outro procedimento no Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- AddressOf operator [Visual Basic]
- delegates [Visual Basic], passing procedures
ms.assetid: 5adbba15-5a1d-413f-ab3e-3ff6cc0a4669
ms.openlocfilehash: c28ac7a640ec863b37bd7407d0273a1918964ac4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33647179"
---
# <a name="how-to-pass-procedures-to-another-procedure-in-visual-basic"></a><span data-ttu-id="1243d-102">Como passar procedimentos para outro procedimento no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1243d-102">How to: Pass Procedures to Another Procedure in Visual Basic</span></span>
<span data-ttu-id="1243d-103">Este exemplo mostra como usar delegados para passar um procedimento para outro procedimento.</span><span class="sxs-lookup"><span data-stu-id="1243d-103">This example shows how to use delegates to pass a procedure to another procedure.</span></span>  
  
 <span data-ttu-id="1243d-104">Um delegado é um tipo que você pode usar como qualquer outro tipo no Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="1243d-104">A delegate is a type that you can use like any other type in Visual Basic.</span></span> <span data-ttu-id="1243d-105">O `AddressOf` operador retorna um objeto delegado quando aplicado a um nome de procedimento.</span><span class="sxs-lookup"><span data-stu-id="1243d-105">The `AddressOf` operator returns a delegate object when applied to a procedure name.</span></span>  
  
 <span data-ttu-id="1243d-106">Este exemplo tem um procedimento com um parâmetro delegado que pode levar a uma referência a outro procedimento, obtida com o `AddressOf` operador.</span><span class="sxs-lookup"><span data-stu-id="1243d-106">This example has a procedure with a delegate parameter that can take a reference to another procedure, obtained with the `AddressOf` operator.</span></span>  
  
### <a name="create-the-delegate-and-matching-procedures"></a><span data-ttu-id="1243d-107">Crie o delegado e procedimentos correspondentes.</span><span class="sxs-lookup"><span data-stu-id="1243d-107">Create the delegate and matching procedures</span></span>  
  
1.  <span data-ttu-id="1243d-108">Cria um delegado de nome `MathOperator`.</span><span class="sxs-lookup"><span data-stu-id="1243d-108">Create a delegate named `MathOperator`.</span></span>  
  
     [!code-vb[VbVbalrDelegates#1](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_1.vb)]  
  
2.  <span data-ttu-id="1243d-109">Criar um procedimento denominado `AddNumbers` com parâmetros e valor de retorno que correspondem do `MathOperator`, de modo que as assinaturas forem correspondentes.</span><span class="sxs-lookup"><span data-stu-id="1243d-109">Create a procedure named `AddNumbers` with parameters and return value that match those of `MathOperator`, so that the signatures match.</span></span>  
  
     [!code-vb[VbVbalrDelegates#2](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_2.vb)]  
  
3.  <span data-ttu-id="1243d-110">Criar um procedimento denominado `SubtractNumbers` com uma assinatura que corresponde a `MathOperator`.</span><span class="sxs-lookup"><span data-stu-id="1243d-110">Create a procedure named `SubtractNumbers` with a signature that matches `MathOperator`.</span></span>  
  
     [!code-vb[VbVbalrDelegates#3](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_3.vb)]  
  
4.  <span data-ttu-id="1243d-111">Criar um procedimento denominado `DelegateTest` que usa um delegado como um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="1243d-111">Create a procedure named `DelegateTest` that takes a delegate as a parameter.</span></span>  
  
     <span data-ttu-id="1243d-112">Esse procedimento pode aceitar uma referência a `AddNumbers` ou `SubtractNumbers`, porque suas assinaturas correspondem a `MathOperator` assinatura.</span><span class="sxs-lookup"><span data-stu-id="1243d-112">This procedure can accept a reference to `AddNumbers` or `SubtractNumbers`, because their signatures match the `MathOperator` signature.</span></span>  
  
     [!code-vb[VbVbalrDelegates#4](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_4.vb)]  
  
5.  <span data-ttu-id="1243d-113">Criar um procedimento denominado `Test` que chama `DelegateTest` uma vez com o representante para `AddNumbers` como um parâmetro e, novamente com o delegado para `SubtractNumbers` como um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="1243d-113">Create a procedure named `Test` that calls `DelegateTest` once with the delegate for `AddNumbers` as a parameter, and again with the delegate for `SubtractNumbers` as a parameter.</span></span>  
  
     [!code-vb[VbVbalrDelegates#5](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_5.vb)]  
  
     <span data-ttu-id="1243d-114">Quando `Test` é chamado, ele primeiro mostra o resultado de `AddNumbers` atuando em `5` e `3`, que é 8.</span><span class="sxs-lookup"><span data-stu-id="1243d-114">When `Test` is called, it first displays the result of `AddNumbers` acting on `5` and `3`, which is 8.</span></span> <span data-ttu-id="1243d-115">Em seguida, o resultado de `SubtractNumbers` atuando em `9` e `3` for exibido, que é 6.</span><span class="sxs-lookup"><span data-stu-id="1243d-115">Then the result of `SubtractNumbers` acting on `9` and `3` is displayed, which is 6.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1243d-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1243d-116">See Also</span></span>  
 [<span data-ttu-id="1243d-117">Delegados</span><span class="sxs-lookup"><span data-stu-id="1243d-117">Delegates</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 [<span data-ttu-id="1243d-118">Operador AddressOf</span><span class="sxs-lookup"><span data-stu-id="1243d-118">AddressOf Operator</span></span>](../../../../visual-basic/language-reference/operators/addressof-operator.md)  
 [<span data-ttu-id="1243d-119">Instrução Delegate</span><span class="sxs-lookup"><span data-stu-id="1243d-119">Delegate Statement</span></span>](../../../../visual-basic/language-reference/statements/delegate-statement.md)  
 [<span data-ttu-id="1243d-120">Como invocar um método delegado</span><span class="sxs-lookup"><span data-stu-id="1243d-120">How to: Invoke a Delegate Method</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)
