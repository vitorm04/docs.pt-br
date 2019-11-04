---
title: Parâmetros de tipo resolvidos estaticamente
description: Saiba como usar um F# parâmetro de tipo estaticamente resolvido, que é substituído por um tipo real em tempo de compilação em vez de em tempo de execução.
ms.date: 05/16/2016
ms.openlocfilehash: 017c18dd3caaa484ddc653557573f548e3224ca0
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73425004"
---
# <a name="statically-resolved-type-parameters"></a><span data-ttu-id="990c1-103">Parâmetros de tipo resolvidos estaticamente</span><span class="sxs-lookup"><span data-stu-id="990c1-103">Statically Resolved Type Parameters</span></span>

<span data-ttu-id="990c1-104">Um *parâmetro de tipo estaticamente resolvido* é um parâmetro de tipo que é substituído por um tipo real em tempo de compilação em vez de em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="990c1-104">A *statically resolved type parameter* is a type parameter that is replaced with an actual type at compile time instead of at run time.</span></span> <span data-ttu-id="990c1-105">Elas são precedidas por um símbolo de acento circunflexo (^).</span><span class="sxs-lookup"><span data-stu-id="990c1-105">They are preceded by a caret (^) symbol.</span></span>

## <a name="syntax"></a><span data-ttu-id="990c1-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="990c1-106">Syntax</span></span>

```fsharp
ˆtype-parameter
```

## <a name="remarks"></a><span data-ttu-id="990c1-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="990c1-107">Remarks</span></span>

<span data-ttu-id="990c1-108">No F# idioma, há dois tipos distintos de parâmetros de tipo.</span><span class="sxs-lookup"><span data-stu-id="990c1-108">In the F# language, there are two distinct kinds of type parameters.</span></span> <span data-ttu-id="990c1-109">O primeiro tipo é o parâmetro de tipo genérico padrão.</span><span class="sxs-lookup"><span data-stu-id="990c1-109">The first kind is the standard generic type parameter.</span></span> <span data-ttu-id="990c1-110">Eles são indicados por um apóstrofo ('), como em `'T` e `'U`.</span><span class="sxs-lookup"><span data-stu-id="990c1-110">These are indicated by an apostrophe ('), as in `'T` and `'U`.</span></span> <span data-ttu-id="990c1-111">Eles são equivalentes a parâmetros de tipo genérico em outras linguagens de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="990c1-111">They are equivalent to generic type parameters in other .NET Framework languages.</span></span> <span data-ttu-id="990c1-112">O outro tipo é resolvido estaticamente e é indicado por um símbolo de cursor, como em `^T` e `^U`.</span><span class="sxs-lookup"><span data-stu-id="990c1-112">The other kind is statically resolved and is indicated by a caret symbol, as in `^T` and `^U`.</span></span>

<span data-ttu-id="990c1-113">Parâmetros de tipo estaticamente resolvidos são úteis principalmente em conjunto com restrições de membro, que são restrições que permitem especificar que um argumento de tipo deve ter um membro específico ou membros para serem usados.</span><span class="sxs-lookup"><span data-stu-id="990c1-113">Statically resolved type parameters are primarily useful in conjunction with member constraints, which are constraints that allow you to specify that a type argument must have a particular member or members in order to be used.</span></span> <span data-ttu-id="990c1-114">Não é possível criar esse tipo de restrição usando um parâmetro de tipo genérico regular.</span><span class="sxs-lookup"><span data-stu-id="990c1-114">There is no way to create this kind of constraint by using a regular generic type parameter.</span></span>

<span data-ttu-id="990c1-115">A tabela a seguir resume as semelhanças e diferenças entre os dois tipos de parâmetros de tipo.</span><span class="sxs-lookup"><span data-stu-id="990c1-115">The following table summarizes the similarities and differences between the two kinds of type parameters.</span></span>

