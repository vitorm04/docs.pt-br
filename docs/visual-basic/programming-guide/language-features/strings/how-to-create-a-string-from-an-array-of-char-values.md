---
title: "Como criar uma cadeia de caracteres a partir de uma matriz de valores de caracteres (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
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
  - "exemplos [Visual Basic], matrizes"
  - "exemplos [Visual Basic], tipo de dados Char"
ms.assetid: 69f94e85-d57c-4ccc-a62a-426e829f5c5e
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como criar uma cadeia de caracteres a partir de uma matriz de valores de caracteres (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Este exemplo cria a sequência de caracteres individuais "Abcd".  
  
## Exemplo  
 [!code-vb[VbVbalrStrings#61](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-create-a-string-from-an-array-of-char-values_1.vb)]  
  
## Compilando o código  
 Este método não possui requisitos especiais.  
  
 A sintaxe `"a"c`, onde um único `c` segue um único caractere entre aspas, é usada para criar um caractere literal.  
  
## Programação robusta  
 Caracteres nulos \(equivalente a `Chr(0)`\) na sequência levar a resultados inesperados ao se usar a sequência de caracteres.  O caractere nulo será incluído com a sequência de caracteres, mas caracteres após o caractere nulo não serão exibidas em algumas situações.  
  
## Consulte também  
 <xref:System.String>   
 [Tipo de dados Char](../../../../visual-basic/language-reference/data-types/char-data-type.md)   
 [Tipos de dados](../../../../visual-basic/programming-guide/language-features/data-types/index.md)