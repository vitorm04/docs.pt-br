---
title: Como criar um procedimento que retorne um valor
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedures [Visual Basic], returning a value
ms.assetid: 8ee19f95-a9ef-4033-963b-d224dca207c4
ms.openlocfilehash: 3d28162d2a2103477a20b08fc03c937de8b5a475
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91071866"
---
# <a name="how-to-create-a-procedure-that-returns-a-value-visual-basic"></a><span data-ttu-id="7e961-102">Como criar um procedimento que retorne um valor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7e961-102">How to: Create a Procedure that Returns a Value (Visual Basic)</span></span>

<span data-ttu-id="7e961-103">Você usa um `Function` procedimento para retornar um valor para o código de chamada.</span><span class="sxs-lookup"><span data-stu-id="7e961-103">You use a `Function` procedure to return a value to the calling code.</span></span>  
  
### <a name="to-create-a-procedure-that-returns-a-value"></a><span data-ttu-id="7e961-104">Para criar um procedimento que retorna um valor</span><span class="sxs-lookup"><span data-stu-id="7e961-104">To create a procedure that returns a value</span></span>  
  
1. <span data-ttu-id="7e961-105">Fora de qualquer outro procedimento, use uma `Function` instrução, seguida por uma `End Function` instrução.</span><span class="sxs-lookup"><span data-stu-id="7e961-105">Outside any other procedure, use a `Function` statement, followed by an `End Function` statement.</span></span>  
  
2. <span data-ttu-id="7e961-106">Na `Function` instrução, siga a `Function` palavra-chave com o nome do procedimento e, em seguida, a lista de parâmetros entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="7e961-106">In the `Function` statement, follow the `Function` keyword with the name of the procedure, and then the parameter list in parentheses.</span></span>  
  
3. <span data-ttu-id="7e961-107">Siga os parênteses com uma `As` cláusula para especificar o tipo de dados do valor retornado.</span><span class="sxs-lookup"><span data-stu-id="7e961-107">Follow the parentheses with an `As` clause to specify the data type of the returned value.</span></span>  
  
4. <span data-ttu-id="7e961-108">Coloque as instruções de código do procedimento entre `Function` as `End Function` instruções e.</span><span class="sxs-lookup"><span data-stu-id="7e961-108">Place the procedure's code statements between the `Function` and `End Function` statements.</span></span>  
  
5. <span data-ttu-id="7e961-109">Use uma `Return` instrução para retornar o valor para o código de chamada.</span><span class="sxs-lookup"><span data-stu-id="7e961-109">Use a `Return` statement to return the value to the calling code.</span></span>  
  
     <span data-ttu-id="7e961-110">O procedimento a seguir `Function` calcula o lado mais longo, ou hipotenusa, de um triângulo à direita, dado os valores para os outros dois lados.</span><span class="sxs-lookup"><span data-stu-id="7e961-110">The following `Function` procedure calculates the longest side, or hypotenuse, of a right triangle, given the values for the other two sides.</span></span>  
  
     [!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]  
  
     <span data-ttu-id="7e961-111">O exemplo a seguir mostra uma chamada típica para `hypotenuse` .</span><span class="sxs-lookup"><span data-stu-id="7e961-111">The following example shows a typical call to `hypotenuse`.</span></span>  
  
     [!code-vb[VbVbcnProcedures#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="7e961-112">Confira também</span><span class="sxs-lookup"><span data-stu-id="7e961-112">See also</span></span>

- [<span data-ttu-id="7e961-113">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="7e961-113">Procedures</span></span>](./index.md)
- [<span data-ttu-id="7e961-114">Subprocedimentos</span><span class="sxs-lookup"><span data-stu-id="7e961-114">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="7e961-115">Procedimentos de propriedade</span><span class="sxs-lookup"><span data-stu-id="7e961-115">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="7e961-116">Procedimentos do operador</span><span class="sxs-lookup"><span data-stu-id="7e961-116">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="7e961-117">Parâmetros e Argumentos de Procedimento</span><span class="sxs-lookup"><span data-stu-id="7e961-117">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="7e961-118">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="7e961-118">Function Statement</span></span>](../../../language-reference/statements/function-statement.md)
- [<span data-ttu-id="7e961-119">Como retornar um valor de um procedimento</span><span class="sxs-lookup"><span data-stu-id="7e961-119">How to: Return a Value from a Procedure</span></span>](./how-to-return-a-value-from-a-procedure.md)
- [<span data-ttu-id="7e961-120">Como chamar um procedimento que retorna um valor</span><span class="sxs-lookup"><span data-stu-id="7e961-120">How to: Call a Procedure That Returns a Value</span></span>](./how-to-call-a-procedure-that-returns-a-value.md)
