---
title: "Como acessar caracteres em cadeias de caracteres no Visual Basic | Microsoft Docs"
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
  - "caracteres [Visual Basic], acessando em cadeias de caracteres"
  - "cadeias de caracteres {Visual Basic], acessando caracteres"
ms.assetid: 02c5206c-ffab-494d-b648-3b2ea358dc34
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como acessar caracteres em cadeias de caracteres no Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Este exemplo demonstra como usar a propriedade <xref:System.String.Chars%2A> para acessar o caractere no local especificado em uma sequência de caracteres.  
  
## Exemplo  
 Às vezes é útil ter informações sobre os caracteres em sua sequência de caracteres e as posições desses caracteres dentro sua sequência.  Você pode pensar em uma sequência de caracteres como uma matriz de caracteres \(instâncias `Char`\); você pode recuperar um determinado caractere consultando o índice do caractere através da propriedade <xref:System.String.Chars%2A>.  
  
 [!code-vb[VbVbalrStrings#49](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-access-characters-in-strings_1.vb)]  
  
 O parâmetro `index` da propriedade <xref:System.String.Chars%2A> é baseado em zero.  
  
## Programação robusta  
 A propriedade <xref:System.String.Chars%2A> retorna o caractere na posição especificada.  No entanto, alguns caracteres Unicode podem ser representados por mais de um caractere.  Para obter mais informações sobre como trabalhar com caracteres Unicode, consulte [Como converter uma cadeia de caracteres em uma matriz de caracteres](../Topic/How%20to:%20Convert%20a%20String%20to%20an%20Array%20of%20Characters%20in%20Visual%20Basic.md).  
  
 A propriedade <xref:System.String.Chars%2A> lança uma exceção <xref:System.IndexOutOfRangeException> se o parâmetro `index` é maior ou igual ao comprimento da sequência de caracteres, ou se ele for menor que zero  
  
## Consulte também  
 <xref:System.String.Chars%2A>   
 [Como converter uma cadeia de caracteres em uma matriz de caracteres](../Topic/How%20to:%20Convert%20a%20String%20to%20an%20Array%20of%20Characters%20in%20Visual%20Basic.md)   
 [Convertendo entre cadeias de caracteres e outros tipos de dados no Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/converting-between-strings-and-other-data-types.md)   
 [Cadeias de caracteres](../../../../visual-basic/programming-guide/language-features/strings/index.md)