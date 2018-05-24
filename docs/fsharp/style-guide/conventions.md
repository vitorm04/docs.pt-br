---
title: 'Convenções de codificação do F #'
description: 'Saiba mais idiomas e as diretrizes gerais ao escrever código F #.'
ms.date: 05/14/2018
ms.openlocfilehash: f3d16f735ddc1901aeaa5ebb39e2fa2b70a3d836
ms.sourcegitcommit: 43924acbdbb3981d103e11049bbe460457d42073
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/23/2018
---
# <a name="f-coding-conventions"></a><span data-ttu-id="da4c3-103">Convenções de codificação do F #</span><span class="sxs-lookup"><span data-stu-id="da4c3-103">F# coding conventions</span></span>

<span data-ttu-id="da4c3-104">As seguintes convenções são formuladas com experiência de trabalhar com grandes F # bases de código.</span><span class="sxs-lookup"><span data-stu-id="da4c3-104">The following conventions are formulated from experience working with large F# codebases.</span></span> <span data-ttu-id="da4c3-105">O [cinco princípios de código F # bom](index.md#five-principles-of-good-f-code) são a base de cada recomendação.</span><span class="sxs-lookup"><span data-stu-id="da4c3-105">The [Five principles of good F# code](index.md#five-principles-of-good-f-code) are the foundation of each recommendation.</span></span> <span data-ttu-id="da4c3-106">Estão relacionadas a [diretrizes de design do componente F #](component-design-guidelines.md), mas são aplicáveis a qualquer código F #, não apenas componentes, como bibliotecas.</span><span class="sxs-lookup"><span data-stu-id="da4c3-106">They are related to the [F# component design guidelines](component-design-guidelines.md), but are applicable for any F# code, not just components such as libraries.</span></span>

## <a name="organizing-code"></a><span data-ttu-id="da4c3-107">Organização de código</span><span class="sxs-lookup"><span data-stu-id="da4c3-107">Organizing code</span></span>

<span data-ttu-id="da4c3-108">F # apresenta duas maneiras principais de organizar código: módulos e namespaces.</span><span class="sxs-lookup"><span data-stu-id="da4c3-108">F# features two primary ways to organize code: modules and namespaces.</span></span> <span data-ttu-id="da4c3-109">Elas são semelhantes, mas têm as seguintes diferenças:</span><span class="sxs-lookup"><span data-stu-id="da4c3-109">These are similar, but do have the following differences:</span></span>

* <span data-ttu-id="da4c3-110">Namespaces são compilados como namespaces .NET.</span><span class="sxs-lookup"><span data-stu-id="da4c3-110">Namespaces are compiled as .NET namespaces.</span></span> <span data-ttu-id="da4c3-111">Módulos são compilados como classes estáticas.</span><span class="sxs-lookup"><span data-stu-id="da4c3-111">Modules are compiled as static classes.</span></span>
* <span data-ttu-id="da4c3-112">Namespaces são sempre de nível superior.</span><span class="sxs-lookup"><span data-stu-id="da4c3-112">Namespaces are always top level.</span></span> <span data-ttu-id="da4c3-113">Módulos podem ser aninhada dentro de outros módulos e de alto nível.</span><span class="sxs-lookup"><span data-stu-id="da4c3-113">Modules can be top-level and nested within other modules.</span></span>
* <span data-ttu-id="da4c3-114">Namespaces podem abranger vários arquivos.</span><span class="sxs-lookup"><span data-stu-id="da4c3-114">Namespaces can span multiple files.</span></span> <span data-ttu-id="da4c3-115">Módulos não podem.</span><span class="sxs-lookup"><span data-stu-id="da4c3-115">Modules cannot.</span></span>
* <span data-ttu-id="da4c3-116">Os módulos podem ser decorados com `[<RequireQualifiedAccess>]` e `[<AutoOpen>]`.</span><span class="sxs-lookup"><span data-stu-id="da4c3-116">Modules can be decorated with `[<RequireQualifiedAccess>]` and `[<AutoOpen>]`.</span></span>

<span data-ttu-id="da4c3-117">As diretrizes a seguir ajudará você a usá-las para organizar seu código.</span><span class="sxs-lookup"><span data-stu-id="da4c3-117">The following guidelines will help you use these to organize your code.</span></span>

### <a name="prefer-namespaces-at-the-top-level"></a><span data-ttu-id="da4c3-118">Preferir namespaces no nível superior</span><span class="sxs-lookup"><span data-stu-id="da4c3-118">Prefer namespaces at the top level</span></span>

<span data-ttu-id="da4c3-119">Para qualquer código publicamente consumível, namespaces são preferenciais para módulos no nível superior.</span><span class="sxs-lookup"><span data-stu-id="da4c3-119">For any publicly consumable code, namespaces are preferential to modules at the top level.</span></span> <span data-ttu-id="da4c3-120">Como eles são compilados como namespaces .NET, eles são consumíveis a partir de c# com nenhum problema.</span><span class="sxs-lookup"><span data-stu-id="da4c3-120">Because they are compiled as .NET namespaces, they are consumable from C# with no issue.</span></span>

```fsharp
// Good!
namespace MyCode

type MyClass() =
    ...
```

<span data-ttu-id="da4c3-121">Usando um módulo de nível superior não pode ser diferente quando chamado apenas de F #, mas para c# consumidores, os chamadores podem surpreso por ter que qualificar `MyClass` com o `MyCode` módulo.</span><span class="sxs-lookup"><span data-stu-id="da4c3-121">Using a top-level module may not appear different when called only from F#, but for C# consumers, callers may be surprised by having to qualify `MyClass` with the `MyCode` module.</span></span>

```fsharp
// Bad!
module MyCode

type MyClass() =
    ...
```

### <a name="carefully-apply-autoopen"></a><span data-ttu-id="da4c3-122">Aplicar cuidadosamente `[<AutoOpen>]`</span><span class="sxs-lookup"><span data-stu-id="da4c3-122">Carefully apply `[<AutoOpen>]`</span></span>

<span data-ttu-id="da4c3-123">O `[<AutoOpen>]` construção pode poluir o escopo do que está disponível a chamadores e a resposta para onde algo vêm é "magic".</span><span class="sxs-lookup"><span data-stu-id="da4c3-123">The `[<AutoOpen>]` construct can pollute the scope of what is available to callers, and the answer to where something comes from is "magic".</span></span> <span data-ttu-id="da4c3-124">Isso geralmente não é bom.</span><span class="sxs-lookup"><span data-stu-id="da4c3-124">This is generally not a good thing.</span></span> <span data-ttu-id="da4c3-125">Uma exceção a essa regra é a biblioteca principal do F # em si (embora esse fato também é um pouco controverso).</span><span class="sxs-lookup"><span data-stu-id="da4c3-125">An exception to this rule is the F# Core Library itself (though this fact is also a bit controversial).</span></span>

<span data-ttu-id="da4c3-126">No entanto, é uma conveniência se você tem funcionalidade auxiliar para uma API pública que você deseja organizar separadamente dessa API pública.</span><span class="sxs-lookup"><span data-stu-id="da4c3-126">However, it is a convenience if you have helper functionality for a public API that you wish to organize separately from that public API.</span></span>

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

<span data-ttu-id="da4c3-127">Isso lhe permite detalhes de implementação de separado corretamente na API pública de uma função sem ter que qualificar totalmente um auxiliar de cada vez que você chamá-lo.</span><span class="sxs-lookup"><span data-stu-id="da4c3-127">This lets you cleanly separate implementation details from the public API of a function without having to fully qualify a helper each time you call it.</span></span>

<span data-ttu-id="da4c3-128">Além disso, expor métodos de extensão e construtores de expressões no nível do namespace pode ser organizado expresso com `[<AutoOpen>]`.</span><span class="sxs-lookup"><span data-stu-id="da4c3-128">Additionally, exposing extension methods and expression builders at the namespace level can be neatly expressed with `[<AutoOpen>]`.</span></span>

### <a name="use-requirequalifiedaccess-whenever-names-could-conflict-or-you-feel-it-helps-with-readability"></a><span data-ttu-id="da4c3-129">Use `[<RequireQualifiedAccess>]` sempre que os nomes podem entrar em conflito, ou se você achar ajuda com legibilidade</span><span class="sxs-lookup"><span data-stu-id="da4c3-129">Use `[<RequireQualifiedAccess>]` whenever names could conflict or you feel it helps with readability</span></span>

<span data-ttu-id="da4c3-130">Adicionando o `[<RequireQualifiedAccess>]` atributo para um módulo indica que o módulo não pode ser aberto e que as referências aos elementos do módulo exigem explícita qualificado acesso.</span><span class="sxs-lookup"><span data-stu-id="da4c3-130">Adding the `[<RequireQualifiedAccess>]` attribute to a module indicates that the module may not be opened and that references to the elements of the module require explicit qualified access.</span></span> <span data-ttu-id="da4c3-131">Por exemplo, o `Microsoft.FSharp.Collections.List` módulo tem esse atributo.</span><span class="sxs-lookup"><span data-stu-id="da4c3-131">For example, the `Microsoft.FSharp.Collections.List` module has this attribute.</span></span>

<span data-ttu-id="da4c3-132">Isso é útil quando funções e os valores no módulo têm nomes que possam entrar em conflito com nomes em outros módulos.</span><span class="sxs-lookup"><span data-stu-id="da4c3-132">This is useful when functions and values in the module have names that are likely to conflict with names in other modules.</span></span> <span data-ttu-id="da4c3-133">Exigir acesso qualificado pode aumentar significativamente a facilidade de manutenção de longo prazo e evolvability de uma biblioteca.</span><span class="sxs-lookup"><span data-stu-id="da4c3-133">Requiring qualified access can greatly increase the long-term maintainability and evolvability of a library.</span></span>

```fsharp
[<RequireQualifiedAccess>]
module StringTokenization =
    let parse s = ...

...

let s = getAString()
let parsed = StringTokenization.parse s // Must qualify to use 'parse'
```

### <a name="sort-open-statements-topologically"></a><span data-ttu-id="da4c3-134">Classificação `open` instruções topologicamente</span><span class="sxs-lookup"><span data-stu-id="da4c3-134">Sort `open` statements topologically</span></span>

