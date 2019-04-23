---
title: 'Como: Criar um procedimento que retorna um valor (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedures [Visual Basic], returning a value
ms.assetid: 8ee19f95-a9ef-4033-963b-d224dca207c4
ms.openlocfilehash: 115c1df4bd49d5848d72c4cbd0242a49a12740c7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59335492"
---
# <a name="how-to-create-a-procedure-that-returns-a-value-visual-basic"></a><span data-ttu-id="cdceb-102">Como: Criar um procedimento que retorna um valor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cdceb-102">How to: Create a Procedure that Returns a Value (Visual Basic)</span></span>
<span data-ttu-id="cdceb-103">Você usa um `Function` procedimento retornar um valor para o código de chamada.</span><span class="sxs-lookup"><span data-stu-id="cdceb-103">You use a `Function` procedure to return a value to the calling code.</span></span>  
  
### <a name="to-create-a-procedure-that-returns-a-value"></a><span data-ttu-id="cdceb-104">Para criar um procedimento que retorna um valor</span><span class="sxs-lookup"><span data-stu-id="cdceb-104">To create a procedure that returns a value</span></span>  
  
1. <span data-ttu-id="cdceb-105">Fora de qualquer outro procedimento, utilize uma `Function` instrução, seguida por um `End Function` instrução.</span><span class="sxs-lookup"><span data-stu-id="cdceb-105">Outside any other procedure, use a `Function` statement, followed by an `End Function` statement.</span></span>  
  
2. <span data-ttu-id="cdceb-106">No `Function` instrução, siga o `Function` palavra-chave com o nome do procedimento e, em seguida, a lista de parâmetros entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="cdceb-106">In the `Function` statement, follow the `Function` keyword with the name of the procedure, and then the parameter list in parentheses.</span></span>  
  
3. <span data-ttu-id="cdceb-107">Siga os parênteses com um `As` cláusula para especificar o tipo de dados do valor retornado.</span><span class="sxs-lookup"><span data-stu-id="cdceb-107">Follow the parentheses with an `As` clause to specify the data type of the returned value.</span></span>  
  
4. <span data-ttu-id="cdceb-108">Colocar instruções de código do procedimento entre o `Function` e `End Function` instruções.</span><span class="sxs-lookup"><span data-stu-id="cdceb-108">Place the procedure's code statements between the `Function` and `End Function` statements.</span></span>  
  
5. <span data-ttu-id="cdceb-109">Use um `Return` instrução para retornar o valor para o código de chamada.</span><span class="sxs-lookup"><span data-stu-id="cdceb-109">Use a `Return` statement to return the value to the calling code.</span></span>  
  
     <span data-ttu-id="cdceb-110">O seguinte `Function` procedimento calcula o lado mais longo, ou hipotenusa de um triângulo, considerando os valores para os dois lados.</span><span class="sxs-lookup"><span data-stu-id="cdceb-110">The following `Function` procedure calculates the longest side, or hypotenuse, of a right triangle, given the values for the other two sides.</span></span>  
  
     [!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]  
  
     <span data-ttu-id="cdceb-111">O exemplo a seguir mostra uma chamada típica para `hypotenuse`.</span><span class="sxs-lookup"><span data-stu-id="cdceb-111">The following example shows a typical call to `hypotenuse`.</span></span>  
  
     [!code-vb[VbVbcnProcedures#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="cdceb-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cdceb-112">See also</span></span>

- [<span data-ttu-id="cdceb-113">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="cdceb-113">Procedures</span></span>](./index.md)
- [<span data-ttu-id="cdceb-114">Subprocedimentos</span><span class="sxs-lookup"><span data-stu-id="cdceb-114">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="cdceb-115">Procedimentos de Propriedade</span><span class="sxs-lookup"><span data-stu-id="cdceb-115">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="cdceb-116">Procedimentos de Operador</span><span class="sxs-lookup"><span data-stu-id="cdceb-116">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="cdceb-117">Parâmetros e Argumentos de Procedimento</span><span class="sxs-lookup"><span data-stu-id="cdceb-117">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="cdceb-118">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="cdceb-118">Function Statement</span></span>](../../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="cdceb-119">Como: Retornar um valor de um procedimento</span><span class="sxs-lookup"><span data-stu-id="cdceb-119">How to: Return a Value from a Procedure</span></span>](./how-to-return-a-value-from-a-procedure.md)
- [<span data-ttu-id="cdceb-120">Como: Chamar um procedimento que retorna um valor</span><span class="sxs-lookup"><span data-stu-id="cdceb-120">How to: Call a Procedure That Returns a Value</span></span>](./how-to-call-a-procedure-that-returns-a-value.md)
