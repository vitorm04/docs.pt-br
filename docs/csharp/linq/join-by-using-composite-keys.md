---
title: Unir usando chaves compostas (LINQ em C#)
description: Saiba como unir usando chaves compostas em LINQ.
ms.date: 12/1/2016
ms.assetid: da70b54d-3213-45eb-8437-fbe75cbcf935
ms.openlocfilehash: ae37d03f996f0b0cc184a86663f16d62e6c29c69
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/16/2018
ms.locfileid: "45609510"
---
# <a name="join-by-using-composite-keys"></a><span data-ttu-id="fe613-103">Unir usando chaves compostas</span><span class="sxs-lookup"><span data-stu-id="fe613-103">Join by using composite keys</span></span>

<span data-ttu-id="fe613-104">Este exemplo mostra como realizar operações de junção nas quais você deseja usar mais de uma chave para definir uma correspondência.</span><span class="sxs-lookup"><span data-stu-id="fe613-104">This example shows how to perform join operations in which you want to use more than one key to define a match.</span></span> <span data-ttu-id="fe613-105">Isso é realizado por meio de uma chave composta.</span><span class="sxs-lookup"><span data-stu-id="fe613-105">This is accomplished by using a composite key.</span></span> <span data-ttu-id="fe613-106">Uma chave composta é criada como um tipo anônimo ou como um tipo nomeado com os valores que você deseja comparar.</span><span class="sxs-lookup"><span data-stu-id="fe613-106">You create a composite key as an anonymous type or named typed with the values that you want to compare.</span></span> <span data-ttu-id="fe613-107">Se a variável de consulta será passada entre limites de método, use um tipo nomeado que substitui <xref:System.Object.Equals%2A> e <xref:System.Object.GetHashCode%2A> para a chave.</span><span class="sxs-lookup"><span data-stu-id="fe613-107">If the query variable will be passed across method boundaries, use a named type that overrides <xref:System.Object.Equals%2A> and <xref:System.Object.GetHashCode%2A> for the key.</span></span> <span data-ttu-id="fe613-108">Os nomes das propriedades e a ordem em que elas ocorrem, devem ser idênticas em cada chave.</span><span class="sxs-lookup"><span data-stu-id="fe613-108">The names of the properties, and the order in which they occur, must be identical in each key.</span></span>

## <a name="example"></a><span data-ttu-id="fe613-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="fe613-109">Example</span></span>

<span data-ttu-id="fe613-110">O exemplo a seguir demonstra como usar uma chave composta para unir dados de três tabelas:</span><span class="sxs-lookup"><span data-stu-id="fe613-110">The following example demonstrates how to use a composite key to join data from three tables:</span></span>

```csharp
var query = from o in db.Orders
    from p in db.Products
    join d in db.OrderDetails
        on new {o.OrderID, p.ProductID} equals new {d.OrderID, d.ProductID} into details
        from d in details
        select new {o.OrderID, p.ProductID, d.UnitPrice};
```

<span data-ttu-id="fe613-111">A inferência de tipos em chaves compostas depende dos nomes das propriedades nas chaves e da ordem em que elas ocorrem.</span><span class="sxs-lookup"><span data-stu-id="fe613-111">Type inference on composite keys depends on the names of the properties in the keys, and the order in which they occur.</span></span> <span data-ttu-id="fe613-112">Quando as propriedades nas sequências de origem não têm os mesmos nomes, você precisa atribuir novos nomes nas chaves.</span><span class="sxs-lookup"><span data-stu-id="fe613-112">If the properties in the source sequences don't have the same names, you must assign new names in the keys.</span></span> <span data-ttu-id="fe613-113">Por exemplo, se a tabela `Orders` e a tabela `OrderDetails` usaram nomes diferentes para suas colunas, você poderia criar chaves compostas ao atribuir nomes idênticos nos tipos anônimos:</span><span class="sxs-lookup"><span data-stu-id="fe613-113">For example, if the `Orders` table and `OrderDetails` table each used different names for their columns, you could create composite keys by assigning identical names in the anonymous types:</span></span>

```csharp
join...on new {Name = o.CustomerName, ID = o.CustID} equals
    new {Name = d.CustName, ID = d.CustID }
```

<span data-ttu-id="fe613-114">As chaves compostas também podem ser usadas em uma cláusula `group`.</span><span class="sxs-lookup"><span data-stu-id="fe613-114">Composite keys can be also used in a `group` clause.</span></span>

## <a name="see-also"></a><span data-ttu-id="fe613-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fe613-115">See also</span></span>

- [<span data-ttu-id="fe613-116">LINQ (Consulta Integrada à Linguagem)</span><span class="sxs-lookup"><span data-stu-id="fe613-116">Language Integrated Query (LINQ)</span></span>](index.md)  
- [<span data-ttu-id="fe613-117">Cláusula join</span><span class="sxs-lookup"><span data-stu-id="fe613-117">join clause</span></span>](../language-reference/keywords/join-clause.md)  
- [<span data-ttu-id="fe613-118">Cláusula group</span><span class="sxs-lookup"><span data-stu-id="fe613-118">group clause</span></span>](../language-reference/keywords/group-clause.md)  