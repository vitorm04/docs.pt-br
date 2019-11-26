---
title: 'Como: Alterar o namespace XML para uma árvore inteira'
ms.date: 07/20/2015
ms.assetid: 1837324b-5cb5-4fa8-95b9-3071efa0f913
ms.openlocfilehash: 37edb426b106d3fbf90ea06118526abab0a78bf8
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346920"
---
# <a name="how-to-change-the-namespace-for-an-entire-xml-tree-visual-basic"></a>How to: Change the Namespace for an Entire XML Tree (Visual Basic)
Às vezes você tem que alterar programaticamente ao namespace para um elemento ou atributo. LINQ to XML faz isso fácil. A propriedade de <xref:System.Xml.Linq.XElement.Name%2A?displayProperty=nameWithType> pode ser definida. A propriedade de <xref:System.Xml.Linq.XAttribute.Name%2A?displayProperty=nameWithType> não pode ser definida, mas você pode facilmente copiar os atributos em <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>, remover os atributos existentes, e então adiciona novos atributos que estão no novo namespace desejada.  
  
 For more information, see [Namespaces Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).  
  
## <a name="example"></a>Exemplo  
 O código a seguir cria duas árvores XML em qualquer namespace. Altera o namespace de cada uma das árvores, e as combina em uma única árvore.  
  
```vb  
Dim tree1 As XElement = _  
    <Data>  
        <Child MyAttr="content">content</Child>  
    </Data>  
Dim tree2 As XElement = _  
    <Data>  
        <Child MyAttr="content">content</Child>  
    </Data>  
Dim aw As XNamespace = "http://www.adventure-works.com"  
Dim ad As XNamespace = "http://www.adatum.com"  
' change the namespace of every element and attribute in the first tree  
For Each el As XElement In tree1.DescendantsAndSelf  
    el.Name = aw.GetName(el.Name.LocalName)  
    Dim atList As List(Of XAttribute) = el.Attributes().ToList()  
    el.Attributes().Remove()  
    For Each at As XAttribute In atList  
        el.Add(New XAttribute(aw.GetName(at.Name.LocalName), at.Value))  
    Next  
Next  
' change the namespace of every element and attribute in the second tree  
For Each el As XElement In tree2.DescendantsAndSelf()  
    el.Name = ad.GetName(el.Name.LocalName)  
    Dim atList As List(Of XAttribute) = el.Attributes().ToList()  
    el.Attributes().Remove()  
    For Each at As XAttribute In atList  
        el.Add(New XAttribute(ad.GetName(at.Name.LocalName), at.Value))  
    Next  
Next  
' add attribute namespaces so that the tree will be serialized with  
' the aw and ad namespace prefixes  
tree1.Add( _  
    New XAttribute(XNamespace.Xmlns + "aw", "http://www.adventure-works.com") _  
)  
tree2.Add( _  
    New XAttribute(XNamespace.Xmlns + "ad", "http://www.adatum.com") _  
)  
' create a new composite tree  
Dim root As XElement = _  
    <Root>  
        <%= tree1 %>  
        <%= tree2 %>  
    </Root>  
Console.WriteLine(root)  
```  
  
 Este exemplo gera a seguinte saída:  
  
```xml  
<Root>  
  <aw:Data xmlns:aw="http://www.adventure-works.com">  
    <aw:Child aw:MyAttr="content">content</aw:Child>  
  </aw:Data>  
  <ad:Data xmlns:ad="http://www.adatum.com">  
    <ad:Child ad:MyAttr="content">content</ad:Child>  
  </ad:Data>  
</Root>  
```  
  
## <a name="see-also"></a>Consulte também

- [Modifying XML Trees (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
