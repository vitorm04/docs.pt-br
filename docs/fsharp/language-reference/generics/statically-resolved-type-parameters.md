---
title: Parâmetros de tipo resolvidos estaticamente (F#)
description: 'Saiba como usar F # parâmetro de tipo estaticamente resolvidos, o que é substituído por um tipo real em tempo de compilação em vez de em tempo de execução.'
ms.date: 05/16/2016
ms.openlocfilehash: 747917fef2746dcbf363ef4b717ace5e47229800
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45973164"
---
# <a name="statically-resolved-type-parameters"></a><span data-ttu-id="80193-103">Parâmetros de tipo resolvidos estaticamente</span><span class="sxs-lookup"><span data-stu-id="80193-103">Statically Resolved Type Parameters</span></span>

<span data-ttu-id="80193-104">Um *parâmetro de tipo estaticamente resolvido* é um parâmetro de tipo que é substituído por um tipo real em tempo de compilação em vez de em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="80193-104">A *statically resolved type parameter* is a type parameter that is replaced with an actual type at compile time instead of at run time.</span></span> <span data-ttu-id="80193-105">Eles são precedidos por um símbolo de acento circunflexo (^).</span><span class="sxs-lookup"><span data-stu-id="80193-105">They are preceded by a caret (^) symbol.</span></span>

## <a name="syntax"></a><span data-ttu-id="80193-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="80193-106">Syntax</span></span>

```
ˆtype-parameter
```

## <a name="remarks"></a><span data-ttu-id="80193-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="80193-107">Remarks</span></span>

<span data-ttu-id="80193-108">Na linguagem F #, há dois tipos diferentes de parâmetros de tipo.</span><span class="sxs-lookup"><span data-stu-id="80193-108">In the F# language, there are two distinct kinds of type parameters.</span></span> <span data-ttu-id="80193-109">O primeiro tipo é o parâmetro de tipo genérico padrão.</span><span class="sxs-lookup"><span data-stu-id="80193-109">The first kind is the standard generic type parameter.</span></span> <span data-ttu-id="80193-110">Eles são indicados por um apóstrofo ('), como em `'T` e `'U`.</span><span class="sxs-lookup"><span data-stu-id="80193-110">These are indicated by an apostrophe ('), as in `'T` and `'U`.</span></span> <span data-ttu-id="80193-111">Eles são equivalentes aos parâmetros de tipo genérico em outras linguagens do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="80193-111">They are equivalent to generic type parameters in other .NET Framework languages.</span></span> <span data-ttu-id="80193-112">O outro tipo é estaticamente resolvido e indicado por um símbolo de acento circunflexo, como em `^T` e `^U`.</span><span class="sxs-lookup"><span data-stu-id="80193-112">The other kind is statically resolved and is indicated by a caret symbol, as in `^T` and `^U`.</span></span>

<span data-ttu-id="80193-113">Parâmetros de tipo estaticamente resolvidos são úteis principalmente em conjunto com restrições de membro, que são restrições que permitem que você especifique que um argumento de tipo deve ter um determinado membro ou membros para ser usado.</span><span class="sxs-lookup"><span data-stu-id="80193-113">Statically resolved type parameters are primarily useful in conjunction with member constraints, which are constraints that allow you to specify that a type argument must have a particular member or members in order to be used.</span></span> <span data-ttu-id="80193-114">Não há nenhuma maneira de criar esse tipo de restrição usando um parâmetro de tipo genérico normal.</span><span class="sxs-lookup"><span data-stu-id="80193-114">There is no way to create this kind of constraint by using a regular generic type parameter.</span></span>

<span data-ttu-id="80193-115">A tabela a seguir resume as semelhanças e diferenças entre os dois tipos de parâmetros de tipo.</span><span class="sxs-lookup"><span data-stu-id="80193-115">The following table summarizes the similarities and differences between the two kinds of type parameters.</span></span>

|<span data-ttu-id="80193-116">Recurso</span><span class="sxs-lookup"><span data-stu-id="80193-116">Feature</span></span>|<span data-ttu-id="80193-117">Genérico</span><span class="sxs-lookup"><span data-stu-id="80193-117">Generic</span></span>|<span data-ttu-id="80193-118">Resolvidos estaticamente</span><span class="sxs-lookup"><span data-stu-id="80193-118">Statically resolved</span></span>|
|-------|-------|-------------------|
|<span data-ttu-id="80193-119">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="80193-119">Syntax</span></span>|<span data-ttu-id="80193-120">`'T`, `'U`</span><span class="sxs-lookup"><span data-stu-id="80193-120">`'T`, `'U`</span></span>|<span data-ttu-id="80193-121">`^T`, `^U`</span><span class="sxs-lookup"><span data-stu-id="80193-121">`^T`, `^U`</span></span>|
|<span data-ttu-id="80193-122">Tempo de resolução</span><span class="sxs-lookup"><span data-stu-id="80193-122">Resolution time</span></span>|<span data-ttu-id="80193-123">Tempo de execução</span><span class="sxs-lookup"><span data-stu-id="80193-123">Run time</span></span>|<span data-ttu-id="80193-124">Tempo de compilação</span><span class="sxs-lookup"><span data-stu-id="80193-124">Compile time</span></span>|
|<span data-ttu-id="80193-125">Restrições de membro</span><span class="sxs-lookup"><span data-stu-id="80193-125">Member constraints</span></span>|<span data-ttu-id="80193-126">Não pode ser usado com restrições de membro.</span><span class="sxs-lookup"><span data-stu-id="80193-126">Cannot be used with member constraints.</span></span>|<span data-ttu-id="80193-127">Pode ser usado com restrições de membro.</span><span class="sxs-lookup"><span data-stu-id="80193-127">Can be used with member constraints.</span></span>|
|<span data-ttu-id="80193-128">Geração de código</span><span class="sxs-lookup"><span data-stu-id="80193-128">Code generation</span></span>|<span data-ttu-id="80193-129">Um tipo (ou método) com parâmetros de tipo genéricos padrão resulta na geração de um único tipo genérico ou método.</span><span class="sxs-lookup"><span data-stu-id="80193-129">A type (or method) with standard generic type parameters results in the generation of a single generic type or method.</span></span>|<span data-ttu-id="80193-130">Várias instanciações de tipos e métodos são geradas, uma para cada tipo que é necessária.</span><span class="sxs-lookup"><span data-stu-id="80193-130">Multiple instantiations of types and methods are generated, one for each type that is needed.</span></span>|
|<span data-ttu-id="80193-131">Use com tipos</span><span class="sxs-lookup"><span data-stu-id="80193-131">Use with types</span></span>|<span data-ttu-id="80193-132">Pode ser usada em tipos.</span><span class="sxs-lookup"><span data-stu-id="80193-132">Can be used on types.</span></span>|<span data-ttu-id="80193-133">Não pode ser usada em tipos.</span><span class="sxs-lookup"><span data-stu-id="80193-133">Cannot be used on types.</span></span>|
|<span data-ttu-id="80193-134">Use com funções embutidas</span><span class="sxs-lookup"><span data-stu-id="80193-134">Use with inline functions</span></span>|<span data-ttu-id="80193-135">Nº</span><span class="sxs-lookup"><span data-stu-id="80193-135">No.</span></span> <span data-ttu-id="80193-136">Uma função embutida não pode ser parametrizada com um parâmetro de tipo genérico padrão.</span><span class="sxs-lookup"><span data-stu-id="80193-136">An inline function cannot be parameterized with a standard generic type parameter.</span></span>|<span data-ttu-id="80193-137">Sim.</span><span class="sxs-lookup"><span data-stu-id="80193-137">Yes.</span></span> <span data-ttu-id="80193-138">Parâmetros de tipo estaticamente resolvidos não podem ser usados em funções ou métodos que não estejam embutidos.</span><span class="sxs-lookup"><span data-stu-id="80193-138">Statically resolved type parameters cannot be used on functions or methods that are not inline.</span></span>|

<span data-ttu-id="80193-139">Muitas F # core funções de biblioteca, principalmente operadores, têm parâmetros de tipo estaticamente resolvidos.</span><span class="sxs-lookup"><span data-stu-id="80193-139">Many F# core library functions, especially operators, have statically resolved type parameters.</span></span> <span data-ttu-id="80193-140">Essas funções e operadores são embutidos e resultam na geração de código eficiente para cálculos numéricos.</span><span class="sxs-lookup"><span data-stu-id="80193-140">These functions and operators are inline, and result in efficient code generation for numeric computations.</span></span>

<span data-ttu-id="80193-141">Métodos embutidos e funções que usam operadores ou usam outras funções que resolveram estaticamente os parâmetros de tipo, também podem usar parâmetros de tipo estaticamente resolvidos.</span><span class="sxs-lookup"><span data-stu-id="80193-141">Inline methods and functions that use operators, or use other functions that have statically resolved type parameters, can also use statically resolved type parameters themselves.</span></span> <span data-ttu-id="80193-142">Muitas vezes, a inferência de tipo infere tais funções embutidas para parâmetros de tipo estaticamente resolvidos.</span><span class="sxs-lookup"><span data-stu-id="80193-142">Often, type inference infers such inline functions to have statically resolved type parameters.</span></span> <span data-ttu-id="80193-143">O exemplo a seguir ilustra uma definição de operador que é inferida para ter um parâmetro de tipo estaticamente resolvidos.</span><span class="sxs-lookup"><span data-stu-id="80193-143">The following example illustrates an operator definition that is inferred to have a statically resolved type parameter.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet401.fs)]

