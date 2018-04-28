---
title: Funções como valores de primeira classe (F#)
description: 'Saiba como as funções são elevadas para o status de primeira classe em F # linguagem de programação.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 7db99aa23211ce4a7af5cdfcc809017fafb1d5a1
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2018
---
# <a name="functions-as-first-class-values"></a><span data-ttu-id="3fcb8-103">Funções como valores de primeira classe</span><span class="sxs-lookup"><span data-stu-id="3fcb8-103">Functions as First-Class Values</span></span>

<span data-ttu-id="3fcb8-104">Uma característica de definição de linguagens de programação funcionais é a elevação de funções para o status de primeira classe.</span><span class="sxs-lookup"><span data-stu-id="3fcb8-104">A defining characteristic of functional programming languages is the elevation of functions to first-class status.</span></span> <span data-ttu-id="3fcb8-105">Você deve ser capaz de fazer com uma função que você pode fazer com os valores dos outros tipos internos e ser capaz de fazer isso com um nível semelhante de esforço.</span><span class="sxs-lookup"><span data-stu-id="3fcb8-105">You should be able to do with a function whatever you can do with values of the other built-in types, and be able to do so with a comparable degree of effort.</span></span>

<span data-ttu-id="3fcb8-106">Medidas típicas de primeira classe status incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="3fcb8-106">Typical measures of first-class status include the following:</span></span>

- <span data-ttu-id="3fcb8-107">Você pode associar funções aos identificadores?</span><span class="sxs-lookup"><span data-stu-id="3fcb8-107">Can you bind functions to identifiers?</span></span> <span data-ttu-id="3fcb8-108">Ou seja, pode dá-los nomes?</span><span class="sxs-lookup"><span data-stu-id="3fcb8-108">That is, can you give them names?</span></span>

- <span data-ttu-id="3fcb8-109">Você pode armazenar funções nas estruturas de dados, como em uma lista?</span><span class="sxs-lookup"><span data-stu-id="3fcb8-109">Can you store functions in data structures, such as in a list?</span></span>

- <span data-ttu-id="3fcb8-110">Você pode passar uma função como um argumento em uma chamada de função?</span><span class="sxs-lookup"><span data-stu-id="3fcb8-110">Can you pass a function as an argument in a function call?</span></span>

- <span data-ttu-id="3fcb8-111">Você pode retornar uma função de uma chamada de função?</span><span class="sxs-lookup"><span data-stu-id="3fcb8-111">Can you return a function from a function call?</span></span>

<span data-ttu-id="3fcb8-112">As últimas duas medidas que definem o que é conhecido como *operações de ordem superior* ou *funções de ordem superior*.</span><span class="sxs-lookup"><span data-stu-id="3fcb8-112">The last two measures define what are known as *higher-order operations* or *higher-order functions*.</span></span> <span data-ttu-id="3fcb8-113">Funções de ordem superior aceitam funções como argumentos e retornam funções como o valor de chamadas de função.</span><span class="sxs-lookup"><span data-stu-id="3fcb8-113">Higher-order functions accept functions as arguments and return functions as the value of function calls.</span></span> <span data-ttu-id="3fcb8-114">Essas operações oferecem suporte a esses fundamentos da programação funcional como mapeamento de funções e a composição de funções.</span><span class="sxs-lookup"><span data-stu-id="3fcb8-114">These operations support such mainstays of functional programming as mapping functions and composition of functions.</span></span>


## <a name="give-the-value-a-name"></a><span data-ttu-id="3fcb8-115">Nomeie o valor</span><span class="sxs-lookup"><span data-stu-id="3fcb8-115">Give the Value a Name</span></span>

<span data-ttu-id="3fcb8-116">Se uma função é um valor de primeira classe, você deve ser capaz de nome, assim como você pode nomear inteiros, cadeias de caracteres e outros tipos internos.</span><span class="sxs-lookup"><span data-stu-id="3fcb8-116">If a function is a first-class value, you must be able to name it, just as you can name integers, strings, and other built-in types.</span></span> <span data-ttu-id="3fcb8-117">Isso é conhecido na literatura de programação funcional como um identificador de associação para um valor.</span><span class="sxs-lookup"><span data-stu-id="3fcb8-117">This is referred to in functional programming literature as binding an identifier to a value.</span></span> <span data-ttu-id="3fcb8-118">F # usa [ `let` associações](../language-reference/functions/let-bindings.md) para associar nomes de valores: `let <identifier> = <value>`.</span><span class="sxs-lookup"><span data-stu-id="3fcb8-118">F# uses [`let` bindings](../language-reference/functions/let-bindings.md) to bind names to values: `let <identifier> = <value>`.</span></span> <span data-ttu-id="3fcb8-119">O código a seguir mostra dois exemplos.</span><span class="sxs-lookup"><span data-stu-id="3fcb8-119">The following code shows two examples.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet20.fs)]

<span data-ttu-id="3fcb8-120">Você pode nomear uma função com a maior facilidade.</span><span class="sxs-lookup"><span data-stu-id="3fcb8-120">You can name a function just as easily.</span></span> <span data-ttu-id="3fcb8-121">O exemplo a seguir define uma função chamada `squareIt` associando o identificador `squareIt` para o [expressão lambda](../language-reference/functions/lambda-expressions-the-fun-keyword.md) `fun n -> n * n`.</span><span class="sxs-lookup"><span data-stu-id="3fcb8-121">The following example defines a function named `squareIt` by binding the identifier `squareIt` to the [lambda expression](../language-reference/functions/lambda-expressions-the-fun-keyword.md) `fun n -> n * n`.</span></span> <span data-ttu-id="3fcb8-122">Função `squareIt` tem um parâmetro, `n`, e retorna o quadrado do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="3fcb8-122">Function `squareIt` has one parameter, `n`, and it returns the square of that parameter.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet21.fs)]

