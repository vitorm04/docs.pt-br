---
title: Usuários de LINQ to XML para XPath
ms.date: 07/20/2015
ms.assetid: 0e64911c-a7cc-4c20-b927-ca99078b5656
ms.openlocfilehash: 4d5749e72acc8b051db2180b751051696ae04d57
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345462"
---
# <a name="linq-to-xml-for-xpath-users-visual-basic"></a>LINQ to XML for XPath Users (Visual Basic)

Este conjunto de tópicos mostra algumas expressões XPath e seus equivalentes [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].  
  
 Todos os exemplos usam a funcionalidade XPath no [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] disponibilizada pelos métodos de extensão em <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>. Os exemplos executam a expressão XPath e a expressão [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]. Cada exemplo compara os resultados das duas consultas, validando se a expressão XPath é funcionalmente equivalente à consulta [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]. Como os dois tipos de consultas retornam nós da mesma árvore XML, a comparação do resultado da consulta é feita usando identidade referencial.  
  
## <a name="in-this-section"></a>Nesta seção  
  
|Tópico|Descrição|  
|-----------|-----------------|  
|[Comparação de XPath e de LINQ to XML](../../../../csharp/programming-guide/concepts/linq/comparison-of-xpath-and-linq-to-xml.md)|Apresenta uma visão geral das semelhanças e das diferenças entre XPath e [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].|  
|[How to: Find a Child Element (XPath-LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-a-child-element-xpath-linq-to-xml.md)|Compara o eixo do elemento filho XPath com o método [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.Linq.XContainer.Element%2A>.<br /><br /> A expressão XPath associada é:`"DeliveryNotes"`.|  
|[How to: Find a List of Child Elements (XPath-LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-a-list-of-child-elements-xpath-linq-to-xml.md)|Compara o eixo de elementos filho XPath com o eixo [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.Linq.XContainer.Elements%2A>.<br /><br /> A expressão XPath associada é:`"./*"`|  
|[How to: Find the Root Element (XPath-LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-the-root-element-xpath-linq-to-xml.md)|Compara como obter o elemento raiz com XPath e [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].<br /><br /> A expressão XPath associada é:`"/PurchaseOrders"`|  
|[How to: Find Descendant Elements (XPath-LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-descendant-elements-xpath-linq-to-xml.md)|Compara como obter os elementos descendentes com um nome específico com XPath e [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].<br /><br /> A expressão XPath associada é:`"//Name"`|  
|[How to: Filter on an Attribute (XPath-LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-filter-on-an-attribute-xpath-linq-to-xml.md)|Compara como obter os elementos descendentes com um nome especificado e com um atributo com um valor especificado com XPath e [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].<br /><br /> A expressão XPath associada é:`"./Address[@Type='Shipping']"`|  
|[How to: Find Related Elements (XPath-LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-related-elements-xpath-linq-to-xml.md)|Compara como obter um elemento selecionando em um atributo que é referenciado pelo valor de outro elemento com XPath e [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].<br /><br /> A expressão XPath associada é:`"./Customer[@CustomerID=/Root/Orders/Order[12]/CustomerID]"`|  
|[How to: Find Elements in a Namespace (XPath-LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-elements-in-a-namespace.md)|Compara o uso da classe XPath <xref:System.Xml.XmlNamespaceManager> com a propriedade [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.Linq.XName.Namespace%2A> da classe <xref:System.Xml.Linq.XName> para trabalhar com namespaces XML.<br /><br /> A expressão XPath associada é:`"./aw:*"`|  
|[How to: Find Preceding Siblings (XPath-LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-preceding-siblings-xpath-linq-to-xml.md)|Compara o eixo XPath `preceding-sibling` com o eixo [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] filho <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType>.<br /><br /> A expressão XPath associada é:`"preceding-sibling::*"`|  
|[How to: Find Descendants of a Child Element (XPath-LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-descendants-of-a-child-element-xpath-linq-to-xml.md)|Compara como obter os elementos descendentes de um elemento filho com um nome específico com XPath e [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].<br /><br /> A expressão XPath associada é:`"./Paragraph//Text/text()"`|  
|[How to: Find a Union of Two Location Paths (XPath-LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-a-union-of-two-location-paths-xpath.md)|Compara o uso do operador de união, <code>&#124;</code>, no XPath com o operador de consulta padrão <xref:System.Linq.Enumerable.Concat%2A> em [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].<br /><br /> A expressão XPath associada é:<code>"//Category&#124;//Price"</code>|  
|[How to: Find Sibling Nodes (XPath-LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-sibling-nodes-xpath-linq-to-xml.md)|Compara como localizar todos os irmãos de um nó que têm um nome específico com XPath e [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].<br /><br /> A expressão XPath associada é:`"../Book"`|  
|[How to: Find an Attribute of the Parent (XPath-LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-an-attribute-of-the-parent-xpath-linq-to-xml.md)|Compara como navegar para o elemento pai e localizar um atributo associado usando XPath e [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].<br /><br /> A expressão XPath associada é:`"../@id"`|  
|[How to: Find Attributes of Siblings with a Specific Name (XPath-LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-attributes-of-siblings-with-a-specific-name.md)|Compara como localizar atributos específicos dos irmãos do nó de contexto com XPath e [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].<br /><br /> A expressão XPath associada é:`"../Book/@id"`|  
|[How to: Find Elements with a Specific Attribute (XPath-LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-elements-with-a-specific-attribute.md)|Compara como localizar todos os elementos que contêm um atributo específico usando XPath e [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].<br /><br /> A expressão XPath associada é:`"./*[@Select]"`|  
|[How to: Find Child Elements Based on Position (XPath-LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-child-elements-based-on-position.md)|Compara como localizar um elemento com base em sua posição relativa usando XPath e [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].<br /><br /> A expressão XPath associada é:`"Test[position() >= 2 and position() <= 4]"`|  
|[How to: Find the Immediate Preceding Sibling (XPath-LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-the-immediate-preceding-sibling-xpath-linq-to-xml.md)|Compara como localizar o irmão imediatamente precedente de um nó usando XPath e [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].<br /><br /> A expressão XPath associada é:`"preceding-sibling::*[1]"`|  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Xml.XPath?displayProperty=nameWithType>
- [Querying XML Trees (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/querying-xml-trees.md)
- [Processar dados XML usando o modelo de dados XPath](../../../../standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
