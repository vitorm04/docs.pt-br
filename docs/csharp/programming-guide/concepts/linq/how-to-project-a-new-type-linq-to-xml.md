---
title: Como projetar um novo tipo (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: 48145cf9-1e0b-4e73-bbfd-28fc04800dc4
ms.openlocfilehash: 3a54677fa0fa2845dd635f89ddb7ed1c5c279e03
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345716"
---
# <a name="how-to-project-a-new-type-linq-to-xml-c"></a><span data-ttu-id="9a108-102">Como projetar um novo tipo (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="9a108-102">How to project a new type (LINQ to XML) (C#)</span></span>

<span data-ttu-id="9a108-103">Outros exemplos nesta seção mostraram consultas que os resultados de retorno como <xref:System.Collections.Generic.IEnumerable%601> de <xref:System.Xml.Linq.XElement>, <xref:System.Collections.Generic.IEnumerable%601> de `string`, e <xref:System.Collections.Generic.IEnumerable%601> de `int`.</span><span class="sxs-lookup"><span data-stu-id="9a108-103">Other examples in this section have shown queries that return results as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, <xref:System.Collections.Generic.IEnumerable%601> of `string`, and <xref:System.Collections.Generic.IEnumerable%601> of `int`.</span></span> <span data-ttu-id="9a108-104">Esses são tipos comuns de resultado, mas não são adequados para cada cenário.</span><span class="sxs-lookup"><span data-stu-id="9a108-104">These are common result types, but they are not appropriate for every scenario.</span></span> <span data-ttu-id="9a108-105">Em muitos casos você desejará suas consultas para retornar <xref:System.Collections.Generic.IEnumerable%601> de qualquer outro tipo.</span><span class="sxs-lookup"><span data-stu-id="9a108-105">In many cases you will want your queries to return an <xref:System.Collections.Generic.IEnumerable%601> of some other type.</span></span>

## <a name="example"></a><span data-ttu-id="9a108-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9a108-106">Example</span></span>

<span data-ttu-id="9a108-107">Este exemplo mostra como instanciar objetos na cláusula `select` .</span><span class="sxs-lookup"><span data-stu-id="9a108-107">This example shows how to instantiate objects in the `select` clause.</span></span> <span data-ttu-id="9a108-108">O código define primeiro uma nova classe com um construtor, e altera a declaração de `select` de modo que a expressão é uma nova instância da nova classe.</span><span class="sxs-lookup"><span data-stu-id="9a108-108">The code first defines a new class with a constructor, and then modifies the `select` statement so that the expression is a new instance of the new class.</span></span>

<span data-ttu-id="9a108-109">Este exemplo usa o seguinte documento XML: [Arquivo XML de exemplo: ordem de compra típica (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span><span class="sxs-lookup"><span data-stu-id="9a108-109">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span>

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

<span data-ttu-id="9a108-110">Este exemplo usa o método <xref:System.Xml.Linq.XContainer.Element%2A> que foi introduzido no tópico [como recuperar um único elemento filho (LINQ to XML) (C#)](how-to-retrieve-a-single-child-element-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="9a108-110">This example uses the <xref:System.Xml.Linq.XContainer.Element%2A> method that was introduced in the topic [How to retrieve a single child element (LINQ to XML) (C#)](how-to-retrieve-a-single-child-element-linq-to-xml.md).</span></span> <span data-ttu-id="9a108-111">Também usa conversões para recuperar os valores dos elementos que são retornados pelo método de <xref:System.Xml.Linq.XContainer.Element%2A> .</span><span class="sxs-lookup"><span data-stu-id="9a108-111">It also uses casts to retrieve the values of the elements that are returned by the <xref:System.Xml.Linq.XContainer.Element%2A> method.</span></span>  

<span data-ttu-id="9a108-112">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="9a108-112">This example produces the following output:</span></span>

```output
Lawnmower:1
Baby Monitor:2
```
