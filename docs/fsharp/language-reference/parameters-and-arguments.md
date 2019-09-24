---
title: Parâmetros e argumentos
description: Saiba mais F# sobre o suporte a idiomas para definir parâmetros e passar argumentos para funções, métodos e propriedades.
ms.date: 05/16/2016
ms.openlocfilehash: e8094ffbc55870b5de75acb740aa2736ec6590a5
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216829"
---
# <a name="parameters-and-arguments"></a><span data-ttu-id="df150-103">Parâmetros e argumentos</span><span class="sxs-lookup"><span data-stu-id="df150-103">Parameters and Arguments</span></span>

<span data-ttu-id="df150-104">Este tópico descreve o suporte a idiomas para definir parâmetros e passar argumentos para funções, métodos e propriedades.</span><span class="sxs-lookup"><span data-stu-id="df150-104">This topic describes language support for defining parameters and passing arguments to functions, methods, and properties.</span></span> <span data-ttu-id="df150-105">Ele inclui informações sobre como passar por referência e como definir e usar métodos que podem usar um número variável de argumentos.</span><span class="sxs-lookup"><span data-stu-id="df150-105">It includes information about how to pass by reference, and how to define and use methods that can take a variable number of arguments.</span></span>

## <a name="parameters-and-arguments"></a><span data-ttu-id="df150-106">Parâmetros e argumentos</span><span class="sxs-lookup"><span data-stu-id="df150-106">Parameters and Arguments</span></span>

<span data-ttu-id="df150-107">O *parâmetro* Term é usado para descrever os nomes de valores que devem ser fornecidos.</span><span class="sxs-lookup"><span data-stu-id="df150-107">The term *parameter* is used to describe the names for values that are expected to be supplied.</span></span> <span data-ttu-id="df150-108">O *argumento* de termo é usado para os valores fornecidos para cada parâmetro.</span><span class="sxs-lookup"><span data-stu-id="df150-108">The term *argument* is used for the values provided for each parameter.</span></span>

<span data-ttu-id="df150-109">Os parâmetros podem ser especificados no formulário tupla ou na forma curried, ou em alguma combinação dos dois.</span><span class="sxs-lookup"><span data-stu-id="df150-109">Parameters can be specified in tuple or curried form, or in some combination of the two.</span></span> <span data-ttu-id="df150-110">Você pode passar argumentos usando um nome de parâmetro explícito.</span><span class="sxs-lookup"><span data-stu-id="df150-110">You can pass arguments by using an explicit parameter name.</span></span> <span data-ttu-id="df150-111">Parâmetros de métodos podem ser especificados como opcionais e recebem um valor padrão.</span><span class="sxs-lookup"><span data-stu-id="df150-111">Parameters of methods can be specified as optional and given a default value.</span></span>

## <a name="parameter-patterns"></a><span data-ttu-id="df150-112">Padrões de parâmetro</span><span class="sxs-lookup"><span data-stu-id="df150-112">Parameter Patterns</span></span>

<span data-ttu-id="df150-113">Os parâmetros fornecidos a funções e métodos são, em geral, padrões separados por espaços.</span><span class="sxs-lookup"><span data-stu-id="df150-113">Parameters supplied to functions and methods are, in general, patterns separated by spaces.</span></span> <span data-ttu-id="df150-114">Isso significa que, em princípio, qualquer um dos padrões descritos em [expressões de correspondência](match-expressions.md) pode ser usado em uma lista de parâmetros para uma função ou um membro.</span><span class="sxs-lookup"><span data-stu-id="df150-114">This means that, in principle, any of the patterns described in [Match Expressions](match-expressions.md) can be used in a parameter list for a function or member.</span></span>