<span data-ttu-id="3fcb8-123">F # fornece a seguinte sintaxe mais conciso para alcançar o mesmo resultado com menos digitação.</span><span class="sxs-lookup"><span data-stu-id="3fcb8-123">F# provides the following more concise syntax to achieve the same result with less typing.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet22.fs)]

<span data-ttu-id="3fcb8-124">Os exemplos a seguir geralmente usam o estilo primeiro, `let <function-name> = <lambda-expression>`, para enfatizar as semelhanças entre a declaração de funções e a declaração de outros tipos de valores.</span><span class="sxs-lookup"><span data-stu-id="3fcb8-124">The examples that follow mostly use the first style, `let <function-name> = <lambda-expression>`, to emphasize the similarities between the declaration of functions and the declaration of other types of values.</span></span> <span data-ttu-id="3fcb8-125">No entanto, todas as funções nomeadas também podem ser escritas com a sintaxe concisa.</span><span class="sxs-lookup"><span data-stu-id="3fcb8-125">However, all the named functions can also be written with the concise syntax.</span></span> <span data-ttu-id="3fcb8-126">Alguns exemplos são gravados em ambos os sentidos.</span><span class="sxs-lookup"><span data-stu-id="3fcb8-126">Some of the examples are written in both ways.</span></span>


## <a name="store-the-value-in-a-data-structure"></a><span data-ttu-id="3fcb8-127">Armazene o valor em uma estrutura de dados</span><span class="sxs-lookup"><span data-stu-id="3fcb8-127">Store the Value in a Data Structure</span></span>

<span data-ttu-id="3fcb8-128">Um valor de primeira classe pode ser armazenado em uma estrutura de dados.</span><span class="sxs-lookup"><span data-stu-id="3fcb8-128">A first-class value can be stored in a data structure.</span></span> <span data-ttu-id="3fcb8-129">O código a seguir mostra exemplos que armazenam valores em listas em tuplas.</span><span class="sxs-lookup"><span data-stu-id="3fcb8-129">The following code shows examples that store values in lists and in tuples.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet23.fs)]

