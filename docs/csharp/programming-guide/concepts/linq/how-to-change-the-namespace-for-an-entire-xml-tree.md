---
title: 'Como: Alterar o namespace de uma árvore XML inteira (C#)'
ms.date: 07/20/2015
ms.assetid: 1584ff3b-c77d-4241-ab62-80adfb7bfc1b
ms.openlocfilehash: 020d072cfb58c90720317734199d241c6892511f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54539916"
---
# <a name="how-to-change-the-namespace-for-an-entire-xml-tree-c"></a><span data-ttu-id="3dc38-102">Como: Alterar o namespace de uma árvore XML inteira (C#)</span><span class="sxs-lookup"><span data-stu-id="3dc38-102">How to: Change the Namespace for an Entire XML Tree (C#)</span></span>
<span data-ttu-id="3dc38-103">Às vezes você tem que alterar programaticamente ao namespace para um elemento ou atributo.</span><span class="sxs-lookup"><span data-stu-id="3dc38-103">You sometimes have to programmatically change the namespace for an element or an attribute.</span></span> <span data-ttu-id="3dc38-104">LINQ to XML faz isso fácil.</span><span class="sxs-lookup"><span data-stu-id="3dc38-104">LINQ to XML makes this easy.</span></span> <span data-ttu-id="3dc38-105">A propriedade de <xref:System.Xml.Linq.XElement.Name%2A?displayProperty=nameWithType> pode ser definida.</span><span class="sxs-lookup"><span data-stu-id="3dc38-105">The <xref:System.Xml.Linq.XElement.Name%2A?displayProperty=nameWithType> property can be set.</span></span> <span data-ttu-id="3dc38-106">A propriedade de <xref:System.Xml.Linq.XAttribute.Name%2A?displayProperty=nameWithType> não pode ser definida, mas você pode facilmente copiar os atributos em <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>, remover os atributos existentes, e então adiciona novos atributos que estão no novo namespace desejada.</span><span class="sxs-lookup"><span data-stu-id="3dc38-106">The <xref:System.Xml.Linq.XAttribute.Name%2A?displayProperty=nameWithType> property cannot be set, but you can easily copy the attributes into a <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>, remove the existing attributes, and then add new attributes that are in the new desired namespace.</span></span>  
  
 <span data-ttu-id="3dc38-107">Para obter mais informações, consulte [Trabalhando com namespaces XML (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="3dc38-107">For more information, see [Working with XML Namespaces (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3dc38-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3dc38-108">Example</span></span>  
 <span data-ttu-id="3dc38-109">O código a seguir cria duas árvores XML em qualquer namespace.</span><span class="sxs-lookup"><span data-stu-id="3dc38-109">The following code creates two XML trees in no namespace.</span></span> <span data-ttu-id="3dc38-110">Altera o namespace de cada uma das árvores, e as combina em uma única árvore.</span><span class="sxs-lookup"><span data-stu-id="3dc38-110">It then changes the namespace of each of the trees, and combines them into a single tree.</span></span>  
  
```csharp  
XElement tree1 = new XElement("Data",  
    new XElement("Child", "content",  
        new XAttribute("MyAttr", "content")  
    )  
);  
XElement tree2 = new XElement("Data",  
    new XElement("Child", "content",  
        new XAttribute("MyAttr", "content")  
    )  
);  
XNamespace aw = "http://www.adventure-works.com";  
XNamespace ad = "http://www.adatum.com";  
// change the namespace of every element and attribute in the first tree  
foreach (XElement el in tree1.DescendantsAndSelf())  
{  
    el.Name = aw.GetName(el.Name.LocalName);  
    List<XAttribute> atList = el.Attributes().ToList();  
    el.Attributes().Remove();  
    foreach (XAttribute at in atList)  
        el.Add(new XAttribute(aw.GetName(at.Name.LocalName), at.Value));  
}  
// change the namespace of every element and attribute in the second tree  
foreach (XElement el in tree2.DescendantsAndSelf())  
{  
    el.Name = ad.GetName(el.Name.LocalName);  
    List<XAttribute> atList = el.Attributes().ToList();  
    el.Attributes().Remove();  
    foreach (XAttribute at in atList)  
        el.Add(new XAttribute(ad.GetName(at.Name.LocalName), at.Value));  
}  
// add attribute namespaces so that the tree will be serialized with  
// the aw and ad namespace prefixes  
tree1.Add(  
    new XAttribute(XNamespace.Xmlns + "aw", "http://www.adventure-works.com")  
);  
tree2.Add(  
    new XAttribute(XNamespace.Xmlns + "ad", "http://www.adatum.com")  
);  
// create a new composite tree  
XElement root = new XElement("Root",  
    tree1,  
    tree2  
);  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="3dc38-111">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="3dc38-111">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <aw:Data xmlns:aw="http://www.adventure-works.com">  
    <aw:Child aw:MyAttr="content">content</aw:Child>  
  </aw:Data>  
  <ad:Data xmlns:ad="http://www.adatum.com">  
    <ad:Child ad:MyAttr="content">content</ad:Child>  
  </ad:Data>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3dc38-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3dc38-112">See also</span></span>

- [<span data-ttu-id="3dc38-113">Modificando árvores XML (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="3dc38-113">Modifying XML Trees (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
