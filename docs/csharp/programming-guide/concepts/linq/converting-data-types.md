---
title: Convertendo Tipos de Dados (C#)
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 46e5682f-77a1-4302-8f93-a2b53c408808
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 454fb0ce937d7d20dfce26d92dbf49de24f062f0
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="converting-data-types-c"></a><span data-ttu-id="6ff96-102">Convertendo Tipos de Dados (C#)</span><span class="sxs-lookup"><span data-stu-id="6ff96-102">Converting Data Types (C#)</span></span>
<span data-ttu-id="6ff96-103">Os métodos de conversão alteram o tipo dos objetos de entrada.</span><span class="sxs-lookup"><span data-stu-id="6ff96-103">Conversion methods change the type of input objects.</span></span>  
  
 <span data-ttu-id="6ff96-104">As operações de conversão em consultas LINQ são úteis em diversas aplicações.</span><span class="sxs-lookup"><span data-stu-id="6ff96-104">Conversion operations in LINQ queries are useful in a variety of applications.</span></span> <span data-ttu-id="6ff96-105">A seguir estão alguns exemplos:</span><span class="sxs-lookup"><span data-stu-id="6ff96-105">Following are some examples:</span></span>  
  
-   <span data-ttu-id="6ff96-106">O método <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=fullName> pode ser usado para ocultar a implementação personalizada de um tipo de um operador de consulta padrão.</span><span class="sxs-lookup"><span data-stu-id="6ff96-106">The <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=fullName> method can be used to hide a type's custom implementation of a standard query operator.</span></span>  
  
-   <span data-ttu-id="6ff96-107">O método <xref:System.Linq.Enumerable.OfType%2A?displayProperty=fullName> pode ser usado para habilitar coleções sem parâmetros para consulta LINQ.</span><span class="sxs-lookup"><span data-stu-id="6ff96-107">The <xref:System.Linq.Enumerable.OfType%2A?displayProperty=fullName> method can be used to enable non-parameterized collections for LINQ querying.</span></span>  
  
-   <span data-ttu-id="6ff96-108">Os métodos <xref:System.Linq.Enumerable.ToArray%2A?displayProperty=fullName>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=fullName>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=fullName> e <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=fullName> podem ser usados para forçar a execução de consulta imediata em vez de adiá-la até que a consulta seja enumerada.</span><span class="sxs-lookup"><span data-stu-id="6ff96-108">The <xref:System.Linq.Enumerable.ToArray%2A?displayProperty=fullName>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=fullName>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=fullName>, and <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=fullName> methods can be used to force immediate query execution instead of deferring it until the query is enumerated.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6ff96-109">Métodos</span><span class="sxs-lookup"><span data-stu-id="6ff96-109">Methods</span></span>  
 <span data-ttu-id="6ff96-110">A tabela a seguir lista os métodos de operador de consulta padrão que realizam conversões de tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="6ff96-110">The following table lists the standard query operator methods that perform data-type conversions.</span></span>  
  
 <span data-ttu-id="6ff96-111">Os métodos de conversão nesta tabela cujos nomes começam com "As" alteram o tipo estático da coleção de origem, mas não a enumeram.</span><span class="sxs-lookup"><span data-stu-id="6ff96-111">The conversion methods in this table whose names start with "As" change the static type of the source collection but do not enumerate it.</span></span> <span data-ttu-id="6ff96-112">Os métodos cujos nomes começam com "To" enumeram a coleção de origem e colocam os itens na coleção de tipo correspondente.</span><span class="sxs-lookup"><span data-stu-id="6ff96-112">The methods whose names start with "To" enumerate the source collection and put the items into the corresponding collection type.</span></span>  
  
|<span data-ttu-id="6ff96-113">Nome do método</span><span class="sxs-lookup"><span data-stu-id="6ff96-113">Method Name</span></span>|<span data-ttu-id="6ff96-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="6ff96-114">Description</span></span>|<span data-ttu-id="6ff96-115">Sintaxe de expressão de consulta C#</span><span class="sxs-lookup"><span data-stu-id="6ff96-115">C# Query Expression Syntax</span></span>|<span data-ttu-id="6ff96-116">Mais informações</span><span class="sxs-lookup"><span data-stu-id="6ff96-116">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="6ff96-117">AsEnumerable</span><span class="sxs-lookup"><span data-stu-id="6ff96-117">AsEnumerable</span></span>|<span data-ttu-id="6ff96-118">Retorna a entrada digitada como <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="6ff96-118">Returns the input typed as <xref:System.Collections.Generic.IEnumerable%601>.</span></span>|<span data-ttu-id="6ff96-119">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="6ff96-119">Not applicable.</span></span>|<xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=fullName>|  
|<span data-ttu-id="6ff96-120">AsQueryable</span><span class="sxs-lookup"><span data-stu-id="6ff96-120">AsQueryable</span></span>|<span data-ttu-id="6ff96-121">Converte um <xref:System.Collections.IEnumerable> (genérico) em um <xref:System.Linq.IQueryable> (genérico).</span><span class="sxs-lookup"><span data-stu-id="6ff96-121">Converts a (generic) <xref:System.Collections.IEnumerable> to a (generic) <xref:System.Linq.IQueryable>.</span></span>|<span data-ttu-id="6ff96-122">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="6ff96-122">Not applicable.</span></span>|<xref:System.Linq.Queryable.AsQueryable%2A?displayProperty=fullName>|  
|<span data-ttu-id="6ff96-123">Conversão</span><span class="sxs-lookup"><span data-stu-id="6ff96-123">Cast</span></span>|<span data-ttu-id="6ff96-124">Converte os elementos de uma coleção em um tipo especificado.</span><span class="sxs-lookup"><span data-stu-id="6ff96-124">Casts the elements of a collection to a specified type.</span></span>|<span data-ttu-id="6ff96-125">Use uma variável de intervalo de tipo explícito.</span><span class="sxs-lookup"><span data-stu-id="6ff96-125">Use an explicitly typed range variable.</span></span> <span data-ttu-id="6ff96-126">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="6ff96-126">For example:</span></span><br /><br /> `from string str in words`|<xref:System.Linq.Enumerable.Cast%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Cast%2A?displayProperty=fullName>|  
|<span data-ttu-id="6ff96-127">OfType</span><span class="sxs-lookup"><span data-stu-id="6ff96-127">OfType</span></span>|<span data-ttu-id="6ff96-128">Filtra valores, dependendo da capacidade de serem convertidos em um tipo especificado.</span><span class="sxs-lookup"><span data-stu-id="6ff96-128">Filters values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="6ff96-129">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="6ff96-129">Not applicable.</span></span>|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=fullName>|  
|<span data-ttu-id="6ff96-130">ToArray</span><span class="sxs-lookup"><span data-stu-id="6ff96-130">ToArray</span></span>|<span data-ttu-id="6ff96-131">Converte uma coleção em uma matriz.</span><span class="sxs-lookup"><span data-stu-id="6ff96-131">Converts a collection to an array.</span></span> <span data-ttu-id="6ff96-132">Esse método força a execução de consulta.</span><span class="sxs-lookup"><span data-stu-id="6ff96-132">This method forces query execution.</span></span>|<span data-ttu-id="6ff96-133">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="6ff96-133">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToArray%2A?displayProperty=fullName>|  
|<span data-ttu-id="6ff96-134">ToDictionary</span><span class="sxs-lookup"><span data-stu-id="6ff96-134">ToDictionary</span></span>|<span data-ttu-id="6ff96-135">Coloca os elementos em um <xref:System.Collections.Generic.Dictionary%602> com base em uma função de seletor de chave.</span><span class="sxs-lookup"><span data-stu-id="6ff96-135">Puts elements into a <xref:System.Collections.Generic.Dictionary%602> based on a key selector function.</span></span> <span data-ttu-id="6ff96-136">Esse método força a execução de consulta.</span><span class="sxs-lookup"><span data-stu-id="6ff96-136">This method forces query execution.</span></span>|<span data-ttu-id="6ff96-137">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="6ff96-137">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=fullName>|  
|<span data-ttu-id="6ff96-138">ToList</span><span class="sxs-lookup"><span data-stu-id="6ff96-138">ToList</span></span>|<span data-ttu-id="6ff96-139">Converte uma coleção em um <xref:System.Collections.Generic.List%601>.</span><span class="sxs-lookup"><span data-stu-id="6ff96-139">Converts a collection to a <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="6ff96-140">Esse método força a execução de consulta.</span><span class="sxs-lookup"><span data-stu-id="6ff96-140">This method forces query execution.</span></span>|<span data-ttu-id="6ff96-141">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="6ff96-141">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToList%2A?displayProperty=fullName>|  
|<span data-ttu-id="6ff96-142">ToLookup</span><span class="sxs-lookup"><span data-stu-id="6ff96-142">ToLookup</span></span>|<span data-ttu-id="6ff96-143">Coloca os elementos em um <xref:System.Linq.Lookup%602> (um dicionário one-to-many) com base em uma função de seletor de chave.</span><span class="sxs-lookup"><span data-stu-id="6ff96-143">Puts elements into a <xref:System.Linq.Lookup%602> (a one-to-many dictionary) based on a key selector function.</span></span> <span data-ttu-id="6ff96-144">Esse método força a execução de consulta.</span><span class="sxs-lookup"><span data-stu-id="6ff96-144">This method forces query execution.</span></span>|<span data-ttu-id="6ff96-145">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="6ff96-145">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=fullName>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="6ff96-146">Exemplo de sintaxe de expressão de consulta</span><span class="sxs-lookup"><span data-stu-id="6ff96-146">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="6ff96-147">O exemplo de código a seguir usa uma variável de intervalo de tipo explícito para converter um tipo em um subtipo antes de acessar um membro que está disponível somente no subtipo.</span><span class="sxs-lookup"><span data-stu-id="6ff96-147">The following code example uses an explicitly-typed range variable  to cast a type to a subtype before accessing a member that is available only on the subtype.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6ff96-148">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6ff96-148">See Also</span></span>  
 <span data-ttu-id="6ff96-149"><xref:System.Linq></span><span class="sxs-lookup"><span data-stu-id="6ff96-149"><xref:System.Linq></span></span>   
 <span data-ttu-id="6ff96-150">[Visão geral de operadores de consulta padrão (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) </span><span class="sxs-lookup"><span data-stu-id="6ff96-150">[Standard Query Operators Overview (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) </span></span>  
 <span data-ttu-id="6ff96-151">[Cláusula from](../../../../csharp/language-reference/keywords/from-clause.md) </span><span class="sxs-lookup"><span data-stu-id="6ff96-151">[from clause](../../../../csharp/language-reference/keywords/from-clause.md) </span></span>  
 <span data-ttu-id="6ff96-152">[Expressões de Consulta LINQ](../../../../csharp/programming-guide/linq-query-expressions/index.md) </span><span class="sxs-lookup"><span data-stu-id="6ff96-152">[LINQ Query Expressions](../../../../csharp/programming-guide/linq-query-expressions/index.md) </span></span>  
 [<span data-ttu-id="6ff96-153">Como consultar um ArrayList com LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="6ff96-153">How to: Query an ArrayList with LINQ (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md)