<span data-ttu-id="3fcb8-130">Para verificar se um nome de função armazenado em uma tupla na verdade avaliado como uma função, o exemplo a seguir usa o `fst` e `snd` operadores para extrair os elementos de primeiro e segundo de tupla `funAndArgTuple`.</span><span class="sxs-lookup"><span data-stu-id="3fcb8-130">To verify that a function name stored in a tuple does in fact evaluate to a function, the following example uses the `fst` and `snd` operators to extract the first and second elements from tuple `funAndArgTuple`.</span></span> <span data-ttu-id="3fcb8-131">O primeiro elemento na tupla é `squareIt` e o segundo elemento é `num`.</span><span class="sxs-lookup"><span data-stu-id="3fcb8-131">The first element in the tuple is `squareIt` and the second element is `num`.</span></span> <span data-ttu-id="3fcb8-132">Identificador `num` está associada a um exemplo anterior para o inteiro 10, um argumento válido para o `squareIt` função.</span><span class="sxs-lookup"><span data-stu-id="3fcb8-132">Identifier `num` is bound in a previous example to integer 10, a valid argument for the `squareIt` function.</span></span> <span data-ttu-id="3fcb8-133">A segunda expressão aplica-se o primeiro elemento na tupla para o segundo elemento na tupla: `squareIt num`.</span><span class="sxs-lookup"><span data-stu-id="3fcb8-133">The second expression applies the first element in the tuple to the second element in the tuple: `squareIt num`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet24.fs)]

<span data-ttu-id="3fcb8-134">Da mesma forma, apenas como identificador `num` e inteiro 10 pode ser usados alternadamente, pode ser identificador `squareIt` e uma expressão lambda `fun n -> n * n`.</span><span class="sxs-lookup"><span data-stu-id="3fcb8-134">Similarly, just as identifier `num` and integer 10 can be used interchangeably, so can identifier `squareIt` and lambda expression `fun n -> n * n`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet25.fs)]
    
## <a name="pass-the-value-as-an-argument"></a><span data-ttu-id="3fcb8-135">Passe o valor como um argumento</span><span class="sxs-lookup"><span data-stu-id="3fcb8-135">Pass the Value as an Argument</span></span>

<span data-ttu-id="3fcb8-136">Se um valor tiver um status de primeira classe em um idioma, você pode passá-lo como um argumento para uma função.</span><span class="sxs-lookup"><span data-stu-id="3fcb8-136">If a value has first-class status in a language, you can pass it as an argument to a function.</span></span> <span data-ttu-id="3fcb8-137">Por exemplo, é comum para transmitir números inteiros e cadeias de caracteres como argumentos.</span><span class="sxs-lookup"><span data-stu-id="3fcb8-137">For example, it is common to pass integers and strings as arguments.</span></span> <span data-ttu-id="3fcb8-138">O código a seguir mostra os números inteiros e cadeias de caracteres transmitidas como argumentos em F #.</span><span class="sxs-lookup"><span data-stu-id="3fcb8-138">The following code shows integers and strings passed as arguments in F#.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet26.fs)]

<span data-ttu-id="3fcb8-139">Se as funções que o status de primeira classe, você deve ser capaz para passá-las como argumentos, da mesma maneira.</span><span class="sxs-lookup"><span data-stu-id="3fcb8-139">If functions have first-class status, you must be able to pass them as arguments in the same way.</span></span> <span data-ttu-id="3fcb8-140">Lembre-se de que esta é a primeira característica de funções de ordem superior.</span><span class="sxs-lookup"><span data-stu-id="3fcb8-140">Remember that this is the first characteristic of higher-order functions.</span></span>

<span data-ttu-id="3fcb8-141">No exemplo a seguir, a função `applyIt` tem dois parâmetros, `op` e `arg`.</span><span class="sxs-lookup"><span data-stu-id="3fcb8-141">In the following example, function `applyIt` has two parameters, `op` and `arg`.</span></span> <span data-ttu-id="3fcb8-142">Se você enviar em uma função que tem um parâmetro para `op` e um argumento apropriado para a função `arg`, a função retorna o resultado da aplicação `op` para `arg`.</span><span class="sxs-lookup"><span data-stu-id="3fcb8-142">If you send in a function that has one parameter for `op` and an appropriate argument for the function to `arg`, the function returns the result of applying `op` to `arg`.</span></span> <span data-ttu-id="3fcb8-143">No exemplo a seguir, o argumento da função e o argumento inteiro são enviados da mesma forma, usando seus nomes.</span><span class="sxs-lookup"><span data-stu-id="3fcb8-143">In the following example, both the function argument and the integer argument are sent in the same way, by using their names.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet27.fs)]

