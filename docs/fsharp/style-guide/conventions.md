---
title: Convenções de codificação do F#
description: Aprenda as diretrizes gerais e os idiomas ao F# escrever código.
ms.date: 10/22/2019
ms.openlocfilehash: 6700f64aa61308cbfc0b7a38724d69a281a088db
ms.sourcegitcommit: 9bd1c09128e012b6e34bdcbdf3576379f58f3137
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/23/2019
ms.locfileid: "72799109"
---
# <a name="f-coding-conventions"></a><span data-ttu-id="00a74-103">Convenções de codificação do F#</span><span class="sxs-lookup"><span data-stu-id="00a74-103">F# coding conventions</span></span>

<span data-ttu-id="00a74-104">As convenções a seguir são formuladas de experiência de trabalho F# com grandes bases de código.</span><span class="sxs-lookup"><span data-stu-id="00a74-104">The following conventions are formulated from experience working with large F# codebases.</span></span> <span data-ttu-id="00a74-105">Os [cinco princípios de um F# bom código](index.md#five-principles-of-good-f-code) são a base de cada recomendação.</span><span class="sxs-lookup"><span data-stu-id="00a74-105">The [Five principles of good F# code](index.md#five-principles-of-good-f-code) are the foundation of each recommendation.</span></span> <span data-ttu-id="00a74-106">Eles estão relacionados às [ F# diretrizes de design de componentes](component-design-guidelines.md), mas são aplicáveis a qualquer F# código, não apenas a componentes como bibliotecas.</span><span class="sxs-lookup"><span data-stu-id="00a74-106">They are related to the [F# component design guidelines](component-design-guidelines.md), but are applicable for any F# code, not just components such as libraries.</span></span>

## <a name="organizing-code"></a><span data-ttu-id="00a74-107">Organizando o código</span><span class="sxs-lookup"><span data-stu-id="00a74-107">Organizing code</span></span>

<span data-ttu-id="00a74-108">F#apresenta duas maneiras principais de organizar código: módulos e namespaces.</span><span class="sxs-lookup"><span data-stu-id="00a74-108">F# features two primary ways to organize code: modules and namespaces.</span></span> <span data-ttu-id="00a74-109">Eles são semelhantes, mas têm as seguintes diferenças:</span><span class="sxs-lookup"><span data-stu-id="00a74-109">These are similar, but do have the following differences:</span></span>

* <span data-ttu-id="00a74-110">Os namespaces são compilados como namespaces .NET.</span><span class="sxs-lookup"><span data-stu-id="00a74-110">Namespaces are compiled as .NET namespaces.</span></span> <span data-ttu-id="00a74-111">Os módulos são compilados como classes estáticas.</span><span class="sxs-lookup"><span data-stu-id="00a74-111">Modules are compiled as static classes.</span></span>
* <span data-ttu-id="00a74-112">Os namespaces são sempre de nível superior.</span><span class="sxs-lookup"><span data-stu-id="00a74-112">Namespaces are always top level.</span></span> <span data-ttu-id="00a74-113">Os módulos podem ser de nível superior e aninhados dentro de outros módulos.</span><span class="sxs-lookup"><span data-stu-id="00a74-113">Modules can be top-level and nested within other modules.</span></span>
* <span data-ttu-id="00a74-114">Os namespaces podem abranger vários arquivos.</span><span class="sxs-lookup"><span data-stu-id="00a74-114">Namespaces can span multiple files.</span></span> <span data-ttu-id="00a74-115">Os módulos não podem.</span><span class="sxs-lookup"><span data-stu-id="00a74-115">Modules cannot.</span></span>
* <span data-ttu-id="00a74-116">Os módulos podem ser decorados com `[<RequireQualifiedAccess>]` e `[<AutoOpen>]`.</span><span class="sxs-lookup"><span data-stu-id="00a74-116">Modules can be decorated with `[<RequireQualifiedAccess>]` and `[<AutoOpen>]`.</span></span>

<span data-ttu-id="00a74-117">As diretrizes a seguir ajudarão você a usá-las para organizar seu código.</span><span class="sxs-lookup"><span data-stu-id="00a74-117">The following guidelines will help you use these to organize your code.</span></span>

### <a name="prefer-namespaces-at-the-top-level"></a><span data-ttu-id="00a74-118">Preferir namespaces no nível superior</span><span class="sxs-lookup"><span data-stu-id="00a74-118">Prefer namespaces at the top level</span></span>

<span data-ttu-id="00a74-119">Para qualquer código de consumo publicamente, os namespaces são preferenciais aos módulos no nível superior.</span><span class="sxs-lookup"><span data-stu-id="00a74-119">For any publicly consumable code, namespaces are preferential to modules at the top level.</span></span> <span data-ttu-id="00a74-120">Como eles são compilados como namespaces do .NET, eles são consumíveis de C# sem problemas.</span><span class="sxs-lookup"><span data-stu-id="00a74-120">Because they are compiled as .NET namespaces, they are consumable from C# with no issue.</span></span>

```fsharp
// Good!
namespace MyCode

type MyClass() =
    ...
```

<span data-ttu-id="00a74-121">Usar um módulo de nível superior pode não aparecer diferente quando chamado apenas de F#, mas para C# consumidores, os chamadores podem ficar surpresos ao se qualificar`MyClass`com o módulo`MyCode`.</span><span class="sxs-lookup"><span data-stu-id="00a74-121">Using a top-level module may not appear different when called only from F#, but for C# consumers, callers may be surprised by having to qualify `MyClass` with the `MyCode` module.</span></span>

```fsharp
// Bad!
module MyCode

type MyClass() =
    ...
```

### <a name="carefully-apply-autoopen"></a><span data-ttu-id="00a74-122">Aplicar cuidadosamente `[<AutoOpen>]`</span><span class="sxs-lookup"><span data-stu-id="00a74-122">Carefully apply `[<AutoOpen>]`</span></span>

<span data-ttu-id="00a74-123">A construção de `[<AutoOpen>]` pode poluir o escopo do que está disponível para os chamadores e a resposta para onde algo vem é "mágica".</span><span class="sxs-lookup"><span data-stu-id="00a74-123">The `[<AutoOpen>]` construct can pollute the scope of what is available to callers, and the answer to where something comes from is "magic".</span></span> <span data-ttu-id="00a74-124">Isso geralmente não é algo bom.</span><span class="sxs-lookup"><span data-stu-id="00a74-124">This is generally not a good thing.</span></span> <span data-ttu-id="00a74-125">Uma exceção a essa regra é a F# própria biblioteca principal (embora esse fato também seja um pouco controverso).</span><span class="sxs-lookup"><span data-stu-id="00a74-125">An exception to this rule is the F# Core Library itself (though this fact is also a bit controversial).</span></span>

<span data-ttu-id="00a74-126">No entanto, é uma conveniência se você tiver a funcionalidade auxiliar para uma API pública que você deseja organizar separadamente dessa API pública.</span><span class="sxs-lookup"><span data-stu-id="00a74-126">However, it is a convenience if you have helper functionality for a public API that you wish to organize separately from that public API.</span></span>

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

<span data-ttu-id="00a74-127">Isso permite que você separe de forma limpa os detalhes de implementação da API pública de uma função sem precisar qualificar totalmente um auxiliar cada vez que chamá-lo.</span><span class="sxs-lookup"><span data-stu-id="00a74-127">This lets you cleanly separate implementation details from the public API of a function without having to fully qualify a helper each time you call it.</span></span>

<span data-ttu-id="00a74-128">Além disso, a exposição de métodos de extensão e construtores de expressão no nível de namespace pode ser expressamente expressa com `[<AutoOpen>]`.</span><span class="sxs-lookup"><span data-stu-id="00a74-128">Additionally, exposing extension methods and expression builders at the namespace level can be neatly expressed with `[<AutoOpen>]`.</span></span>

### <a name="use-requirequalifiedaccess-whenever-names-could-conflict-or-you-feel-it-helps-with-readability"></a><span data-ttu-id="00a74-129">Use `[<RequireQualifiedAccess>]` sempre que os nomes puderem entrar em conflito ou se você achar que ele ajuda na legibilidade</span><span class="sxs-lookup"><span data-stu-id="00a74-129">Use `[<RequireQualifiedAccess>]` whenever names could conflict or you feel it helps with readability</span></span>

<span data-ttu-id="00a74-130">Adicionar o atributo `[<RequireQualifiedAccess>]` a um módulo indica que o módulo pode não estar aberto e que as referências aos elementos do módulo exigem acesso qualificado explícito.</span><span class="sxs-lookup"><span data-stu-id="00a74-130">Adding the `[<RequireQualifiedAccess>]` attribute to a module indicates that the module may not be opened and that references to the elements of the module require explicit qualified access.</span></span> <span data-ttu-id="00a74-131">Por exemplo, o módulo `Microsoft.FSharp.Collections.List` tem esse atributo.</span><span class="sxs-lookup"><span data-stu-id="00a74-131">For example, the `Microsoft.FSharp.Collections.List` module has this attribute.</span></span>

<span data-ttu-id="00a74-132">Isso é útil quando as funções e os valores no módulo têm nomes que provavelmente estão em conflito com nomes em outros módulos.</span><span class="sxs-lookup"><span data-stu-id="00a74-132">This is useful when functions and values in the module have names that are likely to conflict with names in other modules.</span></span> <span data-ttu-id="00a74-133">Exigir acesso qualificado pode aumentar muito a manutenção e o evolucionabilidade de longo prazo de uma biblioteca.</span><span class="sxs-lookup"><span data-stu-id="00a74-133">Requiring qualified access can greatly increase the long-term maintainability and evolvability of a library.</span></span>

```fsharp
[<RequireQualifiedAccess>]
module StringTokenization =
    let parse s = ...

...

let s = getAString()
let parsed = StringTokenization.parse s // Must qualify to use 'parse'
```

### <a name="sort-open-statements-topologically"></a><span data-ttu-id="00a74-134">Classificar instruções de `open` topologicamente</span><span class="sxs-lookup"><span data-stu-id="00a74-134">Sort `open` statements topologically</span></span>

