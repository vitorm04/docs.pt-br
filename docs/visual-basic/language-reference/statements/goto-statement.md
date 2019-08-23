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
ms.openlocfilehash: 3034c84684e94dfe8c334107a16df8cbd227c4d4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912456"
---
# <a name="goto-statement"></a><span data-ttu-id="3f79b-102">Instrução GoTo</span><span class="sxs-lookup"><span data-stu-id="3f79b-102">GoTo Statement</span></span>
<span data-ttu-id="3f79b-103">Ramifica incondicionalmente para uma linha especificada em um procedimento.</span><span class="sxs-lookup"><span data-stu-id="3f79b-103">Branches unconditionally to a specified line in a procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f79b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3f79b-104">Syntax</span></span>  
  
```  
GoTo line  
```  
  
## <a name="part"></a><span data-ttu-id="3f79b-105">Parte</span><span class="sxs-lookup"><span data-stu-id="3f79b-105">Part</span></span>  
 `line`  
 <span data-ttu-id="3f79b-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="3f79b-106">Required.</span></span> <span data-ttu-id="3f79b-107">Qualquer rótulo de linha.</span><span class="sxs-lookup"><span data-stu-id="3f79b-107">Any line label.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3f79b-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="3f79b-108">Remarks</span></span>  
 <span data-ttu-id="3f79b-109">A `GoTo` instrução pode ramificar somente para linhas no procedimento em que ele aparece.</span><span class="sxs-lookup"><span data-stu-id="3f79b-109">The `GoTo` statement can branch only to lines in the procedure in which it appears.</span></span> <span data-ttu-id="3f79b-110">A linha deve ter um rótulo de linha `GoTo` que possa se referir.</span><span class="sxs-lookup"><span data-stu-id="3f79b-110">The line must have a line label that `GoTo` can refer to.</span></span> <span data-ttu-id="3f79b-111">Para obter mais informações, confira [Como: Instruções](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md)de rótulo.</span><span class="sxs-lookup"><span data-stu-id="3f79b-111">For more information, see [How to: Label Statements](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3f79b-112">`GoTo`as instruções podem dificultar a leitura e a manutenção do código.</span><span class="sxs-lookup"><span data-stu-id="3f79b-112">`GoTo` statements can make code difficult to read and maintain.</span></span> <span data-ttu-id="3f79b-113">Sempre que possível, use uma estrutura de controle em vez disso.</span><span class="sxs-lookup"><span data-stu-id="3f79b-113">Whenever possible, use a control structure instead.</span></span> <span data-ttu-id="3f79b-114">Para obter mais informações, consulte [fluxo de controle](../../../visual-basic/programming-guide/language-features/control-flow/index.md).</span><span class="sxs-lookup"><span data-stu-id="3f79b-114">For more information, see [Control Flow](../../../visual-basic/programming-guide/language-features/control-flow/index.md).</span></span>  
  
 <span data-ttu-id="3f79b-115">Não é possível usar `GoTo` uma instrução para ramificação de `For`fora de um... `Next`, `For Each`... `Next`, `SyncLock`... `End SyncLock`, `Try`... `Catch`... `Finally`, `With`... `End With`, ou`Using`... `End Using` construção para um rótulo dentro de.</span><span class="sxs-lookup"><span data-stu-id="3f79b-115">You cannot use a `GoTo` statement to branch from outside a `For`...`Next`, `For Each`...`Next`, `SyncLock`...`End SyncLock`, `Try`...`Catch`...`Finally`, `With`...`End With`, or `Using`...`End Using` construction to a label inside.</span></span>  
  
## <a name="branching-and-try-constructions"></a><span data-ttu-id="3f79b-116">Ramificação e experimente construções</span><span class="sxs-lookup"><span data-stu-id="3f79b-116">Branching and Try Constructions</span></span>  
 <span data-ttu-id="3f79b-117">Em um `Try`... `Catch`... construção, as regras a seguir se aplicam à ramificação com a `GoTo` instrução. `Finally`</span><span class="sxs-lookup"><span data-stu-id="3f79b-117">Within a `Try`...`Catch`...`Finally` construction, the following rules apply to branching with the `GoTo` statement.</span></span>  
  
|<span data-ttu-id="3f79b-118">Bloco ou região</span><span class="sxs-lookup"><span data-stu-id="3f79b-118">Block or region</span></span>|<span data-ttu-id="3f79b-119">Ramificando de fora</span><span class="sxs-lookup"><span data-stu-id="3f79b-119">Branching in from outside</span></span>|<span data-ttu-id="3f79b-120">Ramificação de dentro</span><span class="sxs-lookup"><span data-stu-id="3f79b-120">Branching out from inside</span></span>|  
|---------------------|-------------------------------|-------------------------------|  
|<span data-ttu-id="3f79b-121">`Try`impeça</span><span class="sxs-lookup"><span data-stu-id="3f79b-121">`Try` block</span></span>|<span data-ttu-id="3f79b-122">Somente de um `Catch` bloco da mesma construção <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="3f79b-122">Only from a `Catch` block of the same construction <sup>1</sup></span></span>|<span data-ttu-id="3f79b-123">Somente para fora da construção inteira</span><span class="sxs-lookup"><span data-stu-id="3f79b-123">Only to outside the whole construction</span></span>|  
|<span data-ttu-id="3f79b-124">`Catch`impeça</span><span class="sxs-lookup"><span data-stu-id="3f79b-124">`Catch` block</span></span>|<span data-ttu-id="3f79b-125">Nunca permitido</span><span class="sxs-lookup"><span data-stu-id="3f79b-125">Never allowed</span></span>|<span data-ttu-id="3f79b-126">Somente para fora da construção inteira ou para o `Try` bloco da mesma construção <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="3f79b-126">Only to outside the whole construction, or to the `Try` block of the same construction <sup>1</sup></span></span>|  
|<span data-ttu-id="3f79b-127">`Finally`impeça</span><span class="sxs-lookup"><span data-stu-id="3f79b-127">`Finally` block</span></span>|<span data-ttu-id="3f79b-128">Nunca permitido</span><span class="sxs-lookup"><span data-stu-id="3f79b-128">Never allowed</span></span>|<span data-ttu-id="3f79b-129">Nunca permitido</span><span class="sxs-lookup"><span data-stu-id="3f79b-129">Never allowed</span></span>|  
  
 <span data-ttu-id="3f79b-130"><sup>1</sup> se `Try`houver... `Catch`... a construção é aninhada dentro de `Catch` outra, um `Try` bloco pode ramificar no bloco em seu próprio nível de aninhamento, mas `Try` não em nenhum outro bloco. `Finally`</span><span class="sxs-lookup"><span data-stu-id="3f79b-130"><sup>1</sup> If one `Try`...`Catch`...`Finally` construction is nested within another, a `Catch` block can branch into the `Try` block at its own nesting level, but not into any other `Try` block.</span></span> <span data-ttu-id="3f79b-131">Um aninhado `Try`... `Catch`... a construção deve estar contida completamente em `Try` um `Catch` bloco ou da construção na qual está aninhada. `Finally`</span><span class="sxs-lookup"><span data-stu-id="3f79b-131">A nested `Try`...`Catch`...`Finally` construction must be contained completely in a `Try` or `Catch` block of the construction within which it is nested.</span></span>  
  
 <span data-ttu-id="3f79b-132">A ilustração a seguir mostra `Try` uma construção aninhada dentro de outra.</span><span class="sxs-lookup"><span data-stu-id="3f79b-132">The following illustration shows one `Try` construction nested within another.</span></span> <span data-ttu-id="3f79b-133">Várias ramificações entre os blocos das duas construções são indicadas como válidas ou inválidas.</span><span class="sxs-lookup"><span data-stu-id="3f79b-133">Various branches among the blocks of the two constructions are indicated as valid or invalid.</span></span>  
  
 ![Diagrama gráfico de ramificação em construções try](./media/goto-statement/try-construction-branching.gif)  
  
## <a name="example"></a><span data-ttu-id="3f79b-135">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3f79b-135">Example</span></span>  
 <span data-ttu-id="3f79b-136">O exemplo a seguir usa `GoTo` a instrução para ramificar para rótulos de linha em um procedimento.</span><span class="sxs-lookup"><span data-stu-id="3f79b-136">The following example uses the `GoTo` statement to branch to line labels in a procedure.</span></span>  
  
 [!code-vb[VbVbalrStatements#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#31)]  
  
## <a name="see-also"></a><span data-ttu-id="3f79b-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3f79b-137">See also</span></span>

- [<span data-ttu-id="3f79b-138">Instrução Do...Loop</span><span class="sxs-lookup"><span data-stu-id="3f79b-138">Do...Loop Statement</span></span>](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [<span data-ttu-id="3f79b-139">Instrução For...Next</span><span class="sxs-lookup"><span data-stu-id="3f79b-139">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [<span data-ttu-id="3f79b-140">Instrução For Each...Next</span><span class="sxs-lookup"><span data-stu-id="3f79b-140">For Each...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [<span data-ttu-id="3f79b-141">Instrução If...Then...Else</span><span class="sxs-lookup"><span data-stu-id="3f79b-141">If...Then...Else Statement</span></span>](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [<span data-ttu-id="3f79b-142">Instrução Select...Case</span><span class="sxs-lookup"><span data-stu-id="3f79b-142">Select...Case Statement</span></span>](../../../visual-basic/language-reference/statements/select-case-statement.md)
- [<span data-ttu-id="3f79b-143">Instrução Try...Catch...Finally</span><span class="sxs-lookup"><span data-stu-id="3f79b-143">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [<span data-ttu-id="3f79b-144">Instrução While...End While</span><span class="sxs-lookup"><span data-stu-id="3f79b-144">While...End While Statement</span></span>](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
- [<span data-ttu-id="3f79b-145">Instrução With ... End With</span><span class="sxs-lookup"><span data-stu-id="3f79b-145">With...End With Statement</span></span>](../../../visual-basic/language-reference/statements/with-end-with-statement.md)
