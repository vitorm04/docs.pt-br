---
title: Construção funcional (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: feac4273-39ab-43ae-bab7-4059c807a785
ms.openlocfilehash: a51360d6c8d44770c462afb728a1fb78d3e2cd42
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75636842"
---
# <a name="functional-construction-linq-to-xml-visual-basic"></a>Construção funcional (LINQ to XML) (Visual Basic)
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] fornece uma maneira eficiente de criar elementos XML chamada *construção funcional*. Construção funcional é a capacidade de criar uma árvore XML em uma única instrução.  
  
 Há vários recursos chave da interface de programação do [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] que permitem a construção funcional:  
  
- O construtor <xref:System.Xml.Linq.XElement> utiliza vários tipos de argumentos para o conteúdo. Por exemplo, você pode passar outro objeto <xref:System.Xml.Linq.XElement>, que se torna um elemento filho. Você pode passar um objeto <xref:System.Xml.Linq.XAttribute>, que se torna um atributo do elemento. Ou você pode passar qualquer outro tipo de objeto, que é convertido em uma cadeia de caracteres e torna-se o conteúdo de texto do elemento.  
  
- O construtor <xref:System.Xml.Linq.XElement> utiliza uma matriz de `params` do tipo <xref:System.Object>, para que você possa passar qualquer número de objetos para o construtor. Isso permite que você crie um elemento que tem o conteúdo complexo.  
  
- Se um objeto implementar <xref:System.Collections.Generic.IEnumerable%601>, a coleção no objeto será enumerada, e todos os itens da coleção serão adicionados. Se a coleção contiver objetos <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XAttribute>, cada item da coleção será adicionado separadamente. Isso é importante porque permite que você passe os resultados de uma consulta LINQ para o construtor.  
  
 Veja um exemplo a seguir:  
  
 Esses recursos permitem que você escreva código usando literais XML para criar uma árvore XML e também para escrever código que usa os resultados de consultas LINQ quando você cria uma árvore XML:  
  
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
  
## <a name="see-also"></a>Veja também

- [Criando árvores XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)
