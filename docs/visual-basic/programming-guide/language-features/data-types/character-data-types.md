---
title: "Tipos de dados de caractere (Visual Basic) | Microsoft Docs"
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
  - "tipo de dados Char, tipos de dados de caracteres"
  - "tipos de dados de caractere [Visual Basic]"
  - "tipos de dados [Visual Basic], caractere"
  - "tipos de dados [Visual Basic], escolha"
  - "tipo de dados String, tipos de dados de caracteres"
ms.assetid: 902479ef-1679-47fc-9911-0c1c5008226c
caps.latest.revision: 23
caps.handback.revision: 23
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Tipos de dados de caractere (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] fornece  *tipos de dados de caracteres*  para lidar com caracteres que podem ser impressos e exibidos.  Enquanto ambos lidem com caracteres Unicode, `Char` mantém um único caractere ao passo que `String` contém um número indefinido de caracteres.  
  
 Para obter uma tabela que exiba uma comparação lado\-a\-lado dos [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] tipos de dados, consulte [Tipos de dados](../../../../visual-basic/language-reference/data-types/data-type-summary.md).  
  
## Tipo Char  
 O tipo de dados `Char` é um caractere Unicode único de dois bytes \(16 bits\).  Se uma variável sempre armazena exatamente um caractere, declare\-a como `Char`.  Por exemplo:  
  
 [!CODE [VbVbalrCharTypes#1](../CodeSnippet/VS_Snippets_VBCSharp/vbvbalrchartypes#1)]  
  
 Cada valor possível em um `Char` ou `String` variável é um  *código aponte*, ou o código de caractere, no conjunto de caracteres Unicode.  Os caracteres Unicode incluem o conjunto básico de caracteres ASCII, várias outras letras do alfabeto, acentos, unidades monetárias, frações, diacríticos, símbolos matemáticos e outros símbolos técnicos.  
  
> [!NOTE]
>  O conjunto de caracteres Unicode reserva os pontos de código entre D800 e DFFF \(55296 até 55551 em decimal\) para *pares substitutos*, que requerem dois valores de 16 bits para representar um único ponto de código.  Uma variável `Char` não pode armazenar um par substituto, e uma `String` usa duas posições para armazenar tal par.  
  
 Para obter mais informações, consulte [Tipo de dados Char](../../../../visual-basic/language-reference/data-types/char-data-type.md).  
  
## Tipo Sequência de Caracteres  
 O tipo de dados `String` é uma sequência de zero ou mais caracteres Unicode de dois bytes \(16 bits\).  Se uma variável pode conter um número de caracteres indefinido, declare\-a como `String`.  Por exemplo:  
  
 [!CODE [VbVbalrCharTypes#2](../CodeSnippet/VS_Snippets_VBCSharp/vbvbalrchartypes#2)]  
  
 Para obter mais informações, consulte [Tipo de dados da cadeia de caracteres](../../../../visual-basic/language-reference/data-types/string-data-type.md).  
  
## Consulte também  
 [Tipos de dados elementares](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)   
 [Tipos de dados compostos](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)   
 [Tipos genéricos no Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)   
 [Tipos de valor e referência](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)   
 [Conversões de tipo no Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)   
 [Solucionando problemas de tipos de dados](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)   
 [Caracteres de tipo](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)