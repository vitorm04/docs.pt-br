---
title: Funções definidas pelo usuário
ms.date: 12/13/2019
description: Saiba como criar funções escalares e de agregação definidas pelo usuário.
ms.openlocfilehash: 9ee3fbac73215353c8dc82199203b0d25e580cdb
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447170"
---
# <a name="user-defined-functions"></a><span data-ttu-id="37dfa-103">Funções definidas pelo usuário</span><span class="sxs-lookup"><span data-stu-id="37dfa-103">User-defined functions</span></span>

<span data-ttu-id="37dfa-104">A maioria dos bancos de dados tem um dialeto de procedimento do SQL que você pode usar para definir suas próprias funções.</span><span class="sxs-lookup"><span data-stu-id="37dfa-104">Most databases have a procedural dialect of SQL that you can use to define your own functions.</span></span> <span data-ttu-id="37dfa-105">No entanto, o SQLite é executado em processo com seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="37dfa-105">SQLite however, runs in-process with your app.</span></span> <span data-ttu-id="37dfa-106">Em vez de ter que aprender um novo dialeto do SQL, você pode usar apenas a linguagem de programação do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="37dfa-106">Instead of having to learn a new dialect of SQL, you can just use the programming language of your app.</span></span>

## <a name="scalar-functions"></a><span data-ttu-id="37dfa-107">Funções escalares</span><span class="sxs-lookup"><span data-stu-id="37dfa-107">Scalar functions</span></span>

<span data-ttu-id="37dfa-108">As funções escalares retornam um valor escalar único para cada linha em uma consulta.</span><span class="sxs-lookup"><span data-stu-id="37dfa-108">Scalar functions return a single, scalar value for each row in a query.</span></span> <span data-ttu-id="37dfa-109">Defina novas funções escalares e substitua as internas usando <xref:Microsoft.Data.Sqlite.SqliteConnection.CreateFunction%2A>.</span><span class="sxs-lookup"><span data-stu-id="37dfa-109">Define new scalar functions and override the built-in ones using <xref:Microsoft.Data.Sqlite.SqliteConnection.CreateFunction%2A>.</span></span>

<span data-ttu-id="37dfa-110">Consulte [tipos de dados](types.md) para obter uma lista de parâmetros com suporte e tipos de retorno para o argumento `func`.</span><span class="sxs-lookup"><span data-stu-id="37dfa-110">See [Data types](types.md) for a list of supported parameter and return types for the `func` argument.</span></span>

<span data-ttu-id="37dfa-111">A especificação do argumento `state` passará esse valor para cada invocação da função.</span><span class="sxs-lookup"><span data-stu-id="37dfa-111">Specifying the `state` argument will pass that value into every invocation of the function.</span></span> <span data-ttu-id="37dfa-112">Use isso para evitar fechamentos.</span><span class="sxs-lookup"><span data-stu-id="37dfa-112">Use this to avoid closures.</span></span>

<span data-ttu-id="37dfa-113">Especifique `isDeterministic` se sua função for determinística para permitir que o SQLite use otimizações adicionais ao compilar consultas.</span><span class="sxs-lookup"><span data-stu-id="37dfa-113">Specify `isDeterministic` if your function is deterministic to allow SQLite to use additional optimizations when compiling queries.</span></span>

<span data-ttu-id="37dfa-114">O exemplo a seguir mostra como adicionar uma função escalar para calcular o raio de um cilindro.</span><span class="sxs-lookup"><span data-stu-id="37dfa-114">The following example shows how to add a scalar function to calculate the radius of a cylinder.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/ScalarFunctionSample/Program.cs?name=snippet_CreateFunction)]

## <a name="operators"></a><span data-ttu-id="37dfa-115">Operadores</span><span class="sxs-lookup"><span data-stu-id="37dfa-115">Operators</span></span>

<span data-ttu-id="37dfa-116">Os seguintes operadores SQLite são implementados pelas funções escalares correspondentes.</span><span class="sxs-lookup"><span data-stu-id="37dfa-116">The following SQLite operators are implemented by corresponding scalar functions.</span></span> <span data-ttu-id="37dfa-117">Definir essas funções escalares em seu aplicativo substituirá o comportamento desses operadores.</span><span class="sxs-lookup"><span data-stu-id="37dfa-117">Defining these scalar functions in your app will override the behavior of these operators.</span></span>

