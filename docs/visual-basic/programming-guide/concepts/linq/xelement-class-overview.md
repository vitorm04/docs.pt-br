---
title: "Vis&#227;o geral da classe de XElement (Visual Basic) | Microsoft Docs"
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
ms.assetid: 52331fcd-6023-4d19-b423-7b24f2d86ded
caps.latest.revision: 3
caps.handback.revision: 3
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Vis&#227;o geral da classe de XElement (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

O <xref:System.Xml.Linq.XElement> classe é uma das classes fundamentais no [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]. Representa um elemento XML. Você pode usar essa classe para criar elementos; alterar o conteúdo do elemento; Adicionar, alterar ou excluir elementos filho; Adicionar atributos a um elemento. ou serializar o conteúdo de um elemento na forma de texto. Você também pode interoperar com outras classes no <xref:System.Xml?displayProperty=fullName>, como <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, e <xref:System.Xml.Xsl.XslCompiledTransform>.  
  
## Funcionalidade de XElement  
 Este tópico descreve a funcionalidade fornecida pelo <xref:System.Xml.Linq.XElement> classe.  
  
### Construindo árvores XML  
 Você pode construir árvores XML de várias maneiras, incluindo o seguinte:  
  
-   Você pode construir uma árvore XML no código. Para obter mais informações, consulte [Criando árvores XML \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md).  
  
-   Você pode analisar o XML de várias fontes, incluindo um <xref:System.IO.TextReader>, arquivos de texto ou um endereço Web \(URL\). Para obter mais informações, consulte [Análise de XML \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md).  
  
-   Você pode usar um <xref:System.Xml.XmlReader> para popular a árvore. Para obter mais informações, consulte <xref:System.Xml.Linq.XNode.ReadFrom%2A>.  
  
-   Se você tiver um módulo que possa gravar conteúdo em um <xref:System.Xml.XmlWriter>, você pode usar o <xref:System.Xml.Linq.XContainer.CreateWriter%2A> método para criar um gravador, passar o gravador para o módulo e, em seguida, usar o conteúdo gravado para o <xref:System.Xml.XmlWriter> para popular a árvore XML.  
  
 No entanto, a maneira mais comum para criar uma árvore XML é da seguinte maneira:  
  
```vb  
Dim contacts As XElement = _  
    <Contacts>  
        <Contact>  
            <Name>Patrick Hines</Name>  
            <Phone>206-555-0144</Phone>  
            <Address>  
                <Street1>123 Main St</Street1>  
                <City>Mercer Island</City>  
                <State>WA</State>  
                <Postal>68042</Postal>  
            </Address>  
        </Contact>  
    </Contacts>  
```  
  
 Outra técnica muito comum para a criação de uma árvore XML envolve usando os resultados de uma [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] consulta para preencher uma árvore XML, conforme mostrado no exemplo a seguir:  
  
```vb  
Dim srcTree As XElement = _  
    <Root>  
        <Element>1</Element>  
        <Element>2</Element>  
        <Element>3</Element>  
        <Element>4</Element>  
        <Element>5</Element>  
    </Root>  
Dim xmlTree As XElement = _  
    <Root>  
        <Child>1</Child>  
        <Child>2</Child>  
        <%= From el In srcTree.Elements() _  
            Where el.Value > 2 _  
            Select el %>  
    </Root>  
Console.WriteLine(xmlTree)  
```  
  
 Este exemplo produz a seguinte saída:  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Element>3</Element>  
  <Element>4</Element>  
  <Element>5</Element>  
</Root>  
```  
  
### Serializando árvores XML  
 Você pode serializar a árvore XML para um <xref:System.IO.File>, um <xref:System.IO.TextWriter>, ou um <xref:System.Xml.XmlWriter>.  
  
 Para obter mais informações, consulte [Serializando árvores XML \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/linq/serializing-xml-trees.md).  
  
### Recuperando dados XML por meio de métodos de eixo  
 Você pode usar métodos de eixo para recuperar elementos filho, atributos, elementos descendentes e elementos ancestrais.[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] consultas operam em métodos de eixo e fornecem várias maneiras flexíveis e eficientes para navegar e processar uma árvore XML.  
  
 Para obter mais informações, consulte [Eixos LINQ to XML \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md).  
  
### Consultando árvores XML  
 Você pode escrever [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] consultas que extraem dados de uma árvore XML.  
  
 Para obter mais informações, consulte [Querying XML Trees \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/linq/querying-xml-trees.md).  
  
### Modificando árvores XML  
 Você pode modificar um elemento de várias maneiras, incluindo alterar seu conteúdo ou atributos. Você também pode remover um elemento de seu pai.  
  
 Para obter mais informações, consulte [Modifying XML Trees \(LINQ to XML\) \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md).  
  
## Consulte também  
 [LINQ para visão geral da programação XML \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)