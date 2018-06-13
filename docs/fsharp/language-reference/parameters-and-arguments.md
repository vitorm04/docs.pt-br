---
title: Parâmetros e argumentos (F#)
description: 'Saiba mais sobre o suporte da linguagem F # para definir parâmetros e argumentos de passagem para funções, métodos e propriedades.'
ms.date: 05/16/2016
ms.openlocfilehash: 319cf0e7346d498ce34e41a9993fe0160038461a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33566214"
---
# <a name="parameters-and-arguments"></a><span data-ttu-id="f267a-103">Parâmetros e argumentos</span><span class="sxs-lookup"><span data-stu-id="f267a-103">Parameters and Arguments</span></span>

<span data-ttu-id="f267a-104">Este tópico descreve o suporte de idioma para definir parâmetros e argumentos de passagem para funções, métodos e propriedades.</span><span class="sxs-lookup"><span data-stu-id="f267a-104">This topic describes language support for defining parameters and passing arguments to functions, methods, and properties.</span></span> <span data-ttu-id="f267a-105">Ela inclui informações sobre como passar por referência e como definir e usar os métodos que podem levar a um número variável de argumentos.</span><span class="sxs-lookup"><span data-stu-id="f267a-105">It includes information about how to pass by reference, and how to define and use methods that can take a variable number of arguments.</span></span>


## <a name="parameters-and-arguments"></a><span data-ttu-id="f267a-106">Parâmetros e argumentos</span><span class="sxs-lookup"><span data-stu-id="f267a-106">Parameters and Arguments</span></span>
<span data-ttu-id="f267a-107">O termo *parâmetro* é usado para descrever os nomes de valores que devem ser fornecidos.</span><span class="sxs-lookup"><span data-stu-id="f267a-107">The term *parameter* is used to describe the names for values that are expected to be supplied.</span></span> <span data-ttu-id="f267a-108">O termo *argumento* é usado para os valores fornecidos para cada parâmetro.</span><span class="sxs-lookup"><span data-stu-id="f267a-108">The term *argument* is used for the values provided for each parameter.</span></span>

<span data-ttu-id="f267a-109">Parâmetros podem ser especificados na tupla ou um formulário na forma curried, ou em uma combinação dos dois.</span><span class="sxs-lookup"><span data-stu-id="f267a-109">Parameters can be specified in tuple or curried form, or in some combination of the two.</span></span> <span data-ttu-id="f267a-110">Você pode passar argumentos usando um nome de parâmetro explícito.</span><span class="sxs-lookup"><span data-stu-id="f267a-110">You can pass arguments by using an explicit parameter name.</span></span> <span data-ttu-id="f267a-111">Parâmetros de métodos podem ser especificados como opcionais e recebe um valor padrão.</span><span class="sxs-lookup"><span data-stu-id="f267a-111">Parameters of methods can be specified as optional and given a default value.</span></span>


## <a name="parameter-patterns"></a><span data-ttu-id="f267a-112">Padrões de parâmetro</span><span class="sxs-lookup"><span data-stu-id="f267a-112">Parameter Patterns</span></span>
<span data-ttu-id="f267a-113">Em geral, os parâmetros fornecidos para funções e métodos são padrões separados por espaços.</span><span class="sxs-lookup"><span data-stu-id="f267a-113">Parameters supplied to functions and methods are, in general, patterns separated by spaces.</span></span> <span data-ttu-id="f267a-114">Isso significa que, a princípio, qualquer um dos padrões descritas em [correspondência expressões](match-expressions.md) pode ser usado em uma lista de parâmetro para uma função ou um membro.</span><span class="sxs-lookup"><span data-stu-id="f267a-114">This means that, in principle, any of the patterns described in [Match Expressions](match-expressions.md) can be used in a parameter list for a function or member.</span></span>

<span data-ttu-id="f267a-115">Métodos geralmente usam o formato de tupla de argumentos de passagem.</span><span class="sxs-lookup"><span data-stu-id="f267a-115">Methods usually use the tuple form of passing arguments.</span></span> <span data-ttu-id="f267a-116">Gera um resultado mais claro da perspectiva de outras linguagens .NET porque a forma de tupla corresponde a maneira como os argumentos são passados em métodos do .NET.</span><span class="sxs-lookup"><span data-stu-id="f267a-116">This achieves a clearer result from the perspective of other .NET languages because the tuple form matches the way arguments are passed in .NET methods.</span></span>

<span data-ttu-id="f267a-117">O formulário na forma curried geralmente é usado com funções criadas usando `let` associações.</span><span class="sxs-lookup"><span data-stu-id="f267a-117">The curried form is most often used with functions created by using `let` bindings.</span></span>

<span data-ttu-id="f267a-118">O pseudocódigo a seguir mostra exemplos de tupla e argumentos na forma curried.</span><span class="sxs-lookup"><span data-stu-id="f267a-118">The following pseudocode shows examples of tuple and curried arguments.</span></span>

```fsharp
// Tuple form.
member this.SomeMethod(param1, param2) = ...
// Curried form.
let function1 param1 param2 = ...
```

<span data-ttu-id="f267a-119">Formulários combinados são possíveis quando alguns argumentos são em tuplas e outros não.</span><span class="sxs-lookup"><span data-stu-id="f267a-119">Combined forms are possible when some arguments are in tuples and some are not.</span></span>

```fsharp
let function2 param1 (param2a, param2b) param3 = ...
```

<span data-ttu-id="f267a-120">Outros padrões também podem ser usados em listas de parâmetros, mas se o padrão de parâmetro não corresponde a todas as entradas possíveis, pode haver uma correspondência incompleta em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="f267a-120">Other patterns can also be used in parameter lists, but if the parameter pattern does not match all possible inputs, there might be an incomplete match at run time.</span></span> <span data-ttu-id="f267a-121">A exceção `MatchFailureException` é gerado quando o valor de um argumento não coincide com os padrões especificados na lista de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="f267a-121">The exception `MatchFailureException` is generated when the value of an argument does not match the patterns specified in the parameter list.</span></span> <span data-ttu-id="f267a-122">O compilador emite um aviso quando um padrão de parâmetro permite correspondências incompletas.</span><span class="sxs-lookup"><span data-stu-id="f267a-122">The compiler issues a warning when a parameter pattern allows for incomplete matches.</span></span> <span data-ttu-id="f267a-123">Pelo menos um outro padrão é normalmente útil para listas de parâmetros e que é o padrão de curinga.</span><span class="sxs-lookup"><span data-stu-id="f267a-123">At least one other pattern is commonly useful for parameter lists, and that is the wildcard pattern.</span></span> <span data-ttu-id="f267a-124">Você pode usar o padrão de curinga em uma lista de parâmetros quando você deseja simplesmente ignorar quaisquer argumentos fornecidos.</span><span class="sxs-lookup"><span data-stu-id="f267a-124">You use the wildcard pattern in a parameter list when you simply want to ignore any arguments that are supplied.</span></span> <span data-ttu-id="f267a-125">O código a seguir ilustra o uso do padrão de curinga em uma lista de argumentos.</span><span class="sxs-lookup"><span data-stu-id="f267a-125">The following code illustrates the use of the wildcard pattern in an argument list.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3801.fs)]

