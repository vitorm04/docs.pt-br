---
title: Introdução à programação funcional em F#
description: Conheça os conceitos básicos da programação funcional no F#.
ms.date: 10/29/2018
ms.openlocfilehash: e1a0edc61dbe13012c48e166d490e22ebc70d6a0
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424705"
---
# <a name="introduction-to-functional-programming-in-f"></a><span data-ttu-id="728be-103">Introdução à programação funcional no F\#</span><span class="sxs-lookup"><span data-stu-id="728be-103">Introduction to Functional Programming in F\#</span></span>

<span data-ttu-id="728be-104">A programação funcional é um estilo de programação que enfatiza o uso de funções e dados imutáveis.</span><span class="sxs-lookup"><span data-stu-id="728be-104">Functional programming is a style of programming that emphasizes the use of functions and immutable data.</span></span> <span data-ttu-id="728be-105">A programação funcional digitada é quando a programação funcional é combinada com tipos estáticos F#, como com.</span><span class="sxs-lookup"><span data-stu-id="728be-105">Typed functional programming is when functional programming is combined with static types, such as with F#.</span></span> <span data-ttu-id="728be-106">Em geral, os seguintes conceitos são enfatizados na programação funcional:</span><span class="sxs-lookup"><span data-stu-id="728be-106">In general, the following concepts are emphasized in functional programming:</span></span>

* <span data-ttu-id="728be-107">Funções como as construções primárias que você usa</span><span class="sxs-lookup"><span data-stu-id="728be-107">Functions as the primary constructs you use</span></span>
* <span data-ttu-id="728be-108">Expressões em vez de instruções</span><span class="sxs-lookup"><span data-stu-id="728be-108">Expressions instead of statements</span></span>
* <span data-ttu-id="728be-109">Valores imutáveis sobre variáveis</span><span class="sxs-lookup"><span data-stu-id="728be-109">Immutable values over variables</span></span>
* <span data-ttu-id="728be-110">Programação declarativa sobre programação imperativa</span><span class="sxs-lookup"><span data-stu-id="728be-110">Declarative programming over imperative programming</span></span>

<span data-ttu-id="728be-111">Em toda esta série, você explorará os conceitos e padrões na programação F#funcional usando o.</span><span class="sxs-lookup"><span data-stu-id="728be-111">Throughout this series, you'll explore concepts and patterns in functional programming using F#.</span></span> <span data-ttu-id="728be-112">Ao longo do caminho, você aprenderá F# também.</span><span class="sxs-lookup"><span data-stu-id="728be-112">Along the way, you'll learn some F# too.</span></span>

## <a name="terminology"></a><span data-ttu-id="728be-113">Terminologia</span><span class="sxs-lookup"><span data-stu-id="728be-113">Terminology</span></span>

<span data-ttu-id="728be-114">A programação funcional, como outros paradigmas de programação, vem com um vocabulário que você eventualmente precisará aprender.</span><span class="sxs-lookup"><span data-stu-id="728be-114">Functional programming, like other programming paradigms, comes with a vocabulary that you will eventually need to learn.</span></span> <span data-ttu-id="728be-115">Aqui estão alguns termos comuns que você verá todo o tempo:</span><span class="sxs-lookup"><span data-stu-id="728be-115">Here are some common terms you'll see all of the time:</span></span>

