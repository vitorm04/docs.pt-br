---
title: Como o Entity SQL difere do Transact-SQL
ms.date: 03/30/2017
ms.assetid: 9c9ee36d-f294-4c8b-a196-f0114c94f559
ms.openlocfilehash: e0af0a415d812337d6abf449e9ee170526c3df0c
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833718"
---
# <a name="how-entity-sql-differs-from-transact-sql"></a><span data-ttu-id="3ed64-102">Como o Entity SQL difere do Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="3ed64-102">How Entity SQL Differs from Transact-SQL</span></span>
<span data-ttu-id="3ed64-103">Este tópico descreve as diferenças entre [!INCLUDE[esql](../../../../../../includes/esql-md.md)] o e o Transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="3ed64-103">This topic describes the differences between [!INCLUDE[esql](../../../../../../includes/esql-md.md)] and Transact-SQL.</span></span>  
  
## <a name="inheritance-and-relationships-support"></a><span data-ttu-id="3ed64-104">Suporte a herança e relações</span><span class="sxs-lookup"><span data-stu-id="3ed64-104">Inheritance and Relationships Support</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="3ed64-105">funciona diretamente com esquemas de entidade conceitual e oferece suporte a recursos de modelo conceitual, como herança e relações.</span><span class="sxs-lookup"><span data-stu-id="3ed64-105">works directly with conceptual entity schemas and supports conceptual model features such as inheritance and relationships.</span></span>  
  
 <span data-ttu-id="3ed64-106">Ao trabalhar com herança, geralmente é útil selecionar instâncias de um subtipo de uma coleção de instâncias de supertipo.</span><span class="sxs-lookup"><span data-stu-id="3ed64-106">When working with inheritance, it is often useful to select instances of a subtype from a collection of supertype instances.</span></span> <span data-ttu-id="3ed64-107">O operador [OfType](oftype-entity-sql.md) em [!INCLUDE[esql](../../../../../../includes/esql-md.md)] (semelhante a `oftype` em C# sequences) fornece esse recurso.</span><span class="sxs-lookup"><span data-stu-id="3ed64-107">The [oftype](oftype-entity-sql.md) operator in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] (similar to `oftype` in C# Sequences) provides this capability.</span></span>  
  
## <a name="support-for-collections"></a><span data-ttu-id="3ed64-108">Suporte para coleções</span><span class="sxs-lookup"><span data-stu-id="3ed64-108">Support for Collections</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="3ed64-109">Trata as coleções como entidades de primeira classe.</span><span class="sxs-lookup"><span data-stu-id="3ed64-109">treats collections as first-class entities.</span></span> <span data-ttu-id="3ed64-110">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="3ed64-110">For example:</span></span>  
  
- <span data-ttu-id="3ed64-111">As expressões de coleção são válidas em uma cláusula `from`.</span><span class="sxs-lookup"><span data-stu-id="3ed64-111">Collection expressions are valid in a `from` clause.</span></span>  
  
- <span data-ttu-id="3ed64-112">As subconsultas `in` e `exists` foram generalizadas para permitir quaisquer coleções.</span><span class="sxs-lookup"><span data-stu-id="3ed64-112">`in` and `exists` subqueries have been generalized to allow any collections.</span></span>  
  
     <span data-ttu-id="3ed64-113">Um subconsulta é um tipo de coleção.</span><span class="sxs-lookup"><span data-stu-id="3ed64-113">A subquery is one kind of collection.</span></span> <span data-ttu-id="3ed64-114">`e1 in e2` e `exists(e)` são as construções [!INCLUDE[esql](../../../../../../includes/esql-md.md)] para executar essas operações.</span><span class="sxs-lookup"><span data-stu-id="3ed64-114">`e1 in e2` and `exists(e)` are the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] constructs to perform these operations.</span></span>  
  
- <span data-ttu-id="3ed64-115">A operações de conjunto, como `union`, `intersect` e `except`, agora funcionam em coleções.</span><span class="sxs-lookup"><span data-stu-id="3ed64-115">Set operations, such as `union`, `intersect`, and `except`, now operate on collections.</span></span>  
  
- <span data-ttu-id="3ed64-116">As junções funcionam em coleções.</span><span class="sxs-lookup"><span data-stu-id="3ed64-116">Joins operate on collections.</span></span>  
  
