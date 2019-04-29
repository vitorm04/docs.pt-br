---
title: Introdução à programação funcional em F#
description: Conheça os conceitos básicos da programação funcional em F#.
ms.date: 10/29/2018
ms.openlocfilehash: 84022e58c0f17b9e9875402c653c31e494e940da
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61772782"
---
# <a name="introduction-to-functional-programming-in-f"></a><span data-ttu-id="1f7f5-103">Introdução à programação funcional em F\#</span><span class="sxs-lookup"><span data-stu-id="1f7f5-103">Introduction to Functional Programming in F\#</span></span>

<span data-ttu-id="1f7f5-104">Programação funcional é um estilo de programação que enfatiza o uso de funções e dados imutáveis.</span><span class="sxs-lookup"><span data-stu-id="1f7f5-104">Functional programming is a style of programming that emphasizes the use of functions and immutable data.</span></span> <span data-ttu-id="1f7f5-105">Programação funcional tipada é quando a programação funcional é combinada com tipos estáticos, como com F#.</span><span class="sxs-lookup"><span data-stu-id="1f7f5-105">Typed functional programming is when functional programming is combined with static types, such as with F#.</span></span> <span data-ttu-id="1f7f5-106">Em geral, os conceitos a seguir são enfatizados na programação funcional:</span><span class="sxs-lookup"><span data-stu-id="1f7f5-106">In general, the following concepts are emphasized in functional programming:</span></span>

* <span data-ttu-id="1f7f5-107">Funções como as principais construções em que você usar</span><span class="sxs-lookup"><span data-stu-id="1f7f5-107">Functions as the primary constructs you use</span></span>
* <span data-ttu-id="1f7f5-108">Expressões em vez de instruções</span><span class="sxs-lookup"><span data-stu-id="1f7f5-108">Expressions instead of statements</span></span>
* <span data-ttu-id="1f7f5-109">Valores imutáveis sobre as variáveis</span><span class="sxs-lookup"><span data-stu-id="1f7f5-109">Immutable values over variables</span></span>
* <span data-ttu-id="1f7f5-110">Programação declarativa sobre programação imperativa</span><span class="sxs-lookup"><span data-stu-id="1f7f5-110">Declarative programming over imperative programming</span></span>

<span data-ttu-id="1f7f5-111">Em toda esta série, você irá explorar os conceitos e padrões na programação funcional usando F#.</span><span class="sxs-lookup"><span data-stu-id="1f7f5-111">Throughout this series, you'll explore concepts and patterns in functional programming using F#.</span></span> <span data-ttu-id="1f7f5-112">Ao longo do caminho, você aprenderá sobre alguns F# muito.</span><span class="sxs-lookup"><span data-stu-id="1f7f5-112">Along the way, you'll learn some F# too.</span></span>

## <a name="terminology"></a><span data-ttu-id="1f7f5-113">Terminologia</span><span class="sxs-lookup"><span data-stu-id="1f7f5-113">Terminology</span></span>

<span data-ttu-id="1f7f5-114">Programação funcional, como outras paradigmas de programação, vem com um vocabulário que, eventualmente, você precisará aprender.</span><span class="sxs-lookup"><span data-stu-id="1f7f5-114">Functional programming, like other programming paradigms, comes with a vocabulary that you will eventually need to learn.</span></span> <span data-ttu-id="1f7f5-115">Aqui estão alguns termos comuns que você verá que o tempo todo:</span><span class="sxs-lookup"><span data-stu-id="1f7f5-115">Here are some common terms you'll see all of the time:</span></span>