<span data-ttu-id="df150-115">Normalmente, os métodos usam a forma de tupla de argumentos de passagem.</span><span class="sxs-lookup"><span data-stu-id="df150-115">Methods usually use the tuple form of passing arguments.</span></span> <span data-ttu-id="df150-116">Isso alcança um resultado mais claro da perspectiva de outras linguagens .NET porque o formulário de tupla corresponde à maneira como os argumentos são passados em métodos .NET.</span><span class="sxs-lookup"><span data-stu-id="df150-116">This achieves a clearer result from the perspective of other .NET languages because the tuple form matches the way arguments are passed in .NET methods.</span></span>

<span data-ttu-id="df150-117">O formulário na forma curried é usado com mais frequência com funções criadas usando `let` associações.</span><span class="sxs-lookup"><span data-stu-id="df150-117">The curried form is most often used with functions created by using `let` bindings.</span></span>

<span data-ttu-id="df150-118">O pseudocódigo a seguir mostra exemplos de argumentos de tupla e na forma curried.</span><span class="sxs-lookup"><span data-stu-id="df150-118">The following pseudocode shows examples of tuple and curried arguments.</span></span>

```fsharp
// Tuple form.
member this.SomeMethod(param1, param2) = ...
// Curried form.
let function1 param1 param2 = ...
```

<span data-ttu-id="df150-119">Formulários combinados são possíveis quando alguns argumentos estão em tuplas e outros não são.</span><span class="sxs-lookup"><span data-stu-id="df150-119">Combined forms are possible when some arguments are in tuples and some are not.</span></span>

```fsharp
let function2 param1 (param2a, param2b) param3 = ...
```

<span data-ttu-id="df150-120">Outros padrões também podem ser usados em listas de parâmetros, mas se o padrão de parâmetro não corresponder a todas as entradas possíveis, poderá haver uma correspondência incompleta no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="df150-120">Other patterns can also be used in parameter lists, but if the parameter pattern does not match all possible inputs, there might be an incomplete match at run time.</span></span> <span data-ttu-id="df150-121">A exceção `MatchFailureException` é gerada quando o valor de um argumento não corresponde aos padrões especificados na lista de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="df150-121">The exception `MatchFailureException` is generated when the value of an argument does not match the patterns specified in the parameter list.</span></span> <span data-ttu-id="df150-122">O compilador emite um aviso quando um padrão de parâmetro permite correspondências incompletas.</span><span class="sxs-lookup"><span data-stu-id="df150-122">The compiler issues a warning when a parameter pattern allows for incomplete matches.</span></span> <span data-ttu-id="df150-123">Pelo menos um outro padrão é normalmente útil para listas de parâmetros, e esse é o padrão curinga.</span><span class="sxs-lookup"><span data-stu-id="df150-123">At least one other pattern is commonly useful for parameter lists, and that is the wildcard pattern.</span></span> <span data-ttu-id="df150-124">Você usa o padrão curinga em uma lista de parâmetros quando simplesmente deseja ignorar todos os argumentos fornecidos.</span><span class="sxs-lookup"><span data-stu-id="df150-124">You use the wildcard pattern in a parameter list when you simply want to ignore any arguments that are supplied.</span></span> <span data-ttu-id="df150-125">O código a seguir ilustra o uso do padrão curinga em uma lista de argumentos.</span><span class="sxs-lookup"><span data-stu-id="df150-125">The following code illustrates the use of the wildcard pattern in an argument list.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3801.fs)]

<span data-ttu-id="df150-126">O padrão curinga pode ser útil sempre que você não precisar dos argumentos passados, como no ponto de entrada principal para um programa, quando você não estiver interessado nos argumentos de linha de comando que normalmente são fornecidos como uma matriz de cadeia de caracteres, como no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="df150-126">The wildcard pattern can be useful whenever you do not need the arguments passed in, such as in the main entry point to a program, when you are not interested in the command-line arguments that are normally supplied as a string array, as in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3802.fs)]

<span data-ttu-id="df150-127">Outros padrões que às vezes são usados em argumentos são `as` o padrão e os padrões de identificador associados a uniões discriminadas e padrões ativos.</span><span class="sxs-lookup"><span data-stu-id="df150-127">Other patterns that are sometimes used in arguments are the `as` pattern, and identifier patterns associated with discriminated unions and active patterns.</span></span> <span data-ttu-id="df150-128">Você pode usar o padrão de união discriminada de caso único da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="df150-128">You can use the single-case discriminated union pattern as follows.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3803.fs)]

