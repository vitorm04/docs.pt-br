---
title: Indexadores em interfaces – Guia de Programação em C#
ms.date: 02/08/2020
helpviewer_keywords:
- indexers [C#], in interfaces
- accessors [C#], indexers
ms.assetid: e16b54bd-4a83-4f52-bd75-65819fca79e8
ms.openlocfilehash: 667a4213626ee37bfc5bf8c4fe78c2cf7186a73e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77627832"
---
# <a name="indexers-in-interfaces-c-programming-guide"></a><span data-ttu-id="c7ffb-102">Indexadores em interfaces (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="c7ffb-102">Indexers in Interfaces (C# Programming Guide)</span></span>

<span data-ttu-id="c7ffb-103">Os indexadores podem ser declarados em uma [interface](../../language-reference/keywords/interface.md).</span><span class="sxs-lookup"><span data-stu-id="c7ffb-103">Indexers can be declared on an [interface](../../language-reference/keywords/interface.md).</span></span> <span data-ttu-id="c7ffb-104">Acessadores de indexadores de interface diferem dos acessadores de indexadores de [classe](../../language-reference/keywords/class.md) das seguintes maneiras:</span><span class="sxs-lookup"><span data-stu-id="c7ffb-104">Accessors of interface indexers differ from the accessors of [class](../../language-reference/keywords/class.md) indexers in the following ways:</span></span>

- <span data-ttu-id="c7ffb-105">Os acessadores de interface não usam modificadores.</span><span class="sxs-lookup"><span data-stu-id="c7ffb-105">Interface accessors do not use modifiers.</span></span>
- <span data-ttu-id="c7ffb-106">Um acessório de interface normalmente não tem um corpo.</span><span class="sxs-lookup"><span data-stu-id="c7ffb-106">An interface accessor typically does not have a body.</span></span>

<span data-ttu-id="c7ffb-107">O objetivo do acessório é indicar se o indexador é leitura-gravação, somente leitura ou somente gravação.</span><span class="sxs-lookup"><span data-stu-id="c7ffb-107">The purpose of the accessor is to indicate whether the indexer is read-write, read-only, or write-only.</span></span> <span data-ttu-id="c7ffb-108">Você pode fornecer uma implementação para um indexador definido em uma interface, mas isso é raro.</span><span class="sxs-lookup"><span data-stu-id="c7ffb-108">You may provide an implementation for an indexer defined in an interface, but this is rare.</span></span> <span data-ttu-id="c7ffb-109">Os indexadores normalmente definem uma API para acessar campos de dados, e os campos de dados não podem ser definidos em uma interface.</span><span class="sxs-lookup"><span data-stu-id="c7ffb-109">Indexers typically define an API to access data fields, and data fields cannot be defined in an interface.</span></span>

<span data-ttu-id="c7ffb-110">Este é um exemplo de um acessador de indexador de interface:</span><span class="sxs-lookup"><span data-stu-id="c7ffb-110">The following is an example of an interface indexer accessor:</span></span>

[!code-csharp[DefineInterface](~/samples/snippets/csharp/interfaces/indexers.cs#DefineIndexer)]

<span data-ttu-id="c7ffb-111">A assinatura de um indexador deve ser diferente das assinaturas de todos os outros indexadores declarados na mesma interface.</span><span class="sxs-lookup"><span data-stu-id="c7ffb-111">The signature of an indexer must differ from the signatures of all other indexers declared in the same interface.</span></span>

## <a name="example"></a><span data-ttu-id="c7ffb-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c7ffb-112">Example</span></span>

<span data-ttu-id="c7ffb-113">O exemplo a seguir mostra como implementar indexadores de interface.</span><span class="sxs-lookup"><span data-stu-id="c7ffb-113">The following example shows how to implement interface indexers.</span></span>

[!code-csharp[Implement](~/samples/snippets/csharp/interfaces/indexers.cs#ImplementInterface)]

[!code-csharp[DefineInterface](~/samples/snippets/csharp/interfaces/indexers.cs#ExampleCode)]

<span data-ttu-id="c7ffb-114">No exemplo anterior, é possível usar a implementação de membro de interface explícita usando o nome totalmente qualificado do membro de interface.</span><span class="sxs-lookup"><span data-stu-id="c7ffb-114">In the preceding example, you could use the explicit interface member implementation by using the fully qualified name of the interface member.</span></span> <span data-ttu-id="c7ffb-115">Por exemplo</span><span class="sxs-lookup"><span data-stu-id="c7ffb-115">For example</span></span>

```csharp
string IIndexInterface.this[int index]
{
}
```

<span data-ttu-id="c7ffb-116">No entanto, o nome totalmente qualificado só será necessário para evitar ambiguidade quando a classe estiver implementando mais de uma interface com a mesma assinatura do indexador.</span><span class="sxs-lookup"><span data-stu-id="c7ffb-116">However, the fully qualified name is only needed to avoid ambiguity when the class is implementing more than one interface with the same indexer signature.</span></span> <span data-ttu-id="c7ffb-117">Por exemplo, se uma classe `Employee` estiver implementando dois interfaces, `ICitizen` e `IEmployee`, e as duas interfaces tiverem a mesma assinatura de indexador, a implementação de membro de interface explícita é necessária.</span><span class="sxs-lookup"><span data-stu-id="c7ffb-117">For example, if an `Employee` class is implementing two interfaces, `ICitizen` and `IEmployee`, and both interfaces have the same indexer signature, the explicit interface member implementation is necessary.</span></span> <span data-ttu-id="c7ffb-118">Ou seja, a seguinte declaração de indexador:</span><span class="sxs-lookup"><span data-stu-id="c7ffb-118">That is, the following indexer declaration:</span></span>

```csharp
string IEmployee.this[int index]
{
}
``

implements the indexer on the `IEmployee` interface, while the following declaration:

```csharp
string ICitizen.this[int index]
{
}
```

<span data-ttu-id="c7ffb-119">implementa o indexador na interface `ICitizen`.</span><span class="sxs-lookup"><span data-stu-id="c7ffb-119">implements the indexer on the `ICitizen` interface.</span></span>

## <a name="see-also"></a><span data-ttu-id="c7ffb-120">Confira também</span><span class="sxs-lookup"><span data-stu-id="c7ffb-120">See also</span></span>

- [<span data-ttu-id="c7ffb-121">C# Guia de Programação</span><span class="sxs-lookup"><span data-stu-id="c7ffb-121">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="c7ffb-122">Indexadores</span><span class="sxs-lookup"><span data-stu-id="c7ffb-122">Indexers</span></span>](./index.md)
- [<span data-ttu-id="c7ffb-123">Propriedades</span><span class="sxs-lookup"><span data-stu-id="c7ffb-123">Properties</span></span>](../classes-and-structs/properties.md)
- [<span data-ttu-id="c7ffb-124">Interfaces</span><span class="sxs-lookup"><span data-stu-id="c7ffb-124">Interfaces</span></span>](../interfaces/index.md)
