---
title: "Como inserir express&#245;es em literais XML (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "expressões inseridas [Visual Basic]"
  - "literais XML [Visual Basic], expressões inseridas"
ms.assetid: 75016fad-0141-42de-8564-5051be29487e
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como inserir express&#245;es em literais XML (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Você pode combinar literais XML com espressões embutidas para criar um documento XML, fragmento ou elemento que contenha o conteúdo criado no momento de execução.  Os exemplos a seguir demonstram como usar expressões embutidas para gerar conteúdo de elemento, atributos e nomes de elementos no momento de execução.  
  
 A sintaxe de uma expressão incorporada é `<%=``exp``%>`, que é a mesma sintaxe que [!INCLUDE[vstecasp](../../../../visual-basic/developing-apps/programming/drives-directories-files/includes/vstecasp_md.md)] usa. Para obter mais informações, consulte [Expressões inseridas no XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).  
  
 Você também pode usar os APIs [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] para criar objetos [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].  Para obter mais informações, consulte <xref:System.Xml.Linq.XElement>.  
  
## Procedimentos  
  
#### Para inserir texto como conteúdo de elemento  
  
-   O exemplo a seguir mostra como inserir o texto que está contido na variável `contactName` entre os nomes de elementos de abertura e fechamento.  
  
     [!CODE [VbXMLSamples#39](../CodeSnippet/VS_Snippets_VBCSharp/VbXMLSamples#39)]  
  
     Esse exemplo produz a seguinte saída.  
  
    ```  
    <contact>  
      <name>Patrick Hines</name>  
    </contact>  
    ```  
  
#### Para inserir texto como um valor de atributo:  
  
-   O exemplo a seguir mostra como inserir o texto que está contido na variável `phoneType` como o valor para o atributo `type`.  
  
     [!CODE [VbXMLSamples#40](../CodeSnippet/VS_Snippets_VBCSharp/VbXMLSamples#40)]  
  
     Esse exemplo produz a seguinte saída.  
  
    ```  
    <contact>  
      <phone type="home">206-555-0144</phone>  
    </contact>  
    ```  
  
#### Para inserir texto para um nome de elemento  
  
-   O exemplo a seguir mostra como inserir texto que está contido na variável `elementName` como o nome de um elemento.  
  
     Quando criar elementos usando esta técnica, você deve fechá\-los com a etiqueta \<\/\>.  
  
     [!CODE [VbXMLSamples#41](../CodeSnippet/VS_Snippets_VBCSharp/VbXMLSamples#41)]  
  
     Esse exemplo produz a seguinte saída.  
  
    ```  
    <contact>  
      <name>Patrick Hines</name>  
    </contact>  
    ```  
  
## Consulte também  
 [Como criar literais XML](../Topic/How%20to:%20Create%20XML%20Literals%20\(Visual%20Basic\).md)   
 [Expressões inseridas no XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)   
 [Criando XML no Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)   
 [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)