---
title: "Parâmetros de tipo resolvidos estaticamente (F#)"
description: "Saiba como usar uma linguagem F # parâmetro de tipo resolvidos estaticamente, que é substituído por um tipo real em tempo de compilação em vez de em tempo de execução."
keywords: "visual f#, f#, programação funcional"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: b3797415-3e49-4f8a-a8ee-fa614c5721aa
ms.openlocfilehash: 14c629d6223584113af47636495be61decca02ad
ms.sourcegitcommit: 96cc82cac4650adfb65ba351506d8a8fbcd17b5c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2018
---
# <a name="statically-resolved-type-parameters"></a><span data-ttu-id="6a560-104">Parâmetros de tipo resolvidos estaticamente</span><span class="sxs-lookup"><span data-stu-id="6a560-104">Statically Resolved Type Parameters</span></span>

<span data-ttu-id="6a560-105">Um *parâmetro de tipo resolvidos estaticamente* é um parâmetro de tipo que é substituído por um tipo real em tempo de compilação em vez de em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="6a560-105">A *statically resolved type parameter* is a type parameter that is replaced with an actual type at compile time instead of at run time.</span></span> <span data-ttu-id="6a560-106">Eles são precedidos por um símbolo de acento circunflexo (^).</span><span class="sxs-lookup"><span data-stu-id="6a560-106">They are preceded by a caret (^) symbol.</span></span>


## <a name="syntax"></a><span data-ttu-id="6a560-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6a560-107">Syntax</span></span>

```
ˆtype-parameter
```

## <a name="remarks"></a><span data-ttu-id="6a560-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="6a560-108">Remarks</span></span>
<span data-ttu-id="6a560-109">Na linguagem F #, há dois tipos distintos de parâmetros de tipo.</span><span class="sxs-lookup"><span data-stu-id="6a560-109">In the F# language, there are two distinct kinds of type parameters.</span></span> <span data-ttu-id="6a560-110">O primeiro tipo é o parâmetro de tipo genérico padrão.</span><span class="sxs-lookup"><span data-stu-id="6a560-110">The first kind is the standard generic type parameter.</span></span> <span data-ttu-id="6a560-111">Esses são indicadas por um apóstrofo ('), como em `'T` e `'U`.</span><span class="sxs-lookup"><span data-stu-id="6a560-111">These are indicated by an apostrophe ('), as in `'T` and `'U`.</span></span> <span data-ttu-id="6a560-112">Eles são equivalentes aos parâmetros de tipo genérico em outras linguagens do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6a560-112">They are equivalent to generic type parameters in other .NET Framework languages.</span></span> <span data-ttu-id="6a560-113">O outro tipo é resolvido estaticamente e é indicado por um símbolo de cursor, como em `^T` e `^U`.</span><span class="sxs-lookup"><span data-stu-id="6a560-113">The other kind is statically resolved and is indicated by a caret symbol, as in `^T` and `^U`.</span></span>

<span data-ttu-id="6a560-114">Parâmetros de tipo resolvidos estaticamente são útil principalmente em conjunto com as restrições de membro, que são as restrições que permitem que você especifique que um argumento de tipo deve ter um determinado membro ou membros para ser usado.</span><span class="sxs-lookup"><span data-stu-id="6a560-114">Statically resolved type parameters are primarily useful in conjunction with member constraints, which are constraints that allow you to specify that a type argument must have a particular member or members in order to be used.</span></span> <span data-ttu-id="6a560-115">Não há nenhuma maneira de criar esse tipo de restrição usando um parâmetro de tipo genérico regular.</span><span class="sxs-lookup"><span data-stu-id="6a560-115">There is no way to create this kind of constraint by using a regular generic type parameter.</span></span>

<span data-ttu-id="6a560-116">A tabela a seguir resume as semelhanças e diferenças entre os dois tipos de parâmetros de tipo.</span><span class="sxs-lookup"><span data-stu-id="6a560-116">The following table summarizes the similarities and differences between the two kinds of type parameters.</span></span>