## <a name="support-for-expressions"></a><span data-ttu-id="3ed64-117">Suporte para expressões</span><span class="sxs-lookup"><span data-stu-id="3ed64-117">Support for Expressions</span></span>  
 <span data-ttu-id="3ed64-118">O Transact-SQL tem subconsultas (tabelas) e expressões (linhas e colunas).</span><span class="sxs-lookup"><span data-stu-id="3ed64-118">Transact-SQL has subqueries (tables) and expressions (rows and columns).</span></span>  
  
 <span data-ttu-id="3ed64-119">Para dar suporte a coleções e coleções [!INCLUDE[esql](../../../../../../includes/esql-md.md)] aninhadas, o transforma tudo em uma expressão.</span><span class="sxs-lookup"><span data-stu-id="3ed64-119">To support collections and nested collections, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] makes everything an expression.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="3ed64-120">é mais combinável do que o Transact-SQL – cada expressão pode ser usada em qualquer lugar.</span><span class="sxs-lookup"><span data-stu-id="3ed64-120">is more composable than Transact-SQL—every expression can be used anywhere.</span></span> <span data-ttu-id="3ed64-121">As expressões de consulta sempre resultam em coleções dos tipos projetados e podem ser usadas em qualquer lugar em que uma expressão de coleção seja permitida.</span><span class="sxs-lookup"><span data-stu-id="3ed64-121">Query expressions always result in collections of the projected types and can be used anywhere a collection expression is allowed.</span></span> <span data-ttu-id="3ed64-122">Para obter informações sobre expressões Transact-SQL que não têm suporte [!INCLUDE[esql](../../../../../../includes/esql-md.md)]no, consulte [expressões sem suporte](unsupported-expressions-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="3ed64-122">For information about Transact-SQL expressions that are not supported in [!INCLUDE[esql](../../../../../../includes/esql-md.md)], see [Unsupported Expressions](unsupported-expressions-entity-sql.md).</span></span>  
  
 <span data-ttu-id="3ed64-123">Os itens a seguir são todos consultas [!INCLUDE[esql](../../../../../../includes/esql-md.md)] válidas:</span><span class="sxs-lookup"><span data-stu-id="3ed64-123">The following are all valid [!INCLUDE[esql](../../../../../../includes/esql-md.md)] queries:</span></span>  
  
```sql  
1+2 *3  
"abc"  
row(1 as a, 2 as b)  
{ 1, 3, 5}   
e1 union all e2  
set(e1)  
```  
  
## <a name="uniform-treatment-of-subqueries"></a><span data-ttu-id="3ed64-124">Tratamento uniforme de subconsultas</span><span class="sxs-lookup"><span data-stu-id="3ed64-124">Uniform Treatment of Subqueries</span></span>  
 <span data-ttu-id="3ed64-125">Considerando sua ênfase em tabelas, o Transact-SQL executa a interpretação contextual de subconsultas.</span><span class="sxs-lookup"><span data-stu-id="3ed64-125">Given its emphasis on tables, Transact-SQL performs contextual interpretation of subqueries.</span></span> <span data-ttu-id="3ed64-126">Por exemplo, uma subconsulta na `from` cláusula é considerada uma multiconjunto (tabela).</span><span class="sxs-lookup"><span data-stu-id="3ed64-126">For example, a subquery in the `from` clause is considered to be a multiset (table).</span></span> <span data-ttu-id="3ed64-127">Mas a mesma subconsulta usada na cláusula `select` é considerada uma subconsulta escalar.</span><span class="sxs-lookup"><span data-stu-id="3ed64-127">But the same subquery used in the `select` clause is considered to be a scalar subquery.</span></span> <span data-ttu-id="3ed64-128">Da mesma forma, uma subconsulta usada no lado esquerdo de `in` um operador é considerada uma subconsulta escalar, enquanto o lado direito deve ser uma subconsulta multiconjunto.</span><span class="sxs-lookup"><span data-stu-id="3ed64-128">Similarly, a subquery used on the left side of an `in` operator is considered to be a scalar subquery, while the right side is expected to be a multiset subquery.</span></span>  
  
 <span data-ttu-id="3ed64-129">O [!INCLUDE[esql](../../../../../../includes/esql-md.md)] elimina essas diferenças.</span><span class="sxs-lookup"><span data-stu-id="3ed64-129">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] eliminates these differences.</span></span> <span data-ttu-id="3ed64-130">Uma expressão tem uma interpretação uniforme que não depende do contexto no qual é usada.</span><span class="sxs-lookup"><span data-stu-id="3ed64-130">An expression has a uniform interpretation that does not depend on the context in which it is used.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="3ed64-131">considera que todas as subconsultas sejam subconsultas multiconjunto.</span><span class="sxs-lookup"><span data-stu-id="3ed64-131">considers all subqueries to be multiset subqueries.</span></span> <span data-ttu-id="3ed64-132">Se for desejado um valor escalar da subconsulta, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] o fornecerá o `anyelement` operador que opera em uma coleção (nesse caso, a subconsulta) e extrairá um valor singleton da coleção.</span><span class="sxs-lookup"><span data-stu-id="3ed64-132">If a scalar value is desired from the subquery, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] provides the `anyelement` operator that operates on a collection (in this case, the subquery), and extracts a singleton value from the collection.</span></span>  
  
