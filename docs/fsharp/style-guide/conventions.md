---
title: 'Convenções de codificação do F #'
description: 'Saiba mais linguagens e as diretrizes gerais ao escrever código F #.'
ms.date: 05/14/2018
ms.openlocfilehash: 21119b6d69e00f359104bfb6eab7681bdbfb8d78
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/02/2018
ms.locfileid: "49087382"
---
# <a name="f-coding-conventions"></a><span data-ttu-id="8ecad-103">Convenções de codificação do F #</span><span class="sxs-lookup"><span data-stu-id="8ecad-103">F# coding conventions</span></span>

<span data-ttu-id="8ecad-104">As seguintes convenções são formuladas de experiência trabalhando com o F # grandes bases de código.</span><span class="sxs-lookup"><span data-stu-id="8ecad-104">The following conventions are formulated from experience working with large F# codebases.</span></span> <span data-ttu-id="8ecad-105">O [cinco princípios de código F # boa](index.md#five-principles-of-good-f-code) são a base de cada recomendação.</span><span class="sxs-lookup"><span data-stu-id="8ecad-105">The [Five principles of good F# code](index.md#five-principles-of-good-f-code) are the foundation of each recommendation.</span></span> <span data-ttu-id="8ecad-106">Estão relacionadas com o [diretrizes de design do componente F #](component-design-guidelines.md), mas são aplicáveis a qualquer código F #, não apenas componentes, como bibliotecas.</span><span class="sxs-lookup"><span data-stu-id="8ecad-106">They are related to the [F# component design guidelines](component-design-guidelines.md), but are applicable for any F# code, not just components such as libraries.</span></span>

## <a name="organizing-code"></a><span data-ttu-id="8ecad-107">Organizando o código</span><span class="sxs-lookup"><span data-stu-id="8ecad-107">Organizing code</span></span>

<span data-ttu-id="8ecad-108">F # possui duas maneiras principais de organizar o código: módulos e namespaces.</span><span class="sxs-lookup"><span data-stu-id="8ecad-108">F# features two primary ways to organize code: modules and namespaces.</span></span> <span data-ttu-id="8ecad-109">Elas são semelhantes, mas têm as seguintes diferenças:</span><span class="sxs-lookup"><span data-stu-id="8ecad-109">These are similar, but do have the following differences:</span></span>

* <span data-ttu-id="8ecad-110">Namespaces são compilados como namespaces .NET.</span><span class="sxs-lookup"><span data-stu-id="8ecad-110">Namespaces are compiled as .NET namespaces.</span></span> <span data-ttu-id="8ecad-111">Módulos são compilados como classes estáticas.</span><span class="sxs-lookup"><span data-stu-id="8ecad-111">Modules are compiled as static classes.</span></span>
* <span data-ttu-id="8ecad-112">Namespaces são sempre de nível superior.</span><span class="sxs-lookup"><span data-stu-id="8ecad-112">Namespaces are always top level.</span></span> <span data-ttu-id="8ecad-113">Módulos podem ser aninhadas dentro de outros módulos e de alto nível.</span><span class="sxs-lookup"><span data-stu-id="8ecad-113">Modules can be top-level and nested within other modules.</span></span>
* <span data-ttu-id="8ecad-114">Namespaces podem abranger vários arquivos.</span><span class="sxs-lookup"><span data-stu-id="8ecad-114">Namespaces can span multiple files.</span></span> <span data-ttu-id="8ecad-115">Módulos não podem.</span><span class="sxs-lookup"><span data-stu-id="8ecad-115">Modules cannot.</span></span>
* <span data-ttu-id="8ecad-116">Módulos poderão ser decorados com `[<RequireQualifiedAccess>]` e `[<AutoOpen>]`.</span><span class="sxs-lookup"><span data-stu-id="8ecad-116">Modules can be decorated with `[<RequireQualifiedAccess>]` and `[<AutoOpen>]`.</span></span>

<span data-ttu-id="8ecad-117">As diretrizes a seguir ajudará você a usá-los para organizar seu código.</span><span class="sxs-lookup"><span data-stu-id="8ecad-117">The following guidelines will help you use these to organize your code.</span></span>

### <a name="prefer-namespaces-at-the-top-level"></a><span data-ttu-id="8ecad-118">Prefira namespaces no nível superior</span><span class="sxs-lookup"><span data-stu-id="8ecad-118">Prefer namespaces at the top level</span></span>

<span data-ttu-id="8ecad-119">Para qualquer código publicamente consumível, namespaces são preferenciais para módulos de nível superior.</span><span class="sxs-lookup"><span data-stu-id="8ecad-119">For any publicly consumable code, namespaces are preferential to modules at the top level.</span></span> <span data-ttu-id="8ecad-120">Como eles são compilados como namespaces .NET, eles são consumíveis do c# com nenhum problema.</span><span class="sxs-lookup"><span data-stu-id="8ecad-120">Because they are compiled as .NET namespaces, they are consumable from C# with no issue.</span></span>

```fsharp
// Good!
namespace MyCode

type MyClass() =
    ...
```

<span data-ttu-id="8ecad-121">Usando um módulo de nível superior não pode aparecer diferente quando chamado apenas de F #, mas para consumidores de c#, os chamadores podem ficar surpreso por ter que qualificar `MyClass` com o `MyCode` módulo.</span><span class="sxs-lookup"><span data-stu-id="8ecad-121">Using a top-level module may not appear different when called only from F#, but for C# consumers, callers may be surprised by having to qualify `MyClass` with the `MyCode` module.</span></span>

```fsharp
// Bad!
module MyCode

type MyClass() =
    ...
```

### <a name="carefully-apply-autoopen"></a><span data-ttu-id="8ecad-122">Aplicar com cuidado `[<AutoOpen>]`</span><span class="sxs-lookup"><span data-stu-id="8ecad-122">Carefully apply `[<AutoOpen>]`</span></span>

<span data-ttu-id="8ecad-123">O `[<AutoOpen>]` construção pode poluam o escopo do que está disponível para chamadores, e a resposta para onde algo vêm é "mágica".</span><span class="sxs-lookup"><span data-stu-id="8ecad-123">The `[<AutoOpen>]` construct can pollute the scope of what is available to callers, and the answer to where something comes from is "magic".</span></span> <span data-ttu-id="8ecad-124">Geralmente isso não é algo bom.</span><span class="sxs-lookup"><span data-stu-id="8ecad-124">This is generally not a good thing.</span></span> <span data-ttu-id="8ecad-125">Uma exceção a essa regra é a biblioteca principal de F # em si (embora esse fato também é um pouco controverso).</span><span class="sxs-lookup"><span data-stu-id="8ecad-125">An exception to this rule is the F# Core Library itself (though this fact is also a bit controversial).</span></span>

<span data-ttu-id="8ecad-126">No entanto, ele é uma conveniência, se você tem a funcionalidade de auxiliar para uma API pública que você deseja organizar de separadamente da API pública.</span><span class="sxs-lookup"><span data-stu-id="8ecad-126">However, it is a convenience if you have helper functionality for a public API that you wish to organize separately from that public API.</span></span>

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

<span data-ttu-id="8ecad-127">Isso lhe dá os detalhes de implementação de separadas corretamente da API pública de uma função sem precisar qualificar totalmente um auxiliar de cada vez que você chamá-lo.</span><span class="sxs-lookup"><span data-stu-id="8ecad-127">This lets you cleanly separate implementation details from the public API of a function without having to fully qualify a helper each time you call it.</span></span>

<span data-ttu-id="8ecad-128">Além disso, expor métodos de extensão e construtores de expressões no nível do namespace pode ser claramente expresso com `[<AutoOpen>]`.</span><span class="sxs-lookup"><span data-stu-id="8ecad-128">Additionally, exposing extension methods and expression builders at the namespace level can be neatly expressed with `[<AutoOpen>]`.</span></span>

### <a name="use-requirequalifiedaccess-whenever-names-could-conflict-or-you-feel-it-helps-with-readability"></a><span data-ttu-id="8ecad-129">Use `[<RequireQualifiedAccess>]` sempre que nomes possam entrar em conflito ou você acha que eles ajudam a facilitar a leitura</span><span class="sxs-lookup"><span data-stu-id="8ecad-129">Use `[<RequireQualifiedAccess>]` whenever names could conflict or you feel it helps with readability</span></span>

<span data-ttu-id="8ecad-130">Adicionando o `[<RequireQualifiedAccess>]` atributo a um módulo indica que o módulo não pode ser aberto e que as referências aos elementos do módulo exigem explícita qualificados acesso.</span><span class="sxs-lookup"><span data-stu-id="8ecad-130">Adding the `[<RequireQualifiedAccess>]` attribute to a module indicates that the module may not be opened and that references to the elements of the module require explicit qualified access.</span></span> <span data-ttu-id="8ecad-131">Por exemplo, o `Microsoft.FSharp.Collections.List` módulo tem esse atributo.</span><span class="sxs-lookup"><span data-stu-id="8ecad-131">For example, the `Microsoft.FSharp.Collections.List` module has this attribute.</span></span>

<span data-ttu-id="8ecad-132">Isso é útil quando funções e valores no módulo têm nomes que têm probabilidade de entrar em conflito com nomes em outros módulos.</span><span class="sxs-lookup"><span data-stu-id="8ecad-132">This is useful when functions and values in the module have names that are likely to conflict with names in other modules.</span></span> <span data-ttu-id="8ecad-133">Exigir acesso qualificado pode aumentar muito a manutenção de longo prazo e a capacidade de evolução de uma biblioteca.</span><span class="sxs-lookup"><span data-stu-id="8ecad-133">Requiring qualified access can greatly increase the long-term maintainability and evolvability of a library.</span></span>

```fsharp
[<RequireQualifiedAccess>]
module StringTokenization =
    let parse s = ...

...

let s = getAString()
let parsed = StringTokenization.parse s // Must qualify to use 'parse'
```

### <a name="sort-open-statements-topologically"></a><span data-ttu-id="8ecad-134">Classificação `open` instruções topologicamente</span><span class="sxs-lookup"><span data-stu-id="8ecad-134">Sort `open` statements topologically</span></span>

