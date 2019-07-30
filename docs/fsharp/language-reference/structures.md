---
title: Estruturas
description: Saiba mais sobre F# a estrutura, um tipo de objeto compacto geralmente mais eficiente do que uma classe para tipos com uma pequena quantidade de dados e comportamento simples.
ms.date: 05/16/2016
ms.openlocfilehash: e638b450fe43e0993c9980cade246c3f26d25e2d
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630766"
---
# <a name="structures"></a><span data-ttu-id="557df-103">Estruturas</span><span class="sxs-lookup"><span data-stu-id="557df-103">Structures</span></span>

<span data-ttu-id="557df-104">Uma *estrutura* é um tipo de objeto compacto que pode ser mais eficiente do que uma classe para tipos que têm uma pequena quantidade de dados e comportamento simples.</span><span class="sxs-lookup"><span data-stu-id="557df-104">A *structure* is a compact object type that can be more efficient than a class for types that have a small amount of data and simple behavior.</span></span>

## <a name="syntax"></a><span data-ttu-id="557df-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="557df-105">Syntax</span></span>

```fsharp
[ attributes ]
type [accessibility-modifier] type-name =
    struct
        type-definition-elements-and-members
    end
// or
[ attributes ]
[<StructAttribute>]
type [accessibility-modifier] type-name =
    type-definition-elements-and-members
```

## <a name="remarks"></a><span data-ttu-id="557df-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="557df-106">Remarks</span></span>

<span data-ttu-id="557df-107">Estruturas são *tipos de valor*, o que significa que elas são armazenadas diretamente na pilha ou, quando são usadas como campos ou elementos de matriz, embutidos no tipo pai.</span><span class="sxs-lookup"><span data-stu-id="557df-107">Structures are *value types*, which means that they are stored directly on the stack or, when they are used as fields or array elements, inline in the parent type.</span></span> <span data-ttu-id="557df-108">Ao contrário de classes e registros, as estruturas têm semântica de passar-por-valor.</span><span class="sxs-lookup"><span data-stu-id="557df-108">Unlike classes and records, structures have pass-by-value semantics.</span></span> <span data-ttu-id="557df-109">Isso significa que elas são úteis principalmente para pequenos agregados de dados que são acessados e copiados com frequência.</span><span class="sxs-lookup"><span data-stu-id="557df-109">This means that they are useful primarily for small aggregates of data that are accessed and copied frequently.</span></span>

<span data-ttu-id="557df-110">Na sintaxe anterior, duas formas são mostradas.</span><span class="sxs-lookup"><span data-stu-id="557df-110">In the previous syntax, two forms are shown.</span></span> <span data-ttu-id="557df-111">A primeira não é a sintaxe leve, mas ela é usada com frequência, pois quando você usa as palavras-chave `struct` e `end`, é possível omitir o atributo `StructAttribute`, que aparece na segunda forma.</span><span class="sxs-lookup"><span data-stu-id="557df-111">The first is not the lightweight syntax, but it is nevertheless frequently used because, when you use the `struct` and `end` keywords, you can omit the `StructAttribute` attribute, which appears in the second form.</span></span> <span data-ttu-id="557df-112">É possível abreviar `StructAttribute` como apenas `Struct`.</span><span class="sxs-lookup"><span data-stu-id="557df-112">You can abbreviate `StructAttribute` to just `Struct`.</span></span>

<span data-ttu-id="557df-113">Os *elementos Type-Definition-Elements-and-Members* na sintaxe anterior representam definições e declarações de membros.</span><span class="sxs-lookup"><span data-stu-id="557df-113">The *type-definition-elements-and-members* in the previous syntax represents member declarations and definitions.</span></span> <span data-ttu-id="557df-114">As estruturas podem ter construtores e campos mutáveis e imutáveis e podem declarar membros e implementações de interface.</span><span class="sxs-lookup"><span data-stu-id="557df-114">Structures can have constructors and mutable and immutable fields, and they can declare members and interface implementations.</span></span> <span data-ttu-id="557df-115">Para obter mais informações, consulte [Membros](./members/index.md).</span><span class="sxs-lookup"><span data-stu-id="557df-115">For more information, see [Members](./members/index.md).</span></span>

