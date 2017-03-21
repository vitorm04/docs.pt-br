---
title: "Visão geral sobre namespaces (LINQ to XML) | Documentos do Microsoft"
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
ms.assetid: b8eb31fa-4b26-4acf-8050-6e705687f458
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: cec2efd31c96af17ad717abaa8f4359210e99a78
ms.lasthandoff: 03/13/2017

---
# <a name="namespaces-overview-linq-to-xml"></a>Visão geral sobre namespaces (LINQ to XML)
Este tópico apresenta namespaces, a <xref:System.Xml.Linq.XName>classe e a <xref:System.Xml.Linq.XNamespace>classe.</xref:System.Xml.Linq.XNamespace> </xref:System.Xml.Linq.XName>  
  
## <a name="xml-names"></a>Nomes XML  
 Os nomes XML são geralmente uma fonte de complexidade na programação XML. Um nome de XML consiste em um namespace XML (também chamado um URI de um namespace XML) e um nome local. Um namespace XML é semelhante a um namespace em um programa baseadas em [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)]. Permite que você determine exclusivamente os nomes de elementos e atributos. Isso ajuda a evitar conflitos de nome entre várias partes de um documento XML. Quando você declarar um namespace XML, você pode selecionar um nome local que só deve ser exclusivo dentro desse namespace.  
  
 Outro aspecto de nomes XML é XML *prefixos de namespace*. Os prefixos XML causam a maioria da complexidade de nomes XML. Esses prefixos permite que você crie um atalho para um namespace XML, que faz o documento XML mais concisas e legível. No entanto, os prefixos XML depende do seu contexto para ter significado, que adiciona a complexidade. Por exemplo, o prefixo `aw` XML pode ser associado com a um namespace XML de uma parte de uma árvore XML, e com um outro namespace XML em uma parte diferente da árvore XML.  
  
 Ao usar [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] com literais XML e Visual Basic, você deve usar prefixos de namespace ao trabalhar com documentos em namespaces.  
  
 Em [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)], a classe que representa nomes XML é <xref:System.Xml.Linq.XName>.</xref:System.Xml.Linq.XName> Nomes XML aparece com frequência em todo o [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] API, e sempre que é necessário um nome XML, você encontrará um <xref:System.Xml.Linq.XName>parâmetro.</xref:System.Xml.Linq.XName> No entanto, raramente você trabalha diretamente com um <xref:System.Xml.Linq.XName>.</xref:System.Xml.Linq.XName> <xref:System.Xml.Linq.XName>contém uma conversão implícita de cadeia de caracteres.</xref:System.Xml.Linq.XName>  
  
 Para obter mais informações, consulte <xref:System.Xml.Linq.XNamespace>e <xref:System.Xml.Linq.XName>.</xref:System.Xml.Linq.XName> </xref:System.Xml.Linq.XNamespace>  
  
## <a name="see-also"></a>Consulte também  
 [Trabalhando com Namespaces XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)
