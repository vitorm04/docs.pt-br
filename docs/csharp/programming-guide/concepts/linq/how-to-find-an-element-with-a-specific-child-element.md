---
title: Como localizar um elemento com um elemento filho específico (C#)
ms.date: 07/20/2015
ms.assetid: 00cf5555-374e-4369-bf93-7bd2e7f21db3
ms.openlocfilehash: 0536b1b92d4d7fc18b5d406bbcd24aefc6a840c6
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141150"
---
# <a name="how-to-find-an-element-with-a-specific-child-element-c"></a><span data-ttu-id="0bb44-102">Como localizar um elemento com um elemento filho específico (C#)</span><span class="sxs-lookup"><span data-stu-id="0bb44-102">How to find an element with a specific child element (C#)</span></span>
<span data-ttu-id="0bb44-103">Este tópico mostra como localizar determinado elemento que tem um elemento filho com um valor específico.</span><span class="sxs-lookup"><span data-stu-id="0bb44-103">This topic shows how to find a particular element that has a child element with a specific value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0bb44-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0bb44-104">Example</span></span>  
 <span data-ttu-id="0bb44-105">O exemplo localiza o elemento `Test` que possui um elemento filho `CommandLine` com o valor "Examp2.EXE".</span><span class="sxs-lookup"><span data-stu-id="0bb44-105">The example finds the `Test` element that has a `CommandLine` child element with the value of "Examp2.EXE".</span></span>  
  
 <span data-ttu-id="0bb44-106">Este exemplo usa o seguinte documento XML: [Arquivo XML de exemplo: configuração de teste (LINQ to XML)](./sample-xml-file-test-configuration-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="0bb44-106">This example uses the following XML document: [Sample XML File: Test Configuration (LINQ to XML)](./sample-xml-file-test-configuration-linq-to-xml.md).</span></span>  
  
```csharp  
XElement root = XElement.Load("TestConfig.xml");  
IEnumerable<XElement> tests =  
    from el in root.Elements("Test")  
    where (string)el.Element("CommandLine") == "Examp2.EXE"  
    select el;  
foreach (XElement el in tests)  
    Console.WriteLine((string)el.Attribute("TestId"));  
```  
  
 <span data-ttu-id="0bb44-107">Esse código gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="0bb44-107">This code produces the following output:</span></span>  
  
```output  
0002  
0006  
```  
  
## <a name="example"></a><span data-ttu-id="0bb44-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0bb44-108">Example</span></span>  
 <span data-ttu-id="0bb44-109">O exemplo a seguir mostra a mesma consulta para XML que está em um namespace.</span><span class="sxs-lookup"><span data-stu-id="0bb44-109">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="0bb44-110">Para obter mais informações, consulte [Visão geral de namespaces (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="0bb44-110">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="0bb44-111">Este exemplo usa o seguinte documento XML: [Arquivo XML de exemplo: configuração de teste em um namespace](./sample-xml-file-test-configuration-in-a-namespace1.md).</span><span class="sxs-lookup"><span data-stu-id="0bb44-111">This example uses the following XML document: [Sample XML File: Test Configuration in a Namespace](./sample-xml-file-test-configuration-in-a-namespace1.md).</span></span>  
  
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
  
 <span data-ttu-id="0bb44-112">Esse código gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="0bb44-112">This code produces the following output:</span></span>  
  
```output  
0002  
0006  
```  
  
## <a name="see-also"></a><span data-ttu-id="0bb44-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0bb44-113">See also</span></span>

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [<span data-ttu-id="0bb44-114">Visão geral de operadores de consulta padrão (C#)</span><span class="sxs-lookup"><span data-stu-id="0bb44-114">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="0bb44-115">Operações de projeção (C#)</span><span class="sxs-lookup"><span data-stu-id="0bb44-115">Projection Operations (C#)</span></span>](./projection-operations.md)
