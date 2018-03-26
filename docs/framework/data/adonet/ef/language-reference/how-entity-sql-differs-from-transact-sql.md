---
title: Como o Entity SQL difere do Transact-SQL
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9c9ee36d-f294-4c8b-a196-f0114c94f559
caps.latest.revision: ''
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: 3f80ec1ac51dded1f91d1a18c4d4e24836cf92cd
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/26/2018
---
# <a name="how-entity-sql-differs-from-transact-sql"></a><span data-ttu-id="a9a3b-102">Como o Entity SQL difere do Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="a9a3b-102">How Entity SQL Differs from Transact-SQL</span></span>
<span data-ttu-id="a9a3b-103">Este tópico descreve as diferenças entre [!INCLUDE[esql](../../../../../../includes/esql-md.md)] e [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a9a3b-103">This topic describes the differences between [!INCLUDE[esql](../../../../../../includes/esql-md.md)] and [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)].</span></span>  
  
## <a name="inheritance-and-relationships-support"></a><span data-ttu-id="a9a3b-104">Suporte a herança e relações</span><span class="sxs-lookup"><span data-stu-id="a9a3b-104">Inheritance and Relationships Support</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="a9a3b-105"> trabalha diretamente com os esquemas de entidade conceitual e dá suporte a recursos de modelo conceitual como herança e relações.</span><span class="sxs-lookup"><span data-stu-id="a9a3b-105"> works directly with conceptual entity schemas and supports conceptual model features such as inheritance and relationships.</span></span>  
  
 <span data-ttu-id="a9a3b-106">Ao trabalhar com herança, geralmente é útil selecionar instâncias de um subtipo de uma coleção de instâncias de supertipo.</span><span class="sxs-lookup"><span data-stu-id="a9a3b-106">When working with inheritance, it is often useful to select instances of a subtype from a collection of supertype instances.</span></span> <span data-ttu-id="a9a3b-107">O [oftype](../../../../../../docs/framework/data/adonet/ef/language-reference/oftype-entity-sql.md) operador em [!INCLUDE[esql](../../../../../../includes/esql-md.md)] (semelhante a `oftype` em sequências de c#) fornece essa funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="a9a3b-107">The [oftype](../../../../../../docs/framework/data/adonet/ef/language-reference/oftype-entity-sql.md) operator in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] (similar to `oftype` in C# Sequences) provides this capability.</span></span>  
  
## <a name="support-for-collections"></a><span data-ttu-id="a9a3b-108">Suporte para coleções</span><span class="sxs-lookup"><span data-stu-id="a9a3b-108">Support for Collections</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="a9a3b-109"> trata coleções como entidades de primeira classe.</span><span class="sxs-lookup"><span data-stu-id="a9a3b-109"> treats collections as first-class entities.</span></span> <span data-ttu-id="a9a3b-110">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="a9a3b-110">For example:</span></span>  
  
-   <span data-ttu-id="a9a3b-111">As expressões de coleção são válidas em uma cláusula `from`.</span><span class="sxs-lookup"><span data-stu-id="a9a3b-111">Collection expressions are valid in a `from` clause.</span></span>  
  
-   <span data-ttu-id="a9a3b-112">As subconsultas `in` e `exists` foram generalizadas para permitir quaisquer coleções.</span><span class="sxs-lookup"><span data-stu-id="a9a3b-112">`in` and `exists` subqueries have been generalized to allow any collections.</span></span>  
  
     <span data-ttu-id="a9a3b-113">Um subconsulta é um tipo de coleção.</span><span class="sxs-lookup"><span data-stu-id="a9a3b-113">A subquery is one kind of collection.</span></span> <span data-ttu-id="a9a3b-114">`e1 in e2` e `exists(e)` são as construções [!INCLUDE[esql](../../../../../../includes/esql-md.md)] para executar essas operações.</span><span class="sxs-lookup"><span data-stu-id="a9a3b-114">`e1 in e2` and `exists(e)` are the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] constructs to perform these operations.</span></span>  
  
-   <span data-ttu-id="a9a3b-115">A operações de conjunto, como `union`, `intersect` e `except`, agora funcionam em coleções.</span><span class="sxs-lookup"><span data-stu-id="a9a3b-115">Set operations, such as `union`, `intersect`, and `except`, now operate on collections.</span></span>  
  
-   <span data-ttu-id="a9a3b-116">As junções funcionam em coleções.</span><span class="sxs-lookup"><span data-stu-id="a9a3b-116">Joins operate on collections.</span></span>  
  
## <a name="support-for-expressions"></a><span data-ttu-id="a9a3b-117">Suporte para expressões</span><span class="sxs-lookup"><span data-stu-id="a9a3b-117">Support for Expressions</span></span>  
 [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]<span data-ttu-id="a9a3b-118"> tem (tabelas) de subconsultas e expressões (linhas e colunas).</span><span class="sxs-lookup"><span data-stu-id="a9a3b-118"> has subqueries (tables) and expressions (rows and columns).</span></span>  
  
 <span data-ttu-id="a9a3b-119">Para dar suporte a coleções e aninhadas, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] torna tudo em uma expressão.</span><span class="sxs-lookup"><span data-stu-id="a9a3b-119">To support collections and nested collections, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] makes everything an expression.</span></span> <span data-ttu-id="a9a3b-120">O [!INCLUDE[esql](../../../../../../includes/esql-md.md)] é mais combinável do que o [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] — cada expressão pode ser usada em qualquer lugar.</span><span class="sxs-lookup"><span data-stu-id="a9a3b-120">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] is more composable than [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]—every expression can be used anywhere.</span></span> <span data-ttu-id="a9a3b-121">As expressões de consulta sempre resultam em coleções dos tipos projetados e podem ser usadas em qualquer lugar em que uma expressão de coleção seja permitida.</span><span class="sxs-lookup"><span data-stu-id="a9a3b-121">Query expressions always result in collections of the projected types and can be used anywhere a collection expression is allowed.</span></span> <span data-ttu-id="a9a3b-122">Para obter informações sobre [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] expressões que não têm suporte em [!INCLUDE[esql](../../../../../../includes/esql-md.md)], consulte [expressões](../../../../../../docs/framework/data/adonet/ef/language-reference/unsupported-expressions-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="a9a3b-122">For information about [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] expressions that are not supported in [!INCLUDE[esql](../../../../../../includes/esql-md.md)], see [Unsupported Expressions](../../../../../../docs/framework/data/adonet/ef/language-reference/unsupported-expressions-entity-sql.md).</span></span>  
  
 <span data-ttu-id="a9a3b-123">Os itens a seguir são todos consultas [!INCLUDE[esql](../../../../../../includes/esql-md.md)] válidas:</span><span class="sxs-lookup"><span data-stu-id="a9a3b-123">The following are all valid [!INCLUDE[esql](../../../../../../includes/esql-md.md)] queries:</span></span>  
  
```  
1+2 *3  
"abc"  
row(1 as a, 2 as b)  
{ 1, 3, 5}   
e1 union all e2  
set(e1)  
```  
  
## <a name="uniform-treatment-of-subqueries"></a><span data-ttu-id="a9a3b-124">Tratamento uniforme de subconsultas</span><span class="sxs-lookup"><span data-stu-id="a9a3b-124">Uniform Treatment of Subqueries</span></span>  
 <span data-ttu-id="a9a3b-125">Considerando sua ênfase em tabelas, [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] executa contextual interpretação de subconsultas.</span><span class="sxs-lookup"><span data-stu-id="a9a3b-125">Given its emphasis on tables, [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] performs contextual interpretation of subqueries.</span></span> <span data-ttu-id="a9a3b-126">Por exemplo, uma subconsulta no `from` cláusula é considerada um multiconjunto (tabela).</span><span class="sxs-lookup"><span data-stu-id="a9a3b-126">For example, a subquery in the `from` clause is considered to be a multiset (table).</span></span> <span data-ttu-id="a9a3b-127">Mas a mesma subconsulta usada na cláusula `select` é considerada uma subconsulta escalar.</span><span class="sxs-lookup"><span data-stu-id="a9a3b-127">But the same subquery used in the `select` clause is considered to be a scalar subquery.</span></span> <span data-ttu-id="a9a3b-128">Da mesma forma, uma subconsulta usada no lado esquerdo de uma `in` operador é considerado uma subconsulta escalar, enquanto o lado direito deve ser uma subconsulta multiset.</span><span class="sxs-lookup"><span data-stu-id="a9a3b-128">Similarly, a subquery used on the left side of an `in` operator is considered to be a scalar subquery, while the right side is expected to be a multiset subquery.</span></span>  
  
 <span data-ttu-id="a9a3b-129">O [!INCLUDE[esql](../../../../../../includes/esql-md.md)] elimina essas diferenças.</span><span class="sxs-lookup"><span data-stu-id="a9a3b-129">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] eliminates these differences.</span></span> <span data-ttu-id="a9a3b-130">Uma expressão tem uma interpretação uniforme que não depende do contexto no qual é usada.</span><span class="sxs-lookup"><span data-stu-id="a9a3b-130">An expression has a uniform interpretation that does not depend on the context in which it is used.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="a9a3b-131"> considera todas as subconsultas ser subconsultas multiset.</span><span class="sxs-lookup"><span data-stu-id="a9a3b-131"> considers all subqueries to be multiset subqueries.</span></span> <span data-ttu-id="a9a3b-132">Se um valor escalar é desejado da subconsulta, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] fornece o `anyelement` operador que opera em uma coleção (nesse caso, a subconsulta) e extrai um valor de singleton da coleção.</span><span class="sxs-lookup"><span data-stu-id="a9a3b-132">If a scalar value is desired from the subquery, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] provides the `anyelement` operator that operates on a collection (in this case, the subquery), and extracts a singleton value from the collection.</span></span>  
  
