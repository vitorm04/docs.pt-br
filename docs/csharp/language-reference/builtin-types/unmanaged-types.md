---
title: Tipos não gerenciados – referência em C#
ms.date: 09/06/2019
helpviewer_keywords:
- unmanaged type [C#]
ms.openlocfilehash: 469309276c440493f6ed5b655139167f9a8b0885
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/03/2020
ms.locfileid: "78239736"
---
# <a name="unmanaged-types-c-reference"></a><span data-ttu-id="2129c-102">Tipos não gerenciados (referência em C#)</span><span class="sxs-lookup"><span data-stu-id="2129c-102">Unmanaged types (C# reference)</span></span>

<span data-ttu-id="2129c-103">Um tipo é um **tipo não gerenciado** , se for qualquer um dos seguintes tipos:</span><span class="sxs-lookup"><span data-stu-id="2129c-103">A type is an **unmanaged type** if it's any of the following types:</span></span>

- <span data-ttu-id="2129c-104">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, `float`, `double`, `decimal` ou `bool`</span><span class="sxs-lookup"><span data-stu-id="2129c-104">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, `float`, `double`, `decimal`, or `bool`</span></span>
- <span data-ttu-id="2129c-105">Todo tipo [enumerado](enum.md)</span><span class="sxs-lookup"><span data-stu-id="2129c-105">Any [enum](enum.md) type</span></span>
- <span data-ttu-id="2129c-106">Todo tipo [ponteiro](../../programming-guide/unsafe-code-pointers/pointer-types.md)</span><span class="sxs-lookup"><span data-stu-id="2129c-106">Any [pointer](../../programming-guide/unsafe-code-pointers/pointer-types.md) type</span></span>
- <span data-ttu-id="2129c-107">Qualquer tipo de [struct](struct.md) definido pelo usuário que contém campos de tipos não gerenciados somente e, C# em 7,3 e anterior, não é um tipo construído (um tipo que inclui pelo menos um argumento de tipo)</span><span class="sxs-lookup"><span data-stu-id="2129c-107">Any user-defined [struct](struct.md) type that contains fields of unmanaged types only and, in C# 7.3 and earlier, is not a constructed type (a type that includes at least one type argument)</span></span>

<span data-ttu-id="2129c-108">A partir C# do 7,3, você pode usar a [restrição`unmanaged`](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) para especificar que um parâmetro de tipo é um tipo não gerenciado não-ponteiro e não anulável.</span><span class="sxs-lookup"><span data-stu-id="2129c-108">Beginning with C# 7.3, you can use the [`unmanaged` constraint](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) to specify that a type parameter is a non-pointer, non-nullable unmanaged type.</span></span>

<span data-ttu-id="2129c-109">A partir C# do 8,0, um tipo struct *construído* que contém campos de tipos não gerenciados também é não gerenciado, como mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="2129c-109">Beginning with C# 8.0, a *constructed* struct type that contains fields of unmanaged types only is also unmanaged, as the following example shows:</span></span>

[!code-csharp[unmanaged constructed types](~/samples/snippets/csharp/language-reference/builtin-types/UnmanagedTypes.cs#ProgramExample)]

<span data-ttu-id="2129c-110">Uma estrutura genérica pode ser a fonte de tipos construídos não gerenciados e não gerenciados.</span><span class="sxs-lookup"><span data-stu-id="2129c-110">A generic struct may be the source of both unmanaged and not unmanaged constructed types.</span></span> <span data-ttu-id="2129c-111">O exemplo anterior define um struct genérico `Coords<T>` e apresenta os exemplos de tipos construídos não gerenciados.</span><span class="sxs-lookup"><span data-stu-id="2129c-111">The preceding example defines a generic struct `Coords<T>` and presents the examples of unmanaged constructed types.</span></span> <span data-ttu-id="2129c-112">O exemplo de um tipo não gerenciado é `Coords<object>`.</span><span class="sxs-lookup"><span data-stu-id="2129c-112">The example of not an unmanaged type is `Coords<object>`.</span></span> <span data-ttu-id="2129c-113">Não é não gerenciado porque tem os campos do tipo `object`, que não são gerenciados.</span><span class="sxs-lookup"><span data-stu-id="2129c-113">It's not unmanaged because it has the fields of the `object` type, which is not unmanaged.</span></span> <span data-ttu-id="2129c-114">Se você quiser que *todos os* tipos construídos sejam tipos não gerenciados, use a restrição `unmanaged` na definição de uma struct genérica:</span><span class="sxs-lookup"><span data-stu-id="2129c-114">If you want *all* constructed types to be unmanaged types, use the `unmanaged` constraint in the definition of a generic struct:</span></span>

[!code-csharp[unmanaged constraint in type definition](~/samples/snippets/csharp/language-reference/builtin-types/UnmanagedTypes.cs#AlwaysUnmanaged)]

## <a name="c-language-specification"></a><span data-ttu-id="2129c-115">especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="2129c-115">C# language specification</span></span>

<span data-ttu-id="2129c-116">Para saber mais, confira a seção [Tipos de ponteiro](~/_csharplang/spec/unsafe-code.md#pointer-types) na [Especificação da linguagem C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="2129c-116">For more information, see the [Pointer types](~/_csharplang/spec/unsafe-code.md#pointer-types) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2129c-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="2129c-117">See also</span></span>

- [<span data-ttu-id="2129c-118">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="2129c-118">C# reference</span></span>](../index.md)
- [<span data-ttu-id="2129c-119">Tipos de ponteiro</span><span class="sxs-lookup"><span data-stu-id="2129c-119">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="2129c-120">Tipos relativos a memória e extensão</span><span class="sxs-lookup"><span data-stu-id="2129c-120">Memory and span-related types</span></span>](../../../standard/memory-and-spans/index.md)
- [<span data-ttu-id="2129c-121">Operador sizeof</span><span class="sxs-lookup"><span data-stu-id="2129c-121">sizeof operator</span></span>](../operators/sizeof.md)
- [<span data-ttu-id="2129c-122">Operador stackalloc</span><span class="sxs-lookup"><span data-stu-id="2129c-122">stackalloc operator</span></span>](../operators/stackalloc.md)
