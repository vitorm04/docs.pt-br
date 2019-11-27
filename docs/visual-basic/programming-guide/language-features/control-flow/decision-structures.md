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
ms.openlocfilehash: d0d4039ff2edc61ee8b4b732c6adcb6e420d73ea
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353972"
---
# <a name="decision-structures-visual-basic"></a>Estruturas de decisão (Visual Basic)
Visual Basic permite testar condições e executar operações diferentes dependendo dos resultados desse teste. Você pode testar se uma condição é verdadeira ou falsa, para vários valores de uma expressão ou para várias exceções geradas quando você executa uma série de instruções.  
  
 A ilustração a seguir mostra uma estrutura de decisão que testa se uma condição é verdadeira e executa ações diferentes dependendo se ela é verdadeira ou falsa.  
  
 ![Um gráfico de fluxo de um If...Then...Else construção.](./media/decision-structures/if-then-else-construction.gif)  
  
## <a name="ifthenelse-construction"></a>If...Then...Else construção  
 `If...Then...Else` construções permitem testar uma ou mais condições e executar uma ou mais instruções, dependendo de cada condição. Você pode testar condições e executar ações das seguintes maneiras:  
  
- Executar uma ou mais instruções se uma condição for `True`  
  
- Executar uma ou mais instruções se uma condição for `False`  
  
- Execute algumas instruções se uma condição for `True` e outras se for `False`  
  
- Testar uma condição adicional se uma condição anterior for `False`  
  
 A estrutura de controle que oferece todas essas possibilidades é a [If... Então... Else](../../../../visual-basic/language-reference/statements/if-then-else-statement.md). Você pode usar uma versão de linha única se tiver apenas um teste e uma instrução para executar. Se você tiver um conjunto mais complexo de condições e ações, poderá usar a versão de várias linhas.  
  
## <a name="selectcase-construction"></a>Select...Case construção  
 A construção `Select...Case` permite avaliar uma expressão uma vez e executar diferentes conjuntos de instruções com base em diferentes valores possíveis. Para obter mais informações, consulte [Select... Instrução Case](../../../../visual-basic/language-reference/statements/select-case-statement.md).  
  
## <a name="trycatchfinally-construction"></a>Try...Catch...Finally, construção  
 `Try...Catch...Finally` construções permitem que você execute um conjunto de instruções em um ambiente que retenha o controle se qualquer uma de suas instruções causar uma exceção. Você pode executar ações diferentes para exceções diferentes. Opcionalmente, você pode especificar um bloco de código que é executado antes de sair da construção de `Try...Catch...Finally` inteira, independentemente do que ocorrer. Para obter mais informações, consulte [Instrução Try...Catch...Finally](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
> [!NOTE]
> Para muitas estruturas de controle, quando você clica em uma palavra-chave, todas as palavras-chave na estrutura são realçadas. Por exemplo, quando você clica em `If` em uma construção de `If...Then...Else`, todas as instâncias de `If`, `Then`, `ElseIf`, `Else`e `End If` na construção são realçadas. Para mover para a próxima palavra-chave realçada ou anterior, pressione CTRL + SHIFT + seta para baixo ou CTRL + SHIFT + seta para cima.  
  
## <a name="see-also"></a>Consulte também

- [Fluxo de Controle](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [Estruturas de Loop](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [Outras Estruturas de Controle](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)
- [Estruturas de Controle Aninhadas](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [Operador If](../../../../visual-basic/language-reference/operators/if-operator.md)
