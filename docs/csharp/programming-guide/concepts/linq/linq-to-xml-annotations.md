---
title: "Anotações LINQ to XML 3"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 54e7b9d0-07f5-488f-9065-b6e6b870f810
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: eadbc55ac6188fa3634745bf8bb222f07675a308
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="linq-to-xml-annotations"></a>Anotações LINQ to XML
Anotações em [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] permitem associar qualquer objeto arbitrário de qualquer tipo arbitrário com qualquer componente XML em uma árvore XML.  
  
 Para adicionar uma anotação a um componente XML, como <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XAttribute>, você chama o método de <xref:System.Xml.Linq.XObject.AddAnnotation%2A> . Você recupera anotações pelo tipo.  
  
 Observe que as anotações não são parte de infoset XML; não são serializados ou não estão desserializados.  
  
## <a name="methods"></a>Métodos  
 Você pode usar os seguintes métodos para trabalhar com anotações:  
  
|Método|Descrição|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XObject.AddAnnotation%2A>|Adiciona um objeto à lista de anotação de <xref:System.Xml.Linq.XObject>.|  
|<xref:System.Xml.Linq.XObject.Annotation%2A>|Obtém o primeiro objeto de anotação do tipo especificado de <xref:System.Xml.Linq.XObject>.|  
|<xref:System.Xml.Linq.XObject.Annotations%2A>|Obtém uma coleção de anotações do tipo especificado para <xref:System.Xml.Linq.XObject>.|  
|<xref:System.Xml.Linq.XObject.RemoveAnnotations%2A>|Remove as anotações do tipo especificado de <xref:System.Xml.Linq.XObject>.|  
  
## <a name="see-also"></a>Consulte também  
 [Programação LINQ to XML avançada (C#)](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
