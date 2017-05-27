---
title: "Guia de programação (LINQ to XML) (C#) | Microsoft Docs"
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
ms.assetid: 4b1ffd10-ab81-4a0d-a0ca-e9876478d924
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 5e1e95d92123b2874aace0c36005a8a07a6203fc
ms.contentlocale: pt-br
ms.lasthandoff: 05/24/2017

---
# <a name="programming-guide-linq-to-xml-c"></a>Guia de Programação (LINQ to XML) (C#)
Esta seção fornece informações e instruções conceituais sobre como programar com o [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].  
  
## <a name="who-should-read-this-documentation"></a>Quem deve ler esta documentação  
 Esta documentação é direcionada aos desenvolvedores que já compreendem o C# e alguns aspectos básicos do [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)].  
  
 A meta desta documentação é facilitar o uso do [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] para todos os tipos de desenvolvedores. O [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] facilita a programação XML. Você não precisa ser um desenvolvedor especialista para usá-lo.  
  
 O [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] depende fortemente de classes genéricas. Portanto, é muito importante que você compreenda como usar classes genéricas. Além disso, será útil se você estiver familiarizado com os representantes declarados como tipos parametrizados. Se você não estiver familiarizado com as classes genéricas do C#, consulte [Classes genéricas](../../../../csharp/programming-guide/generics/generic-classes.md).  
  
## <a name="in-this-section"></a>Nesta seção  
  
|Tópico|Descrição|  
|-----------|-----------------|  
|[Visão geral da programação LINQ to XML (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)|Fornece uma visão geral das classes do [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] e informações detalhadas sobre três das classes mais importantes: <xref:System.Xml.Linq.XElement>, <xref:System.Xml.Linq.XAttribute> e <xref:System.Xml.Linq.XDocument>.|  
|[Criando árvores XML (C#)](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md)|Fornece informações conceituais e baseadas em tarefas sobre como criar árvores XML. Você pode criar árvores XML usando construção funcional ou analisando o texto XML de uma cadeia de caracteres ou de um arquivo. Você também pode usar um <xref:System.Xml.XmlReader> para popular uma árvore XML.|  
|[Trabalhando com namespaces XML (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md)|Fornece informações detalhadas sobre como criar árvores XML que usam namespaces.|  
|[Serializando árvores XML (C#)](../../../../csharp/programming-guide/concepts/linq/serializing-xml-trees.md)|Descreve várias abordagens para serializar uma árvore XML e fornece orientações sobre qual abordagem usar.|  
|[Eixos do LINQ to XML (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md)|Enumera e descreve os métodos de eixo do [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)], que você deve compreender antes de escrever consultas [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].|  
|[Consultando árvores XML (C#)](../../../../csharp/programming-guide/concepts/linq/querying-xml-trees.md)|Fornece exemplos comuns de como consultar árvores XML.|  
|[Modificando árvores XML (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)|Como o DOM (Modelo de Objeto do Documento), o [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] permite modificar uma árvore XML no lugar.|  
|[Programação LINQ to XML avançada (C#)](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)|Fornece informações sobre anotações, eventos, streaming e outros cenários avançados.|  
|[Segurança do LINQ to XML (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-security.md)|Descreve problemas de segurança associados ao LINQ to XML e fornece alguma orientação para minimizar a exposição de segurança.|  
|[Documentos XML de exemplo (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-documents-linq-to-xml.md)|Contém os documentos XML de exemplo que são usados por muitos exemplos desta documentação.|  
  
## <a name="see-also"></a>Consulte também  
 [Introdução (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/getting-started-linq-to-xml.md)   
 [LINQ to XML (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml.md)
