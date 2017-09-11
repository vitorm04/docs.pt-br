---
title: 'Como: criar um procedimento (Visual Basic) | Documentos do Microsoft'
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
- Visual Basic code, reusing
- procedure declarations
- procedures, about procedures
ms.assetid: 4f779247-0b50-47e8-9e5c-ab5cf39ac0d2
caps.latest.revision: 27
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
ms.openlocfilehash: c97bf12b8b25044043a3bee96f0b5cbfa2bc6c9f
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-create-a-procedure-visual-basic"></a><span data-ttu-id="2250c-102">Como criar um procedimento (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2250c-102">How to: Create a Procedure (Visual Basic)</span></span>
<span data-ttu-id="2250c-103">Você coloca um procedimento entre uma declaração inicial (`Sub` ou `Function`) e uma declaração final (`End Sub` ou `End Function`).</span><span class="sxs-lookup"><span data-stu-id="2250c-103">You enclose a procedure between a starting declaration statement (`Sub` or `Function`) and an ending declaration statement (`End Sub` or `End Function`).</span></span> <span data-ttu-id="2250c-104">Todo o código do procedimento fica entre essas instruções.</span><span class="sxs-lookup"><span data-stu-id="2250c-104">All the procedure's code lies between these statements.</span></span>  
  
 <span data-ttu-id="2250c-105">Um procedimento não pode conter outro procedimento, portanto, suas declarações inicial e final devem estar fora de qualquer outro procedimento.</span><span class="sxs-lookup"><span data-stu-id="2250c-105">A procedure cannot contain another procedure, so its starting and ending statements must be outside any other procedure.</span></span>  
  
 <span data-ttu-id="2250c-106">Se você tiver um código que executa a mesma tarefa em locais diferentes, você pode escrever a tarefa uma vez como um procedimento e, em seguida, chamá-la em locais diferentes em seu código.</span><span class="sxs-lookup"><span data-stu-id="2250c-106">If you have code that performs the same task in different places, you can write the task once as a procedure and then call it from different places in your code.</span></span>  
  
### <a name="to-create-a-procedure-that-does-not-return-a-value"></a><span data-ttu-id="2250c-107">Para criar um procedimento que não retorna um valor</span><span class="sxs-lookup"><span data-stu-id="2250c-107">To create a procedure that does not return a value</span></span>  
  
1.  <span data-ttu-id="2250c-108">Fora de qualquer outro procedimento, utilize uma `Sub` instrução, seguida por um `End Sub` instrução.</span><span class="sxs-lookup"><span data-stu-id="2250c-108">Outside any other procedure, use a `Sub` statement, followed by an `End Sub` statement.</span></span>  
  
2.  <span data-ttu-id="2250c-109">No `Sub` instrução, siga o `Sub` palavra-chave com o nome do procedimento, a lista de parâmetros entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="2250c-109">In the `Sub` statement, follow the `Sub` keyword with the name of the procedure, then the parameter list in parentheses.</span></span>  
  
3.  <span data-ttu-id="2250c-110">Coloque as declarações de código do procedimento entre o `Sub` e `End Sub` instruções.</span><span class="sxs-lookup"><span data-stu-id="2250c-110">Place the procedure's code statements between the `Sub` and `End Sub` statements.</span></span>  
  
### <a name="to-create-a-procedure-that-returns-a-value"></a><span data-ttu-id="2250c-111">Para criar um procedimento que retorna um valor</span><span class="sxs-lookup"><span data-stu-id="2250c-111">To create a procedure that returns a value</span></span>  
  
1.  <span data-ttu-id="2250c-112">Fora de qualquer outro procedimento, utilize uma `Function` instrução, seguida por um `End Function` instrução.</span><span class="sxs-lookup"><span data-stu-id="2250c-112">Outside any other procedure, use a `Function` statement, followed by an `End Function` statement.</span></span>  
  
2.  <span data-ttu-id="2250c-113">No `Function` instrução, siga o `Function` o nome do procedimento, a lista de parâmetros entre parênteses, a palavra-chave e, em seguida, um `As` cláusula especificando o tipo de dados do valor de retorno.</span><span class="sxs-lookup"><span data-stu-id="2250c-113">In the `Function` statement, follow the `Function` keyword with the name of the procedure, then the parameter list in parentheses, and then an `As` clause specifying the data type of the return value.</span></span>  
  
3.  <span data-ttu-id="2250c-114">Coloque as declarações de código do procedimento entre o `Function` e `End Function` instruções.</span><span class="sxs-lookup"><span data-stu-id="2250c-114">Place the procedure's code statements between the `Function` and `End Function` statements.</span></span>  
  
