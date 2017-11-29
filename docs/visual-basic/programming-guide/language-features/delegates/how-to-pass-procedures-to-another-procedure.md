---
title: Como passar procedimentos para outro procedimento no Visual Basic
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- AddressOf operator [Visual Basic]
- delegates [Visual Basic], passing procedures
ms.assetid: 5adbba15-5a1d-413f-ab3e-3ff6cc0a4669
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4e8e205f5238aab39aa92574bc5c680e68cc8a81
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-pass-procedures-to-another-procedure-in-visual-basic"></a><span data-ttu-id="237aa-102">Como passar procedimentos para outro procedimento no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="237aa-102">How to: Pass Procedures to Another Procedure in Visual Basic</span></span>
<span data-ttu-id="237aa-103">Este exemplo mostra como usar delegados para passar um procedimento para outro procedimento.</span><span class="sxs-lookup"><span data-stu-id="237aa-103">This example shows how to use delegates to pass a procedure to another procedure.</span></span>  
  
 <span data-ttu-id="237aa-104">Um delegado é um tipo que você pode usar como qualquer outro tipo em [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span><span class="sxs-lookup"><span data-stu-id="237aa-104">A delegate is a type that you can use like any other type in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span> <span data-ttu-id="237aa-105">O `AddressOf` operador retorna um objeto delegado quando aplicado a um nome de procedimento.</span><span class="sxs-lookup"><span data-stu-id="237aa-105">The `AddressOf` operator returns a delegate object when applied to a procedure name.</span></span>  
  
 <span data-ttu-id="237aa-106">Este exemplo tem um procedimento com um parâmetro delegado que pode levar a uma referência a outro procedimento, obtida com o `AddressOf` operador.</span><span class="sxs-lookup"><span data-stu-id="237aa-106">This example has a procedure with a delegate parameter that can take a reference to another procedure, obtained with the `AddressOf` operator.</span></span>  
  
### <a name="create-the-delegate-and-matching-procedures"></a><span data-ttu-id="237aa-107">Crie o delegado e procedimentos correspondentes.</span><span class="sxs-lookup"><span data-stu-id="237aa-107">Create the delegate and matching procedures</span></span>  
  
1.  <span data-ttu-id="237aa-108">Cria um delegado de nome `MathOperator`.</span><span class="sxs-lookup"><span data-stu-id="237aa-108">Create a delegate named `MathOperator`.</span></span>  
  
     [!code-vb[VbVbalrDelegates#1](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_1.vb)]  
  
2.  <span data-ttu-id="237aa-109">Criar um procedimento denominado `AddNumbers` com parâmetros e valor de retorno que correspondem do `MathOperator`, de modo que as assinaturas forem correspondentes.</span><span class="sxs-lookup"><span data-stu-id="237aa-109">Create a procedure named `AddNumbers` with parameters and return value that match those of `MathOperator`, so that the signatures match.</span></span>  
  
     [!code-vb[VbVbalrDelegates#2](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_2.vb)]  
  
3.  <span data-ttu-id="237aa-110">Criar um procedimento denominado `SubtractNumbers` com uma assinatura que corresponde a `MathOperator`.</span><span class="sxs-lookup"><span data-stu-id="237aa-110">Create a procedure named `SubtractNumbers` with a signature that matches `MathOperator`.</span></span>  
  
     [!code-vb[VbVbalrDelegates#3](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_3.vb)]  
  
4.  <span data-ttu-id="237aa-111">Criar um procedimento denominado `DelegateTest` que usa um delegado como um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="237aa-111">Create a procedure named `DelegateTest` that takes a delegate as a parameter.</span></span>  
  
     <span data-ttu-id="237aa-112">Esse procedimento pode aceitar uma referência a `AddNumbers` ou `SubtractNumbers`, porque suas assinaturas correspondem a `MathOperator` assinatura.</span><span class="sxs-lookup"><span data-stu-id="237aa-112">This procedure can accept a reference to `AddNumbers` or `SubtractNumbers`, because their signatures match the `MathOperator` signature.</span></span>  
  
     [!code-vb[VbVbalrDelegates#4](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_4.vb)]  
  
5.  <span data-ttu-id="237aa-113">Criar um procedimento denominado `Test` que chama `DelegateTest` uma vez com o representante para `AddNumbers` como um parâmetro e, novamente com o delegado para `SubtractNumbers` como um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="237aa-113">Create a procedure named `Test` that calls `DelegateTest` once with the delegate for `AddNumbers` as a parameter, and again with the delegate for `SubtractNumbers` as a parameter.</span></span>  
  
     [!code-vb[VbVbalrDelegates#5](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_5.vb)]  
  
     <span data-ttu-id="237aa-114">Quando `Test` é chamado, ele primeiro mostra o resultado de `AddNumbers` atuando em `5` e `3`, que é 8.</span><span class="sxs-lookup"><span data-stu-id="237aa-114">When `Test` is called, it first displays the result of `AddNumbers` acting on `5` and `3`, which is 8.</span></span> <span data-ttu-id="237aa-115">Em seguida, o resultado de `SubtractNumbers` atuando em `9` e `3` for exibido, que é 6.</span><span class="sxs-lookup"><span data-stu-id="237aa-115">Then the result of `SubtractNumbers` acting on `9` and `3` is displayed, which is 6.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="237aa-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="237aa-116">See Also</span></span>  
 [<span data-ttu-id="237aa-117">Delegados</span><span class="sxs-lookup"><span data-stu-id="237aa-117">Delegates</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 [<span data-ttu-id="237aa-118">Operador AddressOf</span><span class="sxs-lookup"><span data-stu-id="237aa-118">AddressOf Operator</span></span>](../../../../visual-basic/language-reference/operators/addressof-operator.md)  
 [<span data-ttu-id="237aa-119">Instrução Delegate</span><span class="sxs-lookup"><span data-stu-id="237aa-119">Delegate Statement</span></span>](../../../../visual-basic/language-reference/statements/delegate-statement.md)  
 [<span data-ttu-id="237aa-120">Como invocar um método delegado</span><span class="sxs-lookup"><span data-stu-id="237aa-120">How to: Invoke a Delegate Method</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)
