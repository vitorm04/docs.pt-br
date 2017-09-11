---
title: "Decisão de estruturas (Visual Basic) | Documentos do Microsoft"
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
- statements [Visual Basic], control flow
- If statement, decision structures
- If statement, If...Then...Else
- control flow, decision structures
- decision structures
- conditional statements, decision structures
ms.assetid: 2e2e0895-4483-442a-b17c-26aead751ec2
caps.latest.revision: 29
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
ms.openlocfilehash: dcbfb4bc3318d5f79870d04e606fab8bfa2dafb9
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="decision-structures-visual-basic"></a><span data-ttu-id="c329e-102">Estruturas de decisão (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c329e-102">Decision Structures (Visual Basic)</span></span>
[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="c329e-103">permite testar condições e executar diferentes operações dependendo dos resultados do teste.</span><span class="sxs-lookup"><span data-stu-id="c329e-103"> lets you test conditions and perform different operations depending on the results of that test.</span></span> <span data-ttu-id="c329e-104">Você pode testar uma condição ser verdadeira ou falsa para vários valores de uma expressão, ou para várias exceções geradas quando você executa uma série de instruções.</span><span class="sxs-lookup"><span data-stu-id="c329e-104">You can test for a condition being true or false, for various values of an expression, or for various exceptions generated when you execute a series of statements.</span></span>  
  
 <span data-ttu-id="c329e-105">A ilustração a seguir mostra uma estrutura de decisão que testa uma condição ser verdadeira e toma diferentes ações dependendo se é true ou false.</span><span class="sxs-lookup"><span data-stu-id="c329e-105">The following illustration shows a decision structure that tests for a condition being true and takes different actions depending on whether it is true or false.</span></span>  
  
 <span data-ttu-id="c329e-106">![Gráfico de fluxo de uma instrução If... Then... Outra construção](../../../../visual-basic/programming-guide/language-features/control-flow/media/ifthenelse.gif "IfThenElse")</span><span class="sxs-lookup"><span data-stu-id="c329e-106">![Flow chart of an If...Then...Else construction](../../../../visual-basic/programming-guide/language-features/control-flow/media/ifthenelse.gif "IfThenElse")</span></span>  
<span data-ttu-id="c329e-107">Tomando diferentes ações quando uma condição é verdadeira e quando é falsa.</span><span class="sxs-lookup"><span data-stu-id="c329e-107">Taking different actions when a condition is true and when it is false</span></span>  
  
## <a name="ifthenelse-construction"></a><span data-ttu-id="c329e-108">If... Then... Outra construção</span><span class="sxs-lookup"><span data-stu-id="c329e-108">If...Then...Else Construction</span></span>  
 <span data-ttu-id="c329e-109">`If...Then...Else`construções permitem testar uma ou mais condições e executar uma ou mais instruções dependendo de cada condição.</span><span class="sxs-lookup"><span data-stu-id="c329e-109">`If...Then...Else` constructions let you test for one or more conditions and run one or more statements depending on each condition.</span></span> <span data-ttu-id="c329e-110">Você pode testar condições e executar ações das seguintes maneiras:</span><span class="sxs-lookup"><span data-stu-id="c329e-110">You can test conditions and take actions in the following ways:</span></span>  
  
-   <span data-ttu-id="c329e-111">Execute uma ou mais declarações se uma condição é`True`</span><span class="sxs-lookup"><span data-stu-id="c329e-111">Run one or more statements if a condition is `True`</span></span>  
  
-   <span data-ttu-id="c329e-112">Execute uma ou mais declarações se uma condição é`False`</span><span class="sxs-lookup"><span data-stu-id="c329e-112">Run one or more statements if a condition is `False`</span></span>  
  
-   <span data-ttu-id="c329e-113">Execute algumas declarações se uma condição é `True` e outras se é`False`</span><span class="sxs-lookup"><span data-stu-id="c329e-113">Run some statements if a condition is `True` and others if it is `False`</span></span>  
  
-   <span data-ttu-id="c329e-114">Teste uma condição adicional se uma condição anterior é`False`</span><span class="sxs-lookup"><span data-stu-id="c329e-114">Test an additional condition if a prior condition is `False`</span></span>  
  
 <span data-ttu-id="c329e-115">A estrutura de controle que oferece todas essas possibilidade é o [se... Then... Instrução else](../../../../visual-basic/language-reference/statements/if-then-else-statement.md).</span><span class="sxs-lookup"><span data-stu-id="c329e-115">The control structure that offers all these possibilities is the [If...Then...Else Statement](../../../../visual-basic/language-reference/statements/if-then-else-statement.md).</span></span> <span data-ttu-id="c329e-116">Você pode usar uma versão de linha única, se você tiver apenas um teste e uma declaração para executar.</span><span class="sxs-lookup"><span data-stu-id="c329e-116">You can use a single-line version if you have just one test and one statement to run.</span></span> <span data-ttu-id="c329e-117">Se você tiver um conjunto mais complexo de condições e ações, você pode usar a versão de várias linhas.</span><span class="sxs-lookup"><span data-stu-id="c329e-117">If you have a more complex set of conditions and actions, you can use the multiple-line version.</span></span>  
  
## <a name="selectcase-construction"></a><span data-ttu-id="c329e-118">Selecione... Construção de caso</span><span class="sxs-lookup"><span data-stu-id="c329e-118">Select...Case Construction</span></span>  
 <span data-ttu-id="c329e-119">O `Select...Case` construção permite avaliar uma expressão uma vez e executar diferentes conjuntos de condições baseados nos diferentes valores possíveis.</span><span class="sxs-lookup"><span data-stu-id="c329e-119">The `Select...Case` construction lets you evaluate an expression one time and run different sets of statements based on different possible values.</span></span> <span data-ttu-id="c329e-120">Para obter mais informações, consulte [selecione... Instrução Case](../../../../visual-basic/language-reference/statements/select-case-statement.md).</span><span class="sxs-lookup"><span data-stu-id="c329e-120">For more information, see [Select...Case Statement](../../../../visual-basic/language-reference/statements/select-case-statement.md).</span></span>  
  
## <a name="trycatchfinally-construction"></a><span data-ttu-id="c329e-121">Try... Catch... Por fim, construção</span><span class="sxs-lookup"><span data-stu-id="c329e-121">Try...Catch...Finally Construction</span></span>  
 <span data-ttu-id="c329e-122">`Try...Catch...Finally`permitem executar um conjunto de instruções em um ambiente que toma controle se alguma de suas declarações causa uma exceção.</span><span class="sxs-lookup"><span data-stu-id="c329e-122">`Try...Catch...Finally` constructions let you run a set of statements under an environment that retains control if any one of your statements causes an exception.</span></span> <span data-ttu-id="c329e-123">Você pode executar ações diferentes para exceções diferentes.</span><span class="sxs-lookup"><span data-stu-id="c329e-123">You can take different actions for different exceptions.</span></span> <span data-ttu-id="c329e-124">Opcionalmente, você pode especificar um bloco de código que é executado antes que você sai da `Try...Catch...Finally` construção, independentemente do que ocorre.</span><span class="sxs-lookup"><span data-stu-id="c329e-124">You can optionally specify a block of code that runs before you exit the whole `Try...Catch...Finally` construction, regardless of what occurs.</span></span> <span data-ttu-id="c329e-125">Para obter mais informações, consulte [Try... Catch... Instrução Finally](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="c329e-125">For more information, see [Try...Catch...Finally Statement](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c329e-126">Para muitas estruturas de controle quando você clica em uma palavra-chave, todas as palavras-chave da estrutura são realçadas.</span><span class="sxs-lookup"><span data-stu-id="c329e-126">For many control structures, when you click a keyword, all of the keywords in the structure are highlighted.</span></span> <span data-ttu-id="c329e-127">Por exemplo, quando você clica em `If` em uma `If...Then...Else` construção, todas as instâncias de `If`, `Then`, `ElseIf`, `Else`, e `End If` na construção são realçadas.</span><span class="sxs-lookup"><span data-stu-id="c329e-127">For instance, when you click `If` in an `If...Then...Else` construction, all instances of `If`, `Then`, `ElseIf`, `Else`, and `End If` in the construction are highlighted.</span></span> <span data-ttu-id="c329e-128">Para mover para a palavra-chave do próximo ou anterior, pressione CTRL + SHIFT + DOWN ARROW ou CTRL + SHIFT + seta acima.</span><span class="sxs-lookup"><span data-stu-id="c329e-128">To move to the next or previous highlighted keyword, press CTRL+SHIFT+DOWN ARROW or CTRL+SHIFT+UP ARROW.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c329e-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c329e-129">See Also</span></span>  
 <span data-ttu-id="c329e-130">[Fluxo de controle](../../../../visual-basic/programming-guide/language-features/control-flow/index.md) </span><span class="sxs-lookup"><span data-stu-id="c329e-130">[Control Flow](../../../../visual-basic/programming-guide/language-features/control-flow/index.md) </span></span>  
<span data-ttu-id="c329e-131"> [Estruturas de loop](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md) </span><span class="sxs-lookup"><span data-stu-id="c329e-131"> [Loop Structures](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md) </span></span>  
<span data-ttu-id="c329e-132"> [Outras estruturas de controle](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md) </span><span class="sxs-lookup"><span data-stu-id="c329e-132"> [Other Control Structures](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md) </span></span>  
<span data-ttu-id="c329e-133"> [Estruturas de controle aninhadas](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md) </span><span class="sxs-lookup"><span data-stu-id="c329e-133"> [Nested Control Structures](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md) </span></span>  
<span data-ttu-id="c329e-134"> [Operador If](../../../../visual-basic/language-reference/operators/if-operator.md)</span><span class="sxs-lookup"><span data-stu-id="c329e-134"> [If Operator](../../../../visual-basic/language-reference/operators/if-operator.md)</span></span>