<span data-ttu-id="df150-129">A saída é a seguinte.</span><span class="sxs-lookup"><span data-stu-id="df150-129">The output is as follows.</span></span>

```console
Data begins at 0 and ends at 4 in string Et tu, Brute?
Et tu
```

<span data-ttu-id="df150-130">Os padrões ativos podem ser úteis como parâmetros, por exemplo, ao transformar um argumento em um formato desejado, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="df150-130">Active patterns can be useful as parameters, for example, when transforming an argument into a desired format, as in the following example:</span></span>

```fsharp
type Point = { x : float; y : float }

let (| Polar |) { x = x; y = y} =
    ( sqrt (x*x + y*y), System.Math.Atan (y/ x) )

let radius (Polar(r, _)) = r
let angle (Polar(_, theta)) = theta
```

<span data-ttu-id="df150-131">Você pode usar o `as` padrão para armazenar um valor correspondente como um valor local, como é mostrado na linha de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="df150-131">You can use the `as` pattern to store a matched value as a local value, as is shown in the following line of code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3805.fs)]

<span data-ttu-id="df150-132">Outro padrão usado ocasionalmente é uma função que deixa o último argumento sem nome, fornecendo, como o corpo da função, uma expressão lambda que executa imediatamente uma correspondência de padrão no argumento implícito.</span><span class="sxs-lookup"><span data-stu-id="df150-132">Another pattern that is used occasionally is a function that leaves the last argument unnamed by providing, as the body of the function, a lambda expression that immediately performs a pattern match on the implicit argument.</span></span> <span data-ttu-id="df150-133">Um exemplo disso é a linha de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="df150-133">An example of this is the following line of code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3804.fs)]

<span data-ttu-id="df150-134">Esse código define uma função que usa uma lista genérica e retorna `true` se a lista estiver vazia e `false` , caso contrário,.</span><span class="sxs-lookup"><span data-stu-id="df150-134">This code defines a function that takes a generic list and returns `true` if the list is empty, and `false` otherwise.</span></span> <span data-ttu-id="df150-135">O uso dessas técnicas pode tornar o código mais difícil de ler.</span><span class="sxs-lookup"><span data-stu-id="df150-135">The use of such techniques can make code more difficult to read.</span></span>

<span data-ttu-id="df150-136">Ocasionalmente, os padrões que envolvem correspondências incompletas são úteis, por exemplo, se você souber que as listas em seu programa têm apenas três elementos, você pode usar um padrão como o seguinte em uma lista de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="df150-136">Occasionally, patterns that involve incomplete matches are useful, for example, if you know that the lists in your program have only three elements, you might use a pattern like the following in a parameter list.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3806.fs)]

<span data-ttu-id="df150-137">O uso de padrões que têm correspondências incompletas é melhor reservado para rápida criação de protótipos e outros usos temporários.</span><span class="sxs-lookup"><span data-stu-id="df150-137">The use of patterns that have incomplete matches is best reserved for quick prototyping and other temporary uses.</span></span> <span data-ttu-id="df150-138">O compilador emitirá um aviso para esse código.</span><span class="sxs-lookup"><span data-stu-id="df150-138">The compiler will issue a warning for such code.</span></span> <span data-ttu-id="df150-139">Tais padrões não podem abranger o caso geral de todas as entradas possíveis e, portanto, não são adequadas para APIs de componente.</span><span class="sxs-lookup"><span data-stu-id="df150-139">Such patterns cannot cover the general case of all possible inputs and therefore are not suitable for component APIs.</span></span>

## <a name="named-arguments"></a><span data-ttu-id="df150-140">Argumentos nomeados</span><span class="sxs-lookup"><span data-stu-id="df150-140">Named Arguments</span></span>

