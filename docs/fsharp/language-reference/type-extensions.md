---
title: Extensões de tipo
description: Saiba como F# as extensões de tipo permitem adicionar novos membros a um tipo de objeto definido anteriormente.
ms.date: 11/04/2019
ms.openlocfilehash: 3e2c6971156bd562ed5d5428e6b7ffdc520c4cf5
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75341564"
---
# <a name="type-extensions"></a><span data-ttu-id="49c86-103">Extensões de tipo</span><span class="sxs-lookup"><span data-stu-id="49c86-103">Type extensions</span></span>

<span data-ttu-id="49c86-104">Extensões de tipo (também chamadas de _aumentos_) são uma família de recursos que permitem adicionar novos membros a um tipo de objeto definido anteriormente.</span><span class="sxs-lookup"><span data-stu-id="49c86-104">Type extensions (also called _augmentations_) are a family of features that let you add new members to a previously defined object type.</span></span> <span data-ttu-id="49c86-105">Os três recursos são:</span><span class="sxs-lookup"><span data-stu-id="49c86-105">The three features are:</span></span>

- <span data-ttu-id="49c86-106">Extensões de tipo intrínseco</span><span class="sxs-lookup"><span data-stu-id="49c86-106">Intrinsic type extensions</span></span>
- <span data-ttu-id="49c86-107">Extensões de tipo opcionais</span><span class="sxs-lookup"><span data-stu-id="49c86-107">Optional type extensions</span></span>
- <span data-ttu-id="49c86-108">Métodos de extensão</span><span class="sxs-lookup"><span data-stu-id="49c86-108">Extension methods</span></span>

<span data-ttu-id="49c86-109">Cada um pode ser usado em diferentes cenários e tem compensações diferentes.</span><span class="sxs-lookup"><span data-stu-id="49c86-109">Each can be used in different scenarios and has different tradeoffs.</span></span>

## <a name="syntax"></a><span data-ttu-id="49c86-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="49c86-110">Syntax</span></span>

```fsharp
// Intrinsic and optional extensions
type typename with
    member self-identifier.member-name =
        body
    ...

// Extension methods
open System.Runtime.CompilerServices

[<Extension>]
type Extensions() =
    [static] member self-identifier.extension-name (ty: typename, [args]) =
        body
    ...
```

## <a name="intrinsic-type-extensions"></a><span data-ttu-id="49c86-111">Extensões de tipo intrínseco</span><span class="sxs-lookup"><span data-stu-id="49c86-111">Intrinsic type extensions</span></span>

<span data-ttu-id="49c86-112">Uma extensão de tipo intrínseco é uma extensão de tipo que estende um tipo definido pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="49c86-112">An intrinsic type extension is a type extension that extends a user-defined type.</span></span>

<span data-ttu-id="49c86-113">As extensões de tipo intrínseco devem ser definidas no mesmo arquivo **e** no mesmo namespace ou módulo que o tipo que está sendo estendido.</span><span class="sxs-lookup"><span data-stu-id="49c86-113">Intrinsic type extensions must be defined in the same file **and** in the same namespace or module as the type they're extending.</span></span> <span data-ttu-id="49c86-114">Qualquer outra definição fará com que elas sejam [extensões de tipo opcionais](type-extensions.md#optional-type-extensions).</span><span class="sxs-lookup"><span data-stu-id="49c86-114">Any other definition will result in them being [optional type extensions](type-extensions.md#optional-type-extensions).</span></span>

<span data-ttu-id="49c86-115">As extensões de tipo intrínseco, às vezes, são uma maneira mais limpa de separar a funcionalidade da declaração de tipo.</span><span class="sxs-lookup"><span data-stu-id="49c86-115">Intrinsic type extensions are sometimes a cleaner way to separate functionality from the type declaration.</span></span> <span data-ttu-id="49c86-116">O exemplo a seguir mostra como definir uma extensão de tipo intrínseco:</span><span class="sxs-lookup"><span data-stu-id="49c86-116">The following example shows how to define an intrinsic type extension:</span></span>

```fsharp
namespace Example

type Variant =
    | Num of int
    | Str of string
  
module Variant =
    let print v =
        match v with
        | Num n -> printf "Num %d" n
        | Str s -> printf "Str %s" s

// Add a member to Variant as an extension
type Variant with
    member x.Print() = Variant.print x
```

