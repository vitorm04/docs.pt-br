---
title: "LINQ to XML para XPath usuários (Visual Basic) | Documentos do Microsoft"
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
ms.assetid: 0e64911c-a7cc-4c20-b927-ca99078b5656
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 376e7d67edf1719dc1a020974b38e3600831d660
ms.lasthandoff: 03/13/2017


---
# <a name="linq-to-xml-for-xpath-users-visual-basic"></a>LINQ to XML para XPath usuários (Visual Basic)
Este conjunto de tópicos mostra algumas expressões XPath e seus equivalentes [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].  
  
 Todos os exemplos usam a funcionalidade do XPath em [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] que é disponibilizado pelos métodos de extensão no <xref:System.Xml.XPath.Extensions?displayProperty=fullName>.</xref:System.Xml.XPath.Extensions?displayProperty=fullName> Os exemplos executam a expressão XPath e a expressão [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]. Cada exemplo compara os resultados das duas consultas, validando se a expressão XPath é funcionalmente equivalente à consulta [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]. Como os dois tipos de consultas retornam nós da mesma árvore XML, a comparação do resultado da consulta é feita usando identidade referencial.  
  
## <a name="in-this-section"></a>Nesta seção  
  
|Tópico|Descrição|  
|-----------|-----------------|  
|[Comparação de XPath e de LINQ to XML](../../../../visual-basic/programming-guide/concepts/linq/comparison-of-xpath-and-linq-to-xml.md)|Apresenta uma visão geral das semelhanças e das diferenças entre XPath e [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].|  
|[Como: localizar um elemento filho (XPath-LINQ para XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-a-child-element-xpath-linq-to-xml.md)|Compara o eixo de elemento filho XPath com o [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] <xref:System.Xml.Linq.XContainer.Element%2A>método.</xref:System.Xml.Linq.XContainer.Element%2A><br /><br /> A expressão XPath associada é:`"DeliveryNotes"`.|  
|[Como: localizar uma lista dos elementos filho (XPath-LINQ para XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-a-list-of-child-elements-xpath-linq-to-xml.md)|Compara o eixo de elementos filho XPath com o [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] <xref:System.Xml.Linq.XContainer.Elements%2A>eixo.</xref:System.Xml.Linq.XContainer.Elements%2A><br /><br /> A expressão XPath associada é:`"./*"`|  
|[Como: localizar o elemento raiz (XPath-LINQ para XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-the-root-element-xpath-linq-to-xml.md)|Compara como obter o elemento raiz com XPath e [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].<br /><br /> A expressão XPath associada é:`"/PurchaseOrders"`|  
|[Como: localizar elementos descendentes (XPath-LINQ para XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-descendant-elements-xpath-linq-to-xml.md)|Compara como obter os elementos descendentes com um nome específico com XPath e [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].<br /><br /> A expressão XPath associada é:`"//Name"`|  
|[Como: Filtrar em um atributo (XPath-LINQ para XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-filter-on-an-attribute-xpath-linq-to-xml.md)|Compara como obter os elementos descendentes com um nome especificado e com um atributo com um valor especificado com XPath e [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].<br /><br /> A expressão XPath associada é:`".//Address[@Type='Shipping']"`|  
|[Como: elementos inter-relacionados de alterações (XPath-LINQ para XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-related-elements-xpath-linq-to-xml.md)|Compara como obter um elemento selecionando em um atributo que é referenciado pelo valor de outro elemento com XPath e [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].<br /><br /> A expressão XPath associada é:`".//Customer[@CustomerID=/Root/Orders/Order[12]/CustomerID]"`|  
|[Como: localizar elementos em um Namespace (XPath-LINQ para XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-elements-in-a-namespace.md)|Compara o uso do XPath <xref:System.Xml.XmlNamespaceManager>classe com o [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] <xref:System.Xml.Linq.XName.Namespace%2A>propriedade o <xref:System.Xml.Linq.XName>classe para trabalhar com namespaces XML.</xref:System.Xml.Linq.XName> </xref:System.Xml.Linq.XName.Namespace%2A> </xref:System.Xml.XmlNamespaceManager><br /><br /> A expressão XPath associada é:`"./aw:*"`|  
|[Como: Localizar anterior irmãos (XPath-LINQ para XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-preceding-siblings-xpath-linq-to-xml.md)|Compara o XPath `preceding-sibling` eixo para o [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] filho <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=fullName>eixo.</xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=fullName><br /><br /> A expressão XPath associada é:`"preceding-sibling::*"`|  
|[Como: localizar descendentes de um elemento filho (XPath-LINQ para XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-descendants-of-a-child-element-xpath-linq-to-xml.md)|Compara como obter os elementos descendentes de um elemento filho com um nome específico com XPath e [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].<br /><br /> A expressão XPath associada é:`"./Paragraph//Text/text()"`|  
|[Como: localizar uma união de dois caminhos de local (XPath-LINQ para XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-a-union-of-two-location-paths-xpath.md)|Compara o uso do operador de união, `&#124;`, em XPath com o <xref:System.Linq.Enumerable.Concat%2A>operador de consulta padrão em [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].</xref:System.Linq.Enumerable.Concat%2A><br /><br /> A expressão XPath associada é:`"//Category&#124;//Price"`|  
|[Como: nós irmãos de alterações (XPath-LINQ para XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-sibling-nodes-xpath-linq-to-xml.md)|Compara como localizar todos os irmãos de um nó que têm um nome específico com XPath e [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].<br /><br /> A expressão XPath associada é:`"../Book"`|  
|[Como: localizar um atributo do pai (XPath-LINQ para XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-an-attribute-of-the-parent-xpath-linq-to-xml.md)|Compara como navegar para o elemento pai e localizar um atributo associado usando XPath e [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].<br /><br /> A expressão XPath associada é:`"../@id"`|  
|[Como: localizar os atributos de irmãos com um nome específico (XPath-LINQ para XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-attributes-of-siblings-with-a-specific-name.md)|Compara como localizar atributos específicos dos irmãos do nó de contexto com XPath e [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].<br /><br /> A expressão XPath associada é:`"``../Book/@id``"`|  
|[Como: localizar elementos com um atributo específico (XPath-LINQ para XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-elements-with-a-specific-attribute.md)|Compara como localizar todos os elementos que contêm um atributo específico usando XPath e [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].<br /><br /> A expressão XPath associada é:`"./*[@Select]"`|  
|[Como: localizar elementos filho com base na posição (XPath-LINQ para XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-child-elements-based-on-position.md)|Compara como localizar um elemento com base em sua posição relativa usando XPath e [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].<br /><br /> A expressão XPath associada é:`"Test[position() >= 2 and position() <= 4]"`|  
|[Como: localizar o irmão anterior imediato (XPath-LINQ para XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-the-immediate-preceding-sibling-xpath-linq-to-xml.md)|Compara como localizar o irmão imediatamente precedente de um nó usando XPath e [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].<br /><br /> A expressão XPath associada é:`"preceding-sibling::*[1]"`|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Xml.XPath?displayProperty=fullName></xref:System.Xml.XPath?displayProperty=fullName>   
 [Consultando árvores XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/querying-xml-trees.md)   
 [Processar dados XML usando o modelo de dados XPath](http://msdn.microsoft.com/library/536c6fce-1453-4654-9c72-bca54d47e081)
