---
title: Como localizar descendentes com um nome de elemento específico (C#)
description: Saiba como localizar todos os descendentes com um nome específico usando o eixo descendentes. Consulte exemplos de código e recursos adicionais.
ms.date: 07/20/2015
ms.assetid: f684da20-bee9-47f5-9607-7e3fd7e67470
ms.openlocfilehash: 96ebf2d10a9ed5e07aab2870142f9869903ad442
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303238"
---
# <a name="how-to-find-descendants-with-a-specific-element-name-c"></a><span data-ttu-id="1c7ff-104">Como localizar descendentes com um nome de elemento específico (C#)</span><span class="sxs-lookup"><span data-stu-id="1c7ff-104">How to find descendants with a specific element name (C#)</span></span>
<span data-ttu-id="1c7ff-105">Às vezes, você deseja localizar todos os descendentes com um nome específico.</span><span class="sxs-lookup"><span data-stu-id="1c7ff-105">Sometimes you want to find all descendants with a particular name.</span></span> <span data-ttu-id="1c7ff-106">Você poderia escrever um código para iterar por todos os descendentes, mas é mais fácil usar o eixo <xref:System.Xml.Linq.XContainer.Descendants%2A>.</span><span class="sxs-lookup"><span data-stu-id="1c7ff-106">You could write code to iterate through all of the descendants, but it is easier to use the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1c7ff-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1c7ff-107">Example</span></span>  
 <span data-ttu-id="1c7ff-108">O exemplo a seguir mostra como localizar os descendentes com base no nome do elemento.</span><span class="sxs-lookup"><span data-stu-id="1c7ff-108">The following example shows how to find descendants based on the element name.</span></span>  
  
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
  
 <span data-ttu-id="1c7ff-109">Este código produz a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="1c7ff-109">This code produces the following output:</span></span>  
  
```output  
Some text that is broken up into multiple segments.  
```  
  
## <a name="example"></a><span data-ttu-id="1c7ff-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1c7ff-110">Example</span></span>  
 <span data-ttu-id="1c7ff-111">O exemplo a seguir mostra a mesma consulta para XML que está em um namespace.</span><span class="sxs-lookup"><span data-stu-id="1c7ff-111">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="1c7ff-112">Para obter mais informações, consulte [Visão geral de namespaces (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="1c7ff-112">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="1c7ff-113">Este código produz a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="1c7ff-113">This code produces the following output:</span></span>  
  
```output  
Some text that is broken up into multiple segments.  
```  
  
## <a name="see-also"></a><span data-ttu-id="1c7ff-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="1c7ff-114">See also</span></span>

- <xref:System.Xml.Linq.XContainer.Descendants%2A>