|<span data-ttu-id="990c1-116">Recurso</span><span class="sxs-lookup"><span data-stu-id="990c1-116">Feature</span></span>|<span data-ttu-id="990c1-117">Genérico</span><span class="sxs-lookup"><span data-stu-id="990c1-117">Generic</span></span>|<span data-ttu-id="990c1-118">Resolvido estaticamente</span><span class="sxs-lookup"><span data-stu-id="990c1-118">Statically resolved</span></span>|
|-------|-------|-------------------|
|<span data-ttu-id="990c1-119">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="990c1-119">Syntax</span></span>|<span data-ttu-id="990c1-120">`'T`, `'U`</span><span class="sxs-lookup"><span data-stu-id="990c1-120">`'T`, `'U`</span></span>|<span data-ttu-id="990c1-121">`^T`, `^U`</span><span class="sxs-lookup"><span data-stu-id="990c1-121">`^T`, `^U`</span></span>|
|<span data-ttu-id="990c1-122">Tempo de resolução</span><span class="sxs-lookup"><span data-stu-id="990c1-122">Resolution time</span></span>|<span data-ttu-id="990c1-123">Tempo de execução</span><span class="sxs-lookup"><span data-stu-id="990c1-123">Run time</span></span>|<span data-ttu-id="990c1-124">Tempo de compilação</span><span class="sxs-lookup"><span data-stu-id="990c1-124">Compile time</span></span>|
|<span data-ttu-id="990c1-125">Restrições de membro</span><span class="sxs-lookup"><span data-stu-id="990c1-125">Member constraints</span></span>|<span data-ttu-id="990c1-126">Não pode ser usado com restrições de membro.</span><span class="sxs-lookup"><span data-stu-id="990c1-126">Cannot be used with member constraints.</span></span>|<span data-ttu-id="990c1-127">Pode ser usado com restrições de membro.</span><span class="sxs-lookup"><span data-stu-id="990c1-127">Can be used with member constraints.</span></span>|
|<span data-ttu-id="990c1-128">Geração de código</span><span class="sxs-lookup"><span data-stu-id="990c1-128">Code generation</span></span>|<span data-ttu-id="990c1-129">Um tipo (ou método) com parâmetros de tipo genérico padrão resulta na geração de um único tipo ou método genérico.</span><span class="sxs-lookup"><span data-stu-id="990c1-129">A type (or method) with standard generic type parameters results in the generation of a single generic type or method.</span></span>|<span data-ttu-id="990c1-130">Várias instanciações de tipos e métodos são geradas, uma para cada tipo necessário.</span><span class="sxs-lookup"><span data-stu-id="990c1-130">Multiple instantiations of types and methods are generated, one for each type that is needed.</span></span>|
|<span data-ttu-id="990c1-131">Usar com tipos</span><span class="sxs-lookup"><span data-stu-id="990c1-131">Use with types</span></span>|<span data-ttu-id="990c1-132">Pode ser usado em tipos.</span><span class="sxs-lookup"><span data-stu-id="990c1-132">Can be used on types.</span></span>|<span data-ttu-id="990c1-133">Não pode ser usado em tipos.</span><span class="sxs-lookup"><span data-stu-id="990c1-133">Cannot be used on types.</span></span>|
|<span data-ttu-id="990c1-134">Usar com funções embutidas</span><span class="sxs-lookup"><span data-stu-id="990c1-134">Use with inline functions</span></span>|<span data-ttu-id="990c1-135">Nº</span><span class="sxs-lookup"><span data-stu-id="990c1-135">No.</span></span> <span data-ttu-id="990c1-136">Uma função embutida não pode ser parametrizada com um parâmetro de tipo genérico padrão.</span><span class="sxs-lookup"><span data-stu-id="990c1-136">An inline function cannot be parameterized with a standard generic type parameter.</span></span>|<span data-ttu-id="990c1-137">Sim.</span><span class="sxs-lookup"><span data-stu-id="990c1-137">Yes.</span></span> <span data-ttu-id="990c1-138">Parâmetros de tipo estaticamente resolvidos não podem ser usados em funções ou métodos que não são embutidos.</span><span class="sxs-lookup"><span data-stu-id="990c1-138">Statically resolved type parameters cannot be used on functions or methods that are not inline.</span></span>|

<span data-ttu-id="990c1-139">Muitas F# funções de biblioteca principal, especialmente operadores, têm parâmetros de tipo estaticamente resolvidos.</span><span class="sxs-lookup"><span data-stu-id="990c1-139">Many F# core library functions, especially operators, have statically resolved type parameters.</span></span> <span data-ttu-id="990c1-140">Essas funções e operadores são embutidos e resultam em uma geração de código eficiente para cálculos numéricos.</span><span class="sxs-lookup"><span data-stu-id="990c1-140">These functions and operators are inline, and result in efficient code generation for numeric computations.</span></span>

