---
title: Funções de primeira classe
description: Saiba mais sobre as funções de primeira classe e como elas são importantes para a F#programação funcional no.
ms.date: 10/29/2018
ms.openlocfilehash: 4681d32abd59cc4aade6f4cb2d062e7888bcfbbc
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68629718"
---
# <a name="first-class-functions"></a><span data-ttu-id="002f3-103">Funções de primeira classe</span><span class="sxs-lookup"><span data-stu-id="002f3-103">First-class functions</span></span>

<span data-ttu-id="002f3-104">Uma característica de definição de linguagens de programação funcional é a elevação de funções para o status de primeira classe.</span><span class="sxs-lookup"><span data-stu-id="002f3-104">A defining characteristic of functional programming languages is the elevation of functions to first-class status.</span></span> <span data-ttu-id="002f3-105">Você deve ser capaz de fazer com uma função o que você pode fazer com valores dos outros tipos internos e ser capaz de fazer isso com um grau de esforço comparável.</span><span class="sxs-lookup"><span data-stu-id="002f3-105">You should be able to do with a function whatever you can do with values of the other built-in types, and be able to do so with a comparable degree of effort.</span></span>

<span data-ttu-id="002f3-106">As medidas típicas de status de primeira classe incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="002f3-106">Typical measures of first-class status include the following:</span></span>

- <span data-ttu-id="002f3-107">Você pode associar funções a identificadores?</span><span class="sxs-lookup"><span data-stu-id="002f3-107">Can you bind functions to identifiers?</span></span> <span data-ttu-id="002f3-108">Ou seja, você pode dar a eles nomes?</span><span class="sxs-lookup"><span data-stu-id="002f3-108">That is, can you give them names?</span></span>

- <span data-ttu-id="002f3-109">É possível armazenar funções em estruturas de dados, como em uma lista?</span><span class="sxs-lookup"><span data-stu-id="002f3-109">Can you store functions in data structures, such as in a list?</span></span>

- <span data-ttu-id="002f3-110">Você pode passar uma função como um argumento em uma chamada de função?</span><span class="sxs-lookup"><span data-stu-id="002f3-110">Can you pass a function as an argument in a function call?</span></span>

- <span data-ttu-id="002f3-111">Você pode retornar uma função de uma chamada de função?</span><span class="sxs-lookup"><span data-stu-id="002f3-111">Can you return a function from a function call?</span></span>

<span data-ttu-id="002f3-112">As duas últimas medidas definem o que é conhecido como *operações de ordem superior* ou *funções de ordem superior*.</span><span class="sxs-lookup"><span data-stu-id="002f3-112">The last two measures define what are known as *higher-order operations* or *higher-order functions*.</span></span> <span data-ttu-id="002f3-113">As funções de ordem superior aceitam funções como argumentos e retornam funções como o valor de chamadas de função.</span><span class="sxs-lookup"><span data-stu-id="002f3-113">Higher-order functions accept functions as arguments and return functions as the value of function calls.</span></span> <span data-ttu-id="002f3-114">Essas operações dão suporte a tais fundamentos de programação funcional como funções de mapeamento e composição de funções.</span><span class="sxs-lookup"><span data-stu-id="002f3-114">These operations support such mainstays of functional programming as mapping functions and composition of functions.</span></span>

## <a name="give-the-value-a-name"></a><span data-ttu-id="002f3-115">Dê um nome ao valor</span><span class="sxs-lookup"><span data-stu-id="002f3-115">Give the Value a Name</span></span>

<span data-ttu-id="002f3-116">Se uma função for um valor de primeira classe, você deverá ser capaz de nomeá-la, assim como você pode nomear inteiros, cadeias de caracteres e outros tipos internos.</span><span class="sxs-lookup"><span data-stu-id="002f3-116">If a function is a first-class value, you must be able to name it, just as you can name integers, strings, and other built-in types.</span></span> <span data-ttu-id="002f3-117">Isso é referenciado na literatura de programação funcional como associação de um identificador a um valor.</span><span class="sxs-lookup"><span data-stu-id="002f3-117">This is referred to in functional programming literature as binding an identifier to a value.</span></span> <span data-ttu-id="002f3-118">F#`let <identifier> = <value>` [ usa`let` associações](../language-reference/functions/let-bindings.md) para associar nomes a valores:.</span><span class="sxs-lookup"><span data-stu-id="002f3-118">F# uses [`let` bindings](../language-reference/functions/let-bindings.md) to bind names to values: `let <identifier> = <value>`.</span></span> <span data-ttu-id="002f3-119">O código a seguir mostra dois exemplos.</span><span class="sxs-lookup"><span data-stu-id="002f3-119">The following code shows two examples.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet20.fs)]

