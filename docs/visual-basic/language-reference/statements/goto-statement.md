---
title: Instrução GoTo (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.GoTo
helpviewer_keywords:
- GoTo statement [Visual Basic]
- control flow [Visual Basic], branching
- unconditional branching [Visual Basic]
- branching [Visual Basic]
- branching [Visual Basic], unconditional
- branching [Visual Basic], conditional
- conditional statements [Visual Basic], GoTo statement
- GoTo statement [Visual Basic], syntax
ms.assetid: 313274c2-8ab3-4b9c-9ba3-0fd6798e4f6d
ms.openlocfilehash: 5e7aa036f632b4c310c4978d0d684c1222d2b096
ms.sourcegitcommit: 16aefeb2d265e69c0d80967580365fabf0c5d39a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58125558"
---
# <a name="goto-statement"></a><span data-ttu-id="1ebe8-102">Instrução GoTo</span><span class="sxs-lookup"><span data-stu-id="1ebe8-102">GoTo Statement</span></span>
<span data-ttu-id="1ebe8-103">Branch incondicionalmente para uma linha especificada em um procedimento.</span><span class="sxs-lookup"><span data-stu-id="1ebe8-103">Branches unconditionally to a specified line in a procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ebe8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1ebe8-104">Syntax</span></span>  
  
```  
GoTo line  
```  
  
## <a name="part"></a><span data-ttu-id="1ebe8-105">Parte</span><span class="sxs-lookup"><span data-stu-id="1ebe8-105">Part</span></span>  
 `line`  
 <span data-ttu-id="1ebe8-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="1ebe8-106">Required.</span></span> <span data-ttu-id="1ebe8-107">Qualquer rótulo de linha.</span><span class="sxs-lookup"><span data-stu-id="1ebe8-107">Any line label.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1ebe8-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="1ebe8-108">Remarks</span></span>  
 <span data-ttu-id="1ebe8-109">O `GoTo` instrução pode ramificar somente para linhas no procedimento no qual ele aparece.</span><span class="sxs-lookup"><span data-stu-id="1ebe8-109">The `GoTo` statement can branch only to lines in the procedure in which it appears.</span></span> <span data-ttu-id="1ebe8-110">A linha deve ter uma linha do rótulo que `GoTo` pode consultar.</span><span class="sxs-lookup"><span data-stu-id="1ebe8-110">The line must have a line label that `GoTo` can refer to.</span></span> <span data-ttu-id="1ebe8-111">Para obter mais informações, confira [Como: Rotular instruções](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md).</span><span class="sxs-lookup"><span data-stu-id="1ebe8-111">For more information, see [How to: Label Statements](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1ebe8-112">`GoTo` instruções podem tornar o código difícil de ler e manter.</span><span class="sxs-lookup"><span data-stu-id="1ebe8-112">`GoTo` statements can make code difficult to read and maintain.</span></span> <span data-ttu-id="1ebe8-113">Sempre que possível, use uma estrutura de controle.</span><span class="sxs-lookup"><span data-stu-id="1ebe8-113">Whenever possible, use a control structure instead.</span></span> <span data-ttu-id="1ebe8-114">Para obter mais informações, consulte [fluxo de controle](../../../visual-basic/programming-guide/language-features/control-flow/index.md).</span><span class="sxs-lookup"><span data-stu-id="1ebe8-114">For more information, see [Control Flow](../../../visual-basic/programming-guide/language-features/control-flow/index.md).</span></span>  
  
 <span data-ttu-id="1ebe8-115">Não é possível usar um `GoTo` instrução para ramificar de fora de um `For`... `Next`, `For Each`... `Next`, `SyncLock`... `End SyncLock`, `Try`... `Catch`... `Finally`, `With`... `End With`, ou `Using`... `End Using` construção para um rótulo dentro.</span><span class="sxs-lookup"><span data-stu-id="1ebe8-115">You cannot use a `GoTo` statement to branch from outside a `For`...`Next`, `For Each`...`Next`, `SyncLock`...`End SyncLock`, `Try`...`Catch`...`Finally`, `With`...`End With`, or `Using`...`End Using` construction to a label inside.</span></span>  
  
## <a name="branching-and-try-constructions"></a><span data-ttu-id="1ebe8-116">Ramificações e construções Try</span><span class="sxs-lookup"><span data-stu-id="1ebe8-116">Branching and Try Constructions</span></span>  
 <span data-ttu-id="1ebe8-117">Dentro de um `Try`... `Catch`... `Finally` construção, as seguintes regras se aplicam a ramificação com o `GoTo` instrução.</span><span class="sxs-lookup"><span data-stu-id="1ebe8-117">Within a `Try`...`Catch`...`Finally` construction, the following rules apply to branching with the `GoTo` statement.</span></span>  
  
|<span data-ttu-id="1ebe8-118">Bloco ou região</span><span class="sxs-lookup"><span data-stu-id="1ebe8-118">Block or region</span></span>|<span data-ttu-id="1ebe8-119">Ramificação em de fora</span><span class="sxs-lookup"><span data-stu-id="1ebe8-119">Branching in from outside</span></span>|<span data-ttu-id="1ebe8-120">Ramificação fora do dentro</span><span class="sxs-lookup"><span data-stu-id="1ebe8-120">Branching out from inside</span></span>|  
|---------------------|-------------------------------|-------------------------------|  
|<span data-ttu-id="1ebe8-121">`Try` Bloco</span><span class="sxs-lookup"><span data-stu-id="1ebe8-121">`Try` block</span></span>|<span data-ttu-id="1ebe8-122">Somente de um `Catch` bloco de construção mesmo <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="1ebe8-122">Only from a `Catch` block of the same construction <sup>1</sup></span></span>|<span data-ttu-id="1ebe8-123">Somente a fora da construção inteira</span><span class="sxs-lookup"><span data-stu-id="1ebe8-123">Only to outside the whole construction</span></span>|  
|<span data-ttu-id="1ebe8-124">`Catch` Bloco</span><span class="sxs-lookup"><span data-stu-id="1ebe8-124">`Catch` block</span></span>|<span data-ttu-id="1ebe8-125">Nunca permitidos</span><span class="sxs-lookup"><span data-stu-id="1ebe8-125">Never allowed</span></span>|<span data-ttu-id="1ebe8-126">Somente a fora da construção inteira, ou para o `Try` bloco de construção mesmo <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="1ebe8-126">Only to outside the whole construction, or to the `Try` block of the same construction <sup>1</sup></span></span>|  
|<span data-ttu-id="1ebe8-127">`Finally` Bloco</span><span class="sxs-lookup"><span data-stu-id="1ebe8-127">`Finally` block</span></span>|<span data-ttu-id="1ebe8-128">Nunca permitidos</span><span class="sxs-lookup"><span data-stu-id="1ebe8-128">Never allowed</span></span>|<span data-ttu-id="1ebe8-129">Nunca permitidos</span><span class="sxs-lookup"><span data-stu-id="1ebe8-129">Never allowed</span></span>|  
  
 <span data-ttu-id="1ebe8-130"><sup>1</sup> se um `Try`... `Catch`... `Finally` estiver aninhada dentro de outra, uma `Catch` bloco pode ramificar para o `Try` bloco no seu próprio nível de aninhamento, mas não para qualquer outro `Try` bloco.</span><span class="sxs-lookup"><span data-stu-id="1ebe8-130"><sup>1</sup> If one `Try`...`Catch`...`Finally` construction is nested within another, a `Catch` block can branch into the `Try` block at its own nesting level, but not into any other `Try` block.</span></span> <span data-ttu-id="1ebe8-131">Aninhado `Try`... `Catch`... `Finally` construção deve estar contida completamente em um `Try` ou `Catch` bloco de construção dentro do qual ele está aninhado.</span><span class="sxs-lookup"><span data-stu-id="1ebe8-131">A nested `Try`...`Catch`...`Finally` construction must be contained completely in a `Try` or `Catch` block of the construction within which it is nested.</span></span>  
  
 <span data-ttu-id="1ebe8-132">A ilustração a seguir mostra uma `Try` aninhada em outra.</span><span class="sxs-lookup"><span data-stu-id="1ebe8-132">The following illustration shows one `Try` construction nested within another.</span></span> <span data-ttu-id="1ebe8-133">Várias ramificações entre os blocos das duas construções são indicadas como válidas ou inválidas.</span><span class="sxs-lookup"><span data-stu-id="1ebe8-133">Various branches among the blocks of the two constructions are indicated as valid or invalid.</span></span>  
  
 ![Diagrama gráfico de ramificações em construções Try](./media/goto-statement/try-construction-branching.gif)  
  
## <a name="example"></a><span data-ttu-id="1ebe8-135">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1ebe8-135">Example</span></span>  
 <span data-ttu-id="1ebe8-136">O exemplo a seguir usa o `GoTo` instrução para ramificar para rótulos de linha em um procedimento.</span><span class="sxs-lookup"><span data-stu-id="1ebe8-136">The following example uses the `GoTo` statement to branch to line labels in a procedure.</span></span>  
  
 [!code-vb[VbVbalrStatements#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#31)]  
  
## <a name="see-also"></a><span data-ttu-id="1ebe8-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1ebe8-137">See also</span></span>
- [<span data-ttu-id="1ebe8-138">Instrução Do...Loop</span><span class="sxs-lookup"><span data-stu-id="1ebe8-138">Do...Loop Statement</span></span>](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [<span data-ttu-id="1ebe8-139">Instrução For...Next</span><span class="sxs-lookup"><span data-stu-id="1ebe8-139">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [<span data-ttu-id="1ebe8-140">Instrução For Each...Next</span><span class="sxs-lookup"><span data-stu-id="1ebe8-140">For Each...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [<span data-ttu-id="1ebe8-141">Instrução If...Then...Else</span><span class="sxs-lookup"><span data-stu-id="1ebe8-141">If...Then...Else Statement</span></span>](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [<span data-ttu-id="1ebe8-142">Instrução Select...Case</span><span class="sxs-lookup"><span data-stu-id="1ebe8-142">Select...Case Statement</span></span>](../../../visual-basic/language-reference/statements/select-case-statement.md)
- [<span data-ttu-id="1ebe8-143">Instrução Try...Catch...Finally</span><span class="sxs-lookup"><span data-stu-id="1ebe8-143">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [<span data-ttu-id="1ebe8-144">Instrução While...End While</span><span class="sxs-lookup"><span data-stu-id="1ebe8-144">While...End While Statement</span></span>](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
- [<span data-ttu-id="1ebe8-145">Instrução With ... End With</span><span class="sxs-lookup"><span data-stu-id="1ebe8-145">With...End With Statement</span></span>](../../../visual-basic/language-reference/statements/with-end-with-statement.md)
