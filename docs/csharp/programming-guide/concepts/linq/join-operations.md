---
title: Operações de JoinC#()
ms.date: 07/20/2015
ms.assetid: 5105e0da-1267-4c00-837a-f0e9602279b8
no-loc:
- Join
- GroupJoin
ms.openlocfilehash: d4bf9fe76238d8824c5255df8910c1000503dcdf
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746964"
---
# <a name="opno-locjoin-operations-c"></a><span data-ttu-id="d7178-102">Operações de [!OP.NO-LOC(Join)]C#()</span><span class="sxs-lookup"><span data-stu-id="d7178-102">[!OP.NO-LOC(Join)] Operations (C#)</span></span>
<span data-ttu-id="d7178-103">Uma *junção* de duas fontes de dados é a associação de objetos em uma fonte de dados, com objetos que compartilham um atributo comum em outra fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="d7178-103">A *join* of two data sources is the association of objects in one data source with objects that share a common attribute in another data source.</span></span>  
  
 <span data-ttu-id="d7178-104">A junção é uma operação importante em consultas que têm como destino fontes de dados cujas relações entre si não podem ser seguidas diretamente.</span><span class="sxs-lookup"><span data-stu-id="d7178-104">Joining is an important operation in queries that target data sources whose relationships to each other cannot be followed directly.</span></span> <span data-ttu-id="d7178-105">Na programação orientada a objeto, isso pode significar uma correlação entre objetos que não são modelados, como a direção retroativa de uma relação unidirecional.</span><span class="sxs-lookup"><span data-stu-id="d7178-105">In object-oriented programming, this could mean a correlation between objects that is not modeled, such as the backwards direction of a one-way relationship.</span></span> <span data-ttu-id="d7178-106">Um exemplo de uma relação unidirecional é uma classe Cliente que tem uma propriedade do tipo Cidade, mas a classe Cidade ainda não tem uma propriedade que é uma coleção de objetos Cliente.</span><span class="sxs-lookup"><span data-stu-id="d7178-106">An example of a one-way relationship is a Customer class that has a property of type City, but the City class does not have a property that is a collection of Customer objects.</span></span> <span data-ttu-id="d7178-107">Se você tem uma lista de objetos Cidade e você quer encontrar todos os clientes em cada cidade, você pode usar uma operação de junção para encontrá-los.</span><span class="sxs-lookup"><span data-stu-id="d7178-107">If you have a list of City objects and you want to find all the customers in each city, you could use a join operation to find them.</span></span>  
  
 <span data-ttu-id="d7178-108">Os métodos de junção fornecidos na estrutura do LINQ são <xref:System.Linq.Enumerable.[!OP.NO-LOC(Join)]%2A> e <xref:System.Linq.Enumerable.[!OP.NO-LOC(GroupJoin)]%2A>.</span><span class="sxs-lookup"><span data-stu-id="d7178-108">The join methods provided in the LINQ framework are <xref:System.Linq.Enumerable.[!OP.NO-LOC(Join)]%2A> and <xref:System.Linq.Enumerable.[!OP.NO-LOC(GroupJoin)]%2A>.</span></span> <span data-ttu-id="d7178-109">Esses métodos executam junção por igualdade ou junções que correspondem duas fontes de dados com base na igualdade de suas chaves.</span><span class="sxs-lookup"><span data-stu-id="d7178-109">These methods perform equijoins, or joins that match two data sources based on equality of their keys.</span></span> <span data-ttu-id="d7178-110">(Para comparação, o Transact-SQL dá suporte a operadores de junção diferentes de ' Equals ', por exemplo, o operador ' less than '.) Em termos de banco de dados relacional, <xref:System.Linq.Enumerable.[!OP.NO-LOC(Join)]%2A> implementa uma junção interna, um tipo de junção em que somente os objetos que têm uma correspondência no outro conjunto de dado são retornados.</span><span class="sxs-lookup"><span data-stu-id="d7178-110">(For comparison, Transact-SQL supports join operators other than 'equals', for example the 'less than' operator.) In relational database terms, <xref:System.Linq.Enumerable.[!OP.NO-LOC(Join)]%2A> implements an inner join, a type of join in which only those objects that have a match in the other data set are returned.</span></span> <span data-ttu-id="d7178-111">O método <xref:System.Linq.Enumerable.[!OP.NO-LOC(GroupJoin)]%2A> não tem equivalente direto em termos de banco de dados relacional, mas ele implementa um superconjunto de junções internas e junções externas esquerdas.</span><span class="sxs-lookup"><span data-stu-id="d7178-111">The <xref:System.Linq.Enumerable.[!OP.NO-LOC(GroupJoin)]%2A> method has no direct equivalent in relational database terms, but it implements a superset of inner joins and left outer joins.</span></span> <span data-ttu-id="d7178-112">Uma junção externa esquerda é uma junção que retorna cada elemento da primeira (esquerda) fonte de dados, mesmo que ele não tenha elementos correlacionados na outra fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="d7178-112">A left outer join is a join that returns each element of the first (left) data source, even if it has no correlated elements in the other data source.</span></span>  
  
 <span data-ttu-id="d7178-113">A ilustração a seguir mostra uma visão conceitual de dois conjuntos e os elementos dentro desses conjuntos que estão incluídos em uma junção interna ou externa à esquerda.</span><span class="sxs-lookup"><span data-stu-id="d7178-113">The following illustration shows a conceptual view of two sets and the elements within those sets that are included in either an inner join or a left outer join.</span></span>  
  
 ![Dois círculos sobrepostos mostrando interna/externa.](./media/join-operations/join-method-overlapping-circles.png)  
  
