---
title: Propriedades de interface – Guia de Programação em C#
ms.date: 01/31/2020
helpviewer_keywords:
- properties [C#], on interfaces
- interfaces [C#], properties
ms.assetid: 6503e9ed-33d7-44ec-b4c1-cc16c084b795
ms.openlocfilehash: 5798b80526f34e923e2eaab43847b98f6c64e14b
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77626614"
---
# <a name="interface-properties-c-programming-guide"></a><span data-ttu-id="5e470-102">Propriedades de interface (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="5e470-102">Interface Properties (C# Programming Guide)</span></span>

<span data-ttu-id="5e470-103">As propriedades podem ser declaradas em uma [interface](../../language-reference/keywords/interface.md).</span><span class="sxs-lookup"><span data-stu-id="5e470-103">Properties can be declared on an [interface](../../language-reference/keywords/interface.md).</span></span> <span data-ttu-id="5e470-104">O exemplo a seguir declara um acessador de propriedade de interface:</span><span class="sxs-lookup"><span data-stu-id="5e470-104">The following example declares an interface property accessor:</span></span>

[!code-csharp[DeclareProperties](~/samples/snippets/csharp/interfaces/properties.cs#DeclareInterfaceProperties)]

<span data-ttu-id="5e470-105">Normalmente, as propriedades de interface não têm um corpo.</span><span class="sxs-lookup"><span data-stu-id="5e470-105">Interface properties typically don't have a body.</span></span> <span data-ttu-id="5e470-106">Os acessadores indicam se a propriedade é de leitura/gravação, somente leitura ou somente gravação.</span><span class="sxs-lookup"><span data-stu-id="5e470-106">The accessors indicate whether the property is read-write, read-only, or write-only.</span></span> <span data-ttu-id="5e470-107">Ao contrário de classes e structs, a declaração dos acessadores sem um corpo não declara uma [propriedade implementada automaticamente](auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="5e470-107">Unlike in classes and structs, declaring the accessors without a body doesn't declare an [auto-implemented property](auto-implemented-properties.md).</span></span> <span data-ttu-id="5e470-108">A partir C# do 8,0, uma interface pode definir uma implementação padrão para membros, incluindo propriedades.</span><span class="sxs-lookup"><span data-stu-id="5e470-108">Beginning with C# 8.0, an interface may define a default implementation for members, including properties.</span></span> <span data-ttu-id="5e470-109">Definir uma implementação padrão para uma propriedade em uma interface é raro porque as interfaces não podem definir campos de dados de instância.</span><span class="sxs-lookup"><span data-stu-id="5e470-109">Defining a default implementation for a property in an interface is rare because interfaces may not define instance data fields.</span></span>

## <a name="example"></a><span data-ttu-id="5e470-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5e470-110">Example</span></span>

<span data-ttu-id="5e470-111">Neste exemplo, a interface `IEmployee` tem uma propriedade de leitura/gravação, `Name` e uma propriedade somente leitura, `Counter`.</span><span class="sxs-lookup"><span data-stu-id="5e470-111">In this example, the interface `IEmployee` has a read-write property, `Name`, and a read-only property, `Counter`.</span></span> <span data-ttu-id="5e470-112">A classe `Employee` implementa a interface `IEmployee` e usa essas duas propriedades.</span><span class="sxs-lookup"><span data-stu-id="5e470-112">The class `Employee` implements the `IEmployee` interface and uses these two properties.</span></span> <span data-ttu-id="5e470-113">O programa lê o nome de um novo funcionário e o número atual de funcionários e exibe o nome do funcionário e o número do funcionário computado.</span><span class="sxs-lookup"><span data-stu-id="5e470-113">The program reads the name of a new employee and the current number of employees and displays the employee name and the computed employee number.</span></span>

<span data-ttu-id="5e470-114">Seria possível usar o nome totalmente qualificado da propriedade, que referencia a interface na qual o membro é declarado.</span><span class="sxs-lookup"><span data-stu-id="5e470-114">You could use the fully qualified name of the property, which references the interface in which the member is declared.</span></span> <span data-ttu-id="5e470-115">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="5e470-115">For example:</span></span>

[!code-csharp[ExplicitProperties](~/samples/snippets/csharp/interfaces/properties.cs#ExplicitImplementation)]

<span data-ttu-id="5e470-116">O exemplo anterior demonstra a [implementação de interface explícita](../interfaces/explicit-interface-implementation.md).</span><span class="sxs-lookup"><span data-stu-id="5e470-116">The preceding example demonstrates [Explicit Interface Implementation](../interfaces/explicit-interface-implementation.md).</span></span> <span data-ttu-id="5e470-117">Por exemplo, se a classe `Employee` estiver implementando duas interfaces `ICitizen` e `IEmployee` e as duas interfaces tiverem a propriedade `Name`, será necessária a implementação explícita de membro da interface.</span><span class="sxs-lookup"><span data-stu-id="5e470-117">For example, if the class `Employee` is implementing two interfaces `ICitizen` and `IEmployee` and both interfaces have the `Name` property, the explicit interface member implementation will be necessary.</span></span> <span data-ttu-id="5e470-118">Ou seja, a seguinte declaração de propriedade:</span><span class="sxs-lookup"><span data-stu-id="5e470-118">That is, the following property declaration:</span></span>

[!code-csharp[ExplicitProperties](~/samples/snippets/csharp/interfaces/properties.cs#ExplicitImplementation)]

<span data-ttu-id="5e470-119">implementa a propriedade `Name` na interface `IEmployee`, enquanto a seguinte declaração:</span><span class="sxs-lookup"><span data-stu-id="5e470-119">implements the `Name` property on the `IEmployee` interface, while the following declaration:</span></span>

[!code-csharp[ExplicitProperties](~/samples/snippets/csharp/interfaces/properties.cs#CitizenImplementation)]

<span data-ttu-id="5e470-120">implementa a propriedade `Name` na interface `ICitizen`.</span><span class="sxs-lookup"><span data-stu-id="5e470-120">implements the `Name` property on the `ICitizen` interface.</span></span>

[!code-csharp[Example](~/samples/snippets/csharp/interfaces/properties.cs#PropertyExample)]
[!code-csharp[Example](~/samples/snippets/csharp/interfaces/properties.cs#UseProperty)]

**`210 Hazem Abolrous`**

## <a name="sample-output"></a><span data-ttu-id="5e470-121">Saída de exemplo</span><span class="sxs-lookup"><span data-stu-id="5e470-121">Sample output</span></span>

```console
Enter number of employees: 210
Enter the name of the new employee: Hazem Abolrous
The employee information:
Employee number: 211
Employee name: Hazem Abolrous
```

## <a name="see-also"></a><span data-ttu-id="5e470-122">Confira também</span><span class="sxs-lookup"><span data-stu-id="5e470-122">See also</span></span>

- [<span data-ttu-id="5e470-123">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="5e470-123">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="5e470-124">Propriedades</span><span class="sxs-lookup"><span data-stu-id="5e470-124">Properties</span></span>](./properties.md)
- [<span data-ttu-id="5e470-125">Usando propriedades</span><span class="sxs-lookup"><span data-stu-id="5e470-125">Using Properties</span></span>](./using-properties.md)
- [<span data-ttu-id="5e470-126">Comparação entre propriedades e indexadores</span><span class="sxs-lookup"><span data-stu-id="5e470-126">Comparison Between Properties and Indexers</span></span>](../indexers/comparison-between-properties-and-indexers.md)
- [<span data-ttu-id="5e470-127">Indexadores</span><span class="sxs-lookup"><span data-stu-id="5e470-127">Indexers</span></span>](../indexers/index.md)
- [<span data-ttu-id="5e470-128">Interfaces</span><span class="sxs-lookup"><span data-stu-id="5e470-128">Interfaces</span></span>](../interfaces/index.md)
