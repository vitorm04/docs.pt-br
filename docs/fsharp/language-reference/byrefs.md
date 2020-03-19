---
title: Byrefs
description: Saiba mais sobre os tipos byref e byref em F#, que são usados para programação de baixo nível.
ms.date: 11/04/2019
ms.openlocfilehash: 527f465ee87fe153a2deae1306b6730531dc4123
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187046"
---
# <a name="byrefs"></a><span data-ttu-id="e220a-103">Byrefs</span><span class="sxs-lookup"><span data-stu-id="e220a-103">Byrefs</span></span>

<span data-ttu-id="e220a-104">F# tem duas principais áreas de destaque que lidam com o espaço de programação de baixo nível:</span><span class="sxs-lookup"><span data-stu-id="e220a-104">F# has two major feature areas that deal in the space of low-level programming:</span></span>

* <span data-ttu-id="e220a-105">`byref` / Os `inref` / tipos, que são ponteiros gerenciados. `outref`</span><span class="sxs-lookup"><span data-stu-id="e220a-105">The `byref`/`inref`/`outref` types, which are managed pointers.</span></span> <span data-ttu-id="e220a-106">Eles têm restrições de uso para que você não possa compilar um programa que seja inválido no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="e220a-106">They have restrictions on usage so that you cannot compile a program that is invalid at run time.</span></span>
* <span data-ttu-id="e220a-107">Uma `byref`estrutura semelhante, que é uma [estrutura](structures.md) que tem semântica semelhante `byref<'T>`e as mesmas restrições de tempo de compilação que .</span><span class="sxs-lookup"><span data-stu-id="e220a-107">A `byref`-like struct, which is a [structure](structures.md) that has similar semantics and the same compile-time restrictions as `byref<'T>`.</span></span> <span data-ttu-id="e220a-108">Um exemplo <xref:System.Span%601>é .</span><span class="sxs-lookup"><span data-stu-id="e220a-108">One example is <xref:System.Span%601>.</span></span>

## <a name="syntax"></a><span data-ttu-id="e220a-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e220a-109">Syntax</span></span>

```fsharp
// Byref types as parameters
let f (x: byref<'T>) = ()
let g (x: inref<'T>) = ()
let h (x: outref<'T>) = ()

// Calling a function with a byref parameter
let mutable x = 3
f &x

// Declaring a byref-like struct
open System.Runtime.CompilerServices

[<Struct; IsByRefLike>]
type S(count1: int, count2: int) =
    member x.Count1 = count1
    member x.Count2 = count2
```

## <a name="byref-inref-and-outref"></a><span data-ttu-id="e220a-110">Byref, inref e outref</span><span class="sxs-lookup"><span data-stu-id="e220a-110">Byref, inref, and outref</span></span>

<span data-ttu-id="e220a-111">Existem três `byref`formas de:</span><span class="sxs-lookup"><span data-stu-id="e220a-111">There are three forms of `byref`:</span></span>

* <span data-ttu-id="e220a-112">`inref<'T>`, um ponteiro gerenciado para ler o valor subjacente.</span><span class="sxs-lookup"><span data-stu-id="e220a-112">`inref<'T>`, a managed pointer for reading the underlying value.</span></span>
* <span data-ttu-id="e220a-113">`outref<'T>`, um ponteiro gerenciado para escrever para o valor subjacente.</span><span class="sxs-lookup"><span data-stu-id="e220a-113">`outref<'T>`, a managed pointer for writing to the underlying value.</span></span>
* <span data-ttu-id="e220a-114">`byref<'T>`, um ponteiro gerenciado para ler e escrever o valor subjacente.</span><span class="sxs-lookup"><span data-stu-id="e220a-114">`byref<'T>`, a managed pointer for reading and writing the underlying value.</span></span>

<span data-ttu-id="e220a-115">Pode `byref<'T>` ser passado `inref<'T>` onde um é esperado.</span><span class="sxs-lookup"><span data-stu-id="e220a-115">A `byref<'T>` can be passed where an `inref<'T>` is expected.</span></span> <span data-ttu-id="e220a-116">Da mesma `byref<'T>` forma, pode-se passar onde se espera um. `outref<'T>`</span><span class="sxs-lookup"><span data-stu-id="e220a-116">Similarly, a `byref<'T>` can be passed where an `outref<'T>` is expected.</span></span>

