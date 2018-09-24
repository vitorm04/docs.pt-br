---
title: interface (Referência de C#)
ms.date: 07/20/2015
f1_keywords:
- interface_CSharpKeyword
helpviewer_keywords:
- interface keyword [C#]
ms.assetid: 7da38e81-4f99-4bc5-b07d-c986b687eeba
ms.openlocfilehash: 4adc7ba106e0044ba6aff94ea3180d9c8e3ded7b
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2018
ms.locfileid: "46711292"
---
# <a name="interface-c-reference"></a><span data-ttu-id="62019-102">interface (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="62019-102">interface (C# Reference)</span></span>

<span data-ttu-id="62019-103">Uma interface contém apenas as assinaturas de [métodos](../../programming-guide/classes-and-structs/methods.md), [propriedades](../../programming-guide/classes-and-structs/properties.md), [eventos](../../programming-guide/events/index.md) ou [indexadores](../../programming-guide/indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="62019-103">An interface contains only the signatures of [methods](../../programming-guide/classes-and-structs/methods.md), [properties](../../programming-guide/classes-and-structs/properties.md), [events](../../programming-guide/events/index.md) or [indexers](../../programming-guide/indexers/index.md).</span></span> <span data-ttu-id="62019-104">Uma classe ou struct que implementa a interface deve implementar os membros da interface que estão especificados na definição de interface.</span><span class="sxs-lookup"><span data-stu-id="62019-104">A class or struct that implements the interface must implement the members of the interface that are specified in the interface definition.</span></span> <span data-ttu-id="62019-105">No exemplo a seguir, a classe `ImplementationClass` deve implementar um método chamado `SampleMethod` que não tem parâmetros e retorna `void`.</span><span class="sxs-lookup"><span data-stu-id="62019-105">In the following example, class `ImplementationClass` must implement a method named `SampleMethod` that has no parameters and returns `void`.</span></span>

<span data-ttu-id="62019-106">Para obter mais informações e exemplos, consulte [Interfaces](../../programming-guide/interfaces/index.md).</span><span class="sxs-lookup"><span data-stu-id="62019-106">For more information and examples, see [Interfaces](../../programming-guide/interfaces/index.md).</span></span>

## <a name="example"></a><span data-ttu-id="62019-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="62019-107">Example</span></span>

[!code-csharp[csrefKeywordsTypes#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#14)]

<span data-ttu-id="62019-108">Uma interface pode ser um membro de um namespace ou de uma classe e pode conter assinaturas dos seguintes membros:</span><span class="sxs-lookup"><span data-stu-id="62019-108">An interface can be a member of a namespace or a class and can contain signatures of the following members:</span></span>

- [<span data-ttu-id="62019-109">Métodos</span><span class="sxs-lookup"><span data-stu-id="62019-109">Methods</span></span>](../../programming-guide/classes-and-structs/methods.md)

- [<span data-ttu-id="62019-110">Propriedades</span><span class="sxs-lookup"><span data-stu-id="62019-110">Properties</span></span>](../../programming-guide/classes-and-structs/using-properties.md)

- [<span data-ttu-id="62019-111">Indexadores</span><span class="sxs-lookup"><span data-stu-id="62019-111">Indexers</span></span>](../../programming-guide/indexers/using-indexers.md)

- [<span data-ttu-id="62019-112">Eventos</span><span class="sxs-lookup"><span data-stu-id="62019-112">Events</span></span>](event.md)

<span data-ttu-id="62019-113">Uma interface pode herdar de uma ou mais interfaces base.</span><span class="sxs-lookup"><span data-stu-id="62019-113">An interface can inherit from one or more base interfaces.</span></span>

<span data-ttu-id="62019-114">Quando uma lista de tipos base contém uma classe base e interfaces, a classe base deve vir em primeiro na lista.</span><span class="sxs-lookup"><span data-stu-id="62019-114">When a base type list contains a base class and interfaces, the base class must come first in the list.</span></span>

<span data-ttu-id="62019-115">Uma classe que implementa uma interface pode implementar membros dessa interface explicitamente.</span><span class="sxs-lookup"><span data-stu-id="62019-115">A class that implements an interface can explicitly implement members of that interface.</span></span> <span data-ttu-id="62019-116">Um membro implementado explicitamente não pode ser acessado por meio de uma instância da classe, mas apenas por meio de uma instância da interface.</span><span class="sxs-lookup"><span data-stu-id="62019-116">An explicitly implemented member cannot be accessed through a class instance, but only through an instance of the interface.</span></span>

<span data-ttu-id="62019-117">Para obter mais detalhes e exemplos de código sobre a implementação explícita da interface, consulte [Implementação explícita da interface](../../programming-guide/interfaces/explicit-interface-implementation.md).</span><span class="sxs-lookup"><span data-stu-id="62019-117">For more details and code examples on explicit interface implementation, see [Explicit Interface Implementation](../../programming-guide/interfaces/explicit-interface-implementation.md).</span></span>

## <a name="example"></a><span data-ttu-id="62019-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="62019-118">Example</span></span>

<span data-ttu-id="62019-119">O exemplo a seguir demonstra a implementação da interface.</span><span class="sxs-lookup"><span data-stu-id="62019-119">The following example demonstrates interface implementation.</span></span> <span data-ttu-id="62019-120">Neste exemplo, a interface contém a declaração de propriedade e a classe contém a implementação.</span><span class="sxs-lookup"><span data-stu-id="62019-120">In this example, the interface contains the property declaration and the class contains the implementation.</span></span> <span data-ttu-id="62019-121">Qualquer instância de uma classe que implementa `IPoint` tem propriedades de inteiro `x` e `y`.</span><span class="sxs-lookup"><span data-stu-id="62019-121">Any instance of a class that implements `IPoint` has integer properties `x` and `y`.</span></span>

[!code-csharp[csrefKeywordsTypes#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#15)]

## <a name="c-language-specification"></a><span data-ttu-id="62019-122">especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="62019-122">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="62019-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="62019-123">See also</span></span>

- [<span data-ttu-id="62019-124">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="62019-124">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="62019-125">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="62019-125">C# Programming Guide</span></span>](../../programming-guide/index.md)  
- [<span data-ttu-id="62019-126">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="62019-126">C# Keywords</span></span>](index.md)  
- [<span data-ttu-id="62019-127">Tipos de referência</span><span class="sxs-lookup"><span data-stu-id="62019-127">Reference Types</span></span>](reference-types.md)  
- [<span data-ttu-id="62019-128">Interfaces</span><span class="sxs-lookup"><span data-stu-id="62019-128">Interfaces</span></span>](../../programming-guide/interfaces/index.md)  
- [<span data-ttu-id="62019-129">Usando propriedades</span><span class="sxs-lookup"><span data-stu-id="62019-129">Using Properties</span></span>](../../programming-guide/classes-and-structs/using-properties.md)  
- [<span data-ttu-id="62019-130">Usando indexadores</span><span class="sxs-lookup"><span data-stu-id="62019-130">Using Indexers</span></span>](../../programming-guide/indexers/using-indexers.md)  
- [<span data-ttu-id="62019-131">class</span><span class="sxs-lookup"><span data-stu-id="62019-131">class</span></span>](class.md)  
- [<span data-ttu-id="62019-132">struct</span><span class="sxs-lookup"><span data-stu-id="62019-132">struct</span></span>](struct.md)  
- [<span data-ttu-id="62019-133">Interfaces</span><span class="sxs-lookup"><span data-stu-id="62019-133">Interfaces</span></span>](../../programming-guide/interfaces/index.md)
