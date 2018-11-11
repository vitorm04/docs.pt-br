---
title: Funções (F#)
description: Saiba mais sobre funções em F# e como F# oferece suporte a construções de programação funcionais comuns.
ms.date: 05/16/2016
ms.openlocfilehash: 717eba7e69398048d229173e07ccc376797171bb
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/02/2018
ms.locfileid: "48839560"
---
# <a name="functions"></a><span data-ttu-id="095be-103">Funções</span><span class="sxs-lookup"><span data-stu-id="095be-103">Functions</span></span>

<span data-ttu-id="095be-104">As funções são a unidade fundamental de execução do programa em qualquer linguagem de programação.</span><span class="sxs-lookup"><span data-stu-id="095be-104">Functions are the fundamental unit of program execution in any programming language.</span></span> <span data-ttu-id="095be-105">Como em outras linguagens, uma função do F# tem um nome, pode ter parâmetros e receber argumentos, e tem um corpo.</span><span class="sxs-lookup"><span data-stu-id="095be-105">As in other languages, an F# function has a name, can have parameters and take arguments, and has a body.</span></span> <span data-ttu-id="095be-106">O F# também oferece suporte a construções de programação funcional como tratamento de funções como valores, uso de funções sem nome em expressões, composição de funções para formar novas funções, funções via currying e a definição implícita de funções por meio da aplicação parcial dos argumentos da função.</span><span class="sxs-lookup"><span data-stu-id="095be-106">F# also supports functional programming constructs such as treating functions as values, using unnamed functions in expressions, composition of functions to form new functions, curried functions, and the implicit definition of functions by way of the partial application of function arguments.</span></span>

<span data-ttu-id="095be-107">Defina funções usando a palavra-chave `let`, ou, se a função for recursiva, a combinação de palavras-chave `let rec`.</span><span class="sxs-lookup"><span data-stu-id="095be-107">You define functions by using the `let` keyword, or, if the function is recursive, the `let rec` keyword combination.</span></span>

## <a name="syntax"></a><span data-ttu-id="095be-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="095be-108">Syntax</span></span>

```fsharp
// Non-recursive function definition.
let [inline] function-name parameter-list [ : return-type ] = function-body
// Recursive function definition.
let rec function-name parameter-list = recursive-function-body
```

## <a name="remarks"></a><span data-ttu-id="095be-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="095be-109">Remarks</span></span>

<span data-ttu-id="095be-110">*function-name* é um identificador que representa a função.</span><span class="sxs-lookup"><span data-stu-id="095be-110">The *function-name* is an identifier that represents the function.</span></span> <span data-ttu-id="095be-111">*parameter-list* é formado por parâmetros sucessivos separados por espaços.</span><span class="sxs-lookup"><span data-stu-id="095be-111">The *parameter-list* consists of successive parameters that are separated by spaces.</span></span> <span data-ttu-id="095be-112">Você pode especificar um tipo explícito para cada parâmetro, conforme descrito na seção Parâmetros.</span><span class="sxs-lookup"><span data-stu-id="095be-112">You can specify an explicit type for each parameter, as described in the Parameters section.</span></span> <span data-ttu-id="095be-113">Se você não especificar um tipo de argumento específico, o compilador tentará inferir o tipo do corpo da função.</span><span class="sxs-lookup"><span data-stu-id="095be-113">If you do not specify a specific argument type, the compiler attempts to infer the type from the function body.</span></span> <span data-ttu-id="095be-114">*function-body* é formado por uma expressão.</span><span class="sxs-lookup"><span data-stu-id="095be-114">The *function-body* consists of an expression.</span></span> <span data-ttu-id="095be-115">A expressão que constitui o corpo da função normalmente é uma expressão composta formada por diversas expressões que culminam em uma expressão final, que é o valor de retorno.</span><span class="sxs-lookup"><span data-stu-id="095be-115">The expression that makes up the function body is typically a compound expression consisting of a number of expressions that culminate in a final expression that is the return value.</span></span> <span data-ttu-id="095be-116">*return-type* é um sinal de dois-pontos seguido por um tipo, e é opcional.</span><span class="sxs-lookup"><span data-stu-id="095be-116">The *return-type* is a colon followed by a type and is optional.</span></span> <span data-ttu-id="095be-117">Se você não especificar explicitamente o tipo do valor de retorno, o compilador determinará o tipo de retorno da expressão final.</span><span class="sxs-lookup"><span data-stu-id="095be-117">If you do not specify the type of the return value explicitly, the compiler determines the return type from the final expression.</span></span>

<span data-ttu-id="095be-118">Uma definição de função simples é semelhante à seguinte:</span><span class="sxs-lookup"><span data-stu-id="095be-118">A simple function definition resembles the following:</span></span>

```fsharp
let f x = x + 1
```

<span data-ttu-id="095be-119">No exemplo anterior, o nome da função é `f`, o argumento é `x`, que tem o tipo `int`, o corpo da função é `x + 1` e o valor de retorno é do tipo `int`.</span><span class="sxs-lookup"><span data-stu-id="095be-119">In the previous example, the function name is `f`, the argument is `x`, which has type `int`, the function body is `x + 1`, and the return value is of type `int`.</span></span>

<span data-ttu-id="095be-120">As funções podem ser marcadas como `inline`.</span><span class="sxs-lookup"><span data-stu-id="095be-120">Functions can be marked `inline`.</span></span> <span data-ttu-id="095be-121">Para saber mais sobre `inline`, veja [Funções embutidas](../functions/inline-functions.md).</span><span class="sxs-lookup"><span data-stu-id="095be-121">For information about `inline`, see [Inline Functions](../functions/inline-functions.md).</span></span>

## <a name="scope"></a><span data-ttu-id="095be-122">Escopo</span><span class="sxs-lookup"><span data-stu-id="095be-122">Scope</span></span>

<span data-ttu-id="095be-123">Em qualquer nível de escopo diferente do escopo do módulo, não é errado reutilizar um nome de função ou valor.</span><span class="sxs-lookup"><span data-stu-id="095be-123">At any level of scope other than module scope, it is not an error to reuse a value or function name.</span></span> <span data-ttu-id="095be-124">Se você reutilizar um nome, o nome declarado posteriormente cobrirá o nome declarado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="095be-124">If you reuse a name, the name declared later shadows the name declared earlier.</span></span> <span data-ttu-id="095be-125">No entanto, no escopo de nível superior em um módulo, os nomes devem ser exclusivos.</span><span class="sxs-lookup"><span data-stu-id="095be-125">However, at the top level scope in a module, names must be unique.</span></span> <span data-ttu-id="095be-126">Por exemplo, o código a seguir gera um erro quando é exibido no escopo do módulo, mas não quando aparece dentro de uma função:</span><span class="sxs-lookup"><span data-stu-id="095be-126">For example, the following code produces an error when it appears at module scope, but not when it appears inside a function:</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet101.fs)]

