---
title: "Tipos de m&#233;todos de manipula&#231;&#227;o da cadeia de caracteres no Visual Basic | Microsoft Docs"
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
  - "manipulação de cadeias de caracteres"
  - "cadeias de caracteres {Visual Basic], manipulando [Visual Basic]"
ms.assetid: 905055cd-7f50-48fb-9eed-b0995af1dc1f
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Tipos de m&#233;todos de manipula&#231;&#227;o da cadeia de caracteres no Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Há várias maneiras diferentes de analisar e manipular suas sequências de caracteres.  Alguns dos métodos fazem parte da linguagem [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], e outros são inerentes à classe `String`.  
  
## Linguagem Visual Basic e o Framework .NET  
 Os métodos [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] são usados como sendo funções inerentes da linguagem.  Eles podem ser usados sem qualificação no seu código.  O exemplo a seguir mostra uso típico de um comando de manipulação de cadeia de caracteres do [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] :  
  
 [!code-vb[VbVbalrStrings#44](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/types-of-string-manipulation-methods_1.vb)]  
  
 Nesse exemplo, a função `Mid` executa uma operação em `aString` e atribui o valor à `bString`.  
  
 Para obter uma lista dos métodos de manipulação de seqüência de caracteres Visual Basic, consulte [Resumo de manipulação da cadeia de caracteres](../../../../visual-basic/language-reference/keywords/string-manipulation-summary.md).  
  
### Métodos Compartilhados e Métodos da Instância  
 Você também pode manipular sequências de caracteres com os métodos da classe `String`.  Há dois tipos de métodos em  `String`: métodos *compartilhados* e  métodos de  *instância* .  
  
#### Métodos compartilhados  
 Um método compartilhado é um método que deriva da classe `String` e não requer uma instância da classe para funcionar.  Esses métodos podem ser qualificados com o nome da classe \(`String`\) em vez de uma instância da classe `String`.  Por exemplo:  
  
 [!code-vb[VbVbalrStrings#45](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/types-of-string-manipulation-methods_2.vb)]  
  
 No exemplo anterior, o método <xref:System.String.Copy%2A?displayProperty=fullName> é um método estático, que age sobre uma expressão fornecida e atribui o valor resultante à `bString`.  
  
#### Métodos de instância  
 Métodos de instância, por outro lado, derivam de uma determinada instância de `String` e devem ser qualificados com o nome da instância.  Por exemplo:  
  
 [!code-vb[VbVbalrStrings#46](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/types-of-string-manipulation-methods_3.vb)]  
  
 Nesse exemplo, o método <xref:System.String.Substring%2A?displayProperty=fullName> é um método de instância de `String` \(ou seja, `aString`\).  Ele realiza uma operação em `aString` e atribui o valor a `bString`.  
  
 Para obter mais informações, consulte a documentação para o <xref:System.String> classe.  
  
## Consulte também  
 [Introdução a cadeias de caracteres no Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)