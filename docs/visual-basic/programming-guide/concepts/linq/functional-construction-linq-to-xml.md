---
title: "Constru&#231;&#227;o funcional (LINQ to XML) (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
ms.assetid: feac4273-39ab-43ae-bab7-4059c807a785
caps.latest.revision: 3
caps.handback.revision: 3
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Constru&#231;&#227;o funcional (LINQ to XML) (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] Fornece uma maneira eficiente de criar elementos XML chamados *construção funcional*. Construção funcional é a capacidade de criar uma árvore XML em uma única instrução.  
  
 Há vários recursos importantes do [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] interface de programação que permitem a construção funcional:  
  
-   O <xref:System.Xml.Linq.XElement> construtor aceita vários tipos de argumentos para o conteúdo. Por exemplo, você pode passar outro <xref:System.Xml.Linq.XElement> objeto, que se torna um elemento filho. Você pode passar um <xref:System.Xml.Linq.XAttribute> objeto, que se torna um atributo do elemento. Ou você pode passar qualquer outro tipo de objeto, que é convertido em uma cadeia de caracteres e torna\-se o conteúdo de texto do elemento.  
  
-   O <xref:System.Xml.Linq.XElement> construtor aceita um `params` matriz do tipo <xref:System.Object>, de modo que você pode passar qualquer número de objetos para o construtor. Isso permite que você crie um elemento que tem conteúdo complexo.  
  
-   Se um objeto implementa <xref:System.Collections.Generic.IEnumerable%601>, a coleção do objeto será enumerada, e todos os itens da coleção são adicionados. Se a coleção contiver <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XAttribute> objetos, cada item da coleção será adicionado separadamente. Isso é importante porque permite que você passe os resultados de uma [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] consulta para o construtor.  
  
 Este é um exemplo:  
  
 Esses recursos permitem que você escrever código usando literais XML para criar uma árvore XML e também para escrever um código que usa os resultados de [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] consultas quando você cria uma árvore XML:  
  
```vb  
Dim srcTree As XElement = _  
    <Root>  
        <Element>1</Element>  
        <Element>2</Element>  
        <Element>3</Element>  
        <Element>4</Element>  
        <Element>5</Element>  
    </Root>  
Dim xmlTree As XElement = _  
    <Root>  
        <Child>1</Child>  
        <Child>2</Child>  
        <%= From el In srcTree.Elements() _  
            Where CInt(el) > 2 _  
            Select el %>  
    </Root>  
Console.WriteLine(xmlTree)  
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
 [Criando árvores XML \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)