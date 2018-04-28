---
title: Generalização automática (F#)
description: 'Saiba como F # automaticamente generaliza os argumentos e tipos de funções para que eles funcionem com vários tipos, quando possível.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 9b599fd9fe1220b41987bc14a420ed5740aa05f5
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2018
---
# <a name="automatic-generalization"></a><span data-ttu-id="c4135-103">Generalização automática</span><span class="sxs-lookup"><span data-stu-id="c4135-103">Automatic Generalization</span></span>

<span data-ttu-id="c4135-104">F # usa a inferência de tipo para avaliar os tipos de funções e expressões.</span><span class="sxs-lookup"><span data-stu-id="c4135-104">F# uses type inference to evaluate the types of functions and expressions.</span></span> <span data-ttu-id="c4135-105">Este tópico descreve como F # automaticamente generaliza os argumentos e tipos de funções para que eles funcionem com vários tipos, quando possível.</span><span class="sxs-lookup"><span data-stu-id="c4135-105">This topic describes how F# automatically generalizes the arguments and types of functions so that they work with multiple types when this is possible.</span></span>


## <a name="automatic-generalization"></a><span data-ttu-id="c4135-106">Generalização automática</span><span class="sxs-lookup"><span data-stu-id="c4135-106">Automatic Generalization</span></span>
<span data-ttu-id="c4135-107">O compilador F #, quando ele executa a inferência de tipo em uma função, determina se um determinado parâmetro pode ser genérico.</span><span class="sxs-lookup"><span data-stu-id="c4135-107">The F# compiler, when it performs type inference on a function, determines whether a given parameter can be generic.</span></span> <span data-ttu-id="c4135-108">O compilador examina cada parâmetro e determina se a função tem uma dependência no tipo específico de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="c4135-108">The compiler examines each parameter and determines whether the function has a dependency on the specific type of that parameter.</span></span> <span data-ttu-id="c4135-109">Se não estiver, o tipo é inferido para ser genérico.</span><span class="sxs-lookup"><span data-stu-id="c4135-109">If it does not, the type is inferred to be generic.</span></span>

<span data-ttu-id="c4135-110">O exemplo de código a seguir ilustra uma função que o compilador infere para ser genérico.</span><span class="sxs-lookup"><span data-stu-id="c4135-110">The following code example illustrates a function that the compiler infers to be generic.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet101.fs)]

<span data-ttu-id="c4135-111">O tipo é inferido para ser `'a -> 'a -> 'a`.</span><span class="sxs-lookup"><span data-stu-id="c4135-111">The type is inferred to be `'a -> 'a -> 'a`.</span></span>

<span data-ttu-id="c4135-112">O tipo indica que se trata de uma função que leva dois argumentos do mesmo tipo desconhecido e retorna um valor do mesmo tipo.</span><span class="sxs-lookup"><span data-stu-id="c4135-112">The type indicates that this is a function that takes two arguments of the same unknown type and returns a value of that same type.</span></span> <span data-ttu-id="c4135-113">Um dos motivos que a função anterior pode ser genérico é que o maior-que o operador (`>`) é genérico.</span><span class="sxs-lookup"><span data-stu-id="c4135-113">One of the reasons that the previous function can be generic is that the greater-than operator (`>`) is itself generic.</span></span> <span data-ttu-id="c4135-114">O maior-que o operador tem a assinatura `'a -> 'a -> bool`.</span><span class="sxs-lookup"><span data-stu-id="c4135-114">The greater-than operator has the signature `'a -> 'a -> bool`.</span></span> <span data-ttu-id="c4135-115">Nem todos os operadores são genéricos e se o código em uma função usa um tipo de parâmetro junto com uma função não genérico ou operador, esse tipo de parâmetro não pode ser generalizado.</span><span class="sxs-lookup"><span data-stu-id="c4135-115">Not all operators are generic, and if the code in a function uses a parameter type together with a non-generic function or operator, that parameter type cannot be generalized.</span></span>

<span data-ttu-id="c4135-116">Porque `max` é genérico, ele pode ser usado com tipos como `int`, `float`e assim por diante, conforme mostrado nos exemplos a seguir.</span><span class="sxs-lookup"><span data-stu-id="c4135-116">Because `max` is generic, it can be used with types such as `int`, `float`, and so on, as shown in the following examples.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet102.fs)]

