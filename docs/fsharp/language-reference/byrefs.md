---
title: 'Zkratka (F #)'
description: 'Saiba mais sobre byref e byref tipos em F #, que são usados para programação de nível baixo.'
ms.date: 09/02/2018
ms.openlocfilehash: 6131104e4325f77da84368c337f998c6b2b5309b
ms.sourcegitcommit: ba5c189bf44d44204a3e8838e59ec378a62d82f3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/12/2018
ms.locfileid: "44699640"
---
# <a name="byrefs"></a><span data-ttu-id="31cce-103">Zkratka</span><span class="sxs-lookup"><span data-stu-id="31cce-103">Byrefs</span></span>

<span data-ttu-id="31cce-104">O F # tem duas principais áreas de recurso que lidam no espaço de programação de nível baixo:</span><span class="sxs-lookup"><span data-stu-id="31cce-104">F# has two major feature areas that deal in the space of low-level programming:</span></span>

* <span data-ttu-id="31cce-105">O `byref` / `inref` / `outref` tipos, que são um ponteiros gerenciados.</span><span class="sxs-lookup"><span data-stu-id="31cce-105">The `byref`/`inref`/`outref` types, which are a managed pointers.</span></span> <span data-ttu-id="31cce-106">Eles têm restrições no uso, de modo que você não pode compilar um programa que é inválido em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="31cce-106">They have restrictions on usage so that you cannot compile a program that is invalid at runtime.</span></span>
* <span data-ttu-id="31cce-107">Um `byref`-como struct, que é um [estrutura](structures.md) que tem semântica semelhante e as mesmas restrições de tempo de compilação que `byref<'T>`.</span><span class="sxs-lookup"><span data-stu-id="31cce-107">A `byref`-like struct, which is a [structure](structures.md) that has similar semantics and the same compile-time restrictions as `byref<'T>`.</span></span> <span data-ttu-id="31cce-108">Um exemplo é <xref:System.Span%601>.</span><span class="sxs-lookup"><span data-stu-id="31cce-108">One example is <xref:System.Span%601>.</span></span>

## <a name="syntax"></a><span data-ttu-id="31cce-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="31cce-109">Syntax</span></span>

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

## <a name="byref-inref-and-outref"></a><span data-ttu-id="31cce-110">ByRef, inref e outref</span><span class="sxs-lookup"><span data-stu-id="31cce-110">Byref, inref, and outref</span></span>

<span data-ttu-id="31cce-111">Há três formas de `byref`:</span><span class="sxs-lookup"><span data-stu-id="31cce-111">There are three forms of `byref`:</span></span>

* <span data-ttu-id="31cce-112">`inref<'T>`, um ponteiro gerenciado para ler o valor subjacente.</span><span class="sxs-lookup"><span data-stu-id="31cce-112">`inref<'T>`, a managed pointer for reading the underlying value.</span></span>
* <span data-ttu-id="31cce-113">`outref<'T>`, um ponteiro gerenciado para gravar o valor subjacente.</span><span class="sxs-lookup"><span data-stu-id="31cce-113">`outref<'T>`, a managed pointer for writing to the underlying value.</span></span>
* <span data-ttu-id="31cce-114">`byref<'T>`, um ponteiro gerenciado para ler e gravar o valor subjacente.</span><span class="sxs-lookup"><span data-stu-id="31cce-114">`byref<'T>`, a managed pointer for reading and writing the underlying value.</span></span>

<span data-ttu-id="31cce-115">Um `byref<'T>` pode ser passado em que um `inref<'T>` é esperado.</span><span class="sxs-lookup"><span data-stu-id="31cce-115">A `byref<'T>` can be passed where an `inref<'T>` is expected.</span></span> <span data-ttu-id="31cce-116">Da mesma forma, uma `byref<'T>` pode ser passado em que um `outref<'T>` é esperado.</span><span class="sxs-lookup"><span data-stu-id="31cce-116">Similarly, a `byref<'T>` can be passed where an `outref<'T>` is expected.</span></span>

