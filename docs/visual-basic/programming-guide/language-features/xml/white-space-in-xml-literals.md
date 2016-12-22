---
title: "Espa&#231;o em branco em literais XML (Visual Basic) | Microsoft Docs"
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
  - "espaço em branco [XML no Visual Basic]"
  - "literais XML [Visual Basic], espaço em branco"
ms.assetid: dfe3a9ff-d69a-418e-a6b5-476f4ed84219
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Espa&#231;o em branco em literais XML (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

O [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilador incorpora apenas os caracteres de espaço em branco significativo de um literal XML quando cria um [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] objeto.  Os caracteres insignificante espaços em branco não são incorporados.  
  
## Espaços em branco significativo e insignificante  
 Caracteres de espaço em branco em literais XML são significativos em apenas três áreas:  
  
-   Quando estão em um valor de atributo.  
  
-   Quando eles fazem parte do conteúdo de texto de um elemento e o texto também contém outros caracteres.  
  
-   Quando estão em uma expressão incorporada para o conteúdo de texto de um elemento.  
  
 Caso contrário, o compilador trata os caracteres de espaço em branco como insignificante e inclua, em seguida, o [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] o objeto para o literal.  
  
 Para incluir espaços em branco não significativos em um literal XML, use uma expressão incorporada que contém uma seqüência literal com o espaço em branco.  
  
> [!NOTE]
>  Se a `xml:space` atributo será exibida em um elemento XML literal, o [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilador inclui o atributo na <xref:System.Xml.Linq.XElement> objeto, mas adicionando este atributo não é alterado, como o compilador trata o espaço em branco.  
  
## Exemplos  
 O exemplo a seguir contém dois elementos XML, externos e internos.  Ambos os elementos podem conter espaços em branco no conteúdo do texto.  O espaço em branco no elemento externo é insignificante, pois ele contém somente espaços em branco e um elemento XML.  O espaço em branco no elemento interno é significativo porque contém espaços em branco e texto.  
  
 [!CODE [VbXMLSamples#29](../CodeSnippet/VS_Snippets_VBCSharp/VbXMLSamples#29)]  
  
 Quando executado, esse código exibe o texto a seguir.  
  
```  
<outer>  
  <inner>  
                                          Inner text  
                                      </inner>  
</outer>  
```  
  
## Consulte também  
 [Criando XML no Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)