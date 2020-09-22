---
title: Instrução Return
ms.date: 07/20/2015
f1_keywords:
- vb.Return
helpviewer_keywords:
- Return statement [Visual Basic], syntax
- control flow [Visual Basic], returning control to expressions
- Return statement [Visual Basic]
- expressions [Visual Basic], returning control to
ms.assetid: ac86e7f0-5a67-42c3-9834-0e0381efa3ec
ms.openlocfilehash: 3ca705409bc8233bc2562c64b8e7704f08dd7641
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90871803"
---
# <a name="return-statement-visual-basic"></a><span data-ttu-id="0cc05-102">Instrução Return (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0cc05-102">Return Statement (Visual Basic)</span></span>

<span data-ttu-id="0cc05-103">Retorna o controle para o código que chamou `Function` um `Sub` procedimento,, `Get` , `Set` ou `Operator` .</span><span class="sxs-lookup"><span data-stu-id="0cc05-103">Returns control to the code that called a `Function`, `Sub`, `Get`, `Set`, or `Operator` procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0cc05-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0cc05-104">Syntax</span></span>  
  
```vb  
Return  
' -or-  
Return expression  
```  
  
## <a name="part"></a><span data-ttu-id="0cc05-105">Parte</span><span class="sxs-lookup"><span data-stu-id="0cc05-105">Part</span></span>  

 `expression`  
 <span data-ttu-id="0cc05-106">Necessário em um `Function` `Get` procedimento, ou `Operator` .</span><span class="sxs-lookup"><span data-stu-id="0cc05-106">Required in a `Function`, `Get`, or `Operator` procedure.</span></span> <span data-ttu-id="0cc05-107">Expressão que representa o valor a ser retornado para o código de chamada.</span><span class="sxs-lookup"><span data-stu-id="0cc05-107">Expression that represents the value to be returned to the calling code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0cc05-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="0cc05-108">Remarks</span></span>  

 <span data-ttu-id="0cc05-109">Em um `Sub` `Set` procedimento ou, a `Return` instrução é equivalente a uma `Exit Sub` `Exit Property` instrução or e `expression` não deve ser fornecida.</span><span class="sxs-lookup"><span data-stu-id="0cc05-109">In a `Sub` or `Set` procedure, the `Return` statement is equivalent to an `Exit Sub` or `Exit Property` statement, and `expression` must not be supplied.</span></span>  
  
 <span data-ttu-id="0cc05-110">Em um `Function` `Get` procedimento,, ou `Operator` , a `Return` instrução deve incluir `expression` e `expression` deve ser avaliada como um tipo de dados que é conversível para o tipo de retorno do procedimento.</span><span class="sxs-lookup"><span data-stu-id="0cc05-110">In a `Function`, `Get`, or `Operator` procedure, the `Return` statement must include `expression`, and `expression` must evaluate to a data type that is convertible to the return type of the procedure.</span></span> <span data-ttu-id="0cc05-111">Em um `Function` `Get` procedimento ou, você também tem a alternativa de atribuir uma expressão ao nome do procedimento para servir como o valor de retorno e, em seguida, executar `Exit Function` uma `Exit Property` instrução or.</span><span class="sxs-lookup"><span data-stu-id="0cc05-111">In a `Function` or `Get` procedure, you also have the alternative of assigning an expression to the procedure name to serve as the return value, and then executing an `Exit Function` or `Exit Property` statement.</span></span> <span data-ttu-id="0cc05-112">Em um `Operator` procedimento, você deve usar `Return expression` .</span><span class="sxs-lookup"><span data-stu-id="0cc05-112">In an `Operator` procedure, you must use `Return expression`.</span></span>  
  
 <span data-ttu-id="0cc05-113">Você pode incluir quantas `Return` instruções forem apropriadas no mesmo procedimento.</span><span class="sxs-lookup"><span data-stu-id="0cc05-113">You can include as many `Return` statements as appropriate in the same procedure.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0cc05-114">O código em um `Finally` bloco é executado depois `Return` que uma instrução em um `Try` `Catch` bloco ou é encontrada, mas antes que essa `Return` instrução seja executada.</span><span class="sxs-lookup"><span data-stu-id="0cc05-114">The code in a `Finally` block runs after a `Return` statement in a `Try` or `Catch` block is encountered, but before that `Return` statement executes.</span></span> <span data-ttu-id="0cc05-115">Uma `Return` instrução não pode ser incluída em um `Finally` bloco.</span><span class="sxs-lookup"><span data-stu-id="0cc05-115">A `Return` statement cannot be included in a `Finally` block.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0cc05-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0cc05-116">Example</span></span>  

 <span data-ttu-id="0cc05-117">O exemplo a seguir usa a `Return` instrução várias vezes para retornar ao código de chamada quando o procedimento não precisa fazer mais nada.</span><span class="sxs-lookup"><span data-stu-id="0cc05-117">The following example uses the `Return` statement several times to return to the calling code when the procedure does not have to do anything else.</span></span>  
  
 [!code-vb[VbVbalrStatements#53](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#53)]  
  
## <a name="see-also"></a><span data-ttu-id="0cc05-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="0cc05-118">See also</span></span>

- [<span data-ttu-id="0cc05-119">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="0cc05-119">Function Statement</span></span>](function-statement.md)
- [<span data-ttu-id="0cc05-120">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="0cc05-120">Sub Statement</span></span>](sub-statement.md)
- [<span data-ttu-id="0cc05-121">Instrução Get</span><span class="sxs-lookup"><span data-stu-id="0cc05-121">Get Statement</span></span>](get-statement.md)
- [<span data-ttu-id="0cc05-122">Instrução SET</span><span class="sxs-lookup"><span data-stu-id="0cc05-122">Set Statement</span></span>](set-statement.md)
- [<span data-ttu-id="0cc05-123">Instrução Operator</span><span class="sxs-lookup"><span data-stu-id="0cc05-123">Operator Statement</span></span>](operator-statement.md)
- [<span data-ttu-id="0cc05-124">Instrução Property</span><span class="sxs-lookup"><span data-stu-id="0cc05-124">Property Statement</span></span>](property-statement.md)
- [<span data-ttu-id="0cc05-125">Instrução Exit</span><span class="sxs-lookup"><span data-stu-id="0cc05-125">Exit Statement</span></span>](exit-statement.md)
- [<span data-ttu-id="0cc05-126">Instrução Try...Catch...Finally</span><span class="sxs-lookup"><span data-stu-id="0cc05-126">Try...Catch...Finally Statement</span></span>](try-catch-finally-statement.md)
