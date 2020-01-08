---
title: Como escrever consultas em XML em namespaces (C#)
ms.date: 07/20/2015
ms.assetid: 7c54df81-15e4-4091-8c81-a87637029130
ms.openlocfilehash: a8b8d55daaad1ae00e43fed897080ed7a62fafab
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75337367"
---
# <a name="how-to-write-queries-on-xml-in-namespaces-c"></a>Como escrever consultas em XML em namespaces (C#)
Para escrever uma consulta em XML que está em um namespace, você deve usar os objetos <xref:System.Xml.Linq.XName> que têm o namespace correto.  
  
 Para C#, a abordagem mais comum é inicializar um <xref:System.Xml.Linq.XNamespace> usando uma cadeia de caracteres que contém o URI, em seguida, usar a sobrecarga de operador de adição para combinar o namespace com o nome local.  
  
 O primeiro conjunto de exemplos neste tópico mostra como criar uma árvore XML em um namespace padrão. O segundo conjunto mostra como criar uma árvore XML em um namespace com um prefixo.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir cria uma árvore XML que está em um namespace padrão. Ele então recupera uma coleção de elementos.  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = XElement.Parse(  
@"<Root xmlns='http://www.adventure-works.com'>  
    <Child>1</Child>  
    <Child>2</Child>  
    <Child>3</Child>  
    <AnotherChild>4</AnotherChild>  
    <AnotherChild>5</AnotherChild>  
    <AnotherChild>6</AnotherChild>  
</Root>");  
IEnumerable<XElement> c1 =  
    from el in root.Elements(aw + "Child")  
    select el;  
foreach (XElement el in c1)  
    Console.WriteLine((int)el);  
```  
  
 Este exemplo gera a seguinte saída:  
  
```output  
1  
2  
3  
```  
  
## <a name="example"></a>Exemplo  
 No C#, você escreve consultas da mesma forma independentemente se estiver escrevendo consultas em uma árvore XML que usa um namespace com um prefixo ou em uma árvore XML com um namespace padrão.  
  
 O exemplo a seguir cria uma árvore XML que está em um namespace com um prefixo. Ele então recupera uma coleção de elementos.  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = XElement.Parse(  
@"<aw:Root xmlns:aw='http://www.adventure-works.com'>  
    <aw:Child>1</aw:Child>  
    <aw:Child>2</aw:Child>  
    <aw:Child>3</aw:Child>  
    <aw:AnotherChild>4</aw:AnotherChild>  
    <aw:AnotherChild>5</aw:AnotherChild>  
    <aw:AnotherChild>6</aw:AnotherChild>  
</aw:Root>");  
IEnumerable<XElement> c1 =  
    from el in root.Elements(aw + "Child")  
    select el;  
foreach (XElement el in c1)  
    Console.WriteLine((int)el);  
```  
  
 Este exemplo gera a seguinte saída:  
  
```output  
1  
2  
3  
```  
  
## <a name="see-also"></a>Veja também

- [Visão geral sobre namespaces (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md)