<span data-ttu-id="00a74-135">No F#, a ordem das declarações é importante, incluindo com `open`instruções.</span><span class="sxs-lookup"><span data-stu-id="00a74-135">In F#, the order of declarations matters, including with `open` statements.</span></span> <span data-ttu-id="00a74-136">Isso é diferente C#de, onde o efeito de`using`e`using static`é independente da ordenação dessas instruções em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="00a74-136">This is unlike C#, where the effect of `using` and `using static` is independent of the ordering of those statements in a file.</span></span>

<span data-ttu-id="00a74-137">No F#, os elementos abertos em um escopo podem sombrear outros já presentes.</span><span class="sxs-lookup"><span data-stu-id="00a74-137">In F#, elements opened into a scope can shadow others already present.</span></span> <span data-ttu-id="00a74-138">Isso significa que reordenar `open` instruções poderia alterar o significado do código.</span><span class="sxs-lookup"><span data-stu-id="00a74-138">This means that reordering `open` statements could alter the meaning of code.</span></span> <span data-ttu-id="00a74-139">Como resultado, qualquer classificação arbitrária de todas as instruções de `open` (por exemplo, alfanuméricamente) geralmente não é recomendada, última você gera um comportamento diferente que você pode esperar.</span><span class="sxs-lookup"><span data-stu-id="00a74-139">As a result, any arbitrary sorting of all `open` statements (for example, alphanumerically) is generally not recommended, lest you generate different behavior that you might expect.</span></span>

