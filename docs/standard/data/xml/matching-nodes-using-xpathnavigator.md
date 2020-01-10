---
title: Nós compatíveis usando XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: e6848c47-ee5d-401a-89a5-50b5eed40f30
ms.openlocfilehash: f0988c3a112fefc351175de02c790dc25fe6e94a
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710681"
---
# <a name="matching-nodes-using-xpathnavigator"></a>Nós compatíveis usando XPathNavigator
A classe de <xref:System.Xml.XPath.XPathNavigator> fornece o método de <xref:System.Xml.XPath.XPathNavigator.Matches%2A> para determinar se um nó corresponde uma expressão XPath. O método de <xref:System.Xml.XPath.XPathNavigator.Matches%2A> usa uma expressão XPath como entrada e retorna <xref:System.Boolean> que indica se o nó atual corresponde a expressão XPath determinada ou o objeto compilado dado de <xref:System.Xml.XPath.XPathExpression> .  
  
## <a name="matching-nodes"></a>Nós compatíveis  
 O método de <xref:System.Xml.XPath.XPathNavigator.Matches%2A> retorna `true` se o nó atual corresponde a expressão XPath especificada. Por exemplo, no exemplo de código que segue, o método de <xref:System.Xml.XPath.XPathNavigator.Matches%2A> retornará `true` se o nó atual é o elemento `b`, e o elemento `b` tem um atributo `c`.  
  
> [!NOTE]
> O método de <xref:System.Xml.XPath.XPathNavigator.Matches%2A> não altera o estado de <xref:System.Xml.XPath.XPathNavigator>.  
  
```vb  
Dim document as XPathDocument = New XPathDocument("input.xml")  
Dim navigator as XPathNavigator = document.CreateNavigator()  
  
navigator.Matches("b[@c]")  
```  
  
```csharp  
XPathDocument document = new XPathDocument("input.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
navigator.Matches("b[@c]");  
```  
  
## <a name="see-also"></a>Veja também

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [Processar dados XML usando o modelo de dados XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [Selecionar dados XML usando XPathNavigator](../../../../docs/standard/data/xml/select-xml-data-using-xpathnavigator.md)
- [Avaliar as expressões XPath usando XPathNavigator](../../../../docs/standard/data/xml/evaluate-xpath-expressions-using-xpathnavigator.md)
- [Tipos de nós reconhecidos com consultas XPath](../../../../docs/standard/data/xml/node-types-recognized-with-xpath-queries.md)
- [Consultas e Namespaces de XPath](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)
- [Expressões XPath compilados](../../../../docs/standard/data/xml/compiled-xpath-expressions.md)