## <a name="using-byrefs"></a><span data-ttu-id="31cce-117">Usando zkratka</span><span class="sxs-lookup"><span data-stu-id="31cce-117">Using byrefs</span></span>

<span data-ttu-id="31cce-118">Para usar um `inref<'T>`, você precisa obter um valor de ponteiro com `&`:</span><span class="sxs-lookup"><span data-stu-id="31cce-118">To use a `inref<'T>`, you need to get a pointer value with `&`:</span></span>

```fsharp
open System

let f (dt: inref<DateTime>) =
    printfn "Now: %s" (dt.ToString())

let dt = DateTime.Now
f &dt // Pass a pointer to 'dt'
```

<span data-ttu-id="31cce-119">Para gravar o ponteiro, usando um `outref<'T>` ou `byref<'T>`, você também deve verificar o valor que você Pegue um ponteiro para `mutable`.</span><span class="sxs-lookup"><span data-stu-id="31cce-119">To write to the pointer by using an `outref<'T>` or `byref<'T>`, you must also make the value you grab a pointer to `mutable`.</span></span>

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

<span data-ttu-id="31cce-120">Se você estiver apenas escrevendo o ponteiro em vez de lê-lo, considere o uso `outref<'T>` em vez de `byref<'T>`.</span><span class="sxs-lookup"><span data-stu-id="31cce-120">If you are only writing the pointer instead of reading it, consider using `outref<'T>` instead of `byref<'T>`.</span></span>

### <a name="inref-semantics"></a><span data-ttu-id="31cce-121">Semântica de Inref</span><span class="sxs-lookup"><span data-stu-id="31cce-121">Inref semantics</span></span>

<span data-ttu-id="31cce-122">Considere o código a seguir:</span><span class="sxs-lookup"><span data-stu-id="31cce-122">Consider the following code:</span></span>

```fsharp
let f (x: inref<SomeStruct>) = s.SomeField
```

<span data-ttu-id="31cce-123">Semanticamente, isso significa que o seguinte:</span><span class="sxs-lookup"><span data-stu-id="31cce-123">Semantically, this means the following:</span></span>

* <span data-ttu-id="31cce-124">O proprietário do `x` ponteiro só pode usá-lo para ler o valor.</span><span class="sxs-lookup"><span data-stu-id="31cce-124">The holder of the `x` pointer may only use it to read the value.</span></span>
* <span data-ttu-id="31cce-125">Adquiridos, qualquer ponteiro para `struct` campos aninhados `SomeStruct` recebem o tipo `inref<_>`.</span><span class="sxs-lookup"><span data-stu-id="31cce-125">Any pointer acquired to `struct` fields nested within `SomeStruct` are given type `inref<_>`.</span></span>

<span data-ttu-id="31cce-126">O seguinte também é verdadeiro:</span><span class="sxs-lookup"><span data-stu-id="31cce-126">The following is also true:</span></span>

* <span data-ttu-id="31cce-127">Não há nenhuma implicação que outros threads ou aliases não tem acesso de gravação ao `x`.</span><span class="sxs-lookup"><span data-stu-id="31cce-127">There is no implication that other threads or aliases do not have write access to `x`.</span></span>
* <span data-ttu-id="31cce-128">Não há nenhuma implicação que `SomeStruct` é imutável em virtude da `x` sendo um `inref`.</span><span class="sxs-lookup"><span data-stu-id="31cce-128">There is no implication that `SomeStruct` is immutable by virtue of `x` being an `inref`.</span></span>

<span data-ttu-id="31cce-129">No entanto, para F # tipos de valores que **estão** imutável, o `this` ponteiro é inferido para ser um `inref`.</span><span class="sxs-lookup"><span data-stu-id="31cce-129">However, for F# value types that **are** immutable, the `this` pointer is inferred to be an `inref`.</span></span>

