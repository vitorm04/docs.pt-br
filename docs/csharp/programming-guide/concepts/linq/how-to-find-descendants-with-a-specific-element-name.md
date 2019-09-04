---
title: 'Como: Localizar descendentes com um nome de elemento específico (C#)'
ms.date: 07/20/2015
ms.assetid: f684da20-bee9-47f5-9607-7e3fd7e67470
ms.openlocfilehash: 8c859c555109a6f68a6b4290c536b10114620f3d
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253689"
---
# <a name="how-to-find-descendants-with-a-specific-element-name-c"></a><span data-ttu-id="069bd-102">Como: Localizar descendentes com um nome de elemento específico (C#)</span><span class="sxs-lookup"><span data-stu-id="069bd-102">How to: Find Descendants with a Specific Element Name (C#)</span></span>
<span data-ttu-id="069bd-103">Às vezes, você deseja localizar todos os descendentes com um nome específico.</span><span class="sxs-lookup"><span data-stu-id="069bd-103">Sometimes you want to find all descendants with a particular name.</span></span> <span data-ttu-id="069bd-104">Você poderia escrever um código para iterar por todos os descendentes, mas é mais fácil usar o eixo <xref:System.Xml.Linq.XContainer.Descendants%2A>.</span><span class="sxs-lookup"><span data-stu-id="069bd-104">You could write code to iterate through all of the descendants, but it is easier to use the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis.</span></span>  
  
## <a name="example"></a><span data-ttu-id="069bd-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="069bd-105">Example</span></span>  
 <span data-ttu-id="069bd-106">O exemplo a seguir mostra como localizar os descendentes com base no nome do elemento.</span><span class="sxs-lookup"><span data-stu-id="069bd-106">The following example shows how to find descendants based on the element name.</span></span>  
  
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
  
 <span data-ttu-id="069bd-107">Esse código gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="069bd-107">This code produces the following output:</span></span>  
  
```output  
Some text that is broken up into multiple segments.  
```  
  
## <a name="example"></a><span data-ttu-id="069bd-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="069bd-108">Example</span></span>  
 <span data-ttu-id="069bd-109">O exemplo a seguir mostra a mesma consulta para XML que está em um namespace.</span><span class="sxs-lookup"><span data-stu-id="069bd-109">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="069bd-110">Para obter mais informações, consulte [Visão geral de namespaces (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="069bd-110">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="069bd-111">Esse código gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="069bd-111">This code produces the following output:</span></span>  
  
```output  
Some text that is broken up into multiple segments.  
```  
  
## <a name="see-also"></a><span data-ttu-id="069bd-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="069bd-112">See also</span></span>

- <xref:System.Xml.Linq.XContainer.Descendants%2A>
