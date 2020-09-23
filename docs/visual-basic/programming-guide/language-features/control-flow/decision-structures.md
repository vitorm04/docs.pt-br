---
title: Estruturas de decisão
ms.date: 07/20/2015
helpviewer_keywords:
- statements [Visual Basic], control flow
- If statement [Visual Basic], decision structures
- If statement [Visual Basic], If...Then...Else
- control flow [Visual Basic], decision structures
- decision structures [Visual Basic]
- conditional statements [Visual Basic], decision structures
ms.assetid: 2e2e0895-4483-442a-b17c-26aead751ec2
ms.openlocfilehash: 79c4949cd4d5b07d1b1d666b21467bf8db41ab3d
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91095610"
---
# <a name="decision-structures-visual-basic"></a><span data-ttu-id="f57f4-102">Estruturas de decisão (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f57f4-102">Decision Structures (Visual Basic)</span></span>

<span data-ttu-id="f57f4-103">Visual Basic permite testar condições e executar operações diferentes dependendo dos resultados desse teste.</span><span class="sxs-lookup"><span data-stu-id="f57f4-103">Visual Basic lets you test conditions and perform different operations depending on the results of that test.</span></span> <span data-ttu-id="f57f4-104">Você pode testar se uma condição é verdadeira ou falsa, para vários valores de uma expressão ou para várias exceções geradas quando você executa uma série de instruções.</span><span class="sxs-lookup"><span data-stu-id="f57f4-104">You can test for a condition being true or false, for various values of an expression, or for various exceptions generated when you execute a series of statements.</span></span>  
  
 <span data-ttu-id="f57f4-105">A ilustração a seguir mostra uma estrutura de decisão que testa se uma condição é verdadeira e executa ações diferentes dependendo se ela é verdadeira ou falsa.</span><span class="sxs-lookup"><span data-stu-id="f57f4-105">The following illustration shows a decision structure that tests for a condition being true and takes different actions depending on whether it is true or false.</span></span>  
  
 ![Um gráfico de fluxo de um if... Então... Outra construção.](./media/decision-structures/if-then-else-construction.gif)  
  
## <a name="ifthenelse-construction"></a><span data-ttu-id="f57f4-107">Se... Então... Construção else</span><span class="sxs-lookup"><span data-stu-id="f57f4-107">If...Then...Else Construction</span></span>  

 <span data-ttu-id="f57f4-108">`If...Then...Else` as construções permitem testar uma ou mais condições e executar uma ou mais instruções, dependendo de cada condição.</span><span class="sxs-lookup"><span data-stu-id="f57f4-108">`If...Then...Else` constructions let you test for one or more conditions and run one or more statements depending on each condition.</span></span> <span data-ttu-id="f57f4-109">Você pode testar condições e executar ações das seguintes maneiras:</span><span class="sxs-lookup"><span data-stu-id="f57f4-109">You can test conditions and take actions in the following ways:</span></span>  
  
- <span data-ttu-id="f57f4-110">Executar uma ou mais instruções se uma condição for `True`</span><span class="sxs-lookup"><span data-stu-id="f57f4-110">Run one or more statements if a condition is `True`</span></span>  
  
- <span data-ttu-id="f57f4-111">Executar uma ou mais instruções se uma condição for `False`</span><span class="sxs-lookup"><span data-stu-id="f57f4-111">Run one or more statements if a condition is `False`</span></span>  
  
- <span data-ttu-id="f57f4-112">Executar algumas instruções se uma condição for `True` e outras se for `False`</span><span class="sxs-lookup"><span data-stu-id="f57f4-112">Run some statements if a condition is `True` and others if it is `False`</span></span>  
  
- <span data-ttu-id="f57f4-113">Testar uma condição adicional se uma condição anterior for `False`</span><span class="sxs-lookup"><span data-stu-id="f57f4-113">Test an additional condition if a prior condition is `False`</span></span>  
  
 <span data-ttu-id="f57f4-114">A estrutura de controle que oferece todas essas possibilidades é a [If... Então... Else](../../../language-reference/statements/if-then-else-statement.md).</span><span class="sxs-lookup"><span data-stu-id="f57f4-114">The control structure that offers all these possibilities is the [If...Then...Else Statement](../../../language-reference/statements/if-then-else-statement.md).</span></span> <span data-ttu-id="f57f4-115">Você pode usar uma versão de linha única se tiver apenas um teste e uma instrução para executar.</span><span class="sxs-lookup"><span data-stu-id="f57f4-115">You can use a single-line version if you have just one test and one statement to run.</span></span> <span data-ttu-id="f57f4-116">Se você tiver um conjunto mais complexo de condições e ações, poderá usar a versão de várias linhas.</span><span class="sxs-lookup"><span data-stu-id="f57f4-116">If you have a more complex set of conditions and actions, you can use the multiple-line version.</span></span>  
  