* <span data-ttu-id="1f7f5-116">**Função** -uma função é uma construção que produzirá uma saída quando recebe uma entrada.</span><span class="sxs-lookup"><span data-stu-id="1f7f5-116">**Function** - A function is a construct that will produce an output when given an input.</span></span> <span data-ttu-id="1f7f5-117">Mais formalmente, ele _mapeia_ um item de um conjunto para outro conjunto.</span><span class="sxs-lookup"><span data-stu-id="1f7f5-117">More formally, it _maps_ an item from one set to another set.</span></span> <span data-ttu-id="1f7f5-118">Essa formalidade é elevada na concretas de várias maneiras, especialmente ao usar funções que operam em coleções de dados.</span><span class="sxs-lookup"><span data-stu-id="1f7f5-118">This formalism is lifted into the concrete in many ways, especially when using functions that operate on collections of data.</span></span> <span data-ttu-id="1f7f5-119">Ele é o conceito mais básico (e importante) na programação funcional.</span><span class="sxs-lookup"><span data-stu-id="1f7f5-119">It is the most basic (and important) concept in functional programming.</span></span> 
* <span data-ttu-id="1f7f5-120">**Expressão** -uma expressão é uma construção de código que produz um valor.</span><span class="sxs-lookup"><span data-stu-id="1f7f5-120">**Expression** - An expression is a construct in code that produces a value.</span></span> <span data-ttu-id="1f7f5-121">No F#, esse valor deve ser associado ou explicitamente ignorado.</span><span class="sxs-lookup"><span data-stu-id="1f7f5-121">In F#, this value must be bound or explicitly ignored.</span></span> <span data-ttu-id="1f7f5-122">Uma expressão pode ser facilmente substituída por uma chamada de função.</span><span class="sxs-lookup"><span data-stu-id="1f7f5-122">An expression can be trivially replaced by a function call.</span></span>
* <span data-ttu-id="1f7f5-123">**Pureza** -pureza é uma propriedade de uma função de modo que seu valor de retorno é sempre o mesmo para os mesmos argumentos, e que sua avaliação não tem efeitos colaterais.</span><span class="sxs-lookup"><span data-stu-id="1f7f5-123">**Purity** - Purity is a property of a function such that its return value is always the same for the same arguments, and that its evaluation has no side effects.</span></span> <span data-ttu-id="1f7f5-124">Uma função pura depende inteiramente em seus argumentos.</span><span class="sxs-lookup"><span data-stu-id="1f7f5-124">A pure function depends entirely on its arguments.</span></span>
* <span data-ttu-id="1f7f5-125">**Transparência referencial** -transparência referencial é uma propriedade de expressões, de modo que eles podem ser substituídos por suas saídas sem afetar o comportamento do programa.</span><span class="sxs-lookup"><span data-stu-id="1f7f5-125">**Referential Transparency** - Referential Transparency is a property of expressions such that they can be replaced with their output without affecting a program's behavior.</span></span>
* <span data-ttu-id="1f7f5-126">**Imutabilidade** -significa que a imutabilidade que um valor não pode ser alterada no local.</span><span class="sxs-lookup"><span data-stu-id="1f7f5-126">**Immutability** - Immutability means that a value cannot be changed in-place.</span></span> <span data-ttu-id="1f7f5-127">Isso é diferente das variáveis, que podem ser alterado em vigor.</span><span class="sxs-lookup"><span data-stu-id="1f7f5-127">This is in contrast with variables, which can change in place.</span></span>

## <a name="examples"></a><span data-ttu-id="1f7f5-128">Exemplos</span><span class="sxs-lookup"><span data-stu-id="1f7f5-128">Examples</span></span>

<span data-ttu-id="1f7f5-129">Os exemplos a seguir demonstram esses conceitos básicos.</span><span class="sxs-lookup"><span data-stu-id="1f7f5-129">The following examples demonstrate these core concepts.</span></span>

### <a name="functions"></a><span data-ttu-id="1f7f5-130">Funções</span><span class="sxs-lookup"><span data-stu-id="1f7f5-130">Functions</span></span>

<span data-ttu-id="1f7f5-131">Construção mais fundamental e comuns na programação funcional é a função.</span><span class="sxs-lookup"><span data-stu-id="1f7f5-131">The most common and fundamental construct in functional programming is the function.</span></span> <span data-ttu-id="1f7f5-132">Aqui está uma função simples que adiciona 1 em um inteiro:</span><span class="sxs-lookup"><span data-stu-id="1f7f5-132">Here's a simple function that adds 1 to an integer:</span></span>

