---
title: Como o Entity SQL difere do Transact-SQL
ms.date: 03/30/2017
ms.assetid: 9c9ee36d-f294-4c8b-a196-f0114c94f559
ms.openlocfilehash: 299cb9bbe90c72619cf809a8fc673fca456bd6fd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150225"
---
# <a name="how-entity-sql-differs-from-transact-sql"></a><span data-ttu-id="36427-102">Como o Entity SQL difere do Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="36427-102">How Entity SQL Differs from Transact-SQL</span></span>
<span data-ttu-id="36427-103">Este tópico descreve as [!INCLUDE[esql](../../../../../../includes/esql-md.md)] diferenças entre transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="36427-103">This topic describes the differences between [!INCLUDE[esql](../../../../../../includes/esql-md.md)] and Transact-SQL.</span></span>  
  
## <a name="inheritance-and-relationships-support"></a><span data-ttu-id="36427-104">Suporte a herança e relações</span><span class="sxs-lookup"><span data-stu-id="36427-104">Inheritance and Relationships Support</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="36427-105">trabalha diretamente com entidades conceituais e apoia características conceituais do modelo, como herança e relacionamentos.</span><span class="sxs-lookup"><span data-stu-id="36427-105">works directly with conceptual entity schemas and supports conceptual model features such as inheritance and relationships.</span></span>  
  
 <span data-ttu-id="36427-106">Ao trabalhar com herança, geralmente é útil selecionar instâncias de um subtipo de uma coleção de instâncias de supertipo.</span><span class="sxs-lookup"><span data-stu-id="36427-106">When working with inheritance, it is often useful to select instances of a subtype from a collection of supertype instances.</span></span> <span data-ttu-id="36427-107">O operador [de tipo](oftype-entity-sql.md) em [!INCLUDE[esql](../../../../../../includes/esql-md.md)] (semelhante a `oftype` em Seqüências C#) fornece esse recurso.</span><span class="sxs-lookup"><span data-stu-id="36427-107">The [oftype](oftype-entity-sql.md) operator in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] (similar to `oftype` in C# Sequences) provides this capability.</span></span>  
  
## <a name="support-for-collections"></a><span data-ttu-id="36427-108">Suporte para coleções</span><span class="sxs-lookup"><span data-stu-id="36427-108">Support for Collections</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="36427-109">trata as coleções como entidades de primeira classe.</span><span class="sxs-lookup"><span data-stu-id="36427-109">treats collections as first-class entities.</span></span> <span data-ttu-id="36427-110">Por exemplo: </span><span class="sxs-lookup"><span data-stu-id="36427-110">For example:</span></span>  
  
- <span data-ttu-id="36427-111">As expressões de coleção são válidas em uma cláusula `from`.</span><span class="sxs-lookup"><span data-stu-id="36427-111">Collection expressions are valid in a `from` clause.</span></span>  
  
- <span data-ttu-id="36427-112">As subconsultas `in` e `exists` foram generalizadas para permitir quaisquer coleções.</span><span class="sxs-lookup"><span data-stu-id="36427-112">`in` and `exists` subqueries have been generalized to allow any collections.</span></span>  
  
     <span data-ttu-id="36427-113">Um subconsulta é um tipo de coleção.</span><span class="sxs-lookup"><span data-stu-id="36427-113">A subquery is one kind of collection.</span></span> <span data-ttu-id="36427-114">`e1 in e2` e `exists(e)` são as construções [!INCLUDE[esql](../../../../../../includes/esql-md.md)] para executar essas operações.</span><span class="sxs-lookup"><span data-stu-id="36427-114">`e1 in e2` and `exists(e)` are the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] constructs to perform these operations.</span></span>  
  
- <span data-ttu-id="36427-115">A operações de conjunto, como `union`, `intersect` e `except`, agora funcionam em coleções.</span><span class="sxs-lookup"><span data-stu-id="36427-115">Set operations, such as `union`, `intersect`, and `except`, now operate on collections.</span></span>  
  
- <span data-ttu-id="36427-116">As junções funcionam em coleções.</span><span class="sxs-lookup"><span data-stu-id="36427-116">Joins operate on collections.</span></span>  
  
