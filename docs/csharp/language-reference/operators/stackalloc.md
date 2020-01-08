---
title: Operador stackalloc – referência do C#
ms.custom: seodec18
ms.date: 09/20/2019
f1_keywords:
- stackalloc_CSharpKeyword
helpviewer_keywords:
- stackalloc operator [C#]
ms.openlocfilehash: 4f3ba6594eb16cf16db6a1de78fe05509c5f4d7d
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345280"
---
# <a name="stackalloc-operator-c-reference"></a><span data-ttu-id="63a08-102">Operador stackalloc (referência do C#)</span><span class="sxs-lookup"><span data-stu-id="63a08-102">stackalloc operator (C# reference)</span></span>

<span data-ttu-id="63a08-103">O operador `stackalloc` aloca um bloco de memória na pilha.</span><span class="sxs-lookup"><span data-stu-id="63a08-103">The `stackalloc` operator allocates a block of memory on the stack.</span></span> <span data-ttu-id="63a08-104">Um bloco de memória alocado na pilha criado durante a execução do método é descartado automaticamente quando esse método é retornado.</span><span class="sxs-lookup"><span data-stu-id="63a08-104">A stack allocated memory block created during the method execution is automatically discarded when that method returns.</span></span> <span data-ttu-id="63a08-105">Não é possível liberar explicitamente a memória alocada com o operador `stackalloc`.</span><span class="sxs-lookup"><span data-stu-id="63a08-105">You cannot explicitly free memory allocated with the `stackalloc` operator.</span></span> <span data-ttu-id="63a08-106">Um bloco de memória alocado de pilha não está sujeito à [coleta de lixo](../../../standard/garbage-collection/index.md) e não precisa ser fixado com uma [instrução`fixed`](../keywords/fixed-statement.md).</span><span class="sxs-lookup"><span data-stu-id="63a08-106">A stack allocated memory block is not subject to [garbage collection](../../../standard/garbage-collection/index.md) and doesn't have to be pinned with a [`fixed` statement](../keywords/fixed-statement.md).</span></span>

<span data-ttu-id="63a08-107">Você pode atribuir o resultado do operador `stackalloc` a uma variável de um dos seguintes tipos:</span><span class="sxs-lookup"><span data-stu-id="63a08-107">You can assign the result of the `stackalloc` operator to a variable of one of the following types:</span></span>

- <span data-ttu-id="63a08-108">A partir C# do 7,2, <xref:System.Span%601?displayProperty=nameWithType> ou <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>, como mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="63a08-108">Beginning with C# 7.2, <xref:System.Span%601?displayProperty=nameWithType> or <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>, as the following example shows:</span></span>

  [!code-csharp[stackalloc span](~/samples/csharp/language-reference/operators/StackallocOperator.cs#AssignToSpan)]

  <span data-ttu-id="63a08-109">Você não precisa usar um contexto [unsafe](../keywords/unsafe.md) quando atribui um bloco de memória alocado na pilha a uma variável <xref:System.Span%601> ou <xref:System.ReadOnlySpan%601>.</span><span class="sxs-lookup"><span data-stu-id="63a08-109">You don't have to use an [unsafe](../keywords/unsafe.md) context when you assign a stack allocated memory block to a <xref:System.Span%601> or <xref:System.ReadOnlySpan%601> variable.</span></span>

  <span data-ttu-id="63a08-110">Ao trabalhar com esses tipos, você pode usar uma expressão `stackalloc` em [condicional](conditional-operator.md) ou expressões de atribuição, como mostra o seguinte exemplo:</span><span class="sxs-lookup"><span data-stu-id="63a08-110">When you work with those types, you can use a `stackalloc` expression in [conditional](conditional-operator.md) or assignment expressions, as the following example shows:</span></span>

  [!code-csharp[stackalloc expression](~/samples/csharp/language-reference/operators/StackallocOperator.cs#AsExpression)]

  <span data-ttu-id="63a08-111">A partir C# do 8,0, você pode usar uma `stackalloc` expressão dentro de outras expressões sempre que uma variável <xref:System.Span%601> ou <xref:System.ReadOnlySpan%601> é permitida, como mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="63a08-111">Beginning with C# 8.0, you can use a `stackalloc` expression inside other expressions whenever a <xref:System.Span%601> or <xref:System.ReadOnlySpan%601> variable is allowed, as the following example shows:</span></span>

  [!code-csharp[stackalloc in nested expressions](~/samples/csharp/language-reference/operators/StackallocOperator.cs#Nested)]

  > [!NOTE]
  > <span data-ttu-id="63a08-112">É recomendável usar os tipos <xref:System.Span%601> ou <xref:System.ReadOnlySpan%601> sempre que possível para trabalhar com memória alocada na pilha.</span><span class="sxs-lookup"><span data-stu-id="63a08-112">We recommend using <xref:System.Span%601> or <xref:System.ReadOnlySpan%601> types to work with stack allocated memory whenever possible.</span></span>

- <span data-ttu-id="63a08-113">Um [tipo de ponteiro](../../programming-guide/unsafe-code-pointers/pointer-types.md), como mostra o seguinte exemplo:</span><span class="sxs-lookup"><span data-stu-id="63a08-113">A [pointer type](../../programming-guide/unsafe-code-pointers/pointer-types.md), as the following example shows:</span></span>

  [!code-csharp[stackalloc pointer](~/samples/csharp/language-reference/operators/StackallocOperator.cs#AssignToPointer)]

  <span data-ttu-id="63a08-114">Como mostra o exemplo anterior, você precisa usar um contexto `unsafe` ao trabalhar com tipos de ponteiro.</span><span class="sxs-lookup"><span data-stu-id="63a08-114">As the preceding example shows, you must use an `unsafe` context when you work with pointer types.</span></span>

  <span data-ttu-id="63a08-115">No caso de tipos de ponteiro, você pode usar uma `stackalloc` expressão somente em uma declaração de variável local para inicializar a variável.</span><span class="sxs-lookup"><span data-stu-id="63a08-115">In the case of pointer types, you can use a `stackalloc` expression only in a local variable declaration to initialize the variable.</span></span>

<span data-ttu-id="63a08-116">O conteúdo da memória recém-alocada é indefinido.</span><span class="sxs-lookup"><span data-stu-id="63a08-116">The content of the newly allocated memory is undefined.</span></span> <span data-ttu-id="63a08-117">A partir C# do 7,3, você pode usar a sintaxe do inicializador de matriz para definir o conteúdo da memória alocada recentemente.</span><span class="sxs-lookup"><span data-stu-id="63a08-117">Beginning with C# 7.3, you can use array initializer syntax to define the content of the newly allocated memory.</span></span> <span data-ttu-id="63a08-118">O seguinte exemplo demonstra várias maneiras de fazer isso:</span><span class="sxs-lookup"><span data-stu-id="63a08-118">The following example demonstrates various ways to do that:</span></span>

[!code-csharp[stackalloc initialization](~/samples/csharp/language-reference/operators/StackallocOperator.cs#StackallocInit)]

<span data-ttu-id="63a08-119">No Expression `stackalloc T[E]`, `T` deve ser um [tipo não gerenciado](../builtin-types/unmanaged-types.md) e `E` deve ser uma expressão do tipo [int](../builtin-types/integral-numeric-types.md).</span><span class="sxs-lookup"><span data-stu-id="63a08-119">In expression `stackalloc T[E]`, `T` must be an [unmanaged type](../builtin-types/unmanaged-types.md) and `E` must be an expression of type [int](../builtin-types/integral-numeric-types.md).</span></span>

## <a name="security"></a><span data-ttu-id="63a08-120">Segurança</span><span class="sxs-lookup"><span data-stu-id="63a08-120">Security</span></span>

<span data-ttu-id="63a08-121">O uso de `stackalloc` habilita automaticamente os recursos de detecção de estouro de buffer no CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="63a08-121">The use of `stackalloc` automatically enables buffer overrun detection features in the common language runtime (CLR).</span></span> <span data-ttu-id="63a08-122">Se for detectada uma estouro de buffer, o processo será encerrado assim que possível para minimizar a chance de o código mal-intencionado ser executado.</span><span class="sxs-lookup"><span data-stu-id="63a08-122">If a buffer overrun is detected, the process is terminated as quickly as possible to minimize the chance that malicious code is executed.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="63a08-123">especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="63a08-123">C# language specification</span></span>

<span data-ttu-id="63a08-124">Para obter mais informações, consulte a seção [alocação de pilha](~/_csharplang/spec/unsafe-code.md#stack-allocation) da especificação de [ C# linguagem](~/_csharplang/spec/introduction.md) e a nota de proposta de recurso de [`stackalloc` em contextos aninhados](~/_csharplang/proposals/csharp-8.0/nested-stackalloc.md) .</span><span class="sxs-lookup"><span data-stu-id="63a08-124">For more information, see the [Stack allocation](~/_csharplang/spec/unsafe-code.md#stack-allocation) section of the [C# language specification](~/_csharplang/spec/introduction.md) and the [Permit `stackalloc` in nested contexts](~/_csharplang/proposals/csharp-8.0/nested-stackalloc.md) feature proposal note.</span></span>

## <a name="see-also"></a><span data-ttu-id="63a08-125">Veja também</span><span class="sxs-lookup"><span data-stu-id="63a08-125">See also</span></span>

- [<span data-ttu-id="63a08-126">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="63a08-126">C# reference</span></span>](../index.md)
- [<span data-ttu-id="63a08-127">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="63a08-127">C# operators</span></span>](index.md)
- [<span data-ttu-id="63a08-128">Operadores relacionados a ponteiro</span><span class="sxs-lookup"><span data-stu-id="63a08-128">Pointer related operators</span></span>](pointer-related-operators.md)
- [<span data-ttu-id="63a08-129">Tipos de ponteiro</span><span class="sxs-lookup"><span data-stu-id="63a08-129">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="63a08-130">Tipos relativos a memória e extensão</span><span class="sxs-lookup"><span data-stu-id="63a08-130">Memory and span-related types</span></span>](../../../standard/memory-and-spans/index.md)