```fsharp
let addOne x = x + 1
```

<span data-ttu-id="1f7f5-133">Sua assinatura do tipo é da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="1f7f5-133">Its type signature is as follows:</span></span>

```fsharp
val addOne: x:int -> int
```

<span data-ttu-id="1f7f5-134">A assinatura pode ser lido como, "`addOne` aceita um `int` denominado `x` e produzirá um `int`".</span><span class="sxs-lookup"><span data-stu-id="1f7f5-134">The signature can be read as, "`addOne` accepts an `int` named `x` and will produce an `int`".</span></span> <span data-ttu-id="1f7f5-135">Mais formalmente, `addOne` está _mapeamento_ um valor do conjunto de números inteiros para o conjunto de números inteiros.</span><span class="sxs-lookup"><span data-stu-id="1f7f5-135">More formally, `addOne` is _mapping_ a value from the set of integers to the set of integers.</span></span> <span data-ttu-id="1f7f5-136">O `->` token significa que esse mapeamento.</span><span class="sxs-lookup"><span data-stu-id="1f7f5-136">The `->` token signifies this mapping.</span></span> <span data-ttu-id="1f7f5-137">No F#, você pode examinar a assinatura de função para ter uma ideia para o que ele faz normalmente.</span><span class="sxs-lookup"><span data-stu-id="1f7f5-137">In F#, you can usually look at the function signature to get a sense for what it does.</span></span>

<span data-ttu-id="1f7f5-138">Então, por que é a assinatura importante?</span><span class="sxs-lookup"><span data-stu-id="1f7f5-138">So, why is the signature important?</span></span> <span data-ttu-id="1f7f5-139">Na programação funcional tipada, a implementação de uma função geralmente é menos importante do que a assinatura de tipo real!</span><span class="sxs-lookup"><span data-stu-id="1f7f5-139">In typed functional programming, the implementation of a function is often less important than the actual type signature!</span></span> <span data-ttu-id="1f7f5-140">O fato de que `addOne` adiciona o valor 1 para um número inteiro é interessante em tempo de execução, mas quando você estiver construindo um programa, o fato de que ele aceita e retorna um `int` é o que informa como você realmente usar essa função.</span><span class="sxs-lookup"><span data-stu-id="1f7f5-140">The fact that `addOne` adds the value 1 to an integer is interesting at runtime, but when you are constructing a program, the fact that it accepts and returns an `int` is what informs how you will actually use this function.</span></span> <span data-ttu-id="1f7f5-141">Além disso, depois que você usa essa função corretamente (com respeito à sua assinatura do tipo), diagnóstico de problemas pode ser feito somente dentro do corpo do `addOne` função.</span><span class="sxs-lookup"><span data-stu-id="1f7f5-141">Furthermore, once you use this function correctly (with respect to its type signature), diagnosing any problems can be done only within the body of the `addOne` function.</span></span> <span data-ttu-id="1f7f5-142">Esse é o motivo por trás da programação funcional tipada.</span><span class="sxs-lookup"><span data-stu-id="1f7f5-142">This is the impetus behind typed functional programming.</span></span>

### <a name="expressions"></a><span data-ttu-id="1f7f5-143">Expressões</span><span class="sxs-lookup"><span data-stu-id="1f7f5-143">Expressions</span></span>

<span data-ttu-id="1f7f5-144">As expressões são construções que avaliam um valor.</span><span class="sxs-lookup"><span data-stu-id="1f7f5-144">Expressions are constructs that evaluate to a value.</span></span> <span data-ttu-id="1f7f5-145">Em contraste com as instruções que executam uma ação, expressões podem ser consideradas executando uma ação que devolve um valor.</span><span class="sxs-lookup"><span data-stu-id="1f7f5-145">In contrast to statements, which perform an action, expressions can be thought of performing an action that gives back a value.</span></span> <span data-ttu-id="1f7f5-146">Expressões quase sempre são usadas em favor de instruções na programação funcional.</span><span class="sxs-lookup"><span data-stu-id="1f7f5-146">Expressions are almost always used in favor of statements in functional programming.</span></span>

