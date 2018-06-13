---
title: Como localizar um elemento com um elemento filho específico (C#)
ms.date: 07/20/2015
ms.assetid: 00cf5555-374e-4369-bf93-7bd2e7f21db3
ms.openlocfilehash: e7528784f898f0f9ba84095b080eb82f8458424e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33323882"
---
# <a name="how-to-find-an-element-with-a-specific-child-element-c"></a><span data-ttu-id="4075a-102">Como localizar um elemento com um elemento filho específico (C#)</span><span class="sxs-lookup"><span data-stu-id="4075a-102">How to: Find an Element with a Specific Child Element (C#)</span></span>
<span data-ttu-id="4075a-103">Este tópico mostra como localizar determinado elemento que tem um elemento filho com um valor específico.</span><span class="sxs-lookup"><span data-stu-id="4075a-103">This topic shows how to find a particular element that has a child element with a specific value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4075a-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4075a-104">Example</span></span>  
 <span data-ttu-id="4075a-105">O exemplo localiza o elemento `Test` que possui um elemento filho `CommandLine` com o valor "Examp2.EXE".</span><span class="sxs-lookup"><span data-stu-id="4075a-105">The example finds the `Test` element that has a `CommandLine` child element with the value of "Examp2.EXE".</span></span>  
  
 <span data-ttu-id="4075a-106">Este exemplo usa o seguinte documento XML: [Arquivo XML de exemplo: configuração de teste (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-test-configuration-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="4075a-106">This example uses the following XML document: [Sample XML File: Test Configuration (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-test-configuration-linq-to-xml.md).</span></span>  
  
```csharp  
XElement root = XElement.Load("TestConfig.xml");  
IEnumerable<XElement> tests =  
    from el in root.Elements("Test")  
    where (string)el.Element("CommandLine") == "Examp2.EXE"  
    select el;  
foreach (XElement el in tests)  
    Console.WriteLine((string)el.Attribute("TestId"));  
```  
  
 <span data-ttu-id="4075a-107">Esse código gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="4075a-107">This code produces the following output:</span></span>  
  
```  
0002  
0006  
```  
  
## <a name="example"></a><span data-ttu-id="4075a-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4075a-108">Example</span></span>  
 <span data-ttu-id="4075a-109">O exemplo a seguir mostra a mesma consulta para XML que está em um namespace.</span><span class="sxs-lookup"><span data-stu-id="4075a-109">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="4075a-110">Para obter mais informações, consulte [Trabalhando com namespaces XML (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="4075a-110">For more information, see [Working with XML Namespaces (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
 <span data-ttu-id="4075a-111">Este exemplo usa o seguinte documento XML: [Arquivo XML de exemplo: configuração de teste em um namespace](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-test-configuration-in-a-namespace1.md).</span><span class="sxs-lookup"><span data-stu-id="4075a-111">This example uses the following XML document: [Sample XML File: Test Configuration in a Namespace](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-test-configuration-in-a-namespace1.md).</span></span>  
  
```csharp  
XElement root = XElement.Load("TestConfigInNamespace.xml");  
XNamespace ad = "http://www.adatum.com";  
IEnumerable<XElement> tests =  
    from el in root.Elements(ad + "Test")  
    where (string)el.Element(ad + "CommandLine") == "Examp2.EXE"  
    select el;  
foreach (XElement el in tests)  
    Console.WriteLine((string)el.Attribute("TestId"));  
```  
  
 <span data-ttu-id="4075a-112">Esse código gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="4075a-112">This code produces the following output:</span></span>  
  
```  
0002  
0006  
```  
  
## <a name="see-also"></a><span data-ttu-id="4075a-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4075a-113">See Also</span></span>  
 <xref:System.Xml.Linq.XElement.Attribute%2A>  
 <xref:System.Xml.Linq.XContainer.Elements%2A>  
 [<span data-ttu-id="4075a-114">Consultas básicas (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="4075a-114">Basic Queries (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)  
 [<span data-ttu-id="4075a-115">Visão geral de operadores de consulta padrão (C#)</span><span class="sxs-lookup"><span data-stu-id="4075a-115">Standard Query Operators Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [<span data-ttu-id="4075a-116">Operações de projeção (C#)</span><span class="sxs-lookup"><span data-stu-id="4075a-116">Projection Operations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/projection-operations.md)
