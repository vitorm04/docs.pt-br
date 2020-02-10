---
title: Byrefs
description: Saiba mais sobre tipos ByRef e ByRef no F#, que são usados para programação de baixo nível.
ms.date: 11/04/2019
ms.openlocfilehash: 2d98d325dc4ad26548fb2cc6aa5b872e152ee0a8
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77092782"
---
# <a name="byrefs"></a><span data-ttu-id="2b3f2-103">Byrefs</span><span class="sxs-lookup"><span data-stu-id="2b3f2-103">Byrefs</span></span>

<span data-ttu-id="2b3f2-104">F#o tem duas áreas principais de recursos que lidam com o espaço de programação de baixo nível:</span><span class="sxs-lookup"><span data-stu-id="2b3f2-104">F# has two major feature areas that deal in the space of low-level programming:</span></span>

* <span data-ttu-id="2b3f2-105">Os `byref`/`inref`/tipos de `outref`, que são ponteiros gerenciados.</span><span class="sxs-lookup"><span data-stu-id="2b3f2-105">The `byref`/`inref`/`outref` types, which are managed pointers.</span></span> <span data-ttu-id="2b3f2-106">Eles têm restrições de uso para que você não possa compilar um programa inválido em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="2b3f2-106">They have restrictions on usage so that you cannot compile a program that is invalid at run time.</span></span>
* <span data-ttu-id="2b3f2-107">Um struct `byref`como, que é uma [estrutura](structures.md) que tem semântica semelhante e as mesmas restrições de tempo de compilação que `byref<'T>`.</span><span class="sxs-lookup"><span data-stu-id="2b3f2-107">A `byref`-like struct, which is a [structure](structures.md) that has similar semantics and the same compile-time restrictions as `byref<'T>`.</span></span> <span data-ttu-id="2b3f2-108">Um exemplo é <xref:System.Span%601>.</span><span class="sxs-lookup"><span data-stu-id="2b3f2-108">One example is <xref:System.Span%601>.</span></span>

## <a name="syntax"></a><span data-ttu-id="2b3f2-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2b3f2-109">Syntax</span></span>

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

## <a name="byref-inref-and-outref"></a><span data-ttu-id="2b3f2-110">ByRef, inref e outref</span><span class="sxs-lookup"><span data-stu-id="2b3f2-110">Byref, inref, and outref</span></span>

<span data-ttu-id="2b3f2-111">Há três formas de `byref`:</span><span class="sxs-lookup"><span data-stu-id="2b3f2-111">There are three forms of `byref`:</span></span>

* <span data-ttu-id="2b3f2-112">`inref<'T>`, um ponteiro gerenciado para ler o valor subjacente.</span><span class="sxs-lookup"><span data-stu-id="2b3f2-112">`inref<'T>`, a managed pointer for reading the underlying value.</span></span>
* <span data-ttu-id="2b3f2-113">`outref<'T>`, um ponteiro gerenciado para gravar no valor subjacente.</span><span class="sxs-lookup"><span data-stu-id="2b3f2-113">`outref<'T>`, a managed pointer for writing to the underlying value.</span></span>
* <span data-ttu-id="2b3f2-114">`byref<'T>`, um ponteiro gerenciado para ler e gravar o valor subjacente.</span><span class="sxs-lookup"><span data-stu-id="2b3f2-114">`byref<'T>`, a managed pointer for reading and writing the underlying value.</span></span>

<span data-ttu-id="2b3f2-115">Um `byref<'T>` pode ser passado onde um `inref<'T>` é esperado.</span><span class="sxs-lookup"><span data-stu-id="2b3f2-115">A `byref<'T>` can be passed where an `inref<'T>` is expected.</span></span> <span data-ttu-id="2b3f2-116">Da mesma forma, um `byref<'T>` pode ser passado onde um `outref<'T>` é esperado.</span><span class="sxs-lookup"><span data-stu-id="2b3f2-116">Similarly, a `byref<'T>` can be passed where an `outref<'T>` is expected.</span></span>

## <a name="using-byrefs"></a><span data-ttu-id="2b3f2-117">Usando byrefs</span><span class="sxs-lookup"><span data-stu-id="2b3f2-117">Using byrefs</span></span>

