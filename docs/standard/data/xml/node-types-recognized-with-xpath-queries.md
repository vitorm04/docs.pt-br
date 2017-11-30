---
title: "Tipos de nós reconhecidos com consultas XPath"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1d33e22d-18e5-43f8-a466-2e3d0a8dd094
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 1c1e48bbfd6388686fdb83f08668f7f0234275a5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="node-types-recognized-with-xpath-queries"></a>Tipos de nós reconhecidos com consultas XPath
Os tipos de nós reconhecidas em uma consulta XPath não são os mesmos tipos de nós localizados em Document Object Model (DOM).  
  
## <a name="w3c-xpath-node-types"></a>Tipos de nós XPath W3C  
 Os tipos de nós reconhecidas em uma consulta XPath não são tipos de nós localizados em Document Object Model (DOM). A seguir estão os tipos de nós XPath representados pela enumeração de <xref:System.Xml.XPath.XPathNodeType> .  
  
-   <xref:System.Xml.XPath.XPathNodeType.All>  
  
-   <xref:System.Xml.XPath.XPathNodeType.Attribute>  
  
-   <xref:System.Xml.XPath.XPathNodeType.Comment>  
  
-   <xref:System.Xml.XPath.XPathNodeType.Element>  
  
-   <xref:System.Xml.XPath.XPathNodeType.Namespace>  
  
-   <xref:System.Xml.XPath.XPathNodeType.ProcessingInstruction>  
  
-   <xref:System.Xml.XPath.XPathNodeType.Root>  
  
-   <xref:System.Xml.XPath.XPathNodeType.SignificantWhitespace>  
  
-   <xref:System.Xml.XPath.XPathNodeType.Text>  
  
-   <xref:System.Xml.XPath.XPathNodeType.Whitespace>  
  
 Esses tipos de nós são baseados no modelo de dados XPath, onde os nós são derivados do conjunto de informações XML. Os tipos de nós de <xref:System.Xml.XPath.XPathNodeType.SignificantWhitespace> e de <xref:System.Xml.XPath.XPathNodeType.Whitespace> são extensões do Microsoft .NET Framework para tipos de nós de base descritos no modelo de dados XPath.  
  
 O tipo de nó de atributo é usado de forma diferente no modelo de dados XPath do que está em DOM. No modelo de dados XPath, o nó do elemento tem um conjunto de nós de atributo relacionados a ele e o nó do elemento é o pai de cada nó de atributo. No entanto, em DOM, o nó do elemento é o proprietário e não o pai. Em ambos os modelos, o atributo e os nós de namespace não são considerados nós filho do nó do elemento.  
  
 O tipo de nó de namespace é uma adição ao modelo de dados XPath e não é um tipo de nó reconhecido DOM.  
  
 Para obter mais informações sobre como navegar de elemento, atributo e nós de namespace, consulte o [nó definido navegação usando XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md) e [atributo e Namespace nó de navegação usando XPathNavigator](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md) tópicos.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [Processar dados XML usando o modelo de dados XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [Selecionar dados XML usando XPathNavigator](../../../../docs/standard/data/xml/select-xml-data-using-xpathnavigator.md)  
 [Avalia as expressões XPath usando XPathNavigator](../../../../docs/standard/data/xml/evaluate-xpath-expressions-using-xpathnavigator.md)  
 [Nós compatíveis usando XPathNavigator](../../../../docs/standard/data/xml/matching-nodes-using-xpathnavigator.md)  
 [Consultas XPath e namespaces](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)  
 [Expressões XPath compilados](../../../../docs/standard/data/xml/compiled-xpath-expressions.md)