### <a name="avoiding-implicit-coercions-for-subqueries"></a><span data-ttu-id="a9a3b-133">Evitando coerções implícitas para subconsultas</span><span class="sxs-lookup"><span data-stu-id="a9a3b-133">Avoiding Implicit Coercions for Subqueries</span></span>  
 <span data-ttu-id="a9a3b-134">Um efeito colateral relacionado ao tratamento uniforme de subconsultas é a conversão implícita de subconsultas em valores escalares.</span><span class="sxs-lookup"><span data-stu-id="a9a3b-134">A related side effect of uniform treatment of subqueries is implicit conversion of subqueries to scalar values.</span></span> <span data-ttu-id="a9a3b-135">Especificamente, no [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], um multiset de linhas (com um único campo) é convertido implicitamente em um valor escalar cujo tipo de dados é o do campo.</span><span class="sxs-lookup"><span data-stu-id="a9a3b-135">Specifically, in [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], a multiset of rows (with a single field) is implicitly converted into a scalar value whose data type is that of the field.</span></span>  
  
 <span data-ttu-id="a9a3b-136">O [!INCLUDE[esql](../../../../../../includes/esql-md.md)] não oferece suporte a essa coerção implícita.</span><span class="sxs-lookup"><span data-stu-id="a9a3b-136">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] does not support this implicit coercion.</span></span> <span data-ttu-id="a9a3b-137">O [!INCLUDE[esql](../../../../../../includes/esql-md.md)] fornece o operador de ANYELEMENT para extrair um valor singleton de uma coleção, e uma cláusula `select value` para evitar criar um wrapper de linha durante uma expressão de consulta.</span><span class="sxs-lookup"><span data-stu-id="a9a3b-137">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] provides the ANYELEMENT operator to extract a singleton value from a collection, and a `select value` clause to avoid creating a row-wrapper during a query expression.</span></span>  
  