* <span data-ttu-id="728be-116">**Função** – uma função é uma construção que produzirá uma saída quando uma entrada for fornecida.</span><span class="sxs-lookup"><span data-stu-id="728be-116">**Function** - A function is a construct that will produce an output when given an input.</span></span> <span data-ttu-id="728be-117">Mais formalmente, ele _mapeia_ um item de um conjunto para outro definido.</span><span class="sxs-lookup"><span data-stu-id="728be-117">More formally, it _maps_ an item from one set to another set.</span></span> <span data-ttu-id="728be-118">Essa formalização é levantada no concreto de várias maneiras, especialmente ao usar funções que operam em coleções de dados.</span><span class="sxs-lookup"><span data-stu-id="728be-118">This formalism is lifted into the concrete in many ways, especially when using functions that operate on collections of data.</span></span> <span data-ttu-id="728be-119">É o conceito mais básico (e importante) na programação funcional.</span><span class="sxs-lookup"><span data-stu-id="728be-119">It is the most basic (and important) concept in functional programming.</span></span>
* <span data-ttu-id="728be-120">**Expressão** -uma expressão é um constructo no código que produz um valor.</span><span class="sxs-lookup"><span data-stu-id="728be-120">**Expression** - An expression is a construct in code that produces a value.</span></span> <span data-ttu-id="728be-121">No F#, esse valor deve ser associado ou ignorado explicitamente.</span><span class="sxs-lookup"><span data-stu-id="728be-121">In F#, this value must be bound or explicitly ignored.</span></span> <span data-ttu-id="728be-122">Uma expressão pode ser substituída trivial por uma chamada de função.</span><span class="sxs-lookup"><span data-stu-id="728be-122">An expression can be trivially replaced by a function call.</span></span>
* <span data-ttu-id="728be-123">**Pureza** -pureza é uma propriedade de uma função, de modo que seu valor de retorno é sempre o mesmo para os mesmos argumentos e que sua avaliação não tem efeitos colaterais.</span><span class="sxs-lookup"><span data-stu-id="728be-123">**Purity** - Purity is a property of a function such that its return value is always the same for the same arguments, and that its evaluation has no side effects.</span></span> <span data-ttu-id="728be-124">Uma função pura depende inteiramente de seus argumentos.</span><span class="sxs-lookup"><span data-stu-id="728be-124">A pure function depends entirely on its arguments.</span></span>
* <span data-ttu-id="728be-125">**Transparência referencial** -transparência referencial é uma propriedade de expressões, de modo que elas possam ser substituídas por sua saída sem afetar o comportamento de um programa.</span><span class="sxs-lookup"><span data-stu-id="728be-125">**Referential Transparency** - Referential Transparency is a property of expressions such that they can be replaced with their output without affecting a program's behavior.</span></span>
* <span data-ttu-id="728be-126">**Imutabilidade** -imutabilidade significa que um valor não pode ser alterado in-loco.</span><span class="sxs-lookup"><span data-stu-id="728be-126">**Immutability** - Immutability means that a value cannot be changed in-place.</span></span> <span data-ttu-id="728be-127">Isso está em contraste com variáveis, que podem ser alteradas no local.</span><span class="sxs-lookup"><span data-stu-id="728be-127">This is in contrast with variables, which can change in place.</span></span>

## <a name="examples"></a><span data-ttu-id="728be-128">Exemplos</span><span class="sxs-lookup"><span data-stu-id="728be-128">Examples</span></span>

<span data-ttu-id="728be-129">Os exemplos a seguir demonstram esses conceitos principais.</span><span class="sxs-lookup"><span data-stu-id="728be-129">The following examples demonstrate these core concepts.</span></span>

### <a name="functions"></a><span data-ttu-id="728be-130">Funções</span><span class="sxs-lookup"><span data-stu-id="728be-130">Functions</span></span>

<span data-ttu-id="728be-131">A construção mais comum e fundamental na programação funcional é a função.</span><span class="sxs-lookup"><span data-stu-id="728be-131">The most common and fundamental construct in functional programming is the function.</span></span> <span data-ttu-id="728be-132">Aqui está uma função simples que adiciona 1 a um inteiro:</span><span class="sxs-lookup"><span data-stu-id="728be-132">Here's a simple function that adds 1 to an integer:</span></span>

```fsharp
let addOne x = x + 1
```

<span data-ttu-id="728be-133">Sua assinatura de tipo é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="728be-133">Its type signature is as follows:</span></span>

```fsharp
val addOne: x:int -> int
```

<span data-ttu-id="728be-134">A assinatura pode ser lida como "`addOne` aceita um `int` chamado `x` e produzirá um `int`".</span><span class="sxs-lookup"><span data-stu-id="728be-134">The signature can be read as, "`addOne` accepts an `int` named `x` and will produce an `int`".</span></span> <span data-ttu-id="728be-135">Mais formalmente, `addOne` está _mapeando_ um valor do conjunto de inteiros para o conjunto de inteiros.</span><span class="sxs-lookup"><span data-stu-id="728be-135">More formally, `addOne` is _mapping_ a value from the set of integers to the set of integers.</span></span> <span data-ttu-id="728be-136">O token de `->` significa esse mapeamento.</span><span class="sxs-lookup"><span data-stu-id="728be-136">The `->` token signifies this mapping.</span></span> <span data-ttu-id="728be-137">No F#, normalmente você pode examinar a assinatura da função para ter um sentido para o que ela faz.</span><span class="sxs-lookup"><span data-stu-id="728be-137">In F#, you can usually look at the function signature to get a sense for what it does.</span></span>