<span data-ttu-id="df150-141">Argumentos para métodos podem ser especificados por posição em uma lista de argumentos separados por vírgulas ou podem ser passados para um método explicitamente fornecendo o nome, seguido por um sinal de igual e o valor a ser passado.</span><span class="sxs-lookup"><span data-stu-id="df150-141">Arguments for methods can be specified by position in a comma-separated argument list, or they can be passed to a method explicitly by providing the name, followed by an equal sign and the value to be passed in.</span></span> <span data-ttu-id="df150-142">Se especificado fornecendo o nome, eles podem aparecer em uma ordem diferente da usada na declaração.</span><span class="sxs-lookup"><span data-stu-id="df150-142">If specified by providing the name, they can appear in a different order from that used in the declaration.</span></span>

<span data-ttu-id="df150-143">Os argumentos nomeados podem tornar o código mais legível e mais adaptável para determinados tipos de alterações na API, como uma reordenação de parâmetros de método.</span><span class="sxs-lookup"><span data-stu-id="df150-143">Named arguments can make code more readable and more adaptable to certain types of changes in the API, such as a reordering of method parameters.</span></span>

<span data-ttu-id="df150-144">Os argumentos nomeados são permitidos somente para métodos, `let`não para funções associadas, valores de função ou expressões lambda.</span><span class="sxs-lookup"><span data-stu-id="df150-144">Named arguments are allowed only for methods, not for `let`-bound functions, function values, or lambda expressions.</span></span>

<span data-ttu-id="df150-145">O exemplo de código a seguir demonstra o uso de argumentos nomeados.</span><span class="sxs-lookup"><span data-stu-id="df150-145">The following code example demonstrates the use of named arguments.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3807.fs)]

<span data-ttu-id="df150-146">Em uma chamada para um construtor de classe, você pode definir os valores das propriedades da classe usando uma sintaxe semelhante à dos argumentos nomeados.</span><span class="sxs-lookup"><span data-stu-id="df150-146">In a call to a class constructor, you can set the values of properties of the class by using a syntax similar to that of named arguments.</span></span> <span data-ttu-id="df150-147">O exemplo a seguir mostra essa sintaxe.</span><span class="sxs-lookup"><span data-stu-id="df150-147">The following example shows this syntax.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3506.fs)]

<span data-ttu-id="df150-148">Para obter mais informações, consulte [construtores (F#)](https://msdn.microsoft.com/library/2cd0ed07-d214-4125-8317-4f288af99f05).</span><span class="sxs-lookup"><span data-stu-id="df150-148">For more information, see [Constructors (F#)](https://msdn.microsoft.com/library/2cd0ed07-d214-4125-8317-4f288af99f05).</span></span>

## <a name="optional-parameters"></a><span data-ttu-id="df150-149">Parâmetros opcionais</span><span class="sxs-lookup"><span data-stu-id="df150-149">Optional Parameters</span></span>

<span data-ttu-id="df150-150">Você pode especificar um parâmetro opcional para um método usando um ponto de interrogação na frente do nome do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="df150-150">You can specify an optional parameter for a method by using a question mark in front of the parameter name.</span></span> <span data-ttu-id="df150-151">Os parâmetros opcionais são interpretados como o tipo de opção, de modo que você pode consultá-los de forma regular F# que os tipos `match` de opção são consultados, usando uma expressão com `Some` and `None`.</span><span class="sxs-lookup"><span data-stu-id="df150-151">Optional parameters are interpreted as the F# option type, so you can query them in the regular way that option types are queried, by using a `match` expression with `Some` and `None`.</span></span> <span data-ttu-id="df150-152">Parâmetros opcionais são permitidos somente em membros, não em funções criadas usando `let` associações.</span><span class="sxs-lookup"><span data-stu-id="df150-152">Optional parameters are permitted only on members, not on functions created by using `let` bindings.</span></span>

<span data-ttu-id="df150-153">Você pode passar valores opcionais existentes para o método pelo nome do parâmetro `?arg=None` , `?arg=Some(3)` como `?arg=arg`ou ou.</span><span class="sxs-lookup"><span data-stu-id="df150-153">You can pass existing optional values to method by parameter name, such as `?arg=None` or `?arg=Some(3)` or `?arg=arg`.</span></span> <span data-ttu-id="df150-154">Isso pode ser útil ao criar um método que passe argumentos opcionais para outro método.</span><span class="sxs-lookup"><span data-stu-id="df150-154">This can be useful when building a method that passes optional arguments to another method.</span></span>

<span data-ttu-id="df150-155">Você também pode usar uma função `defaultArg`, que define um valor padrão de um argumento opcional.</span><span class="sxs-lookup"><span data-stu-id="df150-155">You can also use a function `defaultArg`, which sets a default value of an optional argument.</span></span> <span data-ttu-id="df150-156">A `defaultArg` função usa o parâmetro opcional como o primeiro argumento e o valor padrão como o segundo.</span><span class="sxs-lookup"><span data-stu-id="df150-156">The `defaultArg` function takes the optional parameter as the first argument and the default value as the second.</span></span>

<span data-ttu-id="df150-157">O exemplo a seguir ilustra o uso de parâmetros opcionais.</span><span class="sxs-lookup"><span data-stu-id="df150-157">The following example illustrates the use of optional parameters.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3808.fs)]

