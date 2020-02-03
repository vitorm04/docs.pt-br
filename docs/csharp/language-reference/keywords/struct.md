---
title: struct – Referência de C#
ms.date: 07/20/2015
f1_keywords:
- struct_CSharpKeyword
helpviewer_keywords:
- struct keyword [C#]
- structs [C#], struct keyword
ms.assetid: ff3dd9b7-dc93-4720-8855-ef5558f65c7c
ms.openlocfilehash: 8d9a23a0813423571c894758257b284ad67a72e2
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744653"
---
# <a name="struct-c-reference"></a><span data-ttu-id="403bf-102">struct (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="403bf-102">struct (C# Reference)</span></span>

<span data-ttu-id="403bf-103">O tipo `struct` é um tipo de valor normalmente usado para encapsular pequenos grupos de variáveis relacionadas, tais como coordenadas de um retângulo ou as características de um item em um inventário.</span><span class="sxs-lookup"><span data-stu-id="403bf-103">A `struct` type is a value type that is typically used to encapsulate small groups of related variables, such as the coordinates of a rectangle or the characteristics of an item in an inventory.</span></span> <span data-ttu-id="403bf-104">O seguinte exemplo mostra uma declaração simples de struct:</span><span class="sxs-lookup"><span data-stu-id="403bf-104">The following example shows a simple struct declaration:</span></span>

```csharp
public struct Book
{
    public decimal price;
    public string title;
    public string author;
}
```

## <a name="remarks"></a><span data-ttu-id="403bf-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="403bf-105">Remarks</span></span>

<span data-ttu-id="403bf-106">Os structs também podem conter [construtores](../../programming-guide/classes-and-structs/constructors.md), [constantes](../../programming-guide/classes-and-structs/constants.md), [campos](../../programming-guide/classes-and-structs/fields.md), [métodos](../../programming-guide/classes-and-structs/methods.md), [propriedades](../../programming-guide/classes-and-structs/properties.md), [indexadores](../../programming-guide/indexers/index.md), [operadores](../operators/index.md), [eventos](../../programming-guide/events/index.md) e [tipos aninhados](../../programming-guide/classes-and-structs/nested-types.md), embora, se vários desses membros forem necessários, você deva considerar tonar seu tipo uma classe.</span><span class="sxs-lookup"><span data-stu-id="403bf-106">Structs can also contain [constructors](../../programming-guide/classes-and-structs/constructors.md), [constants](../../programming-guide/classes-and-structs/constants.md), [fields](../../programming-guide/classes-and-structs/fields.md), [methods](../../programming-guide/classes-and-structs/methods.md), [properties](../../programming-guide/classes-and-structs/properties.md), [indexers](../../programming-guide/indexers/index.md), [operators](../operators/index.md), [events](../../programming-guide/events/index.md), and [nested types](../../programming-guide/classes-and-structs/nested-types.md), although if several such members are required, you should consider making your type a class instead.</span></span>

<span data-ttu-id="403bf-107">Para obter exemplos, consulte [Usando structs](../../programming-guide/classes-and-structs/using-structs.md).</span><span class="sxs-lookup"><span data-stu-id="403bf-107">For examples, see [Using Structs](../../programming-guide/classes-and-structs/using-structs.md).</span></span>

<span data-ttu-id="403bf-108">Os structs podem implantar uma interface, mas não podem herdá-la de outra struct.</span><span class="sxs-lookup"><span data-stu-id="403bf-108">Structs can implement an interface but they cannot inherit from another struct.</span></span> <span data-ttu-id="403bf-109">Por esse motivo, os membros de struct não podem ser declarados como `protected`.</span><span class="sxs-lookup"><span data-stu-id="403bf-109">For that reason, struct members cannot be declared as `protected`.</span></span>

<span data-ttu-id="403bf-110">Para obter mais informações, consulte [Structs](../../programming-guide/classes-and-structs/structs.md).</span><span class="sxs-lookup"><span data-stu-id="403bf-110">For more information, see [Structs](../../programming-guide/classes-and-structs/structs.md).</span></span>

## <a name="examples"></a><span data-ttu-id="403bf-111">Exemplos</span><span class="sxs-lookup"><span data-stu-id="403bf-111">Examples</span></span>

<span data-ttu-id="403bf-112">Para obter exemplos e mais informações, consulte [Usando structs](../../programming-guide/classes-and-structs/using-structs.md).</span><span class="sxs-lookup"><span data-stu-id="403bf-112">For examples and more information, see [Using Structs](../../programming-guide/classes-and-structs/using-structs.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="403bf-113">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="403bf-113">C# language specification</span></span>

<span data-ttu-id="403bf-114">Para obter exemplos, consulte [Usando structs](../../programming-guide/classes-and-structs/using-structs.md).</span><span class="sxs-lookup"><span data-stu-id="403bf-114">For examples, see [Using Structs](../../programming-guide/classes-and-structs/using-structs.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="403bf-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="403bf-115">See also</span></span>

- [<span data-ttu-id="403bf-116">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="403bf-116">C# reference</span></span>](../index.md)
- [<span data-ttu-id="403bf-117">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="403bf-117">C# keywords</span></span>](index.md)
- [<span data-ttu-id="403bf-118">Tabela de tipos internos</span><span class="sxs-lookup"><span data-stu-id="403bf-118">Built-in types table</span></span>](built-in-types-table.md)
- [<span data-ttu-id="403bf-119">Tipos de valor</span><span class="sxs-lookup"><span data-stu-id="403bf-119">Value types</span></span>](../builtin-types/value-types.md)
- [<span data-ttu-id="403bf-120">class</span><span class="sxs-lookup"><span data-stu-id="403bf-120">class</span></span>](class.md)
- [<span data-ttu-id="403bf-121">interface</span><span class="sxs-lookup"><span data-stu-id="403bf-121">interface</span></span>](interface.md)
- [<span data-ttu-id="403bf-122">Classes e structs</span><span class="sxs-lookup"><span data-stu-id="403bf-122">Classes and structs</span></span>](../../programming-guide/classes-and-structs/index.md)
