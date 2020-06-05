---
title: Cláusula Aggregate
ms.date: 08/28/2018
f1_keywords:
- vb.QueryAggregateIn
- vb.QueryAggregate
- vb.QueryAggregateInto
helpviewer_keywords:
- Aggregate clause [Visual Basic]
- Aggregate statement [Visual Basic]
- queries [Visual Basic], Aggregate
ms.assetid: 1315a814-5db6-4077-b34b-b141e11cc0eb
ms.openlocfilehash: 326c3306368ceca2122e912556efd84e4bfef1f1
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84412995"
---
# <a name="aggregate-clause-visual-basic"></a><span data-ttu-id="44a4b-102">Cláusula Aggregate (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="44a4b-102">Aggregate Clause (Visual Basic)</span></span>
<span data-ttu-id="44a4b-103">Aplica uma ou mais funções de agregação a uma coleção.</span><span class="sxs-lookup"><span data-stu-id="44a4b-103">Applies one or more aggregate functions to a collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44a4b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="44a4b-104">Syntax</span></span>  
  
```vb  
Aggregate element [As type] In collection _  
  [, element2 [As type2] In collection2, [...]]  
  [ clause ]  
  Into expressionList  
```  
  
## <a name="parts"></a><span data-ttu-id="44a4b-105">Partes</span><span class="sxs-lookup"><span data-stu-id="44a4b-105">Parts</span></span>  
  