## <a name="using-byrefs"></a><span data-ttu-id="e220a-117">Usando byrefs</span><span class="sxs-lookup"><span data-stu-id="e220a-117">Using byrefs</span></span>

<span data-ttu-id="e220a-118">Para usar `inref<'T>`um , você precisa `&`obter um valor de ponteiro com :</span><span class="sxs-lookup"><span data-stu-id="e220a-118">To use a `inref<'T>`, you need to get a pointer value with `&`:</span></span>

```fsharp
open System

let f (dt: inref<DateTime>) =
    printfn "Now: %s" (dt.ToString())

let usage =
    let dt = DateTime.Now
    f &dt // Pass a pointer to 'dt'
```

<span data-ttu-id="e220a-119">Para escrever no ponteiro `outref<'T>` usando `byref<'T>`um ou , você também deve `mutable`fazer o valor que você pegar um ponteiro para .</span><span class="sxs-lookup"><span data-stu-id="e220a-119">To write to the pointer by using an `outref<'T>` or `byref<'T>`, you must also make the value you grab a pointer to `mutable`.</span></span>

```fsharp
open System

let f (dt: byref<DateTime>) =
    printfn "Now: %s" (dt.ToString())
    dt <- DateTime.Now

// Make 'dt' mutable
let mutable dt = DateTime.Now

// Now you can pass the pointer to 'dt'
f &dt
```

<span data-ttu-id="e220a-120">Se você estiver apenas escrevendo o ponteiro `outref<'T>` em `byref<'T>`vez de lê-lo, considere usar em vez de .</span><span class="sxs-lookup"><span data-stu-id="e220a-120">If you are only writing the pointer instead of reading it, consider using `outref<'T>` instead of `byref<'T>`.</span></span>

### <a name="inref-semantics"></a><span data-ttu-id="e220a-121">Semântica inref</span><span class="sxs-lookup"><span data-stu-id="e220a-121">Inref semantics</span></span>

<span data-ttu-id="e220a-122">Considere o código a seguir:</span><span class="sxs-lookup"><span data-stu-id="e220a-122">Consider the following code:</span></span>

```fsharp
let f (x: inref<SomeStruct>) = x.SomeField
```

<span data-ttu-id="e220a-123">Semanticamente, isso significa o seguinte:</span><span class="sxs-lookup"><span data-stu-id="e220a-123">Semantically, this means the following:</span></span>

* <span data-ttu-id="e220a-124">O suporte `x` do ponteiro só pode usá-lo para ler o valor.</span><span class="sxs-lookup"><span data-stu-id="e220a-124">The holder of the `x` pointer may only use it to read the value.</span></span>
* <span data-ttu-id="e220a-125">Qualquer ponteiro adquirido `struct` para campos `SomeStruct` aninhados dentro é dado tipo `inref<_>`.</span><span class="sxs-lookup"><span data-stu-id="e220a-125">Any pointer acquired to `struct` fields nested within `SomeStruct` are given type `inref<_>`.</span></span>

<span data-ttu-id="e220a-126">O seguinte também é verdadeiro:</span><span class="sxs-lookup"><span data-stu-id="e220a-126">The following is also true:</span></span>

* <span data-ttu-id="e220a-127">Não há implicação de que outros segmentos ou `x`codinomes não tenham acesso à gravação .</span><span class="sxs-lookup"><span data-stu-id="e220a-127">There is no implication that other threads or aliases do not have write access to `x`.</span></span>
* <span data-ttu-id="e220a-128">Não há implicação que `SomeStruct` seja imutável em virtude de `x` ser um `inref`.</span><span class="sxs-lookup"><span data-stu-id="e220a-128">There is no implication that `SomeStruct` is immutable by virtue of `x` being an `inref`.</span></span>

<span data-ttu-id="e220a-129">No entanto, para **are** os tipos de valor `this` F# que são `inref`imutáveis, o ponteiro é inferido como um .</span><span class="sxs-lookup"><span data-stu-id="e220a-129">However, for F# value types that **are** immutable, the `this` pointer is inferred to be an `inref`.</span></span>

<span data-ttu-id="e220a-130">Todas essas regras juntas significam que `inref` o titular de um ponteiro não pode modificar o conteúdo imediato da memória que está sendo apontada.</span><span class="sxs-lookup"><span data-stu-id="e220a-130">All of these rules together mean that the holder of an `inref` pointer may not modify the immediate contents of the memory being pointed to.</span></span>

