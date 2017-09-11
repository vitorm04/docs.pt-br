---
title: 'Como: criar um procedimento que retorna um valor (Visual Basic) | Documentos do Microsoft'
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
- procedures, defining
- Visual Basic code, procedures
- procedures, returning a value
ms.assetid: 8ee19f95-a9ef-4033-963b-d224dca207c4
caps.latest.revision: 16
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
ms.openlocfilehash: 79bc69e59f0f1d265d49fa92a6a8d5c52931497c
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-create-a-procedure-that-returns-a-value-visual-basic"></a><span data-ttu-id="7ded0-102">Como criar um procedimento que retorne um valor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7ded0-102">How to: Create a Procedure that Returns a Value (Visual Basic)</span></span>
<span data-ttu-id="7ded0-103">Você usa uma `Function` procedimento retorne um valor para o código de chamada.</span><span class="sxs-lookup"><span data-stu-id="7ded0-103">You use a `Function` procedure to return a value to the calling code.</span></span>  
  
### <a name="to-create-a-procedure-that-returns-a-value"></a><span data-ttu-id="7ded0-104">Para criar um procedimento que retorna um valor</span><span class="sxs-lookup"><span data-stu-id="7ded0-104">To create a procedure that returns a value</span></span>  
  
1.  <span data-ttu-id="7ded0-105">Fora de qualquer outro procedimento, utilize uma `Function` instrução, seguida por um `End Function` instrução.</span><span class="sxs-lookup"><span data-stu-id="7ded0-105">Outside any other procedure, use a `Function` statement, followed by an `End Function` statement.</span></span>  
  
2.  <span data-ttu-id="7ded0-106">No `Function` instrução, siga o `Function` palavra-chave com o nome do procedimento e, em seguida, a lista de parâmetros entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="7ded0-106">In the `Function` statement, follow the `Function` keyword with the name of the procedure, and then the parameter list in parentheses.</span></span>  
  
3.  <span data-ttu-id="7ded0-107">Siga os parênteses com uma `As` cláusula para especificar o tipo de dados do valor retornado.</span><span class="sxs-lookup"><span data-stu-id="7ded0-107">Follow the parentheses with an `As` clause to specify the data type of the returned value.</span></span>  
  
4.  <span data-ttu-id="7ded0-108">Coloque as declarações de código do procedimento entre o `Function` e `End Function` instruções.</span><span class="sxs-lookup"><span data-stu-id="7ded0-108">Place the procedure's code statements between the `Function` and `End Function` statements.</span></span>  
  
5.  <span data-ttu-id="7ded0-109">Use um `Return` instrução para retornar o valor para o código de chamada.</span><span class="sxs-lookup"><span data-stu-id="7ded0-109">Use a `Return` statement to return the value to the calling code.</span></span>  
  
     <span data-ttu-id="7ded0-110">O seguinte `Function` procedimento calcula o maior lado, ou hipotenusa, de um triângulo, considerando os valores para os dois lados.</span><span class="sxs-lookup"><span data-stu-id="7ded0-110">The following `Function` procedure calculates the longest side, or hypotenuse, of a right triangle, given the values for the other two sides.</span></span>  
  
     <span data-ttu-id="7ded0-111">[!code-vb[VbVbcnProcedures n º&1;](./codesnippet/VisualBasic/how-to-create-a-procedure-that-returns-a-value_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="7ded0-111">[!code-vb[VbVbcnProcedures#1](./codesnippet/VisualBasic/how-to-create-a-procedure-that-returns-a-value_1.vb)]</span></span>  
  
     <span data-ttu-id="7ded0-112">O exemplo a seguir mostra uma chamada típica para `hypotenuse`.</span><span class="sxs-lookup"><span data-stu-id="7ded0-112">The following example shows a typical call to `hypotenuse`.</span></span>  
  
     <span data-ttu-id="7ded0-113">[!code-vb[VbVbcnProcedures n º&6;](./codesnippet/VisualBasic/how-to-create-a-procedure-that-returns-a-value_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="7ded0-113">[!code-vb[VbVbcnProcedures#6](./codesnippet/VisualBasic/how-to-create-a-procedure-that-returns-a-value_2.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ded0-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7ded0-114">See Also</span></span>  
 <span data-ttu-id="7ded0-115">[Procedimentos](./index.md) </span><span class="sxs-lookup"><span data-stu-id="7ded0-115">[Procedures](./index.md) </span></span>  
<span data-ttu-id="7ded0-116"> [Procedimentos Sub](./sub-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="7ded0-116"> [Sub Procedures](./sub-procedures.md) </span></span>  
<span data-ttu-id="7ded0-117"> [Procedimentos de propriedade](./property-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="7ded0-117"> [Property Procedures](./property-procedures.md) </span></span>  
<span data-ttu-id="7ded0-118"> [Procedimentos de operador](./operator-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="7ded0-118"> [Operator Procedures](./operator-procedures.md) </span></span>  
<span data-ttu-id="7ded0-119"> [Argumentos e parâmetros de procedimento](./procedure-parameters-and-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="7ded0-119"> [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md) </span></span>  
<span data-ttu-id="7ded0-120"> [Instrução Function](../../../../visual-basic/language-reference/statements/function-statement.md) </span><span class="sxs-lookup"><span data-stu-id="7ded0-120"> [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md) </span></span>  
<span data-ttu-id="7ded0-121"> [Como: retornar um valor de um procedimento](./how-to-return-a-value-from-a-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="7ded0-121"> [How to: Return a Value from a Procedure](./how-to-return-a-value-from-a-procedure.md) </span></span>  
<span data-ttu-id="7ded0-122"> [Como chamar um procedimento que retorna um valor](./how-to-call-a-procedure-that-returns-a-value.md)</span><span class="sxs-lookup"><span data-stu-id="7ded0-122"> [How to: Call a Procedure That Returns a Value](./how-to-call-a-procedure-that-returns-a-value.md)</span></span>