<span data-ttu-id="49c86-117">O uso de uma extensão de tipo permite que você separe cada uma das seguintes opções:</span><span class="sxs-lookup"><span data-stu-id="49c86-117">Using a type extension allows you to separate each of the following:</span></span>

- <span data-ttu-id="49c86-118">A declaração de um tipo de `Variant`</span><span class="sxs-lookup"><span data-stu-id="49c86-118">The declaration of a `Variant` type</span></span>
- <span data-ttu-id="49c86-119">Funcionalidade para imprimir a classe `Variant` dependendo de sua "forma"</span><span class="sxs-lookup"><span data-stu-id="49c86-119">Functionality to print the `Variant` class depending on its "shape"</span></span>
- <span data-ttu-id="49c86-120">Uma maneira de acessar a funcionalidade de impressão com a `.`-Notation de estilo de objeto</span><span class="sxs-lookup"><span data-stu-id="49c86-120">A way to access the printing functionality with object-style `.`-notation</span></span>

<span data-ttu-id="49c86-121">Essa é uma alternativa à definição de tudo como um membro em `Variant`.</span><span class="sxs-lookup"><span data-stu-id="49c86-121">This is an alternative to defining everything as a member on `Variant`.</span></span> <span data-ttu-id="49c86-122">Embora não seja uma abordagem inerentemente melhor, pode ser uma representação mais limpa da funcionalidade em algumas situações.</span><span class="sxs-lookup"><span data-stu-id="49c86-122">Although it is not an inherently better approach, it can be a cleaner representation of functionality in some situations.</span></span>

<span data-ttu-id="49c86-123">As extensões de tipo intrínseco são compiladas como membros do tipo que aumentam e aparecem no tipo quando o tipo é examinado por reflexão.</span><span class="sxs-lookup"><span data-stu-id="49c86-123">Intrinsic type extensions are compiled as members of the type they augment, and appear on the type when the type is examined by reflection.</span></span>

## <a name="optional-type-extensions"></a><span data-ttu-id="49c86-124">Extensões de tipo opcionais</span><span class="sxs-lookup"><span data-stu-id="49c86-124">Optional type extensions</span></span>

<span data-ttu-id="49c86-125">Uma extensão de tipo opcional é uma extensão que aparece fora do módulo, namespace ou assembly original do tipo que está sendo estendido.</span><span class="sxs-lookup"><span data-stu-id="49c86-125">An optional type extension is an extension that appears outside the original module, namespace, or assembly of the type being extended.</span></span>

<span data-ttu-id="49c86-126">Extensões de tipo opcional são úteis para estender um tipo que você não definiu por conta própria.</span><span class="sxs-lookup"><span data-stu-id="49c86-126">Optional type extensions are useful for extending a type that you have not defined yourself.</span></span> <span data-ttu-id="49c86-127">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="49c86-127">For example:</span></span>

```fsharp
module Extensions

type IEnumerable<'T> with
    /// Repeat each element of the sequence n times
    member xs.RepeatElements(n: int) =
        seq {
            for x in xs do
                for _ in 1 .. n -> x
        }
```

<span data-ttu-id="49c86-128">Agora você pode acessar `RepeatElements` como se fosse membro de <xref:System.Collections.Generic.IEnumerable%601>, desde que o módulo `Extensions` seja aberto no escopo no qual você está trabalhando.</span><span class="sxs-lookup"><span data-stu-id="49c86-128">You can now access `RepeatElements` as if it's a member of <xref:System.Collections.Generic.IEnumerable%601> as long as the `Extensions` module is opened in the scope that you are working in.</span></span>

<span data-ttu-id="49c86-129">As extensões opcionais não aparecem no tipo estendido quando examinadas por reflexão.</span><span class="sxs-lookup"><span data-stu-id="49c86-129">Optional extensions do not appear on the extended type when examined by reflection.</span></span> <span data-ttu-id="49c86-130">As extensões opcionais devem estar em módulos e só estão no escopo quando o módulo que contém a extensão está aberto ou está no escopo.</span><span class="sxs-lookup"><span data-stu-id="49c86-130">Optional extensions must be in modules, and they're only in scope when the module that contains the extension is open or is otherwise in scope.</span></span>