| <span data-ttu-id="37dfa-118">Operador</span><span class="sxs-lookup"><span data-stu-id="37dfa-118">Operator</span></span>          | <span data-ttu-id="37dfa-119">Função</span><span class="sxs-lookup"><span data-stu-id="37dfa-119">Function</span></span>      |
| ----------------- | ------------- |
| <span data-ttu-id="37dfa-120">X GLOB Y</span><span class="sxs-lookup"><span data-stu-id="37dfa-120">X GLOB Y</span></span>          | <span data-ttu-id="37dfa-121">Glob (Y, X)</span><span class="sxs-lookup"><span data-stu-id="37dfa-121">glob(Y, X)</span></span>    |
| <span data-ttu-id="37dfa-122">X COMO Y</span><span class="sxs-lookup"><span data-stu-id="37dfa-122">X LIKE Y</span></span>          | <span data-ttu-id="37dfa-123">Like (Y, X)</span><span class="sxs-lookup"><span data-stu-id="37dfa-123">like(Y, X)</span></span>    |
| <span data-ttu-id="37dfa-124">X COMO Y ESCAPE Z</span><span class="sxs-lookup"><span data-stu-id="37dfa-124">X LIKE Y ESCAPE Z</span></span> | <span data-ttu-id="37dfa-125">Like (Y, X, Z)</span><span class="sxs-lookup"><span data-stu-id="37dfa-125">like(Y, X, Z)</span></span> |
| <span data-ttu-id="37dfa-126">X CORRESPONDÊNCIA Y</span><span class="sxs-lookup"><span data-stu-id="37dfa-126">X MATCH Y</span></span>         | <span data-ttu-id="37dfa-127">corresponder (Y, X)</span><span class="sxs-lookup"><span data-stu-id="37dfa-127">match(Y, X)</span></span>   |
| <span data-ttu-id="37dfa-128">X REGEXP Y</span><span class="sxs-lookup"><span data-stu-id="37dfa-128">X REGEXP Y</span></span>        | <span data-ttu-id="37dfa-129">RegExp (Y, X)</span><span class="sxs-lookup"><span data-stu-id="37dfa-129">regexp(Y, X)</span></span>  |

<span data-ttu-id="37dfa-130">O exemplo a seguir mostra como definir a função RegExp para habilitar seu operador correspondente.</span><span class="sxs-lookup"><span data-stu-id="37dfa-130">The following example shows how to define the regexp function to enable its corresponding operator.</span></span> <span data-ttu-id="37dfa-131">O SQLite não inclui uma implementação padrão da função RegExp.</span><span class="sxs-lookup"><span data-stu-id="37dfa-131">SQLite doesn't include a default implementation of the regexp function.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/RegularExpressionSample/Program.cs?name=snippet_Regex)]

## <a name="aggregate-functions"></a><span data-ttu-id="37dfa-132">Funções de Agregação</span><span class="sxs-lookup"><span data-stu-id="37dfa-132">Aggregate functions</span></span>

<span data-ttu-id="37dfa-133">As funções de agregação retornam um valor agregado único para todas as linhas em uma consulta.</span><span class="sxs-lookup"><span data-stu-id="37dfa-133">Aggregate functions return a single, aggregated value for all the rows in a query.</span></span> <span data-ttu-id="37dfa-134">Definir e substituir funções de agregação usando <xref:Microsoft.Data.Sqlite.SqliteConnection.CreateAggregate%2A>.</span><span class="sxs-lookup"><span data-stu-id="37dfa-134">Define and override aggregate functions using <xref:Microsoft.Data.Sqlite.SqliteConnection.CreateAggregate%2A>.</span></span>

<span data-ttu-id="37dfa-135">O argumento `seed` especifica o estado inicial do contexto.</span><span class="sxs-lookup"><span data-stu-id="37dfa-135">The `seed` argument specifies the initial state of the context.</span></span> <span data-ttu-id="37dfa-136">Use isso para evitar fechamentos também.</span><span class="sxs-lookup"><span data-stu-id="37dfa-136">Use this to avoid closures also.</span></span>

<span data-ttu-id="37dfa-137">O argumento `func` é invocado uma vez por linha.</span><span class="sxs-lookup"><span data-stu-id="37dfa-137">The `func` argument is invoked once per row.</span></span> <span data-ttu-id="37dfa-138">Use o contexto para acumular um resultado final.</span><span class="sxs-lookup"><span data-stu-id="37dfa-138">Use the context to accumulate a final result.</span></span> <span data-ttu-id="37dfa-139">Retornar o contexto.</span><span class="sxs-lookup"><span data-stu-id="37dfa-139">Return the context.</span></span> <span data-ttu-id="37dfa-140">Esse padrão permite que o contexto seja um tipo de valor ou imutável.</span><span class="sxs-lookup"><span data-stu-id="37dfa-140">This pattern allows the context to be a value type or immutable.</span></span>

<span data-ttu-id="37dfa-141">Se nenhum `resultSelector` for especificado, o estado final do contexto será usado como resultado.</span><span class="sxs-lookup"><span data-stu-id="37dfa-141">If no `resultSelector` is specified, the final state of the context is used as the result.</span></span> <span data-ttu-id="37dfa-142">Isso pode simplificar a definição de funções como Sum e Count que precisam apenas incrementar um número cada linha e retorná-la.</span><span class="sxs-lookup"><span data-stu-id="37dfa-142">This can simplify the definition of functions like sum and count that only need to increment a number each row and return it.</span></span>

