---
title: Interfaces
description: Saiba como F# as interfaces especificam conjuntos de membros relacionados que outras classes implementam.
ms.date: 05/16/2016
ms.openlocfilehash: 8f054a668ad0fbc2453a45883e8052471280eca3
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627655"
---
# <a name="interfaces"></a><span data-ttu-id="9bebb-103">Interfaces</span><span class="sxs-lookup"><span data-stu-id="9bebb-103">Interfaces</span></span>

<span data-ttu-id="9bebb-104">*Interfaces* especificam conjuntos de membros relacionados que outras classes implementam.</span><span class="sxs-lookup"><span data-stu-id="9bebb-104">*Interfaces* specify sets of related members that other classes implement.</span></span>

## <a name="syntax"></a><span data-ttu-id="9bebb-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9bebb-105">Syntax</span></span>

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

## <a name="remarks"></a><span data-ttu-id="9bebb-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="9bebb-106">Remarks</span></span>

<span data-ttu-id="9bebb-107">Declarações de interface assemelham-se a declarações de classe, exceto que nenhum membro é implementado.</span><span class="sxs-lookup"><span data-stu-id="9bebb-107">Interface declarations resemble class declarations except that no members are implemented.</span></span> <span data-ttu-id="9bebb-108">Em vez disso, todos os membros são abstratos, conforme indicado `abstract`pela palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="9bebb-108">Instead, all the members are abstract, as indicated by the keyword `abstract`.</span></span> <span data-ttu-id="9bebb-109">Você não fornece um corpo de método para métodos abstratos.</span><span class="sxs-lookup"><span data-stu-id="9bebb-109">You do not provide a method body for abstract methods.</span></span> <span data-ttu-id="9bebb-110">No entanto, você pode fornecer uma implementação padrão, incluindo também uma definição separada do membro como um método junto com `default` a palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="9bebb-110">However, you can provide a default implementation by also including a separate definition of the member as a method together with the `default` keyword.</span></span> <span data-ttu-id="9bebb-111">Isso é equivalente a criar um método virtual em uma classe base em outras linguagens .NET.</span><span class="sxs-lookup"><span data-stu-id="9bebb-111">Doing so is equivalent to creating a virtual method in a base class in other .NET languages.</span></span> <span data-ttu-id="9bebb-112">Tal método virtual pode ser substituído em classes que implementam a interface.</span><span class="sxs-lookup"><span data-stu-id="9bebb-112">Such a virtual method can be overridden in classes that implement the interface.</span></span>

<span data-ttu-id="9bebb-113">A acessibilidade padrão para interfaces é `public`.</span><span class="sxs-lookup"><span data-stu-id="9bebb-113">The default accessibility for interfaces is `public`.</span></span>

<span data-ttu-id="9bebb-114">Opcionalmente, você pode atribuir um nome a cada parâmetro de F# método usando a sintaxe normal:</span><span class="sxs-lookup"><span data-stu-id="9bebb-114">You can optionally give each method parameter a name using normal F# syntax:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet24032.fs)]

<span data-ttu-id="9bebb-115">No exemplo acima `ISprintable` , o `Print` método tem um único parâmetro do tipo `string` com o nome `format`.</span><span class="sxs-lookup"><span data-stu-id="9bebb-115">In the above `ISprintable` example, the `Print` method has a single parameter of the type `string` with the name `format`.</span></span>

<span data-ttu-id="9bebb-116">Há duas maneiras de implementar interfaces: usando expressões de objeto e usando tipos de classe.</span><span class="sxs-lookup"><span data-stu-id="9bebb-116">There are two ways to implement interfaces: by using object expressions, and by using class types.</span></span> <span data-ttu-id="9bebb-117">Em ambos os casos, o tipo de classe ou expressão de objeto fornece corpos de método para métodos abstratos da interface.</span><span class="sxs-lookup"><span data-stu-id="9bebb-117">In either case, the class type or object expression provides method bodies for abstract methods of the interface.</span></span> <span data-ttu-id="9bebb-118">As implementações são específicas para cada tipo que implementa a interface.</span><span class="sxs-lookup"><span data-stu-id="9bebb-118">Implementations are specific to each type that implements the interface.</span></span> <span data-ttu-id="9bebb-119">Portanto, os métodos de interface em diferentes tipos podem ser diferentes uns dos outros.</span><span class="sxs-lookup"><span data-stu-id="9bebb-119">Therefore, interface methods on different types might be different from each other.</span></span>

<span data-ttu-id="9bebb-120">As palavras-chave `interface` e `end`, que marcam o início e o final da definição, são opcionais quando você usa a sintaxe leve.</span><span class="sxs-lookup"><span data-stu-id="9bebb-120">The keywords `interface` and `end`, which mark the start and end of the definition, are optional when you use lightweight syntax.</span></span> <span data-ttu-id="9bebb-121">Se você não usar essas palavras-chave, o compilador tentará inferir se o tipo é uma classe ou uma interface analisando as construções que você usa.</span><span class="sxs-lookup"><span data-stu-id="9bebb-121">If you do not use these keywords, the compiler attempts to infer whether the type is a class or an interface by analyzing the constructs that you use.</span></span> <span data-ttu-id="9bebb-122">Se você definir um membro ou usar outra sintaxe de classe, o tipo será interpretado como uma classe.</span><span class="sxs-lookup"><span data-stu-id="9bebb-122">If you define a member or use other class syntax, the type is interpreted as a class.</span></span>

