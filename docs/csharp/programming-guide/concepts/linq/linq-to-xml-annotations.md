---
title: "Anotações de LINQ to XML 3 | Microsoft Docs"
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
ms.assetid: 54e7b9d0-07f5-488f-9065-b6e6b870f810
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 13718f509eee46853020cfe1dd27ee85437d2e6d
ms.lasthandoff: 03/13/2017


---
# <a name="linq-to-xml-annotations"></a>Anotações LINQ to XML
Anotações em [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] permitem associar qualquer objeto arbitrário de qualquer tipo arbitrário com qualquer componente XML em uma árvore XML.  
  
 Para adicionar uma anotação a um componente XML, como um <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XAttribute>, chame o método <xref:System.Xml.Linq.XObject.AddAnnotation%2A>. Você recupera anotações pelo tipo.  
  
 Observe que as anotações não são parte de infoset XML; não são serializados ou não estão desserializados.  
  
## <a name="methods"></a>Métodos  
 Você pode usar os seguintes métodos para trabalhar com anotações:  
  
|Método|Descrição|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XObject.AddAnnotation%2A>|Adiciona um objeto à lista de anotação de um <xref:System.Xml.Linq.XObject>.|  
|<xref:System.Xml.Linq.XObject.Annotation%2A>|Obtém o primeiro objeto de anotação do tipo especificado de um <xref:System.Xml.Linq.XObject>.|  
|<xref:System.Xml.Linq.XObject.Annotations%2A>|Obtém uma coleção de anotações de um tipo especificado para um <xref:System.Xml.Linq.XObject>.|  
|<xref:System.Xml.Linq.XObject.RemoveAnnotations%2A>|Remove as anotações do tipo especificado de um <xref:System.Xml.Linq.XObject>.|  
  
## <a name="see-also"></a>Consulte também  
 [Programação LINQ to XML avançada (C#)](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
