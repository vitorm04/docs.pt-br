---
title: "Vis&#227;o geral da classe XDocument (Visual Basic) | Microsoft Docs"
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
ms.assetid: 45cb7e71-196a-47da-bfe9-7a5589db1eed
caps.latest.revision: 3
caps.handback.revision: 3
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Vis&#227;o geral da classe XDocument (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Este tópico apresenta o <xref:System.Xml.Linq.XDocument> classe.  
  
## Visão geral da classe XDocument  
 O <xref:System.Xml.Linq.XDocument> classe contém as informações necessárias para um documento XML válido. Isso inclui uma declaração XML, instruções de processamento e comentários.  
  
 Observe que você precisa criar <xref:System.Xml.Linq.XDocument> objetos se você precisa da funcionalidade específica fornecida pelo <xref:System.Xml.Linq.XDocument> classe. Em muitas circunstâncias, você pode trabalhar diretamente com <xref:System.Xml.Linq.XElement>. Trabalhar diretamente com <xref:System.Xml.Linq.XElement> é um modelo de programação mais simples.  
  
 <xref:System.Xml.Linq.XDocument> deriva de <xref:System.Xml.Linq.XContainer>. Portanto, ele pode conter nós filho. No entanto, <xref:System.Xml.Linq.XDocument> objetos podem ter apenas um filho <xref:System.Xml.Linq.XElement> nó. Isso reflete o padrão XML que pode haver somente um elemento raiz em um documento XML.  
  
## Componentes de XDocument  
 Um <xref:System.Xml.Linq.XDocument> pode conter os seguintes elementos:  
  
-   Um <xref:System.Xml.Linq.XDeclaration> objeto.<xref:System.Xml.Linq.XDeclaration> permite que você especifique as partes pertinentes de uma declaração XML: a versão XML, a codificação do documento, e se o documento XML é autônomo.  
  
-   Um <xref:System.Xml.Linq.XElement> objeto. Esse é o nó raiz do documento XML.  
  
-   Qualquer número de <xref:System.Xml.Linq.XProcessingInstruction> objetos. Uma instrução de processamento comunica informações a um aplicativo que processa o XML.  
  
-   Qualquer número de <xref:System.Xml.Linq.XComment> objetos. Os comentários serão irmãos do elemento raiz. O <xref:System.Xml.Linq.XComment> objeto não pode ser o primeiro argumento na lista, porque ele não é válido para um documento XML iniciar com um comentário.  
  
-   Um <xref:System.Xml.Linq.XDocumentType> para o DTD.  
  
 Quando você serializa um <xref:System.Xml.Linq.XDocument>, mesmo se `XDocument.Declaration` for `null`, a saída terá uma declaração XML se o gravador tiver `Writer.Settings.OmitXmlDeclaration` definida como `false` \(o padrão\).  
  
 Por padrão, [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] define a versão como "1.0" e define a codificação como "utf\-8".  
  
## Usando XElement sem XDocument  
 Como mencionado anteriormente, a <xref:System.Xml.Linq.XElement> classe é a classe principal do [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] interface de programação. Em muitos casos, seu aplicativo não exigirá que você cria um documento. Usando o <xref:System.Xml.Linq.XElement> classe, criar uma árvore XML, adicionar outras árvores XML a ela, modificar a árvore XML e salvá\-lo.  
  
## Usando XDocument  
 Para construir um <xref:System.Xml.Linq.XDocument>, use a construção funcional exatamente como você faz para construir <xref:System.Xml.Linq.XElement> objetos.  
  
 O código a seguir cria um <xref:System.Xml.Linq.XDocument> objeto e seus associados objetos contidos.  
  
```vb  
Dim doc As XDocument = <?xml version="1.0" encoding="utf-8"?>  
                       <!--This is a comment.-->  
                       <?xml-stylesheet href='mystyle.css' title='Compact' type='text/css'?>  
                       <Pubs>  
                           <Book>  
                               <Title>Artifacts of Roman Civilization</Title>  
                               <Author>Moreno, Jordao</Author>  
                           </Book>  
                           <Book>  
                               <Title>Midieval Tools and Implements</Title>  
                               <Author>Gazit, Inbar</Author>  
                           </Book>  
                       </Pubs>  
                       <!--This is another comment.-->  
doc.Save("test.xml")  
```  
  
 Ao examinar o arquivo Test. XML, você pode obter a seguinte saída:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<!--This is a comment.-->  
<?xml-stylesheet href='mystyle.css' title='Compact' type='text/css'?>  
<Pubs>  
  <Book>  
    <Title>Artifacts of Roman Civilization</Title>  
    <Author>Moreno, Jordao</Author>  
  </Book>  
  <Book>  
    <Title>Midieval Tools and Implements</Title>  
    <Author>Gazit, Inbar</Author>  
  </Book>  
</Pubs>  
<!--This is another comment.-->  
```  
  
## Consulte também  
 [LINQ para visão geral da programação XML \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)