<span data-ttu-id="002f3-120">Você pode nomear uma função com a mesma facilidade.</span><span class="sxs-lookup"><span data-stu-id="002f3-120">You can name a function just as easily.</span></span> <span data-ttu-id="002f3-121">O exemplo a seguir define uma função `squareIt` chamada ligando o identificador `squareIt` à [expressão](../language-reference/functions/lambda-expressions-the-fun-keyword.md) `fun n -> n * n`lambda.</span><span class="sxs-lookup"><span data-stu-id="002f3-121">The following example defines a function named `squareIt` by binding the identifier `squareIt` to the [lambda expression](../language-reference/functions/lambda-expressions-the-fun-keyword.md) `fun n -> n * n`.</span></span> <span data-ttu-id="002f3-122">A `squareIt` função tem um parâmetro `n`, e retorna o quadrado desse parâmetro.</span><span class="sxs-lookup"><span data-stu-id="002f3-122">Function `squareIt` has one parameter, `n`, and it returns the square of that parameter.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet21.fs)]

<span data-ttu-id="002f3-123">F#fornece a seguinte sintaxe mais concisa para obter o mesmo resultado com menos digitação.</span><span class="sxs-lookup"><span data-stu-id="002f3-123">F# provides the following more concise syntax to achieve the same result with less typing.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet22.fs)]

<span data-ttu-id="002f3-124">Os exemplos a seguir usam principalmente o primeiro estilo, `let <function-name> = <lambda-expression>`, para enfatizar as semelhanças entre a declaração de funções e a declaração de outros tipos de valores.</span><span class="sxs-lookup"><span data-stu-id="002f3-124">The examples that follow mostly use the first style, `let <function-name> = <lambda-expression>`, to emphasize the similarities between the declaration of functions and the declaration of other types of values.</span></span> <span data-ttu-id="002f3-125">No entanto, todas as funções nomeadas também podem ser escritas com a sintaxe concisa.</span><span class="sxs-lookup"><span data-stu-id="002f3-125">However, all the named functions can also be written with the concise syntax.</span></span> <span data-ttu-id="002f3-126">Alguns dos exemplos são escritos de ambas as maneiras.</span><span class="sxs-lookup"><span data-stu-id="002f3-126">Some of the examples are written in both ways.</span></span>

## <a name="store-the-value-in-a-data-structure"></a><span data-ttu-id="002f3-127">Armazenar o valor em uma estrutura de dados</span><span class="sxs-lookup"><span data-stu-id="002f3-127">Store the Value in a Data Structure</span></span>

<span data-ttu-id="002f3-128">Um valor de primeira classe pode ser armazenado em uma estrutura de dados.</span><span class="sxs-lookup"><span data-stu-id="002f3-128">A first-class value can be stored in a data structure.</span></span> <span data-ttu-id="002f3-129">O código a seguir mostra exemplos que armazenam valores em listas e em tuplas.</span><span class="sxs-lookup"><span data-stu-id="002f3-129">The following code shows examples that store values in lists and in tuples.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet23.fs)]

