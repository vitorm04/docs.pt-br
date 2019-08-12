---
title: 'Como: Controlar prefixos de namespace (C#) (LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: 64de5186-b81a-4ddd-8327-8693df59a01b
ms.openlocfilehash: 5b836be46001b660547532311b1b507ff234975f
ms.sourcegitcommit: eb9ff6f364cde6f11322e03800d8f5ce302f3c73
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/01/2019
ms.locfileid: "68710156"
---
# <a name="how-to-control-namespace-prefixes-c-linq-to-xml"></a>Como: Controlar prefixos de namespace (C#) (LINQ to XML)
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

- [Visão geral sobre namespaces (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md)
