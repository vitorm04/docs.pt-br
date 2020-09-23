---
title: Como passar procedimentos para outro procedimento
ms.date: 07/20/2015
helpviewer_keywords:
- AddressOf operator [Visual Basic]
- delegates [Visual Basic], passing procedures
ms.assetid: 5adbba15-5a1d-413f-ab3e-3ff6cc0a4669
ms.openlocfilehash: 3a7a653bbf238b50e3c7339da76df0f68ab9b59f
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91085783"
---
# <a name="how-to-pass-procedures-to-another-procedure-in-visual-basic"></a><span data-ttu-id="2dde1-102">Como passar procedimentos para outro procedimento no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2dde1-102">How to: Pass Procedures to Another Procedure in Visual Basic</span></span>

<span data-ttu-id="2dde1-103">Este exemplo mostra como usar delegados para passar um procedimento para outro procedimento.</span><span class="sxs-lookup"><span data-stu-id="2dde1-103">This example shows how to use delegates to pass a procedure to another procedure.</span></span>  
  
 <span data-ttu-id="2dde1-104">Um delegado é um tipo que você pode usar como qualquer outro tipo em Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="2dde1-104">A delegate is a type that you can use like any other type in Visual Basic.</span></span> <span data-ttu-id="2dde1-105">O `AddressOf` operador retorna um objeto delegado quando aplicado a um nome de procedimento.</span><span class="sxs-lookup"><span data-stu-id="2dde1-105">The `AddressOf` operator returns a delegate object when applied to a procedure name.</span></span>  
  
 <span data-ttu-id="2dde1-106">Este exemplo tem um procedimento com um parâmetro delegado que pode usar uma referência a outro procedimento, obtido com o `AddressOf` operador.</span><span class="sxs-lookup"><span data-stu-id="2dde1-106">This example has a procedure with a delegate parameter that can take a reference to another procedure, obtained with the `AddressOf` operator.</span></span>  
  
### <a name="create-the-delegate-and-matching-procedures"></a><span data-ttu-id="2dde1-107">Criar o delegado e os procedimentos correspondentes</span><span class="sxs-lookup"><span data-stu-id="2dde1-107">Create the delegate and matching procedures</span></span>  
  
1. <span data-ttu-id="2dde1-108">Crie um delegado chamado `MathOperator` .</span><span class="sxs-lookup"><span data-stu-id="2dde1-108">Create a delegate named `MathOperator`.</span></span>  
  
     [!code-vb[VbVbalrDelegates#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#1)]  
  
2. <span data-ttu-id="2dde1-109">Crie um procedimento chamado `AddNumbers` com parâmetros e valor de retorno que correspondam aos de `MathOperator` , para que as assinaturas correspondam.</span><span class="sxs-lookup"><span data-stu-id="2dde1-109">Create a procedure named `AddNumbers` with parameters and return value that match those of `MathOperator`, so that the signatures match.</span></span>  
  
     [!code-vb[VbVbalrDelegates#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#2)]  
  
3. <span data-ttu-id="2dde1-110">Crie um procedimento chamado `SubtractNumbers` com uma assinatura que corresponda a `MathOperator` .</span><span class="sxs-lookup"><span data-stu-id="2dde1-110">Create a procedure named `SubtractNumbers` with a signature that matches `MathOperator`.</span></span>  
  
     [!code-vb[VbVbalrDelegates#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#3)]  
  
4. <span data-ttu-id="2dde1-111">Crie um procedimento chamado `DelegateTest` que usa um delegado como parâmetro.</span><span class="sxs-lookup"><span data-stu-id="2dde1-111">Create a procedure named `DelegateTest` that takes a delegate as a parameter.</span></span>  
  
     <span data-ttu-id="2dde1-112">Esse procedimento pode aceitar uma referência a `AddNumbers` ou `SubtractNumbers` , porque suas assinaturas correspondem à `MathOperator` assinatura.</span><span class="sxs-lookup"><span data-stu-id="2dde1-112">This procedure can accept a reference to `AddNumbers` or `SubtractNumbers`, because their signatures match the `MathOperator` signature.</span></span>  
  
     [!code-vb[VbVbalrDelegates#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#4)]  
  
5. <span data-ttu-id="2dde1-113">Crie um procedimento chamado `Test` que chame `DelegateTest` uma vez com o delegado para `AddNumbers` como um parâmetro e novamente com o delegado para `SubtractNumbers` como um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="2dde1-113">Create a procedure named `Test` that calls `DelegateTest` once with the delegate for `AddNumbers` as a parameter, and again with the delegate for `SubtractNumbers` as a parameter.</span></span>  
  
     [!code-vb[VbVbalrDelegates#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#5)]  
  
     <span data-ttu-id="2dde1-114">Quando `Test` é chamado, ele primeiro exibe o resultado de `AddNumbers` atuar em `5` e `3` , que é 8.</span><span class="sxs-lookup"><span data-stu-id="2dde1-114">When `Test` is called, it first displays the result of `AddNumbers` acting on `5` and `3`, which is 8.</span></span> <span data-ttu-id="2dde1-115">Em seguida, o resultado de `SubtractNumbers` atuar em `9` e `3` é exibido, que é 6.</span><span class="sxs-lookup"><span data-stu-id="2dde1-115">Then the result of `SubtractNumbers` acting on `9` and `3` is displayed, which is 6.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2dde1-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="2dde1-116">See also</span></span>

- [<span data-ttu-id="2dde1-117">Representantes</span><span class="sxs-lookup"><span data-stu-id="2dde1-117">Delegates</span></span>](index.md)
- [<span data-ttu-id="2dde1-118">Operador AddressOf</span><span class="sxs-lookup"><span data-stu-id="2dde1-118">AddressOf Operator</span></span>](../../../language-reference/operators/addressof-operator.md)
- [<span data-ttu-id="2dde1-119">Instrução Delegate</span><span class="sxs-lookup"><span data-stu-id="2dde1-119">Delegate Statement</span></span>](../../../language-reference/statements/delegate-statement.md)
- [<span data-ttu-id="2dde1-120">Como invocar um método delegado</span><span class="sxs-lookup"><span data-stu-id="2dde1-120">How to: Invoke a Delegate Method</span></span>](how-to-invoke-a-delegate-method.md)
