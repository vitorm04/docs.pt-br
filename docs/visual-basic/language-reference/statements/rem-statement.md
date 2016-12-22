---
title: "Instru&#231;&#227;o REM (Visual Basic) | Microsoft Docs"
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
  - "vb.'"
  - "vb.Rem"
  - "Rem"
  - "'"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "caractere marcador de comentário ' [Visual Basic]"
  - "comentários de código, Visual Basic"
  - "comentários, código do Visual Basic"
  - "instrução REM"
  - "código do Visual Basic, comentários"
ms.assetid: 34126d7f-e0f9-476d-91e6-b31b398615dc
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Instru&#231;&#227;o REM (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Usado para incluir comentários explicativos no código\-fonte de um programa.  
  
## Sintaxe  
  
```  
REM comment  
' comment  
```  
  
## Partes  
 `comment`  
 Opcional.  O texto de qualquer comentário que você deseja incluir.  Um espaço é necessário entre o `REM` palavra\-chave e `comment`.  
  
## Comentários  
 Você pode colocar uma instrução `REM` sozinho em uma linha, ou você pode colocá\-lo em uma linha após outra instrução.  A instrução `REM` deve ser a última instrução na linha.  Se ela segue outra instrução, a instrução `REM` deve ser separada dessa instrução por um espaço.  
  
 Você pode usar uma aspas simples \(`'`\) em vez de `REM`.  Isso é verdadeiro se o seu comentário segue outra instrução na mesma linha ou fica sozinho em uma linha.  
  
> [!NOTE]
>  Você não pode continuar uma instrução `REM` usando uma seqüência de continuação de linha \(`_` Quando um comentário começa, o compilador não examina os caracteres para um significado especial.  Para um comentário de várias linhas, use outra instrução `REM` ou um símbolo de comentário \(`'`\) em cada linha.  
  
## Exemplo  
 O exemplo a seguir ilustra a instrução `REM`, que é usada para incluir comentários explicativos em um programa.  Ele também mostra a alternativa de usar o caractere aspas simples \(`'`\) em vez de `REM`.  
  
 [!code-vb[VbVbalrStatements#6](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/rem-statement_1.vb)]  
  
## Consulte também  
 [Comentários no código](../../../visual-basic/programming-guide/program-structure/comments-in-code.md)   
 [Como quebrar e combinar instruções no código](../Topic/How%20to:%20Break%20and%20Combine%20Statements%20in%20Code%20\(Visual%20Basic\).md)