<span data-ttu-id="31cce-130">Todas essas regras juntas significam que o proprietário de um `inref` ponteiro não pode modificar o conteúdo imediato da memória que está sendo apontado.</span><span class="sxs-lookup"><span data-stu-id="31cce-130">All of these rules together mean that the holder of an `inref` pointer may not modify the immediate contents of the memory being pointed to.</span></span>

### <a name="outref-semantics"></a><span data-ttu-id="31cce-131">Semântica de Outref</span><span class="sxs-lookup"><span data-stu-id="31cce-131">Outref semantics</span></span>

<span data-ttu-id="31cce-132">A finalidade de `outref<'T>` é para indicar que o ponteiro só deve ser lidos do.</span><span class="sxs-lookup"><span data-stu-id="31cce-132">The purpose of `outref<'T>` is to indicate that the pointer should only be read from.</span></span> <span data-ttu-id="31cce-133">Inesperadamente, `outref<'T>` permite ler subjacente valor apesar do nome.</span><span class="sxs-lookup"><span data-stu-id="31cce-133">Unexpectedly, `outref<'T>` permits reading the underlying value despite its name.</span></span> <span data-ttu-id="31cce-134">Isso é para fins de compatibilidade.</span><span class="sxs-lookup"><span data-stu-id="31cce-134">This is for compatibility purposes.</span></span> <span data-ttu-id="31cce-135">Semanticamente, `outref<'T>` não é diferente de `byref<'T>`.</span><span class="sxs-lookup"><span data-stu-id="31cce-135">Semantically, `outref<'T>` is no different than `byref<'T>`.</span></span>

### <a name="interop-with-c"></a><span data-ttu-id="31cce-136">Interoperabilidade com c#</span><span class="sxs-lookup"><span data-stu-id="31cce-136">Interop with C#</span></span> #

<span data-ttu-id="31cce-137">C# é compatível com o `in ref` e `out ref` palavras-chave, além de `ref` retorna.</span><span class="sxs-lookup"><span data-stu-id="31cce-137">C# supports the `in ref` and `out ref` keywords, in addition to `ref` returns.</span></span> <span data-ttu-id="31cce-138">A tabela a seguir mostra como F # interpreta o que c# emite:</span><span class="sxs-lookup"><span data-stu-id="31cce-138">The following table shows how F# interprets what C# emits:</span></span>

|<span data-ttu-id="31cce-139">Construção de linguagem c#</span><span class="sxs-lookup"><span data-stu-id="31cce-139">C# construct</span></span>|<span data-ttu-id="31cce-140">F # infere</span><span class="sxs-lookup"><span data-stu-id="31cce-140">F# infers</span></span>|
|------------|---------|
|<span data-ttu-id="31cce-141">`ref` Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="31cce-141">`ref` return value</span></span>|`outref<'T>`|
|<span data-ttu-id="31cce-142">`ref readonly` Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="31cce-142">`ref readonly` return value</span></span>|`inref<'T>`|
|<span data-ttu-id="31cce-143">Parâmetro `in ref`</span><span class="sxs-lookup"><span data-stu-id="31cce-143">`in ref` parameter</span></span>|`inref<'T>`|
|<span data-ttu-id="31cce-144">Parâmetro `out ref`</span><span class="sxs-lookup"><span data-stu-id="31cce-144">`out ref` parameter</span></span>|`outref<'T>`|

<span data-ttu-id="31cce-145">A tabela a seguir mostra o que F # emite:</span><span class="sxs-lookup"><span data-stu-id="31cce-145">The following table shows what F# emits:</span></span>