|<span data-ttu-id="44a4b-106">Termo</span><span class="sxs-lookup"><span data-stu-id="44a4b-106">Term</span></span>|<span data-ttu-id="44a4b-107">Definição</span><span class="sxs-lookup"><span data-stu-id="44a4b-107">Definition</span></span>|  
|---|---|  
|`element`|<span data-ttu-id="44a4b-108">Obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="44a4b-108">Required.</span></span> <span data-ttu-id="44a4b-109">Variável usada para iterar pelos elementos da coleção.</span><span class="sxs-lookup"><span data-stu-id="44a4b-109">Variable used to iterate through the elements of the collection.</span></span>|  
|`type`|<span data-ttu-id="44a4b-110">Opcional.</span><span class="sxs-lookup"><span data-stu-id="44a4b-110">Optional.</span></span> <span data-ttu-id="44a4b-111">O tipo de `element`.</span><span class="sxs-lookup"><span data-stu-id="44a4b-111">The type of `element`.</span></span> <span data-ttu-id="44a4b-112">Se nenhum tipo for especificado, o tipo de `element` será inferido de `collection` .</span><span class="sxs-lookup"><span data-stu-id="44a4b-112">If no type is specified, the type of `element` is inferred from `collection`.</span></span>|  
|`collection`|<span data-ttu-id="44a4b-113">Obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="44a4b-113">Required.</span></span> <span data-ttu-id="44a4b-114">Refere-se à coleção na qual operar.</span><span class="sxs-lookup"><span data-stu-id="44a4b-114">Refers to the collection to operate on.</span></span>|  
|`clause`|<span data-ttu-id="44a4b-115">Opcional.</span><span class="sxs-lookup"><span data-stu-id="44a4b-115">Optional.</span></span> <span data-ttu-id="44a4b-116">Uma ou mais cláusulas de consulta, como uma `Where` cláusula, para refinar o resultado da consulta para aplicar a cláusula ou cláusulas de agregação ao.</span><span class="sxs-lookup"><span data-stu-id="44a4b-116">One or more query clauses, such as a `Where` clause, to refine the query result to apply the aggregate clause or clauses to.</span></span>|  
|`expressionList`|<span data-ttu-id="44a4b-117">Obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="44a4b-117">Required.</span></span> <span data-ttu-id="44a4b-118">Uma ou mais expressões delimitadas por vírgula que identificam uma função de agregação a ser aplicada à coleção.</span><span class="sxs-lookup"><span data-stu-id="44a4b-118">One or more comma-delimited expressions that identify an aggregate function to apply to the collection.</span></span> <span data-ttu-id="44a4b-119">Você pode aplicar um alias a uma função de agregação para especificar um nome de membro para o resultado da consulta.</span><span class="sxs-lookup"><span data-stu-id="44a4b-119">You can apply an alias to an aggregate function to specify a member name for the query result.</span></span> <span data-ttu-id="44a4b-120">Se nenhum alias for fornecido, o nome da função de agregação será usado.</span><span class="sxs-lookup"><span data-stu-id="44a4b-120">If no alias is supplied, the name of the aggregate function is used.</span></span> <span data-ttu-id="44a4b-121">Para obter exemplos, consulte a seção sobre funções de agregação mais adiante neste tópico.</span><span class="sxs-lookup"><span data-stu-id="44a4b-121">For examples, see the section about aggregate functions later in this topic.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="44a4b-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="44a4b-122">Remarks</span></span>  
 <span data-ttu-id="44a4b-123">A `Aggregate` cláusula pode ser usada para incluir funções de agregação em suas consultas.</span><span class="sxs-lookup"><span data-stu-id="44a4b-123">The `Aggregate` clause can be used to include aggregate functions in your queries.</span></span> <span data-ttu-id="44a4b-124">As funções de agregação executam verificações e computações em um conjunto de valores e retornam um único valor.</span><span class="sxs-lookup"><span data-stu-id="44a4b-124">Aggregate functions perform checks and computations over a set of values and return a single value.</span></span> <span data-ttu-id="44a4b-125">Você pode acessar o valor computado usando um membro do tipo de resultado da consulta.</span><span class="sxs-lookup"><span data-stu-id="44a4b-125">You can access the computed value by using a member of the query result type.</span></span> <span data-ttu-id="44a4b-126">As funções de agregação padrão que você pode usar são as `All` funções,,,,,, `Any` `Average` `Count` `LongCount` `Max` `Min` e `Sum` .</span><span class="sxs-lookup"><span data-stu-id="44a4b-126">The standard aggregate functions that you can use are the `All`, `Any`, `Average`, `Count`, `LongCount`, `Max`, `Min`, and `Sum` functions.</span></span> <span data-ttu-id="44a4b-127">Essas funções são familiares aos desenvolvedores que estão familiarizados com agregações no SQL.</span><span class="sxs-lookup"><span data-stu-id="44a4b-127">These functions are familiar to developers who are familiar with aggregates in SQL.</span></span> <span data-ttu-id="44a4b-128">Eles são descritos na seção a seguir deste tópico.</span><span class="sxs-lookup"><span data-stu-id="44a4b-128">They are described in the following section of this topic.</span></span>  
  
 <span data-ttu-id="44a4b-129">O resultado de uma função de agregação é incluído no resultado da consulta como um campo do tipo de resultado da consulta.</span><span class="sxs-lookup"><span data-stu-id="44a4b-129">The result of an aggregate function is included in the query result as a field of the query result type.</span></span> <span data-ttu-id="44a4b-130">Você pode fornecer um alias para o resultado da função de agregação para especificar o nome do membro do tipo de resultado da consulta que conterá o valor de agregação.</span><span class="sxs-lookup"><span data-stu-id="44a4b-130">You can supply an alias for the aggregate function result to specify the name of the member of the query result type that will hold the aggregate value.</span></span> <span data-ttu-id="44a4b-131">Se nenhum alias for fornecido, o nome da função de agregação será usado.</span><span class="sxs-lookup"><span data-stu-id="44a4b-131">If no alias is supplied, the name of the aggregate function is used.</span></span>  
  
 <span data-ttu-id="44a4b-132">A `Aggregate` cláusula pode iniciar uma consulta ou pode ser incluída como uma cláusula adicional em uma consulta.</span><span class="sxs-lookup"><span data-stu-id="44a4b-132">The `Aggregate` clause can begin a query, or it can be included as an additional clause in a query.</span></span> <span data-ttu-id="44a4b-133">Se a `Aggregate` cláusula iniciar uma consulta, o resultado será um valor único que é o resultado da função de agregação especificada na `Into` cláusula.</span><span class="sxs-lookup"><span data-stu-id="44a4b-133">If the `Aggregate` clause begins a query, the result is a single value that is the result of the aggregate function specified in the `Into` clause.</span></span> <span data-ttu-id="44a4b-134">Se mais de uma função de agregação for especificada na `Into` cláusula, a consulta retornará um único tipo com uma propriedade separada para referenciar o resultado de cada função de agregação na `Into` cláusula.</span><span class="sxs-lookup"><span data-stu-id="44a4b-134">If more than one aggregate function is specified in the `Into` clause, the query returns a single type with a separate property to reference the result of each aggregate function in the `Into` clause.</span></span> <span data-ttu-id="44a4b-135">Se a `Aggregate` cláusula for incluída como uma cláusula adicional em uma consulta, o tipo retornado na coleção de consulta terá uma propriedade separada para referenciar o resultado de cada função de agregação na `Into` cláusula.</span><span class="sxs-lookup"><span data-stu-id="44a4b-135">If the `Aggregate` clause is included as an additional clause in a query, the type returned in the query collection will have a separate property to reference the result of each aggregate function in the `Into` clause.</span></span>  
  
