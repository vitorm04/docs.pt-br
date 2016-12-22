---
title: "Instru&#231;&#227;o Continue (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.continue"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "instrução Continue [Visual Basic]"
  - "loops, transferindo para a próxima iteração"
ms.assetid: 3ad00103-358b-4af3-a3a8-1b9ea0e995d3
caps.latest.revision: 21
caps.handback.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Instru&#231;&#227;o Continue (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Transfere controle imediatamente para a próxima iteração de um loop.  
  
## Sintaxe  
  
```  
Continue { Do | For | While }  
```  
  
## Comentários  
 Você pode transferir de dentro de um loop `Do`, `For` ou `While` para a próxima iteração daquele loop.  O controle passa imediatamente para o teste de condição do loop, que é equivalente a transferir para a declaração `For` ou `While` , ou para a declaração `Do` ou `Loop` que contém a cláusula `Until` ou `While` .  
  
 Você pode usar `Continue` em qualquer posição no loop que permite transferências.  As regras permitindo transferência de controle são as mesma que [Instrução GoTo](../../../visual-basic/language-reference/statements/goto-statement.md).  
  
 Por exemplo, se um loop está totalmente contido dentro de um bloco `Try`, um bloco `Catch`, ou um bloco `Finally`, você pode usar `Continue` para transferir para fora do loop.  Se, por outro lado, a estrutura `Try`...`End Try` está contida dentro do loop, você não pode usar `Continue` para tranferir o controle para fora do bloco `Finally` , e você pode usar isso para transferir para fora de um bloco  `Try` ou `Catch`somente se você transferir completamente para fora da estrutura `Try`...`End Try`.  
  
 Se você tem loops aninhados do mesmo tipo, por exemplo um loop `Do` dentro de outro loop `Do`, uma declaração `Continue Do` ignora a próxima iteração do loop `Do` mais interno que a contém.  Você pode usar `Continue` para ignorar a próxima iteração de um loop continente do mesmo tipo.  
  
 Se você tem loops aninhados de diferentes tipos , por exemplo um loop `Do` dentro de outro loop `For`, você pode pular a próxima iteração de qualquer um loop usando ou `Continue Do` ou `Continue For`.  
  
## Exemplo  
 O código de exemplo a seguir usa uma declaração `Continue While` para ignorar a próxima coluna de uma matriz se o divisor é zero.  O `Continue While` está dentro de um loop `For`.  Ele transfere para a declaração `While col < lastcol`, a qual é a próxima iteração do loop `While` mais interno que contém o loop `For`.  
  
 [!code-vb[VbVbalrStatements#14](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/continue-statement_1.vb)]  
  
## Consulte também  
 [Instrução Do...Loop](../../../visual-basic/language-reference/statements/do-loop-statement.md)   
 [Instrução For...Next](../../../visual-basic/language-reference/statements/for-next-statement.md)   
 [Instrução While...End While](../../../visual-basic/language-reference/statements/while-end-while-statement.md)   
 [Instrução Try...Catch...Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)