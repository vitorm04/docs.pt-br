---
title: Convertendo Tipos de Dados (C#)
ms.date: 07/20/2015
ms.assetid: 46e5682f-77a1-4302-8f93-a2b53c408808
ms.openlocfilehash: 9e8b7726b94871a17a4be50a9b24d8b73abcf79c
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69594635"
---
# <a name="converting-data-types-c"></a><span data-ttu-id="16334-102">Convertendo Tipos de Dados (C#)</span><span class="sxs-lookup"><span data-stu-id="16334-102">Converting Data Types (C#)</span></span>
<span data-ttu-id="16334-103">Os métodos de conversão alteram o tipo dos objetos de entrada.</span><span class="sxs-lookup"><span data-stu-id="16334-103">Conversion methods change the type of input objects.</span></span>  
  
 <span data-ttu-id="16334-104">As operações de conversão em consultas LINQ são úteis em diversas aplicações.</span><span class="sxs-lookup"><span data-stu-id="16334-104">Conversion operations in LINQ queries are useful in a variety of applications.</span></span> <span data-ttu-id="16334-105">A seguir estão alguns exemplos:</span><span class="sxs-lookup"><span data-stu-id="16334-105">Following are some examples:</span></span>  
  
- <span data-ttu-id="16334-106">O método <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> pode ser usado para ocultar a implementação personalizada de um tipo de um operador de consulta padrão.</span><span class="sxs-lookup"><span data-stu-id="16334-106">The <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> method can be used to hide a type's custom implementation of a standard query operator.</span></span>  
  
- <span data-ttu-id="16334-107">O método <xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> pode ser usado para habilitar coleções sem parâmetros para consulta LINQ.</span><span class="sxs-lookup"><span data-stu-id="16334-107">The <xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> method can be used to enable non-parameterized collections for LINQ querying.</span></span>  
  
- <span data-ttu-id="16334-108">Os métodos <xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> e <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> podem ser usados para forçar a execução de consulta imediata em vez de adiá-la até que a consulta seja enumerada.</span><span class="sxs-lookup"><span data-stu-id="16334-108">The <xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>, and <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> methods can be used to force immediate query execution instead of deferring it until the query is enumerated.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="16334-109">Métodos</span><span class="sxs-lookup"><span data-stu-id="16334-109">Methods</span></span>  
 <span data-ttu-id="16334-110">A tabela a seguir lista os métodos de operador de consulta padrão que realizam conversões de tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="16334-110">The following table lists the standard query operator methods that perform data-type conversions.</span></span>  
  
 <span data-ttu-id="16334-111">Os métodos de conversão nesta tabela cujos nomes começam com "As" alteram o tipo estático da coleção de origem, mas não a enumeram.</span><span class="sxs-lookup"><span data-stu-id="16334-111">The conversion methods in this table whose names start with "As" change the static type of the source collection but do not enumerate it.</span></span> <span data-ttu-id="16334-112">Os métodos cujos nomes começam com "To" enumeram a coleção de origem e colocam os itens na coleção de tipo correspondente.</span><span class="sxs-lookup"><span data-stu-id="16334-112">The methods whose names start with "To" enumerate the source collection and put the items into the corresponding collection type.</span></span>  
  
|<span data-ttu-id="16334-113">Nome do método</span><span class="sxs-lookup"><span data-stu-id="16334-113">Method Name</span></span>|<span data-ttu-id="16334-114">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="16334-114">Description</span></span>|<span data-ttu-id="16334-115">Sintaxe de expressão de consulta C#</span><span class="sxs-lookup"><span data-stu-id="16334-115">C# Query Expression Syntax</span></span>|<span data-ttu-id="16334-116">Mais informações</span><span class="sxs-lookup"><span data-stu-id="16334-116">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="16334-117">AsEnumerable</span><span class="sxs-lookup"><span data-stu-id="16334-117">AsEnumerable</span></span>|<span data-ttu-id="16334-118">Retorna a entrada digitada como <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="16334-118">Returns the input typed as <xref:System.Collections.Generic.IEnumerable%601>.</span></span>|<span data-ttu-id="16334-119">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="16334-119">Not applicable.</span></span>|<xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="16334-120">AsQueryable</span><span class="sxs-lookup"><span data-stu-id="16334-120">AsQueryable</span></span>|<span data-ttu-id="16334-121">Converte um <xref:System.Collections.IEnumerable> (genérico) em um <xref:System.Linq.IQueryable> (genérico).</span><span class="sxs-lookup"><span data-stu-id="16334-121">Converts a (generic) <xref:System.Collections.IEnumerable> to a (generic) <xref:System.Linq.IQueryable>.</span></span>|<span data-ttu-id="16334-122">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="16334-122">Not applicable.</span></span>|<xref:System.Linq.Queryable.AsQueryable%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="16334-123">Conversão</span><span class="sxs-lookup"><span data-stu-id="16334-123">Cast</span></span>|<span data-ttu-id="16334-124">Converte os elementos de uma coleção em um tipo especificado.</span><span class="sxs-lookup"><span data-stu-id="16334-124">Casts the elements of a collection to a specified type.</span></span>|<span data-ttu-id="16334-125">Use uma variável de intervalo de tipo explícito.</span><span class="sxs-lookup"><span data-stu-id="16334-125">Use an explicitly typed range variable.</span></span> <span data-ttu-id="16334-126">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="16334-126">For example:</span></span><br /><br /> `from string str in words`|<xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Cast%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="16334-127">OfType</span><span class="sxs-lookup"><span data-stu-id="16334-127">OfType</span></span>|<span data-ttu-id="16334-128">Filtra valores, dependendo da capacidade de serem convertidos em um tipo especificado.</span><span class="sxs-lookup"><span data-stu-id="16334-128">Filters values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="16334-129">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="16334-129">Not applicable.</span></span>|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="16334-130">ToArray</span><span class="sxs-lookup"><span data-stu-id="16334-130">ToArray</span></span>|<span data-ttu-id="16334-131">Converte uma coleção em uma matriz.</span><span class="sxs-lookup"><span data-stu-id="16334-131">Converts a collection to an array.</span></span> <span data-ttu-id="16334-132">Esse método força a execução de consulta.</span><span class="sxs-lookup"><span data-stu-id="16334-132">This method forces query execution.</span></span>|<span data-ttu-id="16334-133">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="16334-133">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="16334-134">ToDictionary</span><span class="sxs-lookup"><span data-stu-id="16334-134">ToDictionary</span></span>|<span data-ttu-id="16334-135">Coloca os elementos em um <xref:System.Collections.Generic.Dictionary%602> com base em uma função de seletor de chave.</span><span class="sxs-lookup"><span data-stu-id="16334-135">Puts elements into a <xref:System.Collections.Generic.Dictionary%602> based on a key selector function.</span></span> <span data-ttu-id="16334-136">Esse método força a execução de consulta.</span><span class="sxs-lookup"><span data-stu-id="16334-136">This method forces query execution.</span></span>|<span data-ttu-id="16334-137">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="16334-137">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="16334-138">ToList</span><span class="sxs-lookup"><span data-stu-id="16334-138">ToList</span></span>|<span data-ttu-id="16334-139">Converte uma coleção em um <xref:System.Collections.Generic.List%601>.</span><span class="sxs-lookup"><span data-stu-id="16334-139">Converts a collection to a <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="16334-140">Esse método força a execução de consulta.</span><span class="sxs-lookup"><span data-stu-id="16334-140">This method forces query execution.</span></span>|<span data-ttu-id="16334-141">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="16334-141">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="16334-142">ToLookup</span><span class="sxs-lookup"><span data-stu-id="16334-142">ToLookup</span></span>|<span data-ttu-id="16334-143">Coloca os elementos em um <xref:System.Linq.Lookup%602> (um dicionário one-to-many) com base em uma função de seletor de chave.</span><span class="sxs-lookup"><span data-stu-id="16334-143">Puts elements into a <xref:System.Linq.Lookup%602> (a one-to-many dictionary) based on a key selector function.</span></span> <span data-ttu-id="16334-144">Esse método força a execução de consulta.</span><span class="sxs-lookup"><span data-stu-id="16334-144">This method forces query execution.</span></span>|<span data-ttu-id="16334-145">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="16334-145">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="16334-146">Exemplo de sintaxe de expressão de consulta</span><span class="sxs-lookup"><span data-stu-id="16334-146">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="16334-147">O exemplo de código a seguir usa uma variável de intervalo de tipo explícito para converter um tipo em um subtipo antes de acessar um membro que está disponível somente no subtipo.</span><span class="sxs-lookup"><span data-stu-id="16334-147">The following code example uses an explicitly-typed range variable  to cast a type to a subtype before accessing a member that is available only on the subtype.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="16334-148">Consulte também</span><span class="sxs-lookup"><span data-stu-id="16334-148">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="16334-149">Visão geral de operadores de consulta padrão (C#)</span><span class="sxs-lookup"><span data-stu-id="16334-149">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="16334-150">Cláusula From</span><span class="sxs-lookup"><span data-stu-id="16334-150">from clause</span></span>](../../../language-reference/keywords/from-clause.md)
- [<span data-ttu-id="16334-151">Expressões de consulta LINQ</span><span class="sxs-lookup"><span data-stu-id="16334-151">LINQ Query Expressions</span></span>](../../linq-query-expressions/index.md)
- [<span data-ttu-id="16334-152">Como: Consultar uma ArrayList com LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="16334-152">How to: Query an ArrayList with LINQ (C#)</span></span>](./how-to-query-an-arraylist-with-linq.md)