## <a name="aggregate-functions"></a><span data-ttu-id="44a4b-136">Funções de Agregação</span><span class="sxs-lookup"><span data-stu-id="44a4b-136">Aggregate Functions</span></span>

<span data-ttu-id="44a4b-137">A seguir estão as funções de agregação padrão que podem ser usadas com a `Aggregate` cláusula.</span><span class="sxs-lookup"><span data-stu-id="44a4b-137">The following are the standard aggregate functions that can be used with the `Aggregate` clause.</span></span>  
  
### <a name="all"></a><span data-ttu-id="44a4b-138">Tudo</span><span class="sxs-lookup"><span data-stu-id="44a4b-138">All</span></span>

<span data-ttu-id="44a4b-139">Retorna `true` se todos os elementos na coleção atendem a uma condição especificada; caso contrário, retorna `false` .</span><span class="sxs-lookup"><span data-stu-id="44a4b-139">Returns `true` if all elements in the collection satisfy a specified condition; otherwise returns `false`.</span></span> <span data-ttu-id="44a4b-140">A seguir, é mostrado um exemplo:</span><span class="sxs-lookup"><span data-stu-id="44a4b-140">The following is an example:</span></span>

 [!code-vb[VbSimpleQuerySamples#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#5)]

### <a name="any"></a><span data-ttu-id="44a4b-141">Qualquer</span><span class="sxs-lookup"><span data-stu-id="44a4b-141">Any</span></span>

<span data-ttu-id="44a4b-142">Retorna `true` se qualquer elemento na coleção satisfizer uma condição especificada; caso contrário, retornará `false` .</span><span class="sxs-lookup"><span data-stu-id="44a4b-142">Returns `true` if any element in the collection satisfies a specified condition; otherwise returns `false`.</span></span> <span data-ttu-id="44a4b-143">A seguir, é mostrado um exemplo:</span><span class="sxs-lookup"><span data-stu-id="44a4b-143">The following is an example:</span></span>

 [!code-vb[VbSimpleQuerySamples#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#6)]

### <a name="average"></a><span data-ttu-id="44a4b-144">Média</span><span class="sxs-lookup"><span data-stu-id="44a4b-144">Average</span></span>

<span data-ttu-id="44a4b-145">Calcula a média de todos os elementos na coleção ou computa uma expressão fornecida para todos os elementos na coleção.</span><span class="sxs-lookup"><span data-stu-id="44a4b-145">Computes the average of all elements in the collection, or computes a supplied expression for all elements in the collection.</span></span> <span data-ttu-id="44a4b-146">A seguir, é mostrado um exemplo:</span><span class="sxs-lookup"><span data-stu-id="44a4b-146">The following is an example:</span></span>

 [!code-vb[VbSimpleQuerySamples#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#7)]

### <a name="count"></a><span data-ttu-id="44a4b-147">Contagem</span><span class="sxs-lookup"><span data-stu-id="44a4b-147">Count</span></span>

<span data-ttu-id="44a4b-148">Conta o número de elementos na coleção.</span><span class="sxs-lookup"><span data-stu-id="44a4b-148">Counts the number of elements in the collection.</span></span> <span data-ttu-id="44a4b-149">Você pode fornecer uma `Boolean` expressão opcional para contar apenas o número de elementos na coleção que atendem a uma condição.</span><span class="sxs-lookup"><span data-stu-id="44a4b-149">You can supply an optional `Boolean` expression to count only the number of elements in the collection that satisfy a condition.</span></span> <span data-ttu-id="44a4b-150">A seguir, é mostrado um exemplo:</span><span class="sxs-lookup"><span data-stu-id="44a4b-150">The following is an example:</span></span>

 [!code-vb[VbSimpleQuerySamples#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#8)]

### <a name="group"></a><span data-ttu-id="44a4b-151">Agrupar</span><span class="sxs-lookup"><span data-stu-id="44a4b-151">Group</span></span>

<span data-ttu-id="44a4b-152">Refere-se aos resultados da consulta que são agrupados como resultado de uma `Group By` `Group Join` cláusula or.</span><span class="sxs-lookup"><span data-stu-id="44a4b-152">Refers to query results that are grouped as a result of a `Group By` or `Group Join` clause.</span></span> <span data-ttu-id="44a4b-153">A `Group` função é válida somente na `Into` cláusula de uma `Group By` cláusula or `Group Join` .</span><span class="sxs-lookup"><span data-stu-id="44a4b-153">The `Group` function is valid only in the `Into` clause of a `Group By` or `Group Join` clause.</span></span> <span data-ttu-id="44a4b-154">Para obter mais informações e exemplos, consulte cláusula [Group by](group-by-clause.md) e Group [Join](group-join-clause.md).</span><span class="sxs-lookup"><span data-stu-id="44a4b-154">For more information and examples, see [Group By Clause](group-by-clause.md) and [Group Join Clause](group-join-clause.md).</span></span>

### <a name="longcount"></a><span data-ttu-id="44a4b-155">LongCount</span><span class="sxs-lookup"><span data-stu-id="44a4b-155">LongCount</span></span>

<span data-ttu-id="44a4b-156">Conta o número de elementos na coleção.</span><span class="sxs-lookup"><span data-stu-id="44a4b-156">Counts the number of elements in the collection.</span></span> <span data-ttu-id="44a4b-157">Você pode fornecer uma `Boolean` expressão opcional para contar apenas o número de elementos na coleção que atendem a uma condição.</span><span class="sxs-lookup"><span data-stu-id="44a4b-157">You can supply an optional `Boolean` expression to count only the number of elements in the collection that satisfy a condition.</span></span> <span data-ttu-id="44a4b-158">Retorna o resultado como um `Long` .</span><span class="sxs-lookup"><span data-stu-id="44a4b-158">Returns the result as a `Long`.</span></span> <span data-ttu-id="44a4b-159">Para obter um exemplo, consulte a `Count` função de agregação.</span><span class="sxs-lookup"><span data-stu-id="44a4b-159">For an example, see the `Count` aggregate function.</span></span>

### <a name="max"></a><span data-ttu-id="44a4b-160">Max</span><span class="sxs-lookup"><span data-stu-id="44a4b-160">Max</span></span>

<span data-ttu-id="44a4b-161">Computa o valor máximo da coleção ou computa uma expressão fornecida para todos os elementos na coleção.</span><span class="sxs-lookup"><span data-stu-id="44a4b-161">Computes the maximum value from the collection, or computes a supplied expression for all elements in the collection.</span></span> <span data-ttu-id="44a4b-162">A seguir, é mostrado um exemplo:</span><span class="sxs-lookup"><span data-stu-id="44a4b-162">The following is an example:</span></span>

 [!code-vb[VbSimpleQuerySamples#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#9)]

### <a name="min"></a><span data-ttu-id="44a4b-163">Mín</span><span class="sxs-lookup"><span data-stu-id="44a4b-163">Min</span></span>

<span data-ttu-id="44a4b-164">Computa o valor mínimo da coleção ou computa uma expressão fornecida para todos os elementos na coleção.</span><span class="sxs-lookup"><span data-stu-id="44a4b-164">Computes the minimum value from the collection, or computes a supplied expression for all elements in the collection.</span></span> <span data-ttu-id="44a4b-165">A seguir, é mostrado um exemplo:</span><span class="sxs-lookup"><span data-stu-id="44a4b-165">The following is an example:</span></span>

 [!code-vb[VbSimpleQuerySamples#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#10)]

### <a name="sum"></a><span data-ttu-id="44a4b-166">Soma</span><span class="sxs-lookup"><span data-stu-id="44a4b-166">Sum</span></span>

<span data-ttu-id="44a4b-167">Computa a soma de todos os elementos na coleção ou computa uma expressão fornecida para todos os elementos na coleção.</span><span class="sxs-lookup"><span data-stu-id="44a4b-167">Computes the sum of all elements in the collection, or computes a supplied expression for all elements in the collection.</span></span> <span data-ttu-id="44a4b-168">A seguir, é mostrado um exemplo:</span><span class="sxs-lookup"><span data-stu-id="44a4b-168">The following is an example:</span></span>

 [!code-vb[VbSimpleQuerySamples#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#15)]

## <a name="example"></a><span data-ttu-id="44a4b-169">Exemplo</span><span class="sxs-lookup"><span data-stu-id="44a4b-169">Example</span></span>  

<span data-ttu-id="44a4b-170">O exemplo a seguir mostra como usar a `Aggregate` cláusula para aplicar funções de agregação a um resultado de consulta.</span><span class="sxs-lookup"><span data-stu-id="44a4b-170">The following example shows how to use the `Aggregate` clause to apply aggregate functions to a query result.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#4)]  
  
## <a name="creating-user-defined-aggregate-functions"></a><span data-ttu-id="44a4b-171">Criando funções de agregação definidas pelo usuário</span><span class="sxs-lookup"><span data-stu-id="44a4b-171">Creating User-Defined Aggregate Functions</span></span>

 <span data-ttu-id="44a4b-172">Você pode incluir suas próprias funções de agregação personalizadas em uma expressão de consulta adicionando métodos de extensão ao <xref:System.Collections.Generic.IEnumerable%601> tipo.</span><span class="sxs-lookup"><span data-stu-id="44a4b-172">You can include your own custom aggregate functions in a query expression by adding extension methods to the <xref:System.Collections.Generic.IEnumerable%601> type.</span></span> <span data-ttu-id="44a4b-173">O método personalizado pode então executar um cálculo ou uma operação na coleção enumerável que referenciou sua função de agregação.</span><span class="sxs-lookup"><span data-stu-id="44a4b-173">Your custom method can then perform a calculation or operation on the enumerable collection that has referenced your aggregate function.</span></span> <span data-ttu-id="44a4b-174">Para obter mais informações sobre os métodos de extensão, consulte [Métodos de extensão](../../programming-guide/language-features/procedures/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="44a4b-174">For more information about extension methods, see [Extension Methods](../../programming-guide/language-features/procedures/extension-methods.md).</span></span>  
  
 <span data-ttu-id="44a4b-175">Por exemplo, o exemplo a seguir mostra uma função de agregação personalizada que calcula o valor mediano de uma coleção de números.</span><span class="sxs-lookup"><span data-stu-id="44a4b-175">For example, the following example shows a custom aggregate function that calculates the median value of a collection of numbers.</span></span> <span data-ttu-id="44a4b-176">Há duas sobrecargas do método de `Median` extensão.</span><span class="sxs-lookup"><span data-stu-id="44a4b-176">There are two overloads of the `Median` extension method.</span></span> <span data-ttu-id="44a4b-177">A primeira sobrecarga aceita, como entrada, uma coleção do tipo `IEnumerable(Of Double)` .</span><span class="sxs-lookup"><span data-stu-id="44a4b-177">The first overload accepts, as input, a collection of type `IEnumerable(Of Double)`.</span></span> <span data-ttu-id="44a4b-178">Se a `Median` função de agregação for chamada para um campo de consulta do tipo `Double` , esse método será chamado.</span><span class="sxs-lookup"><span data-stu-id="44a4b-178">If the `Median` aggregate function is called for a query field of type `Double`, this method will be called.</span></span> <span data-ttu-id="44a4b-179">A segunda sobrecarga do `Median` método pode ser passada para qualquer tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="44a4b-179">The second overload of the `Median` method can be passed any generic type.</span></span> <span data-ttu-id="44a4b-180">A sobrecarga genérica do `Median` método usa um segundo parâmetro que faz referência à `Func(Of T, Double)` expressão lambda para projetar um valor para um tipo (de uma coleção) como o valor correspondente do tipo `Double` .</span><span class="sxs-lookup"><span data-stu-id="44a4b-180">The generic overload of the `Median` method takes a second parameter that references the `Func(Of T, Double)` lambda expression to project a value for a type (from a collection) as the corresponding value of type `Double`.</span></span> <span data-ttu-id="44a4b-181">Em seguida, ele delega o cálculo do valor mediano para a outra sobrecarga do `Median` método.</span><span class="sxs-lookup"><span data-stu-id="44a4b-181">It then delegates the calculation of the median value to the other overload of the `Median` method.</span></span> <span data-ttu-id="44a4b-182">Para obter mais informações sobre expressões lambda, consulte [expressões lambda](../../programming-guide/language-features/procedures/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="44a4b-182">For more information about lambda expressions, see [Lambda Expressions](../../programming-guide/language-features/procedures/lambda-expressions.md).</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/UserDefinedAggregates.vb#18)]  
  
 <span data-ttu-id="44a4b-183">O exemplo a seguir mostra as consultas de exemplo que chamam a `Median` função de agregação em uma coleção do tipo `Integer` e uma coleção do tipo `Double` .</span><span class="sxs-lookup"><span data-stu-id="44a4b-183">The following example shows sample queries that call the `Median` aggregate function on a collection of type `Integer`, and a collection of type `Double`.</span></span> <span data-ttu-id="44a4b-184">A consulta que chama a `Median` função de agregação na coleção de tipo `Double` chama a sobrecarga do `Median` método que aceita, como entrada, uma coleção do tipo `Double` .</span><span class="sxs-lookup"><span data-stu-id="44a4b-184">The query that calls the `Median` aggregate function on the collection of type `Double` calls the overload of the `Median` method that accepts, as input, a collection of type `Double`.</span></span> <span data-ttu-id="44a4b-185">A consulta que chama a `Median` função de agregação na coleção de tipo `Integer` chama a sobrecarga genérica do `Median` método.</span><span class="sxs-lookup"><span data-stu-id="44a4b-185">The query that calls the `Median` aggregate function on the collection of type `Integer` calls the generic overload of the `Median` method.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/UserDefinedAggregates.vb#19)]  
  
## <a name="see-also"></a><span data-ttu-id="44a4b-186">Confira também</span><span class="sxs-lookup"><span data-stu-id="44a4b-186">See also</span></span>

- [<span data-ttu-id="44a4b-187">Introdução a LINQ no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="44a4b-187">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="44a4b-188">Consultas</span><span class="sxs-lookup"><span data-stu-id="44a4b-188">Queries</span></span>](index.md)
- [<span data-ttu-id="44a4b-189">Cláusula SELECT</span><span class="sxs-lookup"><span data-stu-id="44a4b-189">Select Clause</span></span>](select-clause.md)
- [<span data-ttu-id="44a4b-190">Cláusula from</span><span class="sxs-lookup"><span data-stu-id="44a4b-190">From Clause</span></span>](from-clause.md)
- [<span data-ttu-id="44a4b-191">Cláusula WHERE</span><span class="sxs-lookup"><span data-stu-id="44a4b-191">Where Clause</span></span>](where-clause.md)
- [<span data-ttu-id="44a4b-192">Cláusula Group By</span><span class="sxs-lookup"><span data-stu-id="44a4b-192">Group By Clause</span></span>](group-by-clause.md)
