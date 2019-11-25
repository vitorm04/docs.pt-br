---
title: Byrefs
description: Saiba mais sobre tipos ByRef e ByRef no F#, que são usados para programação de baixo nível.
ms.date: 11/04/2019
ms.openlocfilehash: 2c46cea2329b6817dd753e67c6702fb163ce2193
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976822"
---
# <a name="byrefs"></a><span data-ttu-id="d6e7c-103">Byrefs</span><span class="sxs-lookup"><span data-stu-id="d6e7c-103">Byrefs</span></span>

<span data-ttu-id="d6e7c-104">F#o tem duas áreas principais de recursos que lidam com o espaço de programação de baixo nível:</span><span class="sxs-lookup"><span data-stu-id="d6e7c-104">F# has two major feature areas that deal in the space of low-level programming:</span></span>

* <span data-ttu-id="d6e7c-105">Os `byref`/`inref`/tipos de `outref`, que são ponteiros gerenciados.</span><span class="sxs-lookup"><span data-stu-id="d6e7c-105">The `byref`/`inref`/`outref` types, which are a managed pointers.</span></span> <span data-ttu-id="d6e7c-106">Eles têm restrições de uso para que você não possa compilar um programa inválido em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="d6e7c-106">They have restrictions on usage so that you cannot compile a program that is invalid at runtime.</span></span>
* <span data-ttu-id="d6e7c-107">Um struct `byref`como, que é uma [estrutura](structures.md) que tem semântica semelhante e as mesmas restrições de tempo de compilação que `byref<'T>`.</span><span class="sxs-lookup"><span data-stu-id="d6e7c-107">A `byref`-like struct, which is a [structure](structures.md) that has similar semantics and the same compile-time restrictions as `byref<'T>`.</span></span> <span data-ttu-id="d6e7c-108">Um exemplo é <xref:System.Span%601>.</span><span class="sxs-lookup"><span data-stu-id="d6e7c-108">One example is <xref:System.Span%601>.</span></span>

## <a name="syntax"></a><span data-ttu-id="d6e7c-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d6e7c-109">Syntax</span></span>

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

## <a name="byref-inref-and-outref"></a><span data-ttu-id="d6e7c-110">ByRef, inref e outref</span><span class="sxs-lookup"><span data-stu-id="d6e7c-110">Byref, inref, and outref</span></span>

<span data-ttu-id="d6e7c-111">Há três formas de `byref`:</span><span class="sxs-lookup"><span data-stu-id="d6e7c-111">There are three forms of `byref`:</span></span>

* <span data-ttu-id="d6e7c-112">`inref<'T>`, um ponteiro gerenciado para ler o valor subjacente.</span><span class="sxs-lookup"><span data-stu-id="d6e7c-112">`inref<'T>`, a managed pointer for reading the underlying value.</span></span>
* <span data-ttu-id="d6e7c-113">`outref<'T>`, um ponteiro gerenciado para gravar no valor subjacente.</span><span class="sxs-lookup"><span data-stu-id="d6e7c-113">`outref<'T>`, a managed pointer for writing to the underlying value.</span></span>
* <span data-ttu-id="d6e7c-114">`byref<'T>`, um ponteiro gerenciado para ler e gravar o valor subjacente.</span><span class="sxs-lookup"><span data-stu-id="d6e7c-114">`byref<'T>`, a managed pointer for reading and writing the underlying value.</span></span>

<span data-ttu-id="d6e7c-115">Um `byref<'T>` pode ser passado onde um `inref<'T>` é esperado.</span><span class="sxs-lookup"><span data-stu-id="d6e7c-115">A `byref<'T>` can be passed where an `inref<'T>` is expected.</span></span> <span data-ttu-id="d6e7c-116">Da mesma forma, um `byref<'T>` pode ser passado onde um `outref<'T>` é esperado.</span><span class="sxs-lookup"><span data-stu-id="d6e7c-116">Similarly, a `byref<'T>` can be passed where an `outref<'T>` is expected.</span></span>