## <a name="methods"></a><span data-ttu-id="d7178-115">{1&gt;Métodos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d7178-115">Methods</span></span>  
  
|<span data-ttu-id="d7178-116">Nome do método</span><span class="sxs-lookup"><span data-stu-id="d7178-116">Method Name</span></span>|<span data-ttu-id="d7178-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="d7178-117">Description</span></span>|<span data-ttu-id="d7178-118">Sintaxe de expressão de consulta C#</span><span class="sxs-lookup"><span data-stu-id="d7178-118">C# Query Expression Syntax</span></span>|<span data-ttu-id="d7178-119">Mais Informações</span><span class="sxs-lookup"><span data-stu-id="d7178-119">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|Join|<span data-ttu-id="d7178-120">Une duas sequências com base nas funções de seletor de chave e extrai pares de valores.</span><span class="sxs-lookup"><span data-stu-id="d7178-120">Joins two sequences based on key selector functions and extracts pairs of values.</span></span>|`join … in … on … equals …`|<xref:System.Linq.Enumerable.Join%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Join%2A?displayProperty=nameWithType>|  
|GroupJoin|<span data-ttu-id="d7178-121">Une duas sequências baseadas em funções de seletor de chave e agrupa as correspondências resultantes para cada elemento.</span><span class="sxs-lookup"><span data-stu-id="d7178-121">Joins two sequences based on key selector functions and groups the resulting matches for each element.</span></span>|`join … in … on … equals … into …`|<xref:System.Linq.Enumerable.GroupJoin%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.GroupJoin%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="d7178-122">Exemplos de sintaxe de expressão de consulta</span><span class="sxs-lookup"><span data-stu-id="d7178-122">Query expression syntax examples</span></span>
  
### Join  
  
<span data-ttu-id="d7178-123">O exemplo a seguir usa a cláusula `join … in … on … equals …` para unir duas sequências com base no valor específico:</span><span class="sxs-lookup"><span data-stu-id="d7178-123">The following example uses the `join … in … on … equals …` clause to join two sequences based on specific value:</span></span>
  
[!code-csharp[Join](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQJoin/CS/JoinOperation.cs#Join)]  

### GroupJoin  

<span data-ttu-id="d7178-124">O exemplo a seguir usa a cláusula `join … in … on … equals … into …` para unir duas sequências com base em um valor específico e agrupa as correspondências resultantes para cada elemento:</span><span class="sxs-lookup"><span data-stu-id="d7178-124">The following example uses the `join … in … on … equals … into …` clause to join two sequences based on specific value and groups the resulting matches for each element:</span></span>
  
[!code-csharp[GroupJoin](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQJoin/CS/JoinOperation.cs#GroupJoin)]  
  
## <a name="see-also"></a><span data-ttu-id="d7178-125">Veja também</span><span class="sxs-lookup"><span data-stu-id="d7178-125">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="d7178-126">Visão geral de operadores de consulta padrão (C#)</span><span class="sxs-lookup"><span data-stu-id="d7178-126">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="d7178-127">Tipos Anônimos</span><span class="sxs-lookup"><span data-stu-id="d7178-127">Anonymous Types</span></span>](../../classes-and-structs/anonymous-types.md)
- [<span data-ttu-id="d7178-128">Formular junções e consultas entre produtos</span><span class="sxs-lookup"><span data-stu-id="d7178-128">Formulate Joins and Cross-Product Queries</span></span>](../../../../framework/data/adonet/sql/linq/formulate-joins-and-cross-product-queries.md)
- [<span data-ttu-id="d7178-129">Cláusula join</span><span class="sxs-lookup"><span data-stu-id="d7178-129">join clause</span></span>](../../../language-reference/keywords/join-clause.md)
- <span data-ttu-id="d7178-130">[Join usando chaves compostas](../../../linq/join-by-using-composite-keys.md)</span><span class="sxs-lookup"><span data-stu-id="d7178-130">[Join by using composite keys](../../../linq/join-by-using-composite-keys.md)</span></span>
- [<span data-ttu-id="d7178-131">Como unir conteúdo de arquivos diferentes (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="d7178-131">How to join content from dissimilar files (LINQ) (C#)</span></span>](./how-to-join-content-from-dissimilar-files-linq.md)
- [<span data-ttu-id="d7178-132">Ordenar os resultados de uma cláusula join</span><span class="sxs-lookup"><span data-stu-id="d7178-132">Order the results of a join clause</span></span>](../../../linq/order-the-results-of-a-join-clause.md)
- [<span data-ttu-id="d7178-133">Executar operações de junção personalizadas</span><span class="sxs-lookup"><span data-stu-id="d7178-133">Perform custom join operations</span></span>](../../../linq/perform-custom-join-operations.md)
- [<span data-ttu-id="d7178-134">Executar junções agrupadas</span><span class="sxs-lookup"><span data-stu-id="d7178-134">Perform grouped joins</span></span>](../../../linq/perform-grouped-joins.md)
- [<span data-ttu-id="d7178-135">Executar junções internas</span><span class="sxs-lookup"><span data-stu-id="d7178-135">Perform inner joins</span></span>](../../../linq/perform-inner-joins.md)
- [<span data-ttu-id="d7178-136">Executar junções externas esquerdas</span><span class="sxs-lookup"><span data-stu-id="d7178-136">Perform left outer joins</span></span>](../../../linq/perform-left-outer-joins.md)
- [<span data-ttu-id="d7178-137">Como preencher coleções de objetos de várias fontes (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="d7178-137">How to populate object collections from multiple sources (LINQ) (C#)</span></span>](./how-to-populate-object-collections-from-multiple-sources-linq.md)
