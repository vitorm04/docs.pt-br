---
title: "LINQ to XML para usuários do XPath (C#) | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 91774511-1dca-4f06-ac0b-913746f104fe
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
ms.translationtype: Human Translation
ms.sourcegitcommit: fe32676f0e39ed109a68f39584cf41aec5f5ce90
ms.openlocfilehash: db09a2438df5592f4afa0b3882d7b8d5de6fa1c1
ms.contentlocale: pt-br
ms.lasthandoff: 05/10/2017


---
# <a name="linq-to-xml-for-xpath-users-c"></a>Usuários do LINQ to XML para XPath (C#)
Este conjunto de tópicos mostra algumas expressões XPath e seus equivalentes [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].  
  
 Todos os exemplos usam a funcionalidade XPath no [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] disponibilizada pelos métodos de extensão em <xref:System.Xml.XPath.Extensions?displayProperty=fullName>. Os exemplos executam a expressão XPath e a expressão [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]. Cada exemplo compara os resultados das duas consultas, validando se a expressão XPath é funcionalmente equivalente à consulta [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]. Como os dois tipos de consultas retornam nós da mesma árvore XML, a comparação do resultado da consulta é feita usando identidade referencial.  
  
## <a name="in-this-section"></a>Nesta seção  
  
|Tópico|Descrição|  
|-----------|-----------------|  
|[Comparação de XPath e de LINQ to XML](../../../../csharp/programming-guide/concepts/linq/comparison-of-xpath-and-linq-to-xml.md)|Apresenta uma visão geral das semelhanças e das diferenças entre XPath e [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].|  
|[Como localizar um elemento filho (XPath-LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-find-a-child-element-xpath-linq-to-xml.md)|Compara o eixo do elemento filho XPath com o método [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] <xref:System.Xml.Linq.XContainer.Element%2A>.<br /><br /> A expressão XPath associada é:`"DeliveryNotes"`.|  
|[Como localizar uma lista dos elementos filho (XPath-LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-find-a-list-of-child-elements-xpath-linq-to-xml.md)|Compara o eixo de elementos filho XPath com o eixo [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] <xref:System.Xml.Linq.XContainer.Elements%2A>.<br /><br /> A expressão XPath associada é:`"./*"`|  
|[Como localizar o elemento raiz (XPath-LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-find-the-root-element-xpath-linq-to-xml.md)|Compara como obter o elemento raiz com XPath e [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].<br /><br /> A expressão XPath associada é:`"/PurchaseOrders"`|  
|[Como localizar elementos descendentes (XPath-LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-find-descendant-elements-xpath-linq-to-xml.md)|Compara como obter os elementos descendentes com um nome específico com XPath e [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].<br /><br /> A expressão XPath associada é:`"//Name"`|  
|[Como filtrar em um atributo (XPath-LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-filter-on-an-attribute-xpath-linq-to-xml.md)|Compara como obter os elementos descendentes com um nome especificado e com um atributo com um valor especificado com XPath e [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].<br /><br /> A expressão XPath associada é:`".//Address[@Type='Shipping']"`|  
|[Como localizar elementos relacionados (XPath-LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-find-related-elements-xpath-linq-to-xml.md)|Compara como obter um elemento selecionando em um atributo que é referenciado pelo valor de outro elemento com XPath e [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].<br /><br /> A expressão XPath associada é:`".//Customer[@CustomerID=/Root/Orders/Order[12]/CustomerID]"`|  
|[Como localizar elementos em um namespace (XPath-LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-find-elements-in-a-namespace-xpath-linq-to-xml.md)|Compara o uso da classe XPath <xref:System.Xml.XmlNamespaceManager> com a propriedade [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] <xref:System.Xml.Linq.XName.Namespace%2A> da classe <xref:System.Xml.Linq.XName> para trabalhar com namespaces XML.<br /><br /> A expressão XPath associada é:`"./aw:*"`|  
|[Como localizar irmãos anteriores (XPath-LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-find-preceding-siblings-xpath-linq-to-xml.md)|Compara o eixo XPath `preceding-sibling` com o eixo [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] filho <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=fullName>.<br /><br /> A expressão XPath associada é:`"preceding-sibling::*"`|  
|[Como localizar descendentes de um elemento filho (XPath-LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-find-descendants-of-a-child-element-xpath-linq-to-xml.md)|Compara como obter os elementos descendentes de um elemento filho com um nome específico com XPath e [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].<br /><br /> A expressão XPath associada é:`"./Paragraph//Text/text()"`|  
|[Como localizar uma união de dois caminhos de local (XPath-LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-find-a-union-of-two-location-paths-xpath-linq-to-xml.md)|Compara o uso do operador de união, `&#124;`, no XPath com o operador de consulta padrão <xref:System.Linq.Enumerable.Concat%2A> em [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].<br /><br /> A expressão XPath associada é:`"//Category&#124;//Price"`|  
|[Como localizar nós irmãos (XPath-LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-find-sibling-nodes-xpath-linq-to-xml.md)|Compara como localizar todos os irmãos de um nó que têm um nome específico com XPath e [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].<br /><br /> A expressão XPath associada é:`"../Book"`|  
|[Como localizar um atributo do pai (XPath-LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-find-an-attribute-of-the-parent-xpath-linq-to-xml.md)|Compara como navegar para o elemento pai e localizar um atributo associado usando XPath e [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].<br /><br /> A expressão XPath associada é:`"../@id"`|  
|[Como localizar atributos de irmãos com um nome específico (XPath-LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-find-attributes-of-siblings-with-a-specific-name-xpath-linq-to-xml.md)|Compara como localizar atributos específicos dos irmãos do nó de contexto com XPath e [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].<br /><br /> A expressão XPath associada é:`"``../Book/@id``"`|  
|[Como localizar elementos com um atributo específico (XPath-LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-find-elements-with-a-specific-attribute-xpath-linq-to-xml.md)|Compara como localizar todos os elementos que contêm um atributo específico usando XPath e [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].<br /><br /> A expressão XPath associada é:`"./*[@Select]"`|  
|[Como localizar elementos filho com base na posição (XPath-LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-find-child-elements-based-on-position-xpath-linq-to-xml.md)|Compara como localizar um elemento com base em sua posição relativa usando XPath e [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].<br /><br /> A expressão XPath associada é:`"Test[position() >= 2 and position() <= 4]"`|  
|[Como localizar o irmão imediatamente anterior (XPath-LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-find-the-immediate-preceding-sibling-xpath-linq-to-xml.md)|Compara como localizar o irmão imediatamente precedente de um nó usando XPath e [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].<br /><br /> A expressão XPath associada é:`"preceding-sibling::*[1]"`|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Xml.XPath?displayProperty=fullName>   
 [Consultando árvores XML (C#)](../../../../csharp/programming-guide/concepts/linq/querying-xml-trees.md)   
 [Processar dados XML usando o modelo de dados XPath](../../../../standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
