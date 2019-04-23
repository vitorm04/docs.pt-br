---
title: 'Como: Retornar um valor de um procedimento (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], returning from
- procedures [Visual Basic], returning a value
ms.assetid: 4bcc4724-2b4e-4df8-9b4b-16054607f87d
ms.openlocfilehash: 8b53df1634d2b9971bc44c968a17db81cac3924f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59307880"
---
# <a name="how-to-return-a-value-from-a-procedure-visual-basic"></a><span data-ttu-id="cb27d-102">Como: Retornar um valor de um procedimento (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cb27d-102">How to: Return a Value from a Procedure (Visual Basic)</span></span>
<span data-ttu-id="cb27d-103">Um `Function` procedimento retorna um valor para o código de chamada seja executando uma `Return` instrução ou encontrando uma `Exit Function` ou `End Function` instrução.</span><span class="sxs-lookup"><span data-stu-id="cb27d-103">A `Function` procedure returns a value to the calling code either by executing a `Return` statement or by encountering an `Exit Function` or `End Function` statement.</span></span>  
  
### <a name="to-return-a-value-using-the-return-statement"></a><span data-ttu-id="cb27d-104">Para retornar um valor usando a instrução Return</span><span class="sxs-lookup"><span data-stu-id="cb27d-104">To return a value using the Return statement</span></span>  
  
1. <span data-ttu-id="cb27d-105">Coloque um `Return` instrução no ponto em que as tarefas do procedimento é concluída.</span><span class="sxs-lookup"><span data-stu-id="cb27d-105">Put a `Return` statement at the point where the procedure's task is completed.</span></span>  
  
2. <span data-ttu-id="cb27d-106">Siga o `Return` palavra-chave com uma expressão que produz o valor que você deseja retornar ao código de chamada.</span><span class="sxs-lookup"><span data-stu-id="cb27d-106">Follow the `Return` keyword with an expression that yields the value you want to return to the calling code.</span></span>  
  
3. <span data-ttu-id="cb27d-107">Você pode ter mais de um demonstrativo `Return` no mesmo procedimento.</span><span class="sxs-lookup"><span data-stu-id="cb27d-107">You can have more than one `Return` statement in the same procedure.</span></span>  
  
     <span data-ttu-id="cb27d-108">O seguinte `Function` procedimento calcula o lado mais longo, ou hipotenusa de um triângulo e o retorna ao código de chamada.</span><span class="sxs-lookup"><span data-stu-id="cb27d-108">The following `Function` procedure calculates the longest side, or hypotenuse, of a right triangle, and returns it to the calling code.</span></span>  
  
     [!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]  
  
     <span data-ttu-id="cb27d-109">O exemplo a seguir mostra uma chamada típica para `hypotenuse`, que armazena o valor retornado.</span><span class="sxs-lookup"><span data-stu-id="cb27d-109">The following example shows a typical call to `hypotenuse`, which stores the returned value.</span></span>  
  
     [!code-vb[VbVbcnProcedures#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#6)]  
  
### <a name="to-return-a-value-using-exit-function-or-end-function"></a><span data-ttu-id="cb27d-110">Para retornar um valor usando Exit Function ou End Function</span><span class="sxs-lookup"><span data-stu-id="cb27d-110">To return a value using Exit Function or End Function</span></span>  
  
1. <span data-ttu-id="cb27d-111">Em pelo menos um lugar a `Function` procedimento, atribua um valor ao nome do procedimento.</span><span class="sxs-lookup"><span data-stu-id="cb27d-111">In at least one place in the `Function` procedure, assign a value to the procedure's name.</span></span>  
  
2. <span data-ttu-id="cb27d-112">Quando você executa um `Exit Function` ou `End Function` instrução, o Visual Basic retorna o valor mais recentemente atribuído ao nome do procedimento.</span><span class="sxs-lookup"><span data-stu-id="cb27d-112">When you execute an `Exit Function` or `End Function` statement, Visual Basic returns the value most recently assigned to the procedure's name.</span></span>  
  
3. <span data-ttu-id="cb27d-113">Você pode ter mais de um demonstrativo `Exit Function` no mesmo procedimento e mesclar os demonstrativos `Return` e `Exit Function` no mesmo procedimento.</span><span class="sxs-lookup"><span data-stu-id="cb27d-113">You can have more than one `Exit Function` statement in the same procedure, and you can mix `Return` and `Exit Function` statements in the same procedure.</span></span>  
  
4. <span data-ttu-id="cb27d-114">Você pode ter apenas um `End Function` instrução em um `Function` procedimento.</span><span class="sxs-lookup"><span data-stu-id="cb27d-114">You can have only one `End Function` statement in a `Function` procedure.</span></span>  
  
     <span data-ttu-id="cb27d-115">Para obter mais informações e um exemplo, consulte "Valor de retorno" em [instrução Function](../../../../visual-basic/language-reference/statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="cb27d-115">For more information and an example, see "Return Value" in [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb27d-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cb27d-116">See also</span></span>

- [<span data-ttu-id="cb27d-117">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="cb27d-117">Procedures</span></span>](./index.md)
- [<span data-ttu-id="cb27d-118">Subprocedimentos</span><span class="sxs-lookup"><span data-stu-id="cb27d-118">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="cb27d-119">Procedimentos de Propriedade</span><span class="sxs-lookup"><span data-stu-id="cb27d-119">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="cb27d-120">Procedimentos de Operador</span><span class="sxs-lookup"><span data-stu-id="cb27d-120">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="cb27d-121">Parâmetros e Argumentos de Procedimento</span><span class="sxs-lookup"><span data-stu-id="cb27d-121">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="cb27d-122">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="cb27d-122">Function Statement</span></span>](../../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="cb27d-123">Instrução Return</span><span class="sxs-lookup"><span data-stu-id="cb27d-123">Return Statement</span></span>](../../../../visual-basic/language-reference/statements/return-statement.md)
- [<span data-ttu-id="cb27d-124">Como: Criar um procedimento que retorna um valor</span><span class="sxs-lookup"><span data-stu-id="cb27d-124">How to: Create a Procedure that Returns a Value</span></span>](./how-to-create-a-procedure-that-returns-a-value.md)
- [<span data-ttu-id="cb27d-125">Como: Chamar um procedimento que retorna um valor</span><span class="sxs-lookup"><span data-stu-id="cb27d-125">How to: Call a Procedure That Returns a Value</span></span>](./how-to-call-a-procedure-that-returns-a-value.md)
