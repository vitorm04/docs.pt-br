---
title: 'Como: Localizar elementos com um atributo específico (XPath-LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: daed00dd-923a-43be-8a90-eee406f6f574
ms.openlocfilehash: c5b8ae9a41c5b05438d14f2717c8edfb151d47c0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54709371"
---
# <a name="how-to-find-elements-with-a-specific-attribute-xpath-linq-to-xml-c"></a><span data-ttu-id="bf8c4-102">Como: Localizar elementos com um atributo específico (XPath-LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="bf8c4-102">How to: Find Elements with a Specific Attribute (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="bf8c4-103">Às vezes você deseja localizar todos os elementos que têm um atributo específico.</span><span class="sxs-lookup"><span data-stu-id="bf8c4-103">Sometimes you want to find all elements that have a specific attribute.</span></span> <span data-ttu-id="bf8c4-104">Você não está preocupado com o conteúdo do atributo.</span><span class="sxs-lookup"><span data-stu-id="bf8c4-104">You are not concerned about the contents of the attribute.</span></span> <span data-ttu-id="bf8c4-105">Você quer selecionar com base na existência do atributo.</span><span class="sxs-lookup"><span data-stu-id="bf8c4-105">Instead, you want to select based on the existence of the attribute.</span></span>  
  
 <span data-ttu-id="bf8c4-106">A expressão XPath é:</span><span class="sxs-lookup"><span data-stu-id="bf8c4-106">The XPath expression is:</span></span>  
  
 `./*[@Select]`  
  
## <a name="example"></a><span data-ttu-id="bf8c4-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bf8c4-107">Example</span></span>  
 <span data-ttu-id="bf8c4-108">O código a seguir seleciona apenas os elementos que têm o atributo `Select`.</span><span class="sxs-lookup"><span data-stu-id="bf8c4-108">The following code selects just the elements that have the `Select` attribute.</span></span>  
  
```csharp  
XElement doc = XElement.Parse(  
@"<Root>  
    <Child1>1</Child1>  
    <Child2 Select='true'>2</Child2>  
    <Child3>3</Child3>  
    <Child4 Select='true'>4</Child4>  
    <Child5>5</Child5>  
</Root>");  
  
// LINQ to XML query  
IEnumerable<XElement> list1 =  
    from el in doc.Elements()  
    where el.Attribute("Select") != null  
    select el;  
  
// XPath expression  
IEnumerable<XElement> list2 =  
    ((IEnumerable)doc.XPathEvaluate("./*[@Select]")).Cast<XElement>();  
  
if (list1.Count() == list2.Count() &&  
        list1.Intersect(list2).Count() == list1.Count())  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="bf8c4-109">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="bf8c4-109">This example produces the following output:</span></span>  
  
```  
Results are identical  
<Child2 Select="true">2</Child2>  
<Child4 Select="true">4</Child4>  
```  
  
## <a name="see-also"></a><span data-ttu-id="bf8c4-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bf8c4-110">See also</span></span>

- [<span data-ttu-id="bf8c4-111">Usuários do LINQ to XML para XPath (C#)</span><span class="sxs-lookup"><span data-stu-id="bf8c4-111">LINQ to XML for XPath Users (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
