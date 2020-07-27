---
title: :::no-loc(Join):::Operações (C#)
description: Uma junção de duas fontes de dados associa objetos a objetos que compartilham um atributo entre fontes de dados. Saiba mais sobre os métodos de junção na estrutura do LINQ em C#.
ms.date: 07/20/2015
ms.assetid: 5105e0da-1267-4c00-837a-f0e9602279b8
no-loc:
- ':::no-loc(Join):::'
- ':::no-loc(GroupJoin):::'
ms.openlocfilehash: 1b453f1752edf0cc126f8e27dbdd9e91ad9143f3
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165690"
---
# <a name="no-locjoin-operations-c"></a><span data-ttu-id="b75de-104">:::no-loc(Join):::Operações (C#)</span><span class="sxs-lookup"><span data-stu-id="b75de-104">:::no-loc(Join)::: Operations (C#)</span></span>

<span data-ttu-id="b75de-105">Uma *junção* de duas fontes de dados é a associação de objetos em uma fonte de dados, com objetos que compartilham um atributo comum em outra fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="b75de-105">A *join* of two data sources is the association of objects in one data source with objects that share a common attribute in another data source.</span></span>  
  
 <span data-ttu-id="b75de-106">:::no-loc(Join):::o ing é uma operação importante em consultas que direcionam fontes de dados cujas relações entre si não podem ser seguidas diretamente.</span><span class="sxs-lookup"><span data-stu-id="b75de-106">:::no-loc(Join):::ing is an important operation in queries that target data sources whose relationships to each other cannot be followed directly.</span></span> <span data-ttu-id="b75de-107">Na programação orientada a objeto, isso pode significar uma correlação entre objetos que não são modelados, como a direção retroativa de uma relação unidirecional.</span><span class="sxs-lookup"><span data-stu-id="b75de-107">In object-oriented programming, this could mean a correlation between objects that is not modeled, such as the backwards direction of a one-way relationship.</span></span> <span data-ttu-id="b75de-108">Um exemplo de uma relação unidirecional é uma classe Cliente que tem uma propriedade do tipo Cidade, mas a classe Cidade ainda não tem uma propriedade que é uma coleção de objetos Cliente.</span><span class="sxs-lookup"><span data-stu-id="b75de-108">An example of a one-way relationship is a Customer class that has a property of type City, but the City class does not have a property that is a collection of Customer objects.</span></span> <span data-ttu-id="b75de-109">Se você tem uma lista de objetos Cidade e você quer encontrar todos os clientes em cada cidade, você pode usar uma operação de junção para encontrá-los.</span><span class="sxs-lookup"><span data-stu-id="b75de-109">If you have a list of City objects and you want to find all the customers in each city, you could use a join operation to find them.</span></span>  
  
 <span data-ttu-id="b75de-110">Os métodos de junção fornecidos na estrutura do LINQ são <xref:System.Linq.Enumerable.:::no-loc(Join):::%2A> e <xref:System.Linq.Enumerable.:::no-loc(GroupJoin):::%2A>.</span><span class="sxs-lookup"><span data-stu-id="b75de-110">The join methods provided in the LINQ framework are <xref:System.Linq.Enumerable.:::no-loc(Join):::%2A> and <xref:System.Linq.Enumerable.:::no-loc(GroupJoin):::%2A>.</span></span> <span data-ttu-id="b75de-111">Esses métodos executam junção por igualdade ou junções que correspondem duas fontes de dados com base na igualdade de suas chaves.</span><span class="sxs-lookup"><span data-stu-id="b75de-111">These methods perform equijoins, or joins that match two data sources based on equality of their keys.</span></span> <span data-ttu-id="b75de-112">(Para comparação, o Transact-SQL dá suporte a operadores de junção diferentes de ' Equals ', por exemplo, o operador ' less than '.) Em termos de banco de dados relacional, o <xref:System.Linq.Enumerable.:::no-loc(Join):::%2A> implementa uma junção interna, um tipo de junção em que somente os objetos que têm uma correspondência no outro conjunto são retornados.</span><span class="sxs-lookup"><span data-stu-id="b75de-112">(For comparison, Transact-SQL supports join operators other than 'equals', for example the 'less than' operator.) In relational database terms, <xref:System.Linq.Enumerable.:::no-loc(Join):::%2A> implements an inner join, a type of join in which only those objects that have a match in the other data set are returned.</span></span> <span data-ttu-id="b75de-113">O método <xref:System.Linq.Enumerable.:::no-loc(GroupJoin):::%2A> não tem equivalente direto em termos de banco de dados relacional, mas ele implementa um superconjunto de junções internas e junções externas esquerdas.</span><span class="sxs-lookup"><span data-stu-id="b75de-113">The <xref:System.Linq.Enumerable.:::no-loc(GroupJoin):::%2A> method has no direct equivalent in relational database terms, but it implements a superset of inner joins and left outer joins.</span></span> <span data-ttu-id="b75de-114">Uma junção externa esquerda é uma junção que retorna cada elemento da primeira (esquerda) fonte de dados, mesmo que ele não tenha elementos correlacionados na outra fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="b75de-114">A left outer join is a join that returns each element of the first (left) data source, even if it has no correlated elements in the other data source.</span></span>  
  
 <span data-ttu-id="b75de-115">A ilustração a seguir mostra uma visão conceitual de dois conjuntos e os elementos dentro desses conjuntos que estão incluídos em uma junção interna ou externa à esquerda.</span><span class="sxs-lookup"><span data-stu-id="b75de-115">The following illustration shows a conceptual view of two sets and the elements within those sets that are included in either an inner join or a left outer join.</span></span>  
  
 ![Dois círculos sobrepostos mostrando interna/externa.](./media/join-operations/join-method-overlapping-circles.png)  
  
## <a name="methods"></a><span data-ttu-id="b75de-117">Métodos</span><span class="sxs-lookup"><span data-stu-id="b75de-117">Methods</span></span>  
  
|<span data-ttu-id="b75de-118">Nome do método</span><span class="sxs-lookup"><span data-stu-id="b75de-118">Method Name</span></span>|<span data-ttu-id="b75de-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="b75de-119">Description</span></span>|<span data-ttu-id="b75de-120">Sintaxe de expressão de consulta C#</span><span class="sxs-lookup"><span data-stu-id="b75de-120">C# Query Expression Syntax</span></span>|<span data-ttu-id="b75de-121">Mais informações</span><span class="sxs-lookup"><span data-stu-id="b75de-121">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|:::no-loc(Join):::|<span data-ttu-id="b75de-122">:::no-loc(Join):::s duas sequências baseadas em funções de seletor de chave e extraem pares de valores.</span><span class="sxs-lookup"><span data-stu-id="b75de-122">:::no-loc(Join):::s two sequences based on key selector functions and extracts pairs of values.</span></span>|`join … in … on … equals …`|<xref:System.Linq.Enumerable.:::no-loc(Join):::%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.:::no-loc(Join):::%2A?displayProperty=nameWithType>|  
|:::no-loc(GroupJoin):::|<span data-ttu-id="b75de-123">:::no-loc(Join):::s duas sequências baseadas em funções de seletor de chave e agrupa as correspondências resultantes para cada elemento.</span><span class="sxs-lookup"><span data-stu-id="b75de-123">:::no-loc(Join):::s two sequences based on key selector functions and groups the resulting matches for each element.</span></span>|`join … in … on … equals … into …`|<xref:System.Linq.Enumerable.:::no-loc(GroupJoin):::%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.:::no-loc(GroupJoin):::%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="b75de-124">Exemplos de sintaxe de expressão de consulta</span><span class="sxs-lookup"><span data-stu-id="b75de-124">Query expression syntax examples</span></span>
  
### :::no-loc(Join):::  
  
<span data-ttu-id="b75de-125">O exemplo a seguir usa a `join … in … on … equals …` cláusula para unir duas sequências com base no valor específico:</span><span class="sxs-lookup"><span data-stu-id="b75de-125">The following example uses the `join … in … on … equals …` clause to join two sequences based on specific value:</span></span>
  
[!code-csharp[:::no-loc(Join):::](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csLINQ:::no-loc(Join):::Operation/CS/:::no-loc(Join):::Operation.cs#:::no-loc(Join):::)]  

### :::no-loc(GroupJoin):::  

<span data-ttu-id="b75de-126">O exemplo a seguir usa a `join … in … on … equals … into …` cláusula para unir duas sequências com base em um valor específico e agrupa as correspondências resultantes para cada elemento:</span><span class="sxs-lookup"><span data-stu-id="b75de-126">The following example uses the `join … in … on … equals … into …` clause to join two sequences based on specific value and groups the resulting matches for each element:</span></span>
  
[!code-csharp[:::no-loc(GroupJoin):::](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csLINQ:::no-loc(Join):::Operation/CS/:::no-loc(Join):::Operation.cs#:::no-loc(GroupJoin):::)]  
  
## <a name="see-also"></a><span data-ttu-id="b75de-127">Confira também</span><span class="sxs-lookup"><span data-stu-id="b75de-127">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="b75de-128">Visão geral de operadores de consulta padrão (C#)</span><span class="sxs-lookup"><span data-stu-id="b75de-128">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="b75de-129">Tipos anônimos</span><span class="sxs-lookup"><span data-stu-id="b75de-129">Anonymous Types</span></span>](../../classes-and-structs/anonymous-types.md)
- [<span data-ttu-id="b75de-130">Formular :::no-loc(Join)::: consultas de s e produtos cruzados</span><span class="sxs-lookup"><span data-stu-id="b75de-130">Formulate :::no-loc(Join):::s and Cross-Product Queries</span></span>](../../../../framework/data/adonet/sql/linq/formulate-joins-and-cross-product-queries.md)
- [<span data-ttu-id="b75de-131">Cláusula join</span><span class="sxs-lookup"><span data-stu-id="b75de-131">join clause</span></span>](../../../language-reference/keywords/join-clause.md)
- [<span data-ttu-id="b75de-132">:::no-loc(Join):::usando chaves compostas</span><span class="sxs-lookup"><span data-stu-id="b75de-132">:::no-loc(Join)::: by using composite keys</span></span>](../../../linq/join-by-using-composite-keys.md)
- [<span data-ttu-id="b75de-133">Como unir conteúdo de arquivos diferentes (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="b75de-133">How to join content from dissimilar files (LINQ) (C#)</span></span>](./how-to-join-content-from-dissimilar-files-linq.md)
- [<span data-ttu-id="b75de-134">Ordenar os resultados de uma cláusula join</span><span class="sxs-lookup"><span data-stu-id="b75de-134">Order the results of a join clause</span></span>](../../../linq/order-the-results-of-a-join-clause.md)
- [<span data-ttu-id="b75de-135">Executar operações de junção personalizadas</span><span class="sxs-lookup"><span data-stu-id="b75de-135">Perform custom join operations</span></span>](../../../linq/perform-custom-join-operations.md)
- [<span data-ttu-id="b75de-136">Executar junções agrupadas</span><span class="sxs-lookup"><span data-stu-id="b75de-136">Perform grouped joins</span></span>](../../../linq/perform-grouped-joins.md)
- [<span data-ttu-id="b75de-137">Executar junções internas</span><span class="sxs-lookup"><span data-stu-id="b75de-137">Perform inner joins</span></span>](../../../linq/perform-inner-joins.md)
- [<span data-ttu-id="b75de-138">Executar junções externas esquerdas</span><span class="sxs-lookup"><span data-stu-id="b75de-138">Perform left outer joins</span></span>](../../../linq/perform-left-outer-joins.md)
- [<span data-ttu-id="b75de-139">Como preencher coleções de objetos de várias fontes (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="b75de-139">How to populate object collections from multiple sources (LINQ) (C#)</span></span>](./how-to-populate-object-collections-from-multiple-sources-linq.md)