<span data-ttu-id="728be-138">Então, por que a assinatura é importante?</span><span class="sxs-lookup"><span data-stu-id="728be-138">So, why is the signature important?</span></span> <span data-ttu-id="728be-139">Na programação funcional digitada, a implementação de uma função é geralmente menos importante do que a assinatura de tipo real!</span><span class="sxs-lookup"><span data-stu-id="728be-139">In typed functional programming, the implementation of a function is often less important than the actual type signature!</span></span> <span data-ttu-id="728be-140">O fato de que `addOne` adiciona o valor 1 a um inteiro é interessante em tempo de execução, mas quando você está construindo um programa, o fato de que ele aceita e retorna um `int` é o que informa como você realmente usará essa função.</span><span class="sxs-lookup"><span data-stu-id="728be-140">The fact that `addOne` adds the value 1 to an integer is interesting at runtime, but when you are constructing a program, the fact that it accepts and returns an `int` is what informs how you will actually use this function.</span></span> <span data-ttu-id="728be-141">Além disso, depois de usar essa função corretamente (com relação à sua assinatura de tipo), o diagnóstico de qualquer problema pode ser feito somente dentro do corpo da função `addOne`.</span><span class="sxs-lookup"><span data-stu-id="728be-141">Furthermore, once you use this function correctly (with respect to its type signature), diagnosing any problems can be done only within the body of the `addOne` function.</span></span> <span data-ttu-id="728be-142">Este é o ímpeto por trás da programação funcional de tipo.</span><span class="sxs-lookup"><span data-stu-id="728be-142">This is the impetus behind typed functional programming.</span></span>

### <a name="expressions"></a><span data-ttu-id="728be-143">Expressões</span><span class="sxs-lookup"><span data-stu-id="728be-143">Expressions</span></span>

<span data-ttu-id="728be-144">As expressões são construções que são avaliadas como um valor.</span><span class="sxs-lookup"><span data-stu-id="728be-144">Expressions are constructs that evaluate to a value.</span></span> <span data-ttu-id="728be-145">Em contraste com as instruções, que executam uma ação, as expressões podem ser consideradas para executar uma ação que retorna um valor.</span><span class="sxs-lookup"><span data-stu-id="728be-145">In contrast to statements, which perform an action, expressions can be thought of performing an action that gives back a value.</span></span> <span data-ttu-id="728be-146">As expressões são quase sempre usadas em favor de instruções na programação funcional.</span><span class="sxs-lookup"><span data-stu-id="728be-146">Expressions are almost always used in favor of statements in functional programming.</span></span>

<span data-ttu-id="728be-147">Considere a função anterior, `addOne`.</span><span class="sxs-lookup"><span data-stu-id="728be-147">Consider the previous function, `addOne`.</span></span> <span data-ttu-id="728be-148">O corpo de `addOne` é uma expressão:</span><span class="sxs-lookup"><span data-stu-id="728be-148">The body of `addOne` is an expression:</span></span>

```fsharp
// 'x + 1' is an expression!
let addOne x = x + 1
```

<span data-ttu-id="728be-149">É o resultado dessa expressão que define o tipo de resultado da função `addOne`.</span><span class="sxs-lookup"><span data-stu-id="728be-149">It is the result of this expression that defines the result type of the `addOne` function.</span></span> <span data-ttu-id="728be-150">Por exemplo, a expressão que compõe essa função pode ser alterada para ser um tipo diferente, como uma `string`:</span><span class="sxs-lookup"><span data-stu-id="728be-150">For example, the expression that makes up this function could be changed to be a different type, such as a `string`:</span></span>

```fsharp
let addOne x = x.ToString() + "1"
```