## <a name="select-value-avoiding-the-implicit-row-wrapper"></a><span data-ttu-id="a9a3b-138">Select Value: evitando o wrapper de linha implícito</span><span class="sxs-lookup"><span data-stu-id="a9a3b-138">Select Value: Avoiding the Implicit Row Wrapper</span></span>  
 <span data-ttu-id="a9a3b-139">Cláusula select em uma [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] subconsulta cria implicitamente um wrapper de linha ao redor dos itens na cláusula.</span><span class="sxs-lookup"><span data-stu-id="a9a3b-139">The select clause in a [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] subquery implicitly creates a row wrapper around the items in the clause.</span></span> <span data-ttu-id="a9a3b-140">Isso indica que não podemos criar coleções de escalares ou objetos.</span><span class="sxs-lookup"><span data-stu-id="a9a3b-140">This implies that we cannot create collections of scalars or objects.</span></span> [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]<span data-ttu-id="a9a3b-141"> permite que uma coerção implícita entre um rowtype com um campo e um valor de singleton do mesmo tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="a9a3b-141"> allows an implicit coercion between a rowtype with one field, and a singleton value of the same data type.</span></span>  
  
 <span data-ttu-id="a9a3b-142">O [!INCLUDE[esql](../../../../../../includes/esql-md.md)] fornece a cláusula `select value` para ignorar a construção de linha implícita.</span><span class="sxs-lookup"><span data-stu-id="a9a3b-142">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] provides the `select value` clause to skip the implicit row construction.</span></span> <span data-ttu-id="a9a3b-143">Somente um item pode ser especificado em uma cláusula `select value`.</span><span class="sxs-lookup"><span data-stu-id="a9a3b-143">Only one item may be specified in a `select value` clause.</span></span> <span data-ttu-id="a9a3b-144">Quando tal cláusula é usada, nenhum wrapper de linha é construído ao redor dos itens na cláusula `select`, e uma coleção da forma desejada pode ser gerada, por exemplo: `select value a`.</span><span class="sxs-lookup"><span data-stu-id="a9a3b-144">When such a clause is used, no row wrapper is constructed around the items in the `select` clause, and a collection of the desired shape may be produced, for example: `select value a`.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="a9a3b-145"> também fornece o construtor de linha para construir linhas arbitrárias.</span><span class="sxs-lookup"><span data-stu-id="a9a3b-145"> also provides the row constructor to construct arbitrary rows.</span></span> <span data-ttu-id="a9a3b-146">`select` utiliza um ou mais elementos da projeção e resulta em um registro de dados com campos, como a seguir:</span><span class="sxs-lookup"><span data-stu-id="a9a3b-146">`select` takes one or more elements in the projection and results in a data record with fields, as follows:</span></span>  
  
 `select a, b, c`  
  
