---
title: Modificando elementos, atributos e nós em um Tree1 XML
ms.date: 07/20/2015
ms.assetid: 865cf54e-f8ac-4871-863b-a3e6fc61a4b9
ms.openlocfilehash: d548e6f5912437e5c5df27f55fcdb28990e92c8d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61666138"
---
# <a name="modifying-elements-attributes-and-nodes-in-an-xml-tree"></a>Modificando elementos, atributos e nós em uma árvore XML
A tabela a seguir resume os métodos e as propriedades que você pode usar para modificar um elemento, seus elementos filho ou seus atributos.  
  
 Os seguintes métodos modificam uma classe <xref:System.Xml.Linq.XElement>.  
  
|Método|Descrição|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>|Substitui um elemento pelo XML analisado.|  
|<xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=nameWithType>|Remove todo o conteúdo (nós filho e atributos) de um elemento.|  
|<xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=nameWithType>|Remove os atributos de um elemento.|  
|<xref:System.Xml.Linq.XElement.ReplaceAll%2A?displayProperty=nameWithType>|Substitui todo o conteúdo (nós filho e atributos) de um elemento.|  
|<xref:System.Xml.Linq.XElement.ReplaceAttributes%2A?displayProperty=nameWithType>|Substitui os atributos de um elemento.|  
|<xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=nameWithType>|Define o valor de um atributo. Cria o atributo se ele não existir. Se o valor for definido como `null`, o método removerá o atributo.|  
|<xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=nameWithType>|Define o valor de um elemento filho. Cria o elemento se ele não existir. Se o valor for definido como `null`, o método removerá o elemento.|  
|<xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType>|Substitui o conteúdo (nós filho) de um elemento pelo texto especificado.|  
|<xref:System.Xml.Linq.XElement.SetValue%2A?displayProperty=nameWithType>|Define o valor de um elemento.|  
  
 Os seguintes métodos modificam uma classe <xref:System.Xml.Linq.XAttribute>.  
  
|Método|Descrição|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType>|Define o valor de um atributo.|  
|<xref:System.Xml.Linq.XAttribute.SetValue%2A?displayProperty=nameWithType>|Define o valor de um atributo.|  
  
 Os seguintes métodos modificam uma classe <xref:System.Xml.Linq.XNode> (incluindo <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XDocument>).  
  
|Método|Descrição|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.ReplaceWith%2A?displayProperty=nameWithType>|Substitui um nó pelo novo conteúdo.|  
  
 Os métodos a seguir modificam uma classe <xref:System.Xml.Linq.XContainer> (<xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XDocument>).  
  
|Método|Descrição|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XContainer.ReplaceNodes%2A?displayProperty=nameWithType>|Substitui os nós filho pelo novo conteúdo.|  
  
## <a name="see-also"></a>Consulte também

- [Modificando árvores XML (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