<span data-ttu-id="da4c3-135">Em F #, a ordem das declarações é importante, inclusive com `open` instruções.</span><span class="sxs-lookup"><span data-stu-id="da4c3-135">In F#, the order of declarations matters, including with `open` statements.</span></span> <span data-ttu-id="da4c3-136">Isso é diferente de c#, onde o efeito de `using` e `using static` é independente da ordenação dessas instruções em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="da4c3-136">This is unlike C#, where the effect of `using` and `using static` is independent of the ordering of those statements in a file.</span></span>

<span data-ttu-id="da4c3-137">Em F #, elementos abertos em um escopo podem sombrear outros já está presente.</span><span class="sxs-lookup"><span data-stu-id="da4c3-137">In F#, elements opened into a scope can shadow others already present.</span></span> <span data-ttu-id="da4c3-138">Isso significa que a reordenação `open` instruções podem alterar o significado do código.</span><span class="sxs-lookup"><span data-stu-id="da4c3-138">This means that reordering `open` statements could alter the meaning of code.</span></span> <span data-ttu-id="da4c3-139">Como resultado, qualquer arbitrário de classificação de todos os `open` instruções (por exemplo, ordem alfanumérica) geralmente não é recomendado, fim de que você gerar um comportamento diferente que você esperava.</span><span class="sxs-lookup"><span data-stu-id="da4c3-139">As a result, any arbitrary sorting of all `open` statements (for example, alphanumerically) is generally not recommended, lest you generate different behavior that you might expect.</span></span>