<span data-ttu-id="1f7f5-147">Considere a função anterior, `addOne`.</span><span class="sxs-lookup"><span data-stu-id="1f7f5-147">Consider the previous function, `addOne`.</span></span> <span data-ttu-id="1f7f5-148">O corpo da `addOne` é uma expressão:</span><span class="sxs-lookup"><span data-stu-id="1f7f5-148">The body of `addOne` is an expression:</span></span>

```fsharp
// 'x + 1' is an expression!
let addOne x = x + 1
```

<span data-ttu-id="1f7f5-149">É o resultado dessa expressão que define o tipo de resultado de `addOne` função.</span><span class="sxs-lookup"><span data-stu-id="1f7f5-149">It is the result of this expression that defines the result type of the `addOne` function.</span></span> <span data-ttu-id="1f7f5-150">Por exemplo, a expressão que compõe essa função pode ser alterada para ser um tipo diferente, como um `string`:</span><span class="sxs-lookup"><span data-stu-id="1f7f5-150">For example, the expression that makes up this function could be changed to be a different type, such as a `string`:</span></span>

```fsharp
let addOne x = x.ToString() + "1"
```

<span data-ttu-id="1f7f5-151">A assinatura da função é agora:</span><span class="sxs-lookup"><span data-stu-id="1f7f5-151">The signature of the function is now:</span></span>

```fsharp
val addOne: x:'a -> string
```

<span data-ttu-id="1f7f5-152">Desde qualquer tipo em F# pode ter `ToString()` chamado nela, o tipo de `x` foi feita genérico (chamados [generalização automática](../language-reference/generics/automatic-generalization.md)), e o tipo resultante é um `string`.</span><span class="sxs-lookup"><span data-stu-id="1f7f5-152">Since any type in F# can have `ToString()` called on it, the type of `x` has been made generic (called [Automatic Generalization](../language-reference/generics/automatic-generalization.md)), and the resultant type is a `string`.</span></span>

<span data-ttu-id="1f7f5-153">Expressões não são apenas os corpos de funções.</span><span class="sxs-lookup"><span data-stu-id="1f7f5-153">Expressions are not just the bodies of functions.</span></span> <span data-ttu-id="1f7f5-154">Você pode ter expressões que produzem um valor que você pode usar em outro lugar.</span><span class="sxs-lookup"><span data-stu-id="1f7f5-154">You can have expressions that produce a value you use elsewhere.</span></span> <span data-ttu-id="1f7f5-155">Um comum que um é `if`:</span><span class="sxs-lookup"><span data-stu-id="1f7f5-155">A common one is `if`:</span></span>

```fsharp
// Checks if 'x' is odd by using the mod operator
let isOdd x = x % 2 <> 0

let addOneIfOdd input =
    let result =
        if isOdd input then
            input + 1
        else
            input

    result
```

<span data-ttu-id="1f7f5-156">O `if` expressão produzir um valor chamado `result`.</span><span class="sxs-lookup"><span data-stu-id="1f7f5-156">The `if` expression produces a value called `result`.</span></span> <span data-ttu-id="1f7f5-157">Observe que você poderia omitir `result` totalmente, tornando o `if` o corpo da expressão do `addOneIfOdd` função.</span><span class="sxs-lookup"><span data-stu-id="1f7f5-157">Note that you could omit `result` entirely, making the `if` expression the body of the `addOneIfOdd` function.</span></span> <span data-ttu-id="1f7f5-158">O mais importante lembrar sobre expressões é que eles produzem um valor.</span><span class="sxs-lookup"><span data-stu-id="1f7f5-158">The key thing to remember about expressions is that they produce a value.</span></span>

