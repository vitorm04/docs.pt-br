---
title: "Estruturas de decis&#227;o (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Instruções condicionais, estruturas de decisão"
  - "fluxo de controle, estruturas de decisão"
  - "estruturas de decisão"
  - "instrução If, estruturas de decisão"
  - "instrução If, If...Then...Else"
  - "instruções [Visual Basic], fluxo de controle"
ms.assetid: 2e2e0895-4483-442a-b17c-26aead751ec2
caps.latest.revision: 29
caps.handback.revision: 29
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Estruturas de decis&#227;o (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] permite testar condições e executar diferentes operações dependendo dos resultados do teste.  Você pode testar para um condição ser falsa ou verdadeira, para vários valores de uma expressão, ou para várias exceções geradas quando você executa uma série de declarações.  
  
 A seguinte ilustração mostra uma estrutura de decisão que testa por uma condição ser verdadeira e toma diferentes ações dependendo se é verdadeira ou falsa.  
  
 ![Gráfico de fluxo de uma instrução If...Então...Construção de outra pessoa](../../../../visual-basic/programming-guide/language-features/control-flow/media/ifthenelse.png "IfThenElse")  
Tomando diferentes ações quando a condição é verdadeira e quando é falsa.  
  
## Construção If...Then...Else  
 A construção `If...Then...Else` permite testar por uma ou mais condições e executar uma ou mais declarações dependendo de cada condição.   Você pode testar condições e tomar ações nos seguintes modos:  
  
-   Execute uma ou mais declarações se uma condição é `True`  
  
-   Execute uma ou mais declarações se uma condição é `False`  
  
-   Execute algumas declarações se a condição é `True` e outras se é `False`  
  
-   Teste uma condição adicional se uma condição anterior é `False`  
  
 A estrutura de controle que oferece todas essas possibilidade é a [Instrução If...Then...Else](../../../../visual-basic/language-reference/statements/if-then-else-statement.md).  Você pode usar uma versão de uma linha se você tem somente um test e uma declaração para executar.  Se você tem um conjunto mais complexo de condições e ações, você pode usar a versão com múltiplas linhas.  
  
## Construção Select\/Case  
 A construção `Select...Case` permite avaliar uma expressão uma vez e executar diferentes conjuntos de condições baseados nos diferentes valores possíveis.  Para obter mais informações, consulte [Instrução Select...Case](../../../../visual-basic/language-reference/statements/select-case-statement.md).  
  
## Construção Try...Catch...Finally  
 Contruções `Try...Catch...Finally` permitem executar um conjunto de declarações dentro de um ambiente que toma controle se alguma de suas declarações causa uma exceção.  Você pode tomar diferentes ações para diferentes exceções.  Você pode opcionalmente especificar um bloco de código que é executado antes que você sai da construção `Try...Catch...Finally`, independente do que ocorrer.  Para obter mais informações, consulte [Instrução Try...Catch...Finally](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
> [!NOTE]
>  Para muitas estruturas de controle, quando você clica um palavra\-chave, todos os palavra\-chave na estrutura são realçadas.  Por exemplo, quando você clica `If` em uma compilação de `If...Then...Else` , todas as instâncias de `If`, de `Then`, de `ElseIf`, de `Else`, e de`End If` na compilação são realçadas.  Para mover para palavra\-chave realçado a seguir ou anterior, pressione ALT\+SETA de CTRL\+SHIFT\+DOWN ou a SETA de CTRL\+SHIFT\+UP.  
  
## Consulte também  
 [Fluxo de controle](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)   
 [Estruturas de loop](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)   
 [Outras estruturas de controle](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)   
 [Estruturas de controle aninhadas](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)   
 [Operador If](../../../../visual-basic/language-reference/operators/if-operator.md)