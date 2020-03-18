---
title: Implementação de interface explícita – Guia de Programação em C#
ms.date: 01/24/2020
helpviewer_keywords:
- explicit interfaces [C#]
- interfaces [C#], explicit
ms.assetid: 181c901f-0d4c-4f29-97fc-895079617bf2
ms.openlocfilehash: ea32a279b7c464174a7fada5ef93ccf62ef39884
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79167667"
---
# <a name="explicit-interface-implementation-c-programming-guide"></a><span data-ttu-id="fabb7-102">Implementação de interface explícita (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="fabb7-102">Explicit Interface Implementation (C# Programming Guide)</span></span>

<span data-ttu-id="fabb7-103">Caso uma [classe](../../language-reference/keywords/class.md) implemente duas interfaces que contêm um membro com a mesma assinatura, logo, implementar esse membro na classe fará com que as duas interfaces usem tal membro como sua implementação.</span><span class="sxs-lookup"><span data-stu-id="fabb7-103">If a [class](../../language-reference/keywords/class.md) implements two interfaces that contain a member with the same signature, then implementing that member on the class will cause both interfaces to use that member as their implementation.</span></span> <span data-ttu-id="fabb7-104">No exemplo a seguir, todas as chamadas para `Paint` invocam o mesmo método.</span><span class="sxs-lookup"><span data-stu-id="fabb7-104">In the following example, all the calls to `Paint` invoke the same method.</span></span> <span data-ttu-id="fabb7-105">Esta primeira amostra define os tipos:</span><span class="sxs-lookup"><span data-stu-id="fabb7-105">This first sample defines the types:</span></span>

[!code-csharp[DefineSimpleTypes](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#DefineTypes)]

<span data-ttu-id="fabb7-106">A seguinte amostra chama os métodos:</span><span class="sxs-lookup"><span data-stu-id="fabb7-106">The following sample calls the methods:</span></span>

[!code-csharp[DefineSimpleTypes](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#CallMethods)]

<span data-ttu-id="fabb7-107">Quando dois membros da interface não executam a mesma função, isso leva a uma implementação incorreta de uma ou ambas as interfaces.</span><span class="sxs-lookup"><span data-stu-id="fabb7-107">When two interface members don't perform the same function, it leads to an incorrect implementation of one or both of the interfaces.</span></span> <span data-ttu-id="fabb7-108">É possível implementar um membro de interface explicitamente — criando um membro de classe que é chamado apenas através da interface e é específico para essa interface.</span><span class="sxs-lookup"><span data-stu-id="fabb7-108">It's possible to implement an interface member explicitly—creating a class member that is only called through the interface, and is specific to that interface.</span></span> <span data-ttu-id="fabb7-109">Nomeie o membro da classe com o nome da interface e um período.</span><span class="sxs-lookup"><span data-stu-id="fabb7-109">Name the class member with the name of the interface and a period.</span></span> <span data-ttu-id="fabb7-110">Por exemplo: </span><span class="sxs-lookup"><span data-stu-id="fabb7-110">For example:</span></span>

[!code-csharp[DefineExplicitImplementation](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#ExplicitImplementation)]

<span data-ttu-id="fabb7-111">O membro da classe `IControl.Paint` está disponível somente por meio da interface `IControl` e `ISurface.Paint` está disponível apenas por meio do `ISurface`.</span><span class="sxs-lookup"><span data-stu-id="fabb7-111">The class member `IControl.Paint` is only available through the `IControl` interface, and `ISurface.Paint` is only available through `ISurface`.</span></span> <span data-ttu-id="fabb7-112">Ambas as implementações do método são separadas, e nenhuma delas está disponível diretamente na classe.</span><span class="sxs-lookup"><span data-stu-id="fabb7-112">Both method implementations are separate, and neither are available directly on the class.</span></span> <span data-ttu-id="fabb7-113">Por exemplo: </span><span class="sxs-lookup"><span data-stu-id="fabb7-113">For example:</span></span>

[!code-csharp[CallExplicitImplementation](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#CallExplicitImplementation)]

<span data-ttu-id="fabb7-114">A implementação explícita também é usada para resolver casos em que duas interfaces declaram membros diferentes com o mesmo nome, como uma propriedade e um método.</span><span class="sxs-lookup"><span data-stu-id="fabb7-114">Explicit implementation is also used to resolve cases where two interfaces each declare different members of the same name such as a property and a method.</span></span> <span data-ttu-id="fabb7-115">Para implementar ambas as interfaces, uma classe deve `P`usar a `P`implementação explícita para a propriedade, ou para o método, ou ambos, para evitar um erro do compilador.</span><span class="sxs-lookup"><span data-stu-id="fabb7-115">To implement both interfaces, a class has to use explicit implementation either for the property `P`, or the method `P`, or both, to avoid a compiler error.</span></span> <span data-ttu-id="fabb7-116">Por exemplo: </span><span class="sxs-lookup"><span data-stu-id="fabb7-116">For example:</span></span>

[!code-csharp[NameCollisions](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#NameCollision)]

<span data-ttu-id="fabb7-117">Começando com [C# 8.0](../../whats-new/csharp-8.md#default-interface-methods), você pode definir uma implementação para membros declarados em uma interface.</span><span class="sxs-lookup"><span data-stu-id="fabb7-117">Beginning with [C# 8.0](../../whats-new/csharp-8.md#default-interface-methods), you can define an implementation for members declared in an interface.</span></span> <span data-ttu-id="fabb7-118">Se uma classe herdar uma implementação de método a partir de uma interface, esse método só será acessível através de uma referência do tipo de interface.</span><span class="sxs-lookup"><span data-stu-id="fabb7-118">If a class inherits a method implementation from an interface, that method is only accessible through a reference of the interface type.</span></span> <span data-ttu-id="fabb7-119">O membro herdado não aparece como parte da interface pública.</span><span class="sxs-lookup"><span data-stu-id="fabb7-119">The inherited member doesn't appear as part of the public interface.</span></span> <span data-ttu-id="fabb7-120">A amostra a seguir define uma implementação padrão para um método de interface:</span><span class="sxs-lookup"><span data-stu-id="fabb7-120">The following sample defines a default implementation for an interface method:</span></span>

[!code-csharp[NameCollisions](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#DefaultImplementation)]

<span data-ttu-id="fabb7-121">A seguinte amostra invoca a implementação padrão:</span><span class="sxs-lookup"><span data-stu-id="fabb7-121">The following sample invokes the default implementation:</span></span>

[!code-csharp[NameCollisions](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#CallDefaultImplementation)]

<span data-ttu-id="fabb7-122">Qualquer classe que `IControl` implemente a interface `Paint` pode substituir o método padrão, seja como um método público, ou como uma implementação de interface explícita.</span><span class="sxs-lookup"><span data-stu-id="fabb7-122">Any class that implements the `IControl` interface can override the default `Paint` method, either as a public method, or as an explicit interface implementation.</span></span>

## <a name="see-also"></a><span data-ttu-id="fabb7-123">Confira também</span><span class="sxs-lookup"><span data-stu-id="fabb7-123">See also</span></span>

- [<span data-ttu-id="fabb7-124">C# Guia de Programação</span><span class="sxs-lookup"><span data-stu-id="fabb7-124">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="fabb7-125">Classes e structs</span><span class="sxs-lookup"><span data-stu-id="fabb7-125">Classes and Structs</span></span>](../classes-and-structs/index.md)
- [<span data-ttu-id="fabb7-126">Interfaces</span><span class="sxs-lookup"><span data-stu-id="fabb7-126">Interfaces</span></span>](./index.md)
- [<span data-ttu-id="fabb7-127">Herança</span><span class="sxs-lookup"><span data-stu-id="fabb7-127">Inheritance</span></span>](../classes-and-structs/inheritance.md)
