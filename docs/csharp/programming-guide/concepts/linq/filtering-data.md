---
title: Filtrando dados (C#)
ms.date: 07/20/2015
ms.assetid: fbaece0d-0f23-47f7-89c5-f3ea8db692b6
ms.openlocfilehash: 74399244990f8ff2deaa1d10576ea94a57c16bee
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346985"
---
# <a name="filtering-data-c"></a><span data-ttu-id="da914-102">Filtrando dados (C#)</span><span class="sxs-lookup"><span data-stu-id="da914-102">Filtering Data (C#)</span></span>
<span data-ttu-id="da914-103">A filtragem é a operação de restringir o conjunto de resultados de forma que ele contenha apenas os elementos correspondentes a uma condição especificada.</span><span class="sxs-lookup"><span data-stu-id="da914-103">Filtering refers to the operation of restricting the result set to contain only those elements that satisfy a specified condition.</span></span> <span data-ttu-id="da914-104">Ela também é conhecida como seleção.</span><span class="sxs-lookup"><span data-stu-id="da914-104">It is also known as selection.</span></span>  
  
 <span data-ttu-id="da914-105">A ilustração a seguir mostra os resultados da filtragem de uma sequência de caracteres.</span><span class="sxs-lookup"><span data-stu-id="da914-105">The following illustration shows the results of filtering a sequence of characters.</span></span> <span data-ttu-id="da914-106">O predicado para a operação de filtragem especifica que o caractere deve ser "A".</span><span class="sxs-lookup"><span data-stu-id="da914-106">The predicate for the filtering operation specifies that the character must be 'A'.</span></span>  
  
 ![Diagrama que mostra uma operação de filtragem do LINQ](./media/filtering-data/linq-filter-operation.png)  
  
 <span data-ttu-id="da914-108">Os métodos de operador de consulta padrão que realizam a seleção estão listados na seção a seguir.</span><span class="sxs-lookup"><span data-stu-id="da914-108">The standard query operator methods that perform selection are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="da914-109">{1&gt;Métodos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="da914-109">Methods</span></span>  
  
|<span data-ttu-id="da914-110">Nome do método</span><span class="sxs-lookup"><span data-stu-id="da914-110">Method Name</span></span>|<span data-ttu-id="da914-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="da914-111">Description</span></span>|<span data-ttu-id="da914-112">Sintaxe de expressão de consulta C#</span><span class="sxs-lookup"><span data-stu-id="da914-112">C# Query Expression Syntax</span></span>|<span data-ttu-id="da914-113">Mais Informações</span><span class="sxs-lookup"><span data-stu-id="da914-113">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="da914-114">OfType</span><span class="sxs-lookup"><span data-stu-id="da914-114">OfType</span></span>|<span data-ttu-id="da914-115">Seleciona valores, dependendo da capacidade de serem convertidos em um tipo especificado.</span><span class="sxs-lookup"><span data-stu-id="da914-115">Selects values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="da914-116">{1&gt;Não aplicável.&lt;1}</span><span class="sxs-lookup"><span data-stu-id="da914-116">Not applicable.</span></span>|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="da914-117">Onde</span><span class="sxs-lookup"><span data-stu-id="da914-117">Where</span></span>|<span data-ttu-id="da914-118">Seleciona valores com base em uma função de predicado.</span><span class="sxs-lookup"><span data-stu-id="da914-118">Selects values that are based on a predicate function.</span></span>|`where`|<xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Where%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="da914-119">Exemplo de sintaxe de expressão de consulta</span><span class="sxs-lookup"><span data-stu-id="da914-119">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="da914-120">O exemplo a seguir usa a cláusula `where` para filtrar em uma matriz as cadeias de caracteres com um tamanho específico.</span><span class="sxs-lookup"><span data-stu-id="da914-120">The following example uses the `where` clause to filter from an array those strings that have a specific length.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="da914-121">Veja também</span><span class="sxs-lookup"><span data-stu-id="da914-121">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="da914-122">Visão geral de operadores de consulta padrão (C#)</span><span class="sxs-lookup"><span data-stu-id="da914-122">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="da914-123">Cláusula where</span><span class="sxs-lookup"><span data-stu-id="da914-123">where clause</span></span>](../../../language-reference/keywords/where-clause.md)
- [<span data-ttu-id="da914-124">Especificar filtros predicados dinamicamente em runtime</span><span class="sxs-lookup"><span data-stu-id="da914-124">Dynamically specify predicate filters at runtime</span></span>](../../../linq/dynamically-specify-predicate-filters-at-runtime.md)
- [<span data-ttu-id="da914-125">Como consultar metadados de um assembly com reflexão (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="da914-125">How to query an assembly's metadata with Reflection (LINQ) (C#)</span></span>](./how-to-query-an-assembly-s-metadata-with-reflection-linq.md)
- [<span data-ttu-id="da914-126">Como consultar arquivos com um atributo ou nome especificado (C#)</span><span class="sxs-lookup"><span data-stu-id="da914-126">How to query for files with a specified attribute or name (C#)</span></span>](./how-to-query-for-files-with-a-specified-attribute-or-name.md)
- [<span data-ttu-id="da914-127">Como classificar ou filtrar dados de texto por qualquer palavra ou campo (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="da914-127">How to sort or filter text data by any word or field (LINQ) (C#)</span></span>](./how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