<span data-ttu-id="095be-127">Mas o código a seguir é aceitável em qualquer nível do escopo:</span><span class="sxs-lookup"><span data-stu-id="095be-127">But the following code is acceptable at any level of scope:</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet102.fs)]

### <a name="parameters"></a><span data-ttu-id="095be-128">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="095be-128">Parameters</span></span>

<span data-ttu-id="095be-129">Os nomes de parâmetros são listados após o nome da função.</span><span class="sxs-lookup"><span data-stu-id="095be-129">Names of parameters are listed after the function name.</span></span> <span data-ttu-id="095be-130">Você pode especificar um tipo para um parâmetro, conforme mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="095be-130">You can specify a type for a parameter, as shown in the following example:</span></span>

```fsharp
let f (x : int) = x + 1
```

<span data-ttu-id="095be-131">Se você especificar um tipo, ele virá após o nome do parâmetro e será separado do nome por dois-pontos.</span><span class="sxs-lookup"><span data-stu-id="095be-131">If you specify a type, it follows the name of the parameter and is separated from the name by a colon.</span></span> <span data-ttu-id="095be-132">Se você omitir o tipo do parâmetro, o tipo de parâmetro será inferido pelo compilador.</span><span class="sxs-lookup"><span data-stu-id="095be-132">If you omit the type for the parameter, the parameter type is inferred by the compiler.</span></span> <span data-ttu-id="095be-133">Por exemplo, na definição de função a seguir, o argumento `x` é inferido como sendo do tipo `int`, pois 1 é do tipo `int`.</span><span class="sxs-lookup"><span data-stu-id="095be-133">For example, in the following function definition, the argument `x` is inferred to be of type `int` because 1 is of type `int`.</span></span>