<span data-ttu-id="1f7f5-159">Há um tipo especial, `unit`, que é usado quando não há nada para retornar.</span><span class="sxs-lookup"><span data-stu-id="1f7f5-159">There is a special type, `unit`, that is used when there is nothing to return.</span></span> <span data-ttu-id="1f7f5-160">Por exemplo, considere essa função simples:</span><span class="sxs-lookup"><span data-stu-id="1f7f5-160">For example, consider this simple function:</span></span>

```fsharp
let printString (str: string) =
    printfn "String is: %s" str
```

<span data-ttu-id="1f7f5-161">A assinatura tem esta aparência:</span><span class="sxs-lookup"><span data-stu-id="1f7f5-161">The signature looks like this:</span></span>

```fsharp
val printString: str:string -> unit
```

<span data-ttu-id="1f7f5-162">O `unit` tipo indica que não há nenhum valor real que está sendo retornado.</span><span class="sxs-lookup"><span data-stu-id="1f7f5-162">The `unit` type indicates that there is no actual value being returned.</span></span> <span data-ttu-id="1f7f5-163">Isso é útil quando você tem uma rotina que deve "trabalho" Apesar de não ter nenhum valor a ser retornado como resultado desse trabalho.</span><span class="sxs-lookup"><span data-stu-id="1f7f5-163">This is useful when you have a routine that must "do work" despite having no value to return as a result of that work.</span></span>

<span data-ttu-id="1f7f5-164">Isso é um nítido contraste com programação imperativa, em que o equivalente `if` construção é uma instrução e produzir valores geralmente é feito com a mutação de variáveis.</span><span class="sxs-lookup"><span data-stu-id="1f7f5-164">This is in sharp contrast to imperative programming, where the equivalent `if` construct is a statement, and producing values is often done with mutating variables.</span></span> <span data-ttu-id="1f7f5-165">Por exemplo, em C#, o código pode ser escrito da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="1f7f5-165">For example, in C#, the code might be written like this:</span></span>

```csharp
bool IsOdd(int x) => x % 2 != 0;

int AddOneIfOdd(int input)
{
    var result = input;

    if (IsOdd(input))
    {
        result = input + 1;
    }

    return result;
}
```

<span data-ttu-id="1f7f5-166">Vale a pena observar que C# e outras linguagens de estilo C têm suporte para o [expressão ternária](../../csharp/language-reference/operators/conditional-operator.md), que permite a programação condicional baseada em expressão.</span><span class="sxs-lookup"><span data-stu-id="1f7f5-166">It's worth noting that C# and other C-style languages do support the [ternary expression](../../csharp/language-reference/operators/conditional-operator.md), which allows for expression-based conditional programming.</span></span>

<span data-ttu-id="1f7f5-167">Na programação funcional, é raro para modificar os valores com instruções.</span><span class="sxs-lookup"><span data-stu-id="1f7f5-167">In functional programming, it is rare to mutate values with statements.</span></span> <span data-ttu-id="1f7f5-168">Embora algumas linguagens funcionais ofereçam suporte a instruções e a mutação, não é comum usar esses conceitos em programação funcional.</span><span class="sxs-lookup"><span data-stu-id="1f7f5-168">Although some functional languages support statements and mutation, it is not common to use these concepts in functional programming.</span></span>

### <a name="pure-functions"></a><span data-ttu-id="1f7f5-169">Funções puras</span><span class="sxs-lookup"><span data-stu-id="1f7f5-169">Pure functions</span></span>

<span data-ttu-id="1f7f5-170">Como mencionadas anteriormente, puras funções são funções que:</span><span class="sxs-lookup"><span data-stu-id="1f7f5-170">As previously mentioned, pure functions are functions that:</span></span>