<span data-ttu-id="557df-116">As estruturas não podem participar da herança, não podem conter associações `let` ou `do` e não podem conter recursivamente campos de seu próprio tipo (embora possam conter células de referência que fazem referência ao seu próprio tipo).</span><span class="sxs-lookup"><span data-stu-id="557df-116">Structures cannot participate in inheritance, cannot contain `let` or `do` bindings, and cannot recursively contain fields of their own type (although they can contain reference cells that reference their own type).</span></span>

<span data-ttu-id="557df-117">Como as estruturas não permitem associações `let`, você deve declarar campos em estruturas usando a palavra-chave `val`.</span><span class="sxs-lookup"><span data-stu-id="557df-117">Because structures do not allow `let` bindings, you must declare fields in structures by using the `val` keyword.</span></span> <span data-ttu-id="557df-118">A palavra-chave `val` define um campo e seu tipo, mas não permite inicialização.</span><span class="sxs-lookup"><span data-stu-id="557df-118">The `val` keyword defines a field and its type but does not allow initialization.</span></span> <span data-ttu-id="557df-119">Em vez disso, as declarações `val` são inicializadas como zero ou nulo.</span><span class="sxs-lookup"><span data-stu-id="557df-119">Instead, `val` declarations are initialized to zero or null.</span></span> <span data-ttu-id="557df-120">Por esse motivo, as estruturas que possuem um construtor implícito (ou seja, parâmetros que são fornecidos imediatamente após o nome da estrutura na declaração) requerem que declarações `val` sejam anotadas com o atributo `DefaultValue`.</span><span class="sxs-lookup"><span data-stu-id="557df-120">For this reason, structures that have an implicit constructor (that is, parameters that are given immediately after the structure name in the declaration) require that `val` declarations be annotated with the `DefaultValue` attribute.</span></span> <span data-ttu-id="557df-121">As estruturas que tenham um construtor definido ainda oferecem suporte à inicialização como zero.</span><span class="sxs-lookup"><span data-stu-id="557df-121">Structures that have a defined constructor still support zero-initialization.</span></span> <span data-ttu-id="557df-122">Portanto, o atributo `DefaultValue` é uma declaração de que um valor zero é válido para o campo.</span><span class="sxs-lookup"><span data-stu-id="557df-122">Therefore, the `DefaultValue` attribute is a declaration that such a zero value is valid for the field.</span></span> <span data-ttu-id="557df-123">Construtores implícitos para estruturas não executam nenhuma ação, pois as associações `let` e `do` não são permitidas no tipo, mas os valores de parâmetro construtor implícito passados estão disponíveis como campos particulares.</span><span class="sxs-lookup"><span data-stu-id="557df-123">Implicit constructors for structures do not perform any actions because `let` and `do` bindings aren’t allowed on the type, but the implicit constructor parameter values passed in are available as private fields.</span></span>

<span data-ttu-id="557df-124">Construtores explícitos podem envolver inicialização de valores do campo.</span><span class="sxs-lookup"><span data-stu-id="557df-124">Explicit constructors might involve initialization of field values.</span></span> <span data-ttu-id="557df-125">Quando você tem uma estrutura que possui um construtor explícito, ela ainda suporta inicialização como zero; no entanto, você não usa o atributo `DefaultValue` nas declarações `val`, pois ela entra em conflito com o construtor explícito.</span><span class="sxs-lookup"><span data-stu-id="557df-125">When you have a structure that has an explicit constructor, it still supports zero-initialization; however, you do not use the `DefaultValue` attribute on the `val` declarations because it conflicts with the explicit constructor.</span></span> <span data-ttu-id="557df-126">Para obter mais informações `val` sobre declarações, [consulte campos explícitos: A `val` palavra](./members/explicit-fields-the-val-keyword.md)-chave.</span><span class="sxs-lookup"><span data-stu-id="557df-126">For more information about `val` declarations, see [Explicit Fields: The `val` Keyword](./members/explicit-fields-the-val-keyword.md).</span></span>