<span data-ttu-id="df150-158">A saída é a seguinte.</span><span class="sxs-lookup"><span data-stu-id="df150-158">The output is as follows.</span></span>

```console
Baud Rate: 9600 Duplex: Full Parity: false
Baud Rate: 4800 Duplex: Half Parity: false
Baud Rate: 300 Duplex: Half Parity: true
Baud Rate: 9600 Duplex: Full Parity: false
Baud Rate: 9600 Duplex: Full Parity: false
Baud Rate: 4800 Duplex: Half Parity: false
```

<span data-ttu-id="df150-159">Para fins de C# e Visual Basic interoperabilidade, você pode usar `[<Optional; DefaultParameterValue<(...)>]` os F#atributos no para que os chamadores vejam um argumento como opcional.</span><span class="sxs-lookup"><span data-stu-id="df150-159">For the purposes of C# and Visual Basic interop you can use the attributes `[<Optional; DefaultParameterValue<(...)>]` in F#, so that callers will see an argument as optional.</span></span> <span data-ttu-id="df150-160">Isso é equivalente a definir o argumento como opcional no C# como em `MyMethod(int i = 3)`.</span><span class="sxs-lookup"><span data-stu-id="df150-160">This is equivalent to defining the argument as optional in C# as in `MyMethod(int i = 3)`.</span></span>

```fsharp
open System
open System.Runtime.InteropServices
type C =
    static member Foo([<Optional; DefaultParameterValue("Hello world")>] message) =
        printfn "%s" message
```

<span data-ttu-id="df150-161">Você também pode especificar um novo objeto como um valor de parâmetro padrão.</span><span class="sxs-lookup"><span data-stu-id="df150-161">You can also specify a new object as a default parameter value.</span></span> <span data-ttu-id="df150-162">Por exemplo, o `Foo` membro poderia ter um opcional `CancellationToken` como entrada, em vez disso:</span><span class="sxs-lookup"><span data-stu-id="df150-162">For example, the `Foo` member could have an optional `CancellationToken` as input instead:</span></span>

```fsharp
open System.Threading
open System.Runtime.InteropServices
type C =
    static member Foo([<Optional; DefaultParameterValue(CancellationToken())>] ct: CancellationToken) =
        printfn "%A" ct
```

<span data-ttu-id="df150-163">O valor fornecido como argumento para `DefaultParameterValue` deve corresponder ao tipo do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="df150-163">The value given as argument to `DefaultParameterValue` must match the type of the parameter.</span></span> <span data-ttu-id="df150-164">Por exemplo, o seguinte não é permitido:</span><span class="sxs-lookup"><span data-stu-id="df150-164">For example, the following is not allowed:</span></span>

