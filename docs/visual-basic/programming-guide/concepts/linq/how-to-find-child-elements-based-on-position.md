---
title: 'Como: Localizar elementos filho com base na posição (XPath-LINQ to XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 6831e1db-5e97-444f-a7a1-d0a87104b005
ms.openlocfilehash: 11a9fdd7ed8565c38b0527d266af75b8fb611a20
ms.sourcegitcommit: d7c298f6c2e3aab0c7498bfafc0a0a94ea1fe23e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/10/2019
ms.locfileid: "72249702"
---
# <a name="how-to-find-child-elements-based-on-position-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="77b45-102">Como: Localizar elementos filho com base na posição (XPath-LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="77b45-102">How to: Find Child Elements Based on Position (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="77b45-103">Às vezes você deseja localizar elementos com base em sua posição.</span><span class="sxs-lookup"><span data-stu-id="77b45-103">Sometimes you want to find elements based on their position.</span></span> <span data-ttu-id="77b45-104">Você pode desejar localizar o segundo elemento, ou você talvez queira localizar o terceiro através do quinto elemento.</span><span class="sxs-lookup"><span data-stu-id="77b45-104">You might want to find the second element, or you might want to find the third through the fifth element.</span></span>  
  
 <span data-ttu-id="77b45-105">A expressão XPath é:</span><span class="sxs-lookup"><span data-stu-id="77b45-105">The XPath expression is:</span></span>  
  
 `Test[position() >= 2 and position() <= 4]`  
  
 <span data-ttu-id="77b45-106">Há duas abordagens para escrever esta consulta de [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] de uma maneira lazy.</span><span class="sxs-lookup"><span data-stu-id="77b45-106">There are two approaches to writing this [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query in a lazy way.</span></span> <span data-ttu-id="77b45-107">Você pode usar os operadores de <xref:System.Linq.Enumerable.Skip%2A> e de <xref:System.Linq.Enumerable.Take%2A> , ou você pode usar a sobrecarga de <xref:System.Linq.Enumerable.Where%2A> que usa um índice.</span><span class="sxs-lookup"><span data-stu-id="77b45-107">You can use the <xref:System.Linq.Enumerable.Skip%2A> and <xref:System.Linq.Enumerable.Take%2A> operators, or you can use the <xref:System.Linq.Enumerable.Where%2A> overload that takes an index.</span></span> <span data-ttu-id="77b45-108">Quando você usa a sobrecarga de <xref:System.Linq.Enumerable.Where%2A> , você usa uma expressão lambda que leva dois argumentos.</span><span class="sxs-lookup"><span data-stu-id="77b45-108">When you use the <xref:System.Linq.Enumerable.Where%2A> overload, you use a lambda expression that takes two arguments.</span></span> <span data-ttu-id="77b45-109">O exemplo a seguir mostra os dois métodos de selecione a posição de functionamento base.</span><span class="sxs-lookup"><span data-stu-id="77b45-109">The following example shows both methods of selecting based on position.</span></span>  
  
## <a name="example"></a><span data-ttu-id="77b45-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="77b45-110">Example</span></span>  
 <span data-ttu-id="77b45-111">Este exemplo localiza o segundo a quarto elemento de `Test` .</span><span class="sxs-lookup"><span data-stu-id="77b45-111">This example finds the second through the fourth `Test` element.</span></span> <span data-ttu-id="77b45-112">O resultado é uma coleção de elementos.</span><span class="sxs-lookup"><span data-stu-id="77b45-112">The result is a collection of elements.</span></span>  
  
 <span data-ttu-id="77b45-113">Este exemplo usa o seguinte documento XML: [Arquivo XML de exemplo: Configuração de teste (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-test-configuration-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="77b45-113">This example uses the following XML document: [Sample XML File: Test Configuration (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-test-configuration-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="77b45-114">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="77b45-114">This example produces the following output:</span></span>  
  
```console  
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
  
## <a name="see-also"></a><span data-ttu-id="77b45-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="77b45-115">See also</span></span>

- [<span data-ttu-id="77b45-116">LINQ to XML para usuários do XPath (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="77b45-116">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
