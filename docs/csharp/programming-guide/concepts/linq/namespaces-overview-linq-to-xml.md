---
title: "Vis&#227;o geral sobre namespaces (LINQ to XML) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
ms.assetid: 16283322-8238-4918-ab11-802ac6748eb7
caps.latest.revision: 3
caps.handback.revision: 3
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Vis&#227;o geral sobre namespaces (LINQ to XML)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Este tópico apresenta namespaces, a <xref:System.Xml.Linq.XName> classe e o <xref:System.Xml.Linq.XNamespace> classe.  
  
## Nomes XML  
 Nomes XML são geralmente uma fonte de complexidade na programação de XML. Um nome XML consiste em um namespace XML \(também chamado de um URI de namespace XML\) e um nome local. Um namespace XML é semelhante a um namespace em um [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)]\-programa baseado em. Ele permite que você determine exclusivamente os nomes de elementos e atributos. Isso ajuda a evitar conflitos de nome entre várias partes de um documento XML. Quando você declarar um namespace XML, você pode selecionar um nome local que só deve ser exclusivo dentro desse namespace.  
  
 Outro aspecto de nomes XML é XML *prefixos de namespace*. Prefixos XML causam a maioria da complexidade de nomes XML. Esses prefixos permitem que você crie um atalho para um namespace XML, que torna o documento XML mais concisas e legível. No entanto, prefixos XML depende de seu contexto para ter significado, que adiciona complexidade. Por exemplo, o prefixo XML `aw` pode ser associado com um namespace XML em uma parte de uma árvore XML e com um namespace XML diferente em uma parte diferente da árvore XML.  
  
 Uma das vantagens de usar [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] com c\# é que você não precisa usar prefixos XML. Quando [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] carrega ou analisa um documento XML, cada prefixo XML é resolvido para o namespace XML correspondente. Depois disso, quando você trabalha com um documento que usa namespaces, você quase sempre acessar os namespaces através do URI de namespace e não o prefixo de namespace. Quando os desenvolvedores trabalham com nomes XML em [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] sempre funcionam com um nome XML totalmente qualificado \(ou seja, um namespace XML e um nome local\). No entanto, quando necessário, [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] permite que você trabalhe com controle e prefixos de namespace.  
  
 Em [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)], a classe que representa nomes XML é <xref:System.Xml.Linq.XName>. Nomes XML aparece com frequência em todo o [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] API, e sempre que é necessário um nome XML, você encontrará um <xref:System.Xml.Linq.XName> parâmetro. No entanto, raramente você trabalha diretamente com um <xref:System.Xml.Linq.XName>.<xref:System.Xml.Linq.XName> contém uma conversão implícita de cadeia de caracteres.  
  
 Para obter mais informações, consulte <xref:System.Xml.Linq.XNamespace> e <xref:System.Xml.Linq.XName>.  
  
## Consulte também  
 [Trabalhando com Namespaces XML \(c\#\)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md)