---
title: Diretrizes de formatação de código do F#
description: Aprenda as diretrizes para formatar o código F# .
ms.date: 11/04/2019
ms.openlocfilehash: 2086b515b8ec9b69a44e2e65ca06fb320670dff2
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81278932"
---
# <a name="f-code-formatting-guidelines"></a><span data-ttu-id="49ca9-103">Diretrizes de formatação de código do F#</span><span class="sxs-lookup"><span data-stu-id="49ca9-103">F# code formatting guidelines</span></span>

<span data-ttu-id="49ca9-104">Este artigo oferece diretrizes de como formatar seu código para que seu código F# seja:</span><span class="sxs-lookup"><span data-stu-id="49ca9-104">This article offers guidelines for how to format your code so that your F# code is:</span></span>

* <span data-ttu-id="49ca9-105">Geralmente visto como mais legível</span><span class="sxs-lookup"><span data-stu-id="49ca9-105">Generally viewed as more legible</span></span>
* <span data-ttu-id="49ca9-106">Está de acordo com as convenções aplicadas por ferramentas de formatação no Visual Studio e outros editores</span><span class="sxs-lookup"><span data-stu-id="49ca9-106">Is in accordance with conventions applied by formatting tools in Visual Studio and other editors</span></span>
* <span data-ttu-id="49ca9-107">Semelhante a outro código online</span><span class="sxs-lookup"><span data-stu-id="49ca9-107">Similar to other code online</span></span>

