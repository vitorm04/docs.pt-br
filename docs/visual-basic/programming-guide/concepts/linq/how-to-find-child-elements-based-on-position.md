---
title: "Como: localizar elementos filho com base na posição (XPath-LINQ para XML) (Visual Basic) | Documentos do Microsoft"
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
ms.assetid: 6831e1db-5e97-444f-a7a1-d0a87104b005
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: 14abadaf548e228244a1ff7ca72fa3896ef4eb5d
ms.openlocfilehash: 5e42a12605eecc6633da45342ee0111dcc4b0cc1
ms.contentlocale: pt-br
ms.lasthandoff: 05/23/2017


---
# <a name="how-to-find-child-elements-based-on-position-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="3d23f-102">Como: localizar elementos filho com base na posição (XPath-LINQ para XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3d23f-102">How to: Find Child Elements Based on Position (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="3d23f-103">Às vezes você deseja localizar elementos com base em sua posição.</span><span class="sxs-lookup"><span data-stu-id="3d23f-103">Sometimes you want to find elements based on their position.</span></span> <span data-ttu-id="3d23f-104">Você pode desejar localizar o segundo elemento, ou você talvez queira localizar o terceiro através do quinto elemento.</span><span class="sxs-lookup"><span data-stu-id="3d23f-104">You might want to find the second element, or you might want to find the third through the fifth element.</span></span>  
  
 <span data-ttu-id="3d23f-105">A expressão XPath é:</span><span class="sxs-lookup"><span data-stu-id="3d23f-105">The XPath expression is:</span></span>  
  
 `Test[position() >= 2 and position() <= 4]`  
  
 <span data-ttu-id="3d23f-106">Há duas abordagens para escrever esta consulta de [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] de uma maneira lazy.</span><span class="sxs-lookup"><span data-stu-id="3d23f-106">There are two approaches to writing this [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] query in a lazy way.</span></span> <span data-ttu-id="3d23f-107">Você pode usar o <xref:System.Linq.Enumerable.Skip%2A>e <xref:System.Linq.Enumerable.Take%2A>operadores, ou você pode usar o <xref:System.Linq.Enumerable.Where%2A>sobrecarga que utiliza um índice.</xref:System.Linq.Enumerable.Where%2A> </xref:System.Linq.Enumerable.Take%2A> </xref:System.Linq.Enumerable.Skip%2A></span><span class="sxs-lookup"><span data-stu-id="3d23f-107">You can use the <xref:System.Linq.Enumerable.Skip%2A> and <xref:System.Linq.Enumerable.Take%2A> operators, or you can use the <xref:System.Linq.Enumerable.Where%2A> overload that takes an index.</span></span> <span data-ttu-id="3d23f-108">Quando você usa o <xref:System.Linq.Enumerable.Where%2A>sobrecarga, você usar uma expressão lambda que leva dois argumentos.</xref:System.Linq.Enumerable.Where%2A></span><span class="sxs-lookup"><span data-stu-id="3d23f-108">When you use the <xref:System.Linq.Enumerable.Where%2A> overload, you use a lambda expression that takes two arguments.</span></span> <span data-ttu-id="3d23f-109">O exemplo a seguir mostra os dois métodos de selecione a posição de functionamento base.</span><span class="sxs-lookup"><span data-stu-id="3d23f-109">The following example shows both methods of selecting based on position.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3d23f-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3d23f-110">Example</span></span>  
 <span data-ttu-id="3d23f-111">Este exemplo localiza o segundo a quarto elemento de `Test` .</span><span class="sxs-lookup"><span data-stu-id="3d23f-111">This example finds the second through the fourth `Test` element.</span></span> <span data-ttu-id="3d23f-112">O resultado é uma coleção de elementos.</span><span class="sxs-lookup"><span data-stu-id="3d23f-112">The result is a collection of elements.</span></span>  
  
 <span data-ttu-id="3d23f-113">Este exemplo usa o seguinte documento XML: [arquivo XML de exemplo: configuração de teste (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-test-configuration-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="3d23f-113">This example uses the following XML document: [Sample XML File: Test Configuration (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-test-configuration-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="3d23f-114">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="3d23f-114">This example produces the following output:</span></span>  
  
```  
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
  
## <a name="see-also"></a><span data-ttu-id="3d23f-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3d23f-115">See Also</span></span>  
 [<span data-ttu-id="3d23f-116">LINQ to XML para XPath usuários (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3d23f-116">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)