<span data-ttu-id="2b3f2-118">Para usar um `inref<'T>`, você precisa obter um valor de ponteiro com `&`:</span><span class="sxs-lookup"><span data-stu-id="2b3f2-118">To use a `inref<'T>`, you need to get a pointer value with `&`:</span></span>

```fsharp
open System

let f (dt: inref<DateTime>) =
    printfn "Now: %s" (dt.ToString())

let usage =
    let dt = DateTime.Now
    f &dt // Pass a pointer to 'dt'
```

<span data-ttu-id="2b3f2-119">Para gravar no ponteiro usando um `outref<'T>` ou `byref<'T>`, você também deve fazer com que o valor para o qual você obtém um ponteiro `mutable`.</span><span class="sxs-lookup"><span data-stu-id="2b3f2-119">To write to the pointer by using an `outref<'T>` or `byref<'T>`, you must also make the value you grab a pointer to `mutable`.</span></span>

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

<span data-ttu-id="2b3f2-120">Se você estiver apenas escrevendo o ponteiro em vez de lê-lo, considere o uso de `outref<'T>` em vez de `byref<'T>`.</span><span class="sxs-lookup"><span data-stu-id="2b3f2-120">If you are only writing the pointer instead of reading it, consider using `outref<'T>` instead of `byref<'T>`.</span></span>

### <a name="inref-semantics"></a><span data-ttu-id="2b3f2-121">Semântica Inref</span><span class="sxs-lookup"><span data-stu-id="2b3f2-121">Inref semantics</span></span>

<span data-ttu-id="2b3f2-122">Considere o código a seguir:</span><span class="sxs-lookup"><span data-stu-id="2b3f2-122">Consider the following code:</span></span>

```fsharp
let f (x: inref<SomeStruct>) = x.SomeField
```

<span data-ttu-id="2b3f2-123">Semanticamente, isso significa o seguinte:</span><span class="sxs-lookup"><span data-stu-id="2b3f2-123">Semantically, this means the following:</span></span>

* <span data-ttu-id="2b3f2-124">O detentor do ponteiro de `x` só pode usá-lo para ler o valor.</span><span class="sxs-lookup"><span data-stu-id="2b3f2-124">The holder of the `x` pointer may only use it to read the value.</span></span>
* <span data-ttu-id="2b3f2-125">Qualquer ponteiro adquirido para `struct` campos aninhados em `SomeStruct` recebe `inref<_>`de tipo.</span><span class="sxs-lookup"><span data-stu-id="2b3f2-125">Any pointer acquired to `struct` fields nested within `SomeStruct` are given type `inref<_>`.</span></span>

<span data-ttu-id="2b3f2-126">O seguinte também é verdadeiro:</span><span class="sxs-lookup"><span data-stu-id="2b3f2-126">The following is also true:</span></span>

* <span data-ttu-id="2b3f2-127">Não há implicação de que outros threads ou aliases não tenham acesso de gravação para `x`.</span><span class="sxs-lookup"><span data-stu-id="2b3f2-127">There is no implication that other threads or aliases do not have write access to `x`.</span></span>
* <span data-ttu-id="2b3f2-128">Não há implicação de que `SomeStruct` seja imutável em virtude de `x` ser uma `inref`.</span><span class="sxs-lookup"><span data-stu-id="2b3f2-128">There is no implication that `SomeStruct` is immutable by virtue of `x` being an `inref`.</span></span>

<span data-ttu-id="2b3f2-129">No entanto F# , para tipos de valor que **são** imutáveis, o ponteiro de `this` é inferido para ser um `inref`.</span><span class="sxs-lookup"><span data-stu-id="2b3f2-129">However, for F# value types that **are** immutable, the `this` pointer is inferred to be an `inref`.</span></span>

<span data-ttu-id="2b3f2-130">Todas essas regras em conjunto significam que o detentor de um ponteiro de `inref` pode não modificar o conteúdo imediato da memória que está sendo apontada.</span><span class="sxs-lookup"><span data-stu-id="2b3f2-130">All of these rules together mean that the holder of an `inref` pointer may not modify the immediate contents of the memory being pointed to.</span></span>

