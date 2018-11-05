---
title: Código F# diretrizes de formatação
description: Aprenda diretrizes para a formatação de código F#.
ms.date: 05/14/2018
ms.openlocfilehash: 0d7d2d1771710db55bf990f3a06079b2aec48fd7
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/02/2018
ms.locfileid: "43857999"
---
# <a name="f-code-formatting-guidelines"></a><span data-ttu-id="d3a6f-103">Código F# diretrizes de formatação</span><span class="sxs-lookup"><span data-stu-id="d3a6f-103">F# code formatting guidelines</span></span>

<span data-ttu-id="d3a6f-104">Este artigo oferece diretrizes para formatar seu código para que seu código F# é:</span><span class="sxs-lookup"><span data-stu-id="d3a6f-104">This article offers guidelines for how to format your code so that your F# code is:</span></span>

* <span data-ttu-id="d3a6f-105">Geralmente é visto como mais legível</span><span class="sxs-lookup"><span data-stu-id="d3a6f-105">Generally viewed as more legible</span></span>
* <span data-ttu-id="d3a6f-106">Está de acordo com as convenções aplicadas por ferramentas de formatação no Visual Studio e outros editores</span><span class="sxs-lookup"><span data-stu-id="d3a6f-106">Is in accordance with conventions applied by formatting tools in Visual Studio and other editors</span></span>
* <span data-ttu-id="d3a6f-107">Semelhante a outro código online</span><span class="sxs-lookup"><span data-stu-id="d3a6f-107">Similar to other code online</span></span>