|<span data-ttu-id="31cce-146">Construção F #</span><span class="sxs-lookup"><span data-stu-id="31cce-146">F# construct</span></span>|<span data-ttu-id="31cce-147">Construção emitida</span><span class="sxs-lookup"><span data-stu-id="31cce-147">Emitted construct</span></span>|
|------------|-----------------|
|<span data-ttu-id="31cce-148">`inref<'T>` argumento</span><span class="sxs-lookup"><span data-stu-id="31cce-148">`inref<'T>` argument</span></span>|<span data-ttu-id="31cce-149">`[In]` atributo no argumento</span><span class="sxs-lookup"><span data-stu-id="31cce-149">`[In]` attribute on argument</span></span>|
|<span data-ttu-id="31cce-150">`inref<'T>` Retornar</span><span class="sxs-lookup"><span data-stu-id="31cce-150">`inref<'T>` return</span></span>|<span data-ttu-id="31cce-151">`modreq` atributo de valor</span><span class="sxs-lookup"><span data-stu-id="31cce-151">`modreq` attribute on value</span></span>|
|<span data-ttu-id="31cce-152">`inref<'T>` no slot abstrata ou na implementação</span><span class="sxs-lookup"><span data-stu-id="31cce-152">`inref<'T>` in abstract slot or implementation</span></span>|<span data-ttu-id="31cce-153">`modreq` no argumento ou retorno</span><span class="sxs-lookup"><span data-stu-id="31cce-153">`modreq` on argument or return</span></span>|
|<span data-ttu-id="31cce-154">`outref<'T>` argumento</span><span class="sxs-lookup"><span data-stu-id="31cce-154">`outref<'T>` argument</span></span>|<span data-ttu-id="31cce-155">`[Out]` atributo no argumento</span><span class="sxs-lookup"><span data-stu-id="31cce-155">`[Out]` attribute on argument</span></span>|

### <a name="type-inference-and-overloading-rules"></a><span data-ttu-id="31cce-156">Inferência de tipo e a sobrecarga de regras</span><span class="sxs-lookup"><span data-stu-id="31cce-156">Type inference and overloading rules</span></span>

<span data-ttu-id="31cce-157">Um `inref<'T>` tipo é inferido pelo compilador do F # nos seguintes casos:</span><span class="sxs-lookup"><span data-stu-id="31cce-157">An `inref<'T>` type is inferred by the F# compiler in the following cases:</span></span>

1. <span data-ttu-id="31cce-158">Um tipo de parâmetro ou retornado de .NET que tem um `IsReadOnly` atributo.</span><span class="sxs-lookup"><span data-stu-id="31cce-158">A .NET parameter or return type that has an `IsReadOnly` attribute.</span></span>
2. <span data-ttu-id="31cce-159">O `this` ponteiro em um tipo de struct que não tem nenhum campo mutável.</span><span class="sxs-lookup"><span data-stu-id="31cce-159">The `this` pointer on a struct type that has no mutable fields.</span></span>
3. <span data-ttu-id="31cce-160">O endereço de um local de memória é derivado de outro `inref<_>` ponteiro.</span><span class="sxs-lookup"><span data-stu-id="31cce-160">The address of a memory location derived from another `inref<_>` pointer.</span></span>

<span data-ttu-id="31cce-161">Quando um endereço implícito de um `inref` estiver sendo feito, uma sobrecarga com um argumento do tipo `SomeType` é preferencial para uma sobrecarga com um argumento do tipo `inref<SomeType>`.</span><span class="sxs-lookup"><span data-stu-id="31cce-161">When an implicit address of an `inref` is being taken, an overload with an argument of type `SomeType` is preferred to an overload with an argument of type `inref<SomeType>`.</span></span> <span data-ttu-id="31cce-162">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="31cce-162">For example:</span></span>

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

<span data-ttu-id="31cce-163">Em ambos os casos, as sobrecargas `System.DateTime` são resolvidos em vez de sobrecargas `inref<System.DateTime>`.</span><span class="sxs-lookup"><span data-stu-id="31cce-163">In both cases, the overloads taking `System.DateTime` are resolved rather than the overloads taking `inref<System.DateTime>`.</span></span>

## <a name="byref-like-structs"></a><span data-ttu-id="31cce-164">Estruturas do tipo ByRef</span><span class="sxs-lookup"><span data-stu-id="31cce-164">Byref-like structs</span></span>

