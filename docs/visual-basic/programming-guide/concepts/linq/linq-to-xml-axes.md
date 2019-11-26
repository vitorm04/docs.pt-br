---
title: Eixos LINQ to XML
ms.date: 07/20/2015
ms.assetid: ecd3bd00-28e5-4517-a59f-53bff39fd478
ms.openlocfilehash: 73c5325c23c4724a28a123af5c2f8c25b2fd02de
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352014"
---
# <a name="linq-to-xml-axes-visual-basic"></a>LINQ to XML Axes (Visual Basic)
Após criar uma árvore XML ou carregar um documento XML em uma árvore XML, você poderá consultá-la para localizar elementos e atributos, e recuperar seus valores.  
  
 Antes de poder criar consultas, você deve entender os eixos [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]. Há dois tipos de métodos de eixo: primeiro, existem métodos que você chama em um único objeto <xref:System.Xml.Linq.XElement>, objeto <xref:System.Xml.Linq.XDocument> ou objeto <xref:System.Xml.Linq.XNode>. Esses métodos operam em um único objeto e retornam uma coleção de objetos <xref:System.Xml.Linq.XElement>, <xref:System.Xml.Linq.XAttribute> ou <xref:System.Xml.Linq.XNode>. Segundo, existem métodos de extensão que operam em coleções e retornam coleções. Os métodos de extensão enumeram a coleção de origem, chamam o método de eixo apropriado em cada item na coleção e concatenam os resultados.  
  
## <a name="in-this-section"></a>Nesta seção  
  
|Tópico|Descrição|  
|-----------|-----------------|  
|[LINQ to XML Axes Overview (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes-overview.md)|Define os eixos e explica como eles são usados no contexto de consultas [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].|  
|[How to: Retrieve a Collection of Elements (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-a-collection-of-elements-linq-to-xml.md)|Apresenta o método <xref:System.Xml.Linq.XContainer.Elements%2A>. Esse método retorna uma coleção de elementos filho de um elemento.|  
|[How to: Retrieve the Value of an Element (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-element-linq-to-xml.md)|Mostra como obter os valores de elementos.|  
|[How to: Filter on Element Names (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-filter-on-element-names-linq-to-xml.md)|Mostra como filtrar em nomes de elementos ao usar eixos.|  
|[How to: Chain Axis Method Calls (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-chain-axis-method-calls-linq-to-xml.md)|Mostra como encadear chamadas a métodos de eixos.|  
|[How to: Retrieve a Single Child Element (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-a-single-child-element-linq-to-xml.md)|Mostra como recuperar um único elemento filho de um elemento, dado o nome da marca do elemento filho.|  
|[How to: Retrieve a Collection of Attributes (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-a-collection-of-attributes-linq-to-xml.md)|Apresenta o método <xref:System.Xml.Linq.XElement.Attributes%2A>. Esse método recupera os atributos de um elemento.|  
|[How to: Retrieve a Single Attribute (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-a-single-attribute-linq-to-xml.md)|Mostra como recuperar um único atributo de um elemento, dado o nome do atributo.|  
|[How to: Retrieve the Value of an Attribute (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-attribute-linq-to-xml.md)|Mostra como obter os valores de atributos.|  
|[How to: Retrieve the Shallow Value of an Element (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-the-shallow-value-of-an-element.md)|Mostra como recuperar o valor superficial de um elemento.|  
|[Language-Integrated Axes in Visual Basic (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/language-integrated-axes.md)|Summarizes the Visual Basic integrated axes.|  
  
## <a name="see-also"></a>Consulte também

- [Programming Guide (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)
