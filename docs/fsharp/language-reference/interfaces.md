---
title: Interfaces
description: 'Saiba como as interfaces F # especificam conjuntos de membros relacionados que outras classes implementam.'
ms.date: 08/15/2020
ms.openlocfilehash: 0cef2932045dae401f5aa069107815543457ca4a
ms.sourcegitcommit: f99115e12a5eb75638abe45072e023a3ce3351ac
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/12/2020
ms.locfileid: "94557045"
---
# <a name="interfaces"></a><span data-ttu-id="ca655-103">Interfaces</span><span class="sxs-lookup"><span data-stu-id="ca655-103">Interfaces</span></span>

<span data-ttu-id="ca655-104">*Interfaces* especificam conjuntos de membros relacionados que outras classes implementam.</span><span class="sxs-lookup"><span data-stu-id="ca655-104">*Interfaces* specify sets of related members that other classes implement.</span></span>

## <a name="syntax"></a><span data-ttu-id="ca655-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ca655-105">Syntax</span></span>

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

## <a name="remarks"></a><span data-ttu-id="ca655-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="ca655-106">Remarks</span></span>

<span data-ttu-id="ca655-107">Declarações de interface assemelham-se a declarações de classe, exceto que nenhum membro é implementado.</span><span class="sxs-lookup"><span data-stu-id="ca655-107">Interface declarations resemble class declarations except that no members are implemented.</span></span> <span data-ttu-id="ca655-108">Em vez disso, todos os membros são abstratos, conforme indicado pela palavra-chave `abstract` .</span><span class="sxs-lookup"><span data-stu-id="ca655-108">Instead, all the members are abstract, as indicated by the keyword `abstract`.</span></span> <span data-ttu-id="ca655-109">Você não fornece um corpo de método para métodos abstratos.</span><span class="sxs-lookup"><span data-stu-id="ca655-109">You do not provide a method body for abstract methods.</span></span> <span data-ttu-id="ca655-110">No entanto, você pode fornecer uma implementação padrão, incluindo também uma definição separada do membro como um método junto com a `default` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="ca655-110">However, you can provide a default implementation by also including a separate definition of the member as a method together with the `default` keyword.</span></span> <span data-ttu-id="ca655-111">Isso é equivalente a criar um método virtual em uma classe base em outras linguagens .NET.</span><span class="sxs-lookup"><span data-stu-id="ca655-111">Doing so is equivalent to creating a virtual method in a base class in other .NET languages.</span></span> <span data-ttu-id="ca655-112">Tal método virtual pode ser substituído em classes que implementam a interface.</span><span class="sxs-lookup"><span data-stu-id="ca655-112">Such a virtual method can be overridden in classes that implement the interface.</span></span>

<span data-ttu-id="ca655-113">A acessibilidade padrão para interfaces é `public` .</span><span class="sxs-lookup"><span data-stu-id="ca655-113">The default accessibility for interfaces is `public`.</span></span>

<span data-ttu-id="ca655-114">Opcionalmente, você pode atribuir um nome a cada parâmetro de método usando a sintaxe F # normal:</span><span class="sxs-lookup"><span data-stu-id="ca655-114">You can optionally give each method parameter a name using normal F# syntax:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet24032.fs)]

<span data-ttu-id="ca655-115">No exemplo acima `ISprintable` , o `Print` método tem um único parâmetro do tipo `string` com o nome `format` .</span><span class="sxs-lookup"><span data-stu-id="ca655-115">In the above `ISprintable` example, the `Print` method has a single parameter of the type `string` with the name `format`.</span></span>

<span data-ttu-id="ca655-116">Há duas maneiras de implementar interfaces: usando expressões de objeto e usando tipos de classe.</span><span class="sxs-lookup"><span data-stu-id="ca655-116">There are two ways to implement interfaces: by using object expressions, and by using class types.</span></span> <span data-ttu-id="ca655-117">Em ambos os casos, o tipo de classe ou expressão de objeto fornece corpos de método para métodos abstratos da interface.</span><span class="sxs-lookup"><span data-stu-id="ca655-117">In either case, the class type or object expression provides method bodies for abstract methods of the interface.</span></span> <span data-ttu-id="ca655-118">As implementações são específicas para cada tipo que implementa a interface.</span><span class="sxs-lookup"><span data-stu-id="ca655-118">Implementations are specific to each type that implements the interface.</span></span> <span data-ttu-id="ca655-119">Portanto, os métodos de interface em diferentes tipos podem ser diferentes uns dos outros.</span><span class="sxs-lookup"><span data-stu-id="ca655-119">Therefore, interface methods on different types might be different from each other.</span></span>

