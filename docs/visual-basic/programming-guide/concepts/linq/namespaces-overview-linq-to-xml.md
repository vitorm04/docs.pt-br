---
title: Visão geral sobre namespaces (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: b8eb31fa-4b26-4acf-8050-6e705687f458
ms.openlocfilehash: 3133a96c356138ddb70df01c11ee0dac8cf11b16
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65592880"
---
# <a name="namespaces-overview-linq-to-xml"></a>Visão geral sobre namespaces (LINQ to XML)
Este tópico apresenta namespaces, a classe <xref:System.Xml.Linq.XName> e a classe <xref:System.Xml.Linq.XNamespace>.  
  
## <a name="xml-names"></a>Nomes XML  
 Os nomes XML são geralmente uma fonte de complexidade na programação XML. Um nome de XML consiste em um namespace XML (também chamado um URI de um namespace XML) e um nome local. Um namespace de XML é semelhante a um namespace em um programa baseado no .NET Framework. Permite que você determine exclusivamente os nomes de elementos e atributos. Isso ajuda a evitar conflitos de nome entre várias partes de um documento XML. Quando você declarar um namespace de XML, poderá selecionar um nome local que somente deve ser exclusivo dentro desse namespace.  
  
 Outro aspecto de nomes XML são os *prefixos de namespace* de XML. Os prefixos XML causam a maioria da complexidade de nomes XML. Esses prefixos permite que você crie um atalho para um namespace XML, que faz o documento XML mais concisas e legível. No entanto, os prefixos XML depende do seu contexto para ter significado, que adiciona a complexidade. Por exemplo, o prefixo `aw` XML pode ser associado com a um namespace XML de uma parte de uma árvore XML, e com um outro namespace XML em uma parte diferente da árvore XML.  
  
 Ao usar [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] com literais XML e Visual Basic, você deve usar prefixos de namespace ao trabalhar com documentos em namespaces.  
  
 Em [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], a classe que representa nomes XML é <xref:System.Xml.Linq.XName>. Os nomes XML aparecem com frequência em toda a API [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] e, em qualquer lugar em que um nome XML for necessário, você encontrará um parâmetro <xref:System.Xml.Linq.XName>. No entanto, raramente você trabalha diretamente com um <xref:System.Xml.Linq.XName>. <xref:System.Xml.Linq.XName> contém uma conversão implícita de cadeia de caracteres.  
  
 Para obter mais informações, consulte <xref:System.Xml.Linq.XNamespace> e <xref:System.Xml.Linq.XName>.  
  
## <a name="see-also"></a>Consulte também

- [Trabalhando com Namespaces XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)