## <a name="left-correlation-and-aliasing"></a><span data-ttu-id="a9a3b-147">Correlação à esquerda e aliases</span><span class="sxs-lookup"><span data-stu-id="a9a3b-147">Left Correlation and Aliasing</span></span>  
 <span data-ttu-id="a9a3b-148">No [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], as expressões em um determinado escopo (uma cláusula única, como `select` ou `from`) não podem referenciar expressões definidas anteriormente no mesmo escopo.</span><span class="sxs-lookup"><span data-stu-id="a9a3b-148">In [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], expressions in a given scope (a single clause like `select` or `from`) cannot reference expressions defined earlier in the same scope.</span></span> <span data-ttu-id="a9a3b-149">Alguns dialetos do SQL (incluindo [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]) oferecem suporte a formas limitadas delas na cláusula `from`.</span><span class="sxs-lookup"><span data-stu-id="a9a3b-149">Some dialects of SQL (including [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]) do support limited forms of these in the `from` clause.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="a9a3b-150"> generaliza correlações esquerdas no `from` cláusula e trata-los uniformemente.</span><span class="sxs-lookup"><span data-stu-id="a9a3b-150"> generalizes left correlations in the `from` clause, and treats them uniformly.</span></span> <span data-ttu-id="a9a3b-151">As expressões na cláusula `from` podem referenciar as definições anteriores (definições à esquerda) na mesma cláusula sem a necessidade de sintaxe adicional.</span><span class="sxs-lookup"><span data-stu-id="a9a3b-151">Expressions in the `from` clause can reference earlier definitions (definitions to the left) in the same clause without the need for additional syntax.</span></span>  
  
 <span data-ttu-id="a9a3b-152">O [!INCLUDE[esql](../../../../../../includes/esql-md.md)] também impõe restrições adicionais em consultas que envolvem cláusulas `group by`.</span><span class="sxs-lookup"><span data-stu-id="a9a3b-152">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] also imposes additional restrictions on queries involving `group by` clauses.</span></span> <span data-ttu-id="a9a3b-153">Expressões no `select` cláusula e `having` só pode se referir a cláusula de tais consultas a `group by` chaves por meio de seus aliases.</span><span class="sxs-lookup"><span data-stu-id="a9a3b-153">Expressions in the `select` clause and `having` clause of such queries may only refer to the `group by` keys via their aliases.</span></span> <span data-ttu-id="a9a3b-154">A construção a seguir é válida em [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] , mas não estão no [!INCLUDE[esql](../../../../../../includes/esql-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="a9a3b-154">The following construct is valid in [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] but are not in [!INCLUDE[esql](../../../../../../includes/esql-md.md)]:</span></span>  
  
```  
select t.x + t.y from T as t group by t.x + t.y  
```  
  
 <span data-ttu-id="a9a3b-155">Para fazer isso em [!INCLUDE[esql](../../../../../../includes/esql-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="a9a3b-155">To do this in [!INCLUDE[esql](../../../../../../includes/esql-md.md)]:</span></span>  
  
```  
select k from T as t group by (t.x + t.y) as k  
```  
  
## <a name="referencing-columns-properties-of-tables-collections"></a><span data-ttu-id="a9a3b-156">Referenciando colunas (propriedades) de tabelas (coleções)</span><span class="sxs-lookup"><span data-stu-id="a9a3b-156">Referencing Columns (Properties) of Tables (Collections)</span></span>  
 <span data-ttu-id="a9a3b-157">Todas as referências a colunas em [!INCLUDE[esql](../../../../../../includes/esql-md.md)] devem ser qualificadas com o alias de tabela.</span><span class="sxs-lookup"><span data-stu-id="a9a3b-157">All column references in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] must be qualified with the table alias.</span></span> <span data-ttu-id="a9a3b-158">A construção a seguir (supondo que `a` é uma coluna válida da tabela `T`) é válido em [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] , mas não no [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a9a3b-158">The following construct (assuming that `a` is a valid column of table `T`) is valid in [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] but not in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>  
  
```  
select a from T  
```  
  
 <span data-ttu-id="a9a3b-159">A forma em [!INCLUDE[esql](../../../../../../includes/esql-md.md)] é</span><span class="sxs-lookup"><span data-stu-id="a9a3b-159">The [!INCLUDE[esql](../../../../../../includes/esql-md.md)] form is</span></span>  
  
```  
select t.a as A from T as t  
```  
  
 <span data-ttu-id="a9a3b-160">Os aliases de tabela são opcionais na cláusula `from`.</span><span class="sxs-lookup"><span data-stu-id="a9a3b-160">The table aliases are optional in the `from` clause.</span></span> <span data-ttu-id="a9a3b-161">O nome da tabela é usado como o alias implícito.</span><span class="sxs-lookup"><span data-stu-id="a9a3b-161">The name of the table is used as the implicit alias.</span></span> <span data-ttu-id="a9a3b-162">O [!INCLUDE[esql](../../../../../../includes/esql-md.md)] permite também a forma a seguir:</span><span class="sxs-lookup"><span data-stu-id="a9a3b-162">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] allows the following form as well:</span></span>  
  
```  
select Tab.a from Tab  
```  
  
## <a name="navigation-through-objects"></a><span data-ttu-id="a9a3b-163">Navegação por objetos</span><span class="sxs-lookup"><span data-stu-id="a9a3b-163">Navigation Through Objects</span></span>  
 <span data-ttu-id="a9a3b-164">O [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] usa a notação “.” para referenciar colunas de (uma linha de) uma tabela.</span><span class="sxs-lookup"><span data-stu-id="a9a3b-164">[!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] uses the "." notation for referencing columns of (a row of) a table.</span></span> <span data-ttu-id="a9a3b-165">O [!INCLUDE[esql](../../../../../../includes/esql-md.md)] amplia essa notação (emprestada de linguagens de programação) para oferecer suporte à navegação pelas propriedades de um objeto.</span><span class="sxs-lookup"><span data-stu-id="a9a3b-165">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] extends this notation (borrowed from programming languages) to support navigation through properties of an object.</span></span>  
  
 <span data-ttu-id="a9a3b-166">Por exemplo, se `p` for uma expressão do tipo Pessoa, a sintaxe [!INCLUDE[esql](../../../../../../includes/esql-md.md)] a seguir fará referência à cidade do endereço dessa pessoa.</span><span class="sxs-lookup"><span data-stu-id="a9a3b-166">For example, if `p` is an expression of type Person, the following is the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] syntax for referencing the city of the address of this person.</span></span>  
  
```  
p.Address.City   
```  
  
## <a name="no-support-for-"></a><span data-ttu-id="a9a3b-167">Nenhum suporte para \*</span><span class="sxs-lookup"><span data-stu-id="a9a3b-167">No Support for \*</span></span>  
 [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]<span data-ttu-id="a9a3b-168"> oferece suporte a qualificados \* sintaxe como um alias para a linha inteira e o qualificado \* sintaxe (t.\*) como um atalho para os campos da tabela.</span><span class="sxs-lookup"><span data-stu-id="a9a3b-168"> supports the unqualified \* syntax as an alias for the entire row, and the qualified \* syntax (t.\*) as a shortcut for the fields of that table.</span></span> <span data-ttu-id="a9a3b-169">Além disso, [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] permite que uma conta especial (\*) agregação, que inclui valores nulos.</span><span class="sxs-lookup"><span data-stu-id="a9a3b-169">In addition, [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] allows for a special count(\*) aggregate, which includes nulls.</span></span>  
  
 <span data-ttu-id="a9a3b-170">O [!INCLUDE[esql](../../../../../../includes/esql-md.md)] não oferece suporte à construção \*.</span><span class="sxs-lookup"><span data-stu-id="a9a3b-170">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] does not support the \* construct.</span></span> <span data-ttu-id="a9a3b-171">As consultas [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] da forma `select * from T` e `select T1.* from T1, T2...` podem ser expressas em [!INCLUDE[esql](../../../../../../includes/esql-md.md)] como `select value t from T as t` e `select value t1 from T1 as t1, T2 as t2...`, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="a9a3b-171">[!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] queries of the form `select * from T` and `select T1.* from T1, T2...` can be expressed in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] as `select value t from T as t` and `select value t1 from T1 as t1, T2 as t2...`, respectively.</span></span> <span data-ttu-id="a9a3b-172">Além disso, essas construções manipulam a herança (substituibilidade do valor), embora as variantes `select *` sejam restritas a propriedades de nível superior do tipo declarado.</span><span class="sxs-lookup"><span data-stu-id="a9a3b-172">Additionally, these constructs handle inheritance (value substitutability), while the `select *` variants are restricted to top-level properties of the declared type.</span></span>  
  
 <span data-ttu-id="a9a3b-173">O [!INCLUDE[esql](../../../../../../includes/esql-md.md)] não oferece suporte à agregação `count(*)`.</span><span class="sxs-lookup"><span data-stu-id="a9a3b-173">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] does not support the `count(*)` aggregate.</span></span> <span data-ttu-id="a9a3b-174">Use `count(0)` em seu lugar.</span><span class="sxs-lookup"><span data-stu-id="a9a3b-174">Use `count(0)` instead.</span></span>  
  
