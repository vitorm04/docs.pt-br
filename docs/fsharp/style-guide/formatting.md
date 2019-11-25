---
title: Diretrizes de formatação de código do F#
description: Aprenda as diretrizes para F# a formatação de código.
ms.date: 11/04/2019
ms.openlocfilehash: 895c8211731b47bd4c59d762d5806cfc1bfe232d
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74089314"
---
# <a name="f-code-formatting-guidelines"></a><span data-ttu-id="f6d3c-103">Diretrizes de formatação de código do F#</span><span class="sxs-lookup"><span data-stu-id="f6d3c-103">F# code formatting guidelines</span></span>

<span data-ttu-id="f6d3c-104">Este artigo oferece diretrizes sobre como formatar seu código para que seu F# código seja:</span><span class="sxs-lookup"><span data-stu-id="f6d3c-104">This article offers guidelines for how to format your code so that your F# code is:</span></span>

* <span data-ttu-id="f6d3c-105">Geralmente exibido como mais legível</span><span class="sxs-lookup"><span data-stu-id="f6d3c-105">Generally viewed as more legible</span></span>
* <span data-ttu-id="f6d3c-106">Está de acordo com as convenções aplicadas pelas ferramentas de formatação no Visual Studio e em outros editores</span><span class="sxs-lookup"><span data-stu-id="f6d3c-106">Is in accordance with conventions applied by formatting tools in Visual Studio and other editors</span></span>
* <span data-ttu-id="f6d3c-107">Semelhante a outro código online</span><span class="sxs-lookup"><span data-stu-id="f6d3c-107">Similar to other code online</span></span>