4.  <span data-ttu-id="2250c-115">Use um `Return` instrução para retornar o valor para o código de chamada.</span><span class="sxs-lookup"><span data-stu-id="2250c-115">Use a `Return` statement to return the value to the calling code.</span></span>  
  
### <a name="to-connect-your-new-procedure-with-the-old-repetitive-blocks-of-code"></a><span data-ttu-id="2250c-116">Para conectar seu novo procedimento com os blocos antigos e repetitivos de código</span><span class="sxs-lookup"><span data-stu-id="2250c-116">To connect your new procedure with the old, repetitive blocks of code</span></span>  
  
1.  <span data-ttu-id="2250c-117">Certifique-se de que definir o novo procedimento em um local onde o código antigo tem acesso a ele.</span><span class="sxs-lookup"><span data-stu-id="2250c-117">Make sure you define the new procedure in a place where the old code has access to it.</span></span>  
  
2.  <span data-ttu-id="2250c-118">No seu bloco de código repetitivo antigo, substitua as declarações que executam a tarefa repetitiva com uma declaração única que chama o `Sub` ou `Function` procedimento.</span><span class="sxs-lookup"><span data-stu-id="2250c-118">In your old, repetitive code block, replace the statements that perform the repetitive task with a single statement that calls the `Sub` or `Function` procedure.</span></span>  
  
3.  <span data-ttu-id="2250c-119">Se seu procedimento é um `Function` que retorna um valor, garanta que sua declaração de chamada executa uma ação com o valor retornado, como armazená-lo em uma variável, ou então o valor será perdido.</span><span class="sxs-lookup"><span data-stu-id="2250c-119">If your procedure is a `Function` that returns a value, ensure that your calling statement performs an action with the returned value, such as storing it in a variable, or else the value will be lost.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2250c-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2250c-120">Example</span></span>  
 <span data-ttu-id="2250c-121">O seguinte `Function` procedimento calcula o maior lado, ou hipotenusa, de um triângulo, considerando os valores para os dois lados.</span><span class="sxs-lookup"><span data-stu-id="2250c-121">The following `Function` procedure calculates the longest side, or hypotenuse, of a right triangle, given the values for the other two sides.</span></span>  
  
 <span data-ttu-id="2250c-122">[!code-vb[VbVbcnProcedures n º&1;](./codesnippet/VisualBasic/how-to-create-a-procedure_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="2250c-122">[!code-vb[VbVbcnProcedures#1](./codesnippet/VisualBasic/how-to-create-a-procedure_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2250c-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2250c-123">See Also</span></span>  
 <span data-ttu-id="2250c-124">[Procedimentos](./index.md) </span><span class="sxs-lookup"><span data-stu-id="2250c-124">[Procedures](./index.md) </span></span>  
<span data-ttu-id="2250c-125"> [Procedimentos Sub](./sub-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="2250c-125"> [Sub Procedures](./sub-procedures.md) </span></span>  
<span data-ttu-id="2250c-126"> [Procedimentos de função](./function-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="2250c-126"> [Function Procedures](./function-procedures.md) </span></span>  
<span data-ttu-id="2250c-127"> [Procedimentos de propriedade](./property-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="2250c-127"> [Property Procedures](./property-procedures.md) </span></span>  
<span data-ttu-id="2250c-128"> [Procedimentos de operador](./operator-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="2250c-128"> [Operator Procedures](./operator-procedures.md) </span></span>  
<span data-ttu-id="2250c-129"> [Argumentos e parâmetros de procedimento](./procedure-parameters-and-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="2250c-129"> [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md) </span></span>  
<span data-ttu-id="2250c-130"> [Procedimentos recursivos](./recursive-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="2250c-130"> [Recursive Procedures](./recursive-procedures.md) </span></span>  
<span data-ttu-id="2250c-131"> [Sobrecarga de procedimento](./procedure-overloading.md) </span><span class="sxs-lookup"><span data-stu-id="2250c-131"> [Procedure Overloading](./procedure-overloading.md) </span></span>  
<span data-ttu-id="2250c-132"> [Objetos e Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md) </span><span class="sxs-lookup"><span data-stu-id="2250c-132"> [Objects and Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md) </span></span>  
<span data-ttu-id="2250c-133"> [Programação Orientada a Objeto](http://msdn.microsoft.com/library/1cf6e655-3f30-45f1-9a5d-4a88ca24a1c2)</span><span class="sxs-lookup"><span data-stu-id="2250c-133"> [Object-Oriented Programming](http://msdn.microsoft.com/library/1cf6e655-3f30-45f1-9a5d-4a88ca24a1c2)</span></span>