## <a name="using-byrefs"></a><span data-ttu-id="d6e7c-117">Usando byrefs</span><span class="sxs-lookup"><span data-stu-id="d6e7c-117">Using byrefs</span></span>

<span data-ttu-id="d6e7c-118">Para usar um `inref<'T>`, você precisa obter um valor de ponteiro com `&`:</span><span class="sxs-lookup"><span data-stu-id="d6e7c-118">To use a `inref<'T>`, you need to get a pointer value with `&`:</span></span>

```fsharp
open System

let f (dt: inref<DateTime>) =
    printfn "Now: %s" (dt.ToString())

let usage =
    let dt = DateTime.Now
    f &dt // Pass a pointer to 'dt'
```

<span data-ttu-id="d6e7c-119">Para gravar no ponteiro usando um `outref<'T>` ou `byref<'T>`, você também deve fazer com que o valor para o qual você obtém um ponteiro `mutable`.</span><span class="sxs-lookup"><span data-stu-id="d6e7c-119">To write to the pointer by using an `outref<'T>` or `byref<'T>`, you must also make the value you grab a pointer to `mutable`.</span></span>

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

<span data-ttu-id="d6e7c-120">Se você estiver apenas escrevendo o ponteiro em vez de lê-lo, considere o uso de `outref<'T>` em vez de `byref<'T>`.</span><span class="sxs-lookup"><span data-stu-id="d6e7c-120">If you are only writing the pointer instead of reading it, consider using `outref<'T>` instead of `byref<'T>`.</span></span>

### <a name="inref-semantics"></a><span data-ttu-id="d6e7c-121">Semântica Inref</span><span class="sxs-lookup"><span data-stu-id="d6e7c-121">Inref semantics</span></span>

<span data-ttu-id="d6e7c-122">Considere o código a seguir:</span><span class="sxs-lookup"><span data-stu-id="d6e7c-122">Consider the following code:</span></span>

```fsharp
let f (x: inref<SomeStruct>) = x.SomeField
```

<span data-ttu-id="d6e7c-123">Semanticamente, isso significa o seguinte:</span><span class="sxs-lookup"><span data-stu-id="d6e7c-123">Semantically, this means the following:</span></span>

* <span data-ttu-id="d6e7c-124">O detentor do ponteiro de `x` só pode usá-lo para ler o valor.</span><span class="sxs-lookup"><span data-stu-id="d6e7c-124">The holder of the `x` pointer may only use it to read the value.</span></span>
* <span data-ttu-id="d6e7c-125">Qualquer ponteiro adquirido para `struct` campos aninhados em `SomeStruct` recebe `inref<_>`de tipo.</span><span class="sxs-lookup"><span data-stu-id="d6e7c-125">Any pointer acquired to `struct` fields nested within `SomeStruct` are given type `inref<_>`.</span></span>

<span data-ttu-id="d6e7c-126">O seguinte também é verdadeiro:</span><span class="sxs-lookup"><span data-stu-id="d6e7c-126">The following is also true:</span></span>

* <span data-ttu-id="d6e7c-127">Não há implicação de que outros threads ou aliases não tenham acesso de gravação para `x`.</span><span class="sxs-lookup"><span data-stu-id="d6e7c-127">There is no implication that other threads or aliases do not have write access to `x`.</span></span>
* <span data-ttu-id="d6e7c-128">Não há implicação de que `SomeStruct` seja imutável em virtude de `x` ser uma `inref`.</span><span class="sxs-lookup"><span data-stu-id="d6e7c-128">There is no implication that `SomeStruct` is immutable by virtue of `x` being an `inref`.</span></span>

<span data-ttu-id="d6e7c-129">No entanto F# , para tipos de valor que **são** imutáveis, o ponteiro de `this` é inferido para ser um `inref`.</span><span class="sxs-lookup"><span data-stu-id="d6e7c-129">However, for F# value types that **are** immutable, the `this` pointer is inferred to be an `inref`.</span></span>

<span data-ttu-id="d6e7c-130">Todas essas regras em conjunto significam que o detentor de um ponteiro de `inref` pode não modificar o conteúdo imediato da memória que está sendo apontada.</span><span class="sxs-lookup"><span data-stu-id="d6e7c-130">All of these rules together mean that the holder of an `inref` pointer may not modify the immediate contents of the memory being pointed to.</span></span>

