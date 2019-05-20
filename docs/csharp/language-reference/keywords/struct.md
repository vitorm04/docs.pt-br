---
title: struct – Referência de C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- struct_CSharpKeyword
helpviewer_keywords:
- struct keyword [C#]
- structs [C#], struct keyword
ms.assetid: ff3dd9b7-dc93-4720-8855-ef5558f65c7c
ms.openlocfilehash: 5317ea403575dca7ed64a5784fa9c993fa8d2f64
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65633817"
---
# <a name="struct-c-reference"></a><span data-ttu-id="32593-102">struct (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="32593-102">struct (C# Reference)</span></span>

<span data-ttu-id="32593-103">O tipo `struct` é um tipo de valor normalmente usado para encapsular pequenos grupos de variáveis relacionadas, tais como coordenadas de um retângulo ou as características de um item em um inventário.</span><span class="sxs-lookup"><span data-stu-id="32593-103">A `struct` type is a value type that is typically used to encapsulate small groups of related variables, such as the coordinates of a rectangle or the characteristics of an item in an inventory.</span></span> <span data-ttu-id="32593-104">O seguinte exemplo mostra uma declaração simples de struct:</span><span class="sxs-lookup"><span data-stu-id="32593-104">The following example shows a simple struct declaration:</span></span>

```csharp
public struct Book
{
    public decimal price;
    public string title;
    public string author;
}
```

## <a name="remarks"></a><span data-ttu-id="32593-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="32593-105">Remarks</span></span>

<span data-ttu-id="32593-106">Os structs também podem conter [construtores](../../programming-guide/classes-and-structs/constructors.md), [constantes](../../programming-guide/classes-and-structs/constants.md), [campos](../../programming-guide/classes-and-structs/fields.md), [métodos](../../programming-guide/classes-and-structs/methods.md), [propriedades](../../programming-guide/classes-and-structs/properties.md), [indexadores](../../programming-guide/indexers/index.md), [operadores](../../programming-guide/statements-expressions-operators/operators.md), [eventos](../../programming-guide/events/index.md) e [tipos aninhados](../../programming-guide/classes-and-structs/nested-types.md), embora, se vários desses membros forem necessários, você deva considerar tonar seu tipo uma classe.</span><span class="sxs-lookup"><span data-stu-id="32593-106">Structs can also contain [constructors](../../programming-guide/classes-and-structs/constructors.md), [constants](../../programming-guide/classes-and-structs/constants.md), [fields](../../programming-guide/classes-and-structs/fields.md), [methods](../../programming-guide/classes-and-structs/methods.md), [properties](../../programming-guide/classes-and-structs/properties.md), [indexers](../../programming-guide/indexers/index.md), [operators](../../programming-guide/statements-expressions-operators/operators.md), [events](../../programming-guide/events/index.md), and [nested types](../../programming-guide/classes-and-structs/nested-types.md), although if several such members are required, you should consider making your type a class instead.</span></span>

<span data-ttu-id="32593-107">Para obter exemplos, consulte [Usando structs](../../programming-guide/classes-and-structs/using-structs.md).</span><span class="sxs-lookup"><span data-stu-id="32593-107">For examples, see [Using Structs](../../programming-guide/classes-and-structs/using-structs.md).</span></span>

<span data-ttu-id="32593-108">Os structs podem implantar uma interface, mas não podem herdá-la de outra struct.</span><span class="sxs-lookup"><span data-stu-id="32593-108">Structs can implement an interface but they cannot inherit from another struct.</span></span> <span data-ttu-id="32593-109">Por esse motivo, os membros de struct não podem ser declarados como `protected`.</span><span class="sxs-lookup"><span data-stu-id="32593-109">For that reason, struct members cannot be declared as `protected`.</span></span>

<span data-ttu-id="32593-110">Para obter mais informações, consulte [Structs](../../programming-guide/classes-and-structs/structs.md).</span><span class="sxs-lookup"><span data-stu-id="32593-110">For more information, see [Structs](../../programming-guide/classes-and-structs/structs.md).</span></span>

## <a name="examples"></a><span data-ttu-id="32593-111">Exemplos</span><span class="sxs-lookup"><span data-stu-id="32593-111">Examples</span></span>

<span data-ttu-id="32593-112">Para obter exemplos e mais informações, consulte [Usando structs](../../programming-guide/classes-and-structs/using-structs.md).</span><span class="sxs-lookup"><span data-stu-id="32593-112">For examples and more information, see [Using Structs](../../programming-guide/classes-and-structs/using-structs.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="32593-113">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="32593-113">C# language specification</span></span>

<span data-ttu-id="32593-114">Para obter exemplos, consulte [Usando structs](../../programming-guide/classes-and-structs/using-structs.md).</span><span class="sxs-lookup"><span data-stu-id="32593-114">For examples, see [Using Structs](../../programming-guide/classes-and-structs/using-structs.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="32593-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="32593-115">See also</span></span>

- [<span data-ttu-id="32593-116">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="32593-116">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="32593-117">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="32593-117">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="32593-118">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="32593-118">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="32593-119">Tabela de valores padrão</span><span class="sxs-lookup"><span data-stu-id="32593-119">Default Values Table</span></span>](default-values-table.md)
- [<span data-ttu-id="32593-120">Tabela de tipos internos</span><span class="sxs-lookup"><span data-stu-id="32593-120">Built-In Types Table</span></span>](built-in-types-table.md)
- [<span data-ttu-id="32593-121">Tipos</span><span class="sxs-lookup"><span data-stu-id="32593-121">Types</span></span>](types.md)
- [<span data-ttu-id="32593-122">Tipos de valor</span><span class="sxs-lookup"><span data-stu-id="32593-122">Value Types</span></span>](value-types.md)
- [<span data-ttu-id="32593-123">class</span><span class="sxs-lookup"><span data-stu-id="32593-123">class</span></span>](class.md)
- [<span data-ttu-id="32593-124">interface</span><span class="sxs-lookup"><span data-stu-id="32593-124">interface</span></span>](interface.md)
- [<span data-ttu-id="32593-125">Classes e Structs</span><span class="sxs-lookup"><span data-stu-id="32593-125">Classes and Structs</span></span>](../../programming-guide/classes-and-structs/index.md)
