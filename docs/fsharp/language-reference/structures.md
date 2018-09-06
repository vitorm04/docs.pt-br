---
title: Estruturas (F#)
description: 'Saiba mais sobre a estrutura F #, um tipo de objeto compacto geralmente mais eficiente do que uma classe para tipos com uma pequena quantidade de dados e comportamento simples.'
ms.date: 05/16/2016
ms.openlocfilehash: 889d493af3c9c388bdc7969c02bc7b021b82517d
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43799665"
---
# <a name="structures"></a><span data-ttu-id="4c4a2-103">Estruturas</span><span class="sxs-lookup"><span data-stu-id="4c4a2-103">Structures</span></span>

<span data-ttu-id="4c4a2-104">Um *estrutura* é um tipo de objeto compacto que pode ser mais eficiente do que uma classe para tipos que têm uma pequena quantidade de dados e comportamento simples.</span><span class="sxs-lookup"><span data-stu-id="4c4a2-104">A *structure* is a compact object type that can be more efficient than a class for types that have a small amount of data and simple behavior.</span></span>

## <a name="syntax"></a><span data-ttu-id="4c4a2-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4c4a2-105">Syntax</span></span>

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

## <a name="remarks"></a><span data-ttu-id="4c4a2-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="4c4a2-106">Remarks</span></span>

<span data-ttu-id="4c4a2-107">Estruturas são *tipos de valor*, que significa que eles são armazenados diretamente na pilha ou, quando eles são usados como campos ou elementos de matriz, embutido no pai de tipo.</span><span class="sxs-lookup"><span data-stu-id="4c4a2-107">Structures are *value types*, which means that they are stored directly on the stack or, when they are used as fields or array elements, inline in the parent type.</span></span> <span data-ttu-id="4c4a2-108">Ao contrário de classes e registros, as estruturas têm semântica de passar-por-valor.</span><span class="sxs-lookup"><span data-stu-id="4c4a2-108">Unlike classes and records, structures have pass-by-value semantics.</span></span> <span data-ttu-id="4c4a2-109">Isso significa que elas são úteis principalmente para pequenos agregados de dados que são acessados e copiados com frequência.</span><span class="sxs-lookup"><span data-stu-id="4c4a2-109">This means that they are useful primarily for small aggregates of data that are accessed and copied frequently.</span></span>

<span data-ttu-id="4c4a2-110">Na sintaxe anterior, duas formas são mostradas.</span><span class="sxs-lookup"><span data-stu-id="4c4a2-110">In the previous syntax, two forms are shown.</span></span> <span data-ttu-id="4c4a2-111">A primeira não é a sintaxe leve, mas ela é usada com frequência, pois quando você usa as palavras-chave `struct` e `end`, é possível omitir o atributo `StructAttribute`, que aparece na segunda forma.</span><span class="sxs-lookup"><span data-stu-id="4c4a2-111">The first is not the lightweight syntax, but it is nevertheless frequently used because, when you use the `struct` and `end` keywords, you can omit the `StructAttribute` attribute, which appears in the second form.</span></span> <span data-ttu-id="4c4a2-112">É possível abreviar `StructAttribute` como apenas `Struct`.</span><span class="sxs-lookup"><span data-stu-id="4c4a2-112">You can abbreviate `StructAttribute` to just `Struct`.</span></span>

<span data-ttu-id="4c4a2-113">O *-definição-elementos-e-membros de tipo* na sintaxe anterior representa definições e declarações de membro.</span><span class="sxs-lookup"><span data-stu-id="4c4a2-113">The *type-definition-elements-and-members* in the previous syntax represents member declarations and definitions.</span></span> <span data-ttu-id="4c4a2-114">As estruturas podem ter construtores e campos mutáveis e imutáveis e podem declarar membros e implementações de interface.</span><span class="sxs-lookup"><span data-stu-id="4c4a2-114">Structures can have constructors and mutable and immutable fields, and they can declare members and interface implementations.</span></span> <span data-ttu-id="4c4a2-115">Para obter mais informações, consulte [membros](members/index.md).</span><span class="sxs-lookup"><span data-stu-id="4c4a2-115">For more information, see [Members](members/index.md).</span></span>

<span data-ttu-id="4c4a2-116">As estruturas não podem participar da herança, não podem conter associações `let` ou `do` e não podem conter recursivamente campos de seu próprio tipo (embora possam conter células de referência que fazem referência ao seu próprio tipo).</span><span class="sxs-lookup"><span data-stu-id="4c4a2-116">Structures cannot participate in inheritance, cannot contain `let` or `do` bindings, and cannot recursively contain fields of their own type (although they can contain reference cells that reference their own type).</span></span>

<span data-ttu-id="4c4a2-117">Como as estruturas não permitem associações `let`, você deve declarar campos em estruturas usando a palavra-chave `val`.</span><span class="sxs-lookup"><span data-stu-id="4c4a2-117">Because structures do not allow `let` bindings, you must declare fields in structures by using the `val` keyword.</span></span> <span data-ttu-id="4c4a2-118">A palavra-chave `val` define um campo e seu tipo, mas não permite inicialização.</span><span class="sxs-lookup"><span data-stu-id="4c4a2-118">The `val` keyword defines a field and its type but does not allow initialization.</span></span> <span data-ttu-id="4c4a2-119">Em vez disso, as declarações `val` são inicializadas como zero ou nulo.</span><span class="sxs-lookup"><span data-stu-id="4c4a2-119">Instead, `val` declarations are initialized to zero or null.</span></span> <span data-ttu-id="4c4a2-120">Por esse motivo, as estruturas que possuem um construtor implícito (ou seja, parâmetros que são fornecidos imediatamente após o nome da estrutura na declaração) requerem que declarações `val` sejam anotadas com o atributo `DefaultValue`.</span><span class="sxs-lookup"><span data-stu-id="4c4a2-120">For this reason, structures that have an implicit constructor (that is, parameters that are given immediately after the structure name in the declaration) require that `val` declarations be annotated with the `DefaultValue` attribute.</span></span> <span data-ttu-id="4c4a2-121">As estruturas que tenham um construtor definido ainda oferecem suporte à inicialização como zero.</span><span class="sxs-lookup"><span data-stu-id="4c4a2-121">Structures that have a defined constructor still support zero-initialization.</span></span> <span data-ttu-id="4c4a2-122">Portanto, o atributo `DefaultValue` é uma declaração de que um valor zero é válido para o campo.</span><span class="sxs-lookup"><span data-stu-id="4c4a2-122">Therefore, the `DefaultValue` attribute is a declaration that such a zero value is valid for the field.</span></span> <span data-ttu-id="4c4a2-123">Construtores implícitos para estruturas não executam nenhuma ação, pois as associações `let` e `do` não são permitidas no tipo, mas os valores de parâmetro construtor implícito passados estão disponíveis como campos particulares.</span><span class="sxs-lookup"><span data-stu-id="4c4a2-123">Implicit constructors for structures do not perform any actions because `let` and `do` bindings aren’t allowed on the type, but the implicit constructor parameter values passed in are available as private fields.</span></span>

<span data-ttu-id="4c4a2-124">Construtores explícitos podem envolver inicialização de valores do campo.</span><span class="sxs-lookup"><span data-stu-id="4c4a2-124">Explicit constructors might involve initialization of field values.</span></span> <span data-ttu-id="4c4a2-125">Quando você tem uma estrutura que possui um construtor explícito, ela ainda suporta inicialização como zero; no entanto, você não usa o atributo `DefaultValue` nas declarações `val`, pois ela entra em conflito com o construtor explícito.</span><span class="sxs-lookup"><span data-stu-id="4c4a2-125">When you have a structure that has an explicit constructor, it still supports zero-initialization; however, you do not use the `DefaultValue` attribute on the `val` declarations because it conflicts with the explicit constructor.</span></span> <span data-ttu-id="4c4a2-126">Para obter mais informações sobre `val` declarações, consulte [campos explícitos: A `val` palavra-chave](members/explicit-fields-the-val-keyword.md).</span><span class="sxs-lookup"><span data-stu-id="4c4a2-126">For more information about `val` declarations, see [Explicit Fields: The `val` Keyword](members/explicit-fields-the-val-keyword.md).</span></span>

<span data-ttu-id="4c4a2-127">Modificadores de atributos e de acessibilidade são permitidos em estruturas e seguem as mesmas regras dos outros tipos.</span><span class="sxs-lookup"><span data-stu-id="4c4a2-127">Attributes and accessibility modifiers are allowed on structures, and follow the same rules as those for other types.</span></span> <span data-ttu-id="4c4a2-128">Para obter mais informações, consulte [atributos](attributes.md) e [controle de acesso](access-control.md).</span><span class="sxs-lookup"><span data-stu-id="4c4a2-128">For more information, see [Attributes](attributes.md) and [Access Control](access-control.md).</span></span>

<span data-ttu-id="4c4a2-129">Os exemplos de código a seguir ilustram definições de estrutura.</span><span class="sxs-lookup"><span data-stu-id="4c4a2-129">The following code examples illustrate structure definitions.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2501.fs)]

