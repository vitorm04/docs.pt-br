---
title: Loop de estruturas (Visual Basic) | Documentos do Microsoft
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- control flow, loops
- For keyword [Visual Basic], loop structures
- loops
- loop structures
- statements [Visual Basic], loop
- Do statement, Do loops
- conditional statements, loop structures
ms.assetid: ecacb09b-a4c9-42be-98b2-a15d368b5db8
caps.latest.revision: 18
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
ms.openlocfilehash: eba728d782bb5a6259467fb48f738f35580049c0
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="loop-structures-visual-basic"></a><span data-ttu-id="a3c32-102">Estruturas de loop (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a3c32-102">Loop Structures (Visual Basic)</span></span>
[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="a3c32-103">estruturas de loop permitem que você execute uma ou mais linhas de código repetidamente.</span><span class="sxs-lookup"><span data-stu-id="a3c32-103"> loop structures allow you to run one or more lines of code repetitively.</span></span> <span data-ttu-id="a3c32-104">Você pode repetir as instruções em uma estrutura de loop até que uma condição seja `True`, até que uma condição seja `False`, um especificado o número de vezes ou uma vez para cada elemento em uma coleção.</span><span class="sxs-lookup"><span data-stu-id="a3c32-104">You can repeat the statements in a loop structure until a condition is `True`, until a condition is `False`, a specified number of times, or once for each element in a collection.</span></span>  
  
 <span data-ttu-id="a3c32-105">A ilustração a seguir mostra uma estrutura de loop que executa um conjunto de instruções até que uma condição for verdadeira.</span><span class="sxs-lookup"><span data-stu-id="a3c32-105">The following illustration shows a loop structure that runs a set of statements until a condition becomes true.</span></span>  
  
 <span data-ttu-id="a3c32-106">![Gráfico de fluxo de um... Até que o loop](../../../../visual-basic/programming-guide/language-features/control-flow/media/dountilloop.gif "DoUntilLoop")</span><span class="sxs-lookup"><span data-stu-id="a3c32-106">![Flow chart of a Do...Until loop](../../../../visual-basic/programming-guide/language-features/control-flow/media/dountilloop.gif "DoUntilLoop")</span></span>  
<span data-ttu-id="a3c32-107">Execução de um conjunto de instruções até que uma condição for verdadeira</span><span class="sxs-lookup"><span data-stu-id="a3c32-107">Running a set of statements until a condition becomes true</span></span>  
  
## <a name="while-loops"></a><span data-ttu-id="a3c32-108">Embora Loops</span><span class="sxs-lookup"><span data-stu-id="a3c32-108">While Loops</span></span>  
 <span data-ttu-id="a3c32-109">The `While`... `End While` construção executa um conjunto de instruções enquanto a condição especificada no `While` instrução é `True`.</span><span class="sxs-lookup"><span data-stu-id="a3c32-109">The `While`...`End While` construction runs a set of statements as long as the condition specified in the `While` statement is `True`.</span></span> <span data-ttu-id="a3c32-110">Para obter mais informações, consulte [enquanto... End While Statement](../../../../visual-basic/language-reference/statements/while-end-while-statement.md).</span><span class="sxs-lookup"><span data-stu-id="a3c32-110">For more information, see [While...End While Statement](../../../../visual-basic/language-reference/statements/while-end-while-statement.md).</span></span>  
  
## <a name="do-loops"></a><span data-ttu-id="a3c32-111">Fazer Loops</span><span class="sxs-lookup"><span data-stu-id="a3c32-111">Do Loops</span></span>  
 <span data-ttu-id="a3c32-112">The `Do`... `Loop` construção permite testar uma condição no início ou no final de uma estrutura de loop.</span><span class="sxs-lookup"><span data-stu-id="a3c32-112">The `Do`...`Loop` construction allows you to test a condition at either the beginning or the end of a loop structure.</span></span> <span data-ttu-id="a3c32-113">Você também pode especificar se deseja repetir o loop, enquanto a condição permanecer `True` ou até que ele fique `True`.</span><span class="sxs-lookup"><span data-stu-id="a3c32-113">You can also specify whether to repeat the loop while the condition remains `True` or until it becomes `True`.</span></span> <span data-ttu-id="a3c32-114">Para obter mais informações, consulte [fazer... Loop Statement](../../../../visual-basic/language-reference/statements/do-loop-statement.md).</span><span class="sxs-lookup"><span data-stu-id="a3c32-114">For more information, see [Do...Loop Statement](../../../../visual-basic/language-reference/statements/do-loop-statement.md).</span></span>  
  
## <a name="for-loops"></a><span data-ttu-id="a3c32-115">Loops</span><span class="sxs-lookup"><span data-stu-id="a3c32-115">For Loops</span></span>  
 <span data-ttu-id="a3c32-116">The `For`... `Next` construção executa loop um determinado número de vezes.</span><span class="sxs-lookup"><span data-stu-id="a3c32-116">The `For`...`Next` construction performs the loop a set number of times.</span></span> <span data-ttu-id="a3c32-117">Ele usa uma variável de controle de loop, também chamada de um *contador*, para controlar as repetições.</span><span class="sxs-lookup"><span data-stu-id="a3c32-117">It uses a loop control variable, also called a *counter*, to keep track of the repetitions.</span></span> <span data-ttu-id="a3c32-118">Especifique os valores inicial e final para esse contador e, opcionalmente, você pode especificar a quantidade pela qual ele aumenta de uma repetição para a próxima.</span><span class="sxs-lookup"><span data-stu-id="a3c32-118">You specify the starting and ending values for this counter, and you can optionally specify the amount by which it increases from one repetition to the next.</span></span> <span data-ttu-id="a3c32-119">Para obter mais informações, consulte [para... Próxima instrução](../../../../visual-basic/language-reference/statements/for-next-statement.md).</span><span class="sxs-lookup"><span data-stu-id="a3c32-119">For more information, see [For...Next Statement](../../../../visual-basic/language-reference/statements/for-next-statement.md).</span></span>  
  
## <a name="for-each-loops"></a><span data-ttu-id="a3c32-120">Loops For Each</span><span class="sxs-lookup"><span data-stu-id="a3c32-120">For Each Loops</span></span>  
 <span data-ttu-id="a3c32-121">The `For Each`... `Next` construção executa um conjunto de instruções uma vez para cada elemento em uma coleção.</span><span class="sxs-lookup"><span data-stu-id="a3c32-121">The `For Each`...`Next` construction runs a set of statements once for each element in a collection.</span></span> <span data-ttu-id="a3c32-122">Especifique a variável de controle de loop, mas você não precisa determinar inicial ou final valores para ele.</span><span class="sxs-lookup"><span data-stu-id="a3c32-122">You specify the loop control variable, but you do not have to determine starting or ending values for it.</span></span> <span data-ttu-id="a3c32-123">Para obter mais informações, consulte [para cada uma... Próxima instrução](../../../../visual-basic/language-reference/statements/for-each-next-statement.md).</span><span class="sxs-lookup"><span data-stu-id="a3c32-123">For more information, see [For Each...Next Statement](../../../../visual-basic/language-reference/statements/for-each-next-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3c32-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a3c32-124">See Also</span></span>  
 <span data-ttu-id="a3c32-125">[Fluxo de controle](../../../../visual-basic/programming-guide/language-features/control-flow/index.md) </span><span class="sxs-lookup"><span data-stu-id="a3c32-125">[Control Flow](../../../../visual-basic/programming-guide/language-features/control-flow/index.md) </span></span>  
<span data-ttu-id="a3c32-126"> [Estruturas de decisão](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md) </span><span class="sxs-lookup"><span data-stu-id="a3c32-126"> [Decision Structures](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md) </span></span>  
<span data-ttu-id="a3c32-127"> [Outras estruturas de controle](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md) </span><span class="sxs-lookup"><span data-stu-id="a3c32-127"> [Other Control Structures](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md) </span></span>  
<span data-ttu-id="a3c32-128"> [Estruturas de Controle Aninhadas](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)</span><span class="sxs-lookup"><span data-stu-id="a3c32-128"> [Nested Control Structures](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)</span></span>