* <span data-ttu-id="1f7f5-171">Sempre avalie para o mesmo valor para a mesma entrada.</span><span class="sxs-lookup"><span data-stu-id="1f7f5-171">Always evaluate to the same value for the same input.</span></span>
* <span data-ttu-id="1f7f5-172">Não têm efeitos colaterais.</span><span class="sxs-lookup"><span data-stu-id="1f7f5-172">Have no side effects.</span></span>

<span data-ttu-id="1f7f5-173">É útil pensar em funções matemáticas neste contexto.</span><span class="sxs-lookup"><span data-stu-id="1f7f5-173">It is helpful to think of mathematical functions in this context.</span></span> <span data-ttu-id="1f7f5-174">Em matemática, funções dependem apenas em seus argumentos e não tem nenhum efeito colateral.</span><span class="sxs-lookup"><span data-stu-id="1f7f5-174">In mathematics, functions depend only on their arguments and do not have any side effects.</span></span> <span data-ttu-id="1f7f5-175">Na função matemática `f(x) = x + 1`, o valor da `f(x)` depende apenas do valor de `x`.</span><span class="sxs-lookup"><span data-stu-id="1f7f5-175">In the mathematical function `f(x) = x + 1`, the value of `f(x)` depends only on the value of `x`.</span></span> <span data-ttu-id="1f7f5-176">Funções puras na programação funcional são da mesma maneira.</span><span class="sxs-lookup"><span data-stu-id="1f7f5-176">Pure functions in functional programming are the same way.</span></span>

<span data-ttu-id="1f7f5-177">Ao escrever uma função pura, a função deve depender apenas de seus argumentos e não realiza qualquer ação que resulta em um efeito colateral.</span><span class="sxs-lookup"><span data-stu-id="1f7f5-177">When writing a pure function, the function must depend only on its arguments and not perform any action that results in a side effect.</span></span>

<span data-ttu-id="1f7f5-178">Aqui está um exemplo de uma função não pura porque ele depende do estado mutável, global:</span><span class="sxs-lookup"><span data-stu-id="1f7f5-178">Here is an example of a non-pure function because it depends on global, mutable state:</span></span>

```fsharp
let mutable value = 1

let addOneToValue x = x + value
```

<span data-ttu-id="1f7f5-179">O `addOneToValue` função é claramente impuras, porque `value` poderia ser alterado a qualquer momento para ter um valor diferente de 1.</span><span class="sxs-lookup"><span data-stu-id="1f7f5-179">The `addOneToValue` function is clearly impure, because `value` could be changed at any time to have a different value than 1.</span></span> <span data-ttu-id="1f7f5-180">Esse padrão de acordo com um valor global é a serem evitados na programação funcional.</span><span class="sxs-lookup"><span data-stu-id="1f7f5-180">This pattern of depending on a global value is to be avoided in functional programming.</span></span>

<span data-ttu-id="1f7f5-181">Aqui está outro exemplo de uma função não pura, pois ele executa um efeito colateral:</span><span class="sxs-lookup"><span data-stu-id="1f7f5-181">Here is another example of a non-pure function, because it performs a side effect:</span></span>

```fsharp
let addOneToValue x = 
    printfn "x is %d" x
    x + 1
```

<span data-ttu-id="1f7f5-182">Embora essa função não depende de um valor global, ele grava o valor de `x` para a saída do programa.</span><span class="sxs-lookup"><span data-stu-id="1f7f5-182">Although this function does not depend on a global value, it writes the value of `x` to the output of the program.</span></span> <span data-ttu-id="1f7f5-183">Embora não haja nada errado com isso, isso significa que a função não é pura.</span><span class="sxs-lookup"><span data-stu-id="1f7f5-183">Although there is nothing inherently wrong with doing this, it does mean that the function is not pure.</span></span> <span data-ttu-id="1f7f5-184">Se outra parte do seu programa depende de algo externo ao programa, como o buffer de saída, em seguida, chamar essa função pode afetar essa outra parte do seu programa.</span><span class="sxs-lookup"><span data-stu-id="1f7f5-184">If another part of your program depends on something external to the program, such as the output buffer, then calling this function can affect that other part of your program.</span></span>