<span data-ttu-id="3fcb8-144">A capacidade de enviar uma função como um argumento para outra função subjacente abstrações comuns em linguagens de programação funcionais, como operações de mapa ou filtro.</span><span class="sxs-lookup"><span data-stu-id="3fcb8-144">The ability to send a function as an argument to another function underlies common abstractions in functional programming languages, such as map or filter operations.</span></span> <span data-ttu-id="3fcb8-145">Uma operação de mapa, por exemplo, é uma função de ordem superior que captura a computação compartilhada por funções que percorrer uma lista, fazer alguma coisa para cada elemento e, em seguida, retornam uma lista dos resultados.</span><span class="sxs-lookup"><span data-stu-id="3fcb8-145">A map operation, for example, is a higher-order function that captures the computation shared by functions that step through a list, do something to each element, and then return a list of the results.</span></span> <span data-ttu-id="3fcb8-146">Você pode deseja incrementar a cada elemento em uma lista de números inteiros, ou quadrado cada elemento ou alterar cada elemento em uma lista de cadeias de caracteres para maiusculas.</span><span class="sxs-lookup"><span data-stu-id="3fcb8-146">You might want to increment each element in a list of integers, or to square each element, or to change each element in a list of strings to uppercase.</span></span> <span data-ttu-id="3fcb8-147">A parte propensas a erros de computação é o processo de recursiva que percorre a lista e cria uma lista de resultados para retornar.</span><span class="sxs-lookup"><span data-stu-id="3fcb8-147">The error-prone part of the computation is the recursive process that steps through the list and builds a list of the results to return.</span></span> <span data-ttu-id="3fcb8-148">Essa parte é capturada na função de mapeamento.</span><span class="sxs-lookup"><span data-stu-id="3fcb8-148">That part is captured in the mapping function.</span></span> <span data-ttu-id="3fcb8-149">Você precisa gravar para um determinado aplicativo é a função que você deseja aplicar a cada elemento da lista individualmente (Adicionar, elevar, alterando caso).</span><span class="sxs-lookup"><span data-stu-id="3fcb8-149">All you have to write for a particular application is the function that you want to apply to each list element individually (adding, squaring, changing case).</span></span> <span data-ttu-id="3fcb8-150">Que função será enviada como um argumento para a função de mapeamento, assim como `squareIt` é enviada para `applyIt` no exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="3fcb8-150">That function is sent as an argument to the mapping function, just as `squareIt` is sent to `applyIt` in the previous example.</span></span>

<span data-ttu-id="3fcb8-151">F # fornece métodos de mapa para a maioria dos tipos de coleção, incluindo [lista](../language-reference/lists.md), [matrizes](../language-reference/arrays.md), e [sequências](../language-reference/sequences.md).</span><span class="sxs-lookup"><span data-stu-id="3fcb8-151">F# provides map methods for most collection types, including [lists](../language-reference/lists.md), [arrays](../language-reference/arrays.md), and [sequences](../language-reference/sequences.md).</span></span> <span data-ttu-id="3fcb8-152">Os exemplos seguintes usam listas.</span><span class="sxs-lookup"><span data-stu-id="3fcb8-152">The following examples use lists.</span></span> <span data-ttu-id="3fcb8-153">A sintaxe é `List.map <the function> <the list>`.</span><span class="sxs-lookup"><span data-stu-id="3fcb8-153">The syntax is `List.map <the function> <the list>`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet28.fs)]

<span data-ttu-id="3fcb8-154">Para obter mais informações, consulte [lista](../language-reference/lists.md).</span><span class="sxs-lookup"><span data-stu-id="3fcb8-154">For more information, see [Lists](../language-reference/lists.md).</span></span>

## <a name="return-the-value-from-a-function-call"></a><span data-ttu-id="3fcb8-155">O valor de retorno de uma chamada de função</span><span class="sxs-lookup"><span data-stu-id="3fcb8-155">Return the Value from a Function Call</span></span>

<span data-ttu-id="3fcb8-156">Por fim, se uma função tiver o status de primeira classe em um idioma, você deve ser capaz para retorná-lo como o valor de uma chamada de função, assim como retornam outros tipos, como números inteiros e cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="3fcb8-156">Finally, if a function has first-class status in a language, you must be able to return it as the value of a function call, just as you return other types, such as integers and strings.</span></span>

<span data-ttu-id="3fcb8-157">As chamadas de função a seguir retornam números inteiros e exibem-los.</span><span class="sxs-lookup"><span data-stu-id="3fcb8-157">The following function calls return integers and display them.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet29.fs)]