<span data-ttu-id="f267a-126">O padrão de curinga pode ser útil sempre que você não precisa de argumentos passados, como o ponto de entrada principal para um programa, quando você não estiver interessado nos argumentos de linha de comando que normalmente são fornecidos como uma matriz de cadeia de caracteres, como no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="f267a-126">The wildcard pattern can be useful whenever you do not need the arguments passed in, such as in the main entry point to a program, when you are not interested in the command-line arguments that are normally supplied as a string array, as in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3802.fs)]

<span data-ttu-id="f267a-127">Outros padrões que às vezes são usados nos argumentos são o `as` padrão e padrões de identificador associados uniões discriminadas e padrões ativos.</span><span class="sxs-lookup"><span data-stu-id="f267a-127">Other patterns that are sometimes used in arguments are the `as` pattern, and identifier patterns associated with discriminated unions and active patterns.</span></span> <span data-ttu-id="f267a-128">Você pode usar o padrão de união discriminado único caso, da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="f267a-128">You can use the single-case discriminated union pattern as follows.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3803.fs)]

<span data-ttu-id="f267a-129">A saída é a seguinte.</span><span class="sxs-lookup"><span data-stu-id="f267a-129">The output is as follows.</span></span>

```
Data begins at 0 and ends at 4 in string Et tu, Brute?
Et tu
```

