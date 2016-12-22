---
title: "Como controlar prefixos de namespace (C#) (LINQ to XML) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
ms.assetid: 64de5186-b81a-4ddd-8327-8693df59a01b
caps.latest.revision: 3
caps.handback.revision: 3
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Como controlar prefixos de namespace (C#) (LINQ to XML)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Este tópico descreve como você pode controlar prefixos de namespace ao serializar uma árvore XML.  
  
 Em muitas situações, não é necessário controlar prefixos de namespace.  
  
 No entanto, determinadas ferramentas de programação XML requerem controle específico de prefixos de namespace. Por exemplo, você pode manipular uma folha de estilos XSLT ou um documento XAML que contém expressões XPath inseridas que se referem a prefixos de namespace específicas; Nesse caso, é importante que o documento seja serializado com esses prefixos específicos.  
  
 Essa é a razão mais comum para controlar prefixos de namespace.  
  
 Outra razão comum para controlar prefixos de namespace é que você deseja que os usuários editem o documento XML manualmente, e você deseja criar prefixos de namespace são convenientes para o usuário digitar. Por exemplo, você pode gerar um documento XSD. As convenções de esquemas sugerem que você use `xs` ou `xsd` como o prefixo do namespace do esquema.  
  
 Para controlar prefixos de namespace, você insere os atributos que declaram os namespaces. Se você declarar os namespaces com prefixos específicos, [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] tentará respeitar os prefixos de namespace ao serializar.  
  
 Para criar um atributo que declara um namespace com um prefixo, você cria um atributo onde o namespace do nome do atributo é <xref:System.Xml.Linq.XNamespace.Xmlns%2A>, e o nome do atributo é o prefixo de namespace. O valor do atributo é o URI do namespace.  
  
## Exemplo  
 Este exemplo declara dois namespaces. Especifica que o `http://www.adventure-works.com` namespace tem o prefixo de `aw`, e que o `www.fourthcoffee.com` namespace tem o prefixo `fc`.  
  
```c#  
XNamespace aw = "http://www.adventure-works.com";  
XNamespace fc = "www.fourthcoffee.com";  
XElement root = new XElement(aw + "Root",  
    new XAttribute(XNamespace.Xmlns + "aw", "http://www.adventure-works.com"),  
    new XAttribute(XNamespace.Xmlns + "fc", "www.fourthcoffee.com"),  
    new XElement(fc + "Child",  
        new XElement(aw + "DifferentChild", "other content")  
    ),  
    new XElement(aw + "Child2", "c2 content"),  
    new XElement(fc + "Child3", "c3 content")  
);  
Console.WriteLine(root);  
```  
  
 Este exemplo produz a seguinte saída:  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com" xmlns:fc="www.fourthcoffee.com">  
  <fc:Child>  
    <aw:DifferentChild>other content</aw:DifferentChild>  
  </fc:Child>  
  <aw:Child2>c2 content</aw:Child2>  
  <fc:Child3>c3 content</fc:Child3>  
</aw:Root>  
```  
  
## Consulte também  
 [Trabalhando com Namespaces XML \(c\#\)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md)