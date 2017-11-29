---
title: Unir usando chaves compostas
description: Como unir usando chaves compostas.
keywords: .NET, .NET Core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: da70b54d-3213-45eb-8437-fbe75cbcf935
ms.openlocfilehash: c285e768d64d1da7e428e29fc67838e87575500c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="join-by-using-composite-keys"></a><span data-ttu-id="4549c-104">Unir usando chaves compostas</span><span class="sxs-lookup"><span data-stu-id="4549c-104">Join by using composite keys</span></span>

<span data-ttu-id="4549c-105">Este exemplo mostra como realizar operações de junção nas quais você deseja usar mais de uma chave para definir uma correspondência.</span><span class="sxs-lookup"><span data-stu-id="4549c-105">This example shows how to perform join operations in which you want to use more than one key to define a match.</span></span> <span data-ttu-id="4549c-106">Isso é realizado por meio de uma chave composta.</span><span class="sxs-lookup"><span data-stu-id="4549c-106">This is accomplished by using a composite key.</span></span> <span data-ttu-id="4549c-107">Uma chave composta é criada como um tipo anônimo ou como um tipo nomeado com os valores que você deseja comparar.</span><span class="sxs-lookup"><span data-stu-id="4549c-107">You create a composite key as an anonymous type or named typed with the values that you want to compare.</span></span> <span data-ttu-id="4549c-108">Se a variável de consulta será passada entre limites de método, use um tipo nomeado que substitui <xref:System.Object.Equals%2A> e <xref:System.Object.GetHashCode%2A> para a chave.</span><span class="sxs-lookup"><span data-stu-id="4549c-108">If the query variable will be passed across method boundaries, use a named type that overrides <xref:System.Object.Equals%2A> and <xref:System.Object.GetHashCode%2A> for the key.</span></span> <span data-ttu-id="4549c-109">Os nomes das propriedades e a ordem em que elas ocorrem, devem ser idênticas em cada chave.</span><span class="sxs-lookup"><span data-stu-id="4549c-109">The names of the properties, and the order in which they occur, must be identical in each key.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4549c-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4549c-110">Example</span></span>  
 <span data-ttu-id="4549c-111">O exemplo a seguir demonstra como usar uma chave composta para unir dados de três tabelas:</span><span class="sxs-lookup"><span data-stu-id="4549c-111">The following example demonstrates how to use a composite key to join data from three tables:</span></span>  
  
```csharp  
var query = from o in db.Orders  
    from p in db.Products  
    join d in db.OrderDetails   
        on new {o.OrderID, p.ProductID} equals new {d.OrderID,        d.ProductID} into details  
        from d in details  
        select new {o.OrderID, p.ProductID, d.UnitPrice};  
```  
  
 <span data-ttu-id="4549c-112">A inferência de tipos em chaves compostas depende dos nomes das propriedades nas chaves e da ordem em que elas ocorrem.</span><span class="sxs-lookup"><span data-stu-id="4549c-112">Type inference on composite keys depends on the names of the properties in the keys, and the order in which they occur.</span></span> <span data-ttu-id="4549c-113">Se as propriedades nas sequências de origem não têm os mesmos nomes, você deve atribuir novos nomes nas chaves.</span><span class="sxs-lookup"><span data-stu-id="4549c-113">If the properties in the source sequences do not have the same names, you must assign new names in the keys.</span></span> <span data-ttu-id="4549c-114">Por exemplo, se a tabela `Orders` e a tabela `OrderDetails` usaram nomes diferentes para suas colunas, você poderia criar chaves compostas ao atribuir nomes idênticos nos tipos anônimos:</span><span class="sxs-lookup"><span data-stu-id="4549c-114">For example, if the `Orders` table and `OrderDetails` table each used different names for their columns, you could create composite keys by assigning identical names in the anonymous types:</span></span>  
  
```csharp  
join...on new {Name = o.CustomerName, ID = o.CustID} equals   
    new {Name = d.CustName, ID = d.CustID }  
```  
  
 <span data-ttu-id="4549c-115">As chaves compostas também podem ser usadas em uma cláusula `group`.</span><span class="sxs-lookup"><span data-stu-id="4549c-115">Composite keys can be also used in a `group` clause.</span></span>  

## <a name="see-also"></a><span data-ttu-id="4549c-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4549c-116">See also</span></span>  
 [<span data-ttu-id="4549c-117">Expressões de consulta LINQ</span><span class="sxs-lookup"><span data-stu-id="4549c-117">LINQ query expressions</span></span>](index.md)  
 [<span data-ttu-id="4549c-118">Cláusula join</span><span class="sxs-lookup"><span data-stu-id="4549c-118">join clause</span></span>](../language-reference/keywords/join-clause.md)  
 [<span data-ttu-id="4549c-119">Cláusula group</span><span class="sxs-lookup"><span data-stu-id="4549c-119">group clause</span></span>](../language-reference/keywords/group-clause.md)
