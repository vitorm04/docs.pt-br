---
title: JoinOperações (C#)
ms.date: 07/20/2015
ms.assetid: 5105e0da-1267-4c00-837a-f0e9602279b8
no-loc:
- Join
- GroupJoin
ms.openlocfilehash: 6e2ec1a0c8120f6869b7c0a196b77d118762a8dd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76867999"
---
# <a name="join-operations-c"></a><span data-ttu-id="a06ef-102">Operações de junção (C#)</span><span class="sxs-lookup"><span data-stu-id="a06ef-102">Join Operations (C#)</span></span>

<span data-ttu-id="a06ef-103">Uma *junção* de duas fontes de dados é a associação de objetos em uma fonte de dados, com objetos que compartilham um atributo comum em outra fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="a06ef-103">A *join* of two data sources is the association of objects in one data source with objects that share a common attribute in another data source.</span></span>  
  
 <span data-ttu-id="a06ef-104">A junção é uma operação importante em consultas que têm como destino fontes de dados cujas relações entre si não podem ser seguidas diretamente.</span><span class="sxs-lookup"><span data-stu-id="a06ef-104">Joining is an important operation in queries that target data sources whose relationships to each other cannot be followed directly.</span></span> <span data-ttu-id="a06ef-105">Na programação orientada a objeto, isso pode significar uma correlação entre objetos que não são modelados, como a direção retroativa de uma relação unidirecional.</span><span class="sxs-lookup"><span data-stu-id="a06ef-105">In object-oriented programming, this could mean a correlation between objects that is not modeled, such as the backwards direction of a one-way relationship.</span></span> <span data-ttu-id="a06ef-106">Um exemplo de uma relação unidirecional é uma classe Cliente que tem uma propriedade do tipo Cidade, mas a classe Cidade ainda não tem uma propriedade que é uma coleção de objetos Cliente.</span><span class="sxs-lookup"><span data-stu-id="a06ef-106">An example of a one-way relationship is a Customer class that has a property of type City, but the City class does not have a property that is a collection of Customer objects.</span></span> <span data-ttu-id="a06ef-107">Se você tem uma lista de objetos Cidade e você quer encontrar todos os clientes em cada cidade, você pode usar uma operação de junção para encontrá-los.</span><span class="sxs-lookup"><span data-stu-id="a06ef-107">If you have a list of City objects and you want to find all the customers in each city, you could use a join operation to find them.</span></span>  
  
 <span data-ttu-id="a06ef-108">Os métodos de junção fornecidos na estrutura do LINQ são <xref:System.Linq.Enumerable.Join%2A> e <xref:System.Linq.Enumerable.GroupJoin%2A>.</span><span class="sxs-lookup"><span data-stu-id="a06ef-108">The join methods provided in the LINQ framework are <xref:System.Linq.Enumerable.Join%2A> and <xref:System.Linq.Enumerable.GroupJoin%2A>.</span></span> <span data-ttu-id="a06ef-109">Esses métodos executam junção por igualdade ou junções que correspondem duas fontes de dados com base na igualdade de suas chaves.</span><span class="sxs-lookup"><span data-stu-id="a06ef-109">These methods perform equijoins, or joins that match two data sources based on equality of their keys.</span></span> <span data-ttu-id="a06ef-110">(Para comparação, o Transact-SQL suporta unir operadores que não os "iguais", por exemplo, o operador 'menos que'.) Em termos de banco <xref:System.Linq.Enumerable.Join%2A> de dados relacionais, implementa uma adesão interna, um tipo de adesão em que apenas os objetos que têm uma correspondência no outro conjunto de dados são devolvidos.</span><span class="sxs-lookup"><span data-stu-id="a06ef-110">(For comparison, Transact-SQL supports join operators other than 'equals', for example the 'less than' operator.) In relational database terms, <xref:System.Linq.Enumerable.Join%2A> implements an inner join, a type of join in which only those objects that have a match in the other data set are returned.</span></span> <span data-ttu-id="a06ef-111">O método <xref:System.Linq.Enumerable.GroupJoin%2A> não tem equivalente direto em termos de banco de dados relacional, mas ele implementa um superconjunto de junções internas e junções externas esquerdas.</span><span class="sxs-lookup"><span data-stu-id="a06ef-111">The <xref:System.Linq.Enumerable.GroupJoin%2A> method has no direct equivalent in relational database terms, but it implements a superset of inner joins and left outer joins.</span></span> <span data-ttu-id="a06ef-112">Uma junção externa esquerda é uma junção que retorna cada elemento da primeira (esquerda) fonte de dados, mesmo que ele não tenha elementos correlacionados na outra fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="a06ef-112">A left outer join is a join that returns each element of the first (left) data source, even if it has no correlated elements in the other data source.</span></span>  
  
 <span data-ttu-id="a06ef-113">A ilustração a seguir mostra uma visão conceitual de dois conjuntos e os elementos dentro desses conjuntos que estão incluídos em uma junção interna ou externa à esquerda.</span><span class="sxs-lookup"><span data-stu-id="a06ef-113">The following illustration shows a conceptual view of two sets and the elements within those sets that are included in either an inner join or a left outer join.</span></span>  
  
 ![Dois círculos sobrepostos mostrando interna/externa.](./media/join-operations/join-method-overlapping-circles.png)  
  
## <a name="methods"></a><span data-ttu-id="a06ef-115">Métodos</span><span class="sxs-lookup"><span data-stu-id="a06ef-115">Methods</span></span>  
  
|<span data-ttu-id="a06ef-116">Nome do método</span><span class="sxs-lookup"><span data-stu-id="a06ef-116">Method Name</span></span>|<span data-ttu-id="a06ef-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="a06ef-117">Description</span></span>|<span data-ttu-id="a06ef-118">Sintaxe de expressão de consulta C#</span><span class="sxs-lookup"><span data-stu-id="a06ef-118">C# Query Expression Syntax</span></span>|<span data-ttu-id="a06ef-119">Mais informações</span><span class="sxs-lookup"><span data-stu-id="a06ef-119">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|Join|<span data-ttu-id="a06ef-120">Une duas sequências com base nas funções de seletor de chave e extrai pares de valores.</span><span class="sxs-lookup"><span data-stu-id="a06ef-120">Joins two sequences based on key selector functions and extracts pairs of values.</span></span>|`join … in … on … equals …`|<xref:System.Linq.Enumerable.Join%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Join%2A?displayProperty=nameWithType>|  
|GroupJoin|<span data-ttu-id="a06ef-121">Une duas sequências baseadas em funções de seletor de chave e agrupa as correspondências resultantes para cada elemento.</span><span class="sxs-lookup"><span data-stu-id="a06ef-121">Joins two sequences based on key selector functions and groups the resulting matches for each element.</span></span>|`join … in … on … equals … into …`|<xref:System.Linq.Enumerable.GroupJoin%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.GroupJoin%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="a06ef-122">Exemplos de sintaxe de expressão de consulta</span><span class="sxs-lookup"><span data-stu-id="a06ef-122">Query expression syntax examples</span></span>
  
### Join  
  
<span data-ttu-id="a06ef-123">O exemplo a `join … in … on … equals …` seguir usa a cláusula para juntar duas seqüências com base no valor específico:</span><span class="sxs-lookup"><span data-stu-id="a06ef-123">The following example uses the `join … in … on … equals …` clause to join two sequences based on specific value:</span></span>
  
[!code-csharp[Join](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csLINQJoinOperation/CS/JoinOperation.cs#Join)]  

### GroupJoin  

<span data-ttu-id="a06ef-124">O exemplo a `join … in … on … equals … into …` seguir usa a cláusula para juntar duas seqüências com base no valor específico e agrupa as correspondências resultantes para cada elemento:</span><span class="sxs-lookup"><span data-stu-id="a06ef-124">The following example uses the `join … in … on … equals … into …` clause to join two sequences based on specific value and groups the resulting matches for each element:</span></span>
  
[!code-csharp[GroupJoin](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csLINQJoinOperation/CS/JoinOperation.cs#GroupJoin)]  
  
## <a name="see-also"></a><span data-ttu-id="a06ef-125">Confira também</span><span class="sxs-lookup"><span data-stu-id="a06ef-125">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="a06ef-126">Visão geral de operadores de consulta padrão (C#)</span><span class="sxs-lookup"><span data-stu-id="a06ef-126">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="a06ef-127">Tipos Anônimos</span><span class="sxs-lookup"><span data-stu-id="a06ef-127">Anonymous Types</span></span>](../../classes-and-structs/anonymous-types.md)
- [<span data-ttu-id="a06ef-128">Formular junções e consultas entre produtos</span><span class="sxs-lookup"><span data-stu-id="a06ef-128">Formulate Joins and Cross-Product Queries</span></span>](../../../../framework/data/adonet/sql/linq/formulate-joins-and-cross-product-queries.md)
- [<span data-ttu-id="a06ef-129">aderir cláusula</span><span class="sxs-lookup"><span data-stu-id="a06ef-129">join clause</span></span>](../../../language-reference/keywords/join-clause.md)
- <span data-ttu-id="a06ef-130">[Joinusando chaves compostas](../../../linq/join-by-using-composite-keys.md)</span><span class="sxs-lookup"><span data-stu-id="a06ef-130">[Join by using composite keys](../../../linq/join-by-using-composite-keys.md)</span></span>
- [<span data-ttu-id="a06ef-131">Como juntar conteúdo de arquivos diferentes (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="a06ef-131">How to join content from dissimilar files (LINQ) (C#)</span></span>](./how-to-join-content-from-dissimilar-files-linq.md)
- [<span data-ttu-id="a06ef-132">Ordenar os resultados de uma cláusula join</span><span class="sxs-lookup"><span data-stu-id="a06ef-132">Order the results of a join clause</span></span>](../../../linq/order-the-results-of-a-join-clause.md)
- [<span data-ttu-id="a06ef-133">Executar operações de junção personalizadas</span><span class="sxs-lookup"><span data-stu-id="a06ef-133">Perform custom join operations</span></span>](../../../linq/perform-custom-join-operations.md)
- [<span data-ttu-id="a06ef-134">Executar junções agrupadas</span><span class="sxs-lookup"><span data-stu-id="a06ef-134">Perform grouped joins</span></span>](../../../linq/perform-grouped-joins.md)
- [<span data-ttu-id="a06ef-135">Executar junções internas</span><span class="sxs-lookup"><span data-stu-id="a06ef-135">Perform inner joins</span></span>](../../../linq/perform-inner-joins.md)
- [<span data-ttu-id="a06ef-136">Executar junções externas esquerdas</span><span class="sxs-lookup"><span data-stu-id="a06ef-136">Perform left outer joins</span></span>](../../../linq/perform-left-outer-joins.md)
- [<span data-ttu-id="a06ef-137">Como preencher coleções de objetos de várias fontes (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="a06ef-137">How to populate object collections from multiple sources (LINQ) (C#)</span></span>](./how-to-populate-object-collections-from-multiple-sources-linq.md)
