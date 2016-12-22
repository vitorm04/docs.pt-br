---
title: "Como: escrever consultas no XML nos Namespaces (c#) | Microsoft Docs"
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
ms.assetid: 7c54df81-15e4-4091-8c81-a87637029130
caps.latest.revision: 3
caps.handback.revision: 3
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Como: escrever consultas no XML nos Namespaces (c#)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Para escrever uma consulta em XML que está em um namespace, você deve usar <xref:System.Xml.Linq.XName> objetos que têm o namespace correto.  
  
 Para c\#, a abordagem mais comum é inicializar um <xref:System.Xml.Linq.XNamespace> usando uma cadeia de caracteres que contém o URI, usar a sobrecarga de operador de adição para combinar o namespace com o nome local.  
  
 O primeiro conjunto de exemplos neste tópico mostra como criar uma árvore XML em um namespace padrão. O segundo conjunto mostra como criar uma árvore XML em um namespace com um prefixo.  
  
## Exemplo  
 O exemplo a seguir cria uma árvore XML que está em um namespace padrão. Em seguida, ele recupera uma coleção de elementos.  
  
```c#  
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
  
 Este exemplo produz a seguinte saída:  
  
```  
1  
2  
3  
```  
  
## Exemplo  
 No c\#, você pode escrever consultas da mesma maneira, independentemente de se você estiver escrevendo consultas em uma árvore XML que usa um namespace com um prefixo ou em uma árvore XML com um namespace padrão.  
  
 O exemplo a seguir cria uma árvore XML que está em um namespace com um prefixo. Em seguida, ele recupera uma coleção de elementos.  
  
```c#  
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
  
 Este exemplo produz a seguinte saída:  
  
```  
1  
2  
3  
```  
  
## Consulte também  
 [Trabalhando com Namespaces XML \(c\#\)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md)