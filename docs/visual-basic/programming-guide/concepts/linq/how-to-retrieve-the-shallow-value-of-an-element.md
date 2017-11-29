---
title: 'Como: recuperar o valor raso de um elemento (Visual Basic)'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 730a6670-fb8c-41fc-8a1b-eb97a837e432
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 673b890ab842d1c18c8020eefe03d90086d1bf4e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-retrieve-the-shallow-value-of-an-element-visual-basic"></a><span data-ttu-id="3cc8a-102">Como: recuperar o valor raso de um elemento (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3cc8a-102">How to: Retrieve the Shallow Value of an Element (Visual Basic)</span></span>
<span data-ttu-id="3cc8a-103">Este tópico mostra como obter o valor raso de um elemento.</span><span class="sxs-lookup"><span data-stu-id="3cc8a-103">This topic shows how to get the shallow value of an element.</span></span> <span data-ttu-id="3cc8a-104">O valor raso é o valor do elemento específico somente, diferentemente de valor maior, que inclui os valores de todos os elementos descendentes concatenados em uma única cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="3cc8a-104">The shallow value is the value of the specific element only, as opposed to the deep value, which includes the values of all descendent elements concatenated into a single string.</span></span>  
  
 <span data-ttu-id="3cc8a-105">Quando você recupera um valor de elemento usando conversão ou propriedade de <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> , você recupera o valor maior.</span><span class="sxs-lookup"><span data-stu-id="3cc8a-105">When you retrieve an element value by using either casting or the <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> property, you retrieve the deep value.</span></span> <span data-ttu-id="3cc8a-106">Para recuperar o valor raso, você pode usar o método de extensão de `ShallowValue` , conforme mostrado no exemplo follwing.</span><span class="sxs-lookup"><span data-stu-id="3cc8a-106">To retrieve the shallow value, you can use the `ShallowValue` extension method, as shown in the follwing example.</span></span> <span data-ttu-id="3cc8a-107">Recuperar o valor raso é útil quando você deseja selecionar elementos com base no conteúdo.</span><span class="sxs-lookup"><span data-stu-id="3cc8a-107">Retrieving the shallow value is useful when you want to select elements based on their content.</span></span>  
  
 <span data-ttu-id="3cc8a-108">O exemplo a seguir declara um método de extensão que recupera o valor raso de um elemento.</span><span class="sxs-lookup"><span data-stu-id="3cc8a-108">The following example declares an extension method that retrieves the shallow value of an element.</span></span> <span data-ttu-id="3cc8a-109">Use o método de extensão em uma consulta para listar todos os elementos que contém um valor calculado.</span><span class="sxs-lookup"><span data-stu-id="3cc8a-109">It then uses the extension method in a query to list all elements that contain a calculated value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3cc8a-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3cc8a-110">Example</span></span>  
 <span data-ttu-id="3cc8a-111">O seguinte arquivo de texto, Report.xml, é a fonte para esse exemplo.</span><span class="sxs-lookup"><span data-stu-id="3cc8a-111">The following text file, Report.xml, is the source for this example.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<Report>  
  <Section>  
    <Heading>  
      <Column Name="CustomerId">=Customer.CustomerId.Heading</Column>  
      <Column Name="Name">=Customer.Name.Heading</Column>  
    </Heading>  
    <Detail>  
      <Column Name="CustomerId">=Customer.CustomerId</Column>  
      <Column Name="Name">=Customer.Name</Column>  
    </Detail>  
  </Section>  
</Report>  
```  
  
```vb  
Module Module1  
    <System.Runtime.CompilerServices.Extension()> _  
    Public Function ShallowValue(ByVal xe As XElement)  
        Return xe _  
               .Nodes() _  
               .OfType(Of XText)() _  
               .Aggregate(New StringBuilder(), _  
                              Function(s, c) s.Append(c), _  
                              Function(s) s.ToString())  
    End Function  
  
    Sub Main()  
        Dim root As XElement = XElement.Load("Report.xml")  
  
        Dim query As IEnumerable(Of XElement) = _  
            From el In root.Descendants() _  
            Where (el.ShallowValue().StartsWith("=")) _  
            Select el  
  
        For Each q As XElement In query  
            Console.WriteLine("{0}{1}{2}", _  
                q.Name.ToString().PadRight(8), _  
                q.Attribute("Name").ToString().PadRight(20), _  
                q.ShallowValue())  
        Next  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="3cc8a-112">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="3cc8a-112">This example produces the following output:</span></span>  
  
```  
Column  Name="CustomerId"   =Customer.CustomerId.Heading  
Column  Name="Name"         =Customer.Name.Heading  
Column  Name="CustomerId"   =Customer.CustomerId  
Column  Name="Name"         =Customer.Name  
```  
  
## <a name="see-also"></a><span data-ttu-id="3cc8a-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3cc8a-113">See Also</span></span>  
 [<span data-ttu-id="3cc8a-114">Eixos LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3cc8a-114">LINQ to XML Axes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
