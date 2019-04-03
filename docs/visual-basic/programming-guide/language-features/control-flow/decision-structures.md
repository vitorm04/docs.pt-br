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
ms.openlocfilehash: 20b60fb425278dacb56ee5f888967554a1f76aeb
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58825372"
---
# <a name="decision-structures-visual-basic"></a>Estruturas de decisão (Visual Basic)
Visual Basic permite testar condições e executar operações diferentes dependendo dos resultados do teste. Você pode testar uma condição ser verdadeira ou falsa para vários valores de uma expressão, ou para várias exceções geradas quando você executa uma série de instruções.  
  
 A ilustração a seguir mostra uma estrutura de decisão que testa uma condição ser verdadeira e executa ações diferentes dependendo se ele for verdadeiro ou falso.  
  
 ![Gráfico de fluxo de uma instrução If... Then... Outra construção](../../../../visual-basic/programming-guide/language-features/control-flow/media/ifthenelse.gif "IfThenElse")  
Tomando diferentes ações quando uma condição for true e quando é falsa.  
  
## <a name="ifthenelse-construction"></a>If... Then... Outra construção  
 `If...Then...Else` construções permitem que você teste para uma ou mais condições e executar uma ou mais instruções, dependendo de cada condição. Você pode testar condições e tomar ações das seguintes maneiras:  
  
-   Executar uma ou mais instruções, se uma condição for `True`  
  
-   Executar uma ou mais instruções, se uma condição for `False`  
  
-   Execute algumas declarações se uma condição for `True` e outras pessoas se ele for `False`  
  
-   Testar uma condição adicional se uma condição anterior for `False`  
  
 A estrutura de controle que oferece todas essas possibilidades é o [se... Then... Instrução else](../../../../visual-basic/language-reference/statements/if-then-else-statement.md). Você pode usar uma versão de linha única, se você tiver apenas um teste e uma única instrução para executar. Se você tiver um conjunto mais complexo de condições e ações, você pode usar a versão de várias linhas.  
  
## <a name="selectcase-construction"></a>Selecione... Construção de caso  
 O `Select...Case` construção permite que você avalie uma expressão de uma vez e executar diferentes conjuntos de instruções com base em diferentes valores possíveis. Para obter mais informações, consulte [selecione... Instrução de caso](../../../../visual-basic/language-reference/statements/select-case-statement.md).  
  
## <a name="trycatchfinally-construction"></a>Try... Catch... Por fim, construção  
 `Try...Catch...Finally` permitem executar um conjunto de instruções em um ambiente que mantém o controle se alguma de suas declarações causa uma exceção. Você pode executar ações diferentes para diferentes exceções. Opcionalmente, você pode especificar um bloco de código que é executado antes que você sai da `Try...Catch...Finally` construção, independentemente do que ocorre. Para obter mais informações, consulte [Instrução Try...Catch...Finally](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
> [!NOTE]
>  Para muitas estruturas de controle, quando você clica em uma palavra-chave, todas as palavras-chave na estrutura são realçadas. Por exemplo, quando você clica `If` em um `If...Then...Else` construção, todas as instâncias do `If`, `Then`, `ElseIf`, `Else`, e `End If` na construção são realçadas. Para mover para a palavra-chave a seguinte ou anterior, pressione CTRL + SHIFT + seta abaixo ou CTRL + SHIFT + seta acima.  
  
## <a name="see-also"></a>Consulte também

- [Fluxo de Controle](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [Estruturas de Loop](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [Outras Estruturas de Controle](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)
- [Estruturas de Controle Aninhadas](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [Operador If](../../../../visual-basic/language-reference/operators/if-operator.md)
