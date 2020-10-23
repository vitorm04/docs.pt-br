---
description: 'Saiba mais sobre os tipos não gerenciados em C #'
title: Tipos não gerenciados – referência em C#
ms.date: 09/06/2019
helpviewer_keywords:
- unmanaged type [C#]
ms.openlocfilehash: 4374872af13c94e1a1af6b9f2c431f076c6f7dff
ms.sourcegitcommit: 870bc4b4087510f6fba3c7b1c0d391f02bcc1f3e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/23/2020
ms.locfileid: "92471793"
---
# <a name="unmanaged-types-c-reference"></a><span data-ttu-id="ee5d4-103">Tipos não gerenciados (referência em C#)</span><span class="sxs-lookup"><span data-stu-id="ee5d4-103">Unmanaged types (C# reference)</span></span>

<span data-ttu-id="ee5d4-104">Um tipo é um **tipo não gerenciado** , se for qualquer um dos seguintes tipos:</span><span class="sxs-lookup"><span data-stu-id="ee5d4-104">A type is an **unmanaged type** if it's any of the following types:</span></span>

- <span data-ttu-id="ee5d4-105">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, `float`, `double`, `decimal` ou `bool`</span><span class="sxs-lookup"><span data-stu-id="ee5d4-105">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, `float`, `double`, `decimal`, or `bool`</span></span>
- <span data-ttu-id="ee5d4-106">Qualquer tipo de [Enumeração](enum.md)</span><span class="sxs-lookup"><span data-stu-id="ee5d4-106">Any [enum](enum.md) type</span></span>
- <span data-ttu-id="ee5d4-107">Qualquer tipo de [ponteiro](../../programming-guide/unsafe-code-pointers/pointer-types.md)</span><span class="sxs-lookup"><span data-stu-id="ee5d4-107">Any [pointer](../../programming-guide/unsafe-code-pointers/pointer-types.md) type</span></span>
- <span data-ttu-id="ee5d4-108">Qualquer tipo de [struct](struct.md) definido pelo usuário que contém campos de tipos não gerenciados somente e, em C# 7,3 e anterior, não é um tipo construído (um tipo que inclui pelo menos um argumento de tipo)</span><span class="sxs-lookup"><span data-stu-id="ee5d4-108">Any user-defined [struct](struct.md) type that contains fields of unmanaged types only and, in C# 7.3 and earlier, is not a constructed type (a type that includes at least one type argument)</span></span>

<span data-ttu-id="ee5d4-109">A partir do C# 7,3, você pode usar a [ `unmanaged` restrição](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) para especificar que um parâmetro de tipo é um tipo não gerenciado não-ponteiro e não anulável.</span><span class="sxs-lookup"><span data-stu-id="ee5d4-109">Beginning with C# 7.3, you can use the [`unmanaged` constraint](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) to specify that a type parameter is a non-pointer, non-nullable unmanaged type.</span></span>

<span data-ttu-id="ee5d4-110">A partir do C# 8,0, um tipo struct *construído* que contém campos de tipos não gerenciados também é não gerenciado, como mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="ee5d4-110">Beginning with C# 8.0, a *constructed* struct type that contains fields of unmanaged types only is also unmanaged, as the following example shows:</span></span>

[!code-csharp[unmanaged constructed types](snippets/shared/UnmanagedTypes.cs#ProgramExample)]

<span data-ttu-id="ee5d4-111">Uma estrutura genérica pode ser a fonte de tipos construídos não gerenciados e não gerenciados.</span><span class="sxs-lookup"><span data-stu-id="ee5d4-111">A generic struct may be the source of both unmanaged and not unmanaged constructed types.</span></span> <span data-ttu-id="ee5d4-112">O exemplo anterior define uma struct genérica `Coords<T>` e apresenta os exemplos de tipos construídos não gerenciados.</span><span class="sxs-lookup"><span data-stu-id="ee5d4-112">The preceding example defines a generic struct `Coords<T>` and presents the examples of unmanaged constructed types.</span></span> <span data-ttu-id="ee5d4-113">O exemplo de não é um tipo não gerenciado `Coords<object>` .</span><span class="sxs-lookup"><span data-stu-id="ee5d4-113">The example of not an unmanaged type is `Coords<object>`.</span></span> <span data-ttu-id="ee5d4-114">Não é não gerenciado porque tem os campos do `object` tipo, que não são gerenciados.</span><span class="sxs-lookup"><span data-stu-id="ee5d4-114">It's not unmanaged because it has the fields of the `object` type, which is not unmanaged.</span></span> <span data-ttu-id="ee5d4-115">Se você quiser que *todos os* tipos construídos sejam tipos não gerenciados, use a `unmanaged` restrição na definição de uma estrutura genérica:</span><span class="sxs-lookup"><span data-stu-id="ee5d4-115">If you want *all* constructed types to be unmanaged types, use the `unmanaged` constraint in the definition of a generic struct:</span></span>

[!code-csharp[unmanaged constraint in type definition](snippets/shared/UnmanagedTypes.cs#AlwaysUnmanaged)]

## <a name="c-language-specification"></a><span data-ttu-id="ee5d4-116">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="ee5d4-116">C# language specification</span></span>

<span data-ttu-id="ee5d4-117">Para saber mais, confira a seção [Tipos de ponteiro](~/_csharplang/spec/unsafe-code.md#pointer-types) na [Especificação da linguagem C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="ee5d4-117">For more information, see the [Pointer types](~/_csharplang/spec/unsafe-code.md#pointer-types) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ee5d4-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="ee5d4-118">See also</span></span>

- [<span data-ttu-id="ee5d4-119">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="ee5d4-119">C# reference</span></span>](../index.md)
- [<span data-ttu-id="ee5d4-120">Tipos de ponteiro</span><span class="sxs-lookup"><span data-stu-id="ee5d4-120">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="ee5d4-121">Tipos relacionados a memória e extensão</span><span class="sxs-lookup"><span data-stu-id="ee5d4-121">Memory and span-related types</span></span>](../../../standard/memory-and-spans/index.md)
- [<span data-ttu-id="ee5d4-122">Operador sizeof</span><span class="sxs-lookup"><span data-stu-id="ee5d4-122">sizeof operator</span></span>](../operators/sizeof.md)
- [<span data-ttu-id="ee5d4-123">stackalloc</span><span class="sxs-lookup"><span data-stu-id="ee5d4-123">stackalloc</span></span>](../operators/stackalloc.md)