```fsharp
let f x = x + 1
```

<span data-ttu-id="095be-134">No entanto, o compilador tentará tornar a função a mais genérica possível.</span><span class="sxs-lookup"><span data-stu-id="095be-134">However, the compiler will attempt to make the function as generic as possible.</span></span> <span data-ttu-id="095be-135">Por exemplo, observe o código a seguir:</span><span class="sxs-lookup"><span data-stu-id="095be-135">For example, note the following code:</span></span>

```fsharp
let f x = (x, x)
```

<span data-ttu-id="095be-136">A função cria uma tupla de um argumento de qualquer tipo.</span><span class="sxs-lookup"><span data-stu-id="095be-136">The function creates a tuple from one argument of any type.</span></span> <span data-ttu-id="095be-137">Como o tipo não foi especificado, a função pode ser usada com qualquer tipo de argumento.</span><span class="sxs-lookup"><span data-stu-id="095be-137">Because the type is not specified, the function can be used with any argument type.</span></span> <span data-ttu-id="095be-138">Para saber mais, veja [Generalização automática](../generics/automatic-generalization.md).</span><span class="sxs-lookup"><span data-stu-id="095be-138">For more information, see [Automatic Generalization](../generics/automatic-generalization.md).</span></span>

## <a name="function-bodies"></a><span data-ttu-id="095be-139">Corpos de Função</span><span class="sxs-lookup"><span data-stu-id="095be-139">Function Bodies</span></span>

<span data-ttu-id="095be-140">O corpo de uma função pode conter definições de funções e variáveis locais.</span><span class="sxs-lookup"><span data-stu-id="095be-140">A function body can contain definitions of local variables and functions.</span></span> <span data-ttu-id="095be-141">Essas variáveis e funções estão no escopo no corpo da função atual, mas não fora dela.</span><span class="sxs-lookup"><span data-stu-id="095be-141">Such variables and functions are in scope in the body of the current function but not outside it.</span></span> <span data-ttu-id="095be-142">Quando a opção de sintaxe leve está habilitada, é necessário usar o recuo para indicar que uma definição está em um corpo de função, conforme mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="095be-142">When you have the lightweight syntax option enabled, you must use indentation to indicate that a definition is in a function body, as shown in the following example:</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet103.fs)]

<span data-ttu-id="095be-143">Para saber mais, veja [Diretrizes de formatação de código](../code-formatting-guidelines.md) e [Sintaxe detalhada](../verbose-syntax.md).</span><span class="sxs-lookup"><span data-stu-id="095be-143">For more information, see [Code Formatting Guidelines](../code-formatting-guidelines.md) and [Verbose Syntax](../verbose-syntax.md).</span></span>

## <a name="return-values"></a><span data-ttu-id="095be-144">Valores de Retorno</span><span class="sxs-lookup"><span data-stu-id="095be-144">Return Values</span></span>