<span data-ttu-id="1f7f5-185">Removendo o `printfn` instrução faz com que a função pura:</span><span class="sxs-lookup"><span data-stu-id="1f7f5-185">Removing the `printfn` statement makes the function pure:</span></span>

```fsharp
let addOneToValue x = x + 1
```

<span data-ttu-id="1f7f5-186">Embora essa função não é inerentemente _melhor_ que a versão anterior com o `printfn` instrução, ele garante que tudo o que essa função faz é retornar um valor.</span><span class="sxs-lookup"><span data-stu-id="1f7f5-186">Although this function is not inherently _better_ than the previous version with the `printfn` statement, it does guarantee that all this function does is return a value.</span></span> <span data-ttu-id="1f7f5-187">Chamar essa função a qualquer número de vezes que produz o mesmo resultado: ele produz apenas um valor.</span><span class="sxs-lookup"><span data-stu-id="1f7f5-187">Calling this function any number of times produces the same result: it just produces a value.</span></span> <span data-ttu-id="1f7f5-188">A capacidade de previsão fornecida por pureza é algo que muitos programadores funcionais se esforçam para.</span><span class="sxs-lookup"><span data-stu-id="1f7f5-188">The predictability given by purity is something many functional programmers strive for.</span></span>

### <a name="immutability"></a><span data-ttu-id="1f7f5-189">Imutabilidade</span><span class="sxs-lookup"><span data-stu-id="1f7f5-189">Immutability</span></span>

<span data-ttu-id="1f7f5-190">Por fim, um dos conceitos fundamentais da programação funcional tipada é imutabilidade.</span><span class="sxs-lookup"><span data-stu-id="1f7f5-190">Finally, one of the most fundamental concepts of typed functional programming is immutability.</span></span> <span data-ttu-id="1f7f5-191">No F#, todos os valores são imutáveis por padrão.</span><span class="sxs-lookup"><span data-stu-id="1f7f5-191">In F#, all values are immutable by default.</span></span> <span data-ttu-id="1f7f5-192">Isso significa que eles não podem ser mudados para a posição, a menos que você explicitamente marcá-los como mutáveis.</span><span class="sxs-lookup"><span data-stu-id="1f7f5-192">That means they cannot be mutated in-place unless you explicitly mark them as mutable.</span></span>

<span data-ttu-id="1f7f5-193">Na prática, trabalhar com valores imutáveis significa que você alterar sua abordagem à programação de "Preciso alterar algo", para "preciso gerar um novo valor".</span><span class="sxs-lookup"><span data-stu-id="1f7f5-193">In practice, working with immutable values means that you change your approach to programming from, "I need to change something", to "I need to produce a new value".</span></span>

<span data-ttu-id="1f7f5-194">Por exemplo, adicionando 1 como um valor significa que a produzir um novo valor, não a mutação existente:</span><span class="sxs-lookup"><span data-stu-id="1f7f5-194">For example, adding 1 to a value means producing a new value, not mutating the existing one:</span></span>

```fsharp
let value = 1
let secondValue = value + 1
```

<span data-ttu-id="1f7f5-195">No F#, o código a seguir faz **não** modifica o `value` função; em vez disso, ele executa uma verificação de igualdade:</span><span class="sxs-lookup"><span data-stu-id="1f7f5-195">In F#, the following code does **not** mutate the `value` function; instead, it performs an equality check:</span></span>

```fsharp
let value = 1
value = value + 1 // Produces a 'bool' value!
```

<span data-ttu-id="1f7f5-196">Algumas linguagens de programação funcionais não suportam mutação.</span><span class="sxs-lookup"><span data-stu-id="1f7f5-196">Some functional programming languages do not support mutation at all.</span></span> <span data-ttu-id="1f7f5-197">No F#, há suporte, mas não é o comportamento padrão para valores.</span><span class="sxs-lookup"><span data-stu-id="1f7f5-197">In F#, it is supported, but it is not the default behavior for values.</span></span>