<span data-ttu-id="80193-144">O tipo resolvido de `(+@)` baseia-se no uso de ambos `(+)` e `(*)`, ambos fazem com que a inferência de tipo infira restrições de membros nos parâmetros de tipo estaticamente resolvidos.</span><span class="sxs-lookup"><span data-stu-id="80193-144">The resolved type of `(+@)` is based on the use of both `(+)` and `(*)`, both of which cause type inference to infer member constraints on the statically resolved type parameters.</span></span> <span data-ttu-id="80193-145">O tipo resolvido, conforme mostrado no interpretador da F #, é da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="80193-145">The resolved type, as shown in the F# interpreter, is as follows.</span></span>

```fsharp
^a -> ^c -> ^d
when (^a or ^b) : (static member ( + ) : ^a * ^b -> ^d) and
(^a or ^c) : (static member ( * ) : ^a * ^c -> ^b)
```

<span data-ttu-id="80193-146">A saída é a seguinte.</span><span class="sxs-lookup"><span data-stu-id="80193-146">The output is as follows.</span></span>

```
2
1.500000
```

<span data-ttu-id="80193-147">Começando com o F # 4.1, você pode também especificar nomes de tipo concreto em assinaturas de parâmetro de tipo estaticamente resolvidos.</span><span class="sxs-lookup"><span data-stu-id="80193-147">Starting with F# 4.1, you can also specify concrete type names in statically resolved type parameter signatures.</span></span>  <span data-ttu-id="80193-148">Nas versões anteriores da linguagem, o nome do tipo, na verdade, poderia ser inferido pelo compilador, mas, na verdade, não pôde ser especificado na assinatura.</span><span class="sxs-lookup"><span data-stu-id="80193-148">In previous versions of the language, the type name could actually be inferred by the compiler, but could not actually be specified in the signature.</span></span>  <span data-ttu-id="80193-149">A partir do F # 4.1, você também pode especificar nomes de tipo concreto em assinaturas de parâmetro de tipo estaticamente resolvidos.</span><span class="sxs-lookup"><span data-stu-id="80193-149">As of F# 4.1, you may also specify concrete type names in statically resolved type parameter signatures.</span></span> <span data-ttu-id="80193-150">Veja um exemplo:</span><span class="sxs-lookup"><span data-stu-id="80193-150">Here's an example:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="80193-151">Consulte também</span><span class="sxs-lookup"><span data-stu-id="80193-151">See also</span></span>

- [<span data-ttu-id="80193-152">Genéricos</span><span class="sxs-lookup"><span data-stu-id="80193-152">Generics</span></span>](index.md)
- [<span data-ttu-id="80193-153">Inferência de Tipos</span><span class="sxs-lookup"><span data-stu-id="80193-153">Type Inference</span></span>](../type-inference.md)
- [<span data-ttu-id="80193-154">Generalização Automática</span><span class="sxs-lookup"><span data-stu-id="80193-154">Automatic Generalization</span></span>](automatic-generalization.md)
- [<span data-ttu-id="80193-155">Restrições</span><span class="sxs-lookup"><span data-stu-id="80193-155">Constraints</span></span>](constraints.md)
- [<span data-ttu-id="80193-156">Funções Embutidas</span><span class="sxs-lookup"><span data-stu-id="80193-156">Inline Functions</span></span>](../functions/inline-functions.md)