<span data-ttu-id="095be-145">O compilador usa a expressão final em um corpo de função para determinar o valor de retorno e o tipo.</span><span class="sxs-lookup"><span data-stu-id="095be-145">The compiler uses the final expression in a function body to determine the return value and type.</span></span> <span data-ttu-id="095be-146">O compilador pode inferir o tipo da expressão final a partir das expressões anteriores.</span><span class="sxs-lookup"><span data-stu-id="095be-146">The compiler might infer the type of the final expression from previous expressions.</span></span> <span data-ttu-id="095be-147">Na função `cylinderVolume`, mostrada na seção anterior, o tipo de `pi` é determinado pelo tipo do literal `3.14159` como `float`.</span><span class="sxs-lookup"><span data-stu-id="095be-147">In the function `cylinderVolume`, shown in the previous section, the type of `pi` is determined from the type of the literal `3.14159` to be `float`.</span></span> <span data-ttu-id="095be-148">O compilador usa o tipo de `pi` para determinar o tipo da expressão `h * pi * r * r` como `float`.</span><span class="sxs-lookup"><span data-stu-id="095be-148">The compiler uses the type of `pi` to determine the type of the expression `h * pi * r * r` to be `float`.</span></span> <span data-ttu-id="095be-149">Portanto, o tipo de retorno geral da função é `float`.</span><span class="sxs-lookup"><span data-stu-id="095be-149">Therefore, the overall return type of the function is `float`.</span></span>

<span data-ttu-id="095be-150">Para especificar explicitamente o valor de retorno, escreva o código da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="095be-150">To specify the return value explicitly, write the code as follows:</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet105.fs)]

<span data-ttu-id="095be-151">À medida que o código é escrito acima, o compilador aplica **float** à função inteira; se você também pretende aplicá-lo aos tipos de parâmetro, use o código a seguir:</span><span class="sxs-lookup"><span data-stu-id="095be-151">As the code is written above, the compiler applies **float** to the entire function; if you mean to apply it to the parameter types as well, use the following code:</span></span>

```fsharp
let cylinderVolume (radius : float) (length : float) : float
```

## <a name="calling-a-function"></a><span data-ttu-id="095be-152">Chamando uma Função</span><span class="sxs-lookup"><span data-stu-id="095be-152">Calling a Function</span></span>

<span data-ttu-id="095be-153">Você pode chamar funções especificando o nome da função seguido por um espaço e por quaisquer argumentos, separados por espaços.</span><span class="sxs-lookup"><span data-stu-id="095be-153">You call functions by specifying the function name followed by a space and then any arguments separated by spaces.</span></span> <span data-ttu-id="095be-154">Por exemplo, para chamar a função **cylinderVolume** e atribuir o resultado para o valor **vol**, escreva o código a seguir:</span><span class="sxs-lookup"><span data-stu-id="095be-154">For example, to call the function **cylinderVolume** and assign the result to the value **vol**, you write the following code:</span></span>

```fsharp
let vol = cylinderVolume 2.0 3.0
```

## <a name="partial-application-of-arguments"></a><span data-ttu-id="095be-155">Aplicativo de Argumentos Parcial</span><span class="sxs-lookup"><span data-stu-id="095be-155">Partial Application of Arguments</span></span>

<span data-ttu-id="095be-156">Se você fornecer uma quantidade inferior ao número especificado de argumentos, criará uma nova função que esperará os argumentos restantes.</span><span class="sxs-lookup"><span data-stu-id="095be-156">If you supply fewer than the specified number of arguments, you create a new function that expects the remaining arguments.</span></span> <span data-ttu-id="095be-157">Esse método de manipulação de argumentos é conhecido como *currying*, e é uma característica de linguagens de programação funcionais como F#.</span><span class="sxs-lookup"><span data-stu-id="095be-157">This method of handling arguments is referred to as *currying* and is a characteristic of functional programming languages like F#.</span></span> <span data-ttu-id="095be-158">Por exemplo, vamos supor que você esteja trabalhando com dois tamanhos de pipe: uma com um raio de **2.0** e outro com um raio de **3.0**.</span><span class="sxs-lookup"><span data-stu-id="095be-158">For example, suppose you are working with two sizes of pipe: one has a radius of **2.0** and the other has a radius of **3.0**.</span></span> <span data-ttu-id="095be-159">Você poderia criar funções que determinam o volume do pipe da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="095be-159">You could create functions that determine the volume of pipe as follows:</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet106.fs)]