<span data-ttu-id="728be-151">A assinatura da função agora é:</span><span class="sxs-lookup"><span data-stu-id="728be-151">The signature of the function is now:</span></span>

```fsharp
val addOne: x:'a -> string
```

<span data-ttu-id="728be-152">Como qualquer tipo no F# pode ter `ToString()` chamado, o tipo de `x` tornou-se genérico (chamado de [generalização automática](../language-reference/generics/automatic-generalization.md)) e o tipo resultante é um `string`.</span><span class="sxs-lookup"><span data-stu-id="728be-152">Since any type in F# can have `ToString()` called on it, the type of `x` has been made generic (called [Automatic Generalization](../language-reference/generics/automatic-generalization.md)), and the resultant type is a `string`.</span></span>

<span data-ttu-id="728be-153">As expressões não são apenas os corpos de funções.</span><span class="sxs-lookup"><span data-stu-id="728be-153">Expressions are not just the bodies of functions.</span></span> <span data-ttu-id="728be-154">Você pode ter expressões que produzem um valor que você usa em outro lugar.</span><span class="sxs-lookup"><span data-stu-id="728be-154">You can have expressions that produce a value you use elsewhere.</span></span> <span data-ttu-id="728be-155">Um comum é `if`:</span><span class="sxs-lookup"><span data-stu-id="728be-155">A common one is `if`:</span></span>

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

<span data-ttu-id="728be-156">A expressão `if` produz um valor chamado `result`.</span><span class="sxs-lookup"><span data-stu-id="728be-156">The `if` expression produces a value called `result`.</span></span> <span data-ttu-id="728be-157">Observe que você pode omitir `result` inteiramente, fazendo com que a expressão `if` o corpo da função `addOneIfOdd`.</span><span class="sxs-lookup"><span data-stu-id="728be-157">Note that you could omit `result` entirely, making the `if` expression the body of the `addOneIfOdd` function.</span></span> <span data-ttu-id="728be-158">O importante a ser lembrado sobre expressões é que elas produzem um valor.</span><span class="sxs-lookup"><span data-stu-id="728be-158">The key thing to remember about expressions is that they produce a value.</span></span>

<span data-ttu-id="728be-159">Há um tipo especial, `unit`, que é usado quando não há nada para retornar.</span><span class="sxs-lookup"><span data-stu-id="728be-159">There is a special type, `unit`, that is used when there is nothing to return.</span></span> <span data-ttu-id="728be-160">Por exemplo, considere esta simples função:</span><span class="sxs-lookup"><span data-stu-id="728be-160">For example, consider this simple function:</span></span>

```fsharp
let printString (str: string) =
    printfn "String is: %s" str
```

<span data-ttu-id="728be-161">A assinatura é parecida com esta:</span><span class="sxs-lookup"><span data-stu-id="728be-161">The signature looks like this:</span></span>

```fsharp
val printString: str:string -> unit
```

<span data-ttu-id="728be-162">O tipo de `unit` indica que não há nenhum valor real sendo retornado.</span><span class="sxs-lookup"><span data-stu-id="728be-162">The `unit` type indicates that there is no actual value being returned.</span></span> <span data-ttu-id="728be-163">Isso é útil quando você tem uma rotina que deve "fazer trabalho", apesar de não ter nenhum valor para retornar como resultado desse trabalho.</span><span class="sxs-lookup"><span data-stu-id="728be-163">This is useful when you have a routine that must "do work" despite having no value to return as a result of that work.</span></span>

<span data-ttu-id="728be-164">Isso é um contraste nítido à programação imperativa, em que o `if` construção equivalente é uma instrução, e a produção de valores geralmente é feita com variáveis de mutação.</span><span class="sxs-lookup"><span data-stu-id="728be-164">This is in sharp contrast to imperative programming, where the equivalent `if` construct is a statement, and producing values is often done with mutating variables.</span></span> <span data-ttu-id="728be-165">Por exemplo, no C#, o código pode ser escrito da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="728be-165">For example, in C#, the code might be written like this:</span></span>

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