### <a name="outref-semantics"></a><span data-ttu-id="e220a-131">Semântica outref</span><span class="sxs-lookup"><span data-stu-id="e220a-131">Outref semantics</span></span>

<span data-ttu-id="e220a-132">O objetivo `outref<'T>` é indicar que o ponteiro só deve ser escrito para.</span><span class="sxs-lookup"><span data-stu-id="e220a-132">The purpose of `outref<'T>` is to indicate that the pointer should only be written to.</span></span> <span data-ttu-id="e220a-133">Inesperadamente, `outref<'T>` permite ler o valor subjacente apesar de seu nome.</span><span class="sxs-lookup"><span data-stu-id="e220a-133">Unexpectedly, `outref<'T>` permits reading the underlying value despite its name.</span></span> <span data-ttu-id="e220a-134">Isto é para fins de compatibilidade.</span><span class="sxs-lookup"><span data-stu-id="e220a-134">This is for compatibility purposes.</span></span> <span data-ttu-id="e220a-135">Semanticamente, `outref<'T>` não é `byref<'T>`diferente de .</span><span class="sxs-lookup"><span data-stu-id="e220a-135">Semantically, `outref<'T>` is no different than `byref<'T>`.</span></span>

### <a name="interop-with-c"></a><span data-ttu-id="e220a-136">Interop com C\#</span><span class="sxs-lookup"><span data-stu-id="e220a-136">Interop with C\#</span></span>

<span data-ttu-id="e220a-137">C# suporta `in ref` as `out ref` palavras-chave, `ref` além de retornos.</span><span class="sxs-lookup"><span data-stu-id="e220a-137">C# supports the `in ref` and `out ref` keywords, in addition to `ref` returns.</span></span> <span data-ttu-id="e220a-138">A tabela a seguir mostra como F# interpreta o que C# emite:</span><span class="sxs-lookup"><span data-stu-id="e220a-138">The following table shows how F# interprets what C# emits:</span></span>

|<span data-ttu-id="e220a-139">C# construir</span><span class="sxs-lookup"><span data-stu-id="e220a-139">C# construct</span></span>|<span data-ttu-id="e220a-140">F# infere</span><span class="sxs-lookup"><span data-stu-id="e220a-140">F# infers</span></span>|
|------------|---------|
|<span data-ttu-id="e220a-141">`ref`valor de retorno</span><span class="sxs-lookup"><span data-stu-id="e220a-141">`ref` return value</span></span>|`outref<'T>`|
|<span data-ttu-id="e220a-142">`ref readonly`valor de retorno</span><span class="sxs-lookup"><span data-stu-id="e220a-142">`ref readonly` return value</span></span>|`inref<'T>`|
|<span data-ttu-id="e220a-143">Parâmetro `in ref`</span><span class="sxs-lookup"><span data-stu-id="e220a-143">`in ref` parameter</span></span>|`inref<'T>`|
|<span data-ttu-id="e220a-144">Parâmetro `out ref`</span><span class="sxs-lookup"><span data-stu-id="e220a-144">`out ref` parameter</span></span>|`outref<'T>`|

<span data-ttu-id="e220a-145">A tabela a seguir mostra o que F# emite:</span><span class="sxs-lookup"><span data-stu-id="e220a-145">The following table shows what F# emits:</span></span>

|<span data-ttu-id="e220a-146">F# construir</span><span class="sxs-lookup"><span data-stu-id="e220a-146">F# construct</span></span>|<span data-ttu-id="e220a-147">Construção emitida</span><span class="sxs-lookup"><span data-stu-id="e220a-147">Emitted construct</span></span>|
|------------|-----------------|
|<span data-ttu-id="e220a-148">Argumento `inref<'T>`</span><span class="sxs-lookup"><span data-stu-id="e220a-148">`inref<'T>` argument</span></span>|<span data-ttu-id="e220a-149">`[In]`atributo sobre o argumento</span><span class="sxs-lookup"><span data-stu-id="e220a-149">`[In]` attribute on argument</span></span>|
|<span data-ttu-id="e220a-150">`inref<'T>`Retorno</span><span class="sxs-lookup"><span data-stu-id="e220a-150">`inref<'T>` return</span></span>|<span data-ttu-id="e220a-151">`modreq`atributo sobre o valor</span><span class="sxs-lookup"><span data-stu-id="e220a-151">`modreq` attribute on value</span></span>|
|<span data-ttu-id="e220a-152">`inref<'T>`em slot abstrato ou implementação</span><span class="sxs-lookup"><span data-stu-id="e220a-152">`inref<'T>` in abstract slot or implementation</span></span>|<span data-ttu-id="e220a-153">`modreq`em argumento ou retorno</span><span class="sxs-lookup"><span data-stu-id="e220a-153">`modreq` on argument or return</span></span>|
|<span data-ttu-id="e220a-154">Argumento `outref<'T>`</span><span class="sxs-lookup"><span data-stu-id="e220a-154">`outref<'T>` argument</span></span>|<span data-ttu-id="e220a-155">`[Out]`atributo sobre o argumento</span><span class="sxs-lookup"><span data-stu-id="e220a-155">`[Out]` attribute on argument</span></span>|