<span data-ttu-id="095be-160">Em seguida, você forneceria o argumento adicional, conforme o necessário, para várias durações de pipe dos dois tamanhos diferentes:</span><span class="sxs-lookup"><span data-stu-id="095be-160">You would then supply the additional argument as needed for various lengths of pipe of the two different sizes:</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet107.fs)]

## <a name="recursive-functions"></a><span data-ttu-id="095be-161">Funções Recursivas</span><span class="sxs-lookup"><span data-stu-id="095be-161">Recursive Functions</span></span>

<span data-ttu-id="095be-162">As *funções recursivas* são funções que chamam a si próprias.</span><span class="sxs-lookup"><span data-stu-id="095be-162">*Recursive functions* are functions that call themselves.</span></span> <span data-ttu-id="095be-163">Eles exigem que você especifique a palavra-chave **rec** logo após a palavra-chave **let**.</span><span class="sxs-lookup"><span data-stu-id="095be-163">They require that you specify the **rec** keyword following the **let** keyword.</span></span> <span data-ttu-id="095be-164">Invoque a função recursiva de dentro do corpo da função, exatamente como você invocaria qualquer chamada de função.</span><span class="sxs-lookup"><span data-stu-id="095be-164">Invoke the recursive function from within the body of the function just as you would invoke any function call.</span></span> <span data-ttu-id="095be-165">A função recursiva a seguir calcula a *n*<sup>th</sup> número Fibonacci.</span><span class="sxs-lookup"><span data-stu-id="095be-165">The following recursive function computes the *n*<sup>th</sup> Fibonacci number.</span></span> <span data-ttu-id="095be-166">A sequência numérica de Fibonacci é conhecida desde a antiguidade e é uma sequência na qual cada número sucessivo é a soma dos dois números anteriores na sequência.</span><span class="sxs-lookup"><span data-stu-id="095be-166">The Fibonacci number sequence has been known since antiquity and is a sequence in which each successive number is the sum of the previous two numbers in the sequence.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet108.fs)]

<span data-ttu-id="095be-167">Algumas funções recursivas podem estourar a pilha do programa ou executar de maneira ineficiente se não forem escritas com cuidado e com conhecimento de técnicas especiais, como o uso de acumuladores e continuações.</span><span class="sxs-lookup"><span data-stu-id="095be-167">Some recursive functions might overflow the program stack or perform inefficiently if you do not write them with care and with awareness of special techniques, such as the use of accumulators and continuations.</span></span>

## <a name="function-values"></a><span data-ttu-id="095be-168">Valores de Função</span><span class="sxs-lookup"><span data-stu-id="095be-168">Function Values</span></span>

<span data-ttu-id="095be-169">Em F#, todas as funções são consideradas valores; na verdade, elas são conhecidas como *valores de função*.</span><span class="sxs-lookup"><span data-stu-id="095be-169">In F#, all functions are considered values; in fact, they are known as *function values*.</span></span> <span data-ttu-id="095be-170">Como as funções são valores, elas podem ser usadas como argumentos de outras funções ou em outros contextos nos quais os valores são usados.</span><span class="sxs-lookup"><span data-stu-id="095be-170">Because functions are values, they can be used as arguments to other functions or in other contexts where values are used.</span></span> <span data-ttu-id="095be-171">Veja a seguir um exemplo de uma função que usa um valor de função como argumento:</span><span class="sxs-lookup"><span data-stu-id="095be-171">Following is an example of a function that takes a function value as an argument:</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet109.fs)]