### <a name="avoiding-implicit-coercions-for-subqueries"></a><span data-ttu-id="3ed64-133">Evitando coerções implícitas para subconsultas</span><span class="sxs-lookup"><span data-stu-id="3ed64-133">Avoiding Implicit Coercions for Subqueries</span></span>  
 <span data-ttu-id="3ed64-134">Um efeito colateral relacionado ao tratamento uniforme de subconsultas é a conversão implícita de subconsultas em valores escalares.</span><span class="sxs-lookup"><span data-stu-id="3ed64-134">A related side effect of uniform treatment of subqueries is implicit conversion of subqueries to scalar values.</span></span> <span data-ttu-id="3ed64-135">Especificamente, no Transact-SQL, um multiconjunto de linhas (com um único campo) é implicitamente convertido em um valor escalar cujo tipo de dados é o do campo.</span><span class="sxs-lookup"><span data-stu-id="3ed64-135">Specifically, in Transact-SQL, a multiset of rows (with a single field) is implicitly converted into a scalar value whose data type is that of the field.</span></span>  
  
 <span data-ttu-id="3ed64-136">O [!INCLUDE[esql](../../../../../../includes/esql-md.md)] não oferece suporte a essa coerção implícita.</span><span class="sxs-lookup"><span data-stu-id="3ed64-136">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] does not support this implicit coercion.</span></span> <span data-ttu-id="3ed64-137">O [!INCLUDE[esql](../../../../../../includes/esql-md.md)] fornece o operador de ANYELEMENT para extrair um valor singleton de uma coleção, e uma cláusula `select value` para evitar criar um wrapper de linha durante uma expressão de consulta.</span><span class="sxs-lookup"><span data-stu-id="3ed64-137">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] provides the ANYELEMENT operator to extract a singleton value from a collection, and a `select value` clause to avoid creating a row-wrapper during a query expression.</span></span>  
  
## <a name="select-value-avoiding-the-implicit-row-wrapper"></a><span data-ttu-id="3ed64-138">Selecione o valor: Evitando o wrapper de linha implícito</span><span class="sxs-lookup"><span data-stu-id="3ed64-138">Select Value: Avoiding the Implicit Row Wrapper</span></span>  
 <span data-ttu-id="3ed64-139">A cláusula SELECT em uma subconsulta Transact-SQL cria implicitamente um wrapper de linha em volta dos itens na cláusula.</span><span class="sxs-lookup"><span data-stu-id="3ed64-139">The select clause in a Transact-SQL subquery implicitly creates a row wrapper around the items in the clause.</span></span> <span data-ttu-id="3ed64-140">Isso indica que não podemos criar coleções de escalares ou objetos.</span><span class="sxs-lookup"><span data-stu-id="3ed64-140">This implies that we cannot create collections of scalars or objects.</span></span> <span data-ttu-id="3ed64-141">O Transact-SQL permite uma coerção implícita entre um RowType com um campo e um valor singleton do mesmo tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="3ed64-141">Transact-SQL allows an implicit coercion between a rowtype with one field, and a singleton value of the same data type.</span></span>  
  
 <span data-ttu-id="3ed64-142">O [!INCLUDE[esql](../../../../../../includes/esql-md.md)] fornece a cláusula `select value` para ignorar a construção de linha implícita.</span><span class="sxs-lookup"><span data-stu-id="3ed64-142">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] provides the `select value` clause to skip the implicit row construction.</span></span> <span data-ttu-id="3ed64-143">Somente um item pode ser especificado em uma cláusula `select value`.</span><span class="sxs-lookup"><span data-stu-id="3ed64-143">Only one item may be specified in a `select value` clause.</span></span> <span data-ttu-id="3ed64-144">Quando tal cláusula é usada, nenhum wrapper de linha é construído ao redor dos itens na cláusula `select`, e uma coleção da forma desejada pode ser gerada, por exemplo: `select value a`.</span><span class="sxs-lookup"><span data-stu-id="3ed64-144">When such a clause is used, no row wrapper is constructed around the items in the `select` clause, and a collection of the desired shape may be produced, for example: `select value a`.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="3ed64-145">também fornece o construtor de linha para construir linhas arbitrárias.</span><span class="sxs-lookup"><span data-stu-id="3ed64-145">also provides the row constructor to construct arbitrary rows.</span></span> <span data-ttu-id="3ed64-146">`select` utiliza um ou mais elementos da projeção e resulta em um registro de dados com campos, como a seguir:</span><span class="sxs-lookup"><span data-stu-id="3ed64-146">`select` takes one or more elements in the projection and results in a data record with fields, as follows:</span></span>  
  
 `select a, b, c`  
  
