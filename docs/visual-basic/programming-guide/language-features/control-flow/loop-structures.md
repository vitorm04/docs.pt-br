---
title: Estruturas de loop (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- control flow [Visual Basic], loops
- For keyword [Visual Basic], loop structures
- loops
- loop structures [Visual Basic]
- statements [Visual Basic], loop
- Do statement [Visual Basic], Do loops
- conditional statements [Visual Basic], loop structures
ms.assetid: ecacb09b-a4c9-42be-98b2-a15d368b5db8
ms.openlocfilehash: b72eef632b4564abc69e6ebef43b940eb0950e9a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54523383"
---
# <a name="loop-structures-visual-basic"></a><span data-ttu-id="e93ff-102">Estruturas de loop (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e93ff-102">Loop Structures (Visual Basic)</span></span>
<span data-ttu-id="e93ff-103">Estruturas de loop do Visual Basic permitem que você execute uma ou mais linhas de código repetidamente.</span><span class="sxs-lookup"><span data-stu-id="e93ff-103">Visual Basic loop structures allow you to run one or more lines of code repetitively.</span></span> <span data-ttu-id="e93ff-104">Você pode repetir as instruções em uma estrutura de loop até que uma condição for `True`, até que uma condição é `False`, um especificado o número de vezes ou uma vez para cada elemento em uma coleção.</span><span class="sxs-lookup"><span data-stu-id="e93ff-104">You can repeat the statements in a loop structure until a condition is `True`, until a condition is `False`, a specified number of times, or once for each element in a collection.</span></span>  
  
 <span data-ttu-id="e93ff-105">A ilustração a seguir mostra uma estrutura de loop que executa um conjunto de instruções até que uma condição for verdadeira.</span><span class="sxs-lookup"><span data-stu-id="e93ff-105">The following illustration shows a loop structure that runs a set of statements until a condition becomes true.</span></span>  
  
 <span data-ttu-id="e93ff-106">![Gráfico de fluxo de um, faça... Loop Until](../../../../visual-basic/programming-guide/language-features/control-flow/media/dountilloop.gif "DoUntilLoop")</span><span class="sxs-lookup"><span data-stu-id="e93ff-106">![Flow chart of a Do...Until loop](../../../../visual-basic/programming-guide/language-features/control-flow/media/dountilloop.gif "DoUntilLoop")</span></span>  
<span data-ttu-id="e93ff-107">Execução de um conjunto de instruções até que uma condição for verdadeira</span><span class="sxs-lookup"><span data-stu-id="e93ff-107">Running a set of statements until a condition becomes true</span></span>  
  
## <a name="while-loops"></a><span data-ttu-id="e93ff-108">Embora os Loops</span><span class="sxs-lookup"><span data-stu-id="e93ff-108">While Loops</span></span>  
 <span data-ttu-id="e93ff-109">O `While`... `End While` construção executa um conjunto de instruções desde que a condição especificada em de `While` instrução é `True`.</span><span class="sxs-lookup"><span data-stu-id="e93ff-109">The `While`...`End While` construction runs a set of statements as long as the condition specified in the `While` statement is `True`.</span></span> <span data-ttu-id="e93ff-110">Para obter mais informações, consulte [enquanto... Finalizar instrução While](../../../../visual-basic/language-reference/statements/while-end-while-statement.md).</span><span class="sxs-lookup"><span data-stu-id="e93ff-110">For more information, see [While...End While Statement](../../../../visual-basic/language-reference/statements/while-end-while-statement.md).</span></span>  
  
## <a name="do-loops"></a><span data-ttu-id="e93ff-111">Fazer Loops</span><span class="sxs-lookup"><span data-stu-id="e93ff-111">Do Loops</span></span>  
 <span data-ttu-id="e93ff-112">O `Do`... `Loop` construção permite testar uma condição no início ou final de uma estrutura de loop.</span><span class="sxs-lookup"><span data-stu-id="e93ff-112">The `Do`...`Loop` construction allows you to test a condition at either the beginning or the end of a loop structure.</span></span> <span data-ttu-id="e93ff-113">Você também pode especificar se deseja repetir o loop, enquanto a condição permaneça `True` ou até que ele se torne `True`.</span><span class="sxs-lookup"><span data-stu-id="e93ff-113">You can also specify whether to repeat the loop while the condition remains `True` or until it becomes `True`.</span></span> <span data-ttu-id="e93ff-114">Para obter mais informações, consulte [fazer... Instrução de loop](../../../../visual-basic/language-reference/statements/do-loop-statement.md).</span><span class="sxs-lookup"><span data-stu-id="e93ff-114">For more information, see [Do...Loop Statement](../../../../visual-basic/language-reference/statements/do-loop-statement.md).</span></span>  
  
## <a name="for-loops"></a><span data-ttu-id="e93ff-115">Loops for</span><span class="sxs-lookup"><span data-stu-id="e93ff-115">For Loops</span></span>  
 <span data-ttu-id="e93ff-116">O `For`... `Next` construção executa o loop de um determinado número de vezes.</span><span class="sxs-lookup"><span data-stu-id="e93ff-116">The `For`...`Next` construction performs the loop a set number of times.</span></span> <span data-ttu-id="e93ff-117">Ele usa uma variável de controle de loop, também chamada de um *contador*, para acompanhar as repetições.</span><span class="sxs-lookup"><span data-stu-id="e93ff-117">It uses a loop control variable, also called a *counter*, to keep track of the repetitions.</span></span> <span data-ttu-id="e93ff-118">Especifique os valores inicial e final para este contador e, opcionalmente, você pode especificar a quantidade pela qual ele aumenta de uma repetição para a próxima.</span><span class="sxs-lookup"><span data-stu-id="e93ff-118">You specify the starting and ending values for this counter, and you can optionally specify the amount by which it increases from one repetition to the next.</span></span> <span data-ttu-id="e93ff-119">Para obter mais informações, consulte [para... Próxima instrução](../../../../visual-basic/language-reference/statements/for-next-statement.md).</span><span class="sxs-lookup"><span data-stu-id="e93ff-119">For more information, see [For...Next Statement](../../../../visual-basic/language-reference/statements/for-next-statement.md).</span></span>  
  
## <a name="for-each-loops"></a><span data-ttu-id="e93ff-120">Loops For Each</span><span class="sxs-lookup"><span data-stu-id="e93ff-120">For Each Loops</span></span>  
 <span data-ttu-id="e93ff-121">O `For Each`... `Next` construção executa um conjunto de instruções uma vez para cada elemento em uma coleção.</span><span class="sxs-lookup"><span data-stu-id="e93ff-121">The `For Each`...`Next` construction runs a set of statements once for each element in a collection.</span></span> <span data-ttu-id="e93ff-122">Especifique a variável de controle de loop, mas não é preciso determinar inicial ou final de valores para ele.</span><span class="sxs-lookup"><span data-stu-id="e93ff-122">You specify the loop control variable, but you do not have to determine starting or ending values for it.</span></span> <span data-ttu-id="e93ff-123">Para obter mais informações, consulte [para cada um... Próxima instrução](../../../../visual-basic/language-reference/statements/for-each-next-statement.md).</span><span class="sxs-lookup"><span data-stu-id="e93ff-123">For more information, see [For Each...Next Statement](../../../../visual-basic/language-reference/statements/for-each-next-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e93ff-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e93ff-124">See also</span></span>
- [<span data-ttu-id="e93ff-125">Fluxo de Controle</span><span class="sxs-lookup"><span data-stu-id="e93ff-125">Control Flow</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [<span data-ttu-id="e93ff-126">Estruturas de Decisão</span><span class="sxs-lookup"><span data-stu-id="e93ff-126">Decision Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)
- [<span data-ttu-id="e93ff-127">Outras Estruturas de Controle</span><span class="sxs-lookup"><span data-stu-id="e93ff-127">Other Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)
- [<span data-ttu-id="e93ff-128">Estruturas de Controle Aninhadas</span><span class="sxs-lookup"><span data-stu-id="e93ff-128">Nested Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