<span data-ttu-id="8ecad-135">No F #, a ordem das declarações é importante, inclusive com `open` instruções.</span><span class="sxs-lookup"><span data-stu-id="8ecad-135">In F#, the order of declarations matters, including with `open` statements.</span></span> <span data-ttu-id="8ecad-136">Isso é diferente do c#, onde o efeito `using` e `using static` é independente da ordenação dessas instruções em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="8ecad-136">This is unlike C#, where the effect of `using` and `using static` is independent of the ordering of those statements in a file.</span></span>

<span data-ttu-id="8ecad-137">No F #, os elementos abertos em um escopo podem sombrear outras pessoas já está presente.</span><span class="sxs-lookup"><span data-stu-id="8ecad-137">In F#, elements opened into a scope can shadow others already present.</span></span> <span data-ttu-id="8ecad-138">Isso significa que reordenar `open` instruções podem alterar o significado do código.</span><span class="sxs-lookup"><span data-stu-id="8ecad-138">This means that reordering `open` statements could alter the meaning of code.</span></span> <span data-ttu-id="8ecad-139">Como resultado, qualquer arbitrário de classificação de todas as `open` instruções (por exemplo, em ordem alfanumérica) geralmente não é recomendado, deixa que você gerar um comportamento diferente que você poderia esperar.</span><span class="sxs-lookup"><span data-stu-id="8ecad-139">As a result, any arbitrary sorting of all `open` statements (for example, alphanumerically) is generally not recommended, lest you generate different behavior that you might expect.</span></span>