## <a name="left-correlation-and-aliasing"></a><span data-ttu-id="3ed64-147">Correlação à esquerda e aliases</span><span class="sxs-lookup"><span data-stu-id="3ed64-147">Left Correlation and Aliasing</span></span>  
 <span data-ttu-id="3ed64-148">No Transact-SQL, as expressões em um determinado escopo (uma única cláusula `select` como `from`ou) não podem referenciar expressões definidas anteriormente no mesmo escopo.</span><span class="sxs-lookup"><span data-stu-id="3ed64-148">In Transact-SQL, expressions in a given scope (a single clause like `select` or `from`) cannot reference expressions defined earlier in the same scope.</span></span> <span data-ttu-id="3ed64-149">Alguns dialetos do SQL (incluindo Transact-SQL) dão suporte a `from` formas limitadas deles na cláusula.</span><span class="sxs-lookup"><span data-stu-id="3ed64-149">Some dialects of SQL (including Transact-SQL) do support limited forms of these in the `from` clause.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="3ed64-150">generaliza correlações à esquerda na `from` cláusula e as trata uniformemente.</span><span class="sxs-lookup"><span data-stu-id="3ed64-150">generalizes left correlations in the `from` clause, and treats them uniformly.</span></span> <span data-ttu-id="3ed64-151">As expressões na cláusula `from` podem referenciar as definições anteriores (definições à esquerda) na mesma cláusula sem a necessidade de sintaxe adicional.</span><span class="sxs-lookup"><span data-stu-id="3ed64-151">Expressions in the `from` clause can reference earlier definitions (definitions to the left) in the same clause without the need for additional syntax.</span></span>  
  
 <span data-ttu-id="3ed64-152">O [!INCLUDE[esql](../../../../../../includes/esql-md.md)] também impõe restrições adicionais em consultas que envolvem cláusulas `group by`.</span><span class="sxs-lookup"><span data-stu-id="3ed64-152">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] also imposes additional restrictions on queries involving `group by` clauses.</span></span> <span data-ttu-id="3ed64-153">As expressões na `select` cláusula and `having` da cláusula dessas consultas só `group by` podem fazer referência às chaves por meio de seus aliases.</span><span class="sxs-lookup"><span data-stu-id="3ed64-153">Expressions in the `select` clause and `having` clause of such queries may only refer to the `group by` keys via their aliases.</span></span> <span data-ttu-id="3ed64-154">A construção a seguir é válida no Transact-SQL, mas não [!INCLUDE[esql](../../../../../../includes/esql-md.md)]está em:</span><span class="sxs-lookup"><span data-stu-id="3ed64-154">The following construct is valid in Transact-SQL but are not in [!INCLUDE[esql](../../../../../../includes/esql-md.md)]:</span></span>  
  
```sql  
SELECT t.x + t.y FROM T AS t group BY t.x + t.y
```  
  
 <span data-ttu-id="3ed64-155">Para fazer isso em [!INCLUDE[esql](../../../../../../includes/esql-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="3ed64-155">To do this in [!INCLUDE[esql](../../../../../../includes/esql-md.md)]:</span></span>  
  
```sql  
SELET k FROM T AS t GROUP BY (t.x + t.y) AS k
```  
  
## <a name="referencing-columns-properties-of-tables-collections"></a><span data-ttu-id="3ed64-156">Referenciando colunas (propriedades) de tabelas (coleções)</span><span class="sxs-lookup"><span data-stu-id="3ed64-156">Referencing Columns (Properties) of Tables (Collections)</span></span>  
 <span data-ttu-id="3ed64-157">Todas as referências a colunas em [!INCLUDE[esql](../../../../../../includes/esql-md.md)] devem ser qualificadas com o alias de tabela.</span><span class="sxs-lookup"><span data-stu-id="3ed64-157">All column references in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] must be qualified with the table alias.</span></span> <span data-ttu-id="3ed64-158">A construção a seguir (supondo que `a` seja uma coluna de tabela `T`válida) é válida no Transact-SQL, [!INCLUDE[esql](../../../../../../includes/esql-md.md)]mas não no.</span><span class="sxs-lookup"><span data-stu-id="3ed64-158">The following construct (assuming that `a` is a valid column of table `T`) is valid in Transact-SQL but not in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>  
  
```sql  
SELECT a FROM T
```  
  
 <span data-ttu-id="3ed64-159">A forma em [!INCLUDE[esql](../../../../../../includes/esql-md.md)] é</span><span class="sxs-lookup"><span data-stu-id="3ed64-159">The [!INCLUDE[esql](../../../../../../includes/esql-md.md)] form is</span></span>  
  
```sql  
SELECT t.a AS A FROM T AS t
```  
  
 <span data-ttu-id="3ed64-160">Os aliases de tabela são opcionais na cláusula `from`.</span><span class="sxs-lookup"><span data-stu-id="3ed64-160">The table aliases are optional in the `from` clause.</span></span> <span data-ttu-id="3ed64-161">O nome da tabela é usado como o alias implícito.</span><span class="sxs-lookup"><span data-stu-id="3ed64-161">The name of the table is used as the implicit alias.</span></span> <span data-ttu-id="3ed64-162">O [!INCLUDE[esql](../../../../../../includes/esql-md.md)] permite também a forma a seguir:</span><span class="sxs-lookup"><span data-stu-id="3ed64-162">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] allows the following form as well:</span></span>  
  
