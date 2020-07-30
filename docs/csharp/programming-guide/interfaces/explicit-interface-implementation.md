---
title: Implementação de interface explícita – Guia de Programação em C#
description: Uma classe pode implementar interfaces que contêm um membro com a mesma assinatura em C#. A implementação explícita cria um membro de classe específico a uma interface.
ms.date: 01/24/2020
helpviewer_keywords:
- explicit interfaces [C#]
- interfaces [C#], explicit
ms.assetid: 181c901f-0d4c-4f29-97fc-895079617bf2
ms.openlocfilehash: a6ec328c08d1da84a11431d9400a094df8c72223
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303081"
---
# <a name="explicit-interface-implementation-c-programming-guide"></a><span data-ttu-id="8629f-104">Implementação de interface explícita (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="8629f-104">Explicit Interface Implementation (C# Programming Guide)</span></span>

<span data-ttu-id="8629f-105">Caso uma [classe](../../language-reference/keywords/class.md) implemente duas interfaces que contêm um membro com a mesma assinatura, logo, implementar esse membro na classe fará com que as duas interfaces usem tal membro como sua implementação.</span><span class="sxs-lookup"><span data-stu-id="8629f-105">If a [class](../../language-reference/keywords/class.md) implements two interfaces that contain a member with the same signature, then implementing that member on the class will cause both interfaces to use that member as their implementation.</span></span> <span data-ttu-id="8629f-106">No exemplo a seguir, todas as chamadas para `Paint` invocam o mesmo método.</span><span class="sxs-lookup"><span data-stu-id="8629f-106">In the following example, all the calls to `Paint` invoke the same method.</span></span> <span data-ttu-id="8629f-107">Este primeiro exemplo define os tipos:</span><span class="sxs-lookup"><span data-stu-id="8629f-107">This first sample defines the types:</span></span>

[!code-csharp[DefineSimpleTypes](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#DefineTypes)]

<span data-ttu-id="8629f-108">O exemplo a seguir chama os métodos:</span><span class="sxs-lookup"><span data-stu-id="8629f-108">The following sample calls the methods:</span></span>

[!code-csharp[DefineSimpleTypes](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#CallMethods)]

<span data-ttu-id="8629f-109">Quando dois membros de interface não executam a mesma função, ele leva a uma implementação incorreta de uma ou de ambas as interfaces.</span><span class="sxs-lookup"><span data-stu-id="8629f-109">When two interface members don't perform the same function, it leads to an incorrect implementation of one or both of the interfaces.</span></span> <span data-ttu-id="8629f-110">É possível implementar um membro de interface explicitamente, criando um membro de classe que é chamado apenas por meio da interface e é específico para essa interface.</span><span class="sxs-lookup"><span data-stu-id="8629f-110">It's possible to implement an interface member explicitly—creating a class member that is only called through the interface, and is specific to that interface.</span></span> <span data-ttu-id="8629f-111">Nomeie o membro da classe com o nome da interface e um ponto final.</span><span class="sxs-lookup"><span data-stu-id="8629f-111">Name the class member with the name of the interface and a period.</span></span> <span data-ttu-id="8629f-112">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="8629f-112">For example:</span></span>

[!code-csharp[DefineExplicitImplementation](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#ExplicitImplementation)]

<span data-ttu-id="8629f-113">O membro da classe `IControl.Paint` está disponível somente por meio da interface `IControl` e `ISurface.Paint` está disponível apenas por meio do `ISurface`.</span><span class="sxs-lookup"><span data-stu-id="8629f-113">The class member `IControl.Paint` is only available through the `IControl` interface, and `ISurface.Paint` is only available through `ISurface`.</span></span> <span data-ttu-id="8629f-114">Ambas as implementações de método são separadas e nenhuma está disponível diretamente na classe.</span><span class="sxs-lookup"><span data-stu-id="8629f-114">Both method implementations are separate, and neither are available directly on the class.</span></span> <span data-ttu-id="8629f-115">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="8629f-115">For example:</span></span>

[!code-csharp[CallExplicitImplementation](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#CallExplicitImplementation)]

<span data-ttu-id="8629f-116">A implementação explícita também é usada para resolver casos em que duas interfaces declaram Membros diferentes do mesmo nome, como uma propriedade e um método.</span><span class="sxs-lookup"><span data-stu-id="8629f-116">Explicit implementation is also used to resolve cases where two interfaces each declare different members of the same name such as a property and a method.</span></span> <span data-ttu-id="8629f-117">Para implementar ambas as interfaces, uma classe deve usar a implementação explícita para a propriedade `P` ou o método `P` , ou ambos, para evitar um erro do compilador.</span><span class="sxs-lookup"><span data-stu-id="8629f-117">To implement both interfaces, a class has to use explicit implementation either for the property `P`, or the method `P`, or both, to avoid a compiler error.</span></span> <span data-ttu-id="8629f-118">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="8629f-118">For example:</span></span>

[!code-csharp[NameCollisions](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#NameCollision)]

<span data-ttu-id="8629f-119">A partir do [C# 8,0](../../whats-new/csharp-8.md#default-interface-methods), você pode definir uma implementação para membros declarados em uma interface.</span><span class="sxs-lookup"><span data-stu-id="8629f-119">Beginning with [C# 8.0](../../whats-new/csharp-8.md#default-interface-methods), you can define an implementation for members declared in an interface.</span></span> <span data-ttu-id="8629f-120">Se uma classe herdar uma implementação de método de uma interface, esse método só poderá ser acessado por meio de uma referência do tipo de interface.</span><span class="sxs-lookup"><span data-stu-id="8629f-120">If a class inherits a method implementation from an interface, that method is only accessible through a reference of the interface type.</span></span> <span data-ttu-id="8629f-121">O membro herdado não aparece como parte da interface pública.</span><span class="sxs-lookup"><span data-stu-id="8629f-121">The inherited member doesn't appear as part of the public interface.</span></span> <span data-ttu-id="8629f-122">O exemplo a seguir define uma implementação padrão para um método de interface:</span><span class="sxs-lookup"><span data-stu-id="8629f-122">The following sample defines a default implementation for an interface method:</span></span>

[!code-csharp[NameCollisions](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#DefaultImplementation)]

<span data-ttu-id="8629f-123">O exemplo a seguir invoca a implementação padrão:</span><span class="sxs-lookup"><span data-stu-id="8629f-123">The following sample invokes the default implementation:</span></span>

[!code-csharp[NameCollisions](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#CallDefaultImplementation)]

<span data-ttu-id="8629f-124">Qualquer classe que implemente a `IControl` interface pode substituir o `Paint` método padrão, seja como um método público ou como uma implementação de interface explícita.</span><span class="sxs-lookup"><span data-stu-id="8629f-124">Any class that implements the `IControl` interface can override the default `Paint` method, either as a public method, or as an explicit interface implementation.</span></span>

## <a name="see-also"></a><span data-ttu-id="8629f-125">Veja também</span><span class="sxs-lookup"><span data-stu-id="8629f-125">See also</span></span>

- [<span data-ttu-id="8629f-126">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="8629f-126">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="8629f-127">Classes e structs</span><span class="sxs-lookup"><span data-stu-id="8629f-127">Classes and Structs</span></span>](../classes-and-structs/index.md)
- [<span data-ttu-id="8629f-128">Interfaces</span><span class="sxs-lookup"><span data-stu-id="8629f-128">Interfaces</span></span>](./index.md)
- [<span data-ttu-id="8629f-129">Herança</span><span class="sxs-lookup"><span data-stu-id="8629f-129">Inheritance</span></span>](../classes-and-structs/inheritance.md)
