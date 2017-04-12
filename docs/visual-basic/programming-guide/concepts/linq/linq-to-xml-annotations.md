---
title: LINQ to XML Annotations2 | Documentos do Microsoft
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
ms.assetid: c3e8b3ff-fceb-4428-b0ca-1ed6f128aac8
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 1f2e5bea1cde74548daa1697b6a0a819e3eba3e4
ms.lasthandoff: 03/13/2017


---
# <a name="linq-to-xml-annotations"></a>Anotações LINQ to XML
Anotações em [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] permite associar qualquer objeto arbitrário de qualquer tipo arbitrário com qualquer componente XML em uma árvore XML.  
  
 Para adicionar uma anotação a um componente XML, como um <xref:System.Xml.Linq.XElement>ou <xref:System.Xml.Linq.XAttribute>, chamar o <xref:System.Xml.Linq.XObject.AddAnnotation%2A>método.</xref:System.Xml.Linq.XObject.AddAnnotation%2A> </xref:System.Xml.Linq.XAttribute> </xref:System.Xml.Linq.XElement> Você recupera anotações pelo tipo.  
  
 Observe que as anotações não são parte de infoset XML; não são serializados ou não estão desserializados.  
  
## <a name="methods"></a>Métodos  
 Você pode usar os seguintes métodos para trabalhar com anotações:  
  
|Método|Descrição|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XObject.AddAnnotation%2A></xref:System.Xml.Linq.XObject.AddAnnotation%2A>|Adiciona um objeto à lista de anotação de <xref:System.Xml.Linq.XObject>.</xref:System.Xml.Linq.XObject>|  
|<xref:System.Xml.Linq.XObject.Annotation%2A></xref:System.Xml.Linq.XObject.Annotation%2A>|Obtém o primeiro objeto de anotação do tipo especificado de <xref:System.Xml.Linq.XObject>.</xref:System.Xml.Linq.XObject>|  
|<xref:System.Xml.Linq.XObject.Annotations%2A></xref:System.Xml.Linq.XObject.Annotations%2A>|Obtém uma coleção de anotações do tipo especificado para <xref:System.Xml.Linq.XObject>.</xref:System.Xml.Linq.XObject>|  
|<xref:System.Xml.Linq.XObject.RemoveAnnotations%2A></xref:System.Xml.Linq.XObject.RemoveAnnotations%2A>|Remove as anotações do tipo especificado de <xref:System.Xml.Linq.XObject>.</xref:System.Xml.Linq.XObject>|  
  
## <a name="see-also"></a>Consulte também  
 [Avançada LINQ to XML programação (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