<span data-ttu-id="f267a-130">Padrões ativos podem ser útil como parâmetros, por exemplo, ao transformar um argumento em um formato desejado, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="f267a-130">Active patterns can be useful as parameters, for example, when transforming an argument into a desired format, as in the following example:</span></span>

```fsharp
type Point = { x : float; y : float }

let (| Polar |) { x = x; y = y} =
    ( sqrt (x*x + y*y), System.Math.Atan (y/ x) )

let radius (Polar(r, _)) = r
let angle (Polar(_, theta)) = theta
```

<span data-ttu-id="f267a-131">Você pode usar o `as` padrão para armazenar um valor correspondente como um valor local, conforme é mostrado na seguinte linha de código.</span><span class="sxs-lookup"><span data-stu-id="f267a-131">You can use the `as` pattern to store a matched value as a local value, as is shown in the following line of code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3805.fs)]

<span data-ttu-id="f267a-132">Outro padrão que é usado ocasionalmente é uma função que deixa o último argumento sem nome, fornecendo, como o corpo da função, uma expressão lambda que executa uma correspondência de padrão imediatamente no argumento implícita.</span><span class="sxs-lookup"><span data-stu-id="f267a-132">Another pattern that is used occasionally is a function that leaves the last argument unnamed by providing, as the body of the function, a lambda expression that immediately performs a pattern match on the implicit argument.</span></span> <span data-ttu-id="f267a-133">Um exemplo disso é a seguinte linha de código.</span><span class="sxs-lookup"><span data-stu-id="f267a-133">An example of this is the following line of code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3804.fs)]

<span data-ttu-id="f267a-134">Esse código define uma função que usa uma lista genérica e retorna `true` se a lista estiver vazia, e `false` caso contrário.</span><span class="sxs-lookup"><span data-stu-id="f267a-134">This code defines a function that takes a generic list and returns `true` if the list is empty, and `false` otherwise.</span></span> <span data-ttu-id="f267a-135">O uso dessas técnicas pode tornar o código mais difícil de ler.</span><span class="sxs-lookup"><span data-stu-id="f267a-135">The use of such techniques can make code more difficult to read.</span></span>

<span data-ttu-id="f267a-136">Ocasionalmente, padrões que envolvem incompletas correspondências são úteis, por exemplo, se você souber que as listas em seu programa tem somente três elementos, você pode usar um padrão semelhante ao seguinte em uma lista de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="f267a-136">Occasionally, patterns that involve incomplete matches are useful, for example, if you know that the lists in your program have only three elements, you might use a pattern like the following in a parameter list.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3806.fs)]

<span data-ttu-id="f267a-137">O uso de padrões de correspondência incompleta melhor é reservado para a rápida criação de protótipos e outros usos temporários.</span><span class="sxs-lookup"><span data-stu-id="f267a-137">The use of patterns that have incomplete matches is best reserved for quick prototyping and other temporary uses.</span></span> <span data-ttu-id="f267a-138">O compilador emite um aviso para esse tipo de código.</span><span class="sxs-lookup"><span data-stu-id="f267a-138">The compiler will issue a warning for such code.</span></span> <span data-ttu-id="f267a-139">Esses padrões não podem abranger o caso geral de todas as entradas de possíveis e, portanto, não são adequados para APIs de componente.</span><span class="sxs-lookup"><span data-stu-id="f267a-139">Such patterns cannot cover the general case of all possible inputs and therefore are not suitable for component APIs.</span></span>

## <a name="named-arguments"></a><span data-ttu-id="f267a-140">Argumentos nomeados</span><span class="sxs-lookup"><span data-stu-id="f267a-140">Named Arguments</span></span>
<span data-ttu-id="f267a-141">Argumentos de métodos que podem ser especificados por posição em uma lista de argumentos separados por vírgulas ou podem ser passados para um método explicitamente fornecendo o nome, seguido por um sinal de igual e o valor a ser passado.</span><span class="sxs-lookup"><span data-stu-id="f267a-141">Arguments for methods can be specified by position in a comma-separated argument list, or they can be passed to a method explicitly by providing the name, followed by an equal sign and the value to be passed in.</span></span> <span data-ttu-id="f267a-142">Se especificado, fornecendo o nome, eles podem aparecer em uma ordem diferente daquele usado na declaração.</span><span class="sxs-lookup"><span data-stu-id="f267a-142">If specified by providing the name, they can appear in a different order from that used in the declaration.</span></span>