### <a name="type-inference-and-overloading-rules"></a><span data-ttu-id="e220a-156">Digite regras de inferência e sobrecarga</span><span class="sxs-lookup"><span data-stu-id="e220a-156">Type inference and overloading rules</span></span>

<span data-ttu-id="e220a-157">Um `inref<'T>` tipo é inferido pelo compilador F# nos seguintes casos:</span><span class="sxs-lookup"><span data-stu-id="e220a-157">An `inref<'T>` type is inferred by the F# compiler in the following cases:</span></span>

1. <span data-ttu-id="e220a-158">Um parâmetro .NET ou um `IsReadOnly` tipo de retorno que tenha um atributo.</span><span class="sxs-lookup"><span data-stu-id="e220a-158">A .NET parameter or return type that has an `IsReadOnly` attribute.</span></span>
2. <span data-ttu-id="e220a-159">O `this` ponteiro em um tipo de estrutura que não tem campos mutáveis.</span><span class="sxs-lookup"><span data-stu-id="e220a-159">The `this` pointer on a struct type that has no mutable fields.</span></span>
3. <span data-ttu-id="e220a-160">O endereço de um local `inref<_>` de memória derivado de outro ponteiro.</span><span class="sxs-lookup"><span data-stu-id="e220a-160">The address of a memory location derived from another `inref<_>` pointer.</span></span>

<span data-ttu-id="e220a-161">Quando um endereço `inref` implícito de um está sendo `SomeType` tomado, uma sobrecarga com um `inref<SomeType>`argumento de tipo é preferível a uma sobrecarga com um argumento de tipo .</span><span class="sxs-lookup"><span data-stu-id="e220a-161">When an implicit address of an `inref` is being taken, an overload with an argument of type `SomeType` is preferred to an overload with an argument of type `inref<SomeType>`.</span></span> <span data-ttu-id="e220a-162">Por exemplo: </span><span class="sxs-lookup"><span data-stu-id="e220a-162">For example:</span></span>

```fsharp
type C() =
    static member M(x: System.DateTime) = x.AddDays(1.0)
    static member M(x: inref<System.DateTime>) = x.AddDays(2.0)
    static member M2(x: System.DateTime, y: int) = x.AddDays(1.0)
    static member M2(x: inref<System.DateTime>, y: int) = x.AddDays(2.0)

let res = System.DateTime.Now
let v =  C.M(res)
let v2 =  C.M2(res, 4)
```

<span data-ttu-id="e220a-163">Em ambos os casos, `System.DateTime` as sobrecargas tomadas `inref<System.DateTime>`são resolvidas em vez das sobrecargas tomadas .</span><span class="sxs-lookup"><span data-stu-id="e220a-163">In both cases, the overloads taking `System.DateTime` are resolved rather than the overloads taking `inref<System.DateTime>`.</span></span>

## <a name="byref-like-structs"></a><span data-ttu-id="e220a-164">Estruturas semelhantes a byref</span><span class="sxs-lookup"><span data-stu-id="e220a-164">Byref-like structs</span></span>

<span data-ttu-id="e220a-165">`byref` / `inref` / Além do `outref` trio, você pode definir suas próprias estruturas `byref`que podem aderir à semântica.</span><span class="sxs-lookup"><span data-stu-id="e220a-165">In addition to the `byref`/`inref`/`outref` trio, you can define your own structs that can adhere to `byref`-like semantics.</span></span> <span data-ttu-id="e220a-166">Isso é feito <xref:System.Runtime.CompilerServices.IsByRefLikeAttribute> com o atributo:</span><span class="sxs-lookup"><span data-stu-id="e220a-166">This is done with the <xref:System.Runtime.CompilerServices.IsByRefLikeAttribute> attribute:</span></span>

