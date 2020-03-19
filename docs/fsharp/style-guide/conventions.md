---
title: Convenções de codificação do F#
description: Aprenda diretrizes gerais e expressões idiomáticas ao escrever o código F# .
ms.date: 01/15/2020
ms.openlocfilehash: 7266211e501bdb52564220781e2347d1aceaf296
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400305"
---
# <a name="f-coding-conventions"></a><span data-ttu-id="64039-103">Convenções de codificação do F#</span><span class="sxs-lookup"><span data-stu-id="64039-103">F# coding conventions</span></span>

<span data-ttu-id="64039-104">As convenções a seguir são formuladas a partir da experiência de trabalhar com grandes bases de código F#.</span><span class="sxs-lookup"><span data-stu-id="64039-104">The following conventions are formulated from experience working with large F# codebases.</span></span> <span data-ttu-id="64039-105">Os [Cinco princípios do bom código F#](index.md#five-principles-of-good-f-code) são a base de cada recomendação.</span><span class="sxs-lookup"><span data-stu-id="64039-105">The [Five principles of good F# code](index.md#five-principles-of-good-f-code) are the foundation of each recommendation.</span></span> <span data-ttu-id="64039-106">Eles estão relacionados com as diretrizes de [design de componentes F#,](component-design-guidelines.md)mas são aplicáveis para qualquer código F#, não apenas componentes como bibliotecas.</span><span class="sxs-lookup"><span data-stu-id="64039-106">They are related to the [F# component design guidelines](component-design-guidelines.md), but are applicable for any F# code, not just components such as libraries.</span></span>

## <a name="organizing-code"></a><span data-ttu-id="64039-107">Código organizador</span><span class="sxs-lookup"><span data-stu-id="64039-107">Organizing code</span></span>

<span data-ttu-id="64039-108">F# apresenta duas maneiras principais de organizar código: módulos e namespaces.</span><span class="sxs-lookup"><span data-stu-id="64039-108">F# features two primary ways to organize code: modules and namespaces.</span></span> <span data-ttu-id="64039-109">Estes são semelhantes, mas têm as seguintes diferenças:</span><span class="sxs-lookup"><span data-stu-id="64039-109">These are similar, but do have the following differences:</span></span>

* <span data-ttu-id="64039-110">Os namespaces são compilados como namespaces .NET.</span><span class="sxs-lookup"><span data-stu-id="64039-110">Namespaces are compiled as .NET namespaces.</span></span> <span data-ttu-id="64039-111">Os módulos são compilados como classes estáticas.</span><span class="sxs-lookup"><span data-stu-id="64039-111">Modules are compiled as static classes.</span></span>
* <span data-ttu-id="64039-112">Os namespaces são sempre de nível superior.</span><span class="sxs-lookup"><span data-stu-id="64039-112">Namespaces are always top level.</span></span> <span data-ttu-id="64039-113">Os módulos podem ser de alto nível e aninhados em outros módulos.</span><span class="sxs-lookup"><span data-stu-id="64039-113">Modules can be top-level and nested within other modules.</span></span>
* <span data-ttu-id="64039-114">Os namespaces podem abranger vários arquivos.</span><span class="sxs-lookup"><span data-stu-id="64039-114">Namespaces can span multiple files.</span></span> <span data-ttu-id="64039-115">Módulos não podem.</span><span class="sxs-lookup"><span data-stu-id="64039-115">Modules cannot.</span></span>
* <span data-ttu-id="64039-116">Os módulos podem `[<RequireQualifiedAccess>]` ser `[<AutoOpen>]`decorados com e .</span><span class="sxs-lookup"><span data-stu-id="64039-116">Modules can be decorated with `[<RequireQualifiedAccess>]` and `[<AutoOpen>]`.</span></span>

<span data-ttu-id="64039-117">As seguintes diretrizes ajudarão você a usá-las para organizar seu código.</span><span class="sxs-lookup"><span data-stu-id="64039-117">The following guidelines will help you use these to organize your code.</span></span>

### <a name="prefer-namespaces-at-the-top-level"></a><span data-ttu-id="64039-118">Prefira espaços de nome no nível superior</span><span class="sxs-lookup"><span data-stu-id="64039-118">Prefer namespaces at the top level</span></span>

<span data-ttu-id="64039-119">Para qualquer código de consumo público, os namespaces são preferenciais aos módulos no nível superior.</span><span class="sxs-lookup"><span data-stu-id="64039-119">For any publicly consumable code, namespaces are preferential to modules at the top level.</span></span> <span data-ttu-id="64039-120">Como eles são compilados como namespaces .NET, eles são consumíveis a partir de C# sem problema.</span><span class="sxs-lookup"><span data-stu-id="64039-120">Because they are compiled as .NET namespaces, they are consumable from C# with no issue.</span></span>

```fsharp
// Good!
namespace MyCode

type MyClass() =
    ...
```

<span data-ttu-id="64039-121">O uso de um módulo de nível superior pode não parecer diferente quando chamado apenas de `MyClass` F#, mas para os consumidores C#, os chamadores podem se surpreender por ter que se qualificar com o `MyCode` módulo.</span><span class="sxs-lookup"><span data-stu-id="64039-121">Using a top-level module may not appear different when called only from F#, but for C# consumers, callers may be surprised by having to qualify `MyClass` with the `MyCode` module.</span></span>

```fsharp
// Bad!
module MyCode

type MyClass() =
    ...
```

### <a name="carefully-apply-autoopen"></a><span data-ttu-id="64039-122">Aplique cuidadosamente`[<AutoOpen>]`</span><span class="sxs-lookup"><span data-stu-id="64039-122">Carefully apply `[<AutoOpen>]`</span></span>

<span data-ttu-id="64039-123">A `[<AutoOpen>]` construção pode poluir o escopo do que está disponível para os chamadores, e a resposta para onde algo vem é "mágica".</span><span class="sxs-lookup"><span data-stu-id="64039-123">The `[<AutoOpen>]` construct can pollute the scope of what is available to callers, and the answer to where something comes from is "magic".</span></span> <span data-ttu-id="64039-124">Isso não é uma coisa boa.</span><span class="sxs-lookup"><span data-stu-id="64039-124">This is not a good thing.</span></span> <span data-ttu-id="64039-125">Uma exceção a esta regra é a própria Biblioteca Núcleo F# (embora este fato também seja um pouco controverso).</span><span class="sxs-lookup"><span data-stu-id="64039-125">An exception to this rule is the F# Core Library itself (though this fact is also a bit controversial).</span></span>

<span data-ttu-id="64039-126">No entanto, é uma conveniência se você tiver funcionalidade de ajudante para uma API pública que você deseja organizar separadamente dessa API pública.</span><span class="sxs-lookup"><span data-stu-id="64039-126">However, it is a convenience if you have helper functionality for a public API that you wish to organize separately from that public API.</span></span>

```fsharp
module MyAPI =
    [<AutoOpen>]
    module private Helpers =
        let helper1 x y z =
            ...

    let myFunction1 x =
        let y = ...
        let z = ...

        helper1 x y z
```

<span data-ttu-id="64039-127">Isso permite que você separe os detalhes de implementação da API pública de uma função sem ter que qualificar totalmente um ajudante cada vez que você chamá-lo.</span><span class="sxs-lookup"><span data-stu-id="64039-127">This lets you cleanly separate implementation details from the public API of a function without having to fully qualify a helper each time you call it.</span></span>

<span data-ttu-id="64039-128">Além disso, expor métodos de extensão e construtores de `[<AutoOpen>]`expressões no nível namespace pode ser claramente expresso com .</span><span class="sxs-lookup"><span data-stu-id="64039-128">Additionally, exposing extension methods and expression builders at the namespace level can be neatly expressed with `[<AutoOpen>]`.</span></span>

### <a name="use-requirequalifiedaccess-whenever-names-could-conflict-or-you-feel-it-helps-with-readability"></a><span data-ttu-id="64039-129">Use `[<RequireQualifiedAccess>]` sempre que os nomes podem entrar em conflito ou você sente que ajuda na legibilidade</span><span class="sxs-lookup"><span data-stu-id="64039-129">Use `[<RequireQualifiedAccess>]` whenever names could conflict or you feel it helps with readability</span></span>

<span data-ttu-id="64039-130">Adicionar `[<RequireQualifiedAccess>]` o atributo a um módulo indica que o módulo pode não ser aberto e que as referências aos elementos do módulo requerem acesso qualificado explícito.</span><span class="sxs-lookup"><span data-stu-id="64039-130">Adding the `[<RequireQualifiedAccess>]` attribute to a module indicates that the module may not be opened and that references to the elements of the module require explicit qualified access.</span></span> <span data-ttu-id="64039-131">Por exemplo, `Microsoft.FSharp.Collections.List` o módulo tem esse atributo.</span><span class="sxs-lookup"><span data-stu-id="64039-131">For example, the `Microsoft.FSharp.Collections.List` module has this attribute.</span></span>

<span data-ttu-id="64039-132">Isso é útil quando funções e valores no módulo têm nomes que provavelmente entrarão em conflito com nomes em outros módulos.</span><span class="sxs-lookup"><span data-stu-id="64039-132">This is useful when functions and values in the module have names that are likely to conflict with names in other modules.</span></span> <span data-ttu-id="64039-133">Exigir acesso qualificado pode aumentar muito a manutenção e a evolução de uma biblioteca a longo prazo.</span><span class="sxs-lookup"><span data-stu-id="64039-133">Requiring qualified access can greatly increase the long-term maintainability and evolvability of a library.</span></span>

```fsharp
[<RequireQualifiedAccess>]
module StringTokenization =
    let parse s = ...

...

let s = getAString()
let parsed = StringTokenization.parse s // Must qualify to use 'parse'
```

### <a name="sort-open-statements-topologically"></a><span data-ttu-id="64039-134">Classificar `open` declarações topologicamente</span><span class="sxs-lookup"><span data-stu-id="64039-134">Sort `open` statements topologically</span></span>

<span data-ttu-id="64039-135">Em F#, a ordem das declarações importa, inclusive com `open` declarações.</span><span class="sxs-lookup"><span data-stu-id="64039-135">In F#, the order of declarations matters, including with `open` statements.</span></span> <span data-ttu-id="64039-136">Isto é diferente de C#, onde o efeito `using` e `using static` é independente da ordenação dessas declarações em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="64039-136">This is unlike C#, where the effect of `using` and `using static` is independent of the ordering of those statements in a file.</span></span>

<span data-ttu-id="64039-137">Em F#, elementos abertos em um escopo podem sombrear outros já presentes.</span><span class="sxs-lookup"><span data-stu-id="64039-137">In F#, elements opened into a scope can shadow others already present.</span></span> <span data-ttu-id="64039-138">Isso significa que `open` as declarações de reordenação podem alterar o significado do código.</span><span class="sxs-lookup"><span data-stu-id="64039-138">This means that reordering `open` statements could alter the meaning of code.</span></span> <span data-ttu-id="64039-139">Como resultado, qualquer classificação arbitrária `open` de todas as declarações (por exemplo, alfanuméricamente) não é recomendada, para que você não gere um comportamento diferente do que você poderia esperar.</span><span class="sxs-lookup"><span data-stu-id="64039-139">As a result, any arbitrary sorting of all `open` statements (for example, alphanumerically) is not recommended, lest you generate different behavior that you might expect.</span></span>