<span data-ttu-id="3fcb8-158">A chamada de função a seguir retorna uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="3fcb8-158">The following function call returns a string.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet30.fs)]

<span data-ttu-id="3fcb8-159">A chamada de função a seguir, declarada em linha, retorna um valor booliano.</span><span class="sxs-lookup"><span data-stu-id="3fcb8-159">The following function call, declared inline, returns a Boolean value.</span></span> <span data-ttu-id="3fcb8-160">O valor exibido é `True`.</span><span class="sxs-lookup"><span data-stu-id="3fcb8-160">The value displayed is `True`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet31.fs)]

<span data-ttu-id="3fcb8-161">A capacidade de retornar de uma função como o valor de uma chamada de função é a segunda característica de funções de ordem superior.</span><span class="sxs-lookup"><span data-stu-id="3fcb8-161">The ability to return a function as the value of a function call is the second characteristic of higher-order functions.</span></span> <span data-ttu-id="3fcb8-162">No exemplo a seguir, `checkFor` está definido para ser uma função que usa um argumento, `item`e retorna uma nova função como seu valor.</span><span class="sxs-lookup"><span data-stu-id="3fcb8-162">In the following example, `checkFor` is defined to be a function that takes one argument, `item`, and returns a new function as its value.</span></span> <span data-ttu-id="3fcb8-163">A função retornada usa uma lista como seu argumento, `lst`e procura por `item` em `lst`.</span><span class="sxs-lookup"><span data-stu-id="3fcb8-163">The returned function takes a list as its argument, `lst`, and searches for `item` in `lst`.</span></span> <span data-ttu-id="3fcb8-164">Se `item` estiver presente, a função retornará `true`.</span><span class="sxs-lookup"><span data-stu-id="3fcb8-164">If `item` is present, the function returns `true`.</span></span> <span data-ttu-id="3fcb8-165">Se `item` não estiver presente, a função retornará `false`.</span><span class="sxs-lookup"><span data-stu-id="3fcb8-165">If `item` is not present, the function returns `false`.</span></span> <span data-ttu-id="3fcb8-166">Como na seção anterior, o código a seguir usa uma função de lista fornecida, [EXISTS](https://msdn.microsoft.com/library/15a3ebd5-98f0-44c0-8220-7dedec3e68a8), para a lista de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="3fcb8-166">As in the previous section, the following code uses a provided list function, [List.exists](https://msdn.microsoft.com/library/15a3ebd5-98f0-44c0-8220-7dedec3e68a8), to search the list.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet32.fs)]

<span data-ttu-id="3fcb8-167">O código a seguir usa `checkFor` para criar uma nova função que usa um argumento, uma lista e procura 7 na lista.</span><span class="sxs-lookup"><span data-stu-id="3fcb8-167">The following code uses `checkFor` to create a new function that takes one argument, a list, and searches for 7 in the list.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet33.fs)]

<span data-ttu-id="3fcb8-168">O exemplo a seguir usa o status de primeira classe das funções em F # para declarar uma função, `compose`, que retorna uma composição dos dois argumentos de função.</span><span class="sxs-lookup"><span data-stu-id="3fcb8-168">The following example uses the first-class status of functions in F# to declare a function, `compose`, that returns a composition of two function arguments.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet34.fs)]
    
>[!NOTE]
<span data-ttu-id="3fcb8-169">Para obter uma versão ainda mais curta, consulte a seção a seguir, "Curried funções".</span><span class="sxs-lookup"><span data-stu-id="3fcb8-169">For an even shorter version, see the following section, "Curried Functions."</span></span>


<span data-ttu-id="3fcb8-170">O código a seguir envia duas funções como argumentos para `compose`, ambos do que utilizam um argumento único do mesmo tipo.</span><span class="sxs-lookup"><span data-stu-id="3fcb8-170">The following code sends two functions as arguments to `compose`, both of which take a single argument of the same type.</span></span> <span data-ttu-id="3fcb8-171">O valor de retorno é uma nova função que é uma composição dos argumentos da função de dois.</span><span class="sxs-lookup"><span data-stu-id="3fcb8-171">The return value is a new function that is a composition of the two function arguments.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet35.fs)]
    
