---
title: Como criar um procedimento (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- Visual Basic code, reusing
- procedure declarations
- procedures [Visual Basic], about procedures
ms.assetid: 4f779247-0b50-47e8-9e5c-ab5cf39ac0d2
caps.latest.revision: 27
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5e23358e26dbc993b0f9290a8491a3c66717b4c6
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-create-a-procedure-visual-basic"></a><span data-ttu-id="57e35-102">Como criar um procedimento (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="57e35-102">How to: Create a Procedure (Visual Basic)</span></span>
<span data-ttu-id="57e35-103">Você coloca um procedimento entre uma declaração inicial (`Sub` ou `Function`) e uma declaração final (`End Sub` ou `End Function`).</span><span class="sxs-lookup"><span data-stu-id="57e35-103">You enclose a procedure between a starting declaration statement (`Sub` or `Function`) and an ending declaration statement (`End Sub` or `End Function`).</span></span> <span data-ttu-id="57e35-104">Todo o código do procedimento fica entre essas instruções.</span><span class="sxs-lookup"><span data-stu-id="57e35-104">All the procedure's code lies between these statements.</span></span>  
  
 <span data-ttu-id="57e35-105">Um procedimento não pode conter outro procedimento, portanto, suas instruções iniciais e final devem estar fora de qualquer outro procedimento.</span><span class="sxs-lookup"><span data-stu-id="57e35-105">A procedure cannot contain another procedure, so its starting and ending statements must be outside any other procedure.</span></span>  
  
 <span data-ttu-id="57e35-106">Se você tiver código que executa a mesma tarefa em locais diferentes, pode gravar a tarefa uma vez como um procedimento e chamá-lo a partir de locais diferentes em seu código.</span><span class="sxs-lookup"><span data-stu-id="57e35-106">If you have code that performs the same task in different places, you can write the task once as a procedure and then call it from different places in your code.</span></span>  
  
### <a name="to-create-a-procedure-that-does-not-return-a-value"></a><span data-ttu-id="57e35-107">Para criar um procedimento que não retorna um valor</span><span class="sxs-lookup"><span data-stu-id="57e35-107">To create a procedure that does not return a value</span></span>  
  
1.  <span data-ttu-id="57e35-108">Fora de qualquer outro procedimento, utilize uma `Sub` instrução, seguida por um `End Sub` instrução.</span><span class="sxs-lookup"><span data-stu-id="57e35-108">Outside any other procedure, use a `Sub` statement, followed by an `End Sub` statement.</span></span>  
  
2.  <span data-ttu-id="57e35-109">No `Sub` instrução, siga o `Sub` palavra-chave com o nome do procedimento, a lista de parâmetros entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="57e35-109">In the `Sub` statement, follow the `Sub` keyword with the name of the procedure, then the parameter list in parentheses.</span></span>  
  
3.  <span data-ttu-id="57e35-110">Colocar instruções de código do procedimento entre o `Sub` e `End Sub` instruções.</span><span class="sxs-lookup"><span data-stu-id="57e35-110">Place the procedure's code statements between the `Sub` and `End Sub` statements.</span></span>  
  
### <a name="to-create-a-procedure-that-returns-a-value"></a><span data-ttu-id="57e35-111">Para criar um procedimento que retorna um valor</span><span class="sxs-lookup"><span data-stu-id="57e35-111">To create a procedure that returns a value</span></span>  
  
1.  <span data-ttu-id="57e35-112">Fora de qualquer outro procedimento, utilize uma `Function` instrução, seguida por um `End Function` instrução.</span><span class="sxs-lookup"><span data-stu-id="57e35-112">Outside any other procedure, use a `Function` statement, followed by an `End Function` statement.</span></span>  
  
2.  <span data-ttu-id="57e35-113">No `Function` instrução, siga o `Function` palavra-chave com o nome do procedimento, a lista de parâmetros entre parênteses e, em seguida, um `As` cláusula especificando o tipo de dados do valor de retorno.</span><span class="sxs-lookup"><span data-stu-id="57e35-113">In the `Function` statement, follow the `Function` keyword with the name of the procedure, then the parameter list in parentheses, and then an `As` clause specifying the data type of the return value.</span></span>  
  
3.  <span data-ttu-id="57e35-114">Colocar instruções de código do procedimento entre o `Function` e `End Function` instruções.</span><span class="sxs-lookup"><span data-stu-id="57e35-114">Place the procedure's code statements between the `Function` and `End Function` statements.</span></span>  
  
4.  <span data-ttu-id="57e35-115">Use um `Return` instrução para retornar o valor para o código de chamada.</span><span class="sxs-lookup"><span data-stu-id="57e35-115">Use a `Return` statement to return the value to the calling code.</span></span>  
  
### <a name="to-connect-your-new-procedure-with-the-old-repetitive-blocks-of-code"></a><span data-ttu-id="57e35-116">Para conectar seu novo procedimento com os blocos antigos e repetitivos de código</span><span class="sxs-lookup"><span data-stu-id="57e35-116">To connect your new procedure with the old, repetitive blocks of code</span></span>  
  
1.  <span data-ttu-id="57e35-117">Certifique-se de que definir o novo procedimento em um local onde o código antigo tem acesso a ele.</span><span class="sxs-lookup"><span data-stu-id="57e35-117">Make sure you define the new procedure in a place where the old code has access to it.</span></span>  
  
2.  <span data-ttu-id="57e35-118">No seu bloco de código repetitivo antigo, substitua as declarações que executam a tarefa repetitiva com uma única instrução que chama o `Sub` ou `Function` procedimento.</span><span class="sxs-lookup"><span data-stu-id="57e35-118">In your old, repetitive code block, replace the statements that perform the repetitive task with a single statement that calls the `Sub` or `Function` procedure.</span></span>  
  
3.  <span data-ttu-id="57e35-119">Se seu procedimento é um `Function` que retorna um valor, certifique-se de que sua declaração de chamada executa uma ação com o valor retornado, como fazê-lo em uma variável, ou então o valor será perdido.</span><span class="sxs-lookup"><span data-stu-id="57e35-119">If your procedure is a `Function` that returns a value, ensure that your calling statement performs an action with the returned value, such as storing it in a variable, or else the value will be lost.</span></span>  
  
## <a name="example"></a><span data-ttu-id="57e35-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="57e35-120">Example</span></span>  
 <span data-ttu-id="57e35-121">O seguinte `Function` procedimento calcula o maior lado, ou hipotenusa, de um triângulo retângulo, dado os valores dos outros dois lados.</span><span class="sxs-lookup"><span data-stu-id="57e35-121">The following `Function` procedure calculates the longest side, or hypotenuse, of a right triangle, given the values for the other two sides.</span></span>  
  
 [!code-vb[VbVbcnProcedures#1](./codesnippet/VisualBasic/how-to-create-a-procedure_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="57e35-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="57e35-122">See also</span></span>

 [<span data-ttu-id="57e35-123">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="57e35-123">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="57e35-124">Subprocedimentos</span><span class="sxs-lookup"><span data-stu-id="57e35-124">Sub Procedures</span></span>](./sub-procedures.md)  
 [<span data-ttu-id="57e35-125">Procedimentos de Função</span><span class="sxs-lookup"><span data-stu-id="57e35-125">Function Procedures</span></span>](./function-procedures.md)  
 [<span data-ttu-id="57e35-126">Procedimentos de Propriedade</span><span class="sxs-lookup"><span data-stu-id="57e35-126">Property Procedures</span></span>](./property-procedures.md)  
 [<span data-ttu-id="57e35-127">Procedimentos de Operador</span><span class="sxs-lookup"><span data-stu-id="57e35-127">Operator Procedures</span></span>](./operator-procedures.md)  
 [<span data-ttu-id="57e35-128">Parâmetros e Argumentos de Procedimento</span><span class="sxs-lookup"><span data-stu-id="57e35-128">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="57e35-129">Procedimentos Recursivos</span><span class="sxs-lookup"><span data-stu-id="57e35-129">Recursive Procedures</span></span>](./recursive-procedures.md)  
 [<span data-ttu-id="57e35-130">Sobrecarga de Procedimento</span><span class="sxs-lookup"><span data-stu-id="57e35-130">Procedure Overloading</span></span>](./procedure-overloading.md)  
 [<span data-ttu-id="57e35-131">Objetos e Classes</span><span class="sxs-lookup"><span data-stu-id="57e35-131">Objects and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)  
 [<span data-ttu-id="57e35-132">Programação orientada a objeto (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="57e35-132">Object-Oriented Programming (Visual Basic)</span></span>](../../concepts/object-oriented-programming.md)  