<span data-ttu-id="49c86-131">Membros de extensão opcionais são compilados para membros estáticos para os quais a instância do objeto é passada implicitamente como o primeiro parâmetro.</span><span class="sxs-lookup"><span data-stu-id="49c86-131">Optional extension members are compiled to static members for which the object instance is passed implicitly as the first parameter.</span></span> <span data-ttu-id="49c86-132">No entanto, eles atuam como se fossem membros de instância ou membros estáticos de acordo com o modo como eles são declarados.</span><span class="sxs-lookup"><span data-stu-id="49c86-132">However, they act as if they're instance members or static members according to how they're declared.</span></span>

<span data-ttu-id="49c86-133">Os membros de extensão opcionais também não C# são visíveis para os consumidores do ou Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="49c86-133">Optional extension members are also not visible to C# or Visual Basic consumers.</span></span> <span data-ttu-id="49c86-134">Eles só podem ser consumidos F# em outro código.</span><span class="sxs-lookup"><span data-stu-id="49c86-134">They can only be consumed in other F# code.</span></span>

## <a name="generic-limitation-of-intrinsic-and-optional-type-extensions"></a><span data-ttu-id="49c86-135">Limitação genérica de extensões de tipo intrínsecas e opcionais</span><span class="sxs-lookup"><span data-stu-id="49c86-135">Generic limitation of intrinsic and optional type extensions</span></span>

<span data-ttu-id="49c86-136">É possível declarar uma extensão de tipo em um tipo genérico em que a variável de tipo é restrita.</span><span class="sxs-lookup"><span data-stu-id="49c86-136">It's possible to declare a type extension on a generic type where the type variable is constrained.</span></span> <span data-ttu-id="49c86-137">O requisito é que a restrição da declaração de extensão corresponda à restrição do tipo declarado.</span><span class="sxs-lookup"><span data-stu-id="49c86-137">The requirement is that the constraint of the extension declaration matches the constraint of the declared type.</span></span>

<span data-ttu-id="49c86-138">No entanto, mesmo quando as restrições são correspondidas entre um tipo declarado e uma extensão de tipo, é possível que uma restrição seja inferida pelo corpo de um membro estendido que impõe um requisito diferente no parâmetro de tipo do que o tipo declarado.</span><span class="sxs-lookup"><span data-stu-id="49c86-138">However, even when constraints are matched between a declared type and a type extension, it's possible for a constraint to be inferred by the body of an extended member that imposes a different requirement on the type parameter than the declared type.</span></span> <span data-ttu-id="49c86-139">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="49c86-139">For example:</span></span>

```fsharp
open System.Collections.Generic

// NOT POSSIBLE AND FAILS TO COMPILE!
//
// The member 'Sum' has a different requirement on 'T than the type IEnumerable<'T>
type IEnumerable<'T> with
    member this.Sum() = Seq.sum this
```

<span data-ttu-id="49c86-140">Não há como obter esse código para trabalhar com uma extensão de tipo opcional:</span><span class="sxs-lookup"><span data-stu-id="49c86-140">There is no way to get this code to work with an optional type extension:</span></span>

- <span data-ttu-id="49c86-141">Como está, o membro `Sum` tem uma restrição diferente em `'T` (`static member get_Zero` e `static member (+)`) do que a extensão de tipo define.</span><span class="sxs-lookup"><span data-stu-id="49c86-141">As is, the `Sum` member has a different constraint on `'T` (`static member get_Zero` and `static member (+)`) than what the type extension defines.</span></span>
- <span data-ttu-id="49c86-142">A modificação da extensão de tipo para ter a mesma restrição que `Sum` não corresponderá mais à restrição definida em `IEnumerable<'T>`.</span><span class="sxs-lookup"><span data-stu-id="49c86-142">Modifying the type extension to have the same constraint as `Sum` will no longer match the defined constraint on `IEnumerable<'T>`.</span></span>
- <span data-ttu-id="49c86-143">Alterar `member this.Sum` para `member inline this.Sum` dará um erro informando que as restrições de tipo são incompatíveis.</span><span class="sxs-lookup"><span data-stu-id="49c86-143">Changing `member this.Sum` to `member inline this.Sum` will give an error that type constraints are mismatched.</span></span>