<span data-ttu-id="d3a6f-108">Essas diretrizes se baseiam [um guia abrangente para convenções de formatação do F#](https://github.com/dungpa/fantomas/blob/master/docs/FormattingConventions.md) pela [Anh-Dung Phan](https://github.com/dungpa).</span><span class="sxs-lookup"><span data-stu-id="d3a6f-108">These guidelines are based on [A comprehensive guide to F# Formatting Conventions](https://github.com/dungpa/fantomas/blob/master/docs/FormattingConventions.md) by [Anh-Dung Phan](https://github.com/dungpa).</span></span>

## <a name="general-rules-for-indentation"></a><span data-ttu-id="d3a6f-109">Regras gerais para recuo</span><span class="sxs-lookup"><span data-stu-id="d3a6f-109">General rules for indentation</span></span>

<span data-ttu-id="d3a6f-110">F# usa o espaço em branco significativo por padrão.</span><span class="sxs-lookup"><span data-stu-id="d3a6f-110">F# uses significant white space by default.</span></span> <span data-ttu-id="d3a6f-111">As diretrizes a seguir destinam-se a fornecer orientação sobre como manipular alguns desafios que isso pode impor.</span><span class="sxs-lookup"><span data-stu-id="d3a6f-111">The following guidelines are intended to provide guidance as to how to juggle some challenges this can impose.</span></span>

### <a name="using-spaces"></a><span data-ttu-id="d3a6f-112">Uso de espaços</span><span class="sxs-lookup"><span data-stu-id="d3a6f-112">Using spaces</span></span>

<span data-ttu-id="d3a6f-113">Quando recuo é necessário, você deve usar espaços, tabulações não.</span><span class="sxs-lookup"><span data-stu-id="d3a6f-113">When indentation is required, you must use spaces, not tabs.</span></span> <span data-ttu-id="d3a6f-114">Pelo menos um espaço é necessário.</span><span class="sxs-lookup"><span data-stu-id="d3a6f-114">At least one space is required.</span></span> <span data-ttu-id="d3a6f-115">Sua organização pode criar padrões de codificação para especificar o número de espaços a serem usados para recuo; dois, três ou quatro espaços de recuo em cada nível em que ocorre o recuo é típico.</span><span class="sxs-lookup"><span data-stu-id="d3a6f-115">Your organization can create coding standards to specify the number of spaces to use for indentation; two, three or four spaces of indentation at each level where indentation occurs is typical.</span></span>

<span data-ttu-id="d3a6f-116">**Recomendamos 4 espaços por recuo.**</span><span class="sxs-lookup"><span data-stu-id="d3a6f-116">**We recommend 4 spaces per indentation.**</span></span>

<span data-ttu-id="d3a6f-117">Dito isso, o recuo dos programas é uma questão subjetiva.</span><span class="sxs-lookup"><span data-stu-id="d3a6f-117">That said, indentation of programs is a subjective matter.</span></span> <span data-ttu-id="d3a6f-118">Variações são Okey, mas é a primeira regra que você deve seguir *consistência de recuo*.</span><span class="sxs-lookup"><span data-stu-id="d3a6f-118">Variations are OK, but the first rule you should follow is *consistency of indentation*.</span></span> <span data-ttu-id="d3a6f-119">Escolha um estilo de recuo de geralmente aceito e usá-lo sistematicamente em toda a sua base de código.</span><span class="sxs-lookup"><span data-stu-id="d3a6f-119">Choose a generally accepted style of indentation and use it systematically throughout your codebase.</span></span>

## <a name="formatting-blank-lines"></a><span data-ttu-id="d3a6f-120">Formatação de linhas em branco</span><span class="sxs-lookup"><span data-stu-id="d3a6f-120">Formatting blank lines</span></span>

* <span data-ttu-id="d3a6f-121">Separado nível superior função e classe definições com duas linhas em branco.</span><span class="sxs-lookup"><span data-stu-id="d3a6f-121">Separate top-level function and class definitions with two blank lines.</span></span>
* <span data-ttu-id="d3a6f-122">As definições de método dentro de uma classe são separadas por uma única linha em branco.</span><span class="sxs-lookup"><span data-stu-id="d3a6f-122">Method definitions inside a class are separated by a single blank line.</span></span>
* <span data-ttu-id="d3a6f-123">Linhas em branco extra podem ser usadas (com moderação) para separar grupos de funções relacionadas.</span><span class="sxs-lookup"><span data-stu-id="d3a6f-123">Extra blank lines may be used (sparingly) to separate groups of related functions.</span></span> <span data-ttu-id="d3a6f-124">Linhas em branco podem ser omitidas entre um monte de linhas relacionadas (por exemplo, um conjunto de implementações fictícias).</span><span class="sxs-lookup"><span data-stu-id="d3a6f-124">Blank lines may be omitted between a bunch of related one-liners (for example, a set of dummy implementations).</span></span>
* <span data-ttu-id="d3a6f-125">Use linhas em branco em funções, com moderação, para indicar seções lógicas.</span><span class="sxs-lookup"><span data-stu-id="d3a6f-125">Use blank lines in functions, sparingly, to indicate logical sections.</span></span>

## <a name="formatting-comments"></a><span data-ttu-id="d3a6f-126">Comentários de formatação</span><span class="sxs-lookup"><span data-stu-id="d3a6f-126">Formatting comments</span></span>

<span data-ttu-id="d3a6f-127">Geralmente prefiro vários comentários de barra dupla ao longo de comentários do bloco de estilo de ML.</span><span class="sxs-lookup"><span data-stu-id="d3a6f-127">Generally prefer multiple double-slash comments over ML-style block comments.</span></span>

```fsharp
// Prefer this style of comments when you want
// to express written ideas on multiple lines.

(*
    ML-style comments are fine, but not a .NET-ism.
    They are useful when needing to modify multi-line comments, though.
*)
```

<span data-ttu-id="d3a6f-128">Comentários embutidos devem colocar em maiuscula a primeira letra.</span><span class="sxs-lookup"><span data-stu-id="d3a6f-128">Inline comments should capitalize the first letter.</span></span>

```fsharp
let f x = x + 1 // Increment by one.
```

## <a name="naming-conventions"></a><span data-ttu-id="d3a6f-129">Convenções de nomenclatura</span><span class="sxs-lookup"><span data-stu-id="d3a6f-129">Naming conventions</span></span>

### <a name="use-camelcase-for-class-bound-expression-bound-and-pattern-bound-values-and-functions"></a><span data-ttu-id="d3a6f-130">Use camelCase para valores de limite de classe, expressão ligada à e padrão de associação e funções</span><span class="sxs-lookup"><span data-stu-id="d3a6f-130">Use camelCase for class-bound, expression-bound and pattern-bound values and functions</span></span>

<span data-ttu-id="d3a6f-131">É comum e aceitos F# estilo use camelCase para todos os nomes associados como variáveis locais ou em correspondências de padrões e as definições de função.</span><span class="sxs-lookup"><span data-stu-id="d3a6f-131">It is common and accepted F# style to use camelCase for all names bound as local variables or in pattern matches and function definitions.</span></span>

```fsharp
// OK
let addIAndJ i j = i + j

// Bad
let addIAndJ I J = I+J

// Bad
let AddIAndJ i j = i + j
```

<span data-ttu-id="d3a6f-132">Funções associadas a localmente em classes também devem usar camelCase.</span><span class="sxs-lookup"><span data-stu-id="d3a6f-132">Locally-bound functions in classes should also use camelCase.</span></span>

```fsharp
type MyClass() =

    let doSomething () =

    let firstResult = ...

    let secondResult = ...

    member x.Result = doSomething()
```

### <a name="use-camelcase-for-module-bound-public-functions"></a><span data-ttu-id="d3a6f-133">Use camelCase para funções públicas de associação de módulo</span><span class="sxs-lookup"><span data-stu-id="d3a6f-133">Use camelCase for module-bound public functions</span></span>

<span data-ttu-id="d3a6f-134">Quando uma função associada de módulo fizer parte de uma API pública, ele deve usar camelCase:</span><span class="sxs-lookup"><span data-stu-id="d3a6f-134">When a module-bound function is part of a public API, it should use camelCase:</span></span>

```fsharp
module MyAPI =
    let publicFunctionOne param1 param2 param2 = ...

    let publicFunctionTwo param1 param2 param3 = ...
```

### <a name="use-camelcase-for-internal-and-private-module-bound-values-and-functions"></a><span data-ttu-id="d3a6f-135">Use camelCase para funções e os valores de limite de módulo internos e privados</span><span class="sxs-lookup"><span data-stu-id="d3a6f-135">Use camelCase for internal and private module-bound values and functions</span></span>

<span data-ttu-id="d3a6f-136">Use camelCase para valores de associação de módulo privados, incluindo o seguinte:</span><span class="sxs-lookup"><span data-stu-id="d3a6f-136">Use camelCase for private module-bound values, including the following:</span></span>

* <span data-ttu-id="d3a6f-137">Funções ad hoc em scripts</span><span class="sxs-lookup"><span data-stu-id="d3a6f-137">Ad hoc functions in scripts</span></span>

* <span data-ttu-id="d3a6f-138">Valores que compõem a implementação interna de um módulo ou tipo</span><span class="sxs-lookup"><span data-stu-id="d3a6f-138">Values making up the internal implementation of a module or type</span></span>

```fsharp
let emailMyBossTheLatestResults =
    ...
```

### <a name="use-camelcase-for-parameters"></a><span data-ttu-id="d3a6f-139">Use camelCase para parâmetros</span><span class="sxs-lookup"><span data-stu-id="d3a6f-139">Use camelCase for parameters</span></span>

<span data-ttu-id="d3a6f-140">Todos os parâmetros devem usar camelCase de acordo com as convenções de nomenclatura do .NET.</span><span class="sxs-lookup"><span data-stu-id="d3a6f-140">All parameters should use camelCase in accordance with .NET naming conventions.</span></span>

```fsharp
module MyModule =
    let myFunction paramOne paramTwo = ...

type MyClass() =
    member this.MyMethod(paramOne, paramTwo) = ...
```

### <a name="use-pascalcase-for-modules"></a><span data-ttu-id="d3a6f-141">Usar PascalCase para módulos</span><span class="sxs-lookup"><span data-stu-id="d3a6f-141">Use PascalCase for modules</span></span>

<span data-ttu-id="d3a6f-142">Todos os módulos (nível superior, internos, privados, aninhados) devem usar PascalCase.</span><span class="sxs-lookup"><span data-stu-id="d3a6f-142">All modules (top-level, internal, private, nested) should use PascalCase.</span></span>

```fsharp
module MyTopLevelModule

module Helpers =
    module private SuperHelpers =
        ...

    ...
```

### <a name="use-pascalcase-for-type-declarations-members-and-labels"></a><span data-ttu-id="d3a6f-143">Usar PascalCase para declarações de tipo, membros e rótulos</span><span class="sxs-lookup"><span data-stu-id="d3a6f-143">Use PascalCase for type declarations, members, and labels</span></span>

<span data-ttu-id="d3a6f-144">Classes, interfaces, estruturas, enumerações, delegados, registros e uniões discriminadas devem ser nomeadas com PascalCase.</span><span class="sxs-lookup"><span data-stu-id="d3a6f-144">Classes, interfaces, structs, enumerations, delegates, records, and discriminated unions should all be named with PascalCase.</span></span> <span data-ttu-id="d3a6f-145">Os membros dentro de tipos e rótulos para registros e uniões discriminadas também devem usar PascalCase.</span><span class="sxs-lookup"><span data-stu-id="d3a6f-145">Members within types and labels for records and discriminated unions should also use PascalCase.</span></span>

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

### <a name="use-pascalcase-for-constructs-intrinsic-to-net"></a><span data-ttu-id="d3a6f-146">Usar PascalCase para construções intrínsecas para o .NET</span><span class="sxs-lookup"><span data-stu-id="d3a6f-146">Use PascalCase for constructs intrinsic to .NET</span></span>

<span data-ttu-id="d3a6f-147">Namespaces, exceções, eventos e projeto /`.dll` nomes também devem usar PascalCase.</span><span class="sxs-lookup"><span data-stu-id="d3a6f-147">Namespaces, exceptions, events, and project/`.dll` names should also use PascalCase.</span></span> <span data-ttu-id="d3a6f-148">Não apenas isso faz o consumo de outras linguagens .NET mais naturais para os consumidores, também é consistente com as convenções de nomenclatura do .NET que você provavelmente encontrará.</span><span class="sxs-lookup"><span data-stu-id="d3a6f-148">Not only does this make consumption from other .NET languages feel more natural to consumers, it's also consistent with .NET naming conventions that you are likely to encounter.</span></span>

### <a name="avoid-underscores-in-names"></a><span data-ttu-id="d3a6f-149">Evite sublinhados em nomes</span><span class="sxs-lookup"><span data-stu-id="d3a6f-149">Avoid underscores in names</span></span>

<span data-ttu-id="d3a6f-150">Historicamente, algumas bibliotecas do F# usaram sublinhados em nomes.</span><span class="sxs-lookup"><span data-stu-id="d3a6f-150">Historically, some F# libraries have used underscores in names.</span></span> <span data-ttu-id="d3a6f-151">No entanto, isso não é mais amplamente é aceito, em parte porque ele estiver em conflito com as convenções de nomenclatura do .NET.</span><span class="sxs-lookup"><span data-stu-id="d3a6f-151">However, this is no longer widely accepted, partly because it clashes with .NET naming conventions.</span></span> <span data-ttu-id="d3a6f-152">Dito isso, alguns programadores em F# usam sublinhados intensamente, em parte por razões históricas e tolerância e respeito é importante.</span><span class="sxs-lookup"><span data-stu-id="d3a6f-152">That said, some F# programmers use underscores heavily, partly for historical reasons, and tolerance and respect is important.</span></span> <span data-ttu-id="d3a6f-153">No entanto, lembre-se de que o estilo é geralmente disliked por outras pessoas que têm uma opção sobre se deve usá-lo.</span><span class="sxs-lookup"><span data-stu-id="d3a6f-153">However, be aware that the style is often disliked by others who have a choice about whether to use it.</span></span>

<span data-ttu-id="d3a6f-154">Algumas exceções inclui interoperar com componentes nativos, onde os sublinhados são muito comuns.</span><span class="sxs-lookup"><span data-stu-id="d3a6f-154">Some exceptions includes interoperating with native components, where underscores are very common.</span></span>

### <a name="use-standard-f-operators"></a><span data-ttu-id="d3a6f-155">Usar operadores de padrão F#</span><span class="sxs-lookup"><span data-stu-id="d3a6f-155">Use standard F# operators</span></span>

<span data-ttu-id="d3a6f-156">Os operadores a seguir são definidos na biblioteca padrão do F# e devem ser usados em vez de definir equivalentes.</span><span class="sxs-lookup"><span data-stu-id="d3a6f-156">The following operators are defined in the F# standard library and should be used instead of defining equivalents.</span></span> <span data-ttu-id="d3a6f-157">Usar esses operadores é recomendável como ele tende a tornar o código mais legível e expressões idiomáticas.</span><span class="sxs-lookup"><span data-stu-id="d3a6f-157">Using these operators is recommended as it tends to make code more readable and idiomatic.</span></span> <span data-ttu-id="d3a6f-158">Os desenvolvedores com experiência em OCaml ou outra linguagem de programação funcional talvez esteja acostumados a idiomas diferentes.</span><span class="sxs-lookup"><span data-stu-id="d3a6f-158">Developers with a background in OCaml or other functional programming language may be accustomed to different idioms.</span></span> <span data-ttu-id="d3a6f-159">A lista a seguir resume os operadores de F# recomendados.</span><span class="sxs-lookup"><span data-stu-id="d3a6f-159">The following list summarizes the recommended F# operators.</span></span>

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

### <a name="use-prefix-syntax-for-generics-foot-in-preference-to-postfix-syntax-t-foo"></a><span data-ttu-id="d3a6f-160">Use a sintaxe de prefixo para genéricos (`Foo<T>`) em preferência a sintaxe de sufixo (`T Foo`)</span><span class="sxs-lookup"><span data-stu-id="d3a6f-160">Use prefix syntax for generics (`Foo<T>`) in preference to postfix syntax (`T Foo`)</span></span>

<span data-ttu-id="d3a6f-161">F# herda de ambos os o estilo de ML sufixo de nomeação de tipos genéricos (por exemplo, `int list`), bem como o prefixo de estilo do .NET (por exemplo, `list<int>`).</span><span class="sxs-lookup"><span data-stu-id="d3a6f-161">F# inherits both the postfix ML style of naming generic types (for example, `int list`) as well as the prefix .NET style (for example, `list<int>`).</span></span> <span data-ttu-id="d3a6f-162">Preferir o estilo de .NET, exceto para quatro tipos específicos:</span><span class="sxs-lookup"><span data-stu-id="d3a6f-162">Prefer the .NET style, except for four specific types:</span></span>

1. <span data-ttu-id="d3a6f-163">Para listas do F#, use a forma pós-fixada: `int list` em vez de `list<int>`.</span><span class="sxs-lookup"><span data-stu-id="d3a6f-163">For F# Lists, use the postfix form: `int list` rather than `list<int>`.</span></span>
2. <span data-ttu-id="d3a6f-164">Para opções de F#, use a forma pós-fixada: `int option` em vez de `option<int>`.</span><span class="sxs-lookup"><span data-stu-id="d3a6f-164">For F# Options, use the postfix form: `int option` rather than `option<int>`.</span></span>
3. <span data-ttu-id="d3a6f-165">Para matrizes F#, use o nome sintático `int[]` em vez de `int array` ou `array<int>`.</span><span class="sxs-lookup"><span data-stu-id="d3a6f-165">For F# arrays, use the syntactic name `int[]` rather than `int array` or `array<int>`.</span></span>
4. <span data-ttu-id="d3a6f-166">Para as células de referência, use `int ref` em vez de `ref<int>` ou `Ref<int>`.</span><span class="sxs-lookup"><span data-stu-id="d3a6f-166">For Reference Cells, use `int ref` rather than `ref<int>` or `Ref<int>`.</span></span>

<span data-ttu-id="d3a6f-167">Para todos os outros tipos, use o formulário de prefixo.</span><span class="sxs-lookup"><span data-stu-id="d3a6f-167">For all other types, use the prefix form.</span></span>

## <a name="formatting-tuples"></a><span data-ttu-id="d3a6f-168">As tuplas de formatação</span><span class="sxs-lookup"><span data-stu-id="d3a6f-168">Formatting tuples</span></span>

<span data-ttu-id="d3a6f-169">Uma instanciação de tupla deve estar entre parênteses e vírgulas dentro de delimitadores devem ser seguidas por um único espaço, por exemplo: `(1, 2)`, `(x, y, z)`.</span><span class="sxs-lookup"><span data-stu-id="d3a6f-169">A tuple instantiation should be parenthesized, and the delimiting commas within should be followed by a single space, for example: `(1, 2)`, `(x, y, z)`.</span></span>

<span data-ttu-id="d3a6f-170">Normalmente, ela é aceita para omitir os parênteses na correspondência de padrão de tuplas:</span><span class="sxs-lookup"><span data-stu-id="d3a6f-170">It is commonly accepted to omit parentheses in pattern matching of tuples:</span></span>

```fsharp
let (x, y) = z // Destructuring
let x, y = z // OK

// OK
match x, y with
| 1, _ -> 0
| x, 1 -> 0
| x, y -> 1
```

## <a name="formatting-discriminated-union-declarations"></a><span data-ttu-id="d3a6f-171">Formatação discriminada declarações de união</span><span class="sxs-lookup"><span data-stu-id="d3a6f-171">Formatting discriminated union declarations</span></span>

<span data-ttu-id="d3a6f-172">Recuar `|` na definição de tipo por 4 espaços:</span><span class="sxs-lookup"><span data-stu-id="d3a6f-172">Indent `|` in type definition by 4 spaces:</span></span>

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

## <a name="formatting-discriminated-unions"></a><span data-ttu-id="d3a6f-173">Formatação de uniões discriminadas</span><span class="sxs-lookup"><span data-stu-id="d3a6f-173">Formatting discriminated unions</span></span>

<span data-ttu-id="d3a6f-174">Uniões discriminadas instanciado divididas em várias linhas deve fornecer os dados contidos um novo escopo com recuo:</span><span class="sxs-lookup"><span data-stu-id="d3a6f-174">Instantiated Discriminated Unions that split across multiple lines should give contained data a new scope with indentation:</span></span>

```fsharp
let tree1 =
    BinaryNode
        (BinaryNode(BinaryValue 1, BinaryValue 2),
         BinaryNode(BinaryValue 3, BinaryValue 4))
```

<span data-ttu-id="d3a6f-175">O parêntese de fechamento também pode ser em uma nova linha:</span><span class="sxs-lookup"><span data-stu-id="d3a6f-175">The closing parenthesis can also be on a new line:</span></span>

```fsharp
let tree1 =
    BinaryNode(
        BinaryNode(BinaryValue 1, BinaryValue 2),
        BinaryNode(BinaryValue 3, BinaryValue 4)
    )
```

## <a name="formatting-record-declarations"></a><span data-ttu-id="d3a6f-176">Declarações de registro de formatação</span><span class="sxs-lookup"><span data-stu-id="d3a6f-176">Formatting record declarations</span></span>

<span data-ttu-id="d3a6f-177">Recuar `{` no tipo de definição por 4 espaços e iniciar a lista de campos na mesma linha:</span><span class="sxs-lookup"><span data-stu-id="d3a6f-177">Indent `{` in type definition by 4 spaces and start the field list on the same line:</span></span>

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

<span data-ttu-id="d3a6f-178">Colocando o token de abertura na mesma linha e o token de fechamento em uma nova linha também é bom, mas lembre-se de que você precisa usar o [sintaxe detalhada](../language-reference/verbose-syntax.md) para definir os membros (o `with` palavra-chave):</span><span class="sxs-lookup"><span data-stu-id="d3a6f-178">Placing the opening token on the same line and the closing token on a new line is also fine, but be aware that you need to use the [verbose syntax](../language-reference/verbose-syntax.md) to define members (the `with` keyword):</span></span>

```fsharp
//  OK, but verbose syntax required
type PostalAddress = { 
    Address: string
    City: string
    Zip: string
} with
    member x.ZipAndCity = sprintf "%s %s" x.Zip x.City
```

## <a name="formatting-records"></a><span data-ttu-id="d3a6f-179">Formatação de registros</span><span class="sxs-lookup"><span data-stu-id="d3a6f-179">Formatting records</span></span>

<span data-ttu-id="d3a6f-180">Registros curtos podem ser escritos em uma linha:</span><span class="sxs-lookup"><span data-stu-id="d3a6f-180">Short records can be written in one line:</span></span>

```fsharp
let point = { X = 1.0; Y = 0.0 }
```

<span data-ttu-id="d3a6f-181">Os registros que são mais longas devem usar novas linhas para rótulos:</span><span class="sxs-lookup"><span data-stu-id="d3a6f-181">Records that are longer should use new lines for labels:</span></span>

```fsharp
let rainbow =
    { Boss = "Jeffrey"
      Lackeys = ["Zippy"; "George"; "Bungle"] }
```

<span data-ttu-id="d3a6f-182">Também é bom colocar o token de abertura na mesma linha e o token de fechamento em uma nova linha:</span><span class="sxs-lookup"><span data-stu-id="d3a6f-182">Placing the opening token on the same line and the closing token on a new line is also fine:</span></span>

```fsharp
let rainbow = {
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
```

<span data-ttu-id="d3a6f-183">As mesmas regras se aplicam para elementos list e array.</span><span class="sxs-lookup"><span data-stu-id="d3a6f-183">The same rules apply for list and array elements.</span></span>

## <a name="formatting-lists-and-arrays"></a><span data-ttu-id="d3a6f-184">Formatando listas e matrizes</span><span class="sxs-lookup"><span data-stu-id="d3a6f-184">Formatting lists and arrays</span></span>

<span data-ttu-id="d3a6f-185">Gravar `x :: l` com espaços em torno de `::` operador (`::` é um operador de infixo, portanto, cercado por espaços) e `[1; 2; 3]` (`;` é um delimitador, portanto, seguido por um espaço).</span><span class="sxs-lookup"><span data-stu-id="d3a6f-185">Write `x :: l` with spaces around the `::` operator (`::` is an infix operator, hence surrounded by spaces) and `[1; 2; 3]` (`;` is a delimiter, hence followed by a space).</span></span>

<span data-ttu-id="d3a6f-186">Sempre use pelo menos um espaço entre os dois operadores semelhante de chave distintos.</span><span class="sxs-lookup"><span data-stu-id="d3a6f-186">Always use at least one space between two distinct brace-like operators.</span></span> <span data-ttu-id="d3a6f-187">Por exemplo, deixar um espaço entre um `[` e um `{`.</span><span class="sxs-lookup"><span data-stu-id="d3a6f-187">For example, leave a space between a `[` and a `{`.</span></span>

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

<span data-ttu-id="d3a6f-188">Listas e matrizes que são dividem em várias linhas seguem uma regra semelhante como registros:</span><span class="sxs-lookup"><span data-stu-id="d3a6f-188">Lists and arrays that split across multiple lines follow a similar rule as records do:</span></span>

```fsharp
let pascalsTriangle = [|
    [|1|]
    [|1; 1|]
    [|1; 2; 1|]
    [|1; 3; 3; 1|]
    [|1; 4; 6; 4; 1|]
    [|1; 5; 10; 10; 5; 1|]
    [|1; 6; 15; 20; 15; 6; 1|]
    [|1; 7; 21; 35; 35; 21; 7; 1|]
    [|1; 8; 28; 56; 70; 56; 28; 8; 1|]
|]
```

## <a name="formatting-if-expressions"></a><span data-ttu-id="d3a6f-189">Formatação se expressões</span><span class="sxs-lookup"><span data-stu-id="d3a6f-189">Formatting if expressions</span></span>

<span data-ttu-id="d3a6f-190">Recuo de condicionais depende dos tamanhos das expressões que compõem-los.</span><span class="sxs-lookup"><span data-stu-id="d3a6f-190">Indentation of conditionals depends on the sizes of the expressions that make them up.</span></span> <span data-ttu-id="d3a6f-191">Se `cond`, `e1` e `e2` são curto, simplesmente gravá-los em uma única linha:</span><span class="sxs-lookup"><span data-stu-id="d3a6f-191">If `cond`, `e1` and `e2` are short, simply write them on one line:</span></span>

```fsharp
if cond then e1 else e2
```

<span data-ttu-id="d3a6f-192">Se qualquer um dos `cond`, `e1` ou `e2` são mais tempo, mas não de várias linhas:</span><span class="sxs-lookup"><span data-stu-id="d3a6f-192">If either `cond`, `e1` or `e2` are longer, but not multi-line:</span></span>

```fsharp
if cond
then e1
else e2
```

<span data-ttu-id="d3a6f-193">Se qualquer uma das expressões são várias linhas:</span><span class="sxs-lookup"><span data-stu-id="d3a6f-193">If any of the expressions are multi-line:</span></span>

```fsharp
if cond then
    e1
else
    e2
```

<span data-ttu-id="d3a6f-194">Várias condições com `elif` e `else` são recuadas no mesmo escopo que o `if`:</span><span class="sxs-lookup"><span data-stu-id="d3a6f-194">Multiple conditionals with `elif` and `else` are indented at the same scope as the `if`:</span></span>

```fsharp
if cond1 then e1
elif cond2 then e2
elif cond3 then e3
else e4
```

### <a name="pattern-matching-constructs"></a><span data-ttu-id="d3a6f-195">Construções de correspondência de padrão</span><span class="sxs-lookup"><span data-stu-id="d3a6f-195">Pattern matching constructs</span></span>

<span data-ttu-id="d3a6f-196">Use um `|` para cada cláusula de uma correspondência com nenhum recuo.</span><span class="sxs-lookup"><span data-stu-id="d3a6f-196">Use a `|` for each clause of a match with no indentation.</span></span> <span data-ttu-id="d3a6f-197">Se a expressão for curta, você pode considerar usando uma única linha, se cada subexpressão também é simple.</span><span class="sxs-lookup"><span data-stu-id="d3a6f-197">If the expression is short, you can consider using a single line if each subexpression is also simple.</span></span>

```fsharp
// OK
match l with
| { him = x; her = "Posh" } :: tail -> _
| _ :: tail -> findDavid tail
| [] -> failwith "Couldn't find David"

// Not OK
match l with
    | { him = x; her = "Posh" } :: tail -> _
    | _ :: tail -> findDavid tail
    | [] -> failwith "Couldn't find David"
```

<span data-ttu-id="d3a6f-198">Se a expressão à direita da seta para a correspondência for muito grande, mova-o para a seguinte linha, recuado em uma etapa do `match` / `|`.</span><span class="sxs-lookup"><span data-stu-id="d3a6f-198">If the expression on the right of the pattern matching arrow is too large, move it to the following line, indented one step from the `match`/`|`.</span></span>

```fsharp
match lam with
| Var v -> 1
| Abs(x, body) ->
    1 + sizeLambda body
| App(lam1, lam2) ->
    sizeLambda lam1 + sizeLambda lam2

```

<span data-ttu-id="d3a6f-199">Correspondência de padrões de funções anônimas, começando pelo `function`, não geralmente deve Recuar muito longe.</span><span class="sxs-lookup"><span data-stu-id="d3a6f-199">Pattern matching of anonymous functions, starting by `function`, should generally not indent too far.</span></span> <span data-ttu-id="d3a6f-200">Por exemplo, é bom recuar um escopo da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="d3a6f-200">For example, indenting one scope as follows is fine:</span></span>

```fsharp
lambdaList
|> List.map (function
    | Abs(x, body) -> 1 + sizeLambda 0 body
    | App(lam1, lam2) -> sizeLambda (sizeLambda 0 lam1) lam2
    | Var v -> 1)
```

<span data-ttu-id="d3a6f-201">Correspondência de padrão de funções definidas pelo `let` ou `let rec` deve ser recuados 4 espaços após a inicialização do `let`, mesmo se `function` palavra-chave é usada:</span><span class="sxs-lookup"><span data-stu-id="d3a6f-201">Pattern matching in functions defined by `let` or `let rec` should be indented 4 spaces after starting of `let`, even if `function` keyword is used:</span></span>

```fsharp
let rec sizeLambda acc = function
    | Abs(x, body) -> sizeLambda (succ acc) body
    | App(lam1, lam2) -> sizeLambda (sizeLambda acc lam1) lam2
    | Var v -> succ acc
```

<span data-ttu-id="d3a6f-202">Não recomendamos alinhando setas.</span><span class="sxs-lookup"><span data-stu-id="d3a6f-202">We do not recommend aligning arrows.</span></span>

## <a name="formatting-trywith-expressions"></a><span data-ttu-id="d3a6f-203">Formatação de try / com expressões</span><span class="sxs-lookup"><span data-stu-id="d3a6f-203">Formatting try/with expressions</span></span>

<span data-ttu-id="d3a6f-204">Correspondência de padrão em que o tipo de exceção deve ser recuado no mesmo nível como `with`.</span><span class="sxs-lookup"><span data-stu-id="d3a6f-204">Pattern matching on the exception type should be indented at the same level as `with`.</span></span>

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

## <a name="formatting-function-parameter-application"></a><span data-ttu-id="d3a6f-205">Aplicativo de parâmetro de função de formatação</span><span class="sxs-lookup"><span data-stu-id="d3a6f-205">Formatting function parameter application</span></span>

<span data-ttu-id="d3a6f-206">Em geral, a maioria dos aplicativos de parâmetro de função é feito na mesma linha.</span><span class="sxs-lookup"><span data-stu-id="d3a6f-206">In general, most function parameter application is done on the same line.</span></span>

<span data-ttu-id="d3a6f-207">Se você quiser aplicar os parâmetros para uma função em uma nova linha, recuo-los por um escopo.</span><span class="sxs-lookup"><span data-stu-id="d3a6f-207">If you wish to apply parameters to a function on a new line, indent them by one scope.</span></span>

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

<span data-ttu-id="d3a6f-208">As mesmas diretrizes se aplicam para as expressões lambda como argumentos de função.</span><span class="sxs-lookup"><span data-stu-id="d3a6f-208">The same guidelines apply for lambda expressions as function arguments.</span></span> <span data-ttu-id="d3a6f-209">Se o corpo de uma expressão lambda, o corpo pode ter outra linha, recuada de acordo com um escopo</span><span class="sxs-lookup"><span data-stu-id="d3a6f-209">If the body of a lambda expression, the body can have another line, indented by one scope</span></span>

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

<span data-ttu-id="d3a6f-210">No entanto, se o corpo de uma expressão lambda é a mais de uma linha, considere fatorá-lo em uma função separada em vez de ter uma construção de várias linha aplicada como um único argumento para uma função.</span><span class="sxs-lookup"><span data-stu-id="d3a6f-210">However, if the body of a lambda expression is more than one line, consider factoring it out into a separate function rather than have a multi-line construct applied as a single argument to a function.</span></span>

### <a name="formatting-infix-operators"></a><span data-ttu-id="d3a6f-211">Operadores infixos de formatação</span><span class="sxs-lookup"><span data-stu-id="d3a6f-211">Formatting infix operators</span></span>

<span data-ttu-id="d3a6f-212">Operadores separados por espaços.</span><span class="sxs-lookup"><span data-stu-id="d3a6f-212">Separate operators by spaces.</span></span> <span data-ttu-id="d3a6f-213">Óbvias exceções a essa regra são as `!` e `.` operadores.</span><span class="sxs-lookup"><span data-stu-id="d3a6f-213">Obvious exceptions to this rule are the `!` and `.` operators.</span></span>

<span data-ttu-id="d3a6f-214">Expressões de infixo são Okey para o antecipação da linha na mesma coluna:</span><span class="sxs-lookup"><span data-stu-id="d3a6f-214">Infix expressions are OK to lineup on same column:</span></span>

```fsharp
acc +
(sprintf "\t%s - %i\n\r"
     x.IngredientName x.Quantity)

let function1 arg1 arg2 arg3 arg4 =
    arg1 + arg2 +
    arg3 + arg4
```

### <a name="formatting-pipeline-operators"></a><span data-ttu-id="d3a6f-215">Formatação de operadores de pipeline</span><span class="sxs-lookup"><span data-stu-id="d3a6f-215">Formatting pipeline operators</span></span>

<span data-ttu-id="d3a6f-216">Pipeline `|>` operadores devem ficar sob eles operam em expressões.</span><span class="sxs-lookup"><span data-stu-id="d3a6f-216">Pipeline `|>` operators should go underneath the expressions they operate on.</span></span>

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

### <a name="formatting-modules"></a><span data-ttu-id="d3a6f-217">Formatação de módulos</span><span class="sxs-lookup"><span data-stu-id="d3a6f-217">Formatting modules</span></span>

<span data-ttu-id="d3a6f-218">Em um módulo local deve ser recuado em relação ao módulo, mas o código em um módulo de nível superior não deve ser recuado.</span><span class="sxs-lookup"><span data-stu-id="d3a6f-218">Code in a local module must be indented relative to the module, but code in a top-level module should not be indented.</span></span> <span data-ttu-id="d3a6f-219">Não tem elementos do Namespace a ser recuado.</span><span class="sxs-lookup"><span data-stu-id="d3a6f-219">Namespace elements do not have to be indented.</span></span>

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

### <a name="formatting-object-expressions-and-interfaces"></a><span data-ttu-id="d3a6f-220">Formatação de expressões de objeto e interfaces</span><span class="sxs-lookup"><span data-stu-id="d3a6f-220">Formatting object expressions and interfaces</span></span>

<span data-ttu-id="d3a6f-221">Expressões de objeto e as interfaces devem ser alinhados da mesma forma com `member` sendo recuado após 4 espaços.</span><span class="sxs-lookup"><span data-stu-id="d3a6f-221">Object expressions and interfaces should be aligned in the same way with `member` being indented after 4 spaces.</span></span>

```fsharp
let comparer =
    { new IComparer<string> with
          member x.Compare(s1, s2) =
              let rev (s : String) =
                  new String (Array.rev (s.ToCharArray()))
              let reversed = rev s1
              reversed.CompareTo (rev s2) }
```

### <a name="formatting-white-space-in-expressions"></a><span data-ttu-id="d3a6f-222">Formatação de espaço em branco em expressões</span><span class="sxs-lookup"><span data-stu-id="d3a6f-222">Formatting white space in expressions</span></span>

<span data-ttu-id="d3a6f-223">Evite espaço em branco estranhos em expressões de F#.</span><span class="sxs-lookup"><span data-stu-id="d3a6f-223">Avoid extraneous white space in F# expressions.</span></span>

```fsharp
// OK
spam (ham.[1])

// Not OK
spam ( ham.[ 1 ] )
```

<span data-ttu-id="d3a6f-224">Argumentos nomeados também não devem ter espaço em torno de `=`:</span><span class="sxs-lookup"><span data-stu-id="d3a6f-224">Named arguments should also not have space surrounding the `=`:</span></span>

```fsharp
// OK
let makeStreamReader x = new System.IO.StreamReader(path=x)

// Not OK
let makeStreamReader x = new System.IO.StreamReader(path = x)
```