<span data-ttu-id="ca655-120">As palavras-chave `interface` e `end` , que marcam o início e o final da definição, são opcionais quando você usa a sintaxe leve.</span><span class="sxs-lookup"><span data-stu-id="ca655-120">The keywords `interface` and `end`, which mark the start and end of the definition, are optional when you use lightweight syntax.</span></span> <span data-ttu-id="ca655-121">Se você não usar essas palavras-chave, o compilador tentará inferir se o tipo é uma classe ou uma interface analisando as construções que você usa.</span><span class="sxs-lookup"><span data-stu-id="ca655-121">If you do not use these keywords, the compiler attempts to infer whether the type is a class or an interface by analyzing the constructs that you use.</span></span> <span data-ttu-id="ca655-122">Se você definir um membro ou usar outra sintaxe de classe, o tipo será interpretado como uma classe.</span><span class="sxs-lookup"><span data-stu-id="ca655-122">If you define a member or use other class syntax, the type is interpreted as a class.</span></span>

<span data-ttu-id="ca655-123">O estilo de codificação .NET é iniciar todas as interfaces com um capital `I` .</span><span class="sxs-lookup"><span data-stu-id="ca655-123">The .NET coding style is to begin all interfaces with a capital `I`.</span></span>

<span data-ttu-id="ca655-124">Você pode especificar vários parâmetros de duas maneiras: F #-Style e. Estilo de rede.</span><span class="sxs-lookup"><span data-stu-id="ca655-124">You can specify multiple parameters in two ways: F#-style and .NET-style.</span></span> <span data-ttu-id="ca655-125">Ambas serão compiladas da mesma forma para os consumidores do .NET, mas o estilo F # forçará os chamadores F # a usar o aplicativo de parâmetro de estilo F # e o. O estilo NET forçará os chamadores F # a usar o aplicativo de argumento de tupla.</span><span class="sxs-lookup"><span data-stu-id="ca655-125">Both will compile the same way for .NET consumers, but F#-style will force F# callers to use F#-style parameter application and .NET-style will force F# callers to use tupled argument application.</span></span>

```fsharp
type INumeric1 =
    abstract Add: x: int -> y: int -> int

type INumeric2 =
    abstract Add: x: int * y: int -> int
```

## <a name="implementing-interfaces-by-using-class-types"></a><span data-ttu-id="ca655-126">Implementando interfaces usando tipos de classe</span><span class="sxs-lookup"><span data-stu-id="ca655-126">Implementing Interfaces by Using Class Types</span></span>

<span data-ttu-id="ca655-127">Você pode implementar uma ou mais interfaces em um tipo de classe usando a `interface` palavra-chave, o nome da interface e a `with` palavra-chave, seguida pelas definições de membro da interface, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="ca655-127">You can implement one or more interfaces in a class type by using the `interface` keyword, the name of the interface, and the `with` keyword, followed by the interface member definitions, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2801.fs)]

<span data-ttu-id="ca655-128">Implementações de interface são herdadas, portanto, quaisquer classes derivadas não precisam reimplementá-las.</span><span class="sxs-lookup"><span data-stu-id="ca655-128">Interface implementations are inherited, so any derived classes do not need to reimplement them.</span></span>

## <a name="calling-interface-methods"></a><span data-ttu-id="ca655-129">Chamando métodos de interface</span><span class="sxs-lookup"><span data-stu-id="ca655-129">Calling Interface Methods</span></span>

<span data-ttu-id="ca655-130">Métodos de interface podem ser chamados somente por meio da interface, não por meio de qualquer objeto do tipo que implementa a interface.</span><span class="sxs-lookup"><span data-stu-id="ca655-130">Interface methods can be called only through the interface, not through any object of the type that implements the interface.</span></span> <span data-ttu-id="ca655-131">Portanto, talvez você precise fazer a conversão para o tipo de interface usando o `:>` operador ou o `upcast` operador para chamar esses métodos.</span><span class="sxs-lookup"><span data-stu-id="ca655-131">Thus, you might have to upcast to the interface type by using the `:>` operator or the `upcast` operator in order to call these methods.</span></span>

<span data-ttu-id="ca655-132">Para chamar o método de interface quando você tem um objeto do tipo `SomeClass` , você deve fazer o Convert do objeto para o tipo de interface, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="ca655-132">To call the interface method when you have an object of type `SomeClass`, you must upcast the object to the interface type, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2802.fs)]

<span data-ttu-id="ca655-133">Uma alternativa é declarar um método no objeto que faz a conversão e chama o método de interface, como no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="ca655-133">An alternative is to declare a method on the object that upcasts and calls the interface method, as in the following example.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2803.fs)]

