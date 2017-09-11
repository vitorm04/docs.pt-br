---
title: "Instrução GoTo | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.GoTo
dev_langs:
- VB
helpviewer_keywords:
- GoTo statement
- control flow, branching
- unconditional branching
- branching
- branching, unconditional
- branching, conditional
- conditional statements, GoTo statement
- GoTo statement, syntax
ms.assetid: 313274c2-8ab3-4b9c-9ba3-0fd6798e4f6d
caps.latest.revision: 19
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
ms.openlocfilehash: e43cf9580056062c523d977516b2bb2f9310ce78
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="goto-statement"></a><span data-ttu-id="b8509-102">Instrução GoTo</span><span class="sxs-lookup"><span data-stu-id="b8509-102">GoTo Statement</span></span>
<span data-ttu-id="b8509-103">Ramifica incondicionalmente para uma linha especificada em um procedimento.</span><span class="sxs-lookup"><span data-stu-id="b8509-103">Branches unconditionally to a specified line in a procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8509-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b8509-104">Syntax</span></span>  
  
```  
GoTo line  
```  
  
## <a name="part"></a><span data-ttu-id="b8509-105">Parte</span><span class="sxs-lookup"><span data-stu-id="b8509-105">Part</span></span>  
 `line`  
 <span data-ttu-id="b8509-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="b8509-106">Required.</span></span> <span data-ttu-id="b8509-107">Qualquer rótulo de linha.</span><span class="sxs-lookup"><span data-stu-id="b8509-107">Any line label.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b8509-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="b8509-108">Remarks</span></span>  
 <span data-ttu-id="b8509-109">O `GoTo` instrução pode ramificar somente a linhas no procedimento no qual ele aparece.</span><span class="sxs-lookup"><span data-stu-id="b8509-109">The `GoTo` statement can branch only to lines in the procedure in which it appears.</span></span> <span data-ttu-id="b8509-110">A linha deve ter uma linha de rótulo que `GoTo` pode consultar.</span><span class="sxs-lookup"><span data-stu-id="b8509-110">The line must have a line label that `GoTo` can refer to.</span></span> <span data-ttu-id="b8509-111">Para obter mais informações, consulte [como: Label Statements](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md).</span><span class="sxs-lookup"><span data-stu-id="b8509-111">For more information, see [How to: Label Statements](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b8509-112"> `GoTo`instruções podem dificultar a leitura e manutenção do código.</span><span class="sxs-lookup"><span data-stu-id="b8509-112"> `GoTo` statements can make code difficult to read and maintain.</span></span> <span data-ttu-id="b8509-113">Sempre que possível, use uma estrutura de controle.</span><span class="sxs-lookup"><span data-stu-id="b8509-113">Whenever possible, use a control structure instead.</span></span> <span data-ttu-id="b8509-114">Para obter mais informações, consulte [fluxo de controle](../../../visual-basic/programming-guide/language-features/control-flow/index.md).</span><span class="sxs-lookup"><span data-stu-id="b8509-114">For more information, see [Control Flow](../../../visual-basic/programming-guide/language-features/control-flow/index.md).</span></span>  
  
 <span data-ttu-id="b8509-115">Não é possível usar um `GoTo` instrução para ramificar de fora de um `For`... `Next`, `For Each`... `Next`, `SyncLock`... `End SyncLock`, `Try`... `Catch`... `Finally`, `With`... `End With`, or `Using`... `End Using` construção para um rótulo dentro.</span><span class="sxs-lookup"><span data-stu-id="b8509-115">You cannot use a `GoTo` statement to branch from outside a `For`...`Next`, `For Each`...`Next`, `SyncLock`...`End SyncLock`, `Try`...`Catch`...`Finally`, `With`...`End With`, or `Using`...`End Using` construction to a label inside.</span></span>  
  
## <a name="branching-and-try-constructions"></a><span data-ttu-id="b8509-116">Ramificações e construções Try</span><span class="sxs-lookup"><span data-stu-id="b8509-116">Branching and Try Constructions</span></span>  
 <span data-ttu-id="b8509-117">Dentro de um `Try`... `Catch`... `Finally` construção, as seguintes regras se aplicam a ramificação com o `GoTo` instrução.</span><span class="sxs-lookup"><span data-stu-id="b8509-117">Within a `Try`...`Catch`...`Finally` construction, the following rules apply to branching with the `GoTo` statement.</span></span>  
  
|<span data-ttu-id="b8509-118">Bloco ou região</span><span class="sxs-lookup"><span data-stu-id="b8509-118">Block or region</span></span>|<span data-ttu-id="b8509-119">Ramificação em de fora</span><span class="sxs-lookup"><span data-stu-id="b8509-119">Branching in from outside</span></span>|<span data-ttu-id="b8509-120">Ramificação fora de dentro</span><span class="sxs-lookup"><span data-stu-id="b8509-120">Branching out from inside</span></span>|  
|---------------------|-------------------------------|-------------------------------|  
|<span data-ttu-id="b8509-121">`Try`bloco</span><span class="sxs-lookup"><span data-stu-id="b8509-121">`Try` block</span></span>|<span data-ttu-id="b8509-122">Somente de um `Catch` bloco de construção mesmo <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="b8509-122">Only from a `Catch` block of the same construction <sup>1</sup></span></span>|<span data-ttu-id="b8509-123">Somente para fora da construção inteira</span><span class="sxs-lookup"><span data-stu-id="b8509-123">Only to outside the whole construction</span></span>|  
|<span data-ttu-id="b8509-124">`Catch`bloco</span><span class="sxs-lookup"><span data-stu-id="b8509-124">`Catch` block</span></span>|<span data-ttu-id="b8509-125">Nunca permitidos</span><span class="sxs-lookup"><span data-stu-id="b8509-125">Never allowed</span></span>|<span data-ttu-id="b8509-126">Somente para fora da construção inteira ou para o `Try` bloco de construção mesmo <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="b8509-126">Only to outside the whole construction, or to the `Try` block of the same construction <sup>1</sup></span></span>|  
|<span data-ttu-id="b8509-127">`Finally`bloco</span><span class="sxs-lookup"><span data-stu-id="b8509-127">`Finally` block</span></span>|<span data-ttu-id="b8509-128">Nunca permitidos</span><span class="sxs-lookup"><span data-stu-id="b8509-128">Never allowed</span></span>|<span data-ttu-id="b8509-129">Nunca permitidos</span><span class="sxs-lookup"><span data-stu-id="b8509-129">Never allowed</span></span>|  
  
 <span data-ttu-id="b8509-130"><sup>1</sup> If one `Try`... `Catch`... `Finally` está aninhada em outra, uma `Catch` bloco pode ramificar para o `Try` bloco no seu próprio nível de aninhamento, mas não para qualquer outro `Try` bloco.</span><span class="sxs-lookup"><span data-stu-id="b8509-130"><sup>1</sup> If one `Try`...`Catch`...`Finally` construction is nested within another, a `Catch` block can branch into the `Try` block at its own nesting level, but not into any other `Try` block.</span></span> <span data-ttu-id="b8509-131">Uma construção `Try`... `Catch`... `Finally` aninhada deve estar contida completamente em um `Try` ou `Catch` bloco de construção dentro da qual está aninhada.</span><span class="sxs-lookup"><span data-stu-id="b8509-131">A nested `Try`...`Catch`...`Finally` construction must be contained completely in a `Try` or `Catch` block of the construction within which it is nested.</span></span>  
  
 <span data-ttu-id="b8509-132">A ilustração a seguir mostra uma `Try` aninhada em outra.</span><span class="sxs-lookup"><span data-stu-id="b8509-132">The following illustration shows one `Try` construction nested within another.</span></span> <span data-ttu-id="b8509-133">Várias ramificações entre os blocos das duas construções são indicadas como válidas ou inválidas.</span><span class="sxs-lookup"><span data-stu-id="b8509-133">Various branches among the blocks of the two constructions are indicated as valid or invalid.</span></span>  
  
 <span data-ttu-id="b8509-134">![Diagrama gráfico de ramificações em construções Try](../../../visual-basic/language-reference/statements/media/trybranching.gif "TryBranching")</span><span class="sxs-lookup"><span data-stu-id="b8509-134">![Graphic diagram of branching in Try constructions](../../../visual-basic/language-reference/statements/media/trybranching.gif "TryBranching")</span></span>  
<span data-ttu-id="b8509-135">Ramificações válidas e inválidas em construções Try</span><span class="sxs-lookup"><span data-stu-id="b8509-135">Valid and invalid branches in Try constructions</span></span>  
  
## <a name="example"></a><span data-ttu-id="b8509-136">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b8509-136">Example</span></span>  
 <span data-ttu-id="b8509-137">O exemplo a seguir usa o `GoTo` instrução para ramificar para rótulos de linha em um procedimento.</span><span class="sxs-lookup"><span data-stu-id="b8509-137">The following example uses the `GoTo` statement to branch to line labels in a procedure.</span></span>  
  
 <span data-ttu-id="b8509-138">[!code-vb[VbVbalrStatements&#31;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/goto-statement_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="b8509-138">[!code-vb[VbVbalrStatements#31](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/goto-statement_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8509-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b8509-139">See Also</span></span>  
 <span data-ttu-id="b8509-140">[Fazer... Instrução loop](../../../visual-basic/language-reference/statements/do-loop-statement.md) </span><span class="sxs-lookup"><span data-stu-id="b8509-140">[Do...Loop Statement](../../../visual-basic/language-reference/statements/do-loop-statement.md) </span></span>  
<span data-ttu-id="b8509-141"> [Para... Próxima instrução](../../../visual-basic/language-reference/statements/for-next-statement.md) </span><span class="sxs-lookup"><span data-stu-id="b8509-141"> [For...Next Statement](../../../visual-basic/language-reference/statements/for-next-statement.md) </span></span>  
<span data-ttu-id="b8509-142"> [Para cada um... Próxima instrução](../../../visual-basic/language-reference/statements/for-each-next-statement.md) </span><span class="sxs-lookup"><span data-stu-id="b8509-142"> [For Each...Next Statement](../../../visual-basic/language-reference/statements/for-each-next-statement.md) </span></span>  
<span data-ttu-id="b8509-143"> [If... Then... Instrução else](../../../visual-basic/language-reference/statements/if-then-else-statement.md) </span><span class="sxs-lookup"><span data-stu-id="b8509-143"> [If...Then...Else Statement](../../../visual-basic/language-reference/statements/if-then-else-statement.md) </span></span>  
<span data-ttu-id="b8509-144"> [Selecione... Instrução Case](../../../visual-basic/language-reference/statements/select-case-statement.md) </span><span class="sxs-lookup"><span data-stu-id="b8509-144"> [Select...Case Statement](../../../visual-basic/language-reference/statements/select-case-statement.md) </span></span>  
<span data-ttu-id="b8509-145"> [Instrução Try...Catch...Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md) </span><span class="sxs-lookup"><span data-stu-id="b8509-145"> [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md) </span></span>  
<span data-ttu-id="b8509-146"> [While... End While Statement](../../../visual-basic/language-reference/statements/while-end-while-statement.md) </span><span class="sxs-lookup"><span data-stu-id="b8509-146"> [While...End While Statement](../../../visual-basic/language-reference/statements/while-end-while-statement.md) </span></span>  
<span data-ttu-id="b8509-147"> [Instrução With ... End With](../../../visual-basic/language-reference/statements/with-end-with-statement.md)</span><span class="sxs-lookup"><span data-stu-id="b8509-147"> [With...End With Statement](../../../visual-basic/language-reference/statements/with-end-with-statement.md)</span></span>