<span data-ttu-id="557df-127">Modificadores de atributos e de acessibilidade são permitidos em estruturas e seguem as mesmas regras dos outros tipos.</span><span class="sxs-lookup"><span data-stu-id="557df-127">Attributes and accessibility modifiers are allowed on structures, and follow the same rules as those for other types.</span></span> <span data-ttu-id="557df-128">Para obter mais informações, consulte [atributos](attributes.md) e [controle de acesso](access-control.md).</span><span class="sxs-lookup"><span data-stu-id="557df-128">For more information, see [Attributes](attributes.md) and [Access Control](access-control.md).</span></span>

<span data-ttu-id="557df-129">Os exemplos de código a seguir ilustram definições de estrutura.</span><span class="sxs-lookup"><span data-stu-id="557df-129">The following code examples illustrate structure definitions.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2501.fs)]

## <a name="byreflike-structs"></a><span data-ttu-id="557df-130">ByRefLike structs</span><span class="sxs-lookup"><span data-stu-id="557df-130">ByRefLike structs</span></span>

<span data-ttu-id="557df-131">Você pode definir suas próprias estruturas que podem aderir a `byref`semânticas semelhantes: consulte [byrefs](byrefs.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="557df-131">You can define your own structs that can adhere to `byref`-like semantics: see [Byrefs](byrefs.md) for more information.</span></span> <span data-ttu-id="557df-132">Isso é feito com o <xref:System.Runtime.CompilerServices.IsByRefLikeAttribute> atributo:</span><span class="sxs-lookup"><span data-stu-id="557df-132">This is done with the <xref:System.Runtime.CompilerServices.IsByRefLikeAttribute> attribute:</span></span>

```fsharp
open System
open System.Runtime.CompilerServices

[<IsByRefLike; Struct>]
type S(count1: Span<int>, count2: Span<int>) =
    member x.Count1 = count1
    member x.Count2 = count2
```

<span data-ttu-id="557df-133">`IsByRefLike`Não implica `Struct`.</span><span class="sxs-lookup"><span data-stu-id="557df-133">`IsByRefLike` does not imply `Struct`.</span></span> <span data-ttu-id="557df-134">Ambos devem estar presentes no tipo.</span><span class="sxs-lookup"><span data-stu-id="557df-134">Both must be present on the type.</span></span>

<span data-ttu-id="557df-135">Um struct`byref`"-Like" no F# é um tipo de valor de associação de pilha.</span><span class="sxs-lookup"><span data-stu-id="557df-135">A "`byref`-like" struct in F# is a stack-bound value type.</span></span> <span data-ttu-id="557df-136">Ele nunca é alocado no heap gerenciado.</span><span class="sxs-lookup"><span data-stu-id="557df-136">It is never allocated on the managed heap.</span></span> <span data-ttu-id="557df-137">Um `byref`struct semelhante é útil para programação de alto desempenho, pois é imposta com o conjunto de verificações fortes sobre o tempo de vida e a não captura.</span><span class="sxs-lookup"><span data-stu-id="557df-137">A `byref`-like struct is useful for high-performance programming, as it is enforced with set of strong checks about lifetime and non-capture.</span></span> <span data-ttu-id="557df-138">As regras são:</span><span class="sxs-lookup"><span data-stu-id="557df-138">The rules are:</span></span>

* <span data-ttu-id="557df-139">Eles podem ser usados como parâmetros de função, parâmetros de método, variáveis locais, método retorna.</span><span class="sxs-lookup"><span data-stu-id="557df-139">They can be used as function parameters, method parameters, local variables, method returns.</span></span>
* <span data-ttu-id="557df-140">Eles não podem ser membros estáticos ou de instância de uma classe ou estrutura normal.</span><span class="sxs-lookup"><span data-stu-id="557df-140">They cannot be static or instance members of a class or normal struct.</span></span>
* <span data-ttu-id="557df-141">Eles não podem ser capturados por nenhuma construção`async` de fechamento (métodos ou expressões lambda).</span><span class="sxs-lookup"><span data-stu-id="557df-141">They cannot be captured by any closure construct (`async` methods or lambda expressions).</span></span>
* <span data-ttu-id="557df-142">Eles não podem ser usados como um parâmetro genérico.</span><span class="sxs-lookup"><span data-stu-id="557df-142">They cannot be used as a generic parameter.</span></span>

<span data-ttu-id="557df-143">Embora essas regras restrinjam muito o uso, elas fazem isso para atender à promessa de computação de alto desempenho de maneira segura.</span><span class="sxs-lookup"><span data-stu-id="557df-143">Although these rules very strongly restrict usage, they do so to fulfill the promise of high-performance computing in a safe manner.</span></span>

## <a name="readonly-structs"></a><span data-ttu-id="557df-144">Structs ReadOnly</span><span class="sxs-lookup"><span data-stu-id="557df-144">ReadOnly structs</span></span>

<span data-ttu-id="557df-145">Você pode anotar structs com o <xref:System.Runtime.CompilerServices.IsReadOnlyAttribute> atributo.</span><span class="sxs-lookup"><span data-stu-id="557df-145">You can annotate structs with the <xref:System.Runtime.CompilerServices.IsReadOnlyAttribute> attribute.</span></span> <span data-ttu-id="557df-146">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="557df-146">For example:</span></span>

```fsharp
[<IsReadOnly; Struct>]
type S(count1: int, count2: int) =
    member x.Count1 = count1
    member x.Count2 = count2
```

<span data-ttu-id="557df-147">`IsReadOnly`Não implica `Struct`.</span><span class="sxs-lookup"><span data-stu-id="557df-147">`IsReadOnly` does not imply `Struct`.</span></span> <span data-ttu-id="557df-148">Você deve adicionar ambos para ter uma `IsReadOnly` struct.</span><span class="sxs-lookup"><span data-stu-id="557df-148">You must add both to have an `IsReadOnly` struct.</span></span>

<span data-ttu-id="557df-149">O uso desse atributo emite metadados que permitem F# e C# sabem que o tratam `inref<'T>` como `in ref`e, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="557df-149">Use of this attribute emits metadata letting F# and C# know to treat it as `inref<'T>` and `in ref`, respectively.</span></span>

<span data-ttu-id="557df-150">A definição de um valor mutável dentro de uma struct ReadOnly produz um erro.</span><span class="sxs-lookup"><span data-stu-id="557df-150">Defining a mutable value inside of a readonly struct produces an error.</span></span>

## <a name="struct-records-and-discriminated-unions"></a><span data-ttu-id="557df-151">Registros de struct e uniões discriminadas</span><span class="sxs-lookup"><span data-stu-id="557df-151">Struct Records and Discriminated Unions</span></span>

<span data-ttu-id="557df-152">Você pode representar [registros](records.md) e [uniões discriminadas](discriminated-unions.md) como structs com o `[<Struct>]` atributo.</span><span class="sxs-lookup"><span data-stu-id="557df-152">You can represent [Records](records.md) and [Discriminated Unions](discriminated-unions.md) as structs with the `[<Struct>]` attribute.</span></span>  <span data-ttu-id="557df-153">Consulte cada artigo para saber mais.</span><span class="sxs-lookup"><span data-stu-id="557df-153">See each article to learn more.</span></span>

## <a name="see-also"></a><span data-ttu-id="557df-154">Consulte também</span><span class="sxs-lookup"><span data-stu-id="557df-154">See also</span></span>

- [<span data-ttu-id="557df-155">Referência da Linguagem F#</span><span class="sxs-lookup"><span data-stu-id="557df-155">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="557df-156">Classes</span><span class="sxs-lookup"><span data-stu-id="557df-156">Classes</span></span>](classes.md)
- [<span data-ttu-id="557df-157">Registros</span><span class="sxs-lookup"><span data-stu-id="557df-157">Records</span></span>](records.md)
- [<span data-ttu-id="557df-158">Membros</span><span class="sxs-lookup"><span data-stu-id="557df-158">Members</span></span>](./members/index.md)