<span data-ttu-id="990c1-141">Os métodos embutidos e as funções que usam operadores ou usam outras funções que têm parâmetros de tipo estaticamente resolvidos também podem usar parâmetros de tipo estaticamente resolvidos.</span><span class="sxs-lookup"><span data-stu-id="990c1-141">Inline methods and functions that use operators, or use other functions that have statically resolved type parameters, can also use statically resolved type parameters themselves.</span></span> <span data-ttu-id="990c1-142">Geralmente, a inferência de tipos infere essas funções embutidas para ter parâmetros de tipo estaticamente resolvidos.</span><span class="sxs-lookup"><span data-stu-id="990c1-142">Often, type inference infers such inline functions to have statically resolved type parameters.</span></span> <span data-ttu-id="990c1-143">O exemplo a seguir ilustra uma definição de operador que é inferida para ter um parâmetro de tipo estaticamente resolvido.</span><span class="sxs-lookup"><span data-stu-id="990c1-143">The following example illustrates an operator definition that is inferred to have a statically resolved type parameter.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet401.fs)]

<span data-ttu-id="990c1-144">O tipo resolvido de `(+@)` é baseado no uso de `(+)` e `(*)`, e ambos causam a inferência de tipos para inferir restrições de membro nos parâmetros de tipo estaticamente resolvidos.</span><span class="sxs-lookup"><span data-stu-id="990c1-144">The resolved type of `(+@)` is based on the use of both `(+)` and `(*)`, both of which cause type inference to infer member constraints on the statically resolved type parameters.</span></span> <span data-ttu-id="990c1-145">O tipo resolvido, conforme mostrado no F# intérprete, é o seguinte.</span><span class="sxs-lookup"><span data-stu-id="990c1-145">The resolved type, as shown in the F# interpreter, is as follows.</span></span>

```fsharp
^a -> ^c -> ^d
when (^a or ^b) : (static member ( + ) : ^a * ^b -> ^d) and
(^a or ^c) : (static member ( * ) : ^a * ^c -> ^b)
```

<span data-ttu-id="990c1-146">A saída é a seguinte.</span><span class="sxs-lookup"><span data-stu-id="990c1-146">The output is as follows.</span></span>

```console
2
1.500000
```

<span data-ttu-id="990c1-147">A F# partir do 4,1, você também pode especificar nomes de tipo concreto em assinaturas de parâmetro de tipo estaticamente resolvidas.</span><span class="sxs-lookup"><span data-stu-id="990c1-147">Starting with F# 4.1, you can also specify concrete type names in statically resolved type parameter signatures.</span></span>  <span data-ttu-id="990c1-148">Nas versões anteriores do idioma, o nome do tipo poderia ser realmente inferido pelo compilador, mas não poderia ser realmente especificado na assinatura.</span><span class="sxs-lookup"><span data-stu-id="990c1-148">In previous versions of the language, the type name could actually be inferred by the compiler, but could not actually be specified in the signature.</span></span>  <span data-ttu-id="990c1-149">A partir F# de 4,1, você também pode especificar nomes de tipo concreto em assinaturas de parâmetro de tipo estaticamente resolvidas.</span><span class="sxs-lookup"><span data-stu-id="990c1-149">As of F# 4.1, you may also specify concrete type names in statically resolved type parameter signatures.</span></span> <span data-ttu-id="990c1-150">Veja um exemplo:</span><span class="sxs-lookup"><span data-stu-id="990c1-150">Here's an example:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="990c1-151">Consulte também</span><span class="sxs-lookup"><span data-stu-id="990c1-151">See also</span></span>

- [<span data-ttu-id="990c1-152">Genéricos</span><span class="sxs-lookup"><span data-stu-id="990c1-152">Generics</span></span>](index.md)
- [<span data-ttu-id="990c1-153">Inferência de Tipos</span><span class="sxs-lookup"><span data-stu-id="990c1-153">Type Inference</span></span>](../type-inference.md)
- [<span data-ttu-id="990c1-154">Generalização Automática</span><span class="sxs-lookup"><span data-stu-id="990c1-154">Automatic Generalization</span></span>](automatic-generalization.md)
- [<span data-ttu-id="990c1-155">Restrições</span><span class="sxs-lookup"><span data-stu-id="990c1-155">Constraints</span></span>](constraints.md)
- [<span data-ttu-id="990c1-156">Funções Embutidas</span><span class="sxs-lookup"><span data-stu-id="990c1-156">Inline Functions</span></span>](../functions/inline-functions.md)
