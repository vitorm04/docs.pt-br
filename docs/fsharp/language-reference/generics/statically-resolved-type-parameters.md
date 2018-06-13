---
title: Parâmetros de tipo resolvidos estaticamente (F#)
description: 'Saiba como usar uma linguagem F # parâmetro de tipo resolvidos estaticamente, que é substituído por um tipo real em tempo de compilação em vez de em tempo de execução.'
ms.date: 05/16/2016
ms.openlocfilehash: 12c2af4d9df7ae1e5e77efc9413eb8777459a83c
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34233776"
---
# <a name="statically-resolved-type-parameters"></a><span data-ttu-id="92e62-103">Parâmetros de tipo resolvidos estaticamente</span><span class="sxs-lookup"><span data-stu-id="92e62-103">Statically Resolved Type Parameters</span></span>

<span data-ttu-id="92e62-104">Um *parâmetro de tipo resolvidos estaticamente* é um parâmetro de tipo que é substituído por um tipo real em tempo de compilação em vez de em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="92e62-104">A *statically resolved type parameter* is a type parameter that is replaced with an actual type at compile time instead of at run time.</span></span> <span data-ttu-id="92e62-105">Eles são precedidos por um símbolo de acento circunflexo (^).</span><span class="sxs-lookup"><span data-stu-id="92e62-105">They are preceded by a caret (^) symbol.</span></span>


## <a name="syntax"></a><span data-ttu-id="92e62-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="92e62-106">Syntax</span></span>

```
ˆtype-parameter
```

## <a name="remarks"></a><span data-ttu-id="92e62-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="92e62-107">Remarks</span></span>
<span data-ttu-id="92e62-108">Na linguagem F #, há dois tipos distintos de parâmetros de tipo.</span><span class="sxs-lookup"><span data-stu-id="92e62-108">In the F# language, there are two distinct kinds of type parameters.</span></span> <span data-ttu-id="92e62-109">O primeiro tipo é o parâmetro de tipo genérico padrão.</span><span class="sxs-lookup"><span data-stu-id="92e62-109">The first kind is the standard generic type parameter.</span></span> <span data-ttu-id="92e62-110">Esses são indicadas por um apóstrofo ('), como em `'T` e `'U`.</span><span class="sxs-lookup"><span data-stu-id="92e62-110">These are indicated by an apostrophe ('), as in `'T` and `'U`.</span></span> <span data-ttu-id="92e62-111">Eles são equivalentes aos parâmetros de tipo genérico em outras linguagens do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="92e62-111">They are equivalent to generic type parameters in other .NET Framework languages.</span></span> <span data-ttu-id="92e62-112">O outro tipo é resolvido estaticamente e é indicado por um símbolo de cursor, como em `^T` e `^U`.</span><span class="sxs-lookup"><span data-stu-id="92e62-112">The other kind is statically resolved and is indicated by a caret symbol, as in `^T` and `^U`.</span></span>

<span data-ttu-id="92e62-113">Parâmetros de tipo resolvidos estaticamente são útil principalmente em conjunto com as restrições de membro, que são as restrições que permitem que você especifique que um argumento de tipo deve ter um determinado membro ou membros para ser usado.</span><span class="sxs-lookup"><span data-stu-id="92e62-113">Statically resolved type parameters are primarily useful in conjunction with member constraints, which are constraints that allow you to specify that a type argument must have a particular member or members in order to be used.</span></span> <span data-ttu-id="92e62-114">Não há nenhuma maneira de criar esse tipo de restrição usando um parâmetro de tipo genérico regular.</span><span class="sxs-lookup"><span data-stu-id="92e62-114">There is no way to create this kind of constraint by using a regular generic type parameter.</span></span>

<span data-ttu-id="92e62-115">A tabela a seguir resume as semelhanças e diferenças entre os dois tipos de parâmetros de tipo.</span><span class="sxs-lookup"><span data-stu-id="92e62-115">The following table summarizes the similarities and differences between the two kinds of type parameters.</span></span>

|<span data-ttu-id="92e62-116">Recurso</span><span class="sxs-lookup"><span data-stu-id="92e62-116">Feature</span></span>|<span data-ttu-id="92e62-117">Genérico</span><span class="sxs-lookup"><span data-stu-id="92e62-117">Generic</span></span>|<span data-ttu-id="92e62-118">Resolvidos estaticamente</span><span class="sxs-lookup"><span data-stu-id="92e62-118">Statically resolved</span></span>|
|-------|-------|-------------------|
|<span data-ttu-id="92e62-119">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="92e62-119">Syntax</span></span>|<span data-ttu-id="92e62-120">`'T`, `'U`</span><span class="sxs-lookup"><span data-stu-id="92e62-120">`'T`, `'U`</span></span>|<span data-ttu-id="92e62-121">`^T`, `^U`</span><span class="sxs-lookup"><span data-stu-id="92e62-121">`^T`, `^U`</span></span>|
|<span data-ttu-id="92e62-122">Tempo de resolução</span><span class="sxs-lookup"><span data-stu-id="92e62-122">Resolution time</span></span>|<span data-ttu-id="92e62-123">Tempo de execução</span><span class="sxs-lookup"><span data-stu-id="92e62-123">Run time</span></span>|<span data-ttu-id="92e62-124">Tempo de compilação</span><span class="sxs-lookup"><span data-stu-id="92e62-124">Compile time</span></span>|
|<span data-ttu-id="92e62-125">Restrições de membro</span><span class="sxs-lookup"><span data-stu-id="92e62-125">Member constraints</span></span>|<span data-ttu-id="92e62-126">Não pode ser usado com restrições de membro.</span><span class="sxs-lookup"><span data-stu-id="92e62-126">Cannot be used with member constraints.</span></span>|<span data-ttu-id="92e62-127">Pode ser usado com restrições de membro.</span><span class="sxs-lookup"><span data-stu-id="92e62-127">Can be used with member constraints.</span></span>|
|<span data-ttu-id="92e62-128">Geração de código</span><span class="sxs-lookup"><span data-stu-id="92e62-128">Code generation</span></span>|<span data-ttu-id="92e62-129">Um tipo (ou método) com parâmetros de tipo genérico padrão resulta na geração de um único tipo genérico ou método.</span><span class="sxs-lookup"><span data-stu-id="92e62-129">A type (or method) with standard generic type parameters results in the generation of a single generic type or method.</span></span>|<span data-ttu-id="92e62-130">Várias instâncias de tipos e métodos são geradas, uma para cada tipo que é necessária.</span><span class="sxs-lookup"><span data-stu-id="92e62-130">Multiple instantiations of types and methods are generated, one for each type that is needed.</span></span>|
|<span data-ttu-id="92e62-131">Use com tipos</span><span class="sxs-lookup"><span data-stu-id="92e62-131">Use with types</span></span>|<span data-ttu-id="92e62-132">Pode ser usada em tipos.</span><span class="sxs-lookup"><span data-stu-id="92e62-132">Can be used on types.</span></span>|<span data-ttu-id="92e62-133">Não pode ser usada em tipos.</span><span class="sxs-lookup"><span data-stu-id="92e62-133">Cannot be used on types.</span></span>|
|<span data-ttu-id="92e62-134">Use com funções embutidas</span><span class="sxs-lookup"><span data-stu-id="92e62-134">Use with inline functions</span></span>|<span data-ttu-id="92e62-135">Nº</span><span class="sxs-lookup"><span data-stu-id="92e62-135">No.</span></span> <span data-ttu-id="92e62-136">Uma função embutida não pode ser parametrizada com um parâmetro de tipo genérico padrão.</span><span class="sxs-lookup"><span data-stu-id="92e62-136">An inline function cannot be parameterized with a standard generic type parameter.</span></span>|<span data-ttu-id="92e62-137">Sim.</span><span class="sxs-lookup"><span data-stu-id="92e62-137">Yes.</span></span> <span data-ttu-id="92e62-138">Parâmetros de tipo resolvidos estaticamente não podem ser usados em funções ou métodos que não são embutidos.</span><span class="sxs-lookup"><span data-stu-id="92e62-138">Statically resolved type parameters cannot be used on functions or methods that are not inline.</span></span>|

<span data-ttu-id="92e62-139">Muitos F # principais funções de biblioteca, principalmente operadores, estaticamente resolveu parâmetros de tipo.</span><span class="sxs-lookup"><span data-stu-id="92e62-139">Many F# core library functions, especially operators, have statically resolved type parameters.</span></span> <span data-ttu-id="92e62-140">Esses operadores e funções internas e resultam na geração de código eficiente para cálculos numéricos.</span><span class="sxs-lookup"><span data-stu-id="92e62-140">These functions and operators are inline, and result in efficient code generation for numeric computations.</span></span>

<span data-ttu-id="92e62-141">Métodos embutidos e funções que usam operadores, ou usar outras funções que têm parâmetros de tipo, resolvidos estaticamente também podem usar parâmetros de tipo resolvidos estaticamente próprios.</span><span class="sxs-lookup"><span data-stu-id="92e62-141">Inline methods and functions that use operators, or use other functions that have statically resolved type parameters, can also use statically resolved type parameters themselves.</span></span> <span data-ttu-id="92e62-142">Muitas vezes, a inferência de tipo infere tais funções embutidas para ter parâmetros de tipo resolvidos estaticamente.</span><span class="sxs-lookup"><span data-stu-id="92e62-142">Often, type inference infers such inline functions to have statically resolved type parameters.</span></span> <span data-ttu-id="92e62-143">O exemplo a seguir ilustra uma definição de operador é inferida para ter um parâmetro de tipo resolvidos estaticamente.</span><span class="sxs-lookup"><span data-stu-id="92e62-143">The following example illustrates an operator definition that is inferred to have a statically resolved type parameter.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet401.fs)]