### <a name="outref-semantics"></a><span data-ttu-id="d6e7c-131">Semântica Outref</span><span class="sxs-lookup"><span data-stu-id="d6e7c-131">Outref semantics</span></span>

<span data-ttu-id="d6e7c-132">A finalidade de `outref<'T>` é indicar que o ponteiro só deve ser lido de.</span><span class="sxs-lookup"><span data-stu-id="d6e7c-132">The purpose of `outref<'T>` is to indicate that the pointer should only be read from.</span></span> <span data-ttu-id="d6e7c-133">Inesperadamente, `outref<'T>` permite ler o valor subjacente, apesar do seu nome.</span><span class="sxs-lookup"><span data-stu-id="d6e7c-133">Unexpectedly, `outref<'T>` permits reading the underlying value despite its name.</span></span> <span data-ttu-id="d6e7c-134">Isso é para fins de compatibilidade.</span><span class="sxs-lookup"><span data-stu-id="d6e7c-134">This is for compatibility purposes.</span></span> <span data-ttu-id="d6e7c-135">Semanticamente, `outref<'T>` não é diferente de `byref<'T>`.</span><span class="sxs-lookup"><span data-stu-id="d6e7c-135">Semantically, `outref<'T>` is no different than `byref<'T>`.</span></span>

### <a name="interop-with-c"></a><span data-ttu-id="d6e7c-136">Interoperabilidade com C\#</span><span class="sxs-lookup"><span data-stu-id="d6e7c-136">Interop with C\#</span></span>

<span data-ttu-id="d6e7c-137">C#dá suporte às palavras-chave `in ref` e `out ref`, além de `ref` retorna.</span><span class="sxs-lookup"><span data-stu-id="d6e7c-137">C# supports the `in ref` and `out ref` keywords, in addition to `ref` returns.</span></span> <span data-ttu-id="d6e7c-138">A tabela a seguir mostra F# como o interpreta C# o que emite:</span><span class="sxs-lookup"><span data-stu-id="d6e7c-138">The following table shows how F# interprets what C# emits:</span></span>

|<span data-ttu-id="d6e7c-139">C#construir</span><span class="sxs-lookup"><span data-stu-id="d6e7c-139">C# construct</span></span>|<span data-ttu-id="d6e7c-140">F#infere</span><span class="sxs-lookup"><span data-stu-id="d6e7c-140">F# infers</span></span>|
|------------|---------|
|<span data-ttu-id="d6e7c-141">`ref` valor de retorno</span><span class="sxs-lookup"><span data-stu-id="d6e7c-141">`ref` return value</span></span>|`outref<'T>`|
|<span data-ttu-id="d6e7c-142">`ref readonly` valor de retorno</span><span class="sxs-lookup"><span data-stu-id="d6e7c-142">`ref readonly` return value</span></span>|`inref<'T>`|
|<span data-ttu-id="d6e7c-143">Parâmetro `in ref`</span><span class="sxs-lookup"><span data-stu-id="d6e7c-143">`in ref` parameter</span></span>|`inref<'T>`|
|<span data-ttu-id="d6e7c-144">Parâmetro `out ref`</span><span class="sxs-lookup"><span data-stu-id="d6e7c-144">`out ref` parameter</span></span>|`outref<'T>`|

<span data-ttu-id="d6e7c-145">A tabela a seguir mostra F# o que são emitidos:</span><span class="sxs-lookup"><span data-stu-id="d6e7c-145">The following table shows what F# emits:</span></span>

