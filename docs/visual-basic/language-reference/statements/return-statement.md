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
ms.openlocfilehash: edaaf09f5a984344f7e89c9da988c529774934e9
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583264"
---
# <a name="return-statement-visual-basic"></a><span data-ttu-id="a05c8-102">Instrução Return (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a05c8-102">Return Statement (Visual Basic)</span></span>
<span data-ttu-id="a05c8-103">Retorna o controle para o código que chamou um procedimento `Function`, `Sub`, `Get`, `Set` ou `Operator`.</span><span class="sxs-lookup"><span data-stu-id="a05c8-103">Returns control to the code that called a `Function`, `Sub`, `Get`, `Set`, or `Operator` procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a05c8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a05c8-104">Syntax</span></span>  
  
```vb  
Return  
' -or-  
Return expression  
```  
  
## <a name="part"></a><span data-ttu-id="a05c8-105">Parte</span><span class="sxs-lookup"><span data-stu-id="a05c8-105">Part</span></span>  
 `expression`  
 <span data-ttu-id="a05c8-106">Necessário em um procedimento `Function`, `Get` ou `Operator`.</span><span class="sxs-lookup"><span data-stu-id="a05c8-106">Required in a `Function`, `Get`, or `Operator` procedure.</span></span> <span data-ttu-id="a05c8-107">Expressão que representa o valor a ser retornado para o código de chamada.</span><span class="sxs-lookup"><span data-stu-id="a05c8-107">Expression that represents the value to be returned to the calling code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a05c8-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="a05c8-108">Remarks</span></span>  
 <span data-ttu-id="a05c8-109">Em um procedimento `Sub` ou `Set`, a instrução `Return` é equivalente a uma instrução `Exit Sub` ou `Exit Property` e a `expression` não deve ser fornecida.</span><span class="sxs-lookup"><span data-stu-id="a05c8-109">In a `Sub` or `Set` procedure, the `Return` statement is equivalent to an `Exit Sub` or `Exit Property` statement, and `expression` must not be supplied.</span></span>  
  
 <span data-ttu-id="a05c8-110">Em um procedimento `Function`, `Get` ou `Operator`, a instrução `Return` deve incluir `expression` e `expression` deve ser avaliada como um tipo de dados que é conversível para o tipo de retorno do procedimento.</span><span class="sxs-lookup"><span data-stu-id="a05c8-110">In a `Function`, `Get`, or `Operator` procedure, the `Return` statement must include `expression`, and `expression` must evaluate to a data type that is convertible to the return type of the procedure.</span></span> <span data-ttu-id="a05c8-111">Em um procedimento `Function` ou `Get`, você também tem a alternativa de atribuir uma expressão ao nome do procedimento para servir como o valor de retorno e, em seguida, executar uma instrução `Exit Function` ou `Exit Property`.</span><span class="sxs-lookup"><span data-stu-id="a05c8-111">In a `Function` or `Get` procedure, you also have the alternative of assigning an expression to the procedure name to serve as the return value, and then executing an `Exit Function` or `Exit Property` statement.</span></span> <span data-ttu-id="a05c8-112">Em um procedimento `Operator`, você deve usar `Return expression`.</span><span class="sxs-lookup"><span data-stu-id="a05c8-112">In an `Operator` procedure, you must use `Return expression`.</span></span>  
  
 <span data-ttu-id="a05c8-113">Você pode incluir tantas `Return` instruções, conforme apropriado no mesmo procedimento.</span><span class="sxs-lookup"><span data-stu-id="a05c8-113">You can include as many `Return` statements as appropriate in the same procedure.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a05c8-114">O código em um bloco de `Finally` é executado depois que uma instrução `Return` em um `Try` ou bloco de `Catch` é encontrada, mas antes que a instrução `Return` seja executada.</span><span class="sxs-lookup"><span data-stu-id="a05c8-114">The code in a `Finally` block runs after a `Return` statement in a `Try` or `Catch` block is encountered, but before that `Return` statement executes.</span></span> <span data-ttu-id="a05c8-115">Uma instrução `Return` não pode ser incluída em um bloco de `Finally`.</span><span class="sxs-lookup"><span data-stu-id="a05c8-115">A `Return` statement cannot be included in a `Finally` block.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a05c8-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a05c8-116">Example</span></span>  
 <span data-ttu-id="a05c8-117">O exemplo a seguir usa a instrução `Return` várias vezes para retornar ao código de chamada quando o procedimento não precisa fazer mais nada.</span><span class="sxs-lookup"><span data-stu-id="a05c8-117">The following example uses the `Return` statement several times to return to the calling code when the procedure does not have to do anything else.</span></span>  
  
 [!code-vb[VbVbalrStatements#53](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#53)]  
  
## <a name="see-also"></a><span data-ttu-id="a05c8-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a05c8-118">See also</span></span>

- [<span data-ttu-id="a05c8-119">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="a05c8-119">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="a05c8-120">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="a05c8-120">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="a05c8-121">Instrução Get</span><span class="sxs-lookup"><span data-stu-id="a05c8-121">Get Statement</span></span>](../../../visual-basic/language-reference/statements/get-statement.md)
- [<span data-ttu-id="a05c8-122">Instrução Set</span><span class="sxs-lookup"><span data-stu-id="a05c8-122">Set Statement</span></span>](../../../visual-basic/language-reference/statements/set-statement.md)
- [<span data-ttu-id="a05c8-123">Instrução Operator</span><span class="sxs-lookup"><span data-stu-id="a05c8-123">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)
- [<span data-ttu-id="a05c8-124">Instrução Property</span><span class="sxs-lookup"><span data-stu-id="a05c8-124">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="a05c8-125">Instrução Exit</span><span class="sxs-lookup"><span data-stu-id="a05c8-125">Exit Statement</span></span>](../../../visual-basic/language-reference/statements/exit-statement.md)
- [<span data-ttu-id="a05c8-126">Instrução Try...Catch...Finally</span><span class="sxs-lookup"><span data-stu-id="a05c8-126">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