```fsharp
type C =
    static member Wrong([<Optional; DefaultParameterValue("string")>] i:int) = ()
```

<span data-ttu-id="df150-165">Nesse caso, o compilador gera um aviso e ignorará os dois atributos completamente.</span><span class="sxs-lookup"><span data-stu-id="df150-165">In this case, the compiler generates a warning and will ignore both attributes altogether.</span></span> <span data-ttu-id="df150-166">Observe que o valor `null` padrão precisa ser anotado por tipo, como caso contrário, o compilador infere o tipo errado, `[<Optional; DefaultParameterValue(null:obj)>] o:obj`ou seja,.</span><span class="sxs-lookup"><span data-stu-id="df150-166">Note that the default value `null` needs to be type-annotated, as otherwise the compiler infers the wrong type, i.e. `[<Optional; DefaultParameterValue(null:obj)>] o:obj`.</span></span>

## <a name="passing-by-reference"></a><span data-ttu-id="df150-167">Passando por referência</span><span class="sxs-lookup"><span data-stu-id="df150-167">Passing by Reference</span></span>

<span data-ttu-id="df150-168">A passagem F# de um valor por referência envolve [byrefs](byrefs.md), que são tipos de ponteiros gerenciados.</span><span class="sxs-lookup"><span data-stu-id="df150-168">Passing an F# value by reference involves [byrefs](byrefs.md), which are managed pointer types.</span></span> <span data-ttu-id="df150-169">As diretrizes para o tipo a ser usado são as seguintes:</span><span class="sxs-lookup"><span data-stu-id="df150-169">Guidance for which type to use is as follows:</span></span>

- <span data-ttu-id="df150-170">Use `inref<'T>` se você precisar apenas ler o ponteiro.</span><span class="sxs-lookup"><span data-stu-id="df150-170">Use `inref<'T>` if you only need to read the pointer.</span></span>
- <span data-ttu-id="df150-171">Use `outref<'T>` se você precisar apenas gravar no ponteiro.</span><span class="sxs-lookup"><span data-stu-id="df150-171">Use `outref<'T>` if you only need to write to the pointer.</span></span>
- <span data-ttu-id="df150-172">Use `byref<'T>` se você precisar ler e gravar no ponteiro.</span><span class="sxs-lookup"><span data-stu-id="df150-172">Use `byref<'T>` if you need to both read from and write to the pointer.</span></span>

```fsharp
let example1 (x: inref<int>) = printfn "It's %d" x

let example2 (x: outref<int>) = x <- x + 1

let example3 (x: byref<int>) =
    printfn "It'd %d" x
    x <- x + 1

// No need to make it mutable, since it's read-only
let x = 1
example1 &x

// Needs to be mutable, since we write to it
let mutable y = 2
example2 &y
example3 &y // Now 'y' is 3
```

<span data-ttu-id="df150-173">Como o parâmetro é um ponteiro e o valor é mutável, todas as alterações no valor são mantidas após a execução da função.</span><span class="sxs-lookup"><span data-stu-id="df150-173">Because the parameter is a pointer and the value is mutable, any changes to the value are retained after the execution of the function.</span></span>

<span data-ttu-id="df150-174">Você pode usar uma tupla como um valor de retorno para armazenar `out` quaisquer parâmetros em métodos de biblioteca do .net.</span><span class="sxs-lookup"><span data-stu-id="df150-174">You can use a tuple as a return value to store any `out` parameters in .NET library methods.</span></span> <span data-ttu-id="df150-175">Como alternativa, você pode tratar o `out` parâmetro como um `byref` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="df150-175">Alternatively, you can treat the `out` parameter as a `byref` parameter.</span></span> <span data-ttu-id="df150-176">O exemplo de código a seguir ilustra as duas maneiras.</span><span class="sxs-lookup"><span data-stu-id="df150-176">The following code example illustrates both ways.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3810.fs)]

