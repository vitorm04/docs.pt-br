---
title: Como localizar elementos filho com base na LINQ to XML de posição
description: 'Saiba como localizar elementos de localização com base na posição do elemento. Três métodos são mostrados: um que usa XPathEvaluate, dois que usam LINQ to XML consulta.'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: e35bb269-ec86-4c96-8321-12491a0eb2c3
ms.openlocfilehash: 242bc179be86e14daab4acb66596207f3272bfea
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552331"
---
# <a name="how-to-find-child-elements-based-on-position-linq-to-xml"></a><span data-ttu-id="c218c-104">Como localizar elementos filho com base na posição (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="c218c-104">How to find child elements based on position (LINQ to XML)</span></span>

<span data-ttu-id="c218c-105">Este artigo mostra como usar <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> o para localizar elementos com base na posição do elemento – por exemplo, para encontrar o segundo elemento ou o terceiro por meio do quinto.</span><span class="sxs-lookup"><span data-stu-id="c218c-105">This article shows how to use <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> to find elements based on element position – for example, to find the second element, or the third through the fifth.</span></span> <span data-ttu-id="c218c-106">Ele também mostra duas maneiras de usar LINQ to XML consulta para fazer a mesma coisa.</span><span class="sxs-lookup"><span data-stu-id="c218c-106">It also shows two ways to use LINQ to XML query to do the same thing.</span></span>

<span data-ttu-id="c218c-107">Há duas abordagens para escrever essa LINQ to XML consulta de maneira lenta.</span><span class="sxs-lookup"><span data-stu-id="c218c-107">There are two approaches to writing this LINQ to XML query in a lazy way.</span></span> <span data-ttu-id="c218c-108">Você pode usar os operadores de <xref:System.Linq.Enumerable.Skip%2A> e de <xref:System.Linq.Enumerable.Take%2A> , ou você pode usar a sobrecarga de <xref:System.Linq.Enumerable.Where%2A> que usa um índice.</span><span class="sxs-lookup"><span data-stu-id="c218c-108">You can use the <xref:System.Linq.Enumerable.Skip%2A> and <xref:System.Linq.Enumerable.Take%2A> operators, or you can use the <xref:System.Linq.Enumerable.Where%2A> overload that takes an index.</span></span> <span data-ttu-id="c218c-109">Quando você usa a sobrecarga de <xref:System.Linq.Enumerable.Where%2A> , você usa uma expressão lambda que leva dois argumentos.</span><span class="sxs-lookup"><span data-stu-id="c218c-109">When you use the <xref:System.Linq.Enumerable.Where%2A> overload, you use a lambda expression that takes two arguments.</span></span> <span data-ttu-id="c218c-110">O exemplo a seguir mostra os dois métodos de selecione a posição de functionamento base.</span><span class="sxs-lookup"><span data-stu-id="c218c-110">The following example shows both methods of selecting based on position.</span></span>

## <a name="example-find-the-second-through-the-fourth-test-elements"></a><span data-ttu-id="c218c-111">Exemplo: Localize o segundo por meio dos quarto `Test` elementos</span><span class="sxs-lookup"><span data-stu-id="c218c-111">Example: Find the second through the fourth `Test` elements</span></span>

<span data-ttu-id="c218c-112">Este exemplo localiza o segundo por meio do quarto `Test` elemento no [arquivo XML de exemplo: configuração de teste](sample-xml-file-test-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="c218c-112">This example finds the second through the fourth `Test` element in the [Sample XML file: Test configuration](sample-xml-file-test-configuration.md).</span></span> <span data-ttu-id="c218c-113">O resultado é uma coleção de elementos.</span><span class="sxs-lookup"><span data-stu-id="c218c-113">The result is a collection of elements.</span></span>

<span data-ttu-id="c218c-114">A expressão XPath é `Test[position() >= 2 and position() <= 4]`.</span><span class="sxs-lookup"><span data-stu-id="c218c-114">The XPath expression is `Test[position() >= 2 and position() <= 4]`.</span></span>

```csharp
XElement testCfg = XElement.Load("TestConfig.xml");

// LINQ to XML query
IEnumerable<XElement> list1 =
    testCfg
    .Elements("Test")
    .Skip(1)
    .Take(3);

// LINQ to XML query
IEnumerable<XElement> list2 =
    testCfg
    .Elements("Test")
    .Where((el, idx) => idx >= 1 && idx <= 3);

// XPath expression
IEnumerable<XElement> list3 =
  testCfg.XPathSelectElements("Test[position() >= 2 and position() <= 4]");

if (list1.Count() == list2.Count() &&
    list1.Count() == list3.Count() &&
    list1.Intersect(list2).Count() == list1.Count() &&
    list1.Intersect(list3).Count() == list1.Count())
    Console.WriteLine("Results are identical");
else
    Console.WriteLine("Results differ");
foreach (XElement el in list1)
    Console.WriteLine(el);
```

```vb
Dim testCfg As XElement = XElement.Load("TestConfig.xml")

' LINQ to XML query
Dim list1 As IEnumerable(Of XElement) = _
    testCfg.Elements("Test").Skip(1).Take(3)

'LINQ to XML query
Dim list2 As IEnumerable(Of XElement) = _
    testCfg.Elements("Test"). _
    Where(Function(ByVal el, ByVal idx) idx >= 1 And idx <= 3)

' XPath expression
Dim list3 As IEnumerable(Of XElement) = _
    testCfg.XPathSelectElements("Test[position() >= 2 and position() <= 4]")

If list1.Count() = list2.Count() And _
       list1.Count() = list3.Count() And _
       list1.Intersect(list2).Count() = list1.Count() And _
       list1.Intersect(list3).Count() = list1.Count() Then

    Console.WriteLine("Results are identical")
Else
    Console.WriteLine("Results differ")
End If

For Each el As XElement In list1
    Console.WriteLine(el)
Next
```

<span data-ttu-id="c218c-115">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="c218c-115">This example produces the following output:</span></span>

```output
Results are identical
<Test TestId="0002" TestType="CMD">
  <Name>Find succeeding characters</Name>
  <CommandLine>Examp2.EXE</CommandLine>
  <Input>abc</Input>
  <Output>def</Output>
</Test>
<Test TestId="0003" TestType="GUI">
  <Name>Convert multiple numbers to strings</Name>
  <CommandLine>Examp2.EXE /Verbose</CommandLine>
  <Input>123</Input>
  <Output>One Two Three</Output>
</Test>
<Test TestId="0004" TestType="GUI">
  <Name>Find correlated key</Name>
  <CommandLine>Examp3.EXE</CommandLine>
  <Input>a1</Input>
  <Output>b1</Output>
</Test>
```

## <a name="see-also"></a><span data-ttu-id="c218c-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="c218c-116">See also</span></span>

- [<span data-ttu-id="c218c-117">LINQ to XML para usuários do XPath (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c218c-117">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