```sql  
SELET Tab.a FROM Tab
```  
  
## <a name="navigation-through-objects"></a><span data-ttu-id="3ed64-163">Navegação por objetos</span><span class="sxs-lookup"><span data-stu-id="3ed64-163">Navigation Through Objects</span></span>  
 <span data-ttu-id="3ed64-164">O Transact-SQL usa a notação "." para fazer referência a colunas de (uma linha de) uma tabela.</span><span class="sxs-lookup"><span data-stu-id="3ed64-164">Transact-SQL uses the "." notation for referencing columns of (a row of) a table.</span></span> <span data-ttu-id="3ed64-165">O [!INCLUDE[esql](../../../../../../includes/esql-md.md)] amplia essa notação (emprestada de linguagens de programação) para oferecer suporte à navegação pelas propriedades de um objeto.</span><span class="sxs-lookup"><span data-stu-id="3ed64-165">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] extends this notation (borrowed from programming languages) to support navigation through properties of an object.</span></span>  
  
 <span data-ttu-id="3ed64-166">Por exemplo, se `p` for uma expressão do tipo Pessoa, a sintaxe [!INCLUDE[esql](../../../../../../includes/esql-md.md)] a seguir fará referência à cidade do endereço dessa pessoa.</span><span class="sxs-lookup"><span data-stu-id="3ed64-166">For example, if `p` is an expression of type Person, the following is the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] syntax for referencing the city of the address of this person.</span></span>  
  
```sql  
p.Address.City   
```  
  
## <a name="no-support-for-"></a><span data-ttu-id="3ed64-167">Nenhum suporte para \*</span><span class="sxs-lookup"><span data-stu-id="3ed64-167">No Support for \*</span></span>  
 <span data-ttu-id="3ed64-168">O Transact-SQL dá suporte à sintaxe \* não qualificada como um alias para a linha inteira e \* a sintaxe qualificada\*(t.) como um atalho para os campos dessa tabela.</span><span class="sxs-lookup"><span data-stu-id="3ed64-168">Transact-SQL supports the unqualified \* syntax as an alias for the entire row, and the qualified \* syntax (t.\*) as a shortcut for the fields of that table.</span></span> <span data-ttu-id="3ed64-169">Além disso, o Transact-SQL permite uma agregação de\*contagem especial (), que inclui nulos.</span><span class="sxs-lookup"><span data-stu-id="3ed64-169">In addition, Transact-SQL allows for a special count(\*) aggregate, which includes nulls.</span></span>  
  
 <span data-ttu-id="3ed64-170">O [!INCLUDE[esql](../../../../../../includes/esql-md.md)] não oferece suporte à construção \*.</span><span class="sxs-lookup"><span data-stu-id="3ed64-170">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] does not support the \* construct.</span></span> <span data-ttu-id="3ed64-171">Consultas Transact-SQL do formulário `select * from T` e `select T1.* from T1, T2...` podem ser expressas em [!INCLUDE[esql](../../../../../../includes/esql-md.md)] como `select value t from T as t` e `select value t1 from T1 as t1, T2 as t2...`, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="3ed64-171">Transact-SQL queries of the form `select * from T` and `select T1.* from T1, T2...` can be expressed in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] as `select value t from T as t` and `select value t1 from T1 as t1, T2 as t2...`, respectively.</span></span> <span data-ttu-id="3ed64-172">Além disso, essas construções manipulam a herança (substituibilidade do valor), embora as variantes `select *` sejam restritas a propriedades de nível superior do tipo declarado.</span><span class="sxs-lookup"><span data-stu-id="3ed64-172">Additionally, these constructs handle inheritance (value substitutability), while the `select *` variants are restricted to top-level properties of the declared type.</span></span>  
  
 <span data-ttu-id="3ed64-173">O [!INCLUDE[esql](../../../../../../includes/esql-md.md)] não oferece suporte à agregação `count(*)`.</span><span class="sxs-lookup"><span data-stu-id="3ed64-173">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] does not support the `count(*)` aggregate.</span></span> <span data-ttu-id="3ed64-174">Use `count(0)` em seu lugar.</span><span class="sxs-lookup"><span data-stu-id="3ed64-174">Use `count(0)` instead.</span></span>  
  