|<span data-ttu-id="d6e7c-146">F#construir</span><span class="sxs-lookup"><span data-stu-id="d6e7c-146">F# construct</span></span>|<span data-ttu-id="d6e7c-147">Construção emitida</span><span class="sxs-lookup"><span data-stu-id="d6e7c-147">Emitted construct</span></span>|
|------------|-----------------|
|<span data-ttu-id="d6e7c-148">`inref<'T>` argumento</span><span class="sxs-lookup"><span data-stu-id="d6e7c-148">`inref<'T>` argument</span></span>|<span data-ttu-id="d6e7c-149">atributo de `[In]` no argumento</span><span class="sxs-lookup"><span data-stu-id="d6e7c-149">`[In]` attribute on argument</span></span>|
|<span data-ttu-id="d6e7c-150">`inref<'T>` retornar</span><span class="sxs-lookup"><span data-stu-id="d6e7c-150">`inref<'T>` return</span></span>|<span data-ttu-id="d6e7c-151">`modreq` atributo no valor</span><span class="sxs-lookup"><span data-stu-id="d6e7c-151">`modreq` attribute on value</span></span>|
|<span data-ttu-id="d6e7c-152">`inref<'T>` no slot abstrato ou na implementação</span><span class="sxs-lookup"><span data-stu-id="d6e7c-152">`inref<'T>` in abstract slot or implementation</span></span>|<span data-ttu-id="d6e7c-153">`modreq` no argumento ou retorno</span><span class="sxs-lookup"><span data-stu-id="d6e7c-153">`modreq` on argument or return</span></span>|
|<span data-ttu-id="d6e7c-154">`outref<'T>` argumento</span><span class="sxs-lookup"><span data-stu-id="d6e7c-154">`outref<'T>` argument</span></span>|<span data-ttu-id="d6e7c-155">atributo de `[Out]` no argumento</span><span class="sxs-lookup"><span data-stu-id="d6e7c-155">`[Out]` attribute on argument</span></span>|

### <a name="type-inference-and-overloading-rules"></a><span data-ttu-id="d6e7c-156">Inferência de tipos e regras de sobrecarga</span><span class="sxs-lookup"><span data-stu-id="d6e7c-156">Type inference and overloading rules</span></span>

<span data-ttu-id="d6e7c-157">Um tipo de `inref<'T>` é inferido pelo F# compilador nos seguintes casos:</span><span class="sxs-lookup"><span data-stu-id="d6e7c-157">An `inref<'T>` type is inferred by the F# compiler in the following cases:</span></span>

1. <span data-ttu-id="d6e7c-158">Um parâmetro .NET ou tipo de retorno que tem um atributo `IsReadOnly`.</span><span class="sxs-lookup"><span data-stu-id="d6e7c-158">A .NET parameter or return type that has an `IsReadOnly` attribute.</span></span>
2. <span data-ttu-id="d6e7c-159">O ponteiro de `this` em um tipo de struct que não tem campos mutáveis.</span><span class="sxs-lookup"><span data-stu-id="d6e7c-159">The `this` pointer on a struct type that has no mutable fields.</span></span>
3. <span data-ttu-id="d6e7c-160">O endereço de um local de memória derivado de outro ponteiro de `inref<_>`.</span><span class="sxs-lookup"><span data-stu-id="d6e7c-160">The address of a memory location derived from another `inref<_>` pointer.</span></span>

<span data-ttu-id="d6e7c-161">Quando um endereço implícito de um `inref` está sendo obtido, uma sobrecarga com um argumento do tipo `SomeType` é preferida para uma sobrecarga com um argumento do tipo `inref<SomeType>`.</span><span class="sxs-lookup"><span data-stu-id="d6e7c-161">When an implicit address of an `inref` is being taken, an overload with an argument of type `SomeType` is preferred to an overload with an argument of type `inref<SomeType>`.</span></span> <span data-ttu-id="d6e7c-162">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="d6e7c-162">For example:</span></span>

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

<span data-ttu-id="d6e7c-163">Em ambos os casos, as sobrecargas que levam `System.DateTime` são resolvidas em vez das sobrecargas que levam `inref<System.DateTime>`.</span><span class="sxs-lookup"><span data-stu-id="d6e7c-163">In both cases, the overloads taking `System.DateTime` are resolved rather than the overloads taking `inref<System.DateTime>`.</span></span>

## <a name="byref-like-structs"></a><span data-ttu-id="d6e7c-164">Estruturas do tipo ByRef</span><span class="sxs-lookup"><span data-stu-id="d6e7c-164">Byref-like structs</span></span>