## <a name="support-for-expressions"></a><span data-ttu-id="36427-117">Suporte para expressões</span><span class="sxs-lookup"><span data-stu-id="36427-117">Support for Expressions</span></span>  
 <span data-ttu-id="36427-118">A Transact-SQL tem subconsultas (tabelas) e expressões (linhas e colunas).</span><span class="sxs-lookup"><span data-stu-id="36427-118">Transact-SQL has subqueries (tables) and expressions (rows and columns).</span></span>  
  
 <span data-ttu-id="36427-119">Apoiar coleções e coleções aninhadas, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] faz de tudo uma expressão.</span><span class="sxs-lookup"><span data-stu-id="36427-119">To support collections and nested collections, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] makes everything an expression.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="36427-120">é mais composável do que Transact-SQL — cada expressão pode ser usada em qualquer lugar.</span><span class="sxs-lookup"><span data-stu-id="36427-120">is more composable than Transact-SQL—every expression can be used anywhere.</span></span> <span data-ttu-id="36427-121">As expressões de consulta sempre resultam em coleções dos tipos projetados e podem ser usadas em qualquer lugar em que uma expressão de coleção seja permitida.</span><span class="sxs-lookup"><span data-stu-id="36427-121">Query expressions always result in collections of the projected types and can be used anywhere a collection expression is allowed.</span></span> <span data-ttu-id="36427-122">Para obter informações sobre expressões Transact-SQL [!INCLUDE[esql](../../../../../../includes/esql-md.md)]que não são suportadas em , consulte [Expressões não suportadas](unsupported-expressions-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="36427-122">For information about Transact-SQL expressions that are not supported in [!INCLUDE[esql](../../../../../../includes/esql-md.md)], see [Unsupported Expressions](unsupported-expressions-entity-sql.md).</span></span>  
  
 <span data-ttu-id="36427-123">Os itens a seguir são todos consultas [!INCLUDE[esql](../../../../../../includes/esql-md.md)] válidas:</span><span class="sxs-lookup"><span data-stu-id="36427-123">The following are all valid [!INCLUDE[esql](../../../../../../includes/esql-md.md)] queries:</span></span>  
  
```sql  
1+2 *3  
"abc"  
row(1 as a, 2 as b)  
{ 1, 3, 5}
e1 union all e2  
set(e1)  
```  
  
## <a name="uniform-treatment-of-subqueries"></a><span data-ttu-id="36427-124">Tratamento uniforme de subconsultas</span><span class="sxs-lookup"><span data-stu-id="36427-124">Uniform Treatment of Subqueries</span></span>  
 <span data-ttu-id="36427-125">Dada a sua ênfase em tabelas, a Transact-SQL realiza interpretação contextual das subconsultas.</span><span class="sxs-lookup"><span data-stu-id="36427-125">Given its emphasis on tables, Transact-SQL performs contextual interpretation of subqueries.</span></span> <span data-ttu-id="36427-126">Por exemplo, uma subquery na `from` cláusula é considerada como um multiconjunto (tabela).</span><span class="sxs-lookup"><span data-stu-id="36427-126">For example, a subquery in the `from` clause is considered to be a multiset (table).</span></span> <span data-ttu-id="36427-127">Mas a mesma subconsulta usada na cláusula `select` é considerada uma subconsulta escalar.</span><span class="sxs-lookup"><span data-stu-id="36427-127">But the same subquery used in the `select` clause is considered to be a scalar subquery.</span></span> <span data-ttu-id="36427-128">Da mesma forma, uma subquery usada `in` no lado esquerdo de um operador é considerada uma subquery escalar, enquanto o lado direito é esperado para ser uma subquery multiconjunto.</span><span class="sxs-lookup"><span data-stu-id="36427-128">Similarly, a subquery used on the left side of an `in` operator is considered to be a scalar subquery, while the right side is expected to be a multiset subquery.</span></span>  
  
 <span data-ttu-id="36427-129">O [!INCLUDE[esql](../../../../../../includes/esql-md.md)] elimina essas diferenças.</span><span class="sxs-lookup"><span data-stu-id="36427-129">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] eliminates these differences.</span></span> <span data-ttu-id="36427-130">Uma expressão tem uma interpretação uniforme que não depende do contexto no qual é usada.</span><span class="sxs-lookup"><span data-stu-id="36427-130">An expression has a uniform interpretation that does not depend on the context in which it is used.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="36427-131">considera todas as subconsultas como subconsultas multiconjuntos.</span><span class="sxs-lookup"><span data-stu-id="36427-131">considers all subqueries to be multiset subqueries.</span></span> <span data-ttu-id="36427-132">Se um valor escalar for desejado da [!INCLUDE[esql](../../../../../../includes/esql-md.md)] subquery, fornece ao `anyelement` operador que opera em uma coleção (neste caso, a subquery), e extrai um valor singleton da coleção.</span><span class="sxs-lookup"><span data-stu-id="36427-132">If a scalar value is desired from the subquery, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] provides the `anyelement` operator that operates on a collection (in this case, the subquery), and extracts a singleton value from the collection.</span></span>  
  
