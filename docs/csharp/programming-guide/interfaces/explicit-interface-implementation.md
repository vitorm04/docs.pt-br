---
title: Implementação de interface explícita – Guia de Programação em C#
ms.date: 01/24/2020
helpviewer_keywords:
- explicit interfaces [C#]
- interfaces [C#], explicit
ms.assetid: 181c901f-0d4c-4f29-97fc-895079617bf2
ms.openlocfilehash: c6f1f849e0d4e831802b4c9b8b4bc3887363a34c
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628144"
---
# <a name="explicit-interface-implementation-c-programming-guide"></a><span data-ttu-id="0cbf3-102">Implementação de interface explícita (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="0cbf3-102">Explicit Interface Implementation (C# Programming Guide)</span></span>

<span data-ttu-id="0cbf3-103">Caso uma [classe](../../language-reference/keywords/class.md) implemente duas interfaces que contêm um membro com a mesma assinatura, logo, implementar esse membro na classe fará com que as duas interfaces usem tal membro como sua implementação.</span><span class="sxs-lookup"><span data-stu-id="0cbf3-103">If a [class](../../language-reference/keywords/class.md) implements two interfaces that contain a member with the same signature, then implementing that member on the class will cause both interfaces to use that member as their implementation.</span></span> <span data-ttu-id="0cbf3-104">No exemplo a seguir, todas as chamadas para `Paint` invocam o mesmo método.</span><span class="sxs-lookup"><span data-stu-id="0cbf3-104">In the following example, all the calls to `Paint` invoke the same method.</span></span> <span data-ttu-id="0cbf3-105">Este primeiro exemplo define os tipos:</span><span class="sxs-lookup"><span data-stu-id="0cbf3-105">This first sample defines the types:</span></span>

[!code-csharp[DefineSimpleTypes](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#DefineTypes)]

<span data-ttu-id="0cbf3-106">O exemplo a seguir chama os métodos:</span><span class="sxs-lookup"><span data-stu-id="0cbf3-106">The following sample calls the methods:</span></span>

[!code-csharp[DefineSimpleTypes](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#CallMethods)]

<span data-ttu-id="0cbf3-107">Quando dois membros de interface não executam a mesma função, ele leva a uma implementação incorreta de uma ou de ambas as interfaces.</span><span class="sxs-lookup"><span data-stu-id="0cbf3-107">When two interface members don't perform the same function, it leads to an incorrect implementation of one or both of the interfaces.</span></span> <span data-ttu-id="0cbf3-108">É possível implementar um membro de interface explicitamente, criando um membro de classe que é chamado apenas por meio da interface e é específico para essa interface.</span><span class="sxs-lookup"><span data-stu-id="0cbf3-108">It's possible to implement an interface member explicitly—creating a class member that is only called through the interface, and is specific to that interface.</span></span> <span data-ttu-id="0cbf3-109">Nomeie o membro da classe com o nome da interface e um ponto final.</span><span class="sxs-lookup"><span data-stu-id="0cbf3-109">Name the class member with the name of the interface and a period.</span></span> <span data-ttu-id="0cbf3-110">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="0cbf3-110">For example:</span></span>

[!code-csharp[DefineExplicitImplementation](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#ExplicitImplementation)]

<span data-ttu-id="0cbf3-111">O membro da classe `IControl.Paint` está disponível somente por meio da interface `IControl` e `ISurface.Paint` está disponível apenas por meio do `ISurface`.</span><span class="sxs-lookup"><span data-stu-id="0cbf3-111">The class member `IControl.Paint` is only available through the `IControl` interface, and `ISurface.Paint` is only available through `ISurface`.</span></span> <span data-ttu-id="0cbf3-112">Ambas as implementações de método são separadas e nenhuma está disponível diretamente na classe.</span><span class="sxs-lookup"><span data-stu-id="0cbf3-112">Both method implementations are separate, and neither are available directly on the class.</span></span> <span data-ttu-id="0cbf3-113">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="0cbf3-113">For example:</span></span>

[!code-csharp[CallExplicitImplementation](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#CallExplicitImplementation)]

<span data-ttu-id="0cbf3-114">A implementação explícita também é usada para resolver casos em que duas interfaces declaram Membros diferentes do mesmo nome, como uma propriedade e um método.</span><span class="sxs-lookup"><span data-stu-id="0cbf3-114">Explicit implementation is also used to resolve cases where two interfaces each declare different members of the same name such as a property and a method.</span></span> <span data-ttu-id="0cbf3-115">Para implementar ambas as interfaces, uma classe deve usar a implementação explícita para a propriedade `P`ou o método `P`, ou ambos, para evitar um erro do compilador.</span><span class="sxs-lookup"><span data-stu-id="0cbf3-115">To implement both interfaces, a class has to use explicit implementation either for the property `P`, or the method `P`, or both, to avoid a compiler error.</span></span> <span data-ttu-id="0cbf3-116">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="0cbf3-116">For example:</span></span>

[!code-csharp[NameCollisions](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#NameCollision)]

<span data-ttu-id="0cbf3-117">Se uma classe herdar uma implementação de método de uma interface, esse método só poderá ser acessado por meio de uma referência do tipo de interface.</span><span class="sxs-lookup"><span data-stu-id="0cbf3-117">If a class inherits a method implementation from an interface, that method is only accessible through a reference of the interface type.</span></span> <span data-ttu-id="0cbf3-118">O membro herdado não aparece como parte da interface pública.</span><span class="sxs-lookup"><span data-stu-id="0cbf3-118">The inherited member doesn't appear as part of the public interface.</span></span> <span data-ttu-id="0cbf3-119">O exemplo a seguir define uma implementação padrão para um método de interface:</span><span class="sxs-lookup"><span data-stu-id="0cbf3-119">The following sample defines a default implementation for an interface method:</span></span>

[!code-csharp[NameCollisions](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#DefaultImplementation)]

<span data-ttu-id="0cbf3-120">O exemplo a seguir invoca a implementação padrão:</span><span class="sxs-lookup"><span data-stu-id="0cbf3-120">The following sample invokes the default implementation:</span></span>

[!code-csharp[NameCollisions](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#CallDefaultImplementation)]

<span data-ttu-id="0cbf3-121">Qualquer classe que implemente a interface `IControl` pode substituir o método de `Paint` padrão, como um método público, ou como uma implementação de interface explícita.</span><span class="sxs-lookup"><span data-stu-id="0cbf3-121">Any class that implements the `IControl` interface can override the default `Paint` method, either as a public method, or as an explicit interface implementation.</span></span>

## <a name="see-also"></a><span data-ttu-id="0cbf3-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0cbf3-122">See also</span></span>

- [<span data-ttu-id="0cbf3-123">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="0cbf3-123">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="0cbf3-124">Classes e Structs</span><span class="sxs-lookup"><span data-stu-id="0cbf3-124">Classes and Structs</span></span>](../classes-and-structs/index.md)
- [<span data-ttu-id="0cbf3-125">Interfaces</span><span class="sxs-lookup"><span data-stu-id="0cbf3-125">Interfaces</span></span>](./index.md)
- [<span data-ttu-id="0cbf3-126">Herança</span><span class="sxs-lookup"><span data-stu-id="0cbf3-126">Inheritance</span></span>](../classes-and-structs/inheritance.md)
