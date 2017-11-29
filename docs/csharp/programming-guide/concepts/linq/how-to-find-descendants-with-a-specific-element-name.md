---
title: "Como localizar descendentes com um nome de elemento específico (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: f684da20-bee9-47f5-9607-7e3fd7e67470
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b1cc45f07accd7ae6dcc530f0fd5a9078bce949d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-find-descendants-with-a-specific-element-name-c"></a><span data-ttu-id="5ae48-102">Como localizar descendentes com um nome de elemento específico (C#)</span><span class="sxs-lookup"><span data-stu-id="5ae48-102">How to: Find Descendants with a Specific Element Name (C#)</span></span>
<span data-ttu-id="5ae48-103">Às vezes, você deseja localizar todos os descendentes com um nome específico.</span><span class="sxs-lookup"><span data-stu-id="5ae48-103">Sometimes you want to find all descendants with a particular name.</span></span> <span data-ttu-id="5ae48-104">Você poderia escrever um código para iterar por todos os descendentes, mas é mais fácil usar o eixo <xref:System.Xml.Linq.XContainer.Descendants%2A>.</span><span class="sxs-lookup"><span data-stu-id="5ae48-104">You could write code to iterate through all of the descendants, but it is easier to use the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5ae48-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5ae48-105">Example</span></span>  
 <span data-ttu-id="5ae48-106">O exemplo a seguir mostra como localizar os descendentes com base no nome do elemento.</span><span class="sxs-lookup"><span data-stu-id="5ae48-106">The following example shows how to find descendants based on the element name.</span></span>  
  
```csharp  
XElement root = XElement.Parse(@"<root>  
  <para>  
    <r>  
      <t>Some text </t>  
    </r>  
    <n>  
      <r>  
        <t>that is broken up into </t>  
      </r>  
    </n>  
    <n>  
      <r>  
        <t>multiple segments.</t>  
      </r>  
    </n>  
  </para>  
</root>");  
IEnumerable<string> textSegs =  
    from seg in root.Descendants("t")  
    select (string)seg;  
  
string str = textSegs.Aggregate(new StringBuilder(),  
    (sb, i) => sb.Append(i),  
    sp => sp.ToString()  
);  
  
Console.WriteLine(str);  
```  
  
 <span data-ttu-id="5ae48-107">Esse código gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="5ae48-107">This code produces the following output:</span></span>  
  
```  
Some text that is broken up into multiple segments.  
```  
  
## <a name="example"></a><span data-ttu-id="5ae48-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5ae48-108">Example</span></span>  
 <span data-ttu-id="5ae48-109">O exemplo a seguir mostra a mesma consulta para XML que está em um namespace.</span><span class="sxs-lookup"><span data-stu-id="5ae48-109">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="5ae48-110">Para obter mais informações, consulte [Trabalhando com namespaces XML (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="5ae48-110">For more information, see [Working with XML Namespaces (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
```csharp  
XElement root = XElement.Parse(@"<root xmlns='http://www.adatum.com'>  
  <para>  
    <r>  
      <t>Some text </t>  
    </r>  
    <n>  
      <r>  
        <t>that is broken up into </t>  
      </r>  
    </n>  
    <n>  
      <r>  
        <t>multiple segments.</t>  
      </r>  
    </n>  
  </para>  
</root>");  
XNamespace ad = "http://www.adatum.com";  
IEnumerable<string> textSegs =  
    from seg in root.Descendants(ad + "t")  
    select (string)seg;  
  
string str = textSegs.Aggregate(new StringBuilder(),  
    (sb, i) => sb.Append(i),  
    sp => sp.ToString()  
);  
  
Console.WriteLine(str);  
```  
  
 <span data-ttu-id="5ae48-111">Esse código gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="5ae48-111">This code produces the following output:</span></span>  
  
```  
Some text that is broken up into multiple segments.  
```  
  
## <a name="see-also"></a><span data-ttu-id="5ae48-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5ae48-112">See Also</span></span>  
 <xref:System.Xml.Linq.XContainer.Descendants%2A>  
 [<span data-ttu-id="5ae48-113">Consultas básicas (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="5ae48-113">Basic Queries (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