### <a name="avoiding-implicit-coercions-for-subqueries"></a><span data-ttu-id="36427-133">Evitando coerções implícitas para subconsultas</span><span class="sxs-lookup"><span data-stu-id="36427-133">Avoiding Implicit Coercions for Subqueries</span></span>  
 <span data-ttu-id="36427-134">Um efeito colateral relacionado ao tratamento uniforme de subconsultas é a conversão implícita de subconsultas em valores escalares.</span><span class="sxs-lookup"><span data-stu-id="36427-134">A related side effect of uniform treatment of subqueries is implicit conversion of subqueries to scalar values.</span></span> <span data-ttu-id="36427-135">Especificamente, no Transact-SQL, um multiconjunto de linhas (com um único campo) é implicitamente convertido em um valor escalar cujo tipo de dados é o do campo.</span><span class="sxs-lookup"><span data-stu-id="36427-135">Specifically, in Transact-SQL, a multiset of rows (with a single field) is implicitly converted into a scalar value whose data type is that of the field.</span></span>  
  
 <span data-ttu-id="36427-136">O [!INCLUDE[esql](../../../../../../includes/esql-md.md)] não oferece suporte a essa coerção implícita.</span><span class="sxs-lookup"><span data-stu-id="36427-136">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] does not support this implicit coercion.</span></span> <span data-ttu-id="36427-137">O [!INCLUDE[esql](../../../../../../includes/esql-md.md)] fornece o operador de ANYELEMENT para extrair um valor singleton de uma coleção, e uma cláusula `select value` para evitar criar um wrapper de linha durante uma expressão de consulta.</span><span class="sxs-lookup"><span data-stu-id="36427-137">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] provides the ANYELEMENT operator to extract a singleton value from a collection, and a `select value` clause to avoid creating a row-wrapper during a query expression.</span></span>  
  
## <a name="select-value-avoiding-the-implicit-row-wrapper"></a><span data-ttu-id="36427-138">Select Value: evitando o wrapper de linha implícito</span><span class="sxs-lookup"><span data-stu-id="36427-138">Select Value: Avoiding the Implicit Row Wrapper</span></span>  
 <span data-ttu-id="36427-139">A cláusula de seleção em uma subquery Transact-SQL cria implicitamente um invólucro de linha em torno dos itens da cláusula.</span><span class="sxs-lookup"><span data-stu-id="36427-139">The select clause in a Transact-SQL subquery implicitly creates a row wrapper around the items in the clause.</span></span> <span data-ttu-id="36427-140">Isso indica que não podemos criar coleções de escalares ou objetos.</span><span class="sxs-lookup"><span data-stu-id="36427-140">This implies that we cannot create collections of scalars or objects.</span></span> <span data-ttu-id="36427-141">Transact-SQL permite uma coerção implícita entre um tipo de linha com um campo e um valor singleton do mesmo tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="36427-141">Transact-SQL allows an implicit coercion between a rowtype with one field, and a singleton value of the same data type.</span></span>  
  
 <span data-ttu-id="36427-142">O [!INCLUDE[esql](../../../../../../includes/esql-md.md)] fornece a cláusula `select value` para ignorar a construção de linha implícita.</span><span class="sxs-lookup"><span data-stu-id="36427-142">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] provides the `select value` clause to skip the implicit row construction.</span></span> <span data-ttu-id="36427-143">Somente um item pode ser especificado em uma cláusula `select value`.</span><span class="sxs-lookup"><span data-stu-id="36427-143">Only one item may be specified in a `select value` clause.</span></span> <span data-ttu-id="36427-144">Quando tal cláusula é usada, nenhum wrapper de linha é construído ao redor dos itens na cláusula `select`, e uma coleção da forma desejada pode ser gerada, por exemplo: `select value a`.</span><span class="sxs-lookup"><span data-stu-id="36427-144">When such a clause is used, no row wrapper is constructed around the items in the `select` clause, and a collection of the desired shape may be produced, for example: `select value a`.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="36427-145">também fornece o construtor de linha para construir linhas arbitrárias.</span><span class="sxs-lookup"><span data-stu-id="36427-145">also provides the row constructor to construct arbitrary rows.</span></span> <span data-ttu-id="36427-146">`select` utiliza um ou mais elementos da projeção e resulta em um registro de dados com campos, como a seguir:</span><span class="sxs-lookup"><span data-stu-id="36427-146">`select` takes one or more elements in the projection and results in a data record with fields, as follows:</span></span>  
  
 `select a, b, c`  
  