<span data-ttu-id="728be-166">Vale a pena observar que C# e outras linguagens de estilo C oferecem suporte à [expressão Ternário](../../csharp/language-reference/operators/conditional-operator.md), que permite a programação condicional baseada em expressão.</span><span class="sxs-lookup"><span data-stu-id="728be-166">It's worth noting that C# and other C-style languages do support the [ternary expression](../../csharp/language-reference/operators/conditional-operator.md), which allows for expression-based conditional programming.</span></span>

<span data-ttu-id="728be-167">Na programação funcional, é raro converter valores com instruções.</span><span class="sxs-lookup"><span data-stu-id="728be-167">In functional programming, it is rare to mutate values with statements.</span></span> <span data-ttu-id="728be-168">Embora algumas linguagens funcionais suportem instruções e mutação, não é comum usar esses conceitos na programação funcional.</span><span class="sxs-lookup"><span data-stu-id="728be-168">Although some functional languages support statements and mutation, it is not common to use these concepts in functional programming.</span></span>

### <a name="pure-functions"></a><span data-ttu-id="728be-169">Funções puras</span><span class="sxs-lookup"><span data-stu-id="728be-169">Pure functions</span></span>

<span data-ttu-id="728be-170">Como mencionado anteriormente, as funções puras são funções que:</span><span class="sxs-lookup"><span data-stu-id="728be-170">As previously mentioned, pure functions are functions that:</span></span>

* <span data-ttu-id="728be-171">Sempre avalie o mesmo valor para a mesma entrada.</span><span class="sxs-lookup"><span data-stu-id="728be-171">Always evaluate to the same value for the same input.</span></span>
* <span data-ttu-id="728be-172">Não têm efeitos colaterais.</span><span class="sxs-lookup"><span data-stu-id="728be-172">Have no side effects.</span></span>

<span data-ttu-id="728be-173">É útil considerar as funções matemáticas neste contexto.</span><span class="sxs-lookup"><span data-stu-id="728be-173">It is helpful to think of mathematical functions in this context.</span></span> <span data-ttu-id="728be-174">Na matemática, as funções dependem apenas de seus argumentos e não têm nenhum efeito colateral.</span><span class="sxs-lookup"><span data-stu-id="728be-174">In mathematics, functions depend only on their arguments and do not have any side effects.</span></span> <span data-ttu-id="728be-175">Na função matemática `f(x) = x + 1`, o valor de `f(x)` depende apenas do valor de `x`.</span><span class="sxs-lookup"><span data-stu-id="728be-175">In the mathematical function `f(x) = x + 1`, the value of `f(x)` depends only on the value of `x`.</span></span> <span data-ttu-id="728be-176">Funções puras na programação funcional são as mesmas.</span><span class="sxs-lookup"><span data-stu-id="728be-176">Pure functions in functional programming are the same way.</span></span>

<span data-ttu-id="728be-177">Ao escrever uma função pura, a função deve depender apenas de seus argumentos e não executar nenhuma ação que resulte em um efeito colateral.</span><span class="sxs-lookup"><span data-stu-id="728be-177">When writing a pure function, the function must depend only on its arguments and not perform any action that results in a side effect.</span></span>

<span data-ttu-id="728be-178">Aqui está um exemplo de uma função não pura porque depende do estado global e mutável:</span><span class="sxs-lookup"><span data-stu-id="728be-178">Here is an example of a non-pure function because it depends on global, mutable state:</span></span>

```fsharp
let mutable value = 1

let addOneToValue x = x + value
```

<span data-ttu-id="728be-179">A função `addOneToValue` é claramente impura, porque `value` pode ser alterada a qualquer momento para ter um valor diferente de 1.</span><span class="sxs-lookup"><span data-stu-id="728be-179">The `addOneToValue` function is clearly impure, because `value` could be changed at any time to have a different value than 1.</span></span> <span data-ttu-id="728be-180">Esse padrão de dependendo de um valor global é ser evitado na programação funcional.</span><span class="sxs-lookup"><span data-stu-id="728be-180">This pattern of depending on a global value is to be avoided in functional programming.</span></span>

<span data-ttu-id="728be-181">Aqui está outro exemplo de uma função não pura, pois ela executa um efeito colateral:</span><span class="sxs-lookup"><span data-stu-id="728be-181">Here is another example of a non-pure function, because it performs a side effect:</span></span>

```fsharp
let addOneToValue x =
    printfn "x is %d" x
    x + 1
```