<span data-ttu-id="002f3-130">Para verificar se um nome de função armazenado em uma tupla, na verdade, é avaliado como uma função, o exemplo `fst` a `snd` seguir usa os operadores e para extrair o primeiro e `funAndArgTuple`o segundo elementos da tupla.</span><span class="sxs-lookup"><span data-stu-id="002f3-130">To verify that a function name stored in a tuple does in fact evaluate to a function, the following example uses the `fst` and `snd` operators to extract the first and second elements from tuple `funAndArgTuple`.</span></span> <span data-ttu-id="002f3-131">O primeiro elemento na tupla é `squareIt` e o segundo elemento é. `num`</span><span class="sxs-lookup"><span data-stu-id="002f3-131">The first element in the tuple is `squareIt` and the second element is `num`.</span></span> <span data-ttu-id="002f3-132">O `num` identificador está associado em um exemplo anterior ao inteiro 10, um argumento válido para `squareIt` a função.</span><span class="sxs-lookup"><span data-stu-id="002f3-132">Identifier `num` is bound in a previous example to integer 10, a valid argument for the `squareIt` function.</span></span> <span data-ttu-id="002f3-133">A segunda expressão aplica o primeiro elemento na tupla ao segundo elemento na tupla: `squareIt num`.</span><span class="sxs-lookup"><span data-stu-id="002f3-133">The second expression applies the first element in the tuple to the second element in the tuple: `squareIt num`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet24.fs)]

<span data-ttu-id="002f3-134">Da mesma forma, assim `num` como o identificador e o inteiro 10 podem ser usados de maneira intercambiável, portanto `fun n -> n * n`, pode identificador `squareIt` e expressão lambda.</span><span class="sxs-lookup"><span data-stu-id="002f3-134">Similarly, just as identifier `num` and integer 10 can be used interchangeably, so can identifier `squareIt` and lambda expression `fun n -> n * n`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet25.fs)]

## <a name="pass-the-value-as-an-argument"></a><span data-ttu-id="002f3-135">Passar o valor como um argumento</span><span class="sxs-lookup"><span data-stu-id="002f3-135">Pass the Value as an Argument</span></span>

<span data-ttu-id="002f3-136">Se um valor tiver o status de primeira classe em um idioma, você poderá passá-lo como um argumento para uma função.</span><span class="sxs-lookup"><span data-stu-id="002f3-136">If a value has first-class status in a language, you can pass it as an argument to a function.</span></span> <span data-ttu-id="002f3-137">Por exemplo, é comum passar inteiros e cadeias de caracteres como argumentos.</span><span class="sxs-lookup"><span data-stu-id="002f3-137">For example, it is common to pass integers and strings as arguments.</span></span> <span data-ttu-id="002f3-138">O código a seguir mostra inteiros e cadeias de caracteres passados F#como argumentos em.</span><span class="sxs-lookup"><span data-stu-id="002f3-138">The following code shows integers and strings passed as arguments in F#.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet26.fs)]

<span data-ttu-id="002f3-139">Se as funções tiverem o status de primeira classe, você deverá ser capaz de passá-las como argumentos da mesma maneira.</span><span class="sxs-lookup"><span data-stu-id="002f3-139">If functions have first-class status, you must be able to pass them as arguments in the same way.</span></span> <span data-ttu-id="002f3-140">Lembre-se de que essa é a primeira característica das funções de ordem superior.</span><span class="sxs-lookup"><span data-stu-id="002f3-140">Remember that this is the first characteristic of higher-order functions.</span></span>

<span data-ttu-id="002f3-141">No exemplo a seguir, a `applyIt` função tem dois `op` parâmetros e `arg`.</span><span class="sxs-lookup"><span data-stu-id="002f3-141">In the following example, function `applyIt` has two parameters, `op` and `arg`.</span></span> <span data-ttu-id="002f3-142">Se você enviar em uma função que tenha um parâmetro para `op` e um argumento apropriado para a função para `arg`, a função retornará `arg`o resultado da aplicação `op` de.</span><span class="sxs-lookup"><span data-stu-id="002f3-142">If you send in a function that has one parameter for `op` and an appropriate argument for the function to `arg`, the function returns the result of applying `op` to `arg`.</span></span> <span data-ttu-id="002f3-143">No exemplo a seguir, o argumento de função e o argumento de inteiro são enviados da mesma maneira, usando seus nomes.</span><span class="sxs-lookup"><span data-stu-id="002f3-143">In the following example, both the function argument and the integer argument are sent in the same way, by using their names.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet27.fs)]