## <a name="changes-to-group-by"></a><span data-ttu-id="a9a3b-175">Alterações em group by</span><span class="sxs-lookup"><span data-stu-id="a9a3b-175">Changes to Group By</span></span>  
 <span data-ttu-id="a9a3b-176">O [!INCLUDE[esql](../../../../../../includes/esql-md.md)] oferece suporte a aliases de chaves `group by`.</span><span class="sxs-lookup"><span data-stu-id="a9a3b-176">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] supports aliasing of `group by` keys.</span></span> <span data-ttu-id="a9a3b-177">Expressões de `select` cláusula e `having` cláusula deve se referir ao `group by` chaves via esses aliases.</span><span class="sxs-lookup"><span data-stu-id="a9a3b-177">Expressions in the `select` clause and `having` clause must refer to the `group by` keys via these aliases.</span></span> <span data-ttu-id="a9a3b-178">Por exemplo, isso [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sintaxe:</span><span class="sxs-lookup"><span data-stu-id="a9a3b-178">For example, this [!INCLUDE[esql](../../../../../../includes/esql-md.md)] syntax:</span></span>  
  
```  
select k1, count(t.a), sum(t.a)  
from T as t  
group by t.b + t.c as k1  
```  
  
 <span data-ttu-id="a9a3b-179">...é equivalente à seguinte sintaxe [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="a9a3b-179">...is equivalent to the following [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]:</span></span>  
  
```  
select b + c, count(*), sum(a)   
from T  
group by b + c  
```  
  
## <a name="collection-based-aggregates"></a><span data-ttu-id="a9a3b-180">Agregações baseadas em coleção</span><span class="sxs-lookup"><span data-stu-id="a9a3b-180">Collection-Based Aggregates</span></span>  
 <span data-ttu-id="a9a3b-181">O [!INCLUDE[esql](../../../../../../includes/esql-md.md)] oferece suporte a dois tipos de agregações.</span><span class="sxs-lookup"><span data-stu-id="a9a3b-181">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] supports two kinds of aggregates.</span></span>  
  
 <span data-ttu-id="a9a3b-182">As agregações baseadas em coleção operam em coleções e geram o resultado agregado.</span><span class="sxs-lookup"><span data-stu-id="a9a3b-182">Collection-based aggregates operate on collections and produce the aggregated result.</span></span> <span data-ttu-id="a9a3b-183">Elas podem aparecer em qualquer lugar na consulta, e não requerem uma cláusula `group by`.</span><span class="sxs-lookup"><span data-stu-id="a9a3b-183">These can appear anywhere in the query, and do not require a `group by` clause.</span></span> <span data-ttu-id="a9a3b-184">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="a9a3b-184">For example:</span></span>  
  
```  
select t.a as a, count({1,2,3}) as b from T as t     
```  
  
 <span data-ttu-id="a9a3b-185">O [!INCLUDE[esql](../../../../../../includes/esql-md.md)] também oferece suporte a agregações do tipo SQL.</span><span class="sxs-lookup"><span data-stu-id="a9a3b-185">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] also supports SQL-style aggregates.</span></span> <span data-ttu-id="a9a3b-186">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="a9a3b-186">For example:</span></span>  
  
