---
title: Indexadores em interfaces – Guia de Programação em C#
ms.date: 02/08/2020
helpviewer_keywords:
- indexers [C#], in interfaces
- accessors [C#], indexers
ms.assetid: e16b54bd-4a83-4f52-bd75-65819fca79e8
ms.openlocfilehash: 9ce6e4f0e0533c2880c6241f44409435248a336a
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287474"
---
# <a name="indexers-in-interfaces-c-programming-guide"></a><span data-ttu-id="13c2f-102">Indexadores em interfaces (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="13c2f-102">Indexers in Interfaces (C# Programming Guide)</span></span>

<span data-ttu-id="13c2f-103">Os indexadores podem ser declarados em uma [interface](../../language-reference/keywords/interface.md).</span><span class="sxs-lookup"><span data-stu-id="13c2f-103">Indexers can be declared on an [interface](../../language-reference/keywords/interface.md).</span></span> <span data-ttu-id="13c2f-104">Acessadores de indexadores de interface diferem dos acessadores de indexadores de [classe](../../language-reference/keywords/class.md) das seguintes maneiras:</span><span class="sxs-lookup"><span data-stu-id="13c2f-104">Accessors of interface indexers differ from the accessors of [class](../../language-reference/keywords/class.md) indexers in the following ways:</span></span>

- <span data-ttu-id="13c2f-105">Os acessadores de interface não usam modificadores.</span><span class="sxs-lookup"><span data-stu-id="13c2f-105">Interface accessors do not use modifiers.</span></span>
- <span data-ttu-id="13c2f-106">Um acessador de interface normalmente não tem um corpo.</span><span class="sxs-lookup"><span data-stu-id="13c2f-106">An interface accessor typically does not have a body.</span></span>

<span data-ttu-id="13c2f-107">A finalidade do acessador é indicar se o indexador é de leitura/gravação, somente leitura ou somente gravação.</span><span class="sxs-lookup"><span data-stu-id="13c2f-107">The purpose of the accessor is to indicate whether the indexer is read-write, read-only, or write-only.</span></span> <span data-ttu-id="13c2f-108">Você pode fornecer uma implementação para um indexador definido em uma interface, mas isso é raro.</span><span class="sxs-lookup"><span data-stu-id="13c2f-108">You may provide an implementation for an indexer defined in an interface, but this is rare.</span></span> <span data-ttu-id="13c2f-109">Normalmente, os indexadores definem uma API para acessar os campos de dados e os campos de dados não podem ser definidos em uma interface.</span><span class="sxs-lookup"><span data-stu-id="13c2f-109">Indexers typically define an API to access data fields, and data fields cannot be defined in an interface.</span></span>

<span data-ttu-id="13c2f-110">Este é um exemplo de um acessador de indexador de interface:</span><span class="sxs-lookup"><span data-stu-id="13c2f-110">The following is an example of an interface indexer accessor:</span></span>

[!code-csharp[DefineInterface](~/samples/snippets/csharp/interfaces/indexers.cs#DefineIndexer)]

<span data-ttu-id="13c2f-111">A assinatura de um indexador deve ser diferente das assinaturas de todos os outros indexadores declarados na mesma interface.</span><span class="sxs-lookup"><span data-stu-id="13c2f-111">The signature of an indexer must differ from the signatures of all other indexers declared in the same interface.</span></span>

## <a name="example"></a><span data-ttu-id="13c2f-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="13c2f-112">Example</span></span>

<span data-ttu-id="13c2f-113">O exemplo a seguir mostra como implementar indexadores de interface.</span><span class="sxs-lookup"><span data-stu-id="13c2f-113">The following example shows how to implement interface indexers.</span></span>

[!code-csharp[Implement](~/samples/snippets/csharp/interfaces/indexers.cs#ImplementInterface)]

[!code-csharp[DefineInterface](~/samples/snippets/csharp/interfaces/indexers.cs#ExampleCode)]

<span data-ttu-id="13c2f-114">No exemplo anterior, é possível usar a implementação de membro de interface explícita usando o nome totalmente qualificado do membro de interface.</span><span class="sxs-lookup"><span data-stu-id="13c2f-114">In the preceding example, you could use the explicit interface member implementation by using the fully qualified name of the interface member.</span></span> <span data-ttu-id="13c2f-115">Por exemplo</span><span class="sxs-lookup"><span data-stu-id="13c2f-115">For example</span></span>

```csharp
string IIndexInterface.this[int index]
{
}
```

<span data-ttu-id="13c2f-116">No entanto, o nome totalmente qualificado só será necessário para evitar ambiguidade quando a classe estiver implementando mais de uma interface com a mesma assinatura do indexador.</span><span class="sxs-lookup"><span data-stu-id="13c2f-116">However, the fully qualified name is only needed to avoid ambiguity when the class is implementing more than one interface with the same indexer signature.</span></span> <span data-ttu-id="13c2f-117">Por exemplo, se uma classe `Employee` estiver implementando dois interfaces, `ICitizen` e `IEmployee`, e as duas interfaces tiverem a mesma assinatura de indexador, a implementação de membro de interface explícita é necessária.</span><span class="sxs-lookup"><span data-stu-id="13c2f-117">For example, if an `Employee` class is implementing two interfaces, `ICitizen` and `IEmployee`, and both interfaces have the same indexer signature, the explicit interface member implementation is necessary.</span></span> <span data-ttu-id="13c2f-118">Ou seja, a seguinte declaração de indexador:</span><span class="sxs-lookup"><span data-stu-id="13c2f-118">That is, the following indexer declaration:</span></span>

```csharp
string IEmployee.this[int index]
{
}
```

<span data-ttu-id="13c2f-119">implementa o indexador na interface `IEmployee`, enquanto a seguinte declaração:</span><span class="sxs-lookup"><span data-stu-id="13c2f-119">implements the indexer on the `IEmployee` interface, while the following declaration:</span></span>

```csharp
string ICitizen.this[int index]
{
}
```

<span data-ttu-id="13c2f-120">implementa o indexador na interface `ICitizen`.</span><span class="sxs-lookup"><span data-stu-id="13c2f-120">implements the indexer on the `ICitizen` interface.</span></span>

## <a name="see-also"></a><span data-ttu-id="13c2f-121">Veja também</span><span class="sxs-lookup"><span data-stu-id="13c2f-121">See also</span></span>

- [<span data-ttu-id="13c2f-122">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="13c2f-122">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="13c2f-123">Indexadores</span><span class="sxs-lookup"><span data-stu-id="13c2f-123">Indexers</span></span>](./index.md)
- [<span data-ttu-id="13c2f-124">Propriedades</span><span class="sxs-lookup"><span data-stu-id="13c2f-124">Properties</span></span>](../classes-and-structs/properties.md)
- [<span data-ttu-id="13c2f-125">Interfaces</span><span class="sxs-lookup"><span data-stu-id="13c2f-125">Interfaces</span></span>](../interfaces/index.md)
