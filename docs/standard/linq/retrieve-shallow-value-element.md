---
title: Como recuperar o valor superficial de um elemento-LINQ to XML
description: Use o `ShallowValue` método de extensão para recuperar o valor superficial de um elemento. O valor superficial é o valor somente daquele elemento; ou seja, ele não inclui os valores de elementos descendentes.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 924a2699-72f6-4be1-aaa6-de62f8ec73b9
ms.openlocfilehash: 761ffc07b13ebdc652b75bf96ba5b121c7912fd7
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552061"
---
# <a name="how-to-retrieve-the-shallow-value-of-an-element-linq-to-xml"></a><span data-ttu-id="9a75d-104">Como recuperar o valor superficial de um elemento (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="9a75d-104">How to retrieve the shallow value of an element (LINQ to XML)</span></span>

<span data-ttu-id="9a75d-105">Este artigo mostra como recuperar o valor superficial de um elemento, que é o valor somente daquele elemento, não incluindo valores de elementos descendentes.</span><span class="sxs-lookup"><span data-stu-id="9a75d-105">This article shows how to retrieve the shallow value of an element, which is the value of that element only, not including values of descendent elements.</span></span> <span data-ttu-id="9a75d-106">Recuperar o valor raso é útil quando você deseja selecionar elementos com base no conteúdo.</span><span class="sxs-lookup"><span data-stu-id="9a75d-106">Retrieving the shallow value is useful when you want to select elements based on their content.</span></span>

<span data-ttu-id="9a75d-107">Quando você usa a conversão ou a <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> propriedade para recuperar um valor de elemento, o valor inclui os descendentes.</span><span class="sxs-lookup"><span data-stu-id="9a75d-107">When you use casting or the <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> property to retrieve an element value, the value includes the descendants.</span></span> <span data-ttu-id="9a75d-108">Para recuperar o valor superficial, você pode usar o `ShallowValue` método de extensão, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="9a75d-108">To retrieve the shallow value you can use the `ShallowValue` extension method, as shown in the following example.</span></span> <span data-ttu-id="9a75d-109">O exemplo declara um método de extensão que recupera o valor superficial de um elemento.</span><span class="sxs-lookup"><span data-stu-id="9a75d-109">The example declares an extension method that retrieves the shallow value of an element.</span></span> <span data-ttu-id="9a75d-110">Use o método de extensão em uma consulta para listar todos os elementos que contém um valor calculado.</span><span class="sxs-lookup"><span data-stu-id="9a75d-110">It then uses the extension method in a query to list all elements that contain a calculated value.</span></span>

## <a name="example-use-the-shallowvalue-extension-method-to-retrieve-the-shallow-value-of-an-element"></a><span data-ttu-id="9a75d-111">Exemplo: usar o `ShallowValue` método de extensão para recuperar o valor superficial de um elemento</span><span class="sxs-lookup"><span data-stu-id="9a75d-111">Example: Use the `ShallowValue` extension method to retrieve the shallow value of an element</span></span>

<span data-ttu-id="9a75d-112">Os exemplos usam o arquivo de texto Report.xml que contém o seguinte:</span><span class="sxs-lookup"><span data-stu-id="9a75d-112">The examples uses the text file Report.xml that contains the following:</span></span>

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

<span data-ttu-id="9a75d-113">Este é o código para o exemplo:</span><span class="sxs-lookup"><span data-stu-id="9a75d-113">Here is the code for the example:</span></span>

```csharp
public static class MyExtensions
{
    public static string ShallowValue(this XElement xe)
    {
        return xe
               .Nodes()
               .OfType<XText>()
               .Aggregate(new StringBuilder(),
                          (s, c) => s.Append(c),
                          s => s.ToString());
    }
}

class Program
{
    static void Main(string[] args)
    {
        XElement root = XElement.Load("Report.xml");

        IEnumerable<XElement> query = from el in root.Descendants()
                                      where el.ShallowValue().StartsWith("=")
                                      select el;

        foreach (var q in query)
        {
            Console.WriteLine("{0}{1}{2}",
                q.Name.ToString().PadRight(8),
                q.Attribute("Name").ToString().PadRight(20),
                q.ShallowValue());
        }
    }
}
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

<span data-ttu-id="9a75d-114">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="9a75d-114">This example produces the following output:</span></span>

```output
Column  Name="CustomerId"   =Customer.CustomerId.Heading
Column  Name="Name"         =Customer.Name.Heading
Column  Name="CustomerId"   =Customer.CustomerId
Column  Name="Name"         =Customer.Name
```

## <a name="see-also"></a><span data-ttu-id="9a75d-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="9a75d-115">See also</span></span>

- [<span data-ttu-id="9a75d-116">Visão geral dos eixos de LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="9a75d-116">LINQ to XML axes overview</span></span>](linq-xml-axes-overview.md)
