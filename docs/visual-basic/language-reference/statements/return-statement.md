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
ms.openlocfilehash: 7f8ec0456576133d37dd19b5c0f8878a7ac57dab
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61783897"
---
# <a name="return-statement-visual-basic"></a><span data-ttu-id="1237d-102">Instrução Return (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1237d-102">Return Statement (Visual Basic)</span></span>
<span data-ttu-id="1237d-103">Retorna o controle para o código que chamou um `Function`, `Sub`, `Get`, `Set`, ou `Operator` procedimento.</span><span class="sxs-lookup"><span data-stu-id="1237d-103">Returns control to the code that called a `Function`, `Sub`, `Get`, `Set`, or `Operator` procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1237d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1237d-104">Syntax</span></span>  
  
```  
Return  
-or-  
Return expression  
```  
  
## <a name="part"></a><span data-ttu-id="1237d-105">Parte</span><span class="sxs-lookup"><span data-stu-id="1237d-105">Part</span></span>  
 `expression`  
 <span data-ttu-id="1237d-106">Necessário em uma `Function`, `Get`, ou `Operator` procedimento.</span><span class="sxs-lookup"><span data-stu-id="1237d-106">Required in a `Function`, `Get`, or `Operator` procedure.</span></span> <span data-ttu-id="1237d-107">Expressão que representa o valor a ser retornado para o código de chamada.</span><span class="sxs-lookup"><span data-stu-id="1237d-107">Expression that represents the value to be returned to the calling code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1237d-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="1237d-108">Remarks</span></span>  
 <span data-ttu-id="1237d-109">Em um `Sub` ou `Set` procedimento, o `Return` instrução é equivalente a um `Exit Sub` ou `Exit Property` instrução, e `expression` não deve ser fornecido.</span><span class="sxs-lookup"><span data-stu-id="1237d-109">In a `Sub` or `Set` procedure, the `Return` statement is equivalent to an `Exit Sub` or `Exit Property` statement, and `expression` must not be supplied.</span></span>  
  
 <span data-ttu-id="1237d-110">Em um `Function`, `Get`, ou `Operator` procedimento, o `Return` instrução deve incluir `expression`, e `expression` deve ser avaliada como um tipo de dados que seja conversível para o tipo de retorno do procedimento.</span><span class="sxs-lookup"><span data-stu-id="1237d-110">In a `Function`, `Get`, or `Operator` procedure, the `Return` statement must include `expression`, and `expression` must evaluate to a data type that is convertible to the return type of the procedure.</span></span> <span data-ttu-id="1237d-111">Em um `Function` ou `Get` procedimento, você também tem a alternativa de atribuir uma expressão para o nome do procedimento para servir como o valor de retorno e, em seguida, executar uma `Exit Function` ou `Exit Property` instrução.</span><span class="sxs-lookup"><span data-stu-id="1237d-111">In a `Function` or `Get` procedure, you also have the alternative of assigning an expression to the procedure name to serve as the return value, and then executing an `Exit Function` or `Exit Property` statement.</span></span> <span data-ttu-id="1237d-112">Em um `Operator` procedimento, você deve usar `Return expression`.</span><span class="sxs-lookup"><span data-stu-id="1237d-112">In an `Operator` procedure, you must use `Return expression`.</span></span>  
  
 <span data-ttu-id="1237d-113">Você pode incluir tantos `Return` instruções conforme apropriado no mesmo procedimento.</span><span class="sxs-lookup"><span data-stu-id="1237d-113">You can include as many `Return` statements as appropriate in the same procedure.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1237d-114">O código em um `Finally` bloco é executado depois de uma `Return` instrução em um `Try` ou `Catch` bloco é encontrada, mas antes que `Return` instrução é executada.</span><span class="sxs-lookup"><span data-stu-id="1237d-114">The code in a `Finally` block runs after a `Return` statement in a `Try` or `Catch` block is encountered, but before that `Return` statement executes.</span></span> <span data-ttu-id="1237d-115">Um `Return` instrução não pode ser incluída em um `Finally` bloco.</span><span class="sxs-lookup"><span data-stu-id="1237d-115">A `Return` statement cannot be included in a `Finally` block.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1237d-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1237d-116">Example</span></span>  
 <span data-ttu-id="1237d-117">O exemplo a seguir usa o `Return` instrução várias vezes para retornar para o código de chamada quando o procedimento não precisa fazer mais nada.</span><span class="sxs-lookup"><span data-stu-id="1237d-117">The following example uses the `Return` statement several times to return to the calling code when the procedure does not have to do anything else.</span></span>  
  
 [!code-vb[VbVbalrStatements#53](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#53)]  
  
## <a name="see-also"></a><span data-ttu-id="1237d-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1237d-118">See also</span></span>

- [<span data-ttu-id="1237d-119">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="1237d-119">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="1237d-120">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="1237d-120">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="1237d-121">Instrução Get</span><span class="sxs-lookup"><span data-stu-id="1237d-121">Get Statement</span></span>](../../../visual-basic/language-reference/statements/get-statement.md)
- [<span data-ttu-id="1237d-122">Instrução Set</span><span class="sxs-lookup"><span data-stu-id="1237d-122">Set Statement</span></span>](../../../visual-basic/language-reference/statements/set-statement.md)
- [<span data-ttu-id="1237d-123">Instrução Operator</span><span class="sxs-lookup"><span data-stu-id="1237d-123">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)
- [<span data-ttu-id="1237d-124">Instrução Property</span><span class="sxs-lookup"><span data-stu-id="1237d-124">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="1237d-125">Instrução Exit</span><span class="sxs-lookup"><span data-stu-id="1237d-125">Exit Statement</span></span>](../../../visual-basic/language-reference/statements/exit-statement.md)
- [<span data-ttu-id="1237d-126">Instrução Try...Catch...Finally</span><span class="sxs-lookup"><span data-stu-id="1237d-126">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
