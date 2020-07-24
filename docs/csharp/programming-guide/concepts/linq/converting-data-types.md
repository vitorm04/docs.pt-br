---
title: Convertendo Tipos de Dados (C#)
description: Os métodos de conversão alteram o tipo dos objetos de entrada. Consulte operações de conversão em consultas LINQ em C#, como Enumerable. AsEnumerable e Enumerable. OfType.
ms.date: 07/20/2015
ms.assetid: 46e5682f-77a1-4302-8f93-a2b53c408808
ms.openlocfilehash: 3291690f9aaee945ca7feb04ebbc676db2612894
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105482"
---
# <a name="converting-data-types-c"></a><span data-ttu-id="3fb04-104">Convertendo Tipos de Dados (C#)</span><span class="sxs-lookup"><span data-stu-id="3fb04-104">Converting Data Types (C#)</span></span>
<span data-ttu-id="3fb04-105">Os métodos de conversão alteram o tipo dos objetos de entrada.</span><span class="sxs-lookup"><span data-stu-id="3fb04-105">Conversion methods change the type of input objects.</span></span>

 <span data-ttu-id="3fb04-106">As operações de conversão em consultas LINQ são úteis em diversas aplicações.</span><span class="sxs-lookup"><span data-stu-id="3fb04-106">Conversion operations in LINQ queries are useful in a variety of applications.</span></span> <span data-ttu-id="3fb04-107">A seguir estão alguns exemplos:</span><span class="sxs-lookup"><span data-stu-id="3fb04-107">Following are some examples:</span></span>

- <span data-ttu-id="3fb04-108">O método <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> pode ser usado para ocultar a implementação personalizada de um tipo de um operador de consulta padrão.</span><span class="sxs-lookup"><span data-stu-id="3fb04-108">The <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> method can be used to hide a type's custom implementation of a standard query operator.</span></span>

- <span data-ttu-id="3fb04-109">O método <xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> pode ser usado para habilitar coleções sem parâmetros para consulta LINQ.</span><span class="sxs-lookup"><span data-stu-id="3fb04-109">The <xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> method can be used to enable non-parameterized collections for LINQ querying.</span></span>

- <span data-ttu-id="3fb04-110">Os métodos <xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> e <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> podem ser usados para forçar a execução de consulta imediata em vez de adiá-la até que a consulta seja enumerada.</span><span class="sxs-lookup"><span data-stu-id="3fb04-110">The <xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>, and <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> methods can be used to force immediate query execution instead of deferring it until the query is enumerated.</span></span>

## <a name="methods"></a><span data-ttu-id="3fb04-111">Métodos</span><span class="sxs-lookup"><span data-stu-id="3fb04-111">Methods</span></span>
 <span data-ttu-id="3fb04-112">A tabela a seguir lista os métodos de operador de consulta padrão que realizam conversões de tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="3fb04-112">The following table lists the standard query operator methods that perform data-type conversions.</span></span>

 <span data-ttu-id="3fb04-113">Os métodos de conversão nesta tabela cujos nomes começam com "As" alteram o tipo estático da coleção de origem, mas não a enumeram.</span><span class="sxs-lookup"><span data-stu-id="3fb04-113">The conversion methods in this table whose names start with "As" change the static type of the source collection but do not enumerate it.</span></span> <span data-ttu-id="3fb04-114">Os métodos cujos nomes começam com "To" enumeram a coleção de origem e colocam os itens na coleção de tipo correspondente.</span><span class="sxs-lookup"><span data-stu-id="3fb04-114">The methods whose names start with "To" enumerate the source collection and put the items into the corresponding collection type.</span></span>

|<span data-ttu-id="3fb04-115">Nome do método</span><span class="sxs-lookup"><span data-stu-id="3fb04-115">Method Name</span></span>|<span data-ttu-id="3fb04-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="3fb04-116">Description</span></span>|<span data-ttu-id="3fb04-117">Sintaxe de expressão de consulta C#</span><span class="sxs-lookup"><span data-stu-id="3fb04-117">C# Query Expression Syntax</span></span>|<span data-ttu-id="3fb04-118">Mais informações</span><span class="sxs-lookup"><span data-stu-id="3fb04-118">More Information</span></span>|
|-----------------|-----------------|---------------------------------|----------------------|
|<span data-ttu-id="3fb04-119">AsEnumerable</span><span class="sxs-lookup"><span data-stu-id="3fb04-119">AsEnumerable</span></span>|<span data-ttu-id="3fb04-120">Retorna a entrada digitada como <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="3fb04-120">Returns the input typed as <xref:System.Collections.Generic.IEnumerable%601>.</span></span>|<span data-ttu-id="3fb04-121">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="3fb04-121">Not applicable.</span></span>|<xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType>|
|<span data-ttu-id="3fb04-122">AsQueryable</span><span class="sxs-lookup"><span data-stu-id="3fb04-122">AsQueryable</span></span>|<span data-ttu-id="3fb04-123">Converte um <xref:System.Collections.IEnumerable> (genérico) em um <xref:System.Linq.IQueryable> (genérico).</span><span class="sxs-lookup"><span data-stu-id="3fb04-123">Converts a (generic) <xref:System.Collections.IEnumerable> to a (generic) <xref:System.Linq.IQueryable>.</span></span>|<span data-ttu-id="3fb04-124">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="3fb04-124">Not applicable.</span></span>|<xref:System.Linq.Queryable.AsQueryable%2A?displayProperty=nameWithType>|
|<span data-ttu-id="3fb04-125">Conversão</span><span class="sxs-lookup"><span data-stu-id="3fb04-125">Cast</span></span>|<span data-ttu-id="3fb04-126">Converte os elementos de uma coleção em um tipo especificado.</span><span class="sxs-lookup"><span data-stu-id="3fb04-126">Casts the elements of a collection to a specified type.</span></span>|<span data-ttu-id="3fb04-127">Use uma variável de intervalo de tipo explícito.</span><span class="sxs-lookup"><span data-stu-id="3fb04-127">Use an explicitly typed range variable.</span></span> <span data-ttu-id="3fb04-128">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="3fb04-128">For example:</span></span><br /><br /> `from string str in words`|<xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Cast%2A?displayProperty=nameWithType>|
|<span data-ttu-id="3fb04-129">OfType</span><span class="sxs-lookup"><span data-stu-id="3fb04-129">OfType</span></span>|<span data-ttu-id="3fb04-130">Filtra valores, dependendo da capacidade de serem convertidos em um tipo especificado.</span><span class="sxs-lookup"><span data-stu-id="3fb04-130">Filters values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="3fb04-131">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="3fb04-131">Not applicable.</span></span>|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|
|<span data-ttu-id="3fb04-132">ToArray</span><span class="sxs-lookup"><span data-stu-id="3fb04-132">ToArray</span></span>|<span data-ttu-id="3fb04-133">Converte uma coleção em uma matriz.</span><span class="sxs-lookup"><span data-stu-id="3fb04-133">Converts a collection to an array.</span></span> <span data-ttu-id="3fb04-134">Esse método força a execução de consulta.</span><span class="sxs-lookup"><span data-stu-id="3fb04-134">This method forces query execution.</span></span>|<span data-ttu-id="3fb04-135">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="3fb04-135">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>|
|<span data-ttu-id="3fb04-136">ToDictionary</span><span class="sxs-lookup"><span data-stu-id="3fb04-136">ToDictionary</span></span>|<span data-ttu-id="3fb04-137">Coloca os elementos em um <xref:System.Collections.Generic.Dictionary%602> com base em uma função de seletor de chave.</span><span class="sxs-lookup"><span data-stu-id="3fb04-137">Puts elements into a <xref:System.Collections.Generic.Dictionary%602> based on a key selector function.</span></span> <span data-ttu-id="3fb04-138">Esse método força a execução de consulta.</span><span class="sxs-lookup"><span data-stu-id="3fb04-138">This method forces query execution.</span></span>|<span data-ttu-id="3fb04-139">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="3fb04-139">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>|
|<span data-ttu-id="3fb04-140">ToList</span><span class="sxs-lookup"><span data-stu-id="3fb04-140">ToList</span></span>|<span data-ttu-id="3fb04-141">Converte uma coleção em um <xref:System.Collections.Generic.List%601>.</span><span class="sxs-lookup"><span data-stu-id="3fb04-141">Converts a collection to a <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="3fb04-142">Esse método força a execução de consulta.</span><span class="sxs-lookup"><span data-stu-id="3fb04-142">This method forces query execution.</span></span>|<span data-ttu-id="3fb04-143">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="3fb04-143">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>|
|<span data-ttu-id="3fb04-144">ToLookup</span><span class="sxs-lookup"><span data-stu-id="3fb04-144">ToLookup</span></span>|<span data-ttu-id="3fb04-145">Coloca os elementos em um <xref:System.Linq.Lookup%602> (um dicionário one-to-many) com base em uma função de seletor de chave.</span><span class="sxs-lookup"><span data-stu-id="3fb04-145">Puts elements into a <xref:System.Linq.Lookup%602> (a one-to-many dictionary) based on a key selector function.</span></span> <span data-ttu-id="3fb04-146">Esse método força a execução de consulta.</span><span class="sxs-lookup"><span data-stu-id="3fb04-146">This method forces query execution.</span></span>|<span data-ttu-id="3fb04-147">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="3fb04-147">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|

## <a name="query-expression-syntax-example"></a><span data-ttu-id="3fb04-148">Exemplo de sintaxe de expressão de consulta</span><span class="sxs-lookup"><span data-stu-id="3fb04-148">Query Expression Syntax Example</span></span>

<span data-ttu-id="3fb04-149">O exemplo de código a seguir usa uma variável de intervalo digitada explicitamente para converter um tipo em um subtipo antes de acessar um membro que está disponível somente no subtipo.</span><span class="sxs-lookup"><span data-stu-id="3fb04-149">The following code example uses an explicitly typed range variable to cast a type to a subtype before accessing a member that is available only on the subtype.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="3fb04-150">Confira também</span><span class="sxs-lookup"><span data-stu-id="3fb04-150">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="3fb04-151">Visão geral de operadores de consulta padrão (C#)</span><span class="sxs-lookup"><span data-stu-id="3fb04-151">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="3fb04-152">cláusula from</span><span class="sxs-lookup"><span data-stu-id="3fb04-152">from clause</span></span>](../../../language-reference/keywords/from-clause.md)
- [<span data-ttu-id="3fb04-153">Expressões de Consulta LINQ</span><span class="sxs-lookup"><span data-stu-id="3fb04-153">LINQ Query Expressions</span></span>](../../../linq/index.md)
- [<span data-ttu-id="3fb04-154">Como consultar uma ArrayList com LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="3fb04-154">How to query an ArrayList with LINQ (C#)</span></span>](./how-to-query-an-arraylist-with-linq.md)