## <a name="left-correlation-and-aliasing"></a><span data-ttu-id="36427-147">Correlação à esquerda e aliases</span><span class="sxs-lookup"><span data-stu-id="36427-147">Left Correlation and Aliasing</span></span>  
 <span data-ttu-id="36427-148">No Transact-SQL, expressões em um determinado `select` escopo `from`(uma única cláusula curtida ou ) não podem referenciar expressões definidas anteriormente no mesmo escopo.</span><span class="sxs-lookup"><span data-stu-id="36427-148">In Transact-SQL, expressions in a given scope (a single clause like `select` or `from`) cannot reference expressions defined earlier in the same scope.</span></span> <span data-ttu-id="36427-149">Alguns dialetos de SQL (incluindo Transact-SQL) `from` suportam formas limitadas destes na cláusula.</span><span class="sxs-lookup"><span data-stu-id="36427-149">Some dialects of SQL (including Transact-SQL) do support limited forms of these in the `from` clause.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="36427-150">generaliza correlações esquerdas `from` na cláusula, e trata-los uniformemente.</span><span class="sxs-lookup"><span data-stu-id="36427-150">generalizes left correlations in the `from` clause, and treats them uniformly.</span></span> <span data-ttu-id="36427-151">As expressões na cláusula `from` podem referenciar as definições anteriores (definições à esquerda) na mesma cláusula sem a necessidade de sintaxe adicional.</span><span class="sxs-lookup"><span data-stu-id="36427-151">Expressions in the `from` clause can reference earlier definitions (definitions to the left) in the same clause without the need for additional syntax.</span></span>  
  
 <span data-ttu-id="36427-152">O [!INCLUDE[esql](../../../../../../includes/esql-md.md)] também impõe restrições adicionais em consultas que envolvem cláusulas `group by`.</span><span class="sxs-lookup"><span data-stu-id="36427-152">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] also imposes additional restrictions on queries involving `group by` clauses.</span></span> <span data-ttu-id="36427-153">Expressões na `select` cláusula `having` e cláusula de tais consultas `group by` só podem se referir às chaves através de seus aliases.</span><span class="sxs-lookup"><span data-stu-id="36427-153">Expressions in the `select` clause and `having` clause of such queries may only refer to the `group by` keys via their aliases.</span></span> <span data-ttu-id="36427-154">O seguinte construto é válido no Transact-SQL, mas não está em [!INCLUDE[esql](../../../../../../includes/esql-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="36427-154">The following construct is valid in Transact-SQL but are not in [!INCLUDE[esql](../../../../../../includes/esql-md.md)]:</span></span>  
  
```sql  
SELECT t.x + t.y FROM T AS t group BY t.x + t.y
```  
  
 <span data-ttu-id="36427-155">Para fazer isso em [!INCLUDE[esql](../../../../../../includes/esql-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="36427-155">To do this in [!INCLUDE[esql](../../../../../../includes/esql-md.md)]:</span></span>  
  
```sql  
SELET k FROM T AS t GROUP BY (t.x + t.y) AS k
```  
  
## <a name="referencing-columns-properties-of-tables-collections"></a><span data-ttu-id="36427-156">Referenciando colunas (propriedades) de tabelas (coleções)</span><span class="sxs-lookup"><span data-stu-id="36427-156">Referencing Columns (Properties) of Tables (Collections)</span></span>  
 <span data-ttu-id="36427-157">Todas as referências a colunas em [!INCLUDE[esql](../../../../../../includes/esql-md.md)] devem ser qualificadas com o alias de tabela.</span><span class="sxs-lookup"><span data-stu-id="36427-157">All column references in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] must be qualified with the table alias.</span></span> <span data-ttu-id="36427-158">O seguinte construto `a` (assumindo que `T`é uma coluna válida de tabela ) [!INCLUDE[esql](../../../../../../includes/esql-md.md)]é válido em Transact-SQL, mas não em .</span><span class="sxs-lookup"><span data-stu-id="36427-158">The following construct (assuming that `a` is a valid column of table `T`) is valid in Transact-SQL but not in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>  
  
```sql  
SELECT a FROM T
```  
  
 <span data-ttu-id="36427-159">A forma em [!INCLUDE[esql](../../../../../../includes/esql-md.md)] é</span><span class="sxs-lookup"><span data-stu-id="36427-159">The [!INCLUDE[esql](../../../../../../includes/esql-md.md)] form is</span></span>  
  
```sql  
SELECT t.a AS A FROM T AS t
```  
  
 <span data-ttu-id="36427-160">Os aliases de tabela são opcionais na cláusula `from`.</span><span class="sxs-lookup"><span data-stu-id="36427-160">The table aliases are optional in the `from` clause.</span></span> <span data-ttu-id="36427-161">O nome da tabela é usado como o alias implícito.</span><span class="sxs-lookup"><span data-stu-id="36427-161">The name of the table is used as the implicit alias.</span></span> <span data-ttu-id="36427-162">O [!INCLUDE[esql](../../../../../../includes/esql-md.md)] permite também a forma a seguir:</span><span class="sxs-lookup"><span data-stu-id="36427-162">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] allows the following form as well:</span></span>  
  
```sql  
SELET Tab.a FROM Tab
```  
  
## <a name="navigation-through-objects"></a><span data-ttu-id="36427-163">Navegação por objetos</span><span class="sxs-lookup"><span data-stu-id="36427-163">Navigation Through Objects</span></span>  
 <span data-ttu-id="36427-164">Transact-SQL usa a notação "." para referenciar colunas de (uma linha de) uma tabela.</span><span class="sxs-lookup"><span data-stu-id="36427-164">Transact-SQL uses the "." notation for referencing columns of (a row of) a table.</span></span> <span data-ttu-id="36427-165">O [!INCLUDE[esql](../../../../../../includes/esql-md.md)] amplia essa notação (emprestada de linguagens de programação) para oferecer suporte à navegação pelas propriedades de um objeto.</span><span class="sxs-lookup"><span data-stu-id="36427-165">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] extends this notation (borrowed from programming languages) to support navigation through properties of an object.</span></span>  
  
 <span data-ttu-id="36427-166">Por exemplo, se `p` for uma expressão do tipo Pessoa, a sintaxe [!INCLUDE[esql](../../../../../../includes/esql-md.md)] a seguir fará referência à cidade do endereço dessa pessoa.</span><span class="sxs-lookup"><span data-stu-id="36427-166">For example, if `p` is an expression of type Person, the following is the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] syntax for referencing the city of the address of this person.</span></span>  
  