<span data-ttu-id="002f3-144">A capacidade de enviar uma função como um argumento para outra função baseia-se em abstrações comuns em linguagens de programação funcionais, como operações de mapeamento ou de filtro.</span><span class="sxs-lookup"><span data-stu-id="002f3-144">The ability to send a function as an argument to another function underlies common abstractions in functional programming languages, such as map or filter operations.</span></span> <span data-ttu-id="002f3-145">Uma operação de mapa, por exemplo, é uma função de ordem superior que captura a computação compartilhada por funções que passam por uma lista, fazem algo para cada elemento e, em seguida, retornam uma lista dos resultados.</span><span class="sxs-lookup"><span data-stu-id="002f3-145">A map operation, for example, is a higher-order function that captures the computation shared by functions that step through a list, do something to each element, and then return a list of the results.</span></span> <span data-ttu-id="002f3-146">Você pode desejar incrementar cada elemento em uma lista de inteiros ou para quadradoar cada elemento ou para alterar cada elemento em uma lista de cadeias de caracteres para letras maiúsculas.</span><span class="sxs-lookup"><span data-stu-id="002f3-146">You might want to increment each element in a list of integers, or to square each element, or to change each element in a list of strings to uppercase.</span></span> <span data-ttu-id="002f3-147">A parte propensa a erros da computação é o processo recursivo que percorre a lista e cria uma lista dos resultados a serem retornados.</span><span class="sxs-lookup"><span data-stu-id="002f3-147">The error-prone part of the computation is the recursive process that steps through the list and builds a list of the results to return.</span></span> <span data-ttu-id="002f3-148">Essa parte é capturada na função de mapeamento.</span><span class="sxs-lookup"><span data-stu-id="002f3-148">That part is captured in the mapping function.</span></span> <span data-ttu-id="002f3-149">Tudo o que você precisa escrever para um aplicativo específico é a função que você deseja aplicar a cada elemento de lista individualmente (adicionando, elevando, alterando maiúsculas e minúsculas).</span><span class="sxs-lookup"><span data-stu-id="002f3-149">All you have to write for a particular application is the function that you want to apply to each list element individually (adding, squaring, changing case).</span></span> <span data-ttu-id="002f3-150">Essa função é enviada como um argumento para a função de mapeamento, assim `squareIt` como é enviada `applyIt` para no exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="002f3-150">That function is sent as an argument to the mapping function, just as `squareIt` is sent to `applyIt` in the previous example.</span></span>

<span data-ttu-id="002f3-151">F#fornece métodos de mapa para a maioria dos tipos de coleção, incluindo [listas](../language-reference/lists.md), [matrizes](../language-reference/arrays.md)e [sequências](../language-reference/sequences.md).</span><span class="sxs-lookup"><span data-stu-id="002f3-151">F# provides map methods for most collection types, including [lists](../language-reference/lists.md), [arrays](../language-reference/arrays.md), and [sequences](../language-reference/sequences.md).</span></span> <span data-ttu-id="002f3-152">Os exemplos a seguir usam listas.</span><span class="sxs-lookup"><span data-stu-id="002f3-152">The following examples use lists.</span></span> <span data-ttu-id="002f3-153">A sintaxe é `List.map <the function> <the list>`.</span><span class="sxs-lookup"><span data-stu-id="002f3-153">The syntax is `List.map <the function> <the list>`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet28.fs)]

<span data-ttu-id="002f3-154">Para obter mais informações, consulte [listas](../language-reference/lists.md).</span><span class="sxs-lookup"><span data-stu-id="002f3-154">For more information, see [Lists](../language-reference/lists.md).</span></span>

## <a name="return-the-value-from-a-function-call"></a><span data-ttu-id="002f3-155">Retornar o valor de uma chamada de função</span><span class="sxs-lookup"><span data-stu-id="002f3-155">Return the Value from a Function Call</span></span>

<span data-ttu-id="002f3-156">Por fim, se uma função tiver o status de primeira classe em um idioma, você deverá ser capaz de retorná-la como o valor de uma chamada de função, assim como retorna outros tipos, como inteiros e cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="002f3-156">Finally, if a function has first-class status in a language, you must be able to return it as the value of a function call, just as you return other types, such as integers and strings.</span></span>

<span data-ttu-id="002f3-157">As chamadas de função a seguir retornam inteiros e as exibem.</span><span class="sxs-lookup"><span data-stu-id="002f3-157">The following function calls return integers and display them.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet29.fs)]

