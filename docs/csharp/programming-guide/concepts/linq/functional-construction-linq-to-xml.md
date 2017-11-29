---
title: "Construção funcional (LINQ to XML) (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 57a82bcf-de03-4f1c-a0c8-9a76e989d542
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f357de98fae60b3d0b6548ef195b462b4e2f6a5a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="functional-construction-linq-to-xml-c"></a>Construção funcional (LINQ to XML) (C#)
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] fornece uma maneira eficiente de criar elementos XML chamada *construção funcional*. Construção funcional é a capacidade de criar uma árvore XML em uma única instrução.  
  
 Há vários recursos chave da interface de programação do [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] que permitem a construção funcional:  
  
-   O construtor <xref:System.Xml.Linq.XElement> utiliza vários tipos de argumentos para o conteúdo. Por exemplo, você pode passar outro objeto <xref:System.Xml.Linq.XElement>, que se torna um elemento filho. Você pode passar um objeto <xref:System.Xml.Linq.XAttribute>, que se torna um atributo do elemento. Ou você pode passar qualquer outro tipo de objeto, que é convertido em uma cadeia de caracteres e torna-se o conteúdo de texto do elemento.  
  
-   O construtor <xref:System.Xml.Linq.XElement> utiliza uma matriz de `params` do tipo <xref:System.Object>, para que você possa passar qualquer número de objetos para o construtor. Isso permite que você crie um elemento que tem o conteúdo complexo.  
  
-   Se um objeto implementar <xref:System.Collections.Generic.IEnumerable%601>, a coleção no objeto será enumerada, e todos os itens da coleção serão adicionados. Se a coleção contiver objetos <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XAttribute>, cada item da coleção será adicionado separadamente. Isso é importante porque permite que você passe os resultados de uma consulta [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] para o construtor.  
  
 Esses recursos permitem escrever código para criar uma árvore XML. A seguir está um exemplo:  
  
```csharp  
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
  
 Esses recursos também permitem que você escreva código que usa os resultados de consultas [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] quando cria uma árvore XML, da seguinte maneira:  
  
```csharp  
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
  
 Este exemplo gera a seguinte saída:  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Element>3</Element>  
  <Element>4</Element>  
  <Element>5</Element>  
</Root>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Criando árvores XML (C#)](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md)