<span data-ttu-id="49c86-144">O que é desejado são métodos estáticos que "flutuam no espaço" e podem ser apresentados como se estivessem estendendo um tipo.</span><span class="sxs-lookup"><span data-stu-id="49c86-144">What is desired are static methods that "float in space" and can be presented as if they're extending a type.</span></span> <span data-ttu-id="49c86-145">É aí que os métodos de extensão se tornam necessários.</span><span class="sxs-lookup"><span data-stu-id="49c86-145">This is where extension methods become necessary.</span></span>

## <a name="extension-methods"></a><span data-ttu-id="49c86-146">Métodos de extensão</span><span class="sxs-lookup"><span data-stu-id="49c86-146">Extension methods</span></span>

<span data-ttu-id="49c86-147">Por fim, os métodos de extensão (C# às vezes chamados de "membros de extensão de F# estilo") podem ser declarados em como um método de membro estático em uma classe.</span><span class="sxs-lookup"><span data-stu-id="49c86-147">Finally, extension methods (sometimes called "C# style extension members") can be declared in F# as a static member method on a class.</span></span>

<span data-ttu-id="49c86-148">Os métodos de extensão são úteis para quando você deseja definir extensões em um tipo genérico que restringirá a variável de tipo.</span><span class="sxs-lookup"><span data-stu-id="49c86-148">Extension methods are useful for when you wish to define extensions on a generic type that will constrain the type variable.</span></span> <span data-ttu-id="49c86-149">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="49c86-149">For example:</span></span>

```fsharp
namespace Extensions

open System.Runtime.CompilerServices

[<Extension>]
type IEnumerableExtensions() =
    [<Extension>]
    static member inline Sum(xs: IEnumerable<'T>) = Seq.sum xs
```

<span data-ttu-id="49c86-150">Quando usado, esse código fará com que ele apareça como se `Sum` estiver definido em <xref:System.Collections.Generic.IEnumerable%601>, desde que `Extensions` tenha sido aberto ou esteja no escopo.</span><span class="sxs-lookup"><span data-stu-id="49c86-150">When used, this code will make it appear as if `Sum` is defined on <xref:System.Collections.Generic.IEnumerable%601>, so long as `Extensions` has been opened or is in scope.</span></span>

## <a name="other-remarks"></a><span data-ttu-id="49c86-151">Outros comentários</span><span class="sxs-lookup"><span data-stu-id="49c86-151">Other remarks</span></span>

<span data-ttu-id="49c86-152">As extensões de tipo também têm os seguintes atributos:</span><span class="sxs-lookup"><span data-stu-id="49c86-152">Type extensions also have the following attributes:</span></span>

- <span data-ttu-id="49c86-153">Qualquer tipo que possa ser acessado pode ser estendido.</span><span class="sxs-lookup"><span data-stu-id="49c86-153">Any type that can be accessed can be extended.</span></span>
- <span data-ttu-id="49c86-154">Extensões intrínsecas e opcionais de tipo podem definir _qualquer_ tipo de membro, não apenas métodos.</span><span class="sxs-lookup"><span data-stu-id="49c86-154">Intrinsic and optional type extensions can define _any_ member type, not just methods.</span></span> <span data-ttu-id="49c86-155">Portanto, as propriedades de extensão também são possíveis, por exemplo.</span><span class="sxs-lookup"><span data-stu-id="49c86-155">So extension properties are also possible, for example.</span></span>
- <span data-ttu-id="49c86-156">O token `self-identifier` na [sintaxe](type-extensions.md#syntax) representa a instância do tipo que está sendo invocado, assim como os membros comuns.</span><span class="sxs-lookup"><span data-stu-id="49c86-156">The `self-identifier` token in the [syntax](type-extensions.md#syntax) represents the instance of the type being invoked, just like ordinary members.</span></span>
- <span data-ttu-id="49c86-157">Os membros estendidos podem ser membros estáticos ou de instância.</span><span class="sxs-lookup"><span data-stu-id="49c86-157">Extended members can be static or instance members.</span></span>
- <span data-ttu-id="49c86-158">Variáveis de tipo em uma extensão de tipo devem corresponder às restrições do tipo declarado.</span><span class="sxs-lookup"><span data-stu-id="49c86-158">Type variables on a type extension must match the constraints of the declared type.</span></span>

<span data-ttu-id="49c86-159">As seguintes limitações também existem para extensões de tipo:</span><span class="sxs-lookup"><span data-stu-id="49c86-159">The following limitations also exist for type extensions:</span></span>

- <span data-ttu-id="49c86-160">As extensões de tipo não dão suporte a métodos virtuais ou abstratos.</span><span class="sxs-lookup"><span data-stu-id="49c86-160">Type extensions do not support virtual or abstract methods.</span></span>
- <span data-ttu-id="49c86-161">As extensões de tipo não oferecem suporte a métodos de substituição como aumentos.</span><span class="sxs-lookup"><span data-stu-id="49c86-161">Type extensions do not support override methods as augmentations.</span></span>
- <span data-ttu-id="49c86-162">As extensões de tipo não dão suporte a [parâmetros de tipo resolvidos estaticamente](./generics/statically-resolved-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="49c86-162">Type extensions do not support [Statically Resolved Type Parameters](./generics/statically-resolved-type-parameters.md).</span></span>
- <span data-ttu-id="49c86-163">Extensões de tipo opcional não dão suporte a construtores como aumentos.</span><span class="sxs-lookup"><span data-stu-id="49c86-163">Optional Type extensions do not support constructors as augmentations.</span></span>
- <span data-ttu-id="49c86-164">Extensões de tipo não podem ser definidas em [abreviações de tipo](type-abbreviations.md).</span><span class="sxs-lookup"><span data-stu-id="49c86-164">Type extensions cannot be defined on [type abbreviations](type-abbreviations.md).</span></span>
- <span data-ttu-id="49c86-165">Extensões de tipo não são válidas para `byref<'T>` (embora possam ser declaradas).</span><span class="sxs-lookup"><span data-stu-id="49c86-165">Type extensions are not valid for `byref<'T>` (though they can be declared).</span></span>
- <span data-ttu-id="49c86-166">Extensões de tipo não são válidas para atributos (embora possam ser declaradas).</span><span class="sxs-lookup"><span data-stu-id="49c86-166">Type extensions are not valid for attributes (though they can be declared).</span></span>
- <span data-ttu-id="49c86-167">Você pode definir extensões que sobrecarregam outros métodos de mesmo nome, mas F# o compilador dá preferência a métodos que não são de extensão se houver uma chamada ambígua.</span><span class="sxs-lookup"><span data-stu-id="49c86-167">You can define extensions that overload other methods of the same name, but the F# compiler gives preference to non-extension methods if there is an ambiguous call.</span></span>

<span data-ttu-id="49c86-168">Por fim, se existirem várias extensões de tipo intrínsecos para um tipo, todos os membros deverão ser exclusivos.</span><span class="sxs-lookup"><span data-stu-id="49c86-168">Finally, if multiple intrinsic type extensions exist for one type, all members must be unique.</span></span> <span data-ttu-id="49c86-169">Para extensões de tipo opcionais, os membros em extensões de tipo diferentes para o mesmo tipo podem ter os mesmos nomes.</span><span class="sxs-lookup"><span data-stu-id="49c86-169">For optional type extensions, members in different type extensions to the same type can have the same names.</span></span> <span data-ttu-id="49c86-170">Os erros de ambiguidade ocorrem somente se o código do cliente abrir dois escopos diferentes que definem os mesmos nomes de membro.</span><span class="sxs-lookup"><span data-stu-id="49c86-170">Ambiguity errors occur only if client code opens two different scopes that define the same member names.</span></span>

## <a name="see-also"></a><span data-ttu-id="49c86-171">Veja também</span><span class="sxs-lookup"><span data-stu-id="49c86-171">See also</span></span>

- [<span data-ttu-id="49c86-172">Referência da Linguagem F#</span><span class="sxs-lookup"><span data-stu-id="49c86-172">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="49c86-173">Membros</span><span class="sxs-lookup"><span data-stu-id="49c86-173">Members</span></span>](./members/index.md)