### <a name="outref-semantics"></a><span data-ttu-id="2b3f2-131">Semântica Outref</span><span class="sxs-lookup"><span data-stu-id="2b3f2-131">Outref semantics</span></span>

<span data-ttu-id="2b3f2-132">A finalidade de `outref<'T>` é indicar que o ponteiro só deve ser gravado.</span><span class="sxs-lookup"><span data-stu-id="2b3f2-132">The purpose of `outref<'T>` is to indicate that the pointer should only be written to.</span></span> <span data-ttu-id="2b3f2-133">Inesperadamente, `outref<'T>` permite ler o valor subjacente, apesar do seu nome.</span><span class="sxs-lookup"><span data-stu-id="2b3f2-133">Unexpectedly, `outref<'T>` permits reading the underlying value despite its name.</span></span> <span data-ttu-id="2b3f2-134">Isso é para fins de compatibilidade.</span><span class="sxs-lookup"><span data-stu-id="2b3f2-134">This is for compatibility purposes.</span></span> <span data-ttu-id="2b3f2-135">Semanticamente, `outref<'T>` não é diferente de `byref<'T>`.</span><span class="sxs-lookup"><span data-stu-id="2b3f2-135">Semantically, `outref<'T>` is no different than `byref<'T>`.</span></span>

### <a name="interop-with-c"></a><span data-ttu-id="2b3f2-136">Interoperabilidade com C\#</span><span class="sxs-lookup"><span data-stu-id="2b3f2-136">Interop with C\#</span></span>

<span data-ttu-id="2b3f2-137">C#dá suporte às palavras-chave `in ref` e `out ref`, além de `ref` retorna.</span><span class="sxs-lookup"><span data-stu-id="2b3f2-137">C# supports the `in ref` and `out ref` keywords, in addition to `ref` returns.</span></span> <span data-ttu-id="2b3f2-138">A tabela a seguir mostra F# como o interpreta C# o que emite:</span><span class="sxs-lookup"><span data-stu-id="2b3f2-138">The following table shows how F# interprets what C# emits:</span></span>

|<span data-ttu-id="2b3f2-139">C#construir</span><span class="sxs-lookup"><span data-stu-id="2b3f2-139">C# construct</span></span>|<span data-ttu-id="2b3f2-140">F#infere</span><span class="sxs-lookup"><span data-stu-id="2b3f2-140">F# infers</span></span>|
|------------|---------|
|<span data-ttu-id="2b3f2-141">`ref` valor de retorno</span><span class="sxs-lookup"><span data-stu-id="2b3f2-141">`ref` return value</span></span>|`outref<'T>`|
|<span data-ttu-id="2b3f2-142">`ref readonly` valor de retorno</span><span class="sxs-lookup"><span data-stu-id="2b3f2-142">`ref readonly` return value</span></span>|`inref<'T>`|
|<span data-ttu-id="2b3f2-143">Parâmetro `in ref`</span><span class="sxs-lookup"><span data-stu-id="2b3f2-143">`in ref` parameter</span></span>|`inref<'T>`|
|<span data-ttu-id="2b3f2-144">Parâmetro `out ref`</span><span class="sxs-lookup"><span data-stu-id="2b3f2-144">`out ref` parameter</span></span>|`outref<'T>`|

<span data-ttu-id="2b3f2-145">A tabela a seguir mostra F# o que são emitidos:</span><span class="sxs-lookup"><span data-stu-id="2b3f2-145">The following table shows what F# emits:</span></span>

