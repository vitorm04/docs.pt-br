---
title: "Constru&#231;&#227;o funcional (LINQ to XML) (c#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
ms.assetid: 57a82bcf-de03-4f1c-a0c8-9a76e989d542
caps.latest.revision: 3
caps.handback.revision: 3
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Constru&#231;&#227;o funcional (LINQ to XML) (c#)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] Fornece uma maneira eficiente de criar elementos XML chamados *construção funcional*. Construção funcional é a capacidade de criar uma árvore XML em uma única instrução.  
  
 Há vários recursos importantes do [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] interface de programação que permitem a construção funcional:  
  
-   O <xref:System.Xml.Linq.XElement> construtor aceita vários tipos de argumentos para o conteúdo. Por exemplo, você pode passar outro <xref:System.Xml.Linq.XElement> objeto, que se torna um elemento filho. Você pode passar um <xref:System.Xml.Linq.XAttribute> objeto, que se torna um atributo do elemento. Ou você pode passar qualquer outro tipo de objeto, que é convertido em uma cadeia de caracteres e torna\-se o conteúdo de texto do elemento.  
  
-   O <xref:System.Xml.Linq.XElement> construtor aceita um `params` matriz do tipo <xref:System.Object>, de modo que você pode passar qualquer número de objetos para o construtor. Isso permite que você crie um elemento que tem conteúdo complexo.  
  
-   Se um objeto implementa <xref:System.Collections.Generic.IEnumerable%601>, a coleção do objeto será enumerada, e todos os itens da coleção são adicionados. Se a coleção contiver <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XAttribute> objetos, cada item da coleção será adicionado separadamente. Isso é importante porque permite que você passe os resultados de uma [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] consulta para o construtor.  
  
 Esses recursos permitem que você escreva código para criar uma árvore XML. Este é um exemplo:  
  
```c#  
XElement contacts =  
    new XElement("Contacts",  
        new XElement("Contact",  
            new XElement("Name", "Patrick Hines"),  
            new XElement("Phone", "206-555-0144"),  
            new XElement("Address",  
                new XElement("Street1", "123 Main St"),  
                new XElement("City", "Mercer Island"),  
                new XElement("State", "WA"),  
                new XElement("Postal", "68042")  
            )  
        )  
    );  
```  
  
 Esses recursos também permitem a você escrever código que usa os resultados de [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] consultas quando você cria uma árvore XML, da seguinte maneira:  
  
```c#  
XElement srcTree = new XElement("Root",  
    new XElement("Element", 1),  
    new XElement("Element", 2),  
    new XElement("Element", 3),  
    new XElement("Element", 4),  
    new XElement("Element", 5)  
);  
XElement xmlTree = new XElement("Root",  
    new XElement("Child", 1),  
    new XElement("Child", 2),  
    from el in srcTree.Elements()  
    where (int)el > 2  
    select el  
);  
Console.WriteLine(xmlTree);  
```  
  
 Este exemplo produz a seguinte saída:  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Element>3</Element>  
  <Element>4</Element>  
  <Element>5</Element>  
</Root>  
```  
  
## Consulte também  
 [Criando árvores XML \(c\#\)](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md)