```fsharp
open System
open System.Runtime.CompilerServices

[<IsByRefLike; Struct>]
type S(count1: Span<int>, count2: Span<int>) =
    member x.Count1 = count1
    member x.Count2 = count2
```

<span data-ttu-id="e220a-167">`IsByRefLike`não implica `Struct`.</span><span class="sxs-lookup"><span data-stu-id="e220a-167">`IsByRefLike` does not imply `Struct`.</span></span> <span data-ttu-id="e220a-168">Ambos devem estar presentes no tipo.</span><span class="sxs-lookup"><span data-stu-id="e220a-168">Both must be present on the type.</span></span>

<span data-ttu-id="e220a-169">Uma`byref`estrutura " -like" em F# é um tipo de valor vinculado à pilha.</span><span class="sxs-lookup"><span data-stu-id="e220a-169">A "`byref`-like" struct in F# is a stack-bound value type.</span></span> <span data-ttu-id="e220a-170">Ele nunca é alocado no monte gerenciado.</span><span class="sxs-lookup"><span data-stu-id="e220a-170">It is never allocated on the managed heap.</span></span> <span data-ttu-id="e220a-171">Uma `byref`estrutura semelhante é útil para programação de alto desempenho, pois é aplicada com um conjunto de verificações fortes sobre a vida útil e a não captura.</span><span class="sxs-lookup"><span data-stu-id="e220a-171">A `byref`-like struct is useful for high-performance programming, as it is enforced with set of strong checks about lifetime and non-capture.</span></span> <span data-ttu-id="e220a-172">As regras são:</span><span class="sxs-lookup"><span data-stu-id="e220a-172">The rules are:</span></span>

* <span data-ttu-id="e220a-173">Eles podem ser usados como parâmetros de função, parâmetros de método, variáveis locais, retornos do método.</span><span class="sxs-lookup"><span data-stu-id="e220a-173">They can be used as function parameters, method parameters, local variables, method returns.</span></span>
* <span data-ttu-id="e220a-174">Eles não podem ser membros estáticos ou de instância de uma classe ou estrutura normal.</span><span class="sxs-lookup"><span data-stu-id="e220a-174">They cannot be static or instance members of a class or normal struct.</span></span>
* <span data-ttu-id="e220a-175">Eles não podem ser capturados`async` por qualquer construção de fechamento (métodos ou expressões lambda).</span><span class="sxs-lookup"><span data-stu-id="e220a-175">They cannot be captured by any closure construct (`async` methods or lambda expressions).</span></span>
* <span data-ttu-id="e220a-176">Eles não podem ser usados como parâmetro genérico.</span><span class="sxs-lookup"><span data-stu-id="e220a-176">They cannot be used as a generic parameter.</span></span>

<span data-ttu-id="e220a-177">Este último ponto é crucial para a programação `|>` no estilo de pipeline F#, assim como uma função genérica que parametriza seus tipos de entrada.</span><span class="sxs-lookup"><span data-stu-id="e220a-177">This last point is crucial for F# pipeline-style programming, as `|>` is a generic function that parameterizes its input types.</span></span> <span data-ttu-id="e220a-178">Essa restrição pode `|>` ser relaxada no futuro, pois é inline e não faz nenhuma chamada para funções genéricas não-inlineadas em seu corpo.</span><span class="sxs-lookup"><span data-stu-id="e220a-178">This restriction may be relaxed for `|>` in the future, as it is inline and does not make any calls to non-inlined generic functions in its body.</span></span>

<span data-ttu-id="e220a-179">Embora essas regras restrinjam fortemente o uso, eles o fazem para cumprir a promessa de computação de alto desempenho de forma segura.</span><span class="sxs-lookup"><span data-stu-id="e220a-179">Although these rules strongly restrict usage, they do so to fulfill the promise of high-performance computing in a safe manner.</span></span>

## <a name="byref-returns"></a><span data-ttu-id="e220a-180">Byref retorna</span><span class="sxs-lookup"><span data-stu-id="e220a-180">Byref returns</span></span>