<span data-ttu-id="37dfa-143">Especifique `resultSelector` para calcular o resultado final do contexto depois de iterar por todas as linhas.</span><span class="sxs-lookup"><span data-stu-id="37dfa-143">Specify `resultSelector` to calculate the final result from the context after iterating through all the rows.</span></span>

<span data-ttu-id="37dfa-144">Consulte [tipos de dados](types.md) para obter uma lista de tipos de parâmetro com suporte para o argumento `func` e tipos de retorno para `resultSelector`.</span><span class="sxs-lookup"><span data-stu-id="37dfa-144">See [Data types](types.md) for a list of supported parameter types for the `func` argument and return types for `resultSelector`.</span></span>

<span data-ttu-id="37dfa-145">Se sua função for determinística, especifique `isDeterministic` para permitir que o SQLite use otimizações adicionais ao compilar consultas.</span><span class="sxs-lookup"><span data-stu-id="37dfa-145">If your function is deterministic, specify `isDeterministic` to allow SQLite to use additional optimizations when compiling queries.</span></span>

<span data-ttu-id="37dfa-146">O exemplo a seguir define uma função de agregação para calcular o desvio padrão de uma coluna.</span><span class="sxs-lookup"><span data-stu-id="37dfa-146">The following example defines an aggregate function to calculate the standard deviation of a column.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/AggregateFunctionSample/Program.cs?name=snippet_CreateAggregate)]

## <a name="errors"></a><span data-ttu-id="37dfa-147">Erros do</span><span class="sxs-lookup"><span data-stu-id="37dfa-147">Errors</span></span>

<span data-ttu-id="37dfa-148">Se uma função definida pelo usuário lançar uma exceção, a mensagem será retornada para o SQLite.</span><span class="sxs-lookup"><span data-stu-id="37dfa-148">If a user-defined function throws an exception, the message is returned to SQLite.</span></span> <span data-ttu-id="37dfa-149">O SQLite irá gerar um erro e o Microsoft. Data. sqlite gerará um Sqliteexception.</span><span class="sxs-lookup"><span data-stu-id="37dfa-149">SQLite will then raise an error and Microsoft.Data.Sqlite will throw a SqliteException.</span></span> <span data-ttu-id="37dfa-150">Para obter mais informações, consulte [erros de banco de dados](database-errors.md).</span><span class="sxs-lookup"><span data-stu-id="37dfa-150">For more information, see [Database errors](database-errors.md).</span></span>

<span data-ttu-id="37dfa-151">Por padrão, o código de erro do SQLite de erro será SQLITE_ERROR (ou 1).</span><span class="sxs-lookup"><span data-stu-id="37dfa-151">By default, the error SQLite error code will be SQLITE_ERROR (or 1).</span></span> <span data-ttu-id="37dfa-152">No entanto, você pode alterá-lo lançando um <xref:Microsoft.Data.Sqlite.SqliteException> em sua função com o <xref:Microsoft.Data.Sqlite.SqliteException.SqliteErrorCode> desejado especificado.</span><span class="sxs-lookup"><span data-stu-id="37dfa-152">You can, however, change it by throwing a <xref:Microsoft.Data.Sqlite.SqliteException> in your function with the desired <xref:Microsoft.Data.Sqlite.SqliteException.SqliteErrorCode> specified.</span></span>

## <a name="debugging"></a><span data-ttu-id="37dfa-153">{1&gt;Depuração&lt;1}</span><span class="sxs-lookup"><span data-stu-id="37dfa-153">Debugging</span></span>

<span data-ttu-id="37dfa-154">O SQLite chama sua implementação diretamente.</span><span class="sxs-lookup"><span data-stu-id="37dfa-154">SQLite calls your implementation directly.</span></span> <span data-ttu-id="37dfa-155">Isso permite que você adicione pontos de interrupção que disparam enquanto o SQLite está avaliando consultas.</span><span class="sxs-lookup"><span data-stu-id="37dfa-155">This lets you add breakpoints that trigger while SQLite is evaluating queries.</span></span> <span data-ttu-id="37dfa-156">A experiência completa de depuração do .NET está disponível para ajudá-lo a criar suas funções definidas pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="37dfa-156">The full .NET debugging experience is available to help you create your user-defined functions.</span></span>

## <a name="see-also"></a><span data-ttu-id="37dfa-157">Veja também</span><span class="sxs-lookup"><span data-stu-id="37dfa-157">See also</span></span>

* [<span data-ttu-id="37dfa-158">Tipos de dados</span><span class="sxs-lookup"><span data-stu-id="37dfa-158">Data types</span></span>](types.md)
* [<span data-ttu-id="37dfa-159">Funções principais do SQLite</span><span class="sxs-lookup"><span data-stu-id="37dfa-159">SQLite Core functions</span></span>](https://www.sqlite.org/lang_corefunc.html)
* [<span data-ttu-id="37dfa-160">Funções de agregação do SQLite</span><span class="sxs-lookup"><span data-stu-id="37dfa-160">SQLite Aggregate Functions</span></span>](https://www.sqlite.org/lang_aggfunc.html)
