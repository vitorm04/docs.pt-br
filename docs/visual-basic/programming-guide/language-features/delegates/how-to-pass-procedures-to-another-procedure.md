---
title: 'Como: Passar procedimentos para outro procedimento no Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- AddressOf operator [Visual Basic]
- delegates [Visual Basic], passing procedures
ms.assetid: 5adbba15-5a1d-413f-ab3e-3ff6cc0a4669
ms.openlocfilehash: 312c0e0f100e85256ad4ca856ccf7f35dbaa36dc
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59305241"
---
# <a name="how-to-pass-procedures-to-another-procedure-in-visual-basic"></a><span data-ttu-id="fa019-102">Como: Passar procedimentos para outro procedimento no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fa019-102">How to: Pass Procedures to Another Procedure in Visual Basic</span></span>
<span data-ttu-id="fa019-103">Este exemplo mostra como usar delegados para passar um procedimento para outro procedimento.</span><span class="sxs-lookup"><span data-stu-id="fa019-103">This example shows how to use delegates to pass a procedure to another procedure.</span></span>  
  
 <span data-ttu-id="fa019-104">Um delegado é um tipo que você pode usar como qualquer outro tipo no Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="fa019-104">A delegate is a type that you can use like any other type in Visual Basic.</span></span> <span data-ttu-id="fa019-105">O `AddressOf` operador retorna um objeto delegado quando aplicado a um nome de procedimento.</span><span class="sxs-lookup"><span data-stu-id="fa019-105">The `AddressOf` operator returns a delegate object when applied to a procedure name.</span></span>  
  
 <span data-ttu-id="fa019-106">Este exemplo tem um procedimento com um parâmetro delegado que pode levar a uma referência a outro procedimento, obtida com o `AddressOf` operador.</span><span class="sxs-lookup"><span data-stu-id="fa019-106">This example has a procedure with a delegate parameter that can take a reference to another procedure, obtained with the `AddressOf` operator.</span></span>  
  
### <a name="create-the-delegate-and-matching-procedures"></a><span data-ttu-id="fa019-107">Criar o delegado e procedimentos correspondentes.</span><span class="sxs-lookup"><span data-stu-id="fa019-107">Create the delegate and matching procedures</span></span>  
  
1. <span data-ttu-id="fa019-108">Criar um delegado chamado `MathOperator`.</span><span class="sxs-lookup"><span data-stu-id="fa019-108">Create a delegate named `MathOperator`.</span></span>  
  
     [!code-vb[VbVbalrDelegates#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#1)]  
  
2. <span data-ttu-id="fa019-109">Criar um procedimento denominado `AddNumbers` com parâmetros e valor de retorno que correspondam do `MathOperator`, de modo que as assinaturas forem correspondentes.</span><span class="sxs-lookup"><span data-stu-id="fa019-109">Create a procedure named `AddNumbers` with parameters and return value that match those of `MathOperator`, so that the signatures match.</span></span>  
  
     [!code-vb[VbVbalrDelegates#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#2)]  
  
3. <span data-ttu-id="fa019-110">Criar um procedimento denominado `SubtractNumbers` com uma assinatura que corresponde ao `MathOperator`.</span><span class="sxs-lookup"><span data-stu-id="fa019-110">Create a procedure named `SubtractNumbers` with a signature that matches `MathOperator`.</span></span>  
  
     [!code-vb[VbVbalrDelegates#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#3)]  
  
4. <span data-ttu-id="fa019-111">Crie um procedimento chamado `DelegateTest` que aceita um delegado como um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="fa019-111">Create a procedure named `DelegateTest` that takes a delegate as a parameter.</span></span>  
  
     <span data-ttu-id="fa019-112">Esse procedimento pode aceitar uma referência a `AddNumbers` ou `SubtractNumbers`, porque suas assinaturas correspondem a `MathOperator` assinatura.</span><span class="sxs-lookup"><span data-stu-id="fa019-112">This procedure can accept a reference to `AddNumbers` or `SubtractNumbers`, because their signatures match the `MathOperator` signature.</span></span>  
  
     [!code-vb[VbVbalrDelegates#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#4)]  
  
5. <span data-ttu-id="fa019-113">Criar um procedimento denominado `Test` que chama `DelegateTest` uma vez com o representante `AddNumbers` como um parâmetro e, novamente com o delegado para `SubtractNumbers` como um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="fa019-113">Create a procedure named `Test` that calls `DelegateTest` once with the delegate for `AddNumbers` as a parameter, and again with the delegate for `SubtractNumbers` as a parameter.</span></span>  
  
     [!code-vb[VbVbalrDelegates#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#5)]  
  
     <span data-ttu-id="fa019-114">Quando `Test` é chamado, ele primeiro mostra o resultado da `AddNumbers` atuando em `5` e `3`, que é 8.</span><span class="sxs-lookup"><span data-stu-id="fa019-114">When `Test` is called, it first displays the result of `AddNumbers` acting on `5` and `3`, which is 8.</span></span> <span data-ttu-id="fa019-115">Em seguida, o resultado de `SubtractNumbers` atuando em `9` e `3` for exibida, que é 6.</span><span class="sxs-lookup"><span data-stu-id="fa019-115">Then the result of `SubtractNumbers` acting on `9` and `3` is displayed, which is 6.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa019-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fa019-116">See also</span></span>

- [<span data-ttu-id="fa019-117">Delegados</span><span class="sxs-lookup"><span data-stu-id="fa019-117">Delegates</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [<span data-ttu-id="fa019-118">Operador AddressOf</span><span class="sxs-lookup"><span data-stu-id="fa019-118">AddressOf Operator</span></span>](../../../../visual-basic/language-reference/operators/addressof-operator.md)
- [<span data-ttu-id="fa019-119">Instrução Delegate</span><span class="sxs-lookup"><span data-stu-id="fa019-119">Delegate Statement</span></span>](../../../../visual-basic/language-reference/statements/delegate-statement.md)
- [<span data-ttu-id="fa019-120">Como: invocar um método delegado</span><span class="sxs-lookup"><span data-stu-id="fa019-120">How to: Invoke a Delegate Method</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)
