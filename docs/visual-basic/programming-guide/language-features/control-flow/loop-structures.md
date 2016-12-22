---
title: "Estruturas de loop (Visual Basic) | Microsoft Docs"
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
  - "Instruções condicionais, Estruturas de loop"
  - "fluxo de controle, loops"
  - "instrução Do, loops Do"
  - "palavra-chave For [Visual Basic], Estruturas de loop"
  - "Estruturas de loop"
  - "loops"
  - "instruções [Visual Basic], loop"
ms.assetid: ecacb09b-a4c9-42be-98b2-a15d368b5db8
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Estruturas de loop (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]as estruturas de loop permitem que você execute uma ou mais linhas de código repetidamente.  Você pode repetir as instruções em uma estrutura de loop até que uma condição é `True`, até que uma condição é `False`, um especificado o número de vezes, ou uma vez para cada elemento em uma coleção.  
  
 A ilustração a seguir mostra uma estrutura de loop que executa um conjunto de instruções até que uma condição for verdadeira.  
  
 ![Gráfico de fluxo de um...Até que o loop](../../../../visual-basic/programming-guide/language-features/control-flow/media/dountilloop.gif "DoUntilLoop")  
A execução de um conjunto de instruções até que uma condição for verdadeira  
  
## While Loops  
 The `While`...`End While` construção executa um conjunto de instruções desde que a condição especificada na `While` a declaração é `True`.  Para obter mais informações, consulte [Instrução While...End While](../../../../visual-basic/language-reference/statements/while-end-while-statement.md).  
  
## Não Loops  
 The `Do`...`Loop` construção permite testar uma condição no início ou final de uma estrutura de loop.  Você também pode especificar se deseja repetir o loop, enquanto a condição permanece `True` ou até que ele fique `True`.  Para obter mais informações, consulte [Instrução Do...Loop](../../../../visual-basic/language-reference/statements/do-loop-statement.md).  
  
## Loops for  
 The `For`...`Next` construção executa loop um número definido de vezes.  Ele usa uma variável de controle de loop, também chamada de um  *contador*, para controlar as repetições.  Você especifica o iniciais e finais de valores para esse contador e, opcionalmente, você pode especificar a quantidade pela qual ele aumenta de repetição de um para o próximo.  Para obter mais informações, consulte [Instrução For...Next](../../../../visual-basic/language-reference/statements/for-next-statement.md).  
  
## Loops For Each  
 The `For Each`...`Next` construção executa um conjunto de instruções uma vez para cada elemento em uma coleção.  Você especifica a variável de controle de loop, mas você não precisará determinar inicial ou final de valores para ele.  Para obter mais informações, consulte [Instrução For Each...Next](../../../../visual-basic/language-reference/statements/for-each-next-statement.md).  
  
## Consulte também  
 [Fluxo de controle](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)   
 [Estruturas de decisão](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)   
 [Outras estruturas de controle](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)   
 [Estruturas de controle aninhadas](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)