## <a name="implementing-interfaces-by-using-object-expressions"></a><span data-ttu-id="ca655-134">Implementando interfaces usando expressões de objeto</span><span class="sxs-lookup"><span data-stu-id="ca655-134">Implementing Interfaces by Using Object Expressions</span></span>

<span data-ttu-id="ca655-135">As expressões de objeto fornecem uma maneira curta de implementar uma interface.</span><span class="sxs-lookup"><span data-stu-id="ca655-135">Object expressions provide a short way to implement an interface.</span></span> <span data-ttu-id="ca655-136">Eles são úteis quando você não precisa criar um tipo nomeado e só deseja um objeto que dê suporte aos métodos de interface, sem nenhum método adicional.</span><span class="sxs-lookup"><span data-stu-id="ca655-136">They are useful when you do not have to create a named type, and you just want an object that supports the interface methods, without any additional methods.</span></span> <span data-ttu-id="ca655-137">Uma expressão de objeto é ilustrada no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="ca655-137">An object expression is illustrated in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2804.fs)]

## <a name="interface-inheritance"></a><span data-ttu-id="ca655-138">Herança de interface</span><span class="sxs-lookup"><span data-stu-id="ca655-138">Interface Inheritance</span></span>

<span data-ttu-id="ca655-139">As interfaces podem herdar de uma ou mais interfaces base.</span><span class="sxs-lookup"><span data-stu-id="ca655-139">Interfaces can inherit from one or more base interfaces.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2805.fs)]

## <a name="implementing-interfaces-with-default-implementations"></a><span data-ttu-id="ca655-140">Implementando interfaces com implementações padrão</span><span class="sxs-lookup"><span data-stu-id="ca655-140">Implementing interfaces with default implementations</span></span>

<span data-ttu-id="ca655-141">O C# dá suporte à definição de interfaces com implementações padrão, da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="ca655-141">C# supports defining interfaces with default implementations, like so:</span></span>

```csharp
using System;

namespace CSharp
{
    public interface MyDim
    {
        public int Z => 0;
    }
}
```

<span data-ttu-id="ca655-142">Eles são diretamente consumíveis da F #:</span><span class="sxs-lookup"><span data-stu-id="ca655-142">These are directly consumable from F#:</span></span>

```fsharp
open CSharp

// You can implement the interface via a class
type MyType() =
    member _.M() = ()

    interface MyDim

let md = MyType() :> MyDim
printfn $"DIM from C#: %d{md.Z}"

// You can also implement it via an object expression
let md' = { new MyDim }
printfn $"DIM from C# but via Object Expression: %d{md'.Z}"
```

<span data-ttu-id="ca655-143">Você pode substituir uma implementação padrão por `override` , como substituir qualquer membro virtual.</span><span class="sxs-lookup"><span data-stu-id="ca655-143">You can override a default implementation with `override`, like overriding any virtual member.</span></span>

<span data-ttu-id="ca655-144">Todos os membros em uma interface que não têm uma implementação padrão ainda devem ser implementados explicitamente.</span><span class="sxs-lookup"><span data-stu-id="ca655-144">Any members in an interface that do not have a default implementation must still be explicitly implemented.</span></span>

## <a name="implementing-the-same-interface-at-different-generic-instantiations"></a><span data-ttu-id="ca655-145">Implementando a mesma interface em instanciações genéricas diferentes</span><span class="sxs-lookup"><span data-stu-id="ca655-145">Implementing the same interface at different generic instantiations</span></span>

<span data-ttu-id="ca655-146">O F # dá suporte à implementação da mesma interface em instanciações genéricas diferentes, desta forma:</span><span class="sxs-lookup"><span data-stu-id="ca655-146">F# supports implementing the same interface at different generic instantiations like so:</span></span>

```fsharp
type IA<'T> =
    abstract member Get : unit -> 'T

type MyClass() =
    interface IA<int> with
        member x.Get() = 1
    interface IA<string> with
        member x.Get() = "hello"

let mc = MyClass()
let iaInt = mc :> IA<int>
let iaString = mc :> IA<string>

iaInt.Get() // 1
iaString.Get() // "hello"
```

## <a name="see-also"></a><span data-ttu-id="ca655-147">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ca655-147">See also</span></span>

- [<span data-ttu-id="ca655-148">Referência de linguagem F #</span><span class="sxs-lookup"><span data-stu-id="ca655-148">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="ca655-149">Expressões de objeto</span><span class="sxs-lookup"><span data-stu-id="ca655-149">Object Expressions</span></span>](object-expressions.md)
- [<span data-ttu-id="ca655-150">Classes</span><span class="sxs-lookup"><span data-stu-id="ca655-150">Classes</span></span>](classes.md)