<span data-ttu-id="92e62-144">O tipo resolvido de `(+@)` baseia-se no uso de ambos `(+)` e `(*)`, ambos do que fazer com que a inferência de tipos inferir restrições de membro em parâmetros de tipo resolvidos estaticamente.</span><span class="sxs-lookup"><span data-stu-id="92e62-144">The resolved type of `(+@)` is based on the use of both `(+)` and `(*)`, both of which cause type inference to infer member constraints on the statically resolved type parameters.</span></span> <span data-ttu-id="92e62-145">O tipo resolvido, conforme o interpretador de F #, é o seguinte.</span><span class="sxs-lookup"><span data-stu-id="92e62-145">The resolved type, as shown in the F# interpreter, is as follows.</span></span>

```fsharp
^a -> ^c -> ^d
when (^a or ^b) : (static member ( + ) : ^a * ^b -> ^d) and
(^a or ^c) : (static member ( * ) : ^a * ^c -> ^b)
```

<span data-ttu-id="92e62-146">A saída é a seguinte.</span><span class="sxs-lookup"><span data-stu-id="92e62-146">The output is as follows.</span></span>

```
2
1.500000
```

<span data-ttu-id="92e62-147">A partir do F # 4.1, você pode também especificar nomes de tipo concreto em assinaturas de parâmetro de tipo resolvidos estaticamente.</span><span class="sxs-lookup"><span data-stu-id="92e62-147">Starting with F# 4.1, you can also specify concrete type names in statically resolved type parameter signatures.</span></span>  <span data-ttu-id="92e62-148">Nas versões anteriores do idioma, o nome do tipo, na verdade, pode ser inferido pelo compilador, mas, na verdade, não pôde ser especificado na assinatura.</span><span class="sxs-lookup"><span data-stu-id="92e62-148">In previous versions of the language, the type name could actually be inferred by the compiler, but could not actually be specified in the signature.</span></span>  <span data-ttu-id="92e62-149">A partir do F # 4.1, você também pode especificar nomes de tipo concreto em assinaturas de parâmetro de tipo resolvidos estaticamente.</span><span class="sxs-lookup"><span data-stu-id="92e62-149">As of F# 4.1, you may also specify concrete type names in statically resolved type parameter signatures.</span></span> <span data-ttu-id="92e62-150">Veja um exemplo:</span><span class="sxs-lookup"><span data-stu-id="92e62-150">Here's an example:</span></span>

