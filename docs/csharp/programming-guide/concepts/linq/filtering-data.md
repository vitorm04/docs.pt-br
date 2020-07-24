---
title: Filtrando dados (C#)
description: A filtragem, também conhecida como seleção, restringe os resultados com base em uma condição. Saiba mais sobre os métodos do operador de consulta padrão no LINQ em C# que executam a filtragem.
ms.date: 07/20/2015
ms.assetid: fbaece0d-0f23-47f7-89c5-f3ea8db692b6
ms.openlocfilehash: f9f6d691da73b566e5135f6692c87ba3a8978005
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103931"
---
# <a name="filtering-data-c"></a><span data-ttu-id="e0b05-104">Filtrando dados (C#)</span><span class="sxs-lookup"><span data-stu-id="e0b05-104">Filtering Data (C#)</span></span>
<span data-ttu-id="e0b05-105">A filtragem é a operação de restringir o conjunto de resultados de forma que ele contenha apenas os elementos correspondentes a uma condição especificada.</span><span class="sxs-lookup"><span data-stu-id="e0b05-105">Filtering refers to the operation of restricting the result set to contain only those elements that satisfy a specified condition.</span></span> <span data-ttu-id="e0b05-106">Ela também é conhecida como seleção.</span><span class="sxs-lookup"><span data-stu-id="e0b05-106">It is also known as selection.</span></span>  
  
 <span data-ttu-id="e0b05-107">A ilustração a seguir mostra os resultados da filtragem de uma sequência de caracteres.</span><span class="sxs-lookup"><span data-stu-id="e0b05-107">The following illustration shows the results of filtering a sequence of characters.</span></span> <span data-ttu-id="e0b05-108">O predicado para a operação de filtragem especifica que o caractere deve ser "A".</span><span class="sxs-lookup"><span data-stu-id="e0b05-108">The predicate for the filtering operation specifies that the character must be 'A'.</span></span>  
  
 ![Diagrama que mostra uma operação de filtragem do LINQ](./media/filtering-data/linq-filter-operation.png)  
  
 <span data-ttu-id="e0b05-110">Os métodos de operador de consulta padrão que realizam a seleção estão listados na seção a seguir.</span><span class="sxs-lookup"><span data-stu-id="e0b05-110">The standard query operator methods that perform selection are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e0b05-111">Métodos</span><span class="sxs-lookup"><span data-stu-id="e0b05-111">Methods</span></span>  
  
|<span data-ttu-id="e0b05-112">Nome do método</span><span class="sxs-lookup"><span data-stu-id="e0b05-112">Method Name</span></span>|<span data-ttu-id="e0b05-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="e0b05-113">Description</span></span>|<span data-ttu-id="e0b05-114">Sintaxe de expressão de consulta C#</span><span class="sxs-lookup"><span data-stu-id="e0b05-114">C# Query Expression Syntax</span></span>|<span data-ttu-id="e0b05-115">Mais informações</span><span class="sxs-lookup"><span data-stu-id="e0b05-115">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="e0b05-116">OfType</span><span class="sxs-lookup"><span data-stu-id="e0b05-116">OfType</span></span>|<span data-ttu-id="e0b05-117">Seleciona valores, dependendo da capacidade de serem convertidos em um tipo especificado.</span><span class="sxs-lookup"><span data-stu-id="e0b05-117">Selects values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="e0b05-118">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="e0b05-118">Not applicable.</span></span>|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="e0b05-119">Where</span><span class="sxs-lookup"><span data-stu-id="e0b05-119">Where</span></span>|<span data-ttu-id="e0b05-120">Seleciona valores com base em uma função de predicado.</span><span class="sxs-lookup"><span data-stu-id="e0b05-120">Selects values that are based on a predicate function.</span></span>|`where`|<xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Where%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="e0b05-121">Exemplo de sintaxe de expressão de consulta</span><span class="sxs-lookup"><span data-stu-id="e0b05-121">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="e0b05-122">O exemplo a seguir usa a cláusula `where` para filtrar em uma matriz as cadeias de caracteres com um tamanho específico.</span><span class="sxs-lookup"><span data-stu-id="e0b05-122">The following example uses the `where` clause to filter from an array those strings that have a specific length.</span></span>  
  
```csharp  
string[] words = { "the", "quick", "brown", "fox", "jumps" };  
  
IEnumerable<string> query = from word in words  
                            where word.Length == 3  
                            select word;  
  
foreach (string str in query)  
    Console.WriteLine(str);  
  
/* This code produces the following output:  
  
    the  
    fox  
*/  
```  
  
## <a name="see-also"></a><span data-ttu-id="e0b05-123">Confira também</span><span class="sxs-lookup"><span data-stu-id="e0b05-123">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="e0b05-124">Visão geral de operadores de consulta padrão (C#)</span><span class="sxs-lookup"><span data-stu-id="e0b05-124">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="e0b05-125">cláusula WHERE</span><span class="sxs-lookup"><span data-stu-id="e0b05-125">where clause</span></span>](../../../language-reference/keywords/where-clause.md)
- [<span data-ttu-id="e0b05-126">Especificar filtros predicados dinamicamente em runtime</span><span class="sxs-lookup"><span data-stu-id="e0b05-126">Dynamically specify predicate filters at runtime</span></span>](../../../linq/dynamically-specify-predicate-filters-at-runtime.md)
- [<span data-ttu-id="e0b05-127">Como consultar metadados de um assembly com reflexão (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="e0b05-127">How to query an assembly's metadata with Reflection (LINQ) (C#)</span></span>](./how-to-query-an-assembly-s-metadata-with-reflection-linq.md)
- [<span data-ttu-id="e0b05-128">Como consultar arquivos com um atributo ou nome especificado (C#)</span><span class="sxs-lookup"><span data-stu-id="e0b05-128">How to query for files with a specified attribute or name (C#)</span></span>](./how-to-query-for-files-with-a-specified-attribute-or-name.md)
- [<span data-ttu-id="e0b05-129">Como classificar ou filtrar dados de texto por qualquer palavra ou campo (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="e0b05-129">How to sort or filter text data by any word or field (LINQ) (C#)</span></span>](./how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
