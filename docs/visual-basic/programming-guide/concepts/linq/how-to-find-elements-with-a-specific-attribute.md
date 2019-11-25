---
title: Como localizar elementos com um atributo específico (XPath-LINQ para XML)
ms.date: 07/20/2015
ms.assetid: 4bb38d2c-bc7c-4196-8909-aaf41fb86b28
ms.openlocfilehash: ef8dd26d40f15d3d5a27f0ca5d62f7337f2054ca
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343683"
---
# <a name="how-to-find-elements-with-a-specific-attribute-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="4eeef-102">How to: Find Elements with a Specific Attribute (XPath-LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4eeef-102">How to: Find Elements with a Specific Attribute (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="4eeef-103">Às vezes você deseja localizar todos os elementos que têm um atributo específico.</span><span class="sxs-lookup"><span data-stu-id="4eeef-103">Sometimes you want to find all elements that have a specific attribute.</span></span> <span data-ttu-id="4eeef-104">Você não está preocupado com o conteúdo do atributo.</span><span class="sxs-lookup"><span data-stu-id="4eeef-104">You are not concerned about the contents of the attribute.</span></span> <span data-ttu-id="4eeef-105">Você quer selecionar com base na existência do atributo.</span><span class="sxs-lookup"><span data-stu-id="4eeef-105">Instead, you want to select based on the existence of the attribute.</span></span>  
  
 <span data-ttu-id="4eeef-106">A expressão XPath é:</span><span class="sxs-lookup"><span data-stu-id="4eeef-106">The XPath expression is:</span></span>  
  
 `./*[@Select]`  
  
## <a name="example"></a><span data-ttu-id="4eeef-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4eeef-107">Example</span></span>  
 <span data-ttu-id="4eeef-108">O código a seguir seleciona apenas os elementos que têm o atributo `Select`.</span><span class="sxs-lookup"><span data-stu-id="4eeef-108">The following code selects just the elements that have the `Select` attribute.</span></span>  
  
```vb  
Dim doc As XElement = _   
    <Root>  
        <Child1>1</Child1>  
        <Child2 Select='true'>2</Child2>  
        <Child3>3</Child3>  
        <Child4 Select='true'>4</Child4>  
        <Child5>5</Child5>  
    </Root>  
  
' LINQ to XML query  
Dim list1 As IEnumerable(Of XElement) = _  
    From el In doc.Elements() _  
    Where el.@Select <> Nothing _  
    Select el  
  
' XPath expression  
Dim list2 As IEnumerable(Of XElement) = DirectCast(doc.XPathEvaluate _  
    ("./*[@Select]"), IEnumerable).Cast(Of XElement)()  
  
If list1.Count() = list2.Count() And _  
    list1.Intersect(list2).Count() = list1.Count() Then  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
  
For Each el As XElement In list1  
    Console.WriteLine(el)  
Next  
```  
  
 <span data-ttu-id="4eeef-109">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="4eeef-109">This example produces the following output:</span></span>  
  
```console
Results are identical  
<Child2 Select="true">2</Child2>  
<Child4 Select="true">4</Child4>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4eeef-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4eeef-110">See also</span></span>

- [<span data-ttu-id="4eeef-111">LINQ to XML for XPath Users (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4eeef-111">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
