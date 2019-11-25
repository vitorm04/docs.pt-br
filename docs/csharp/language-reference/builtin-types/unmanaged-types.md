---
title: Tipos não gerenciados – referência em C#
ms.date: 09/06/2019
helpviewer_keywords:
- unmanaged type [C#]
ms.openlocfilehash: 81eef59ceb20bcae6c749dd59578ce35da253826
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/20/2019
ms.locfileid: "74204482"
---
# <a name="unmanaged-types-c-reference"></a><span data-ttu-id="8a4c2-102">Tipos não gerenciados (referência em C#)</span><span class="sxs-lookup"><span data-stu-id="8a4c2-102">Unmanaged types (C# reference)</span></span>

<span data-ttu-id="8a4c2-103">A type is an **unmanaged type** if it's any of the following types:</span><span class="sxs-lookup"><span data-stu-id="8a4c2-103">A type is an **unmanaged type** if it's any of the following types:</span></span>

- <span data-ttu-id="8a4c2-104">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, `float`, `double`, `decimal` ou `bool`</span><span class="sxs-lookup"><span data-stu-id="8a4c2-104">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, `float`, `double`, `decimal`, or `bool`</span></span>
- <span data-ttu-id="8a4c2-105">Todo tipo [enumerado](../keywords/enum.md)</span><span class="sxs-lookup"><span data-stu-id="8a4c2-105">Any [enum](../keywords/enum.md) type</span></span>
- <span data-ttu-id="8a4c2-106">Todo tipo [ponteiro](../../programming-guide/unsafe-code-pointers/pointer-types.md)</span><span class="sxs-lookup"><span data-stu-id="8a4c2-106">Any [pointer](../../programming-guide/unsafe-code-pointers/pointer-types.md) type</span></span>
- <span data-ttu-id="8a4c2-107">Any user-defined [struct](../keywords/struct.md) type that contains fields of unmanaged types only and, in C# 7.3 and earlier, is not a constructed type (a type that includes at least one type argument)</span><span class="sxs-lookup"><span data-stu-id="8a4c2-107">Any user-defined [struct](../keywords/struct.md) type that contains fields of unmanaged types only and, in C# 7.3 and earlier, is not a constructed type (a type that includes at least one type argument)</span></span>

<span data-ttu-id="8a4c2-108">Beginning with C# 7.3, you can use the [`unmanaged` constraint](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) to specify that a type parameter is a non-pointer, non-nullable unmanaged type.</span><span class="sxs-lookup"><span data-stu-id="8a4c2-108">Beginning with C# 7.3, you can use the [`unmanaged` constraint](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) to specify that a type parameter is a non-pointer, non-nullable unmanaged type.</span></span>

<span data-ttu-id="8a4c2-109">Beginning with C# 8.0, a *constructed* struct type that contains fields of unmanaged types only is also unmanaged, as the following example shows:</span><span class="sxs-lookup"><span data-stu-id="8a4c2-109">Beginning with C# 8.0, a *constructed* struct type that contains fields of unmanaged types only is also unmanaged, as the following example shows:</span></span>

[!code-csharp[unmanaged constructed types](~/samples/csharp/language-reference/builtin-types/UnmanagedTypes.cs#ProgramExample)]

<span data-ttu-id="8a4c2-110">A generic struct may be the source of both unmanaged and not unmanaged constructed types.</span><span class="sxs-lookup"><span data-stu-id="8a4c2-110">A generic struct may be the source of both unmanaged and not unmanaged constructed types.</span></span> <span data-ttu-id="8a4c2-111">The preceding example defines a generic struct `Coords<T>` and presents the examples of unmanaged constructed types.</span><span class="sxs-lookup"><span data-stu-id="8a4c2-111">The preceding example defines a generic struct `Coords<T>` and presents the examples of unmanaged constructed types.</span></span> <span data-ttu-id="8a4c2-112">The example of not an unmanaged type is `Coords<object>`.</span><span class="sxs-lookup"><span data-stu-id="8a4c2-112">The example of not an unmanaged type is `Coords<object>`.</span></span> <span data-ttu-id="8a4c2-113">It's not unmanaged because it has the fields of the `object` type, which is not unmanaged.</span><span class="sxs-lookup"><span data-stu-id="8a4c2-113">It's not unmanaged because it has the fields of the `object` type, which is not unmanaged.</span></span> <span data-ttu-id="8a4c2-114">If you want *all* constructed types to be unmanaged types, use the `unmanaged` constraint in the definition of a generic struct:</span><span class="sxs-lookup"><span data-stu-id="8a4c2-114">If you want *all* constructed types to be unmanaged types, use the `unmanaged` constraint in the definition of a generic struct:</span></span>

[!code-csharp[unmanaged constraint in type definition](~/samples/csharp/language-reference/builtin-types/UnmanagedTypes.cs#AlwaysUnmanaged)]

## <a name="c-language-specification"></a><span data-ttu-id="8a4c2-115">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="8a4c2-115">C# language specification</span></span>

<span data-ttu-id="8a4c2-116">Para saber mais, confira a seção [Tipos de ponteiro](~/_csharplang/spec/unsafe-code.md#pointer-types) na [Especificação da linguagem C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="8a4c2-116">For more information, see the [Pointer types](~/_csharplang/spec/unsafe-code.md#pointer-types) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8a4c2-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8a4c2-117">See also</span></span>

- [<span data-ttu-id="8a4c2-118">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="8a4c2-118">C# reference</span></span>](../index.md)
- [<span data-ttu-id="8a4c2-119">Tipos de ponteiro</span><span class="sxs-lookup"><span data-stu-id="8a4c2-119">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="8a4c2-120">Tipos relativos a memória e extensão</span><span class="sxs-lookup"><span data-stu-id="8a4c2-120">Memory and span-related types</span></span>](../../../standard/memory-and-spans/index.md)
- [<span data-ttu-id="8a4c2-121">Operador sizeof</span><span class="sxs-lookup"><span data-stu-id="8a4c2-121">sizeof operator</span></span>](../operators/sizeof.md)
- [<span data-ttu-id="8a4c2-122">Operador stackalloc</span><span class="sxs-lookup"><span data-stu-id="8a4c2-122">stackalloc operator</span></span>](../operators/stackalloc.md)
