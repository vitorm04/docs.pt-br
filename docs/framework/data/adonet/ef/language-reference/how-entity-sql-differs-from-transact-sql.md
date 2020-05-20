---
title: Como o Entity SQL difere do Transact-SQL
ms.date: 03/30/2017
ms.assetid: 9c9ee36d-f294-4c8b-a196-f0114c94f559
ms.openlocfilehash: 96e2283074b6c69e51bb7fee4d4f257cdb58d615
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615625"
---
# <a name="how-entity-sql-differs-from-transact-sql"></a><span data-ttu-id="eb416-102">Como Entity SQL difere do Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="eb416-102">How Entity SQL differs from Transact-SQL</span></span>

<span data-ttu-id="eb416-103">Este artigo descreve as diferenças entre o Entity SQL e o Transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="eb416-103">This article describes the differences between Entity SQL and Transact-SQL.</span></span>  
  
## <a name="inheritance-and-relationships-support"></a><span data-ttu-id="eb416-104">Suporte a herança e relações</span><span class="sxs-lookup"><span data-stu-id="eb416-104">Inheritance and Relationships Support</span></span>  
 <span data-ttu-id="eb416-105">Entity SQL trabalha diretamente com esquemas de entidade conceitual e dá suporte a recursos de modelo conceitual, como herança e relações.</span><span class="sxs-lookup"><span data-stu-id="eb416-105">Entity SQL works directly with conceptual entity schemas and supports conceptual model features such as inheritance and relationships.</span></span>  
  
 <span data-ttu-id="eb416-106">Ao trabalhar com herança, geralmente é útil selecionar instâncias de um subtipo de uma coleção de instâncias de supertipo.</span><span class="sxs-lookup"><span data-stu-id="eb416-106">When working with inheritance, it is often useful to select instances of a subtype from a collection of supertype instances.</span></span> <span data-ttu-id="eb416-107">O operador [OfType](oftype-entity-sql.md) no Entity SQL (semelhante a `oftype` em sequências C#) fornece esse recurso.</span><span class="sxs-lookup"><span data-stu-id="eb416-107">The [oftype](oftype-entity-sql.md) operator in Entity SQL (similar to `oftype` in C# Sequences) provides this capability.</span></span>  
  
## <a name="support-for-collections"></a><span data-ttu-id="eb416-108">Suporte para coleções</span><span class="sxs-lookup"><span data-stu-id="eb416-108">Support for Collections</span></span>  
 <span data-ttu-id="eb416-109">Entity SQL trata as coleções como entidades de primeira classe.</span><span class="sxs-lookup"><span data-stu-id="eb416-109">Entity SQL treats collections as first-class entities.</span></span> <span data-ttu-id="eb416-110">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="eb416-110">For example:</span></span>  
  
- <span data-ttu-id="eb416-111">As expressões de coleção são válidas em uma cláusula `from`.</span><span class="sxs-lookup"><span data-stu-id="eb416-111">Collection expressions are valid in a `from` clause.</span></span>  
  
- <span data-ttu-id="eb416-112">As subconsultas `in` e `exists` foram generalizadas para permitir quaisquer coleções.</span><span class="sxs-lookup"><span data-stu-id="eb416-112">`in` and `exists` subqueries have been generalized to allow any collections.</span></span>  
  
     <span data-ttu-id="eb416-113">Um subconsulta é um tipo de coleção.</span><span class="sxs-lookup"><span data-stu-id="eb416-113">A subquery is one kind of collection.</span></span> <span data-ttu-id="eb416-114">`e1 in e2`e `exists(e)` são as construções de Entity SQL para executar essas operações.</span><span class="sxs-lookup"><span data-stu-id="eb416-114">`e1 in e2` and `exists(e)` are the Entity SQL constructs to perform these operations.</span></span>  
  
- <span data-ttu-id="eb416-115">A operações de conjunto, como `union`, `intersect` e `except`, agora funcionam em coleções.</span><span class="sxs-lookup"><span data-stu-id="eb416-115">Set operations, such as `union`, `intersect`, and `except`, now operate on collections.</span></span>  
  
- <span data-ttu-id="eb416-116">As junções funcionam em coleções.</span><span class="sxs-lookup"><span data-stu-id="eb416-116">Joins operate on collections.</span></span>  
  
## <a name="support-for-expressions"></a><span data-ttu-id="eb416-117">Suporte para expressões</span><span class="sxs-lookup"><span data-stu-id="eb416-117">Support for Expressions</span></span>  
 <span data-ttu-id="eb416-118">O Transact-SQL tem subconsultas (tabelas) e expressões (linhas e colunas).</span><span class="sxs-lookup"><span data-stu-id="eb416-118">Transact-SQL has subqueries (tables) and expressions (rows and columns).</span></span>  
  
 <span data-ttu-id="eb416-119">Para dar suporte a coleções e coleções aninhadas, Entity SQL faz tudo uma expressão.</span><span class="sxs-lookup"><span data-stu-id="eb416-119">To support collections and nested collections, Entity SQL makes everything an expression.</span></span> <span data-ttu-id="eb416-120">Entity SQL é mais combinável do que o Transact-SQL – cada expressão pode ser usada em qualquer lugar.</span><span class="sxs-lookup"><span data-stu-id="eb416-120">Entity SQL is more composable than Transact-SQL—every expression can be used anywhere.</span></span> <span data-ttu-id="eb416-121">As expressões de consulta sempre resultam em coleções dos tipos projetados e podem ser usadas em qualquer lugar em que uma expressão de coleção seja permitida.</span><span class="sxs-lookup"><span data-stu-id="eb416-121">Query expressions always result in collections of the projected types and can be used anywhere a collection expression is allowed.</span></span> <span data-ttu-id="eb416-122">Para obter informações sobre expressões Transact-SQL que não têm suporte no Entity SQL, consulte [expressões sem suporte](unsupported-expressions-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="eb416-122">For information about Transact-SQL expressions that are not supported in Entity SQL, see [Unsupported Expressions](unsupported-expressions-entity-sql.md).</span></span>  
  
 <span data-ttu-id="eb416-123">A seguir estão todas as consultas de Entity SQL válidas:</span><span class="sxs-lookup"><span data-stu-id="eb416-123">The following are all valid Entity SQL queries:</span></span>  
  
```sql  
1+2 *3  
"abc"  
row(1 as a, 2 as b)  
{ 1, 3, 5}
e1 union all e2  
set(e1)  
```  
  
## <a name="uniform-treatment-of-subqueries"></a><span data-ttu-id="eb416-124">Tratamento uniforme de subconsultas</span><span class="sxs-lookup"><span data-stu-id="eb416-124">Uniform Treatment of Subqueries</span></span>  
 <span data-ttu-id="eb416-125">Considerando sua ênfase em tabelas, o Transact-SQL executa a interpretação contextual de subconsultas.</span><span class="sxs-lookup"><span data-stu-id="eb416-125">Given its emphasis on tables, Transact-SQL performs contextual interpretation of subqueries.</span></span> <span data-ttu-id="eb416-126">Por exemplo, uma subconsulta na `from` cláusula é considerada uma multiconjunto (tabela).</span><span class="sxs-lookup"><span data-stu-id="eb416-126">For example, a subquery in the `from` clause is considered to be a multiset (table).</span></span> <span data-ttu-id="eb416-127">Mas a mesma subconsulta usada na cláusula `select` é considerada uma subconsulta escalar.</span><span class="sxs-lookup"><span data-stu-id="eb416-127">But the same subquery used in the `select` clause is considered to be a scalar subquery.</span></span> <span data-ttu-id="eb416-128">Da mesma forma, uma subconsulta usada no lado esquerdo de um `in` operador é considerada uma subconsulta escalar, enquanto o lado direito deve ser uma subconsulta multiconjunto.</span><span class="sxs-lookup"><span data-stu-id="eb416-128">Similarly, a subquery used on the left side of an `in` operator is considered to be a scalar subquery, while the right side is expected to be a multiset subquery.</span></span>  
  
 <span data-ttu-id="eb416-129">Entity SQL elimina essas diferenças.</span><span class="sxs-lookup"><span data-stu-id="eb416-129">Entity SQL eliminates these differences.</span></span> <span data-ttu-id="eb416-130">Uma expressão tem uma interpretação uniforme que não depende do contexto no qual é usada.</span><span class="sxs-lookup"><span data-stu-id="eb416-130">An expression has a uniform interpretation that does not depend on the context in which it is used.</span></span> <span data-ttu-id="eb416-131">Entity SQL considera que todas as subconsultas sejam subconsultas multiconjunto.</span><span class="sxs-lookup"><span data-stu-id="eb416-131">Entity SQL considers all subqueries to be multiset subqueries.</span></span> <span data-ttu-id="eb416-132">Se um valor escalar for desejado da subconsulta, Entity SQL fornecerá o `anyelement` operador que opera em uma coleção (nesse caso, a subconsulta) e extrairá um valor singleton da coleção.</span><span class="sxs-lookup"><span data-stu-id="eb416-132">If a scalar value is desired from the subquery, Entity SQL provides the `anyelement` operator that operates on a collection (in this case, the subquery), and extracts a singleton value from the collection.</span></span>  
  
### <a name="avoiding-implicit-coercions-for-subqueries"></a><span data-ttu-id="eb416-133">Evitando coerções implícitas para subconsultas</span><span class="sxs-lookup"><span data-stu-id="eb416-133">Avoiding Implicit Coercions for Subqueries</span></span>  
 <span data-ttu-id="eb416-134">Um efeito colateral relacionado ao tratamento uniforme de subconsultas é a conversão implícita de subconsultas em valores escalares.</span><span class="sxs-lookup"><span data-stu-id="eb416-134">A related side effect of uniform treatment of subqueries is implicit conversion of subqueries to scalar values.</span></span> <span data-ttu-id="eb416-135">Especificamente, no Transact-SQL, um multiconjunto de linhas (com um único campo) é implicitamente convertido em um valor escalar cujo tipo de dados é o do campo.</span><span class="sxs-lookup"><span data-stu-id="eb416-135">Specifically, in Transact-SQL, a multiset of rows (with a single field) is implicitly converted into a scalar value whose data type is that of the field.</span></span>  
  
 <span data-ttu-id="eb416-136">Entity SQL não dá suporte a essa coerção implícita.</span><span class="sxs-lookup"><span data-stu-id="eb416-136">Entity SQL does not support this implicit coercion.</span></span> <span data-ttu-id="eb416-137">Entity SQL fornece o `ANYELEMENT` operador para extrair um valor singleton de uma coleção e uma `select value` cláusula para evitar a criação de um wrapper de linha durante uma expressão de consulta.</span><span class="sxs-lookup"><span data-stu-id="eb416-137">Entity SQL provides the `ANYELEMENT` operator to extract a singleton value from a collection, and a `select value` clause to avoid creating a row-wrapper during a query expression.</span></span>  
  
## <a name="select-value-avoiding-the-implicit-row-wrapper"></a><span data-ttu-id="eb416-138">Select Value: evitando o wrapper de linha implícito</span><span class="sxs-lookup"><span data-stu-id="eb416-138">Select Value: Avoiding the Implicit Row Wrapper</span></span>  
 <span data-ttu-id="eb416-139">A cláusula SELECT em uma subconsulta Transact-SQL cria implicitamente um wrapper de linha em volta dos itens na cláusula.</span><span class="sxs-lookup"><span data-stu-id="eb416-139">The select clause in a Transact-SQL subquery implicitly creates a row wrapper around the items in the clause.</span></span> <span data-ttu-id="eb416-140">Isso indica que não podemos criar coleções de escalares ou objetos.</span><span class="sxs-lookup"><span data-stu-id="eb416-140">This implies that we cannot create collections of scalars or objects.</span></span> <span data-ttu-id="eb416-141">O Transact-SQL permite uma coerção implícita entre um `rowtype` com um campo e um valor singleton do mesmo tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="eb416-141">Transact-SQL allows an implicit coercion between a `rowtype` with one field and a singleton value of the same data type.</span></span>  
  
 <span data-ttu-id="eb416-142">Entity SQL fornece a `select value` cláusula para ignorar a construção de linha implícita.</span><span class="sxs-lookup"><span data-stu-id="eb416-142">Entity SQL provides the `select value` clause to skip the implicit row construction.</span></span> <span data-ttu-id="eb416-143">Somente um item pode ser especificado em uma cláusula `select value`.</span><span class="sxs-lookup"><span data-stu-id="eb416-143">Only one item may be specified in a `select value` clause.</span></span> <span data-ttu-id="eb416-144">Quando tal cláusula é usada, nenhum wrapper de linha é construído em volta dos itens na `select` cláusula, e uma coleção da forma desejada pode ser produzida, por exemplo, `select value a` .</span><span class="sxs-lookup"><span data-stu-id="eb416-144">When such a clause is used, no row wrapper is constructed around the items in the `select` clause, and a collection of the desired shape may be produced, for example, `select value a`.</span></span>  
  
 <span data-ttu-id="eb416-145">Entity SQL também fornece o Construtor Row para construir linhas arbitrárias.</span><span class="sxs-lookup"><span data-stu-id="eb416-145">Entity SQL also provides the row constructor to construct arbitrary rows.</span></span> <span data-ttu-id="eb416-146">`select`usa um ou mais elementos na projeção e resulta em um registro de dados com campos:</span><span class="sxs-lookup"><span data-stu-id="eb416-146">`select` takes one or more elements in the projection and results in a data record with fields:</span></span>  
  
 `select a, b, c`  
  
## <a name="left-correlation-and-aliasing"></a><span data-ttu-id="eb416-147">Correlação à esquerda e aliases</span><span class="sxs-lookup"><span data-stu-id="eb416-147">Left Correlation and Aliasing</span></span>  
 <span data-ttu-id="eb416-148">No Transact-SQL, as expressões em um determinado escopo (uma única cláusula como `select` ou `from` ) não podem referenciar expressões definidas anteriormente no mesmo escopo.</span><span class="sxs-lookup"><span data-stu-id="eb416-148">In Transact-SQL, expressions in a given scope (a single clause like `select` or `from`) cannot reference expressions defined earlier in the same scope.</span></span> <span data-ttu-id="eb416-149">Alguns dialetos do SQL (incluindo Transact-SQL) dão suporte a formas limitadas deles na `from` cláusula.</span><span class="sxs-lookup"><span data-stu-id="eb416-149">Some dialects of SQL (including Transact-SQL) do support limited forms of these in the `from` clause.</span></span>  
  
 <span data-ttu-id="eb416-150">Entity SQL generaliza correlações à esquerda na `from` cláusula e as trata uniformemente.</span><span class="sxs-lookup"><span data-stu-id="eb416-150">Entity SQL generalizes left correlations in the `from` clause, and treats them uniformly.</span></span> <span data-ttu-id="eb416-151">As expressões na cláusula `from` podem referenciar as definições anteriores (definições à esquerda) na mesma cláusula sem a necessidade de sintaxe adicional.</span><span class="sxs-lookup"><span data-stu-id="eb416-151">Expressions in the `from` clause can reference earlier definitions (definitions to the left) in the same clause without the need for additional syntax.</span></span>  
  
 <span data-ttu-id="eb416-152">Entity SQL também impõe restrições adicionais em consultas que envolvem `group by` cláusulas.</span><span class="sxs-lookup"><span data-stu-id="eb416-152">Entity SQL also imposes additional restrictions on queries involving `group by` clauses.</span></span> <span data-ttu-id="eb416-153">As expressões na `select` cláusula and `having` da cláusula dessas consultas só podem fazer referência às `group by` chaves por meio de seus aliases.</span><span class="sxs-lookup"><span data-stu-id="eb416-153">Expressions in the `select` clause and `having` clause of such queries may only refer to the `group by` keys via their aliases.</span></span> <span data-ttu-id="eb416-154">A construção a seguir é válida no Transact-SQL, mas não está no Entity SQL:</span><span class="sxs-lookup"><span data-stu-id="eb416-154">The following construct is valid in Transact-SQL but are not in Entity SQL:</span></span>  
  
```sql  
SELECT t.x + t.y FROM T AS t group BY t.x + t.y
```  
  
 <span data-ttu-id="eb416-155">Para fazer isso no Entity SQL:</span><span class="sxs-lookup"><span data-stu-id="eb416-155">To do this in Entity SQL:</span></span>  
  
```sql  
SELET k FROM T AS t GROUP BY (t.x + t.y) AS k
```  
  
## <a name="referencing-columns-properties-of-tables-collections"></a><span data-ttu-id="eb416-156">Referenciando colunas (propriedades) de tabelas (coleções)</span><span class="sxs-lookup"><span data-stu-id="eb416-156">Referencing Columns (Properties) of Tables (Collections)</span></span>  
 <span data-ttu-id="eb416-157">Todas as referências de coluna no Entity SQL devem ser qualificadas com o alias da tabela.</span><span class="sxs-lookup"><span data-stu-id="eb416-157">All column references in Entity SQL must be qualified with the table alias.</span></span> <span data-ttu-id="eb416-158">A construção a seguir (supondo que `a` seja uma coluna de tabela válida `T` ) é válida no TRANSACT-SQL, mas não no Entity SQL.</span><span class="sxs-lookup"><span data-stu-id="eb416-158">The following construct (assuming that `a` is a valid column of table `T`) is valid in Transact-SQL but not in Entity SQL.</span></span>  
  
```sql  
SELECT a FROM T
```  
  
 <span data-ttu-id="eb416-159">O formulário de Entity SQL é</span><span class="sxs-lookup"><span data-stu-id="eb416-159">The Entity SQL form is</span></span>  
  
```sql  
SELECT t.a AS A FROM T AS t
```  
  
 <span data-ttu-id="eb416-160">Os aliases de tabela são opcionais na cláusula `from`.</span><span class="sxs-lookup"><span data-stu-id="eb416-160">The table aliases are optional in the `from` clause.</span></span> <span data-ttu-id="eb416-161">O nome da tabela é usado como o alias implícito.</span><span class="sxs-lookup"><span data-stu-id="eb416-161">The name of the table is used as the implicit alias.</span></span> <span data-ttu-id="eb416-162">Entity SQL também permite o seguinte formato:</span><span class="sxs-lookup"><span data-stu-id="eb416-162">Entity SQL allows the following form as well:</span></span>  
  
```sql  
SELET Tab.a FROM Tab
```  
  
## <a name="navigation-through-objects"></a><span data-ttu-id="eb416-163">Navegação por objetos</span><span class="sxs-lookup"><span data-stu-id="eb416-163">Navigation Through Objects</span></span>  
 <span data-ttu-id="eb416-164">O Transact-SQL usa a notação "." para fazer referência a colunas de (uma linha de) uma tabela.</span><span class="sxs-lookup"><span data-stu-id="eb416-164">Transact-SQL uses the "." notation for referencing columns of (a row of) a table.</span></span> <span data-ttu-id="eb416-165">Entity SQL estende essa notação (emprestada de linguagens de programação) para dar suporte à navegação por meio de propriedades de um objeto.</span><span class="sxs-lookup"><span data-stu-id="eb416-165">Entity SQL extends this notation (borrowed from programming languages) to support navigation through properties of an object.</span></span>  
  
 <span data-ttu-id="eb416-166">Por exemplo, se `p` for uma expressão do tipo Person, a seguinte será a sintaxe Entity SQL para referenciar a cidade do endereço dessa pessoa.</span><span class="sxs-lookup"><span data-stu-id="eb416-166">For example, if `p` is an expression of type Person, the following is the Entity SQL syntax for referencing the city of the address of this person.</span></span>  
  
```sql  
p.Address.City
```  
  
## <a name="no-support-for-"></a><span data-ttu-id="eb416-167">Não há suporte para\*</span><span class="sxs-lookup"><span data-stu-id="eb416-167">No Support for \*</span></span>  
 <span data-ttu-id="eb416-168">O Transact-SQL dá suporte à sintaxe não qualificada \* como um alias para toda a linha e a sintaxe qualificada \* (t. \* ) como um atalho para os campos dessa tabela.</span><span class="sxs-lookup"><span data-stu-id="eb416-168">Transact-SQL supports the unqualified \* syntax as an alias for the entire row, and the qualified \* syntax (t.\*) as a shortcut for the fields of that table.</span></span> <span data-ttu-id="eb416-169">Além disso, o Transact-SQL permite uma agregação de contagem especial ( \* ), que inclui nulos.</span><span class="sxs-lookup"><span data-stu-id="eb416-169">In addition, Transact-SQL allows for a special count(\*) aggregate, which includes nulls.</span></span>  
  
 <span data-ttu-id="eb416-170">Entity SQL não dá suporte à construção \*.</span><span class="sxs-lookup"><span data-stu-id="eb416-170">Entity SQL does not support the \* construct.</span></span> <span data-ttu-id="eb416-171">Consultas Transact-SQL do formulário `select * from T` e `select T1.* from T1, T2...` podem ser expressas em Entity SQL como `select value t from T as t` e `select value t1 from T1 as t1, T2 as t2...` , respectivamente.</span><span class="sxs-lookup"><span data-stu-id="eb416-171">Transact-SQL queries of the form `select * from T` and `select T1.* from T1, T2...` can be expressed in Entity SQL as `select value t from T as t` and `select value t1 from T1 as t1, T2 as t2...`, respectively.</span></span> <span data-ttu-id="eb416-172">Além disso, essas construções manipulam a herança (substituibilidade do valor), embora as variantes `select *` sejam restritas a propriedades de nível superior do tipo declarado.</span><span class="sxs-lookup"><span data-stu-id="eb416-172">Additionally, these constructs handle inheritance (value substitutability), while the `select *` variants are restricted to top-level properties of the declared type.</span></span>  
  
 <span data-ttu-id="eb416-173">Entity SQL não oferece suporte à `count(*)` agregação.</span><span class="sxs-lookup"><span data-stu-id="eb416-173">Entity SQL does not support the `count(*)` aggregate.</span></span> <span data-ttu-id="eb416-174">Use `count(0)` em vez disso.</span><span class="sxs-lookup"><span data-stu-id="eb416-174">Use `count(0)` instead.</span></span>  
  
## <a name="changes-to-group-by"></a><span data-ttu-id="eb416-175">Alterações em group by</span><span class="sxs-lookup"><span data-stu-id="eb416-175">Changes to Group By</span></span>  
 <span data-ttu-id="eb416-176">Entity SQL dá suporte a alias de `group by` chaves.</span><span class="sxs-lookup"><span data-stu-id="eb416-176">Entity SQL supports aliasing of `group by` keys.</span></span> <span data-ttu-id="eb416-177">As expressões na `select` cláusula e `having` cláusula devem se referir às `group by` chaves por meio desses aliases.</span><span class="sxs-lookup"><span data-stu-id="eb416-177">Expressions in the `select` clause and `having` clause must refer to the `group by` keys via these aliases.</span></span> <span data-ttu-id="eb416-178">Por exemplo, essa Entity SQL sintaxe:</span><span class="sxs-lookup"><span data-stu-id="eb416-178">For example, this Entity SQL syntax:</span></span>  
  
```sql  
SELECT k1, count(t.a), sum(t.a)
FROM T AS t
GROUP BY t.b + t.c AS k1
```  
  
 <span data-ttu-id="eb416-179">... é equivalente ao Transact-SQL a seguir:</span><span class="sxs-lookup"><span data-stu-id="eb416-179">...is equivalent to the following Transact-SQL:</span></span>  
  
```sql  
SELECT b + c, count(*), sum(a)
FROM T
GROUP BY b + c
```  
  
## <a name="collection-based-aggregates"></a><span data-ttu-id="eb416-180">Agregações baseadas em coleção</span><span class="sxs-lookup"><span data-stu-id="eb416-180">Collection-Based Aggregates</span></span>  
 <span data-ttu-id="eb416-181">Entity SQL dá suporte a dois tipos de agregações.</span><span class="sxs-lookup"><span data-stu-id="eb416-181">Entity SQL supports two kinds of aggregates.</span></span>  
  
 <span data-ttu-id="eb416-182">As agregações baseadas em coleção operam em coleções e geram o resultado agregado.</span><span class="sxs-lookup"><span data-stu-id="eb416-182">Collection-based aggregates operate on collections and produce the aggregated result.</span></span> <span data-ttu-id="eb416-183">Elas podem aparecer em qualquer lugar na consulta, e não requerem uma cláusula `group by`.</span><span class="sxs-lookup"><span data-stu-id="eb416-183">These can appear anywhere in the query, and do not require a `group by` clause.</span></span> <span data-ttu-id="eb416-184">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="eb416-184">For example:</span></span>  
  
```sql  
SELECT t.a AS a, count({1,2,3}) AS b FROM T AS t
```  
  
 <span data-ttu-id="eb416-185">O Entity SQL também dá suporte a agregações de estilo SQL.</span><span class="sxs-lookup"><span data-stu-id="eb416-185">Entity SQL also supports SQL-style aggregates.</span></span> <span data-ttu-id="eb416-186">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="eb416-186">For example:</span></span>  
  
```sql  
SELECT a, sum(t.b) FROM T AS t GROUP BY t.a AS a
```  
  
## <a name="order-by-clause-usage"></a><span data-ttu-id="eb416-187">Uso da cláusula ORDER BY</span><span class="sxs-lookup"><span data-stu-id="eb416-187">ORDER BY Clause Usage</span></span>  
<span data-ttu-id="eb416-188">O Transact-SQL permite que as `ORDER BY` cláusulas sejam especificadas somente no bloco de nível superior `SELECT .. FROM .. WHERE` .</span><span class="sxs-lookup"><span data-stu-id="eb416-188">Transact-SQL allows `ORDER BY` clauses to be specified only in the topmost `SELECT .. FROM .. WHERE` block.</span></span> <span data-ttu-id="eb416-189">No Entity SQL, você pode usar uma expressão aninhada `ORDER BY` e ela pode ser colocada em qualquer lugar na consulta, mas a ordenação em uma consulta aninhada não é preservada.</span><span class="sxs-lookup"><span data-stu-id="eb416-189">In Entity SQL, you can use a nested `ORDER BY` expression and it can be placed anywhere in the query, but ordering in a nested query is not preserved.</span></span>  
  
```sql  
-- The following query will order the results by the last name  
SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact AS C1
        ORDER BY C1.LastName  
```  
  
```sql  
-- In the following query ordering of the nested query is ignored.  
SELECT C2.FirstName, C2.LastName  
    FROM (SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName) as C2  
```  
  
## <a name="identifiers"></a><span data-ttu-id="eb416-190">Identificadores</span><span class="sxs-lookup"><span data-stu-id="eb416-190">Identifiers</span></span>  
 <span data-ttu-id="eb416-191">No Transact-SQL, a comparação de identificador é baseada no agrupamento do banco de dados atual.</span><span class="sxs-lookup"><span data-stu-id="eb416-191">In Transact-SQL, identifier comparison is based on the collation of the current database.</span></span> <span data-ttu-id="eb416-192">No Entity SQL, os identificadores sempre diferenciam maiúsculas de minúsculas e diferenciam acentos (ou seja, Entity SQL diferencia caracteres acentuados e não acentuados; por exemplo, ' a ' não é igual a ' ã ').</span><span class="sxs-lookup"><span data-stu-id="eb416-192">In Entity SQL, identifiers are always case insensitive and accent sensitive (that is, Entity SQL distinguishes between accented and unaccented characters; for example, 'a' is not equal to 'ấ').</span></span> <span data-ttu-id="eb416-193">Entity SQL trata versões de letras que aparecem da mesma forma, mas são de páginas de código diferentes como caracteres diferentes.</span><span class="sxs-lookup"><span data-stu-id="eb416-193">Entity SQL treats versions of letters that appear the same but are from different code pages as different characters.</span></span> <span data-ttu-id="eb416-194">Para obter mais informações, consulte [conjunto de caracteres de entrada](input-character-set-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="eb416-194">For more information, see [Input Character Set](input-character-set-entity-sql.md).</span></span>  
  
## <a name="transact-sql-functionality-not-available-in-entity-sql"></a><span data-ttu-id="eb416-195">Funcionalidade Transact-SQL não disponível em Entity SQL</span><span class="sxs-lookup"><span data-stu-id="eb416-195">Transact-SQL Functionality Not Available in Entity SQL</span></span>  
 <span data-ttu-id="eb416-196">A seguinte funcionalidade Transact-SQL não está disponível no Entity SQL.</span><span class="sxs-lookup"><span data-stu-id="eb416-196">The following Transact-SQL functionality is not available in Entity SQL.</span></span>  
  
 <span data-ttu-id="eb416-197">DML</span><span class="sxs-lookup"><span data-stu-id="eb416-197">DML</span></span>  
 <span data-ttu-id="eb416-198">Atualmente, Entity SQL não fornece suporte para instruções DML (INSERT, Update e Delete).</span><span class="sxs-lookup"><span data-stu-id="eb416-198">Entity SQL currently provides no support for DML statements (insert, update, delete).</span></span>  
  
 <span data-ttu-id="eb416-199">DDL</span><span class="sxs-lookup"><span data-stu-id="eb416-199">DDL</span></span>  
 <span data-ttu-id="eb416-200">O Entity SQL não fornece suporte para DDL na versão atual.</span><span class="sxs-lookup"><span data-stu-id="eb416-200">Entity SQL provides no support for DDL in the current version.</span></span>  
  
 <span data-ttu-id="eb416-201">Programação imperativa</span><span class="sxs-lookup"><span data-stu-id="eb416-201">Imperative Programming</span></span>  
 <span data-ttu-id="eb416-202">O Entity SQL não fornece suporte para programação imperativa, ao contrário do Transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="eb416-202">Entity SQL provides no support for imperative programming, unlike Transact-SQL.</span></span> <span data-ttu-id="eb416-203">Use, em vez disso, uma linguagem de programação.</span><span class="sxs-lookup"><span data-stu-id="eb416-203">Use a programming language instead.</span></span>  
  
 <span data-ttu-id="eb416-204">Funções de agrupamento</span><span class="sxs-lookup"><span data-stu-id="eb416-204">Grouping Functions</span></span>  
 <span data-ttu-id="eb416-205">Entity SQL ainda não fornece suporte para agrupar funções (por exemplo, CUBE, ROLLUP e GROUPING_SET).</span><span class="sxs-lookup"><span data-stu-id="eb416-205">Entity SQL does not yet provide support for grouping functions (for example, CUBE, ROLLUP, and GROUPING_SET).</span></span>  
  
 <span data-ttu-id="eb416-206">Funções Analíticas</span><span class="sxs-lookup"><span data-stu-id="eb416-206">Analytic Functions</span></span>  
 <span data-ttu-id="eb416-207">O Entity SQL ainda não fornece suporte para funções analíticas.</span><span class="sxs-lookup"><span data-stu-id="eb416-207">Entity SQL does not (yet) provide support for analytic functions.</span></span>  
  
 <span data-ttu-id="eb416-208">Funções internas, operadores</span><span class="sxs-lookup"><span data-stu-id="eb416-208">Built-in Functions, Operators</span></span>  
 <span data-ttu-id="eb416-209">O Entity SQL dá suporte a um subconjunto de funções e operadores internos do Transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="eb416-209">Entity SQL supports a subset of Transact-SQL's built in functions and operators.</span></span> <span data-ttu-id="eb416-210">Esses operadores e funções provavelmente têm suporte com os principais provedores de repositório.</span><span class="sxs-lookup"><span data-stu-id="eb416-210">These operators and functions are likely to be supported by the major store providers.</span></span> <span data-ttu-id="eb416-211">Entity SQL usa funções específicas do repositório declaradas em um manifesto do provedor.</span><span class="sxs-lookup"><span data-stu-id="eb416-211">Entity SQL uses the store-specific functions declared in a provider manifest.</span></span> <span data-ttu-id="eb416-212">Além disso, o Entity Framework permite que você declare funções de armazenamento existentes internas e definidas pelo usuário, para Entity SQL usar.</span><span class="sxs-lookup"><span data-stu-id="eb416-212">Additionally, the Entity Framework allows you to declare built-in and user-defined existing store functions, for Entity SQL to use.</span></span>  
  
 <span data-ttu-id="eb416-213">Dicas</span><span class="sxs-lookup"><span data-stu-id="eb416-213">Hints</span></span>  
 <span data-ttu-id="eb416-214">Entity SQL não fornece mecanismos para dicas de consulta.</span><span class="sxs-lookup"><span data-stu-id="eb416-214">Entity SQL does not provide mechanisms for query hints.</span></span>  
  
 <span data-ttu-id="eb416-215">Processando resultados de consulta em lotes</span><span class="sxs-lookup"><span data-stu-id="eb416-215">Batching Query Results</span></span>  
 <span data-ttu-id="eb416-216">Entity SQL não dá suporte a resultados de consulta em lote.</span><span class="sxs-lookup"><span data-stu-id="eb416-216">Entity SQL does not support batching query results.</span></span> <span data-ttu-id="eb416-217">Por exemplo, o seguinte é um Transact-SQL válido (envio como um lote):</span><span class="sxs-lookup"><span data-stu-id="eb416-217">For example, the following is valid Transact-SQL (sending as a batch):</span></span>  
  
```sql  
SELECT * FROM products;
SELECT * FROM catagories;
```  
  
 <span data-ttu-id="eb416-218">No entanto, não há suporte para o Entity SQL equivalente:</span><span class="sxs-lookup"><span data-stu-id="eb416-218">However, the equivalent Entity SQL is not supported:</span></span>  
  
```sql  
SELECT value p FROM Products AS p;
SELECT value c FROM Categories AS c;
```  
  
 <span data-ttu-id="eb416-219">Entity SQL só dá suporte a uma instrução de consulta de produção de resultado por comando.</span><span class="sxs-lookup"><span data-stu-id="eb416-219">Entity SQL only supports one result-producing query statement per command.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb416-220">Confira também</span><span class="sxs-lookup"><span data-stu-id="eb416-220">See also</span></span>

- [<span data-ttu-id="eb416-221">Visão geral da Entity SQL</span><span class="sxs-lookup"><span data-stu-id="eb416-221">Entity SQL Overview</span></span>](entity-sql-overview.md)
- [<span data-ttu-id="eb416-222">Expressões sem suporte</span><span class="sxs-lookup"><span data-stu-id="eb416-222">Unsupported Expressions</span></span>](unsupported-expressions-entity-sql.md)