<span data-ttu-id="31cce-165">Além de `byref` / `inref` / `outref` trio, você pode definir seus próprios structs que podem aderir a `byref`-como semântica.</span><span class="sxs-lookup"><span data-stu-id="31cce-165">In addition to the `byref`/`inref`/`outref` trio, you can define your own structs that can adhere to `byref`-like semantics.</span></span> <span data-ttu-id="31cce-166">Isso é feito com o <xref:System.Runtime.CompilerServices.IsByRefLikeAttribute> atributo:</span><span class="sxs-lookup"><span data-stu-id="31cce-166">This is done with the <xref:System.Runtime.CompilerServices.IsByRefLikeAttribute> attribute:</span></span>

```fsharp
open System
open System.Runtime.CompilerServices

[<IsByRefLike; Struct>]
type S(count1: Span<int>, count2: Span<int>) =
    member x.Count1 = count1
    member x.Count2 = count2
```

<span data-ttu-id="31cce-167">`IsByRefLike` não implica `Struct`.</span><span class="sxs-lookup"><span data-stu-id="31cce-167">`IsByRefLike` does not imply `Struct`.</span></span> <span data-ttu-id="31cce-168">Ambos devem estar presentes no tipo.</span><span class="sxs-lookup"><span data-stu-id="31cce-168">Both must be present on the type.</span></span>

<span data-ttu-id="31cce-169">Um "`byref`-como" struct em F # é um tipo de valor de limite de pilha.</span><span class="sxs-lookup"><span data-stu-id="31cce-169">A "`byref`-like" struct in F# is a stack-bound value type.</span></span> <span data-ttu-id="31cce-170">Ele nunca é alocado no heap gerenciado.</span><span class="sxs-lookup"><span data-stu-id="31cce-170">It is never allocated on the managed heap.</span></span> <span data-ttu-id="31cce-171">Um `byref`-como o struct é útil para programação de alto desempenho, como ela é imposta com o conjunto de verificações forte sobre tempo de vida e não captura.</span><span class="sxs-lookup"><span data-stu-id="31cce-171">A `byref`-like struct is useful for high-performance programming, as it is enforced with set of strong checks about lifetime and non-capture.</span></span> <span data-ttu-id="31cce-172">As regras são:</span><span class="sxs-lookup"><span data-stu-id="31cce-172">The rules are:</span></span>

* <span data-ttu-id="31cce-173">Eles podem ser usados como parâmetros de função, os parâmetros de método, variáveis locais, método retorna.</span><span class="sxs-lookup"><span data-stu-id="31cce-173">They can be used as function parameters, method parameters, local variables, method returns.</span></span>
* <span data-ttu-id="31cce-174">Eles não podem ser estáticos ou membros de uma classe ou struct normal da instância.</span><span class="sxs-lookup"><span data-stu-id="31cce-174">They cannot be static or instance members of a class or normal struct.</span></span>
* <span data-ttu-id="31cce-175">Eles não podem ser capturados por qualquer construção de fechamento (`async` métodos ou expressões lambda).</span><span class="sxs-lookup"><span data-stu-id="31cce-175">They cannot be captured by any closure construct (`async` methods or lambda expressions).</span></span>
* <span data-ttu-id="31cce-176">Eles não podem ser usados como um parâmetro genérico.</span><span class="sxs-lookup"><span data-stu-id="31cce-176">They cannot be used as a generic parameter.</span></span>

<span data-ttu-id="31cce-177">Esse último ponto é crucial para F # programação no estilo do pipeline, como `|>` é uma função genérica que parametriza seus tipos de entrada.</span><span class="sxs-lookup"><span data-stu-id="31cce-177">This last point is crucial for F# pipeline-style programming, as `|>` is a generic function that parameterizes its input types.</span></span> <span data-ttu-id="31cce-178">Essa restrição pode ser reduzida a `|>` no futuro, conforme ele é embutido e não faz todas as chamadas para funções genéricas não embutida em seu corpo.</span><span class="sxs-lookup"><span data-stu-id="31cce-178">This restriction may be relaxed for `|>` in the future, as it is inline and does not make any calls to non-inlined generic functions in its body.</span></span>