|<span data-ttu-id="2b3f2-146">F#construir</span><span class="sxs-lookup"><span data-stu-id="2b3f2-146">F# construct</span></span>|<span data-ttu-id="2b3f2-147">Construção emitida</span><span class="sxs-lookup"><span data-stu-id="2b3f2-147">Emitted construct</span></span>|
|------------|-----------------|
|<span data-ttu-id="2b3f2-148">Argumento `inref<'T>`</span><span class="sxs-lookup"><span data-stu-id="2b3f2-148">`inref<'T>` argument</span></span>|<span data-ttu-id="2b3f2-149">atributo de `[In]` no argumento</span><span class="sxs-lookup"><span data-stu-id="2b3f2-149">`[In]` attribute on argument</span></span>|
|<span data-ttu-id="2b3f2-150">`inref<'T>` retornar</span><span class="sxs-lookup"><span data-stu-id="2b3f2-150">`inref<'T>` return</span></span>|<span data-ttu-id="2b3f2-151">`modreq` atributo no valor</span><span class="sxs-lookup"><span data-stu-id="2b3f2-151">`modreq` attribute on value</span></span>|
|<span data-ttu-id="2b3f2-152">`inref<'T>` no slot abstrato ou na implementação</span><span class="sxs-lookup"><span data-stu-id="2b3f2-152">`inref<'T>` in abstract slot or implementation</span></span>|<span data-ttu-id="2b3f2-153">`modreq` no argumento ou retorno</span><span class="sxs-lookup"><span data-stu-id="2b3f2-153">`modreq` on argument or return</span></span>|
|<span data-ttu-id="2b3f2-154">Argumento `outref<'T>`</span><span class="sxs-lookup"><span data-stu-id="2b3f2-154">`outref<'T>` argument</span></span>|<span data-ttu-id="2b3f2-155">atributo de `[Out]` no argumento</span><span class="sxs-lookup"><span data-stu-id="2b3f2-155">`[Out]` attribute on argument</span></span>|

### <a name="type-inference-and-overloading-rules"></a><span data-ttu-id="2b3f2-156">Inferência de tipos e regras de sobrecarga</span><span class="sxs-lookup"><span data-stu-id="2b3f2-156">Type inference and overloading rules</span></span>

<span data-ttu-id="2b3f2-157">Um tipo de `inref<'T>` é inferido pelo F# compilador nos seguintes casos:</span><span class="sxs-lookup"><span data-stu-id="2b3f2-157">An `inref<'T>` type is inferred by the F# compiler in the following cases:</span></span>

1. <span data-ttu-id="2b3f2-158">Um parâmetro .NET ou tipo de retorno que tem um atributo `IsReadOnly`.</span><span class="sxs-lookup"><span data-stu-id="2b3f2-158">A .NET parameter or return type that has an `IsReadOnly` attribute.</span></span>
2. <span data-ttu-id="2b3f2-159">O ponteiro de `this` em um tipo de struct que não tem campos mutáveis.</span><span class="sxs-lookup"><span data-stu-id="2b3f2-159">The `this` pointer on a struct type that has no mutable fields.</span></span>
3. <span data-ttu-id="2b3f2-160">O endereço de um local de memória derivado de outro ponteiro de `inref<_>`.</span><span class="sxs-lookup"><span data-stu-id="2b3f2-160">The address of a memory location derived from another `inref<_>` pointer.</span></span>

<span data-ttu-id="2b3f2-161">Quando um endereço implícito de um `inref` está sendo obtido, uma sobrecarga com um argumento do tipo `SomeType` é preferida para uma sobrecarga com um argumento do tipo `inref<SomeType>`.</span><span class="sxs-lookup"><span data-stu-id="2b3f2-161">When an implicit address of an `inref` is being taken, an overload with an argument of type `SomeType` is preferred to an overload with an argument of type `inref<SomeType>`.</span></span> <span data-ttu-id="2b3f2-162">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="2b3f2-162">For example:</span></span>

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

<span data-ttu-id="2b3f2-163">Em ambos os casos, as sobrecargas que levam `System.DateTime` são resolvidas em vez das sobrecargas que levam `inref<System.DateTime>`.</span><span class="sxs-lookup"><span data-stu-id="2b3f2-163">In both cases, the overloads taking `System.DateTime` are resolved rather than the overloads taking `inref<System.DateTime>`.</span></span>

## <a name="byref-like-structs"></a><span data-ttu-id="2b3f2-164">Estruturas do tipo ByRef</span><span class="sxs-lookup"><span data-stu-id="2b3f2-164">Byref-like structs</span></span>

<span data-ttu-id="2b3f2-165">Além do `byref`/`inref`/`outref` trio, você pode definir suas próprias estruturas que podem aderir à semântica do tipo `byref`.</span><span class="sxs-lookup"><span data-stu-id="2b3f2-165">In addition to the `byref`/`inref`/`outref` trio, you can define your own structs that can adhere to `byref`-like semantics.</span></span> <span data-ttu-id="2b3f2-166">Isso é feito com o atributo <xref:System.Runtime.CompilerServices.IsByRefLikeAttribute>:</span><span class="sxs-lookup"><span data-stu-id="2b3f2-166">This is done with the <xref:System.Runtime.CompilerServices.IsByRefLikeAttribute> attribute:</span></span>

