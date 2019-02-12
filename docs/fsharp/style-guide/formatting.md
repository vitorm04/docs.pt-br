---
title: F#diretrizes de formatação de código
description: Aprenda diretrizes de formatação F# código.
ms.date: 02/08/2019
ms.openlocfilehash: 7cbd8e4dd1f58cd974a8a12fc8a8c9ee92c546b4
ms.sourcegitcommit: d2ccb199ae6bc5787b4762e9ea6d3f6fe88677af
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56093613"
---
# <a name="f-code-formatting-guidelines"></a><span data-ttu-id="20a20-103">F#diretrizes de formatação de código</span><span class="sxs-lookup"><span data-stu-id="20a20-103">F# code formatting guidelines</span></span>

<span data-ttu-id="20a20-104">Este artigo oferece diretrizes para formatar seu código, de modo que seu F# é de código:</span><span class="sxs-lookup"><span data-stu-id="20a20-104">This article offers guidelines for how to format your code so that your F# code is:</span></span>

* <span data-ttu-id="20a20-105">Geralmente é visto como mais legível</span><span class="sxs-lookup"><span data-stu-id="20a20-105">Generally viewed as more legible</span></span>
* <span data-ttu-id="20a20-106">Está de acordo com as convenções aplicadas por ferramentas de formatação no Visual Studio e outros editores</span><span class="sxs-lookup"><span data-stu-id="20a20-106">Is in accordance with conventions applied by formatting tools in Visual Studio and other editors</span></span>
* <span data-ttu-id="20a20-107">Semelhante a outro código online</span><span class="sxs-lookup"><span data-stu-id="20a20-107">Similar to other code online</span></span>