<span data-ttu-id="095be-172">Especifique o tipo de valor de uma função usando o token `->`.</span><span class="sxs-lookup"><span data-stu-id="095be-172">You specify the type of a function value by using the `->` token.</span></span> <span data-ttu-id="095be-173">À esquerda desse token está o tipo do argumento, e à direita está o valor de retorno.</span><span class="sxs-lookup"><span data-stu-id="095be-173">On the left side of this token is the type of the argument, and on the right side is the return value.</span></span> <span data-ttu-id="095be-174">No exemplo anterior, `apply1` é uma função que use uma função `transform` como um argumento, em que `transform` é uma função que usa um inteiro e retorna outro inteiro.</span><span class="sxs-lookup"><span data-stu-id="095be-174">In the previous example, `apply1` is a function that takes a function `transform` as an argument, where `transform` is a function that takes an integer and returns another integer.</span></span> <span data-ttu-id="095be-175">O código a seguir mostra como usar `apply1`:</span><span class="sxs-lookup"><span data-stu-id="095be-175">The following code shows how to use `apply1`:</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet110.fs)]

<span data-ttu-id="095be-176">O valor de `result` será 101 após a execução do código anterior.</span><span class="sxs-lookup"><span data-stu-id="095be-176">The value of `result` will be 101 after the previous code runs.</span></span>

<span data-ttu-id="095be-177">Vários argumentos são separados por tokens `->` sucessivos, conforme mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="095be-177">Multiple arguments are separated by successive `->` tokens, as shown in the following example:</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet111.fs)]

<span data-ttu-id="095be-178">O resultado é 200.</span><span class="sxs-lookup"><span data-stu-id="095be-178">The result is 200.</span></span>

## <a name="lambda-expressions"></a><span data-ttu-id="095be-179">Expressões lambda</span><span class="sxs-lookup"><span data-stu-id="095be-179">Lambda Expressions</span></span>

<span data-ttu-id="095be-180">Uma *expressão lambda* é uma função sem nome.</span><span class="sxs-lookup"><span data-stu-id="095be-180">A *lambda expression* is an unnamed function.</span></span> <span data-ttu-id="095be-181">Nos exemplos anteriores, em vez de definir as funções nomeadas **increment** e **mul**, use expressões lambda, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="095be-181">In the previous examples, instead of defining named functions **increment** and **mul**, you could use lambda expressions as follows:</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet112.fs)]

<span data-ttu-id="095be-182">Defina expressões lambda usando a palavra-chave `fun`.</span><span class="sxs-lookup"><span data-stu-id="095be-182">You define lambda expressions by using the `fun` keyword.</span></span> <span data-ttu-id="095be-183">Uma expressão lambda é semelhante a uma definição de função, com exceção de que em vez do token `=`, o token `->` é usado para separar a lista de argumentos do corpo da função.</span><span class="sxs-lookup"><span data-stu-id="095be-183">A lambda expression resembles a function definition, except that instead of the `=` token, the `->` token is used to separate the argument list from the function body.</span></span> <span data-ttu-id="095be-184">Assim como em uma definição de função normal, os tipos de argumento podem ser inferidos ou explicitamente especificados, e o tipo de retorno da expressão lambda é inferido do tipo da última expressão no corpo.</span><span class="sxs-lookup"><span data-stu-id="095be-184">As in a regular function definition, the argument types can be inferred or specified explicitly, and the return type of the lambda expression is inferred from the type of the last expression in the body.</span></span> <span data-ttu-id="095be-185">Para saber mais, veja [Expressões lambda: a palavra-chave `fun`](../functions/lambda-expressions-the-fun-keyword.md).</span><span class="sxs-lookup"><span data-stu-id="095be-185">For more information, see [Lambda Expressions: The `fun` Keyword](../functions/lambda-expressions-the-fun-keyword.md).</span></span>

## <a name="function-composition-and-pipelining"></a><span data-ttu-id="095be-186">Composição de Função e Pipelining</span><span class="sxs-lookup"><span data-stu-id="095be-186">Function Composition and Pipelining</span></span>

