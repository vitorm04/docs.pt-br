---
title: "Como criar um documento com namespaces (C#) (LINQ to XML) | Microsoft Docs"
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
ms.assetid: 37e63c57-f86d-47ac-88a7-2c2d107def30
caps.latest.revision: 3
caps.handback.revision: 3
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Como criar um documento com namespaces (C#) (LINQ to XML)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Este tópico mostra como criar documentos com namespaces.  
  
## Exemplo  
 Para criar um elemento ou atributo que está em um namespace, você primeiro declarar e inicializar uma <xref:System.Xml.Linq.XNamespace> objeto. Em seguida, você usar a sobrecarga de operador de adição para combinar o namespace com o nome local, expressado como uma cadeia de caracteres.  
  
 O exemplo a seguir cria um documento com um namespace. Por padrão, [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] serializa esse documento com um namespace padrão.  
  
```c#  
// Create an XML tree in a namespace.  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = new XElement(aw + "Root",  
    new XElement(aw + "Child", "child content")  
);  
Console.WriteLine(root);  
```  
  
 Este exemplo produz a seguinte saída:  
  
```xml  
<Root xmlns="http://www.adventure-works.com">  
  <Child>child content</Child>  
</Root>  
```  
  
## Exemplo  
 O exemplo a seguir cria um documento com um namespace. Ele também cria um atributo que declara o namespace com um prefixo de namespace. Para criar um atributo que declara um namespace com um prefixo, você cria um atributo onde o nome do atributo é o prefixo de namespace e o nome está no <xref:System.Xml.Linq.XNamespace.Xmlns%2A> namespace. O valor desse atributo é o URI do namespace.  
  
```c#  
// Create an XML tree in a namespace, with a specified prefix  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = new XElement(aw + "Root",  
    new XAttribute(XNamespace.Xmlns + "aw", "http://www.adventure-works.com"),  
    new XElement(aw + "Child", "child content")  
);  
Console.WriteLine(root);  
```  
  
 Este exemplo produz a seguinte saída:  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com">  
  <aw:Child>child content</aw:Child>  
</aw:Root>  
```  
  
## Exemplo  
 O exemplo a seguir mostra a criação de um documento que contém dois namespaces. Um é o namespace padrão. Outra é um namespace com um prefixo.  
  
 Ao incluir atributos de namespace no elemento raiz, os namespaces são serializados para que http:\/\/www.adventure\-works.com seja o namespace padrão e www.fourthcoffee.com seja serializado com um prefixo "FC". Para criar um atributo que declara um namespace padrão, você deve criar um atributo com o nome "xmlns", sem um namespace. O valor do atributo é o URI de namespace padrão.  
  
```c#  
// The http://www.adventure-works.com namespace is forced to be the default namespace.  
XNamespace aw = "http://www.adventure-works.com";  
XNamespace fc = "www.fourthcoffee.com";  
XElement root = new XElement(aw + "Root",  
    new XAttribute("xmlns", "http://www.adventure-works.com"),  
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
<Root xmlns="http://www.adventure-works.com" xmlns:fc="www.fourthcoffee.com">  
  <fc:Child>  
    <DifferentChild>other content</DifferentChild>  
  </fc:Child>  
  <Child2>c2 content</Child2>  
  <fc:Child3>c3 content</fc:Child3>  
</Root>  
```  
  
## Exemplo  
 O exemplo a seguir cria um documento que contém dois namespaces, ambos com prefixos de namespace.  
  
```c#  
XNamespace aw = "http://www.adventure-works.com";  
XNamespace fc = "www.fourthcoffee.com";  
XElement root = new XElement(aw + "Root",  
    new XAttribute(XNamespace.Xmlns + "aw", aw.NamespaceName),  
    new XAttribute(XNamespace.Xmlns + "fc", fc.NamespaceName),  
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
  
## Exemplo  
 Outra maneira de obter o mesmo resultado é usar nomes expandidos, em vez de declarar e criar uma <xref:System.Xml.Linq.XNamespace> objeto.  
  
 Essa abordagem tem implicações de desempenho. Cada vez que você passar uma cadeia de caracteres que contém um nome expandido para [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)], [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] deve analisar o nome, localizar o namespace atomizado e localizar o nome atomizado. Esse processo leva tempo de CPU. Se o desempenho for importante, convém declarar e usar um <xref:System.Xml.Linq.XNamespace> objeto explicitamente.  
  
 Se o desempenho for uma questão importante, consulte [Pre\-Atomization of XName Objects \(LINQ to XML\) \(C\#\)](../../../../visual-basic/programming-guide/concepts/linq/pre-atomization-of-xname-objects-linq-to-xml.md) para obter mais informações  
  
```c#  
// Create an XML tree in a namespace, with a specified prefix  
XElement root = new XElement("{http://www.adventure-works.com}Root",  
    new XAttribute(XNamespace.Xmlns + "aw", "http://www.adventure-works.com"),  
    new XElement("{http://www.adventure-works.com}Child", "child content")  
);  
Console.WriteLine(root);  
```  
  
 Este exemplo produz a seguinte saída:  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com">  
  <aw:Child>child content</aw:Child>  
</aw:Root>  
```  
  
## Consulte também  
 [Trabalhando com Namespaces XML \(c\#\)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md)