---
title: "Escopo de namespace padr&#227;o em C# | Microsoft Docs"
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
ms.assetid: fe826236-830f-457a-9027-7ad62c909fae
caps.latest.revision: 3
caps.handback.revision: 3
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Escopo de namespace padr&#227;o em C# #
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Namespaces padrões como representadas na árvore XML não estão no escopo de consultas. Se você tiver XML que está em um namespace padrão, você ainda deve declarar um <xref:System.Xml.Linq.XNamespace> variável e combiná\-lo com o nome do local para um nome qualificado para ser usado na consulta.  
  
 Um dos problemas mais comuns ao consultar árvores XML é que se a árvore XML tem um namespace padrão, o desenvolvedor escreve às vezes a consulta como se o XML não estivesse em um namespace.  
  
 O primeiro conjunto de exemplos neste tópico mostra uma maneira comum que XML em um namespace padrão é carregado, mas é consultado incorretamente.  
  
 O segundo conjunto de exemplos mostram as correções necessárias para que você pode consultar o XML em um namespace.  
  
## Exemplo  
 Este exemplo mostra a criação de XML em um namespace e definir uma consulta que retorna um resultado vazio.  
  
### Código  
  
```c#  
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
    from el in root.Elements("Child")  
    select el;  
Console.WriteLine("Result set follows:");  
foreach (XElement el in c1)  
    Console.WriteLine((int)el);  
Console.WriteLine("End of result set");  
```  
  
### Comentários  
 Este exemplo produz o seguinte resultado:  
  
```  
Result set follows:  
End of result set  
```  
  
## Exemplo  
 Este exemplo mostra a criação de XML em um namespace e uma consulta que é codificada corretamente.  
  
 Em contraste com incorretamente codificado o exemplo acima, a abordagem correta para usar c\# é declarar e inicializar uma <xref:System.Xml.Linq.XNamespace> objeto e usá\-lo ao especificar <xref:System.Xml.Linq.XName> objetos. Nesse caso, o argumento para o <xref:System.Xml.Linq.XElement.Elements%2A> método é um <xref:System.Xml.Linq.XName> objeto.  
  
### Código  
  
```c#  
XElement root = XElement.Parse(  
@"<Root xmlns='http://www.adventure-works.com'>  
    <Child>1</Child>  
    <Child>2</Child>  
    <Child>3</Child>  
    <AnotherChild>4</AnotherChild>  
    <AnotherChild>5</AnotherChild>  
    <AnotherChild>6</AnotherChild>  
</Root>");  
XNamespace aw = "http://www.adventure-works.com";  
IEnumerable<XElement> c1 =  
    from el in root.Elements(aw + "Child")  
    select el;  
Console.WriteLine("Result set follows:");  
foreach (XElement el in c1)  
    Console.WriteLine((int)el);  
Console.WriteLine("End of result set");  
```  
  
### Comentários  
 Este exemplo produz o seguinte resultado:  
  
```  
Result set follows:  
1  
2  
3  
End of result set  
```  
  
## Consulte também  
 [Trabalhando com Namespaces XML \(c\#\)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md)