|<span data-ttu-id="6a560-117">Recurso</span><span class="sxs-lookup"><span data-stu-id="6a560-117">Feature</span></span>|<span data-ttu-id="6a560-118">Genérico</span><span class="sxs-lookup"><span data-stu-id="6a560-118">Generic</span></span>|<span data-ttu-id="6a560-119">Resolvidos estaticamente</span><span class="sxs-lookup"><span data-stu-id="6a560-119">Statically resolved</span></span>|
|-------|-------|-------------------|
|<span data-ttu-id="6a560-120">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6a560-120">Syntax</span></span>|<span data-ttu-id="6a560-121">`'T`, `'U`</span><span class="sxs-lookup"><span data-stu-id="6a560-121">`'T`, `'U`</span></span>|<span data-ttu-id="6a560-122">`^T`, `^U`</span><span class="sxs-lookup"><span data-stu-id="6a560-122">`^T`, `^U`</span></span>|
|<span data-ttu-id="6a560-123">Tempo de resolução</span><span class="sxs-lookup"><span data-stu-id="6a560-123">Resolution time</span></span>|<span data-ttu-id="6a560-124">Tempo de execução</span><span class="sxs-lookup"><span data-stu-id="6a560-124">Run time</span></span>|<span data-ttu-id="6a560-125">Tempo de compilação</span><span class="sxs-lookup"><span data-stu-id="6a560-125">Compile time</span></span>|
|<span data-ttu-id="6a560-126">Restrições de membro</span><span class="sxs-lookup"><span data-stu-id="6a560-126">Member constraints</span></span>|<span data-ttu-id="6a560-127">Não pode ser usado com restrições de membro.</span><span class="sxs-lookup"><span data-stu-id="6a560-127">Cannot be used with member constraints.</span></span>|<span data-ttu-id="6a560-128">Pode ser usado com restrições de membro.</span><span class="sxs-lookup"><span data-stu-id="6a560-128">Can be used with member constraints.</span></span>|
|<span data-ttu-id="6a560-129">Geração de código</span><span class="sxs-lookup"><span data-stu-id="6a560-129">Code generation</span></span>|<span data-ttu-id="6a560-130">Um tipo (ou método) com parâmetros de tipo genérico padrão resulta na geração de um único tipo genérico ou método.</span><span class="sxs-lookup"><span data-stu-id="6a560-130">A type (or method) with standard generic type parameters results in the generation of a single generic type or method.</span></span>|<span data-ttu-id="6a560-131">Várias instâncias de tipos e métodos são geradas, uma para cada tipo que é necessária.</span><span class="sxs-lookup"><span data-stu-id="6a560-131">Multiple instantiations of types and methods are generated, one for each type that is needed.</span></span>|
|<span data-ttu-id="6a560-132">Use com tipos</span><span class="sxs-lookup"><span data-stu-id="6a560-132">Use with types</span></span>|<span data-ttu-id="6a560-133">Pode ser usada em tipos.</span><span class="sxs-lookup"><span data-stu-id="6a560-133">Can be used on types.</span></span>|<span data-ttu-id="6a560-134">Não pode ser usada em tipos.</span><span class="sxs-lookup"><span data-stu-id="6a560-134">Cannot be used on types.</span></span>|
|<span data-ttu-id="6a560-135">Use com funções embutidas</span><span class="sxs-lookup"><span data-stu-id="6a560-135">Use with inline functions</span></span>|<span data-ttu-id="6a560-136">Nº</span><span class="sxs-lookup"><span data-stu-id="6a560-136">No.</span></span> <span data-ttu-id="6a560-137">Uma função embutida não pode ser parametrizada com um parâmetro de tipo genérico padrão.</span><span class="sxs-lookup"><span data-stu-id="6a560-137">An inline function cannot be parameterized with a standard generic type parameter.</span></span>|<span data-ttu-id="6a560-138">Sim.</span><span class="sxs-lookup"><span data-stu-id="6a560-138">Yes.</span></span> <span data-ttu-id="6a560-139">Parâmetros de tipo resolvidos estaticamente não podem ser usados em funções ou métodos que não são embutidos.</span><span class="sxs-lookup"><span data-stu-id="6a560-139">Statically resolved type parameters cannot be used on functions or methods that are not inline.</span></span>|

<span data-ttu-id="6a560-140">Muitos F # principais funções de biblioteca, principalmente operadores, estaticamente resolveu parâmetros de tipo.</span><span class="sxs-lookup"><span data-stu-id="6a560-140">Many F# core library functions, especially operators, have statically resolved type parameters.</span></span> <span data-ttu-id="6a560-141">Esses operadores e funções internas e resultam na geração de código eficiente para cálculos numéricos.</span><span class="sxs-lookup"><span data-stu-id="6a560-141">These functions and operators are inline, and result in efficient code generation for numeric computations.</span></span>

