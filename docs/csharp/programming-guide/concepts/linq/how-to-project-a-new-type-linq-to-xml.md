---
title: Como projetar um novo tipo (LINQ to XML) (C#)
description: Saiba como criar consultas em LINQ to XML em C# que retornam IEnumerable <T> de tipos, além de XElement, String ou int, que são descritas em outros exemplos.
ms.date: 07/20/2015
ms.assetid: 48145cf9-1e0b-4e73-bbfd-28fc04800dc4
ms.openlocfilehash: 013ea852a64b77c04ac583b4d9b71e8006cd4976
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104647"
---
# <a name="how-to-project-a-new-type-linq-to-xml-c"></a><span data-ttu-id="d90f3-103">Como projetar um novo tipo (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="d90f3-103">How to project a new type (LINQ to XML) (C#)</span></span>

<span data-ttu-id="d90f3-104">Outros exemplos nesta seção mostraram consultas que os resultados de retorno como <xref:System.Collections.Generic.IEnumerable%601> de <xref:System.Xml.Linq.XElement>, <xref:System.Collections.Generic.IEnumerable%601> de `string`, e <xref:System.Collections.Generic.IEnumerable%601> de `int`.</span><span class="sxs-lookup"><span data-stu-id="d90f3-104">Other examples in this section have shown queries that return results as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, <xref:System.Collections.Generic.IEnumerable%601> of `string`, and <xref:System.Collections.Generic.IEnumerable%601> of `int`.</span></span> <span data-ttu-id="d90f3-105">Esses são tipos comuns de resultado, mas não são adequados para cada cenário.</span><span class="sxs-lookup"><span data-stu-id="d90f3-105">These are common result types, but they are not appropriate for every scenario.</span></span> <span data-ttu-id="d90f3-106">Em muitos casos você desejará suas consultas para retornar <xref:System.Collections.Generic.IEnumerable%601> de qualquer outro tipo.</span><span class="sxs-lookup"><span data-stu-id="d90f3-106">In many cases you will want your queries to return an <xref:System.Collections.Generic.IEnumerable%601> of some other type.</span></span>

## <a name="example"></a><span data-ttu-id="d90f3-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d90f3-107">Example</span></span>

<span data-ttu-id="d90f3-108">Este exemplo mostra como instanciar objetos na cláusula `select` .</span><span class="sxs-lookup"><span data-stu-id="d90f3-108">This example shows how to instantiate objects in the `select` clause.</span></span> <span data-ttu-id="d90f3-109">O código define primeiro uma nova classe com um construtor, e altera a declaração de `select` de modo que a expressão é uma nova instância da nova classe.</span><span class="sxs-lookup"><span data-stu-id="d90f3-109">The code first defines a new class with a constructor, and then modifies the `select` statement so that the expression is a new instance of the new class.</span></span>

<span data-ttu-id="d90f3-110">Este exemplo usa o seguinte documento XML: [Arquivo XML de exemplo: ordem de compra típica (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span><span class="sxs-lookup"><span data-stu-id="d90f3-110">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span>

```csharp
class NameQty
{
    public string name;
    public int qty;
    public NameQty(string n, int q)
    {
        name = n;
        qty = q;
    }
};

class Program {
    public static void Main()
    {
        XElement po = XElement.Load("PurchaseOrder.xml");
  
        IEnumerable<NameQty> nqList =
            from n in po.Descendants("Item")
            select new NameQty(
                    (string)n.Element("ProductName"),
                    (int)n.Element("Quantity")
                );
  
        foreach (NameQty n in nqList)
            Console.WriteLine(n.name + ":" + n.qty);
    }
}
```

<span data-ttu-id="d90f3-111">Este exemplo usa o <xref:System.Xml.Linq.XContainer.Element%2A> método que foi introduzido no tópico [como recuperar um único elemento filho (LINQ to XML) (C#)](how-to-retrieve-a-single-child-element-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="d90f3-111">This example uses the <xref:System.Xml.Linq.XContainer.Element%2A> method that was introduced in the topic [How to retrieve a single child element (LINQ to XML) (C#)](how-to-retrieve-a-single-child-element-linq-to-xml.md).</span></span> <span data-ttu-id="d90f3-112">Também usa conversões para recuperar os valores dos elementos que são retornados pelo método de <xref:System.Xml.Linq.XContainer.Element%2A> .</span><span class="sxs-lookup"><span data-stu-id="d90f3-112">It also uses casts to retrieve the values of the elements that are returned by the <xref:System.Xml.Linq.XContainer.Element%2A> method.</span></span>  

<span data-ttu-id="d90f3-113">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="d90f3-113">This example produces the following output:</span></span>

```output
Lawnmower:1
Baby Monitor:2
```