<span data-ttu-id="728be-182">Embora essa função não dependa de um valor global, ela grava o valor de `x` para a saída do programa.</span><span class="sxs-lookup"><span data-stu-id="728be-182">Although this function does not depend on a global value, it writes the value of `x` to the output of the program.</span></span> <span data-ttu-id="728be-183">Embora não haja nada inerentemente errado com isso, isso significa que a função não é pura.</span><span class="sxs-lookup"><span data-stu-id="728be-183">Although there is nothing inherently wrong with doing this, it does mean that the function is not pure.</span></span> <span data-ttu-id="728be-184">Se outra parte do seu programa depender de algo externo ao programa, como o buffer de saída, chamar essa função poderá afetar a outra parte do programa.</span><span class="sxs-lookup"><span data-stu-id="728be-184">If another part of your program depends on something external to the program, such as the output buffer, then calling this function can affect that other part of your program.</span></span>

<span data-ttu-id="728be-185">Remover a instrução `printfn` torna a função pura:</span><span class="sxs-lookup"><span data-stu-id="728be-185">Removing the `printfn` statement makes the function pure:</span></span>

```fsharp
let addOneToValue x = x + 1
```

<span data-ttu-id="728be-186">Embora essa função não seja inerentemente _melhor_ do que a versão anterior com a instrução `printfn`, ela garante que toda essa função seja retornar um valor.</span><span class="sxs-lookup"><span data-stu-id="728be-186">Although this function is not inherently _better_ than the previous version with the `printfn` statement, it does guarantee that all this function does is return a value.</span></span> <span data-ttu-id="728be-187">Chamar essa função quantas vezes produz o mesmo resultado: ele apenas produz um valor.</span><span class="sxs-lookup"><span data-stu-id="728be-187">Calling this function any number of times produces the same result: it just produces a value.</span></span> <span data-ttu-id="728be-188">A previsibilidade fornecida pela pureza é algo que muitos programadores funcionais buscam.</span><span class="sxs-lookup"><span data-stu-id="728be-188">The predictability given by purity is something many functional programmers strive for.</span></span>

### <a name="immutability"></a><span data-ttu-id="728be-189">Imutabilidade</span><span class="sxs-lookup"><span data-stu-id="728be-189">Immutability</span></span>

<span data-ttu-id="728be-190">Finalmente, um dos conceitos mais fundamentais da programação funcional tipada é a imutabilidade.</span><span class="sxs-lookup"><span data-stu-id="728be-190">Finally, one of the most fundamental concepts of typed functional programming is immutability.</span></span> <span data-ttu-id="728be-191">No F#, todos os valores são imutáveis por padrão.</span><span class="sxs-lookup"><span data-stu-id="728be-191">In F#, all values are immutable by default.</span></span> <span data-ttu-id="728be-192">Isso significa que eles não podem ser modificados in-loco, a menos que você os marque explicitamente como mutável.</span><span class="sxs-lookup"><span data-stu-id="728be-192">That means they cannot be mutated in-place unless you explicitly mark them as mutable.</span></span>

<span data-ttu-id="728be-193">Na prática, trabalhar com valores imutáveis significa que você altera sua abordagem de programação de, "preciso alterar algo", para "preciso produzir um novo valor".</span><span class="sxs-lookup"><span data-stu-id="728be-193">In practice, working with immutable values means that you change your approach to programming from, "I need to change something", to "I need to produce a new value".</span></span>

<span data-ttu-id="728be-194">Por exemplo, adicionar 1 a um valor significa produzir um novo valor, não mutando o existente:</span><span class="sxs-lookup"><span data-stu-id="728be-194">For example, adding 1 to a value means producing a new value, not mutating the existing one:</span></span>

```fsharp
let value = 1
let secondValue = value + 1
```

<span data-ttu-id="728be-195">No F#, o código a seguir **não modifica a** função `value`; em vez disso, ele executa uma verificação de igualdade:</span><span class="sxs-lookup"><span data-stu-id="728be-195">In F#, the following code does **not** mutate the `value` function; instead, it performs an equality check:</span></span>

```fsharp
let value = 1
value = value + 1 // Produces a 'bool' value!
```