## <a name="changes-to-group-by"></a><span data-ttu-id="3ed64-175">Alterações em group by</span><span class="sxs-lookup"><span data-stu-id="3ed64-175">Changes to Group By</span></span>  
 <span data-ttu-id="3ed64-176">O [!INCLUDE[esql](../../../../../../includes/esql-md.md)] oferece suporte a aliases de chaves `group by`.</span><span class="sxs-lookup"><span data-stu-id="3ed64-176">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] supports aliasing of `group by` keys.</span></span> <span data-ttu-id="3ed64-177">As expressões na `select` cláusula e `having` `group by` cláusula devem se referir às chaves por meio desses aliases.</span><span class="sxs-lookup"><span data-stu-id="3ed64-177">Expressions in the `select` clause and `having` clause must refer to the `group by` keys via these aliases.</span></span> <span data-ttu-id="3ed64-178">Por exemplo, esta [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sintaxe:</span><span class="sxs-lookup"><span data-stu-id="3ed64-178">For example, this [!INCLUDE[esql](../../../../../../includes/esql-md.md)] syntax:</span></span>  
  
```sql  
SELECT k1, count(t.a), sum(t.a)
FROM T AS t
GROUP BY t.b + t.c AS k1
```  
  
 <span data-ttu-id="3ed64-179">... é equivalente ao Transact-SQL a seguir:</span><span class="sxs-lookup"><span data-stu-id="3ed64-179">...is equivalent to the following Transact-SQL:</span></span>  
  
```sql  
SELECT b + c, count(*), sum(a)
FROM T
GROUP BY b + c
```  
  
## <a name="collection-based-aggregates"></a><span data-ttu-id="3ed64-180">Agregações baseadas em coleção</span><span class="sxs-lookup"><span data-stu-id="3ed64-180">Collection-Based Aggregates</span></span>  
 <span data-ttu-id="3ed64-181">O [!INCLUDE[esql](../../../../../../includes/esql-md.md)] oferece suporte a dois tipos de agregações.</span><span class="sxs-lookup"><span data-stu-id="3ed64-181">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] supports two kinds of aggregates.</span></span>  
  
 <span data-ttu-id="3ed64-182">As agregações baseadas em coleção operam em coleções e geram o resultado agregado.</span><span class="sxs-lookup"><span data-stu-id="3ed64-182">Collection-based aggregates operate on collections and produce the aggregated result.</span></span> <span data-ttu-id="3ed64-183">Elas podem aparecer em qualquer lugar na consulta, e não requerem uma cláusula `group by`.</span><span class="sxs-lookup"><span data-stu-id="3ed64-183">These can appear anywhere in the query, and do not require a `group by` clause.</span></span> <span data-ttu-id="3ed64-184">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="3ed64-184">For example:</span></span>  
  
```sql  
SELECT t.a AS a, count({1,2,3}) AS b FROM T AS t
```  
  
 <span data-ttu-id="3ed64-185">O [!INCLUDE[esql](../../../../../../includes/esql-md.md)] também oferece suporte a agregações do tipo SQL.</span><span class="sxs-lookup"><span data-stu-id="3ed64-185">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] also supports SQL-style aggregates.</span></span> <span data-ttu-id="3ed64-186">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="3ed64-186">For example:</span></span>  
  
```sql  
SELECT a, sum(t.b) FROM T AS t GROUP BY t.a AS a
```  
  
