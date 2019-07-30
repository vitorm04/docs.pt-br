---
title: Tipos não gerenciados – referência em C#
ms.date: 07/23/2019
helpviewer_keywords:
- unmanaged type [C#]
ms.openlocfilehash: 2b675be5dbc61006725549f4b69284326650401d
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/26/2019
ms.locfileid: "68512069"
---
# <a name="unmanaged-types-c-reference"></a><span data-ttu-id="5a5c8-102">Tipos não gerenciados (referência em C#)</span><span class="sxs-lookup"><span data-stu-id="5a5c8-102">Unmanaged types (C# reference)</span></span>

<span data-ttu-id="5a5c8-103">Um **tipo não gerenciado** é todo tipo que não seja tipo de referência ou tipo construído (tipo que inclui pelo menos um argumento de tipo) e não contenha campos de tipo de referência ou tipo construído em qualquer nível de aninhamento.</span><span class="sxs-lookup"><span data-stu-id="5a5c8-103">An **unmanaged type** is any type that isn't a reference type or constructed type (a type that includes at least one type argument), and doesn't contain reference type or constructed type fields at any level of nesting.</span></span> <span data-ttu-id="5a5c8-104">Em outras palavras, um tipo não gerenciado é um dos seguintes:</span><span class="sxs-lookup"><span data-stu-id="5a5c8-104">In other words, an unmanaged type is one of the following:</span></span>

- <span data-ttu-id="5a5c8-105">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, `float`, `double`, `decimal` ou `bool`</span><span class="sxs-lookup"><span data-stu-id="5a5c8-105">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, `float`, `double`, `decimal`, or `bool`</span></span>
- <span data-ttu-id="5a5c8-106">Todo tipo [enumerado](../keywords/enum.md)</span><span class="sxs-lookup"><span data-stu-id="5a5c8-106">Any [enum](../keywords/enum.md) type</span></span>
- <span data-ttu-id="5a5c8-107">Todo tipo [ponteiro](../../programming-guide/unsafe-code-pointers/pointer-types.md)</span><span class="sxs-lookup"><span data-stu-id="5a5c8-107">Any [pointer](../../programming-guide/unsafe-code-pointers/pointer-types.md) type</span></span>
- <span data-ttu-id="5a5c8-108">Todo tipo [struct](../keywords/struct.md) definido pelo usuário que não seja tipo construído e contenha somente campos de tipos não gerenciados</span><span class="sxs-lookup"><span data-stu-id="5a5c8-108">Any user-defined [struct](../keywords/struct.md) type that is not a constructed type and contains fields of unmanaged types only</span></span>

<span data-ttu-id="5a5c8-109">Começando com o C# 7.3, você pode usar a restrição [`unmanaged`](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) para especificar que um parâmetro de tipo é um tipo não gerenciado diferente de ponteiro.</span><span class="sxs-lookup"><span data-stu-id="5a5c8-109">Beginning with C# 7.3, you can use the [`unmanaged` constraint](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) to specify that a type parameter is a non-pointer unmanaged type.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="5a5c8-110">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="5a5c8-110">C# language specification</span></span>

<span data-ttu-id="5a5c8-111">Para saber mais, confira a seção [Tipos de ponteiro](~/_csharplang/spec/unsafe-code.md#pointer-types) na [Especificação da linguagem C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="5a5c8-111">For more information, see the [Pointer types](~/_csharplang/spec/unsafe-code.md#pointer-types) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5a5c8-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5a5c8-112">See also</span></span>

- [<span data-ttu-id="5a5c8-113">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="5a5c8-113">C# reference</span></span>](../index.md)
- [<span data-ttu-id="5a5c8-114">Tipos de ponteiro</span><span class="sxs-lookup"><span data-stu-id="5a5c8-114">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="5a5c8-115">Tipos relativos a memória e extensão</span><span class="sxs-lookup"><span data-stu-id="5a5c8-115">Memory and span-related types</span></span>](../../../standard/memory-and-spans/index.md)
- [<span data-ttu-id="5a5c8-116">Operador sizeof</span><span class="sxs-lookup"><span data-stu-id="5a5c8-116">sizeof operator</span></span>](../operators/sizeof.md)
- [<span data-ttu-id="5a5c8-117">Operador stackalloc</span><span class="sxs-lookup"><span data-stu-id="5a5c8-117">stackalloc operator</span></span>](../operators/stackalloc.md)