```sql  
p.Address.City
```  
  
## <a name="no-support-for-"></a><span data-ttu-id="36427-167">Nenhum suporte para \*</span><span class="sxs-lookup"><span data-stu-id="36427-167">No Support for \*</span></span>  
 <span data-ttu-id="36427-168">A Transact-SQL suporta a sintaxe não qualificada \* como um \* alias para\*toda a linha, e a sintaxe qualificada (t. ) como um atalho para os campos dessa tabela.</span><span class="sxs-lookup"><span data-stu-id="36427-168">Transact-SQL supports the unqualified \* syntax as an alias for the entire row, and the qualified \* syntax (t.\*) as a shortcut for the fields of that table.</span></span> <span data-ttu-id="36427-169">Além disso, o Transact-SQL permite\*uma contagem especial, que inclui nulos.</span><span class="sxs-lookup"><span data-stu-id="36427-169">In addition, Transact-SQL allows for a special count(\*) aggregate, which includes nulls.</span></span>  
  
 <span data-ttu-id="36427-170">O [!INCLUDE[esql](../../../../../../includes/esql-md.md)] não oferece suporte à construção \*.</span><span class="sxs-lookup"><span data-stu-id="36427-170">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] does not support the \* construct.</span></span> <span data-ttu-id="36427-171">As consultas transact-SQL `select * from T` do `select T1.* from T1, T2...` formulário podem [!INCLUDE[esql](../../../../../../includes/esql-md.md)] `select value t from T as t` ser `select value t1 from T1 as t1, T2 as t2...`expressas em, como e , respectivamente.</span><span class="sxs-lookup"><span data-stu-id="36427-171">Transact-SQL queries of the form `select * from T` and `select T1.* from T1, T2...` can be expressed in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] as `select value t from T as t` and `select value t1 from T1 as t1, T2 as t2...`, respectively.</span></span> <span data-ttu-id="36427-172">Além disso, essas construções manipulam a herança (substituibilidade do valor), embora as variantes `select *` sejam restritas a propriedades de nível superior do tipo declarado.</span><span class="sxs-lookup"><span data-stu-id="36427-172">Additionally, these constructs handle inheritance (value substitutability), while the `select *` variants are restricted to top-level properties of the declared type.</span></span>  
  
 <span data-ttu-id="36427-173">O [!INCLUDE[esql](../../../../../../includes/esql-md.md)] não oferece suporte à agregação `count(*)`.</span><span class="sxs-lookup"><span data-stu-id="36427-173">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] does not support the `count(*)` aggregate.</span></span> <span data-ttu-id="36427-174">Use `count(0)` em vez disso.</span><span class="sxs-lookup"><span data-stu-id="36427-174">Use `count(0)` instead.</span></span>  
  