<span data-ttu-id="095be-187">As funções em F# podem ser compostas de outras funções.</span><span class="sxs-lookup"><span data-stu-id="095be-187">Functions in F# can be composed from other functions.</span></span> <span data-ttu-id="095be-188">A composição de duas funções **função1** e **função2** é outra função que representa a aplicação da **função1** seguida pela aplicação da **função2**:</span><span class="sxs-lookup"><span data-stu-id="095be-188">The composition of two functions **function1** and **function2** is another function that represents the application of **function1** followed the application of **function2**:</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet113.fs)]

<span data-ttu-id="095be-189">O resultado é 202.</span><span class="sxs-lookup"><span data-stu-id="095be-189">The result is 202.</span></span>

<span data-ttu-id="095be-190">O pipelining permite o encadeamento de chamadas de função como operações sucessivas.</span><span class="sxs-lookup"><span data-stu-id="095be-190">Pipelining enables function calls to be chained together as successive operations.</span></span> <span data-ttu-id="095be-191">O pipelining funciona da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="095be-191">Pipelining works as follows:</span></span>

```fsharp
let result = 100 |> function1 |> function2
```

<span data-ttu-id="095be-192">O resultado é 202 novamente.</span><span class="sxs-lookup"><span data-stu-id="095be-192">The result is again 202.</span></span>

<span data-ttu-id="095be-193">Os operadores de composição usam duas funções e retornam uma função; por outro lado, os operadores de pipeline usam uma função e um argumento e retornam um valor.</span><span class="sxs-lookup"><span data-stu-id="095be-193">The composition operators take two functions and return a function; by contrast, the pipeline operators take a function and an argument and return a value.</span></span> <span data-ttu-id="095be-194">O exemplo de código a seguir mostra a diferença entre os operadores de pipeline e de composição, mostrando as diferenças no uso e nas assinaturas da função.</span><span class="sxs-lookup"><span data-stu-id="095be-194">The following code example shows the difference between the pipeline and composition operators by showing the differences in the function signatures and usage.</span></span>

```fsharp
// Function composition and pipeline operators compared.

let addOne x = x + 1
let timesTwo x = 2 * x

// Composition operator
// ( >> ) : ('T1 -> 'T2) -> ('T2 -> 'T3) -> 'T1 -> 'T3
let Compose2 = addOne >> timesTwo

// Backward composition operator
// ( << ) : ('T2 -> 'T3) -> ('T1 -> 'T2) -> 'T1 -> 'T3
let Compose1 = addOne << timesTwo

// Result is 5
let result1 = Compose1 2

// Result is 6
let result2 = Compose2 2

// Pipelining
// Pipeline operator
// ( |> ) : 'T1 -> ('T1 -> 'U) -> 'U
let Pipeline2 x = addOne x |> timesTwo

// Backward pipeline operator
// ( <| ) : ('T -> 'U) -> 'T -> 'U
let Pipeline1 x = addOne <| timesTwo x

// Result is 5
let result3 = Pipeline1 2

// Result is 6
let result4 = Pipeline2 2
```

## <a name="overloading-functions"></a><span data-ttu-id="095be-195">Sobrecarregando Funções</span><span class="sxs-lookup"><span data-stu-id="095be-195">Overloading Functions</span></span>

<span data-ttu-id="095be-196">Você pode sobrecarregar métodos de um tipo, mas não funções.</span><span class="sxs-lookup"><span data-stu-id="095be-196">You can overload methods of a type but not functions.</span></span> <span data-ttu-id="095be-197">Para saber mais, veja [Métodos](../members/methods.md).</span><span class="sxs-lookup"><span data-stu-id="095be-197">For more information, see [Methods](../members/methods.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="095be-198">Consulte também</span><span class="sxs-lookup"><span data-stu-id="095be-198">See also</span></span>

- [<span data-ttu-id="095be-199">Valores</span><span class="sxs-lookup"><span data-stu-id="095be-199">Values</span></span>](../values/index.md)
- [<span data-ttu-id="095be-200">Referência da Linguagem F#</span><span class="sxs-lookup"><span data-stu-id="095be-200">F# Language Reference</span></span>](../index.md)
