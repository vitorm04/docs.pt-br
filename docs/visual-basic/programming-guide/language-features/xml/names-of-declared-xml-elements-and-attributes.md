---
title: "Nomes de elementos e atributos XML declarados (Visual Basic) | Microsoft Docs"
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
  - "nomes de atributos [XML no Visual Basic]"
  - "declarações [XML no Visual Basic]"
  - "nomes de elementos [XML no Visual Basic]"
  - "nomes em literais XML"
  - "literais XML [Visual Basic], nomes de elementos"
ms.assetid: cc110118-b6cf-4ff9-a4e4-6233c90c9fbf
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Nomes de elementos e atributos XML declarados (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Este tópico fornece [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] diretrizes para nomear elementos XML e atributos em literais XML.  Um literal XML, você pode especificar um nome local ou um nome qualificado.  Um nome qualificado consiste em um prefixo de namespace XML, dois\-pontos e um nome local.  Para obter mais informações sobre os prefixos de namespace XML, consulte [Literal do elemento XML](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).  
  
## Regras  
 Um nome local de um elemento ou atributo na [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] deve aderir às seguintes regras.  
  
-   Ele pode começar com um espaço para nome.  Ele deve começar com um caractere alfabético ou sublinhado \(`_`\).  
  
-   Ele deve conter apenas caracteres alfabéticos, dígitos decimais, sublinhados, pontos \(.\) e hífens \(\-\).  
  
-   Ele não deve ter mais de 1,024 caracteres.  
  
-   Dois pontos que aparecem em nomes indicam demarcação de namespace.  Portanto, você pode usar dois\-pontos somente para especificar um namespace de XML para um determinado nome.  
  
 Além disso, você deve seguir as seguintes diretrizes.  
  
-   A especificação XML 1.0 se reserva todos os nomes que começam com a seqüência de caracteres "xml", de qualquer variação de maiúsculas e minúsculas.  Portanto, não use esses nomes para o elemento e atributo.  
  
### Diretrizes para Comprimento de Nomes  
 Na prática, um nome deve ser mais curto possível enquanto ainda claramente identifica a natureza do elemento.  Isso melhora a legibilidade do código e reduz o comprimento da linha e o tamanho do arquivo\-fonte.  
  
 No entanto, seu nome não deve ser tão curto que ele não adequada de descrever o elemento ou como seu código usa.  Isso é importante para a legibilidade do código.  Se alguém está tentando entendê\-lo, ou se você mesmo estiver observando\-muito tempo depois que você escreveu, nomes de elemento apropriado podem economizar tempo.  
  
## Sensibilidade a Maiúsculas em Nomes  
 Os nomes de elementos XML diferenciam maiúsculas de minúsculas.  Isso significa que, quando o [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilador compara dois nomes diferentes no caso de alfabética apenas, ele interpreta como diferentes nomes.  Por exemplo, ele interpreta `ABC` e `abc` como referência para separar elementos.  
  
## Namespaces XML  
 Ao criar um elemento XML literal, você pode especificar o prefixo de namespace XML para o nome do elemento.  Para obter mais informações, consulte [Literal do elemento XML](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).  
  
## Consulte também  
 [Criando XML no Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)   
 [Literal do elemento XML](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)