<span data-ttu-id="002f3-158">A chamada de função a seguir retorna uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="002f3-158">The following function call returns a string.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet30.fs)]

<span data-ttu-id="002f3-159">A chamada de função a seguir, declarada embutida, retorna um valor booliano.</span><span class="sxs-lookup"><span data-stu-id="002f3-159">The following function call, declared inline, returns a Boolean value.</span></span> <span data-ttu-id="002f3-160">O valor exibido é `True`.</span><span class="sxs-lookup"><span data-stu-id="002f3-160">The value displayed is `True`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet31.fs)]

<span data-ttu-id="002f3-161">A capacidade de retornar uma função como o valor de uma chamada de função é a segunda característica de funções de ordem superior.</span><span class="sxs-lookup"><span data-stu-id="002f3-161">The ability to return a function as the value of a function call is the second characteristic of higher-order functions.</span></span> <span data-ttu-id="002f3-162">No exemplo a seguir, `checkFor` é definido como uma função que usa um argumento, `item`e retorna uma nova função como seu valor.</span><span class="sxs-lookup"><span data-stu-id="002f3-162">In the following example, `checkFor` is defined to be a function that takes one argument, `item`, and returns a new function as its value.</span></span> <span data-ttu-id="002f3-163">A função retornada usa uma lista como seu argumento, `lst`e `item` procura em `lst`.</span><span class="sxs-lookup"><span data-stu-id="002f3-163">The returned function takes a list as its argument, `lst`, and searches for `item` in `lst`.</span></span> <span data-ttu-id="002f3-164">Se `item` estiver presente, a função retornará `true`.</span><span class="sxs-lookup"><span data-stu-id="002f3-164">If `item` is present, the function returns `true`.</span></span> <span data-ttu-id="002f3-165">Se `item` não estiver presente, a função retornará `false`.</span><span class="sxs-lookup"><span data-stu-id="002f3-165">If `item` is not present, the function returns `false`.</span></span> <span data-ttu-id="002f3-166">Como na seção anterior, o código a seguir usa uma função de lista fornecida, [list. Exists](https://msdn.microsoft.com/library/15a3ebd5-98f0-44c0-8220-7dedec3e68a8), para pesquisar a lista.</span><span class="sxs-lookup"><span data-stu-id="002f3-166">As in the previous section, the following code uses a provided list function, [List.exists](https://msdn.microsoft.com/library/15a3ebd5-98f0-44c0-8220-7dedec3e68a8), to search the list.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet32.fs)]

<span data-ttu-id="002f3-167">O código a seguir `checkFor` usa para criar uma nova função que usa um argumento, uma lista e pesquisa 7 na lista.</span><span class="sxs-lookup"><span data-stu-id="002f3-167">The following code uses `checkFor` to create a new function that takes one argument, a list, and searches for 7 in the list.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet33.fs)]

<span data-ttu-id="002f3-168">O exemplo a seguir usa o status de primeira classe de funções F# no para declarar uma função `compose`,, que retorna uma composição de dois argumentos de função.</span><span class="sxs-lookup"><span data-stu-id="002f3-168">The following example uses the first-class status of functions in F# to declare a function, `compose`, that returns a composition of two function arguments.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet34.fs)]

> [!NOTE]
> <span data-ttu-id="002f3-169">Para obter uma versão ainda mais curta, consulte a seção a seguir, "na forma curried Functions".</span><span class="sxs-lookup"><span data-stu-id="002f3-169">For an even shorter version, see the following section, "Curried Functions."</span></span>

<span data-ttu-id="002f3-170">O código a seguir envia duas funções como argumentos `compose`para, que usam um único argumento do mesmo tipo.</span><span class="sxs-lookup"><span data-stu-id="002f3-170">The following code sends two functions as arguments to `compose`, both of which take a single argument of the same type.</span></span> <span data-ttu-id="002f3-171">O valor de retorno é uma nova função que é uma composição dos dois argumentos de função.</span><span class="sxs-lookup"><span data-stu-id="002f3-171">The return value is a new function that is a composition of the two function arguments.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet35.fs)]