```  
select a, sum(t.b) from T as t group by t.a as a  
```  
  
## <a name="order-by-clause-usage"></a><span data-ttu-id="a9a3b-187">Uso da cláusula ORDER BY</span><span class="sxs-lookup"><span data-stu-id="a9a3b-187">ORDER BY Clause Usage</span></span>  
 [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]<span data-ttu-id="a9a3b-188"> permite que as cláusulas ORDER BY seja especificado somente no mais alto, selecione...</span><span class="sxs-lookup"><span data-stu-id="a9a3b-188"> allows ORDER BY clauses to be specified only in the topmost SELECT ..</span></span> <span data-ttu-id="a9a3b-189">DE..</span><span class="sxs-lookup"><span data-stu-id="a9a3b-189">FROM ..</span></span> <span data-ttu-id="a9a3b-190">WHERE mais alto.</span><span class="sxs-lookup"><span data-stu-id="a9a3b-190">WHERE block.</span></span> <span data-ttu-id="a9a3b-191">No [!INCLUDE[esql](../../../../../../includes/esql-md.md)], você pode usar uma expressão ORDER BY aninhada e ela pode ser colocada em qualquer lugar na consulta, mas a ordenação em uma consulta aninhada não é preservada.</span><span class="sxs-lookup"><span data-stu-id="a9a3b-191">In [!INCLUDE[esql](../../../../../../includes/esql-md.md)] you can use a nested ORDER BY expression and it can be placed anywhere in the query, but ordering in a nested query is not preserved.</span></span>  
  
