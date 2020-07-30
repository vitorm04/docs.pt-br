---
title: Indexadores em interfaces – Guia de Programação em C#
description: Indexadores podem ser declarados em uma interface em C#. Saiba como os acessadores de indexadores de interface diferem dos acessadores de indexadores de classe.
ms.date: 02/08/2020
helpviewer_keywords:
- indexers [C#], in interfaces
- accessors [C#], indexers
ms.assetid: e16b54bd-4a83-4f52-bd75-65819fca79e8
ms.openlocfilehash: ec77843bdf3181a543bd6c02cfb034b21ded1ae7
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303095"
---
# <a name="indexers-in-interfaces-c-programming-guide"></a><span data-ttu-id="8f74b-104">Indexadores em interfaces (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="8f74b-104">Indexers in Interfaces (C# Programming Guide)</span></span>

<span data-ttu-id="8f74b-105">Os indexadores podem ser declarados em uma [interface](../../language-reference/keywords/interface.md).</span><span class="sxs-lookup"><span data-stu-id="8f74b-105">Indexers can be declared on an [interface](../../language-reference/keywords/interface.md).</span></span> <span data-ttu-id="8f74b-106">Acessadores de indexadores de interface diferem dos acessadores de indexadores de [classe](../../language-reference/keywords/class.md) das seguintes maneiras:</span><span class="sxs-lookup"><span data-stu-id="8f74b-106">Accessors of interface indexers differ from the accessors of [class](../../language-reference/keywords/class.md) indexers in the following ways:</span></span>

- <span data-ttu-id="8f74b-107">Os acessadores de interface não usam modificadores.</span><span class="sxs-lookup"><span data-stu-id="8f74b-107">Interface accessors do not use modifiers.</span></span>
- <span data-ttu-id="8f74b-108">Um acessador de interface normalmente não tem um corpo.</span><span class="sxs-lookup"><span data-stu-id="8f74b-108">An interface accessor typically does not have a body.</span></span>

<span data-ttu-id="8f74b-109">A finalidade do acessador é indicar se o indexador é de leitura/gravação, somente leitura ou somente gravação.</span><span class="sxs-lookup"><span data-stu-id="8f74b-109">The purpose of the accessor is to indicate whether the indexer is read-write, read-only, or write-only.</span></span> <span data-ttu-id="8f74b-110">Você pode fornecer uma implementação para um indexador definido em uma interface, mas isso é raro.</span><span class="sxs-lookup"><span data-stu-id="8f74b-110">You may provide an implementation for an indexer defined in an interface, but this is rare.</span></span> <span data-ttu-id="8f74b-111">Normalmente, os indexadores definem uma API para acessar os campos de dados e os campos de dados não podem ser definidos em uma interface.</span><span class="sxs-lookup"><span data-stu-id="8f74b-111">Indexers typically define an API to access data fields, and data fields cannot be defined in an interface.</span></span>

<span data-ttu-id="8f74b-112">Este é um exemplo de um acessador de indexador de interface:</span><span class="sxs-lookup"><span data-stu-id="8f74b-112">The following is an example of an interface indexer accessor:</span></span>

[!code-csharp[DefineInterface](~/samples/snippets/csharp/interfaces/indexers.cs#DefineIndexer)]

<span data-ttu-id="8f74b-113">A assinatura de um indexador deve ser diferente das assinaturas de todos os outros indexadores declarados na mesma interface.</span><span class="sxs-lookup"><span data-stu-id="8f74b-113">The signature of an indexer must differ from the signatures of all other indexers declared in the same interface.</span></span>

## <a name="example"></a><span data-ttu-id="8f74b-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8f74b-114">Example</span></span>

<span data-ttu-id="8f74b-115">O exemplo a seguir mostra como implementar indexadores de interface.</span><span class="sxs-lookup"><span data-stu-id="8f74b-115">The following example shows how to implement interface indexers.</span></span>

[!code-csharp[Implement](~/samples/snippets/csharp/interfaces/indexers.cs#ImplementInterface)]

[!code-csharp[DefineInterface](~/samples/snippets/csharp/interfaces/indexers.cs#ExampleCode)]

<span data-ttu-id="8f74b-116">No exemplo anterior, é possível usar a implementação de membro de interface explícita usando o nome totalmente qualificado do membro de interface.</span><span class="sxs-lookup"><span data-stu-id="8f74b-116">In the preceding example, you could use the explicit interface member implementation by using the fully qualified name of the interface member.</span></span> <span data-ttu-id="8f74b-117">Por exemplo</span><span class="sxs-lookup"><span data-stu-id="8f74b-117">For example</span></span>

```csharp
string IIndexInterface.this[int index]
{
}
```

<span data-ttu-id="8f74b-118">No entanto, o nome totalmente qualificado só será necessário para evitar ambiguidade quando a classe estiver implementando mais de uma interface com a mesma assinatura do indexador.</span><span class="sxs-lookup"><span data-stu-id="8f74b-118">However, the fully qualified name is only needed to avoid ambiguity when the class is implementing more than one interface with the same indexer signature.</span></span> <span data-ttu-id="8f74b-119">Por exemplo, se uma classe `Employee` estiver implementando dois interfaces, `ICitizen` e `IEmployee`, e as duas interfaces tiverem a mesma assinatura de indexador, a implementação de membro de interface explícita é necessária.</span><span class="sxs-lookup"><span data-stu-id="8f74b-119">For example, if an `Employee` class is implementing two interfaces, `ICitizen` and `IEmployee`, and both interfaces have the same indexer signature, the explicit interface member implementation is necessary.</span></span> <span data-ttu-id="8f74b-120">Ou seja, a seguinte declaração de indexador:</span><span class="sxs-lookup"><span data-stu-id="8f74b-120">That is, the following indexer declaration:</span></span>

```csharp
string IEmployee.this[int index]
{
}
```

<span data-ttu-id="8f74b-121">implementa o indexador na interface `IEmployee`, enquanto a seguinte declaração:</span><span class="sxs-lookup"><span data-stu-id="8f74b-121">implements the indexer on the `IEmployee` interface, while the following declaration:</span></span>

```csharp
string ICitizen.this[int index]
{
}
```

<span data-ttu-id="8f74b-122">implementa o indexador na interface `ICitizen`.</span><span class="sxs-lookup"><span data-stu-id="8f74b-122">implements the indexer on the `ICitizen` interface.</span></span>

## <a name="see-also"></a><span data-ttu-id="8f74b-123">Veja também</span><span class="sxs-lookup"><span data-stu-id="8f74b-123">See also</span></span>

- [<span data-ttu-id="8f74b-124">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="8f74b-124">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="8f74b-125">Indexadores</span><span class="sxs-lookup"><span data-stu-id="8f74b-125">Indexers</span></span>](./index.md)
- [<span data-ttu-id="8f74b-126">Propriedades</span><span class="sxs-lookup"><span data-stu-id="8f74b-126">Properties</span></span>](../classes-and-structs/properties.md)
- [<span data-ttu-id="8f74b-127">Interfaces</span><span class="sxs-lookup"><span data-stu-id="8f74b-127">Interfaces</span></span>](../interfaces/index.md)