```fsharp
let inline konst x _ = x

type CFunctor() = 
    static member inline fmap (f: ^a -> ^b, a: ^a list) = List.map f a
    static member inline fmap (f: ^a -> ^b, a: ^a option) =
        match a with
        | None -> None
        | Some x -> Some (f x)

    // default implementation of replace
    static member inline replace< ^a, ^b, ^c, ^d, ^e when ^a :> CFunctor and (^a or ^d): (static member fmap: (^b -> ^c) * ^d -> ^e) > (a, f) =
        ((^a or ^d) : (static member fmap : (^b -> ^c) * ^d -> ^e) (konst a, f))

    // call overridden replace if present
    static member inline replace< ^a, ^b, ^c when ^b: (static member replace: ^a * ^b -> ^c)>(a: ^a, f: ^b) =
        (^b : (static member replace: ^a * ^b -> ^c) (a, f))

let inline replace_instance< ^a, ^b, ^c, ^d when (^a or ^c): (static member replace: ^b * ^c -> ^d)> (a: ^b, f: ^c) =
        ((^a or ^c): (static member replace: ^b * ^c -> ^d) (a, f))

// Note the concrete type 'CFunctor' specified in the signature
let inline replace (a: ^a) (f: ^b): ^a0 when (CFunctor or  ^b): (static member replace: ^a *  ^b ->  ^a0) =
    replace_instance<CFunctor, _, _, _> (a, f)
```

## <a name="see-also"></a><span data-ttu-id="92e62-151">Consulte também</span><span class="sxs-lookup"><span data-stu-id="92e62-151">See Also</span></span>
[<span data-ttu-id="92e62-152">Genéricos</span><span class="sxs-lookup"><span data-stu-id="92e62-152">Generics</span></span>](index.md)

[<span data-ttu-id="92e62-153">Inferência de Tipos</span><span class="sxs-lookup"><span data-stu-id="92e62-153">Type Inference</span></span>](../type-inference.md)

[<span data-ttu-id="92e62-154">Generalização Automática</span><span class="sxs-lookup"><span data-stu-id="92e62-154">Automatic Generalization</span></span>](automatic-generalization.md)

[<span data-ttu-id="92e62-155">Restrições</span><span class="sxs-lookup"><span data-stu-id="92e62-155">Constraints</span></span>](constraints.md)

[<span data-ttu-id="92e62-156">Funções Embutidas</span><span class="sxs-lookup"><span data-stu-id="92e62-156">Inline Functions</span></span>](../functions/inline-functions.md)