> [!NOTE]
> <span data-ttu-id="002f3-172">F#fornece dois operadores `<<` e `>>`, que compõem funções.</span><span class="sxs-lookup"><span data-stu-id="002f3-172">F# provides two operators, `<<` and `>>`, that compose functions.</span></span> <span data-ttu-id="002f3-173">Por exemplo, `let squareAndDouble2 = doubleIt << squareIt` é equivalente a `let squareAndDouble = compose doubleIt squareIt` no exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="002f3-173">For example, `let squareAndDouble2 = doubleIt << squareIt` is equivalent to `let squareAndDouble = compose doubleIt squareIt` in the previous example.</span></span>

<span data-ttu-id="002f3-174">O exemplo a seguir de retornar uma função como o valor de uma chamada de função cria um jogo de adivinhação simples.</span><span class="sxs-lookup"><span data-stu-id="002f3-174">The following example of returning a function as the value of a function call creates a simple guessing game.</span></span> <span data-ttu-id="002f3-175">Para criar um jogo, chame `makeGame` com o valor que você deseja que alguém Adivinhe envie. `target`</span><span class="sxs-lookup"><span data-stu-id="002f3-175">To create a game, call `makeGame` with the value that you want someone to guess sent in for `target`.</span></span> <span data-ttu-id="002f3-176">O valor de retorno da `makeGame` função é uma função que usa um argumento (a estimativa) e informa se a estimativa está correta.</span><span class="sxs-lookup"><span data-stu-id="002f3-176">The return value from function `makeGame` is a function that takes one argument (the guess) and reports whether the guess is correct.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet36.fs)]

<span data-ttu-id="002f3-177">O código a seguir `makeGame`chama, enviando o `7` valor `target`para.</span><span class="sxs-lookup"><span data-stu-id="002f3-177">The following code calls `makeGame`, sending the value `7` for `target`.</span></span> <span data-ttu-id="002f3-178">O `playGame` identificador está associado à expressão lambda retornada.</span><span class="sxs-lookup"><span data-stu-id="002f3-178">Identifier `playGame` is bound to the returned lambda expression.</span></span> <span data-ttu-id="002f3-179">Portanto, `playGame` é uma função que usa como um valor de um argumento para `guess`.</span><span class="sxs-lookup"><span data-stu-id="002f3-179">Therefore, `playGame` is a function that takes as its one argument a value for `guess`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet37.fs)]

## <a name="curried-functions"></a><span data-ttu-id="002f3-180">Funções na forma curried</span><span class="sxs-lookup"><span data-stu-id="002f3-180">Curried Functions</span></span>

<span data-ttu-id="002f3-181">Muitos dos exemplos na seção anterior podem ser escritos de forma mais concisa aproveitando o *currying* implícito nas F# declarações de função.</span><span class="sxs-lookup"><span data-stu-id="002f3-181">Many of the examples in the previous section can be written more concisely by taking advantage of the implicit *currying* in F# function declarations.</span></span> <span data-ttu-id="002f3-182">Currying é um processo que transforma uma função que tem mais de um parâmetro em uma série de funções inseridas, cada uma com um único parâmetro.</span><span class="sxs-lookup"><span data-stu-id="002f3-182">Currying is a process that transforms a function that has more than one parameter into a series of embedded functions, each of which has a single parameter.</span></span> <span data-ttu-id="002f3-183">No F#, as funções que têm mais de um parâmetro são inerentemente na forma curried.</span><span class="sxs-lookup"><span data-stu-id="002f3-183">In F#, functions that have more than one parameter are inherently curried.</span></span> <span data-ttu-id="002f3-184">Por exemplo, `compose` da seção anterior pode ser escrito conforme mostrado no estilo conciso a seguir, com três parâmetros.</span><span class="sxs-lookup"><span data-stu-id="002f3-184">For example, `compose` from the previous section can be written as shown in the following concise style, with three parameters.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet38.fs)]

<span data-ttu-id="002f3-185">No entanto, o resultado é uma função de um parâmetro que retorna uma função de um parâmetro que, por sua vez, retorna outra função de um `compose4curried`parâmetro, como mostrado em.</span><span class="sxs-lookup"><span data-stu-id="002f3-185">However, the result is a function of one parameter that returns a function of one parameter that in turn returns another function of one parameter, as shown in `compose4curried`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet39.fs)]

