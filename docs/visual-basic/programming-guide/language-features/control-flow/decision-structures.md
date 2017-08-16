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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: c69b487322dc75ae8d54f42c1c62f8f5cc35757d
ms.lasthandoff: 03/13/2017

---
# <a name="decision-structures-visual-basic"></a>Estruturas de decisão (Visual Basic)
[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]permite testar condições e executar diferentes operações dependendo dos resultados do teste. Você pode testar uma condição ser verdadeira ou falsa para vários valores de uma expressão, ou para várias exceções geradas quando você executa uma série de instruções.  
  
 A ilustração a seguir mostra uma estrutura de decisão que testa uma condição ser verdadeira e toma diferentes ações dependendo se é true ou false.  
  
 ![Gráfico de fluxo de uma instrução If... Then... Outra construção](../../../../visual-basic/programming-guide/language-features/control-flow/media/ifthenelse.gif "IfThenElse")  
Tomando diferentes ações quando uma condição é verdadeira e quando é falsa.  
  
## <a name="ifthenelse-construction"></a>If... Then... Outra construção  
 `If...Then...Else`construções permitem testar uma ou mais condições e executar uma ou mais instruções dependendo de cada condição. Você pode testar condições e executar ações das seguintes maneiras:  
  
-   Execute uma ou mais declarações se uma condição é`True`  
  
-   Execute uma ou mais declarações se uma condição é`False`  
  
-   Execute algumas declarações se uma condição é `True` e outras se é`False`  
  
-   Teste uma condição adicional se uma condição anterior é`False`  
  
 A estrutura de controle que oferece todas essas possibilidade é o [se... Then... Instrução else](../../../../visual-basic/language-reference/statements/if-then-else-statement.md). Você pode usar uma versão de linha única, se você tiver apenas um teste e uma declaração para executar. Se você tiver um conjunto mais complexo de condições e ações, você pode usar a versão de várias linhas.  
  
## <a name="selectcase-construction"></a>Selecione... Construção de caso  
 O `Select...Case` construção permite avaliar uma expressão uma vez e executar diferentes conjuntos de condições baseados nos diferentes valores possíveis. Para obter mais informações, consulte [selecione... Instrução Case](../../../../visual-basic/language-reference/statements/select-case-statement.md).  
  
## <a name="trycatchfinally-construction"></a>Try... Catch... Por fim, construção  
 `Try...Catch...Finally`permitem executar um conjunto de instruções em um ambiente que toma controle se alguma de suas declarações causa uma exceção. Você pode executar ações diferentes para exceções diferentes. Opcionalmente, você pode especificar um bloco de código que é executado antes que você sai da `Try...Catch...Finally` construção, independentemente do que ocorre. Para obter mais informações, consulte [Try... Catch... Instrução Finally](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
> [!NOTE]
>  Para muitas estruturas de controle quando você clica em uma palavra-chave, todas as palavras-chave da estrutura são realçadas. Por exemplo, quando você clica em `If` em uma `If...Then...Else` construção, todas as instâncias de `If`, `Then`, `ElseIf`, `Else`, e `End If` na construção são realçadas. Para mover para a palavra-chave do próximo ou anterior, pressione CTRL + SHIFT + DOWN ARROW ou CTRL + SHIFT + seta acima.  
  
## <a name="see-also"></a>Consulte também  
 [Fluxo de controle](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)   
 [Estruturas de loop](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)   
 [Outras estruturas de controle](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)   
 [Estruturas de controle aninhadas](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)   
 [Operador If](../../../../visual-basic/language-reference/operators/if-operator.md)
