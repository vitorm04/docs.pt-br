---
title: 'Como: retornar um valor de um procedimento (Visual Basic) | Documentos do Microsoft'
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
- Visual Basic code, procedures
- procedures, returning from
- procedures, returning a value
ms.assetid: 4bcc4724-2b4e-4df8-9b4b-16054607f87d
caps.latest.revision: 12
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
ms.openlocfilehash: 601cd3adca0105eb829bb6156f94289b5c9f5f72
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-return-a-value-from-a-procedure-visual-basic"></a><span data-ttu-id="458ff-102">Como retornar um valor de um procedimento (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="458ff-102">How to: Return a Value from a Procedure (Visual Basic)</span></span>
<span data-ttu-id="458ff-103">A `Function` procedimento retorna um valor para o código de chamada seja executando uma `Return` instrução ou encontrando uma `Exit Function` ou `End Function` instrução.</span><span class="sxs-lookup"><span data-stu-id="458ff-103">A `Function` procedure returns a value to the calling code either by executing a `Return` statement or by encountering an `Exit Function` or `End Function` statement.</span></span>  
  
### <a name="to-return-a-value-using-the-return-statement"></a><span data-ttu-id="458ff-104">Para retornar um valor usando a instrução Return</span><span class="sxs-lookup"><span data-stu-id="458ff-104">To return a value using the Return statement</span></span>  
  
1.  <span data-ttu-id="458ff-105">Colocar um `Return` instrução no ponto onde as tarefas do procedimento estão completas.</span><span class="sxs-lookup"><span data-stu-id="458ff-105">Put a `Return` statement at the point where the procedure's task is completed.</span></span>  
  
2.  <span data-ttu-id="458ff-106">Execute o `Return` palavra-chave com uma expressão que produz o valor que você deseja retornar ao código de chamada.</span><span class="sxs-lookup"><span data-stu-id="458ff-106">Follow the `Return` keyword with an expression that yields the value you want to return to the calling code.</span></span>  
  
3.  <span data-ttu-id="458ff-107">Você pode ter mais de uma `Return` instrução no mesmo procedimento.</span><span class="sxs-lookup"><span data-stu-id="458ff-107">You can have more than one `Return` statement in the same procedure.</span></span>  
  
     <span data-ttu-id="458ff-108">O seguinte `Function` procedimento calcula o maior lado, ou hipotenusa, de um triângulo e retorna para o código de chamada.</span><span class="sxs-lookup"><span data-stu-id="458ff-108">The following `Function` procedure calculates the longest side, or hypotenuse, of a right triangle, and returns it to the calling code.</span></span>  
  
     <span data-ttu-id="458ff-109">[!code-vb[VbVbcnProcedures n º&1;](./codesnippet/VisualBasic/how-to-return-a-value-from-a-procedure_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="458ff-109">[!code-vb[VbVbcnProcedures#1](./codesnippet/VisualBasic/how-to-return-a-value-from-a-procedure_1.vb)]</span></span>  
  
     <span data-ttu-id="458ff-110">O exemplo a seguir mostra uma chamada típica para `hypotenuse`, que armazena o valor retornado.</span><span class="sxs-lookup"><span data-stu-id="458ff-110">The following example shows a typical call to `hypotenuse`, which stores the returned value.</span></span>  
  
     <span data-ttu-id="458ff-111">[!code-vb[VbVbcnProcedures n º&6;](./codesnippet/VisualBasic/how-to-return-a-value-from-a-procedure_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="458ff-111">[!code-vb[VbVbcnProcedures#6](./codesnippet/VisualBasic/how-to-return-a-value-from-a-procedure_2.vb)]</span></span>  
  
### <a name="to-return-a-value-using-exit-function-or-end-function"></a><span data-ttu-id="458ff-112">Para retornar um valor usando Exit Function ou End Function</span><span class="sxs-lookup"><span data-stu-id="458ff-112">To return a value using Exit Function or End Function</span></span>  
  
1.  <span data-ttu-id="458ff-113">Em pelo menos um lugar a `Function` procedimento, atribua um valor ao nome do procedimento.</span><span class="sxs-lookup"><span data-stu-id="458ff-113">In at least one place in the `Function` procedure, assign a value to the procedure's name.</span></span>  
  
2.  <span data-ttu-id="458ff-114">Quando você executa um `Exit Function` ou `End Function` instrução, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] retorna o valor mais recentemente atribuído ao nome do procedimento.</span><span class="sxs-lookup"><span data-stu-id="458ff-114">When you execute an `Exit Function` or `End Function` statement, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] returns the value most recently assigned to the procedure's name.</span></span>  
  
3.  <span data-ttu-id="458ff-115">Você pode ter mais de uma `Exit Function` instrução no mesmo procedimento e você pode misturar `Return` e `Exit Function` instruções no mesmo procedimento.</span><span class="sxs-lookup"><span data-stu-id="458ff-115">You can have more than one `Exit Function` statement in the same procedure, and you can mix `Return` and `Exit Function` statements in the same procedure.</span></span>  
  
4.  <span data-ttu-id="458ff-116">Você pode ter apenas uma `End Function` instrução em uma `Function` procedimento.</span><span class="sxs-lookup"><span data-stu-id="458ff-116">You can have only one `End Function` statement in a `Function` procedure.</span></span>  
  
     <span data-ttu-id="458ff-117">Para obter mais informações e um exemplo, consulte "Valor de retorno" em [declaração de função](../../../../visual-basic/language-reference/statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="458ff-117">For more information and an example, see "Return Value" in [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="458ff-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="458ff-118">See Also</span></span>  
 <span data-ttu-id="458ff-119">[Procedimentos](./index.md) </span><span class="sxs-lookup"><span data-stu-id="458ff-119">[Procedures](./index.md) </span></span>  
<span data-ttu-id="458ff-120"> [Procedimentos Sub](./sub-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="458ff-120"> [Sub Procedures](./sub-procedures.md) </span></span>  
<span data-ttu-id="458ff-121"> [Procedimentos de propriedade](./property-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="458ff-121"> [Property Procedures](./property-procedures.md) </span></span>  
<span data-ttu-id="458ff-122"> [Procedimentos de operador](./operator-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="458ff-122"> [Operator Procedures](./operator-procedures.md) </span></span>  
<span data-ttu-id="458ff-123"> [Argumentos e parâmetros de procedimento](./procedure-parameters-and-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="458ff-123"> [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md) </span></span>  
<span data-ttu-id="458ff-124"> [Instrução Function](../../../../visual-basic/language-reference/statements/function-statement.md) </span><span class="sxs-lookup"><span data-stu-id="458ff-124"> [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md) </span></span>  
<span data-ttu-id="458ff-125"> [Instrução Return](../../../../visual-basic/language-reference/statements/return-statement.md) </span><span class="sxs-lookup"><span data-stu-id="458ff-125"> [Return Statement](../../../../visual-basic/language-reference/statements/return-statement.md) </span></span>  
<span data-ttu-id="458ff-126"> [Como: criar um procedimento que retorna um valor](./how-to-create-a-procedure-that-returns-a-value.md) </span><span class="sxs-lookup"><span data-stu-id="458ff-126"> [How to: Create a Procedure that Returns a Value](./how-to-create-a-procedure-that-returns-a-value.md) </span></span>  
<span data-ttu-id="458ff-127"> [Como chamar um procedimento que retorna um valor](./how-to-call-a-procedure-that-returns-a-value.md)</span><span class="sxs-lookup"><span data-stu-id="458ff-127"> [How to: Call a Procedure That Returns a Value](./how-to-call-a-procedure-that-returns-a-value.md)</span></span>