>[!NOTE] 
<span data-ttu-id="3fcb8-172">F # fornece dois operadores, `<<` e `>>`, que compõem a funções.</span><span class="sxs-lookup"><span data-stu-id="3fcb8-172">F# provides two operators, `<<` and `>>`, that compose functions.</span></span> <span data-ttu-id="3fcb8-173">Por exemplo, `let squareAndDouble2 = doubleIt << squareIt` é equivalente a `let squareAndDouble = compose doubleIt squareIt` no exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="3fcb8-173">For example, `let squareAndDouble2 = doubleIt << squareIt` is equivalent to `let squareAndDouble = compose doubleIt squareIt` in the previous example.</span></span>

<span data-ttu-id="3fcb8-174">O exemplo de retorno de uma função como o valor de uma chamada de função a seguir cria um simples de adivinhação de jogo.</span><span class="sxs-lookup"><span data-stu-id="3fcb8-174">The following example of returning a function as the value of a function call creates a simple guessing game.</span></span> <span data-ttu-id="3fcb8-175">Para criar um jogo, chame `makeGame` com o valor que você deseja que alguém adivinhar enviada para `target`.</span><span class="sxs-lookup"><span data-stu-id="3fcb8-175">To create a game, call `makeGame` with the value that you want someone to guess sent in for `target`.</span></span> <span data-ttu-id="3fcb8-176">O valor de retorno da função `makeGame` é uma função que usa um argumento (a suposição) e informa se a previsão está correta.</span><span class="sxs-lookup"><span data-stu-id="3fcb8-176">The return value from function `makeGame` is a function that takes one argument (the guess) and reports whether the guess is correct.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet36.fs)]

<span data-ttu-id="3fcb8-177">O código a seguir chama `makeGame`, enviar o valor `7` para `target`.</span><span class="sxs-lookup"><span data-stu-id="3fcb8-177">The following code calls `makeGame`, sending the value `7` for `target`.</span></span> <span data-ttu-id="3fcb8-178">Identificador `playGame` está associada à expressão lambda retornado.</span><span class="sxs-lookup"><span data-stu-id="3fcb8-178">Identifier `playGame` is bound to the returned lambda expression.</span></span> <span data-ttu-id="3fcb8-179">Portanto, `playGame` é uma função que usa um valor como um argumento para `guess`.</span><span class="sxs-lookup"><span data-stu-id="3fcb8-179">Therefore, `playGame` is a function that takes as its one argument a value for `guess`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet37.fs)]
    
## <a name="curried-functions"></a><span data-ttu-id="3fcb8-180">Funções na forma curried</span><span class="sxs-lookup"><span data-stu-id="3fcb8-180">Curried Functions</span></span>

<span data-ttu-id="3fcb8-181">Muitos dos exemplos na seção anterior podem ser escritos mais maneira concisa, aproveitando o implícita *currying* nas declarações de função em F #.</span><span class="sxs-lookup"><span data-stu-id="3fcb8-181">Many of the examples in the previous section can be written more concisely by taking advantage of the implicit *currying* in F# function declarations.</span></span> <span data-ttu-id="3fcb8-182">Currying é um processo que transforma uma função que tem mais de um parâmetro em uma série de funções internas, cada qual com um único parâmetro.</span><span class="sxs-lookup"><span data-stu-id="3fcb8-182">Currying is a process that transforms a function that has more than one parameter into a series of embedded functions, each of which has a single parameter.</span></span> <span data-ttu-id="3fcb8-183">Em F #, funções que têm mais de um parâmetro são inerentemente na forma curried.</span><span class="sxs-lookup"><span data-stu-id="3fcb8-183">In F#, functions that have more than one parameter are inherently curried.</span></span> <span data-ttu-id="3fcb8-184">Por exemplo, `compose` da seção anterior pode ser escrito como mostrado no seguinte estilo conciso, com três parâmetros.</span><span class="sxs-lookup"><span data-stu-id="3fcb8-184">For example, `compose` from the previous section can be written as shown in the following concise style, with three parameters.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet38.fs)]

<span data-ttu-id="3fcb8-185">No entanto, o resultado é uma função de um parâmetro que retorna uma função de um parâmetro que por sua vez retorna outra função de um parâmetro, conforme mostrado no `compose4curried`.</span><span class="sxs-lookup"><span data-stu-id="3fcb8-185">However, the result is a function of one parameter that returns a function of one parameter that in turn returns another function of one parameter, as shown in `compose4curried`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet39.fs)]