## <a name="parameter-arrays"></a><span data-ttu-id="df150-177">Matrizes de parâmetros</span><span class="sxs-lookup"><span data-stu-id="df150-177">Parameter Arrays</span></span>

<span data-ttu-id="df150-178">Ocasionalmente, é necessário definir uma função que usa um número arbitrário de parâmetros de tipo heterogêneo.</span><span class="sxs-lookup"><span data-stu-id="df150-178">Occasionally it is necessary to define a function that takes an arbitrary number of parameters of heterogeneous type.</span></span> <span data-ttu-id="df150-179">Não seria prático criar todos os métodos sobrecarregados possíveis para considerar todos os tipos que poderiam ser usados.</span><span class="sxs-lookup"><span data-stu-id="df150-179">It would not be practical to create all the possible overloaded methods to account for all the types that could be used.</span></span> <span data-ttu-id="df150-180">As implementações do .NET fornecem suporte para esses métodos por meio do recurso de matriz de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="df150-180">The .NET implementations provide support for such methods through the parameter array feature.</span></span> <span data-ttu-id="df150-181">Um método que usa uma matriz de parâmetros em sua assinatura pode ser fornecido com um número arbitrário de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="df150-181">A method that takes a parameter array in its signature can be provided with an arbitrary number of parameters.</span></span> <span data-ttu-id="df150-182">Os parâmetros são colocados em uma matriz.</span><span class="sxs-lookup"><span data-stu-id="df150-182">The parameters are put into an array.</span></span> <span data-ttu-id="df150-183">O tipo dos elementos da matriz determina os tipos de parâmetro que podem ser passados para a função.</span><span class="sxs-lookup"><span data-stu-id="df150-183">The type of the array elements determines the parameter types that can be passed to the function.</span></span> <span data-ttu-id="df150-184">Se você definir a matriz de parâmetros `System.Object` com como o tipo de elemento, o código do cliente poderá passar valores de qualquer tipo.</span><span class="sxs-lookup"><span data-stu-id="df150-184">If you define the parameter array with `System.Object` as the element type, then client code can pass values of any type.</span></span>

<span data-ttu-id="df150-185">No F#, as matrizes de parâmetros só podem ser definidas em métodos.</span><span class="sxs-lookup"><span data-stu-id="df150-185">In F#, parameter arrays can only be defined in methods.</span></span> <span data-ttu-id="df150-186">Eles não podem ser usados em funções ou funções autônomas definidas em módulos.</span><span class="sxs-lookup"><span data-stu-id="df150-186">They cannot be used in standalone functions or functions that are defined in modules.</span></span>

<span data-ttu-id="df150-187">Você define uma matriz de parâmetros usando o `ParamArray` atributo.</span><span class="sxs-lookup"><span data-stu-id="df150-187">You define a parameter array by using the `ParamArray` attribute.</span></span> <span data-ttu-id="df150-188">O `ParamArray` atributo só pode ser aplicado ao último parâmetro.</span><span class="sxs-lookup"><span data-stu-id="df150-188">The `ParamArray` attribute can only be applied to the last parameter.</span></span>

<span data-ttu-id="df150-189">O código a seguir ilustra como chamar um método .NET que usa uma matriz de parâmetros e a definição de um F# tipo em que tem um método que usa uma matriz de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="df150-189">The following code illustrates both calling a .NET method that takes a parameter array and the definition of a type in F# that has a method that takes a parameter array.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-2/snippet3811.fs)]

<span data-ttu-id="df150-190">Quando executado em um projeto, a saída do código anterior é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="df150-190">When run in a project, the output of the previous code is as follows:</span></span>

```console
a 1 10 Hello world 1 True
"a"
1
10.0
"Hello world"
1u
true
```

## <a name="see-also"></a><span data-ttu-id="df150-191">Consulte também</span><span class="sxs-lookup"><span data-stu-id="df150-191">See also</span></span>

- [<span data-ttu-id="df150-192">Membros</span><span class="sxs-lookup"><span data-stu-id="df150-192">Members</span></span>](./members/index.md)
