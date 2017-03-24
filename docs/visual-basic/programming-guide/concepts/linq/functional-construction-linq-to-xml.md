---
title: "Construção funcional (LINQ to XML) (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: feac4273-39ab-43ae-bab7-4059c807a785
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 9fa8cb3c97a1e23a863296c828c82b240e9ab5db
ms.lasthandoff: 03/13/2017

---
# <a name="functional-construction-linq-to-xml-visual-basic"></a>Construção funcional (LINQ to XML) (Visual Basic)
[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]Fornece uma maneira eficiente de criar elementos XML chamados *construção funcional*. Construção funcional é a capacidade de criar uma árvore XML em uma única instrução.  
  
 Há vários recursos chave da interface de programação do [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] que permitem a construção funcional:  
  
-   O <xref:System.Xml.Linq.XElement>construtor aceita vários tipos de argumentos para o conteúdo.</xref:System.Xml.Linq.XElement> Por exemplo, você pode passar outro <xref:System.Xml.Linq.XElement>objeto, que se torna um elemento filho.</xref:System.Xml.Linq.XElement> Você pode passar um <xref:System.Xml.Linq.XAttribute>objeto, que se torna um atributo do elemento.</xref:System.Xml.Linq.XAttribute> Ou você pode passar qualquer outro tipo de objeto, que é convertido em uma cadeia de caracteres e torna-se o conteúdo de texto do elemento.  
  
-   O <xref:System.Xml.Linq.XElement>construtor aceita um `params` matriz do tipo <xref:System.Object>, de modo que você pode passar qualquer número de objetos para o construtor.</xref:System.Object> </xref:System.Xml.Linq.XElement> Isso permite que você crie um elemento que tem o conteúdo complexo.  
  
-   Se um objeto implementa <xref:System.Collections.Generic.IEnumerable%601>, a coleção do objeto é enumerada e todos os itens na coleção serão adicionados.</xref:System.Collections.Generic.IEnumerable%601> Se a coleção contiver <xref:System.Xml.Linq.XElement>ou <xref:System.Xml.Linq.XAttribute>objetos, cada item da coleção será adicionado separadamente.</xref:System.Xml.Linq.XAttribute> </xref:System.Xml.Linq.XElement> Isso é importante porque permite que você passe os resultados de uma [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] consulta para o construtor.  
  
 A seguir está um exemplo:  
  
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
 [Criando árvores XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)