```fsharp
open System
open System.Runtime.CompilerServices

[<IsByRefLike; Struct>]
type S(count1: Span<int>, count2: Span<int>) =
    member x.Count1 = count1
    member x.Count2 = count2
```

<span data-ttu-id="2b3f2-167">`IsByRefLike` não implica `Struct`.</span><span class="sxs-lookup"><span data-stu-id="2b3f2-167">`IsByRefLike` does not imply `Struct`.</span></span> <span data-ttu-id="2b3f2-168">Ambos devem estar presentes no tipo.</span><span class="sxs-lookup"><span data-stu-id="2b3f2-168">Both must be present on the type.</span></span>

<span data-ttu-id="2b3f2-169">Um struct "`byref`como" no F# é um tipo de valor vinculado à pilha.</span><span class="sxs-lookup"><span data-stu-id="2b3f2-169">A "`byref`-like" struct in F# is a stack-bound value type.</span></span> <span data-ttu-id="2b3f2-170">Ele nunca é alocado no heap gerenciado.</span><span class="sxs-lookup"><span data-stu-id="2b3f2-170">It is never allocated on the managed heap.</span></span> <span data-ttu-id="2b3f2-171">Uma estrutura semelhante a `byref`é útil para programação de alto desempenho, pois é imposta com o conjunto de verificações fortes sobre o tempo de vida e a não captura.</span><span class="sxs-lookup"><span data-stu-id="2b3f2-171">A `byref`-like struct is useful for high-performance programming, as it is enforced with set of strong checks about lifetime and non-capture.</span></span> <span data-ttu-id="2b3f2-172">As regras são:</span><span class="sxs-lookup"><span data-stu-id="2b3f2-172">The rules are:</span></span>

* <span data-ttu-id="2b3f2-173">Eles podem ser usados como parâmetros de função, parâmetros de método, variáveis locais, método retorna.</span><span class="sxs-lookup"><span data-stu-id="2b3f2-173">They can be used as function parameters, method parameters, local variables, method returns.</span></span>
* <span data-ttu-id="2b3f2-174">Eles não podem ser membros estáticos ou de instância de uma classe ou estrutura normal.</span><span class="sxs-lookup"><span data-stu-id="2b3f2-174">They cannot be static or instance members of a class or normal struct.</span></span>
* <span data-ttu-id="2b3f2-175">Eles não podem ser capturados por nenhuma construção de fechamento (`async` métodos ou expressões lambda).</span><span class="sxs-lookup"><span data-stu-id="2b3f2-175">They cannot be captured by any closure construct (`async` methods or lambda expressions).</span></span>
* <span data-ttu-id="2b3f2-176">Eles não podem ser usados como um parâmetro genérico.</span><span class="sxs-lookup"><span data-stu-id="2b3f2-176">They cannot be used as a generic parameter.</span></span>

<span data-ttu-id="2b3f2-177">Esse último ponto é crucial para F# a programação em estilo de pipeline, pois `|>` é uma função genérica que parametriza seus tipos de entrada.</span><span class="sxs-lookup"><span data-stu-id="2b3f2-177">This last point is crucial for F# pipeline-style programming, as `|>` is a generic function that parameterizes its input types.</span></span> <span data-ttu-id="2b3f2-178">Essa restrição pode ser reduzida para `|>` no futuro, pois ela está embutida e não faz nenhuma chamada para funções genéricas não embutidas em seu corpo.</span><span class="sxs-lookup"><span data-stu-id="2b3f2-178">This restriction may be relaxed for `|>` in the future, as it is inline and does not make any calls to non-inlined generic functions in its body.</span></span>

<span data-ttu-id="2b3f2-179">Embora essas regras restrinjam fortemente o uso, elas fazem isso para atender à promessa de computação de alto desempenho de maneira segura.</span><span class="sxs-lookup"><span data-stu-id="2b3f2-179">Although these rules strongly restrict usage, they do so to fulfill the promise of high-performance computing in a safe manner.</span></span>

