---
title: Como retornar um valor de um procedimento
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], returning from
- procedures [Visual Basic], returning a value
ms.assetid: 4bcc4724-2b4e-4df8-9b4b-16054607f87d
ms.openlocfilehash: 1371e4ed0ff28f9caf56eabf2a1bb9290edbe75c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346021"
---
# <a name="how-to-return-a-value-from-a-procedure-visual-basic"></a><span data-ttu-id="8d023-102">Como retornar um valor de um procedimento (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8d023-102">How to: Return a Value from a Procedure (Visual Basic)</span></span>
<span data-ttu-id="8d023-103">A `Function` procedure returns a value to the calling code either by executing a `Return` statement or by encountering an `Exit Function` or `End Function` statement.</span><span class="sxs-lookup"><span data-stu-id="8d023-103">A `Function` procedure returns a value to the calling code either by executing a `Return` statement or by encountering an `Exit Function` or `End Function` statement.</span></span>  
  
### <a name="to-return-a-value-using-the-return-statement"></a><span data-ttu-id="8d023-104">To return a value using the Return statement</span><span class="sxs-lookup"><span data-stu-id="8d023-104">To return a value using the Return statement</span></span>  
  
1. <span data-ttu-id="8d023-105">Put a `Return` statement at the point where the procedure's task is completed.</span><span class="sxs-lookup"><span data-stu-id="8d023-105">Put a `Return` statement at the point where the procedure's task is completed.</span></span>  
  
2. <span data-ttu-id="8d023-106">Follow the `Return` keyword with an expression that yields the value you want to return to the calling code.</span><span class="sxs-lookup"><span data-stu-id="8d023-106">Follow the `Return` keyword with an expression that yields the value you want to return to the calling code.</span></span>  
  
3. <span data-ttu-id="8d023-107">Você pode ter mais de um demonstrativo `Return` no mesmo procedimento.</span><span class="sxs-lookup"><span data-stu-id="8d023-107">You can have more than one `Return` statement in the same procedure.</span></span>  
  
     <span data-ttu-id="8d023-108">The following `Function` procedure calculates the longest side, or hypotenuse, of a right triangle, and returns it to the calling code.</span><span class="sxs-lookup"><span data-stu-id="8d023-108">The following `Function` procedure calculates the longest side, or hypotenuse, of a right triangle, and returns it to the calling code.</span></span>  
  
     [!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]  
  
     <span data-ttu-id="8d023-109">The following example shows a typical call to `hypotenuse`, which stores the returned value.</span><span class="sxs-lookup"><span data-stu-id="8d023-109">The following example shows a typical call to `hypotenuse`, which stores the returned value.</span></span>  
  
     [!code-vb[VbVbcnProcedures#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#6)]  
  
### <a name="to-return-a-value-using-exit-function-or-end-function"></a><span data-ttu-id="8d023-110">To return a value using Exit Function or End Function</span><span class="sxs-lookup"><span data-stu-id="8d023-110">To return a value using Exit Function or End Function</span></span>  
  
1. <span data-ttu-id="8d023-111">In at least one place in the `Function` procedure, assign a value to the procedure's name.</span><span class="sxs-lookup"><span data-stu-id="8d023-111">In at least one place in the `Function` procedure, assign a value to the procedure's name.</span></span>  
  
2. <span data-ttu-id="8d023-112">When you execute an `Exit Function` or `End Function` statement, Visual Basic returns the value most recently assigned to the procedure's name.</span><span class="sxs-lookup"><span data-stu-id="8d023-112">When you execute an `Exit Function` or `End Function` statement, Visual Basic returns the value most recently assigned to the procedure's name.</span></span>  
  
3. <span data-ttu-id="8d023-113">Você pode ter mais de um demonstrativo `Exit Function` no mesmo procedimento e mesclar os demonstrativos `Return` e `Exit Function` no mesmo procedimento.</span><span class="sxs-lookup"><span data-stu-id="8d023-113">You can have more than one `Exit Function` statement in the same procedure, and you can mix `Return` and `Exit Function` statements in the same procedure.</span></span>  
  
4. <span data-ttu-id="8d023-114">You can have only one `End Function` statement in a `Function` procedure.</span><span class="sxs-lookup"><span data-stu-id="8d023-114">You can have only one `End Function` statement in a `Function` procedure.</span></span>  
  
     <span data-ttu-id="8d023-115">For more information and an example, see "Return Value" in [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="8d023-115">For more information and an example, see "Return Value" in [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d023-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8d023-116">See also</span></span>

- [<span data-ttu-id="8d023-117">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="8d023-117">Procedures</span></span>](./index.md)
- [<span data-ttu-id="8d023-118">Subprocedimentos</span><span class="sxs-lookup"><span data-stu-id="8d023-118">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="8d023-119">Procedimentos de Propriedade</span><span class="sxs-lookup"><span data-stu-id="8d023-119">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="8d023-120">Procedimentos de Operador</span><span class="sxs-lookup"><span data-stu-id="8d023-120">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="8d023-121">Parâmetros e Argumentos de Procedimento</span><span class="sxs-lookup"><span data-stu-id="8d023-121">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="8d023-122">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="8d023-122">Function Statement</span></span>](../../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="8d023-123">Instrução Return</span><span class="sxs-lookup"><span data-stu-id="8d023-123">Return Statement</span></span>](../../../../visual-basic/language-reference/statements/return-statement.md)
- [<span data-ttu-id="8d023-124">Como criar um procedimento que retorne um valor</span><span class="sxs-lookup"><span data-stu-id="8d023-124">How to: Create a Procedure that Returns a Value</span></span>](./how-to-create-a-procedure-that-returns-a-value.md)
- [<span data-ttu-id="8d023-125">Como chamar um procedimento que retorna um valor</span><span class="sxs-lookup"><span data-stu-id="8d023-125">How to: Call a Procedure That Returns a Value</span></span>](./how-to-call-a-procedure-that-returns-a-value.md)
