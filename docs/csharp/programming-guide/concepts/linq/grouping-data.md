---
title: Agrupando dados (C#)
description: O agrupamento coloca dados em grupos de elementos que compartilham um atributo. Saiba mais sobre os métodos do operador de consulta padrão no LINQ em C# que agrupam elementos de dados.
ms.date: 07/20/2015
ms.assetid: e414e9e4-343a-4e6e-858f-4a30c5e64492
ms.openlocfilehash: 5e1bca1d360b0f44a081cf2770118a0551629b5b
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103685"
---
# <a name="grouping-data-c"></a><span data-ttu-id="b0c99-104">Agrupando dados (C#)</span><span class="sxs-lookup"><span data-stu-id="b0c99-104">Grouping Data (C#)</span></span>
<span data-ttu-id="b0c99-105">O agrupamento refere-se à operação de colocação de dados em grupos, de modo que os elementos em cada grupo compartilhem um atributo comum.</span><span class="sxs-lookup"><span data-stu-id="b0c99-105">Grouping refers to the operation of putting data into groups so that the elements in each group share a common attribute.</span></span>  
  
 <span data-ttu-id="b0c99-106">A ilustração a seguir mostra os resultados do agrupamento de uma sequência de caracteres.</span><span class="sxs-lookup"><span data-stu-id="b0c99-106">The following illustration shows the results of grouping a sequence of characters.</span></span> <span data-ttu-id="b0c99-107">A chave para cada grupo é o caractere.</span><span class="sxs-lookup"><span data-stu-id="b0c99-107">The key for each group is the character.</span></span>  
  
 ![Diagrama que mostra uma operação de Agrupamento do LINQ.](./media/grouping-data/linq-group-operation.png)  
  
 <span data-ttu-id="b0c99-109">Os métodos do operador de consulta padrão que agrupam elementos de dados estão listados na seção a seguir.</span><span class="sxs-lookup"><span data-stu-id="b0c99-109">The standard query operator methods that group data elements are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b0c99-110">Métodos</span><span class="sxs-lookup"><span data-stu-id="b0c99-110">Methods</span></span>  
  
|<span data-ttu-id="b0c99-111">Nome do método</span><span class="sxs-lookup"><span data-stu-id="b0c99-111">Method Name</span></span>|<span data-ttu-id="b0c99-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="b0c99-112">Description</span></span>|<span data-ttu-id="b0c99-113">Sintaxe de expressão de consulta C#</span><span class="sxs-lookup"><span data-stu-id="b0c99-113">C# Query Expression Syntax</span></span>|<span data-ttu-id="b0c99-114">Mais informações</span><span class="sxs-lookup"><span data-stu-id="b0c99-114">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="b0c99-115">GroupBy</span><span class="sxs-lookup"><span data-stu-id="b0c99-115">GroupBy</span></span>|<span data-ttu-id="b0c99-116">Agrupa elementos que compartilham um atributo comum.</span><span class="sxs-lookup"><span data-stu-id="b0c99-116">Groups elements that share a common attribute.</span></span> <span data-ttu-id="b0c99-117">Cada grupo é representado por um objeto <xref:System.Linq.IGrouping%602>.</span><span class="sxs-lookup"><span data-stu-id="b0c99-117">Each group is represented by an <xref:System.Linq.IGrouping%602> object.</span></span>|`group … by`<br /><br /> <span data-ttu-id="b0c99-118">- ou -</span><span class="sxs-lookup"><span data-stu-id="b0c99-118">-or-</span></span><br /><br /> `group … by … into …`|<xref:System.Linq.Enumerable.GroupBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.GroupBy%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="b0c99-119">ToLookup</span><span class="sxs-lookup"><span data-stu-id="b0c99-119">ToLookup</span></span>|<span data-ttu-id="b0c99-120">Insere os elementos em um <xref:System.Linq.Lookup%602> (um dicionário one-to-many) com base em uma função de seletor de chave.</span><span class="sxs-lookup"><span data-stu-id="b0c99-120">Inserts elements into a <xref:System.Linq.Lookup%602> (a one-to-many dictionary) based on a key selector function.</span></span>|<span data-ttu-id="b0c99-121">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="b0c99-121">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="b0c99-122">Exemplo de sintaxe de expressão de consulta</span><span class="sxs-lookup"><span data-stu-id="b0c99-122">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="b0c99-123">O seguinte exemplo de código usa a cláusula `group by` para agrupar inteiros em uma lista de acordo com se eles são pares ou ímpares.</span><span class="sxs-lookup"><span data-stu-id="b0c99-123">The following code example uses the `group by` clause to group integers in a list according to whether they are even or odd.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b0c99-124">Confira também</span><span class="sxs-lookup"><span data-stu-id="b0c99-124">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="b0c99-125">Visão geral de operadores de consulta padrão (C#)</span><span class="sxs-lookup"><span data-stu-id="b0c99-125">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="b0c99-126">Cláusula group</span><span class="sxs-lookup"><span data-stu-id="b0c99-126">group clause</span></span>](../../../language-reference/keywords/group-clause.md)
- [<span data-ttu-id="b0c99-127">Criar um grupo aninhado</span><span class="sxs-lookup"><span data-stu-id="b0c99-127">Create a nested group</span></span>](../../../linq/create-a-nested-group.md)
- [<span data-ttu-id="b0c99-128">Como agrupar arquivos por extensão (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="b0c99-128">How to group files by extension (LINQ) (C#)</span></span>](./how-to-group-files-by-extension-linq.md)
- [<span data-ttu-id="b0c99-129">Agrupar resultados de consultas</span><span class="sxs-lookup"><span data-stu-id="b0c99-129">Group query results</span></span>](../../../linq/group-query-results.md)
- [<span data-ttu-id="b0c99-130">Executar uma subconsulta em uma operação de agrupamento</span><span class="sxs-lookup"><span data-stu-id="b0c99-130">Perform a subquery on a grouping operation</span></span>](../../../linq/perform-a-subquery-on-a-grouping-operation.md)
- [<span data-ttu-id="b0c99-131">Como dividir um arquivo em vários arquivos usando grupos (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="b0c99-131">How to split a file into many files by using groups (LINQ) (C#)</span></span>](./how-to-split-a-file-into-many-files-by-using-groups-linq.md)
