---
title: 'Como: Passar procedimentos para outro procedimento no Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- AddressOf operator [Visual Basic]
- delegates [Visual Basic], passing procedures
ms.assetid: 5adbba15-5a1d-413f-ab3e-3ff6cc0a4669
ms.openlocfilehash: cf5a8447cbedcd8071da98ac6763ff06eb608199
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54506752"
---
# <a name="how-to-pass-procedures-to-another-procedure-in-visual-basic"></a><span data-ttu-id="51eeb-102">Como: Passar procedimentos para outro procedimento no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="51eeb-102">How to: Pass Procedures to Another Procedure in Visual Basic</span></span>
<span data-ttu-id="51eeb-103">Este exemplo mostra como usar delegados para passar um procedimento para outro procedimento.</span><span class="sxs-lookup"><span data-stu-id="51eeb-103">This example shows how to use delegates to pass a procedure to another procedure.</span></span>  
  
 <span data-ttu-id="51eeb-104">Um delegado é um tipo que você pode usar como qualquer outro tipo no Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="51eeb-104">A delegate is a type that you can use like any other type in Visual Basic.</span></span> <span data-ttu-id="51eeb-105">O `AddressOf` operador retorna um objeto delegado quando aplicado a um nome de procedimento.</span><span class="sxs-lookup"><span data-stu-id="51eeb-105">The `AddressOf` operator returns a delegate object when applied to a procedure name.</span></span>  
  
 <span data-ttu-id="51eeb-106">Este exemplo tem um procedimento com um parâmetro delegado que pode levar a uma referência a outro procedimento, obtida com o `AddressOf` operador.</span><span class="sxs-lookup"><span data-stu-id="51eeb-106">This example has a procedure with a delegate parameter that can take a reference to another procedure, obtained with the `AddressOf` operator.</span></span>  
  
### <a name="create-the-delegate-and-matching-procedures"></a><span data-ttu-id="51eeb-107">Criar o delegado e procedimentos correspondentes.</span><span class="sxs-lookup"><span data-stu-id="51eeb-107">Create the delegate and matching procedures</span></span>  
  
1.  <span data-ttu-id="51eeb-108">Criar um delegado chamado `MathOperator`.</span><span class="sxs-lookup"><span data-stu-id="51eeb-108">Create a delegate named `MathOperator`.</span></span>  
  
     [!code-vb[VbVbalrDelegates#1](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_1.vb)]  
  
2.  <span data-ttu-id="51eeb-109">Criar um procedimento denominado `AddNumbers` com parâmetros e valor de retorno que correspondam do `MathOperator`, de modo que as assinaturas forem correspondentes.</span><span class="sxs-lookup"><span data-stu-id="51eeb-109">Create a procedure named `AddNumbers` with parameters and return value that match those of `MathOperator`, so that the signatures match.</span></span>  
  
     [!code-vb[VbVbalrDelegates#2](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_2.vb)]  
  
3.  <span data-ttu-id="51eeb-110">Criar um procedimento denominado `SubtractNumbers` com uma assinatura que corresponde ao `MathOperator`.</span><span class="sxs-lookup"><span data-stu-id="51eeb-110">Create a procedure named `SubtractNumbers` with a signature that matches `MathOperator`.</span></span>  
  
     [!code-vb[VbVbalrDelegates#3](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_3.vb)]  
  
4.  <span data-ttu-id="51eeb-111">Crie um procedimento chamado `DelegateTest` que aceita um delegado como um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="51eeb-111">Create a procedure named `DelegateTest` that takes a delegate as a parameter.</span></span>  
  
     <span data-ttu-id="51eeb-112">Esse procedimento pode aceitar uma referência a `AddNumbers` ou `SubtractNumbers`, porque suas assinaturas correspondem a `MathOperator` assinatura.</span><span class="sxs-lookup"><span data-stu-id="51eeb-112">This procedure can accept a reference to `AddNumbers` or `SubtractNumbers`, because their signatures match the `MathOperator` signature.</span></span>  
  
     [!code-vb[VbVbalrDelegates#4](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_4.vb)]  
  
5.  <span data-ttu-id="51eeb-113">Criar um procedimento denominado `Test` que chama `DelegateTest` uma vez com o representante `AddNumbers` como um parâmetro e, novamente com o delegado para `SubtractNumbers` como um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="51eeb-113">Create a procedure named `Test` that calls `DelegateTest` once with the delegate for `AddNumbers` as a parameter, and again with the delegate for `SubtractNumbers` as a parameter.</span></span>  
  
     [!code-vb[VbVbalrDelegates#5](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_5.vb)]  
  
     <span data-ttu-id="51eeb-114">Quando `Test` é chamado, ele primeiro mostra o resultado da `AddNumbers` atuando em `5` e `3`, que é 8.</span><span class="sxs-lookup"><span data-stu-id="51eeb-114">When `Test` is called, it first displays the result of `AddNumbers` acting on `5` and `3`, which is 8.</span></span> <span data-ttu-id="51eeb-115">Em seguida, o resultado de `SubtractNumbers` atuando em `9` e `3` for exibida, que é 6.</span><span class="sxs-lookup"><span data-stu-id="51eeb-115">Then the result of `SubtractNumbers` acting on `9` and `3` is displayed, which is 6.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51eeb-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="51eeb-116">See also</span></span>
- [<span data-ttu-id="51eeb-117">Delegados</span><span class="sxs-lookup"><span data-stu-id="51eeb-117">Delegates</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [<span data-ttu-id="51eeb-118">Operador AddressOf</span><span class="sxs-lookup"><span data-stu-id="51eeb-118">AddressOf Operator</span></span>](../../../../visual-basic/language-reference/operators/addressof-operator.md)
- [<span data-ttu-id="51eeb-119">Instrução Delegate</span><span class="sxs-lookup"><span data-stu-id="51eeb-119">Delegate Statement</span></span>](../../../../visual-basic/language-reference/statements/delegate-statement.md)
- [<span data-ttu-id="51eeb-120">Como: Invocar um método delegado</span><span class="sxs-lookup"><span data-stu-id="51eeb-120">How to: Invoke a Delegate Method</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)
