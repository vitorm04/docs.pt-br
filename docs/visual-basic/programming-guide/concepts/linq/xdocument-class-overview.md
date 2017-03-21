---
title: "Visão geral da classe XDocument (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 45cb7e71-196a-47da-bfe9-7a5589db1eed
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 31111b23adb019aad3ad55787c073dc02446291d
ms.lasthandoff: 03/13/2017

---
# <a name="xdocument-class-overview-visual-basic"></a>Visão geral da classe XDocument (Visual Basic)
Este tópico apresenta a <xref:System.Xml.Linq.XDocument>classe.</xref:System.Xml.Linq.XDocument>  
  
## <a name="overview-of-the-xdocument-class"></a>Visão geral da classe XDocument  
 O <xref:System.Xml.Linq.XDocument>classe contém as informações necessárias para um documento XML válido.</xref:System.Xml.Linq.XDocument> Isso inclui uma declaração XML, instruções de processamento e comentários.  
  
 Observe que você só precisa criar <xref:System.Xml.Linq.XDocument>objetos, se você precisar da funcionalidade específica fornecida pela <xref:System.Xml.Linq.XDocument>classe.</xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XDocument> Em muitas circunstâncias, você pode trabalhar diretamente com <xref:System.Xml.Linq.XElement>.</xref:System.Xml.Linq.XElement> Trabalhar diretamente com <xref:System.Xml.Linq.XElement>é um modelo de programação mais simples.</xref:System.Xml.Linq.XElement>  
  
 <xref:System.Xml.Linq.XDocument>deriva de <xref:System.Xml.Linq.XContainer>.</xref:System.Xml.Linq.XContainer></xref:System.Xml.Linq.XDocument> Portanto, pode conter nós filho. No entanto, <xref:System.Xml.Linq.XDocument>objetos podem ter apenas um filho <xref:System.Xml.Linq.XElement>nó.</xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XDocument> Isso reflete o padrão XML de que pode haver apenas um elemento raiz em um documento XML.  
  
## <a name="components-of-xdocument"></a>Componentes de XDocument  
 Um <xref:System.Xml.Linq.XDocument>pode conter os seguintes elementos:</xref:System.Xml.Linq.XDocument>  
  
-   Um <xref:System.Xml.Linq.XDeclaration>objeto.</xref:System.Xml.Linq.XDeclaration> <xref:System.Xml.Linq.XDeclaration>permite que você especifique as partes pertinentes de uma declaração XML: a versão XML, a codificação do documento, e se o documento XML é autônomo.</xref:System.Xml.Linq.XDeclaration>  
  
-   Um <xref:System.Xml.Linq.XElement>objeto.</xref:System.Xml.Linq.XElement> Esse é o nó raiz do documento XML.  
  
-   Qualquer número de <xref:System.Xml.Linq.XProcessingInstruction>objetos.</xref:System.Xml.Linq.XProcessingInstruction> Uma instrução de processamento comunica informações a um aplicativo que processa o XML.  
  
-   Qualquer número de <xref:System.Xml.Linq.XComment>objetos.</xref:System.Xml.Linq.XComment> Os comentários serão irmãos do elemento raiz. O <xref:System.Xml.Linq.XComment>objeto não pode ser o primeiro argumento na lista, porque ele não é válido para um documento XML iniciar com um comentário.</xref:System.Xml.Linq.XComment>  
  
-   Um <xref:System.Xml.Linq.XDocumentType>para o DTD.</xref:System.Xml.Linq.XDocumentType>  
  
 Quando você serializa um <xref:System.Xml.Linq.XDocument>, mesmo se `XDocument.Declaration` é `null`, a saída terá uma declaração XML se o gravador tiver `Writer.Settings.OmitXmlDeclaration` definida como `false` (o padrão).</xref:System.Xml.Linq.XDocument>  
  
 Por padrão, o [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] define a versão como “1.0 " e a codificação como “utf-8”.  
  
## <a name="using-xelement-without-xdocument"></a>Usando XElement sem XDocument  
 Como mencionado anteriormente, a <xref:System.Xml.Linq.XElement>classe é a classe principal do [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] interface de programação.</xref:System.Xml.Linq.XElement> Em muitos casos, seu aplicativo não exigirá que você cria um documento. Usando o <xref:System.Xml.Linq.XElement>classe, criar uma árvore XML, adicionar outras árvores XML a ela, modificar a árvore XML e salvá-la</xref:System.Xml.Linq.XElement>  
  
## <a name="using-xdocument"></a>Usando XDocument  
 Para construir um <xref:System.Xml.Linq.XDocument>, use a construção funcional exatamente como você faz para construir <xref:System.Xml.Linq.XElement>objetos.</xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XDocument>  
  
 O código a seguir cria um <xref:System.Xml.Linq.XDocument>objeto e seus associados objetos contidos.</xref:System.Xml.Linq.XDocument>  
  
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
  
 Quando você examina o arquivo test.xml, obtém a seguinte saída:  
  
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
  
## <a name="see-also"></a>Consulte também  
 [LINQ para visão geral da programação XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