## <a name="changes-to-group-by"></a><span data-ttu-id="36427-175">Alterações em group by</span><span class="sxs-lookup"><span data-stu-id="36427-175">Changes to Group By</span></span>  
 <span data-ttu-id="36427-176">O [!INCLUDE[esql](../../../../../../includes/esql-md.md)] oferece suporte a aliases de chaves `group by`.</span><span class="sxs-lookup"><span data-stu-id="36427-176">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] supports aliasing of `group by` keys.</span></span> <span data-ttu-id="36427-177">Expressões na `select` cláusula `having` e cláusula `group by` devem se referir às chaves através desses pseudônimos.</span><span class="sxs-lookup"><span data-stu-id="36427-177">Expressions in the `select` clause and `having` clause must refer to the `group by` keys via these aliases.</span></span> <span data-ttu-id="36427-178">Por exemplo, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] esta sintaxe:</span><span class="sxs-lookup"><span data-stu-id="36427-178">For example, this [!INCLUDE[esql](../../../../../../includes/esql-md.md)] syntax:</span></span>  
  
```sql  
SELECT k1, count(t.a), sum(t.a)
FROM T AS t
GROUP BY t.b + t.c AS k1
```  
  
 <span data-ttu-id="36427-179">... equivale ao seguinte Transact-SQL:</span><span class="sxs-lookup"><span data-stu-id="36427-179">...is equivalent to the following Transact-SQL:</span></span>  
  
```sql  
SELECT b + c, count(*), sum(a)
FROM T
GROUP BY b + c
```  
  
## <a name="collection-based-aggregates"></a><span data-ttu-id="36427-180">Agregações baseadas em coleção</span><span class="sxs-lookup"><span data-stu-id="36427-180">Collection-Based Aggregates</span></span>  
 <span data-ttu-id="36427-181">O [!INCLUDE[esql](../../../../../../includes/esql-md.md)] oferece suporte a dois tipos de agregações.</span><span class="sxs-lookup"><span data-stu-id="36427-181">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] supports two kinds of aggregates.</span></span>  
  
 <span data-ttu-id="36427-182">As agregações baseadas em coleção operam em coleções e geram o resultado agregado.</span><span class="sxs-lookup"><span data-stu-id="36427-182">Collection-based aggregates operate on collections and produce the aggregated result.</span></span> <span data-ttu-id="36427-183">Elas podem aparecer em qualquer lugar na consulta, e não requerem uma cláusula `group by`.</span><span class="sxs-lookup"><span data-stu-id="36427-183">These can appear anywhere in the query, and do not require a `group by` clause.</span></span> <span data-ttu-id="36427-184">Por exemplo: </span><span class="sxs-lookup"><span data-stu-id="36427-184">For example:</span></span>  
  
```sql  
SELECT t.a AS a, count({1,2,3}) AS b FROM T AS t
```  
  
 <span data-ttu-id="36427-185">O [!INCLUDE[esql](../../../../../../includes/esql-md.md)] também oferece suporte a agregações do tipo SQL.</span><span class="sxs-lookup"><span data-stu-id="36427-185">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] also supports SQL-style aggregates.</span></span> <span data-ttu-id="36427-186">Por exemplo: </span><span class="sxs-lookup"><span data-stu-id="36427-186">For example:</span></span>  
  
```sql  
SELECT a, sum(t.b) FROM T AS t GROUP BY t.a AS a
```  
  
