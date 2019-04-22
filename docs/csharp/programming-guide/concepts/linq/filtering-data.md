---
title: Filtrando dados (C#)
ms.date: 07/20/2015
ms.assetid: fbaece0d-0f23-47f7-89c5-f3ea8db692b6
ms.openlocfilehash: 61d80674fd858063e77749342a33d714e3a57c6e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58826061"
---
# <a name="filtering-data-c"></a><span data-ttu-id="09bac-102">Filtrando dados (C#)</span><span class="sxs-lookup"><span data-stu-id="09bac-102">Filtering Data (C#)</span></span>
<span data-ttu-id="09bac-103">A filtragem é a operação de restringir o conjunto de resultados de forma que ele contenha apenas os elementos correspondentes a uma condição especificada.</span><span class="sxs-lookup"><span data-stu-id="09bac-103">Filtering refers to the operation of restricting the result set to contain only those elements that satisfy a specified condition.</span></span> <span data-ttu-id="09bac-104">Ela também é conhecida como seleção.</span><span class="sxs-lookup"><span data-stu-id="09bac-104">It is also known as selection.</span></span>  
  
 <span data-ttu-id="09bac-105">A ilustração a seguir mostra os resultados da filtragem de uma sequência de caracteres.</span><span class="sxs-lookup"><span data-stu-id="09bac-105">The following illustration shows the results of filtering a sequence of characters.</span></span> <span data-ttu-id="09bac-106">O predicado para a operação de filtragem especifica que o caractere deve ser "A".</span><span class="sxs-lookup"><span data-stu-id="09bac-106">The predicate for the filtering operation specifies that the character must be 'A'.</span></span>  
  
 ![Diagrama que mostra uma operação de filtragem do LINQ](./media/filtering-data/linq-filter-operation.png)  
  
 <span data-ttu-id="09bac-108">Os métodos de operador de consulta padrão que realizam a seleção estão listados na seção a seguir.</span><span class="sxs-lookup"><span data-stu-id="09bac-108">The standard query operator methods that perform selection are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="09bac-109">Métodos</span><span class="sxs-lookup"><span data-stu-id="09bac-109">Methods</span></span>  
  
|<span data-ttu-id="09bac-110">Nome do método</span><span class="sxs-lookup"><span data-stu-id="09bac-110">Method Name</span></span>|<span data-ttu-id="09bac-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="09bac-111">Description</span></span>|<span data-ttu-id="09bac-112">Sintaxe de expressão de consulta C#</span><span class="sxs-lookup"><span data-stu-id="09bac-112">C# Query Expression Syntax</span></span>|<span data-ttu-id="09bac-113">Mais informações</span><span class="sxs-lookup"><span data-stu-id="09bac-113">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="09bac-114">OfType</span><span class="sxs-lookup"><span data-stu-id="09bac-114">OfType</span></span>|<span data-ttu-id="09bac-115">Seleciona valores, dependendo da capacidade de serem convertidos em um tipo especificado.</span><span class="sxs-lookup"><span data-stu-id="09bac-115">Selects values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="09bac-116">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="09bac-116">Not applicable.</span></span>|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="09bac-117">Where</span><span class="sxs-lookup"><span data-stu-id="09bac-117">Where</span></span>|<span data-ttu-id="09bac-118">Seleciona valores com base em uma função de predicado.</span><span class="sxs-lookup"><span data-stu-id="09bac-118">Selects values that are based on a predicate function.</span></span>|`where`|<xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Where%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="09bac-119">Exemplo de sintaxe de expressão de consulta</span><span class="sxs-lookup"><span data-stu-id="09bac-119">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="09bac-120">O exemplo a seguir usa a cláusula `where` para filtrar em uma matriz as cadeias de caracteres com um tamanho específico.</span><span class="sxs-lookup"><span data-stu-id="09bac-120">The following example uses the `where` clause to filter from an array those strings that have a specific length.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="09bac-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="09bac-121">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="09bac-122">Visão geral de operadores de consulta padrão (C#)</span><span class="sxs-lookup"><span data-stu-id="09bac-122">Standard Query Operators Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="09bac-123">Cláusula where</span><span class="sxs-lookup"><span data-stu-id="09bac-123">where clause</span></span>](../../../../csharp/language-reference/keywords/where-clause.md)
- [<span data-ttu-id="09bac-124">Como: Especificar filtros de predicado dinamicamente em tempo de execução</span><span class="sxs-lookup"><span data-stu-id="09bac-124">How to: Dynamically Specify Predicate Filters at Runtime</span></span>](../../../../csharp/programming-guide/linq-query-expressions/how-to-dynamically-specify-predicate-filters-at-runtime.md)
- [<span data-ttu-id="09bac-125">Como: Consultar metadados de um assembly com a reflexão (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="09bac-125">How to: Query An Assembly's Metadata with Reflection (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-query-an-assembly-s-metadata-with-reflection-linq.md)
- [<span data-ttu-id="09bac-126">Como: Consultar arquivos com um atributo ou um nome especificado (C#)</span><span class="sxs-lookup"><span data-stu-id="09bac-126">How to: Query for Files with a Specified Attribute or Name (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-files-with-a-specified-attribute-or-name.md)
- [<span data-ttu-id="09bac-127">Como: Classificar ou filtrar dados de texto por qualquer palavra ou campo (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="09bac-127">How to: Sort or Filter Text Data by Any Word or Field (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