<span data-ttu-id="f267a-143">Argumentos nomeados podem tornar o código mais legível e mais adaptável para determinados tipos de alterações na API, como uma reorganização de parâmetros de método.</span><span class="sxs-lookup"><span data-stu-id="f267a-143">Named arguments can make code more readable and more adaptable to certain types of changes in the API, such as a reordering of method parameters.</span></span>

<span data-ttu-id="f267a-144">Argumentos nomeados são permitidos apenas para métodos, não para `let`-associados a funções, valores de função ou expressões lambda.</span><span class="sxs-lookup"><span data-stu-id="f267a-144">Named arguments are allowed only for methods, not for `let`-bound functions, function values, or lambda expressions.</span></span>

<span data-ttu-id="f267a-145">O exemplo de código a seguir demonstra o uso de argumentos nomeados.</span><span class="sxs-lookup"><span data-stu-id="f267a-145">The following code example demonstrates the use of named arguments.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3807.fs)]

<span data-ttu-id="f267a-146">Em uma chamada para um construtor de classe, você pode definir os valores das propriedades da classe usando uma sintaxe semelhante de argumentos nomeados.</span><span class="sxs-lookup"><span data-stu-id="f267a-146">In a call to a class constructor, you can set the values of properties of the class by using a syntax similar to that of named arguments.</span></span> <span data-ttu-id="f267a-147">O exemplo a seguir mostra essa sintaxe.</span><span class="sxs-lookup"><span data-stu-id="f267a-147">The following example shows this syntax.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet3506.fs)]

<span data-ttu-id="f267a-148">Para obter mais informações, consulte [construtores (F #)](https://msdn.microsoft.com/library/2cd0ed07-d214-4125-8317-4f288af99f05).</span><span class="sxs-lookup"><span data-stu-id="f267a-148">For more information, see [Constructors (F#)](https://msdn.microsoft.com/library/2cd0ed07-d214-4125-8317-4f288af99f05).</span></span>

## <a name="optional-parameters"></a><span data-ttu-id="f267a-149">Parâmetros opcionais</span><span class="sxs-lookup"><span data-stu-id="f267a-149">Optional Parameters</span></span>
<span data-ttu-id="f267a-150">Você pode especificar um parâmetro opcional para um método usando um ponto de interrogação na frente do nome de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="f267a-150">You can specify an optional parameter for a method by using a question mark in front of the parameter name.</span></span> <span data-ttu-id="f267a-151">Parâmetros opcionais são interpretados como o tipo de opção F #, para que você possa consultá-los da maneira normal que tipos de opção são consultados, usando um `match` expressão com `Some` e `None`.</span><span class="sxs-lookup"><span data-stu-id="f267a-151">Optional parameters are interpreted as the F# option type, so you can query them in the regular way that option types are queried, by using a `match` expression with `Some` and `None`.</span></span> <span data-ttu-id="f267a-152">Parâmetros opcionais são permitidos somente em membros, não em funções criados usando `let` associações.</span><span class="sxs-lookup"><span data-stu-id="f267a-152">Optional parameters are permitted only on members, not on functions created by using `let` bindings.</span></span>

<span data-ttu-id="f267a-153">Você também pode usar uma função `defaultArg`, que define um valor padrão de um argumento opcional.</span><span class="sxs-lookup"><span data-stu-id="f267a-153">You can also use a function `defaultArg`, which sets a default value of an optional argument.</span></span> <span data-ttu-id="f267a-154">O `defaultArg` função usa o parâmetro opcional, como o primeiro argumento e o valor padrão como o segundo.</span><span class="sxs-lookup"><span data-stu-id="f267a-154">The `defaultArg` function takes the optional parameter as the first argument and the default value as the second.</span></span>

<span data-ttu-id="f267a-155">O exemplo a seguir ilustra o uso de parâmetros opcionais.</span><span class="sxs-lookup"><span data-stu-id="f267a-155">The following example illustrates the use of optional parameters.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3808.fs)]