<span data-ttu-id="64039-140">Em vez disso, recomendamos que você os [classifique topologicamente;](https://en.wikipedia.org/wiki/Topological_sorting) ou seja, `open` ordeneisuas instruções na ordem em que _as camadas_ do seu sistema são definidas.</span><span class="sxs-lookup"><span data-stu-id="64039-140">Instead, we recommend that you sort them [topologically](https://en.wikipedia.org/wiki/Topological_sorting); that is, order your `open` statements in the order in which _layers_ of your system are defined.</span></span> <span data-ttu-id="64039-141">Fazer classificação alfanumérica dentro de diferentes camadas topológicas também pode ser considerada.</span><span class="sxs-lookup"><span data-stu-id="64039-141">Doing alphanumeric sorting within different topological layers may also be considered.</span></span>

<span data-ttu-id="64039-142">Como exemplo, aqui está a classificação topológica para o arquivo aPI público do serviço de compilação F#:</span><span class="sxs-lookup"><span data-stu-id="64039-142">As an example, here is the topological sorting for the F# compiler service public API file:</span></span>

```fsharp
namespace Microsoft.FSharp.Compiler.SourceCodeServices

open System
open System.Collections.Generic
open System.Collections.Concurrent
open System.Diagnostics
open System.IO
open System.Reflection
open System.Text

open Microsoft.FSharp.Compiler
open Microsoft.FSharp.Compiler.AbstractIL
open Microsoft.FSharp.Compiler.AbstractIL.Diagnostics
open Microsoft.FSharp.Compiler.AbstractIL.IL
open Microsoft.FSharp.Compiler.AbstractIL.ILBinaryReader
open Microsoft.FSharp.Compiler.AbstractIL.Internal
open Microsoft.FSharp.Compiler.AbstractIL.Internal.Library

open Microsoft.FSharp.Compiler.AccessibilityLogic
open Microsoft.FSharp.Compiler.Ast
open Microsoft.FSharp.Compiler.CompileOps
open Microsoft.FSharp.Compiler.CompileOptions
open Microsoft.FSharp.Compiler.Driver
open Microsoft.FSharp.Compiler.ErrorLogger
open Microsoft.FSharp.Compiler.Infos
open Microsoft.FSharp.Compiler.InfoReader
open Microsoft.FSharp.Compiler.Lexhelp
open Microsoft.FSharp.Compiler.Layout
open Microsoft.FSharp.Compiler.Lib
open Microsoft.FSharp.Compiler.NameResolution
open Microsoft.FSharp.Compiler.PrettyNaming
open Microsoft.FSharp.Compiler.Parser
open Microsoft.FSharp.Compiler.Range
open Microsoft.FSharp.Compiler.Tast
open Microsoft.FSharp.Compiler.Tastops
open Microsoft.FSharp.Compiler.TcGlobals
open Microsoft.FSharp.Compiler.TypeChecker
open Microsoft.FSharp.Compiler.SourceCodeServices.SymbolHelpers

open Internal.Utilities
open Internal.Utilities.Collections
```

<span data-ttu-id="64039-143">Observe que uma linha rompe camadas topológicas, com cada camada sendo classificada alfanumérica depois.</span><span class="sxs-lookup"><span data-stu-id="64039-143">Note that a line break separates topological layers, with each layer being sorted alphanumerically afterwards.</span></span> <span data-ttu-id="64039-144">Isso organiza o código de forma limpa sem acidentalmente sombrear valores.</span><span class="sxs-lookup"><span data-stu-id="64039-144">This cleanly organizes code without accidentally shadowing values.</span></span>

## <a name="use-classes-to-contain-values-that-have-side-effects"></a><span data-ttu-id="64039-145">Use classes para conter valores que tenham efeitos colaterais</span><span class="sxs-lookup"><span data-stu-id="64039-145">Use classes to contain values that have side effects</span></span>

<span data-ttu-id="64039-146">Há muitas vezes em que a inicialização de um valor pode ter efeitos colaterais, como instanciar um contexto para um banco de dados ou outro recurso remoto.</span><span class="sxs-lookup"><span data-stu-id="64039-146">There are many times when initializing a value can have side effects, such as instantiating a context to a database or other remote resource.</span></span> <span data-ttu-id="64039-147">É tentador inicializar tais coisas em um módulo e usá-las em funções subseqüentes:</span><span class="sxs-lookup"><span data-stu-id="64039-147">It is tempting to initialize such things in a module and use it in subsequent functions:</span></span>

```fsharp
// This is bad!
module MyApi =
    let dep1 = File.ReadAllText "/Users/{your name}/connectionstring.txt"
    let dep2 = Environment.GetEnvironmentVariable "DEP_2"

    let private r = Random()
    let dep3() = r.Next() // Problematic if multiple threads use this

    let function1 arg = doStuffWith dep1 dep2 dep3 arg
    let function2 arg = doSutffWith dep1 dep2 dep3 arg
```

<span data-ttu-id="64039-148">Esta é freqüentemente uma má idéia por algumas razões:</span><span class="sxs-lookup"><span data-stu-id="64039-148">This is frequently a bad idea for a few reasons:</span></span>

<span data-ttu-id="64039-149">Primeiro, a configuração do aplicativo `dep1` é `dep2`empurrada para a base de código com e .</span><span class="sxs-lookup"><span data-stu-id="64039-149">First, application configuration is pushed into the codebase with `dep1` and `dep2`.</span></span> <span data-ttu-id="64039-150">Isso é difícil de manter em bases de código maiores.</span><span class="sxs-lookup"><span data-stu-id="64039-150">This is difficult to maintain in larger codebases.</span></span>

<span data-ttu-id="64039-151">Em segundo lugar, os dados inicializados estáticamente não devem incluir valores que não são seguros para threads se o próprio componente usar vários segmentos.</span><span class="sxs-lookup"><span data-stu-id="64039-151">Second, statically initialized data should not include values that are not thread safe if your component will itself use multiple threads.</span></span> <span data-ttu-id="64039-152">Isto é claramente violado por `dep3`.</span><span class="sxs-lookup"><span data-stu-id="64039-152">This is clearly violated by `dep3`.</span></span>

<span data-ttu-id="64039-153">Finalmente, a inicialização do módulo compila-se em um construtor estático para toda a unidade de compilação.</span><span class="sxs-lookup"><span data-stu-id="64039-153">Finally, module initialization compiles into a static constructor for the entire compilation unit.</span></span> <span data-ttu-id="64039-154">Se ocorrer algum erro na inicialização de valor let-bound `TypeInitializationException` nesse módulo, ele se manifesta como um cache a toda a vida útil do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="64039-154">If any error occurs in let-bound value initialization in that module, it manifests as a `TypeInitializationException` that is then cached for the entire lifetime of the application.</span></span> <span data-ttu-id="64039-155">Isso pode ser difícil de diagnosticar.</span><span class="sxs-lookup"><span data-stu-id="64039-155">This can be difficult to diagnose.</span></span> <span data-ttu-id="64039-156">Geralmente há uma exceção interna que você pode tentar argumentar, mas se não houver, então não há como dizer qual é a causa raiz.</span><span class="sxs-lookup"><span data-stu-id="64039-156">There is usually an inner exception that you can attempt to reason about, but if there is not, then there is no telling what the root cause is.</span></span>

<span data-ttu-id="64039-157">Em vez disso, basta usar uma classe simples para manter dependências:</span><span class="sxs-lookup"><span data-stu-id="64039-157">Instead, just use a simple class to hold dependencies:</span></span>

```fsharp
type MyParametricApi(dep1, dep2, dep3) =
    member _.Function1 arg1 = doStuffWith dep1 dep2 dep3 arg1
    member _.Function2 arg2 = doStuffWith dep1 dep2 dep3 arg2
```

<span data-ttu-id="64039-158">Isso permite o seguinte:</span><span class="sxs-lookup"><span data-stu-id="64039-158">This enables the following:</span></span>

1. <span data-ttu-id="64039-159">Empurrando qualquer estado dependente fora da própria API.</span><span class="sxs-lookup"><span data-stu-id="64039-159">Pushing any dependent state outside of the API itself.</span></span>
2. <span data-ttu-id="64039-160">A configuração agora pode ser feita fora da API.</span><span class="sxs-lookup"><span data-stu-id="64039-160">Configuration can now be done outside of the API.</span></span>
3. <span data-ttu-id="64039-161">Erros na inicialização de valores dependentes `TypeInitializationException`não são susceptíveis de se manifestar como um .</span><span class="sxs-lookup"><span data-stu-id="64039-161">Errors in initialization for dependent values are not likely to manifest as a `TypeInitializationException`.</span></span>
4. <span data-ttu-id="64039-162">A API agora é mais fácil de testar.</span><span class="sxs-lookup"><span data-stu-id="64039-162">The API is now easier to test.</span></span>

## <a name="error-management"></a><span data-ttu-id="64039-163">Gerenciamento de erros</span><span class="sxs-lookup"><span data-stu-id="64039-163">Error management</span></span>

<span data-ttu-id="64039-164">O gerenciamento de erros em sistemas grandes é um esforço complexo e nuances, e não há balas de prata para garantir que seus sistemas sejam tolerantes a falhas e se comportem bem.</span><span class="sxs-lookup"><span data-stu-id="64039-164">Error management in large systems is a complex and nuanced endeavor, and there are no silver bullets in ensuring your systems are fault-tolerant and behave well.</span></span> <span data-ttu-id="64039-165">As seguintes diretrizes devem oferecer orientação para navegar neste espaço difícil.</span><span class="sxs-lookup"><span data-stu-id="64039-165">The following guidelines should offer guidance in navigating this difficult space.</span></span>

### <a name="represent-error-cases-and-illegal-state-in-types-intrinsic-to-your-domain"></a><span data-ttu-id="64039-166">Representar casos de erro e estado ilegal em tipos intrínsecos ao seu domínio</span><span class="sxs-lookup"><span data-stu-id="64039-166">Represent error cases and illegal state in types intrinsic to your domain</span></span>

<span data-ttu-id="64039-167">Com [sindicatos discriminados,](../language-reference/discriminated-unions.md)F# lhe dá a capacidade de representar o estado de programa defeituoso em seu sistema de tipo.</span><span class="sxs-lookup"><span data-stu-id="64039-167">With [Discriminated Unions](../language-reference/discriminated-unions.md), F# gives you the ability to represent faulty program state in your type system.</span></span> <span data-ttu-id="64039-168">Por exemplo: </span><span class="sxs-lookup"><span data-stu-id="64039-168">For example:</span></span>

```fsharp
type MoneyWithdrawalResult =
    | Success of amount:decimal
    | InsufficientFunds of balance:decimal
    | CardExpired of DateTime
    | UndisclosedFailure
```

<span data-ttu-id="64039-169">Neste caso, existem três maneiras conhecidas de que sacar dinheiro de uma conta bancária pode falhar.</span><span class="sxs-lookup"><span data-stu-id="64039-169">In this case, there are three known ways that withdrawing money from a bank account can fail.</span></span> <span data-ttu-id="64039-170">Cada caso de erro é representado no tipo e, portanto, pode ser tratado com segurança durante todo o programa.</span><span class="sxs-lookup"><span data-stu-id="64039-170">Each error case is represented in the type, and can thus be dealt with safely throughout the program.</span></span>

```fsharp
let handleWithdrawal amount =
    let w = withdrawMoney amount
    match w with
    | Success am -> printfn "Successfully withdrew %f" am
    | InsufficientFunds balance -> printfn "Failed: balance is %f" balance
    | CardExpired expiredDate -> printfn "Failed: card expired on %O" expiredDate
    | UndisclosedFailure -> printfn "Failed: unknown"
```

<span data-ttu-id="64039-171">Em geral, se você pode modelar as diferentes maneiras que algo pode **falhar** em seu domínio, então o código de manipulação de erros não é mais tratado como algo que você deve lidar, além do fluxo regular do programa.</span><span class="sxs-lookup"><span data-stu-id="64039-171">In general, if you can model the different ways that something can **fail** in your domain, then error handling code is no longer treated as something you must deal with in addition to regular program flow.</span></span> <span data-ttu-id="64039-172">É simplesmente uma parte do fluxo normal do programa, e não considerado **excepcional.**</span><span class="sxs-lookup"><span data-stu-id="64039-172">It is simply a part of normal program flow, and not considered **exceptional**.</span></span> <span data-ttu-id="64039-173">Há dois benefícios primários para isso:</span><span class="sxs-lookup"><span data-stu-id="64039-173">There are two primary benefits to this:</span></span>

1. <span data-ttu-id="64039-174">É mais fácil de manter à medida que seu domínio muda com o tempo.</span><span class="sxs-lookup"><span data-stu-id="64039-174">It is easier to maintain as your domain changes over time.</span></span>
2. <span data-ttu-id="64039-175">Os casos de erro são mais fáceis de fazer o teste unitário.</span><span class="sxs-lookup"><span data-stu-id="64039-175">Error cases are easier to unit test.</span></span>

### <a name="use-exceptions-when-errors-cannot-be-represented-with-types"></a><span data-ttu-id="64039-176">Use exceções quando erros não podem ser representados com tipos</span><span class="sxs-lookup"><span data-stu-id="64039-176">Use exceptions when errors cannot be represented with types</span></span>

<span data-ttu-id="64039-177">Nem todos os erros podem ser representados em um domínio de problemas.</span><span class="sxs-lookup"><span data-stu-id="64039-177">Not all errors can be represented in a problem domain.</span></span> <span data-ttu-id="64039-178">Esses tipos de falhas são *excepcionais* na natureza, daí a capacidade de aumentar e capturar exceções em F#.</span><span class="sxs-lookup"><span data-stu-id="64039-178">These kinds of faults are *exceptional* in nature, hence the ability to raise and catch exceptions in F#.</span></span>

<span data-ttu-id="64039-179">Primeiro, recomenda-se que você leia as [Diretrizes de Design de Exceção](../../standard/design-guidelines/exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="64039-179">First, it is recommended that you read the [Exception Design Guidelines](../../standard/design-guidelines/exceptions.md).</span></span> <span data-ttu-id="64039-180">Estes também são aplicáveis a F#.</span><span class="sxs-lookup"><span data-stu-id="64039-180">These are also applicable to F#.</span></span>

<span data-ttu-id="64039-181">Os principais construtos disponíveis em F# para fins de levantar exceções devem ser considerados na seguinte ordem de preferência:</span><span class="sxs-lookup"><span data-stu-id="64039-181">The main constructs available in F# for the purposes of raising exceptions should be considered in the following order of preference:</span></span>

| <span data-ttu-id="64039-182">Função</span><span class="sxs-lookup"><span data-stu-id="64039-182">Function</span></span> | <span data-ttu-id="64039-183">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="64039-183">Syntax</span></span> | <span data-ttu-id="64039-184">Finalidade</span><span class="sxs-lookup"><span data-stu-id="64039-184">Purpose</span></span> |
|----------|--------|---------|
| `nullArg` | `nullArg "argumentName"` | <span data-ttu-id="64039-185">Levanta `System.ArgumentNullException` um com o nome de argumento especificado.</span><span class="sxs-lookup"><span data-stu-id="64039-185">Raises a `System.ArgumentNullException` with the specified argument name.</span></span> |
| `invalidArg` | `invalidArg "argumentName" "message"` | <span data-ttu-id="64039-186">Levanta `System.ArgumentException` um com um nome de argumento e mensagem especificados.</span><span class="sxs-lookup"><span data-stu-id="64039-186">Raises a `System.ArgumentException` with a specified argument name and message.</span></span> |
| `invalidOp` | `invalidOp "message"` | <span data-ttu-id="64039-187">Levanta `System.InvalidOperationException` um com a mensagem especificada.</span><span class="sxs-lookup"><span data-stu-id="64039-187">Raises a `System.InvalidOperationException` with the specified message.</span></span> |
|`raise`| `raise (ExceptionType("message"))` | <span data-ttu-id="64039-188">Mecanismo de uso geral para lançar exceções.</span><span class="sxs-lookup"><span data-stu-id="64039-188">General-purpose mechanism for throwing exceptions.</span></span> |
| `failwith` | `failwith "message"` | <span data-ttu-id="64039-189">Levanta `System.Exception` um com a mensagem especificada.</span><span class="sxs-lookup"><span data-stu-id="64039-189">Raises a `System.Exception` with the specified message.</span></span> |
| `failwithf` | `failwithf "format string" argForFormatString` | <span data-ttu-id="64039-190">Levanta `System.Exception` um com uma mensagem determinada pela seqüência de formato e suas entradas.</span><span class="sxs-lookup"><span data-stu-id="64039-190">Raises a `System.Exception` with a message determined by the format string and its inputs.</span></span> |

<span data-ttu-id="64039-191">Use `nullArg` `invalidArg` , `invalidOp` e como `ArgumentNullException`mecanismo `ArgumentException` `InvalidOperationException` para lançar , e quando apropriado.</span><span class="sxs-lookup"><span data-stu-id="64039-191">Use `nullArg`, `invalidArg` and `invalidOp` as the mechanism to throw `ArgumentNullException`, `ArgumentException` and `InvalidOperationException` when appropriate.</span></span>

<span data-ttu-id="64039-192">As `failwith` `failwithf` funções devem ser geralmente evitadas porque `Exception` elevam o tipo de base, não uma exceção específica.</span><span class="sxs-lookup"><span data-stu-id="64039-192">The `failwith` and `failwithf` functions should generally be avoided because they raise the base `Exception` type, not a specific exception.</span></span> <span data-ttu-id="64039-193">De acordo com as [Diretrizes de Design de Exceção,](../../standard/design-guidelines/exceptions.md)você deseja aumentar as exceções mais específicas quando puder.</span><span class="sxs-lookup"><span data-stu-id="64039-193">As per the [Exception Design Guidelines](../../standard/design-guidelines/exceptions.md), you want to raise more specific exceptions when you can.</span></span>

### <a name="using-exception-handling-syntax"></a><span data-ttu-id="64039-194">Usando sintaxe de manipulação de exceções</span><span class="sxs-lookup"><span data-stu-id="64039-194">Using exception-handling syntax</span></span>

<span data-ttu-id="64039-195">F# suporta padrões `try...with` de exceção através da sintaxe:</span><span class="sxs-lookup"><span data-stu-id="64039-195">F# supports exception patterns via the `try...with` syntax:</span></span>

```fsharp
try
    tryGetFileContents()
with
| :? System.IO.FileNotFoundException as e -> // Do something with it here
| :? System.Security.SecurityException as e -> // Do something with it here
```

<span data-ttu-id="64039-196">Conciliar funcionalidades para executar em face de uma exceção com correspondência de padrões pode ser um pouco complicado se você deseja manter o código limpo.</span><span class="sxs-lookup"><span data-stu-id="64039-196">Reconciling functionality to perform in the face of an exception with pattern matching can be a bit tricky if you wish to keep the code clean.</span></span> <span data-ttu-id="64039-197">Uma dessas maneiras de lidar com isso é usar [padrões ativos](../language-reference/active-patterns.md) como um meio de agrupar a funcionalidade em torno de um caso de erro com uma exceção em si.</span><span class="sxs-lookup"><span data-stu-id="64039-197">One such way to handle this is to use [active patterns](../language-reference/active-patterns.md) as a means to group functionality surrounding an error case with an exception itself.</span></span> <span data-ttu-id="64039-198">Por exemplo, você pode estar consumindo uma API que, quando lança uma exceção, inclui informações valiosas nos metadados de exceção.</span><span class="sxs-lookup"><span data-stu-id="64039-198">For example, you may be consuming an API that, when it throws an exception, encloses valuable information in the exception metadata.</span></span> <span data-ttu-id="64039-199">Desembrulhar um valor útil no corpo da exceção capturada dentro do Active Pattern e devolver esse valor pode ser útil em algumas situações.</span><span class="sxs-lookup"><span data-stu-id="64039-199">Unwrapping a useful value in the body of the captured exception inside the Active Pattern and returning that value can be helpful in some situations.</span></span>

### <a name="do-not-use-monadic-error-handling-to-replace-exceptions"></a><span data-ttu-id="64039-200">Não use o manuseio de erros monádicos para substituir exceções</span><span class="sxs-lookup"><span data-stu-id="64039-200">Do not use monadic error handling to replace exceptions</span></span>

<span data-ttu-id="64039-201">As exceções são vistas como um tabu na programação funcional.</span><span class="sxs-lookup"><span data-stu-id="64039-201">Exceptions are seen as somewhat taboo in functional programming.</span></span> <span data-ttu-id="64039-202">De fato, exceções violam a pureza, por isso é seguro considerá-las não muito funcionais.</span><span class="sxs-lookup"><span data-stu-id="64039-202">Indeed, exceptions violate purity, so it's safe to consider them not-quite functional.</span></span> <span data-ttu-id="64039-203">No entanto, isso ignora a realidade de onde o código deve ser executado, e que erros de tempo de execução podem ocorrer.</span><span class="sxs-lookup"><span data-stu-id="64039-203">However, this ignores the reality of where code must run, and that runtime errors can occur.</span></span> <span data-ttu-id="64039-204">Em geral, escreva código supondo que a maioria das coisas não são puras nem totais, para minimizar surpresas desagradáveis.</span><span class="sxs-lookup"><span data-stu-id="64039-204">In general, write code on the assumption that most things are neither pure nor total, to minimize unpleasant surprises.</span></span>

<span data-ttu-id="64039-205">É importante considerar os seguintes pontos fortes/aspectos centrais das Exceções no que diz respeito à sua relevância e adequação no ecossistema de runtime e cross-language da .NET como um todo:</span><span class="sxs-lookup"><span data-stu-id="64039-205">It is important to consider the following core strengths/aspects of Exceptions with respect to their relevance and appropriateness in the .NET runtime and cross-language ecosystem as a whole:</span></span>

1. <span data-ttu-id="64039-206">Eles contêm informações detalhadas de diagnóstico, o que é muito útil ao depurar um problema.</span><span class="sxs-lookup"><span data-stu-id="64039-206">They contain detailed diagnostic information, which is very helpful when debugging an issue.</span></span>
2. <span data-ttu-id="64039-207">Eles são bem compreendidos pelo tempo de execução e outros idiomas .NET.</span><span class="sxs-lookup"><span data-stu-id="64039-207">They are well-understood by the runtime and other .NET languages.</span></span>
3. <span data-ttu-id="64039-208">Eles podem reduzir caldeiras significativas quando comparados com o código que sai do seu caminho para *evitar* exceções, implementando algum subconjunto de sua semântica em uma base ad-hoc.</span><span class="sxs-lookup"><span data-stu-id="64039-208">They can reduce significant boilerplate when compared with code that goes out of its way to *avoid* exceptions by implementing some subset of their semantics on an ad-hoc basis.</span></span>

<span data-ttu-id="64039-209">Este terceiro ponto é crítico.</span><span class="sxs-lookup"><span data-stu-id="64039-209">This third point is critical.</span></span> <span data-ttu-id="64039-210">Para operações complexas não triviais, não usar exceções pode resultar em lidar com estruturas como esta:</span><span class="sxs-lookup"><span data-stu-id="64039-210">For nontrivial complex operations, failing to use exceptions can result in dealing with structures like this:</span></span>

```fsharp
Result<Result<MyType, string>, string list>
```

<span data-ttu-id="64039-211">O que pode facilmente levar a um código frágil, como a correspondência de padrões em erros "digitados por stringly":</span><span class="sxs-lookup"><span data-stu-id="64039-211">Which can easily lead to fragile code like pattern matching on "stringly-typed" errors:</span></span>

```fsharp
let result = doStuff()
match result with
| Ok r -> ...
| Error e ->
    if e.Contains "Error string 1" then ...
    elif e.Contains "Error string 2" then ...
    else ... // Who knows?
```

<span data-ttu-id="64039-212">Além disso, pode ser tentador engolir qualquer exceção no desejo de uma função "simples" que retorne um tipo "mais agradável":</span><span class="sxs-lookup"><span data-stu-id="64039-212">Additionally, it can be tempting to swallow any exception in the desire for a "simple" function that returns a "nicer" type:</span></span>

```fsharp
// This is bad!
let tryReadAllText (path : string) =
    try System.IO.File.ReadAllText path |> Some
    with _ -> None
```

<span data-ttu-id="64039-213">Infelizmente, `tryReadAllText` pode lançar inúmeras exceções com base na miríade de coisas que podem acontecer em um sistema de arquivos, e este código descarta qualquer informação sobre o que pode realmente estar dando errado em seu ambiente.</span><span class="sxs-lookup"><span data-stu-id="64039-213">Unfortunately, `tryReadAllText` can throw numerous exceptions based on the myriad of things that can happen on a file system, and this code discards away any information about what might actually be going wrong in your environment.</span></span> <span data-ttu-id="64039-214">Se você substituir esse código por um tipo de resultado, então você voltará à análise de mensagem de erro "digitada por stringly":</span><span class="sxs-lookup"><span data-stu-id="64039-214">If you replace this code with a result type, then you're back to "stringly-typed" error message parsing:</span></span>

```fsharp
// This is bad!
let tryReadAllText (path : string) =
    try System.IO.File.ReadAllText path |> Ok
    with e -> Error e.Message

let r = tryReadAllText "path-to-file"
match r with
| Ok text -> ...
| Error e ->
    if e.Contains "uh oh, here we go again..." then ...
    else ...
```

<span data-ttu-id="64039-215">E colocar o objeto `Error` de exceção em si na construtora apenas força você a lidar adequadamente com o tipo de exceção no local de chamada e não na função.</span><span class="sxs-lookup"><span data-stu-id="64039-215">And placing the exception object itself in the `Error` constructor just forces you to properly deal with the exception type at the call site rather than in the function.</span></span> <span data-ttu-id="64039-216">Fazer isso efetivamente cria exceções verificadas, que são notoriamente pouco divertidas de lidar como um chamador de uma API.</span><span class="sxs-lookup"><span data-stu-id="64039-216">Doing this effectively creates checked exceptions, which are notoriously unfun to deal with as a caller of an API.</span></span>

<span data-ttu-id="64039-217">Uma boa alternativa aos exemplos acima é pegar exceções *específicas* e devolver um valor significativo no contexto dessa exceção.</span><span class="sxs-lookup"><span data-stu-id="64039-217">A good alternative to the above examples is to catch *specific* exceptions and return a meaningful value in the context of that exception.</span></span> <span data-ttu-id="64039-218">Se você `tryReadAllText` modificar a função `None` da seguinte forma, tem mais significado:</span><span class="sxs-lookup"><span data-stu-id="64039-218">If you modify the `tryReadAllText` function as follows, `None` has more meaning:</span></span>

```fsharp
let tryReadAllTextIfPresent (path : string) =
    try System.IO.File.ReadAllText path |> Some
    with :? FileNotFoundException -> None
```

<span data-ttu-id="64039-219">Em vez de funcionar como um catch-all, esta função agora lidará adequadamente com o caso quando um arquivo não foi encontrado e atribuirá esse significado a um retorno.</span><span class="sxs-lookup"><span data-stu-id="64039-219">Instead of functioning as a catch-all, this function will now properly handle the case when a file was not found and assign that meaning to a return.</span></span> <span data-ttu-id="64039-220">Esse valor de retorno pode ser mapeado para esse caso de erro, sem descartar nenhuma informação contextual ou forçar os chamadores a lidar com um caso que pode não ser relevante nesse ponto do código.</span><span class="sxs-lookup"><span data-stu-id="64039-220">This return value can map to that error case, while not discarding any contextual information or forcing callers to deal with a case that may not be relevant at that point in the code.</span></span>

<span data-ttu-id="64039-221">Tipos como `Result<'Success, 'Error>` são apropriados para operações básicas onde não estão aninhados, e os tipos opcionais F# são perfeitos para representar quando algo pode retornar *algo* ou *nada*.</span><span class="sxs-lookup"><span data-stu-id="64039-221">Types such as `Result<'Success, 'Error>` are appropriate for basic operations where they aren't nested, and F# optional types are perfect for representing when something could either return *something* or *nothing*.</span></span> <span data-ttu-id="64039-222">No entanto, eles não substituem exceções e não devem ser usados na tentativa de substituir as exceções.</span><span class="sxs-lookup"><span data-stu-id="64039-222">They are not a replacement for exceptions, though, and should not be used in an attempt to replace exceptions.</span></span> <span data-ttu-id="64039-223">Em vez disso, eles devem ser aplicados criteriosamente para abordar aspectos específicos da política de gerenciamento de erros e exceções de maneiras direcionadas.</span><span class="sxs-lookup"><span data-stu-id="64039-223">Rather, they should be applied judiciously to address specific aspects of exception and error management policy in targeted ways.</span></span>

## <a name="partial-application-and-point-free-programming"></a><span data-ttu-id="64039-224">Aplicação parcial e programação sem pontos</span><span class="sxs-lookup"><span data-stu-id="64039-224">Partial application and point-free programming</span></span>

<span data-ttu-id="64039-225">F# suporta aplicação parcial e, portanto, várias maneiras de programar em um estilo sem pontos.</span><span class="sxs-lookup"><span data-stu-id="64039-225">F# supports partial application, and thus, various ways to program in a point-free style.</span></span> <span data-ttu-id="64039-226">Isso pode ser benéfico para a reutilização de código dentro de um módulo ou para a implementação de algo, mas não é algo para expor publicamente.</span><span class="sxs-lookup"><span data-stu-id="64039-226">This can be beneficial for code reuse within a module or the implementation of something, but it is not something to expose publicly.</span></span> <span data-ttu-id="64039-227">Em geral, a programação sem pontos não é uma virtude em si mesma, e pode adicionar uma barreira cognitiva significativa para pessoas que não estão imersas no estilo.</span><span class="sxs-lookup"><span data-stu-id="64039-227">In general, point-free programming is not a virtue in and of itself, and can add a significant cognitive barrier for people who are not immersed in the style.</span></span>

### <a name="do-not-use-partial-application-and-currying-in-public-apis"></a><span data-ttu-id="64039-228">Não use aplicação parcial e currying em APIs públicas</span><span class="sxs-lookup"><span data-stu-id="64039-228">Do not use partial application and currying in public APIs</span></span>

<span data-ttu-id="64039-229">Com pouca exceção, o uso de aplicação parcial em APIs públicas pode ser confuso para os consumidores.</span><span class="sxs-lookup"><span data-stu-id="64039-229">With little exception, the use of partial application in public APIs can be confusing for consumers.</span></span> <span data-ttu-id="64039-230">Normalmente, `let`valores vinculados no código F# são **valores,** não **valores de função**.</span><span class="sxs-lookup"><span data-stu-id="64039-230">Usually, `let`-bound values in F# code are **values**, not **function values**.</span></span> <span data-ttu-id="64039-231">Misturar valores e valores de função pode resultar em salvar um pequeno número de linhas de código em `>>` troca de um pouco de sobrecarga cognitiva, especialmente se combinado com operadores como para compor funções.</span><span class="sxs-lookup"><span data-stu-id="64039-231">Mixing together values and function values can result in saving a small number of lines of code in exchange for quite a bit of cognitive overhead, especially if combined with operators such as `>>` to compose functions.</span></span>

### <a name="consider-the-tooling-implications-for-point-free-programming"></a><span data-ttu-id="64039-232">Considere as implicações de ferramentação para programação sem pontos</span><span class="sxs-lookup"><span data-stu-id="64039-232">Consider the tooling implications for point-free programming</span></span>

<span data-ttu-id="64039-233">As funções curriculares não rotulam seus argumentos.</span><span class="sxs-lookup"><span data-stu-id="64039-233">Curried functions do not label their arguments.</span></span> <span data-ttu-id="64039-234">Isso tem implicações de ferramentas.</span><span class="sxs-lookup"><span data-stu-id="64039-234">This has tooling implications.</span></span> <span data-ttu-id="64039-235">Considere as duas funções a seguir:</span><span class="sxs-lookup"><span data-stu-id="64039-235">Consider the following two functions:</span></span>

```fsharp
let func name age =
    printfn "My name is %s and I am %d years old!" name age

let funcWithApplication =
    printfn "My name is %s and I am %d years old!"
```

<span data-ttu-id="64039-236">Ambas são funções `funcWithApplication` válidas, mas é uma função curricular.</span><span class="sxs-lookup"><span data-stu-id="64039-236">Both are valid functions, but `funcWithApplication` is a curried function.</span></span> <span data-ttu-id="64039-237">Quando você paira sobre seus tipos em um editor, você vê isso:</span><span class="sxs-lookup"><span data-stu-id="64039-237">When you hover over their types in an editor, you see this:</span></span>

```fsharp
val func : name:string -> age:int -> unit

val funcWithApplication : (string -> int -> unit)
```

<span data-ttu-id="64039-238">No site de chamadas, dicas de ferramentas em ferramentas como o Visual `string` `int` Studio não lhe darão informações significativas sobre o que os tipos e de entrada realmente representam.</span><span class="sxs-lookup"><span data-stu-id="64039-238">At the call site, tooltips in tooling such as Visual Studio will not give you meaningful information as to what the `string` and `int` input types actually represent.</span></span>

<span data-ttu-id="64039-239">Se você encontrar um `funcWithApplication` código sem pontos como esse é consumível publicamente, é recomendável fazer uma expansão completa para que as ferramentas possam captar nomes significativos para argumentos.</span><span class="sxs-lookup"><span data-stu-id="64039-239">If you encounter point-free code like `funcWithApplication` that is publicly consumable, it is recommended to do a full η-expansion so that tooling can pick up on meaningful names for arguments.</span></span>

<span data-ttu-id="64039-240">Além disso, depurar código sem pontos pode ser desafiador, se não impossível.</span><span class="sxs-lookup"><span data-stu-id="64039-240">Furthermore, debugging point-free code can be challenging, if not impossible.</span></span> <span data-ttu-id="64039-241">As ferramentas de depuração dependem de `let` valores vinculados a nomes (por exemplo, vinculações) para que você possa inspecionar valores intermediários no meio da execução.</span><span class="sxs-lookup"><span data-stu-id="64039-241">Debugging tools rely on values bound to names (for example, `let` bindings) so that you can inspect intermediate values midway through execution.</span></span> <span data-ttu-id="64039-242">Quando seu código não tem valores para inspecionar, não há nada para depurar.</span><span class="sxs-lookup"><span data-stu-id="64039-242">When your code has no values to inspect, there is nothing to debug.</span></span> <span data-ttu-id="64039-243">No futuro, as ferramentas de depuração podem evoluir para sintetizar esses valores com base em caminhos executados anteriormente, mas não é uma boa ideia proteger suas apostas em *possíveis* funcionalidades de depuração.</span><span class="sxs-lookup"><span data-stu-id="64039-243">In the future, debugging tools may evolve to synthesize these values based on previously executed paths, but it's not a good idea to hedge your bets on *potential* debugging functionality.</span></span>

### <a name="consider-partial-application-as-a-technique-to-reduce-internal-boilerplate"></a><span data-ttu-id="64039-244">Considere a aplicação parcial como uma técnica para reduzir a caldeira interna</span><span class="sxs-lookup"><span data-stu-id="64039-244">Consider partial application as a technique to reduce internal boilerplate</span></span>

<span data-ttu-id="64039-245">Em contraste com o ponto anterior, a aplicação parcial é uma ferramenta maravilhosa para reduzir a caldeira dentro de uma aplicação ou os internos mais profundos de uma API.</span><span class="sxs-lookup"><span data-stu-id="64039-245">In contrast to the previous point, partial application is a wonderful tool for reducing boilerplate inside of an application or the deeper internals of an API.</span></span> <span data-ttu-id="64039-246">Pode ser útil para a unidade testar a implementação de APIs mais complicadas, onde caldeira sao muitas vezes uma dor para lidar.</span><span class="sxs-lookup"><span data-stu-id="64039-246">It can be helpful for unit testing the implementation of more complicated APIs, where boilerplate is often a pain to deal with.</span></span> <span data-ttu-id="64039-247">Por exemplo, o código a seguir mostra como você pode realizar o que a maioria das estruturas de zombaria lhe dão sem ter uma dependência externa de tal estrutura e ter que aprender uma API medida relacionada.</span><span class="sxs-lookup"><span data-stu-id="64039-247">For example, the following code shows how you can accomplish what most mocking frameworks give you without taking an external dependency on such a framework and having to learn a related bespoke API.</span></span>

<span data-ttu-id="64039-248">Por exemplo, considere a seguinte topografia de solução:</span><span class="sxs-lookup"><span data-stu-id="64039-248">For example, consider the following solution topography:</span></span>

```
MySolution.sln
|_/ImplementationLogic.fsproj
|_/ImplementationLogic.Tests.fsproj
|_/API.fsproj
```

<span data-ttu-id="64039-249">`ImplementationLogic.fsproj`pode expor códigos como:</span><span class="sxs-lookup"><span data-stu-id="64039-249">`ImplementationLogic.fsproj` might expose code such as:</span></span>

```fsharp
module Transactions =
    let doTransaction txnContext txnType balance =
        ...

type Transactor(ctx, currentBalance) =
    member _.ExecuteTransaction(txnType) =
        Transactions.doTransaction ctx txtType currentBalance
        ...
```

<span data-ttu-id="64039-250">O teste `Transactions.doTransaction` `ImplementationLogic.Tests.fsproj` unitário é fácil:</span><span class="sxs-lookup"><span data-stu-id="64039-250">Unit testing `Transactions.doTransaction` in `ImplementationLogic.Tests.fsproj` is easy:</span></span>

```fsharp
namespace TransactionsTestingUtil

open Transactions

module TransactionsTestable =
    let getTestableTransactionRoutine mockContext = Transactions.doTransaction mockContext
```

<span data-ttu-id="64039-251">Aplicar parcialmente `doTransaction` com um objeto de contexto zombando permite que você chame a função em todos os testes da unidade sem precisar construir um contexto zombado cada vez:</span><span class="sxs-lookup"><span data-stu-id="64039-251">Partially applying `doTransaction` with a mocking context object lets you call the function in all of your unit tests without needing to construct a mocked context each time:</span></span>

```fsharp
namespace TransactionTests

open Xunit
open TransactionTypes
open TransactionsTestingUtil
open TransactionsTestingUtil.TransactionsTestable

let testableContext =
    { new ITransactionContext with
        member _.TheFirstMember() = ...
        member _.TheSecondMember() = ... }

let transactionRoutine = getTestableTransactionRoutine testableContext

[<Fact>]
let ``Test withdrawal transaction with 0.0 for balance``() =
    let expected = ...
    let actual = transactionRoutine TransactionType.Withdraw 0.0
    Assert.Equal(expected, actual)
```

<span data-ttu-id="64039-252">Esta técnica não deve ser universalmente aplicada a toda a sua base de código, mas é uma boa maneira de reduzir a caldeira para internos complicados e testes unitários desses internos.</span><span class="sxs-lookup"><span data-stu-id="64039-252">This technique should not be universally applied to your entire codebase, but it is a good way to reduce boilerplate for complicated internals and unit testing those internals.</span></span>

## <a name="access-control"></a><span data-ttu-id="64039-253">Controle de acesso</span><span class="sxs-lookup"><span data-stu-id="64039-253">Access control</span></span>

<span data-ttu-id="64039-254">F# tem várias opções para controle de [acesso,](../language-reference/access-control.md)herdadas do que está disponível no tempo de execução .NET.</span><span class="sxs-lookup"><span data-stu-id="64039-254">F# has multiple options for [Access control](../language-reference/access-control.md), inherited from what is available in the .NET runtime.</span></span> <span data-ttu-id="64039-255">Estes não são apenas utilizáveis para tipos - você pode usá-los para funções, também.</span><span class="sxs-lookup"><span data-stu-id="64039-255">These are not just usable for types - you can use them for functions, too.</span></span>

* <span data-ttu-id="64039-256">Prefira`public` não-tipos e membros até que você precise que eles sejam consumíveis publicamente.</span><span class="sxs-lookup"><span data-stu-id="64039-256">Prefer non-`public` types and members until you need them to be publicly consumable.</span></span> <span data-ttu-id="64039-257">Isso também minimiza o que os consumidores acasalam.</span><span class="sxs-lookup"><span data-stu-id="64039-257">This also minimizes what consumers couple to.</span></span>
* <span data-ttu-id="64039-258">Esforce-se para manter `private`todas as funcionalidades de ajudante.</span><span class="sxs-lookup"><span data-stu-id="64039-258">Strive to keep all helper functionality `private`.</span></span>
* <span data-ttu-id="64039-259">Considere o `[<AutoOpen>]` uso em um módulo privado de funções auxiliares se elas se tornarem numerosas.</span><span class="sxs-lookup"><span data-stu-id="64039-259">Consider the use of `[<AutoOpen>]` on a private module of helper functions if they become numerous.</span></span>

## <a name="type-inference-and-generics"></a><span data-ttu-id="64039-260">Inferência de tipo e genéricos</span><span class="sxs-lookup"><span data-stu-id="64039-260">Type inference and generics</span></span>

<span data-ttu-id="64039-261">A inferência de digitação pode salvá-lo de digitar um monte de caldeira.</span><span class="sxs-lookup"><span data-stu-id="64039-261">Type inference can save you from typing a lot of boilerplate.</span></span> <span data-ttu-id="64039-262">E a generalização automática no compilador F# pode ajudá-lo a escrever códigos mais genéricos com quase nenhum esforço extra de sua parte.</span><span class="sxs-lookup"><span data-stu-id="64039-262">And automatic generalization in the F# compiler can help you write more generic code with almost no extra effort on your part.</span></span> <span data-ttu-id="64039-263">No entanto, essas características não são universalmente boas.</span><span class="sxs-lookup"><span data-stu-id="64039-263">However, these features are not universally good.</span></span>

* <span data-ttu-id="64039-264">Considere rotular nomes de argumentos com tipos explícitos em APIs públicas e não confie em inferência de tipo para isso.</span><span class="sxs-lookup"><span data-stu-id="64039-264">Consider labeling argument names with explicit types in public APIs and do not rely on type inference for this.</span></span>

    <span data-ttu-id="64039-265">A razão para isso é que **você** deve estar no controle da forma de sua API, não do compilador.</span><span class="sxs-lookup"><span data-stu-id="64039-265">The reason for this is that **you** should be in control of the shape of your API, not the compiler.</span></span> <span data-ttu-id="64039-266">Embora o compilador possa fazer um bom trabalho em inferir tipos para você, é possível ter a forma de sua mudança de API se os internos em que ele se baseia ter mudado de tipo.</span><span class="sxs-lookup"><span data-stu-id="64039-266">Although the compiler can do a fine job at inferring types for you, it is possible to have the shape of your API change if the internals it relies on have changed types.</span></span> <span data-ttu-id="64039-267">Isso pode ser o que você quer, mas quase certamente resultará em uma mudança de API que os consumidores a jusante terão que lidar.</span><span class="sxs-lookup"><span data-stu-id="64039-267">This may be what you want, but it will almost certainly result in a breaking API change that downstream consumers will then have to deal with.</span></span> <span data-ttu-id="64039-268">Em vez disso, se você controlar explicitamente a forma de sua API pública, então você pode controlar essas mudanças quebrando.</span><span class="sxs-lookup"><span data-stu-id="64039-268">Instead, if you explicitly control the shape of your public API, then you can control these breaking changes.</span></span> <span data-ttu-id="64039-269">Em termos DDD, isso pode ser considerado como uma camada anticorrupção.</span><span class="sxs-lookup"><span data-stu-id="64039-269">In DDD terms, this can be thought of as an Anti-corruption layer.</span></span>

* <span data-ttu-id="64039-270">Considere dar um nome significativo aos seus argumentos genéricos.</span><span class="sxs-lookup"><span data-stu-id="64039-270">Consider giving a meaningful name to your generic arguments.</span></span>

    <span data-ttu-id="64039-271">A menos que você esteja escrevendo códigos verdadeiramente genéricos que não são específicos para um domínio específico, um nome significativo pode ajudar outros programadores a entender o domínio em que estão trabalhando.</span><span class="sxs-lookup"><span data-stu-id="64039-271">Unless you are writing truly generic code that is not specific to a particular domain, a meaningful name can help other programmers understanding the domain they're working in.</span></span> <span data-ttu-id="64039-272">Por exemplo, um parâmetro `'Document` de tipo nomeado no contexto de interagir com um banco de dados de documentos deixa mais claro que tipos de documentos genéricos podem ser aceitos pela função ou membro com quem você está trabalhando.</span><span class="sxs-lookup"><span data-stu-id="64039-272">For example, a type parameter named `'Document` in the context of interacting with a document database makes it clearer that generic document types can be accepted by the function or member you are working with.</span></span>

* <span data-ttu-id="64039-273">Considere nomear parâmetros de tipo genéricos com PascalCase.</span><span class="sxs-lookup"><span data-stu-id="64039-273">Consider naming generic type parameters with PascalCase.</span></span>

    <span data-ttu-id="64039-274">Esta é a maneira geral de fazer as coisas em .NET, por isso é recomendável que você use PascalCase em vez de snake_case ou camelCase.</span><span class="sxs-lookup"><span data-stu-id="64039-274">This is the general way to do things in .NET, so it's recommended that you use PascalCase rather than snake_case or camelCase.</span></span>

<span data-ttu-id="64039-275">Finalmente, a generalização automática nem sempre é um benefício para as pessoas que são novas no F# ou em uma grande base de código.</span><span class="sxs-lookup"><span data-stu-id="64039-275">Finally, automatic generalization is not always a boon for people who are new to F# or a large codebase.</span></span> <span data-ttu-id="64039-276">Há sobrecarga cognitiva no uso de componentes que são genéricos.</span><span class="sxs-lookup"><span data-stu-id="64039-276">There is cognitive overhead in using components that are generic.</span></span> <span data-ttu-id="64039-277">Além disso, se as funções automaticamente generalizadas não forem usadas com diferentes tipos de entrada (muito menos se elas forem destinadas a ser usadas como tal), então não há nenhum benefício real para eles serem genéricos naquele momento.</span><span class="sxs-lookup"><span data-stu-id="64039-277">Furthermore, if automatically generalized functions are not used with different input types (let alone if they are intended to be used as such), then there is no real benefit to them being generic at that point in time.</span></span> <span data-ttu-id="64039-278">Sempre considere se o código que você está escrevendo realmente se beneficiará de ser genérico.</span><span class="sxs-lookup"><span data-stu-id="64039-278">Always consider if the code you are writing will actually benefit from being generic.</span></span>

## <a name="performance"></a><span data-ttu-id="64039-279">Desempenho</span><span class="sxs-lookup"><span data-stu-id="64039-279">Performance</span></span>

### <a name="prefer-structs-for-small-data-types"></a><span data-ttu-id="64039-280">Prefira estruturas para pequenos tipos de dados</span><span class="sxs-lookup"><span data-stu-id="64039-280">Prefer structs for small data types</span></span>

<span data-ttu-id="64039-281">O uso de estruturas (também chamadas tipos de valor) pode muitas vezes resultar em maior desempenho para algum código, porque normalmente evita a alocação de objetos.</span><span class="sxs-lookup"><span data-stu-id="64039-281">Using structs (also called Value Types) can often result in higher performance for some code because it typically avoids allocating objects.</span></span> <span data-ttu-id="64039-282">No entanto, as estruturas nem sempre são um botão "ir mais rápido": se o tamanho dos dados em uma estrutura exceder 16 bytes, copiar os dados pode muitas vezes resultar em mais tempo de CPU gastar do que usar um tipo de referência.</span><span class="sxs-lookup"><span data-stu-id="64039-282">However, structs are not always a "go faster" button: if the size of the data in a struct exceeds 16 bytes, copying the data can often result in more CPU time spend than using a reference type.</span></span>

<span data-ttu-id="64039-283">Para determinar se você deve usar uma estrutura, considere as seguintes condições:</span><span class="sxs-lookup"><span data-stu-id="64039-283">To determine if you should use a struct, consider the following conditions:</span></span>

- <span data-ttu-id="64039-284">Se o tamanho de seus dados for de 16 bytes ou menor.</span><span class="sxs-lookup"><span data-stu-id="64039-284">If the size of your data is 16 bytes or smaller.</span></span>
- <span data-ttu-id="64039-285">Se é provável que você tenha muitos desses tipos de dados residentes na memória em um programa em execução.</span><span class="sxs-lookup"><span data-stu-id="64039-285">If you're likely to have many of these data types resident in memory in a running program.</span></span>

<span data-ttu-id="64039-286">Se a primeira condição se aplicar, você deve geralmente usar uma estrutura.</span><span class="sxs-lookup"><span data-stu-id="64039-286">If the first condition applies, you should generally use a struct.</span></span> <span data-ttu-id="64039-287">Se ambos se aplicam, você deve quase sempre usar uma estrutura.</span><span class="sxs-lookup"><span data-stu-id="64039-287">If both apply, you should almost always use a struct.</span></span> <span data-ttu-id="64039-288">Pode haver alguns casos em que as condições anteriores se aplicam, mas usar uma estrutura não é melhor ou pior do que usar um tipo de referência, mas é provável que sejam raros.</span><span class="sxs-lookup"><span data-stu-id="64039-288">There may be some cases where the previous conditions apply, but using a struct is no better or worse than using a reference type, but they are likely to be rare.</span></span> <span data-ttu-id="64039-289">É importante sempre medir quando se faz mudanças como esta, porém, e não operar em suposição ou intuição.</span><span class="sxs-lookup"><span data-stu-id="64039-289">It's important to always measure when making changes like this, though, and not operate on assumption or intuition.</span></span>

#### <a name="prefer-struct-tuples-when-grouping-small-value-types"></a><span data-ttu-id="64039-290">Prefira tuplas de estrutura ao agrupar pequenos tipos de valor</span><span class="sxs-lookup"><span data-stu-id="64039-290">Prefer struct tuples when grouping small value types</span></span>

<span data-ttu-id="64039-291">Considere as duas funções a seguir:</span><span class="sxs-lookup"><span data-stu-id="64039-291">Consider the following two functions:</span></span>

```fsharp
let rec runWithTuple t offset times =
    let offsetValues x y z offset =
        (x + offset, y + offset, z + offset)

    if times <= 0 then
        t
    else
        let (x, y, z) = t
        let r = offsetValues x y z offset
        runWithTuple r offset (times - 1)

let rec runWithStructTuple t offset times =
    let offsetValues x y z offset =
        struct(x + offset, y + offset, z + offset)

    if times <= 0 then
        t
    else
        let struct(x, y, z) = t
        let r = offsetValues x y z offset
        runWithStructTuple r offset (times - 1)
```

<span data-ttu-id="64039-292">Quando você faz benchmark dessas funções com uma ferramenta de benchmarking `runWithStructTuple` estatístico como [benchmarkDotNet,](https://benchmarkdotnet.org/)você verá que a função que usa tuplas de estrutura é 40% mais rápida e não aloca memória.</span><span class="sxs-lookup"><span data-stu-id="64039-292">When you benchmark these functions with a statistical benchmarking tool like [BenchmarkDotNet](https://benchmarkdotnet.org/), you'll find that the `runWithStructTuple` function that uses struct tuples runs 40% faster and allocates no memory.</span></span>

<span data-ttu-id="64039-293">No entanto, esses resultados nem sempre serão o caso em seu próprio código.</span><span class="sxs-lookup"><span data-stu-id="64039-293">However, these results won't always be the case in your own code.</span></span> <span data-ttu-id="64039-294">Se você marcar `inline`uma função como , código que usa tuplas de referência pode obter algumas otimizações adicionais, ou código que alocaria poderia simplesmente ser otimizado.</span><span class="sxs-lookup"><span data-stu-id="64039-294">If you mark a function as `inline`, code that uses reference tuples may get some additional optimizations, or code that would allocate could simply be optimized away.</span></span> <span data-ttu-id="64039-295">Você deve sempre medir resultados sempre que o desempenho estiver em causa, e nunca operar com base em suposição ou intuição.</span><span class="sxs-lookup"><span data-stu-id="64039-295">You should always measure results whenever performance is concerned, and never operate based on assumption or intuition.</span></span>

#### <a name="prefer-struct-records-when-the-data-type-is-small"></a><span data-ttu-id="64039-296">Prefira registros de estruturaquando o tipo de dados é pequeno</span><span class="sxs-lookup"><span data-stu-id="64039-296">Prefer struct records when the data type is small</span></span>

<span data-ttu-id="64039-297">A regra de ouro descrita anteriormente também vale para [os tipos de registro F#](../language-reference/records.md).</span><span class="sxs-lookup"><span data-stu-id="64039-297">The rule of thumb described earlier also holds for [F# record types](../language-reference/records.md).</span></span> <span data-ttu-id="64039-298">Considere os seguintes tipos de dados e funções que os processam:</span><span class="sxs-lookup"><span data-stu-id="64039-298">Consider the following data types and functions that process them:</span></span>

```fsharp
type Point = { X: float; Y: float; Z: float }

[<Struct>]
type SPoint = { X: float; Y: float; Z: float }

let rec processPoint (p: Point) offset times =
    let inline offsetValues (p: Point) offset =
        { p with X = p.X + offset; Y = p.Y + offset; Z = p.Z + offset }

    if times <= 0 then
        p
    else
        let r = offsetValues p offset
        processPoint r offset (times - 1)

let rec processStructPoint (p: SPoint) offset times =
    let inline offsetValues (p: SPoint) offset =
        { p with X = p.X + offset; Y = p.Y + offset; Z = p.Z + offset }

    if times <= 0 then
        p
    else
        let r = offsetValues p offset
        processStructPoint r offset (times - 1)
```

<span data-ttu-id="64039-299">Isso é semelhante ao código tuplo anterior, mas desta vez o exemplo usa registros e uma função interna inforrada.</span><span class="sxs-lookup"><span data-stu-id="64039-299">This is similar to the previous tuple code, but this time the example uses records and an inlined inner function.</span></span>

<span data-ttu-id="64039-300">Quando você faz benchmark dessas funções com uma ferramenta de benchmarking `processStructPoint` estatístico como [benchmarkDotNet,](https://benchmarkdotnet.org/)você verá que é quase 60% mais rápido e não aloca nada no heap gerenciado.</span><span class="sxs-lookup"><span data-stu-id="64039-300">When you benchmark these functions with a statistical benchmarking tool like [BenchmarkDotNet](https://benchmarkdotnet.org/), you'll find that `processStructPoint` runs nearly 60% faster and allocates nothing on the managed heap.</span></span>

#### <a name="prefer-struct-discriminated-unions-when-the-data-type-is-small"></a><span data-ttu-id="64039-301">Prefira struct sindicatos discriminados quando o tipo de dados é pequeno</span><span class="sxs-lookup"><span data-stu-id="64039-301">Prefer struct discriminated unions when the data type is small</span></span>

<span data-ttu-id="64039-302">As observações anteriores sobre o desempenho com tuplas e registros de estrutura também são para [F# Sindicatos Discriminados](../language-reference/discriminated-unions.md).</span><span class="sxs-lookup"><span data-stu-id="64039-302">The previous observations about performance with struct tuples and records also holds for [F# Discriminated Unions](../language-reference/discriminated-unions.md).</span></span> <span data-ttu-id="64039-303">Considere o código a seguir:</span><span class="sxs-lookup"><span data-stu-id="64039-303">Consider the following code:</span></span>

```fsharp
    type Name = Name of string

    [<Struct>]
    type SName = SName of string

    let reverseName (Name s) =
        s.ToCharArray()
        |> Array.rev
        |> string
        |> Name

    let structReverseName (SName s) =
        s.ToCharArray()
        |> Array.rev
        |> string
        |> SName
```

<span data-ttu-id="64039-304">É comum definir unis unionhas discriminadas como esta para modelagem de domínio.</span><span class="sxs-lookup"><span data-stu-id="64039-304">It's common to define single-case Discriminated Unions like this for domain modeling.</span></span> <span data-ttu-id="64039-305">Quando você faz benchmark dessas funções com uma ferramenta de benchmarking `structReverseName` estatístico como [benchmarkDotNet,](https://benchmarkdotnet.org/)você verá que é cerca de 25% mais rápido do que `reverseName` para pequenas strings.</span><span class="sxs-lookup"><span data-stu-id="64039-305">When you benchmark these functions with a statistical benchmarking tool like [BenchmarkDotNet](https://benchmarkdotnet.org/), you'll find that `structReverseName` runs about 25% faster than `reverseName` for small strings.</span></span> <span data-ttu-id="64039-306">Para cordas grandes, ambos executam quase o mesmo.</span><span class="sxs-lookup"><span data-stu-id="64039-306">For large strings, both perform about the same.</span></span> <span data-ttu-id="64039-307">Então, neste caso, é sempre preferível usar uma estrutura.</span><span class="sxs-lookup"><span data-stu-id="64039-307">So, in this case, it's always preferable to use a struct.</span></span> <span data-ttu-id="64039-308">Como mencionado anteriormente, sempre meça e não opere em pressupostos ou intuições.</span><span class="sxs-lookup"><span data-stu-id="64039-308">As previously mentioned, always measure and do not operate on assumptions or intuition.</span></span>

<span data-ttu-id="64039-309">Embora o exemplo anterior mostrasse que uma União Discriminada de estruturação produziu melhor desempenho, é comum ter sindicatos discriminados maiores ao modelar um domínio.</span><span class="sxs-lookup"><span data-stu-id="64039-309">Although the previous example showed that a struct Discriminated Union yielded better performance, it is common to have larger Discriminated Unions when modeling a domain.</span></span> <span data-ttu-id="64039-310">Tipos de dados maiores como esse podem não funcionar tão bem se forem estruturas dependendo das operações neles, já que mais cópias podem estar envolvidas.</span><span class="sxs-lookup"><span data-stu-id="64039-310">Larger data types like that may not perform as well if they are structs depending on the operations on them, since more copying could be involved.</span></span>

### <a name="functional-programming-and-mutation"></a><span data-ttu-id="64039-311">Programação funcional e mutação</span><span class="sxs-lookup"><span data-stu-id="64039-311">Functional programming and mutation</span></span>

<span data-ttu-id="64039-312">Os valores f# são imutáveis por padrão, o que permite evitar certas classes de bugs (especialmente aqueles que envolvem concorrência e paralelismo).</span><span class="sxs-lookup"><span data-stu-id="64039-312">F# values are immutable by default, which allows you to avoid certain classes of bugs (especially those involving concurrency and parallelism).</span></span> <span data-ttu-id="64039-313">No entanto, em certos casos, a fim de obter a eficiência ideal (ou mesmo razoável) do tempo de execução ou alocações de memória, um período de trabalho pode ser melhor implementado usando mutação de estado no local.</span><span class="sxs-lookup"><span data-stu-id="64039-313">However, in certain cases, in order to achieve optimal (or even reasonable) efficiency of execution time or memory allocations, a span of work may best be implemented by using in-place mutation of state.</span></span> <span data-ttu-id="64039-314">Isso é possível em uma base opt-in com F# com a `mutable` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="64039-314">This is possible in an opt-in basis with F# with the `mutable` keyword.</span></span>

<span data-ttu-id="64039-315">O `mutable` uso de em F# pode se sentir em desacordo com a pureza funcional.</span><span class="sxs-lookup"><span data-stu-id="64039-315">Use of `mutable` in F# may feel at odds with functional purity.</span></span> <span data-ttu-id="64039-316">Isso é compreensível, mas a pureza funcional em todos os lugares pode estar em desacordo com as metas de desempenho.</span><span class="sxs-lookup"><span data-stu-id="64039-316">This is understandable, but functional purity everywhere can be at odds with performance goals.</span></span> <span data-ttu-id="64039-317">Um compromisso é encapsular mutação de tal forma que os chamadores não precisam se preocupar com o que acontece quando eles chamam uma função.</span><span class="sxs-lookup"><span data-stu-id="64039-317">A compromise is to encapsulate mutation such that callers need not care about what happens when they call a function.</span></span> <span data-ttu-id="64039-318">Isso permite que você escreva uma interface funcional sobre uma implementação baseada em mutação para código crítico de desempenho.</span><span class="sxs-lookup"><span data-stu-id="64039-318">This allows you to write a functional interface over a mutation-based implementation for performance-critical code.</span></span>

#### <a name="wrap-mutable-code-in-immutable-interfaces"></a><span data-ttu-id="64039-319">Envoltório código mutável em interfaces imutáveis</span><span class="sxs-lookup"><span data-stu-id="64039-319">Wrap mutable code in immutable interfaces</span></span>

<span data-ttu-id="64039-320">Com a transparência referencial como meta, é fundamental escrever código que não exponha o submundo das funções críticas ao desempenho.</span><span class="sxs-lookup"><span data-stu-id="64039-320">With referential transparency as a goal, it is critical to write code that does not expose the mutable underbelly of performance-critical functions.</span></span> <span data-ttu-id="64039-321">Por exemplo, o código `Array.contains` a seguir implementa a função na biblioteca principal F#:</span><span class="sxs-lookup"><span data-stu-id="64039-321">For example, the following code implements the `Array.contains` function in the F# core library:</span></span>

```fsharp
[<CompiledName("Contains")>]
let inline contains value (array:'T[]) =
    checkNonNull "array" array
    let mutable state = false
    let mutable i = 0
    while not state && i < array.Length do
        state <- value = array.[i]
        i <- i + 1
    state
```

<span data-ttu-id="64039-322">Chamar essa função várias vezes não altera a matriz subjacente, nem exige que você mantenha qualquer estado mutável em consumi-la.</span><span class="sxs-lookup"><span data-stu-id="64039-322">Calling this function multiple times does not change the underlying array, nor does it require you to maintain any mutable state in consuming it.</span></span> <span data-ttu-id="64039-323">É referencialmente transparente, embora quase todas as linhas de código dentro dele use mutação.</span><span class="sxs-lookup"><span data-stu-id="64039-323">It is referentially transparent, even though almost every line of code within it uses mutation.</span></span>

#### <a name="consider-encapsulating-mutable-data-in-classes"></a><span data-ttu-id="64039-324">Considere encapsular dados mutáveis nas classes</span><span class="sxs-lookup"><span data-stu-id="64039-324">Consider encapsulating mutable data in classes</span></span>

<span data-ttu-id="64039-325">O exemplo anterior usou uma única função para encapsular operações usando dados mutáveis.</span><span class="sxs-lookup"><span data-stu-id="64039-325">The previous example used a single function to encapsulate operations using mutable data.</span></span> <span data-ttu-id="64039-326">Isso nem sempre é suficiente para conjuntos de dados mais complexos.</span><span class="sxs-lookup"><span data-stu-id="64039-326">This is not always sufficient for more complex sets of data.</span></span> <span data-ttu-id="64039-327">Considere os seguintes conjuntos de funções:</span><span class="sxs-lookup"><span data-stu-id="64039-327">Consider the following sets of functions:</span></span>

```fsharp
open System.Collections.Generic

let addToClosureTable (key, value) (t: Dictionary<_,_>) =
    if not (t.ContainsKey(key)) then
        t.Add(key, value)
    else
        t.[key] <- value

let closureTableCount (t: Dictionary<_,_>) = t.Count

let closureTableContains (key, value) (t: Dictionary<_, HashSet<_>>) =
    match t.TryGetValue(key) with
    | (true, v) -> v.Equals(value)
    | (false, _) -> false
```

<span data-ttu-id="64039-328">Este código é performante, mas expõe a estrutura de dados baseada em mutação que os chamadores são responsáveis pela manutenção.</span><span class="sxs-lookup"><span data-stu-id="64039-328">This code is performant, but it exposes the mutation-based data structure that callers are responsible for maintaining.</span></span> <span data-ttu-id="64039-329">Isso pode ser embrulhado dentro de uma classe sem membros subjacentes que possam mudar:</span><span class="sxs-lookup"><span data-stu-id="64039-329">This can be wrapped inside of a class with no underlying members that can change:</span></span>

```fsharp
open System.Collections.Generic

/// The results of computing the LALR(1) closure of an LR(0) kernel
type Closure1Table() =
    let t = Dictionary<Item0, HashSet<TerminalIndex>>()

    member _.Add(key, value) =
        if not (t.ContainsKey(key)) then
            t.Add(key, value)
        else
            t.[key] <- value

    member _.Count = t.Count

    member _.Contains(key, value) =
        match t.TryGetValue(key) with
        | (true, v) -> v.Equals(value)
        | (false, _) -> false
```

<span data-ttu-id="64039-330">`Closure1Table`encapsula a estrutura de dados baseada em mutação subjacente, não forçando os chamadores a manter a estrutura de dados subjacente.</span><span class="sxs-lookup"><span data-stu-id="64039-330">`Closure1Table` encapsulates the underlying mutation-based data structure, thereby not forcing callers to maintain the underlying data structure.</span></span> <span data-ttu-id="64039-331">As classes são uma maneira poderosa de encapsular dados e rotinas que são baseadas em mutação sem expor os detalhes aos chamadores.</span><span class="sxs-lookup"><span data-stu-id="64039-331">Classes are a powerful way to encapsulate data and routines that are mutation-based without exposing the details to callers.</span></span>

#### <a name="prefer-let-mutable-to-reference-cells"></a><span data-ttu-id="64039-332">Prefira `let mutable` as células de referência</span><span class="sxs-lookup"><span data-stu-id="64039-332">Prefer `let mutable` to reference cells</span></span>

<span data-ttu-id="64039-333">As células de referência são uma forma de representar a referência a um valor e não ao valor em si.</span><span class="sxs-lookup"><span data-stu-id="64039-333">Reference cells are a way to represent the reference to a value rather than the value itself.</span></span> <span data-ttu-id="64039-334">Embora possam ser usados para código crítico de desempenho, eles não são recomendados.</span><span class="sxs-lookup"><span data-stu-id="64039-334">Although they can be used for performance-critical code, they are not recommended.</span></span> <span data-ttu-id="64039-335">Considere o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="64039-335">Consider the following example:</span></span>

```fsharp
let kernels =
    let acc = ref Set.empty

    processWorkList startKernels (fun kernel ->
        if not ((!acc).Contains(kernel)) then
            acc := (!acc).Add(kernel)
        ...)

    !acc |> Seq.toList
```

<span data-ttu-id="64039-336">O uso de uma célula de referência agora "polui" todo o código subseqüente com a desreferência e rereferência dos dados subjacentes.</span><span class="sxs-lookup"><span data-stu-id="64039-336">The use of a reference cell now "pollutes" all subsequent code with having to dereference and re-reference the underlying data.</span></span> <span data-ttu-id="64039-337">Em vez `let mutable`disso, considere:</span><span class="sxs-lookup"><span data-stu-id="64039-337">Instead, consider `let mutable`:</span></span>

```fsharp
let kernels =
    let mutable acc = Set.empty

    processWorkList startKernels (fun kernel ->
        if not (acc.Contains(kernel)) then
            acc <- acc.Add(kernel)
        ...)

    acc |> Seq.toList
```

<span data-ttu-id="64039-338">Além do único ponto de mutação no meio da expressão lambda, todos os outros códigos `acc` que tocam podem `let`fazê-lo de uma maneira que não é diferente do uso de um valor imutável normal.</span><span class="sxs-lookup"><span data-stu-id="64039-338">Aside from the single point of mutation in the middle of the lambda expression, all other code that touches `acc` can do so in a manner that is no different to the usage of a normal `let`-bound immutable value.</span></span> <span data-ttu-id="64039-339">Isso tornará mais fácil mudar com o tempo.</span><span class="sxs-lookup"><span data-stu-id="64039-339">This will make it easier to change over time.</span></span>

## <a name="object-programming"></a><span data-ttu-id="64039-340">Programação de objetos</span><span class="sxs-lookup"><span data-stu-id="64039-340">Object programming</span></span>

<span data-ttu-id="64039-341">F# tem suporte total para objetos e conceitos orientados a objetos (OO).</span><span class="sxs-lookup"><span data-stu-id="64039-341">F# has full support for objects and object-oriented (OO) concepts.</span></span> <span data-ttu-id="64039-342">Embora muitos conceitos de OO sejam poderosos e úteis, nem todos eles são ideais para usar.</span><span class="sxs-lookup"><span data-stu-id="64039-342">Although many OO concepts are powerful and useful, not all of them are ideal to use.</span></span> <span data-ttu-id="64039-343">As listas a seguir oferecem orientações sobre categorias de recursos oO em um alto nível.</span><span class="sxs-lookup"><span data-stu-id="64039-343">The following lists offer guidance on categories of OO features at a high level.</span></span>

<span data-ttu-id="64039-344">**Considere usar esses recursos em muitas situações:**</span><span class="sxs-lookup"><span data-stu-id="64039-344">**Consider using these features in many situations:**</span></span>

* <span data-ttu-id="64039-345">Notação de`x.Length`dot ()</span><span class="sxs-lookup"><span data-stu-id="64039-345">Dot notation (`x.Length`)</span></span>
* <span data-ttu-id="64039-346">Membros de instância</span><span class="sxs-lookup"><span data-stu-id="64039-346">Instance members</span></span>
* <span data-ttu-id="64039-347">Construtores implícitos</span><span class="sxs-lookup"><span data-stu-id="64039-347">Implicit constructors</span></span>
* <span data-ttu-id="64039-348">Membros estáticos</span><span class="sxs-lookup"><span data-stu-id="64039-348">Static members</span></span>
* <span data-ttu-id="64039-349">Notação do`arr.[x]`indexador ( )</span><span class="sxs-lookup"><span data-stu-id="64039-349">Indexer notation (`arr.[x]`)</span></span>
* <span data-ttu-id="64039-350">Argumentos nomeados e opcionais</span><span class="sxs-lookup"><span data-stu-id="64039-350">Named and Optional arguments</span></span>
* <span data-ttu-id="64039-351">Implementações de interfaces e interfaces</span><span class="sxs-lookup"><span data-stu-id="64039-351">Interfaces and interface implementations</span></span>

<span data-ttu-id="64039-352">**Não alcance esses recursos primeiro, mas aplique-os criteriosamente quando eles são convenientes para resolver um problema:**</span><span class="sxs-lookup"><span data-stu-id="64039-352">**Don't reach for these features first, but do judiciously apply them when they are convenient to solve a problem:**</span></span>

* <span data-ttu-id="64039-353">Sobrecarga de método</span><span class="sxs-lookup"><span data-stu-id="64039-353">Method overloading</span></span>
* <span data-ttu-id="64039-354">Dados mutáveis encapsulados</span><span class="sxs-lookup"><span data-stu-id="64039-354">Encapsulated mutable data</span></span>
* <span data-ttu-id="64039-355">Operadores em tipos</span><span class="sxs-lookup"><span data-stu-id="64039-355">Operators on types</span></span>
* <span data-ttu-id="64039-356">Propriedades automáticas</span><span class="sxs-lookup"><span data-stu-id="64039-356">Auto properties</span></span>
* <span data-ttu-id="64039-357">Implementação `IDisposable` e`IEnumerable`</span><span class="sxs-lookup"><span data-stu-id="64039-357">Implementing `IDisposable` and `IEnumerable`</span></span>
* <span data-ttu-id="64039-358">Tipo extensões</span><span class="sxs-lookup"><span data-stu-id="64039-358">Type extensions</span></span>
* <span data-ttu-id="64039-359">Eventos</span><span class="sxs-lookup"><span data-stu-id="64039-359">Events</span></span>
* <span data-ttu-id="64039-360">Structs</span><span class="sxs-lookup"><span data-stu-id="64039-360">Structs</span></span>
* <span data-ttu-id="64039-361">Delega</span><span class="sxs-lookup"><span data-stu-id="64039-361">Delegates</span></span>
* <span data-ttu-id="64039-362">Enums</span><span class="sxs-lookup"><span data-stu-id="64039-362">Enums</span></span>

<span data-ttu-id="64039-363">**Geralmente evite esses recursos, a menos que você deve usá-los:**</span><span class="sxs-lookup"><span data-stu-id="64039-363">**Generally avoid these features unless you must use them:**</span></span>

* <span data-ttu-id="64039-364">Hierarquias de tipo baseadas em herança e herança de implementação</span><span class="sxs-lookup"><span data-stu-id="64039-364">Inheritance-based type hierarchies and implementation inheritance</span></span>
* <span data-ttu-id="64039-365">Nulos e`Unchecked.defaultof<_>`</span><span class="sxs-lookup"><span data-stu-id="64039-365">Nulls and `Unchecked.defaultof<_>`</span></span>

### <a name="prefer-composition-over-inheritance"></a><span data-ttu-id="64039-366">Prefira composição em vez de herança</span><span class="sxs-lookup"><span data-stu-id="64039-366">Prefer composition over inheritance</span></span>

<span data-ttu-id="64039-367">[Composição sobre herança](https://en.wikipedia.org/wiki/Composition_over_inheritance) é um idioma de longa data que o bom código F# pode aderir.</span><span class="sxs-lookup"><span data-stu-id="64039-367">[Composition over inheritance](https://en.wikipedia.org/wiki/Composition_over_inheritance) is a long-standing idiom that good F# code can adhere to.</span></span> <span data-ttu-id="64039-368">O princípio fundamental é que você não deve expor uma classe base e forçar os chamadores a herdar dessa classe base para obter funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="64039-368">The fundamental principle is that you should not expose a base class and force callers to inherit from that base class to get functionality.</span></span>

### <a name="use-object-expressions-to-implement-interfaces-if-you-dont-need-a-class"></a><span data-ttu-id="64039-369">Use expressões de objeto para implementar interfaces se você não precisar de uma classe</span><span class="sxs-lookup"><span data-stu-id="64039-369">Use object expressions to implement interfaces if you don't need a class</span></span>

<span data-ttu-id="64039-370">[Expressões de objeto](../language-reference/object-expressions.md) permitem que você implemente interfaces em tempo real, vinculando a interface implementada a um valor sem precisar fazê-lo dentro de uma classe.</span><span class="sxs-lookup"><span data-stu-id="64039-370">[Object Expressions](../language-reference/object-expressions.md) allow you to implement interfaces on the fly, binding the implemented interface to a value without needing to do so inside of a class.</span></span> <span data-ttu-id="64039-371">Isso é conveniente, especialmente se você _só_ precisa implementar a interface e não tem necessidade de uma aula completa.</span><span class="sxs-lookup"><span data-stu-id="64039-371">This is convenient, especially if you _only_ need to implement the interface and have no need for a full class.</span></span>

<span data-ttu-id="64039-372">Por exemplo, aqui está o código que é executado em [Ionide](http://ionide.io/) para fornecer uma ação de `open` correção de código se você adicionou um símbolo para o qual você não tem uma declaração:</span><span class="sxs-lookup"><span data-stu-id="64039-372">For example, here is the code that is run in [Ionide](http://ionide.io/) to provide a code fix action if you've added a symbol that you don't have an `open` statement for:</span></span>

```fsharp
    let private createProvider () =
        { new CodeActionProvider with
            member this.provideCodeActions(doc, range, context, ct) =
                let diagnostics = context.diagnostics
                let diagnostic = diagnostics |> Seq.tryFind (fun d -> d.message.Contains "Unused open statement")
                let res =
                    match diagnostic with
                    | None -> [||]
                    | Some d ->
                        let line = doc.lineAt d.range.start.line
                        let cmd = createEmpty<Command>
                        cmd.title <- "Remove unused open"
                        cmd.command <- "fsharp.unusedOpenFix"
                        cmd.arguments <- Some ([| doc |> unbox; line.range |> unbox; |] |> ResizeArray)
                        [|cmd |]
                res
                |> ResizeArray
                |> U2.Case1
        }
```

<span data-ttu-id="64039-373">Como não há necessidade de uma aula ao interagir com a API visual studio code, as Expressões de Objeto são uma ferramenta ideal para isso.</span><span class="sxs-lookup"><span data-stu-id="64039-373">Because there is no need for a class when interacting with the Visual Studio Code API, Object Expressions are an ideal tool for this.</span></span> <span data-ttu-id="64039-374">Eles também são valiosos para testes unitários, quando você quer stub out uma interface com rotinas de teste de uma maneira ad hoc.</span><span class="sxs-lookup"><span data-stu-id="64039-374">They are also valuable for unit testing, when you want to stub out an interface with test routines in an ad hoc manner.</span></span>

## <a name="consider-type-abbreviations-to-shorten-signatures"></a><span data-ttu-id="64039-375">Considere abreviaturas de tipo para encurtar assinaturas</span><span class="sxs-lookup"><span data-stu-id="64039-375">Consider Type Abbreviations to shorten signatures</span></span>

<span data-ttu-id="64039-376">[Abreviaturas de tipo](../language-reference/type-abbreviations.md) são uma maneira conveniente de atribuir um rótulo a outro tipo, como uma assinatura de função ou um tipo mais complexo.</span><span class="sxs-lookup"><span data-stu-id="64039-376">[Type Abbreviations](../language-reference/type-abbreviations.md) are a convenient way to assign a label to another type, such as a function signature or a more complex type.</span></span> <span data-ttu-id="64039-377">Por exemplo, o alias a seguir atribui um rótulo ao necessário para definir uma computação com [CNTK](https://docs.microsoft.com/cognitive-toolkit/), uma biblioteca de aprendizado profundo:</span><span class="sxs-lookup"><span data-stu-id="64039-377">For example, the following alias assigns a label to what's needed to define a computation with [CNTK](https://docs.microsoft.com/cognitive-toolkit/), a deep learning library:</span></span>

```fsharp
open CNTK

// DeviceDescriptor, Variable, and Function all come from CNTK
type Computation = DeviceDescriptor -> Variable -> Function
```

<span data-ttu-id="64039-378">O `Computation` nome é uma maneira conveniente de denotar qualquer função que corresponda à assinatura que está aliando.</span><span class="sxs-lookup"><span data-stu-id="64039-378">The `Computation` name is a convenient way to denote any function that matches the signature it is aliasing.</span></span> <span data-ttu-id="64039-379">Usar abreviaturas de tipo como esta é conveniente e permite um código mais sucinto.</span><span class="sxs-lookup"><span data-stu-id="64039-379">Using Type Abbreviations like this is convenient and allows for more succinct code.</span></span>

### <a name="avoid-using-type-abbreviations-to-represent-your-domain"></a><span data-ttu-id="64039-380">Evite usar abreviaturas de tipo para representar seu domínio</span><span class="sxs-lookup"><span data-stu-id="64039-380">Avoid using Type Abbreviations to represent your domain</span></span>

<span data-ttu-id="64039-381">Embora abreviaturas de tipo sejam convenientes para dar um nome para funcionar assinaturas, elas podem ser confusas ao abreviar outros tipos.</span><span class="sxs-lookup"><span data-stu-id="64039-381">Although Type Abbreviations are convenient for giving a name to function signatures, they can be confusing when abbreviating other types.</span></span> <span data-ttu-id="64039-382">Considere esta abreviação:</span><span class="sxs-lookup"><span data-stu-id="64039-382">Consider this abbreviation:</span></span>

```fsharp
// Does not actually abstract integers.
type BufferSize = int
```

<span data-ttu-id="64039-383">Isso pode ser confuso de várias maneiras:</span><span class="sxs-lookup"><span data-stu-id="64039-383">This can be confusing in multiple ways:</span></span>

* <span data-ttu-id="64039-384">`BufferSize`não é uma abstração; é apenas outro nome para um inteiro.</span><span class="sxs-lookup"><span data-stu-id="64039-384">`BufferSize` is not an abstraction; it is just another name for an integer.</span></span>
* <span data-ttu-id="64039-385">Se `BufferSize` for exposto em uma API pública, pode ser facilmente `int`mal interpretado para significar mais do que apenas .</span><span class="sxs-lookup"><span data-stu-id="64039-385">If `BufferSize` is exposed in a public API, it can easily be misinterpreted to mean more than just `int`.</span></span> <span data-ttu-id="64039-386">Geralmente, os tipos de domínio têm vários atributos para eles e não são tipos primitivos como `int`.</span><span class="sxs-lookup"><span data-stu-id="64039-386">Generally, domain types have multiple attributes to them and are not primitive types like `int`.</span></span> <span data-ttu-id="64039-387">Essa abreviação viola essa suposição.</span><span class="sxs-lookup"><span data-stu-id="64039-387">This abbreviation violates that assumption.</span></span>
* <span data-ttu-id="64039-388">O invólucro de `BufferSize` (PascalCase) implica que este tipo contém mais dados.</span><span class="sxs-lookup"><span data-stu-id="64039-388">The casing of `BufferSize` (PascalCase) implies that this type holds more data.</span></span>
* <span data-ttu-id="64039-389">Este alias não oferece maior clareza em comparação com o fornecimento de um argumento nomeado para uma função.</span><span class="sxs-lookup"><span data-stu-id="64039-389">This alias does not offer increased clarity compared with providing a named argument to a function.</span></span>
* <span data-ttu-id="64039-390">A abreviação não se manifestará em IL compilado; é apenas um inteiro e este alias é uma compilação-tempo de construção.</span><span class="sxs-lookup"><span data-stu-id="64039-390">The abbreviation will not manifest in compiled IL; it is just an integer and this alias is a compile-time construct.</span></span>

```fsharp
module Networking =
    ...
    let send data (bufferSize: int) = ...
```

<span data-ttu-id="64039-391">Em resumo, a armadilha com abreviaturas de tipo é que **elas não** são abstrações sobre os tipos que estão abreviando.</span><span class="sxs-lookup"><span data-stu-id="64039-391">In summary, the pitfall with Type Abbreviations is that they are **not** abstractions over the types they are abbreviating.</span></span> <span data-ttu-id="64039-392">No exemplo anterior, `BufferSize` é `int` apenas um as coberturas, sem dados `int` adicionais, nem quaisquer benefícios do sistema do tipo além do que já tem.</span><span class="sxs-lookup"><span data-stu-id="64039-392">In the previous example, `BufferSize` is just an `int` under the covers, with no additional data, nor any benefits from the type system besides what `int` already has.</span></span>

<span data-ttu-id="64039-393">Uma abordagem alternativa para usar abreviaturas de tipo para representar um domínio é usar sindicatos discriminados em caso único.</span><span class="sxs-lookup"><span data-stu-id="64039-393">An alternative approach to using type abbreviations to represent a domain is to use single-case discriminated unions.</span></span> <span data-ttu-id="64039-394">A amostra anterior pode ser modelada da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="64039-394">The previous sample can be modeled as follows:</span></span>

```fsharp
type BufferSize = BufferSize of int
```

<span data-ttu-id="64039-395">Se você escrever código que opera `BufferSize` em termos e seu valor subjacente, você precisa construir um em vez de passar em qualquer inteiro arbitrário:</span><span class="sxs-lookup"><span data-stu-id="64039-395">If you write code that operates in terms of `BufferSize` and its underlying value, you need to construct one rather than pass in any arbitrary integer:</span></span>

```fsharp
module Networking =
    ...
    let send data (BufferSize size) =
    ...
```

<span data-ttu-id="64039-396">Isso reduz a probabilidade de passar erroneamente um `send` inteiro arbitrário `BufferSize` para a função, porque o chamador deve construir um tipo para envolver um valor antes de chamar a função.</span><span class="sxs-lookup"><span data-stu-id="64039-396">This reduces the likelihood of mistakenly passing an arbitrary integer into the `send` function, because the caller must construct a `BufferSize` type to wrap a value before calling the function.</span></span>
