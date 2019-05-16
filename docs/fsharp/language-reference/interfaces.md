---
title: Interfaces
description: Saiba como F# Interfaces especificam conjuntos de membros relacionados que implementam a outras classes.
ms.date: 05/16/2016
ms.openlocfilehash: 5b57769af6c05b83b3a112635033abf4efaca772
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65645373"
---
# <a name="interfaces"></a><span data-ttu-id="70a63-103">Interfaces</span><span class="sxs-lookup"><span data-stu-id="70a63-103">Interfaces</span></span>

<span data-ttu-id="70a63-104">*Interfaces* especificar conjuntos de membros relacionados que implementam a outras classes.</span><span class="sxs-lookup"><span data-stu-id="70a63-104">*Interfaces* specify sets of related members that other classes implement.</span></span>

## <a name="syntax"></a><span data-ttu-id="70a63-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="70a63-105">Syntax</span></span>

```fsharp
// Interface declaration:
[ attributes ]
type [accessibility-modifier] interface-name =
    [ interface ]     [ inherit base-interface-name ...]
    abstract member1 : [ argument-types1 -> ] return-type1
    abstract member2 : [ argument-types2 -> ] return-type2
    ...
[ end ]

// Implementing, inside a class type definition:
interface interface-name with
    member self-identifier.member1argument-list = method-body1
    member self-identifier.member2argument-list = method-body2

// Implementing, by using an object expression:
[ attributes ]
let class-name (argument-list) =
    { new interface-name with
        member self-identifier.member1argument-list = method-body1
        member self-identifier.member2argument-list = method-body2
        [ base-interface-definitions ]
    }
    member-list
```

## <a name="remarks"></a><span data-ttu-id="70a63-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="70a63-106">Remarks</span></span>

<span data-ttu-id="70a63-107">Declarações de interface se parecer com declarações de classe, exceto que não há membros são implementados.</span><span class="sxs-lookup"><span data-stu-id="70a63-107">Interface declarations resemble class declarations except that no members are implemented.</span></span> <span data-ttu-id="70a63-108">Em vez disso, todos os membros são abstratos, conforme indicado pela palavra-chave `abstract`.</span><span class="sxs-lookup"><span data-stu-id="70a63-108">Instead, all the members are abstract, as indicated by the keyword `abstract`.</span></span> <span data-ttu-id="70a63-109">Você não fornecer um corpo de método para métodos abstratos.</span><span class="sxs-lookup"><span data-stu-id="70a63-109">You do not provide a method body for abstract methods.</span></span> <span data-ttu-id="70a63-110">No entanto, você pode fornecer uma implementação padrão, incluindo também uma definição separada do membro como um método junto com o `default` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="70a63-110">However, you can provide a default implementation by also including a separate definition of the member as a method together with the `default` keyword.</span></span> <span data-ttu-id="70a63-111">Isso é equivalente a criar um método virtual em uma classe base em outras linguagens .NET.</span><span class="sxs-lookup"><span data-stu-id="70a63-111">Doing so is equivalent to creating a virtual method in a base class in other .NET languages.</span></span> <span data-ttu-id="70a63-112">Tal método virtual pode ser substituído nas classes que implementam a interface.</span><span class="sxs-lookup"><span data-stu-id="70a63-112">Such a virtual method can be overridden in classes that implement the interface.</span></span>

<span data-ttu-id="70a63-113">A acessibilidade padrão para interfaces é `public`.</span><span class="sxs-lookup"><span data-stu-id="70a63-113">The default accessibility for interfaces is `public`.</span></span>

<span data-ttu-id="70a63-114">Você pode, opcionalmente, nomeie cada parâmetro de método normal usando o F# sintaxe:</span><span class="sxs-lookup"><span data-stu-id="70a63-114">You can optionally give each method parameter a name using normal F# syntax:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet24032.fs)]

<span data-ttu-id="70a63-115">No acima `ISprintable` exemplo, o `Print` método tem um único parâmetro do tipo `string` com o nome `format`.</span><span class="sxs-lookup"><span data-stu-id="70a63-115">In the above `ISprintable` example, the `Print` method has a single parameter of the type `string` with the name `format`.</span></span>

<span data-ttu-id="70a63-116">Há duas maneiras de implementar interfaces: usando expressões de objeto e usando tipos de classe.</span><span class="sxs-lookup"><span data-stu-id="70a63-116">There are two ways to implement interfaces: by using object expressions, and by using class types.</span></span> <span data-ttu-id="70a63-117">Em ambos os casos, a expressão de tipo ou objeto de classe fornece corpos de método para métodos abstratos da interface.</span><span class="sxs-lookup"><span data-stu-id="70a63-117">In either case, the class type or object expression provides method bodies for abstract methods of the interface.</span></span> <span data-ttu-id="70a63-118">As implementações são específicas para cada tipo que implementa a interface.</span><span class="sxs-lookup"><span data-stu-id="70a63-118">Implementations are specific to each type that implements the interface.</span></span> <span data-ttu-id="70a63-119">Portanto, os métodos de interface em tipos diferentes podem ser diferentes uns dos outros.</span><span class="sxs-lookup"><span data-stu-id="70a63-119">Therefore, interface methods on different types might be different from each other.</span></span>