```  
-- The following query will order the results by the last name  
SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName  
```  
  
```  
-- In the following query ordering of the nested query is ignored.  
SELECT C2.FirstName, C2.LastName  
    FROM (SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName) as C2  
```  
  
## <a name="identifiers"></a><span data-ttu-id="a9a3b-192">Identificadores</span><span class="sxs-lookup"><span data-stu-id="a9a3b-192">Identifiers</span></span>  
 <span data-ttu-id="a9a3b-193">No [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], a comparação de identificadores é baseada no agrupamento do banco de dados atual.</span><span class="sxs-lookup"><span data-stu-id="a9a3b-193">In [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], identifier comparison is based on the collation of the current database.</span></span> <span data-ttu-id="a9a3b-194">Em [!INCLUDE[esql](../../../../../../includes/esql-md.md)], identificadores sempre diferenciam maiusculas de minúsculas e acentos (ou seja, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] faz distinção entre caracteres acentuados e não acentuadas; por exemplo, 'a' não é igual a 'ã').</span><span class="sxs-lookup"><span data-stu-id="a9a3b-194">In [!INCLUDE[esql](../../../../../../includes/esql-md.md)], identifiers are always case insensitive and accent sensitive (that is, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] distinguishes between accented and unaccented characters; for example, 'a' is not equal to 'ấ').</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="a9a3b-195"> trata versões de letras que aparecem o mesmo mas é páginas diferentes de código como caracteres diferentes.</span><span class="sxs-lookup"><span data-stu-id="a9a3b-195"> treats versions of letters that appear the same but are from different code pages as different characters.</span></span> <span data-ttu-id="a9a3b-196">Para obter mais informações, consulte [o conjunto de caracteres de entrada](../../../../../../docs/framework/data/adonet/ef/language-reference/input-character-set-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="a9a3b-196">For more information, see [Input Character Set](../../../../../../docs/framework/data/adonet/ef/language-reference/input-character-set-entity-sql.md).</span></span>  
  
## <a name="transact-sql-functionality-not-available-in-entity-sql"></a><span data-ttu-id="a9a3b-197">Funcionalidade Transact-SQL não disponível em Entity SQL</span><span class="sxs-lookup"><span data-stu-id="a9a3b-197">Transact-SQL Functionality Not Available in Entity SQL</span></span>  
 <span data-ttu-id="a9a3b-198">A funcionalidade [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] a seguir não está disponível em [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a9a3b-198">The following [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] functionality is not available in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>  
  
 <span data-ttu-id="a9a3b-199">DML</span><span class="sxs-lookup"><span data-stu-id="a9a3b-199">DML</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="a9a3b-200"> atualmente não fornece suporte para instruções DML (Inserir, atualizar e excluir).</span><span class="sxs-lookup"><span data-stu-id="a9a3b-200"> currently provides no support for DML statements (insert, update, delete).</span></span>  
  
 <span data-ttu-id="a9a3b-201">DDL</span><span class="sxs-lookup"><span data-stu-id="a9a3b-201">DDL</span></span>  
 <span data-ttu-id="a9a3b-202">O [!INCLUDE[esql](../../../../../../includes/esql-md.md)] não oferece suporte para DDL na versão atual.</span><span class="sxs-lookup"><span data-stu-id="a9a3b-202">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] provides no support for DDL in the current version.</span></span>  
  
 <span data-ttu-id="a9a3b-203">Programação imperativa</span><span class="sxs-lookup"><span data-stu-id="a9a3b-203">Imperative Programming</span></span>  
 <span data-ttu-id="a9a3b-204">O [!INCLUDE[esql](../../../../../../includes/esql-md.md)] não oferece suporte para programação imperativa, ao contrário do [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a9a3b-204">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] provides no support for imperative programming, unlike [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="a9a3b-205">Use, em vez disso, uma linguagem de programação.</span><span class="sxs-lookup"><span data-stu-id="a9a3b-205">Use a programming language instead.</span></span>  
  
 <span data-ttu-id="a9a3b-206">Funções de agrupamento</span><span class="sxs-lookup"><span data-stu-id="a9a3b-206">Grouping Functions</span></span>  
 <span data-ttu-id="a9a3b-207">O [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ainda não oferece suporte para funções de agrupamento (por exemplo, CUBE, ROLLUP e GROUPING_SET).</span><span class="sxs-lookup"><span data-stu-id="a9a3b-207">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] does not yet provide support for grouping functions (for example, CUBE, ROLLUP, and GROUPING_SET).</span></span>  
  
 <span data-ttu-id="a9a3b-208">Funções analíticas</span><span class="sxs-lookup"><span data-stu-id="a9a3b-208">Analytic Functions</span></span>  
 <span data-ttu-id="a9a3b-209">O [!INCLUDE[esql](../../../../../../includes/esql-md.md)] (ainda) não oferece suporte para funções analíticas.</span><span class="sxs-lookup"><span data-stu-id="a9a3b-209">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] does not (yet) provide support for analytic functions.</span></span>  
  
 <span data-ttu-id="a9a3b-210">Funções internas, operadores</span><span class="sxs-lookup"><span data-stu-id="a9a3b-210">Built-in Functions, Operators</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="a9a3b-211"> oferece suporte a um subconjunto de [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]interno em funções e operadores.</span><span class="sxs-lookup"><span data-stu-id="a9a3b-211"> supports a subset of [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]'s built in functions and operators.</span></span> <span data-ttu-id="a9a3b-212">Esses operadores e funções provavelmente têm suporte com os principais provedores de repositório.</span><span class="sxs-lookup"><span data-stu-id="a9a3b-212">These operators and functions are likely to be supported by the major store providers.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="a9a3b-213"> usa as funções específicas do repositório declaradas em um manifesto do provedor.</span><span class="sxs-lookup"><span data-stu-id="a9a3b-213"> uses the store-specific functions declared in a provider manifest.</span></span> <span data-ttu-id="a9a3b-214">Além disso, o [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] permite declarar internas e definidas pelo usuário existentes armazenar funções, para [!INCLUDE[esql](../../../../../../includes/esql-md.md)] para usar.</span><span class="sxs-lookup"><span data-stu-id="a9a3b-214">Additionally, the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] allows you to declare built-in and user-defined existing store functions, for [!INCLUDE[esql](../../../../../../includes/esql-md.md)] to use.</span></span>  
  
 <span data-ttu-id="a9a3b-215">Dicas</span><span class="sxs-lookup"><span data-stu-id="a9a3b-215">Hints</span></span>  
 <span data-ttu-id="a9a3b-216">O [!INCLUDE[esql](../../../../../../includes/esql-md.md)] não oferece mecanismos para dicas de consulta.</span><span class="sxs-lookup"><span data-stu-id="a9a3b-216">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] does not provide mechanisms for query hints.</span></span>  
  
 <span data-ttu-id="a9a3b-217">Processando resultados de consulta em lotes</span><span class="sxs-lookup"><span data-stu-id="a9a3b-217">Batching Query Results</span></span>  
 <span data-ttu-id="a9a3b-218">O [!INCLUDE[esql](../../../../../../includes/esql-md.md)] não oferece suporte a resultados de consulta em lotes.</span><span class="sxs-lookup"><span data-stu-id="a9a3b-218">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] does not support batching query results.</span></span> <span data-ttu-id="a9a3b-219">Por exemplo, o seguinte é válido [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] (de envio em lote):</span><span class="sxs-lookup"><span data-stu-id="a9a3b-219">For example, the following is valid [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] (sending as a batch):</span></span>  
  
