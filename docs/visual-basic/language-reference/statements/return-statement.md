---
title: Instrução Return (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Return
helpviewer_keywords:
- Return statement [Visual Basic], syntax
- control flow [Visual Basic], returning control to expressions
- Return statement [Visual Basic]
- expressions [Visual Basic], returning control to
ms.assetid: ac86e7f0-5a67-42c3-9834-0e0381efa3ec
ms.openlocfilehash: 2f614045be1b91b9c747d961cdefd526ba1bab98
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33603516"
---
# <a name="return-statement-visual-basic"></a><span data-ttu-id="91730-102">Instrução Return (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="91730-102">Return Statement (Visual Basic)</span></span>
<span data-ttu-id="91730-103">Retorna o controle para o código que chamou um `Function`, `Sub`, `Get`, `Set`, ou `Operator` procedimento.</span><span class="sxs-lookup"><span data-stu-id="91730-103">Returns control to the code that called a `Function`, `Sub`, `Get`, `Set`, or `Operator` procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91730-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="91730-104">Syntax</span></span>  
  
```  
Return  
-or-  
Return expression  
```  
  
## <a name="part"></a><span data-ttu-id="91730-105">Parte</span><span class="sxs-lookup"><span data-stu-id="91730-105">Part</span></span>  
 `expression`  
 <span data-ttu-id="91730-106">Necessário em um `Function`, `Get`, ou `Operator` procedimento.</span><span class="sxs-lookup"><span data-stu-id="91730-106">Required in a `Function`, `Get`, or `Operator` procedure.</span></span> <span data-ttu-id="91730-107">Expressão que representa o valor a ser retornado ao código de chamada.</span><span class="sxs-lookup"><span data-stu-id="91730-107">Expression that represents the value to be returned to the calling code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="91730-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="91730-108">Remarks</span></span>  
 <span data-ttu-id="91730-109">Em um `Sub` ou `Set` procedimento, o `Return` instrução é equivalente a uma `Exit Sub` ou `Exit Property` instrução, e `expression` não deve ser fornecido.</span><span class="sxs-lookup"><span data-stu-id="91730-109">In a `Sub` or `Set` procedure, the `Return` statement is equivalent to an `Exit Sub` or `Exit Property` statement, and `expression` must not be supplied.</span></span>  
  
 <span data-ttu-id="91730-110">Em um `Function`, `Get`, ou `Operator` procedimento, o `Return` deve incluir a instrução `expression`, e `expression` devem ser avaliados como um tipo de dados que é conversível para o tipo de retorno do procedimento.</span><span class="sxs-lookup"><span data-stu-id="91730-110">In a `Function`, `Get`, or `Operator` procedure, the `Return` statement must include `expression`, and `expression` must evaluate to a data type that is convertible to the return type of the procedure.</span></span> <span data-ttu-id="91730-111">Em um `Function` ou `Get` procedimento, você também tem a alternativa de atribuir uma expressão para o nome do procedimento para servir como o valor de retorno e, em seguida, executar uma `Exit Function` ou `Exit Property` instrução.</span><span class="sxs-lookup"><span data-stu-id="91730-111">In a `Function` or `Get` procedure, you also have the alternative of assigning an expression to the procedure name to serve as the return value, and then executing an `Exit Function` or `Exit Property` statement.</span></span> <span data-ttu-id="91730-112">Em um `Operator` procedimento, você deve usar `Return``expression`.</span><span class="sxs-lookup"><span data-stu-id="91730-112">In an `Operator` procedure, you must use `Return``expression`.</span></span>  
  
 <span data-ttu-id="91730-113">Você pode incluir tantos `Return` instruções conforme apropriado no mesmo procedimento.</span><span class="sxs-lookup"><span data-stu-id="91730-113">You can include as many `Return` statements as appropriate in the same procedure.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="91730-114">O código em um `Finally` bloco é executado um `Return` instrução em um `Try` ou `Catch` bloco for encontrada, mas antes que `Return` instrução é executada.</span><span class="sxs-lookup"><span data-stu-id="91730-114">The code in a `Finally` block runs after a `Return` statement in a `Try` or `Catch` block is encountered, but before that `Return` statement executes.</span></span> <span data-ttu-id="91730-115">Um `Return` instrução não pode ser incluída em um `Finally` bloco.</span><span class="sxs-lookup"><span data-stu-id="91730-115">A `Return` statement cannot be included in a `Finally` block.</span></span>  
  
## <a name="example"></a><span data-ttu-id="91730-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="91730-116">Example</span></span>  
 <span data-ttu-id="91730-117">O exemplo a seguir usa o `Return` instrução várias vezes para retornar ao código de chamada quando o procedimento não precisa fazer mais nada.</span><span class="sxs-lookup"><span data-stu-id="91730-117">The following example uses the `Return` statement several times to return to the calling code when the procedure does not have to do anything else.</span></span>  
  
 [!code-vb[VbVbalrStatements#53](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/return-statement_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="91730-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="91730-118">See Also</span></span>  
 [<span data-ttu-id="91730-119">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="91730-119">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
 [<span data-ttu-id="91730-120">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="91730-120">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [<span data-ttu-id="91730-121">Instrução Get</span><span class="sxs-lookup"><span data-stu-id="91730-121">Get Statement</span></span>](../../../visual-basic/language-reference/statements/get-statement.md)  
 [<span data-ttu-id="91730-122">Instrução Set</span><span class="sxs-lookup"><span data-stu-id="91730-122">Set Statement</span></span>](../../../visual-basic/language-reference/statements/set-statement.md)  
 [<span data-ttu-id="91730-123">Instrução Operator</span><span class="sxs-lookup"><span data-stu-id="91730-123">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
 [<span data-ttu-id="91730-124">Instrução Property</span><span class="sxs-lookup"><span data-stu-id="91730-124">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
 [<span data-ttu-id="91730-125">Instrução Exit</span><span class="sxs-lookup"><span data-stu-id="91730-125">Exit Statement</span></span>](../../../visual-basic/language-reference/statements/exit-statement.md)  
 [<span data-ttu-id="91730-126">Instrução Try...Catch...Finally</span><span class="sxs-lookup"><span data-stu-id="91730-126">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