<span data-ttu-id="00a74-140">Em vez disso, recomendamos que você os classifique [topologicamente](https://en.wikipedia.org/wiki/Topological_sorting); ou seja, ordene suas instruções de `open` na ordem em que as _camadas_ do seu sistema estão definidas.</span><span class="sxs-lookup"><span data-stu-id="00a74-140">Instead, we recommend that you sort them [topologically](https://en.wikipedia.org/wiki/Topological_sorting); that is, order your `open` statements in the order in which _layers_ of your system are defined.</span></span> <span data-ttu-id="00a74-141">A classificação alfanumérica em diferentes camadas de topológica também pode ser considerada.</span><span class="sxs-lookup"><span data-stu-id="00a74-141">Doing alphanumeric sorting within different topological layers may also be considered.</span></span>

<span data-ttu-id="00a74-142">Como exemplo, aqui está a classificação topológica para o arquivo F# de API pública do serviço de compilador:</span><span class="sxs-lookup"><span data-stu-id="00a74-142">As an example, here is the topological sorting for the F# compiler service public API file:</span></span>

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

<span data-ttu-id="00a74-143">Observe que uma quebra de linha separa as camadas topológica, com cada camada sendo classificada alfanuméricamente depois.</span><span class="sxs-lookup"><span data-stu-id="00a74-143">Note that a line break separates topological layers, with each layer being sorted alphanumerically afterwards.</span></span> <span data-ttu-id="00a74-144">Isso organiza corretamente o código sem sombrear valores de forma acidental.</span><span class="sxs-lookup"><span data-stu-id="00a74-144">This cleanly organizes code without accidentally shadowing values.</span></span>

## <a name="use-classes-to-contain-values-that-have-side-effects"></a><span data-ttu-id="00a74-145">Usar classes para conter valores que têm efeitos colaterais</span><span class="sxs-lookup"><span data-stu-id="00a74-145">Use classes to contain values that have side effects</span></span>

<span data-ttu-id="00a74-146">Há muitas ocasiões em que a inicialização de um valor pode ter efeitos colaterais, como instanciar um contexto para um banco de dados ou outro recurso remoto.</span><span class="sxs-lookup"><span data-stu-id="00a74-146">There are many times when initializing a value can have side effects, such as instantiating a context to a database or other remote resource.</span></span> <span data-ttu-id="00a74-147">É tentador inicializar essas coisas em um módulo e usá-las em funções subsequentes:</span><span class="sxs-lookup"><span data-stu-id="00a74-147">It is tempting to initialize such things in a module and use it in subsequent functions:</span></span>

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

<span data-ttu-id="00a74-148">Geralmente, essa é uma má ideia por alguns motivos:</span><span class="sxs-lookup"><span data-stu-id="00a74-148">This is frequently a bad idea for a few reasons:</span></span>

<span data-ttu-id="00a74-149">Primeiro, a configuração do aplicativo é enviada por push para a base de código com `dep1` e `dep2`.</span><span class="sxs-lookup"><span data-stu-id="00a74-149">First, application configuration is pushed into the codebase with `dep1` and `dep2`.</span></span> <span data-ttu-id="00a74-150">Isso é difícil de ser mantido em bases de código maiores.</span><span class="sxs-lookup"><span data-stu-id="00a74-150">This is difficult to maintain in larger codebases.</span></span>

<span data-ttu-id="00a74-151">Segundo, os dados inicializados estaticamente não devem incluir valores que não sejam thread-safe se o seu componente usar vários threads.</span><span class="sxs-lookup"><span data-stu-id="00a74-151">Second, statically initialized data should not include values that are not thread safe if your component will itself use multiple threads.</span></span> <span data-ttu-id="00a74-152">Isso é claramente violado por `dep3`.</span><span class="sxs-lookup"><span data-stu-id="00a74-152">This is clearly violated by `dep3`.</span></span>

<span data-ttu-id="00a74-153">Por fim, a inicialização do módulo é compilada em um construtor estático para toda a unidade de compilação.</span><span class="sxs-lookup"><span data-stu-id="00a74-153">Finally, module initialization compiles into a static constructor for the entire compilation unit.</span></span> <span data-ttu-id="00a74-154">Se ocorrer algum erro na inicialização de valor de Let associado nesse módulo, ele será manifestado como um `TypeInitializationException` que, em seguida, é armazenado em cache durante todo o tempo de vida do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="00a74-154">If any error occurs in let-bound value initialization in that module, it manifests as a `TypeInitializationException` that is then cached for the entire lifetime of the application.</span></span> <span data-ttu-id="00a74-155">Isso pode ser difícil de diagnosticar.</span><span class="sxs-lookup"><span data-stu-id="00a74-155">This can be difficult to diagnose.</span></span> <span data-ttu-id="00a74-156">Normalmente, há uma exceção interna com a qual você pode tentar se deparar, mas se não houver, não há nenhum informando qual é a causa raiz.</span><span class="sxs-lookup"><span data-stu-id="00a74-156">There is usually an inner exception that you can attempt to reason about, but if there is not, then there is no telling what the root cause is.</span></span>

<span data-ttu-id="00a74-157">Em vez disso, basta usar uma classe simples para manter as dependências:</span><span class="sxs-lookup"><span data-stu-id="00a74-157">Instead, just use a simple class to hold dependencies:</span></span>

```fsharp
type MyParametricApi(dep1, dep2, dep3) =
    member __.Function1 arg1 = doStuffWith dep1 dep2 dep3 arg1
    member __.Function2 arg2 = doStuffWith dep1 dep2 dep3 arg2
```

<span data-ttu-id="00a74-158">Isso permite o seguinte:</span><span class="sxs-lookup"><span data-stu-id="00a74-158">This enables the following:</span></span>

1. <span data-ttu-id="00a74-159">Enviar por push qualquer estado dependente fora da própria API.</span><span class="sxs-lookup"><span data-stu-id="00a74-159">Pushing any dependent state outside of the API itself.</span></span>
2. <span data-ttu-id="00a74-160">Agora, a configuração pode ser feita fora da API.</span><span class="sxs-lookup"><span data-stu-id="00a74-160">Configuration can now be done outside of the API.</span></span>
3. <span data-ttu-id="00a74-161">Erros na inicialização de valores dependentes provavelmente não serão manifestados como um `TypeInitializationException`.</span><span class="sxs-lookup"><span data-stu-id="00a74-161">Errors in initialization for dependent values are not likely to manifest as a `TypeInitializationException`.</span></span>
4. <span data-ttu-id="00a74-162">Agora, a API é mais fácil de testar.</span><span class="sxs-lookup"><span data-stu-id="00a74-162">The API is now easier to test.</span></span>

## <a name="error-management"></a><span data-ttu-id="00a74-163">Gerenciamento de erros</span><span class="sxs-lookup"><span data-stu-id="00a74-163">Error management</span></span>

<span data-ttu-id="00a74-164">O gerenciamento de erros em sistemas grandes é um esforço complexo e nuance, e não há nenhum marcador prata para garantir que seus sistemas sejam tolerantes a falhas e se comporte bem.</span><span class="sxs-lookup"><span data-stu-id="00a74-164">Error management in large systems is a complex and nuanced endeavor, and there are no silver bullets in ensuring your systems are fault-tolerant and behave well.</span></span> <span data-ttu-id="00a74-165">As diretrizes a seguir devem oferecer orientações para navegar nesse espaço difícil.</span><span class="sxs-lookup"><span data-stu-id="00a74-165">The following guidelines should offer guidance in navigating this difficult space.</span></span>

### <a name="represent-error-cases-and-illegal-state-in-types-intrinsic-to-your-domain"></a><span data-ttu-id="00a74-166">Representar casos de erro e estado ilegal em tipos intrínsecos ao seu domínio</span><span class="sxs-lookup"><span data-stu-id="00a74-166">Represent error cases and illegal state in types intrinsic to your domain</span></span>

<span data-ttu-id="00a74-167">Com [uniões discriminadas](../language-reference/discriminated-unions.md), F# o oferece a capacidade de representar o estado do programa com falha em seu sistema de tipos.</span><span class="sxs-lookup"><span data-stu-id="00a74-167">With [Discriminated Unions](../language-reference/discriminated-unions.md), F# gives you the ability to represent faulty program state in your type system.</span></span> <span data-ttu-id="00a74-168">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="00a74-168">For example:</span></span>

```fsharp
type MoneyWithdrawalResult =
    | Success of amount:decimal
    | InsufficientFunds of balance:decimal
    | CardExpired of DateTime
    | UndisclosedFailure
```

<span data-ttu-id="00a74-169">Nesse caso, há três maneiras conhecidas de retirar dinheiro de uma conta bancária.</span><span class="sxs-lookup"><span data-stu-id="00a74-169">In this case, there are three known ways that withdrawing money from a bank account can fail.</span></span> <span data-ttu-id="00a74-170">Cada caso de erro é representado no tipo e, portanto, pode ser tratado com segurança em todo o programa.</span><span class="sxs-lookup"><span data-stu-id="00a74-170">Each error case is represented in the type, and can thus be dealt with safely throughout the program.</span></span>

```fsharp
let handleWithdrawal amount =
    let w = withdrawMoney amount
    match w with
    | Success am -> printfn "Successfully withdrew %f" am
    | InsufficientFunds balance -> printfn "Failed: balance is %f" balance
    | CardExpired expiredDate -> printfn "Failed: card expired on %O" expiredDate
    | UndisclosedFailure -> printfn "Failed: unknown"
```

<span data-ttu-id="00a74-171">Em geral, se você puder modelar as diferentes maneiras pelas quais algo pode **falhar** em seu domínio, o código de tratamento de erros não será mais tratado como algo com o qual você deve lidar, além do fluxo de programa normal.</span><span class="sxs-lookup"><span data-stu-id="00a74-171">In general, if you can model the different ways that something can **fail** in your domain, then error handling code is no longer treated as something you must deal with in addition to regular program flow.</span></span> <span data-ttu-id="00a74-172">Ele é simplesmente parte do fluxo normal do programa e não é considerado **excepcional**.</span><span class="sxs-lookup"><span data-stu-id="00a74-172">It is simply a part of normal program flow, and not considered **exceptional**.</span></span> <span data-ttu-id="00a74-173">Há dois benefícios principais para isso:</span><span class="sxs-lookup"><span data-stu-id="00a74-173">There are two primary benefits to this:</span></span>

1. <span data-ttu-id="00a74-174">É mais fácil de manter à medida que seu domínio muda ao longo do tempo.</span><span class="sxs-lookup"><span data-stu-id="00a74-174">It is easier to maintain as your domain changes over time.</span></span>
2. <span data-ttu-id="00a74-175">Casos de erro são mais fáceis de testar unidade.</span><span class="sxs-lookup"><span data-stu-id="00a74-175">Error cases are easier to unit test.</span></span>

### <a name="use-exceptions-when-errors-cannot-be-represented-with-types"></a><span data-ttu-id="00a74-176">Usar exceções quando erros não puderem ser representados com tipos</span><span class="sxs-lookup"><span data-stu-id="00a74-176">Use exceptions when errors cannot be represented with types</span></span>

<span data-ttu-id="00a74-177">Nem todos os erros podem ser representados em um domínio com problema.</span><span class="sxs-lookup"><span data-stu-id="00a74-177">Not all errors can be represented in a problem domain.</span></span> <span data-ttu-id="00a74-178">Esses tipos de falhas são *excepcionais* por natureza, portanto, a capacidade de gerar e capturar exceções no F#.</span><span class="sxs-lookup"><span data-stu-id="00a74-178">These kinds of faults are *exceptional* in nature, hence the ability to raise and catch exceptions in F#.</span></span>

<span data-ttu-id="00a74-179">Primeiro, é recomendável que você leia as [diretrizes de design de exceção](../../standard/design-guidelines/exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="00a74-179">First, it is recommended that you read the [Exception Design Guidelines](../../standard/design-guidelines/exceptions.md).</span></span> <span data-ttu-id="00a74-180">Elas também são aplicáveis ao F#.</span><span class="sxs-lookup"><span data-stu-id="00a74-180">These are also applicable to F#.</span></span>

<span data-ttu-id="00a74-181">As principais construções disponíveis no F# para fins de geração de exceções devem ser consideradas na seguinte ordem de preferência:</span><span class="sxs-lookup"><span data-stu-id="00a74-181">The main constructs available in F# for the purposes of raising exceptions should be considered in the following order of preference:</span></span>

| <span data-ttu-id="00a74-182">Função</span><span class="sxs-lookup"><span data-stu-id="00a74-182">Function</span></span> | <span data-ttu-id="00a74-183">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="00a74-183">Syntax</span></span> | <span data-ttu-id="00a74-184">Finalidade</span><span class="sxs-lookup"><span data-stu-id="00a74-184">Purpose</span></span> |
|----------|--------|---------|
| `nullArg` | `nullArg "argumentName"` | <span data-ttu-id="00a74-185">Gera um `System.ArgumentNullException` com o nome do argumento especificado.</span><span class="sxs-lookup"><span data-stu-id="00a74-185">Raises a `System.ArgumentNullException` with the specified argument name.</span></span> |
| `invalidArg` | `invalidArg "argumentName" "message"` | <span data-ttu-id="00a74-186">Gera um `System.ArgumentException` com um nome de argumento e uma mensagem especificados.</span><span class="sxs-lookup"><span data-stu-id="00a74-186">Raises a `System.ArgumentException` with a specified argument name and message.</span></span> |
| `invalidOp` | `invalidOp "message"` | <span data-ttu-id="00a74-187">Gera um `System.InvalidOperationException` com a mensagem especificada.</span><span class="sxs-lookup"><span data-stu-id="00a74-187">Raises a `System.InvalidOperationException` with the specified message.</span></span> |
|`raise`| `raise (ExceptionType("message"))` | <span data-ttu-id="00a74-188">Mecanismo de finalidade geral para lançar exceções.</span><span class="sxs-lookup"><span data-stu-id="00a74-188">General-purpose mechanism for throwing exceptions.</span></span> |
| `failwith` | `failwith "message"` | <span data-ttu-id="00a74-189">Gera um `System.Exception` com a mensagem especificada.</span><span class="sxs-lookup"><span data-stu-id="00a74-189">Raises a `System.Exception` with the specified message.</span></span> |
| `failwithf` | `failwithf "format string" argForFormatString` | <span data-ttu-id="00a74-190">Gera um `System.Exception` com uma mensagem determinada pela cadeia de caracteres de formato e suas entradas.</span><span class="sxs-lookup"><span data-stu-id="00a74-190">Raises a `System.Exception` with a message determined by the format string and its inputs.</span></span> |

<span data-ttu-id="00a74-191">Use `nullArg`, `invalidArg` e `invalidOp` como mecanismo para gerar `ArgumentNullException`, `ArgumentException` e `InvalidOperationException` quando apropriado.</span><span class="sxs-lookup"><span data-stu-id="00a74-191">Use `nullArg`, `invalidArg` and `invalidOp` as the mechanism to throw `ArgumentNullException`, `ArgumentException` and `InvalidOperationException` when appropriate.</span></span>

<span data-ttu-id="00a74-192">As funções `failwith` e `failwithf` geralmente devem ser evitadas porque geram o tipo de `Exception` base, não uma exceção específica.</span><span class="sxs-lookup"><span data-stu-id="00a74-192">The `failwith` and `failwithf` functions should generally be avoided because they raise the base `Exception` type, not a specific exception.</span></span> <span data-ttu-id="00a74-193">De acordo com as [diretrizes de design de exceção](../../standard/design-guidelines/exceptions.md), você deseja gerar exceções mais específicas quando puder.</span><span class="sxs-lookup"><span data-stu-id="00a74-193">As per the [Exception Design Guidelines](../../standard/design-guidelines/exceptions.md), you want to raise more specific exceptions when you can.</span></span>

### <a name="using-exception-handling-syntax"></a><span data-ttu-id="00a74-194">Usando a sintaxe de tratamento de exceção</span><span class="sxs-lookup"><span data-stu-id="00a74-194">Using exception-handling syntax</span></span>

<span data-ttu-id="00a74-195">F#dá suporte a padrões de exceção por meio da sintaxe de`try...with`:</span><span class="sxs-lookup"><span data-stu-id="00a74-195">F# supports exception patterns via the `try...with` syntax:</span></span>

```fsharp
try
    tryGetFileContents()
with
| :? System.IO.FileNotFoundException as e -> // Do something with it here
| :? System.Security.SecurityException as e -> // Do something with it here
```

<span data-ttu-id="00a74-196">A reconciliação da funcionalidade a ser executada diante de uma exceção com correspondência de padrões pode ser um pouco complicada se você quiser manter a limpeza do código.</span><span class="sxs-lookup"><span data-stu-id="00a74-196">Reconciling functionality to perform in the face of an exception with pattern matching can be a bit tricky if you wish to keep the code clean.</span></span> <span data-ttu-id="00a74-197">Uma forma de lidar com isso é usar [padrões ativos](../language-reference/active-patterns.md) como um meio de agrupar a funcionalidade em torno de um caso de erro com uma exceção em si.</span><span class="sxs-lookup"><span data-stu-id="00a74-197">One such way to handle this is to use [active patterns](../language-reference/active-patterns.md) as a means to group functionality surrounding an error case with an exception itself.</span></span> <span data-ttu-id="00a74-198">Por exemplo, você pode estar consumindo uma API que, quando ela gera uma exceção, inclui informações valiosas nos metadados de exceção.</span><span class="sxs-lookup"><span data-stu-id="00a74-198">For example, you may be consuming an API that, when it throws an exception, encloses valuable information in the exception metadata.</span></span> <span data-ttu-id="00a74-199">Desencapsular um valor útil no corpo da exceção capturada dentro do padrão ativo e retornar esse valor pode ser útil em algumas situações.</span><span class="sxs-lookup"><span data-stu-id="00a74-199">Unwrapping a useful value in the body of the captured exception inside the Active Pattern and returning that value can be helpful in some situations.</span></span>

### <a name="do-not-use-monadic-error-handling-to-replace-exceptions"></a><span data-ttu-id="00a74-200">Não use o tratamento de erros monadic para substituir exceções</span><span class="sxs-lookup"><span data-stu-id="00a74-200">Do not use monadic error handling to replace exceptions</span></span>

<span data-ttu-id="00a74-201">As exceções são vistas como um pouco da na programação funcional.</span><span class="sxs-lookup"><span data-stu-id="00a74-201">Exceptions are seen as somewhat taboo in functional programming.</span></span> <span data-ttu-id="00a74-202">Na verdade, as exceções violam a pureza, portanto, é seguro considerá-las não muito funcionais.</span><span class="sxs-lookup"><span data-stu-id="00a74-202">Indeed, exceptions violate purity, so it's safe to consider them not-quite functional.</span></span> <span data-ttu-id="00a74-203">No entanto, isso ignora a realidade de onde o código deve ser executado e que podem ocorrer erros de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="00a74-203">However, this ignores the reality of where code must run, and that runtime errors can occur.</span></span> <span data-ttu-id="00a74-204">Em geral, escreva o código na suposição de que a maioria das coisas não é pura nem total, para minimizar surpresas desagradáveis.</span><span class="sxs-lookup"><span data-stu-id="00a74-204">In general, write code on the assumption that most things are neither pure nor total, to minimize unpleasant surprises.</span></span>

<span data-ttu-id="00a74-205">É importante considerar os seguintes pontos fortes/aspectos principais de exceções em relação à sua relevância e à sua adequação no tempo de execução do .NET e no ecossistema entre linguagens como um todo:</span><span class="sxs-lookup"><span data-stu-id="00a74-205">It is important to consider the following core strengths/aspects of Exceptions with respect to their relevance and appropriateness in the .NET runtime and cross-language ecosystem as a whole:</span></span>

1. <span data-ttu-id="00a74-206">Eles contêm informações detalhadas de diagnóstico, o que é muito útil ao depurar um problema.</span><span class="sxs-lookup"><span data-stu-id="00a74-206">They contain detailed diagnostic information, which is very helpful when debugging an issue.</span></span>
2. <span data-ttu-id="00a74-207">Eles são bem compreendidos pelo tempo de execução e por outras linguagens .NET.</span><span class="sxs-lookup"><span data-stu-id="00a74-207">They are well-understood by the runtime and other .NET languages.</span></span>
3. <span data-ttu-id="00a74-208">Eles podem reduzir um timbre significativo em comparação com o código que sai do seu caminho para *evitar* exceções implementando algum subconjunto de sua semântica em uma base ad hoc.</span><span class="sxs-lookup"><span data-stu-id="00a74-208">They can reduce significant boilerplate when compared with code that goes out of its way to *avoid* exceptions by implementing some subset of their semantics on an ad-hoc basis.</span></span>

<span data-ttu-id="00a74-209">Esse terceiro ponto é crítico.</span><span class="sxs-lookup"><span data-stu-id="00a74-209">This third point is critical.</span></span> <span data-ttu-id="00a74-210">Para operações complexas não triviais, a falha ao usar exceções pode resultar em lidar com estruturas como esta:</span><span class="sxs-lookup"><span data-stu-id="00a74-210">For nontrivial complex operations, failing to use exceptions can result in dealing with structures like this:</span></span>

```fsharp
Result<Result<MyType, string>, string list>
```

<span data-ttu-id="00a74-211">Que pode facilmente levar a um código frágil como correspondência de padrões em erros de "tipo de cadeia de caracteres":</span><span class="sxs-lookup"><span data-stu-id="00a74-211">Which can easily lead to fragile code like pattern matching on "stringly-typed" errors:</span></span>

```fsharp
let result = doStuff()
match result with
| Ok r -> ...
| Error e ->
    if e.Contains "Error string 1" then ...
    elif e.Contains "Error string 2" then ...
    else ... // Who knows?
```

<span data-ttu-id="00a74-212">Além disso, pode ser tentador assimilar qualquer exceção no desejo de uma função "simples" que retorna um tipo "interessante":</span><span class="sxs-lookup"><span data-stu-id="00a74-212">Additionally, it can be tempting to swallow any exception in the desire for a "simple" function that returns a "nicer" type:</span></span>

```fsharp
// This is bad!
let tryReadAllText (path : string) =
    try System.IO.File.ReadAllText path |> Some
    with _ -> None
```

<span data-ttu-id="00a74-213">Infelizmente, `tryReadAllText` pode lançar várias exceções com base na infinidade de coisas que podem ocorrer em um sistema de arquivos, e esse código descarta as informações sobre o que pode realmente estar errado em seu ambiente.</span><span class="sxs-lookup"><span data-stu-id="00a74-213">Unfortunately, `tryReadAllText` can throw numerous exceptions based on the myriad of things that can happen on a file system, and this code discards away any information about what might actually be going wrong in your environment.</span></span> <span data-ttu-id="00a74-214">Se você substituir esse código por um tipo de resultado, você voltará à análise da mensagem de erro "tipo de cadeia de caracteres":</span><span class="sxs-lookup"><span data-stu-id="00a74-214">If you replace this code with a result type, then you're back to "stringly-typed" error message parsing:</span></span>

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

<span data-ttu-id="00a74-215">E colocar o objeto de exceção em si no construtor de `Error` apenas força você a lidar corretamente com o tipo de exceção no site de chamada em vez de na função.</span><span class="sxs-lookup"><span data-stu-id="00a74-215">And placing the exception object itself in the `Error` constructor just forces you to properly deal with the exception type at the call site rather than in the function.</span></span> <span data-ttu-id="00a74-216">Fazer isso efetivamente cria exceções marcadas, que são notoriamente unfun para lidar como um chamador de uma API.</span><span class="sxs-lookup"><span data-stu-id="00a74-216">Doing this effectively creates checked exceptions, which are notoriously unfun to deal with as a caller of an API.</span></span>

<span data-ttu-id="00a74-217">Uma boa alternativa para os exemplos acima é capturar exceções *específicas* e retornar um valor significativo no contexto dessa exceção.</span><span class="sxs-lookup"><span data-stu-id="00a74-217">A good alternative to the above examples is to catch *specific* exceptions and return a meaningful value in the context of that exception.</span></span> <span data-ttu-id="00a74-218">Se você modificar a função `tryReadAllText` da seguinte maneira, `None` terá mais significado:</span><span class="sxs-lookup"><span data-stu-id="00a74-218">If you modify the `tryReadAllText` function as follows, `None` has more meaning:</span></span>

```fsharp
let tryReadAllTextIfPresent (path : string) =
    try System.IO.File.ReadAllText path |> Some
    with :? FileNotFoundException -> None
```

<span data-ttu-id="00a74-219">Em vez de funcionar como um problema, essa função agora tratará corretamente o caso quando um arquivo não foi encontrado e atribuirá esse significado a um retorno.</span><span class="sxs-lookup"><span data-stu-id="00a74-219">Instead of functioning as a catch-all, this function will now properly handle the case when a file was not found and assign that meaning to a return.</span></span> <span data-ttu-id="00a74-220">Esse valor de retorno pode mapear para esse caso de erro, sem descartar nenhuma informação contextual ou forçar os chamadores a lidar com um caso que pode não ser relevante nesse ponto no código.</span><span class="sxs-lookup"><span data-stu-id="00a74-220">This return value can map to that error case, while not discarding any contextual information or forcing callers to deal with a case that may not be relevant at that point in the code.</span></span>

<span data-ttu-id="00a74-221">Tipos como `Result<'Success, 'Error>` são apropriados para operações básicas em que não estão aninhados e F# tipos opcionais são perfeitos para representar quando algo poderia retornar *algo* ou *nada*.</span><span class="sxs-lookup"><span data-stu-id="00a74-221">Types such as `Result<'Success, 'Error>` are appropriate for basic operations where they aren't nested, and F# optional types are perfect for representing when something could either return *something* or *nothing*.</span></span> <span data-ttu-id="00a74-222">Eles não são uma substituição de exceções, porém, e não devem ser usados em uma tentativa de substituir exceções.</span><span class="sxs-lookup"><span data-stu-id="00a74-222">They are not a replacement for exceptions, though, and should not be used in an attempt to replace exceptions.</span></span> <span data-ttu-id="00a74-223">Em vez disso, eles devem ser aplicados criteriosamente para abordar aspectos específicos da política de gerenciamento de erros e exceções de formas direcionadas.</span><span class="sxs-lookup"><span data-stu-id="00a74-223">Rather, they should be applied judiciously to address specific aspects of exception and error management policy in targeted ways.</span></span>

## <a name="partial-application-and-point-free-programming"></a><span data-ttu-id="00a74-224">Aplicativo parcial e programação sem ponto</span><span class="sxs-lookup"><span data-stu-id="00a74-224">Partial application and point-free programming</span></span>

<span data-ttu-id="00a74-225">F#dá suporte a aplicativos parciais e, portanto, várias maneiras de programar em um estilo sem ponto.</span><span class="sxs-lookup"><span data-stu-id="00a74-225">F# supports partial application, and thus, various ways to program in a point-free style.</span></span> <span data-ttu-id="00a74-226">Isso pode ser benéfico para a reutilização de código dentro de um módulo ou a implementação de algo, mas geralmente não é algo a ser exposto publicamente.</span><span class="sxs-lookup"><span data-stu-id="00a74-226">This can be beneficial for code reuse within a module or the implementation of something, but it is generally not something to expose publicly.</span></span> <span data-ttu-id="00a74-227">Em geral, a programação sem ponto não é uma questão em si própria e pode adicionar uma barreira cognitiva significativa para pessoas que não estão imersos no estilo.</span><span class="sxs-lookup"><span data-stu-id="00a74-227">In general, point-free programming is not a virtue in and of itself, and can add a significant cognitive barrier for people who are not immersed in the style.</span></span>

### <a name="do-not-use-partial-application-and-currying-in-public-apis"></a><span data-ttu-id="00a74-228">Não use aplicativos parciais e currying em APIs públicas</span><span class="sxs-lookup"><span data-stu-id="00a74-228">Do not use partial application and currying in public APIs</span></span>

<span data-ttu-id="00a74-229">Com pouca exceção, o uso de aplicativos parciais em APIs públicas pode ser confuso para os consumidores.</span><span class="sxs-lookup"><span data-stu-id="00a74-229">With little exception, the use of partial application in public APIs can be confusing for consumers.</span></span> <span data-ttu-id="00a74-230">Normalmente, valores associados a `let`no F# código são **valores**, não **valores de função**.</span><span class="sxs-lookup"><span data-stu-id="00a74-230">Usually, `let`-bound values in F# code are **values**, not **function values**.</span></span> <span data-ttu-id="00a74-231">Misturar valores e valores de função pode resultar em salvar um pequeno número de linhas de código no Exchange para uma grande sobrecarga de cognitiva, especialmente se combinado com operadores como `>>` para compor funções.</span><span class="sxs-lookup"><span data-stu-id="00a74-231">Mixing together values and function values can result in saving a small number of lines of code in exchange for quite a bit of cognitive overhead, especially if combined with operators such as `>>` to compose functions.</span></span>

### <a name="consider-the-tooling-implications-for-point-free-programming"></a><span data-ttu-id="00a74-232">Considere as implicações de ferramentas para a programação sem ponto</span><span class="sxs-lookup"><span data-stu-id="00a74-232">Consider the tooling implications for point-free programming</span></span>

<span data-ttu-id="00a74-233">As funções na forma curried não rotulam seus argumentos.</span><span class="sxs-lookup"><span data-stu-id="00a74-233">Curried functions do not label their arguments.</span></span> <span data-ttu-id="00a74-234">Isso tem implicações de ferramentas.</span><span class="sxs-lookup"><span data-stu-id="00a74-234">This has tooling implications.</span></span> <span data-ttu-id="00a74-235">Considere as duas funções a seguir:</span><span class="sxs-lookup"><span data-stu-id="00a74-235">Consider the following two functions:</span></span>

```fsharp
let func name age =
    printfn "My name is %s and I am %d years old!" name age

let funcWithApplication =
    printfn "My name is %s and I am %d years old!"
```

<span data-ttu-id="00a74-236">Ambas são funções válidas, mas `funcWithApplication` é uma função na forma curried.</span><span class="sxs-lookup"><span data-stu-id="00a74-236">Both are valid functions, but `funcWithApplication` is a curried function.</span></span> <span data-ttu-id="00a74-237">Ao passar o mouse sobre seus tipos em um editor, você verá:</span><span class="sxs-lookup"><span data-stu-id="00a74-237">When you hover over their types in an editor, you see this:</span></span>

```fsharp
val func : name:string -> age:int -> unit

val funcWithApplication : (string -> int -> unit)
```

<span data-ttu-id="00a74-238">No local de chamada, as dicas de ferramenta em ferramentas como o Visual Studio não fornecerão informações significativas sobre o que a `string` e `int` tipos de entrada realmente representam.</span><span class="sxs-lookup"><span data-stu-id="00a74-238">At the call site, tooltips in tooling such as Visual Studio will not give you meaningful information as to what the `string` and `int` input types actually represent.</span></span>

<span data-ttu-id="00a74-239">Se você encontrar um código sem ponto como `funcWithApplication` que é publicamente consumível, é recomendável fazer uma η completa para que as ferramentas possam escolher nomes significativos para os argumentos.</span><span class="sxs-lookup"><span data-stu-id="00a74-239">If you encounter point-free code like `funcWithApplication` that is publicly consumable, it is recommended to do a full η-expansion so that tooling can pick up on meaningful names for arguments.</span></span>

<span data-ttu-id="00a74-240">Além disso, a depuração de código sem ponto pode ser desafiadora, se não impossível.</span><span class="sxs-lookup"><span data-stu-id="00a74-240">Furthermore, debugging point-free code can be challenging, if not impossible.</span></span> <span data-ttu-id="00a74-241">As ferramentas de depuração dependem de valores associados aos nomes (por exemplo, associações de `let`) para que você possa inspecionar valores intermediários no centro por meio da execução.</span><span class="sxs-lookup"><span data-stu-id="00a74-241">Debugging tools rely on values bound to names (for example, `let` bindings) so that you can inspect intermediate values midway through execution.</span></span> <span data-ttu-id="00a74-242">Quando seu código não tem valores a serem inspecionados, não há nada a ser depurado.</span><span class="sxs-lookup"><span data-stu-id="00a74-242">When your code has no values to inspect, there is nothing to debug.</span></span> <span data-ttu-id="00a74-243">No futuro, as ferramentas de depuração podem evoluir para resumir esses valores com base em caminhos executados anteriormente, mas não é uma boa ideia envolver suas opções em *potencial* funcionalidade de depuração.</span><span class="sxs-lookup"><span data-stu-id="00a74-243">In the future, debugging tools may evolve to synthesize these values based on previously executed paths, but it's not a good idea to hedge your bets on *potential* debugging functionality.</span></span>

### <a name="consider-partial-application-as-a-technique-to-reduce-internal-boilerplate"></a><span data-ttu-id="00a74-244">Considere o aplicativo parcial como uma técnica para reduzir o timbre interno</span><span class="sxs-lookup"><span data-stu-id="00a74-244">Consider partial application as a technique to reduce internal boilerplate</span></span>

<span data-ttu-id="00a74-245">Em contraste com o ponto anterior, o aplicativo parcial é uma excelente ferramenta para reduzir o texto clichê dentro de um aplicativo ou os detalhes internos de uma API.</span><span class="sxs-lookup"><span data-stu-id="00a74-245">In contrast to the previous point, partial application is a wonderful tool for reducing boilerplate inside of an application or the deeper internals of an API.</span></span> <span data-ttu-id="00a74-246">Pode ser útil para o teste de unidade da implementação de APIs mais complicadas, em que o clichê é muitas vezes um problema para lidar.</span><span class="sxs-lookup"><span data-stu-id="00a74-246">It can be helpful for unit testing the implementation of more complicated APIs, where boilerplate is often a pain to deal with.</span></span> <span data-ttu-id="00a74-247">Por exemplo, o código a seguir mostra como você pode realizar o que a maioria das estruturas fictícias fornece sem tirar uma dependência externa de tal estrutura e ter que aprender uma API do bespoke relacionada.</span><span class="sxs-lookup"><span data-stu-id="00a74-247">For example, the following code shows how you can accomplish what most mocking frameworks give you without taking an external dependency on such a framework and having to learn a related bespoke API.</span></span>

<span data-ttu-id="00a74-248">Por exemplo, considere a topografia de solução a seguir:</span><span class="sxs-lookup"><span data-stu-id="00a74-248">For example, consider the following solution topography:</span></span>

```
MySolution.sln
|_/ImplementationLogic.fsproj
|_/ImplementationLogic.Tests.fsproj
|_/API.fsproj
```

<span data-ttu-id="00a74-249">`ImplementationLogic.fsproj` pode expor código como:</span><span class="sxs-lookup"><span data-stu-id="00a74-249">`ImplementationLogic.fsproj` might expose code such as:</span></span>

```fsharp
module Transactions =
    let doTransaction txnContext txnType balance =
        ...

type Transactor(ctx, currentBalance) =
    member __.ExecuteTransaction(txnType) =
        Transactions.doTransaction ctx txtType currentBalance
        ...
```

<span data-ttu-id="00a74-250">O teste de unidade `Transactions.doTransaction` no `ImplementationLogic.Tests.fsproj` é fácil:</span><span class="sxs-lookup"><span data-stu-id="00a74-250">Unit testing `Transactions.doTransaction` in `ImplementationLogic.Tests.fsproj` is easy:</span></span>

```fsharp
namespace TransactionsTestingUtil

open Transactions

module TransactionsTestable =
    let getTestableTransactionRoutine mockContext = Transactions.doTransaction mockContext
```

<span data-ttu-id="00a74-251">A aplicação parcial de `doTransaction` com um objeto de contexto fictício permite chamar a função em todos os testes de unidade sem a necessidade de construir um contexto fictício a cada vez:</span><span class="sxs-lookup"><span data-stu-id="00a74-251">Partially applying `doTransaction` with a mocking context object lets you call the function in all of your unit tests without needing to construct a mocked context each time:</span></span>

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

<span data-ttu-id="00a74-252">Essa técnica não deve ser aplicada universalmente a toda a base de código, mas é uma boa maneira de reduzir o texto clichê para os internos complicados e os testes de unidade desses elementos internos.</span><span class="sxs-lookup"><span data-stu-id="00a74-252">This technique should not be universally applied to your entire codebase, but it is a good way to reduce boilerplate for complicated internals and unit testing those internals.</span></span>

## <a name="access-control"></a><span data-ttu-id="00a74-253">Controle de acesso</span><span class="sxs-lookup"><span data-stu-id="00a74-253">Access control</span></span>

<span data-ttu-id="00a74-254">F#tem várias opções para o [controle de acesso](../language-reference/access-control.md), herdadas do que está disponível no tempo de execução do .net.</span><span class="sxs-lookup"><span data-stu-id="00a74-254">F# has multiple options for [Access control](../language-reference/access-control.md), inherited from what is available in the .NET runtime.</span></span> <span data-ttu-id="00a74-255">Eles não são apenas utilizáveis para tipos – você também pode usá-los para funções.</span><span class="sxs-lookup"><span data-stu-id="00a74-255">These are not just usable for types - you can use them for functions, too.</span></span>

* <span data-ttu-id="00a74-256">Prefira tipos e membros não`public` até que você precise que eles sejam publicamente consumíveis.</span><span class="sxs-lookup"><span data-stu-id="00a74-256">Prefer non-`public` types and members until you need them to be publicly consumable.</span></span> <span data-ttu-id="00a74-257">Isso também minimiza o que os consumidores desejam.</span><span class="sxs-lookup"><span data-stu-id="00a74-257">This also minimizes what consumers couple to.</span></span>
* <span data-ttu-id="00a74-258">Busque para manter toda a funcionalidade auxiliar `private`.</span><span class="sxs-lookup"><span data-stu-id="00a74-258">Strive to keep all helper functionality `private`.</span></span>
* <span data-ttu-id="00a74-259">Considere o uso de `[<AutoOpen>]` em um módulo particular de funções auxiliares se eles se tornarem numerosos.</span><span class="sxs-lookup"><span data-stu-id="00a74-259">Consider the use of `[<AutoOpen>]` on a private module of helper functions if they become numerous.</span></span>

## <a name="type-inference-and-generics"></a><span data-ttu-id="00a74-260">Inferência de tipos e genéricos</span><span class="sxs-lookup"><span data-stu-id="00a74-260">Type inference and generics</span></span>

<span data-ttu-id="00a74-261">A inferência de tipos pode evitar que você digite muita clichê.</span><span class="sxs-lookup"><span data-stu-id="00a74-261">Type inference can save you from typing a lot of boilerplate.</span></span> <span data-ttu-id="00a74-262">E a F# generalização automática no compilador pode ajudá-lo a escrever código mais genérico com quase nenhum esforço extra de sua parte.</span><span class="sxs-lookup"><span data-stu-id="00a74-262">And automatic generalization in the F# compiler can help you write more generic code with almost no extra effort on your part.</span></span> <span data-ttu-id="00a74-263">No entanto, esses recursos não são universalmente bons.</span><span class="sxs-lookup"><span data-stu-id="00a74-263">However, these features are not universally good.</span></span>

* <span data-ttu-id="00a74-264">Considere rotular nomes de argumentos com tipos explícitos em APIs públicas e não confie na inferência de tipos para isso.</span><span class="sxs-lookup"><span data-stu-id="00a74-264">Consider labeling argument names with explicit types in public APIs and do not rely on type inference for this.</span></span>

    <span data-ttu-id="00a74-265">O motivo disso é que **você** deve estar no controle da forma de sua API, não do compilador.</span><span class="sxs-lookup"><span data-stu-id="00a74-265">The reason for this is that **you** should be in control of the shape of your API, not the compiler.</span></span> <span data-ttu-id="00a74-266">Embora o compilador possa fazer um bom trabalho em tipos informativos, é possível que a forma da sua API seja alterada se os internos dos quais ele depende tiverem tipos alterados.</span><span class="sxs-lookup"><span data-stu-id="00a74-266">Although the compiler can do a fine job at inferring types for you, it is possible to have the shape of your API change if the internals it relies on have changed types.</span></span> <span data-ttu-id="00a74-267">Isso pode ser o que você deseja, mas certamente resultará em uma alteração de API de interrupção com a qual os consumidores de downstream terão que lidar.</span><span class="sxs-lookup"><span data-stu-id="00a74-267">This may be what you want, but it will almost certainly result in a breaking API change that downstream consumers will then have to deal with.</span></span> <span data-ttu-id="00a74-268">Em vez disso, se você controlar explicitamente a forma de sua API pública, poderá controlar essas alterações significativas.</span><span class="sxs-lookup"><span data-stu-id="00a74-268">Instead, if you explicitly control the shape of your public API, then you can control these breaking changes.</span></span> <span data-ttu-id="00a74-269">Em termos de DDD, isso pode ser considerado uma camada anticorrupção.</span><span class="sxs-lookup"><span data-stu-id="00a74-269">In DDD terms, this can be thought of as an Anti-corruption layer.</span></span>

* <span data-ttu-id="00a74-270">Considere fornecer um nome significativo para seus argumentos genéricos.</span><span class="sxs-lookup"><span data-stu-id="00a74-270">Consider giving a meaningful name to your generic arguments.</span></span>

    <span data-ttu-id="00a74-271">A menos que você esteja escrevendo um código verdadeiramente genérico que não seja específico de um determinado domínio, um nome significativo pode ajudar outros programadores a compreender o domínio no qual estão trabalhando.</span><span class="sxs-lookup"><span data-stu-id="00a74-271">Unless you are writing truly generic code that is not specific to a particular domain, a meaningful name can help other programmers understanding the domain they're working in.</span></span> <span data-ttu-id="00a74-272">Por exemplo, um parâmetro de tipo chamado `'Document` no contexto de interação com um banco de dados de documento torna mais claro que os tipos de documento genéricos podem ser aceitos pela função ou pelo membro com o qual você está trabalhando.</span><span class="sxs-lookup"><span data-stu-id="00a74-272">For example, a type parameter named `'Document` in the context of interacting with a document database makes it clearer that generic document types can be accepted by the function or member you are working with.</span></span>

* <span data-ttu-id="00a74-273">Considere nomear parâmetros de tipo genérico com PascalCase.</span><span class="sxs-lookup"><span data-stu-id="00a74-273">Consider naming generic type parameters with PascalCase.</span></span>

    <span data-ttu-id="00a74-274">Essa é a maneira geral de fazer coisas no .NET, portanto, é recomendável que você use PascalCase em vez de snake_case ou camelCase.</span><span class="sxs-lookup"><span data-stu-id="00a74-274">This is the general way to do things in .NET, so it's recommended that you use PascalCase rather than snake_case or camelCase.</span></span>

<span data-ttu-id="00a74-275">Por fim, a F# generalização automática nem sempre é uma benefício para pessoas que são novas ou uma base de código grande.</span><span class="sxs-lookup"><span data-stu-id="00a74-275">Finally, automatic generalization is not always a boon for people who are new to F# or a large codebase.</span></span> <span data-ttu-id="00a74-276">Há uma sobrecarga cognitiva no uso de componentes genéricos.</span><span class="sxs-lookup"><span data-stu-id="00a74-276">There is cognitive overhead in using components that are generic.</span></span> <span data-ttu-id="00a74-277">Além disso, se as funções generalizadas automaticamente não forem usadas com tipos de entrada diferentes (independentemente de se destinarem a serem usadas como tal), não há nenhum benefício real para eles serem genéricos nesse ponto no tempo.</span><span class="sxs-lookup"><span data-stu-id="00a74-277">Furthermore, if automatically generalized functions are not used with different input types (let alone if they are intended to be used as such), then there is no real benefit to them being generic at that point in time.</span></span> <span data-ttu-id="00a74-278">Sempre considere se o código que você está escrevendo realmente se beneficiará de ser genérico.</span><span class="sxs-lookup"><span data-stu-id="00a74-278">Always consider if the code you are writing will actually benefit from being generic.</span></span>

## <a name="performance"></a><span data-ttu-id="00a74-279">Desempenho</span><span class="sxs-lookup"><span data-stu-id="00a74-279">Performance</span></span>

<span data-ttu-id="00a74-280">F#os valores são imutáveis por padrão, o que permite que você evite determinadas classes de bugs (especialmente aqueles que envolvem simultaneidade e paralelismo).</span><span class="sxs-lookup"><span data-stu-id="00a74-280">F# values are immutable by default, which allows you to avoid certain classes of bugs (especially those involving concurrency and parallelism).</span></span> <span data-ttu-id="00a74-281">No entanto, em determinados casos, para obter eficiência ideal (ou até mesmo razoável) de tempo de execução ou alocações de memória, um intervalo de trabalho pode ser melhor implementado usando a mutação in-loco do estado.</span><span class="sxs-lookup"><span data-stu-id="00a74-281">However, in certain cases, in order to achieve optimal (or even reasonable) efficiency of execution time or memory allocations, a span of work may best be implemented by using in-place mutation of state.</span></span> <span data-ttu-id="00a74-282">Isso é possível em uma base opcional com F# a palavra-chave`mutable`.</span><span class="sxs-lookup"><span data-stu-id="00a74-282">This is possible in an opt-in basis with F# with the `mutable` keyword.</span></span>

<span data-ttu-id="00a74-283">No entanto, o uso F# de `mutable` no pode sentir a probabilidade de uma pureza funcional.</span><span class="sxs-lookup"><span data-stu-id="00a74-283">However, use of `mutable` in F# may feel at odds with functional purity.</span></span> <span data-ttu-id="00a74-284">Isso é bom, se você ajustar as expectativas de pureza para [transparência referencial](https://en.wikipedia.org/wiki/Referential_transparency).</span><span class="sxs-lookup"><span data-stu-id="00a74-284">This is fine, if you adjust expectations from purity to [referential transparency](https://en.wikipedia.org/wiki/Referential_transparency).</span></span> <span data-ttu-id="00a74-285">Transparência referencial-não pureza – é a meta final ao escrever F# funções.</span><span class="sxs-lookup"><span data-stu-id="00a74-285">Referential transparency - not purity - is the end goal when writing F# functions.</span></span> <span data-ttu-id="00a74-286">Isso permite que você escreva uma interface funcional em uma implementação baseada em mutação para código crítico de desempenho.</span><span class="sxs-lookup"><span data-stu-id="00a74-286">This allows you to write a functional interface over a mutation-based implementation for performance critical code.</span></span>

### <a name="wrap-mutable-code-in-immutable-interfaces"></a><span data-ttu-id="00a74-287">Encapsular código mutável em interfaces imutáveis</span><span class="sxs-lookup"><span data-stu-id="00a74-287">Wrap mutable code in immutable interfaces</span></span>

<span data-ttu-id="00a74-288">Com a transparência referencial como meta, é essencial escrever um código que não exponha a Underbelly mutável de funções de desempenho crítico.</span><span class="sxs-lookup"><span data-stu-id="00a74-288">With referential transparency as a goal, it is critical to write code that does not expose the mutable underbelly of performance-critical functions.</span></span> <span data-ttu-id="00a74-289">Por exemplo, o código a seguir implementa a função `Array.contains` na F# biblioteca principal:</span><span class="sxs-lookup"><span data-stu-id="00a74-289">For example, the following code implements the `Array.contains` function in the F# core library:</span></span>

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

<span data-ttu-id="00a74-290">Chamar essa função várias vezes não altera a matriz subjacente, nem requer que você mantenha qualquer estado mutável ao consumi-la.</span><span class="sxs-lookup"><span data-stu-id="00a74-290">Calling this function multiple times does not change the underlying array, nor does it require you to maintain any mutable state in consuming it.</span></span> <span data-ttu-id="00a74-291">Ele é transparevelmente transparente, embora quase todas as linhas de código dentro dele usem mutação.</span><span class="sxs-lookup"><span data-stu-id="00a74-291">It is referentially transparent, even though almost every line of code within it uses mutation.</span></span>

### <a name="consider-encapsulating-mutable-data-in-classes"></a><span data-ttu-id="00a74-292">Considere o encapsulamento de dados mutáveis em classes</span><span class="sxs-lookup"><span data-stu-id="00a74-292">Consider encapsulating mutable data in classes</span></span>

<span data-ttu-id="00a74-293">O exemplo anterior usava uma única função para encapsular operações usando dados mutáveis.</span><span class="sxs-lookup"><span data-stu-id="00a74-293">The previous example used a single function to encapsulate operations using mutable data.</span></span> <span data-ttu-id="00a74-294">Isso nem sempre é suficiente para conjuntos de dados mais complexos.</span><span class="sxs-lookup"><span data-stu-id="00a74-294">This is not always sufficient for more complex sets of data.</span></span> <span data-ttu-id="00a74-295">Considere os seguintes conjuntos de funções:</span><span class="sxs-lookup"><span data-stu-id="00a74-295">Consider the following sets of functions:</span></span>

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

<span data-ttu-id="00a74-296">Esse código é de alto desempenho, mas expõe a estrutura de dados baseada em mutação que os chamadores são responsáveis por manter.</span><span class="sxs-lookup"><span data-stu-id="00a74-296">This code is performant, but it exposes the mutation-based data structure that callers are responsible for maintaining.</span></span> <span data-ttu-id="00a74-297">Isso pode ser encapsulado dentro de uma classe sem Membros subjacentes que podem ser alterados:</span><span class="sxs-lookup"><span data-stu-id="00a74-297">This can be wrapped inside of a class with no underlying members that can change:</span></span>

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

<span data-ttu-id="00a74-298">`Closure1Table` encapsula a estrutura de dados baseada em mutação subjacente, impedindo que os chamadores mantenham a estrutura de dados subjacente.</span><span class="sxs-lookup"><span data-stu-id="00a74-298">`Closure1Table` encapsulates the underlying mutation-based data structure, thereby not forcing callers to maintain the underlying data structure.</span></span> <span data-ttu-id="00a74-299">As classes são uma maneira eficiente de encapsular dados e rotinas com base em mutação sem expor os detalhes aos chamadores.</span><span class="sxs-lookup"><span data-stu-id="00a74-299">Classes are a powerful way to encapsulate data and routines that are mutation-based without exposing the details to callers.</span></span>

### <a name="prefer-let-mutable-to-reference-cells"></a><span data-ttu-id="00a74-300">Preferir `let mutable` para fazer referência a células</span><span class="sxs-lookup"><span data-stu-id="00a74-300">Prefer `let mutable` to reference cells</span></span>

<span data-ttu-id="00a74-301">As células de referência são uma maneira de representar a referência a um valor em vez do próprio valor.</span><span class="sxs-lookup"><span data-stu-id="00a74-301">Reference cells are a way to represent the reference to a value rather than the value itself.</span></span> <span data-ttu-id="00a74-302">Embora eles possam ser usados para código de desempenho crítico, geralmente não são recomendados.</span><span class="sxs-lookup"><span data-stu-id="00a74-302">Although they can be used for performance-critical code, they are generally not recommended.</span></span> <span data-ttu-id="00a74-303">Considere o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="00a74-303">Consider the following example:</span></span>

```fsharp
let kernels =
    let acc = ref Set.empty

    processWorkList startKernels (fun kernel ->
        if not ((!acc).Contains(kernel)) then
            acc := (!acc).Add(kernel)
        ...)

    !acc |> Seq.toList
```

<span data-ttu-id="00a74-304">O uso de uma célula de referência agora "polui" todos os códigos subsequentes com a falta de desreferenciar e rereferenciar os dados subjacentes.</span><span class="sxs-lookup"><span data-stu-id="00a74-304">The use of a reference cell now "pollutes" all subsequent code with having to dereference and re-reference the underlying data.</span></span> <span data-ttu-id="00a74-305">Em vez disso, considere `let mutable`:</span><span class="sxs-lookup"><span data-stu-id="00a74-305">Instead, consider `let mutable`:</span></span>

```fsharp
let kernels =
    let mutable acc = Set.empty

    processWorkList startKernels (fun kernel ->
        if not (acc.Contains(kernel)) then
            acc <- acc.Add(kernel)
        ...)

    acc |> Seq.toList
```

<span data-ttu-id="00a74-306">Além do ponto único de mutação no meio da expressão lambda, todo o outro código que toca `acc` pode fazer isso de uma maneira que não seja diferente do uso de um valor normal de ligação de `let`.</span><span class="sxs-lookup"><span data-stu-id="00a74-306">Aside from the single point of mutation in the middle of the lambda expression, all other code that touches `acc` can do so in a manner that is no different to the usage of a normal `let`-bound immutable value.</span></span> <span data-ttu-id="00a74-307">Isso facilitará a alteração com o passar do tempo.</span><span class="sxs-lookup"><span data-stu-id="00a74-307">This will make it easier to change over time.</span></span>

## <a name="object-programming"></a><span data-ttu-id="00a74-308">Programação de objeto</span><span class="sxs-lookup"><span data-stu-id="00a74-308">Object programming</span></span>

<span data-ttu-id="00a74-309">F#tem suporte completo para objetos e conceitos orientados a objeto (OO).</span><span class="sxs-lookup"><span data-stu-id="00a74-309">F# has full support for objects and object-oriented (OO) concepts.</span></span> <span data-ttu-id="00a74-310">Embora muitos conceitos de OO sejam poderosos e úteis, nem todos eles são ideais para uso.</span><span class="sxs-lookup"><span data-stu-id="00a74-310">Although many OO concepts are powerful and useful, not all of them are ideal to use.</span></span> <span data-ttu-id="00a74-311">As listas a seguir oferecem orientação sobre as categorias de recursos do OO em um alto nível.</span><span class="sxs-lookup"><span data-stu-id="00a74-311">The following lists offer guidance on categories of OO features at a high level.</span></span>

<span data-ttu-id="00a74-312">**Considere o uso desses recursos em muitas situações:**</span><span class="sxs-lookup"><span data-stu-id="00a74-312">**Consider using these features in many situations:**</span></span>

* <span data-ttu-id="00a74-313">Notação de ponto (`x.Length`)</span><span class="sxs-lookup"><span data-stu-id="00a74-313">Dot notation (`x.Length`)</span></span>
* <span data-ttu-id="00a74-314">Membros da instância</span><span class="sxs-lookup"><span data-stu-id="00a74-314">Instance members</span></span>
* <span data-ttu-id="00a74-315">Construtores implícitos</span><span class="sxs-lookup"><span data-stu-id="00a74-315">Implicit constructors</span></span>
* <span data-ttu-id="00a74-316">Membros estáticos</span><span class="sxs-lookup"><span data-stu-id="00a74-316">Static members</span></span>
* <span data-ttu-id="00a74-317">Notação do indexador (`arr.[x]`)</span><span class="sxs-lookup"><span data-stu-id="00a74-317">Indexer notation (`arr.[x]`)</span></span>
* <span data-ttu-id="00a74-318">Argumentos nomeados e opcionais</span><span class="sxs-lookup"><span data-stu-id="00a74-318">Named and Optional arguments</span></span>
* <span data-ttu-id="00a74-319">Interfaces e implementações de interface</span><span class="sxs-lookup"><span data-stu-id="00a74-319">Interfaces and interface implementations</span></span>

<span data-ttu-id="00a74-320">**Não alcance esses recursos primeiro, mas os aplica criteriosamente quando é conveniente resolver um problema:**</span><span class="sxs-lookup"><span data-stu-id="00a74-320">**Don't reach for these features first, but do judiciously apply them when they are convenient to solve a problem:**</span></span>

* <span data-ttu-id="00a74-321">Sobrecarga de método</span><span class="sxs-lookup"><span data-stu-id="00a74-321">Method overloading</span></span>
* <span data-ttu-id="00a74-322">Dados mutáveis encapsulados</span><span class="sxs-lookup"><span data-stu-id="00a74-322">Encapsulated mutable data</span></span>
* <span data-ttu-id="00a74-323">Operadores em tipos</span><span class="sxs-lookup"><span data-stu-id="00a74-323">Operators on types</span></span>
* <span data-ttu-id="00a74-324">Propriedades automáticas</span><span class="sxs-lookup"><span data-stu-id="00a74-324">Auto properties</span></span>
* <span data-ttu-id="00a74-325">Implementando `IDisposable` e `IEnumerable`</span><span class="sxs-lookup"><span data-stu-id="00a74-325">Implementing `IDisposable` and `IEnumerable`</span></span>
* <span data-ttu-id="00a74-326">Extensões de tipo</span><span class="sxs-lookup"><span data-stu-id="00a74-326">Type extensions</span></span>
* <span data-ttu-id="00a74-327">Eventos</span><span class="sxs-lookup"><span data-stu-id="00a74-327">Events</span></span>
* <span data-ttu-id="00a74-328">Structs</span><span class="sxs-lookup"><span data-stu-id="00a74-328">Structs</span></span>
* <span data-ttu-id="00a74-329">Delegados</span><span class="sxs-lookup"><span data-stu-id="00a74-329">Delegates</span></span>
* <span data-ttu-id="00a74-330">Enums</span><span class="sxs-lookup"><span data-stu-id="00a74-330">Enums</span></span>

<span data-ttu-id="00a74-331">**Geralmente, evite esses recursos, a menos que você precise usá-los:**</span><span class="sxs-lookup"><span data-stu-id="00a74-331">**Generally avoid these features unless you must use them:**</span></span>

* <span data-ttu-id="00a74-332">Hierarquias de tipos baseadas em herança e herança de implementação</span><span class="sxs-lookup"><span data-stu-id="00a74-332">Inheritance-based type hierarchies and implementation inheritance</span></span>
* <span data-ttu-id="00a74-333">Nulos e `Unchecked.defaultof<_>`</span><span class="sxs-lookup"><span data-stu-id="00a74-333">Nulls and `Unchecked.defaultof<_>`</span></span>

### <a name="prefer-composition-over-inheritance"></a><span data-ttu-id="00a74-334">Preferir composição sobre herança</span><span class="sxs-lookup"><span data-stu-id="00a74-334">Prefer composition over inheritance</span></span>

<span data-ttu-id="00a74-335">A [composição sobre herança](https://en.wikipedia.org/wiki/Composition_over_inheritance) é um idioma muito positivo que o F# bom código pode aderir.</span><span class="sxs-lookup"><span data-stu-id="00a74-335">[Composition over inheritance](https://en.wikipedia.org/wiki/Composition_over_inheritance) is a long-standing idiom that good F# code can adhere to.</span></span> <span data-ttu-id="00a74-336">O princípio fundamental é que você não deve expor uma classe base e forçar chamadores a herdar dessa classe base para obter a funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="00a74-336">The fundamental principle is that you should not expose a base class and force callers to inherit from that base class to get functionality.</span></span>

### <a name="use-object-expressions-to-implement-interfaces-if-you-dont-need-a-class"></a><span data-ttu-id="00a74-337">Use expressões de objeto para implementar interfaces se você não precisar de uma classe</span><span class="sxs-lookup"><span data-stu-id="00a74-337">Use object expressions to implement interfaces if you don't need a class</span></span>

<span data-ttu-id="00a74-338">As [expressões de objeto](../language-reference/object-expressions.md) permitem que você implemente interfaces dinamicamente, associando a interface implementada a um valor sem precisar fazer isso dentro de uma classe.</span><span class="sxs-lookup"><span data-stu-id="00a74-338">[Object Expressions](../language-reference/object-expressions.md) allow you to implement interfaces on the fly, binding the implemented interface to a value without needing to do so inside of a class.</span></span> <span data-ttu-id="00a74-339">Isso é conveniente, especialmente se você _só_ precisa implementar a interface e não precisa de uma classe completa.</span><span class="sxs-lookup"><span data-stu-id="00a74-339">This is convenient, especially if you _only_ need to implement the interface and have no need for a full class.</span></span>

<span data-ttu-id="00a74-340">Por exemplo, aqui está o código que é executado no [Ionide](http://ionide.io/) para fornecer uma ação de correção de código se você adicionou um símbolo que você não tem uma instrução `open` para:</span><span class="sxs-lookup"><span data-stu-id="00a74-340">For example, here is the code that is run in [Ionide](http://ionide.io/) to provide a code fix action if you've added a symbol that you don't have an `open` statement for:</span></span>

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

<span data-ttu-id="00a74-341">Como não há necessidade de uma classe ao interagir com a API de Visual Studio Code, as expressões de objeto são uma ferramenta ideal para isso.</span><span class="sxs-lookup"><span data-stu-id="00a74-341">Because there is no need for a class when interacting with the Visual Studio Code API, Object Expressions are an ideal tool for this.</span></span> <span data-ttu-id="00a74-342">Eles também são valiosos para testes de unidade, quando você deseja stub de uma interface com rotinas de teste de maneira ad hoc.</span><span class="sxs-lookup"><span data-stu-id="00a74-342">They are also valuable for unit testing, when you want to stub out an interface with test routines in an ad hoc manner.</span></span>

## <a name="consider-type-abbreviations-to-shorten-signatures"></a><span data-ttu-id="00a74-343">Considere abreviações de tipo para diminuir as assinaturas</span><span class="sxs-lookup"><span data-stu-id="00a74-343">Consider Type Abbreviations to shorten signatures</span></span>

<span data-ttu-id="00a74-344">As [abreviações de tipo](../language-reference/type-abbreviations.md) são uma maneira conveniente de atribuir um rótulo a outro tipo, como uma assinatura de função ou um tipo mais complexo.</span><span class="sxs-lookup"><span data-stu-id="00a74-344">[Type Abbreviations](../language-reference/type-abbreviations.md) are a convenient way to assign a label to another type, such as a function signature or a more complex type.</span></span> <span data-ttu-id="00a74-345">Por exemplo, o alias a seguir atribui um rótulo para o que é necessário para definir uma computação com [CNTK](https://docs.microsoft.com/cognitive-toolkit/), uma biblioteca de aprendizado profundo:</span><span class="sxs-lookup"><span data-stu-id="00a74-345">For example, the following alias assigns a label to what's needed to define a computation with [CNTK](https://docs.microsoft.com/cognitive-toolkit/), a deep learning library:</span></span>

```fsharp
open CNTK

// DeviceDescriptor, Variable, and Function all come from CNTK
type Computation = DeviceDescriptor -> Variable -> Function
```

<span data-ttu-id="00a74-346">O nome do `Computation` é uma maneira conveniente de denotar qualquer função que corresponda à assinatura que está sendo alias.</span><span class="sxs-lookup"><span data-stu-id="00a74-346">The `Computation` name is a convenient way to denote any function that matches the signature it is aliasing.</span></span> <span data-ttu-id="00a74-347">Usar abreviações de tipo como essa é conveniente e permite um código mais sucinto.</span><span class="sxs-lookup"><span data-stu-id="00a74-347">Using Type Abbreviations like this is convenient and allows for more succinct code.</span></span>

### <a name="avoid-using-type-abbreviations-to-represent-your-domain"></a><span data-ttu-id="00a74-348">Evite usar abreviações de tipo para representar seu domínio</span><span class="sxs-lookup"><span data-stu-id="00a74-348">Avoid using Type Abbreviations to represent your domain</span></span>

<span data-ttu-id="00a74-349">Embora as abreviações de tipo sejam convenientes para dar um nome às assinaturas de função, elas podem ser confusas ao abreviar outros tipos.</span><span class="sxs-lookup"><span data-stu-id="00a74-349">Although Type Abbreviations are convenient for giving a name to function signatures, they can be confusing when abbreviating other types.</span></span> <span data-ttu-id="00a74-350">Considere esta abreviação:</span><span class="sxs-lookup"><span data-stu-id="00a74-350">Consider this abbreviation:</span></span>

```fsharp
// Does not actually abstract integers.
type BufferSize = int
```

<span data-ttu-id="00a74-351">Isso pode ser confuso de várias maneiras:</span><span class="sxs-lookup"><span data-stu-id="00a74-351">This can be confusing in multiple ways:</span></span>

* <span data-ttu-id="00a74-352">`BufferSize` não é uma abstração; Ele é apenas outro nome para um inteiro.</span><span class="sxs-lookup"><span data-stu-id="00a74-352">`BufferSize` is not an abstraction; it is just another name for an integer.</span></span>
* <span data-ttu-id="00a74-353">Se `BufferSize` for exposta em uma API pública, ela poderá facilmente ser interpretada incorretamente para significar mais do que apenas `int`.</span><span class="sxs-lookup"><span data-stu-id="00a74-353">If `BufferSize` is exposed in a public API, it can easily be misinterpreted to mean more than just `int`.</span></span> <span data-ttu-id="00a74-354">Geralmente, os tipos de domínio têm vários atributos e não são tipos primitivos como `int`.</span><span class="sxs-lookup"><span data-stu-id="00a74-354">Generally, domain types have multiple attributes to them and are not primitive types like `int`.</span></span> <span data-ttu-id="00a74-355">Essa abreviação viola essa suposição.</span><span class="sxs-lookup"><span data-stu-id="00a74-355">This abbreviation violates that assumption.</span></span>
* <span data-ttu-id="00a74-356">A capitalização de `BufferSize` (PascalCase) implica que esse tipo contém mais dados.</span><span class="sxs-lookup"><span data-stu-id="00a74-356">The casing of `BufferSize` (PascalCase) implies that this type holds more data.</span></span>
* <span data-ttu-id="00a74-357">Esse alias não oferece maior clareza em comparação com o fornecimento de um argumento nomeado para uma função.</span><span class="sxs-lookup"><span data-stu-id="00a74-357">This alias does not offer increased clarity compared with providing a named argument to a function.</span></span>
* <span data-ttu-id="00a74-358">A abreviação não será manifestada no IL compilado; é apenas um inteiro e esse alias é uma construção de tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="00a74-358">The abbreviation will not manifest in compiled IL; it is just an integer and this alias is a compile-time construct.</span></span>

```fsharp
module Networking =
    ...
    let send data (bufferSize: int) = ...
```

<span data-ttu-id="00a74-359">Em resumo, a armadilha com abreviações de tipo é que elas **não** são abstrações sobre os tipos que estão abreviando.</span><span class="sxs-lookup"><span data-stu-id="00a74-359">In summary, the pitfall with Type Abbreviations is that they are **not** abstractions over the types they are abbreviating.</span></span> <span data-ttu-id="00a74-360">No exemplo anterior, `BufferSize` é apenas um `int` nos bastidores, sem dados adicionais nem qualquer benefício do sistema de tipos além do que `int` já tem.</span><span class="sxs-lookup"><span data-stu-id="00a74-360">In the previous example, `BufferSize` is just an `int` under the covers, with no additional data, nor any benefits from the type system besides what `int` already has.</span></span>

<span data-ttu-id="00a74-361">Uma abordagem alternativa para usar abreviações de tipo para representar um domínio é usar uniões discriminadas de um único caso.</span><span class="sxs-lookup"><span data-stu-id="00a74-361">An alternative approach to using type abbreviations to represent a domain is to use single-case discriminated unions.</span></span> <span data-ttu-id="00a74-362">O exemplo anterior pode ser modelado da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="00a74-362">The previous sample can be modeled as follows:</span></span>

```fsharp
type BufferSize = BufferSize of int
```

<span data-ttu-id="00a74-363">Se você escrever um código que opere em termos de `BufferSize` e seu valor subjacente, você precisará construir um em vez de passar em qualquer inteiro arbitrário:</span><span class="sxs-lookup"><span data-stu-id="00a74-363">If you write code that operates in terms of `BufferSize` and its underlying value, you need to construct one rather than pass in any arbitrary integer:</span></span>

```fsharp
module Networking =
    ...
    let send data (BufferSize size) =
    ...
```

<span data-ttu-id="00a74-364">Isso reduz a probabilidade de passar erroneamente um inteiro arbitrário para a função `send`, porque o chamador deve construir um tipo de `BufferSize` para encapsular um valor antes de chamar a função.</span><span class="sxs-lookup"><span data-stu-id="00a74-364">This reduces the likelihood of mistakenly passing an arbitrary integer into the `send` function, because the caller must construct a `BufferSize` type to wrap a value before calling the function.</span></span>