<span data-ttu-id="70a63-120">As palavras-chave `interface` e `end`, que marca o início e fim da definição, são opcionais, quando você usa a sintaxe leve.</span><span class="sxs-lookup"><span data-stu-id="70a63-120">The keywords `interface` and `end`, which mark the start and end of the definition, are optional when you use lightweight syntax.</span></span> <span data-ttu-id="70a63-121">Se você não usar essas palavras-chave, o compilador tentará inferir se o tipo é uma classe ou uma interface, analisando as construções que você usa.</span><span class="sxs-lookup"><span data-stu-id="70a63-121">If you do not use these keywords, the compiler attempts to infer whether the type is a class or an interface by analyzing the constructs that you use.</span></span> <span data-ttu-id="70a63-122">Se você define um membro ou usar outra sintaxe de classe, o tipo é interpretado como uma classe.</span><span class="sxs-lookup"><span data-stu-id="70a63-122">If you define a member or use other class syntax, the type is interpreted as a class.</span></span>

<span data-ttu-id="70a63-123">O estilo de codificação do .NET deve iniciar todas as interfaces com uma letra maiuscula `I`.</span><span class="sxs-lookup"><span data-stu-id="70a63-123">The .NET coding style is to begin all interfaces with a capital `I`.</span></span>

## <a name="implementing-interfaces-by-using-class-types"></a><span data-ttu-id="70a63-124">Implementando Interfaces usando tipos de classe</span><span class="sxs-lookup"><span data-stu-id="70a63-124">Implementing Interfaces by Using Class Types</span></span>

<span data-ttu-id="70a63-125">Você pode implementar uma ou mais interfaces em um tipo de classe usando o `interface` palavra-chave, o nome da interface e o `with` palavra-chave, seguido pelas definições de membro de interface, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="70a63-125">You can implement one or more interfaces in a class type by using the `interface` keyword, the name of the interface, and the `with` keyword, followed by the interface member definitions, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2801.fs)]

<span data-ttu-id="70a63-126">Implementações de interface são herdadas, portanto a quaisquer classes derivadas não precisará reimplementá-los.</span><span class="sxs-lookup"><span data-stu-id="70a63-126">Interface implementations are inherited, so any derived classes do not need to reimplement them.</span></span>

## <a name="calling-interface-methods"></a><span data-ttu-id="70a63-127">Chamando métodos de Interface</span><span class="sxs-lookup"><span data-stu-id="70a63-127">Calling Interface Methods</span></span>

<span data-ttu-id="70a63-128">Métodos de interface podem ser chamados apenas por meio da interface, não por meio de qualquer objeto do tipo que implementa a interface.</span><span class="sxs-lookup"><span data-stu-id="70a63-128">Interface methods can be called only through the interface, not through any object of the type that implements the interface.</span></span> <span data-ttu-id="70a63-129">Portanto, talvez você precise upcast para o tipo de interface usando o `:>` operador ou o `upcast` operador para chamar esses métodos.</span><span class="sxs-lookup"><span data-stu-id="70a63-129">Thus, you might have to upcast to the interface type by using the `:>` operator or the `upcast` operator in order to call these methods.</span></span>

<span data-ttu-id="70a63-130">Para chamar o método de interface quando você tem um objeto do tipo `SomeClass`, você deve upcast o objeto para o tipo de interface, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="70a63-130">To call the interface method when you have an object of type `SomeClass`, you must upcast the object to the interface type, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2802.fs)]

<span data-ttu-id="70a63-131">Uma alternativa é declarar um método no objeto que upcasts e chama o método de interface, como no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="70a63-131">An alternative is to declare a method on the object that upcasts and calls the interface method, as in the following example.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2803.fs)]

## <a name="implementing-interfaces-by-using-object-expressions"></a><span data-ttu-id="70a63-132">Implementando Interfaces usando expressões de objeto</span><span class="sxs-lookup"><span data-stu-id="70a63-132">Implementing Interfaces by Using Object Expressions</span></span>

<span data-ttu-id="70a63-133">Expressões de objeto fornecem uma maneira curta para implementar uma interface.</span><span class="sxs-lookup"><span data-stu-id="70a63-133">Object expressions provide a short way to implement an interface.</span></span> <span data-ttu-id="70a63-134">Eles são úteis quando você não precisa criar um tipo nomeado, e você deseja apenas um objeto que dá suporte a métodos de interface, sem quaisquer métodos adicionais.</span><span class="sxs-lookup"><span data-stu-id="70a63-134">They are useful when you do not have to create a named type, and you just want an object that supports the interface methods, without any additional methods.</span></span> <span data-ttu-id="70a63-135">Uma expressão de objeto é ilustrada no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="70a63-135">An object expression is illustrated in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2804.fs)]

## <a name="interface-inheritance"></a><span data-ttu-id="70a63-136">Herança da interface</span><span class="sxs-lookup"><span data-stu-id="70a63-136">Interface Inheritance</span></span>

<span data-ttu-id="70a63-137">Interfaces podem herdar de uma ou mais interfaces base.</span><span class="sxs-lookup"><span data-stu-id="70a63-137">Interfaces can inherit from one or more base interfaces.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2805.fs)]

## <a name="see-also"></a><span data-ttu-id="70a63-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="70a63-138">See also</span></span>

- [<span data-ttu-id="70a63-139">Referência da Linguagem F#</span><span class="sxs-lookup"><span data-stu-id="70a63-139">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="70a63-140">Expressões de Objeto</span><span class="sxs-lookup"><span data-stu-id="70a63-140">Object Expressions</span></span>](object-expressions.md)
- [<span data-ttu-id="70a63-141">Classes</span><span class="sxs-lookup"><span data-stu-id="70a63-141">Classes</span></span>](classes.md)