## <a name="struct-records-and-discriminated-unions"></a><span data-ttu-id="4c4a2-130">Struct registros e uniões discriminadas</span><span class="sxs-lookup"><span data-stu-id="4c4a2-130">Struct Records and Discriminated Unions</span></span>

<span data-ttu-id="4c4a2-131">Começando com o F # 4.1, você pode representar [registros](records.md) e [uniões discriminadas](discriminated-unions.md) como structs com o `[<Struct>]` atributo.</span><span class="sxs-lookup"><span data-stu-id="4c4a2-131">Starting with F# 4.1, you can represent [Records](records.md) and [Discriminated Unions](discriminated-unions.md) as structs with the `[<Struct>]` attribute.</span></span>  <span data-ttu-id="4c4a2-132">Consulte cada artigo para saber mais.</span><span class="sxs-lookup"><span data-stu-id="4c4a2-132">See each article to learn more.</span></span>

## <a name="see-also"></a><span data-ttu-id="4c4a2-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4c4a2-133">See also</span></span>

- [<span data-ttu-id="4c4a2-134">Referência da Linguagem F#</span><span class="sxs-lookup"><span data-stu-id="4c4a2-134">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="4c4a2-135">Classes</span><span class="sxs-lookup"><span data-stu-id="4c4a2-135">Classes</span></span>](classes.md)
- [<span data-ttu-id="4c4a2-136">Registros</span><span class="sxs-lookup"><span data-stu-id="4c4a2-136">Records</span></span>](records.md)
- [<span data-ttu-id="4c4a2-137">Membros</span><span class="sxs-lookup"><span data-stu-id="4c4a2-137">Members</span></span>](members/index.md)
