---
title: Estruturas de decisão (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- statements [Visual Basic], control flow
- If statement [Visual Basic], decision structures
- If statement [Visual Basic], If...Then...Else
- control flow [Visual Basic], decision structures
- decision structures [Visual Basic]
- conditional statements [Visual Basic], decision structures
ms.assetid: 2e2e0895-4483-442a-b17c-26aead751ec2
ms.openlocfilehash: 4a76b2565c343e69ac3c11441035a7682a8f08ec
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61906992"
---
# <a name="decision-structures-visual-basic"></a><span data-ttu-id="b4de3-102">Estruturas de decisão (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b4de3-102">Decision Structures (Visual Basic)</span></span>
<span data-ttu-id="b4de3-103">Visual Basic permite testar condições e executar operações diferentes dependendo dos resultados do teste.</span><span class="sxs-lookup"><span data-stu-id="b4de3-103">Visual Basic lets you test conditions and perform different operations depending on the results of that test.</span></span> <span data-ttu-id="b4de3-104">Você pode testar uma condição ser verdadeira ou falsa para vários valores de uma expressão, ou para várias exceções geradas quando você executa uma série de instruções.</span><span class="sxs-lookup"><span data-stu-id="b4de3-104">You can test for a condition being true or false, for various values of an expression, or for various exceptions generated when you execute a series of statements.</span></span>  
  
 <span data-ttu-id="b4de3-105">A ilustração a seguir mostra uma estrutura de decisão que testa uma condição ser verdadeira e executa ações diferentes dependendo se ele for verdadeiro ou falso.</span><span class="sxs-lookup"><span data-stu-id="b4de3-105">The following illustration shows a decision structure that tests for a condition being true and takes different actions depending on whether it is true or false.</span></span>  
  
 ![Um gráfico de fluxo de uma instrução If... Then... Outra construção.](./media/decision-structures/if-then-else-construction.gif)  
  
## <a name="ifthenelse-construction"></a><span data-ttu-id="b4de3-107">If... Then... Outra construção</span><span class="sxs-lookup"><span data-stu-id="b4de3-107">If...Then...Else Construction</span></span>  
 <span data-ttu-id="b4de3-108">`If...Then...Else` construções permitem que você teste para uma ou mais condições e executar uma ou mais instruções, dependendo de cada condição.</span><span class="sxs-lookup"><span data-stu-id="b4de3-108">`If...Then...Else` constructions let you test for one or more conditions and run one or more statements depending on each condition.</span></span> <span data-ttu-id="b4de3-109">Você pode testar condições e tomar ações das seguintes maneiras:</span><span class="sxs-lookup"><span data-stu-id="b4de3-109">You can test conditions and take actions in the following ways:</span></span>  
  
- <span data-ttu-id="b4de3-110">Executar uma ou mais instruções, se uma condição for `True`</span><span class="sxs-lookup"><span data-stu-id="b4de3-110">Run one or more statements if a condition is `True`</span></span>  
  
- <span data-ttu-id="b4de3-111">Executar uma ou mais instruções, se uma condição for `False`</span><span class="sxs-lookup"><span data-stu-id="b4de3-111">Run one or more statements if a condition is `False`</span></span>  
  
- <span data-ttu-id="b4de3-112">Execute algumas declarações se uma condição for `True` e outras pessoas se ele for `False`</span><span class="sxs-lookup"><span data-stu-id="b4de3-112">Run some statements if a condition is `True` and others if it is `False`</span></span>  
  
- <span data-ttu-id="b4de3-113">Testar uma condição adicional se uma condição anterior for `False`</span><span class="sxs-lookup"><span data-stu-id="b4de3-113">Test an additional condition if a prior condition is `False`</span></span>  
  
 <span data-ttu-id="b4de3-114">A estrutura de controle que oferece todas essas possibilidades é o [se... Then... Instrução else](../../../../visual-basic/language-reference/statements/if-then-else-statement.md).</span><span class="sxs-lookup"><span data-stu-id="b4de3-114">The control structure that offers all these possibilities is the [If...Then...Else Statement](../../../../visual-basic/language-reference/statements/if-then-else-statement.md).</span></span> <span data-ttu-id="b4de3-115">Você pode usar uma versão de linha única, se você tiver apenas um teste e uma única instrução para executar.</span><span class="sxs-lookup"><span data-stu-id="b4de3-115">You can use a single-line version if you have just one test and one statement to run.</span></span> <span data-ttu-id="b4de3-116">Se você tiver um conjunto mais complexo de condições e ações, você pode usar a versão de várias linhas.</span><span class="sxs-lookup"><span data-stu-id="b4de3-116">If you have a more complex set of conditions and actions, you can use the multiple-line version.</span></span>  
  
## <a name="selectcase-construction"></a><span data-ttu-id="b4de3-117">Selecione... Construção de caso</span><span class="sxs-lookup"><span data-stu-id="b4de3-117">Select...Case Construction</span></span>  
 <span data-ttu-id="b4de3-118">O `Select...Case` construção permite que você avalie uma expressão de uma vez e executar diferentes conjuntos de instruções com base em diferentes valores possíveis.</span><span class="sxs-lookup"><span data-stu-id="b4de3-118">The `Select...Case` construction lets you evaluate an expression one time and run different sets of statements based on different possible values.</span></span> <span data-ttu-id="b4de3-119">Para obter mais informações, consulte [selecione... Instrução de caso](../../../../visual-basic/language-reference/statements/select-case-statement.md).</span><span class="sxs-lookup"><span data-stu-id="b4de3-119">For more information, see [Select...Case Statement](../../../../visual-basic/language-reference/statements/select-case-statement.md).</span></span>  
  
## <a name="trycatchfinally-construction"></a><span data-ttu-id="b4de3-120">Try... Catch... Por fim, construção</span><span class="sxs-lookup"><span data-stu-id="b4de3-120">Try...Catch...Finally Construction</span></span>  
 <span data-ttu-id="b4de3-121">`Try...Catch...Finally` permitem executar um conjunto de instruções em um ambiente que mantém o controle se alguma de suas declarações causa uma exceção.</span><span class="sxs-lookup"><span data-stu-id="b4de3-121">`Try...Catch...Finally` constructions let you run a set of statements under an environment that retains control if any one of your statements causes an exception.</span></span> <span data-ttu-id="b4de3-122">Você pode executar ações diferentes para diferentes exceções.</span><span class="sxs-lookup"><span data-stu-id="b4de3-122">You can take different actions for different exceptions.</span></span> <span data-ttu-id="b4de3-123">Opcionalmente, você pode especificar um bloco de código que é executado antes que você sai da `Try...Catch...Finally` construção, independentemente do que ocorre.</span><span class="sxs-lookup"><span data-stu-id="b4de3-123">You can optionally specify a block of code that runs before you exit the whole `Try...Catch...Finally` construction, regardless of what occurs.</span></span> <span data-ttu-id="b4de3-124">Para obter mais informações, consulte [Instrução Try...Catch...Finally](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="b4de3-124">For more information, see [Try...Catch...Finally Statement](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b4de3-125">Para muitas estruturas de controle, quando você clica em uma palavra-chave, todas as palavras-chave na estrutura são realçadas.</span><span class="sxs-lookup"><span data-stu-id="b4de3-125">For many control structures, when you click a keyword, all of the keywords in the structure are highlighted.</span></span> <span data-ttu-id="b4de3-126">Por exemplo, quando você clica `If` em um `If...Then...Else` construção, todas as instâncias do `If`, `Then`, `ElseIf`, `Else`, e `End If` na construção são realçadas.</span><span class="sxs-lookup"><span data-stu-id="b4de3-126">For instance, when you click `If` in an `If...Then...Else` construction, all instances of `If`, `Then`, `ElseIf`, `Else`, and `End If` in the construction are highlighted.</span></span> <span data-ttu-id="b4de3-127">Para mover para a palavra-chave a seguinte ou anterior, pressione CTRL + SHIFT + seta abaixo ou CTRL + SHIFT + seta acima.</span><span class="sxs-lookup"><span data-stu-id="b4de3-127">To move to the next or previous highlighted keyword, press CTRL+SHIFT+DOWN ARROW or CTRL+SHIFT+UP ARROW.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4de3-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b4de3-128">See also</span></span>

- [<span data-ttu-id="b4de3-129">Fluxo de Controle</span><span class="sxs-lookup"><span data-stu-id="b4de3-129">Control Flow</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [<span data-ttu-id="b4de3-130">Estruturas de Loop</span><span class="sxs-lookup"><span data-stu-id="b4de3-130">Loop Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [<span data-ttu-id="b4de3-131">Outras Estruturas de Controle</span><span class="sxs-lookup"><span data-stu-id="b4de3-131">Other Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)
- [<span data-ttu-id="b4de3-132">Estruturas de Controle Aninhadas</span><span class="sxs-lookup"><span data-stu-id="b4de3-132">Nested Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [<span data-ttu-id="b4de3-133">Operador If</span><span class="sxs-lookup"><span data-stu-id="b4de3-133">If Operator</span></span>](../../../../visual-basic/language-reference/operators/if-operator.md)