<span data-ttu-id="1f7f5-198">Estende esse conceito ainda mais para estruturas de dados.</span><span class="sxs-lookup"><span data-stu-id="1f7f5-198">This concept extends even further to data structures.</span></span> <span data-ttu-id="1f7f5-199">Na programação funcional, estruturas de dados imutáveis, como conjuntos (e muito mais) têm uma implementação diferente que você pode inicialmente esperam.</span><span class="sxs-lookup"><span data-stu-id="1f7f5-199">In functional programming, immutable data structures such as sets (and many more) have a different implementation than you might initially expect.</span></span> <span data-ttu-id="1f7f5-200">Conceitualmente, algo assim que adicionar um item a um conjunto não altera o conjunto, ele produz um _novo_ definido com o valor agregado.</span><span class="sxs-lookup"><span data-stu-id="1f7f5-200">Conceptually, something like adding an item to a set does not change the set, it produces a _new_ set with the added value.</span></span> <span data-ttu-id="1f7f5-201">Nos bastidores, isso geralmente é feito por uma estrutura de dados diferentes que permite que um valor de controle com eficiência para que a representação apropriada dos dados pode ser fornecida como resultado.</span><span class="sxs-lookup"><span data-stu-id="1f7f5-201">Under the covers, this is often accomplished by a different data structure that allows for efficiently tracking a value so that the appropriate representation of the data can be given as a result.</span></span>

<span data-ttu-id="1f7f5-202">Esse estilo de trabalhar com valores e estruturas de dados é crítico, pois isso força você a tratar de qualquer operação que modifique algo como se ele cria uma nova versão dessa coisa.</span><span class="sxs-lookup"><span data-stu-id="1f7f5-202">This style of working with values and data structures is critical, as it forces you to treat any operation that modifies something as if it creates a new version of that thing.</span></span> <span data-ttu-id="1f7f5-203">Isso permite coisas como comparação e igualdade para ser consistente em seus programas.</span><span class="sxs-lookup"><span data-stu-id="1f7f5-203">This allows for things like equality and comparability to be consistent in your programs.</span></span>

## <a name="next-steps"></a><span data-ttu-id="1f7f5-204">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="1f7f5-204">Next steps</span></span>

<span data-ttu-id="1f7f5-205">A próxima seção abordará minuciosamente funções, explorando maneiras diferentes, você pode usá-los na programação funcional.</span><span class="sxs-lookup"><span data-stu-id="1f7f5-205">The next section will thoroughly cover functions, exploring different ways you can use them in functional programming.</span></span>

<span data-ttu-id="1f7f5-206">[Funções de primeira classe](first-class-functions.md) explora funções profundamente, mostrando como você pode usá-los em vários contextos.</span><span class="sxs-lookup"><span data-stu-id="1f7f5-206">[First-class functions](first-class-functions.md) explores functions deeply, showing how you can use them in various contexts.</span></span>

## <a name="further-reading"></a><span data-ttu-id="1f7f5-207">Leitura adicional</span><span class="sxs-lookup"><span data-stu-id="1f7f5-207">Further reading</span></span>

<span data-ttu-id="1f7f5-208">O [pensar funcionalmente](https://fsharpforfunandprofit.com/posts/thinking-functionally-intro/) série é outro excelente recurso para saber mais sobre programação funcional com F#.</span><span class="sxs-lookup"><span data-stu-id="1f7f5-208">The [Thinking Functionally](https://fsharpforfunandprofit.com/posts/thinking-functionally-intro/) series is another great resource to learn about functional programming with F#.</span></span> <span data-ttu-id="1f7f5-209">Ele abrange conceitos básicos da programação funcional de forma pragmática e fácil de ler, usando F# recursos para ilustrar os conceitos.</span><span class="sxs-lookup"><span data-stu-id="1f7f5-209">It covers fundamentals of functional programming in a pragmatic and easy-to-read way, using F# features to illustrate the concepts.</span></span>
