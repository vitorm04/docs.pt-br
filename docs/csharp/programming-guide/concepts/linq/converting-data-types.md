---
title: Convertendo Tipos de Dados (C#)
ms.date: 07/20/2015
ms.assetid: 46e5682f-77a1-4302-8f93-a2b53c408808
ms.openlocfilehash: 328c790a1a360907c91f69b3b6330b0b25eb414b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75347199"
---
# <a name="converting-data-types-c"></a><span data-ttu-id="7145e-102">Convertendo Tipos de Dados (C#)</span><span class="sxs-lookup"><span data-stu-id="7145e-102">Converting Data Types (C#)</span></span>
<span data-ttu-id="7145e-103">Os métodos de conversão alteram o tipo dos objetos de entrada.</span><span class="sxs-lookup"><span data-stu-id="7145e-103">Conversion methods change the type of input objects.</span></span>

 <span data-ttu-id="7145e-104">As operações de conversão em consultas LINQ são úteis em diversas aplicações.</span><span class="sxs-lookup"><span data-stu-id="7145e-104">Conversion operations in LINQ queries are useful in a variety of applications.</span></span> <span data-ttu-id="7145e-105">A seguir estão alguns exemplos:</span><span class="sxs-lookup"><span data-stu-id="7145e-105">Following are some examples:</span></span>

- <span data-ttu-id="7145e-106">O método <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> pode ser usado para ocultar a implementação personalizada de um tipo de um operador de consulta padrão.</span><span class="sxs-lookup"><span data-stu-id="7145e-106">The <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> method can be used to hide a type's custom implementation of a standard query operator.</span></span>

- <span data-ttu-id="7145e-107">O método <xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> pode ser usado para habilitar coleções sem parâmetros para consulta LINQ.</span><span class="sxs-lookup"><span data-stu-id="7145e-107">The <xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> method can be used to enable non-parameterized collections for LINQ querying.</span></span>

- <span data-ttu-id="7145e-108">Os métodos <xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> e <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> podem ser usados para forçar a execução de consulta imediata em vez de adiá-la até que a consulta seja enumerada.</span><span class="sxs-lookup"><span data-stu-id="7145e-108">The <xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>, and <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> methods can be used to force immediate query execution instead of deferring it until the query is enumerated.</span></span>

## <a name="methods"></a><span data-ttu-id="7145e-109">Métodos</span><span class="sxs-lookup"><span data-stu-id="7145e-109">Methods</span></span>
 <span data-ttu-id="7145e-110">A tabela a seguir lista os métodos de operador de consulta padrão que realizam conversões de tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="7145e-110">The following table lists the standard query operator methods that perform data-type conversions.</span></span>

 <span data-ttu-id="7145e-111">Os métodos de conversão nesta tabela cujos nomes começam com "As" alteram o tipo estático da coleção de origem, mas não a enumeram.</span><span class="sxs-lookup"><span data-stu-id="7145e-111">The conversion methods in this table whose names start with "As" change the static type of the source collection but do not enumerate it.</span></span> <span data-ttu-id="7145e-112">Os métodos cujos nomes começam com "To" enumeram a coleção de origem e colocam os itens na coleção de tipo correspondente.</span><span class="sxs-lookup"><span data-stu-id="7145e-112">The methods whose names start with "To" enumerate the source collection and put the items into the corresponding collection type.</span></span>

|<span data-ttu-id="7145e-113">Nome do método</span><span class="sxs-lookup"><span data-stu-id="7145e-113">Method Name</span></span>|<span data-ttu-id="7145e-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="7145e-114">Description</span></span>|<span data-ttu-id="7145e-115">Sintaxe de expressão de consulta C#</span><span class="sxs-lookup"><span data-stu-id="7145e-115">C# Query Expression Syntax</span></span>|<span data-ttu-id="7145e-116">Mais informações</span><span class="sxs-lookup"><span data-stu-id="7145e-116">More Information</span></span>|
|-----------------|-----------------|---------------------------------|----------------------|
|<span data-ttu-id="7145e-117">AsEnumerable</span><span class="sxs-lookup"><span data-stu-id="7145e-117">AsEnumerable</span></span>|<span data-ttu-id="7145e-118">Retorna a entrada digitada como <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="7145e-118">Returns the input typed as <xref:System.Collections.Generic.IEnumerable%601>.</span></span>|<span data-ttu-id="7145e-119">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="7145e-119">Not applicable.</span></span>|<xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType>|
|<span data-ttu-id="7145e-120">AsQueryable</span><span class="sxs-lookup"><span data-stu-id="7145e-120">AsQueryable</span></span>|<span data-ttu-id="7145e-121">Converte um <xref:System.Collections.IEnumerable> (genérico) em um <xref:System.Linq.IQueryable> (genérico).</span><span class="sxs-lookup"><span data-stu-id="7145e-121">Converts a (generic) <xref:System.Collections.IEnumerable> to a (generic) <xref:System.Linq.IQueryable>.</span></span>|<span data-ttu-id="7145e-122">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="7145e-122">Not applicable.</span></span>|<xref:System.Linq.Queryable.AsQueryable%2A?displayProperty=nameWithType>|
|<span data-ttu-id="7145e-123">Conversão</span><span class="sxs-lookup"><span data-stu-id="7145e-123">Cast</span></span>|<span data-ttu-id="7145e-124">Converte os elementos de uma coleção em um tipo especificado.</span><span class="sxs-lookup"><span data-stu-id="7145e-124">Casts the elements of a collection to a specified type.</span></span>|<span data-ttu-id="7145e-125">Use uma variável de intervalo de tipo explícito.</span><span class="sxs-lookup"><span data-stu-id="7145e-125">Use an explicitly typed range variable.</span></span> <span data-ttu-id="7145e-126">Por exemplo: </span><span class="sxs-lookup"><span data-stu-id="7145e-126">For example:</span></span><br /><br /> `from string str in words`|<xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Cast%2A?displayProperty=nameWithType>|
|<span data-ttu-id="7145e-127">OfType</span><span class="sxs-lookup"><span data-stu-id="7145e-127">OfType</span></span>|<span data-ttu-id="7145e-128">Filtra valores, dependendo da capacidade de serem convertidos em um tipo especificado.</span><span class="sxs-lookup"><span data-stu-id="7145e-128">Filters values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="7145e-129">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="7145e-129">Not applicable.</span></span>|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|
|<span data-ttu-id="7145e-130">ToArray</span><span class="sxs-lookup"><span data-stu-id="7145e-130">ToArray</span></span>|<span data-ttu-id="7145e-131">Converte uma coleção em uma matriz.</span><span class="sxs-lookup"><span data-stu-id="7145e-131">Converts a collection to an array.</span></span> <span data-ttu-id="7145e-132">Esse método força a execução de consulta.</span><span class="sxs-lookup"><span data-stu-id="7145e-132">This method forces query execution.</span></span>|<span data-ttu-id="7145e-133">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="7145e-133">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>|
|<span data-ttu-id="7145e-134">ToDictionary</span><span class="sxs-lookup"><span data-stu-id="7145e-134">ToDictionary</span></span>|<span data-ttu-id="7145e-135">Coloca os elementos em um <xref:System.Collections.Generic.Dictionary%602> com base em uma função de seletor de chave.</span><span class="sxs-lookup"><span data-stu-id="7145e-135">Puts elements into a <xref:System.Collections.Generic.Dictionary%602> based on a key selector function.</span></span> <span data-ttu-id="7145e-136">Esse método força a execução de consulta.</span><span class="sxs-lookup"><span data-stu-id="7145e-136">This method forces query execution.</span></span>|<span data-ttu-id="7145e-137">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="7145e-137">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>|
|<span data-ttu-id="7145e-138">ToList</span><span class="sxs-lookup"><span data-stu-id="7145e-138">ToList</span></span>|<span data-ttu-id="7145e-139">Converte uma coleção em um <xref:System.Collections.Generic.List%601>.</span><span class="sxs-lookup"><span data-stu-id="7145e-139">Converts a collection to a <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="7145e-140">Esse método força a execução de consulta.</span><span class="sxs-lookup"><span data-stu-id="7145e-140">This method forces query execution.</span></span>|<span data-ttu-id="7145e-141">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="7145e-141">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>|
|<span data-ttu-id="7145e-142">ToLookup</span><span class="sxs-lookup"><span data-stu-id="7145e-142">ToLookup</span></span>|<span data-ttu-id="7145e-143">Coloca os elementos em um <xref:System.Linq.Lookup%602> (um dicionário one-to-many) com base em uma função de seletor de chave.</span><span class="sxs-lookup"><span data-stu-id="7145e-143">Puts elements into a <xref:System.Linq.Lookup%602> (a one-to-many dictionary) based on a key selector function.</span></span> <span data-ttu-id="7145e-144">Esse método força a execução de consulta.</span><span class="sxs-lookup"><span data-stu-id="7145e-144">This method forces query execution.</span></span>|<span data-ttu-id="7145e-145">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="7145e-145">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|

## <a name="query-expression-syntax-example"></a><span data-ttu-id="7145e-146">Exemplo de sintaxe de expressão de consulta</span><span class="sxs-lookup"><span data-stu-id="7145e-146">Query Expression Syntax Example</span></span>

<span data-ttu-id="7145e-147">O exemplo de código a seguir usa uma variável de intervalo explicitamente digitada para lançar um tipo a um subtipo antes de acessar um membro disponível apenas no subtipo.</span><span class="sxs-lookup"><span data-stu-id="7145e-147">The following code example uses an explicitly typed range variable to cast a type to a subtype before accessing a member that is available only on the subtype.</span></span>

```csharp
class Plant
{
    public string Name { get; set; }
}

class CarnivorousPlant : Plant
{
    public string TrapType { get; set; }
}

static void Cast()
{
    Plant[] plants = new Plant[] {
        new CarnivorousPlant { Name = "Venus Fly Trap", TrapType = "Snap Trap" },
        new CarnivorousPlant { Name = "Pitcher Plant", TrapType = "Pitfall Trap" },
        new CarnivorousPlant { Name = "Sundew", TrapType = "Flypaper Trap" },
        new CarnivorousPlant { Name = "Waterwheel Plant", TrapType = "Snap Trap" }
    };

    var query = from CarnivorousPlant cPlant in plants
                where cPlant.TrapType == "Snap Trap"
                select cPlant;

    foreach (Plant plant in query)
        Console.WriteLine(plant.Name);

    /* This code produces the following output:

        Venus Fly Trap
        Waterwheel Plant
    */
}
```

## <a name="see-also"></a><span data-ttu-id="7145e-148">Confira também</span><span class="sxs-lookup"><span data-stu-id="7145e-148">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="7145e-149">Visão geral de operadores de consulta padrão (C#)</span><span class="sxs-lookup"><span data-stu-id="7145e-149">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="7145e-150">de cláusula</span><span class="sxs-lookup"><span data-stu-id="7145e-150">from clause</span></span>](../../../language-reference/keywords/from-clause.md)
- [<span data-ttu-id="7145e-151">Expressões de Consulta LINQ</span><span class="sxs-lookup"><span data-stu-id="7145e-151">LINQ Query Expressions</span></span>](../../../linq/index.md)
- [<span data-ttu-id="7145e-152">Como consultar uma arraylist com LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="7145e-152">How to query an ArrayList with LINQ (C#)</span></span>](./how-to-query-an-arraylist-with-linq.md)
