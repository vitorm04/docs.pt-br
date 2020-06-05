---
title: Estruturas de loop
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
ms.openlocfilehash: 3f60e9dc83dc7174e765903be13f2870ea40ce4c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403506"
---
# <a name="loop-structures-visual-basic"></a><span data-ttu-id="0c973-102">Estruturas de loop (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0c973-102">Loop Structures (Visual Basic)</span></span>
<span data-ttu-id="0c973-103">Estruturas de loop de Visual Basic permitem executar uma ou mais linhas de código repetidamente.</span><span class="sxs-lookup"><span data-stu-id="0c973-103">Visual Basic loop structures allow you to run one or more lines of code repetitively.</span></span> <span data-ttu-id="0c973-104">Você pode repetir as instruções em uma estrutura de loop até que uma condição seja `True` , até que uma condição seja `False` , um número especificado de vezes ou uma vez para cada elemento em uma coleção.</span><span class="sxs-lookup"><span data-stu-id="0c973-104">You can repeat the statements in a loop structure until a condition is `True`, until a condition is `False`, a specified number of times, or once for each element in a collection.</span></span>  
  
 <span data-ttu-id="0c973-105">A ilustração a seguir mostra uma estrutura de loop que executa um conjunto de instruções até que uma condição se torne verdadeira:</span><span class="sxs-lookup"><span data-stu-id="0c973-105">The following illustration shows a loop structure that runs a set of statements until a condition becomes true:</span></span>  
  
 ![Fluxograma que mostra um dos... Loop Until.](./media/loop-structures/do-until-loop-true-condition.gif)  
  
## <a name="while-loops"></a><span data-ttu-id="0c973-107">Loops while</span><span class="sxs-lookup"><span data-stu-id="0c973-107">While Loops</span></span>  
 <span data-ttu-id="0c973-108">A `While` construção... `End While` executa um conjunto de instruções desde que a condição especificada na `While` instrução seja `True` .</span><span class="sxs-lookup"><span data-stu-id="0c973-108">The `While`...`End While` construction runs a set of statements as long as the condition specified in the `While` statement is `True`.</span></span> <span data-ttu-id="0c973-109">Para obter mais informações, consulte [while... Instrução End While](../../../language-reference/statements/while-end-while-statement.md).</span><span class="sxs-lookup"><span data-stu-id="0c973-109">For more information, see [While...End While Statement](../../../language-reference/statements/while-end-while-statement.md).</span></span>  
  
## <a name="do-loops"></a><span data-ttu-id="0c973-110">Executar loops</span><span class="sxs-lookup"><span data-stu-id="0c973-110">Do Loops</span></span>  
 <span data-ttu-id="0c973-111">A `Do` construção... `Loop` permite testar uma condição no início ou no final de uma estrutura de loop.</span><span class="sxs-lookup"><span data-stu-id="0c973-111">The `Do`...`Loop` construction allows you to test a condition at either the beginning or the end of a loop structure.</span></span> <span data-ttu-id="0c973-112">Você também pode especificar se deseja repetir o loop enquanto a condição permanecer `True` ou até se tornar `True` .</span><span class="sxs-lookup"><span data-stu-id="0c973-112">You can also specify whether to repeat the loop while the condition remains `True` or until it becomes `True`.</span></span> <span data-ttu-id="0c973-113">Para obter mais informações, consulte [do... Instrução loop](../../../language-reference/statements/do-loop-statement.md).</span><span class="sxs-lookup"><span data-stu-id="0c973-113">For more information, see [Do...Loop Statement](../../../language-reference/statements/do-loop-statement.md).</span></span>  
  
## <a name="for-loops"></a><span data-ttu-id="0c973-114">Loops for</span><span class="sxs-lookup"><span data-stu-id="0c973-114">For Loops</span></span>  
 <span data-ttu-id="0c973-115">A `For` construção... `Next` executa o loop um número de vezes.</span><span class="sxs-lookup"><span data-stu-id="0c973-115">The `For`...`Next` construction performs the loop a set number of times.</span></span> <span data-ttu-id="0c973-116">Ele usa uma variável de controle de loop, também chamada de *contador*, para controlar as repetições.</span><span class="sxs-lookup"><span data-stu-id="0c973-116">It uses a loop control variable, also called a *counter*, to keep track of the repetitions.</span></span> <span data-ttu-id="0c973-117">Especifique os valores inicial e final para este contador e, opcionalmente, você pode especificar a quantidade pela qual ele aumenta de uma repetição para a próxima.</span><span class="sxs-lookup"><span data-stu-id="0c973-117">You specify the starting and ending values for this counter, and you can optionally specify the amount by which it increases from one repetition to the next.</span></span> <span data-ttu-id="0c973-118">Para obter mais informações, consulte [para... Próxima instrução](../../../language-reference/statements/for-next-statement.md).</span><span class="sxs-lookup"><span data-stu-id="0c973-118">For more information, see [For...Next Statement](../../../language-reference/statements/for-next-statement.md).</span></span>  
  
## <a name="for-each-loops"></a><span data-ttu-id="0c973-119">Para cada loop</span><span class="sxs-lookup"><span data-stu-id="0c973-119">For Each Loops</span></span>  
 <span data-ttu-id="0c973-120">A `For Each` construção... `Next` executa um conjunto de instruções uma vez para cada elemento em uma coleção.</span><span class="sxs-lookup"><span data-stu-id="0c973-120">The `For Each`...`Next` construction runs a set of statements once for each element in a collection.</span></span> <span data-ttu-id="0c973-121">Você especifica a variável de controle de loop, mas não precisa determinar os valores iniciais ou finais para ela.</span><span class="sxs-lookup"><span data-stu-id="0c973-121">You specify the loop control variable, but you do not have to determine starting or ending values for it.</span></span> <span data-ttu-id="0c973-122">Para obter mais informações, consulte [para cada... Próxima instrução](../../../language-reference/statements/for-each-next-statement.md).</span><span class="sxs-lookup"><span data-stu-id="0c973-122">For more information, see [For Each...Next Statement](../../../language-reference/statements/for-each-next-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c973-123">Confira também</span><span class="sxs-lookup"><span data-stu-id="0c973-123">See also</span></span>

- [<span data-ttu-id="0c973-124">Fluxo de controle</span><span class="sxs-lookup"><span data-stu-id="0c973-124">Control Flow</span></span>](index.md)
- [<span data-ttu-id="0c973-125">Estruturas de Decisão</span><span class="sxs-lookup"><span data-stu-id="0c973-125">Decision Structures</span></span>](decision-structures.md)
- [<span data-ttu-id="0c973-126">Outras Estruturas de Controle</span><span class="sxs-lookup"><span data-stu-id="0c973-126">Other Control Structures</span></span>](other-control-structures.md)
- [<span data-ttu-id="0c973-127">Estruturas de Controle Aninhadas</span><span class="sxs-lookup"><span data-stu-id="0c973-127">Nested Control Structures</span></span>](nested-control-structures.md)
