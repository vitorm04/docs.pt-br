---
title: Como criar um procedimento que retorne um valor (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedures [Visual Basic], returning a value
ms.assetid: 8ee19f95-a9ef-4033-963b-d224dca207c4
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 787eddc1fd1cdb9dd6b655a8556b75044b2a49dc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-procedure-that-returns-a-value-visual-basic"></a><span data-ttu-id="da952-102">Como criar um procedimento que retorne um valor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="da952-102">How to: Create a Procedure that Returns a Value (Visual Basic)</span></span>
<span data-ttu-id="da952-103">Você usa um `Function` procedimento retorne um valor para o código de chamada.</span><span class="sxs-lookup"><span data-stu-id="da952-103">You use a `Function` procedure to return a value to the calling code.</span></span>  
  
### <a name="to-create-a-procedure-that-returns-a-value"></a><span data-ttu-id="da952-104">Para criar um procedimento que retorna um valor</span><span class="sxs-lookup"><span data-stu-id="da952-104">To create a procedure that returns a value</span></span>  
  
1.  <span data-ttu-id="da952-105">Fora de qualquer outro procedimento, utilize uma `Function` instrução, seguida por um `End Function` instrução.</span><span class="sxs-lookup"><span data-stu-id="da952-105">Outside any other procedure, use a `Function` statement, followed by an `End Function` statement.</span></span>  
  
2.  <span data-ttu-id="da952-106">No `Function` instrução, siga o `Function` palavra-chave com o nome do procedimento e, em seguida, a lista de parâmetros entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="da952-106">In the `Function` statement, follow the `Function` keyword with the name of the procedure, and then the parameter list in parentheses.</span></span>  
  
3.  <span data-ttu-id="da952-107">Siga os parênteses com uma `As` cláusula para especificar o tipo de dados do valor retornado.</span><span class="sxs-lookup"><span data-stu-id="da952-107">Follow the parentheses with an `As` clause to specify the data type of the returned value.</span></span>  
  
4.  <span data-ttu-id="da952-108">Colocar instruções de código do procedimento entre o `Function` e `End Function` instruções.</span><span class="sxs-lookup"><span data-stu-id="da952-108">Place the procedure's code statements between the `Function` and `End Function` statements.</span></span>  
  
5.  <span data-ttu-id="da952-109">Use um `Return` instrução para retornar o valor para o código de chamada.</span><span class="sxs-lookup"><span data-stu-id="da952-109">Use a `Return` statement to return the value to the calling code.</span></span>  
  
     <span data-ttu-id="da952-110">O seguinte `Function` procedimento calcula o maior lado, ou hipotenusa, de um triângulo retângulo, dado os valores dos outros dois lados.</span><span class="sxs-lookup"><span data-stu-id="da952-110">The following `Function` procedure calculates the longest side, or hypotenuse, of a right triangle, given the values for the other two sides.</span></span>  
  
     [!code-vb[VbVbcnProcedures#1](./codesnippet/VisualBasic/how-to-create-a-procedure-that-returns-a-value_1.vb)]  
  
     <span data-ttu-id="da952-111">O exemplo a seguir mostra uma chamada típica para `hypotenuse`.</span><span class="sxs-lookup"><span data-stu-id="da952-111">The following example shows a typical call to `hypotenuse`.</span></span>  
  
     [!code-vb[VbVbcnProcedures#6](./codesnippet/VisualBasic/how-to-create-a-procedure-that-returns-a-value_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="da952-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="da952-112">See Also</span></span>  
 [<span data-ttu-id="da952-113">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="da952-113">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="da952-114">Subprocedimentos</span><span class="sxs-lookup"><span data-stu-id="da952-114">Sub Procedures</span></span>](./sub-procedures.md)  
 [<span data-ttu-id="da952-115">Procedimentos de Propriedade</span><span class="sxs-lookup"><span data-stu-id="da952-115">Property Procedures</span></span>](./property-procedures.md)  
 [<span data-ttu-id="da952-116">Procedimentos de Operador</span><span class="sxs-lookup"><span data-stu-id="da952-116">Operator Procedures</span></span>](./operator-procedures.md)  
 [<span data-ttu-id="da952-117">Parâmetros e Argumentos de Procedimento</span><span class="sxs-lookup"><span data-stu-id="da952-117">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="da952-118">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="da952-118">Function Statement</span></span>](../../../../visual-basic/language-reference/statements/function-statement.md)  
 [<span data-ttu-id="da952-119">Como retornar um valor de um procedimento</span><span class="sxs-lookup"><span data-stu-id="da952-119">How to: Return a Value from a Procedure</span></span>](./how-to-return-a-value-from-a-procedure.md)  
 [<span data-ttu-id="da952-120">Como chamar um procedimento que retorna um valor</span><span class="sxs-lookup"><span data-stu-id="da952-120">How to: Call a Procedure That Returns a Value</span></span>](./how-to-call-a-procedure-that-returns-a-value.md)
