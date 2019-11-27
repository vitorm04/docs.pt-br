---
title: Instrução GoTo
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
ms.openlocfilehash: d5cdcd214c9679e245645505fe11cb5d521ce085
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351082"
---
# <a name="goto-statement"></a><span data-ttu-id="08495-102">Instrução GoTo</span><span class="sxs-lookup"><span data-stu-id="08495-102">GoTo Statement</span></span>
<span data-ttu-id="08495-103">Ramifica incondicionalmente para uma linha especificada em um procedimento.</span><span class="sxs-lookup"><span data-stu-id="08495-103">Branches unconditionally to a specified line in a procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08495-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="08495-104">Syntax</span></span>  
  
```vb  
GoTo line  
```  
  
## <a name="part"></a><span data-ttu-id="08495-105">Parte</span><span class="sxs-lookup"><span data-stu-id="08495-105">Part</span></span>  
 `line`  
 <span data-ttu-id="08495-106">Necessária.</span><span class="sxs-lookup"><span data-stu-id="08495-106">Required.</span></span> <span data-ttu-id="08495-107">Qualquer rótulo de linha.</span><span class="sxs-lookup"><span data-stu-id="08495-107">Any line label.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="08495-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="08495-108">Remarks</span></span>  
 <span data-ttu-id="08495-109">A instrução `GoTo` pode ramificar somente para linhas no procedimento em que ele aparece.</span><span class="sxs-lookup"><span data-stu-id="08495-109">The `GoTo` statement can branch only to lines in the procedure in which it appears.</span></span> <span data-ttu-id="08495-110">A linha deve ter um rótulo de linha ao qual `GoTo` possa se referir.</span><span class="sxs-lookup"><span data-stu-id="08495-110">The line must have a line label that `GoTo` can refer to.</span></span> <span data-ttu-id="08495-111">Para obter mais informações, consulte [instruções de rótulo](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md).</span><span class="sxs-lookup"><span data-stu-id="08495-111">For more information, see [How to: Label Statements](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="08495-112">`GoTo` instruções podem dificultar a leitura e a manutenção do código.</span><span class="sxs-lookup"><span data-stu-id="08495-112">`GoTo` statements can make code difficult to read and maintain.</span></span> <span data-ttu-id="08495-113">Sempre que possível, use uma estrutura de controle em vez disso.</span><span class="sxs-lookup"><span data-stu-id="08495-113">Whenever possible, use a control structure instead.</span></span> <span data-ttu-id="08495-114">Para obter mais informações, consulte [fluxo de controle](../../../visual-basic/programming-guide/language-features/control-flow/index.md).</span><span class="sxs-lookup"><span data-stu-id="08495-114">For more information, see [Control Flow](../../../visual-basic/programming-guide/language-features/control-flow/index.md).</span></span>  
  
 <span data-ttu-id="08495-115">Você não pode usar uma instrução `GoTo` para ramificar de fora de uma `For`...`Next`, `For Each`...`Next`, `SyncLock`...`End SyncLock`, `Try`...`Catch`...`Finally`, `With`...`End With`ou `Using`...`End Using` construção a um rótulo dentro de.</span><span class="sxs-lookup"><span data-stu-id="08495-115">You cannot use a `GoTo` statement to branch from outside a `For`...`Next`, `For Each`...`Next`, `SyncLock`...`End SyncLock`, `Try`...`Catch`...`Finally`, `With`...`End With`, or `Using`...`End Using` construction to a label inside.</span></span>  
  
## <a name="branching-and-try-constructions"></a><span data-ttu-id="08495-116">Ramificação e experimente construções</span><span class="sxs-lookup"><span data-stu-id="08495-116">Branching and Try Constructions</span></span>  
 <span data-ttu-id="08495-117">Em uma construção `Try`...`Catch`...`Finally`, as regras a seguir se aplicam à ramificação com a instrução `GoTo`.</span><span class="sxs-lookup"><span data-stu-id="08495-117">Within a `Try`...`Catch`...`Finally` construction, the following rules apply to branching with the `GoTo` statement.</span></span>  
  
|<span data-ttu-id="08495-118">Bloco ou região</span><span class="sxs-lookup"><span data-stu-id="08495-118">Block or region</span></span>|<span data-ttu-id="08495-119">Ramificando de fora</span><span class="sxs-lookup"><span data-stu-id="08495-119">Branching in from outside</span></span>|<span data-ttu-id="08495-120">Ramificação de dentro</span><span class="sxs-lookup"><span data-stu-id="08495-120">Branching out from inside</span></span>|  
|---------------------|-------------------------------|-------------------------------|  
|<span data-ttu-id="08495-121">bloco de `Try`</span><span class="sxs-lookup"><span data-stu-id="08495-121">`Try` block</span></span>|<span data-ttu-id="08495-122">Somente de um bloco de `Catch` da mesma construção <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="08495-122">Only from a `Catch` block of the same construction <sup>1</sup></span></span>|<span data-ttu-id="08495-123">Somente para fora da construção inteira</span><span class="sxs-lookup"><span data-stu-id="08495-123">Only to outside the whole construction</span></span>|  
|<span data-ttu-id="08495-124">bloco de `Catch`</span><span class="sxs-lookup"><span data-stu-id="08495-124">`Catch` block</span></span>|<span data-ttu-id="08495-125">Nunca permitido</span><span class="sxs-lookup"><span data-stu-id="08495-125">Never allowed</span></span>|<span data-ttu-id="08495-126">Somente para fora da construção inteira ou para o bloco de `Try` da mesma construção <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="08495-126">Only to outside the whole construction, or to the `Try` block of the same construction <sup>1</sup></span></span>|  
|<span data-ttu-id="08495-127">bloco de `Finally`</span><span class="sxs-lookup"><span data-stu-id="08495-127">`Finally` block</span></span>|<span data-ttu-id="08495-128">Nunca permitido</span><span class="sxs-lookup"><span data-stu-id="08495-128">Never allowed</span></span>|<span data-ttu-id="08495-129">Nunca permitido</span><span class="sxs-lookup"><span data-stu-id="08495-129">Never allowed</span></span>|  
  
 <span data-ttu-id="08495-130"><sup>1</sup> se uma `Try`...`Catch`...`Finally` construção estiver aninhada dentro de outra, um bloco de `Catch` poderá ramificar no bloco de `Try` em seu próprio nível de aninhamento, mas não em qualquer outro bloco de `Try`.</span><span class="sxs-lookup"><span data-stu-id="08495-130"><sup>1</sup> If one `Try`...`Catch`...`Finally` construction is nested within another, a `Catch` block can branch into the `Try` block at its own nesting level, but not into any other `Try` block.</span></span> <span data-ttu-id="08495-131">Uma construção aninhada `Try`...`Catch`...`Finally` deve estar contida completamente em um bloco de `Try` ou `Catch` da construção dentro da qual está aninhada.</span><span class="sxs-lookup"><span data-stu-id="08495-131">A nested `Try`...`Catch`...`Finally` construction must be contained completely in a `Try` or `Catch` block of the construction within which it is nested.</span></span>  
  
 <span data-ttu-id="08495-132">A ilustração a seguir mostra um `Try` construção aninhada dentro de outro.</span><span class="sxs-lookup"><span data-stu-id="08495-132">The following illustration shows one `Try` construction nested within another.</span></span> <span data-ttu-id="08495-133">Várias ramificações entre os blocos das duas construções são indicadas como válidas ou inválidas.</span><span class="sxs-lookup"><span data-stu-id="08495-133">Various branches among the blocks of the two constructions are indicated as valid or invalid.</span></span>  
  
 ![Diagrama gráfico de ramificação em construções try](./media/goto-statement/try-construction-branching.gif)  
  
## <a name="example"></a><span data-ttu-id="08495-135">Exemplo</span><span class="sxs-lookup"><span data-stu-id="08495-135">Example</span></span>  
 <span data-ttu-id="08495-136">O exemplo a seguir usa a instrução `GoTo` para ramificar para rótulos de linha em um procedimento.</span><span class="sxs-lookup"><span data-stu-id="08495-136">The following example uses the `GoTo` statement to branch to line labels in a procedure.</span></span>  
  
 [!code-vb[VbVbalrStatements#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#31)]  
  
## <a name="see-also"></a><span data-ttu-id="08495-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="08495-137">See also</span></span>

- [<span data-ttu-id="08495-138">Instrução Do...Loop</span><span class="sxs-lookup"><span data-stu-id="08495-138">Do...Loop Statement</span></span>](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [<span data-ttu-id="08495-139">Instrução For...Next</span><span class="sxs-lookup"><span data-stu-id="08495-139">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [<span data-ttu-id="08495-140">Instrução For Each...Next</span><span class="sxs-lookup"><span data-stu-id="08495-140">For Each...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [<span data-ttu-id="08495-141">Instrução If...Then...Else</span><span class="sxs-lookup"><span data-stu-id="08495-141">If...Then...Else Statement</span></span>](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [<span data-ttu-id="08495-142">Instrução Select...Case</span><span class="sxs-lookup"><span data-stu-id="08495-142">Select...Case Statement</span></span>](../../../visual-basic/language-reference/statements/select-case-statement.md)
- [<span data-ttu-id="08495-143">Instrução Try...Catch...Finally</span><span class="sxs-lookup"><span data-stu-id="08495-143">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [<span data-ttu-id="08495-144">Instrução While...End While</span><span class="sxs-lookup"><span data-stu-id="08495-144">While...End While Statement</span></span>](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
- [<span data-ttu-id="08495-145">Instrução With ... End With</span><span class="sxs-lookup"><span data-stu-id="08495-145">With...End With Statement</span></span>](../../../visual-basic/language-reference/statements/with-end-with-statement.md)