<span data-ttu-id="c4135-117">No entanto, os dois argumentos devem ser do mesmo tipo.</span><span class="sxs-lookup"><span data-stu-id="c4135-117">However, the two arguments must be of the same type.</span></span> <span data-ttu-id="c4135-118">A assinatura é `'a -> 'a -> 'a`, não `'a -> 'b -> 'a`.</span><span class="sxs-lookup"><span data-stu-id="c4135-118">The signature is `'a -> 'a -> 'a`, not `'a -> 'b -> 'a`.</span></span> <span data-ttu-id="c4135-119">Portanto, o código a seguir produz um erro porque os tipos não correspondem.</span><span class="sxs-lookup"><span data-stu-id="c4135-119">Therefore, the following code produces an error because the types do not match.</span></span>

```fsharp
// Error: type mismatch.
let biggestIntFloat = max 2.0 3
```

<span data-ttu-id="c4135-120">O `max` função também funciona com qualquer tipo que oferece suporte à maior-que o operador.</span><span class="sxs-lookup"><span data-stu-id="c4135-120">The `max` function also works with any type that supports the greater-than operator.</span></span> <span data-ttu-id="c4135-121">Portanto, você também pode usá-lo em uma cadeia de caracteres, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="c4135-121">Therefore, you could also use it on a string, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet104.fs)]
    
## <a name="value-restriction"></a><span data-ttu-id="c4135-122">Restrição de valor</span><span class="sxs-lookup"><span data-stu-id="c4135-122">Value Restriction</span></span>
<span data-ttu-id="c4135-123">O compilador executa generalização automática somente em definições de função completa com argumentos explícitos e valores imutáveis simples.</span><span class="sxs-lookup"><span data-stu-id="c4135-123">The compiler performs automatic generalization only on complete function definitions that have explicit arguments, and on simple immutable values.</span></span>

<span data-ttu-id="c4135-124">Isso significa que o compilador emite um erro se você tentar compilar o código que não é suficientemente restrito para ser um tipo específico, mas também não é generalizável.</span><span class="sxs-lookup"><span data-stu-id="c4135-124">This means that the compiler issues an error if you try to compile code that is not sufficiently constrained to be a specific type, but is also not generalizable.</span></span> <span data-ttu-id="c4135-125">A mensagem de erro para esse problema se refere a essa restrição em generalização automática para valores como o *valor restrição*.</span><span class="sxs-lookup"><span data-stu-id="c4135-125">The error message for this problem refers to this restriction on automatic generalization for values as the *value restriction*.</span></span>

<span data-ttu-id="c4135-126">Normalmente, o erro de restrição de valor ocorre quando você deseja uma construção para ser genérico, mas o compilador não tem informações suficientes para generalizar ou quando você omitir acidentalmente informações suficientes do tipo em uma construção não genérica.</span><span class="sxs-lookup"><span data-stu-id="c4135-126">Typically, the value restriction error occurs either when you want a construct to be generic but the compiler has insufficient information to generalize it, or when you unintentionally omit sufficient type information in a nongeneric construct.</span></span> <span data-ttu-id="c4135-127">A solução para o erro de restrição de valor é fornecer informações mais explícitas para restringir mais totalmente o problema de inferência de tipo, em uma das seguintes maneiras:</span><span class="sxs-lookup"><span data-stu-id="c4135-127">The solution to the value restriction error is to provide more explicit information to more fully constrain the type inference problem, in one of the following ways:</span></span>


- <span data-ttu-id="c4135-128">Restringir um tipo a ser não-genérica pela adição de uma anotação de tipo explícito para um valor ou parâmetro.</span><span class="sxs-lookup"><span data-stu-id="c4135-128">Constrain a type to be nongeneric by adding an explicit type annotation to a value or parameter.</span></span>

- <span data-ttu-id="c4135-129">Se o problema está usando uma construção de nongeneralizable para definir uma função genérica, como uma composição de função ou completamente aplicada argumentos da função na forma curried, tente reescrever a função como uma definição de função comum.</span><span class="sxs-lookup"><span data-stu-id="c4135-129">If the problem is using a nongeneralizable construct to define a generic function, such as a function composition or incompletely applied curried function arguments, try to rewrite the function as an ordinary function definition.</span></span>

- <span data-ttu-id="c4135-130">Se o problema é uma expressão que é muito complexa para ser generalizado, torne-o em uma função adicionando um parâmetro extra, não utilizado.</span><span class="sxs-lookup"><span data-stu-id="c4135-130">If the problem is an expression that is too complex to be generalized, make it into a function by adding an extra, unused parameter.</span></span>

