---
title: Agrupando dados (C#)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: e414e9e4-343a-4e6e-858f-4a30c5e64492
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4aef8d10eaffb384fe919ffa6a1e742cb837f540
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="grouping-data-c"></a><span data-ttu-id="83315-102">Agrupando dados (C#)</span><span class="sxs-lookup"><span data-stu-id="83315-102">Grouping Data (C#)</span></span>
<span data-ttu-id="83315-103">O agrupamento refere-se à operação de colocação de dados em grupos, de modo que os elementos em cada grupo compartilhem um atributo comum.</span><span class="sxs-lookup"><span data-stu-id="83315-103">Grouping refers to the operation of putting data into groups so that the elements in each group share a common attribute.</span></span>  
  
 <span data-ttu-id="83315-104">A ilustração a seguir mostra os resultados do agrupamento de uma sequência de caracteres.</span><span class="sxs-lookup"><span data-stu-id="83315-104">The following illustration shows the results of grouping a sequence of characters.</span></span> <span data-ttu-id="83315-105">A chave para cada grupo é o caractere.</span><span class="sxs-lookup"><span data-stu-id="83315-105">The key for each group is the character.</span></span>  
  
 <span data-ttu-id="83315-106">![Operações de agrupamento LINQ](../../../../csharp/programming-guide/concepts/linq/media/linq_group.png "LINQ_Group")</span><span class="sxs-lookup"><span data-stu-id="83315-106">![LINQ Grouping Operations](../../../../csharp/programming-guide/concepts/linq/media/linq_group.png "LINQ_Group")</span></span>  
  
 <span data-ttu-id="83315-107">Os métodos do operador de consulta padrão que agrupam elementos de dados estão listados na seção a seguir.</span><span class="sxs-lookup"><span data-stu-id="83315-107">The standard query operator methods that group data elements are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="83315-108">Métodos</span><span class="sxs-lookup"><span data-stu-id="83315-108">Methods</span></span>  
  
|<span data-ttu-id="83315-109">Nome do método</span><span class="sxs-lookup"><span data-stu-id="83315-109">Method Name</span></span>|<span data-ttu-id="83315-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="83315-110">Description</span></span>|<span data-ttu-id="83315-111">Sintaxe de expressão de consulta C#</span><span class="sxs-lookup"><span data-stu-id="83315-111">C# Query Expression Syntax</span></span>|<span data-ttu-id="83315-112">Mais informações</span><span class="sxs-lookup"><span data-stu-id="83315-112">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="83315-113">GroupBy</span><span class="sxs-lookup"><span data-stu-id="83315-113">GroupBy</span></span>|<span data-ttu-id="83315-114">Agrupa elementos que compartilham um atributo comum.</span><span class="sxs-lookup"><span data-stu-id="83315-114">Groups elements that share a common attribute.</span></span> <span data-ttu-id="83315-115">Cada grupo é representado por um objeto <xref:System.Linq.IGrouping%602>.</span><span class="sxs-lookup"><span data-stu-id="83315-115">Each group is represented by an <xref:System.Linq.IGrouping%602> object.</span></span>|`group … by`<br /><br /> <span data-ttu-id="83315-116">-ou-</span><span class="sxs-lookup"><span data-stu-id="83315-116">-or-</span></span><br /><br /> `group … by … into …`|<xref:System.Linq.Enumerable.GroupBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.GroupBy%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="83315-117">ToLookup</span><span class="sxs-lookup"><span data-stu-id="83315-117">ToLookup</span></span>|<span data-ttu-id="83315-118">Insere os elementos em um <xref:System.Linq.Lookup%602> (um dicionário one-to-many) com base em uma função de seletor de chave.</span><span class="sxs-lookup"><span data-stu-id="83315-118">Inserts elements into a <xref:System.Linq.Lookup%602> (a one-to-many dictionary) based on a key selector function.</span></span>|<span data-ttu-id="83315-119">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="83315-119">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="83315-120">Exemplo de sintaxe de expressão de consulta</span><span class="sxs-lookup"><span data-stu-id="83315-120">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="83315-121">O seguinte exemplo de código usa a cláusula `group by` para agrupar inteiros em uma lista de acordo com se eles são pares ou ímpares.</span><span class="sxs-lookup"><span data-stu-id="83315-121">The following code example uses the `group by` clause to group integers in a list according to whether they are even or odd.</span></span>  
  
```csharp  
List<int> numbers = new List<int>() { 35, 44, 200, 84, 3987, 4, 199, 329, 446, 208 };  
  
IEnumerable<IGrouping<int, int>> query = from number in numbers  
                                         group number by number % 2;  
  
foreach (var group in query)  
{  
    Console.WriteLine(group.Key == 0 ? "\nEven numbers:" : "\nOdd numbers:");  
    foreach (int i in group)  
        Console.WriteLine(i);  
}  
  
/* This code produces the following output:  
  
    Odd numbers:  
    35  
    3987  
    199  
    329  
  
    Even numbers:  
    44  
    200  
    84  
    4  
    446  
    208  
*/  
```  
  
## <a name="see-also"></a><span data-ttu-id="83315-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="83315-122">See Also</span></span>  
 <xref:System.Linq>  
 [<span data-ttu-id="83315-123">Visão geral de operadores de consulta padrão (C#)</span><span class="sxs-lookup"><span data-stu-id="83315-123">Standard Query Operators Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [<span data-ttu-id="83315-124">Cláusula group</span><span class="sxs-lookup"><span data-stu-id="83315-124">group clause</span></span>](../../../../csharp/language-reference/keywords/group-clause.md)  
 [<span data-ttu-id="83315-125">Como criar um grupo aninhado</span><span class="sxs-lookup"><span data-stu-id="83315-125">How to: Create a Nested Group</span></span>](../../../../csharp/programming-guide/linq-query-expressions/how-to-create-a-nested-group.md)  
 [<span data-ttu-id="83315-126">Como agrupar arquivos por extensão (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="83315-126">How to: Group Files by Extension (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-group-files-by-extension-linq.md)  
 [<span data-ttu-id="83315-127">Como agrupar resultados de consultas</span><span class="sxs-lookup"><span data-stu-id="83315-127">How to: Group Query Results</span></span>](../../../../csharp/programming-guide/linq-query-expressions/how-to-group-query-results.md)  
 [<span data-ttu-id="83315-128">Como executar uma subconsulta em uma operação de agrupamento</span><span class="sxs-lookup"><span data-stu-id="83315-128">How to: Perform a Subquery on a Grouping Operation</span></span>](../../../../csharp/programming-guide/linq-query-expressions/how-to-perform-a-subquery-on-a-grouping-operation.md)  
 [<span data-ttu-id="83315-129">Como dividir um arquivo em vários arquivos usando grupos (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="83315-129">How to: Split a File Into Many Files by Using Groups (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-split-a-file-into-many-files-by-using-groups-linq.md)