```  
select * from products;  
select * from catagories;  
```  
  
 <span data-ttu-id="a9a3b-220">No entanto, a sintaxe [!INCLUDE[esql](../../../../../../includes/esql-md.md)] equivalente não tem suporte:</span><span class="sxs-lookup"><span data-stu-id="a9a3b-220">However, the equivalent [!INCLUDE[esql](../../../../../../includes/esql-md.md)] is not supported:</span></span>  
  
```  
Select value p from Products as p;  
Select value c from Categories as c;  
```  
  
 <span data-ttu-id="a9a3b-221">O [!INCLUDE[esql](../../../../../../includes/esql-md.md)] oferece suporte a apenas uma instrução de consulta que gera resultado por comando.</span><span class="sxs-lookup"><span data-stu-id="a9a3b-221">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] only supports one result-producing query statement per command.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9a3b-222">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a9a3b-222">See Also</span></span>  
 [<span data-ttu-id="a9a3b-223">Visão geral do Entity SQL</span><span class="sxs-lookup"><span data-stu-id="a9a3b-223">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
 [<span data-ttu-id="a9a3b-224">Expressões sem suporte</span><span class="sxs-lookup"><span data-stu-id="a9a3b-224">Unsupported Expressions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/unsupported-expressions-entity-sql.md)
