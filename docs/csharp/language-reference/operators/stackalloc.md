---
title: Operador stackalloc – referência do C#
ms.custom: seodec18
ms.date: 06/10/2019
f1_keywords:
- stackalloc_CSharpKeyword
helpviewer_keywords:
- stackalloc operator [C#]
ms.openlocfilehash: 3be4e827e75e4e26a34d9ed70423af5aa317e7fb
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67025010"
---
# <a name="stackalloc-operator-c-reference"></a><span data-ttu-id="89914-102">Operador stackalloc (referência do C#)</span><span class="sxs-lookup"><span data-stu-id="89914-102">stackalloc operator (C# reference)</span></span>

<span data-ttu-id="89914-103">O operador `stackalloc` aloca um bloco de memória na pilha.</span><span class="sxs-lookup"><span data-stu-id="89914-103">The `stackalloc` operator allocates a block of memory on the stack.</span></span> <span data-ttu-id="89914-104">Um bloco de memória alocado na pilha criado durante a execução do método é descartado automaticamente quando esse método é retornado.</span><span class="sxs-lookup"><span data-stu-id="89914-104">A stack allocated memory block created during the method execution is automatically discarded when that method returns.</span></span> <span data-ttu-id="89914-105">Não é possível liberar explicitamente a memória alocada com o operador `stackalloc`.</span><span class="sxs-lookup"><span data-stu-id="89914-105">You cannot explicitly free memory allocated with the `stackalloc` operator.</span></span> <span data-ttu-id="89914-106">Um bloco de memória alocado na pilha não está sujeito à [coleta de lixo](../../../standard/garbage-collection/index.md) e não precisa ser fixado com a [instrução `fixed`](../keywords/fixed-statement.md).</span><span class="sxs-lookup"><span data-stu-id="89914-106">A stack allocated memory block is not subject to [garbage collection](../../../standard/garbage-collection/index.md) and doesn't have to be pinned with the [`fixed` statement](../keywords/fixed-statement.md).</span></span>

<span data-ttu-id="89914-107">Você pode atribuir o resultado do operador `stackalloc` a uma variável de um dos seguintes tipos:</span><span class="sxs-lookup"><span data-stu-id="89914-107">You can assign the result of the `stackalloc` operator to a variable of one of the following types:</span></span>

- <span data-ttu-id="89914-108">A partir do C# 7.2, <xref:System.Span%601?displayProperty=nameWithType> ou <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>, como mostra o seguinte exemplo:</span><span class="sxs-lookup"><span data-stu-id="89914-108">Starting with C# 7.2, <xref:System.Span%601?displayProperty=nameWithType> or <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>, as the following example shows:</span></span>

  [!code-csharp[stackalloc span](~/samples/csharp/language-reference/operators/StackallocOperator.cs#AssignToSpan)]

  <span data-ttu-id="89914-109">Você não precisa usar um contexto [unsafe](../keywords/unsafe.md) quando atribui um bloco de memória alocado na pilha a uma variável <xref:System.Span%601> ou <xref:System.ReadOnlySpan%601>.</span><span class="sxs-lookup"><span data-stu-id="89914-109">You don't have to use an [unsafe](../keywords/unsafe.md) context when you assign a stack allocated memory block to a <xref:System.Span%601> or <xref:System.ReadOnlySpan%601> variable.</span></span>

  <span data-ttu-id="89914-110">Ao trabalhar com esses tipos, você pode usar uma expressão `stackalloc` em [condicional](conditional-operator.md) ou expressões de atribuição, como mostra o seguinte exemplo:</span><span class="sxs-lookup"><span data-stu-id="89914-110">When you work with those types, you can use a `stackalloc` expression in [conditional](conditional-operator.md) or assignment expressions, as the following example shows:</span></span>

  [!code-csharp[stackalloc expression](~/samples/csharp/language-reference/operators/StackallocOperator.cs#AsExpression)]

  > [!NOTE]
  > <span data-ttu-id="89914-111">É recomendável usar os tipos <xref:System.Span%601> ou <xref:System.ReadOnlySpan%601> sempre que possível para trabalhar com memória alocada na pilha.</span><span class="sxs-lookup"><span data-stu-id="89914-111">We recommend using <xref:System.Span%601> or <xref:System.ReadOnlySpan%601> types to work with stack allocated memory whenever possible.</span></span>

- <span data-ttu-id="89914-112">Um [tipo de ponteiro](../../programming-guide/unsafe-code-pointers/pointer-types.md), como mostra o seguinte exemplo:</span><span class="sxs-lookup"><span data-stu-id="89914-112">A [pointer type](../../programming-guide/unsafe-code-pointers/pointer-types.md), as the following example shows:</span></span>

  [!code-csharp[stackalloc pointer](~/samples/csharp/language-reference/operators/StackallocOperator.cs#AssignToPointer)]

  <span data-ttu-id="89914-113">Como mostra o exemplo anterior, você precisa usar um contexto `unsafe` ao trabalhar com tipos de ponteiro.</span><span class="sxs-lookup"><span data-stu-id="89914-113">As the preceding example shows, you must use an `unsafe` context when you work with pointer types.</span></span>

<span data-ttu-id="89914-114">O conteúdo da memória recém-alocada é indefinido.</span><span class="sxs-lookup"><span data-stu-id="89914-114">The content of the newly allocated memory is undefined.</span></span> <span data-ttu-id="89914-115">A partir do C# 7.3, você pode usar a sintaxe do inicializador de matriz para definir o conteúdo da memória recém-alocada.</span><span class="sxs-lookup"><span data-stu-id="89914-115">Starting with C# 7.3, you can use array initializer syntax to define the content of the newly allocated memory.</span></span> <span data-ttu-id="89914-116">O seguinte exemplo demonstra várias maneiras de fazer isso:</span><span class="sxs-lookup"><span data-stu-id="89914-116">The following example demonstrates various ways to do that:</span></span>

[!code-csharp[stackalloc initialization](~/samples/csharp/language-reference/operators/StackallocOperator.cs#StackallocInit)]

## <a name="security"></a><span data-ttu-id="89914-117">Segurança</span><span class="sxs-lookup"><span data-stu-id="89914-117">Security</span></span>

<span data-ttu-id="89914-118">O uso de `stackalloc` habilita automaticamente os recursos de detecção de estouro de buffer no CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="89914-118">The use of `stackalloc` automatically enables buffer overrun detection features in the common language runtime (CLR).</span></span> <span data-ttu-id="89914-119">Se for detectada uma estouro de buffer, o processo será encerrado assim que possível para minimizar a chance de o código mal-intencionado ser executado.</span><span class="sxs-lookup"><span data-stu-id="89914-119">If a buffer overrun is detected, the process is terminated as quickly as possible to minimize the chance that malicious code is executed.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="89914-120">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="89914-120">C# language specification</span></span>

<span data-ttu-id="89914-121">Para saber mais, confira a seção [Alocação de pilha](~/_csharplang/spec/unsafe-code.md#stack-allocation) da [Especificação da linguagem C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="89914-121">For more information, see the [Stack allocation](~/_csharplang/spec/unsafe-code.md#stack-allocation) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="89914-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="89914-122">See also</span></span>

- [<span data-ttu-id="89914-123">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="89914-123">C# reference</span></span>](../index.md)
- [<span data-ttu-id="89914-124">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="89914-124">C# operators</span></span>](index.md)
- [<span data-ttu-id="89914-125">Operadores relacionados a ponteiro</span><span class="sxs-lookup"><span data-stu-id="89914-125">Pointer related operators</span></span>](pointer-related-operators.md)
- [<span data-ttu-id="89914-126">Tipos de ponteiro</span><span class="sxs-lookup"><span data-stu-id="89914-126">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="89914-127">Tipos relativos a memória e extensão</span><span class="sxs-lookup"><span data-stu-id="89914-127">Memory and span-related types</span></span>](../../../standard/memory-and-spans/index.md)
