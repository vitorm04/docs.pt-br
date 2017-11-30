---
title: Como retornar um valor de um procedimento (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], returning from
- procedures [Visual Basic], returning a value
ms.assetid: 4bcc4724-2b4e-4df8-9b4b-16054607f87d
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6ce7aa0942be413986cb010963753447ea18cdf2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-return-a-value-from-a-procedure-visual-basic"></a><span data-ttu-id="fd891-102">Como retornar um valor de um procedimento (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fd891-102">How to: Return a Value from a Procedure (Visual Basic)</span></span>
<span data-ttu-id="fd891-103">Um `Function` procedimento retorna um valor para o código de chamada seja executando um `Return` instrução ou encontrando um `Exit Function` ou `End Function` instrução.</span><span class="sxs-lookup"><span data-stu-id="fd891-103">A `Function` procedure returns a value to the calling code either by executing a `Return` statement or by encountering an `Exit Function` or `End Function` statement.</span></span>  
  
### <a name="to-return-a-value-using-the-return-statement"></a><span data-ttu-id="fd891-104">Para retornar um valor usando a instrução Return</span><span class="sxs-lookup"><span data-stu-id="fd891-104">To return a value using the Return statement</span></span>  
  
1.  <span data-ttu-id="fd891-105">Colocar um `Return` instrução no ponto em que as tarefas do procedimento é concluída.</span><span class="sxs-lookup"><span data-stu-id="fd891-105">Put a `Return` statement at the point where the procedure's task is completed.</span></span>  
  
2.  <span data-ttu-id="fd891-106">Siga o `Return` palavra-chave com uma expressão que produz o valor que você deseja retornar ao código de chamada.</span><span class="sxs-lookup"><span data-stu-id="fd891-106">Follow the `Return` keyword with an expression that yields the value you want to return to the calling code.</span></span>  
  
3.  <span data-ttu-id="fd891-107">Você pode ter mais de um demonstrativo `Return` no mesmo procedimento.</span><span class="sxs-lookup"><span data-stu-id="fd891-107">You can have more than one `Return` statement in the same procedure.</span></span>  
  
     <span data-ttu-id="fd891-108">O seguinte `Function` procedimento calcula o maior lado, ou hipotenusa, de um triângulo e o retorna ao código de chamada.</span><span class="sxs-lookup"><span data-stu-id="fd891-108">The following `Function` procedure calculates the longest side, or hypotenuse, of a right triangle, and returns it to the calling code.</span></span>  
  
     [!code-vb[VbVbcnProcedures#1](./codesnippet/VisualBasic/how-to-return-a-value-from-a-procedure_1.vb)]  
  
     <span data-ttu-id="fd891-109">O exemplo a seguir mostra uma chamada típica para `hypotenuse`, que armazena o valor retornado.</span><span class="sxs-lookup"><span data-stu-id="fd891-109">The following example shows a typical call to `hypotenuse`, which stores the returned value.</span></span>  
  
     [!code-vb[VbVbcnProcedures#6](./codesnippet/VisualBasic/how-to-return-a-value-from-a-procedure_2.vb)]  
  
### <a name="to-return-a-value-using-exit-function-or-end-function"></a><span data-ttu-id="fd891-110">Para retornar um valor usando Exit Function ou End Function</span><span class="sxs-lookup"><span data-stu-id="fd891-110">To return a value using Exit Function or End Function</span></span>  
  
1.  <span data-ttu-id="fd891-111">Em pelo menos um lugar a `Function` procedimento, atribua um valor para o nome do procedimento.</span><span class="sxs-lookup"><span data-stu-id="fd891-111">In at least one place in the `Function` procedure, assign a value to the procedure's name.</span></span>  
  
2.  <span data-ttu-id="fd891-112">Quando você executa um `Exit Function` ou `End Function` instrução, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] retorna o valor mais recentemente atribuído ao nome do procedimento.</span><span class="sxs-lookup"><span data-stu-id="fd891-112">When you execute an `Exit Function` or `End Function` statement, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] returns the value most recently assigned to the procedure's name.</span></span>  
  
3.  <span data-ttu-id="fd891-113">Você pode ter mais de um demonstrativo `Exit Function` no mesmo procedimento e mesclar os demonstrativos `Return` e `Exit Function` no mesmo procedimento.</span><span class="sxs-lookup"><span data-stu-id="fd891-113">You can have more than one `Exit Function` statement in the same procedure, and you can mix `Return` and `Exit Function` statements in the same procedure.</span></span>  
  
4.  <span data-ttu-id="fd891-114">Você pode ter apenas um `End Function` instrução em uma `Function` procedimento.</span><span class="sxs-lookup"><span data-stu-id="fd891-114">You can have only one `End Function` statement in a `Function` procedure.</span></span>  
  
     <span data-ttu-id="fd891-115">Para obter mais informações e um exemplo, consulte "Valor de retorno" em [instrução Function](../../../../visual-basic/language-reference/statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="fd891-115">For more information and an example, see "Return Value" in [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd891-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fd891-116">See Also</span></span>  
 [<span data-ttu-id="fd891-117">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="fd891-117">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="fd891-118">Subprocedimentos</span><span class="sxs-lookup"><span data-stu-id="fd891-118">Sub Procedures</span></span>](./sub-procedures.md)  
 [<span data-ttu-id="fd891-119">Procedimentos de Propriedade</span><span class="sxs-lookup"><span data-stu-id="fd891-119">Property Procedures</span></span>](./property-procedures.md)  
 [<span data-ttu-id="fd891-120">Procedimentos de Operador</span><span class="sxs-lookup"><span data-stu-id="fd891-120">Operator Procedures</span></span>](./operator-procedures.md)  
 [<span data-ttu-id="fd891-121">Parâmetros e Argumentos de Procedimento</span><span class="sxs-lookup"><span data-stu-id="fd891-121">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="fd891-122">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="fd891-122">Function Statement</span></span>](../../../../visual-basic/language-reference/statements/function-statement.md)  
 [<span data-ttu-id="fd891-123">Instrução Return</span><span class="sxs-lookup"><span data-stu-id="fd891-123">Return Statement</span></span>](../../../../visual-basic/language-reference/statements/return-statement.md)  
 [<span data-ttu-id="fd891-124">Como criar um procedimento que retorne um valor</span><span class="sxs-lookup"><span data-stu-id="fd891-124">How to: Create a Procedure that Returns a Value</span></span>](./how-to-create-a-procedure-that-returns-a-value.md)  
 [<span data-ttu-id="fd891-125">Como chamar um procedimento que retorna um valor</span><span class="sxs-lookup"><span data-stu-id="fd891-125">How to: Call a Procedure That Returns a Value</span></span>](./how-to-call-a-procedure-that-returns-a-value.md)