## <a name="order-by-clause-usage"></a><span data-ttu-id="3ed64-187">Uso da cláusula ORDER BY</span><span class="sxs-lookup"><span data-stu-id="3ed64-187">ORDER BY Clause Usage</span></span>  
<span data-ttu-id="3ed64-188">O Transact-SQL permite que as cláusulas `ORDER BY` sejam especificadas somente no bloco de `SELECT .. FROM .. WHERE` superior.</span><span class="sxs-lookup"><span data-stu-id="3ed64-188">Transact-SQL allows `ORDER BY` clauses to be specified only in the topmost `SELECT .. FROM .. WHERE` block.</span></span> <span data-ttu-id="3ed64-189">No [!INCLUDE[esql](../../../../../../includes/esql-md.md)], você pode usar uma expressão `ORDER BY` aninhada e ela pode ser colocada em qualquer lugar na consulta, mas a ordenação em uma consulta aninhada não é preservada.</span><span class="sxs-lookup"><span data-stu-id="3ed64-189">In [!INCLUDE[esql](../../../../../../includes/esql-md.md)] you can use a nested `ORDER BY` expression and it can be placed anywhere in the query, but ordering in a nested query is not preserved.</span></span>  
  
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
  
## <a name="identifiers"></a><span data-ttu-id="3ed64-190">Identificadores</span><span class="sxs-lookup"><span data-stu-id="3ed64-190">Identifiers</span></span>  
 <span data-ttu-id="3ed64-191">No Transact-SQL, a comparação de identificador é baseada no agrupamento do banco de dados atual.</span><span class="sxs-lookup"><span data-stu-id="3ed64-191">In Transact-SQL, identifier comparison is based on the collation of the current database.</span></span> <span data-ttu-id="3ed64-192">No [!INCLUDE[esql](../../../../../../includes/esql-md.md)], os identificadores sempre diferenciam maiúsculas de minúsculas e diferenciam [!INCLUDE[esql](../../../../../../includes/esql-md.md)] acentos (ou seja, distingue entre caracteres acentuados e não acentuados; por exemplo, ' a ' não é igual a ' ã ').</span><span class="sxs-lookup"><span data-stu-id="3ed64-192">In [!INCLUDE[esql](../../../../../../includes/esql-md.md)], identifiers are always case insensitive and accent sensitive (that is, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] distinguishes between accented and unaccented characters; for example, 'a' is not equal to 'ấ').</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="3ed64-193">trata versões de letras que aparecem o mesmo mas é páginas diferentes de código como caracteres diferentes.</span><span class="sxs-lookup"><span data-stu-id="3ed64-193">treats versions of letters that appear the same but are from different code pages as different characters.</span></span> <span data-ttu-id="3ed64-194">Para obter mais informações, consulte [conjunto de caracteres de entrada](input-character-set-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="3ed64-194">For more information, see [Input Character Set](input-character-set-entity-sql.md).</span></span>  
  
## <a name="transact-sql-functionality-not-available-in-entity-sql"></a><span data-ttu-id="3ed64-195">Funcionalidade Transact-SQL não disponível em Entity SQL</span><span class="sxs-lookup"><span data-stu-id="3ed64-195">Transact-SQL Functionality Not Available in Entity SQL</span></span>  
 <span data-ttu-id="3ed64-196">A seguinte funcionalidade Transact-SQL não está disponível no [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3ed64-196">The following Transact-SQL functionality is not available in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>  
  
 <span data-ttu-id="3ed64-197">DML</span><span class="sxs-lookup"><span data-stu-id="3ed64-197">DML</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="3ed64-198">Atualmente, não fornece suporte para instruções DML (INSERT, Update e Delete).</span><span class="sxs-lookup"><span data-stu-id="3ed64-198">currently provides no support for DML statements (insert, update, delete).</span></span>  
  
 <span data-ttu-id="3ed64-199">DDL</span><span class="sxs-lookup"><span data-stu-id="3ed64-199">DDL</span></span>  
 <span data-ttu-id="3ed64-200">O [!INCLUDE[esql](../../../../../../includes/esql-md.md)] não oferece suporte para DDL na versão atual.</span><span class="sxs-lookup"><span data-stu-id="3ed64-200">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] provides no support for DDL in the current version.</span></span>  
  
 <span data-ttu-id="3ed64-201">Programação imperativa</span><span class="sxs-lookup"><span data-stu-id="3ed64-201">Imperative Programming</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="3ed64-202">não fornece suporte para programação imperativa, ao contrário do Transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="3ed64-202">provides no support for imperative programming, unlike Transact-SQL.</span></span> <span data-ttu-id="3ed64-203">Use, em vez disso, uma linguagem de programação.</span><span class="sxs-lookup"><span data-stu-id="3ed64-203">Use a programming language instead.</span></span>  
  
 <span data-ttu-id="3ed64-204">Funções de agrupamento</span><span class="sxs-lookup"><span data-stu-id="3ed64-204">Grouping Functions</span></span>  
 <span data-ttu-id="3ed64-205">O [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ainda não oferece suporte para funções de agrupamento (por exemplo, CUBE, ROLLUP e GROUPING_SET).</span><span class="sxs-lookup"><span data-stu-id="3ed64-205">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] does not yet provide support for grouping functions (for example, CUBE, ROLLUP, and GROUPING_SET).</span></span>  
  
 <span data-ttu-id="3ed64-206">Funções analíticas</span><span class="sxs-lookup"><span data-stu-id="3ed64-206">Analytic Functions</span></span>  
 <span data-ttu-id="3ed64-207">O [!INCLUDE[esql](../../../../../../includes/esql-md.md)] (ainda) não oferece suporte para funções analíticas.</span><span class="sxs-lookup"><span data-stu-id="3ed64-207">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] does not (yet) provide support for analytic functions.</span></span>  
  
 <span data-ttu-id="3ed64-208">Funções internas, operadores</span><span class="sxs-lookup"><span data-stu-id="3ed64-208">Built-in Functions, Operators</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="3ed64-209">dá suporte a um subconjunto de funções e operadores internos do Transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="3ed64-209">supports a subset of Transact-SQL's built in functions and operators.</span></span> <span data-ttu-id="3ed64-210">Esses operadores e funções provavelmente têm suporte com os principais provedores de repositório.</span><span class="sxs-lookup"><span data-stu-id="3ed64-210">These operators and functions are likely to be supported by the major store providers.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="3ed64-211">usa funções específicas do repositório declaradas em um manifesto do provedor.</span><span class="sxs-lookup"><span data-stu-id="3ed64-211">uses the store-specific functions declared in a provider manifest.</span></span> <span data-ttu-id="3ed64-212">Além disso, o Entity Framework permite que você declare funções de armazenamento existentes internas e definidas pelo usuário para [!INCLUDE[esql](../../../../../../includes/esql-md.md)] usar o.</span><span class="sxs-lookup"><span data-stu-id="3ed64-212">Additionally, the Entity Framework allows you to declare built-in and user-defined existing store functions, for [!INCLUDE[esql](../../../../../../includes/esql-md.md)] to use.</span></span>  
  
 <span data-ttu-id="3ed64-213">Dicas</span><span class="sxs-lookup"><span data-stu-id="3ed64-213">Hints</span></span>  
 <span data-ttu-id="3ed64-214">O [!INCLUDE[esql](../../../../../../includes/esql-md.md)] não oferece mecanismos para dicas de consulta.</span><span class="sxs-lookup"><span data-stu-id="3ed64-214">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] does not provide mechanisms for query hints.</span></span>  
  
 <span data-ttu-id="3ed64-215">Processando resultados de consulta em lotes</span><span class="sxs-lookup"><span data-stu-id="3ed64-215">Batching Query Results</span></span>  
 <span data-ttu-id="3ed64-216">O [!INCLUDE[esql](../../../../../../includes/esql-md.md)] não oferece suporte a resultados de consulta em lotes.</span><span class="sxs-lookup"><span data-stu-id="3ed64-216">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] does not support batching query results.</span></span> <span data-ttu-id="3ed64-217">Por exemplo, o seguinte é um Transact-SQL válido (envio como um lote):</span><span class="sxs-lookup"><span data-stu-id="3ed64-217">For example, the following is valid Transact-SQL (sending as a batch):</span></span>  
  