<span data-ttu-id="31cce-179">Embora essas regras altamente restringem o uso, eles fazem isso para cumprir a promessa de computação de alto desempenho de maneira segura.</span><span class="sxs-lookup"><span data-stu-id="31cce-179">Although these rules very strongly restrict usage, they do so to fulfill the promise of high-performance computing in a safe manner.</span></span>

## <a name="byref-returns"></a><span data-ttu-id="31cce-180">Retornos de ByRef</span><span class="sxs-lookup"><span data-stu-id="31cce-180">Byref returns</span></span>

<span data-ttu-id="31cce-181">Retornos de ByRef do functions em F # ou os membros podem ser gerados e consumidos.</span><span class="sxs-lookup"><span data-stu-id="31cce-181">Byref returns from F# functions or members can be produced and consumed.</span></span> <span data-ttu-id="31cce-182">Ao consumir um `byref`-método de retorno, o valor é deferência implícita.</span><span class="sxs-lookup"><span data-stu-id="31cce-182">When consuming a `byref`-returning method, the value is implicitly dereferenced.</span></span> <span data-ttu-id="31cce-183">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="31cce-183">For example:</span></span>

```fsharp
let safeSum(bytes: Span<byte>) =
    let mutable sum = 0
    for i in 0 .. bytes.Length - 1 do
        sum <- sum + int bytes.[i]
    sum

let sum = safeSum(mySpanOfBytes)
printfn "%d" sum // 'sum' is of type 'int'
```

<span data-ttu-id="31cce-184">Para evitar a desreferência implícita, como passar uma referência por meio de várias chamadas encadeadas, use `&x` (onde `x` é o valor).</span><span class="sxs-lookup"><span data-stu-id="31cce-184">To avoid the implicit dereference, such as passing a reference through multiple chained calls, use `&x` (where `x` is the value).</span></span>

<span data-ttu-id="31cce-185">Você pode também atribuir diretamente a um retorno `byref`.</span><span class="sxs-lookup"><span data-stu-id="31cce-185">You can also directly assign to a return `byref`.</span></span> <span data-ttu-id="31cce-186">Considere o seguinte programa (altamente obrigatório):</span><span class="sxs-lookup"><span data-stu-id="31cce-186">Consider the following (highly imperative) program:</span></span>

```fsharp
type C() =
    let mutable nums = [| 1; 3; 7; 15; 31; 63; 127; 255; 511; 1023 |]

    override __.ToString() = String.Join(' ', nums)

    member __.FindLargestSmallerThan(target: int) =
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

<span data-ttu-id="31cce-187">Esta é a saída:</span><span class="sxs-lookup"><span data-stu-id="31cce-187">This is the output:</span></span>

```console
Original sequence: 1 3 7 15 31 63 127 255 511 1023
New sequence:      1 3 7 30 31 63 127 255 511 1023
```

## <a name="scoping-for-byrefs"></a><span data-ttu-id="31cce-188">Escopo para zkratka</span><span class="sxs-lookup"><span data-stu-id="31cce-188">Scoping for byrefs</span></span>

<span data-ttu-id="31cce-189">Um `let`-valor associado não pode ter sua referência excedam o escopo no qual ele foi definido.</span><span class="sxs-lookup"><span data-stu-id="31cce-189">A `let`-bound value cannot have its reference exceed the scope in which it was defined.</span></span> <span data-ttu-id="31cce-190">Por exemplo, o seguinte não é permitido:</span><span class="sxs-lookup"><span data-stu-id="31cce-190">For example, the following is disallowed:</span></span>

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

<span data-ttu-id="31cce-191">Isso impede que você obter resultados diferentes dependendo se você compilar com otimizações ativada ou desativada.</span><span class="sxs-lookup"><span data-stu-id="31cce-191">This prevents you from getting different results depending on if you compile with optimizations on or off.</span></span>