<span data-ttu-id="f6d3c-108">Essas diretrizes se baseiam em [um guia abrangente F# para formatar convenções](https://github.com/dungpa/fantomas/blob/master/docs/FormattingConventions.md) por [Anh-Dung Phan](https://github.com/dungpa).</span><span class="sxs-lookup"><span data-stu-id="f6d3c-108">These guidelines are based on [A comprehensive guide to F# Formatting Conventions](https://github.com/dungpa/fantomas/blob/master/docs/FormattingConventions.md) by [Anh-Dung Phan](https://github.com/dungpa).</span></span>

## <a name="general-rules-for-indentation"></a><span data-ttu-id="f6d3c-109">Regras gerais para recuo</span><span class="sxs-lookup"><span data-stu-id="f6d3c-109">General rules for indentation</span></span>

<span data-ttu-id="f6d3c-110">F#usa um espaço em branco significativo por padrão.</span><span class="sxs-lookup"><span data-stu-id="f6d3c-110">F# uses significant white space by default.</span></span> <span data-ttu-id="f6d3c-111">As diretrizes a seguir destinam-se a fornecer orientações sobre como manipular alguns desafios que isso pode impor.</span><span class="sxs-lookup"><span data-stu-id="f6d3c-111">The following guidelines are intended to provide guidance as to how to juggle some challenges this can impose.</span></span>

### <a name="using-spaces"></a><span data-ttu-id="f6d3c-112">Usando espaços</span><span class="sxs-lookup"><span data-stu-id="f6d3c-112">Using spaces</span></span>

<span data-ttu-id="f6d3c-113">Quando o recuo é necessário, você deve usar espaços, não tabulações.</span><span class="sxs-lookup"><span data-stu-id="f6d3c-113">When indentation is required, you must use spaces, not tabs.</span></span> <span data-ttu-id="f6d3c-114">Pelo menos um espaço é necessário.</span><span class="sxs-lookup"><span data-stu-id="f6d3c-114">At least one space is required.</span></span> <span data-ttu-id="f6d3c-115">Sua organização pode criar padrões de codificação para especificar o número de espaços a serem usados para recuo; dois, três ou quatro espaços de recuo em cada nível em que o recuo ocorre é típico.</span><span class="sxs-lookup"><span data-stu-id="f6d3c-115">Your organization can create coding standards to specify the number of spaces to use for indentation; two, three or four spaces of indentation at each level where indentation occurs is typical.</span></span>

<span data-ttu-id="f6d3c-116">**Recomendamos 4 espaços por recuo.**</span><span class="sxs-lookup"><span data-stu-id="f6d3c-116">**We recommend 4 spaces per indentation.**</span></span>

<span data-ttu-id="f6d3c-117">Dito isso, o recuo de programas é uma questão subjetiva.</span><span class="sxs-lookup"><span data-stu-id="f6d3c-117">That said, indentation of programs is a subjective matter.</span></span> <span data-ttu-id="f6d3c-118">As variações estão OK, mas a primeira regra que você deve seguir é a *consistência do recuo*.</span><span class="sxs-lookup"><span data-stu-id="f6d3c-118">Variations are OK, but the first rule you should follow is *consistency of indentation*.</span></span> <span data-ttu-id="f6d3c-119">Escolha um estilo de recuo em geral aceito e use-o sistematicamente em toda a base de código.</span><span class="sxs-lookup"><span data-stu-id="f6d3c-119">Choose a generally accepted style of indentation and use it systematically throughout your codebase.</span></span>

## <a name="formatting-white-space"></a><span data-ttu-id="f6d3c-120">Formatando espaço em branco</span><span class="sxs-lookup"><span data-stu-id="f6d3c-120">Formatting white space</span></span>

<span data-ttu-id="f6d3c-121">F#é diferenciação de espaço em branco.</span><span class="sxs-lookup"><span data-stu-id="f6d3c-121">F# is white space sensitive.</span></span> <span data-ttu-id="f6d3c-122">Embora a maioria das semânticas de espaço em branco seja coberta por um recuo adequado, há algumas outras coisas a serem consideradas.</span><span class="sxs-lookup"><span data-stu-id="f6d3c-122">Although most semantics from white space are covered by proper indentation, there are some other things to consider.</span></span>

### <a name="formatting-operators-in-arithmetic-expressions"></a><span data-ttu-id="f6d3c-123">Formatando operadores em expressões aritméticas</span><span class="sxs-lookup"><span data-stu-id="f6d3c-123">Formatting operators in arithmetic expressions</span></span>

<span data-ttu-id="f6d3c-124">Sempre use espaço em branco em relação a expressões aritméticas binárias:</span><span class="sxs-lookup"><span data-stu-id="f6d3c-124">Always use white space around binary arithmetic expressions:</span></span>

```fsharp
let subtractThenAdd x = x - 1 + 3
```

<span data-ttu-id="f6d3c-125">Operadores unários `-` devem sempre ter o valor que eles estão negando imediatamente após:</span><span class="sxs-lookup"><span data-stu-id="f6d3c-125">Unary `-` operators should always have the value they are negating immediately follow:</span></span>

```fsharp
// OK
let negate x = -x

// Bad
let negateBad x = - x
```

<span data-ttu-id="f6d3c-126">Adicionar um caractere de espaço em branco após o operador de `-` pode levar à confusão para outras pessoas.</span><span class="sxs-lookup"><span data-stu-id="f6d3c-126">Adding a white-space character after the `-` operator can lead to confusion for others.</span></span>

<span data-ttu-id="f6d3c-127">Em resumo, é importante sempre:</span><span class="sxs-lookup"><span data-stu-id="f6d3c-127">In summary, it's important to always:</span></span>

* <span data-ttu-id="f6d3c-128">Operadores binários surround com espaço em branco</span><span class="sxs-lookup"><span data-stu-id="f6d3c-128">Surround binary operators with white space</span></span>
* <span data-ttu-id="f6d3c-129">Nunca ter espaço em branco à direita após um operador unário</span><span class="sxs-lookup"><span data-stu-id="f6d3c-129">Never have trailing white space after a unary operator</span></span>

<span data-ttu-id="f6d3c-130">A diretriz de operador aritmético binária é especialmente importante.</span><span class="sxs-lookup"><span data-stu-id="f6d3c-130">The binary arithmetic operator guideline is especially important.</span></span> <span data-ttu-id="f6d3c-131">Falha ao envolver um operador de `-` binário, quando combinado com determinadas opções de formatação, pode levar a interpretá-lo como um `-`unário.</span><span class="sxs-lookup"><span data-stu-id="f6d3c-131">Failing to surround a binary `-` operator, when combined with certain formatting choices, could lead to interpreting it as a unary `-`.</span></span>

### <a name="surround-a-custom-operator-definition-with-white-space"></a><span data-ttu-id="f6d3c-132">Cerca de uma definição de operador personalizada com espaço em branco</span><span class="sxs-lookup"><span data-stu-id="f6d3c-132">Surround a custom operator definition with white space</span></span>

<span data-ttu-id="f6d3c-133">Sempre use o espaço em branco para envolver uma definição de operador:</span><span class="sxs-lookup"><span data-stu-id="f6d3c-133">Always use white space to surround an operator definition:</span></span>

```fsharp
// OK
let ( !> ) x f = f x

// Bad
let (!>) x f = f x
```

<span data-ttu-id="f6d3c-134">Para qualquer operador personalizado que comece com `*` e que tenha mais de um caractere, você precisará adicionar um espaço em branco ao início da definição para evitar uma ambiguidade do compilador.</span><span class="sxs-lookup"><span data-stu-id="f6d3c-134">For any custom operator that starts with `*` and that has more than one character, you need to add a white space to the beginning of the definition to avoid a compiler ambiguity.</span></span> <span data-ttu-id="f6d3c-135">Por isso, é recomendável que você simplesmente coloque as definições de todos os operadores com um único caractere de espaço em branco.</span><span class="sxs-lookup"><span data-stu-id="f6d3c-135">Because of this, we recommend that you simply surround the definitions of all operators with a single white-space character.</span></span>

### <a name="surround-function-parameter-arrows-with-white-space"></a><span data-ttu-id="f6d3c-136">Setas de parâmetro de função surround com espaço em branco</span><span class="sxs-lookup"><span data-stu-id="f6d3c-136">Surround function parameter arrows with white space</span></span>

<span data-ttu-id="f6d3c-137">Ao definir a assinatura de uma função, use espaço em branco em volta do símbolo de `->`:</span><span class="sxs-lookup"><span data-stu-id="f6d3c-137">When defining the signature of a function, use white space around the `->` symbol:</span></span>

```fsharp
// OK
type MyFun = int -> int -> string

// Bad
type MyFunBad = int->int->string
```

### <a name="surround-function-arguments-with-white-space"></a><span data-ttu-id="f6d3c-138">Argumentos da função surround com espaço em branco</span><span class="sxs-lookup"><span data-stu-id="f6d3c-138">Surround function arguments with white space</span></span>

<span data-ttu-id="f6d3c-139">Ao definir uma função, use o espaço em branco em volta de cada argumento.</span><span class="sxs-lookup"><span data-stu-id="f6d3c-139">When defining a function, use white space around each argument.</span></span>

```fsharp
// OK
let myFun (a: decimal) b c = a + b + c

// Bad
let myFunBad (a:decimal)(b)c = a + b + c
```

### <a name="place-parameters-on-a-new-line-for-very-long-member-definitions"></a><span data-ttu-id="f6d3c-140">Coloque os parâmetros em uma nova linha para definições de membros muito longos</span><span class="sxs-lookup"><span data-stu-id="f6d3c-140">Place parameters on a new line for very long member definitions</span></span>

<span data-ttu-id="f6d3c-141">Se você tiver uma definição de membro muito longa, coloque os parâmetros em novas linhas e recue-os em um escopo.</span><span class="sxs-lookup"><span data-stu-id="f6d3c-141">If you have a very long member definition, place the parameters on new lines and indent them one scope.</span></span>

```fsharp
type C() =
    member _.LongMethodWithLotsOfParameters(
        aVeryLongType: AVeryLongTypeThatYouNeedToUse
        aSecondVeryLongType: AVeryLongTypeThatYouNeedToUse
        aThirdVeryLongType: AVeryLongTypeThatYouNeedToUse) =
        // ... the body of the method follows
```

<span data-ttu-id="f6d3c-142">Isso também se aplica a construtores:</span><span class="sxs-lookup"><span data-stu-id="f6d3c-142">This also applies to constructors:</span></span>

```fsharp
type C(
    aVeryLongType: AVeryLongTypeThatYouNeedToUse
    aSecondVeryLongType: AVeryLongTypeThatYouNeedToUse
    aThirdVeryLongType: AVeryLongTypeThatYouNeedToUse) =
    // ... the body of the class follows
```

### <a name="type-annotations"></a><span data-ttu-id="f6d3c-143">Anotações de tipo</span><span class="sxs-lookup"><span data-stu-id="f6d3c-143">Type annotations</span></span>

#### <a name="right-pad-function-argument-type-annotations"></a><span data-ttu-id="f6d3c-144">Anotações do tipo de argumento da função de preenchimento direto</span><span class="sxs-lookup"><span data-stu-id="f6d3c-144">Right-pad function argument type annotations</span></span>

<span data-ttu-id="f6d3c-145">Ao definir argumentos com anotações de tipo, use o espaço em branco após o símbolo de `:`:</span><span class="sxs-lookup"><span data-stu-id="f6d3c-145">When defining arguments with type annotations, use white space after the `:` symbol:</span></span>

```fsharp
// OK
let complexFunction (a: int) (b: int) c = a + b + c

// Bad
let complexFunctionBad (a :int) (b :int) (c:int) = a + b + c
```

#### <a name="surround-return-type-annotations-with-white-space"></a><span data-ttu-id="f6d3c-146">Anotações de tipo de retorno surround com espaço em branco</span><span class="sxs-lookup"><span data-stu-id="f6d3c-146">Surround return type annotations with white space</span></span>

<span data-ttu-id="f6d3c-147">Em uma anotação de tipo de valor ou função que permite associar (tipo de retorno no caso de uma função), use espaço em branco antes e depois do símbolo de `:`:</span><span class="sxs-lookup"><span data-stu-id="f6d3c-147">In a let-bound function or value type annotation (return type in the case of a function), use white space before and after the `:` symbol:</span></span>

```fsharp
// OK
let expensiveToCompute : int = 0 // Type annotation for let-bound value
let myFun (a: decimal) b c : decimal = a + b + c // Type annotation for the return type of a function
// Bad
let expensiveToComputeBad1:int = 1
let expensiveToComputeBad2 :int = 2
let myFunBad (a: decimal) b c:decimal = a + b + c
```

## <a name="formatting-blank-lines"></a><span data-ttu-id="f6d3c-148">Formatando linhas em branco</span><span class="sxs-lookup"><span data-stu-id="f6d3c-148">Formatting blank lines</span></span>

* <span data-ttu-id="f6d3c-149">Separe as definições de função e classe de nível superior com duas linhas em branco.</span><span class="sxs-lookup"><span data-stu-id="f6d3c-149">Separate top-level function and class definitions with two blank lines.</span></span>
* <span data-ttu-id="f6d3c-150">As definições de método dentro de uma classe são separadas por uma única linha em branco.</span><span class="sxs-lookup"><span data-stu-id="f6d3c-150">Method definitions inside a class are separated by a single blank line.</span></span>
* <span data-ttu-id="f6d3c-151">Linhas em branco extras podem ser usadas (com moderação) para separar grupos de funções relacionadas.</span><span class="sxs-lookup"><span data-stu-id="f6d3c-151">Extra blank lines may be used (sparingly) to separate groups of related functions.</span></span> <span data-ttu-id="f6d3c-152">As linhas em branco podem ser omitidas entre uma porção de uma linha única relacionada (por exemplo, um conjunto de implementações fictícias).</span><span class="sxs-lookup"><span data-stu-id="f6d3c-152">Blank lines may be omitted between a bunch of related one-liners (for example, a set of dummy implementations).</span></span>
* <span data-ttu-id="f6d3c-153">Use linhas em branco em funções, com moderação, para indicar seções lógicas.</span><span class="sxs-lookup"><span data-stu-id="f6d3c-153">Use blank lines in functions, sparingly, to indicate logical sections.</span></span>

## <a name="formatting-comments"></a><span data-ttu-id="f6d3c-154">Formatando comentários</span><span class="sxs-lookup"><span data-stu-id="f6d3c-154">Formatting comments</span></span>

<span data-ttu-id="f6d3c-155">Geralmente, prefira vários comentários de barra dupla sobre comentários de bloco no estilo ML.</span><span class="sxs-lookup"><span data-stu-id="f6d3c-155">Generally prefer multiple double-slash comments over ML-style block comments.</span></span>

```fsharp
// Prefer this style of comments when you want
// to express written ideas on multiple lines.

(*
    ML-style comments are fine, but not a .NET-ism.
    They are useful when needing to modify multi-line comments, though.
*)
```

<span data-ttu-id="f6d3c-156">Os comentários embutidos devem colocar a primeira letra em maiúscula.</span><span class="sxs-lookup"><span data-stu-id="f6d3c-156">Inline comments should capitalize the first letter.</span></span>

```fsharp
let f x = x + 1 // Increment by one.
```

## <a name="naming-conventions"></a><span data-ttu-id="f6d3c-157">Convenções de nomenclatura</span><span class="sxs-lookup"><span data-stu-id="f6d3c-157">Naming conventions</span></span>

### <a name="use-camelcase-for-class-bound-expression-bound-and-pattern-bound-values-and-functions"></a><span data-ttu-id="f6d3c-158">Usar camelCase para valores e funções associados à classe, com limite de expressão e de padrão</span><span class="sxs-lookup"><span data-stu-id="f6d3c-158">Use camelCase for class-bound, expression-bound and pattern-bound values and functions</span></span>

<span data-ttu-id="f6d3c-159">É comum e o estilo F# aceito para usar CamelCase para todos os nomes associados como variáveis locais ou em correspondências de padrão e definições de função.</span><span class="sxs-lookup"><span data-stu-id="f6d3c-159">It is common and accepted F# style to use camelCase for all names bound as local variables or in pattern matches and function definitions.</span></span>

```fsharp
// OK
let addIAndJ i j = i + j

// Bad
let addIAndJ I J = I+J

// Bad
let AddIAndJ i j = i + j
```

<span data-ttu-id="f6d3c-160">Funções associadas localmente em classes também devem usar camelCase.</span><span class="sxs-lookup"><span data-stu-id="f6d3c-160">Locally-bound functions in classes should also use camelCase.</span></span>

```fsharp
type MyClass() =

    let doSomething () =

    let firstResult = ...

    let secondResult = ...

    member x.Result = doSomething()
```

### <a name="use-camelcase-for-module-bound-public-functions"></a><span data-ttu-id="f6d3c-161">Usar camelCase para funções públicas associadas a módulo</span><span class="sxs-lookup"><span data-stu-id="f6d3c-161">Use camelCase for module-bound public functions</span></span>

<span data-ttu-id="f6d3c-162">Quando uma função associada a um módulo faz parte de uma API pública, ela deve usar camelCase:</span><span class="sxs-lookup"><span data-stu-id="f6d3c-162">When a module-bound function is part of a public API, it should use camelCase:</span></span>

```fsharp
module MyAPI =
    let publicFunctionOne param1 param2 param2 = ...

    let publicFunctionTwo param1 param2 param3 = ...
```

### <a name="use-camelcase-for-internal-and-private-module-bound-values-and-functions"></a><span data-ttu-id="f6d3c-163">Usar camelCase para valores e funções associados ao módulo interno e privado</span><span class="sxs-lookup"><span data-stu-id="f6d3c-163">Use camelCase for internal and private module-bound values and functions</span></span>

<span data-ttu-id="f6d3c-164">Use camelCase para valores associados ao módulo privado, incluindo o seguinte:</span><span class="sxs-lookup"><span data-stu-id="f6d3c-164">Use camelCase for private module-bound values, including the following:</span></span>

* <span data-ttu-id="f6d3c-165">Funções ad hoc em scripts</span><span class="sxs-lookup"><span data-stu-id="f6d3c-165">Ad hoc functions in scripts</span></span>

* <span data-ttu-id="f6d3c-166">Valores que constituem a implementação interna de um módulo ou tipo</span><span class="sxs-lookup"><span data-stu-id="f6d3c-166">Values making up the internal implementation of a module or type</span></span>

```fsharp
let emailMyBossTheLatestResults =
    ...
```

### <a name="use-camelcase-for-parameters"></a><span data-ttu-id="f6d3c-167">Usar camelCase para parâmetros</span><span class="sxs-lookup"><span data-stu-id="f6d3c-167">Use camelCase for parameters</span></span>

<span data-ttu-id="f6d3c-168">Todos os parâmetros devem usar camelCase de acordo com as convenções de nomenclatura do .NET.</span><span class="sxs-lookup"><span data-stu-id="f6d3c-168">All parameters should use camelCase in accordance with .NET naming conventions.</span></span>

```fsharp
module MyModule =
    let myFunction paramOne paramTwo = ...

type MyClass() =
    member this.MyMethod(paramOne, paramTwo) = ...
```

### <a name="use-pascalcase-for-modules"></a><span data-ttu-id="f6d3c-169">Usar PascalCase para módulos</span><span class="sxs-lookup"><span data-stu-id="f6d3c-169">Use PascalCase for modules</span></span>

<span data-ttu-id="f6d3c-170">Todos os módulos (nível superior, interno, privado, aninhado) devem usar PascalCase.</span><span class="sxs-lookup"><span data-stu-id="f6d3c-170">All modules (top-level, internal, private, nested) should use PascalCase.</span></span>

```fsharp
module MyTopLevelModule

module Helpers =
    module private SuperHelpers =
        ...

    ...
```

### <a name="use-pascalcase-for-type-declarations-members-and-labels"></a><span data-ttu-id="f6d3c-171">Usar PascalCase para declarações de tipo, membros e rótulos</span><span class="sxs-lookup"><span data-stu-id="f6d3c-171">Use PascalCase for type declarations, members, and labels</span></span>

<span data-ttu-id="f6d3c-172">Classes, interfaces, structs, enumerações, delegados, registros e uniões discriminadas devem ser nomeadas com PascalCase.</span><span class="sxs-lookup"><span data-stu-id="f6d3c-172">Classes, interfaces, structs, enumerations, delegates, records, and discriminated unions should all be named with PascalCase.</span></span> <span data-ttu-id="f6d3c-173">Membros dentro de tipos e rótulos para registros e uniões discriminadas também devem usar PascalCase.</span><span class="sxs-lookup"><span data-stu-id="f6d3c-173">Members within types and labels for records and discriminated unions should also use PascalCase.</span></span>

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

### <a name="use-pascalcase-for-constructs-intrinsic-to-net"></a><span data-ttu-id="f6d3c-174">Usar PascalCase para construções intrínsecas ao .NET</span><span class="sxs-lookup"><span data-stu-id="f6d3c-174">Use PascalCase for constructs intrinsic to .NET</span></span>

<span data-ttu-id="f6d3c-175">Namespaces, exceções, eventos e nomes de projeto/`.dll` também devem usar PascalCase.</span><span class="sxs-lookup"><span data-stu-id="f6d3c-175">Namespaces, exceptions, events, and project/`.dll` names should also use PascalCase.</span></span> <span data-ttu-id="f6d3c-176">Isso não apenas faz com que o consumo de outras linguagens .NET pareça mais natural para os consumidores, também é consistente com as convenções de nomenclatura do .NET que você provavelmente encontrará.</span><span class="sxs-lookup"><span data-stu-id="f6d3c-176">Not only does this make consumption from other .NET languages feel more natural to consumers, it's also consistent with .NET naming conventions that you are likely to encounter.</span></span>

### <a name="avoid-underscores-in-names"></a><span data-ttu-id="f6d3c-177">Evitar sublinhados em nomes</span><span class="sxs-lookup"><span data-stu-id="f6d3c-177">Avoid underscores in names</span></span>

<span data-ttu-id="f6d3c-178">Historicamente, algumas F# bibliotecas usaram sublinhados em nomes.</span><span class="sxs-lookup"><span data-stu-id="f6d3c-178">Historically, some F# libraries have used underscores in names.</span></span> <span data-ttu-id="f6d3c-179">No entanto, isso não é mais amplamente aceito, parcialmente porque ele conflita com as convenções de nomenclatura do .NET.</span><span class="sxs-lookup"><span data-stu-id="f6d3c-179">However, this is no longer widely accepted, partly because it clashes with .NET naming conventions.</span></span> <span data-ttu-id="f6d3c-180">Dito isso, alguns F# programadores usam muito sublinhados, parcialmente por razões históricas, e a tolerância e o respeito são importantes.</span><span class="sxs-lookup"><span data-stu-id="f6d3c-180">That said, some F# programmers use underscores heavily, partly for historical reasons, and tolerance and respect is important.</span></span> <span data-ttu-id="f6d3c-181">No entanto, lembre-se de que o estilo geralmente é desgosto por outros que têm a opção de usá-lo.</span><span class="sxs-lookup"><span data-stu-id="f6d3c-181">However, be aware that the style is often disliked by others who have a choice about whether to use it.</span></span>

<span data-ttu-id="f6d3c-182">Algumas exceções incluem a interoperação com componentes nativos, em que sublinhados são muito comuns.</span><span class="sxs-lookup"><span data-stu-id="f6d3c-182">Some exceptions includes interoperating with native components, where underscores are very common.</span></span>

### <a name="use-standard-f-operators"></a><span data-ttu-id="f6d3c-183">Usar operadores F# padrão</span><span class="sxs-lookup"><span data-stu-id="f6d3c-183">Use standard F# operators</span></span>

<span data-ttu-id="f6d3c-184">Os operadores a seguir são definidos na F# biblioteca padrão e devem ser usados em vez de definir equivalentes.</span><span class="sxs-lookup"><span data-stu-id="f6d3c-184">The following operators are defined in the F# standard library and should be used instead of defining equivalents.</span></span> <span data-ttu-id="f6d3c-185">O uso desses operadores é recomendado, pois tende a tornar o código mais legível e idiomática.</span><span class="sxs-lookup"><span data-stu-id="f6d3c-185">Using these operators is recommended as it tends to make code more readable and idiomatic.</span></span> <span data-ttu-id="f6d3c-186">Os desenvolvedores com uma experiência em OCaml ou outra linguagem de programação funcional podem estar acostumados a linguagens diferentes.</span><span class="sxs-lookup"><span data-stu-id="f6d3c-186">Developers with a background in OCaml or other functional programming language may be accustomed to different idioms.</span></span> <span data-ttu-id="f6d3c-187">A lista a seguir resume os operadores F# recomendados.</span><span class="sxs-lookup"><span data-stu-id="f6d3c-187">The following list summarizes the recommended F# operators.</span></span>

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

### <a name="use-prefix-syntax-for-generics-foot-in-preference-to-postfix-syntax-t-foo"></a><span data-ttu-id="f6d3c-188">Usar sintaxe de prefixo para genéricos (`Foo<T>`) em preferência à sintaxe de sufixo (`T Foo`)</span><span class="sxs-lookup"><span data-stu-id="f6d3c-188">Use prefix syntax for generics (`Foo<T>`) in preference to postfix syntax (`T Foo`)</span></span>

<span data-ttu-id="f6d3c-189">F#herda o estilo de ML do sufixo de nomenclatura de tipos genéricos (por exemplo, `int list`), bem como o estilo de prefixo do .NET (por exemplo, `list<int>`).</span><span class="sxs-lookup"><span data-stu-id="f6d3c-189">F# inherits both the postfix ML style of naming generic types (for example, `int list`) as well as the prefix .NET style (for example, `list<int>`).</span></span> <span data-ttu-id="f6d3c-190">Prefira o estilo .NET, exceto para cinco tipos específicos:</span><span class="sxs-lookup"><span data-stu-id="f6d3c-190">Prefer the .NET style, except for five specific types:</span></span>

1. <span data-ttu-id="f6d3c-191">Para F# listas, use o formulário de sufixo: `int list` em vez de `list<int>`.</span><span class="sxs-lookup"><span data-stu-id="f6d3c-191">For F# Lists, use the postfix form: `int list` rather than `list<int>`.</span></span>
2. <span data-ttu-id="f6d3c-192">Para F# opções, use o formulário de sufixo: `int option` em vez de `option<int>`.</span><span class="sxs-lookup"><span data-stu-id="f6d3c-192">For F# Options, use the postfix form: `int option` rather than `option<int>`.</span></span>
3. <span data-ttu-id="f6d3c-193">Para F# opções de valor, use o formulário de sufixo: `int voption` em vez de `voption<int>`.</span><span class="sxs-lookup"><span data-stu-id="f6d3c-193">For F# Value Options, use the postfix form: `int voption` rather than `voption<int>`.</span></span>
4. <span data-ttu-id="f6d3c-194">Para F# matrizes, use o nome sintático `int[]` em vez de `int array` ou `array<int>`.</span><span class="sxs-lookup"><span data-stu-id="f6d3c-194">For F# arrays, use the syntactic name `int[]` rather than `int array` or `array<int>`.</span></span>
5. <span data-ttu-id="f6d3c-195">Para células de referência, use `int ref` em vez de `ref<int>` ou `Ref<int>`.</span><span class="sxs-lookup"><span data-stu-id="f6d3c-195">For Reference Cells, use `int ref` rather than `ref<int>` or `Ref<int>`.</span></span>

<span data-ttu-id="f6d3c-196">Para todos os outros tipos, use o formulário de prefixo.</span><span class="sxs-lookup"><span data-stu-id="f6d3c-196">For all other types, use the prefix form.</span></span>

## <a name="formatting-tuples"></a><span data-ttu-id="f6d3c-197">Formatando tuplas</span><span class="sxs-lookup"><span data-stu-id="f6d3c-197">Formatting tuples</span></span>

<span data-ttu-id="f6d3c-198">Uma instanciação de tupla deve estar entre parênteses e as vírgulas de delimitação dentro devem ser seguidas por um único espaço, por exemplo: `(1, 2)``(x, y, z)`.</span><span class="sxs-lookup"><span data-stu-id="f6d3c-198">A tuple instantiation should be parenthesized, and the delimiting commas within should be followed by a single space, for example: `(1, 2)`, `(x, y, z)`.</span></span>

<span data-ttu-id="f6d3c-199">Normalmente, é aceito para omitir parênteses em correspondência de padrões de tuplas:</span><span class="sxs-lookup"><span data-stu-id="f6d3c-199">It is commonly accepted to omit parentheses in pattern matching of tuples:</span></span>

```fsharp
let (x, y) = z // Destructuring
let x, y = z // OK

// OK
match x, y with
| 1, _ -> 0
| x, 1 -> 0
| x, y -> 1
```

<span data-ttu-id="f6d3c-200">Ele também é aceito para omitir parênteses se a tupla for o valor de retorno de uma função:</span><span class="sxs-lookup"><span data-stu-id="f6d3c-200">It is also commonly accepted to omit parentheses if the tuple is the return value of a function:</span></span>

```fsharp
// OK
let update model msg =
    match msg with
    | 1 -> model + 1, []
    | _ -> model, [ msg ]
```

<span data-ttu-id="f6d3c-201">Em resumo, prefira instanciações de tupla entre parênteses, mas ao usar tuplas para correspondência de padrões ou um valor de retorno, ele é considerado bem para evitar parênteses.</span><span class="sxs-lookup"><span data-stu-id="f6d3c-201">In summary, prefer parenthesized tuple instantiations, but when using tuples for pattern matching or a return value, it is considered fine to avoid parentheses.</span></span>

## <a name="formatting-discriminated-union-declarations"></a><span data-ttu-id="f6d3c-202">Formatando declarações de União discriminadas</span><span class="sxs-lookup"><span data-stu-id="f6d3c-202">Formatting discriminated union declarations</span></span>

<span data-ttu-id="f6d3c-203">Recuar `|` na definição de tipo por 4 espaços:</span><span class="sxs-lookup"><span data-stu-id="f6d3c-203">Indent `|` in type definition by 4 spaces:</span></span>

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

## <a name="formatting-discriminated-unions"></a><span data-ttu-id="f6d3c-204">Formatando uniões discriminadas</span><span class="sxs-lookup"><span data-stu-id="f6d3c-204">Formatting discriminated unions</span></span>

<span data-ttu-id="f6d3c-205">As uniões com instâncias discriminadas que se dividem em várias linhas devem dar aos dados contidos um novo escopo com recuo:</span><span class="sxs-lookup"><span data-stu-id="f6d3c-205">Instantiated Discriminated Unions that split across multiple lines should give contained data a new scope with indentation:</span></span>

```fsharp
let tree1 =
    BinaryNode
        (BinaryNode(BinaryValue 1, BinaryValue 2),
         BinaryNode(BinaryValue 3, BinaryValue 4))
```

<span data-ttu-id="f6d3c-206">O parêntese de fechamento também pode estar em uma nova linha:</span><span class="sxs-lookup"><span data-stu-id="f6d3c-206">The closing parenthesis can also be on a new line:</span></span>

```fsharp
let tree1 =
    BinaryNode(
        BinaryNode(BinaryValue 1, BinaryValue 2),
        BinaryNode(BinaryValue 3, BinaryValue 4)
    )
```

## <a name="formatting-record-declarations"></a><span data-ttu-id="f6d3c-207">Formatando declarações de registro</span><span class="sxs-lookup"><span data-stu-id="f6d3c-207">Formatting record declarations</span></span>

<span data-ttu-id="f6d3c-208">Recue `{` na definição de tipo por 4 espaços e inicie a lista de campos na mesma linha:</span><span class="sxs-lookup"><span data-stu-id="f6d3c-208">Indent `{` in type definition by 4 spaces and start the field list on the same line:</span></span>

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

<span data-ttu-id="f6d3c-209">Colocar o token de abertura em uma nova linha e o token de fechamento em uma nova linha é preferível se você estiver declarando implementações de interface ou membros no registro:</span><span class="sxs-lookup"><span data-stu-id="f6d3c-209">Placing the opening token on a new line and the closing token on a new line is preferable if you are declaring interface implementations or members on the record:</span></span>

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

## <a name="formatting-records"></a><span data-ttu-id="f6d3c-210">Formatando registros</span><span class="sxs-lookup"><span data-stu-id="f6d3c-210">Formatting records</span></span>

<span data-ttu-id="f6d3c-211">Registros curtos podem ser gravados em uma linha:</span><span class="sxs-lookup"><span data-stu-id="f6d3c-211">Short records can be written in one line:</span></span>

```fsharp
let point = { X = 1.0; Y = 0.0 }
```

<span data-ttu-id="f6d3c-212">Os registros que são mais longos devem usar linhas novas para rótulos:</span><span class="sxs-lookup"><span data-stu-id="f6d3c-212">Records that are longer should use new lines for labels:</span></span>

```fsharp
let rainbow =
    { Boss = "Jeffrey"
      Lackeys = ["Zippy"; "George"; "Bungle"] }
```

<span data-ttu-id="f6d3c-213">Colocar o token de abertura em uma nova linha, o conteúdo tabulado em um escopo e o token de fechamento em uma nova linha será preferível se você:</span><span class="sxs-lookup"><span data-stu-id="f6d3c-213">Placing the opening token on a new line, the contents tabbed over one scope, and the closing token on a new line is preferable if you are:</span></span>

* <span data-ttu-id="f6d3c-214">Movendo registros em código com escopos de recuo diferentes</span><span class="sxs-lookup"><span data-stu-id="f6d3c-214">Moving records around in code with different indentation scopes</span></span>
* <span data-ttu-id="f6d3c-215">Canalizando-os para uma função</span><span class="sxs-lookup"><span data-stu-id="f6d3c-215">Piping them into a function</span></span>

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

<span data-ttu-id="f6d3c-216">As mesmas regras se aplicam a elementos de lista e matriz.</span><span class="sxs-lookup"><span data-stu-id="f6d3c-216">The same rules apply for list and array elements.</span></span>

## <a name="formatting-copy-and-update-record-expressions"></a><span data-ttu-id="f6d3c-217">Formatando expressões de registro de copiar e atualizar</span><span class="sxs-lookup"><span data-stu-id="f6d3c-217">Formatting copy-and-update record expressions</span></span>

<span data-ttu-id="f6d3c-218">Uma expressão de registro Copy-and-Update ainda é um registro, portanto, diretrizes semelhantes se aplicam.</span><span class="sxs-lookup"><span data-stu-id="f6d3c-218">A copy-and-update record expression is still a record, so similar guidelines apply.</span></span>

<span data-ttu-id="f6d3c-219">As expressões curtas podem caber em uma linha:</span><span class="sxs-lookup"><span data-stu-id="f6d3c-219">Short expressions can fit on one line:</span></span>

```fsharp
let point2 = { point with X = 1; Y = 2 }
```

<span data-ttu-id="f6d3c-220">As expressões mais longas devem usar novas linhas:</span><span class="sxs-lookup"><span data-stu-id="f6d3c-220">Longer expressions should use new lines:</span></span>

```fsharp
let rainbow2 =
    { rainbow with
        Boss = "Jeffrey"
        Lackeys = ["Zippy"; "George"; "Bungle"] }
```

<span data-ttu-id="f6d3c-221">E, assim como nas diretrizes de registro, talvez você queira dedicar linhas separadas para as chaves e recuar um escopo para a direita com a expressão.</span><span class="sxs-lookup"><span data-stu-id="f6d3c-221">And as with the record guidance, you may want to dedicate separate lines for the braces and indent one scope to the right with the expression.</span></span> <span data-ttu-id="f6d3c-222">Observe que em alguns casos especiais, como encapsular um valor com um opcional sem parênteses, talvez seja necessário manter uma chave em uma linha:</span><span class="sxs-lookup"><span data-stu-id="f6d3c-222">Note that in some special cases, such as wrapping a value with an optional without parentheses, you may need to keep a brace on one line:</span></span>

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

## <a name="formatting-lists-and-arrays"></a><span data-ttu-id="f6d3c-223">Formatando listas e matrizes</span><span class="sxs-lookup"><span data-stu-id="f6d3c-223">Formatting lists and arrays</span></span>

<span data-ttu-id="f6d3c-224">Escreva `x :: l` com espaços em volta do operador de `::` (`::` é um operador infixo, portanto, rodeado por espaços).</span><span class="sxs-lookup"><span data-stu-id="f6d3c-224">Write `x :: l` with spaces around the `::` operator (`::` is an infix operator, hence surrounded by spaces).</span></span>

<span data-ttu-id="f6d3c-225">Lista e matrizes declaradas em uma única linha devem ter um espaço após o colchete de abertura e antes do colchete de fechamento:</span><span class="sxs-lookup"><span data-stu-id="f6d3c-225">List and arrays declared on a single line should have a space after the opening bracket and before the closing bracket:</span></span>

```fsharp
let xs = [ 1; 2; 3 ]
let ys = [| 1; 2; 3; |]
```

<span data-ttu-id="f6d3c-226">Sempre use pelo menos um espaço entre dois operadores de chaves distintas.</span><span class="sxs-lookup"><span data-stu-id="f6d3c-226">Always use at least one space between two distinct brace-like operators.</span></span> <span data-ttu-id="f6d3c-227">Por exemplo, deixe um espaço entre um `[` e um `{`.</span><span class="sxs-lookup"><span data-stu-id="f6d3c-227">For example, leave a space between a `[` and a `{`.</span></span>

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

<span data-ttu-id="f6d3c-228">A mesma diretriz se aplica a listas ou matrizes de tuplas.</span><span class="sxs-lookup"><span data-stu-id="f6d3c-228">The same guideline applies for lists or arrays of tuples.</span></span>

<span data-ttu-id="f6d3c-229">Listas e matrizes que dividem em várias linhas seguem uma regra semelhante à medida que os registros fazem:</span><span class="sxs-lookup"><span data-stu-id="f6d3c-229">Lists and arrays that split across multiple lines follow a similar rule as records do:</span></span>

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

<span data-ttu-id="f6d3c-230">E, assim como acontece com os registros, a declaração dos colchetes de abertura e fechamento em sua própria linha fará com que a movimentação de código e a tubulação em funções sejam mais fáceis.</span><span class="sxs-lookup"><span data-stu-id="f6d3c-230">And as with records, declaring the opening and closing brackets on their own line will make moving code around and piping into functions easier.</span></span>

<span data-ttu-id="f6d3c-231">Ao gerar matrizes e listas programaticamente, prefira `->` sobre `do ... yield` quando um valor é sempre gerado:</span><span class="sxs-lookup"><span data-stu-id="f6d3c-231">When generating arrays and lists programmatically, prefer `->` over `do ... yield` when a value is always generated:</span></span>

```fsharp
// Preferred
let squares = [ for x in 1..10 -> x*x ]

// Not preferred
let squares' = [ for x in 1..10 do yield x*x ]
```

<span data-ttu-id="f6d3c-232">Versões mais antigas do F# idioma exigiam a especificação de `yield` em situações em que os dados podem ser gerados condicionalmente ou pode haver expressões consecutivas a serem avaliadas.</span><span class="sxs-lookup"><span data-stu-id="f6d3c-232">Older versions of the F# language required specifying `yield` in situations where data may be generated conditionally, or there may be consecutive expressions to be evaluated.</span></span> <span data-ttu-id="f6d3c-233">Prefira omitir essas palavras-chave `yield`, a menos que você precise compilar F# com uma versão de idioma mais antiga:</span><span class="sxs-lookup"><span data-stu-id="f6d3c-233">Prefer omitting these `yield` keywords unless you must compile with an older F# language version:</span></span>

```fsharp
// Preferred
let daysOfWeek includeWeekend =
    [
        "Monday"
        "Tuesday"
        "Wednesday"
        "Thursday"
        "Friday"
        if includeWeekend then
            "Saturday"
            "Sunday"
    ]

// Not preferred
let daysOfWeek' includeWeekend =
    [
        yield "Monday"
        yield "Tuesday"
        yield "Wednesday"
        yield "Thursday"
        yield "Friday"
        if includeWeekend then
            yield "Saturday"
            yield "Sunday"
    ]
```

<span data-ttu-id="f6d3c-234">Em alguns casos, `do...yield` pode ajudar na legibilidade.</span><span class="sxs-lookup"><span data-stu-id="f6d3c-234">In some cases, `do...yield` may aid in readability.</span></span> <span data-ttu-id="f6d3c-235">Esses casos, embora subjetivo, devem ser levados em consideração.</span><span class="sxs-lookup"><span data-stu-id="f6d3c-235">These cases, though subjective, should be taken into consideration.</span></span>

## <a name="formatting-if-expressions"></a><span data-ttu-id="f6d3c-236">Formatando expressões If</span><span class="sxs-lookup"><span data-stu-id="f6d3c-236">Formatting if expressions</span></span>

<span data-ttu-id="f6d3c-237">O recuo de condicionais depende dos tamanhos das expressões que as compõem.</span><span class="sxs-lookup"><span data-stu-id="f6d3c-237">Indentation of conditionals depends on the sizes of the expressions that make them up.</span></span> <span data-ttu-id="f6d3c-238">Se `cond`, `e1` e `e2` são curtos, basta escrevê-los em uma linha:</span><span class="sxs-lookup"><span data-stu-id="f6d3c-238">If `cond`, `e1` and `e2` are short, simply write them on one line:</span></span>

```fsharp
if cond then e1 else e2
```

<span data-ttu-id="f6d3c-239">Se `cond`, `e1` ou `e2` serão maiores, mas não várias linhas:</span><span class="sxs-lookup"><span data-stu-id="f6d3c-239">If either `cond`, `e1` or `e2` are longer, but not multi-line:</span></span>

```fsharp
if cond
then e1
else e2
```

<span data-ttu-id="f6d3c-240">Se qualquer uma das expressões for de várias linhas:</span><span class="sxs-lookup"><span data-stu-id="f6d3c-240">If any of the expressions are multi-line:</span></span>

```fsharp
if cond then
    e1
else
    e2
```

<span data-ttu-id="f6d3c-241">Várias condicionais com `elif` e `else` são recuadas no mesmo escopo que o `if`:</span><span class="sxs-lookup"><span data-stu-id="f6d3c-241">Multiple conditionals with `elif` and `else` are indented at the same scope as the `if`:</span></span>

```fsharp
if cond1 then e1
elif cond2 then e2
elif cond3 then e3
else e4
```

### <a name="pattern-matching-constructs"></a><span data-ttu-id="f6d3c-242">Constructos de correspondência de padrões</span><span class="sxs-lookup"><span data-stu-id="f6d3c-242">Pattern matching constructs</span></span>

<span data-ttu-id="f6d3c-243">Use um `|` para cada cláusula de uma correspondência sem recuo.</span><span class="sxs-lookup"><span data-stu-id="f6d3c-243">Use a `|` for each clause of a match with no indentation.</span></span> <span data-ttu-id="f6d3c-244">Se a expressão for curta, você poderá considerar o uso de uma única linha se cada subexpressão também for simples.</span><span class="sxs-lookup"><span data-stu-id="f6d3c-244">If the expression is short, you can consider using a single line if each subexpression is also simple.</span></span>

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

<span data-ttu-id="f6d3c-245">Se a expressão à direita da seta de correspondência de padrões for muito grande, mova-a para a linha a seguir, recuada uma etapa da `match`/`|`.</span><span class="sxs-lookup"><span data-stu-id="f6d3c-245">If the expression on the right of the pattern matching arrow is too large, move it to the following line, indented one step from the `match`/`|`.</span></span>

```fsharp
match lam with
| Var v -> 1
| Abs(x, body) ->
    1 + sizeLambda body
| App(lam1, lam2) ->
    sizeLambda lam1 + sizeLambda lam2

```

<span data-ttu-id="f6d3c-246">A correspondência de padrões de funções anônimas, começando pelo `function`, geralmente não deve ser recuada muito longe.</span><span class="sxs-lookup"><span data-stu-id="f6d3c-246">Pattern matching of anonymous functions, starting by `function`, should generally not indent too far.</span></span> <span data-ttu-id="f6d3c-247">Por exemplo, o recuo de um escopo da seguinte maneira é bom:</span><span class="sxs-lookup"><span data-stu-id="f6d3c-247">For example, indenting one scope as follows is fine:</span></span>

```fsharp
lambdaList
|> List.map (function
    | Abs(x, body) -> 1 + sizeLambda 0 body
    | App(lam1, lam2) -> sizeLambda (sizeLambda 0 lam1) lam2
    | Var v -> 1)
```

<span data-ttu-id="f6d3c-248">A correspondência de padrões nas funções definidas por `let` ou `let rec` deve ser recuada 4 espaços após o início de `let`, mesmo se `function` palavra-chave for usada:</span><span class="sxs-lookup"><span data-stu-id="f6d3c-248">Pattern matching in functions defined by `let` or `let rec` should be indented 4 spaces after starting of `let`, even if `function` keyword is used:</span></span>

```fsharp
let rec sizeLambda acc = function
    | Abs(x, body) -> sizeLambda (succ acc) body
    | App(lam1, lam2) -> sizeLambda (sizeLambda acc lam1) lam2
    | Var v -> succ acc
```

<span data-ttu-id="f6d3c-249">Não recomendamos o alinhamento de setas.</span><span class="sxs-lookup"><span data-stu-id="f6d3c-249">We do not recommend aligning arrows.</span></span>

## <a name="formatting-trywith-expressions"></a><span data-ttu-id="f6d3c-250">Formatando expressões try/com</span><span class="sxs-lookup"><span data-stu-id="f6d3c-250">Formatting try/with expressions</span></span>

<span data-ttu-id="f6d3c-251">A correspondência de padrões no tipo de exceção deve ser recuada no mesmo nível que `with`.</span><span class="sxs-lookup"><span data-stu-id="f6d3c-251">Pattern matching on the exception type should be indented at the same level as `with`.</span></span>

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

## <a name="formatting-function-parameter-application"></a><span data-ttu-id="f6d3c-252">Formatando o aplicativo de parâmetros de função</span><span class="sxs-lookup"><span data-stu-id="f6d3c-252">Formatting function parameter application</span></span>

<span data-ttu-id="f6d3c-253">Em geral, a maioria dos aplicativos de parâmetro de função é feita na mesma linha.</span><span class="sxs-lookup"><span data-stu-id="f6d3c-253">In general, most function parameter application is done on the same line.</span></span>

<span data-ttu-id="f6d3c-254">Se você quiser aplicar parâmetros a uma função em uma nova linha, recue-os por um escopo.</span><span class="sxs-lookup"><span data-stu-id="f6d3c-254">If you wish to apply parameters to a function on a new line, indent them by one scope.</span></span>

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

<span data-ttu-id="f6d3c-255">As mesmas diretrizes se aplicam a expressões lambda como argumentos de função.</span><span class="sxs-lookup"><span data-stu-id="f6d3c-255">The same guidelines apply for lambda expressions as function arguments.</span></span> <span data-ttu-id="f6d3c-256">Se o corpo de uma expressão lambda, o corpo pode ter outra linha, recuada por um escopo</span><span class="sxs-lookup"><span data-stu-id="f6d3c-256">If the body of a lambda expression, the body can have another line, indented by one scope</span></span>

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

<span data-ttu-id="f6d3c-257">No entanto, se o corpo de uma expressão lambda for maior que uma linha, considere a possibilidade de separá-la em uma função separada em vez de ter uma construção de várias linhas aplicada como um único argumento a uma função.</span><span class="sxs-lookup"><span data-stu-id="f6d3c-257">However, if the body of a lambda expression is more than one line, consider factoring it out into a separate function rather than have a multi-line construct applied as a single argument to a function.</span></span>

### <a name="formatting-infix-operators"></a><span data-ttu-id="f6d3c-258">Formatando operadores infixos</span><span class="sxs-lookup"><span data-stu-id="f6d3c-258">Formatting infix operators</span></span>

<span data-ttu-id="f6d3c-259">Separe os operadores por espaços.</span><span class="sxs-lookup"><span data-stu-id="f6d3c-259">Separate operators by spaces.</span></span> <span data-ttu-id="f6d3c-260">As exceções óbvias a essa regra são os operadores `!` e `.`.</span><span class="sxs-lookup"><span data-stu-id="f6d3c-260">Obvious exceptions to this rule are the `!` and `.` operators.</span></span>

<span data-ttu-id="f6d3c-261">As expressões de infixos estão OK para serem organizadas na mesma coluna:</span><span class="sxs-lookup"><span data-stu-id="f6d3c-261">Infix expressions are OK to lineup on same column:</span></span>

```fsharp
acc +
(sprintf "\t%s - %i\n\r"
     x.IngredientName x.Quantity)

let function1 arg1 arg2 arg3 arg4 =
    arg1 + arg2 +
    arg3 + arg4
```

### <a name="formatting-pipeline-operators"></a><span data-ttu-id="f6d3c-262">Formatando operadores de pipeline</span><span class="sxs-lookup"><span data-stu-id="f6d3c-262">Formatting pipeline operators</span></span>

<span data-ttu-id="f6d3c-263">Os operadores de `|>` de pipeline devem ficar abaixo das expressões em que operam.</span><span class="sxs-lookup"><span data-stu-id="f6d3c-263">Pipeline `|>` operators should go underneath the expressions they operate on.</span></span>

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

### <a name="formatting-modules"></a><span data-ttu-id="f6d3c-264">Módulos de formatação</span><span class="sxs-lookup"><span data-stu-id="f6d3c-264">Formatting modules</span></span>

<span data-ttu-id="f6d3c-265">O código em um módulo local deve ser recuado em relação ao módulo, mas o código em um módulo de nível superior não deve ser recuado.</span><span class="sxs-lookup"><span data-stu-id="f6d3c-265">Code in a local module must be indented relative to the module, but code in a top-level module should not be indented.</span></span> <span data-ttu-id="f6d3c-266">Os elementos do namespace não precisam ser recuados.</span><span class="sxs-lookup"><span data-stu-id="f6d3c-266">Namespace elements do not have to be indented.</span></span>

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

### <a name="formatting-object-expressions-and-interfaces"></a><span data-ttu-id="f6d3c-267">Formatando expressões e interfaces de objeto</span><span class="sxs-lookup"><span data-stu-id="f6d3c-267">Formatting object expressions and interfaces</span></span>

<span data-ttu-id="f6d3c-268">As expressões e as interfaces de objeto devem ser alinhadas da mesma maneira com `member` sendo recuadas após 4 espaços.</span><span class="sxs-lookup"><span data-stu-id="f6d3c-268">Object expressions and interfaces should be aligned in the same way with `member` being indented after 4 spaces.</span></span>

```fsharp
let comparer =
    { new IComparer<string> with
          member x.Compare(s1, s2) =
              let rev (s: String) =
                  new String (Array.rev (s.ToCharArray()))
              let reversed = rev s1
              reversed.CompareTo (rev s2) }
```

### <a name="formatting-white-space-in-expressions"></a><span data-ttu-id="f6d3c-269">Formatando espaço em branco em expressões</span><span class="sxs-lookup"><span data-stu-id="f6d3c-269">Formatting white space in expressions</span></span>

<span data-ttu-id="f6d3c-270">Evite espaços em branco incorretos em F# expressões.</span><span class="sxs-lookup"><span data-stu-id="f6d3c-270">Avoid extraneous white space in F# expressions.</span></span>

```fsharp
// OK
spam (ham.[1])

// Not OK
spam ( ham.[ 1 ] )
```

<span data-ttu-id="f6d3c-271">Os argumentos nomeados também não devem ter espaço em torno da `=`:</span><span class="sxs-lookup"><span data-stu-id="f6d3c-271">Named arguments should also not have space surrounding the `=`:</span></span>

```fsharp
// OK
let makeStreamReader x = new System.IO.StreamReader(path=x)

// Not OK
let makeStreamReader x = new System.IO.StreamReader(path = x)
```

## <a name="formatting-attributes"></a><span data-ttu-id="f6d3c-272">Atributos de formatação</span><span class="sxs-lookup"><span data-stu-id="f6d3c-272">Formatting attributes</span></span>

<span data-ttu-id="f6d3c-273">Os [atributos](../language-reference/attributes.md) são colocados acima de um constructo:</span><span class="sxs-lookup"><span data-stu-id="f6d3c-273">[Attributes](../language-reference/attributes.md) are placed above a construct:</span></span>

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

### <a name="formatting-attributes-on-parameters"></a><span data-ttu-id="f6d3c-274">Formatando atributos em parâmetros</span><span class="sxs-lookup"><span data-stu-id="f6d3c-274">Formatting attributes on parameters</span></span>

<span data-ttu-id="f6d3c-275">Os atributos também podem ser locais em parâmetros.</span><span class="sxs-lookup"><span data-stu-id="f6d3c-275">Attributes can also be places on parameters.</span></span> <span data-ttu-id="f6d3c-276">Nesse caso, coloque na mesma linha que o parâmetro e antes do nome:</span><span class="sxs-lookup"><span data-stu-id="f6d3c-276">In this case, place then on the same line as the parameter and before the name:</span></span>

```fsharp
// Defines a class that takes an optional value as input defaulting to false.
type C() =
    member _.M([<Optional; DefaultParameterValue(false)>] doSomething: bool)
```

### <a name="formatting-multiple-attributes"></a><span data-ttu-id="f6d3c-277">Formatando vários atributos</span><span class="sxs-lookup"><span data-stu-id="f6d3c-277">Formatting multiple attributes</span></span>

<span data-ttu-id="f6d3c-278">Quando vários atributos são aplicados a uma construção que não é um parâmetro, eles devem ser colocados de forma que haja um atributo por linha:</span><span class="sxs-lookup"><span data-stu-id="f6d3c-278">When multiple attributes are applied to a construct that is not a parameter, they should be placed such that there is one attribute per line:</span></span>

```fsharp
[<Struct>]
[<IsByRefLike>]
type MyRecord =
    { Label1: int
      Label2: string }
```

<span data-ttu-id="f6d3c-279">Quando aplicado a um parâmetro, eles devem estar na mesma linha e separados por um separador de `;`.</span><span class="sxs-lookup"><span data-stu-id="f6d3c-279">When applied to a parameter, they must be on the same line and separated by a `;` separator.</span></span>

## <a name="formatting-literals"></a><span data-ttu-id="f6d3c-280">Literais de formatação</span><span class="sxs-lookup"><span data-stu-id="f6d3c-280">Formatting literals</span></span>

<span data-ttu-id="f6d3c-281">os literais que usam o atributo `Literal` devem posicionar o atributo em sua própria linha e usar a nomenclatura PascalCase: [ F# ](../language-reference/literals.md)</span><span class="sxs-lookup"><span data-stu-id="f6d3c-281">[F# literals](../language-reference/literals.md) using the `Literal` attribute should place the attribute on its own line and use PascalCase naming:</span></span>

```fsharp
[<Literal>]
let Path = __SOURCE_DIRECTORY__ + "/" + __SOURCE_FILE__

[<Literal>]
let MyUrl = "www.mywebsitethatiamworkingwith.com"
```

<span data-ttu-id="f6d3c-282">Evite colocar o atributo na mesma linha que o valor.</span><span class="sxs-lookup"><span data-stu-id="f6d3c-282">Avoid placing the attribute on the same line as the value.</span></span>