<span data-ttu-id="9bebb-123">O estilo de codificação .NET é iniciar todas as interfaces com um `I`capital.</span><span class="sxs-lookup"><span data-stu-id="9bebb-123">The .NET coding style is to begin all interfaces with a capital `I`.</span></span>

## <a name="implementing-interfaces-by-using-class-types"></a><span data-ttu-id="9bebb-124">Implementando interfaces usando tipos de classe</span><span class="sxs-lookup"><span data-stu-id="9bebb-124">Implementing Interfaces by Using Class Types</span></span>

<span data-ttu-id="9bebb-125">Você pode implementar uma ou mais interfaces em um tipo de classe usando a `interface` palavra-chave, o nome da interface e a `with` palavra-chave, seguida pelas definições de membro da interface, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="9bebb-125">You can implement one or more interfaces in a class type by using the `interface` keyword, the name of the interface, and the `with` keyword, followed by the interface member definitions, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2801.fs)]

<span data-ttu-id="9bebb-126">Implementações de interface são herdadas, portanto, quaisquer classes derivadas não precisam reimplementá-las.</span><span class="sxs-lookup"><span data-stu-id="9bebb-126">Interface implementations are inherited, so any derived classes do not need to reimplement them.</span></span>

## <a name="calling-interface-methods"></a><span data-ttu-id="9bebb-127">Chamando métodos de interface</span><span class="sxs-lookup"><span data-stu-id="9bebb-127">Calling Interface Methods</span></span>

<span data-ttu-id="9bebb-128">Métodos de interface podem ser chamados somente por meio da interface, não por meio de qualquer objeto do tipo que implementa a interface.</span><span class="sxs-lookup"><span data-stu-id="9bebb-128">Interface methods can be called only through the interface, not through any object of the type that implements the interface.</span></span> <span data-ttu-id="9bebb-129">Portanto, talvez você precise fazer a conversão para o tipo de interface usando o `:>` operador ou o `upcast` operador para chamar esses métodos.</span><span class="sxs-lookup"><span data-stu-id="9bebb-129">Thus, you might have to upcast to the interface type by using the `:>` operator or the `upcast` operator in order to call these methods.</span></span>

<span data-ttu-id="9bebb-130">Para chamar o método de interface quando você tem um objeto do `SomeClass`tipo, você deve fazer o Convert do objeto para o tipo de interface, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="9bebb-130">To call the interface method when you have an object of type `SomeClass`, you must upcast the object to the interface type, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2802.fs)]

<span data-ttu-id="9bebb-131">Uma alternativa é declarar um método no objeto que faz a conversão e chama o método de interface, como no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="9bebb-131">An alternative is to declare a method on the object that upcasts and calls the interface method, as in the following example.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2803.fs)]

## <a name="implementing-interfaces-by-using-object-expressions"></a><span data-ttu-id="9bebb-132">Implementando interfaces usando expressões de objeto</span><span class="sxs-lookup"><span data-stu-id="9bebb-132">Implementing Interfaces by Using Object Expressions</span></span>

<span data-ttu-id="9bebb-133">As expressões de objeto fornecem uma maneira curta de implementar uma interface.</span><span class="sxs-lookup"><span data-stu-id="9bebb-133">Object expressions provide a short way to implement an interface.</span></span> <span data-ttu-id="9bebb-134">Eles são úteis quando você não precisa criar um tipo nomeado e só deseja um objeto que dê suporte aos métodos de interface, sem nenhum método adicional.</span><span class="sxs-lookup"><span data-stu-id="9bebb-134">They are useful when you do not have to create a named type, and you just want an object that supports the interface methods, without any additional methods.</span></span> <span data-ttu-id="9bebb-135">Uma expressão de objeto é ilustrada no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="9bebb-135">An object expression is illustrated in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2804.fs)]

## <a name="interface-inheritance"></a><span data-ttu-id="9bebb-136">Herança de interface</span><span class="sxs-lookup"><span data-stu-id="9bebb-136">Interface Inheritance</span></span>

<span data-ttu-id="9bebb-137">As interfaces podem herdar de uma ou mais interfaces base.</span><span class="sxs-lookup"><span data-stu-id="9bebb-137">Interfaces can inherit from one or more base interfaces.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2805.fs)]

## <a name="see-also"></a><span data-ttu-id="9bebb-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9bebb-138">See also</span></span>

- [<span data-ttu-id="9bebb-139">Referência da Linguagem F#</span><span class="sxs-lookup"><span data-stu-id="9bebb-139">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="9bebb-140">Expressões de Objeto</span><span class="sxs-lookup"><span data-stu-id="9bebb-140">Object Expressions</span></span>](object-expressions.md)
- [<span data-ttu-id="9bebb-141">Classes</span><span class="sxs-lookup"><span data-stu-id="9bebb-141">Classes</span></span>](classes.md)
