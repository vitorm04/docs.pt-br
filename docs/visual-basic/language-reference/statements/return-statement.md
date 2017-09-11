---
title: "Instrução Return (Visual Basic) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Return
dev_langs:
- VB
helpviewer_keywords:
- Return statement, syntax
- control flow, returning control to expressions
- Return statement
- expressions [Visual Basic], returning control to
ms.assetid: ac86e7f0-5a67-42c3-9834-0e0381efa3ec
caps.latest.revision: 15
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
ms.openlocfilehash: 4826374ddb26b7bd33da8a010e4b58e44075a54e
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="return-statement-visual-basic"></a><span data-ttu-id="7e19f-102">Instrução Return (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7e19f-102">Return Statement (Visual Basic)</span></span>
<span data-ttu-id="7e19f-103">Retorna o controle para o código que chamou um `Function`, `Sub`, `Get`, `Set`, ou `Operator` procedimento.</span><span class="sxs-lookup"><span data-stu-id="7e19f-103">Returns control to the code that called a `Function`, `Sub`, `Get`, `Set`, or `Operator` procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e19f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7e19f-104">Syntax</span></span>  
  
```  
Return  
-or-  
Return expression  
```  
  
## <a name="part"></a><span data-ttu-id="7e19f-105">Parte</span><span class="sxs-lookup"><span data-stu-id="7e19f-105">Part</span></span>  
 `expression`  
 <span data-ttu-id="7e19f-106">Necessário em um `Function`, `Get`, ou `Operator` procedimento.</span><span class="sxs-lookup"><span data-stu-id="7e19f-106">Required in a `Function`, `Get`, or `Operator` procedure.</span></span> <span data-ttu-id="7e19f-107">Expressão que representa o valor a ser retornado para o código de chamada.</span><span class="sxs-lookup"><span data-stu-id="7e19f-107">Expression that represents the value to be returned to the calling code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7e19f-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="7e19f-108">Remarks</span></span>  
 <span data-ttu-id="7e19f-109">Em um `Sub` ou `Set` procedimento, o `Return` instrução é equivalente a uma `Exit Sub` ou `Exit Property` instrução, e `expression` não deve ser fornecido.</span><span class="sxs-lookup"><span data-stu-id="7e19f-109">In a `Sub` or `Set` procedure, the `Return` statement is equivalent to an `Exit Sub` or `Exit Property` statement, and `expression` must not be supplied.</span></span>  
  
 <span data-ttu-id="7e19f-110">Em um `Function`, `Get`, ou `Operator` procedimento, o `Return` deve incluir a instrução `expression`, e `expression` deve ser avaliada como um tipo de dados que seja conversível para o tipo de retorno do procedimento.</span><span class="sxs-lookup"><span data-stu-id="7e19f-110">In a `Function`, `Get`, or `Operator` procedure, the `Return` statement must include `expression`, and `expression` must evaluate to a data type that is convertible to the return type of the procedure.</span></span> <span data-ttu-id="7e19f-111">Em um `Function` ou `Get` procedimento, você também tem a alternativa de atribuir uma expressão para o nome do procedimento para servir como o valor de retorno e, em seguida, executar uma `Exit Function` ou `Exit Property` instrução.</span><span class="sxs-lookup"><span data-stu-id="7e19f-111">In a `Function` or `Get` procedure, you also have the alternative of assigning an expression to the procedure name to serve as the return value, and then executing an `Exit Function` or `Exit Property` statement.</span></span> <span data-ttu-id="7e19f-112">Em um `Operator` procedimento, você deve usar `Return``expression`.</span><span class="sxs-lookup"><span data-stu-id="7e19f-112">In an `Operator` procedure, you must use `Return``expression`.</span></span>  
  
 <span data-ttu-id="7e19f-113">Você pode incluir tantos `Return` instruções conforme apropriado no mesmo procedimento.</span><span class="sxs-lookup"><span data-stu-id="7e19f-113">You can include as many `Return` statements as appropriate in the same procedure.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7e19f-114">O código em um `Finally` bloco é executado após um `Return` instrução em uma `Try` ou `Catch` bloco for encontrada, mas antes que `Return` instrução é executada.</span><span class="sxs-lookup"><span data-stu-id="7e19f-114">The code in a `Finally` block runs after a `Return` statement in a `Try` or `Catch` block is encountered, but before that `Return` statement executes.</span></span> <span data-ttu-id="7e19f-115">A `Return` instrução não pode ser incluída em um `Finally` bloco.</span><span class="sxs-lookup"><span data-stu-id="7e19f-115">A `Return` statement cannot be included in a `Finally` block.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7e19f-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7e19f-116">Example</span></span>  
 <span data-ttu-id="7e19f-117">O exemplo a seguir usa o `Return` instrução várias vezes para retornar para o código de chamada quando o procedimento não precisa fazer mais nada.</span><span class="sxs-lookup"><span data-stu-id="7e19f-117">The following example uses the `Return` statement several times to return to the calling code when the procedure does not have to do anything else.</span></span>  
  
 <span data-ttu-id="7e19f-118">[!code-vb[VbVbalrStatements&#53;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/return-statement_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="7e19f-118">[!code-vb[VbVbalrStatements#53](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/return-statement_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e19f-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7e19f-119">See Also</span></span>  
 <span data-ttu-id="7e19f-120">[Instrução Function](../../../visual-basic/language-reference/statements/function-statement.md) </span><span class="sxs-lookup"><span data-stu-id="7e19f-120">[Function Statement](../../../visual-basic/language-reference/statements/function-statement.md) </span></span>  
<span data-ttu-id="7e19f-121"> [Instrução sub](../../../visual-basic/language-reference/statements/sub-statement.md) </span><span class="sxs-lookup"><span data-stu-id="7e19f-121"> [Sub Statement](../../../visual-basic/language-reference/statements/sub-statement.md) </span></span>  
<span data-ttu-id="7e19f-122"> [Instrução Get](../../../visual-basic/language-reference/statements/get-statement.md) </span><span class="sxs-lookup"><span data-stu-id="7e19f-122"> [Get Statement](../../../visual-basic/language-reference/statements/get-statement.md) </span></span>  
<span data-ttu-id="7e19f-123"> [Instrução Set](../../../visual-basic/language-reference/statements/set-statement.md) </span><span class="sxs-lookup"><span data-stu-id="7e19f-123"> [Set Statement](../../../visual-basic/language-reference/statements/set-statement.md) </span></span>  
<span data-ttu-id="7e19f-124"> [Instrução Operator](../../../visual-basic/language-reference/statements/operator-statement.md) </span><span class="sxs-lookup"><span data-stu-id="7e19f-124"> [Operator Statement](../../../visual-basic/language-reference/statements/operator-statement.md) </span></span>  
<span data-ttu-id="7e19f-125"> [Instrução Property](../../../visual-basic/language-reference/statements/property-statement.md) </span><span class="sxs-lookup"><span data-stu-id="7e19f-125"> [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md) </span></span>  
<span data-ttu-id="7e19f-126"> [Instrução Exit](../../../visual-basic/language-reference/statements/exit-statement.md) </span><span class="sxs-lookup"><span data-stu-id="7e19f-126"> [Exit Statement](../../../visual-basic/language-reference/statements/exit-statement.md) </span></span>  
<span data-ttu-id="7e19f-127"> [Instrução Try...Catch...Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)</span><span class="sxs-lookup"><span data-stu-id="7e19f-127"> [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)</span></span>