```sql  
SELECT * FROM products;
SELECT * FROM catagories;
```  
  
 <span data-ttu-id="3ed64-218">No entanto, a sintaxe [!INCLUDE[esql](../../../../../../includes/esql-md.md)] equivalente não tem suporte:</span><span class="sxs-lookup"><span data-stu-id="3ed64-218">However, the equivalent [!INCLUDE[esql](../../../../../../includes/esql-md.md)] is not supported:</span></span>  
  
```sql  
SELECT value p FROM Products AS p;
SELECT value c FROM Categories AS c;
```  
  
 <span data-ttu-id="3ed64-219">O [!INCLUDE[esql](../../../../../../includes/esql-md.md)] oferece suporte a apenas uma instrução de consulta que gera resultado por comando.</span><span class="sxs-lookup"><span data-stu-id="3ed64-219">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] only supports one result-producing query statement per command.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ed64-220">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3ed64-220">See also</span></span>

- [<span data-ttu-id="3ed64-221">Visão geral do Entity SQL</span><span class="sxs-lookup"><span data-stu-id="3ed64-221">Entity SQL Overview</span></span>](entity-sql-overview.md)
- [<span data-ttu-id="3ed64-222">Expressões sem suporte</span><span class="sxs-lookup"><span data-stu-id="3ed64-222">Unsupported Expressions</span></span>](unsupported-expressions-entity-sql.md)
