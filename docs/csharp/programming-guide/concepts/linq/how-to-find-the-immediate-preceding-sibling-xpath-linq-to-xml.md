---
title: Como encontrar o irmão precedentes imediatos (XPath-LINQ to XML)C#()
ms.date: 07/20/2015
ms.assetid: 74c06201-0b1b-4b5e-b3ac-0092980614e6
ms.openlocfilehash: 1e5aece41021642d43b7f6f7b78bb105156ee4ee
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141010"
---
# <a name="how-to-find-the-immediate-preceding-sibling-xpath-linq-to-xml-c"></a>Como encontrar o irmão precedentes imediatos (XPath-LINQ to XML)C#()
Às vezes você deseja encontrar o irmão anterior imediato a um nó. Devido a diferença na semântica de predicados posicionais para os eixos anterior irmãos no XPath ao contrário de [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], essa é uma das comparações mais interessantes.  
  
## <a name="example"></a>Exemplo  
 Neste exemplo, a consulta [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] usa o operador <xref:System.Linq.Enumerable.Last%2A> para encontrar o último nó na coleção retornada por <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A>. Por outro lado, a expressão XPath usa um predicado com um valor de 1 para localizar o elemento imediatamente anterior.  
  
```csharp  
XElement root = XElement.Parse(  
    @"<Root>  
    <Child1/>  
    <Child2/>  
    <Child3/>  
    <Child4/>  
</Root>");  
XElement child4 = root.Element("Child4");  
  
// LINQ to XML query  
XElement el1 =  
    child4  
    .ElementsBeforeSelf()  
    .Last();  
  
// XPath expression  
XElement el2 =  
    ((IEnumerable)child4  
                 .XPathEvaluate("preceding-sibling::*[1]"))  
                 .Cast<XElement>()  
                 .First();  
  
if (el1 == el2)  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
Console.WriteLine(el1);  
```  
  
 Este exemplo gera a seguinte saída:  
  
```output  
Results are identical  
<Child3 />  
```  