<span data-ttu-id="728be-196">Algumas linguagens de programação funcional não oferecem suporte a mutação.</span><span class="sxs-lookup"><span data-stu-id="728be-196">Some functional programming languages do not support mutation at all.</span></span> <span data-ttu-id="728be-197">No F#, há suporte para ele, mas não é o comportamento padrão para valores.</span><span class="sxs-lookup"><span data-stu-id="728be-197">In F#, it is supported, but it is not the default behavior for values.</span></span>

<span data-ttu-id="728be-198">Esse conceito se estende ainda mais às estruturas de dados.</span><span class="sxs-lookup"><span data-stu-id="728be-198">This concept extends even further to data structures.</span></span> <span data-ttu-id="728be-199">Na programação funcional, estruturas de dados imutáveis como conjuntos (e muito mais) têm uma implementação diferente da que você pode esperar inicialmente.</span><span class="sxs-lookup"><span data-stu-id="728be-199">In functional programming, immutable data structures such as sets (and many more) have a different implementation than you might initially expect.</span></span> <span data-ttu-id="728be-200">Conceitualmente, algo como adicionar um item a um conjunto não altera o conjunto, ele produz um _novo_ conjunto com o valor adicionado.</span><span class="sxs-lookup"><span data-stu-id="728be-200">Conceptually, something like adding an item to a set does not change the set, it produces a _new_ set with the added value.</span></span> <span data-ttu-id="728be-201">Nos bastidores, isso geralmente é feito por uma estrutura de dados diferente que permite controlar com eficiência um valor para que a representação apropriada dos dados possa ser fornecida como resultado.</span><span class="sxs-lookup"><span data-stu-id="728be-201">Under the covers, this is often accomplished by a different data structure that allows for efficiently tracking a value so that the appropriate representation of the data can be given as a result.</span></span>

<span data-ttu-id="728be-202">Esse estilo de trabalho com valores e estruturas de dados é essencial, pois ele o força a tratar qualquer operação que modifique algo como se ele criasse uma nova versão dessa coisa.</span><span class="sxs-lookup"><span data-stu-id="728be-202">This style of working with values and data structures is critical, as it forces you to treat any operation that modifies something as if it creates a new version of that thing.</span></span> <span data-ttu-id="728be-203">Isso permite que coisas como igualdade e comparação sejam consistentes em seus programas.</span><span class="sxs-lookup"><span data-stu-id="728be-203">This allows for things like equality and comparability to be consistent in your programs.</span></span>

## <a name="next-steps"></a><span data-ttu-id="728be-204">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="728be-204">Next steps</span></span>

<span data-ttu-id="728be-205">A próxima seção abordará minuciosamente as funções, explorando diferentes maneiras de usá-las na programação funcional.</span><span class="sxs-lookup"><span data-stu-id="728be-205">The next section will thoroughly cover functions, exploring different ways you can use them in functional programming.</span></span>

<span data-ttu-id="728be-206">As [funções de primeira classe](first-class-functions.md) exploram as funções profundamente, mostrando como você pode usá-las em vários contextos.</span><span class="sxs-lookup"><span data-stu-id="728be-206">[First-class functions](first-class-functions.md) explores functions deeply, showing how you can use them in various contexts.</span></span>

## <a name="further-reading"></a><span data-ttu-id="728be-207">Leitura adicional</span><span class="sxs-lookup"><span data-stu-id="728be-207">Further reading</span></span>

<span data-ttu-id="728be-208">A série de [funções de raciocínio](https://fsharpforfunandprofit.com/posts/thinking-functionally-intro/) é outro grande recurso para aprender sobre a programação F#funcional com o.</span><span class="sxs-lookup"><span data-stu-id="728be-208">The [Thinking Functionally](https://fsharpforfunandprofit.com/posts/thinking-functionally-intro/) series is another great resource to learn about functional programming with F#.</span></span> <span data-ttu-id="728be-209">Ele aborda os conceitos básicos da programação funcional de forma pragmática e fácil de ler, usando F# recursos para ilustrar os conceitos.</span><span class="sxs-lookup"><span data-stu-id="728be-209">It covers fundamentals of functional programming in a pragmatic and easy-to-read way, using F# features to illustrate the concepts.</span></span>