<span data-ttu-id="002f3-186">Você pode acessar essa função de várias maneiras.</span><span class="sxs-lookup"><span data-stu-id="002f3-186">You can access this function in several ways.</span></span> <span data-ttu-id="002f3-187">Cada um dos exemplos a seguir retorna e exibe 18.</span><span class="sxs-lookup"><span data-stu-id="002f3-187">Each of the following examples returns and displays 18.</span></span> <span data-ttu-id="002f3-188">Você pode substituir `compose4` por `compose4curried` em qualquer um dos exemplos.</span><span class="sxs-lookup"><span data-stu-id="002f3-188">You can replace `compose4` with `compose4curried` in any of the examples.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet40.fs)]

<span data-ttu-id="002f3-189">Para verificar se a função ainda funciona como antes, tente os casos de teste originais novamente.</span><span class="sxs-lookup"><span data-stu-id="002f3-189">To verify that the function still works as it did before, try the original test cases again.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet41.fs)]

> [!NOTE]
> <span data-ttu-id="002f3-190">Você pode restringir currying por meio de parâmetros delimitadores em tuplas.</span><span class="sxs-lookup"><span data-stu-id="002f3-190">You can restrict currying by enclosing parameters in tuples.</span></span> <span data-ttu-id="002f3-191">Para obter mais informações, consulte "padrões de parâmetro" em [parâmetros e argumentos](../language-reference/parameters-and-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="002f3-191">For more information, see "Parameter Patterns" in [Parameters and Arguments](../language-reference/parameters-and-arguments.md).</span></span>

<span data-ttu-id="002f3-192">O exemplo a seguir usa o currying implícito para gravar uma versão mais `makeGame`curta do.</span><span class="sxs-lookup"><span data-stu-id="002f3-192">The following example uses implicit currying to write a shorter version of `makeGame`.</span></span> <span data-ttu-id="002f3-193">Os detalhes de como `makeGame` construções e Devoluções da `game` função são menos explícitos nesse formato, mas você pode verificar usando os casos de teste originais que o resultado é o mesmo.</span><span class="sxs-lookup"><span data-stu-id="002f3-193">The details of how `makeGame` constructs and returns the `game` function are less explicit in this format, but you can verify by using the original test cases that the result is the same.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet42.fs)]

<span data-ttu-id="002f3-194">Para obter mais informações sobre currying, consulte "aplicativo parcial de argumentos" em [funções](../language-reference/functions/index.md).</span><span class="sxs-lookup"><span data-stu-id="002f3-194">For more information about currying, see "Partial Application of Arguments" in [Functions](../language-reference/functions/index.md).</span></span>

## <a name="identifier-and-function-definition-are-interchangeable"></a><span data-ttu-id="002f3-195">Identificador e definição de função são intercambiáveis</span><span class="sxs-lookup"><span data-stu-id="002f3-195">Identifier and Function Definition Are Interchangeable</span></span>

<span data-ttu-id="002f3-196">O nome `num` da variável nos exemplos anteriores é avaliado como o inteiro 10, e não é surpresa que o local `num` seja válido, 10 também é válido.</span><span class="sxs-lookup"><span data-stu-id="002f3-196">The variable name `num` in the previous examples evaluates to the integer 10, and it is no surprise that where `num` is valid, 10 is also valid.</span></span> <span data-ttu-id="002f3-197">O mesmo vale para identificadores de função e seus valores: em qualquer lugar, o nome da função pode ser usado, a expressão lambda à qual ele está associado pode ser usada.</span><span class="sxs-lookup"><span data-stu-id="002f3-197">The same is true of function identifiers and their values: anywhere the name of the function can be used, the lambda expression to which it is bound can be used.</span></span>

<span data-ttu-id="002f3-198">O exemplo a seguir define `Boolean` uma função `isNegative`chamada e, em seguida, usa o nome da função e a definição da função de forma intercambiável.</span><span class="sxs-lookup"><span data-stu-id="002f3-198">The following example defines a `Boolean` function called `isNegative`, and then uses the name of the function and the definition of the function interchangeably.</span></span> <span data-ttu-id="002f3-199">Os próximos três exemplos retornam e exibem `False`.</span><span class="sxs-lookup"><span data-stu-id="002f3-199">The next three examples all return and display `False`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet43.fs)]

