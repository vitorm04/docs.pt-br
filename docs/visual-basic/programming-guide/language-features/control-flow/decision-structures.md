---
title: Estruturas de decisão (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- statements [Visual Basic], control flow
- If statement [Visual Basic], decision structures
- If statement [Visual Basic], If...Then...Else
- control flow [Visual Basic], decision structures
- decision structures [Visual Basic]
- conditional statements [Visual Basic], decision structures
ms.assetid: 2e2e0895-4483-442a-b17c-26aead751ec2
caps.latest.revision: 29
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3b89d6f9b27e086b657c29f3353b63cdd855ae19
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="decision-structures-visual-basic"></a>Estruturas de decisão (Visual Basic)
Visual Basic permite testar condições e executar operações diferentes dependendo dos resultados do teste. Você pode testar uma condição que está sendo verdadeiro ou falso, para vários valores de uma expressão, ou para várias exceções geradas quando você executa uma série de instruções.  
  
 A ilustração a seguir mostra uma estrutura de decisão que testa uma condição ser verdadeira e executa ações diferentes dependendo se é true ou false.  
  
 ![Gráfico de fluxo de uma instrução If... Then... Construção Else](../../../../visual-basic/programming-guide/language-features/control-flow/media/ifthenelse.gif "IfThenElse")  
Tomando diferentes ações quando uma condição é verdadeira e quando é falsa.  
  
## <a name="ifthenelse-construction"></a>If... Then... Construção Else  
 `If...Then...Else` construções permitem para uma ou mais condições de teste e execute uma ou mais instruções dependendo de cada condição. Você pode testar condições e tomar medidas das seguintes maneiras:  
  
-   Execute uma ou mais declarações se uma condição for `True`  
  
-   Execute uma ou mais declarações se uma condição for `False`  
  
-   Execute algumas declarações se uma condição for `True` e outras se é `False`  
  
-   Testar uma condição adicional se uma condição anterior for `False`  
  
 A estrutura de controle que oferece todas essas possibilidade é a [se... Then... Instrução else](../../../../visual-basic/language-reference/statements/if-then-else-statement.md). Você pode usar uma versão de linha única, se você tiver somente um test e uma declaração para executar. Se você tiver um conjunto mais complexo de condições e ações, você pode usar a versão de várias linhas.  
  
## <a name="selectcase-construction"></a>Selecione... Construção de maiusculas  
 O `Select...Case` construção permite avaliar uma expressão uma vez e executar diferentes conjuntos de declarações com base nos diferentes valores possíveis. Para obter mais informações, consulte [selecione... Caso a instrução](../../../../visual-basic/language-reference/statements/select-case-statement.md).  
  
## <a name="trycatchfinally-construction"></a>Try... Catch... Por fim, construção  
 `Try...Catch...Finally` permitem executar um conjunto de instruções em um ambiente que mantém o controle se alguma de suas declarações causa uma exceção. Você pode executar ações diferentes para diferentes exceções. Opcionalmente, você pode especificar um bloco de código que é executado antes que você sai da `Try...Catch...Finally` construção, independentemente do que ocorre. Para obter mais informações, consulte [Instrução Try...Catch...Finally](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
> [!NOTE]
>  Para muitas estruturas de controle, quando você clica em uma palavra-chave, todas as palavras-chave na estrutura são realçadas. Por exemplo, quando você clica em `If` em uma `If...Then...Else` construção, todas as instâncias de `If`, `Then`, `ElseIf`, `Else`, e `End If` na construção são realçados. Para mover para a palavra-chave do próximo ou anterior, pressione CTRL + SHIFT + DOWN ARROW ou CTRL + SHIFT + seta acima.  
  
## <a name="see-also"></a>Consulte também  
 [Fluxo de Controle](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)  
 [Estruturas de Loop](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)  
 [Outras Estruturas de Controle](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)  
 [Estruturas de Controle Aninhadas](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)  
 [Operador If](../../../../visual-basic/language-reference/operators/if-operator.md)
