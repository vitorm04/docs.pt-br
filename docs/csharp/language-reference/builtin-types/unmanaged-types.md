---
title: Tipos não gerenciados – referência em C#
ms.date: 09/06/2019
helpviewer_keywords:
- unmanaged type [C#]
ms.openlocfilehash: 8a4599514115aa21f17c32848ce203fea704072e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78846452"
---
# <a name="unmanaged-types-c-reference"></a><span data-ttu-id="faccb-102">Tipos não gerenciados (referência em C#)</span><span class="sxs-lookup"><span data-stu-id="faccb-102">Unmanaged types (C# reference)</span></span>

<span data-ttu-id="faccb-103">Um tipo é um **tipo não gerenciado** se for algum dos seguintes tipos:</span><span class="sxs-lookup"><span data-stu-id="faccb-103">A type is an **unmanaged type** if it's any of the following types:</span></span>

- <span data-ttu-id="faccb-104">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, `float`, `double`, `decimal` ou `bool`</span><span class="sxs-lookup"><span data-stu-id="faccb-104">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, `float`, `double`, `decimal`, or `bool`</span></span>
- <span data-ttu-id="faccb-105">Qualquer [tipo de enum](enum.md)</span><span class="sxs-lookup"><span data-stu-id="faccb-105">Any [enum](enum.md) type</span></span>
- <span data-ttu-id="faccb-106">Qualquer [tipo de ponteiro](../../programming-guide/unsafe-code-pointers/pointer-types.md)</span><span class="sxs-lookup"><span data-stu-id="faccb-106">Any [pointer](../../programming-guide/unsafe-code-pointers/pointer-types.md) type</span></span>
- <span data-ttu-id="faccb-107">Qualquer tipo de [estrutura](struct.md) definido pelo usuário que contenha apenas campos de tipos não gerenciados e, em C# 7.3 e anterior, não é um tipo construído (um tipo que inclui pelo menos um tipo de argumento)</span><span class="sxs-lookup"><span data-stu-id="faccb-107">Any user-defined [struct](struct.md) type that contains fields of unmanaged types only and, in C# 7.3 and earlier, is not a constructed type (a type that includes at least one type argument)</span></span>

<span data-ttu-id="faccb-108">Começando com C# 7.3, [ `unmanaged` ](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) você pode usar a restrição para especificar que um parâmetro de tipo é um tipo não-ponteiro, não anulado não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="faccb-108">Beginning with C# 7.3, you can use the [`unmanaged` constraint](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) to specify that a type parameter is a non-pointer, non-nullable unmanaged type.</span></span>

<span data-ttu-id="faccb-109">Começando com C# 8.0, um tipo de estrutura *construída* que contém campos de tipos não gerenciados também não é gerenciado, como mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="faccb-109">Beginning with C# 8.0, a *constructed* struct type that contains fields of unmanaged types only is also unmanaged, as the following example shows:</span></span>

[!code-csharp[unmanaged constructed types](snippets/UnmanagedTypes.cs#ProgramExample)]

<span data-ttu-id="faccb-110">Uma estrutura genérica pode ser a fonte de ambos os tipos construídos não gerenciados e não não gerenciados.</span><span class="sxs-lookup"><span data-stu-id="faccb-110">A generic struct may be the source of both unmanaged and not unmanaged constructed types.</span></span> <span data-ttu-id="faccb-111">O exemplo anterior define uma `Coords<T>` estrutura genérica e apresenta os exemplos de tipos construídos não gerenciados.</span><span class="sxs-lookup"><span data-stu-id="faccb-111">The preceding example defines a generic struct `Coords<T>` and presents the examples of unmanaged constructed types.</span></span> <span data-ttu-id="faccb-112">O exemplo de não ser `Coords<object>`um tipo não gerenciado é .</span><span class="sxs-lookup"><span data-stu-id="faccb-112">The example of not an unmanaged type is `Coords<object>`.</span></span> <span data-ttu-id="faccb-113">Não é desgerenciado porque tem os `object` campos do tipo, que não é não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="faccb-113">It's not unmanaged because it has the fields of the `object` type, which is not unmanaged.</span></span> <span data-ttu-id="faccb-114">Se você quiser que *todos os* tipos construídos `unmanaged` sejam tipos não gerenciados, use a restrição na definição de uma estrutura genérica:</span><span class="sxs-lookup"><span data-stu-id="faccb-114">If you want *all* constructed types to be unmanaged types, use the `unmanaged` constraint in the definition of a generic struct:</span></span>

[!code-csharp[unmanaged constraint in type definition](snippets/UnmanagedTypes.cs#AlwaysUnmanaged)]

## <a name="c-language-specification"></a><span data-ttu-id="faccb-115">especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="faccb-115">C# language specification</span></span>

<span data-ttu-id="faccb-116">Para saber mais, confira a seção [Tipos de ponteiro](~/_csharplang/spec/unsafe-code.md#pointer-types) na [Especificação da linguagem C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="faccb-116">For more information, see the [Pointer types](~/_csharplang/spec/unsafe-code.md#pointer-types) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="faccb-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="faccb-117">See also</span></span>

- [<span data-ttu-id="faccb-118">Referência do C#</span><span class="sxs-lookup"><span data-stu-id="faccb-118">C# reference</span></span>](../index.md)
- [<span data-ttu-id="faccb-119">Tipos de Ponteiro</span><span class="sxs-lookup"><span data-stu-id="faccb-119">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="faccb-120">Tipos relacionados a memória e extensão</span><span class="sxs-lookup"><span data-stu-id="faccb-120">Memory and span-related types</span></span>](../../../standard/memory-and-spans/index.md)
- [<span data-ttu-id="faccb-121">tamanhodo operador</span><span class="sxs-lookup"><span data-stu-id="faccb-121">sizeof operator</span></span>](../operators/sizeof.md)
- [<span data-ttu-id="faccb-122">Operador stackalloc</span><span class="sxs-lookup"><span data-stu-id="faccb-122">stackalloc operator</span></span>](../operators/stackalloc.md)