<span data-ttu-id="49ca9-108">Essas diretrizes são baseadas em [um guia abrangente de Convenções de Formatação F#](https://github.com/dungpa/fantomas/blob/master/docs/FormattingConventions.md) por [Anh-Dung Phan](https://github.com/dungpa).</span><span class="sxs-lookup"><span data-stu-id="49ca9-108">These guidelines are based on [A comprehensive guide to F# Formatting Conventions](https://github.com/dungpa/fantomas/blob/master/docs/FormattingConventions.md) by [Anh-Dung Phan](https://github.com/dungpa).</span></span>

## <a name="general-rules-for-indentation"></a><span data-ttu-id="49ca9-109">Regras gerais para recuo</span><span class="sxs-lookup"><span data-stu-id="49ca9-109">General rules for indentation</span></span>

<span data-ttu-id="49ca9-110">F# usa espaço branco significativo por padrão.</span><span class="sxs-lookup"><span data-stu-id="49ca9-110">F# uses significant white space by default.</span></span> <span data-ttu-id="49ca9-111">As seguintes diretrizes destinam-se a orientar sobre como lidar com alguns desafios que isso pode impor.</span><span class="sxs-lookup"><span data-stu-id="49ca9-111">The following guidelines are intended to provide guidance as to how to juggle some challenges this can impose.</span></span>

### <a name="using-spaces"></a><span data-ttu-id="49ca9-112">Usando espaços</span><span class="sxs-lookup"><span data-stu-id="49ca9-112">Using spaces</span></span>

<span data-ttu-id="49ca9-113">Quando o recuo é necessário, você deve usar espaços, não guias.</span><span class="sxs-lookup"><span data-stu-id="49ca9-113">When indentation is required, you must use spaces, not tabs.</span></span> <span data-ttu-id="49ca9-114">Pelo menos um espaço é necessário.</span><span class="sxs-lookup"><span data-stu-id="49ca9-114">At least one space is required.</span></span> <span data-ttu-id="49ca9-115">Sua organização pode criar padrões de codificação para especificar o número de espaços a serem usados para recuo; dois, três ou quatro espaços de recuo em cada nível onde ocorre o recuo é típico.</span><span class="sxs-lookup"><span data-stu-id="49ca9-115">Your organization can create coding standards to specify the number of spaces to use for indentation; two, three or four spaces of indentation at each level where indentation occurs is typical.</span></span>

<span data-ttu-id="49ca9-116">**Recomendamos 4 espaços por recuo.**</span><span class="sxs-lookup"><span data-stu-id="49ca9-116">**We recommend 4 spaces per indentation.**</span></span>

<span data-ttu-id="49ca9-117">Dito isto, o recuo dos programas é uma questão subjetiva.</span><span class="sxs-lookup"><span data-stu-id="49ca9-117">That said, indentation of programs is a subjective matter.</span></span> <span data-ttu-id="49ca9-118">As variações são ok, mas a primeira regra que você deve seguir é *a consistência do recuo*.</span><span class="sxs-lookup"><span data-stu-id="49ca9-118">Variations are OK, but the first rule you should follow is *consistency of indentation*.</span></span> <span data-ttu-id="49ca9-119">Escolha um estilo geralmente aceito de recuo e use-o sistematicamente em toda a sua base de código.</span><span class="sxs-lookup"><span data-stu-id="49ca9-119">Choose a generally accepted style of indentation and use it systematically throughout your codebase.</span></span>

## <a name="formatting-white-space"></a><span data-ttu-id="49ca9-120">Formatação do espaço em branco</span><span class="sxs-lookup"><span data-stu-id="49ca9-120">Formatting white space</span></span>

<span data-ttu-id="49ca9-121">F# é sensível ao espaço branco.</span><span class="sxs-lookup"><span data-stu-id="49ca9-121">F# is white space sensitive.</span></span> <span data-ttu-id="49ca9-122">Embora a maioria das semânticas do espaço branco sejam cobertas por um recuo adequado, há algumas outras coisas a considerar.</span><span class="sxs-lookup"><span data-stu-id="49ca9-122">Although most semantics from white space are covered by proper indentation, there are some other things to consider.</span></span>

### <a name="formatting-operators-in-arithmetic-expressions"></a><span data-ttu-id="49ca9-123">Operadores de formatação em expressões aritméticas</span><span class="sxs-lookup"><span data-stu-id="49ca9-123">Formatting operators in arithmetic expressions</span></span>

<span data-ttu-id="49ca9-124">Use sempre o espaço branco em torno de expressões aritméticas binárias:</span><span class="sxs-lookup"><span data-stu-id="49ca9-124">Always use white space around binary arithmetic expressions:</span></span>

```fsharp
let subtractThenAdd x = x - 1 + 3
```

<span data-ttu-id="49ca9-125">Os `-` operadores unary devem sempre ter o valor que estão negando imediatamente seguir:</span><span class="sxs-lookup"><span data-stu-id="49ca9-125">Unary `-` operators should always have the value they are negating immediately follow:</span></span>

```fsharp
// OK
let negate x = -x

// Bad
let negateBad x = - x
```

<span data-ttu-id="49ca9-126">Adicionar um caractere de `-` espaço branco depois que o operador pode levar a confusão para outros.</span><span class="sxs-lookup"><span data-stu-id="49ca9-126">Adding a white-space character after the `-` operator can lead to confusion for others.</span></span>

<span data-ttu-id="49ca9-127">Em resumo, é importante sempre:</span><span class="sxs-lookup"><span data-stu-id="49ca9-127">In summary, it's important to always:</span></span>

* <span data-ttu-id="49ca9-128">Operadores binários surround com espaço branco</span><span class="sxs-lookup"><span data-stu-id="49ca9-128">Surround binary operators with white space</span></span>
* <span data-ttu-id="49ca9-129">Nunca tenha seguido espaço branco depois de um operador unary</span><span class="sxs-lookup"><span data-stu-id="49ca9-129">Never have trailing white space after a unary operator</span></span>

<span data-ttu-id="49ca9-130">A diretriz do operador aritmético binário é especialmente importante.</span><span class="sxs-lookup"><span data-stu-id="49ca9-130">The binary arithmetic operator guideline is especially important.</span></span> <span data-ttu-id="49ca9-131">Não cercar um `-` operador binário, quando combinado com certas escolhas de formatação, pode levar a interpretá-lo como um unary `-`.</span><span class="sxs-lookup"><span data-stu-id="49ca9-131">Failing to surround a binary `-` operator, when combined with certain formatting choices, could lead to interpreting it as a unary `-`.</span></span>

### <a name="surround-a-custom-operator-definition-with-white-space"></a><span data-ttu-id="49ca9-132">Cerque uma definição de operador personalizado com espaço em branco</span><span class="sxs-lookup"><span data-stu-id="49ca9-132">Surround a custom operator definition with white space</span></span>

<span data-ttu-id="49ca9-133">Use sempre o espaço em branco para cercar uma definição do operador:</span><span class="sxs-lookup"><span data-stu-id="49ca9-133">Always use white space to surround an operator definition:</span></span>

```fsharp
// OK
let ( !> ) x f = f x

// Bad
let (!>) x f = f x
```

<span data-ttu-id="49ca9-134">Para qualquer operador personalizado `*` que comece com e que tenha mais de um caractere, você precisa adicionar um espaço em branco ao início da definição para evitar uma ambiguidade compilador.</span><span class="sxs-lookup"><span data-stu-id="49ca9-134">For any custom operator that starts with `*` and that has more than one character, you need to add a white space to the beginning of the definition to avoid a compiler ambiguity.</span></span> <span data-ttu-id="49ca9-135">Por causa disso, recomendamos que você simplesmente cerque as definições de todos os operadores com um único caractere de espaço branco.</span><span class="sxs-lookup"><span data-stu-id="49ca9-135">Because of this, we recommend that you simply surround the definitions of all operators with a single white-space character.</span></span>

### <a name="surround-function-parameter-arrows-with-white-space"></a><span data-ttu-id="49ca9-136">Setas de parâmetro de função surround com espaço branco</span><span class="sxs-lookup"><span data-stu-id="49ca9-136">Surround function parameter arrows with white space</span></span>

<span data-ttu-id="49ca9-137">Ao definir a assinatura de uma função, use o espaço em branco ao redor do `->` símbolo:</span><span class="sxs-lookup"><span data-stu-id="49ca9-137">When defining the signature of a function, use white space around the `->` symbol:</span></span>

```fsharp
// OK
type MyFun = int -> int -> string

// Bad
type MyFunBad = int->int->string
```

### <a name="surround-function-arguments-with-white-space"></a><span data-ttu-id="49ca9-138">Argumentos de função surround com espaço branco</span><span class="sxs-lookup"><span data-stu-id="49ca9-138">Surround function arguments with white space</span></span>

<span data-ttu-id="49ca9-139">Ao definir uma função, use o espaço em branco em torno de cada argumento.</span><span class="sxs-lookup"><span data-stu-id="49ca9-139">When defining a function, use white space around each argument.</span></span>

```fsharp
// OK
let myFun (a: decimal) b c = a + b + c

// Bad
let myFunBad (a:decimal)(b)c = a + b + c
```

### <a name="place-parameters-on-a-new-line-for-very-long-member-definitions"></a><span data-ttu-id="49ca9-140">Coloque parâmetros em uma nova linha para definições de membros muito longas</span><span class="sxs-lookup"><span data-stu-id="49ca9-140">Place parameters on a new line for very long member definitions</span></span>

<span data-ttu-id="49ca9-141">Se você tiver uma definição de membro muito longa, coloque os parâmetros em novas linhas e recue-os em um escopo.</span><span class="sxs-lookup"><span data-stu-id="49ca9-141">If you have a very long member definition, place the parameters on new lines and indent them one scope.</span></span>

```fsharp
type C() =
    member _.LongMethodWithLotsOfParameters(
        aVeryLongType: AVeryLongTypeThatYouNeedToUse
        aSecondVeryLongType: AVeryLongTypeThatYouNeedToUse
        aThirdVeryLongType: AVeryLongTypeThatYouNeedToUse) =
        // ... the body of the method follows
```

<span data-ttu-id="49ca9-142">Isso também se aplica aos construtores:</span><span class="sxs-lookup"><span data-stu-id="49ca9-142">This also applies to constructors:</span></span>

```fsharp
type C(
    aVeryLongType: AVeryLongTypeThatYouNeedToUse
    aSecondVeryLongType: AVeryLongTypeThatYouNeedToUse
    aThirdVeryLongType: AVeryLongTypeThatYouNeedToUse) =
    // ... the body of the class follows
```

### <a name="type-annotations"></a><span data-ttu-id="49ca9-143">Anotações de tipo</span><span class="sxs-lookup"><span data-stu-id="49ca9-143">Type annotations</span></span>

#### <a name="right-pad-function-argument-type-annotations"></a><span data-ttu-id="49ca9-144">Anotações do tipo de argumento de função do bloco direito</span><span class="sxs-lookup"><span data-stu-id="49ca9-144">Right-pad function argument type annotations</span></span>

<span data-ttu-id="49ca9-145">Ao definir argumentos com anotações de tipo, use o espaço em branco após o `:` símbolo:</span><span class="sxs-lookup"><span data-stu-id="49ca9-145">When defining arguments with type annotations, use white space after the `:` symbol:</span></span>

```fsharp
// OK
let complexFunction (a: int) (b: int) c = a + b + c

// Bad
let complexFunctionBad (a :int) (b :int) (c:int) = a + b + c
```

#### <a name="surround-return-type-annotations-with-white-space"></a><span data-ttu-id="49ca9-146">Anotações do tipo de retorno surround com espaço branco</span><span class="sxs-lookup"><span data-stu-id="49ca9-146">Surround return type annotations with white space</span></span>

<span data-ttu-id="49ca9-147">Em uma função let-bound ou anotação de tipo de valor (tipo de `:` retorno no caso de uma função), use o espaço em branco antes e depois do símbolo:</span><span class="sxs-lookup"><span data-stu-id="49ca9-147">In a let-bound function or value type annotation (return type in the case of a function), use white space before and after the `:` symbol:</span></span>

```fsharp
// OK
let expensiveToCompute : int = 0 // Type annotation for let-bound value
let myFun (a: decimal) b c : decimal = a + b + c // Type annotation for the return type of a function
// Bad
let expensiveToComputeBad1:int = 1
let expensiveToComputeBad2 :int = 2
let myFunBad (a: decimal) b c:decimal = a + b + c
```

## <a name="formatting-blank-lines"></a><span data-ttu-id="49ca9-148">Formatação de linhas em branco</span><span class="sxs-lookup"><span data-stu-id="49ca9-148">Formatting blank lines</span></span>

* <span data-ttu-id="49ca9-149">Separe as definições de função e classe de nível superior com duas linhas em branco.</span><span class="sxs-lookup"><span data-stu-id="49ca9-149">Separate top-level function and class definitions with two blank lines.</span></span>
* <span data-ttu-id="49ca9-150">As definições de método dentro de uma classe são separadas por uma única linha em branco.</span><span class="sxs-lookup"><span data-stu-id="49ca9-150">Method definitions inside a class are separated by a single blank line.</span></span>
* <span data-ttu-id="49ca9-151">Linhas em branco extras podem ser usadas (com moderação) para grupos separados de funções relacionadas.</span><span class="sxs-lookup"><span data-stu-id="49ca9-151">Extra blank lines may be used (sparingly) to separate groups of related functions.</span></span> <span data-ttu-id="49ca9-152">Linhas em branco podem ser omitidas entre um grupo de linhas uniline (por exemplo, um conjunto de implementações manequim).</span><span class="sxs-lookup"><span data-stu-id="49ca9-152">Blank lines may be omitted between a bunch of related one-liners (for example, a set of dummy implementations).</span></span>
* <span data-ttu-id="49ca9-153">Use linhas em branco em funções, com moderação, para indicar seções lógicas.</span><span class="sxs-lookup"><span data-stu-id="49ca9-153">Use blank lines in functions, sparingly, to indicate logical sections.</span></span>

## <a name="formatting-comments"></a><span data-ttu-id="49ca9-154">Formatação de comentários</span><span class="sxs-lookup"><span data-stu-id="49ca9-154">Formatting comments</span></span>

<span data-ttu-id="49ca9-155">Geralmente preferem vários comentários de corte duplo em vez de comentários de bloco no estilo ML.</span><span class="sxs-lookup"><span data-stu-id="49ca9-155">Generally prefer multiple double-slash comments over ML-style block comments.</span></span>

```fsharp
// Prefer this style of comments when you want
// to express written ideas on multiple lines.

(*
    ML-style comments are fine, but not a .NET-ism.
    They are useful when needing to modify multi-line comments, though.
*)
```

<span data-ttu-id="49ca9-156">Comentários inline devem capitalizar a primeira letra.</span><span class="sxs-lookup"><span data-stu-id="49ca9-156">Inline comments should capitalize the first letter.</span></span>

```fsharp
let f x = x + 1 // Increment by one.
```

## <a name="naming-conventions"></a><span data-ttu-id="49ca9-157">Convenções de nomenclatura</span><span class="sxs-lookup"><span data-stu-id="49ca9-157">Naming conventions</span></span>

### <a name="use-camelcase-for-class-bound-expression-bound-and-pattern-bound-values-and-functions"></a><span data-ttu-id="49ca9-158">Use camelCase para valores e funções vinculados à classe, vinculados à expressão e padrão</span><span class="sxs-lookup"><span data-stu-id="49ca9-158">Use camelCase for class-bound, expression-bound and pattern-bound values and functions</span></span>

<span data-ttu-id="49ca9-159">É comum e aceito estilo F# para usar camelCase para todos os nomes vinculados como variáveis locais ou em correspondências de padrão e definições de função.</span><span class="sxs-lookup"><span data-stu-id="49ca9-159">It is common and accepted F# style to use camelCase for all names bound as local variables or in pattern matches and function definitions.</span></span>

```fsharp
// OK
let addIAndJ i j = i + j

// Bad
let addIAndJ I J = I+J

// Bad
let AddIAndJ i j = i + j
```

<span data-ttu-id="49ca9-160">As funções vinculadas localmente nas classes também devem usar camelCase.</span><span class="sxs-lookup"><span data-stu-id="49ca9-160">Locally-bound functions in classes should also use camelCase.</span></span>

```fsharp
type MyClass() =

    let doSomething () =

    let firstResult = ...

    let secondResult = ...

    member x.Result = doSomething()
```

### <a name="use-camelcase-for-module-bound-public-functions"></a><span data-ttu-id="49ca9-161">Use camelCase para funções públicas vinculadas ao módulo</span><span class="sxs-lookup"><span data-stu-id="49ca9-161">Use camelCase for module-bound public functions</span></span>

<span data-ttu-id="49ca9-162">Quando uma função vinculada ao módulo faz parte de uma API pública, ela deve usar camelCase:</span><span class="sxs-lookup"><span data-stu-id="49ca9-162">When a module-bound function is part of a public API, it should use camelCase:</span></span>

```fsharp
module MyAPI =
    let publicFunctionOne param1 param2 param2 = ...

    let publicFunctionTwo param1 param2 param3 = ...
```

### <a name="use-camelcase-for-internal-and-private-module-bound-values-and-functions"></a><span data-ttu-id="49ca9-163">Use camelCase para valores e funções internas e privadas vinculados a módulos</span><span class="sxs-lookup"><span data-stu-id="49ca9-163">Use camelCase for internal and private module-bound values and functions</span></span>

<span data-ttu-id="49ca9-164">Use camelCase para valores privados vinculados a módulos, incluindo o seguinte:</span><span class="sxs-lookup"><span data-stu-id="49ca9-164">Use camelCase for private module-bound values, including the following:</span></span>

* <span data-ttu-id="49ca9-165">Funções ad hoc em scripts</span><span class="sxs-lookup"><span data-stu-id="49ca9-165">Ad hoc functions in scripts</span></span>

* <span data-ttu-id="49ca9-166">Valores que compõem a implementação interna de um módulo ou tipo</span><span class="sxs-lookup"><span data-stu-id="49ca9-166">Values making up the internal implementation of a module or type</span></span>

```fsharp
let emailMyBossTheLatestResults =
    ...
```

### <a name="use-camelcase-for-parameters"></a><span data-ttu-id="49ca9-167">Use cameloCase para parâmetros</span><span class="sxs-lookup"><span data-stu-id="49ca9-167">Use camelCase for parameters</span></span>

<span data-ttu-id="49ca9-168">Todos os parâmetros devem usar camelCase de acordo com as convenções de nomeação .NET.</span><span class="sxs-lookup"><span data-stu-id="49ca9-168">All parameters should use camelCase in accordance with .NET naming conventions.</span></span>

```fsharp
module MyModule =
    let myFunction paramOne paramTwo = ...

type MyClass() =
    member this.MyMethod(paramOne, paramTwo) = ...
```

### <a name="use-pascalcase-for-modules"></a><span data-ttu-id="49ca9-169">Use PascalCase para módulos</span><span class="sxs-lookup"><span data-stu-id="49ca9-169">Use PascalCase for modules</span></span>

<span data-ttu-id="49ca9-170">Todos os módulos (de nível superior, interno, privado, aninhados) devem usar PascalCase.</span><span class="sxs-lookup"><span data-stu-id="49ca9-170">All modules (top-level, internal, private, nested) should use PascalCase.</span></span>

```fsharp
module MyTopLevelModule

module Helpers =
    module private SuperHelpers =
        ...

    ...
```

### <a name="use-pascalcase-for-type-declarations-members-and-labels"></a><span data-ttu-id="49ca9-171">Use PascalCase para declarações de tipo, membros e rótulos</span><span class="sxs-lookup"><span data-stu-id="49ca9-171">Use PascalCase for type declarations, members, and labels</span></span>

<span data-ttu-id="49ca9-172">Classes, interfaces, estruturas, enumerações, delegados, registros e sindicatos discriminados devem ser nomeados com PascalCase.</span><span class="sxs-lookup"><span data-stu-id="49ca9-172">Classes, interfaces, structs, enumerations, delegates, records, and discriminated unions should all be named with PascalCase.</span></span> <span data-ttu-id="49ca9-173">Os membros dentro de tipos e rótulos para registros e sindicatos discriminados também devem usar o PascalCase.</span><span class="sxs-lookup"><span data-stu-id="49ca9-173">Members within types and labels for records and discriminated unions should also use PascalCase.</span></span>

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

### <a name="use-pascalcase-for-constructs-intrinsic-to-net"></a><span data-ttu-id="49ca9-174">Use PascalCase para construções intrínsecas a .NET</span><span class="sxs-lookup"><span data-stu-id="49ca9-174">Use PascalCase for constructs intrinsic to .NET</span></span>

<span data-ttu-id="49ca9-175">Namespaces, exceções, eventos e`.dll` projetos/nomes também devem usar PascalCase.</span><span class="sxs-lookup"><span data-stu-id="49ca9-175">Namespaces, exceptions, events, and project/`.dll` names should also use PascalCase.</span></span> <span data-ttu-id="49ca9-176">Isso não só faz com que o consumo de outras línguas .NET pareça mais natural para os consumidores, como também é consistente com as convenções de nomeação .NET que você provavelmente encontrará.</span><span class="sxs-lookup"><span data-stu-id="49ca9-176">Not only does this make consumption from other .NET languages feel more natural to consumers, it's also consistent with .NET naming conventions that you are likely to encounter.</span></span>

### <a name="avoid-underscores-in-names"></a><span data-ttu-id="49ca9-177">Evite sublinhados em nomes</span><span class="sxs-lookup"><span data-stu-id="49ca9-177">Avoid underscores in names</span></span>

<span data-ttu-id="49ca9-178">Historicamente, algumas bibliotecas F# têm usado sublinhados em nomes.</span><span class="sxs-lookup"><span data-stu-id="49ca9-178">Historically, some F# libraries have used underscores in names.</span></span> <span data-ttu-id="49ca9-179">No entanto, isso não é mais amplamente aceito, em parte porque se choca com as convenções de nomeação .NET.</span><span class="sxs-lookup"><span data-stu-id="49ca9-179">However, this is no longer widely accepted, partly because it clashes with .NET naming conventions.</span></span> <span data-ttu-id="49ca9-180">Dito isto, alguns programadores F# usam sublinhações pesadamente, em parte por razões históricas, e tolerância e respeito é importante.</span><span class="sxs-lookup"><span data-stu-id="49ca9-180">That said, some F# programmers use underscores heavily, partly for historical reasons, and tolerance and respect is important.</span></span> <span data-ttu-id="49ca9-181">No entanto, esteja ciente de que o estilo muitas vezes é detestado por outros que têm uma escolha sobre se usá-lo.</span><span class="sxs-lookup"><span data-stu-id="49ca9-181">However, be aware that the style is often disliked by others who have a choice about whether to use it.</span></span>

<span data-ttu-id="49ca9-182">Algumas exceções incluem inter-operar com componentes nativos, onde sublinhados são muito comuns.</span><span class="sxs-lookup"><span data-stu-id="49ca9-182">Some exceptions includes interoperating with native components, where underscores are very common.</span></span>

### <a name="use-standard-f-operators"></a><span data-ttu-id="49ca9-183">Use operadores F# padrão</span><span class="sxs-lookup"><span data-stu-id="49ca9-183">Use standard F# operators</span></span>

<span data-ttu-id="49ca9-184">Os seguintes operadores são definidos na biblioteca padrão F# e devem ser usados em vez de definir equivalentes.</span><span class="sxs-lookup"><span data-stu-id="49ca9-184">The following operators are defined in the F# standard library and should be used instead of defining equivalents.</span></span> <span data-ttu-id="49ca9-185">O uso desses operadores é recomendado, pois tende a tornar o código mais legível e idiomático.</span><span class="sxs-lookup"><span data-stu-id="49ca9-185">Using these operators is recommended as it tends to make code more readable and idiomatic.</span></span> <span data-ttu-id="49ca9-186">Desenvolvedores com experiência em OCaml ou outra linguagem de programação funcional podem estar acostumados a diferentes expressões.</span><span class="sxs-lookup"><span data-stu-id="49ca9-186">Developers with a background in OCaml or other functional programming language may be accustomed to different idioms.</span></span> <span data-ttu-id="49ca9-187">A lista a seguir resume os operadores F# recomendados.</span><span class="sxs-lookup"><span data-stu-id="49ca9-187">The following list summarizes the recommended F# operators.</span></span>

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

### <a name="use-prefix-syntax-for-generics-foot-in-preference-to-postfix-syntax-t-foo"></a><span data-ttu-id="49ca9-188">Use a sintaxe`Foo<T>`prefixada para genéricos (`T Foo`) em preferência à sintaxe pós-fixação ( )</span><span class="sxs-lookup"><span data-stu-id="49ca9-188">Use prefix syntax for generics (`Foo<T>`) in preference to postfix syntax (`T Foo`)</span></span>

<span data-ttu-id="49ca9-189">F# herda tanto o estilo ML pós-fixação `int list`de nomear tipos genéricos (por `list<int>`exemplo, ) quanto o prefixo .NET estilo (por exemplo, ).</span><span class="sxs-lookup"><span data-stu-id="49ca9-189">F# inherits both the postfix ML style of naming generic types (for example, `int list`) as well as the prefix .NET style (for example, `list<int>`).</span></span> <span data-ttu-id="49ca9-190">Prefira o estilo .NET, exceto por cinco tipos específicos:</span><span class="sxs-lookup"><span data-stu-id="49ca9-190">Prefer the .NET style, except for five specific types:</span></span>

1. <span data-ttu-id="49ca9-191">Para listas F#, use o `int list` formulário `list<int>`postfix: em vez de .</span><span class="sxs-lookup"><span data-stu-id="49ca9-191">For F# Lists, use the postfix form: `int list` rather than `list<int>`.</span></span>
2. <span data-ttu-id="49ca9-192">Para opções F#, use `int option` o `option<int>`formulário postfix: em vez de .</span><span class="sxs-lookup"><span data-stu-id="49ca9-192">For F# Options, use the postfix form: `int option` rather than `option<int>`.</span></span>
3. <span data-ttu-id="49ca9-193">Para f# opções de valor, `int voption` use `voption<int>`o formulário postfix: em vez de .</span><span class="sxs-lookup"><span data-stu-id="49ca9-193">For F# Value Options, use the postfix form: `int voption` rather than `voption<int>`.</span></span>
4. <span data-ttu-id="49ca9-194">Para matrizes F#, use o `int[]` nome `int array` `array<int>`sintático em vez de ou .</span><span class="sxs-lookup"><span data-stu-id="49ca9-194">For F# arrays, use the syntactic name `int[]` rather than `int array` or `array<int>`.</span></span>
5. <span data-ttu-id="49ca9-195">Para células de `int ref` referência, use em vez de `ref<int>` ou `Ref<int>`.</span><span class="sxs-lookup"><span data-stu-id="49ca9-195">For Reference Cells, use `int ref` rather than `ref<int>` or `Ref<int>`.</span></span>

<span data-ttu-id="49ca9-196">Para todos os outros tipos, use a forma de prefixo.</span><span class="sxs-lookup"><span data-stu-id="49ca9-196">For all other types, use the prefix form.</span></span>

## <a name="formatting-tuples"></a><span data-ttu-id="49ca9-197">Formatação de tuplas</span><span class="sxs-lookup"><span data-stu-id="49ca9-197">Formatting tuples</span></span>

<span data-ttu-id="49ca9-198">Uma instanciação tuple deve ser parêntena, e as comúdes delimitadoras dentro devem ser seguidas por um único espaço, por exemplo: `(1, 2)`. `(x, y, z)`</span><span class="sxs-lookup"><span data-stu-id="49ca9-198">A tuple instantiation should be parenthesized, and the delimiting commas within should be followed by a single space, for example: `(1, 2)`, `(x, y, z)`.</span></span>

<span data-ttu-id="49ca9-199">É comumente aceito para omitir parênteses na correspondência de padrões de tuplas:</span><span class="sxs-lookup"><span data-stu-id="49ca9-199">It is commonly accepted to omit parentheses in pattern matching of tuples:</span></span>

```fsharp
let (x, y) = z // Destructuring
let x, y = z // OK

// OK
match x, y with
| 1, _ -> 0
| x, 1 -> 0
| x, y -> 1
```

<span data-ttu-id="49ca9-200">Também é comumente aceito para omitir parênteses se o tuplo é o valor de retorno de uma função:</span><span class="sxs-lookup"><span data-stu-id="49ca9-200">It is also commonly accepted to omit parentheses if the tuple is the return value of a function:</span></span>

```fsharp
// OK
let update model msg =
    match msg with
    | 1 -> model + 1, []
    | _ -> model, [ msg ]
```

<span data-ttu-id="49ca9-201">Em resumo, prefira instanciais tuplas parênteses, mas ao usar tuplas para correspondência de padrões ou um valor de retorno, é considerado bom para evitar parênteses.</span><span class="sxs-lookup"><span data-stu-id="49ca9-201">In summary, prefer parenthesized tuple instantiations, but when using tuples for pattern matching or a return value, it is considered fine to avoid parentheses.</span></span>

## <a name="formatting-discriminated-union-declarations"></a><span data-ttu-id="49ca9-202">Formatação de declarações sindicais discriminadas</span><span class="sxs-lookup"><span data-stu-id="49ca9-202">Formatting discriminated union declarations</span></span>

<span data-ttu-id="49ca9-203">Recuo `|` na definição do tipo por 4 espaços:</span><span class="sxs-lookup"><span data-stu-id="49ca9-203">Indent `|` in type definition by 4 spaces:</span></span>

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

## <a name="formatting-discriminated-unions"></a><span data-ttu-id="49ca9-204">Formatação de sindicatos discriminados</span><span class="sxs-lookup"><span data-stu-id="49ca9-204">Formatting discriminated unions</span></span>

<span data-ttu-id="49ca9-205">Sindicatos discriminados instanciados que se dividem em várias linhas devem dar aos dados contidos um novo escopo com recuo:</span><span class="sxs-lookup"><span data-stu-id="49ca9-205">Instantiated Discriminated Unions that split across multiple lines should give contained data a new scope with indentation:</span></span>

```fsharp
let tree1 =
    BinaryNode
        (BinaryNode(BinaryValue 1, BinaryValue 2),
         BinaryNode(BinaryValue 3, BinaryValue 4))
```

<span data-ttu-id="49ca9-206">Os parênteses de fechamento também podem estar em uma nova linha:</span><span class="sxs-lookup"><span data-stu-id="49ca9-206">The closing parenthesis can also be on a new line:</span></span>

```fsharp
let tree1 =
    BinaryNode(
        BinaryNode(BinaryValue 1, BinaryValue 2),
        BinaryNode(BinaryValue 3, BinaryValue 4)
    )
```

## <a name="formatting-record-declarations"></a><span data-ttu-id="49ca9-207">Formatação de declarações de registro</span><span class="sxs-lookup"><span data-stu-id="49ca9-207">Formatting record declarations</span></span>

<span data-ttu-id="49ca9-208">Recue `{` na definição de tipo por 4 espaços e inicie a lista de campo na mesma linha:</span><span class="sxs-lookup"><span data-stu-id="49ca9-208">Indent `{` in type definition by 4 spaces and start the field list on the same line:</span></span>

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

<span data-ttu-id="49ca9-209">Colocar o token de abertura em uma nova linha e o token de fechamento em uma nova linha é preferível se você estiver declarando implementações de interface ou membros no registro:</span><span class="sxs-lookup"><span data-stu-id="49ca9-209">Placing the opening token on a new line and the closing token on a new line is preferable if you are declaring interface implementations or members on the record:</span></span>

```fsharp
// Declaring additional members on PostalAddress
type PostalAddress =
    {
        Address: string
        City: string
        Zip: string
    }
    member x.ZipAndCity = sprintf "%s %s" x.Zip x.City

type MyRecord =
    {
        SomeField: int
    }
    interface IMyInterface
```

## <a name="formatting-records"></a><span data-ttu-id="49ca9-210">Formatação de registros</span><span class="sxs-lookup"><span data-stu-id="49ca9-210">Formatting records</span></span>

<span data-ttu-id="49ca9-211">Registros curtos podem ser escritos em uma linha:</span><span class="sxs-lookup"><span data-stu-id="49ca9-211">Short records can be written in one line:</span></span>

```fsharp
let point = { X = 1.0; Y = 0.0 }
```

<span data-ttu-id="49ca9-212">Os registros que são mais longos devem usar novas linhas para rótulos:</span><span class="sxs-lookup"><span data-stu-id="49ca9-212">Records that are longer should use new lines for labels:</span></span>

```fsharp
let rainbow =
    { Boss = "Jeffrey"
      Lackeys = ["Zippy"; "George"; "Bungle"] }
```

<span data-ttu-id="49ca9-213">Colocando o token de abertura em uma nova linha, o conteúdo tabulado em um escopo e o token de fechamento em uma nova linha é preferível se você for:</span><span class="sxs-lookup"><span data-stu-id="49ca9-213">Placing the opening token on a new line, the contents tabbed over one scope, and the closing token on a new line is preferable if you are:</span></span>

* <span data-ttu-id="49ca9-214">Movendo registros em código com diferentes escopos de recuo</span><span class="sxs-lookup"><span data-stu-id="49ca9-214">Moving records around in code with different indentation scopes</span></span>
* <span data-ttu-id="49ca9-215">Encanando-os em uma função</span><span class="sxs-lookup"><span data-stu-id="49ca9-215">Piping them into a function</span></span>

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

<span data-ttu-id="49ca9-216">As mesmas regras se aplicam a elementos de lista e matriz.</span><span class="sxs-lookup"><span data-stu-id="49ca9-216">The same rules apply for list and array elements.</span></span>

## <a name="formatting-copy-and-update-record-expressions"></a><span data-ttu-id="49ca9-217">Formatação de expressões de registro de cópia e atualização</span><span class="sxs-lookup"><span data-stu-id="49ca9-217">Formatting copy-and-update record expressions</span></span>

<span data-ttu-id="49ca9-218">Uma expressão de registro de cópia e atualização ainda é um registro, então diretrizes semelhantes se aplicam.</span><span class="sxs-lookup"><span data-stu-id="49ca9-218">A copy-and-update record expression is still a record, so similar guidelines apply.</span></span>

<span data-ttu-id="49ca9-219">Expressões curtas podem caber em uma linha:</span><span class="sxs-lookup"><span data-stu-id="49ca9-219">Short expressions can fit on one line:</span></span>

```fsharp
let point2 = { point with X = 1; Y = 2 }
```

<span data-ttu-id="49ca9-220">Expressões mais longas devem usar novas linhas:</span><span class="sxs-lookup"><span data-stu-id="49ca9-220">Longer expressions should use new lines:</span></span>

```fsharp
let rainbow2 =
    { rainbow with
        Boss = "Jeffrey"
        Lackeys = ["Zippy"; "George"; "Bungle"] }
```

<span data-ttu-id="49ca9-221">E como com a orientação de registro, você pode querer dedicar linhas separadas para o aparelho e recue um escopo para a direita com a expressão.</span><span class="sxs-lookup"><span data-stu-id="49ca9-221">And as with the record guidance, you may want to dedicate separate lines for the braces and indent one scope to the right with the expression.</span></span> <span data-ttu-id="49ca9-222">Observe que em alguns casos especiais, como embrulhar um valor com um opcional sem parênteses, você pode precisar manter uma cinta em uma linha:</span><span class="sxs-lookup"><span data-stu-id="49ca9-222">Note that in some special cases, such as wrapping a value with an optional without parentheses, you may need to keep a brace on one line:</span></span>

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

## <a name="formatting-lists-and-arrays"></a><span data-ttu-id="49ca9-223">Listas de formatação e matrizes</span><span class="sxs-lookup"><span data-stu-id="49ca9-223">Formatting lists and arrays</span></span>

<span data-ttu-id="49ca9-224">Escreva `x :: l` com espaços `::` ao`::` redor do operador ( é um operador de infixo, portanto cercado por espaços).</span><span class="sxs-lookup"><span data-stu-id="49ca9-224">Write `x :: l` with spaces around the `::` operator (`::` is an infix operator, hence surrounded by spaces).</span></span>

<span data-ttu-id="49ca9-225">Lista e matrizes declaradas em uma única linha devem ter um espaço após o suporte de abertura e antes do suporte de fechamento:</span><span class="sxs-lookup"><span data-stu-id="49ca9-225">List and arrays declared on a single line should have a space after the opening bracket and before the closing bracket:</span></span>

```fsharp
let xs = [ 1; 2; 3 ]
let ys = [| 1; 2; 3; |]
```

<span data-ttu-id="49ca9-226">Use sempre pelo menos um espaço entre dois operadores distintos.</span><span class="sxs-lookup"><span data-stu-id="49ca9-226">Always use at least one space between two distinct brace-like operators.</span></span> <span data-ttu-id="49ca9-227">Por exemplo, deixe um `[` espaço `{`entre a e a .</span><span class="sxs-lookup"><span data-stu-id="49ca9-227">For example, leave a space between a `[` and a `{`.</span></span>

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

<span data-ttu-id="49ca9-228">A mesma diretriz se aplica a listas ou matrizes de tuplas.</span><span class="sxs-lookup"><span data-stu-id="49ca9-228">The same guideline applies for lists or arrays of tuples.</span></span>

<span data-ttu-id="49ca9-229">Listas e matrizes divididas em várias linhas seguem uma regra semelhante à dos registros:</span><span class="sxs-lookup"><span data-stu-id="49ca9-229">Lists and arrays that split across multiple lines follow a similar rule as records do:</span></span>

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

<span data-ttu-id="49ca9-230">E como acontece com os registros, declarar os suportes de abertura e fechamento em sua própria linha facilitará a movimentação de códigos e tubulações em funções.</span><span class="sxs-lookup"><span data-stu-id="49ca9-230">And as with records, declaring the opening and closing brackets on their own line will make moving code around and piping into functions easier.</span></span>

<span data-ttu-id="49ca9-231">Ao gerar matrizes e listas programáticas, prefira `->` quando `do ... yield` um valor é sempre gerado:</span><span class="sxs-lookup"><span data-stu-id="49ca9-231">When generating arrays and lists programmatically, prefer `->` over `do ... yield` when a value is always generated:</span></span>

```fsharp
// Preferred
let squares = [ for x in 1..10 -> x*x ]

// Not preferred
let squares' = [ for x in 1..10 do yield x*x ]
```

<span data-ttu-id="49ca9-232">Versões mais antigas do `yield` idioma F# são necessárias especificando em situações em que os dados podem ser gerados condicionalmente, ou podem haver expressões consecutivas a serem avaliadas.</span><span class="sxs-lookup"><span data-stu-id="49ca9-232">Older versions of the F# language required specifying `yield` in situations where data may be generated conditionally, or there may be consecutive expressions to be evaluated.</span></span> <span data-ttu-id="49ca9-233">Prefira `yield` omitir essas palavras-chave, a menos que você deve compilar com uma versão mais antiga do idioma F#:</span><span class="sxs-lookup"><span data-stu-id="49ca9-233">Prefer omitting these `yield` keywords unless you must compile with an older F# language version:</span></span>

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

<span data-ttu-id="49ca9-234">Em alguns `do...yield` casos, pode auxiliar na legibilidade.</span><span class="sxs-lookup"><span data-stu-id="49ca9-234">In some cases, `do...yield` may aid in readability.</span></span> <span data-ttu-id="49ca9-235">Esses casos, embora subjetivos, devem ser levados em consideração.</span><span class="sxs-lookup"><span data-stu-id="49ca9-235">These cases, though subjective, should be taken into consideration.</span></span>

## <a name="formatting-if-expressions"></a><span data-ttu-id="49ca9-236">Formatação se expressões</span><span class="sxs-lookup"><span data-stu-id="49ca9-236">Formatting if expressions</span></span>

<span data-ttu-id="49ca9-237">O recuo das condicionalidades depende dos tamanhos das expressões que as compõem.</span><span class="sxs-lookup"><span data-stu-id="49ca9-237">Indentation of conditionals depends on the sizes of the expressions that make them up.</span></span> <span data-ttu-id="49ca9-238">Se `cond` `e1` , `e2` e for curto, basta escrevê-los em uma linha:</span><span class="sxs-lookup"><span data-stu-id="49ca9-238">If `cond`, `e1` and `e2` are short, simply write them on one line:</span></span>

```fsharp
if cond then e1 else e2
```

<span data-ttu-id="49ca9-239">Se `cond`for `e1` `e2` em tempo maior, mas não em várias linhas:</span><span class="sxs-lookup"><span data-stu-id="49ca9-239">If either `cond`, `e1` or `e2` are longer, but not multi-line:</span></span>

```fsharp
if cond
then e1
else e2
```

<span data-ttu-id="49ca9-240">Se alguma das expressões for multi-linha:</span><span class="sxs-lookup"><span data-stu-id="49ca9-240">If any of the expressions are multi-line:</span></span>

```fsharp
if cond then
    e1
else
    e2
```

<span data-ttu-id="49ca9-241">Múltiplas condicionales `elif` com `else` e são recuadas no `if`mesmo escopo que:</span><span class="sxs-lookup"><span data-stu-id="49ca9-241">Multiple conditionals with `elif` and `else` are indented at the same scope as the `if`:</span></span>

```fsharp
if cond1 then e1
elif cond2 then e2
elif cond3 then e3
else e4
```

### <a name="pattern-matching-constructs"></a><span data-ttu-id="49ca9-242">Construções de correspondência de padrões</span><span class="sxs-lookup"><span data-stu-id="49ca9-242">Pattern matching constructs</span></span>

<span data-ttu-id="49ca9-243">Use `|` a para cada cláusula de uma partida sem recuo.</span><span class="sxs-lookup"><span data-stu-id="49ca9-243">Use a `|` for each clause of a match with no indentation.</span></span> <span data-ttu-id="49ca9-244">Se a expressão for curta, você pode considerar o uso de uma única linha se cada subexpressão também for simples.</span><span class="sxs-lookup"><span data-stu-id="49ca9-244">If the expression is short, you can consider using a single line if each subexpression is also simple.</span></span>

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

<span data-ttu-id="49ca9-245">Se a expressão à direita da seta de correspondência de padrão for muito grande, `match` / `|`mova-a para a linha seguinte, recuada a um passo da .</span><span class="sxs-lookup"><span data-stu-id="49ca9-245">If the expression on the right of the pattern matching arrow is too large, move it to the following line, indented one step from the `match`/`|`.</span></span>

```fsharp
match lam with
| Var v -> 1
| Abs(x, body) ->
    1 + sizeLambda body
| App(lam1, lam2) ->
    sizeLambda lam1 + sizeLambda lam2

```

<span data-ttu-id="49ca9-246">A correspondência de padrões `function`de funções anônimas, a partir de , geralmente não deve se identificar muito longe.</span><span class="sxs-lookup"><span data-stu-id="49ca9-246">Pattern matching of anonymous functions, starting by `function`, should generally not indent too far.</span></span> <span data-ttu-id="49ca9-247">Por exemplo, recuar um escopo da seguinte forma é bom:</span><span class="sxs-lookup"><span data-stu-id="49ca9-247">For example, indenting one scope as follows is fine:</span></span>

```fsharp
lambdaList
|> List.map (function
    | Abs(x, body) -> 1 + sizeLambda 0 body
    | App(lam1, lam2) -> sizeLambda (sizeLambda 0 lam1) lam2
    | Var v -> 1)
```

<span data-ttu-id="49ca9-248">A correspondência de padrões `let rec` em funções definidas ou `let` `let` deve `function` ser recuada 4 espaços após o início de , mesmo que a palavra-chave seja usada:</span><span class="sxs-lookup"><span data-stu-id="49ca9-248">Pattern matching in functions defined by `let` or `let rec` should be indented 4 spaces after starting of `let`, even if `function` keyword is used:</span></span>

```fsharp
let rec sizeLambda acc = function
    | Abs(x, body) -> sizeLambda (succ acc) body
    | App(lam1, lam2) -> sizeLambda (sizeLambda acc lam1) lam2
    | Var v -> succ acc
```

<span data-ttu-id="49ca9-249">Não recomendamos alinhar setas.</span><span class="sxs-lookup"><span data-stu-id="49ca9-249">We do not recommend aligning arrows.</span></span>

## <a name="formatting-trywith-expressions"></a><span data-ttu-id="49ca9-250">Formatação try/com expressões</span><span class="sxs-lookup"><span data-stu-id="49ca9-250">Formatting try/with expressions</span></span>

<span data-ttu-id="49ca9-251">A correspondência de padrões no tipo de exceção deve ser recuada no mesmo nível que `with`.</span><span class="sxs-lookup"><span data-stu-id="49ca9-251">Pattern matching on the exception type should be indented at the same level as `with`.</span></span>

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

## <a name="formatting-function-parameter-application"></a><span data-ttu-id="49ca9-252">Aplicativo de parâmetro de função de formatação</span><span class="sxs-lookup"><span data-stu-id="49ca9-252">Formatting function parameter application</span></span>

<span data-ttu-id="49ca9-253">Em geral, a maior parte da aplicação do parâmetro de função é feita na mesma linha.</span><span class="sxs-lookup"><span data-stu-id="49ca9-253">In general, most function parameter application is done on the same line.</span></span>

<span data-ttu-id="49ca9-254">Se você deseja aplicar parâmetros a uma função em uma nova linha, recue-os por um escopo.</span><span class="sxs-lookup"><span data-stu-id="49ca9-254">If you wish to apply parameters to a function on a new line, indent them by one scope.</span></span>

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

<span data-ttu-id="49ca9-255">As mesmas diretrizes se aplicam às expressões lambda como argumentos de função.</span><span class="sxs-lookup"><span data-stu-id="49ca9-255">The same guidelines apply for lambda expressions as function arguments.</span></span> <span data-ttu-id="49ca9-256">Se o corpo de uma expressão lambda, o corpo pode ter outra linha, recuada por um escopo</span><span class="sxs-lookup"><span data-stu-id="49ca9-256">If the body of a lambda expression, the body can have another line, indented by one scope</span></span>

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

<span data-ttu-id="49ca9-257">No entanto, se o corpo de uma expressão lambda é mais do que uma linha, considere fatorá-lo em uma função separada em vez de ter uma construção multi-linha aplicada como um único argumento para uma função.</span><span class="sxs-lookup"><span data-stu-id="49ca9-257">However, if the body of a lambda expression is more than one line, consider factoring it out into a separate function rather than have a multi-line construct applied as a single argument to a function.</span></span>

### <a name="formatting-infix-operators"></a><span data-ttu-id="49ca9-258">Formatação de operadores de infixo</span><span class="sxs-lookup"><span data-stu-id="49ca9-258">Formatting infix operators</span></span>

<span data-ttu-id="49ca9-259">Operadores separados por espaços.</span><span class="sxs-lookup"><span data-stu-id="49ca9-259">Separate operators by spaces.</span></span> <span data-ttu-id="49ca9-260">Exceções óbvias a `!` esta `.` regra são os operadores.</span><span class="sxs-lookup"><span data-stu-id="49ca9-260">Obvious exceptions to this rule are the `!` and `.` operators.</span></span>

<span data-ttu-id="49ca9-261">As expressões infix são OK para lineup na mesma coluna:</span><span class="sxs-lookup"><span data-stu-id="49ca9-261">Infix expressions are OK to lineup on same column:</span></span>

```fsharp
acc +
(sprintf "\t%s - %i\n\r"
     x.IngredientName x.Quantity)

let function1 arg1 arg2 arg3 arg4 =
    arg1 + arg2 +
    arg3 + arg4
```

### <a name="formatting-pipeline-operators"></a><span data-ttu-id="49ca9-262">Operadores de gasodutos de formatação</span><span class="sxs-lookup"><span data-stu-id="49ca9-262">Formatting pipeline operators</span></span>

<span data-ttu-id="49ca9-263">Os `|>` operadores de gasodutos devem ir por baixo das expressões em que operam.</span><span class="sxs-lookup"><span data-stu-id="49ca9-263">Pipeline `|>` operators should go underneath the expressions they operate on.</span></span>

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

### <a name="formatting-modules"></a><span data-ttu-id="49ca9-264">Módulos de formatação</span><span class="sxs-lookup"><span data-stu-id="49ca9-264">Formatting modules</span></span>

<span data-ttu-id="49ca9-265">O código em um módulo local deve ser recuado em relação ao módulo, mas o código em um módulo de nível superior não deve ser recuado.</span><span class="sxs-lookup"><span data-stu-id="49ca9-265">Code in a local module must be indented relative to the module, but code in a top-level module should not be indented.</span></span> <span data-ttu-id="49ca9-266">Os elementos de namespace não devem ser recuados.</span><span class="sxs-lookup"><span data-stu-id="49ca9-266">Namespace elements do not have to be indented.</span></span>

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

### <a name="formatting-object-expressions-and-interfaces"></a><span data-ttu-id="49ca9-267">Formatação de expressões e interfaces de objeto</span><span class="sxs-lookup"><span data-stu-id="49ca9-267">Formatting object expressions and interfaces</span></span>

<span data-ttu-id="49ca9-268">Expressões e interfaces de objeto devem ser `member` alinhadas da mesma forma com o recuo após 4 espaços.</span><span class="sxs-lookup"><span data-stu-id="49ca9-268">Object expressions and interfaces should be aligned in the same way with `member` being indented after 4 spaces.</span></span>

```fsharp
let comparer =
    { new IComparer<string> with
          member x.Compare(s1, s2) =
              let rev (s: String) =
                  new String (Array.rev (s.ToCharArray()))
              let reversed = rev s1
              reversed.CompareTo (rev s2) }
```

### <a name="formatting-white-space-in-expressions"></a><span data-ttu-id="49ca9-269">Formatação do espaço em branco em expressões</span><span class="sxs-lookup"><span data-stu-id="49ca9-269">Formatting white space in expressions</span></span>

<span data-ttu-id="49ca9-270">Evite espaço branco estranho nas expressões F#.</span><span class="sxs-lookup"><span data-stu-id="49ca9-270">Avoid extraneous white space in F# expressions.</span></span>

```fsharp
// OK
spam (ham.[1])

// Not OK
spam ( ham.[ 1 ] )
```

<span data-ttu-id="49ca9-271">Os argumentos nomeados também `=`não devem ter espaço em torno do:</span><span class="sxs-lookup"><span data-stu-id="49ca9-271">Named arguments should also not have space surrounding the `=`:</span></span>

```fsharp
// OK
let makeStreamReader x = new System.IO.StreamReader(path=x)

// Not OK
let makeStreamReader x = new System.IO.StreamReader(path = x)
```

## <a name="formatting-attributes"></a><span data-ttu-id="49ca9-272">Atributos de formatação</span><span class="sxs-lookup"><span data-stu-id="49ca9-272">Formatting attributes</span></span>

<span data-ttu-id="49ca9-273">[Os atributos](../language-reference/attributes.md) são colocados acima de um construto:</span><span class="sxs-lookup"><span data-stu-id="49ca9-273">[Attributes](../language-reference/attributes.md) are placed above a construct:</span></span>

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

### <a name="formatting-attributes-on-parameters"></a><span data-ttu-id="49ca9-274">Formatação de atributos em parâmetros</span><span class="sxs-lookup"><span data-stu-id="49ca9-274">Formatting attributes on parameters</span></span>

<span data-ttu-id="49ca9-275">Atributos também podem ser colocados em parâmetros.</span><span class="sxs-lookup"><span data-stu-id="49ca9-275">Attributes can also be places on parameters.</span></span> <span data-ttu-id="49ca9-276">Neste caso, coloque na mesma linha do parâmetro e antes do nome:</span><span class="sxs-lookup"><span data-stu-id="49ca9-276">In this case, place then on the same line as the parameter and before the name:</span></span>

```fsharp
// Defines a class that takes an optional value as input defaulting to false.
type C() =
    member _.M([<Optional; DefaultParameterValue(false)>] doSomething: bool)
```

### <a name="formatting-multiple-attributes"></a><span data-ttu-id="49ca9-277">Formatação de vários atributos</span><span class="sxs-lookup"><span data-stu-id="49ca9-277">Formatting multiple attributes</span></span>

<span data-ttu-id="49ca9-278">Quando vários atributos são aplicados a um construto que não é um parâmetro, eles devem ser colocados de tal forma que haja um atributo por linha:</span><span class="sxs-lookup"><span data-stu-id="49ca9-278">When multiple attributes are applied to a construct that is not a parameter, they should be placed such that there is one attribute per line:</span></span>

```fsharp
[<Struct>]
[<IsByRefLike>]
type MyRecord =
    { Label1: int
      Label2: string }
```

<span data-ttu-id="49ca9-279">Quando aplicados a um parâmetro, devem estar na mesma `;` linha e separados por um separador.</span><span class="sxs-lookup"><span data-stu-id="49ca9-279">When applied to a parameter, they must be on the same line and separated by a `;` separator.</span></span>

## <a name="formatting-literals"></a><span data-ttu-id="49ca9-280">Formatação de literais</span><span class="sxs-lookup"><span data-stu-id="49ca9-280">Formatting literals</span></span>

<span data-ttu-id="49ca9-281">[Os literais f#](../language-reference/literals.md) que usam o atributo `Literal` devem colocar o atributo em sua própria linha e usar a nomenclatura PascalCase:</span><span class="sxs-lookup"><span data-stu-id="49ca9-281">[F# literals](../language-reference/literals.md) using the `Literal` attribute should place the attribute on its own line and use PascalCase naming:</span></span>

```fsharp
[<Literal>]
let Path = __SOURCE_DIRECTORY__ + "/" + __SOURCE_FILE__

[<Literal>]
let MyUrl = "www.mywebsitethatiamworkingwith.com"
```

<span data-ttu-id="49ca9-282">Evite colocar o atributo na mesma linha que o valor.</span><span class="sxs-lookup"><span data-stu-id="49ca9-282">Avoid placing the attribute on the same line as the value.</span></span>
