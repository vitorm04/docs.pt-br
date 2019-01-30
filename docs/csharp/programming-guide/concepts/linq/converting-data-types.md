---
title: Convertendo Tipos de Dados (C#)
ms.date: 07/20/2015
ms.assetid: 46e5682f-77a1-4302-8f93-a2b53c408808
ms.openlocfilehash: ea1f204ab59ecdd3e3e7e65d12c1be37e9b09f01
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54736874"
---
# <a name="converting-data-types-c"></a><span data-ttu-id="11bb6-102">Convertendo Tipos de Dados (C#)</span><span class="sxs-lookup"><span data-stu-id="11bb6-102">Converting Data Types (C#)</span></span>
<span data-ttu-id="11bb6-103">Os métodos de conversão alteram o tipo dos objetos de entrada.</span><span class="sxs-lookup"><span data-stu-id="11bb6-103">Conversion methods change the type of input objects.</span></span>  
  
 <span data-ttu-id="11bb6-104">As operações de conversão em consultas LINQ são úteis em diversas aplicações.</span><span class="sxs-lookup"><span data-stu-id="11bb6-104">Conversion operations in LINQ queries are useful in a variety of applications.</span></span> <span data-ttu-id="11bb6-105">A seguir estão alguns exemplos:</span><span class="sxs-lookup"><span data-stu-id="11bb6-105">Following are some examples:</span></span>  
  
-   <span data-ttu-id="11bb6-106">O método <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> pode ser usado para ocultar a implementação personalizada de um tipo de um operador de consulta padrão.</span><span class="sxs-lookup"><span data-stu-id="11bb6-106">The <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> method can be used to hide a type's custom implementation of a standard query operator.</span></span>  
  
-   <span data-ttu-id="11bb6-107">O método <xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> pode ser usado para habilitar coleções sem parâmetros para consulta LINQ.</span><span class="sxs-lookup"><span data-stu-id="11bb6-107">The <xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> method can be used to enable non-parameterized collections for LINQ querying.</span></span>  
  
-   <span data-ttu-id="11bb6-108">Os métodos <xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> e <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> podem ser usados para forçar a execução de consulta imediata em vez de adiá-la até que a consulta seja enumerada.</span><span class="sxs-lookup"><span data-stu-id="11bb6-108">The <xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>, and <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> methods can be used to force immediate query execution instead of deferring it until the query is enumerated.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="11bb6-109">Métodos</span><span class="sxs-lookup"><span data-stu-id="11bb6-109">Methods</span></span>  
 <span data-ttu-id="11bb6-110">A tabela a seguir lista os métodos de operador de consulta padrão que realizam conversões de tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="11bb6-110">The following table lists the standard query operator methods that perform data-type conversions.</span></span>  
  
 <span data-ttu-id="11bb6-111">Os métodos de conversão nesta tabela cujos nomes começam com "As" alteram o tipo estático da coleção de origem, mas não a enumeram.</span><span class="sxs-lookup"><span data-stu-id="11bb6-111">The conversion methods in this table whose names start with "As" change the static type of the source collection but do not enumerate it.</span></span> <span data-ttu-id="11bb6-112">Os métodos cujos nomes começam com "To" enumeram a coleção de origem e colocam os itens na coleção de tipo correspondente.</span><span class="sxs-lookup"><span data-stu-id="11bb6-112">The methods whose names start with "To" enumerate the source collection and put the items into the corresponding collection type.</span></span>  
  
|<span data-ttu-id="11bb6-113">Nome do método</span><span class="sxs-lookup"><span data-stu-id="11bb6-113">Method Name</span></span>|<span data-ttu-id="11bb6-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="11bb6-114">Description</span></span>|<span data-ttu-id="11bb6-115">Sintaxe de expressão de consulta C#</span><span class="sxs-lookup"><span data-stu-id="11bb6-115">C# Query Expression Syntax</span></span>|<span data-ttu-id="11bb6-116">Mais informações</span><span class="sxs-lookup"><span data-stu-id="11bb6-116">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="11bb6-117">AsEnumerable</span><span class="sxs-lookup"><span data-stu-id="11bb6-117">AsEnumerable</span></span>|<span data-ttu-id="11bb6-118">Retorna a entrada digitada como <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="11bb6-118">Returns the input typed as <xref:System.Collections.Generic.IEnumerable%601>.</span></span>|<span data-ttu-id="11bb6-119">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="11bb6-119">Not applicable.</span></span>|<xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="11bb6-120">AsQueryable</span><span class="sxs-lookup"><span data-stu-id="11bb6-120">AsQueryable</span></span>|<span data-ttu-id="11bb6-121">Converte um <xref:System.Collections.IEnumerable> (genérico) em um <xref:System.Linq.IQueryable> (genérico).</span><span class="sxs-lookup"><span data-stu-id="11bb6-121">Converts a (generic) <xref:System.Collections.IEnumerable> to a (generic) <xref:System.Linq.IQueryable>.</span></span>|<span data-ttu-id="11bb6-122">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="11bb6-122">Not applicable.</span></span>|<xref:System.Linq.Queryable.AsQueryable%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="11bb6-123">Conversão</span><span class="sxs-lookup"><span data-stu-id="11bb6-123">Cast</span></span>|<span data-ttu-id="11bb6-124">Converte os elementos de uma coleção em um tipo especificado.</span><span class="sxs-lookup"><span data-stu-id="11bb6-124">Casts the elements of a collection to a specified type.</span></span>|<span data-ttu-id="11bb6-125">Use uma variável de intervalo de tipo explícito.</span><span class="sxs-lookup"><span data-stu-id="11bb6-125">Use an explicitly typed range variable.</span></span> <span data-ttu-id="11bb6-126">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="11bb6-126">For example:</span></span><br /><br /> `from string str in words`|<xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Cast%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="11bb6-127">OfType</span><span class="sxs-lookup"><span data-stu-id="11bb6-127">OfType</span></span>|<span data-ttu-id="11bb6-128">Filtra valores, dependendo da capacidade de serem convertidos em um tipo especificado.</span><span class="sxs-lookup"><span data-stu-id="11bb6-128">Filters values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="11bb6-129">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="11bb6-129">Not applicable.</span></span>|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="11bb6-130">ToArray</span><span class="sxs-lookup"><span data-stu-id="11bb6-130">ToArray</span></span>|<span data-ttu-id="11bb6-131">Converte uma coleção em uma matriz.</span><span class="sxs-lookup"><span data-stu-id="11bb6-131">Converts a collection to an array.</span></span> <span data-ttu-id="11bb6-132">Esse método força a execução de consulta.</span><span class="sxs-lookup"><span data-stu-id="11bb6-132">This method forces query execution.</span></span>|<span data-ttu-id="11bb6-133">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="11bb6-133">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="11bb6-134">ToDictionary</span><span class="sxs-lookup"><span data-stu-id="11bb6-134">ToDictionary</span></span>|<span data-ttu-id="11bb6-135">Coloca os elementos em um <xref:System.Collections.Generic.Dictionary%602> com base em uma função de seletor de chave.</span><span class="sxs-lookup"><span data-stu-id="11bb6-135">Puts elements into a <xref:System.Collections.Generic.Dictionary%602> based on a key selector function.</span></span> <span data-ttu-id="11bb6-136">Esse método força a execução de consulta.</span><span class="sxs-lookup"><span data-stu-id="11bb6-136">This method forces query execution.</span></span>|<span data-ttu-id="11bb6-137">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="11bb6-137">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="11bb6-138">ToList</span><span class="sxs-lookup"><span data-stu-id="11bb6-138">ToList</span></span>|<span data-ttu-id="11bb6-139">Converte uma coleção em um <xref:System.Collections.Generic.List%601>.</span><span class="sxs-lookup"><span data-stu-id="11bb6-139">Converts a collection to a <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="11bb6-140">Esse método força a execução de consulta.</span><span class="sxs-lookup"><span data-stu-id="11bb6-140">This method forces query execution.</span></span>|<span data-ttu-id="11bb6-141">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="11bb6-141">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="11bb6-142">ToLookup</span><span class="sxs-lookup"><span data-stu-id="11bb6-142">ToLookup</span></span>|<span data-ttu-id="11bb6-143">Coloca os elementos em um <xref:System.Linq.Lookup%602> (um dicionário one-to-many) com base em uma função de seletor de chave.</span><span class="sxs-lookup"><span data-stu-id="11bb6-143">Puts elements into a <xref:System.Linq.Lookup%602> (a one-to-many dictionary) based on a key selector function.</span></span> <span data-ttu-id="11bb6-144">Esse método força a execução de consulta.</span><span class="sxs-lookup"><span data-stu-id="11bb6-144">This method forces query execution.</span></span>|<span data-ttu-id="11bb6-145">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="11bb6-145">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="11bb6-146">Exemplo de sintaxe de expressão de consulta</span><span class="sxs-lookup"><span data-stu-id="11bb6-146">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="11bb6-147">O exemplo de código a seguir usa uma variável de intervalo de tipo explícito para converter um tipo em um subtipo antes de acessar um membro que está disponível somente no subtipo.</span><span class="sxs-lookup"><span data-stu-id="11bb6-147">The following code example uses an explicitly-typed range variable  to cast a type to a subtype before accessing a member that is available only on the subtype.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="11bb6-148">Consulte também</span><span class="sxs-lookup"><span data-stu-id="11bb6-148">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="11bb6-149">Visão geral de operadores de consulta padrão (C#)</span><span class="sxs-lookup"><span data-stu-id="11bb6-149">Standard Query Operators Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="11bb6-150">Cláusula From</span><span class="sxs-lookup"><span data-stu-id="11bb6-150">from clause</span></span>](../../../../csharp/language-reference/keywords/from-clause.md)
- [<span data-ttu-id="11bb6-151">Expressões de consulta LINQ</span><span class="sxs-lookup"><span data-stu-id="11bb6-151">LINQ Query Expressions</span></span>](../../../../csharp/programming-guide/linq-query-expressions/index.md)
- [<span data-ttu-id="11bb6-152">Como: Consultar uma ArrayList com LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="11bb6-152">How to: Query an ArrayList with LINQ (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md)