<span data-ttu-id="6a560-142">Métodos embutidos e funções que usam operadores, ou usar outras funções que têm parâmetros de tipo, resolvidos estaticamente também podem usar parâmetros de tipo resolvidos estaticamente próprios.</span><span class="sxs-lookup"><span data-stu-id="6a560-142">Inline methods and functions that use operators, or use other functions that have statically resolved type parameters, can also use statically resolved type parameters themselves.</span></span> <span data-ttu-id="6a560-143">Muitas vezes, a inferência de tipo infere tais funções embutidas para ter parâmetros de tipo resolvidos estaticamente.</span><span class="sxs-lookup"><span data-stu-id="6a560-143">Often, type inference infers such inline functions to have statically resolved type parameters.</span></span> <span data-ttu-id="6a560-144">O exemplo a seguir ilustra uma definição de operador é inferida para ter um parâmetro de tipo resolvidos estaticamente.</span><span class="sxs-lookup"><span data-stu-id="6a560-144">The following example illustrates an operator definition that is inferred to have a statically resolved type parameter.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet401.fs)]

<span data-ttu-id="6a560-145">O tipo resolvido de `(+@)` baseia-se no uso de ambos `(+)` e `(*)`, ambos do que fazer com que a inferência de tipos inferir restrições de membro em parâmetros de tipo resolvidos estaticamente.</span><span class="sxs-lookup"><span data-stu-id="6a560-145">The resolved type of `(+@)` is based on the use of both `(+)` and `(*)`, both of which cause type inference to infer member constraints on the statically resolved type parameters.</span></span> <span data-ttu-id="6a560-146">O tipo resolvido, conforme o interpretador de F #, é o seguinte.</span><span class="sxs-lookup"><span data-stu-id="6a560-146">The resolved type, as shown in the F# interpreter, is as follows.</span></span>

```fsharp
^a -> ^c -> ^d
when (^a or ^b) : (static member ( + ) : ^a * ^b -> ^d) and
(^a or ^c) : (static member ( * ) : ^a * ^c -> ^b)
```

<span data-ttu-id="6a560-147">A saída é a seguinte.</span><span class="sxs-lookup"><span data-stu-id="6a560-147">The output is as follows.</span></span>

```
2
1.500000
```

<span data-ttu-id="6a560-148">A partir do F # 4.1, você pode também especificar nomes de tipo concreto em assinaturas de parâmetro de tipo resolvidos estaticamente.</span><span class="sxs-lookup"><span data-stu-id="6a560-148">Starting with F# 4.1, you can also specify concrete type names in statically resolved type parameter signatures.</span></span>  <span data-ttu-id="6a560-149">Nas versões anteriores do idioma, o nome do tipo, na verdade, pode ser inferido pelo compilador, mas, na verdade, não pôde ser especificado na assinatura.</span><span class="sxs-lookup"><span data-stu-id="6a560-149">In previous versions of the language, the type name could actually be inferred by the compiler, but could not actually be specified in the signature.</span></span>  <span data-ttu-id="6a560-150">A partir do F # 4.1, você também pode especificar nomes de tipo concreto em assinaturas de parâmetro de tipo resolvidos estaticamente.</span><span class="sxs-lookup"><span data-stu-id="6a560-150">As of F# 4.1, you may also specify concrete type names in statically resolved type parameter signatures.</span></span> <span data-ttu-id="6a560-151">Veja um exemplo:</span><span class="sxs-lookup"><span data-stu-id="6a560-151">Here's an example:</span></span>

```fsharp
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

## <a name="see-also"></a><span data-ttu-id="6a560-152">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6a560-152">See Also</span></span>
[<span data-ttu-id="6a560-153">Genéricos</span><span class="sxs-lookup"><span data-stu-id="6a560-153">Generics</span></span>](index.md)

[<span data-ttu-id="6a560-154">Inferência de Tipos</span><span class="sxs-lookup"><span data-stu-id="6a560-154">Type Inference</span></span>](../type-inference.md)

[<span data-ttu-id="6a560-155">Generalização Automática</span><span class="sxs-lookup"><span data-stu-id="6a560-155">Automatic Generalization</span></span>](automatic-generalization.md)

[<span data-ttu-id="6a560-156">Restrições</span><span class="sxs-lookup"><span data-stu-id="6a560-156">Constraints</span></span>](constraints.md)

[<span data-ttu-id="6a560-157">Funções Embutidas</span><span class="sxs-lookup"><span data-stu-id="6a560-157">Inline Functions</span></span>](../functions/inline-functions.md)