<span data-ttu-id="002f3-200">Para levá-lo um passo adiante, substitua o valor `applyIt` que está associado a `applyIt`para.</span><span class="sxs-lookup"><span data-stu-id="002f3-200">To take it one step further, substitute the value that `applyIt` is bound to for `applyIt`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet44.fs)]

## <a name="functions-are-first-class-values-in-f"></a><span data-ttu-id="002f3-201">Funções são valores de primeira classe em F\#</span><span class="sxs-lookup"><span data-stu-id="002f3-201">Functions Are First-Class Values in F\#</span></span>

<span data-ttu-id="002f3-202">Os exemplos nas seções anteriores demonstram que as funções F# no atendem aos critérios para serem valores de primeira F#classe no:</span><span class="sxs-lookup"><span data-stu-id="002f3-202">The examples in the previous sections demonstrate that functions in F# satisfy the criteria for being first-class values in F#:</span></span>

- <span data-ttu-id="002f3-203">Você pode associar um identificador a uma definição de função.</span><span class="sxs-lookup"><span data-stu-id="002f3-203">You can bind an identifier to a function definition.</span></span>
[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet21.fs)]

- <span data-ttu-id="002f3-204">Você pode armazenar uma função em uma estrutura de dados.</span><span class="sxs-lookup"><span data-stu-id="002f3-204">You can store a function in a data structure.</span></span>
[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet45.fs)]

- <span data-ttu-id="002f3-205">Você pode passar uma função como um argumento.</span><span class="sxs-lookup"><span data-stu-id="002f3-205">You can pass a function as an argument.</span></span>
[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet46.fs)]

- <span data-ttu-id="002f3-206">Você pode retornar uma função como o valor de uma chamada de função.</span><span class="sxs-lookup"><span data-stu-id="002f3-206">You can return a function as the value of a function call.</span></span>
[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet32.fs)]

<span data-ttu-id="002f3-207">Para obter mais informações F#sobre o, consulte a [ F# referência de linguagem](../language-reference/index.md).</span><span class="sxs-lookup"><span data-stu-id="002f3-207">For more information about F#, see the [F# Language Reference](../language-reference/index.md).</span></span>

## <a name="example"></a><span data-ttu-id="002f3-208">Exemplo</span><span class="sxs-lookup"><span data-stu-id="002f3-208">Example</span></span>

### <a name="description"></a><span data-ttu-id="002f3-209">Descrição</span><span class="sxs-lookup"><span data-stu-id="002f3-209">Description</span></span>

<span data-ttu-id="002f3-210">O código a seguir contém todos os exemplos neste tópico.</span><span class="sxs-lookup"><span data-stu-id="002f3-210">The following code contains all the examples in this topic.</span></span>

### <a name="code"></a><span data-ttu-id="002f3-211">Código</span><span class="sxs-lookup"><span data-stu-id="002f3-211">Code</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet47.fs)]

## <a name="see-also"></a><span data-ttu-id="002f3-212">Consulte também</span><span class="sxs-lookup"><span data-stu-id="002f3-212">See also</span></span>

- [<span data-ttu-id="002f3-213">Listas</span><span class="sxs-lookup"><span data-stu-id="002f3-213">Lists</span></span>](../language-reference/lists.md)
- [<span data-ttu-id="002f3-214">Tuplas</span><span class="sxs-lookup"><span data-stu-id="002f3-214">Tuples</span></span>](../language-reference/tuples.md)
- [<span data-ttu-id="002f3-215">Funções</span><span class="sxs-lookup"><span data-stu-id="002f3-215">Functions</span></span>](../language-reference/functions/index.md)
- [<span data-ttu-id="002f3-216">`let`Associações</span><span class="sxs-lookup"><span data-stu-id="002f3-216">`let` Bindings</span></span>](../language-reference/functions/let-bindings.md)
- [<span data-ttu-id="002f3-217">Expressões lambda: A Palavra-chave `fun` </span><span class="sxs-lookup"><span data-stu-id="002f3-217">Lambda Expressions: The `fun` Keyword</span></span>](../language-reference/functions/lambda-expressions-the-fun-keyword.md)