<span data-ttu-id="3fcb8-186">Você pode acessar essa função de várias maneiras.</span><span class="sxs-lookup"><span data-stu-id="3fcb8-186">You can access this function in several ways.</span></span> <span data-ttu-id="3fcb8-187">Cada um dos exemplos a seguir retorna e exibe a 18.</span><span class="sxs-lookup"><span data-stu-id="3fcb8-187">Each of the following examples returns and displays 18.</span></span> <span data-ttu-id="3fcb8-188">Você pode substituir `compose4` com `compose4curried` em qualquer um dos exemplos.</span><span class="sxs-lookup"><span data-stu-id="3fcb8-188">You can replace `compose4` with `compose4curried` in any of the examples.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet40.fs)]

<span data-ttu-id="3fcb8-189">Para verificar se a função ainda funciona como antes, tente novamente os casos de teste originais.</span><span class="sxs-lookup"><span data-stu-id="3fcb8-189">To verify that the function still works as it did before, try the original test cases again.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet41.fs)]
    
>[!NOTE] 
<span data-ttu-id="3fcb8-190">Você pode restringir currying colocando parâmetros em tuplas.</span><span class="sxs-lookup"><span data-stu-id="3fcb8-190">You can restrict currying by enclosing parameters in tuples.</span></span> <span data-ttu-id="3fcb8-191">Para obter mais informações, consulte "Padrões de parâmetro" [parâmetros e argumentos](../language-reference/parameters-and-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="3fcb8-191">For more information, see "Parameter Patterns" in [Parameters and Arguments](../language-reference/parameters-and-arguments.md).</span></span>

<span data-ttu-id="3fcb8-192">O exemplo a seguir usa currying implícita para gravar uma versão reduzida da `makeGame`.</span><span class="sxs-lookup"><span data-stu-id="3fcb8-192">The following example uses implicit currying to write a shorter version of `makeGame`.</span></span> <span data-ttu-id="3fcb8-193">Os detalhes de como `makeGame` constrói e retorna o `game` função são menos explícitas neste formato, mas você pode verificar usando os casos de teste originais que o resultado é o mesmo.</span><span class="sxs-lookup"><span data-stu-id="3fcb8-193">The details of how `makeGame` constructs and returns the `game` function are less explicit in this format, but you can verify by using the original test cases that the result is the same.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet42.fs)]

<span data-ttu-id="3fcb8-194">Para obter mais informações sobre currying, consulte o "Aplicativo parcial de argumentos" [funções](../language-reference/functions/index.md).</span><span class="sxs-lookup"><span data-stu-id="3fcb8-194">For more information about currying, see "Partial Application of Arguments" in [Functions](../language-reference/functions/index.md).</span></span>


## <a name="identifier-and-function-definition-are-interchangeable"></a><span data-ttu-id="3fcb8-195">Identificador e uma definição de função são intercambiáveis</span><span class="sxs-lookup"><span data-stu-id="3fcb8-195">Identifier and Function Definition Are Interchangeable</span></span>
<span data-ttu-id="3fcb8-196">O nome da variável `num` no anterior exemplos é avaliada para o inteiro 10 e não é surpresa que foram `num` é válido, 10 também é válido.</span><span class="sxs-lookup"><span data-stu-id="3fcb8-196">The variable name `num` in the previous examples evaluates to the integer 10, and it is no surprise that where `num` is valid, 10 is also valid.</span></span> <span data-ttu-id="3fcb8-197">O mesmo é verdadeiro de identificadores de função e seus valores: em qualquer lugar do nome da função pode ser usado, a expressão lambda ao qual ele está vinculado pode ser usada.</span><span class="sxs-lookup"><span data-stu-id="3fcb8-197">The same is true of function identifiers and their values: anywhere the name of the function can be used, the lambda expression to which it is bound can be used.</span></span>

<span data-ttu-id="3fcb8-198">O exemplo a seguir define uma `Boolean` função chamada `isNegative`e usa o nome da função e a definição da função de maneira intercambiável.</span><span class="sxs-lookup"><span data-stu-id="3fcb8-198">The following example defines a `Boolean` function called `isNegative`, and then uses the name of the function and the definition of the function interchangeably.</span></span> <span data-ttu-id="3fcb8-199">Os três exemplos todos retornar e exibir `False`.</span><span class="sxs-lookup"><span data-stu-id="3fcb8-199">The next three examples all return and display `False`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet43.fs)]