<span data-ttu-id="f267a-156">A saída é a seguinte.</span><span class="sxs-lookup"><span data-stu-id="f267a-156">The output is as follows.</span></span>

```
Baud Rate: 9600 Duplex: Full Parity: false
Baud Rate: 4800 Duplex: Half Parity: false
Baud Rate: 300 Duplex: Half Parity: true
```

## <a name="passing-by-reference"></a><span data-ttu-id="f267a-157">Passagem por referência</span><span class="sxs-lookup"><span data-stu-id="f267a-157">Passing by Reference</span></span>
<span data-ttu-id="f267a-158">F # suporta o `byref` palavra-chave, que especifica se um parâmetro é passado por referência.</span><span class="sxs-lookup"><span data-stu-id="f267a-158">F# supports the `byref` keyword, which specifies that a parameter is passed by reference.</span></span> <span data-ttu-id="f267a-159">Isso significa que as alterações para o valor são mantidas após a execução da função.</span><span class="sxs-lookup"><span data-stu-id="f267a-159">This means that any changes to the value are retained after the execution of the function.</span></span> <span data-ttu-id="f267a-160">Os valores fornecidos para um `byref` parâmetro deve ser mutável.</span><span class="sxs-lookup"><span data-stu-id="f267a-160">Values provided to a `byref` parameter must be mutable.</span></span> <span data-ttu-id="f267a-161">Como alternativa, você pode passar as células de referência do tipo apropriado.</span><span class="sxs-lookup"><span data-stu-id="f267a-161">Alternatively, you can pass reference cells of the appropriate type.</span></span>

<span data-ttu-id="f267a-162">Passagem por referência em linguagens .NET evoluído como uma maneira de retornar mais de um valor de uma função.</span><span class="sxs-lookup"><span data-stu-id="f267a-162">Passing by reference in .NET languages evolved as a way to return more than one value from a function.</span></span> <span data-ttu-id="f267a-163">Em F #, você pode retornar uma coleção de itens para essa finalidade, ou usar uma célula de referência mutável como um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="f267a-163">In F#, you can return a tuple for this purpose, or use a mutable reference cell as a parameter.</span></span> <span data-ttu-id="f267a-164">O `byref` parâmetro for fornecido principalmente para interoperabilidade com bibliotecas .NET.</span><span class="sxs-lookup"><span data-stu-id="f267a-164">The `byref` parameter is mainly provided for interoperability with .NET libraries.</span></span>

<span data-ttu-id="f267a-165">Os exemplos a seguir ilustram o uso do `byref` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="f267a-165">The following examples illustrate the use of the `byref` keyword.</span></span> <span data-ttu-id="f267a-166">Observe que quando você usa uma célula de referência como um parâmetro, você deve criar uma célula de referência como um valor nomeado e usá-lo como o parâmetro, não basta adicionar o `ref` operador conforme mostrado na primeira chamada para `Increment` no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="f267a-166">Note that when you use a reference cell as a parameter, you must create a reference cell as a named value and use that as the parameter, not just add the `ref` operator as shown in the first call to `Increment` in the following code.</span></span> <span data-ttu-id="f267a-167">Como criar uma célula de referência cria uma cópia do valor subjacente, a primeira chamada incrementa apenas um valor temporário.</span><span class="sxs-lookup"><span data-stu-id="f267a-167">Because creating a reference cell creates a copy of the underlying value, the first call just increments a temporary value.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3809.fs)]

<span data-ttu-id="f267a-168">Você pode usar uma tupla como um valor de retorno para armazenar as `out` parâmetros em métodos de biblioteca do .NET.</span><span class="sxs-lookup"><span data-stu-id="f267a-168">You can use a tuple as a return value to store any `out` parameters in .NET library methods.</span></span> <span data-ttu-id="f267a-169">Como alternativa, você pode tratar o `out` parâmetro como um `byref` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="f267a-169">Alternatively, you can treat the `out` parameter as a `byref` parameter.</span></span> <span data-ttu-id="f267a-170">O exemplo de código a seguir ilustra duas formas.</span><span class="sxs-lookup"><span data-stu-id="f267a-170">The following code example illustrates both ways.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3810.fs)]