## <a name="selectcase-construction"></a><span data-ttu-id="f57f4-117">Selecionar... Construção de caso</span><span class="sxs-lookup"><span data-stu-id="f57f4-117">Select...Case Construction</span></span>  

 <span data-ttu-id="f57f4-118">A `Select...Case` construção permite avaliar uma expressão uma vez e executar diferentes conjuntos de instruções com base em diferentes valores possíveis.</span><span class="sxs-lookup"><span data-stu-id="f57f4-118">The `Select...Case` construction lets you evaluate an expression one time and run different sets of statements based on different possible values.</span></span> <span data-ttu-id="f57f4-119">Para obter mais informações, consulte [Select... Instrução Case](../../../language-reference/statements/select-case-statement.md).</span><span class="sxs-lookup"><span data-stu-id="f57f4-119">For more information, see [Select...Case Statement](../../../language-reference/statements/select-case-statement.md).</span></span>  
  
## <a name="trycatchfinally-construction"></a><span data-ttu-id="f57f4-120">Tentar... Capturar... Por fim, construção</span><span class="sxs-lookup"><span data-stu-id="f57f4-120">Try...Catch...Finally Construction</span></span>  

 <span data-ttu-id="f57f4-121">`Try...Catch...Finally` as construções permitem que você execute um conjunto de instruções em um ambiente que retenha o controle se qualquer uma de suas instruções causar uma exceção.</span><span class="sxs-lookup"><span data-stu-id="f57f4-121">`Try...Catch...Finally` constructions let you run a set of statements under an environment that retains control if any one of your statements causes an exception.</span></span> <span data-ttu-id="f57f4-122">Você pode executar ações diferentes para exceções diferentes.</span><span class="sxs-lookup"><span data-stu-id="f57f4-122">You can take different actions for different exceptions.</span></span> <span data-ttu-id="f57f4-123">Opcionalmente, você pode especificar um bloco de código que é executado antes de sair da `Try...Catch...Finally` construção inteira, independentemente do que ocorrer.</span><span class="sxs-lookup"><span data-stu-id="f57f4-123">You can optionally specify a block of code that runs before you exit the whole `Try...Catch...Finally` construction, regardless of what occurs.</span></span> <span data-ttu-id="f57f4-124">Para obter mais informações, consulte [Instrução Try...Catch...Finally](../../../language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="f57f4-124">For more information, see [Try...Catch...Finally Statement](../../../language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f57f4-125">Para muitas estruturas de controle, quando você clica em uma palavra-chave, todas as palavras-chave na estrutura são realçadas.</span><span class="sxs-lookup"><span data-stu-id="f57f4-125">For many control structures, when you click a keyword, all of the keywords in the structure are highlighted.</span></span> <span data-ttu-id="f57f4-126">Por exemplo, quando você clica `If` em uma `If...Then...Else` construção, todas as instâncias de `If` ,, `Then` `ElseIf` , `Else` e `End If` na construção são realçadas.</span><span class="sxs-lookup"><span data-stu-id="f57f4-126">For instance, when you click `If` in an `If...Then...Else` construction, all instances of `If`, `Then`, `ElseIf`, `Else`, and `End If` in the construction are highlighted.</span></span> <span data-ttu-id="f57f4-127">Para mover para a próxima palavra-chave realçada ou anterior, pressione CTRL + SHIFT + seta para baixo ou CTRL + SHIFT + seta para cima.</span><span class="sxs-lookup"><span data-stu-id="f57f4-127">To move to the next or previous highlighted keyword, press CTRL+SHIFT+DOWN ARROW or CTRL+SHIFT+UP ARROW.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f57f4-128">Confira também</span><span class="sxs-lookup"><span data-stu-id="f57f4-128">See also</span></span>

- [<span data-ttu-id="f57f4-129">Fluxo de Controle</span><span class="sxs-lookup"><span data-stu-id="f57f4-129">Control Flow</span></span>](index.md)
- [<span data-ttu-id="f57f4-130">Estruturas de Loop</span><span class="sxs-lookup"><span data-stu-id="f57f4-130">Loop Structures</span></span>](loop-structures.md)
- [<span data-ttu-id="f57f4-131">Outras Estruturas de Controle</span><span class="sxs-lookup"><span data-stu-id="f57f4-131">Other Control Structures</span></span>](other-control-structures.md)
- [<span data-ttu-id="f57f4-132">Estruturas de Controle Aninhadas</span><span class="sxs-lookup"><span data-stu-id="f57f4-132">Nested Control Structures</span></span>](nested-control-structures.md)
- [<span data-ttu-id="f57f4-133">Operador If</span><span class="sxs-lookup"><span data-stu-id="f57f4-133">If Operator</span></span>](../../../language-reference/operators/if-operator.md)
