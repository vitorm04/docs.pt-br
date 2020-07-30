---
title: Como localizar um elemento com um elemento filho específico (C#)
description: Saiba como localizar um elemento que tem um elemento filho específico. Consulte exemplos de código e recursos adicionais.
ms.date: 07/20/2015
ms.assetid: 00cf5555-374e-4369-bf93-7bd2e7f21db3
ms.openlocfilehash: 1d02f3d3af0a3711a5361941727e2e0b6c8bbdc9
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301704"
---
# <a name="how-to-find-an-element-with-a-specific-child-element-c"></a><span data-ttu-id="a2a1b-104">Como localizar um elemento com um elemento filho específico (C#)</span><span class="sxs-lookup"><span data-stu-id="a2a1b-104">How to find an element with a specific child element (C#)</span></span>
<span data-ttu-id="a2a1b-105">Este tópico mostra como localizar determinado elemento que tem um elemento filho com um valor específico.</span><span class="sxs-lookup"><span data-stu-id="a2a1b-105">This topic shows how to find a particular element that has a child element with a specific value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a2a1b-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a2a1b-106">Example</span></span>  
 <span data-ttu-id="a2a1b-107">O exemplo localiza o elemento `Test` que possui um elemento filho `CommandLine` com o valor "Examp2.EXE".</span><span class="sxs-lookup"><span data-stu-id="a2a1b-107">The example finds the `Test` element that has a `CommandLine` child element with the value of "Examp2.EXE".</span></span>  
  
 <span data-ttu-id="a2a1b-108">Este exemplo usa o seguinte documento XML: [Arquivo XML de exemplo: configuração de teste (LINQ to XML)](./sample-xml-file-test-configuration-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="a2a1b-108">This example uses the following XML document: [Sample XML File: Test Configuration (LINQ to XML)](./sample-xml-file-test-configuration-linq-to-xml.md).</span></span>  
  
```csharp  
XElement root = XElement.Load("TestConfig.xml");  
IEnumerable<XElement> tests =  
    from el in root.Elements("Test")  
    where (string)el.Element("CommandLine") == "Examp2.EXE"  
    select el;  
foreach (XElement el in tests)  
    Console.WriteLine((string)el.Attribute("TestId"));  
```  
  
 <span data-ttu-id="a2a1b-109">Este código produz a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="a2a1b-109">This code produces the following output:</span></span>  
  
```output  
0002  
0006  
```  
  
## <a name="example"></a><span data-ttu-id="a2a1b-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a2a1b-110">Example</span></span>  
 <span data-ttu-id="a2a1b-111">O exemplo a seguir mostra a mesma consulta para XML que está em um namespace.</span><span class="sxs-lookup"><span data-stu-id="a2a1b-111">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="a2a1b-112">Para obter mais informações, consulte [Visão geral de namespaces (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="a2a1b-112">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="a2a1b-113">Este exemplo usa o seguinte documento XML: [Arquivo XML de exemplo: configuração de teste em um namespace](./sample-xml-file-test-configuration-in-a-namespace1.md).</span><span class="sxs-lookup"><span data-stu-id="a2a1b-113">This example uses the following XML document: [Sample XML File: Test Configuration in a Namespace](./sample-xml-file-test-configuration-in-a-namespace1.md).</span></span>  
  
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
  
 <span data-ttu-id="a2a1b-114">Este código produz a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="a2a1b-114">This code produces the following output:</span></span>  
  
```output  
0002  
0006  
```  
  
## <a name="see-also"></a><span data-ttu-id="a2a1b-115">Veja também</span><span class="sxs-lookup"><span data-stu-id="a2a1b-115">See also</span></span>

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [<span data-ttu-id="a2a1b-116">Visão geral de operadores de consulta padrão (C#)</span><span class="sxs-lookup"><span data-stu-id="a2a1b-116">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="a2a1b-117">Operações de projeção (C#)</span><span class="sxs-lookup"><span data-stu-id="a2a1b-117">Projection Operations (C#)</span></span>](./projection-operations.md)