- <span data-ttu-id="c4135-131">Adicione parâmetros de tipo genérico explícito.</span><span class="sxs-lookup"><span data-stu-id="c4135-131">Add explicit generic type parameters.</span></span> <span data-ttu-id="c4135-132">Essa opção raramente é usada.</span><span class="sxs-lookup"><span data-stu-id="c4135-132">This option is rarely used.</span></span>

- <span data-ttu-id="c4135-133">Os exemplos de código a seguir ilustram cada um desses cenários.</span><span class="sxs-lookup"><span data-stu-id="c4135-133">The following code examples illustrate each of these scenarios.</span></span>

<span data-ttu-id="c4135-134">Caso 1: Uma expressão muito complexa.</span><span class="sxs-lookup"><span data-stu-id="c4135-134">Case 1: Too complex an expression.</span></span> <span data-ttu-id="c4135-135">Neste exemplo, a lista `counter` se destina a ser `int option ref`, mas ele não está definido como um valor imutável simples.</span><span class="sxs-lookup"><span data-stu-id="c4135-135">In this example, the list `counter` is intended to be `int option ref`, but it is not defined as a simple immutable value.</span></span>

```fsharp
let counter = ref None
// Adding a type annotation fixes the problem:
let counter : int option ref = ref None
```

<span data-ttu-id="c4135-136">Caso 2: Uso da construção nongeneralizable para definir uma função genérica.</span><span class="sxs-lookup"><span data-stu-id="c4135-136">Case 2: Using a nongeneralizable construct to define a generic function.</span></span> <span data-ttu-id="c4135-137">Neste exemplo, a construção é nongeneralizable porque ela envolve a aplicação parcial de argumentos de função.</span><span class="sxs-lookup"><span data-stu-id="c4135-137">In this example, the construct is nongeneralizable because it involves partial application of function arguments.</span></span>

```fsharp
let maxhash = max << hash
// The following is acceptable because the argument for maxhash is explicit:
let maxhash obj = (max << hash) obj
```

<span data-ttu-id="c4135-138">Caso 3: Adicionando um parâmetro extra, não utilizado.</span><span class="sxs-lookup"><span data-stu-id="c4135-138">Case 3: Adding an extra, unused parameter.</span></span> <span data-ttu-id="c4135-139">Como essa expressão não é simple o suficiente para generalização, o compilador emite o erro de restrição de valor.</span><span class="sxs-lookup"><span data-stu-id="c4135-139">Because this expression is not simple enough for generalization, the compiler issues the value restriction error.</span></span>

```fsharp
let emptyList10 = Array.create 10 []
// Adding an extra (unused) parameter makes it a function, which is generalizable.
let emptyList10 () = Array.create 10 []
```

<span data-ttu-id="c4135-140">Caso 4: Adicionando tipo parâmetros.</span><span class="sxs-lookup"><span data-stu-id="c4135-140">Case 4: Adding type parameters.</span></span>

```fsharp
let arrayOf10Lists = Array.create 10 []
// Adding a type parameter and type annotation lets you write a generic value.
let arrayOf10Lists<'T> = Array.create 10 ([]:'T list)
```

<span data-ttu-id="c4135-141">No último caso, o valor torna-se um tipo de função, que pode ser usado para criar valores de vários tipos diferentes, por exemplo da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="c4135-141">In the last case, the value becomes a type function, which may be used to create values of many different types, for example as follows:</span></span>

```fsharp
let intLists = arrayOf10Lists<int>
let floatLists = arrayOf10Lists<float>
```

## <a name="see-also"></a><span data-ttu-id="c4135-142">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c4135-142">See Also</span></span>
[<span data-ttu-id="c4135-143">Inferência de Tipos</span><span class="sxs-lookup"><span data-stu-id="c4135-143">Type Inference</span></span>](../type-inference.md)

[<span data-ttu-id="c4135-144">Genéricos</span><span class="sxs-lookup"><span data-stu-id="c4135-144">Generics</span></span>](index.md)

[<span data-ttu-id="c4135-145">Parâmetros de Tipo Resolvidos Estaticamente</span><span class="sxs-lookup"><span data-stu-id="c4135-145">Statically Resolved Type Parameters</span></span>](statically-resolved-type-parameters.md)

[<span data-ttu-id="c4135-146">Restrições</span><span class="sxs-lookup"><span data-stu-id="c4135-146">Constraints</span></span>](constraints.md)

