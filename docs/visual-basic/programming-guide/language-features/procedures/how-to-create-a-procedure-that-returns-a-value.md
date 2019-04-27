---
title: 'Como: Criar um procedimento que retorna um valor (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedures [Visual Basic], returning a value
ms.assetid: 8ee19f95-a9ef-4033-963b-d224dca207c4
ms.openlocfilehash: 115c1df4bd49d5848d72c4cbd0242a49a12740c7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61863721"
---
# <a name="how-to-create-a-procedure-that-returns-a-value-visual-basic"></a><span data-ttu-id="96c3a-102">Como: Criar um procedimento que retorna um valor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="96c3a-102">How to: Create a Procedure that Returns a Value (Visual Basic)</span></span>
<span data-ttu-id="96c3a-103">Você usa um `Function` procedimento retornar um valor para o código de chamada.</span><span class="sxs-lookup"><span data-stu-id="96c3a-103">You use a `Function` procedure to return a value to the calling code.</span></span>  
  
### <a name="to-create-a-procedure-that-returns-a-value"></a><span data-ttu-id="96c3a-104">Para criar um procedimento que retorna um valor</span><span class="sxs-lookup"><span data-stu-id="96c3a-104">To create a procedure that returns a value</span></span>  
  
1. <span data-ttu-id="96c3a-105">Fora de qualquer outro procedimento, utilize uma `Function` instrução, seguida por um `End Function` instrução.</span><span class="sxs-lookup"><span data-stu-id="96c3a-105">Outside any other procedure, use a `Function` statement, followed by an `End Function` statement.</span></span>  
  
2. <span data-ttu-id="96c3a-106">No `Function` instrução, siga o `Function` palavra-chave com o nome do procedimento e, em seguida, a lista de parâmetros entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="96c3a-106">In the `Function` statement, follow the `Function` keyword with the name of the procedure, and then the parameter list in parentheses.</span></span>  
  
3. <span data-ttu-id="96c3a-107">Siga os parênteses com um `As` cláusula para especificar o tipo de dados do valor retornado.</span><span class="sxs-lookup"><span data-stu-id="96c3a-107">Follow the parentheses with an `As` clause to specify the data type of the returned value.</span></span>  
  
4. <span data-ttu-id="96c3a-108">Colocar instruções de código do procedimento entre o `Function` e `End Function` instruções.</span><span class="sxs-lookup"><span data-stu-id="96c3a-108">Place the procedure's code statements between the `Function` and `End Function` statements.</span></span>  
  
5. <span data-ttu-id="96c3a-109">Use um `Return` instrução para retornar o valor para o código de chamada.</span><span class="sxs-lookup"><span data-stu-id="96c3a-109">Use a `Return` statement to return the value to the calling code.</span></span>  
  
     <span data-ttu-id="96c3a-110">O seguinte `Function` procedimento calcula o lado mais longo, ou hipotenusa de um triângulo, considerando os valores para os dois lados.</span><span class="sxs-lookup"><span data-stu-id="96c3a-110">The following `Function` procedure calculates the longest side, or hypotenuse, of a right triangle, given the values for the other two sides.</span></span>  
  
     [!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]  
  
     <span data-ttu-id="96c3a-111">O exemplo a seguir mostra uma chamada típica para `hypotenuse`.</span><span class="sxs-lookup"><span data-stu-id="96c3a-111">The following example shows a typical call to `hypotenuse`.</span></span>  
  
     [!code-vb[VbVbcnProcedures#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="96c3a-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="96c3a-112">See also</span></span>

- [<span data-ttu-id="96c3a-113">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="96c3a-113">Procedures</span></span>](./index.md)
- [<span data-ttu-id="96c3a-114">Subprocedimentos</span><span class="sxs-lookup"><span data-stu-id="96c3a-114">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="96c3a-115">Procedimentos de Propriedade</span><span class="sxs-lookup"><span data-stu-id="96c3a-115">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="96c3a-116">Procedimentos de Operador</span><span class="sxs-lookup"><span data-stu-id="96c3a-116">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="96c3a-117">Parâmetros e Argumentos de Procedimento</span><span class="sxs-lookup"><span data-stu-id="96c3a-117">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="96c3a-118">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="96c3a-118">Function Statement</span></span>](../../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="96c3a-119">Como: Retornar um valor de um procedimento</span><span class="sxs-lookup"><span data-stu-id="96c3a-119">How to: Return a Value from a Procedure</span></span>](./how-to-return-a-value-from-a-procedure.md)
- [<span data-ttu-id="96c3a-120">Como: Chamar um procedimento que retorna um valor</span><span class="sxs-lookup"><span data-stu-id="96c3a-120">How to: Call a Procedure That Returns a Value</span></span>](./how-to-call-a-procedure-that-returns-a-value.md)
