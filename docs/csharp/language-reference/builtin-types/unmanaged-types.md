---
title: Tipos não gerenciados – referência em C#
ms.date: 09/06/2019
helpviewer_keywords:
- unmanaged type [C#]
ms.openlocfilehash: 25aa42ba8c8f0023b4f818feb2edbb325f805fb6
ms.sourcegitcommit: c70542d02736e082e8dac67dad922c19249a8893
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2019
ms.locfileid: "70374109"
---
# <a name="unmanaged-types-c-reference"></a><span data-ttu-id="a11db-102">Tipos não gerenciados (referência em C#)</span><span class="sxs-lookup"><span data-stu-id="a11db-102">Unmanaged types (C# reference)</span></span>

<span data-ttu-id="a11db-103">Um tipo é um **tipo não gerenciado** , se for qualquer um dos seguintes tipos:</span><span class="sxs-lookup"><span data-stu-id="a11db-103">A type is an **unmanaged type** if it's any of the following types:</span></span>

- <span data-ttu-id="a11db-104">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, `float`, `double`, `decimal` ou `bool`</span><span class="sxs-lookup"><span data-stu-id="a11db-104">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, `float`, `double`, `decimal`, or `bool`</span></span>
- <span data-ttu-id="a11db-105">Todo tipo [enumerado](../keywords/enum.md)</span><span class="sxs-lookup"><span data-stu-id="a11db-105">Any [enum](../keywords/enum.md) type</span></span>
- <span data-ttu-id="a11db-106">Todo tipo [ponteiro](../../programming-guide/unsafe-code-pointers/pointer-types.md)</span><span class="sxs-lookup"><span data-stu-id="a11db-106">Any [pointer](../../programming-guide/unsafe-code-pointers/pointer-types.md) type</span></span>
- <span data-ttu-id="a11db-107">Qualquer tipo de [struct](../keywords/struct.md) definido pelo usuário que contém campos de tipos não gerenciados somente e, C# em 7,3 e anterior, não é um tipo construído (um tipo que inclui pelo menos um argumento de tipo)</span><span class="sxs-lookup"><span data-stu-id="a11db-107">Any user-defined [struct](../keywords/struct.md) type that contains fields of unmanaged types only and, in C# 7.3 and earlier, is not a constructed type (a type that includes at least one type argument)</span></span>

<span data-ttu-id="a11db-108">Começando com o C# 7.3, você pode usar a restrição [`unmanaged`](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) para especificar que um parâmetro de tipo é um tipo não gerenciado diferente de ponteiro.</span><span class="sxs-lookup"><span data-stu-id="a11db-108">Beginning with C# 7.3, you can use the [`unmanaged` constraint](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) to specify that a type parameter is a non-pointer unmanaged type.</span></span>

<span data-ttu-id="a11db-109">A partir C# do 8,0, um tipo struct *construído* que contém campos de tipos não gerenciados também é não gerenciado, como mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="a11db-109">Beginning with C# 8.0, a *constructed* struct type that contains fields of unmanaged types only is also unmanaged, as the following example shows:</span></span>

[!code-csharp[unmanaged constructed types](~/samples/csharp/language-reference/builtin-types/UnmanagedTypes.cs#ProgramExample)]

<span data-ttu-id="a11db-110">Uma estrutura genérica pode ser a fonte de tipos construídos não gerenciados e não gerenciados.</span><span class="sxs-lookup"><span data-stu-id="a11db-110">A generic struct may be the source of both unmanaged and not unmanaged constructed types.</span></span> <span data-ttu-id="a11db-111">O exemplo anterior define uma struct `Coords<T>` genérica e apresenta os exemplos de tipos construídos não gerenciados.</span><span class="sxs-lookup"><span data-stu-id="a11db-111">The preceding example defines a generic struct `Coords<T>` and presents the examples of unmanaged constructed types.</span></span> <span data-ttu-id="a11db-112">O exemplo de não é `Coords<object>`um tipo não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="a11db-112">The example of not an unmanaged type is `Coords<object>`.</span></span> <span data-ttu-id="a11db-113">Não é não gerenciado porque tem os campos do `object` tipo, que não são gerenciados.</span><span class="sxs-lookup"><span data-stu-id="a11db-113">It's not unmanaged because it has the fields of the `object` type, which is not unmanaged.</span></span> <span data-ttu-id="a11db-114">Se você quiser que *todos os* tipos construídos sejam tipos não gerenciados, use `unmanaged` a restrição na definição de uma estrutura genérica:</span><span class="sxs-lookup"><span data-stu-id="a11db-114">If you want *all* constructed types to be unmanaged types, use the `unmanaged` constraint in the definition of a generic struct:</span></span>

[!code-csharp[unmanaged constraint in type definition](~/samples/csharp/language-reference/builtin-types/UnmanagedTypes.cs#AlwaysUnmanaged)]

## <a name="c-language-specification"></a><span data-ttu-id="a11db-115">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="a11db-115">C# language specification</span></span>

<span data-ttu-id="a11db-116">Para saber mais, confira a seção [Tipos de ponteiro](~/_csharplang/spec/unsafe-code.md#pointer-types) na [Especificação da linguagem C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="a11db-116">For more information, see the [Pointer types](~/_csharplang/spec/unsafe-code.md#pointer-types) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a11db-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a11db-117">See also</span></span>

- [<span data-ttu-id="a11db-118">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="a11db-118">C# reference</span></span>](../index.md)
- [<span data-ttu-id="a11db-119">Tipos de ponteiro</span><span class="sxs-lookup"><span data-stu-id="a11db-119">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="a11db-120">Tipos relativos a memória e extensão</span><span class="sxs-lookup"><span data-stu-id="a11db-120">Memory and span-related types</span></span>](../../../standard/memory-and-spans/index.md)
- [<span data-ttu-id="a11db-121">Operador sizeof</span><span class="sxs-lookup"><span data-stu-id="a11db-121">sizeof operator</span></span>](../operators/sizeof.md)
- [<span data-ttu-id="a11db-122">Operador stackalloc</span><span class="sxs-lookup"><span data-stu-id="a11db-122">stackalloc operator</span></span>](../operators/stackalloc.md)