<span data-ttu-id="da4c3-140">Em vez disso, recomendamos que você classificar [topologicamente](https://en.wikipedia.org/wiki/Topological_sorting); ou seja, solicitar sua `open` instruções na ordem em que _camadas_ do sistema são definidos.</span><span class="sxs-lookup"><span data-stu-id="da4c3-140">Instead, we recommend that you sort them [topologically](https://en.wikipedia.org/wiki/Topological_sorting); that is, order your `open` statements in the order in which _layers_ of your system are defined.</span></span> <span data-ttu-id="da4c3-141">Fazendo alfanumérico de classificação em diferentes camadas topológicas também pode ser considerado.</span><span class="sxs-lookup"><span data-stu-id="da4c3-141">Doing alphanumeric sorting within different topological layers may also be considered.</span></span>

<span data-ttu-id="da4c3-142">Por exemplo, aqui está a classificação topológicas do F # compilador serviço público API arquivo:</span><span class="sxs-lookup"><span data-stu-id="da4c3-142">As an example, here is the topological sorting for the F# compiler service public API file:</span></span>

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

<span data-ttu-id="da4c3-143">Observe que uma quebra de linha separa topológicas camadas, com cada camada que estão sendo classificada ordem alfanumérica posteriormente.</span><span class="sxs-lookup"><span data-stu-id="da4c3-143">Note that a line break separates topological layers, with each layer being sorted alphanumerically afterwards.</span></span> <span data-ttu-id="da4c3-144">Isso organiza corretamente código sem sombreamento acidentalmente valores.</span><span class="sxs-lookup"><span data-stu-id="da4c3-144">This cleanly organizes code without accidentally shadowing values.</span></span>

## <a name="use-classes-to-contain-values-that-have-side-effects"></a><span data-ttu-id="da4c3-145">Usar classes para conter valores que têm efeitos colaterais</span><span class="sxs-lookup"><span data-stu-id="da4c3-145">Use classes to contain values that have side effects</span></span>

<span data-ttu-id="da4c3-146">Há muitas vezes quando a inicialização de um valor pode ter efeitos colaterais, como criar uma instância de um contexto para um banco de dados ou outro recurso remoto.</span><span class="sxs-lookup"><span data-stu-id="da4c3-146">There are many times when initializing a value can have side effects, such as instantiating a context to a database or other remote resource.</span></span> <span data-ttu-id="da4c3-147">É tentador inicializar itens em um módulo e usá-lo em funções subsequentes:</span><span class="sxs-lookup"><span data-stu-id="da4c3-147">It is tempting to initialize such things in a module and use it in subsequent functions:</span></span>

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

<span data-ttu-id="da4c3-148">Isso geralmente é uma boa ideia por alguns motivos:</span><span class="sxs-lookup"><span data-stu-id="da4c3-148">This is frequently a bad idea for a few reasons:</span></span>

<span data-ttu-id="da4c3-149">Primeiro, a configuração de aplicativo é empurrada para a base de código com `dep1` e `dep2`.</span><span class="sxs-lookup"><span data-stu-id="da4c3-149">First, application configuration is pushed into the codebase with `dep1` and `dep2`.</span></span> <span data-ttu-id="da4c3-150">Isso é difícil de manter em bases de código maior.</span><span class="sxs-lookup"><span data-stu-id="da4c3-150">This is difficult to maintain in larger codebases.</span></span>

<span data-ttu-id="da4c3-151">Dados estaticamente inicializados segundo não devem incluir valores que não são thread-safe se o componente se usar vários threads.</span><span class="sxs-lookup"><span data-stu-id="da4c3-151">Second, statically initialized data should not include values that are not thread safe if your component will itself use multiple threads.</span></span> <span data-ttu-id="da4c3-152">Isso é claramente violado por `dep3`.</span><span class="sxs-lookup"><span data-stu-id="da4c3-152">This is clearly violated by `dep3`.</span></span>

<span data-ttu-id="da4c3-153">Por fim, inicialização do módulo compila em um construtor estático para a unidade de compilação inteira.</span><span class="sxs-lookup"><span data-stu-id="da4c3-153">Finally, module initialization compiles into a static constructor for the entire compilation unit.</span></span> <span data-ttu-id="da4c3-154">Se ocorrer algum erro na inicialização do valor de limite permitem em que o módulo, ele se manifesta como um `TypeInitializationException` , em seguida, que é armazenado em cache para todo o tempo de vida do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="da4c3-154">If any error occurs in let-bound value initialization in that module, it manifests as a `TypeInitializationException` that is then cached for the entire lifetime of the application.</span></span> <span data-ttu-id="da4c3-155">Isso pode ser difícil diagnosticar.</span><span class="sxs-lookup"><span data-stu-id="da4c3-155">This can be difficult to diagnose.</span></span> <span data-ttu-id="da4c3-156">Normalmente, não há uma exceção interna que você pode tentar argumentar sobre, mas se não houver, em seguida, não há nenhum informando o que é a causa raiz.</span><span class="sxs-lookup"><span data-stu-id="da4c3-156">There is usually an inner exception that you can attempt to reason about, but if there is not, then there is no telling what the root cause is.</span></span>

<span data-ttu-id="da4c3-157">Em vez disso, use apenas uma classe simples para manter dependências:</span><span class="sxs-lookup"><span data-stu-id="da4c3-157">Instead, just use a simple class to hold dependencies:</span></span>

```fsharp
type MyParametricApi(dep1, dep2, dep3) =
    member __.Function1 arg1 = doStuffWith dep1 dep2 dep3 arg1
    member __.Function2 arg2 = doStuffWith dep1 dep2 dep3 arg2
```

<span data-ttu-id="da4c3-158">Isso permite que o seguinte:</span><span class="sxs-lookup"><span data-stu-id="da4c3-158">This enables the following:</span></span>

1. <span data-ttu-id="da4c3-159">Enviar por push qualquer estado dependente fora a própria API.</span><span class="sxs-lookup"><span data-stu-id="da4c3-159">Pushing any dependent state outside of the API itself.</span></span>
2. <span data-ttu-id="da4c3-160">Configuração agora pode ser feita fora da API.</span><span class="sxs-lookup"><span data-stu-id="da4c3-160">Configuration can now be done outside of the API.</span></span>
3. <span data-ttu-id="da4c3-161">Erros na inicialização para valores dependentes não são provavelmente manifeste como um `TypeInitializationException`.</span><span class="sxs-lookup"><span data-stu-id="da4c3-161">Errors in initialization for dependent values are not likely to manifest as a `TypeInitializationException`.</span></span>
4. <span data-ttu-id="da4c3-162">A API agora é mais fácil de testar.</span><span class="sxs-lookup"><span data-stu-id="da4c3-162">The API is now easier to test.</span></span>

## <a name="error-management"></a><span data-ttu-id="da4c3-163">Gerenciamento de erros</span><span class="sxs-lookup"><span data-stu-id="da4c3-163">Error management</span></span>

<span data-ttu-id="da4c3-164">Gerenciamento de erro em grandes sistemas é um desafio complexo e sutis e não há nenhum prata marcadores garantir que seus sistemas são tolerantes a falhas e se comportam bem.</span><span class="sxs-lookup"><span data-stu-id="da4c3-164">Error management in large systems is a complex and nuanced endeavor, and there are no silver bullets in ensuring your systems are fault-tolerant and behave well.</span></span> <span data-ttu-id="da4c3-165">As diretrizes a seguir devem oferecer diretrizes navegar neste espaço difícil.</span><span class="sxs-lookup"><span data-stu-id="da4c3-165">The following guidelines should offer guidance in navigating this difficult space.</span></span>

### <a name="represent-error-cases-and-illegal-state-in-types-intrinsic-to-your-domain"></a><span data-ttu-id="da4c3-166">Representam os casos de erro e o estado inválido em tipos intrínsecos ao seu domínio</span><span class="sxs-lookup"><span data-stu-id="da4c3-166">Represent error cases and illegal state in types intrinsic to your domain</span></span>

<span data-ttu-id="da4c3-167">Com [uniões discriminada](../language-reference/discriminated-unions.md), F # oferece a capacidade de representar o estado do programa defeituoso no seu sistema de tipo.</span><span class="sxs-lookup"><span data-stu-id="da4c3-167">With [Discriminated Unions](../language-reference/discriminated-unions.md), F# gives you the ability to represent faulty program state in your type system.</span></span> <span data-ttu-id="da4c3-168">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="da4c3-168">For example:</span></span>

```fsharp
type MoneyWithdrawalResult =
    | Success of amount:decimal
    | InsufficientFunds of balance:decimal
    | CardExpired of DateTime
    | UndisclosedFailure
```

<span data-ttu-id="da4c3-169">Nesse caso, há três maneiras de conhecidos retirando dinheiro de uma conta bancária pode falhar.</span><span class="sxs-lookup"><span data-stu-id="da4c3-169">In this case, there are three known ways that withdrawing money from a bank account can fail.</span></span> <span data-ttu-id="da4c3-170">Cada caso de erro é representado no tipo e pode, portanto, ser tratado com segurança em todo o programa.</span><span class="sxs-lookup"><span data-stu-id="da4c3-170">Each error case is represented in the type, and can thus be dealt with safely throughout the program.</span></span>

```fsharp
let handleWithdrawal amount =
    let w = withdrawMoney amount
    match w with
    | Success am -> printfn "Successfully withdrew %f" am
    | InsufficientFunds balance -> printfn "Failed: balance is %f" balance
    | CardExpired expiredDate -> printfn "Failed: card expired on %O" expiredDate
    | UndisclosedFailure -> printfn "Failed: unknown"
```

<span data-ttu-id="da4c3-171">Em geral, se você pode modelar as diferentes maneiras que algo pode **falha** em seu domínio, em seguida, código de tratamento de erros é não mais tratados como algo que você deve lidar com além de fluxo normal do programa.</span><span class="sxs-lookup"><span data-stu-id="da4c3-171">In general, if you can model the different ways that something can **fail** in your domain, then error handling code is no longer treated as something you must deal with in addition to regular program flow.</span></span> <span data-ttu-id="da4c3-172">Ele é simplesmente uma parte do fluxo normal do programa e não é considerado **excepcional**.</span><span class="sxs-lookup"><span data-stu-id="da4c3-172">It is simply a part of normal program flow, and not considered **exceptional**.</span></span> <span data-ttu-id="da4c3-173">Há duas vantagens principais para isso:</span><span class="sxs-lookup"><span data-stu-id="da4c3-173">There are two primary benefits to this:</span></span>

1. <span data-ttu-id="da4c3-174">É mais fácil de manter como seu domínio é alterado ao longo do tempo.</span><span class="sxs-lookup"><span data-stu-id="da4c3-174">It is easier to maintain as your domain changes over time.</span></span>
2. <span data-ttu-id="da4c3-175">Casos de erro são mais fáceis de teste de unidade.</span><span class="sxs-lookup"><span data-stu-id="da4c3-175">Error cases are easier to unit test.</span></span>

### <a name="use-exceptions-when-errors-cannot-be-represented-with-types"></a><span data-ttu-id="da4c3-176">Usar exceções quando erros não podem ser representados com tipos</span><span class="sxs-lookup"><span data-stu-id="da4c3-176">Use exceptions when errors cannot be represented with types</span></span>

<span data-ttu-id="da4c3-177">Nem todos os erros podem ser representados em um domínio do problema.</span><span class="sxs-lookup"><span data-stu-id="da4c3-177">Not all errors can be represented in a problem domain.</span></span> <span data-ttu-id="da4c3-178">Esses tipos de falhas são *excepcional* por natureza, portanto, a capacidade de gerar e capturar exceções em F #.</span><span class="sxs-lookup"><span data-stu-id="da4c3-178">These kinds of faults are *exceptional* in nature, hence the ability to raise and catch exceptions in F#.</span></span>

<span data-ttu-id="da4c3-179">Primeiro, é recomendável que você leia o [diretrizes de Design de exceção](../../standard/design-guidelines/exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="da4c3-179">First, it is recommended that you read the [Exception Design Guidelines](../../standard/design-guidelines/exceptions.md).</span></span> <span data-ttu-id="da4c3-180">Eles também são aplicáveis para F #.</span><span class="sxs-lookup"><span data-stu-id="da4c3-180">These are also applicable to F#.</span></span>

<span data-ttu-id="da4c3-181">As principais construções disponíveis em F # para fins de gerar exceções devem ser consideradas na seguinte ordem de preferência:</span><span class="sxs-lookup"><span data-stu-id="da4c3-181">The main constructs available in F# for the purposes of raising exceptions should be considered in the following order of preference:</span></span>

| <span data-ttu-id="da4c3-182">Função</span><span class="sxs-lookup"><span data-stu-id="da4c3-182">Function</span></span> | <span data-ttu-id="da4c3-183">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="da4c3-183">Syntax</span></span> | <span data-ttu-id="da4c3-184">Finalidade</span><span class="sxs-lookup"><span data-stu-id="da4c3-184">Purpose</span></span> |
|----------|--------|---------|
| `nullArg` | `nullArg "argumentName"` | <span data-ttu-id="da4c3-185">Gera um `System.ArgumentNullException` com o nome do argumento especificado.</span><span class="sxs-lookup"><span data-stu-id="da4c3-185">Raises a `System.ArgumentNullException` with the specified argument name.</span></span> |
| `invalidArg` | `invalidArg "argumentName" "message"` | <span data-ttu-id="da4c3-186">Gera um `System.ArgumentException` com uma mensagem e o nome do argumento especificado.</span><span class="sxs-lookup"><span data-stu-id="da4c3-186">Raises a `System.ArgumentException` with a specified argument name and message.</span></span> |
| `invalidOp` | `invalidOp "message"` | <span data-ttu-id="da4c3-187">Gera um `System.InvalidOperationException` com a mensagem especificada.</span><span class="sxs-lookup"><span data-stu-id="da4c3-187">Raises a `System.InvalidOperationException` with the specified message.</span></span> |
|`raise`| `raise (ExceptionType("message"))` | <span data-ttu-id="da4c3-188">Mecanismo de finalidade geral para lançar exceções.</span><span class="sxs-lookup"><span data-stu-id="da4c3-188">General-purpose mechanism for throwing exceptions.</span></span> |
| `failwith` | `failwith "message"` | <span data-ttu-id="da4c3-189">Gera um `System.Exception` com a mensagem especificada.</span><span class="sxs-lookup"><span data-stu-id="da4c3-189">Raises a `System.Exception` with the specified message.</span></span> |
| `failwithf` | `failwithf "format string" argForFormatString` | <span data-ttu-id="da4c3-190">Gera um `System.Exception` com uma mensagem determinada, a cadeia de caracteres de formato e suas entradas.</span><span class="sxs-lookup"><span data-stu-id="da4c3-190">Raises a `System.Exception` with a message determined by the format string and its inputs.</span></span> |

<span data-ttu-id="da4c3-191">Use `nullArg`, `invalidArg` e `invalidOp` como o mecanismo para lançar `ArgumentNullException`, `ArgumentException` e `InvalidOperationException` quando apropriado.</span><span class="sxs-lookup"><span data-stu-id="da4c3-191">Use `nullArg`, `invalidArg` and `invalidOp` as the mechanism to throw `ArgumentNullException`, `ArgumentException` and `InvalidOperationException` when appropriate.</span></span>

<span data-ttu-id="da4c3-192">O `failwith` e `failwithf` funções geralmente devem ser evitadas porque elas geram a base de `Exception` de tipo não é uma exceção específica.</span><span class="sxs-lookup"><span data-stu-id="da4c3-192">The `failwith` and `failwithf` functions should generally be avoided because they raise the base `Exception` type, not a specific exception.</span></span> <span data-ttu-id="da4c3-193">Conforme o [diretrizes de Design de exceção](../../standard/design-guidelines/exceptions.md), você deseja gerar exceções mais específicas, quando possível.</span><span class="sxs-lookup"><span data-stu-id="da4c3-193">As per the [Exception Design Guidelines](../../standard/design-guidelines/exceptions.md), you want to raise more specific exceptions when you can.</span></span>

### <a name="using-exception-handling-syntax"></a><span data-ttu-id="da4c3-194">Usando a sintaxe de manipulação de exceção</span><span class="sxs-lookup"><span data-stu-id="da4c3-194">Using exception-handling syntax</span></span>

<span data-ttu-id="da4c3-195">F # oferece suporte a padrões de exceção por meio de `try...with` sintaxe:</span><span class="sxs-lookup"><span data-stu-id="da4c3-195">F# supports exception patterns via the `try...with` syntax:</span></span>

```fsharp
try
    tryGetFileContents()
with
| :? System.IO.FileNotFoundException as e -> // Do something with it here
| :? System.Security.SecurityException as e -> // Do something with it here
```

<span data-ttu-id="da4c3-196">Reconciliar funcionalidade para executar caso ocorra uma exceção com a correspondência de padrão pode ser um pouco difícil, se você deseja manter o código de limpeza.</span><span class="sxs-lookup"><span data-stu-id="da4c3-196">Reconciling functionality to perform in the face of an exception with pattern matching can be a bit tricky if you wish to keep the code clean.</span></span> <span data-ttu-id="da4c3-197">Um modo para lidar com isso é usar [padrões ativos](../language-reference/active-patterns.md) como um meio de funcionalidade de grupos ao redor de um caso de erro com uma exceção em si.</span><span class="sxs-lookup"><span data-stu-id="da4c3-197">One such way to handle this is to use [active patterns](../language-reference/active-patterns.md) as a means to group functionality surrounding an error case with an exception itself.</span></span> <span data-ttu-id="da4c3-198">Por exemplo, você pode consumir uma API que, quando ele lança uma exceção, inclui informações importantes nos metadados de exceção.</span><span class="sxs-lookup"><span data-stu-id="da4c3-198">For example, you may be consuming an API that, when it throws an exception, encloses valuable information in the exception metadata.</span></span> <span data-ttu-id="da4c3-199">Um valor útil no corpo da exceção capturada dentro do padrão ativo o desempacotamento e retornando que o valor pode ser útil em algumas situações.</span><span class="sxs-lookup"><span data-stu-id="da4c3-199">Unwrapping a useful value in the body of the captured exception inside the Active Pattern and returning that value can be helpful in some situations.</span></span>

### <a name="do-not-use-monadic-error-handling-to-replace-exceptions"></a><span data-ttu-id="da4c3-200">Não use monadic tratamento de erros para substituir as exceções</span><span class="sxs-lookup"><span data-stu-id="da4c3-200">Do not use monadic error handling to replace exceptions</span></span>

<span data-ttu-id="da4c3-201">Exceções são vistas como um pouco um tabu em programação funcional.</span><span class="sxs-lookup"><span data-stu-id="da4c3-201">Exceptions are seen as somewhat taboo in functional programming.</span></span> <span data-ttu-id="da4c3-202">Na verdade, exceções violam pureza, portanto, é seguro considerar não é funcional.</span><span class="sxs-lookup"><span data-stu-id="da4c3-202">Indeed, exceptions violate purity, so it's safe to consider them not-quite functional.</span></span> <span data-ttu-id="da4c3-203">No entanto, isso ignora a realidade de qual código deve ser executado e que podem ocorrer erros de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="da4c3-203">However, this ignores the reality of where code must run, and that runtime errors can occur.</span></span> <span data-ttu-id="da4c3-204">Em geral, grave o código na suposição de que a maioria das tarefas são puro nem total, para minimizar as surpresas desagradáveis.</span><span class="sxs-lookup"><span data-stu-id="da4c3-204">In general, write code on the assumption that most things are neither pure nor total, to minimize unpleasant surprises.</span></span>

<span data-ttu-id="da4c3-205">É importante considerar os seguintes pontos fortes/aspectos principais de exceções em relação à sua relevância e conveniência no tempo de execução do .NET e o ecossistema de qualquer idioma como um todo:</span><span class="sxs-lookup"><span data-stu-id="da4c3-205">It is important to consider the following core strengths/aspects of Exceptions with respect to their relevance and appropriateness in the .NET runtime and cross-language ecosystem as a whole:</span></span>

1. <span data-ttu-id="da4c3-206">Elas contêm informações de diagnóstico detalhadas, que é muito útil ao depurar um problema.</span><span class="sxs-lookup"><span data-stu-id="da4c3-206">They contain detailed diagnostic information, which is very helpful when debugging an issue.</span></span>
2. <span data-ttu-id="da4c3-207">Eles são bem compreendidos pelo tempo de execução e outras linguagens .NET.</span><span class="sxs-lookup"><span data-stu-id="da4c3-207">They are well-understood by the runtime and other .NET languages.</span></span>
3. <span data-ttu-id="da4c3-208">Eles podem reduzir boilerplate significativa em comparação com o código que sai do seu caminho para *evitar* exceções implementando algum subconjunto dos seu semântica em uma base ad hoc.</span><span class="sxs-lookup"><span data-stu-id="da4c3-208">They can reduce significant boilerplate when compared with code that goes out of its way to *avoid* exceptions by implementing some subset of their semantics on an ad-hoc basis.</span></span>

<span data-ttu-id="da4c3-209">Esse terceiro ponto é crítico.</span><span class="sxs-lookup"><span data-stu-id="da4c3-209">This third point is critical.</span></span> <span data-ttu-id="da4c3-210">Para operações complexas não triviais, não use exceções pode resultar em lidar com estruturas como este:</span><span class="sxs-lookup"><span data-stu-id="da4c3-210">For nontrivial complex operations, failing to use exceptions can result in dealing with structures like this:</span></span>

```fsharp
Result<Result<MyType, string>, string list>
```

<span data-ttu-id="da4c3-211">Facilmente, que pode levar a código frágil como padrões coincidentes em erros de "stringly digitado":</span><span class="sxs-lookup"><span data-stu-id="da4c3-211">Which can easily lead to fragile code like pattern matching on "stringly-typed" errors:</span></span>

```fsharp
let result = doStuff()
match result with
| Ok r -> ...
| Error e ->
    if e.Contains "Error string 1" then ...
    elif e.Contains "Error string 2" then ...
    else ... // Who knows?
```

<span data-ttu-id="da4c3-212">Além disso, ele pode ser tentador assimilar qualquer exceção no desejo de uma função "simples" que retorna um tipo de "melhor":</span><span class="sxs-lookup"><span data-stu-id="da4c3-212">Additionally, it can be tempting to swallow any exception in the desire for a "simple" function that returns a "nicer" type:</span></span>

```fsharp
// This is bad!
let tryReadAllText (path : string) =
    try System.IO.File.ReadAllText path |> Some
    with _ -> None
```

<span data-ttu-id="da4c3-213">Infelizmente, `tryReadAllText` pode gerar várias exceções com base em uma infinidade de coisas que podem acontecer em um sistema de arquivos e, em seguida, esse código imediatamente descarta todas as informações sobre o que pode ser entrar errado em seu ambiente.</span><span class="sxs-lookup"><span data-stu-id="da4c3-213">Unfortunately, `tryReadAllText` can throw numerous exceptions based on the myriad of things that can happen on a file system, and this code discards away any information about what might actually be going wrong in your environment.</span></span> <span data-ttu-id="da4c3-214">Se você substituir esse código com um tipo de resultado, você está para análise de mensagem de erro "stringly digitado":</span><span class="sxs-lookup"><span data-stu-id="da4c3-214">If you replace this code with a result type, then you're back to "stringly-typed" error message parsing:</span></span>

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

<span data-ttu-id="da4c3-215">E colocar o próprio objeto de exceção no `Error` construtor apenas força lidar corretamente com o tipo de exceção no site de chamada em vez de na função.</span><span class="sxs-lookup"><span data-stu-id="da4c3-215">And placing the exception object itself in the `Error` constructor just forces you to properly deal with the exception type at the call site rather than in the function.</span></span> <span data-ttu-id="da4c3-216">Isso efetivamente cria exceções verificadas, que são notoriamente unfun lidar com como um chamador de uma API.</span><span class="sxs-lookup"><span data-stu-id="da4c3-216">Doing this effectively creates checked exceptions, which are notoriously unfun to deal with as a caller of an API.</span></span>

<span data-ttu-id="da4c3-217">É uma boa alternativa para os exemplos anteriores capturar *específico* exceções e retornar um valor significativo no contexto dessa exceção.</span><span class="sxs-lookup"><span data-stu-id="da4c3-217">A good alternative to the above examples is to catch *specific* exceptions and return a meaningful value in the context of that exception.</span></span> <span data-ttu-id="da4c3-218">Se você modificar o `tryReadAllText` funciona da seguinte maneira `None` tem um significado mais:</span><span class="sxs-lookup"><span data-stu-id="da4c3-218">If you modify the `tryReadAllText` function as follows, `None` has more meaning:</span></span>

```fsharp
let tryReadAllTextIfPresent (path : string) =
    try System.IO.File.ReadAllText path |> Some
    with :? FileNotFoundException -> None
```

<span data-ttu-id="da4c3-219">Em vez de funcionar como uma pega-tudo, essa função agora manipulará corretamente o caso quando um arquivo não foi encontrado e atribuir esse significado para retornar.</span><span class="sxs-lookup"><span data-stu-id="da4c3-219">Instead of functioning as a catch-all, this function will now properly handle the case when a file was not found and assign that meaning to a return.</span></span> <span data-ttu-id="da4c3-220">Esse valor de retorno pode mapear para esse caso de erro, enquanto não descartar todas as informações contextuais ou forçar os chamadores para lidar com uma situação que não pode ser relevante nesse ponto no código.</span><span class="sxs-lookup"><span data-stu-id="da4c3-220">This return value can map to that error case, while not discarding any contextual information or forcing callers to deal with a case that may not be relevant at that point in the code.</span></span>

<span data-ttu-id="da4c3-221">Tipos, como `Result<'Success, 'Error>` são apropriadas para operações básicas de onde eles não são aninhados, e tipos F # opcionais são perfeitos para representar quando algo foi devolva *algo* ou *nada*.</span><span class="sxs-lookup"><span data-stu-id="da4c3-221">Types such as `Result<'Success, 'Error>` are appropriate for basic operations where they aren't nested, and F# optional types are perfect for representing when something could either return *something* or *nothing*.</span></span> <span data-ttu-id="da4c3-222">Eles não são uma substituição para exceções, porém e não devem ser usados em uma tentativa de substituir exceções.</span><span class="sxs-lookup"><span data-stu-id="da4c3-222">They are not a replacement for exceptions, though, and should not be used in an attempt to replace exceptions.</span></span> <span data-ttu-id="da4c3-223">Em vez disso, eles devem ser aplicados criteriosamente para aspectos específicos de endereço de exceção e a política de gerenciamento de erro de maneiras de destino.</span><span class="sxs-lookup"><span data-stu-id="da4c3-223">Rather, they should be applied judiciously to address specific aspects of exception and error management policy in targeted ways.</span></span>

## <a name="partial-application-and-point-free-programming"></a><span data-ttu-id="da4c3-224">Aplicativo parcial e livre de ponto de programação</span><span class="sxs-lookup"><span data-stu-id="da4c3-224">Partial application and point-free programming</span></span>

<span data-ttu-id="da4c3-225">F # oferece suporte a aplicativo parcial e, assim, várias formas de programa em um estilo livre de ponto.</span><span class="sxs-lookup"><span data-stu-id="da4c3-225">F# supports partial application, and thus, various ways to program in a point-free style.</span></span> <span data-ttu-id="da4c3-226">Isso pode ser útil para reutilização de código dentro de um módulo ou a implementação de algo, mas geralmente não é algo para expor publicamente.</span><span class="sxs-lookup"><span data-stu-id="da4c3-226">This can be beneficial for code reuse within a module or the implementation of something, but it is generally not something to expose publicly.</span></span> <span data-ttu-id="da4c3-227">Em geral, livre de ponto de programação não é um porque, por si só e pode adicionar uma barreira cognitiva significativa para as pessoas que não tenha o estilo.</span><span class="sxs-lookup"><span data-stu-id="da4c3-227">In general, point-free programming is not a virtue in and of itself, and can add a significant cognitive barrier for people who are not immersed in the style.</span></span>

### <a name="do-not-use-partial-application-and-currying-in-public-apis"></a><span data-ttu-id="da4c3-228">Não usar o aplicativo parcial e currying em APIs públicas</span><span class="sxs-lookup"><span data-stu-id="da4c3-228">Do not use partial application and currying in public APIs</span></span>

<span data-ttu-id="da4c3-229">Com poucas exceções, o uso do aplicativo parcial em APIs públicas pode confundir os consumidores.</span><span class="sxs-lookup"><span data-stu-id="da4c3-229">With little exception, the use of partial application in public APIs can be confusing for consumers.</span></span> <span data-ttu-id="da4c3-230">Normalmente, `let`-são valores de limite no código F # **valores**, não **valores de função**.</span><span class="sxs-lookup"><span data-stu-id="da4c3-230">Usually, `let`-bound values in F# code are **values**, not **function values**.</span></span> <span data-ttu-id="da4c3-231">Combinação de valores e valores de função juntos pode resultar em Salvar um pequeno número de linhas de código em troca de uma grande quantidade de sobrecarga cognitiva, especialmente se combinado com operadores, como `>>` para compor funções.</span><span class="sxs-lookup"><span data-stu-id="da4c3-231">Mixing together values and function values can result in saving a small number of lines of code in exchange for quite a bit of cognitive overhead, especially if combined with operators such as `>>` to compose functions.</span></span>

### <a name="consider-the-tooling-implications-for-point-free-programming"></a><span data-ttu-id="da4c3-232">Considere as implicações de ferramentas para liberar o ponto de programação</span><span class="sxs-lookup"><span data-stu-id="da4c3-232">Consider the tooling implications for point-free programming</span></span>

<span data-ttu-id="da4c3-233">Funções na forma curried não rótulo seus argumentos.</span><span class="sxs-lookup"><span data-stu-id="da4c3-233">Curried functions do not label their arguments.</span></span> <span data-ttu-id="da4c3-234">Isso tem implicações de ferramentas.</span><span class="sxs-lookup"><span data-stu-id="da4c3-234">This has tooling implications.</span></span> <span data-ttu-id="da4c3-235">Considere as duas funções a seguir:</span><span class="sxs-lookup"><span data-stu-id="da4c3-235">Consider the following two functions:</span></span>

```fsharp
let func name age =
    printfn "My name is %s and I am %d years old!" name age

let funcWithApplication =
    printfn "My name is %s and I am %d years old!"
```

<span data-ttu-id="da4c3-236">Ambos são funções válidas, mas `funcWithApplication` é uma função na forma curried.</span><span class="sxs-lookup"><span data-stu-id="da4c3-236">Both are valid functions, but `funcWithApplication` is a curried function.</span></span> <span data-ttu-id="da4c3-237">Quando você focaliza seus tipos em um editor, você verá:</span><span class="sxs-lookup"><span data-stu-id="da4c3-237">When you hover over their types in an editor, you see this:</span></span>

```fsharp
val func : name:string -> age:int -> unit

val funcWithApplication : (string -> int -> unit)
```

<span data-ttu-id="da4c3-238">No site de chamada, dicas de ferramenta em ferramentas como o Visual Studio não fornecerá informações significativas sobre o que o `string` e `int` realmente representam tipos de entrada.</span><span class="sxs-lookup"><span data-stu-id="da4c3-238">At the call site, tooltips in tooling such as Visual Studio will not give you meaningful information as to what the `string` and `int` input types actually represent.</span></span>

<span data-ttu-id="da4c3-239">Se você encontrar livre de ponto de código como `funcWithApplication` que é consumível publicamente, é recomendável fazer uma expansão de η completa para que as ferramentas podem escolher até diante nomes significativos para argumentos.</span><span class="sxs-lookup"><span data-stu-id="da4c3-239">If you encounter point-free code like `funcWithApplication` that is publicly consumable, it is recommended to do a full η-expansion so that tooling can pick up on meaningful names for arguments.</span></span>

<span data-ttu-id="da4c3-240">Além disso, depurando livre de ponto de código pode ser um desafio, se não impossível.</span><span class="sxs-lookup"><span data-stu-id="da4c3-240">Furthermore, debugging point-free code can be challenging, if not impossible.</span></span> <span data-ttu-id="da4c3-241">Ferramentas de depuração contam com os valores associados aos nomes (por exemplo, `let` associações) para que você pode inspecionar o Centro de valores intermediários por meio da execução.</span><span class="sxs-lookup"><span data-stu-id="da4c3-241">Debugging tools rely on values bound to names (for example, `let` bindings) so that you can inspect intermediate values midway through execution.</span></span> <span data-ttu-id="da4c3-242">Quando seu código não tem valores para inspecionar, não há nada para depurar.</span><span class="sxs-lookup"><span data-stu-id="da4c3-242">When your code has no values to inspect, there is nothing to debug.</span></span> <span data-ttu-id="da4c3-243">No futuro, as ferramentas de depuração podem evoluir para sintetizar esses valores com base em caminhos executados anteriormente, mas não é uma boa ideia para restringir suas opções em *potencial* funcionalidades de depuração.</span><span class="sxs-lookup"><span data-stu-id="da4c3-243">In the future, debugging tools may evolve to synthesize these values based on previously executed paths, but it's not a good idea to hedge your bets on *potential* debugging functionality.</span></span>

### <a name="consider-partial-application-as-a-technique-to-reduce-internal-boilerplate"></a><span data-ttu-id="da4c3-244">Considere a possibilidade de aplicativo parcial como uma técnica para reduzir boilerplate interno</span><span class="sxs-lookup"><span data-stu-id="da4c3-244">Consider partial application as a technique to reduce internal boilerplate</span></span>

<span data-ttu-id="da4c3-245">Em contraste com o ponto anterior, o aplicativo parcial é uma ferramenta bons para reduzir boilerplate dentro de um aplicativo ou os recursos internos de mais de uma API.</span><span class="sxs-lookup"><span data-stu-id="da4c3-245">In contrast to the previous point, partial application is a wonderful tool for reducing boilerplate inside of an application or the deeper internals of an API.</span></span> <span data-ttu-id="da4c3-246">Ele pode ser útil para a implementação das APIs mais complicado, onde boilerplate geralmente é um problema para lidar com teste de unidade.</span><span class="sxs-lookup"><span data-stu-id="da4c3-246">It can be helpful for unit testing the implementation of more complicated APIs, where boilerplate is often a pain to deal with.</span></span> <span data-ttu-id="da4c3-247">Por exemplo, o código a seguir mostra como é possível realizar quais estruturas fictícias mais proporcionam sem colocar uma dependência externa em tal estrutura e aprender um relacionados bespoke API.</span><span class="sxs-lookup"><span data-stu-id="da4c3-247">For example, the following code shows how you can accomplish what most mocking frameworks give you without taking an external dependency on such a framework and having to learn a related bespoke API.</span></span>

<span data-ttu-id="da4c3-248">Por exemplo, considere a topografia de solução a seguir:</span><span class="sxs-lookup"><span data-stu-id="da4c3-248">For example, consider the following solution topography:</span></span>

```
MySolution.sln
|_/ImplementationLogic.fsproj
|_/ImplementationLogic.Tests.fsproj
|_/API.fsproj
```

<span data-ttu-id="da4c3-249">`ImplementationLogic.fsproj` pode expor o código, como:</span><span class="sxs-lookup"><span data-stu-id="da4c3-249">`ImplementationLogic.fsproj` might expose code such as:</span></span>

```fsharp
module Transactions =
    let doTransaction txnContext txnType balance =
        ...

type Transactor(ctx, currentBalance) =
    member __.ExecuteTransaction(txnType) =
        Transactions.doTransaction ctx txtType currentBalance
        ...
```

<span data-ttu-id="da4c3-250">Teste de unidade `Transactions.doTransaction` em `ImplementationLogic.Tests.fspoj` é fácil:</span><span class="sxs-lookup"><span data-stu-id="da4c3-250">Unit testing `Transactions.doTransaction` in `ImplementationLogic.Tests.fspoj` is easy:</span></span>

```fsharp
namespace TransactionsTestingUtil

open Transactions

module TransactionsTestable =
    let getTestableTransactionRoutine mockContext = Transactions.doTransaction mockContext
```

<span data-ttu-id="da4c3-251">Aplicando parcialmente `doTransaction` com um contexto de simulação o objeto permite que você chame a função em todos os testes de unidade sem a necessidade de construir um contexto fictícios cada vez:</span><span class="sxs-lookup"><span data-stu-id="da4c3-251">Partially applying `doTransaction` with a mocking context object lets you call the function in all of your unit tests without needing to construct a mocked context each time:</span></span>

```fsharp
namespace TransactionTests

open Xunit
open TransactionTypes
open TransactionsTestingUtil
open TransactionsTestingUtil.TransactionsTestable

let testableContext =
    { new ITransactionContext with
        member __.TheFirstMember() = ...
        member __.TheSecondMember() = ... }

let transactionRoutine = getTestableTransactionRoutine testableContext

[<Fact>]
let ``Test withdrawal transaction with 0.0 for balance``() =
    let expected = ...
    let actual = transactionRoutine TransactionType.Withdraw 0.0
    Assert.Equal(expected, actual)
```

<span data-ttu-id="da4c3-252">Essa técnica não deve ser aplicada universalmente a sua base de código inteiro, mas é uma boa maneira de reduzir clichê para operações internas complicadas e os recursos internos de teste de unidade.</span><span class="sxs-lookup"><span data-stu-id="da4c3-252">This technique should not be universally applied to your entire codebase, but it is a good way to reduce boilerplate for complicated internals and unit testing those internals.</span></span>

## <a name="access-control"></a><span data-ttu-id="da4c3-253">Controle de acesso</span><span class="sxs-lookup"><span data-stu-id="da4c3-253">Access control</span></span>

<span data-ttu-id="da4c3-254">F # tem várias opções para [controle de acesso](../language-reference/access-control.md), herdado do que está disponível no tempo de execução .NET.</span><span class="sxs-lookup"><span data-stu-id="da4c3-254">F# has multiple options for [Access control](../language-reference/access-control.md), inherited from what is available in the .NET runtime.</span></span> <span data-ttu-id="da4c3-255">Eles não são úteis apenas para tipos de-você pode usá-los para funções, muito.</span><span class="sxs-lookup"><span data-stu-id="da4c3-255">These are not just usable for types - you can use them for functions, too.</span></span>

* <span data-ttu-id="da4c3-256">Preferir não`public` tipos e membros até que você precisa para ser consumível publicamente.</span><span class="sxs-lookup"><span data-stu-id="da4c3-256">Prefer non-`public` types and members until you need them to be publicly consumable.</span></span> <span data-ttu-id="da4c3-257">Isso também minimiza que alguns consumidores para</span><span class="sxs-lookup"><span data-stu-id="da4c3-257">This also minimizes what consumers couple to</span></span>
* <span data-ttu-id="da4c3-258">Tentar manter todas as funcionalidades de auxiliar `private`.</span><span class="sxs-lookup"><span data-stu-id="da4c3-258">Strive to keep all helper functionality `private`.</span></span>
* <span data-ttu-id="da4c3-259">Considere o uso de `[<AutoOpen>]` em um módulo privado de funções auxiliares se eles se tornarem vários.</span><span class="sxs-lookup"><span data-stu-id="da4c3-259">Consider the use of `[<AutoOpen>]` on a private module of helper functions if they become numerous.</span></span>

## <a name="type-inference-and-generics"></a><span data-ttu-id="da4c3-260">Inferência de tipo e genéricos</span><span class="sxs-lookup"><span data-stu-id="da4c3-260">Type inference and generics</span></span>

<span data-ttu-id="da4c3-261">Inferência de tipo pode salvar da digitação muita boilerplate.</span><span class="sxs-lookup"><span data-stu-id="da4c3-261">Type inference can save you from typing a lot of boilerplate.</span></span> <span data-ttu-id="da4c3-262">E generalização automática no compilador F # pode ajudá-lo a escrever mais códigos genéricos com quase nenhum esforço adicional de sua parte.</span><span class="sxs-lookup"><span data-stu-id="da4c3-262">And automatic generalization in the F# compiler can help you write more generic code with almost no extra effort on your part.</span></span> <span data-ttu-id="da4c3-263">No entanto, esses recursos não são bons universalmente.</span><span class="sxs-lookup"><span data-stu-id="da4c3-263">However, these features are not universally good.</span></span>

* <span data-ttu-id="da4c3-264">Considere a rotulagem de nomes de argumentos com tipos explícitos em APIs públicas e não dependem de inferência de tipo para isso.</span><span class="sxs-lookup"><span data-stu-id="da4c3-264">Consider labeling argument names with explicit types in public APIs and do not rely on type inference for this.</span></span>

    <span data-ttu-id="da4c3-265">A razão para isso é que **você** devem estar no controle da forma de sua API, não o compilador.</span><span class="sxs-lookup"><span data-stu-id="da4c3-265">The reason for this is that **you** should be in control of the shape of your API, not the compiler.</span></span> <span data-ttu-id="da4c3-266">Embora o compilador pode fazer um bom trabalho em inferindo tipos para você, é possível ter a forma de sua alteração de API se os componentes internos depende alterou tipos.</span><span class="sxs-lookup"><span data-stu-id="da4c3-266">Although the compiler can do a fine job at inferring types for you, it is possible to have the shape of your API change if the internals it relies on have changed types.</span></span> <span data-ttu-id="da4c3-267">Isso pode ser o que você deseja, mas provavelmente resultará em uma alteração de API de quebra que os consumidores de downstream terá de lidar com.</span><span class="sxs-lookup"><span data-stu-id="da4c3-267">This may be what you want, but it will almost certainly result in a breaking API change that downstream consumers will then have to deal with.</span></span> <span data-ttu-id="da4c3-268">Em vez disso, se você controlar a forma de sua API pública explicitamente, você pode controlar essas alterações significativas.</span><span class="sxs-lookup"><span data-stu-id="da4c3-268">Instead, if you explicitly control the shape of your public API, then you can control these breaking changes.</span></span> <span data-ttu-id="da4c3-269">Em termos DDD, isso pode ser pensado como uma camada contra dano.</span><span class="sxs-lookup"><span data-stu-id="da4c3-269">In DDD terms, this can be thought of as an Anti-corruption layer.</span></span>

* <span data-ttu-id="da4c3-270">É recomendável atribuir um nome significativo para seus argumentos genéricos.</span><span class="sxs-lookup"><span data-stu-id="da4c3-270">Consider giving a meaningful name to your generic arguments.</span></span>

    <span data-ttu-id="da4c3-271">A menos que você está escrevendo código realmente genérico que não é específico para um domínio específico, um nome significativo pode ajudar outros programadores Noções básicas sobre o domínio que está trabalhando.</span><span class="sxs-lookup"><span data-stu-id="da4c3-271">Unless you are writing truly generic code that is not specific to a particular domain, a meaningful name can help other programmers understanding the domain they're working in.</span></span> <span data-ttu-id="da4c3-272">Por exemplo, um parâmetro de tipo denominado `'Document` no contexto de interagir com um documento de banco de dados torna mais claro de que tipos de documento genérico podem ser aceito para a função ou um membro que você está trabalhando com.</span><span class="sxs-lookup"><span data-stu-id="da4c3-272">For example, a type parameter named `'Document` in the context of interacting with a document database makes it clearer that generic document types can be accepted by the function or member you are working with.</span></span>

* <span data-ttu-id="da4c3-273">Considere a possibilidade de nomenclatura de parâmetros de tipo genérico com PascalCase.</span><span class="sxs-lookup"><span data-stu-id="da4c3-273">Consider naming generic type parameters with PascalCase.</span></span>

    <span data-ttu-id="da4c3-274">Essa é a maneira geral para fazer coisas no .NET, portanto, é recomendável que você use PascalCase em vez de snake_case ou camelCase.</span><span class="sxs-lookup"><span data-stu-id="da4c3-274">This is the general way to do things in .NET, so it's recommended that you use PascalCase rather than snake_case or camelCase.</span></span>

<span data-ttu-id="da4c3-275">Por fim, generalização automática nem sempre é um recurso para as pessoas que são novos para F # ou uma grande base de código.</span><span class="sxs-lookup"><span data-stu-id="da4c3-275">Finally, automatic generalization is not always a boon for people who are new to F# or a large codebase.</span></span> <span data-ttu-id="da4c3-276">Há sobrecarga cognitiva usando componentes genéricos.</span><span class="sxs-lookup"><span data-stu-id="da4c3-276">There is cognitive overhead in using components that are generic.</span></span> <span data-ttu-id="da4c3-277">Além disso, se automaticamente generalizadas funções não são usadas com diferentes tipos de entrada (permitem apenas se eles se destinam a ser usada como tal), não há nenhum benefício real-los sendo genérico no momento.</span><span class="sxs-lookup"><span data-stu-id="da4c3-277">Furthermore, if automatically generalized functions are not used with different input types (let alone if they are intended to be used as such), then there is no real benefit to them being generic at that point in time.</span></span> <span data-ttu-id="da4c3-278">Sempre considere se o código que você está escrevendo realmente se beneficiam sendo genérico.</span><span class="sxs-lookup"><span data-stu-id="da4c3-278">Always consider if the code you are writing will actually benefit from being generic.</span></span>

## <a name="performance"></a><span data-ttu-id="da4c3-279">Desempenho</span><span class="sxs-lookup"><span data-stu-id="da4c3-279">Performance</span></span>

<span data-ttu-id="da4c3-280">Valores de F # são imutáveis por padrão, o que permite que você evite determinadas classes de bugs (especialmente as que envolvem simultaneidade e paralelismo).</span><span class="sxs-lookup"><span data-stu-id="da4c3-280">F# values are immutable by default, which allows you to avoid certain classes of bugs (especially those involving concurrency and parallelism).</span></span> <span data-ttu-id="da4c3-281">No entanto, em alguns casos, para obter eficiência ideal (ou até mesmo razoável) de tempo de execução ou as alocações de memória, um intervalo de trabalho pode melhor ser implementado usando mutação no local do estado.</span><span class="sxs-lookup"><span data-stu-id="da4c3-281">However, in certain cases, in order to achieve optimal (or even reasonable) efficiency of execution time or memory allocations, a span of work may best be implemented by using in-place mutation of state.</span></span> <span data-ttu-id="da4c3-282">Isso é possível em uma base de aceitação com F # com o `mutable` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="da4c3-282">This is possible in an opt-in basis with F# with the `mutable` keyword.</span></span>

<span data-ttu-id="da4c3-283">No entanto, usar `mutable` em F # podem achar acordo pureza funcional.</span><span class="sxs-lookup"><span data-stu-id="da4c3-283">However, use of `mutable` in F# may feel at odds with functional purity.</span></span> <span data-ttu-id="da4c3-284">Isso é bom, se você ajustar as expectativas de pureza para [transparência referencial](https://en.wikipedia.org/wiki/Referential_transparency).</span><span class="sxs-lookup"><span data-stu-id="da4c3-284">This is fine, if you adjust expectations from purity to [referential transparency](https://en.wikipedia.org/wiki/Referential_transparency).</span></span> <span data-ttu-id="da4c3-285">Transparência referencial - não pureza - é o objetivo final ao escrever funções F #.</span><span class="sxs-lookup"><span data-stu-id="da4c3-285">Referential transparency - not purity - is the end goal when writing F# functions.</span></span> <span data-ttu-id="da4c3-286">Isso permite que você escreva uma interface funcional em uma implementação baseada em mutação para código crítico de desempenho.</span><span class="sxs-lookup"><span data-stu-id="da4c3-286">This allows you to write a functional interface over a mutation-based implementation for performance critical code.</span></span>

### <a name="wrap-mutable-code-in-immutable-interfaces"></a><span data-ttu-id="da4c3-287">Encapsular um código mutável interfaces imutáveis</span><span class="sxs-lookup"><span data-stu-id="da4c3-287">Wrap mutable code in immutable interfaces</span></span>

<span data-ttu-id="da4c3-288">Com transparência referencial como uma meta, é essencial para escrever código que não expõe o underbelly mutável de funções críticas de desempenho.</span><span class="sxs-lookup"><span data-stu-id="da4c3-288">With referential transparency as a goal, it is critical to write code that does not expose the mutable underbelly of performance-critical functions.</span></span> <span data-ttu-id="da4c3-289">Por exemplo, o código a seguir implementa a `Array.contains` função na biblioteca F # principais:</span><span class="sxs-lookup"><span data-stu-id="da4c3-289">For example, the following code implements the `Array.contains` function in the F# core library:</span></span>

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

<span data-ttu-id="da4c3-290">Chamar essa função várias vezes alterará a matriz subjacente nem exigem manter qualquer estado mutável no consumi-las.</span><span class="sxs-lookup"><span data-stu-id="da4c3-290">Calling this function multiple times does not change the underlying array, nor does it require you to maintain any mutable state in consuming it.</span></span> <span data-ttu-id="da4c3-291">É origem transparente, mesmo que quase todas as linhas de código em seu usa mutação.</span><span class="sxs-lookup"><span data-stu-id="da4c3-291">It is referentially transparent, even though almost every line of code within it uses mutation.</span></span>

### <a name="consider-encapsulating-mutable-data-in-classes"></a><span data-ttu-id="da4c3-292">Considere a possibilidade de encapsulamento de dados mutável em classes</span><span class="sxs-lookup"><span data-stu-id="da4c3-292">Consider encapsulating mutable data in classes</span></span>

<span data-ttu-id="da4c3-293">O exemplo anterior usado uma única função para encapsular operações usando dados mutável.</span><span class="sxs-lookup"><span data-stu-id="da4c3-293">The previous example used a single function to encapsulate operations using mutable data.</span></span> <span data-ttu-id="da4c3-294">Isso sempre não é suficiente para mais conjuntos de dados.</span><span class="sxs-lookup"><span data-stu-id="da4c3-294">This is not always sufficient for more complex sets of data.</span></span> <span data-ttu-id="da4c3-295">Considere os seguintes conjuntos de funções:</span><span class="sxs-lookup"><span data-stu-id="da4c3-295">Consider the following sets of functions:</span></span>

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

<span data-ttu-id="da4c3-296">Esse código é funcional, mas expõe a estrutura de dados com base em mutação que os chamadores são responsáveis por manter.</span><span class="sxs-lookup"><span data-stu-id="da4c3-296">This code is performant, but it exposes the mutation-based data structure that callers are responsible for maintaining.</span></span> <span data-ttu-id="da4c3-297">Isso pode ser encapsulado dentro de uma classe com não membros subjacentes que pode alterar:</span><span class="sxs-lookup"><span data-stu-id="da4c3-297">This can be wrapped inside of a class with no underlying members that can change:</span></span>

```fsharp
open System.Collections.Generic

/// The results of computing the LALR(1) closure of an LR(0) kernel
type Closure1Table() =
    let t = Dictionary<Item0, HashSet<TerminalIndex>>()

    member __.Add(key, value) =
        if not (t.ContainsKey(key)) then
            t.Add(key, value)
        else
            t.[key] <- value

    member __.Count = t.Count

    member __.Contains(key, value) =
        match t.TryGetValue(key) with
        | (true, v) -> v.Equals(value)
        | (false, _) -> false
```

<span data-ttu-id="da4c3-298">`Closure1Table` encapsula a estrutura de dados com base em mutação subjacente, assim, não forçar chamadores para manter a estrutura de dados subjacente.</span><span class="sxs-lookup"><span data-stu-id="da4c3-298">`Closure1Table` encapsulates the underlying mutation-based data structure, thereby not forcing callers to maintain the underlying data structure.</span></span> <span data-ttu-id="da4c3-299">Classes são uma maneira eficiente para encapsular dados e rotinas que são baseados em mutação sem expor os detalhes para chamadores.</span><span class="sxs-lookup"><span data-stu-id="da4c3-299">Classes are a powerful way to encapsulate data and routines that are mutation-based without exposing the details to callers.</span></span>

### <a name="prefer-let-mutable-to-reference-cells"></a><span data-ttu-id="da4c3-300">Preferir `let mutable` às células de referência</span><span class="sxs-lookup"><span data-stu-id="da4c3-300">Prefer `let mutable` to reference cells</span></span>

<span data-ttu-id="da4c3-301">As células de referência são uma forma de representar a referência a um valor em vez do próprio valor.</span><span class="sxs-lookup"><span data-stu-id="da4c3-301">Reference cells are a way to represent the reference to a value rather than the value itself.</span></span> <span data-ttu-id="da4c3-302">Embora possam ser usados para código crítico em termos de desempenho, eles geralmente não são recomendados.</span><span class="sxs-lookup"><span data-stu-id="da4c3-302">Although they can be used for performance-critical code, they are generally not recommended.</span></span> <span data-ttu-id="da4c3-303">Considere o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="da4c3-303">Consider the following example:</span></span>

```fsharp
let kernels =
    let acc = ref Set.empty

    processWorkList startKernels (fun kernel ->
        if not ((!acc).Contains(kernel)) then
            acc := (!acc).Add(kernel)
        ...)

    !acc |> Seq.toList
```

<span data-ttu-id="da4c3-304">O uso de uma célula de referência "polui" todo o código subsequente com precisar cancelar e referenciar novamente os dados subjacentes.</span><span class="sxs-lookup"><span data-stu-id="da4c3-304">The use of a reference cell now "pollutes" all subsequent code with having to dereference and re-reference the underlying data.</span></span> <span data-ttu-id="da4c3-305">Em vez disso, considere a possibilidade de `let mutable`:</span><span class="sxs-lookup"><span data-stu-id="da4c3-305">Instead, consider `let mutable`:</span></span>

```fsharp
let kernels =
    let mutable acc = Set.empty

    processWorkList startKernels (fun kernel ->
        if not (acc.Contains(kernel)) then
            acc <- acc.Add(kernel)
        ...)

    acc |> Seq.toList
```

<span data-ttu-id="da4c3-306">O ponto único de mutação no meio da expressão lambda, além de todos os outros códigos toca `acc` pode fazer isso de forma que não é diferente para o uso de um normal `let`-valor imutável associada.</span><span class="sxs-lookup"><span data-stu-id="da4c3-306">Aside from the single point of mutation in the middle of the lambda expression, all other code that touches `acc` can do so in a manner that is no different to the usage of a normal `let`-bound immutable value.</span></span> <span data-ttu-id="da4c3-307">Isso tornará mais fácil mudar ao longo do tempo.</span><span class="sxs-lookup"><span data-stu-id="da4c3-307">This will make it easier to change over time.</span></span>

## <a name="object-programming"></a><span data-ttu-id="da4c3-308">Objeto de programação</span><span class="sxs-lookup"><span data-stu-id="da4c3-308">Object programming</span></span>

<span data-ttu-id="da4c3-309">F # tem total suporte para objetos e conceitos (OO) e orientada a objeto.</span><span class="sxs-lookup"><span data-stu-id="da4c3-309">F# has full support for objects and object-oriented (OO) concepts.</span></span> <span data-ttu-id="da4c3-310">Embora muitos conceitos OO são úteis e eficientes, nem todos eles são ideais para uso.</span><span class="sxs-lookup"><span data-stu-id="da4c3-310">Although many OO concepts are powerful and useful, not all of them are ideal to use.</span></span> <span data-ttu-id="da4c3-311">As listas a seguir oferecem orientação sobre categorias de recursos OO em um alto nível.</span><span class="sxs-lookup"><span data-stu-id="da4c3-311">The following lists offer guidance on categories of OO features at a high level.</span></span>

<span data-ttu-id="da4c3-312">**Considere o uso desses recursos em muitas situações:**</span><span class="sxs-lookup"><span data-stu-id="da4c3-312">**Consider using these features in many situations:**</span></span>

* <span data-ttu-id="da4c3-313">A notação de ponto (`x.Length`)</span><span class="sxs-lookup"><span data-stu-id="da4c3-313">Dot notation (`x.Length`)</span></span>
* <span data-ttu-id="da4c3-314">Membros de instância</span><span class="sxs-lookup"><span data-stu-id="da4c3-314">Instance members</span></span>
* <span data-ttu-id="da4c3-315">Construtores implícita</span><span class="sxs-lookup"><span data-stu-id="da4c3-315">Implicit constructors</span></span>
* <span data-ttu-id="da4c3-316">Membros estáticos</span><span class="sxs-lookup"><span data-stu-id="da4c3-316">Static members</span></span>
* <span data-ttu-id="da4c3-317">Notação de indexador (`arr.[x]`)</span><span class="sxs-lookup"><span data-stu-id="da4c3-317">Indexer notation (`arr.[x]`)</span></span>
* <span data-ttu-id="da4c3-318">Argumentos nomeados e opcionais</span><span class="sxs-lookup"><span data-stu-id="da4c3-318">Named and Optional arguments</span></span>
* <span data-ttu-id="da4c3-319">Interfaces e implementações de interface</span><span class="sxs-lookup"><span data-stu-id="da4c3-319">Interfaces and interface implementations</span></span>

<span data-ttu-id="da4c3-320">**Não acessar esses recursos pela primeira vez, mas aplicá-las cuidado quando for convenientes resolver um problema:**</span><span class="sxs-lookup"><span data-stu-id="da4c3-320">**Don't reach for these features first, but do judiciously apply them when they are convenient to solve a problem:**</span></span>

* <span data-ttu-id="da4c3-321">Sobrecarga de método</span><span class="sxs-lookup"><span data-stu-id="da4c3-321">Method overloading</span></span>
* <span data-ttu-id="da4c3-322">Dados mutáveis encapsulados</span><span class="sxs-lookup"><span data-stu-id="da4c3-322">Encapsulated mutable data</span></span>
* <span data-ttu-id="da4c3-323">Operadores em tipos</span><span class="sxs-lookup"><span data-stu-id="da4c3-323">Operators on types</span></span>
* <span data-ttu-id="da4c3-324">Propriedades automática</span><span class="sxs-lookup"><span data-stu-id="da4c3-324">Auto properties</span></span>
* <span data-ttu-id="da4c3-325">Implementando `IDisposable` e `IEnumerable`</span><span class="sxs-lookup"><span data-stu-id="da4c3-325">Implementing `IDisposable` and `IEnumerable`</span></span>
* <span data-ttu-id="da4c3-326">Extensões de tipo</span><span class="sxs-lookup"><span data-stu-id="da4c3-326">Type extensions</span></span>
* <span data-ttu-id="da4c3-327">Eventos</span><span class="sxs-lookup"><span data-stu-id="da4c3-327">Events</span></span>
* <span data-ttu-id="da4c3-328">Structs</span><span class="sxs-lookup"><span data-stu-id="da4c3-328">Structs</span></span>
* <span data-ttu-id="da4c3-329">Delegados</span><span class="sxs-lookup"><span data-stu-id="da4c3-329">Delegates</span></span>
* <span data-ttu-id="da4c3-330">Enums</span><span class="sxs-lookup"><span data-stu-id="da4c3-330">Enums</span></span>

<span data-ttu-id="da4c3-331">**Em geral, evite esses recursos, a menos que você deve usá-los:**</span><span class="sxs-lookup"><span data-stu-id="da4c3-331">**Generally avoid these features unless you must use them:**</span></span>

* <span data-ttu-id="da4c3-332">Hierarquias de herança com base no tipo e a implementação de herança</span><span class="sxs-lookup"><span data-stu-id="da4c3-332">Inheritance-based type hierarchies and implementation inheritance</span></span>
* <span data-ttu-id="da4c3-333">Valores nulos e `Unchecked.defaultof<_>`</span><span class="sxs-lookup"><span data-stu-id="da4c3-333">Nulls and `Unchecked.defaultof<_>`</span></span>

### <a name="prefer-composition-over-inheritance"></a><span data-ttu-id="da4c3-334">Prefira a herança de composição</span><span class="sxs-lookup"><span data-stu-id="da4c3-334">Prefer composition over inheritance</span></span>

<span data-ttu-id="da4c3-335">[Composição de herança](https://en.wikipedia.org/wiki/Composition_over_inheritance) é um idioma longa pode cumprir bom código F #.</span><span class="sxs-lookup"><span data-stu-id="da4c3-335">[Composition over inheritance](https://en.wikipedia.org/wiki/Composition_over_inheritance) is a long-standing idiom that good F# code can adhere to.</span></span> <span data-ttu-id="da4c3-336">O princípio fundamental é que você não deve expor uma classe base e forçar os chamadores herdam da classe base para obter funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="da4c3-336">The fundamental principle is that you should not expose a base class and force callers to inherit from that base class to get functionality.</span></span>

### <a name="use-object-expressions-to-implement-interfaces-if-you-dont-need-a-class"></a><span data-ttu-id="da4c3-337">Usar expressões de objeto para implementar interfaces se não precisar de uma classe</span><span class="sxs-lookup"><span data-stu-id="da4c3-337">Use object expressions to implement interfaces if you don't need a class</span></span>

<span data-ttu-id="da4c3-338">[Expressões de objeto](../language-reference/object-expressions.md) permitem que você implemente as interfaces em tempo real, associação a interface implementada como um valor sem a necessidade de fazer isso dentro de uma classe.</span><span class="sxs-lookup"><span data-stu-id="da4c3-338">[Object Expressions](../language-reference/object-expressions.md) allow you to implement interfaces on the fly, binding the implemented interface to a value without needing to do so inside of a class.</span></span> <span data-ttu-id="da4c3-339">Isso é prático, especialmente se você _somente_ precisa implementar a interface e não precisam de uma classe completa.</span><span class="sxs-lookup"><span data-stu-id="da4c3-339">This is convenient, especially if you _only_ need to implement the interface and have no need for a full class.</span></span>

<span data-ttu-id="da4c3-340">Por exemplo, aqui está o código que é executado em [Ionide](http://ionide.io/) para fornecer uma ação de correção de código, se você tiver adicionado um símbolo que você não tem um `open` instrução para:</span><span class="sxs-lookup"><span data-stu-id="da4c3-340">For example, here is the code that is run in [Ionide](http://ionide.io/) to provide a code fix action if you've added a symbol that you don't have an `open` statement for:</span></span>

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

<span data-ttu-id="da4c3-341">Como não é necessário para uma classe ao interagir com a API de código do Visual Studio, expressões de objeto são uma ferramenta ideal para isso.</span><span class="sxs-lookup"><span data-stu-id="da4c3-341">Because there is no need for a class when interacting with the Visual Studio Code API, Object Expressions are an ideal tool for this.</span></span> <span data-ttu-id="da4c3-342">Eles também são úteis para teste de unidade, quando você quiser stub em uma interface com rotinas de teste de maneira ad hoc.</span><span class="sxs-lookup"><span data-stu-id="da4c3-342">They are also valuable for unit testing, when you want to stub out an interface with test routines in an ad hoc manner.</span></span>

## <a name="type-abbreviations"></a><span data-ttu-id="da4c3-343">Abreviações de tipo</span><span class="sxs-lookup"><span data-stu-id="da4c3-343">Type Abbreviations</span></span>

<span data-ttu-id="da4c3-344">[Abreviações de tipo](../language-reference/type-abbreviations.md) são uma maneira conveniente para atribuir um rótulo para outro tipo, como uma assinatura de função ou um tipo mais complexo.</span><span class="sxs-lookup"><span data-stu-id="da4c3-344">[Type Abbreviations](../language-reference/type-abbreviations.md) are a convenient way to assign a label to another type, such as a function signature or a more complex type.</span></span> <span data-ttu-id="da4c3-345">Por exemplo, o alias a seguir atribui um rótulo para o que é necessário definir uma computação com [CNTK](https://www.microsoft.com/cognitive-toolkit/), um profundo aprendizado biblioteca:</span><span class="sxs-lookup"><span data-stu-id="da4c3-345">For example, the following alias assigns a label to what's needed to define a computation with [CNTK](https://www.microsoft.com/cognitive-toolkit/), a deep learning library:</span></span>

```fsharp
open CNTK

// DeviceDescriptor, Variable, and Function all come from CNTK
type Computation = DeviceDescriptor -> Variable -> Function
```

<span data-ttu-id="da4c3-346">O `Computation` nome é uma maneira conveniente para indicar qualquer função que corresponda à assinatura que é um alias.</span><span class="sxs-lookup"><span data-stu-id="da4c3-346">The `Computation` name is a convenient way to denote any function that matches the signature it is aliasing.</span></span> <span data-ttu-id="da4c3-347">Usando abreviações de tipo como isso é conveniente e permite que o código mais sucinto.</span><span class="sxs-lookup"><span data-stu-id="da4c3-347">Using Type Abbreviations like this is convenient and allows for more succinct code.</span></span>

### <a name="avoid-using-type-abbreviations-to-represent-your-domain"></a><span data-ttu-id="da4c3-348">Evite usar abreviações de tipo para representar seu domínio</span><span class="sxs-lookup"><span data-stu-id="da4c3-348">Avoid using Type Abbreviations to represent your domain</span></span>

<span data-ttu-id="da4c3-349">Embora as abreviações de tipo são convenientes para dar um nome para assinaturas de função, eles podem ser confusos quando abreviando outros tipos.</span><span class="sxs-lookup"><span data-stu-id="da4c3-349">Although Type Abbreviations are convenient for giving a name to function signatures, they can be confusing when abbreviating other types.</span></span> <span data-ttu-id="da4c3-350">Considere esta abreviação:</span><span class="sxs-lookup"><span data-stu-id="da4c3-350">Consider this abbreviation:</span></span>

```fsharp
// Does not actually abstract integers.
type BufferSize = int
```

<span data-ttu-id="da4c3-351">Isso pode ser confuso de várias maneiras:</span><span class="sxs-lookup"><span data-stu-id="da4c3-351">This can be confusing in multiple ways:</span></span>

* <span data-ttu-id="da4c3-352">`BufferSize` não é uma abstração; ele é apenas outro nome de um número inteiro.</span><span class="sxs-lookup"><span data-stu-id="da4c3-352">`BufferSize` is not an abstraction; it is just another name for an integer.</span></span>
* <span data-ttu-id="da4c3-353">Se `BufferSize` é exposto em uma API pública, ele pode facilmente ser interpretados incorretamente significa mais do que apenas `int`.</span><span class="sxs-lookup"><span data-stu-id="da4c3-353">If `BufferSize` is exposed in a public API, it can easily be misinterpreted to mean more than just `int`.</span></span> <span data-ttu-id="da4c3-354">Em geral, os tipos de domínio tem vários atributos a eles e não são tipos primitivos como `int`.</span><span class="sxs-lookup"><span data-stu-id="da4c3-354">Generally, domain types have multiple attributes to them and are not primitive types like `int`.</span></span> <span data-ttu-id="da4c3-355">Esta abreviação viola essa suposição.</span><span class="sxs-lookup"><span data-stu-id="da4c3-355">This abbreviation violates that assumption.</span></span>
* <span data-ttu-id="da4c3-356">O uso de maiusculas e minúsculas de `BufferSize` (PascalCase) indica que esse tipo armazena mais dados.</span><span class="sxs-lookup"><span data-stu-id="da4c3-356">The casing of `BufferSize` (PascalCase) implies that this type holds more data.</span></span>
* <span data-ttu-id="da4c3-357">Este alias não oferece maior clareza, em comparação com o fornecimento de um argumento nomeado para uma função.</span><span class="sxs-lookup"><span data-stu-id="da4c3-357">This alias does not offer increased clarity compared with providing a named argument to a function.</span></span>
* <span data-ttu-id="da4c3-358">A abreviação não será manifesto em IL compilado; ele é apenas um inteiro e esse alias é uma construção de tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="da4c3-358">The abbreviation will not manifest in compiled IL; it is just an integer and this alias is a compile-time construct.</span></span>

```fsharp
module Networking =
    ...
    let send data (bufferSize: int) =
        ...
```

<span data-ttu-id="da4c3-359">Em resumo, as armadilhas com abreviações de tipo são que eles são **não** abstrações sobre os tipos que são abreviando.</span><span class="sxs-lookup"><span data-stu-id="da4c3-359">In summary, the pitfall with Type Abbreviations is that they are **not** abstractions over the types they are abbreviating.</span></span> <span data-ttu-id="da4c3-360">No exemplo anterior, `BufferSize` é apenas um `int` nos bastidores, com nenhum dado adicionais nem qualquer benefícios do sistema de tipo, além de quais `int` já tem.</span><span class="sxs-lookup"><span data-stu-id="da4c3-360">In the previous example, `BufferSize` is just an `int` under the covers, with no additional data, nor any benefits from the type system besides what `int` already has.</span></span>