<span data-ttu-id="d6e7c-165">Além do `byref`/`inref`/`outref` trio, você pode definir suas próprias estruturas que podem aderir à semântica do tipo `byref`.</span><span class="sxs-lookup"><span data-stu-id="d6e7c-165">In addition to the `byref`/`inref`/`outref` trio, you can define your own structs that can adhere to `byref`-like semantics.</span></span> <span data-ttu-id="d6e7c-166">Isso é feito com o atributo <xref:System.Runtime.CompilerServices.IsByRefLikeAttribute>:</span><span class="sxs-lookup"><span data-stu-id="d6e7c-166">This is done with the <xref:System.Runtime.CompilerServices.IsByRefLikeAttribute> attribute:</span></span>

```fsharp
open System
open System.Runtime.CompilerServices

[<IsByRefLike; Struct>]
type S(count1: Span<int>, count2: Span<int>) =
    member x.Count1 = count1
    member x.Count2 = count2
```

<span data-ttu-id="d6e7c-167">`IsByRefLike` não implica `Struct`.</span><span class="sxs-lookup"><span data-stu-id="d6e7c-167">`IsByRefLike` does not imply `Struct`.</span></span> <span data-ttu-id="d6e7c-168">Ambos devem estar presentes no tipo.</span><span class="sxs-lookup"><span data-stu-id="d6e7c-168">Both must be present on the type.</span></span>

<span data-ttu-id="d6e7c-169">Um struct "`byref`como" no F# é um tipo de valor vinculado à pilha.</span><span class="sxs-lookup"><span data-stu-id="d6e7c-169">A "`byref`-like" struct in F# is a stack-bound value type.</span></span> <span data-ttu-id="d6e7c-170">Ele nunca é alocado no heap gerenciado.</span><span class="sxs-lookup"><span data-stu-id="d6e7c-170">It is never allocated on the managed heap.</span></span> <span data-ttu-id="d6e7c-171">Uma estrutura semelhante a `byref`é útil para programação de alto desempenho, pois é imposta com o conjunto de verificações fortes sobre o tempo de vida e a não captura.</span><span class="sxs-lookup"><span data-stu-id="d6e7c-171">A `byref`-like struct is useful for high-performance programming, as it is enforced with set of strong checks about lifetime and non-capture.</span></span> <span data-ttu-id="d6e7c-172">As regras são:</span><span class="sxs-lookup"><span data-stu-id="d6e7c-172">The rules are:</span></span>

* <span data-ttu-id="d6e7c-173">Eles podem ser usados como parâmetros de função, parâmetros de método, variáveis locais, método retorna.</span><span class="sxs-lookup"><span data-stu-id="d6e7c-173">They can be used as function parameters, method parameters, local variables, method returns.</span></span>
* <span data-ttu-id="d6e7c-174">Eles não podem ser membros estáticos ou de instância de uma classe ou estrutura normal.</span><span class="sxs-lookup"><span data-stu-id="d6e7c-174">They cannot be static or instance members of a class or normal struct.</span></span>
* <span data-ttu-id="d6e7c-175">Eles não podem ser capturados por nenhuma construção de fechamento (`async` métodos ou expressões lambda).</span><span class="sxs-lookup"><span data-stu-id="d6e7c-175">They cannot be captured by any closure construct (`async` methods or lambda expressions).</span></span>
* <span data-ttu-id="d6e7c-176">Eles não podem ser usados como um parâmetro genérico.</span><span class="sxs-lookup"><span data-stu-id="d6e7c-176">They cannot be used as a generic parameter.</span></span>

<span data-ttu-id="d6e7c-177">Esse último ponto é crucial para F# a programação em estilo de pipeline, pois `|>` é uma função genérica que parametriza seus tipos de entrada.</span><span class="sxs-lookup"><span data-stu-id="d6e7c-177">This last point is crucial for F# pipeline-style programming, as `|>` is a generic function that parameterizes its input types.</span></span> <span data-ttu-id="d6e7c-178">Essa restrição pode ser reduzida para `|>` no futuro, pois ela está embutida e não faz nenhuma chamada para funções genéricas não embutidas em seu corpo.</span><span class="sxs-lookup"><span data-stu-id="d6e7c-178">This restriction may be relaxed for `|>` in the future, as it is inline and does not make any calls to non-inlined generic functions in its body.</span></span>

