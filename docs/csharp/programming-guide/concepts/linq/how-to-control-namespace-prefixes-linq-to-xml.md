---
title: Como controlar prefixos de namespace (C#) (LINQ to XML)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 64de5186-b81a-4ddd-8327-8693df59a01b
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: fc8d652c54be62fdf38e0aa05fcf6a81af3f719b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-control-namespace-prefixes-c-linq-to-xml"></a>Como controlar prefixos de namespace (C#) (LINQ to XML)
Este tópico descreve como você pode controlar prefixos de namespace ao serializar uma árvore XML.  
  
 Em muitas situações, não é necessário controlar prefixos de namespace.  
  
 No entanto, determinadas ferramentas de programação XML requerem controle específico de prefixos de namespace. Por exemplo, você pode manipular uma folha de estilos XSLT ou um documento XAML que contenha as expressões XPath inseridas que se referem a prefixos de namespace específicos. Nesse caso, é importante que o documento seja serializado com esses prefixos específicos.  
  
 Esse é o motivo mais comum para controlar prefixos de namespace.  
  
 Outra razão comum para controlar prefixos de namespace é que você deseja que os usuários editem manualmente o documento XML e deseja criar prefixos de namespace que sejam convenientes para o usuário digitar. Por exemplo, você pode estar gerando um documento XSD. As convenções de esquemas sugerem que você use `xs` ou `xsd` como o prefixo do namespace do esquema.  
  
 Para controlar prefixos de namespace, você insere os atributos que declaram os namespaces. Se você declarar namespaces com prefixos específicos, o [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] tentará respeitar os prefixos de namespace ao serializar.  
  
 Para criar um atributo que declare um namespace com um prefixo, você cria um atributo onde o namespace do nome do atributo é <xref:System.Xml.Linq.XNamespace.Xmlns%2A>, e o nome do atributo é o prefixo do namespace. O valor do atributo é o URI do namespace.  
  
## <a name="example"></a>Exemplo  
 Esse exemplo declara dois namespaces. Ele especifica que o namespace `http://www.adventure-works.com` tem o prefixo `aw` e que o namespace `www.fourthcoffee.com` tem o prefixo `fc`.  
  
```csharp  
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
  
 Este exemplo gera a seguinte saída:  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com" xmlns:fc="www.fourthcoffee.com">  
  <fc:Child>  
    <aw:DifferentChild>other content</aw:DifferentChild>  
  </fc:Child>  
  <aw:Child2>c2 content</aw:Child2>  
  <fc:Child3>c3 content</fc:Child3>  
</aw:Root>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Trabalhando com namespaces XML (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md)
