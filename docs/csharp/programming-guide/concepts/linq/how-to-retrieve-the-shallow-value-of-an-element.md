---
title: 'Como: Recuperar o valor superficial de um elemento (C#)'
ms.date: 07/20/2015
ms.assetid: 924a2699-72f6-4be1-aaa6-de62f8ec73b9
ms.openlocfilehash: 593fe1c22664f1e4e8322cb8816e58f4721c5bf8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54672820"
---
# <a name="how-to-retrieve-the-shallow-value-of-an-element-c"></a><span data-ttu-id="16d65-102">Como: Recuperar o valor superficial de um elemento (C#)</span><span class="sxs-lookup"><span data-stu-id="16d65-102">How to: Retrieve the Shallow Value of an Element (C#)</span></span>
<span data-ttu-id="16d65-103">Este tópico mostra como obter o valor raso de um elemento.</span><span class="sxs-lookup"><span data-stu-id="16d65-103">This topic shows how to get the shallow value of an element.</span></span> <span data-ttu-id="16d65-104">O valor raso é o valor do elemento específico somente, diferentemente de valor maior, que inclui os valores de todos os elementos descendentes concatenados em uma única cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="16d65-104">The shallow value is the value of the specific element only, as opposed to the deep value, which includes the values of all descendent elements concatenated into a single string.</span></span>  
  
 <span data-ttu-id="16d65-105">Quando você recupera um valor de elemento usando conversão ou propriedade de <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> , você recupera o valor maior.</span><span class="sxs-lookup"><span data-stu-id="16d65-105">When you retrieve an element value by using either casting or the <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> property, you retrieve the deep value.</span></span> <span data-ttu-id="16d65-106">Para recuperar o valor raso, você pode usar o método de extensão de `ShallowValue`, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="16d65-106">To retrieve the shallow value, you can use the `ShallowValue` extension method, as shown in the following example.</span></span> <span data-ttu-id="16d65-107">Recuperar o valor raso é útil quando você deseja selecionar elementos com base no conteúdo.</span><span class="sxs-lookup"><span data-stu-id="16d65-107">Retrieving the shallow value is useful when you want to select elements based on their content.</span></span>  
  
 <span data-ttu-id="16d65-108">O exemplo a seguir declara um método de extensão que recupera o valor raso de um elemento.</span><span class="sxs-lookup"><span data-stu-id="16d65-108">The following example declares an extension method that retrieves the shallow value of an element.</span></span> <span data-ttu-id="16d65-109">Use o método de extensão em uma consulta para listar todos os elementos que contém um valor calculado.</span><span class="sxs-lookup"><span data-stu-id="16d65-109">It then uses the extension method in a query to list all elements that contain a calculated value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="16d65-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="16d65-110">Example</span></span>  
 <span data-ttu-id="16d65-111">O seguinte arquivo de texto, Report.xml, é a fonte para esse exemplo.</span><span class="sxs-lookup"><span data-stu-id="16d65-111">The following text file, Report.xml, is the source for this example.</span></span>  
  
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
  
 <span data-ttu-id="16d65-112">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="16d65-112">This example produces the following output:</span></span>  
  
```  
Column  Name="CustomerId"   =Customer.CustomerId.Heading  
Column  Name="Name"         =Customer.Name.Heading  
Column  Name="CustomerId"   =Customer.CustomerId  
Column  Name="Name"         =Customer.Name  
```  
  
## <a name="see-also"></a><span data-ttu-id="16d65-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="16d65-113">See also</span></span>

- [<span data-ttu-id="16d65-114">Eixos do LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="16d65-114">LINQ to XML Axes (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md)