<span data-ttu-id="8ecad-140">Em vez disso, é recomendável que você classificar [topologicamente](https://en.wikipedia.org/wiki/Topological_sorting); ou seja, solicitar sua `open` instruções na ordem em que _camadas_ do seu sistema são definidos.</span><span class="sxs-lookup"><span data-stu-id="8ecad-140">Instead, we recommend that you sort them [topologically](https://en.wikipedia.org/wiki/Topological_sorting); that is, order your `open` statements in the order in which _layers_ of your system are defined.</span></span> <span data-ttu-id="8ecad-141">Fazendo alfanumérico de classificação em diferentes camadas topológicas também pode ser considerado.</span><span class="sxs-lookup"><span data-stu-id="8ecad-141">Doing alphanumeric sorting within different topological layers may also be considered.</span></span>

<span data-ttu-id="8ecad-142">Por exemplo, aqui está a classificação topológica F # compilador arquivo de serviço público API:</span><span class="sxs-lookup"><span data-stu-id="8ecad-142">As an example, here is the topological sorting for the F# compiler service public API file:</span></span>

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

<span data-ttu-id="8ecad-143">Observe que uma quebra de linha separa topológicas camadas, com cada camada que está sendo classificada em ordem alfanumérica posteriormente.</span><span class="sxs-lookup"><span data-stu-id="8ecad-143">Note that a line break separates topological layers, with each layer being sorted alphanumerically afterwards.</span></span> <span data-ttu-id="8ecad-144">Isso organiza o código corretamente sem acidentalmente sombreamento valores.</span><span class="sxs-lookup"><span data-stu-id="8ecad-144">This cleanly organizes code without accidentally shadowing values.</span></span>

## <a name="use-classes-to-contain-values-that-have-side-effects"></a><span data-ttu-id="8ecad-145">Classes de uso para armazenar valores que têm efeitos colaterais</span><span class="sxs-lookup"><span data-stu-id="8ecad-145">Use classes to contain values that have side effects</span></span>

<span data-ttu-id="8ecad-146">Há muitas vezes quando a inicialização de um valor pode ter efeitos colaterais, como criar uma instância de um contexto para um banco de dados ou outro recurso remoto.</span><span class="sxs-lookup"><span data-stu-id="8ecad-146">There are many times when initializing a value can have side effects, such as instantiating a context to a database or other remote resource.</span></span> <span data-ttu-id="8ecad-147">É tentador para inicializar essas coisas em um módulo e usá-lo em funções subsequentes:</span><span class="sxs-lookup"><span data-stu-id="8ecad-147">It is tempting to initialize such things in a module and use it in subsequent functions:</span></span>

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

<span data-ttu-id="8ecad-148">Isso frequentemente é uma má ideia por alguns motivos:</span><span class="sxs-lookup"><span data-stu-id="8ecad-148">This is frequently a bad idea for a few reasons:</span></span>

<span data-ttu-id="8ecad-149">Em primeiro lugar, a configuração de aplicativo é empurrada para a base de código com `dep1` e `dep2`.</span><span class="sxs-lookup"><span data-stu-id="8ecad-149">First, application configuration is pushed into the codebase with `dep1` and `dep2`.</span></span> <span data-ttu-id="8ecad-150">Isso é difícil de manter em bases de código maiores.</span><span class="sxs-lookup"><span data-stu-id="8ecad-150">This is difficult to maintain in larger codebases.</span></span>

<span data-ttu-id="8ecad-151">Segundo, inicializados estaticamente dados não devem incluir valores que não são thread-safe se seu componente em si usará vários threads.</span><span class="sxs-lookup"><span data-stu-id="8ecad-151">Second, statically initialized data should not include values that are not thread safe if your component will itself use multiple threads.</span></span> <span data-ttu-id="8ecad-152">Isso é claramente violado por `dep3`.</span><span class="sxs-lookup"><span data-stu-id="8ecad-152">This is clearly violated by `dep3`.</span></span>

<span data-ttu-id="8ecad-153">Por fim, a inicialização do módulo compila em um construtor estático para a unidade de compilação inteiro.</span><span class="sxs-lookup"><span data-stu-id="8ecad-153">Finally, module initialization compiles into a static constructor for the entire compilation unit.</span></span> <span data-ttu-id="8ecad-154">Se ocorrer algum erro na inicialização do valor de associação let nesse módulo, ele se manifesta como um `TypeInitializationException` , em seguida, que é armazenado em cache para o tempo de vida inteiro do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8ecad-154">If any error occurs in let-bound value initialization in that module, it manifests as a `TypeInitializationException` that is then cached for the entire lifetime of the application.</span></span> <span data-ttu-id="8ecad-155">Isso pode ser difícil de diagnosticar.</span><span class="sxs-lookup"><span data-stu-id="8ecad-155">This can be difficult to diagnose.</span></span> <span data-ttu-id="8ecad-156">Normalmente, há uma exceção interna que você pode tentar justificar, mas se não houver, em seguida, não há nenhuma informar o que é a causa raiz.</span><span class="sxs-lookup"><span data-stu-id="8ecad-156">There is usually an inner exception that you can attempt to reason about, but if there is not, then there is no telling what the root cause is.</span></span>

<span data-ttu-id="8ecad-157">Em vez disso, use apenas uma classe simples para manter as dependências:</span><span class="sxs-lookup"><span data-stu-id="8ecad-157">Instead, just use a simple class to hold dependencies:</span></span>

```fsharp
type MyParametricApi(dep1, dep2, dep3) =
    member __.Function1 arg1 = doStuffWith dep1 dep2 dep3 arg1
    member __.Function2 arg2 = doStuffWith dep1 dep2 dep3 arg2
```

<span data-ttu-id="8ecad-158">Isso permite que o seguinte:</span><span class="sxs-lookup"><span data-stu-id="8ecad-158">This enables the following:</span></span>

1. <span data-ttu-id="8ecad-159">Enviar por push qualquer estado dependente fora da API propriamente dita.</span><span class="sxs-lookup"><span data-stu-id="8ecad-159">Pushing any dependent state outside of the API itself.</span></span>
2. <span data-ttu-id="8ecad-160">Configuração agora pode ser feita fora da API.</span><span class="sxs-lookup"><span data-stu-id="8ecad-160">Configuration can now be done outside of the API.</span></span>
3. <span data-ttu-id="8ecad-161">Erros na inicialização para valores dependentes não provavelmente se manifestar como um `TypeInitializationException`.</span><span class="sxs-lookup"><span data-stu-id="8ecad-161">Errors in initialization for dependent values are not likely to manifest as a `TypeInitializationException`.</span></span>
4. <span data-ttu-id="8ecad-162">A API agora é mais fácil de testar.</span><span class="sxs-lookup"><span data-stu-id="8ecad-162">The API is now easier to test.</span></span>

## <a name="error-management"></a><span data-ttu-id="8ecad-163">Gerenciamento de erros</span><span class="sxs-lookup"><span data-stu-id="8ecad-163">Error management</span></span>

<span data-ttu-id="8ecad-164">Gerenciamento de erros em sistemas de grande porte é um empreendimento sutil e complexo, e não há nenhum silver marcadores garantir que seus sistemas são tolerantes a falhas e se comportam bem.</span><span class="sxs-lookup"><span data-stu-id="8ecad-164">Error management in large systems is a complex and nuanced endeavor, and there are no silver bullets in ensuring your systems are fault-tolerant and behave well.</span></span> <span data-ttu-id="8ecad-165">As diretrizes a seguir devem oferecer diretrizes esse espaço difíceis de navegar.</span><span class="sxs-lookup"><span data-stu-id="8ecad-165">The following guidelines should offer guidance in navigating this difficult space.</span></span>

### <a name="represent-error-cases-and-illegal-state-in-types-intrinsic-to-your-domain"></a><span data-ttu-id="8ecad-166">Representam os casos de erro e o estado ilegal em tipos intrínsecos ao seu domínio</span><span class="sxs-lookup"><span data-stu-id="8ecad-166">Represent error cases and illegal state in types intrinsic to your domain</span></span>

<span data-ttu-id="8ecad-167">Com o [uniões discriminadas](../language-reference/discriminated-unions.md), F # oferece a capacidade de representar o estado do programa com defeito no seu sistema de tipos.</span><span class="sxs-lookup"><span data-stu-id="8ecad-167">With [Discriminated Unions](../language-reference/discriminated-unions.md), F# gives you the ability to represent faulty program state in your type system.</span></span> <span data-ttu-id="8ecad-168">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="8ecad-168">For example:</span></span>

```fsharp
type MoneyWithdrawalResult =
    | Success of amount:decimal
    | InsufficientFunds of balance:decimal
    | CardExpired of DateTime
    | UndisclosedFailure
```

<span data-ttu-id="8ecad-169">Nesse caso, há três maneiras conhecidas que pode falhar, retirando dinheiro de uma conta bancária.</span><span class="sxs-lookup"><span data-stu-id="8ecad-169">In this case, there are three known ways that withdrawing money from a bank account can fail.</span></span> <span data-ttu-id="8ecad-170">Cada caso de erro é representado no tipo e pode, portanto, ser tratado com segurança em todo o programa.</span><span class="sxs-lookup"><span data-stu-id="8ecad-170">Each error case is represented in the type, and can thus be dealt with safely throughout the program.</span></span>

```fsharp
let handleWithdrawal amount =
    let w = withdrawMoney amount
    match w with
    | Success am -> printfn "Successfully withdrew %f" am
    | InsufficientFunds balance -> printfn "Failed: balance is %f" balance
    | CardExpired expiredDate -> printfn "Failed: card expired on %O" expiredDate
    | UndisclosedFailure -> printfn "Failed: unknown"
```

<span data-ttu-id="8ecad-171">Em geral, se você pode modelar as diferentes maneiras de que algo pode **falhar** em seu domínio, em seguida, código de tratamento de erro é não mais tratado como algo que você deve lidar com além do fluxo de programa regular.</span><span class="sxs-lookup"><span data-stu-id="8ecad-171">In general, if you can model the different ways that something can **fail** in your domain, then error handling code is no longer treated as something you must deal with in addition to regular program flow.</span></span> <span data-ttu-id="8ecad-172">Ele é simplesmente uma parte do fluxo normal do programa e não é considerado **excepcionais**.</span><span class="sxs-lookup"><span data-stu-id="8ecad-172">It is simply a part of normal program flow, and not considered **exceptional**.</span></span> <span data-ttu-id="8ecad-173">Há duas vantagens principais para isso:</span><span class="sxs-lookup"><span data-stu-id="8ecad-173">There are two primary benefits to this:</span></span>

1. <span data-ttu-id="8ecad-174">Ele é mais fácil manter seu domínio que as alterações ao longo do tempo.</span><span class="sxs-lookup"><span data-stu-id="8ecad-174">It is easier to maintain as your domain changes over time.</span></span>
2. <span data-ttu-id="8ecad-175">Casos de erro são mais fáceis de teste de unidade.</span><span class="sxs-lookup"><span data-stu-id="8ecad-175">Error cases are easier to unit test.</span></span>

### <a name="use-exceptions-when-errors-cannot-be-represented-with-types"></a><span data-ttu-id="8ecad-176">Use as exceções quando erros não podem ser representados com tipos</span><span class="sxs-lookup"><span data-stu-id="8ecad-176">Use exceptions when errors cannot be represented with types</span></span>

<span data-ttu-id="8ecad-177">Nem todos os erros podem ser representados em um domínio do problema.</span><span class="sxs-lookup"><span data-stu-id="8ecad-177">Not all errors can be represented in a problem domain.</span></span> <span data-ttu-id="8ecad-178">Esses tipos de falhas são *excepcionais* por natureza, portanto, a capacidade de gerar e capturar exceções em F #.</span><span class="sxs-lookup"><span data-stu-id="8ecad-178">These kinds of faults are *exceptional* in nature, hence the ability to raise and catch exceptions in F#.</span></span>

<span data-ttu-id="8ecad-179">Primeiro, é recomendável que você leia as [diretrizes de Design de exceção](../../standard/design-guidelines/exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="8ecad-179">First, it is recommended that you read the [Exception Design Guidelines](../../standard/design-guidelines/exceptions.md).</span></span> <span data-ttu-id="8ecad-180">Eles também são aplicáveis ao F #.</span><span class="sxs-lookup"><span data-stu-id="8ecad-180">These are also applicable to F#.</span></span>

<span data-ttu-id="8ecad-181">As principais construções disponíveis no F # para fins de geração de exceções devem ser consideradas na seguinte ordem de preferência:</span><span class="sxs-lookup"><span data-stu-id="8ecad-181">The main constructs available in F# for the purposes of raising exceptions should be considered in the following order of preference:</span></span>

| <span data-ttu-id="8ecad-182">Função</span><span class="sxs-lookup"><span data-stu-id="8ecad-182">Function</span></span> | <span data-ttu-id="8ecad-183">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8ecad-183">Syntax</span></span> | <span data-ttu-id="8ecad-184">Finalidade</span><span class="sxs-lookup"><span data-stu-id="8ecad-184">Purpose</span></span> |
|----------|--------|---------|
| `nullArg` | `nullArg "argumentName"` | <span data-ttu-id="8ecad-185">Gera um `System.ArgumentNullException` com o nome do argumento especificado.</span><span class="sxs-lookup"><span data-stu-id="8ecad-185">Raises a `System.ArgumentNullException` with the specified argument name.</span></span> |
| `invalidArg` | `invalidArg "argumentName" "message"` | <span data-ttu-id="8ecad-186">Gera um `System.ArgumentException` com uma mensagem e o nome do argumento especificado.</span><span class="sxs-lookup"><span data-stu-id="8ecad-186">Raises a `System.ArgumentException` with a specified argument name and message.</span></span> |
| `invalidOp` | `invalidOp "message"` | <span data-ttu-id="8ecad-187">Gera um `System.InvalidOperationException` com a mensagem especificada.</span><span class="sxs-lookup"><span data-stu-id="8ecad-187">Raises a `System.InvalidOperationException` with the specified message.</span></span> |
|`raise`| `raise (ExceptionType("message"))` | <span data-ttu-id="8ecad-188">Mecanismo de propósito geral para lançar exceções.</span><span class="sxs-lookup"><span data-stu-id="8ecad-188">General-purpose mechanism for throwing exceptions.</span></span> |
| `failwith` | `failwith "message"` | <span data-ttu-id="8ecad-189">Gera um `System.Exception` com a mensagem especificada.</span><span class="sxs-lookup"><span data-stu-id="8ecad-189">Raises a `System.Exception` with the specified message.</span></span> |
| `failwithf` | `failwithf "format string" argForFormatString` | <span data-ttu-id="8ecad-190">Gera um `System.Exception` com uma mensagem determinada pela cadeia de caracteres de formato e suas entradas.</span><span class="sxs-lookup"><span data-stu-id="8ecad-190">Raises a `System.Exception` with a message determined by the format string and its inputs.</span></span> |

<span data-ttu-id="8ecad-191">Use `nullArg`, `invalidArg` e `invalidOp` como o mecanismo para lançar `ArgumentNullException`, `ArgumentException` e `InvalidOperationException` quando apropriado.</span><span class="sxs-lookup"><span data-stu-id="8ecad-191">Use `nullArg`, `invalidArg` and `invalidOp` as the mechanism to throw `ArgumentNullException`, `ArgumentException` and `InvalidOperationException` when appropriate.</span></span>

<span data-ttu-id="8ecad-192">O `failwith` e `failwithf` funções geralmente devem ser evitadas porque eles geram a base de `Exception` digitar, não uma exceção específica.</span><span class="sxs-lookup"><span data-stu-id="8ecad-192">The `failwith` and `failwithf` functions should generally be avoided because they raise the base `Exception` type, not a specific exception.</span></span> <span data-ttu-id="8ecad-193">De acordo o [diretrizes de Design de exceção](../../standard/design-guidelines/exceptions.md), ao acionar exceções mais específicas, quando possível.</span><span class="sxs-lookup"><span data-stu-id="8ecad-193">As per the [Exception Design Guidelines](../../standard/design-guidelines/exceptions.md), you want to raise more specific exceptions when you can.</span></span>

### <a name="using-exception-handling-syntax"></a><span data-ttu-id="8ecad-194">Usando a sintaxe de manipulação de exceção</span><span class="sxs-lookup"><span data-stu-id="8ecad-194">Using exception-handling syntax</span></span>

<span data-ttu-id="8ecad-195">F # oferece suporte a padrões de exceção por meio de `try...with` sintaxe:</span><span class="sxs-lookup"><span data-stu-id="8ecad-195">F# supports exception patterns via the `try...with` syntax:</span></span>

```fsharp
try
    tryGetFileContents()
with
| :? System.IO.FileNotFoundException as e -> // Do something with it here
| :? System.Security.SecurityException as e -> // Do something with it here
```

<span data-ttu-id="8ecad-196">Reconciliar funcionalidade para executar diante de uma exceção com correspondência de padrão pode ser um pouco complicada, se você quiser manter o código limpo.</span><span class="sxs-lookup"><span data-stu-id="8ecad-196">Reconciling functionality to perform in the face of an exception with pattern matching can be a bit tricky if you wish to keep the code clean.</span></span> <span data-ttu-id="8ecad-197">Uma forma de lidar com isso é usar [padrões ativos](../language-reference/active-patterns.md) como um meio para funcionalidade de grupos ao redor de um caso de erro com uma exceção em si.</span><span class="sxs-lookup"><span data-stu-id="8ecad-197">One such way to handle this is to use [active patterns](../language-reference/active-patterns.md) as a means to group functionality surrounding an error case with an exception itself.</span></span> <span data-ttu-id="8ecad-198">Por exemplo, você pode consumir uma API que, quando ele gera uma exceção, inclui informações valiosas nos metadados de exceção.</span><span class="sxs-lookup"><span data-stu-id="8ecad-198">For example, you may be consuming an API that, when it throws an exception, encloses valuable information in the exception metadata.</span></span> <span data-ttu-id="8ecad-199">Um valor útil no corpo da exceção capturada dentro do padrão ativo o desempacotamento e retornando a que valor pode ser útil em algumas situações.</span><span class="sxs-lookup"><span data-stu-id="8ecad-199">Unwrapping a useful value in the body of the captured exception inside the Active Pattern and returning that value can be helpful in some situations.</span></span>

### <a name="do-not-use-monadic-error-handling-to-replace-exceptions"></a><span data-ttu-id="8ecad-200">Não use monadic tratamento de erros para substituir as exceções</span><span class="sxs-lookup"><span data-stu-id="8ecad-200">Do not use monadic error handling to replace exceptions</span></span>

<span data-ttu-id="8ecad-201">As exceções são vistas como um pouco um tabu em programação funcional.</span><span class="sxs-lookup"><span data-stu-id="8ecad-201">Exceptions are seen as somewhat taboo in functional programming.</span></span> <span data-ttu-id="8ecad-202">Na verdade, as exceções violam a pureza, portanto, é seguro considerá-las não é funcional.</span><span class="sxs-lookup"><span data-stu-id="8ecad-202">Indeed, exceptions violate purity, so it's safe to consider them not-quite functional.</span></span> <span data-ttu-id="8ecad-203">No entanto, isso ignora a realidade de qual código deve ser executado e que podem ocorrer erros de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="8ecad-203">However, this ignores the reality of where code must run, and that runtime errors can occur.</span></span> <span data-ttu-id="8ecad-204">Em geral, escreva o código na suposição de que a maioria das coisas não são puro nem total, para minimizar surpresas desagradáveis.</span><span class="sxs-lookup"><span data-stu-id="8ecad-204">In general, write code on the assumption that most things are neither pure nor total, to minimize unpleasant surprises.</span></span>

<span data-ttu-id="8ecad-205">É importante considerar os seguintes pontos fortes/aspectos principais de exceções em relação à sua relevância e adequação no tempo de execução do .NET e o ecossistema de idioma como um todo:</span><span class="sxs-lookup"><span data-stu-id="8ecad-205">It is important to consider the following core strengths/aspects of Exceptions with respect to their relevance and appropriateness in the .NET runtime and cross-language ecosystem as a whole:</span></span>

1. <span data-ttu-id="8ecad-206">Elas contêm informações detalhadas de diagnóstico, que é muito útil ao depurar um problema.</span><span class="sxs-lookup"><span data-stu-id="8ecad-206">They contain detailed diagnostic information, which is very helpful when debugging an issue.</span></span>
2. <span data-ttu-id="8ecad-207">Eles são bem compreendidos, o tempo de execução e outras linguagens .NET.</span><span class="sxs-lookup"><span data-stu-id="8ecad-207">They are well-understood by the runtime and other .NET languages.</span></span>
3. <span data-ttu-id="8ecad-208">Eles podem reduzir clichês significativos quando comparados com o código que sai do seu caminho para *evitar* exceções com a implementação de algum subconjunto dos seu semântica em uma base ad hoc.</span><span class="sxs-lookup"><span data-stu-id="8ecad-208">They can reduce significant boilerplate when compared with code that goes out of its way to *avoid* exceptions by implementing some subset of their semantics on an ad-hoc basis.</span></span>

<span data-ttu-id="8ecad-209">Neste terceiro ponto é essencial.</span><span class="sxs-lookup"><span data-stu-id="8ecad-209">This third point is critical.</span></span> <span data-ttu-id="8ecad-210">Para operações complexas não triviais, Falha ao usar exceções pode resultar em lidar com estruturas como este:</span><span class="sxs-lookup"><span data-stu-id="8ecad-210">For nontrivial complex operations, failing to use exceptions can result in dealing with structures like this:</span></span>

```fsharp
Result<Result<MyType, string>, string list>
```

<span data-ttu-id="8ecad-211">Que pode facilmente levar a um código frágil, como correspondência de padrão em erros de "stringly tipificou":</span><span class="sxs-lookup"><span data-stu-id="8ecad-211">Which can easily lead to fragile code like pattern matching on "stringly-typed" errors:</span></span>

```fsharp
let result = doStuff()
match result with
| Ok r -> ...
| Error e ->
    if e.Contains "Error string 1" then ...
    elif e.Contains "Error string 2" then ...
    else ... // Who knows?
```

<span data-ttu-id="8ecad-212">Além disso, pode ser tentador para se fazer qualquer exceção no desejo de uma função "simples" que retorna um tipo de "melhor":</span><span class="sxs-lookup"><span data-stu-id="8ecad-212">Additionally, it can be tempting to swallow any exception in the desire for a "simple" function that returns a "nicer" type:</span></span>

```fsharp
// This is bad!
let tryReadAllText (path : string) =
    try System.IO.File.ReadAllText path |> Some
    with _ -> None
```

<span data-ttu-id="8ecad-213">Infelizmente, `tryReadAllText` pode acionar diversas exceções com base em uma infinidade de coisas que podem ocorrer em um sistema de arquivos e, em seguida, esse código imediatamente descarta todas as informações sobre o que pode realmente estar errado em seu ambiente.</span><span class="sxs-lookup"><span data-stu-id="8ecad-213">Unfortunately, `tryReadAllText` can throw numerous exceptions based on the myriad of things that can happen on a file system, and this code discards away any information about what might actually be going wrong in your environment.</span></span> <span data-ttu-id="8ecad-214">Se você substituir esse código com um tipo de resultado, você estará para análise de mensagem de erro "stringly tipificou":</span><span class="sxs-lookup"><span data-stu-id="8ecad-214">If you replace this code with a result type, then you're back to "stringly-typed" error message parsing:</span></span>

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

<span data-ttu-id="8ecad-215">E colocar o próprio objeto de exceção no `Error` construtor apenas força você a lidar adequadamente com o tipo de exceção no site de chamada em vez de na função.</span><span class="sxs-lookup"><span data-stu-id="8ecad-215">And placing the exception object itself in the `Error` constructor just forces you to properly deal with the exception type at the call site rather than in the function.</span></span> <span data-ttu-id="8ecad-216">Isso efetivamente cria exceções verificadas, o que são notoriamente unfun lidar com que um chamador de uma API.</span><span class="sxs-lookup"><span data-stu-id="8ecad-216">Doing this effectively creates checked exceptions, which are notoriously unfun to deal with as a caller of an API.</span></span>

<span data-ttu-id="8ecad-217">Uma boa alternativa para os exemplos acima é capturar *específico* exceções e retorne um valor significativo no contexto de tal exceção.</span><span class="sxs-lookup"><span data-stu-id="8ecad-217">A good alternative to the above examples is to catch *specific* exceptions and return a meaningful value in the context of that exception.</span></span> <span data-ttu-id="8ecad-218">Se você modificar a `tryReadAllText` funcionam da seguinte maneira, `None` tem mais significado:</span><span class="sxs-lookup"><span data-stu-id="8ecad-218">If you modify the `tryReadAllText` function as follows, `None` has more meaning:</span></span>

```fsharp
let tryReadAllTextIfPresent (path : string) =
    try System.IO.File.ReadAllText path |> Some
    with :? FileNotFoundException -> None
```

<span data-ttu-id="8ecad-219">Em vez de funcionar como um catch-all, essa função agora manipulará corretamente o caso quando um arquivo não foi encontrado e atribuir esse significado para um retorno.</span><span class="sxs-lookup"><span data-stu-id="8ecad-219">Instead of functioning as a catch-all, this function will now properly handle the case when a file was not found and assign that meaning to a return.</span></span> <span data-ttu-id="8ecad-220">Esse valor de retorno pode mapear para esse caso de erro, ao mesmo tempo não descartando todas as informações contextuais ou forçar os chamadores para lidar com um caso que pode não ser relevante nesse ponto no código.</span><span class="sxs-lookup"><span data-stu-id="8ecad-220">This return value can map to that error case, while not discarding any contextual information or forcing callers to deal with a case that may not be relevant at that point in the code.</span></span>

<span data-ttu-id="8ecad-221">Tipos, como `Result<'Success, 'Error>` são apropriados para operações básicas em que eles não estão aninhados e tipos F # opcionais são perfeitos para representar quando algo poderia retornar *algo* ou *nada*.</span><span class="sxs-lookup"><span data-stu-id="8ecad-221">Types such as `Result<'Success, 'Error>` are appropriate for basic operations where they aren't nested, and F# optional types are perfect for representing when something could either return *something* or *nothing*.</span></span> <span data-ttu-id="8ecad-222">Eles não são uma substituição para exceções, no entanto e não devem ser usados em uma tentativa de substituir as exceções.</span><span class="sxs-lookup"><span data-stu-id="8ecad-222">They are not a replacement for exceptions, though, and should not be used in an attempt to replace exceptions.</span></span> <span data-ttu-id="8ecad-223">Em vez disso, eles devem ser aplicados criteriosamente para aspectos específicos do endereço de exceção e a política de gerenciamento de erro de maneiras de destino.</span><span class="sxs-lookup"><span data-stu-id="8ecad-223">Rather, they should be applied judiciously to address specific aspects of exception and error management policy in targeted ways.</span></span>

## <a name="partial-application-and-point-free-programming"></a><span data-ttu-id="8ecad-224">Aplicativo parcial e livre de ponto de programação</span><span class="sxs-lookup"><span data-stu-id="8ecad-224">Partial application and point-free programming</span></span>

<span data-ttu-id="8ecad-225">F # oferece suporte a aplicativo parcial e, assim, várias maneiras de programar em um estilo livre de ponto.</span><span class="sxs-lookup"><span data-stu-id="8ecad-225">F# supports partial application, and thus, various ways to program in a point-free style.</span></span> <span data-ttu-id="8ecad-226">Isso pode ser benéfico para reutilização de código dentro de um módulo ou a implementação de algo, mas geralmente não é algo para expor publicamente.</span><span class="sxs-lookup"><span data-stu-id="8ecad-226">This can be beneficial for code reuse within a module or the implementation of something, but it is generally not something to expose publicly.</span></span> <span data-ttu-id="8ecad-227">Em geral, livre de ponto de programação não é uma virtude por si só e pode adicionar uma barreira cognitiva significativa para as pessoas que não são imersos no estilo.</span><span class="sxs-lookup"><span data-stu-id="8ecad-227">In general, point-free programming is not a virtue in and of itself, and can add a significant cognitive barrier for people who are not immersed in the style.</span></span>

### <a name="do-not-use-partial-application-and-currying-in-public-apis"></a><span data-ttu-id="8ecad-228">Não usar o aplicativo parcial e currying em APIs públicas</span><span class="sxs-lookup"><span data-stu-id="8ecad-228">Do not use partial application and currying in public APIs</span></span>

<span data-ttu-id="8ecad-229">Com poucas exceções, o uso do aplicativo parcial em APIs públicas pode confundir os consumidores.</span><span class="sxs-lookup"><span data-stu-id="8ecad-229">With little exception, the use of partial application in public APIs can be confusing for consumers.</span></span> <span data-ttu-id="8ecad-230">Geralmente, `let`-são os valores ligados no código F # **valores**, e não **valores de função**.</span><span class="sxs-lookup"><span data-stu-id="8ecad-230">Usually, `let`-bound values in F# code are **values**, not **function values**.</span></span> <span data-ttu-id="8ecad-231">Misturando valores e os valores de função pode resultar em Salvar um pequeno número de linhas de código em troca de uma grande quantidade de sobrecarga cognitiva, especialmente se combinado com operadores como `>>` a composição de funções.</span><span class="sxs-lookup"><span data-stu-id="8ecad-231">Mixing together values and function values can result in saving a small number of lines of code in exchange for quite a bit of cognitive overhead, especially if combined with operators such as `>>` to compose functions.</span></span>

### <a name="consider-the-tooling-implications-for-point-free-programming"></a><span data-ttu-id="8ecad-232">Considere as implicações de ferramentas para a programação livre de ponto</span><span class="sxs-lookup"><span data-stu-id="8ecad-232">Consider the tooling implications for point-free programming</span></span>

<span data-ttu-id="8ecad-233">Funções curried rotula seus argumentos.</span><span class="sxs-lookup"><span data-stu-id="8ecad-233">Curried functions do not label their arguments.</span></span> <span data-ttu-id="8ecad-234">Isso tem implicações de ferramentas.</span><span class="sxs-lookup"><span data-stu-id="8ecad-234">This has tooling implications.</span></span> <span data-ttu-id="8ecad-235">Considere as duas funções a seguir:</span><span class="sxs-lookup"><span data-stu-id="8ecad-235">Consider the following two functions:</span></span>

```fsharp
let func name age =
    printfn "My name is %s and I am %d years old!" name age

let funcWithApplication =
    printfn "My name is %s and I am %d years old!"
```

<span data-ttu-id="8ecad-236">Ambos são funções válidas, mas `funcWithApplication` é uma função na forma curried.</span><span class="sxs-lookup"><span data-stu-id="8ecad-236">Both are valid functions, but `funcWithApplication` is a curried function.</span></span> <span data-ttu-id="8ecad-237">Quando você focaliza em seus tipos em um editor, você verá isso:</span><span class="sxs-lookup"><span data-stu-id="8ecad-237">When you hover over their types in an editor, you see this:</span></span>

```fsharp
val func : name:string -> age:int -> unit

val funcWithApplication : (string -> int -> unit)
```

<span data-ttu-id="8ecad-238">No site de chamada, as dicas de ferramenta em ferramentas como o Visual Studio não dará informações significativas sobre o que o `string` e `int` , na verdade, representam tipos de entrada.</span><span class="sxs-lookup"><span data-stu-id="8ecad-238">At the call site, tooltips in tooling such as Visual Studio will not give you meaningful information as to what the `string` and `int` input types actually represent.</span></span>

<span data-ttu-id="8ecad-239">Se você encontrar livre de ponto de código como `funcWithApplication` que é consumível publicamente, é recomendável fazer uma expansão de η completa para que as ferramentas podem escolher até diante nomes significativos para os argumentos.</span><span class="sxs-lookup"><span data-stu-id="8ecad-239">If you encounter point-free code like `funcWithApplication` that is publicly consumable, it is recommended to do a full η-expansion so that tooling can pick up on meaningful names for arguments.</span></span>

<span data-ttu-id="8ecad-240">Além disso, livre de ponto de código de depuração pode ser um desafio, se não impossível.</span><span class="sxs-lookup"><span data-stu-id="8ecad-240">Furthermore, debugging point-free code can be challenging, if not impossible.</span></span> <span data-ttu-id="8ecad-241">Ferramentas de depuração contam com os valores associados a nomes (por exemplo, `let` associações) para que você possa inspecionar midway valores intermediários por meio da execução.</span><span class="sxs-lookup"><span data-stu-id="8ecad-241">Debugging tools rely on values bound to names (for example, `let` bindings) so that you can inspect intermediate values midway through execution.</span></span> <span data-ttu-id="8ecad-242">Quando seu código não tem valores para inspecionar, não há nada para depurar.</span><span class="sxs-lookup"><span data-stu-id="8ecad-242">When your code has no values to inspect, there is nothing to debug.</span></span> <span data-ttu-id="8ecad-243">No futuro, as ferramentas de depuração podem evoluir para sintetizar esses valores com base nos caminhos executados anteriormente, mas não é uma boa ideia restringir as suas apostas *potencial* funcionalidade de depuração.</span><span class="sxs-lookup"><span data-stu-id="8ecad-243">In the future, debugging tools may evolve to synthesize these values based on previously executed paths, but it's not a good idea to hedge your bets on *potential* debugging functionality.</span></span>

### <a name="consider-partial-application-as-a-technique-to-reduce-internal-boilerplate"></a><span data-ttu-id="8ecad-244">Considere a aplicação parcial como uma técnica para reduzir clichês interno</span><span class="sxs-lookup"><span data-stu-id="8ecad-244">Consider partial application as a technique to reduce internal boilerplate</span></span>

<span data-ttu-id="8ecad-245">Em contraste com o ponto anterior, o aplicativo parcial é uma ferramenta excelente para reduzir o clichê dentro de um aplicativo ou os recursos internos de mais de uma API.</span><span class="sxs-lookup"><span data-stu-id="8ecad-245">In contrast to the previous point, partial application is a wonderful tool for reducing boilerplate inside of an application or the deeper internals of an API.</span></span> <span data-ttu-id="8ecad-246">Ele pode ser útil para a implementação das APIs mais complicadas, onde o clichê geralmente é um problema para lidar com teste de unidade.</span><span class="sxs-lookup"><span data-stu-id="8ecad-246">It can be helpful for unit testing the implementation of more complicated APIs, where boilerplate is often a pain to deal with.</span></span> <span data-ttu-id="8ecad-247">Por exemplo, o código a seguir mostra como é possível realizar quais estruturas de simulação mais lhe sem colocar uma dependência externa em uma estrutura e ter que aprender um relacionados bespoke API.</span><span class="sxs-lookup"><span data-stu-id="8ecad-247">For example, the following code shows how you can accomplish what most mocking frameworks give you without taking an external dependency on such a framework and having to learn a related bespoke API.</span></span>

<span data-ttu-id="8ecad-248">Por exemplo, considere a topografia de solução a seguir:</span><span class="sxs-lookup"><span data-stu-id="8ecad-248">For example, consider the following solution topography:</span></span>

```
MySolution.sln
|_/ImplementationLogic.fsproj
|_/ImplementationLogic.Tests.fsproj
|_/API.fsproj
```

<span data-ttu-id="8ecad-249">`ImplementationLogic.fsproj` pode expor o código como:</span><span class="sxs-lookup"><span data-stu-id="8ecad-249">`ImplementationLogic.fsproj` might expose code such as:</span></span>

```fsharp
module Transactions =
    let doTransaction txnContext txnType balance =
        ...

type Transactor(ctx, currentBalance) =
    member __.ExecuteTransaction(txnType) =
        Transactions.doTransaction ctx txtType currentBalance
        ...
```

<span data-ttu-id="8ecad-250">Teste de unidade `Transactions.doTransaction` em `ImplementationLogic.Tests.fspoj` é fácil:</span><span class="sxs-lookup"><span data-stu-id="8ecad-250">Unit testing `Transactions.doTransaction` in `ImplementationLogic.Tests.fspoj` is easy:</span></span>

```fsharp
namespace TransactionsTestingUtil

open Transactions

module TransactionsTestable =
    let getTestableTransactionRoutine mockContext = Transactions.doTransaction mockContext
```

<span data-ttu-id="8ecad-251">Aplicando parcialmente `doTransaction` com um contexto de simulação o objeto permite que você chame a função em todos os seus testes de unidade sem a necessidade de construir um contexto fictício cada vez:</span><span class="sxs-lookup"><span data-stu-id="8ecad-251">Partially applying `doTransaction` with a mocking context object lets you call the function in all of your unit tests without needing to construct a mocked context each time:</span></span>

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

<span data-ttu-id="8ecad-252">Essa técnica não deve ser universalmente aplicada a toda sua base de código, mas é uma boa maneira de reduzir clichês para internals complicadas e os recursos internos de teste de unidade.</span><span class="sxs-lookup"><span data-stu-id="8ecad-252">This technique should not be universally applied to your entire codebase, but it is a good way to reduce boilerplate for complicated internals and unit testing those internals.</span></span>

## <a name="access-control"></a><span data-ttu-id="8ecad-253">Controle de acesso</span><span class="sxs-lookup"><span data-stu-id="8ecad-253">Access control</span></span>

<span data-ttu-id="8ecad-254">O F # tem várias opções para [controle de acesso](../language-reference/access-control.md), herdados do que está disponível no tempo de execução .NET.</span><span class="sxs-lookup"><span data-stu-id="8ecad-254">F# has multiple options for [Access control](../language-reference/access-control.md), inherited from what is available in the .NET runtime.</span></span> <span data-ttu-id="8ecad-255">Esses não são apenas pode ser usados para tipos – você pode usá-los para funções, muito.</span><span class="sxs-lookup"><span data-stu-id="8ecad-255">These are not just usable for types - you can use them for functions, too.</span></span>

* <span data-ttu-id="8ecad-256">Prefira não -`public` tipos e membros até que você precisa deles para ser consumível publicamente.</span><span class="sxs-lookup"><span data-stu-id="8ecad-256">Prefer non-`public` types and members until you need them to be publicly consumable.</span></span> <span data-ttu-id="8ecad-257">Isso minimiza também que alguns consumidores para.</span><span class="sxs-lookup"><span data-stu-id="8ecad-257">This also minimizes what consumers couple to.</span></span>
* <span data-ttu-id="8ecad-258">Tente manter todas as funcionalidades de auxiliar `private`.</span><span class="sxs-lookup"><span data-stu-id="8ecad-258">Strive to keep all helper functionality `private`.</span></span>
* <span data-ttu-id="8ecad-259">Considere o uso de `[<AutoOpen>]` em um módulo privado de funções auxiliares se tornarem vários.</span><span class="sxs-lookup"><span data-stu-id="8ecad-259">Consider the use of `[<AutoOpen>]` on a private module of helper functions if they become numerous.</span></span>

## <a name="type-inference-and-generics"></a><span data-ttu-id="8ecad-260">Inferência de tipo e genéricos</span><span class="sxs-lookup"><span data-stu-id="8ecad-260">Type inference and generics</span></span>

<span data-ttu-id="8ecad-261">Inferência de tipo pode economizar muito texto clichê de digitando.</span><span class="sxs-lookup"><span data-stu-id="8ecad-261">Type inference can save you from typing a lot of boilerplate.</span></span> <span data-ttu-id="8ecad-262">E a generalização automática no compilador F # pode ajudá-lo a escrever mais códigos genéricos com quase nenhum esforço extra da sua parte.</span><span class="sxs-lookup"><span data-stu-id="8ecad-262">And automatic generalization in the F# compiler can help you write more generic code with almost no extra effort on your part.</span></span> <span data-ttu-id="8ecad-263">No entanto, esses recursos não estão universalmente boas.</span><span class="sxs-lookup"><span data-stu-id="8ecad-263">However, these features are not universally good.</span></span>

* <span data-ttu-id="8ecad-264">Considere a rotulagem de nomes de argumentos com tipos explícitos em APIs públicas e não dependem de inferência de tipo para isso.</span><span class="sxs-lookup"><span data-stu-id="8ecad-264">Consider labeling argument names with explicit types in public APIs and do not rely on type inference for this.</span></span>

    <span data-ttu-id="8ecad-265">A razão para isso é que **você** deve estar no controle da forma de sua API, não o compilador.</span><span class="sxs-lookup"><span data-stu-id="8ecad-265">The reason for this is that **you** should be in control of the shape of your API, not the compiler.</span></span> <span data-ttu-id="8ecad-266">Embora o compilador pode fazer um bom trabalho ao inferir tipos para você, é possível ter a forma de sua alteração de API se os componentes internos que ele se baseia em alterou tipos.</span><span class="sxs-lookup"><span data-stu-id="8ecad-266">Although the compiler can do a fine job at inferring types for you, it is possible to have the shape of your API change if the internals it relies on have changed types.</span></span> <span data-ttu-id="8ecad-267">Isso pode ser o que você deseja, mas certamente, isso resultará em uma alteração de API significativa que os consumidores de downstream, em seguida, terá que lidar com.</span><span class="sxs-lookup"><span data-stu-id="8ecad-267">This may be what you want, but it will almost certainly result in a breaking API change that downstream consumers will then have to deal with.</span></span> <span data-ttu-id="8ecad-268">Em vez disso, se você controlar explicitamente a forma de sua API pública, você pode controlar essas alterações significativas.</span><span class="sxs-lookup"><span data-stu-id="8ecad-268">Instead, if you explicitly control the shape of your public API, then you can control these breaking changes.</span></span> <span data-ttu-id="8ecad-269">Em termos DDD, isso pode ser pensado como uma camada anticorrupção.</span><span class="sxs-lookup"><span data-stu-id="8ecad-269">In DDD terms, this can be thought of as an Anti-corruption layer.</span></span>

* <span data-ttu-id="8ecad-270">É recomendável atribuir um nome significativo para seus argumentos genéricos.</span><span class="sxs-lookup"><span data-stu-id="8ecad-270">Consider giving a meaningful name to your generic arguments.</span></span>

    <span data-ttu-id="8ecad-271">A menos que você está escrevendo código realmente genérico que não é específico para um domínio específico, um nome significativo pode ajudar outros programadores Noções básicas sobre o domínio em que eles estão trabalhando.</span><span class="sxs-lookup"><span data-stu-id="8ecad-271">Unless you are writing truly generic code that is not specific to a particular domain, a meaningful name can help other programmers understanding the domain they're working in.</span></span> <span data-ttu-id="8ecad-272">Por exemplo, um parâmetro de tipo denominado `'Document` no contexto de interagir com um documento de banco de dados torna mais clara de que tipos de documento genérico podem ser aceitos pela função ou membro que você está trabalhando.</span><span class="sxs-lookup"><span data-stu-id="8ecad-272">For example, a type parameter named `'Document` in the context of interacting with a document database makes it clearer that generic document types can be accepted by the function or member you are working with.</span></span>

* <span data-ttu-id="8ecad-273">Considere nomear os parâmetros de tipo genérico com PascalCase.</span><span class="sxs-lookup"><span data-stu-id="8ecad-273">Consider naming generic type parameters with PascalCase.</span></span>

    <span data-ttu-id="8ecad-274">Essa é a maneira geral para fazer coisas no .NET, portanto, é recomendável que você use PascalCase, em vez de snake_case ou camelCase.</span><span class="sxs-lookup"><span data-stu-id="8ecad-274">This is the general way to do things in .NET, so it's recommended that you use PascalCase rather than snake_case or camelCase.</span></span>

<span data-ttu-id="8ecad-275">Por fim, generalização automática nem sempre é uma vantagem para as pessoas que são novas para F # ou uma grande base de código.</span><span class="sxs-lookup"><span data-stu-id="8ecad-275">Finally, automatic generalization is not always a boon for people who are new to F# or a large codebase.</span></span> <span data-ttu-id="8ecad-276">Há sobrecarga cognitiva usando componentes que são genéricos.</span><span class="sxs-lookup"><span data-stu-id="8ecad-276">There is cognitive overhead in using components that are generic.</span></span> <span data-ttu-id="8ecad-277">Além disso, se automaticamente generalizadas funções não são usadas com diferentes tipos de entrada (apenas se eles se destinam a ser usada como tal, let), então não há nenhum benefício real para eles sendo genérico nesse ponto no tempo.</span><span class="sxs-lookup"><span data-stu-id="8ecad-277">Furthermore, if automatically generalized functions are not used with different input types (let alone if they are intended to be used as such), then there is no real benefit to them being generic at that point in time.</span></span> <span data-ttu-id="8ecad-278">Sempre considere se você estiver escrevendo código realmente beneficiarão de genérico.</span><span class="sxs-lookup"><span data-stu-id="8ecad-278">Always consider if the code you are writing will actually benefit from being generic.</span></span>

## <a name="performance"></a><span data-ttu-id="8ecad-279">Desempenho</span><span class="sxs-lookup"><span data-stu-id="8ecad-279">Performance</span></span>

<span data-ttu-id="8ecad-280">Valores de F # são imutáveis por padrão, que permite que você evite determinadas classes de bug (especialmente os que envolvem simultaneidade e paralelismo).</span><span class="sxs-lookup"><span data-stu-id="8ecad-280">F# values are immutable by default, which allows you to avoid certain classes of bugs (especially those involving concurrency and parallelism).</span></span> <span data-ttu-id="8ecad-281">No entanto, em alguns casos, para alcançar eficiência ideal (ou até mesmo razoável) de tempo de execução ou alocações de memória, um intervalo de trabalho pode melhor ser implementado usando in loco mutação do estado.</span><span class="sxs-lookup"><span data-stu-id="8ecad-281">However, in certain cases, in order to achieve optimal (or even reasonable) efficiency of execution time or memory allocations, a span of work may best be implemented by using in-place mutation of state.</span></span> <span data-ttu-id="8ecad-282">Isso é possível em uma base de aceitação do F # com o `mutable` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="8ecad-282">This is possible in an opt-in basis with F# with the `mutable` keyword.</span></span>

<span data-ttu-id="8ecad-283">No entanto, usar de `mutable` em F # podem achar conflitante com a pureza funcional.</span><span class="sxs-lookup"><span data-stu-id="8ecad-283">However, use of `mutable` in F# may feel at odds with functional purity.</span></span> <span data-ttu-id="8ecad-284">Isso é bom, se você ajustar a pureza para as suas expectativas [transparência referencial](https://en.wikipedia.org/wiki/Referential_transparency).</span><span class="sxs-lookup"><span data-stu-id="8ecad-284">This is fine, if you adjust expectations from purity to [referential transparency](https://en.wikipedia.org/wiki/Referential_transparency).</span></span> <span data-ttu-id="8ecad-285">Transparência referencial - não pureza - é a meta final ao escrever o functions em F #.</span><span class="sxs-lookup"><span data-stu-id="8ecad-285">Referential transparency - not purity - is the end goal when writing F# functions.</span></span> <span data-ttu-id="8ecad-286">Isso permite que você escreva uma interface funcional ao longo de uma implementação baseada em mutação para o código crítico de desempenho.</span><span class="sxs-lookup"><span data-stu-id="8ecad-286">This allows you to write a functional interface over a mutation-based implementation for performance critical code.</span></span>

### <a name="wrap-mutable-code-in-immutable-interfaces"></a><span data-ttu-id="8ecad-287">Encapsule o código mutável em interfaces imutáveis</span><span class="sxs-lookup"><span data-stu-id="8ecad-287">Wrap mutable code in immutable interfaces</span></span>

<span data-ttu-id="8ecad-288">Com transparência referencial como um objetivo, é essencial para escrever um código que não expõe o underbelly mutável das funções críticas de desempenho.</span><span class="sxs-lookup"><span data-stu-id="8ecad-288">With referential transparency as a goal, it is critical to write code that does not expose the mutable underbelly of performance-critical functions.</span></span> <span data-ttu-id="8ecad-289">Por exemplo, o código a seguir implementa o `Array.contains` função na biblioteca principal F #:</span><span class="sxs-lookup"><span data-stu-id="8ecad-289">For example, the following code implements the `Array.contains` function in the F# core library:</span></span>

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

<span data-ttu-id="8ecad-290">Chamar essa função várias vezes não altera a matriz subjacente, nem exigem manter qualquer estado mutável em consumi-las.</span><span class="sxs-lookup"><span data-stu-id="8ecad-290">Calling this function multiple times does not change the underlying array, nor does it require you to maintain any mutable state in consuming it.</span></span> <span data-ttu-id="8ecad-291">Ele é referencialmente transparente, mesmo que quase todas as linhas de código dentro dele usa mutação.</span><span class="sxs-lookup"><span data-stu-id="8ecad-291">It is referentially transparent, even though almost every line of code within it uses mutation.</span></span>

### <a name="consider-encapsulating-mutable-data-in-classes"></a><span data-ttu-id="8ecad-292">Considere o encapsulamento de dados mutáveis em classes</span><span class="sxs-lookup"><span data-stu-id="8ecad-292">Consider encapsulating mutable data in classes</span></span>

<span data-ttu-id="8ecad-293">O exemplo anterior usou uma única função para encapsular operações usando dados mutáveis.</span><span class="sxs-lookup"><span data-stu-id="8ecad-293">The previous example used a single function to encapsulate operations using mutable data.</span></span> <span data-ttu-id="8ecad-294">Isso nem sempre é suficiente para a mais complexos conjuntos de dados.</span><span class="sxs-lookup"><span data-stu-id="8ecad-294">This is not always sufficient for more complex sets of data.</span></span> <span data-ttu-id="8ecad-295">Considere os seguintes conjuntos de funções:</span><span class="sxs-lookup"><span data-stu-id="8ecad-295">Consider the following sets of functions:</span></span>

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

<span data-ttu-id="8ecad-296">Esse código é o alto desempenho, mas ele expõe a estrutura de dados com base em mutação que os chamadores são responsáveis por manter.</span><span class="sxs-lookup"><span data-stu-id="8ecad-296">This code is performant, but it exposes the mutation-based data structure that callers are responsible for maintaining.</span></span> <span data-ttu-id="8ecad-297">Isso pode ser encapsulado dentro de uma classe sem membros subjacentes que podem ser alterados:</span><span class="sxs-lookup"><span data-stu-id="8ecad-297">This can be wrapped inside of a class with no underlying members that can change:</span></span>

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

<span data-ttu-id="8ecad-298">`Closure1Table` encapsula a estrutura de dados com base em mutação subjacente, assim, sem forçar os chamadores para manter a estrutura de dados subjacente.</span><span class="sxs-lookup"><span data-stu-id="8ecad-298">`Closure1Table` encapsulates the underlying mutation-based data structure, thereby not forcing callers to maintain the underlying data structure.</span></span> <span data-ttu-id="8ecad-299">Classes são uma maneira eficiente para encapsular dados e rotinas que são baseados em mutação sem expor os detalhes para os chamadores.</span><span class="sxs-lookup"><span data-stu-id="8ecad-299">Classes are a powerful way to encapsulate data and routines that are mutation-based without exposing the details to callers.</span></span>

### <a name="prefer-let-mutable-to-reference-cells"></a><span data-ttu-id="8ecad-300">Prefira `let mutable` às células de referência</span><span class="sxs-lookup"><span data-stu-id="8ecad-300">Prefer `let mutable` to reference cells</span></span>

<span data-ttu-id="8ecad-301">Células de referência são uma forma de representar a referência a um valor, em vez do valor em si.</span><span class="sxs-lookup"><span data-stu-id="8ecad-301">Reference cells are a way to represent the reference to a value rather than the value itself.</span></span> <span data-ttu-id="8ecad-302">Embora possam ser usados para o código crítico de desempenho, eles geralmente não são recomendados.</span><span class="sxs-lookup"><span data-stu-id="8ecad-302">Although they can be used for performance-critical code, they are generally not recommended.</span></span> <span data-ttu-id="8ecad-303">Considere o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="8ecad-303">Consider the following example:</span></span>

```fsharp
let kernels =
    let acc = ref Set.empty

    processWorkList startKernels (fun kernel ->
        if not ((!acc).Contains(kernel)) then
            acc := (!acc).Add(kernel)
        ...)

    !acc |> Seq.toList
```

<span data-ttu-id="8ecad-304">O uso de uma célula de referência "polui" todo o código subsequente com a necessidade de cancelar a referência e referenciar novamente os dados subjacentes.</span><span class="sxs-lookup"><span data-stu-id="8ecad-304">The use of a reference cell now "pollutes" all subsequent code with having to dereference and re-reference the underlying data.</span></span> <span data-ttu-id="8ecad-305">Em vez disso, considere `let mutable`:</span><span class="sxs-lookup"><span data-stu-id="8ecad-305">Instead, consider `let mutable`:</span></span>

```fsharp
let kernels =
    let mutable acc = Set.empty

    processWorkList startKernels (fun kernel ->
        if not (acc.Contains(kernel)) then
            acc <- acc.Add(kernel)
        ...)

    acc |> Seq.toList
```

<span data-ttu-id="8ecad-306">O ponto único de mutação no meio da expressão lambda, além de todos os outros códigos que envolve `acc` pode ser feito de forma que não é diferente para o uso de um normal `let`-valor imutável de limite.</span><span class="sxs-lookup"><span data-stu-id="8ecad-306">Aside from the single point of mutation in the middle of the lambda expression, all other code that touches `acc` can do so in a manner that is no different to the usage of a normal `let`-bound immutable value.</span></span> <span data-ttu-id="8ecad-307">Isso tornará mais fácil alterar ao longo do tempo.</span><span class="sxs-lookup"><span data-stu-id="8ecad-307">This will make it easier to change over time.</span></span>

## <a name="object-programming"></a><span data-ttu-id="8ecad-308">Programação de objeto</span><span class="sxs-lookup"><span data-stu-id="8ecad-308">Object programming</span></span>

<span data-ttu-id="8ecad-309">F # tem suporte completo para objetos e orientada a objeto (OO) conceitos.</span><span class="sxs-lookup"><span data-stu-id="8ecad-309">F# has full support for objects and object-oriented (OO) concepts.</span></span> <span data-ttu-id="8ecad-310">Embora muitos conceitos OO sejam poderoso e útil, nem todos eles são ideais para uso.</span><span class="sxs-lookup"><span data-stu-id="8ecad-310">Although many OO concepts are powerful and useful, not all of them are ideal to use.</span></span> <span data-ttu-id="8ecad-311">As listas a seguir oferecem orientação sobre categorias de recursos OO em um alto nível.</span><span class="sxs-lookup"><span data-stu-id="8ecad-311">The following lists offer guidance on categories of OO features at a high level.</span></span>

<span data-ttu-id="8ecad-312">**Considere o uso desses recursos em muitas situações:**</span><span class="sxs-lookup"><span data-stu-id="8ecad-312">**Consider using these features in many situations:**</span></span>

* <span data-ttu-id="8ecad-313">A notação de ponto (`x.Length`)</span><span class="sxs-lookup"><span data-stu-id="8ecad-313">Dot notation (`x.Length`)</span></span>
* <span data-ttu-id="8ecad-314">Membros de instância</span><span class="sxs-lookup"><span data-stu-id="8ecad-314">Instance members</span></span>
* <span data-ttu-id="8ecad-315">Construtores implícitos</span><span class="sxs-lookup"><span data-stu-id="8ecad-315">Implicit constructors</span></span>
* <span data-ttu-id="8ecad-316">Membros estáticos</span><span class="sxs-lookup"><span data-stu-id="8ecad-316">Static members</span></span>
* <span data-ttu-id="8ecad-317">Notação do indexador (`arr.[x]`)</span><span class="sxs-lookup"><span data-stu-id="8ecad-317">Indexer notation (`arr.[x]`)</span></span>
* <span data-ttu-id="8ecad-318">Argumentos nomeados e opcionais</span><span class="sxs-lookup"><span data-stu-id="8ecad-318">Named and Optional arguments</span></span>
* <span data-ttu-id="8ecad-319">Interfaces e implementações de interface</span><span class="sxs-lookup"><span data-stu-id="8ecad-319">Interfaces and interface implementations</span></span>

<span data-ttu-id="8ecad-320">**Não alcançam primeiro para esses recursos, mas aplicá-las com cuidado quando eles são convenientes resolver um problema:**</span><span class="sxs-lookup"><span data-stu-id="8ecad-320">**Don't reach for these features first, but do judiciously apply them when they are convenient to solve a problem:**</span></span>

* <span data-ttu-id="8ecad-321">Sobrecarga de método</span><span class="sxs-lookup"><span data-stu-id="8ecad-321">Method overloading</span></span>
* <span data-ttu-id="8ecad-322">Dados mutáveis encapsulados</span><span class="sxs-lookup"><span data-stu-id="8ecad-322">Encapsulated mutable data</span></span>
* <span data-ttu-id="8ecad-323">Operadores em tipos</span><span class="sxs-lookup"><span data-stu-id="8ecad-323">Operators on types</span></span>
* <span data-ttu-id="8ecad-324">Propriedades automáticas</span><span class="sxs-lookup"><span data-stu-id="8ecad-324">Auto properties</span></span>
* <span data-ttu-id="8ecad-325">Implementando `IDisposable` e `IEnumerable`</span><span class="sxs-lookup"><span data-stu-id="8ecad-325">Implementing `IDisposable` and `IEnumerable`</span></span>
* <span data-ttu-id="8ecad-326">Extensões de tipo</span><span class="sxs-lookup"><span data-stu-id="8ecad-326">Type extensions</span></span>
* <span data-ttu-id="8ecad-327">Eventos</span><span class="sxs-lookup"><span data-stu-id="8ecad-327">Events</span></span>
* <span data-ttu-id="8ecad-328">Structs</span><span class="sxs-lookup"><span data-stu-id="8ecad-328">Structs</span></span>
* <span data-ttu-id="8ecad-329">Delegados</span><span class="sxs-lookup"><span data-stu-id="8ecad-329">Delegates</span></span>
* <span data-ttu-id="8ecad-330">Enums</span><span class="sxs-lookup"><span data-stu-id="8ecad-330">Enums</span></span>

<span data-ttu-id="8ecad-331">**Evite a esses recursos, a menos que você deve usá-los:**</span><span class="sxs-lookup"><span data-stu-id="8ecad-331">**Generally avoid these features unless you must use them:**</span></span>

* <span data-ttu-id="8ecad-332">Hierarquias de herança com base no tipo e herança de implementação</span><span class="sxs-lookup"><span data-stu-id="8ecad-332">Inheritance-based type hierarchies and implementation inheritance</span></span>
* <span data-ttu-id="8ecad-333">Valores nulos e `Unchecked.defaultof<_>`</span><span class="sxs-lookup"><span data-stu-id="8ecad-333">Nulls and `Unchecked.defaultof<_>`</span></span>

### <a name="prefer-composition-over-inheritance"></a><span data-ttu-id="8ecad-334">Preferir a composição em vez de herança</span><span class="sxs-lookup"><span data-stu-id="8ecad-334">Prefer composition over inheritance</span></span>

<span data-ttu-id="8ecad-335">[Composição em vez da herança](https://en.wikipedia.org/wiki/Composition_over_inheritance) é uma linguagem de duradoura bom código de F # pode aderir a.</span><span class="sxs-lookup"><span data-stu-id="8ecad-335">[Composition over inheritance](https://en.wikipedia.org/wiki/Composition_over_inheritance) is a long-standing idiom that good F# code can adhere to.</span></span> <span data-ttu-id="8ecad-336">O princípio fundamental é que você não deve expor uma classe base e forçar os chamadores herdar da classe base para obter a funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="8ecad-336">The fundamental principle is that you should not expose a base class and force callers to inherit from that base class to get functionality.</span></span>

### <a name="use-object-expressions-to-implement-interfaces-if-you-dont-need-a-class"></a><span data-ttu-id="8ecad-337">Usar expressões de objeto para implementar interfaces, se você não precisa de uma classe</span><span class="sxs-lookup"><span data-stu-id="8ecad-337">Use object expressions to implement interfaces if you don't need a class</span></span>

<span data-ttu-id="8ecad-338">[Expressões de objeto](../language-reference/object-expressions.md) permitem que você implemente as interfaces em tempo real, associação a interface implementada como um valor sem a necessidade de fazer isso dentro de uma classe.</span><span class="sxs-lookup"><span data-stu-id="8ecad-338">[Object Expressions](../language-reference/object-expressions.md) allow you to implement interfaces on the fly, binding the implemented interface to a value without needing to do so inside of a class.</span></span> <span data-ttu-id="8ecad-339">Isso é conveniente, especialmente se você _apenas_ precisa implementar a interface e não precisa de uma classe completa.</span><span class="sxs-lookup"><span data-stu-id="8ecad-339">This is convenient, especially if you _only_ need to implement the interface and have no need for a full class.</span></span>

<span data-ttu-id="8ecad-340">Por exemplo, aqui está o código que é executado no [Ionide](http://ionide.io/) para fornecer uma ação de correção de código se você adicionou um símbolo que você não tiver um `open` instrução para:</span><span class="sxs-lookup"><span data-stu-id="8ecad-340">For example, here is the code that is run in [Ionide](http://ionide.io/) to provide a code fix action if you've added a symbol that you don't have an `open` statement for:</span></span>

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

<span data-ttu-id="8ecad-341">Como não há nenhuma necessidade de uma classe ao interagir com a API de código do Visual Studio, expressões de objeto são uma ferramenta ideal para isso.</span><span class="sxs-lookup"><span data-stu-id="8ecad-341">Because there is no need for a class when interacting with the Visual Studio Code API, Object Expressions are an ideal tool for this.</span></span> <span data-ttu-id="8ecad-342">Eles também são importantes para testes de unidade, quando você deseja criar um stub de uma interface com rotinas de teste de maneira ad hoc.</span><span class="sxs-lookup"><span data-stu-id="8ecad-342">They are also valuable for unit testing, when you want to stub out an interface with test routines in an ad hoc manner.</span></span>

## <a name="type-abbreviations"></a><span data-ttu-id="8ecad-343">Abreviações de tipo</span><span class="sxs-lookup"><span data-stu-id="8ecad-343">Type Abbreviations</span></span>

<span data-ttu-id="8ecad-344">[Abreviações de tipo](../language-reference/type-abbreviations.md) são uma maneira conveniente de atribuir um rótulo para outro tipo, como uma assinatura de função ou um tipo mais complexo.</span><span class="sxs-lookup"><span data-stu-id="8ecad-344">[Type Abbreviations](../language-reference/type-abbreviations.md) are a convenient way to assign a label to another type, such as a function signature or a more complex type.</span></span> <span data-ttu-id="8ecad-345">Por exemplo, o alias a seguir atribui um rótulo para o que é necessário definir uma computação com [CNTK](https://www.microsoft.com/en-us/cognitive-toolkit/), uma biblioteca de aprendizado profundo:</span><span class="sxs-lookup"><span data-stu-id="8ecad-345">For example, the following alias assigns a label to what's needed to define a computation with [CNTK](https://www.microsoft.com/en-us/cognitive-toolkit/), a deep learning library:</span></span>

```fsharp
open CNTK

// DeviceDescriptor, Variable, and Function all come from CNTK
type Computation = DeviceDescriptor -> Variable -> Function
```

<span data-ttu-id="8ecad-346">O `Computation` nome é uma maneira conveniente para indicar qualquer função que corresponda à assinatura é um alias.</span><span class="sxs-lookup"><span data-stu-id="8ecad-346">The `Computation` name is a convenient way to denote any function that matches the signature it is aliasing.</span></span> <span data-ttu-id="8ecad-347">Usar abreviações de tipo, como isso é conveniente e permite que o código mais sucinto.</span><span class="sxs-lookup"><span data-stu-id="8ecad-347">Using Type Abbreviations like this is convenient and allows for more succinct code.</span></span>

### <a name="avoid-using-type-abbreviations-to-represent-your-domain"></a><span data-ttu-id="8ecad-348">Evitar o uso de abreviações de tipo para representar seu domínio</span><span class="sxs-lookup"><span data-stu-id="8ecad-348">Avoid using Type Abbreviations to represent your domain</span></span>

<span data-ttu-id="8ecad-349">Apesar de abreviações de tipo são convenientes para dar um nome para assinaturas de função, eles podem ser confusos quando abreviando outros tipos.</span><span class="sxs-lookup"><span data-stu-id="8ecad-349">Although Type Abbreviations are convenient for giving a name to function signatures, they can be confusing when abbreviating other types.</span></span> <span data-ttu-id="8ecad-350">Considere essa abreviação:</span><span class="sxs-lookup"><span data-stu-id="8ecad-350">Consider this abbreviation:</span></span>

```fsharp
// Does not actually abstract integers.
type BufferSize = int
```

<span data-ttu-id="8ecad-351">Isso pode ser confuso de várias maneiras:</span><span class="sxs-lookup"><span data-stu-id="8ecad-351">This can be confusing in multiple ways:</span></span>

* <span data-ttu-id="8ecad-352">`BufferSize` não é uma abstração; ele é apenas outro nome de um número inteiro.</span><span class="sxs-lookup"><span data-stu-id="8ecad-352">`BufferSize` is not an abstraction; it is just another name for an integer.</span></span>
* <span data-ttu-id="8ecad-353">Se `BufferSize` é exposto em uma API pública, ele pode facilmente ser interpretados incorretamente para significar mais do que apenas `int`.</span><span class="sxs-lookup"><span data-stu-id="8ecad-353">If `BufferSize` is exposed in a public API, it can easily be misinterpreted to mean more than just `int`.</span></span> <span data-ttu-id="8ecad-354">Em geral, os tipos de domínio tem vários atributos para eles e não são tipos primitivos como `int`.</span><span class="sxs-lookup"><span data-stu-id="8ecad-354">Generally, domain types have multiple attributes to them and are not primitive types like `int`.</span></span> <span data-ttu-id="8ecad-355">Essa abreviação viola essa suposição.</span><span class="sxs-lookup"><span data-stu-id="8ecad-355">This abbreviation violates that assumption.</span></span>
* <span data-ttu-id="8ecad-356">O uso de maiusculas e minúsculas de `BufferSize` (PascalCase) indica que esse tipo armazena mais dados.</span><span class="sxs-lookup"><span data-stu-id="8ecad-356">The casing of `BufferSize` (PascalCase) implies that this type holds more data.</span></span>
* <span data-ttu-id="8ecad-357">Este alias não oferece maior clareza, em comparação com o fornecimento de um argumento nomeado para uma função.</span><span class="sxs-lookup"><span data-stu-id="8ecad-357">This alias does not offer increased clarity compared with providing a named argument to a function.</span></span>
* <span data-ttu-id="8ecad-358">A abreviação não se manifestará IL compilado; ele é um inteiro e esse alias é um constructo de tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="8ecad-358">The abbreviation will not manifest in compiled IL; it is just an integer and this alias is a compile-time construct.</span></span>

```fsharp
module Networking =
    ...
    let send data (bufferSize: int) =
        ...
```

<span data-ttu-id="8ecad-359">Em resumo, as armadilhas com as abreviações de tipo são que eles sejam **não** abstrações sobre os tipos que eles são abreviando.</span><span class="sxs-lookup"><span data-stu-id="8ecad-359">In summary, the pitfall with Type Abbreviations is that they are **not** abstractions over the types they are abbreviating.</span></span> <span data-ttu-id="8ecad-360">No exemplo anterior, `BufferSize` é apenas um `int` nos bastidores, com nenhum dado adicional, nem todos os benefícios do sistema de tipo, além de quais `int` já tem.</span><span class="sxs-lookup"><span data-stu-id="8ecad-360">In the previous example, `BufferSize` is just an `int` under the covers, with no additional data, nor any benefits from the type system besides what `int` already has.</span></span>