## <a name="parameter-arrays"></a><span data-ttu-id="f267a-171">Matrizes de parâmetros</span><span class="sxs-lookup"><span data-stu-id="f267a-171">Parameter Arrays</span></span>
<span data-ttu-id="f267a-172">Ocasionalmente, é necessário definir uma função que recebe um número arbitrário de parâmetros de tipo heterogêneo.</span><span class="sxs-lookup"><span data-stu-id="f267a-172">Occasionally it is necessary to define a function that takes an arbitrary number of parameters of heterogeneous type.</span></span> <span data-ttu-id="f267a-173">Não ser prático criar todos os métodos sobrecarregados possíveis para a conta para todos os tipos que podem ser usados.</span><span class="sxs-lookup"><span data-stu-id="f267a-173">It would not be practical to create all the possible overloaded methods to account for all the types that could be used.</span></span> <span data-ttu-id="f267a-174">As implementações de .NET oferecem suporte para esses métodos por meio do recurso de matriz de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="f267a-174">The .NET implementations provide support for such methods through the parameter array feature.</span></span> <span data-ttu-id="f267a-175">Um método que usa uma matriz de parâmetros na sua assinatura pode ser fornecido com um número arbitrário de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="f267a-175">A method that takes a parameter array in its signature can be provided with an arbitrary number of parameters.</span></span> <span data-ttu-id="f267a-176">Os parâmetros são colocados em uma matriz.</span><span class="sxs-lookup"><span data-stu-id="f267a-176">The parameters are put into an array.</span></span> <span data-ttu-id="f267a-177">O tipo dos elementos da matriz determina os tipos de parâmetro que podem ser passados para a função.</span><span class="sxs-lookup"><span data-stu-id="f267a-177">The type of the array elements determines the parameter types that can be passed to the function.</span></span> <span data-ttu-id="f267a-178">Se você definir a matriz de parâmetros com `System.Object` como o tipo de elemento, em seguida, o código do cliente pode passar valores de qualquer tipo.</span><span class="sxs-lookup"><span data-stu-id="f267a-178">If you define the parameter array with `System.Object` as the element type, then client code can pass values of any type.</span></span>

<span data-ttu-id="f267a-179">Em F #, matrizes de parâmetros só podem ser definidas em métodos.</span><span class="sxs-lookup"><span data-stu-id="f267a-179">In F#, parameter arrays can only be defined in methods.</span></span> <span data-ttu-id="f267a-180">Eles não podem ser usados em autônomo ou funções que são definidas em módulos.</span><span class="sxs-lookup"><span data-stu-id="f267a-180">They cannot be used in standalone functions or functions that are defined in modules.</span></span>

<span data-ttu-id="f267a-181">Você define uma matriz de parâmetros usando o `ParamArray` atributo.</span><span class="sxs-lookup"><span data-stu-id="f267a-181">You define a parameter array by using the `ParamArray` attribute.</span></span> <span data-ttu-id="f267a-182">O `ParamArray` atributo só pode ser aplicado ao último parâmetro.</span><span class="sxs-lookup"><span data-stu-id="f267a-182">The `ParamArray` attribute can only be applied to the last parameter.</span></span>

<span data-ttu-id="f267a-183">O código a seguir ilustra os dois chamando um método de .NET que usa uma matriz de parâmetros e a definição de um tipo em F # que tem um método que usa uma matriz de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="f267a-183">The following code illustrates both calling a .NET method that takes a parameter array and the definition of a type in F# that has a method that takes a parameter array.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-2/snippet3811.fs)]

<span data-ttu-id="f267a-184">Quando executado em um projeto, a saída do código anterior é da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="f267a-184">When run in a project, the output of the previous code is as follows:</span></span>

```
a 1 10 Hello world 1 True
"a"
1
10.0
"Hello world"
1u
true
```

## <a name="see-also"></a><span data-ttu-id="f267a-185">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f267a-185">See Also</span></span>
[<span data-ttu-id="f267a-186">Membros</span><span class="sxs-lookup"><span data-stu-id="f267a-186">Members</span></span>](members/index.md)