<span data-ttu-id="3fcb8-200">Para ir um pouco mais, o valor de substituição que `applyIt` é vinculado ao `applyIt`.</span><span class="sxs-lookup"><span data-stu-id="3fcb8-200">To take it one step further, substitute the value that `applyIt` is bound to for `applyIt`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet44.fs)]

## <a name="functions-are-first-class-values-in-f"></a><span data-ttu-id="3fcb8-201">Funções são valores de primeira classe em F #</span><span class="sxs-lookup"><span data-stu-id="3fcb8-201">Functions Are First-Class Values in F#</span></span> #

<span data-ttu-id="3fcb8-202">Os exemplos nas seções anteriores demonstram que funções em F # atendem aos critérios para valores de primeira classe em F #:</span><span class="sxs-lookup"><span data-stu-id="3fcb8-202">The examples in the previous sections demonstrate that functions in F# satisfy the criteria for being first-class values in F#:</span></span>

- <span data-ttu-id="3fcb8-203">Você pode associar um identificador para uma definição de função.</span><span class="sxs-lookup"><span data-stu-id="3fcb8-203">You can bind an identifier to a function definition.</span></span>
[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet21.fs)]

- <span data-ttu-id="3fcb8-204">Você pode armazenar uma função em uma estrutura de dados.</span><span class="sxs-lookup"><span data-stu-id="3fcb8-204">You can store a function in a data structure.</span></span>
[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet45.fs)]

- <span data-ttu-id="3fcb8-205">Você pode passar uma função como um argumento.</span><span class="sxs-lookup"><span data-stu-id="3fcb8-205">You can pass a function as an argument.</span></span>
[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet46.fs)]

- <span data-ttu-id="3fcb8-206">Você pode retornar uma função como o valor de uma chamada de função.</span><span class="sxs-lookup"><span data-stu-id="3fcb8-206">You can return a function as the value of a function call.</span></span>
[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet32.fs)]

<span data-ttu-id="3fcb8-207">Para obter mais informações sobre F #, consulte o [referência da linguagem F #](../language-reference/index.md).</span><span class="sxs-lookup"><span data-stu-id="3fcb8-207">For more information about F#, see the [F# Language Reference](../language-reference/index.md).</span></span>

## <a name="example"></a><span data-ttu-id="3fcb8-208">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3fcb8-208">Example</span></span>

### <a name="description"></a><span data-ttu-id="3fcb8-209">Descrição</span><span class="sxs-lookup"><span data-stu-id="3fcb8-209">Description</span></span>

<span data-ttu-id="3fcb8-210">O código a seguir contém todos os exemplos neste tópico.</span><span class="sxs-lookup"><span data-stu-id="3fcb8-210">The following code contains all the examples in this topic.</span></span>

### <a name="code"></a><span data-ttu-id="3fcb8-211">Código</span><span class="sxs-lookup"><span data-stu-id="3fcb8-211">Code</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet47.fs)]
    
## <a name="see-also"></a><span data-ttu-id="3fcb8-212">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3fcb8-212">See Also</span></span>

[<span data-ttu-id="3fcb8-213">Listas</span><span class="sxs-lookup"><span data-stu-id="3fcb8-213">Lists</span></span>](../language-reference/lists.md)

[<span data-ttu-id="3fcb8-214">Tuplas</span><span class="sxs-lookup"><span data-stu-id="3fcb8-214">Tuples</span></span>](../language-reference/tuples.md)

[<span data-ttu-id="3fcb8-215">Funções</span><span class="sxs-lookup"><span data-stu-id="3fcb8-215">Functions</span></span>](../language-reference/functions/index.md)

[<span data-ttu-id="3fcb8-216">`let` Associações</span><span class="sxs-lookup"><span data-stu-id="3fcb8-216">`let` Bindings</span></span>](../language-reference/functions/let-bindings.md)

[<span data-ttu-id="3fcb8-217">Expressões lambda: A `fun` palavra-chave</span><span class="sxs-lookup"><span data-stu-id="3fcb8-217">Lambda Expressions: The `fun` Keyword</span></span>](../language-reference/functions/lambda-expressions-the-fun-keyword.md)