## <a name="order-by-clause-usage"></a><span data-ttu-id="36427-187">Uso da cláusula ORDER BY</span><span class="sxs-lookup"><span data-stu-id="36427-187">ORDER BY Clause Usage</span></span>  
<span data-ttu-id="36427-188">O Transact-SQL permite que `ORDER BY` as cláusulas `SELECT .. FROM .. WHERE` sejam especificadas apenas no bloco superior.</span><span class="sxs-lookup"><span data-stu-id="36427-188">Transact-SQL allows `ORDER BY` clauses to be specified only in the topmost `SELECT .. FROM .. WHERE` block.</span></span> <span data-ttu-id="36427-189">Você [!INCLUDE[esql](../../../../../../includes/esql-md.md)] pode usar uma `ORDER BY` expressão aninhada e ela pode ser colocada em qualquer lugar da consulta, mas o pedido em uma consulta aninhada não é preservado.</span><span class="sxs-lookup"><span data-stu-id="36427-189">In [!INCLUDE[esql](../../../../../../includes/esql-md.md)] you can use a nested `ORDER BY` expression and it can be placed anywhere in the query, but ordering in a nested query is not preserved.</span></span>  
  
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
  
## <a name="identifiers"></a><span data-ttu-id="36427-190">Identificadores</span><span class="sxs-lookup"><span data-stu-id="36427-190">Identifiers</span></span>  
 <span data-ttu-id="36427-191">No Transact-SQL, a comparação de identificadores é baseada na colagem do banco de dados atual.</span><span class="sxs-lookup"><span data-stu-id="36427-191">In Transact-SQL, identifier comparison is based on the collation of the current database.</span></span> <span data-ttu-id="36427-192">Em [!INCLUDE[esql](../../../../../../includes/esql-md.md)], identificadores são sempre insensíveis e [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sensíveis ao sotaque (ou seja, distingue entre personagens acentuados e não acentuados; por exemplo, 'a' não é igual a ''' ).").</span><span class="sxs-lookup"><span data-stu-id="36427-192">In [!INCLUDE[esql](../../../../../../includes/esql-md.md)], identifiers are always case insensitive and accent sensitive (that is, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] distinguishes between accented and unaccented characters; for example, 'a' is not equal to 'ấ').</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="36427-193">trata versões de letras que aparecem o mesmo mas é páginas diferentes de código como caracteres diferentes.</span><span class="sxs-lookup"><span data-stu-id="36427-193">treats versions of letters that appear the same but are from different code pages as different characters.</span></span> <span data-ttu-id="36427-194">Para obter mais informações, consulte [Input Character Set](input-character-set-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="36427-194">For more information, see [Input Character Set](input-character-set-entity-sql.md).</span></span>  
  
## <a name="transact-sql-functionality-not-available-in-entity-sql"></a><span data-ttu-id="36427-195">Funcionalidade Transact-SQL não disponível em Entity SQL</span><span class="sxs-lookup"><span data-stu-id="36427-195">Transact-SQL Functionality Not Available in Entity SQL</span></span>  
 <span data-ttu-id="36427-196">A seguinte funcionalidade Transact-SQL não [!INCLUDE[esql](../../../../../../includes/esql-md.md)]está disponível em .</span><span class="sxs-lookup"><span data-stu-id="36427-196">The following Transact-SQL functionality is not available in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>  
  
 <span data-ttu-id="36427-197">DML</span><span class="sxs-lookup"><span data-stu-id="36427-197">DML</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="36427-198">atualmente, não oferece suporte para instruções DML (inserir, atualizar, excluir).</span><span class="sxs-lookup"><span data-stu-id="36427-198">currently provides no support for DML statements (insert, update, delete).</span></span>  
  
 <span data-ttu-id="36427-199">DDL</span><span class="sxs-lookup"><span data-stu-id="36427-199">DDL</span></span>  
 <span data-ttu-id="36427-200">O [!INCLUDE[esql](../../../../../../includes/esql-md.md)] não oferece suporte para DDL na versão atual.</span><span class="sxs-lookup"><span data-stu-id="36427-200">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] provides no support for DDL in the current version.</span></span>  
  
 <span data-ttu-id="36427-201">Programação imperativa</span><span class="sxs-lookup"><span data-stu-id="36427-201">Imperative Programming</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="36427-202">não fornece suporte para programação imperativa, ao contrário da Transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="36427-202">provides no support for imperative programming, unlike Transact-SQL.</span></span> <span data-ttu-id="36427-203">Use, em vez disso, uma linguagem de programação.</span><span class="sxs-lookup"><span data-stu-id="36427-203">Use a programming language instead.</span></span>  
  
 <span data-ttu-id="36427-204">Funções de agrupamento</span><span class="sxs-lookup"><span data-stu-id="36427-204">Grouping Functions</span></span>  
 <span data-ttu-id="36427-205">O [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ainda não oferece suporte para funções de agrupamento (por exemplo, CUBE, ROLLUP e GROUPING_SET).</span><span class="sxs-lookup"><span data-stu-id="36427-205">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] does not yet provide support for grouping functions (for example, CUBE, ROLLUP, and GROUPING_SET).</span></span>  
  
 <span data-ttu-id="36427-206">Funções Analíticas</span><span class="sxs-lookup"><span data-stu-id="36427-206">Analytic Functions</span></span>  
 <span data-ttu-id="36427-207">O [!INCLUDE[esql](../../../../../../includes/esql-md.md)] (ainda) não oferece suporte para funções analíticas.</span><span class="sxs-lookup"><span data-stu-id="36427-207">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] does not (yet) provide support for analytic functions.</span></span>  
  
 <span data-ttu-id="36427-208">Funções internas, operadores</span><span class="sxs-lookup"><span data-stu-id="36427-208">Built-in Functions, Operators</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="36427-209">suporta um subconjunto de funções e operadores incorporados da Transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="36427-209">supports a subset of Transact-SQL's built in functions and operators.</span></span> <span data-ttu-id="36427-210">Esses operadores e funções provavelmente têm suporte com os principais provedores de repositório.</span><span class="sxs-lookup"><span data-stu-id="36427-210">These operators and functions are likely to be supported by the major store providers.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="36427-211">usa as funções específicas da loja declaradas em um manifesto do provedor.</span><span class="sxs-lookup"><span data-stu-id="36427-211">uses the store-specific functions declared in a provider manifest.</span></span> <span data-ttu-id="36427-212">Além disso, o Entity Framework permite que você declare funções de [!INCLUDE[esql](../../../../../../includes/esql-md.md)] armazenamento existentes incorporadas e definidas pelo usuário para uso.</span><span class="sxs-lookup"><span data-stu-id="36427-212">Additionally, the Entity Framework allows you to declare built-in and user-defined existing store functions, for [!INCLUDE[esql](../../../../../../includes/esql-md.md)] to use.</span></span>  
  
 <span data-ttu-id="36427-213">Dicas</span><span class="sxs-lookup"><span data-stu-id="36427-213">Hints</span></span>  
 <span data-ttu-id="36427-214">O [!INCLUDE[esql](../../../../../../includes/esql-md.md)] não oferece mecanismos para dicas de consulta.</span><span class="sxs-lookup"><span data-stu-id="36427-214">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] does not provide mechanisms for query hints.</span></span>  
  
 <span data-ttu-id="36427-215">Processando resultados de consulta em lotes</span><span class="sxs-lookup"><span data-stu-id="36427-215">Batching Query Results</span></span>  
 <span data-ttu-id="36427-216">O [!INCLUDE[esql](../../../../../../includes/esql-md.md)] não oferece suporte a resultados de consulta em lotes.</span><span class="sxs-lookup"><span data-stu-id="36427-216">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] does not support batching query results.</span></span> <span data-ttu-id="36427-217">Por exemplo, o seguinte é transact-SQL válido (envio como um lote):</span><span class="sxs-lookup"><span data-stu-id="36427-217">For example, the following is valid Transact-SQL (sending as a batch):</span></span>  
  
```sql  
SELECT * FROM products;
SELECT * FROM catagories;
```  
  
 <span data-ttu-id="36427-218">No entanto, a sintaxe [!INCLUDE[esql](../../../../../../includes/esql-md.md)] equivalente não tem suporte:</span><span class="sxs-lookup"><span data-stu-id="36427-218">However, the equivalent [!INCLUDE[esql](../../../../../../includes/esql-md.md)] is not supported:</span></span>  
  
```sql  
SELECT value p FROM Products AS p;
SELECT value c FROM Categories AS c;
```  
  
 <span data-ttu-id="36427-219">O [!INCLUDE[esql](../../../../../../includes/esql-md.md)] oferece suporte a apenas uma instrução de consulta que gera resultado por comando.</span><span class="sxs-lookup"><span data-stu-id="36427-219">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] only supports one result-producing query statement per command.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36427-220">Confira também</span><span class="sxs-lookup"><span data-stu-id="36427-220">See also</span></span>

- [<span data-ttu-id="36427-221">Visão geral da Entity SQL</span><span class="sxs-lookup"><span data-stu-id="36427-221">Entity SQL Overview</span></span>](entity-sql-overview.md)
- [<span data-ttu-id="36427-222">Expressões sem suporte</span><span class="sxs-lookup"><span data-stu-id="36427-222">Unsupported Expressions</span></span>](unsupported-expressions-entity-sql.md)