<span data-ttu-id="20a20-108">Essas diretrizes se baseiam [um guia abrangente para F# convenções de formatação](https://github.com/dungpa/fantomas/blob/master/docs/FormattingConventions.md) por [Anh-Dung Phan](https://github.com/dungpa).</span><span class="sxs-lookup"><span data-stu-id="20a20-108">These guidelines are based on [A comprehensive guide to F# Formatting Conventions](https://github.com/dungpa/fantomas/blob/master/docs/FormattingConventions.md) by [Anh-Dung Phan](https://github.com/dungpa).</span></span>

## <a name="general-rules-for-indentation"></a><span data-ttu-id="20a20-109">Regras gerais para recuo</span><span class="sxs-lookup"><span data-stu-id="20a20-109">General rules for indentation</span></span>

<span data-ttu-id="20a20-110">F#Por padrão, usa o espaço em branco significativo.</span><span class="sxs-lookup"><span data-stu-id="20a20-110">F# uses significant white space by default.</span></span> <span data-ttu-id="20a20-111">As diretrizes a seguir destinam-se a fornecer orientação sobre como manipular alguns desafios que isso pode impor.</span><span class="sxs-lookup"><span data-stu-id="20a20-111">The following guidelines are intended to provide guidance as to how to juggle some challenges this can impose.</span></span>

### <a name="using-spaces"></a><span data-ttu-id="20a20-112">Uso de espaços</span><span class="sxs-lookup"><span data-stu-id="20a20-112">Using spaces</span></span>

<span data-ttu-id="20a20-113">Quando recuo é necessário, você deve usar espaços, tabulações não.</span><span class="sxs-lookup"><span data-stu-id="20a20-113">When indentation is required, you must use spaces, not tabs.</span></span> <span data-ttu-id="20a20-114">Pelo menos um espaço é necessário.</span><span class="sxs-lookup"><span data-stu-id="20a20-114">At least one space is required.</span></span> <span data-ttu-id="20a20-115">Sua organização pode criar padrões de codificação para especificar o número de espaços a serem usados para recuo; dois, três ou quatro espaços de recuo em cada nível em que ocorre o recuo é típico.</span><span class="sxs-lookup"><span data-stu-id="20a20-115">Your organization can create coding standards to specify the number of spaces to use for indentation; two, three or four spaces of indentation at each level where indentation occurs is typical.</span></span>

<span data-ttu-id="20a20-116">**Recomendamos 4 espaços por recuo.**</span><span class="sxs-lookup"><span data-stu-id="20a20-116">**We recommend 4 spaces per indentation.**</span></span>

<span data-ttu-id="20a20-117">Dito isso, o recuo dos programas é uma questão subjetiva.</span><span class="sxs-lookup"><span data-stu-id="20a20-117">That said, indentation of programs is a subjective matter.</span></span> <span data-ttu-id="20a20-118">Variações são Okey, mas é a primeira regra que você deve seguir *consistência de recuo*.</span><span class="sxs-lookup"><span data-stu-id="20a20-118">Variations are OK, but the first rule you should follow is *consistency of indentation*.</span></span> <span data-ttu-id="20a20-119">Escolha um estilo de recuo de geralmente aceito e usá-lo sistematicamente em toda a sua base de código.</span><span class="sxs-lookup"><span data-stu-id="20a20-119">Choose a generally accepted style of indentation and use it systematically throughout your codebase.</span></span>

## <a name="formatting-white-space"></a><span data-ttu-id="20a20-120">Formatação de espaço em branco</span><span class="sxs-lookup"><span data-stu-id="20a20-120">Formatting white space</span></span>

<span data-ttu-id="20a20-121">F#espaço em branco são confidenciais.</span><span class="sxs-lookup"><span data-stu-id="20a20-121">F# is white space sensitive.</span></span> <span data-ttu-id="20a20-122">Embora a maioria das semânticas de espaço em branco são cobertas pelo recuo adequado, há algumas outras coisas a considerar.</span><span class="sxs-lookup"><span data-stu-id="20a20-122">Although most semantics from white space are covered by proper indentation, there are some other things to consider.</span></span>

### <a name="formatting-operators-in-arithmetic-expressions"></a><span data-ttu-id="20a20-123">Formatação de operadores em expressões aritméticas</span><span class="sxs-lookup"><span data-stu-id="20a20-123">Formatting operators in arithmetic expressions</span></span>

<span data-ttu-id="20a20-124">Sempre use o espaço em branco em torno das expressões aritméticas binários:</span><span class="sxs-lookup"><span data-stu-id="20a20-124">Always use white space around binary arithmetic expressions:</span></span>

```fsharp
let subtractThenAdd x = x - 1 + 3
```

<span data-ttu-id="20a20-125">Unário `-` operadores sempre devem ter o valor que eles são negando seguem imediatamente:</span><span class="sxs-lookup"><span data-stu-id="20a20-125">Unary `-` operators should always have the value they are negating immediately follow:</span></span>

```fsharp
// OK
let negate x = -x

// Bad
let negateBad x = - x
```

<span data-ttu-id="20a20-126">Adição de um caractere de espaço em branco após o `-` operador pode causar confusão para outras pessoas.</span><span class="sxs-lookup"><span data-stu-id="20a20-126">Adding a white-space character after the `-` operator can lead to confusion for others.</span></span>

<span data-ttu-id="20a20-127">Em resumo, é importante sempre:</span><span class="sxs-lookup"><span data-stu-id="20a20-127">In summary, it's important to always:</span></span>

* <span data-ttu-id="20a20-128">Operadores binários de surround com espaço em branco</span><span class="sxs-lookup"><span data-stu-id="20a20-128">Surround binary operators with white space</span></span>
* <span data-ttu-id="20a20-129">Nunca ter espaço em branco à direita após um operador unário</span><span class="sxs-lookup"><span data-stu-id="20a20-129">Never have trailing white space after a unary operator</span></span>

<span data-ttu-id="20a20-130">A diretriz de binário operador aritmético é especialmente importante.</span><span class="sxs-lookup"><span data-stu-id="20a20-130">The binary arithmetic operator guideline is especially important.</span></span> <span data-ttu-id="20a20-131">Falha ao colocar um binário `-` operador, quando combinado com determinadas opções de formatação, pode levar a Interpretando-o como um unário `-`.</span><span class="sxs-lookup"><span data-stu-id="20a20-131">Failing to surround a binary `-` operator, when combined with certain formatting choices, could lead to interpreting it as a unary `-`.</span></span>

### <a name="surround-a-custom-operator-definition-with-white-space"></a><span data-ttu-id="20a20-132">Coloque uma definição de operador personalizado com espaço em branco</span><span class="sxs-lookup"><span data-stu-id="20a20-132">Surround a custom operator definition with white space</span></span>

<span data-ttu-id="20a20-133">Sempre use o espaço em branco ao redor de uma definição de operador:</span><span class="sxs-lookup"><span data-stu-id="20a20-133">Always use white space to surround an operator definition:</span></span>

```fsharp
// OK
let ( !> ) x f = f x

// Bad
let (!>) x f = f x
```

<span data-ttu-id="20a20-134">Para qualquer operador personalizado que começa com `*`, você precisará adicionar um espaço em branco para o início da definição para evitar uma ambiguidade de compilador.</span><span class="sxs-lookup"><span data-stu-id="20a20-134">For any custom operator that starts with `*`, you'll need to add a white space to the beginning of the definition to avoid a compiler ambiguity.</span></span> <span data-ttu-id="20a20-135">Por isso, é recomendável que você simplesmente colocar as definições de todos os operadores com um único caractere de espaço em branco.</span><span class="sxs-lookup"><span data-stu-id="20a20-135">Because of this, it's recommended that you simply surround the definitions of all operators with a single white-space character.</span></span>

### <a name="surround-function-parameter-arrows-with-white-space"></a><span data-ttu-id="20a20-136">Coloque as setas de parâmetro de função com espaço em branco</span><span class="sxs-lookup"><span data-stu-id="20a20-136">Surround function parameter arrows with white space</span></span>

<span data-ttu-id="20a20-137">Ao definir a assinatura de uma função, use o espaço em branco em torno de `->` símbolo:</span><span class="sxs-lookup"><span data-stu-id="20a20-137">When defining the signature of a function, use white space around the `->` symbol:</span></span>

```fsharp
// OK
type MyFun = int -> int -> string

// Bad
type MyFunBad = int->int->string
```

## <a name="formatting-blank-lines"></a><span data-ttu-id="20a20-138">Formatação de linhas em branco</span><span class="sxs-lookup"><span data-stu-id="20a20-138">Formatting blank lines</span></span>

* <span data-ttu-id="20a20-139">Separado nível superior função e classe definições com duas linhas em branco.</span><span class="sxs-lookup"><span data-stu-id="20a20-139">Separate top-level function and class definitions with two blank lines.</span></span>
* <span data-ttu-id="20a20-140">As definições de método dentro de uma classe são separadas por uma única linha em branco.</span><span class="sxs-lookup"><span data-stu-id="20a20-140">Method definitions inside a class are separated by a single blank line.</span></span>
* <span data-ttu-id="20a20-141">Linhas em branco extra podem ser usadas (com moderação) para separar grupos de funções relacionadas.</span><span class="sxs-lookup"><span data-stu-id="20a20-141">Extra blank lines may be used (sparingly) to separate groups of related functions.</span></span> <span data-ttu-id="20a20-142">Linhas em branco podem ser omitidas entre um monte de linhas relacionadas (por exemplo, um conjunto de implementações fictícias).</span><span class="sxs-lookup"><span data-stu-id="20a20-142">Blank lines may be omitted between a bunch of related one-liners (for example, a set of dummy implementations).</span></span>
* <span data-ttu-id="20a20-143">Use linhas em branco em funções, com moderação, para indicar seções lógicas.</span><span class="sxs-lookup"><span data-stu-id="20a20-143">Use blank lines in functions, sparingly, to indicate logical sections.</span></span>

## <a name="formatting-comments"></a><span data-ttu-id="20a20-144">Comentários de formatação</span><span class="sxs-lookup"><span data-stu-id="20a20-144">Formatting comments</span></span>

<span data-ttu-id="20a20-145">Geralmente prefiro vários comentários de barra dupla ao longo de comentários do bloco de estilo de ML.</span><span class="sxs-lookup"><span data-stu-id="20a20-145">Generally prefer multiple double-slash comments over ML-style block comments.</span></span>

```fsharp
// Prefer this style of comments when you want
// to express written ideas on multiple lines.

(*
    ML-style comments are fine, but not a .NET-ism.
    They are useful when needing to modify multi-line comments, though.
*)
```

<span data-ttu-id="20a20-146">Comentários embutidos devem colocar em maiuscula a primeira letra.</span><span class="sxs-lookup"><span data-stu-id="20a20-146">Inline comments should capitalize the first letter.</span></span>

```fsharp
let f x = x + 1 // Increment by one.
```

## <a name="naming-conventions"></a><span data-ttu-id="20a20-147">Convenções de nomenclatura</span><span class="sxs-lookup"><span data-stu-id="20a20-147">Naming conventions</span></span>

### <a name="use-camelcase-for-class-bound-expression-bound-and-pattern-bound-values-and-functions"></a><span data-ttu-id="20a20-148">Use camelCase para valores de limite de classe, expressão ligada à e padrão de associação e funções</span><span class="sxs-lookup"><span data-stu-id="20a20-148">Use camelCase for class-bound, expression-bound and pattern-bound values and functions</span></span>

<span data-ttu-id="20a20-149">É comum e aceitos F# estilo a ser usado em camelCase para todos os nomes associados como variáveis locais ou em correspondências de padrões e as definições de função.</span><span class="sxs-lookup"><span data-stu-id="20a20-149">It is common and accepted F# style to use camelCase for all names bound as local variables or in pattern matches and function definitions.</span></span>

```fsharp
// OK
let addIAndJ i j = i + j

// Bad
let addIAndJ I J = I+J

// Bad
let AddIAndJ i j = i + j
```

<span data-ttu-id="20a20-150">Funções associadas a localmente em classes também devem usar camelCase.</span><span class="sxs-lookup"><span data-stu-id="20a20-150">Locally-bound functions in classes should also use camelCase.</span></span>

```fsharp
type MyClass() =

    let doSomething () =

    let firstResult = ...

    let secondResult = ...

    member x.Result = doSomething()
```

### <a name="use-camelcase-for-module-bound-public-functions"></a><span data-ttu-id="20a20-151">Use camelCase para funções públicas de associação de módulo</span><span class="sxs-lookup"><span data-stu-id="20a20-151">Use camelCase for module-bound public functions</span></span>

<span data-ttu-id="20a20-152">Quando uma função associada de módulo fizer parte de uma API pública, ele deve usar camelCase:</span><span class="sxs-lookup"><span data-stu-id="20a20-152">When a module-bound function is part of a public API, it should use camelCase:</span></span>

```fsharp
module MyAPI =
    let publicFunctionOne param1 param2 param2 = ...

    let publicFunctionTwo param1 param2 param3 = ...
```

### <a name="use-camelcase-for-internal-and-private-module-bound-values-and-functions"></a><span data-ttu-id="20a20-153">Use camelCase para funções e os valores de limite de módulo internos e privados</span><span class="sxs-lookup"><span data-stu-id="20a20-153">Use camelCase for internal and private module-bound values and functions</span></span>

<span data-ttu-id="20a20-154">Use camelCase para valores de associação de módulo privados, incluindo o seguinte:</span><span class="sxs-lookup"><span data-stu-id="20a20-154">Use camelCase for private module-bound values, including the following:</span></span>

* <span data-ttu-id="20a20-155">Funções ad hoc em scripts</span><span class="sxs-lookup"><span data-stu-id="20a20-155">Ad hoc functions in scripts</span></span>

* <span data-ttu-id="20a20-156">Valores que compõem a implementação interna de um módulo ou tipo</span><span class="sxs-lookup"><span data-stu-id="20a20-156">Values making up the internal implementation of a module or type</span></span>

```fsharp
let emailMyBossTheLatestResults =
    ...
```

### <a name="use-camelcase-for-parameters"></a><span data-ttu-id="20a20-157">Use camelCase para parâmetros</span><span class="sxs-lookup"><span data-stu-id="20a20-157">Use camelCase for parameters</span></span>

<span data-ttu-id="20a20-158">Todos os parâmetros devem usar camelCase de acordo com as convenções de nomenclatura do .NET.</span><span class="sxs-lookup"><span data-stu-id="20a20-158">All parameters should use camelCase in accordance with .NET naming conventions.</span></span>

```fsharp
module MyModule =
    let myFunction paramOne paramTwo = ...

type MyClass() =
    member this.MyMethod(paramOne, paramTwo) = ...
```

### <a name="use-pascalcase-for-modules"></a><span data-ttu-id="20a20-159">Usar PascalCase para módulos</span><span class="sxs-lookup"><span data-stu-id="20a20-159">Use PascalCase for modules</span></span>

<span data-ttu-id="20a20-160">Todos os módulos (nível superior, internos, privados, aninhados) devem usar PascalCase.</span><span class="sxs-lookup"><span data-stu-id="20a20-160">All modules (top-level, internal, private, nested) should use PascalCase.</span></span>

```fsharp
module MyTopLevelModule

module Helpers =
    module private SuperHelpers =
        ...

    ...
```

### <a name="use-pascalcase-for-type-declarations-members-and-labels"></a><span data-ttu-id="20a20-161">Usar PascalCase para declarações de tipo, membros e rótulos</span><span class="sxs-lookup"><span data-stu-id="20a20-161">Use PascalCase for type declarations, members, and labels</span></span>

<span data-ttu-id="20a20-162">Classes, interfaces, estruturas, enumerações, delegados, registros e uniões discriminadas devem ser nomeadas com PascalCase.</span><span class="sxs-lookup"><span data-stu-id="20a20-162">Classes, interfaces, structs, enumerations, delegates, records, and discriminated unions should all be named with PascalCase.</span></span> <span data-ttu-id="20a20-163">Os membros dentro de tipos e rótulos para registros e uniões discriminadas também devem usar PascalCase.</span><span class="sxs-lookup"><span data-stu-id="20a20-163">Members within types and labels for records and discriminated unions should also use PascalCase.</span></span>

```fsharp
type IMyInterface =
    abstract Something: int

type MyClass() =
    member this.MyMethod(x, y) = x + y

type MyRecord = { IntVal: int; StringVal: string }

type SchoolPerson =
    | Professor
    | Student
    | Advisor
    | Administrator
```

### <a name="use-pascalcase-for-constructs-intrinsic-to-net"></a><span data-ttu-id="20a20-164">Usar PascalCase para construções intrínsecas para o .NET</span><span class="sxs-lookup"><span data-stu-id="20a20-164">Use PascalCase for constructs intrinsic to .NET</span></span>

<span data-ttu-id="20a20-165">Namespaces, exceções, eventos e projeto /`.dll` nomes também devem usar PascalCase.</span><span class="sxs-lookup"><span data-stu-id="20a20-165">Namespaces, exceptions, events, and project/`.dll` names should also use PascalCase.</span></span> <span data-ttu-id="20a20-166">Não apenas isso faz o consumo de outras linguagens .NET mais naturais para os consumidores, também é consistente com as convenções de nomenclatura do .NET que você provavelmente encontrará.</span><span class="sxs-lookup"><span data-stu-id="20a20-166">Not only does this make consumption from other .NET languages feel more natural to consumers, it's also consistent with .NET naming conventions that you are likely to encounter.</span></span>

### <a name="avoid-underscores-in-names"></a><span data-ttu-id="20a20-167">Evite sublinhados em nomes</span><span class="sxs-lookup"><span data-stu-id="20a20-167">Avoid underscores in names</span></span>

<span data-ttu-id="20a20-168">Historicamente, alguns F# bibliotecas usou sublinhados em nomes.</span><span class="sxs-lookup"><span data-stu-id="20a20-168">Historically, some F# libraries have used underscores in names.</span></span> <span data-ttu-id="20a20-169">No entanto, isso não é mais amplamente é aceito, em parte porque ele estiver em conflito com as convenções de nomenclatura do .NET.</span><span class="sxs-lookup"><span data-stu-id="20a20-169">However, this is no longer widely accepted, partly because it clashes with .NET naming conventions.</span></span> <span data-ttu-id="20a20-170">Dito isso, alguns F# os programadores usam sublinhados intensamente, em parte a razões históricas e tolerância e respeito é importante.</span><span class="sxs-lookup"><span data-stu-id="20a20-170">That said, some F# programmers use underscores heavily, partly for historical reasons, and tolerance and respect is important.</span></span> <span data-ttu-id="20a20-171">No entanto, lembre-se de que o estilo é geralmente disliked por outras pessoas que têm uma opção sobre se deve usá-lo.</span><span class="sxs-lookup"><span data-stu-id="20a20-171">However, be aware that the style is often disliked by others who have a choice about whether to use it.</span></span>

<span data-ttu-id="20a20-172">Algumas exceções inclui interoperar com componentes nativos, onde os sublinhados são muito comuns.</span><span class="sxs-lookup"><span data-stu-id="20a20-172">Some exceptions includes interoperating with native components, where underscores are very common.</span></span>

### <a name="use-standard-f-operators"></a><span data-ttu-id="20a20-173">Padrão de uso F# operadores</span><span class="sxs-lookup"><span data-stu-id="20a20-173">Use standard F# operators</span></span>

<span data-ttu-id="20a20-174">Os operadores a seguir são definidos no F# biblioteca padrão e deve ser usado em vez de definir equivalentes.</span><span class="sxs-lookup"><span data-stu-id="20a20-174">The following operators are defined in the F# standard library and should be used instead of defining equivalents.</span></span> <span data-ttu-id="20a20-175">Usar esses operadores é recomendável como ele tende a tornar o código mais legível e expressões idiomáticas.</span><span class="sxs-lookup"><span data-stu-id="20a20-175">Using these operators is recommended as it tends to make code more readable and idiomatic.</span></span> <span data-ttu-id="20a20-176">Os desenvolvedores com experiência em OCaml ou outra linguagem de programação funcional talvez esteja acostumados a idiomas diferentes.</span><span class="sxs-lookup"><span data-stu-id="20a20-176">Developers with a background in OCaml or other functional programming language may be accustomed to different idioms.</span></span> <span data-ttu-id="20a20-177">A lista a seguir resume o recomendado F# operadores.</span><span class="sxs-lookup"><span data-stu-id="20a20-177">The following list summarizes the recommended F# operators.</span></span>

```fsharp
x |> f // Forward pipeline
f >> g // Forward composition
x |> ignore // Discard away a value
x + y // Overloaded addition (including string concatenation)
x - y // Overloaded subtraction
x * y // Overloaded multiplication
x / y // Overloaded division
x % y // Overloaded modulus
x && y // Lazy/short-cut "and"
x || y // Lazy/short-cut "or"
x <<< y // Bitwise left shift
x >>> y // Bitwise right shift
x ||| y // Bitwise or, also for working with “flags” enumeration
x &&& y // Bitwise and, also for working with “flags” enumeration
x ^^^ y // Bitwise xor, also for working with “flags” enumeration
```

### <a name="use-prefix-syntax-for-generics-foot-in-preference-to-postfix-syntax-t-foo"></a><span data-ttu-id="20a20-178">Use a sintaxe de prefixo para genéricos (`Foo<T>`) em preferência a sintaxe de sufixo (`T Foo`)</span><span class="sxs-lookup"><span data-stu-id="20a20-178">Use prefix syntax for generics (`Foo<T>`) in preference to postfix syntax (`T Foo`)</span></span>

<span data-ttu-id="20a20-179">F#herda de ambos os o estilo de ML sufixo de nomeação de tipos genéricos (por exemplo, `int list`), bem como o prefixo de estilo do .NET (por exemplo, `list<int>`).</span><span class="sxs-lookup"><span data-stu-id="20a20-179">F# inherits both the postfix ML style of naming generic types (for example, `int list`) as well as the prefix .NET style (for example, `list<int>`).</span></span> <span data-ttu-id="20a20-180">Preferir o estilo de .NET, exceto para quatro tipos específicos:</span><span class="sxs-lookup"><span data-stu-id="20a20-180">Prefer the .NET style, except for four specific types:</span></span>

1. <span data-ttu-id="20a20-181">Para F# listas, use o formulário de sufixo: `int list` vez `list<int>`.</span><span class="sxs-lookup"><span data-stu-id="20a20-181">For F# Lists, use the postfix form: `int list` rather than `list<int>`.</span></span>
2. <span data-ttu-id="20a20-182">Para F# opções, use o formulário de sufixo: `int option` vez `option<int>`.</span><span class="sxs-lookup"><span data-stu-id="20a20-182">For F# Options, use the postfix form: `int option` rather than `option<int>`.</span></span>
3. <span data-ttu-id="20a20-183">Para F# matrizes, use o nome sintático `int[]` vez `int array` ou `array<int>`.</span><span class="sxs-lookup"><span data-stu-id="20a20-183">For F# arrays, use the syntactic name `int[]` rather than `int array` or `array<int>`.</span></span>
4. <span data-ttu-id="20a20-184">Para as células de referência, use `int ref` em vez de `ref<int>` ou `Ref<int>`.</span><span class="sxs-lookup"><span data-stu-id="20a20-184">For Reference Cells, use `int ref` rather than `ref<int>` or `Ref<int>`.</span></span>

<span data-ttu-id="20a20-185">Para todos os outros tipos, use o formulário de prefixo.</span><span class="sxs-lookup"><span data-stu-id="20a20-185">For all other types, use the prefix form.</span></span>

## <a name="formatting-tuples"></a><span data-ttu-id="20a20-186">As tuplas de formatação</span><span class="sxs-lookup"><span data-stu-id="20a20-186">Formatting tuples</span></span>

<span data-ttu-id="20a20-187">Uma instanciação de tupla deve estar entre parênteses e vírgulas dentro de delimitadores devem ser seguidas por um único espaço, por exemplo: `(1, 2)`, `(x, y, z)`.</span><span class="sxs-lookup"><span data-stu-id="20a20-187">A tuple instantiation should be parenthesized, and the delimiting commas within should be followed by a single space, for example: `(1, 2)`, `(x, y, z)`.</span></span>

<span data-ttu-id="20a20-188">Normalmente, ela é aceita para omitir os parênteses na correspondência de padrão de tuplas:</span><span class="sxs-lookup"><span data-stu-id="20a20-188">It is commonly accepted to omit parentheses in pattern matching of tuples:</span></span>

```fsharp
let (x, y) = z // Destructuring
let x, y = z // OK

// OK
match x, y with
| 1, _ -> 0
| x, 1 -> 0
| x, y -> 1
```

<span data-ttu-id="20a20-189">Ele também geralmente é aceito para omitir os parênteses se a tupla é o valor de retorno de uma função:</span><span class="sxs-lookup"><span data-stu-id="20a20-189">It is also commonly accepted to omit parentheses if the tuple is the return value of a function:</span></span>

```fsharp
// OK
let update model msg =
    match msg with
    | 1 -> model + 1, []
    | _ -> model, [ msg ]
```
<span data-ttu-id="20a20-190">Em resumo, prefira instanciações de tupla entre parênteses, mas ao usar tuplas para correspondência de padrão ou um valor de retorno, ele é considerado bom evitar parênteses.</span><span class="sxs-lookup"><span data-stu-id="20a20-190">In summary, prefer parenthesized tuple instantiations, but when using tuples for pattern matching or a return value, it is considered fine to avoid parentheses.</span></span>

## <a name="formatting-discriminated-union-declarations"></a><span data-ttu-id="20a20-191">Formatação discriminada declarações de união</span><span class="sxs-lookup"><span data-stu-id="20a20-191">Formatting discriminated union declarations</span></span>

<span data-ttu-id="20a20-192">Recuar `|` na definição de tipo por 4 espaços:</span><span class="sxs-lookup"><span data-stu-id="20a20-192">Indent `|` in type definition by 4 spaces:</span></span>

```fsharp
// OK
type Volume =
    | Liter of float
    | FluidOunce of float
    | ImperialPint of float

// Not OK
type Volume =
| Liter of float
| USPint of float
| ImperialPint of float
```

## <a name="formatting-discriminated-unions"></a><span data-ttu-id="20a20-193">Formatação de uniões discriminadas</span><span class="sxs-lookup"><span data-stu-id="20a20-193">Formatting discriminated unions</span></span>

<span data-ttu-id="20a20-194">Uniões discriminadas instanciado divididas em várias linhas deve fornecer os dados contidos um novo escopo com recuo:</span><span class="sxs-lookup"><span data-stu-id="20a20-194">Instantiated Discriminated Unions that split across multiple lines should give contained data a new scope with indentation:</span></span>

```fsharp
let tree1 =
    BinaryNode
        (BinaryNode(BinaryValue 1, BinaryValue 2),
         BinaryNode(BinaryValue 3, BinaryValue 4))
```

<span data-ttu-id="20a20-195">O parêntese de fechamento também pode ser em uma nova linha:</span><span class="sxs-lookup"><span data-stu-id="20a20-195">The closing parenthesis can also be on a new line:</span></span>

```fsharp
let tree1 =
    BinaryNode(
        BinaryNode(BinaryValue 1, BinaryValue 2),
        BinaryNode(BinaryValue 3, BinaryValue 4)
    )
```

## <a name="formatting-record-declarations"></a><span data-ttu-id="20a20-196">Declarações de registro de formatação</span><span class="sxs-lookup"><span data-stu-id="20a20-196">Formatting record declarations</span></span>

<span data-ttu-id="20a20-197">Recuar `{` no tipo de definição por 4 espaços e iniciar a lista de campos na mesma linha:</span><span class="sxs-lookup"><span data-stu-id="20a20-197">Indent `{` in type definition by 4 spaces and start the field list on the same line:</span></span>

```fsharp
// OK
type PostalAddress =
    { Address: string
      City: string
      Zip: string }
    member x.ZipAndCity = sprintf "%s %s" x.Zip x.City

// Not OK
type PostalAddress =
  { Address: string
    City: string
    Zip: string }
    member x.ZipAndCity = sprintf "%s %s" x.Zip x.City
    
// Unusual in F#
type PostalAddress =
    { 
        Address: string
        City: string
        Zip: string
    }
```

<span data-ttu-id="20a20-198">Colocar o token de abertura em uma nova linha e o token de fechamento em uma nova linha é preferível se você está declarando a implementações de interface ou membros no registro:</span><span class="sxs-lookup"><span data-stu-id="20a20-198">Placing the opening token on a new line and the closing token on a new line is preferable if you are declaring interface implementations or members on the record:</span></span>

```fsharp
// Declaring additional members on PostalAddress
type PostalAddress =
    { 
        Address: string
        City: string
        Zip: string
    } with
    member x.ZipAndCity = sprintf "%s %s" x.Zip x.City
    
type MyRecord =
    {
        SomeField: int
    }
    interface IMyInterface
```

## <a name="formatting-records"></a><span data-ttu-id="20a20-199">Formatação de registros</span><span class="sxs-lookup"><span data-stu-id="20a20-199">Formatting records</span></span>

<span data-ttu-id="20a20-200">Registros curtos podem ser escritos em uma linha:</span><span class="sxs-lookup"><span data-stu-id="20a20-200">Short records can be written in one line:</span></span>

```fsharp
let point = { X = 1.0; Y = 0.0 }
```

<span data-ttu-id="20a20-201">Os registros que são mais longas devem usar novas linhas para rótulos:</span><span class="sxs-lookup"><span data-stu-id="20a20-201">Records that are longer should use new lines for labels:</span></span>

```fsharp
let rainbow =
    { Boss = "Jeffrey"
      Lackeys = ["Zippy"; "George"; "Bungle"] }
```

<span data-ttu-id="20a20-202">Colocando a abertura guias do token em uma nova linha, o conteúdo em um escopo, e o token de fechamento em uma nova linha é preferível se você for:</span><span class="sxs-lookup"><span data-stu-id="20a20-202">Placing the opening token on a new line, the contents tabbed over one scope, and the closing token on a new line is preferable if you are:</span></span>

* <span data-ttu-id="20a20-203">Movimentação de registros no código com escopos diferentes de recuo</span><span class="sxs-lookup"><span data-stu-id="20a20-203">Moving records around in code with different indentation scopes</span></span>
* <span data-ttu-id="20a20-204">Direcionando-os em uma função</span><span class="sxs-lookup"><span data-stu-id="20a20-204">Piping them into a function</span></span>

```fsharp
let rainbow =
    {
        Boss1 = "Jeffrey"
        Boss2 = "Jeffrey"
        Boss3 = "Jeffrey"
        Boss4 = "Jeffrey"
        Boss5 = "Jeffrey"
        Boss6 = "Jeffrey"
        Boss7 = "Jeffrey"
        Boss8 = "Jeffrey"
        Lackeys = ["Zippy"; "George"; "Bungle"]
    }
    
type MyRecord =
    {
        SomeField: int
    }
    interface IMyInterface

let foo a =
    a
    |> Option.map (fun x ->
        {
            MyField = x
        })
```

<span data-ttu-id="20a20-205">As mesmas regras se aplicam para elementos list e array.</span><span class="sxs-lookup"><span data-stu-id="20a20-205">The same rules apply for list and array elements.</span></span>

## <a name="formatting-copy-and-update-record-expressions"></a><span data-ttu-id="20a20-206">Expressões de registro de atualização e cópia de formatação</span><span class="sxs-lookup"><span data-stu-id="20a20-206">Formatting copy-and-update record expressions</span></span>

<span data-ttu-id="20a20-207">Uma expressão de registro de atualização e cópia ainda é um registro, diretrizes semelhantes se aplicam.</span><span class="sxs-lookup"><span data-stu-id="20a20-207">A copy-and-update record expression is still a record, so similar guidelines apply.</span></span>

<span data-ttu-id="20a20-208">Expressões curtas podem caber em uma única linha:</span><span class="sxs-lookup"><span data-stu-id="20a20-208">Short expressions can fit on one line:</span></span>

```fsharp
let point2 = { point with X = 1; Y = 2 }
```

<span data-ttu-id="20a20-209">Expressões mais longas devem usar as novas linhas:</span><span class="sxs-lookup"><span data-stu-id="20a20-209">Longer expressions should use new lines:</span></span>

```fsharp
let rainbow2 =
    { rainbow with
        Boss = "Jeffrey"
        Lackeys = ["Zippy"; "George"; "Bungle"] }
```

<span data-ttu-id="20a20-210">E, como com as diretrizes de registro, você talvez queira dedicar linhas separadas para as chaves e recuar um escopo para a direita com a expressão.</span><span class="sxs-lookup"><span data-stu-id="20a20-210">And as with the record guidance, you may want to dedicate separate lines for the braces and indent one scope to the right with the expression.</span></span> <span data-ttu-id="20a20-211">Observe que em alguns casos especiais, como quebra automática de um valor com um recurso opcional sem parênteses, talvez você precise manter uma chave em uma única linha:</span><span class="sxs-lookup"><span data-stu-id="20a20-211">Note that in some special cases, such as wrapping a value with an optional without parentheses, you may need to keep a brace on one line:</span></span>

```fsharp    
type S = { F1: int; F2: string }
type State = { F:  S option }

let state = { F = Some { F1 = 1; F2 = "Hello" } }
let newState = 
    {
        state with
            F = Some {
                    F1 = 0
                    F2 = ""
                }
    }
```

## <a name="formatting-lists-and-arrays"></a><span data-ttu-id="20a20-212">Formatando listas e matrizes</span><span class="sxs-lookup"><span data-stu-id="20a20-212">Formatting lists and arrays</span></span>

<span data-ttu-id="20a20-213">Gravar `x :: l` com espaços em torno de `::` operador (`::` é um operador de infixo, portanto, cercado por espaços).</span><span class="sxs-lookup"><span data-stu-id="20a20-213">Write `x :: l` with spaces around the `::` operator (`::` is an infix operator, hence surrounded by spaces).</span></span>

<span data-ttu-id="20a20-214">Lista e matrizes declaradas em uma única linha devem ter um espaço após o colchete de abertura e antes do colchete de fechamento:</span><span class="sxs-lookup"><span data-stu-id="20a20-214">List and arrays declared on a single line should have a space after the opening bracket and before the closing bracket:</span></span>

```fsharp
let xs = [ 1; 2; 3 ]
let ys = [| 1; 2; 3; |]
```

<span data-ttu-id="20a20-215">Sempre use pelo menos um espaço entre os dois operadores semelhante de chave distintos.</span><span class="sxs-lookup"><span data-stu-id="20a20-215">Always use at least one space between two distinct brace-like operators.</span></span> <span data-ttu-id="20a20-216">Por exemplo, deixar um espaço entre um `[` e um `{`.</span><span class="sxs-lookup"><span data-stu-id="20a20-216">For example, leave a space between a `[` and a `{`.</span></span>

```fsharp
// OK
[ { IngredientName = "Green beans"; Quantity = 250 }
  { IngredientName = "Pine nuts"; Quantity = 250 }
  { IngredientName = "Feta cheese"; Quantity = 250 }
  { IngredientName = "Olive oil"; Quantity = 10 }
  { IngredientName = "Lemon"; Quantity = 1 } ]

// Not OK
[{ IngredientName = "Green beans"; Quantity = 250 }
 { IngredientName = "Pine nuts"; Quantity = 250 }
 { IngredientName = "Feta cheese"; Quantity = 250 }
 { IngredientName = "Olive oil"; Quantity = 10 }
 { IngredientName = "Lemon"; Quantity = 1 }]
```

<span data-ttu-id="20a20-217">A mesma diretriz se aplica para listas ou matrizes de tuplas.</span><span class="sxs-lookup"><span data-stu-id="20a20-217">The same guideline applies for lists or arrays of tuples.</span></span>

<span data-ttu-id="20a20-218">Listas e matrizes que são dividem em várias linhas seguem uma regra semelhante como registros:</span><span class="sxs-lookup"><span data-stu-id="20a20-218">Lists and arrays that split across multiple lines follow a similar rule as records do:</span></span>

```fsharp
let pascalsTriangle =
    [|
        [| 1 |]
        [| 1; 1 |]
        [| 1; 2; 1 |]
        [| 1; 3; 3; 1 |]
        [| 1; 4; 6; 4; 1 |]
        [| 1; 5; 10; 10; 5; 1 |]
        [| 1; 6; 15; 20; 15; 6; 1 |]
        [| 1; 7; 21; 35; 35; 21; 7; 1 |]
        [| 1; 8; 28; 56; 70; 56; 28; 8; 1 |]
    |]
```

<span data-ttu-id="20a20-219">E assim como acontece com registros, declarando os colchetes de abertura e fechamento em sua própria linha facilitará mudança de um código ao redor e tubulação em funções.</span><span class="sxs-lookup"><span data-stu-id="20a20-219">And as with records, declaring the opening and closing brackets on their own line will make moving code around and piping into functions easier.</span></span>

## <a name="formatting-if-expressions"></a><span data-ttu-id="20a20-220">Formatação se expressões</span><span class="sxs-lookup"><span data-stu-id="20a20-220">Formatting if expressions</span></span>

<span data-ttu-id="20a20-221">Recuo de condicionais depende dos tamanhos das expressões que compõem-los.</span><span class="sxs-lookup"><span data-stu-id="20a20-221">Indentation of conditionals depends on the sizes of the expressions that make them up.</span></span> <span data-ttu-id="20a20-222">Se `cond`, `e1` e `e2` são curto, simplesmente gravá-los em uma única linha:</span><span class="sxs-lookup"><span data-stu-id="20a20-222">If `cond`, `e1` and `e2` are short, simply write them on one line:</span></span>

```fsharp
if cond then e1 else e2
```

<span data-ttu-id="20a20-223">Se qualquer um dos `cond`, `e1` ou `e2` são mais tempo, mas não de várias linhas:</span><span class="sxs-lookup"><span data-stu-id="20a20-223">If either `cond`, `e1` or `e2` are longer, but not multi-line:</span></span>

```fsharp
if cond
then e1
else e2
```

<span data-ttu-id="20a20-224">Se qualquer uma das expressões são várias linhas:</span><span class="sxs-lookup"><span data-stu-id="20a20-224">If any of the expressions are multi-line:</span></span>

```fsharp
if cond then
    e1
else
    e2
```

<span data-ttu-id="20a20-225">Várias condições com `elif` e `else` são recuadas no mesmo escopo que o `if`:</span><span class="sxs-lookup"><span data-stu-id="20a20-225">Multiple conditionals with `elif` and `else` are indented at the same scope as the `if`:</span></span>

```fsharp
if cond1 then e1
elif cond2 then e2
elif cond3 then e3
else e4
```

### <a name="pattern-matching-constructs"></a><span data-ttu-id="20a20-226">Construções de correspondência de padrão</span><span class="sxs-lookup"><span data-stu-id="20a20-226">Pattern matching constructs</span></span>

<span data-ttu-id="20a20-227">Use um `|` para cada cláusula de uma correspondência com nenhum recuo.</span><span class="sxs-lookup"><span data-stu-id="20a20-227">Use a `|` for each clause of a match with no indentation.</span></span> <span data-ttu-id="20a20-228">Se a expressão for curta, você pode considerar usando uma única linha, se cada subexpressão também é simple.</span><span class="sxs-lookup"><span data-stu-id="20a20-228">If the expression is short, you can consider using a single line if each subexpression is also simple.</span></span>

```fsharp
// OK
match l with
| { him = x; her = "Posh" } :: tail -> x
| _ :: tail -> findDavid tail
| [] -> failwith "Couldn't find David"

// Not OK
match l with
    | { him = x; her = "Posh" } :: tail -> x
    | _ :: tail -> findDavid tail
    | [] -> failwith "Couldn't find David"
```

<span data-ttu-id="20a20-229">Se a expressão à direita da seta para a correspondência for muito grande, mova-o para a seguinte linha, recuado em uma etapa do `match` / `|`.</span><span class="sxs-lookup"><span data-stu-id="20a20-229">If the expression on the right of the pattern matching arrow is too large, move it to the following line, indented one step from the `match`/`|`.</span></span>

```fsharp
match lam with
| Var v -> 1
| Abs(x, body) ->
    1 + sizeLambda body
| App(lam1, lam2) ->
    sizeLambda lam1 + sizeLambda lam2

```

<span data-ttu-id="20a20-230">Correspondência de padrões de funções anônimas, começando pelo `function`, não geralmente deve Recuar muito longe.</span><span class="sxs-lookup"><span data-stu-id="20a20-230">Pattern matching of anonymous functions, starting by `function`, should generally not indent too far.</span></span> <span data-ttu-id="20a20-231">Por exemplo, é bom recuar um escopo da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="20a20-231">For example, indenting one scope as follows is fine:</span></span>

```fsharp
lambdaList
|> List.map (function
    | Abs(x, body) -> 1 + sizeLambda 0 body
    | App(lam1, lam2) -> sizeLambda (sizeLambda 0 lam1) lam2
    | Var v -> 1)
```

<span data-ttu-id="20a20-232">Correspondência de padrão de funções definidas pelo `let` ou `let rec` deve ser recuados 4 espaços após a inicialização do `let`, mesmo se `function` palavra-chave é usada:</span><span class="sxs-lookup"><span data-stu-id="20a20-232">Pattern matching in functions defined by `let` or `let rec` should be indented 4 spaces after starting of `let`, even if `function` keyword is used:</span></span>

```fsharp
let rec sizeLambda acc = function
    | Abs(x, body) -> sizeLambda (succ acc) body
    | App(lam1, lam2) -> sizeLambda (sizeLambda acc lam1) lam2
    | Var v -> succ acc
```

<span data-ttu-id="20a20-233">Não recomendamos alinhando setas.</span><span class="sxs-lookup"><span data-stu-id="20a20-233">We do not recommend aligning arrows.</span></span>

## <a name="formatting-trywith-expressions"></a><span data-ttu-id="20a20-234">Formatação de try / com expressões</span><span class="sxs-lookup"><span data-stu-id="20a20-234">Formatting try/with expressions</span></span>

<span data-ttu-id="20a20-235">Correspondência de padrão em que o tipo de exceção deve ser recuado no mesmo nível como `with`.</span><span class="sxs-lookup"><span data-stu-id="20a20-235">Pattern matching on the exception type should be indented at the same level as `with`.</span></span>

```fsharp
try
    if System.DateTime.Now.Second % 3 = 0 then
        raise (new System.Exception())
    else
        raise (new System.ApplicationException())
with
| :? System.ApplicationException ->
    printfn "A second that was not a multiple of 3"
| _ ->
    printfn "A second that was a multiple of 3"
```

## <a name="formatting-function-parameter-application"></a><span data-ttu-id="20a20-236">Aplicativo de parâmetro de função de formatação</span><span class="sxs-lookup"><span data-stu-id="20a20-236">Formatting function parameter application</span></span>

<span data-ttu-id="20a20-237">Em geral, a maioria dos aplicativos de parâmetro de função é feito na mesma linha.</span><span class="sxs-lookup"><span data-stu-id="20a20-237">In general, most function parameter application is done on the same line.</span></span>

<span data-ttu-id="20a20-238">Se você quiser aplicar os parâmetros para uma função em uma nova linha, recuo-los por um escopo.</span><span class="sxs-lookup"><span data-stu-id="20a20-238">If you wish to apply parameters to a function on a new line, indent them by one scope.</span></span>

```fsharp
// OK
sprintf "\t%s - %i\n\r"
     x.IngredientName x.Quantity

// OK
sprintf
     "\t%s - %i\n\r"
     x.IngredientName x.Quantity

// OK
let printVolumes x =
    printf "Volume in liters = %f, in us pints = %f, in imperial = %f"
        (convertVolumeToLiter x)
        (convertVolumeUSPint x)
        (convertVolumeImperialPint x)
```

<span data-ttu-id="20a20-239">As mesmas diretrizes se aplicam para as expressões lambda como argumentos de função.</span><span class="sxs-lookup"><span data-stu-id="20a20-239">The same guidelines apply for lambda expressions as function arguments.</span></span> <span data-ttu-id="20a20-240">Se o corpo de uma expressão lambda, o corpo pode ter outra linha, recuada de acordo com um escopo</span><span class="sxs-lookup"><span data-stu-id="20a20-240">If the body of a lambda expression, the body can have another line, indented by one scope</span></span>

```fsharp
let printListWithOffset a list1 =
    List.iter
        (fun elem -> printfn "%d" (a + elem))
        list1

// OK if lambda body is long enough
let printListWithOffset a list1 =
    List.iter
        (fun elem ->
            printfn "%d" (a + elem))
        list1
```

<span data-ttu-id="20a20-241">No entanto, se o corpo de uma expressão lambda é a mais de uma linha, considere fatorá-lo em uma função separada em vez de ter uma construção de várias linha aplicada como um único argumento para uma função.</span><span class="sxs-lookup"><span data-stu-id="20a20-241">However, if the body of a lambda expression is more than one line, consider factoring it out into a separate function rather than have a multi-line construct applied as a single argument to a function.</span></span>

### <a name="formatting-infix-operators"></a><span data-ttu-id="20a20-242">Operadores infixos de formatação</span><span class="sxs-lookup"><span data-stu-id="20a20-242">Formatting infix operators</span></span>

<span data-ttu-id="20a20-243">Operadores separados por espaços.</span><span class="sxs-lookup"><span data-stu-id="20a20-243">Separate operators by spaces.</span></span> <span data-ttu-id="20a20-244">Óbvias exceções a essa regra são as `!` e `.` operadores.</span><span class="sxs-lookup"><span data-stu-id="20a20-244">Obvious exceptions to this rule are the `!` and `.` operators.</span></span>

<span data-ttu-id="20a20-245">Expressões de infixo são Okey para o antecipação da linha na mesma coluna:</span><span class="sxs-lookup"><span data-stu-id="20a20-245">Infix expressions are OK to lineup on same column:</span></span>

```fsharp
acc +
(sprintf "\t%s - %i\n\r"
     x.IngredientName x.Quantity)

let function1 arg1 arg2 arg3 arg4 =
    arg1 + arg2 +
    arg3 + arg4
```

### <a name="formatting-pipeline-operators"></a><span data-ttu-id="20a20-246">Formatação de operadores de pipeline</span><span class="sxs-lookup"><span data-stu-id="20a20-246">Formatting pipeline operators</span></span>

<span data-ttu-id="20a20-247">Pipeline `|>` operadores devem ficar sob eles operam em expressões.</span><span class="sxs-lookup"><span data-stu-id="20a20-247">Pipeline `|>` operators should go underneath the expressions they operate on.</span></span>

```fsharp
// Preferred approach
let methods2 =
    System.AppDomain.CurrentDomain.GetAssemblies()
    |> List.ofArray
    |> List.map (fun assm -> assm.GetTypes())
    |> Array.concat
    |> List.ofArray
    |> List.map (fun t -> t.GetMethods())
    |> Array.concat

// Not OK
let methods2 = System.AppDomain.CurrentDomain.GetAssemblies()
            |> List.ofArray
            |> List.map (fun assm -> assm.GetTypes())
            |> Array.concat
            |> List.ofArray
            |> List.map (fun t -> t.GetMethods())
            |> Array.concat
```

### <a name="formatting-modules"></a><span data-ttu-id="20a20-248">Formatação de módulos</span><span class="sxs-lookup"><span data-stu-id="20a20-248">Formatting modules</span></span>

<span data-ttu-id="20a20-249">Em um módulo local deve ser recuado em relação ao módulo, mas o código em um módulo de nível superior não deve ser recuado.</span><span class="sxs-lookup"><span data-stu-id="20a20-249">Code in a local module must be indented relative to the module, but code in a top-level module should not be indented.</span></span> <span data-ttu-id="20a20-250">Não tem elementos do Namespace a ser recuado.</span><span class="sxs-lookup"><span data-stu-id="20a20-250">Namespace elements do not have to be indented.</span></span>

```fsharp
// A is a top-level module.
module A

let function1 a b = a - b * b
```

```fsharp
// A1 and A2 are local modules.
module A1 =
    let function1 a b = a*a + b*b

module A2 =
    let function2 a b = a*a - b*b
```

### <a name="formatting-object-expressions-and-interfaces"></a><span data-ttu-id="20a20-251">Formatação de expressões de objeto e interfaces</span><span class="sxs-lookup"><span data-stu-id="20a20-251">Formatting object expressions and interfaces</span></span>

<span data-ttu-id="20a20-252">Expressões de objeto e as interfaces devem ser alinhados da mesma forma com `member` sendo recuado após 4 espaços.</span><span class="sxs-lookup"><span data-stu-id="20a20-252">Object expressions and interfaces should be aligned in the same way with `member` being indented after 4 spaces.</span></span>

```fsharp
let comparer =
    { new IComparer<string> with
          member x.Compare(s1, s2) =
              let rev (s: String) =
                  new String (Array.rev (s.ToCharArray()))
              let reversed = rev s1
              reversed.CompareTo (rev s2) }
```

### <a name="formatting-white-space-in-expressions"></a><span data-ttu-id="20a20-253">Formatação de espaço em branco em expressões</span><span class="sxs-lookup"><span data-stu-id="20a20-253">Formatting white space in expressions</span></span>

<span data-ttu-id="20a20-254">Evite espaço em branco estranhos na F# expressões.</span><span class="sxs-lookup"><span data-stu-id="20a20-254">Avoid extraneous white space in F# expressions.</span></span>

```fsharp
// OK
spam (ham.[1])

// Not OK
spam ( ham.[ 1 ] )
```

<span data-ttu-id="20a20-255">Argumentos nomeados também não devem ter espaço em torno de `=`:</span><span class="sxs-lookup"><span data-stu-id="20a20-255">Named arguments should also not have space surrounding the `=`:</span></span>

```fsharp
// OK
let makeStreamReader x = new System.IO.StreamReader(path=x)

// Not OK
let makeStreamReader x = new System.IO.StreamReader(path = x)
```

## <a name="formatting-attributes"></a><span data-ttu-id="20a20-256">Atributos de formatação</span><span class="sxs-lookup"><span data-stu-id="20a20-256">Formatting attributes</span></span>

<span data-ttu-id="20a20-257">[Atributos](../language-reference/attributes.md) são colocados acima uma construção:</span><span class="sxs-lookup"><span data-stu-id="20a20-257">[Attributes](../language-reference/attributes.md) are placed above a construct:</span></span>

```fsharp
[<SomeAttribute>]
type MyClass() = ...

[<RequireQualifiedAccess>]
module M =
    let f x = x

[<Struct>]
type MyRecord =
    { Label1: int
      Label2: string }
```

### <a name="formatting-attributes-on-parameters"></a><span data-ttu-id="20a20-258">Atributos em parâmetros de formatação</span><span class="sxs-lookup"><span data-stu-id="20a20-258">Formatting attributes on parameters</span></span>

<span data-ttu-id="20a20-259">Atributos também podem ser locais nos parâmetros.</span><span class="sxs-lookup"><span data-stu-id="20a20-259">Attributes can also be places on parameters.</span></span> <span data-ttu-id="20a20-260">Nesse caso, coloque-os na mesma linha como o parâmetro e antes do nome:</span><span class="sxs-lookup"><span data-stu-id="20a20-260">In this case, place then on the same line as the parameter and before the name:</span></span>

```fsharp
// Defines a class that takes an optional value as input defaulting to false.
type C() =
    member __.M([<Optional; DefaultParameterValue(false)>] doSomething: bool)
```

### <a name="formatting-multiple-attributes"></a><span data-ttu-id="20a20-261">Vários atributos de formatação</span><span class="sxs-lookup"><span data-stu-id="20a20-261">Formatting multiple attributes</span></span>

<span data-ttu-id="20a20-262">Quando vários atributos são aplicados a uma construção que não é um parâmetro, eles devem ser colocados, de modo que há um atributo por linha:</span><span class="sxs-lookup"><span data-stu-id="20a20-262">When multiple attributes are applied to a construct that is not a parameter, they should be placed such that there is one attribute per line:</span></span>

```fsharp
[<Struct>]
[<IsByRefLike>]
type MyRecord =
    { Label1: int
      Label2: string }
```

<span data-ttu-id="20a20-263">Quando aplicado a um parâmetro, elas devem estar na mesma linha e separados por um `;` separador.</span><span class="sxs-lookup"><span data-stu-id="20a20-263">When applied to a parameter, they must be on the same line and separated by a `;` separator.</span></span>

## <a name="formatting-literals"></a><span data-ttu-id="20a20-264">Literais de formatação</span><span class="sxs-lookup"><span data-stu-id="20a20-264">Formatting literals</span></span>

<span data-ttu-id="20a20-265">[F#literais](../language-reference/literals.md) usando o `Literal` atributo deve colocar o atributo em sua própria linha e usar a nomenclatura camelCase:</span><span class="sxs-lookup"><span data-stu-id="20a20-265">[F# literals](../language-reference/literals.md) using the `Literal` attribute should place the attribute on its own line and use camelCase naming:</span></span>

```fsharp
[<Literal>]
let path = __SOURCE_DIRECTORY__ + "/" + __SOURCE_FILE__

[<Literal>]
let myUrl = "www.mywebsitethatiamworkingwith.com"
```

<span data-ttu-id="20a20-266">Evite colocar o atributo na mesma linha como o valor.</span><span class="sxs-lookup"><span data-stu-id="20a20-266">Avoid placing the attribute on the same line as the value.</span></span>