## <a name="byref-returns"></a><span data-ttu-id="2b3f2-180">Retornos de ByRef</span><span class="sxs-lookup"><span data-stu-id="2b3f2-180">Byref returns</span></span>

<span data-ttu-id="2b3f2-181">O ByRef retorna F# de funções ou membros pode ser produzido e consumido.</span><span class="sxs-lookup"><span data-stu-id="2b3f2-181">Byref returns from F# functions or members can be produced and consumed.</span></span> <span data-ttu-id="2b3f2-182">Ao consumir um método de retorno de `byref`, o valor é implicitamente desreferenciado.</span><span class="sxs-lookup"><span data-stu-id="2b3f2-182">When consuming a `byref`-returning method, the value is implicitly dereferenced.</span></span> <span data-ttu-id="2b3f2-183">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="2b3f2-183">For example:</span></span>

```fsharp
let squareAndPrint (data : byref<int>) = 
    let squared = data*data    // data is implicitly dereferenced
    printfn "%d" squared
```

<span data-ttu-id="2b3f2-184">Para retornar um valor ByRef, a variável que contém o valor deve residir mais tempo do que o escopo atual.</span><span class="sxs-lookup"><span data-stu-id="2b3f2-184">To return a value byref, the variable that contains the value must live longer than the current scope.</span></span>
<span data-ttu-id="2b3f2-185">Além disso, para retornar ByRef, use `&value` (em que value é uma variável que permanece mais longa do que o escopo atual).</span><span class="sxs-lookup"><span data-stu-id="2b3f2-185">Also, to return byref, use `&value` (where value is a variable that lives longer than the current scope).</span></span>

```fsharp
let mutable sum = 0
let safeSum (bytes: Span<byte>) =
    for i in 0 .. bytes.Length - 1 do
        sum <- sum + int bytes.[i]
    &sum  // sum lives longer than the scope of this function.
```

<span data-ttu-id="2b3f2-186">Para evitar a desreferência implícita, como passar uma referência por meio de várias chamadas encadeadas, use `&x` (em que `x` é o valor).</span><span class="sxs-lookup"><span data-stu-id="2b3f2-186">To avoid the implicit dereference, such as passing a reference through multiple chained calls, use `&x` (where `x` is the value).</span></span>

<span data-ttu-id="2b3f2-187">Você também pode atribuir diretamente a um `byref`de retorno.</span><span class="sxs-lookup"><span data-stu-id="2b3f2-187">You can also directly assign to a return `byref`.</span></span> <span data-ttu-id="2b3f2-188">Considere o seguinte programa (altamente imperativo):</span><span class="sxs-lookup"><span data-stu-id="2b3f2-188">Consider the following (highly imperative) program:</span></span>

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

<span data-ttu-id="2b3f2-189">Esta é a saída:</span><span class="sxs-lookup"><span data-stu-id="2b3f2-189">This is the output:</span></span>

```console
Original sequence: 1 3 7 15 31 63 127 255 511 1023
New sequence:      1 3 7 30 31 63 127 255 511 1023
```

## <a name="scoping-for-byrefs"></a><span data-ttu-id="2b3f2-190">Escopo para byrefs</span><span class="sxs-lookup"><span data-stu-id="2b3f2-190">Scoping for byrefs</span></span>

<span data-ttu-id="2b3f2-191">Um valor associado a `let`não pode ter sua referência exceder o escopo no qual ele foi definido.</span><span class="sxs-lookup"><span data-stu-id="2b3f2-191">A `let`-bound value cannot have its reference exceed the scope in which it was defined.</span></span> <span data-ttu-id="2b3f2-192">Por exemplo, o seguinte não é permitido:</span><span class="sxs-lookup"><span data-stu-id="2b3f2-192">For example, the following is disallowed:</span></span>

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

<span data-ttu-id="2b3f2-193">Isso impede que você obtenha resultados diferentes dependendo de se você compilar com otimizações ou não.</span><span class="sxs-lookup"><span data-stu-id="2b3f2-193">This prevents you from getting different results depending on if you compile with optimizations or not.</span></span>