<span data-ttu-id="d6e7c-179">Embora essas regras restrinjam muito o uso, elas fazem isso para atender à promessa de computação de alto desempenho de maneira segura.</span><span class="sxs-lookup"><span data-stu-id="d6e7c-179">Although these rules very strongly restrict usage, they do so to fulfill the promise of high-performance computing in a safe manner.</span></span>

## <a name="byref-returns"></a><span data-ttu-id="d6e7c-180">Retornos de ByRef</span><span class="sxs-lookup"><span data-stu-id="d6e7c-180">Byref returns</span></span>

<span data-ttu-id="d6e7c-181">O ByRef retorna F# de funções ou membros pode ser produzido e consumido.</span><span class="sxs-lookup"><span data-stu-id="d6e7c-181">Byref returns from F# functions or members can be produced and consumed.</span></span> <span data-ttu-id="d6e7c-182">Ao consumir um método de retorno de `byref`, o valor é implicitamente desreferenciado.</span><span class="sxs-lookup"><span data-stu-id="d6e7c-182">When consuming a `byref`-returning method, the value is implicitly dereferenced.</span></span> <span data-ttu-id="d6e7c-183">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="d6e7c-183">For example:</span></span>

```fsharp
let safeSum(bytes: Span<byte>) =
    let mutable sum = 0
    for i in 0 .. bytes.Length - 1 do
        sum <- sum + int bytes.[i]
    sum

let sum = safeSum(mySpanOfBytes)
printfn "%d" sum // 'sum' is of type 'int'
```

<span data-ttu-id="d6e7c-184">Para evitar a desreferência implícita, como passar uma referência por meio de várias chamadas encadeadas, use `&x` (em que `x` é o valor).</span><span class="sxs-lookup"><span data-stu-id="d6e7c-184">To avoid the implicit dereference, such as passing a reference through multiple chained calls, use `&x` (where `x` is the value).</span></span>

<span data-ttu-id="d6e7c-185">Você também pode atribuir diretamente a um `byref`de retorno.</span><span class="sxs-lookup"><span data-stu-id="d6e7c-185">You can also directly assign to a return `byref`.</span></span> <span data-ttu-id="d6e7c-186">Considere o seguinte programa (altamente imperativo):</span><span class="sxs-lookup"><span data-stu-id="d6e7c-186">Consider the following (highly imperative) program:</span></span>

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

<span data-ttu-id="d6e7c-187">Esta é a saída:</span><span class="sxs-lookup"><span data-stu-id="d6e7c-187">This is the output:</span></span>

```console
Original sequence: 1 3 7 15 31 63 127 255 511 1023
New sequence:      1 3 7 30 31 63 127 255 511 1023
```

## <a name="scoping-for-byrefs"></a><span data-ttu-id="d6e7c-188">Escopo para byrefs</span><span class="sxs-lookup"><span data-stu-id="d6e7c-188">Scoping for byrefs</span></span>

<span data-ttu-id="d6e7c-189">Um valor associado a `let`não pode ter sua referência exceder o escopo no qual ele foi definido.</span><span class="sxs-lookup"><span data-stu-id="d6e7c-189">A `let`-bound value cannot have its reference exceed the scope in which it was defined.</span></span> <span data-ttu-id="d6e7c-190">Por exemplo, o seguinte não é permitido:</span><span class="sxs-lookup"><span data-stu-id="d6e7c-190">For example, the following is disallowed:</span></span>

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

<span data-ttu-id="d6e7c-191">Isso impede que você obtenha resultados diferentes dependendo de se você compilar com otimizações ativadas ou desativadas.</span><span class="sxs-lookup"><span data-stu-id="d6e7c-191">This prevents you from getting different results depending on if you compile with optimizations on or off.</span></span>
