---
title: Extensões de tipo (F#)
description: 'Saiba como o F #, extensões de tipo permitem que você adicionar novos membros a um tipo de objeto definido anteriormente.'
ms.date: 07/20/2018
ms.openlocfilehash: 27238db1fd0803f62c32755fbc4ab7688f5c107e
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43874973"
---
# <a name="type-extensions"></a><span data-ttu-id="48993-103">Extensões de tipo</span><span class="sxs-lookup"><span data-stu-id="48993-103">Type extensions</span></span>

<span data-ttu-id="48993-104">As extensões de tipo (também chamado de _acréscimos_) são uma família de recursos que permitem que você adicione novos membros a um tipo de objeto definido anteriormente.</span><span class="sxs-lookup"><span data-stu-id="48993-104">Type extensions (also called _augmentations_) are a family of features that let you add new members to a previously defined object type.</span></span> <span data-ttu-id="48993-105">Os três recursos são:</span><span class="sxs-lookup"><span data-stu-id="48993-105">The three features are:</span></span>

* <span data-ttu-id="48993-106">Extensões de tipo intrínseco</span><span class="sxs-lookup"><span data-stu-id="48993-106">Intrinsic type extensions</span></span>
* <span data-ttu-id="48993-107">Extensões de tipo opcional</span><span class="sxs-lookup"><span data-stu-id="48993-107">Optional type extensions</span></span>
* <span data-ttu-id="48993-108">Métodos de extensão</span><span class="sxs-lookup"><span data-stu-id="48993-108">Extension methods</span></span>

<span data-ttu-id="48993-109">Cada um pode ser usada em cenários diferentes e tem diferentes vantagens e desvantagens.</span><span class="sxs-lookup"><span data-stu-id="48993-109">Each can be used in different scenarios and has different tradeoffs.</span></span>

## <a name="syntax"></a><span data-ttu-id="48993-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="48993-110">Syntax</span></span>

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

## <a name="intrinsic-type-extensions"></a><span data-ttu-id="48993-111">Extensões de tipo intrínseco</span><span class="sxs-lookup"><span data-stu-id="48993-111">Intrinsic type extensions</span></span>

<span data-ttu-id="48993-112">Uma extensão de tipo intrínseco é uma extensão de tipo que estende um tipo definido pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="48993-112">An intrinsic type extension is a type extension that extends a user-defined type.</span></span>

<span data-ttu-id="48993-113">Extensões intrínsecas de tipo devem ser definidas no mesmo arquivo **e** no mesmo namespace ou módulo, como o tipo que estão estendendo.</span><span class="sxs-lookup"><span data-stu-id="48993-113">Intrinsic type extensions must be defined in the same file **and** in the same namespace or module as the type they're extending.</span></span> <span data-ttu-id="48993-114">Qualquer outra definição resultará no que está sendo [extensões de tipo opcional](type-extensions.md#optional-type-extensions).</span><span class="sxs-lookup"><span data-stu-id="48993-114">Any other definition will result in them being [optional type extensions](type-extensions.md#optional-type-extensions).</span></span>

<span data-ttu-id="48993-115">Extensões de tipo intrínseco, às vezes, são uma maneira mais limpa para separar a funcionalidade da declaração de tipo.</span><span class="sxs-lookup"><span data-stu-id="48993-115">Intrinsic type extensions are sometimes a cleaner way to separate functionality from the type declaration.</span></span> <span data-ttu-id="48993-116">O exemplo a seguir mostra como definir uma extensão de tipo intrínseco:</span><span class="sxs-lookup"><span data-stu-id="48993-116">The following example shows how to define an intrinsic type extension:</span></span>

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

<span data-ttu-id="48993-117">Usar uma extensão de tipo permite que você separe cada um dos seguintes:</span><span class="sxs-lookup"><span data-stu-id="48993-117">Using a type extension allows you to separate each of the following:</span></span>

* <span data-ttu-id="48993-118">A declaração de um `Variant` tipo</span><span class="sxs-lookup"><span data-stu-id="48993-118">The declaration of a `Variant` type</span></span>
* <span data-ttu-id="48993-119">A funcionalidade para imprimir o `Variant` classe dependendo de sua "forma"</span><span class="sxs-lookup"><span data-stu-id="48993-119">Functionality to print the `Variant` class depending on its "shape"</span></span>
* <span data-ttu-id="48993-120">Uma maneira de acessar a funcionalidade de impressão com estilo de objeto `.`-notação</span><span class="sxs-lookup"><span data-stu-id="48993-120">A way to access the printing functionality with object-style `.`-notation</span></span>

<span data-ttu-id="48993-121">Essa é uma alternativa para definir tudo como um membro em `Variant`.</span><span class="sxs-lookup"><span data-stu-id="48993-121">This is an alternative to defining everything as a member on `Variant`.</span></span> <span data-ttu-id="48993-122">Embora não seja uma abordagem melhor inerentemente, ele pode ser uma representação mais clara de funcionalidade em algumas situações.</span><span class="sxs-lookup"><span data-stu-id="48993-122">Although it is not an inherently better approach, it can be a cleaner representation of functionality in some situations.</span></span>

<span data-ttu-id="48993-123">Extensões de tipo intrínseco são compiladas como membros do tipo eles aumentam e aparecem no tipo quando o tipo é examinado por reflexão.</span><span class="sxs-lookup"><span data-stu-id="48993-123">Intrinsic type extensions are compiled as members of the type they augment, and appear on the type when the type is examined by reflection.</span></span>

## <a name="optional-type-extensions"></a><span data-ttu-id="48993-124">Extensões de tipo opcional</span><span class="sxs-lookup"><span data-stu-id="48993-124">Optional type extensions</span></span>

<span data-ttu-id="48993-125">Uma extensão de tipo opcional é uma extensão que aparece fora do módulo, namespace ou assembly do tipo que está sendo estendido original.</span><span class="sxs-lookup"><span data-stu-id="48993-125">An optional type extension is an extension that appears outside the original module, namespace, or assembly of the type being extended.</span></span>

<span data-ttu-id="48993-126">Extensões de tipo opcionais são úteis para estender um tipo que você não definiu por conta própria.</span><span class="sxs-lookup"><span data-stu-id="48993-126">Optional type extensions are useful for extending a type that you have not defined yourself.</span></span> <span data-ttu-id="48993-127">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="48993-127">For example:</span></span>

```fsharp
module Extensions

open System.Collections.Generic

type IEnumerable<'T> with
    /// Repeat each element of the sequence n times
    member xs.RepeatElements(n: int) =
        seq {
            for x in xs do
                for i in 1 .. n do
                    yield x
        }
```

<span data-ttu-id="48993-128">Agora você pode acessar `RepeatElements` como se fosse um membro do <xref:System.Collections.Generic.IEnumerable%601> desde que o `Extensions` módulo é aberto no escopo que você está trabalhando no.</span><span class="sxs-lookup"><span data-stu-id="48993-128">You can now access `RepeatElements` as if it's a member of <xref:System.Collections.Generic.IEnumerable%601> as long as the `Extensions` module is opened in the scope that you are working in.</span></span>

<span data-ttu-id="48993-129">As extensões opcionais não aparecem no tipo estendido quando examinado por reflexão.</span><span class="sxs-lookup"><span data-stu-id="48993-129">Optional extensions do not appear on the extended type when examined by reflection.</span></span> <span data-ttu-id="48993-130">As extensões opcionais devem estar em módulos, e eles são somente no escopo quando o módulo que contém a extensão está aberto ou caso contrário, está no escopo.</span><span class="sxs-lookup"><span data-stu-id="48993-130">Optional extensions must be in modules, and they're only in scope when the module that contains the extension is open or is otherwise in scope.</span></span>

<span data-ttu-id="48993-131">Membros opcionais de extensão são compilados a membros estáticos para o qual a instância do objeto é transmitida implicitamente como primeiro parâmetro.</span><span class="sxs-lookup"><span data-stu-id="48993-131">Optional extension members are compiled to static members for which the object instance is passed implicitly as the first parameter.</span></span> <span data-ttu-id="48993-132">No entanto, eles atuam como se fossem membros de instância ou os membros estáticos de acordo com como elas são declaradas.</span><span class="sxs-lookup"><span data-stu-id="48993-132">However, they act as if they're instance members or static members according to how they're declared.</span></span>

## <a name="generic-limitation-of-intrinsic-and-optional-type-extensions"></a><span data-ttu-id="48993-133">Limitação genérica de extensões de tipo intrínseco e opcionais</span><span class="sxs-lookup"><span data-stu-id="48993-133">Generic limitation of intrinsic and optional type extensions</span></span>

<span data-ttu-id="48993-134">É possível declarar uma extensão de tipo em um tipo genérico, em que a variável de tipo é restrito.</span><span class="sxs-lookup"><span data-stu-id="48993-134">It's possible to declare a type extension on a generic type where the type variable is constrained.</span></span> <span data-ttu-id="48993-135">O requisito é que a restrição da declaração de extensão corresponde à restrição do tipo declarado.</span><span class="sxs-lookup"><span data-stu-id="48993-135">The requirement is that the constraint of the extension declaration matches the constraint of the declared type.</span></span>

<span data-ttu-id="48993-136">No entanto, mesmo quando as restrições são compatíveis entre um tipo de declaração e uma extensão de tipo, é possível para uma restrição ser inferido pelo corpo de um membro estendido que impõe um requisito diferente no parâmetro de tipo que o tipo declarado.</span><span class="sxs-lookup"><span data-stu-id="48993-136">However, even when constraints are matched between a declared type and a type extension, it's possible for a constraint to be inferred by the body of an extended member that imposes a different requirement on the type parameter than the declared type.</span></span> <span data-ttu-id="48993-137">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="48993-137">For example:</span></span>

```fsharp
open System.Collections.Generic

// NOT POSSIBLE AND FAILS TO COMPILE!
//
// The member 'Sum' has a different requirement on 'T than the type IEnumerable<'T>
type IEnumerable<'T> with
    member this.Sum() = Seq.sum this
```

<span data-ttu-id="48993-138">Não há nenhuma maneira de obter esse código funcione com uma extensão de tipo opcionais:</span><span class="sxs-lookup"><span data-stu-id="48993-138">There is no way to get this code to work with an optional type extension:</span></span>

* <span data-ttu-id="48993-139">Como é, o `Sum` membro tem uma restrição diferente no `'T` (`static member get_Zero` e `static member (+)`) que o que define a extensão de tipo.</span><span class="sxs-lookup"><span data-stu-id="48993-139">As is, the `Sum` member has a different constraint on `'T` (`static member get_Zero` and `static member (+)`) than what the type extension defines.</span></span>
* <span data-ttu-id="48993-140">Modificando a extensão de tipo para ter a mesma restrição como `Sum` não será mais correspondente a restrição definida na `IEnumerable<'T>`.</span><span class="sxs-lookup"><span data-stu-id="48993-140">Modifying the type extension to have the same constraint as `Sum` will no longer match the defined constraint on `IEnumerable<'T>`.</span></span>
* <span data-ttu-id="48993-141">Fazer a alteração de membro a ser `member inline Sum` fornecerão um erro que restrições de tipo são incompatíveis</span><span class="sxs-lookup"><span data-stu-id="48993-141">Making changing the member to `member inline Sum` will give an error that type constraints are mismatched</span></span>

<span data-ttu-id="48993-142">O que é desejado são métodos estáticos que "flutuem no espaço de" e podem ser apresentados como se eles estiverem estendendo um tipo.</span><span class="sxs-lookup"><span data-stu-id="48993-142">What is desired are static methods that "float in space" and can be presented as if they're extending a type.</span></span> <span data-ttu-id="48993-143">Isso é onde os métodos de extensão tornam-se necessário.</span><span class="sxs-lookup"><span data-stu-id="48993-143">This is where extension methods become necessary.</span></span>

## <a name="extension-methods"></a><span data-ttu-id="48993-144">Métodos de extensão</span><span class="sxs-lookup"><span data-stu-id="48993-144">Extension methods</span></span>

<span data-ttu-id="48993-145">Por fim, os métodos de extensão (às vezes chamados de "membros de extensão do estilo C#") podem ser declarados em F # como um método de membro estático em uma classe.</span><span class="sxs-lookup"><span data-stu-id="48993-145">Finally, extension methods (sometimes called "C# style extension members") can be declared in F# as a static member method on a class.</span></span>

<span data-ttu-id="48993-146">Métodos de extensão são úteis para quando você deseja definir as extensões em um tipo genérico que restringe a variável de tipo.</span><span class="sxs-lookup"><span data-stu-id="48993-146">Extension methods are useful for when you wish to define extensions on a generic type that will constrain the type variable.</span></span> <span data-ttu-id="48993-147">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="48993-147">For example:</span></span>

```fsharp
namespace Extensions

open System.Runtime.CompilerServices

[<Extension>]
type IEnumerableExtensions() =
    [<Extension>]
    static member inline Sum(xs: IEnumerable<'T>) = Seq.sum xs
```

<span data-ttu-id="48993-148">Quando usado, esse código irá fazer com que pareça como se `Sum` é definido em <xref:System.Collections.Generic.IEnumerable%601>, desde que os `Extensions` foi aberto ou está no escopo.</span><span class="sxs-lookup"><span data-stu-id="48993-148">When used, this code will make it appear as if `Sum` is defined on <xref:System.Collections.Generic.IEnumerable%601>, so long as `Extensions` has been opened or is in scope.</span></span>

## <a name="other-remarks"></a><span data-ttu-id="48993-149">Outros comentários</span><span class="sxs-lookup"><span data-stu-id="48993-149">Other remarks</span></span>

<span data-ttu-id="48993-150">Extensões de tipo também tem os seguintes atributos:</span><span class="sxs-lookup"><span data-stu-id="48993-150">Type extensions also have the following attributes:</span></span>

* <span data-ttu-id="48993-151">Pode ser estendido a qualquer tipo que pode ser acessado.</span><span class="sxs-lookup"><span data-stu-id="48993-151">Any type that can be accessed can be extended.</span></span>
* <span data-ttu-id="48993-152">Extensões de tipo intrínseco e opcional podem definir _qualquer_ tipo de membro, não apenas métodos.</span><span class="sxs-lookup"><span data-stu-id="48993-152">Intrinsic and optional type extensions can define _any_ member type, not just methods.</span></span> <span data-ttu-id="48993-153">Portanto, as propriedades de extensão também são possíveis, por exemplo.</span><span class="sxs-lookup"><span data-stu-id="48993-153">So extension properties are also possible, for example.</span></span>
* <span data-ttu-id="48993-154">O `self-identifier` token em de [sintaxe](type-extensions.md#syntax) representa a instância do tipo que está sendo invocado, assim como os membros comuns.</span><span class="sxs-lookup"><span data-stu-id="48993-154">The `self-identifier` token in the [syntax](type-extensions.md#syntax) represents the instance of the type being invoked, just like ordinary members.</span></span>
* <span data-ttu-id="48993-155">Membros estendidos podem ser estáticos ou membros de instância.</span><span class="sxs-lookup"><span data-stu-id="48993-155">Extended members can be static or instance members.</span></span>
* <span data-ttu-id="48993-156">Variáveis de tipo em uma extensão de tipo devem corresponder as restrições do tipo declarado.</span><span class="sxs-lookup"><span data-stu-id="48993-156">Type variables on a type extension must match the constraints of the declared type.</span></span>

<span data-ttu-id="48993-157">Também existem as seguintes limitações para extensões de tipo:</span><span class="sxs-lookup"><span data-stu-id="48993-157">The following limitations also exist for type extensions:</span></span>

* <span data-ttu-id="48993-158">Extensões de tipo não têm suporte para métodos virtuais ou abstratos.</span><span class="sxs-lookup"><span data-stu-id="48993-158">Type extensions do not support virtual or abstract methods.</span></span>
* <span data-ttu-id="48993-159">Extensões de tipo não dão suporte a métodos de substituição como acréscimos.</span><span class="sxs-lookup"><span data-stu-id="48993-159">Type extensions do not support override methods as augmentations.</span></span>
* <span data-ttu-id="48993-160">Extensões de tipo não têm suporte [estaticamente parâmetros de tipo resolvidos](generics/statically-resolved-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="48993-160">Type extensions do not support [Statically Resolved Type Parameters](generics/statically-resolved-type-parameters.md).</span></span>
* <span data-ttu-id="48993-161">As extensões de tipo opcionais não têm suporte para construtores como acréscimos.</span><span class="sxs-lookup"><span data-stu-id="48993-161">Optional Type extensions do not support constructors as augmentations.</span></span>
* <span data-ttu-id="48993-162">Extensões de tipo não podem ser definidas [abreviações de tipo](type-abbreviations.md).</span><span class="sxs-lookup"><span data-stu-id="48993-162">Type extensions cannot be defined on [type abbreviations](type-abbreviations.md).</span></span>
* <span data-ttu-id="48993-163">Extensões de tipo não são válidas para `byref<'T>` (embora eles podem ser declarados).</span><span class="sxs-lookup"><span data-stu-id="48993-163">Type extensions are not valid for `byref<'T>` (though they can be declared).</span></span>
* <span data-ttu-id="48993-164">Extensões de tipo não são válidas para os atributos (embora eles podem ser declarados).</span><span class="sxs-lookup"><span data-stu-id="48993-164">Type extensions are not valid for attributes (though they can be declared).</span></span>
* <span data-ttu-id="48993-165">Você pode definir as extensões que sobrecarregam outros métodos de mesmo nome, mas o compilador F # dá preferência a métodos sem extensão se não houver uma chamada ambígua.</span><span class="sxs-lookup"><span data-stu-id="48993-165">You can define extensions that overload other methods of the same name, but the F# compiler gives preference to non-extension methods if there is an ambiguous call.</span></span>

<span data-ttu-id="48993-166">Por fim, se existirem várias extensões de tipo intrínseco para um tipo, todos os membros devem ser exclusivos.</span><span class="sxs-lookup"><span data-stu-id="48993-166">Finally, if multiple intrinsic type extensions exist for one type, all members must be unique.</span></span> <span data-ttu-id="48993-167">Para extensões de tipo opcionais, membros em diferentes extensões de tipo para o mesmo tipo podem ter os mesmos nomes.</span><span class="sxs-lookup"><span data-stu-id="48993-167">For optional type extensions, members in different type extensions to the same type can have the same names.</span></span> <span data-ttu-id="48993-168">Erros de ambiguidade surgem somente se o código do cliente abrir dois escopos diferentes que definem os mesmos nomes de membro.</span><span class="sxs-lookup"><span data-stu-id="48993-168">Ambiguity errors occur only if client code opens two different scopes that define the same member names.</span></span>

## <a name="see-also"></a><span data-ttu-id="48993-169">Consulte também</span><span class="sxs-lookup"><span data-stu-id="48993-169">See also</span></span>

- [<span data-ttu-id="48993-170">Referência da Linguagem F#</span><span class="sxs-lookup"><span data-stu-id="48993-170">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="48993-171">Membros</span><span class="sxs-lookup"><span data-stu-id="48993-171">Members</span></span>](members/index.md)