<span data-ttu-id="e220a-181">Byref retorna de funções F# ou membros podem ser produzidos e consumidos.</span><span class="sxs-lookup"><span data-stu-id="e220a-181">Byref returns from F# functions or members can be produced and consumed.</span></span> <span data-ttu-id="e220a-182">Ao consumir `byref`um método de retorno, o valor é implicitamente desreferenciado.</span><span class="sxs-lookup"><span data-stu-id="e220a-182">When consuming a `byref`-returning method, the value is implicitly dereferenced.</span></span> <span data-ttu-id="e220a-183">Por exemplo: </span><span class="sxs-lookup"><span data-stu-id="e220a-183">For example:</span></span>

```fsharp
let squareAndPrint (data : byref<int>) =
    let squared = data*data    // data is implicitly dereferenced
    printfn "%d" squared
```

<span data-ttu-id="e220a-184">Para devolver um byref de valor, a variável que contém o valor deve viver mais do que o escopo atual.</span><span class="sxs-lookup"><span data-stu-id="e220a-184">To return a value byref, the variable that contains the value must live longer than the current scope.</span></span>
<span data-ttu-id="e220a-185">Além disso, para retornar `&value` byref, use (onde o valor é uma variável que vive mais do que o escopo atual).</span><span class="sxs-lookup"><span data-stu-id="e220a-185">Also, to return byref, use `&value` (where value is a variable that lives longer than the current scope).</span></span>

```fsharp
let mutable sum = 0
let safeSum (bytes: Span<byte>) =
    for i in 0 .. bytes.Length - 1 do
        sum <- sum + int bytes.[i]
    &sum  // sum lives longer than the scope of this function.
```

<span data-ttu-id="e220a-186">Para evitar a dereferência implícita, como passar uma referência `&x` através `x` de várias chamadas acorrentadas, use (onde está o valor).</span><span class="sxs-lookup"><span data-stu-id="e220a-186">To avoid the implicit dereference, such as passing a reference through multiple chained calls, use `&x` (where `x` is the value).</span></span>

<span data-ttu-id="e220a-187">Você também pode atribuir diretamente `byref`a um retorno .</span><span class="sxs-lookup"><span data-stu-id="e220a-187">You can also directly assign to a return `byref`.</span></span> <span data-ttu-id="e220a-188">Considere o seguinte programa (altamente imperativo):</span><span class="sxs-lookup"><span data-stu-id="e220a-188">Consider the following (highly imperative) program:</span></span>

```fsharp
type C() =
    let mutable nums = [| 1; 3; 7; 15; 31; 63; 127; 255; 511; 1023 |]

    override _.ToString() = String.Join(' ', nums)

    member _.FindLargestSmallerThan(target: int) =
        let mutable ctr = nums.Length - 1

        while ctr > 0 && nums.[ctr] >= target do ctr <- ctr - 1

        if ctr > 0 then &nums.[ctr] else &nums.[0]

[<EntryPoint>]
let main argv =
    let c = C()
    printfn "Original sequence: %s" (c.ToString())

    let v = &c.FindLargestSmallerThan 16

    v <- v*2 // Directly assign to the byref return

    printfn "New sequence:      %s" (c.ToString())

    0 // return an integer exit code
```

<span data-ttu-id="e220a-189">Esta é a saída:</span><span class="sxs-lookup"><span data-stu-id="e220a-189">This is the output:</span></span>

```console
Original sequence: 1 3 7 15 31 63 127 255 511 1023
New sequence:      1 3 7 30 31 63 127 255 511 1023
```

## <a name="scoping-for-byrefs"></a><span data-ttu-id="e220a-190">Escopo para byrefs</span><span class="sxs-lookup"><span data-stu-id="e220a-190">Scoping for byrefs</span></span>

<span data-ttu-id="e220a-191">Um `let`valor vinculado não pode ter sua referência excedendo o escopo em que foi definido.</span><span class="sxs-lookup"><span data-stu-id="e220a-191">A `let`-bound value cannot have its reference exceed the scope in which it was defined.</span></span> <span data-ttu-id="e220a-192">Por exemplo, o seguinte é proibido:</span><span class="sxs-lookup"><span data-stu-id="e220a-192">For example, the following is disallowed:</span></span>

```fsharp
let test2 () =
    let x = 12
    &x // Error: 'x' exceeds its defined scope!

let test () =
    let x =
        let y = 1
        &y // Error: `y` exceeds its defined scope!
    ()
```

<span data-ttu-id="e220a-193">Isso evita que você tenha resultados diferentes dependendo se você compila com otimizações ou não.</span><span class="sxs-lookup"><span data-stu-id="e220a-193">This prevents you from getting different results depending on if you compile with optimizations or not.</span></span>
