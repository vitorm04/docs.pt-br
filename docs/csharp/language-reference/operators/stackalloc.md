---
title: expressão stackalloc-referência C#
ms.date: 03/13/2020
f1_keywords:
- stackalloc_CSharpKeyword
helpviewer_keywords:
- stackalloc expression [C#]
ms.openlocfilehash: 32ac85f678912cb7e5f506244265b1bf57d0b4aa
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87555600"
---
# <a name="stackalloc-expression-c-reference"></a><span data-ttu-id="8d6c9-102">expressão stackalloc (referência C#)</span><span class="sxs-lookup"><span data-stu-id="8d6c9-102">stackalloc expression (C# reference)</span></span>

<span data-ttu-id="8d6c9-103">Uma `stackalloc` expressão aloca um bloco de memória na pilha.</span><span class="sxs-lookup"><span data-stu-id="8d6c9-103">A `stackalloc` expression allocates a block of memory on the stack.</span></span> <span data-ttu-id="8d6c9-104">Um bloco de memória alocado na pilha criado durante a execução do método é descartado automaticamente quando esse método é retornado.</span><span class="sxs-lookup"><span data-stu-id="8d6c9-104">A stack allocated memory block created during the method execution is automatically discarded when that method returns.</span></span> <span data-ttu-id="8d6c9-105">Não é possível liberar explicitamente a memória alocada com `stackalloc` .</span><span class="sxs-lookup"><span data-stu-id="8d6c9-105">You cannot explicitly free the memory allocated with `stackalloc`.</span></span> <span data-ttu-id="8d6c9-106">Um bloco de memória alocado de pilha não está sujeito à [coleta de lixo](../../../standard/garbage-collection/index.md) e não precisa ser fixado com uma [ `fixed` instrução](../keywords/fixed-statement.md).</span><span class="sxs-lookup"><span data-stu-id="8d6c9-106">A stack allocated memory block is not subject to [garbage collection](../../../standard/garbage-collection/index.md) and doesn't have to be pinned with a [`fixed` statement](../keywords/fixed-statement.md).</span></span>

<span data-ttu-id="8d6c9-107">Você pode atribuir o resultado de uma `stackalloc` expressão a uma variável de um dos seguintes tipos:</span><span class="sxs-lookup"><span data-stu-id="8d6c9-107">You can assign the result of a `stackalloc` expression to a variable of one of the following types:</span></span>

- <span data-ttu-id="8d6c9-108">A partir do C# 7,2 <xref:System.Span%601?displayProperty=nameWithType> ou <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> , como mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="8d6c9-108">Beginning with C# 7.2, <xref:System.Span%601?displayProperty=nameWithType> or <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>, as the following example shows:</span></span>

  [!code-csharp[stackalloc span](snippets/StackallocOperator.cs#AssignToSpan)]

  <span data-ttu-id="8d6c9-109">Você não precisa usar um contexto [unsafe](../keywords/unsafe.md) quando atribui um bloco de memória alocado na pilha a uma variável <xref:System.Span%601> ou <xref:System.ReadOnlySpan%601>.</span><span class="sxs-lookup"><span data-stu-id="8d6c9-109">You don't have to use an [unsafe](../keywords/unsafe.md) context when you assign a stack allocated memory block to a <xref:System.Span%601> or <xref:System.ReadOnlySpan%601> variable.</span></span>

  <span data-ttu-id="8d6c9-110">Ao trabalhar com esses tipos, você pode usar uma expressão `stackalloc` em [condicional](conditional-operator.md) ou expressões de atribuição, como mostra o seguinte exemplo:</span><span class="sxs-lookup"><span data-stu-id="8d6c9-110">When you work with those types, you can use a `stackalloc` expression in [conditional](conditional-operator.md) or assignment expressions, as the following example shows:</span></span>

  [!code-csharp[stackalloc expression](snippets/StackallocOperator.cs#AsExpression)]

  <span data-ttu-id="8d6c9-111">A partir do C# 8,0, você pode usar uma `stackalloc` expressão dentro de outras expressões sempre que uma <xref:System.Span%601> <xref:System.ReadOnlySpan%601> variável ou é permitida, como mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="8d6c9-111">Beginning with C# 8.0, you can use a `stackalloc` expression inside other expressions whenever a <xref:System.Span%601> or <xref:System.ReadOnlySpan%601> variable is allowed, as the following example shows:</span></span>

  [!code-csharp[stackalloc in nested expressions](snippets/StackallocOperator.cs#Nested)]

  > [!NOTE]
  > <span data-ttu-id="8d6c9-112">É recomendável usar os tipos <xref:System.Span%601> ou <xref:System.ReadOnlySpan%601> sempre que possível para trabalhar com memória alocada na pilha.</span><span class="sxs-lookup"><span data-stu-id="8d6c9-112">We recommend using <xref:System.Span%601> or <xref:System.ReadOnlySpan%601> types to work with stack allocated memory whenever possible.</span></span>

- <span data-ttu-id="8d6c9-113">Um [tipo de ponteiro](../../programming-guide/unsafe-code-pointers/pointer-types.md), como mostra o seguinte exemplo:</span><span class="sxs-lookup"><span data-stu-id="8d6c9-113">A [pointer type](../../programming-guide/unsafe-code-pointers/pointer-types.md), as the following example shows:</span></span>

  [!code-csharp[stackalloc pointer](snippets/StackallocOperator.cs#AssignToPointer)]

  <span data-ttu-id="8d6c9-114">Como mostra o exemplo anterior, você precisa usar um contexto `unsafe` ao trabalhar com tipos de ponteiro.</span><span class="sxs-lookup"><span data-stu-id="8d6c9-114">As the preceding example shows, you must use an `unsafe` context when you work with pointer types.</span></span>

  <span data-ttu-id="8d6c9-115">No caso de tipos de ponteiro, você pode usar uma `stackalloc` expressão somente em uma declaração de variável local para inicializar a variável.</span><span class="sxs-lookup"><span data-stu-id="8d6c9-115">In the case of pointer types, you can use a `stackalloc` expression only in a local variable declaration to initialize the variable.</span></span>

<span data-ttu-id="8d6c9-116">A quantidade de memória disponível na pilha é limitada.</span><span class="sxs-lookup"><span data-stu-id="8d6c9-116">The amount of memory available on the stack is limited.</span></span> <span data-ttu-id="8d6c9-117">Se você alocar muita memória na pilha, um <xref:System.StackOverflowException> será lançado.</span><span class="sxs-lookup"><span data-stu-id="8d6c9-117">If you allocate too much memory on the stack, a <xref:System.StackOverflowException> is thrown.</span></span> <span data-ttu-id="8d6c9-118">Para evitar isso, siga as regras abaixo:</span><span class="sxs-lookup"><span data-stu-id="8d6c9-118">To avoid that, follow the rules below:</span></span>

- <span data-ttu-id="8d6c9-119">Limite a quantidade de memória que você aloca com `stackalloc` :</span><span class="sxs-lookup"><span data-stu-id="8d6c9-119">Limit the amount of memory you allocate with `stackalloc`:</span></span>

  [!code-csharp[limit stackalloc](snippets/StackallocOperator.cs#LimitStackalloc)]

  <span data-ttu-id="8d6c9-120">Como a quantidade de memória disponível na pilha depende do ambiente no qual o código é executado, seja conservador quando você define o valor de limite real.</span><span class="sxs-lookup"><span data-stu-id="8d6c9-120">Because the amount of memory available on the stack depends on the environment in which the code is executed, be conservative when you define the actual limit value.</span></span>

- <span data-ttu-id="8d6c9-121">Evite usar `stackalloc` loops internos.</span><span class="sxs-lookup"><span data-stu-id="8d6c9-121">Avoid using `stackalloc` inside loops.</span></span> <span data-ttu-id="8d6c9-122">Aloque o bloco de memória fora de um loop e reutilize-o dentro do loop.</span><span class="sxs-lookup"><span data-stu-id="8d6c9-122">Allocate the memory block outside a loop and reuse it inside the loop.</span></span>

<span data-ttu-id="8d6c9-123">O conteúdo da memória recém-alocada é indefinido.</span><span class="sxs-lookup"><span data-stu-id="8d6c9-123">The content of the newly allocated memory is undefined.</span></span> <span data-ttu-id="8d6c9-124">Você deve inicializá-lo antes do uso.</span><span class="sxs-lookup"><span data-stu-id="8d6c9-124">You should initialize it before the use.</span></span> <span data-ttu-id="8d6c9-125">Por exemplo, você pode usar o <xref:System.Span%601.Clear%2A?displayProperty=nameWithType> método que define todos os itens com o valor padrão do tipo `T` .</span><span class="sxs-lookup"><span data-stu-id="8d6c9-125">For example, you can use the <xref:System.Span%601.Clear%2A?displayProperty=nameWithType> method that sets all the items to the default value of type `T`.</span></span>

<span data-ttu-id="8d6c9-126">A partir do C# 7,3, você pode usar a sintaxe do inicializador de matriz para definir o conteúdo da memória alocada recentemente.</span><span class="sxs-lookup"><span data-stu-id="8d6c9-126">Beginning with C# 7.3, you can use array initializer syntax to define the content of the newly allocated memory.</span></span> <span data-ttu-id="8d6c9-127">O seguinte exemplo demonstra várias maneiras de fazer isso:</span><span class="sxs-lookup"><span data-stu-id="8d6c9-127">The following example demonstrates various ways to do that:</span></span>

[!code-csharp[stackalloc initialization](snippets/StackallocOperator.cs#StackallocInit)]

<span data-ttu-id="8d6c9-128">Em Expression `stackalloc T[E]` , `T` deve ser um [tipo não gerenciado](../builtin-types/unmanaged-types.md) e `E` deve ser avaliado como um valor [int](../builtin-types/integral-numeric-types.md) não negativo.</span><span class="sxs-lookup"><span data-stu-id="8d6c9-128">In expression `stackalloc T[E]`, `T` must be an [unmanaged type](../builtin-types/unmanaged-types.md) and `E` must evaluate to a non-negative [int](../builtin-types/integral-numeric-types.md) value.</span></span>

## <a name="security"></a><span data-ttu-id="8d6c9-129">Segurança</span><span class="sxs-lookup"><span data-stu-id="8d6c9-129">Security</span></span>

<span data-ttu-id="8d6c9-130">O uso de `stackalloc` habilita automaticamente os recursos de detecção de estouro de buffer no CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="8d6c9-130">The use of `stackalloc` automatically enables buffer overrun detection features in the common language runtime (CLR).</span></span> <span data-ttu-id="8d6c9-131">Se for detectada uma estouro de buffer, o processo será encerrado assim que possível para minimizar a chance de o código mal-intencionado ser executado.</span><span class="sxs-lookup"><span data-stu-id="8d6c9-131">If a buffer overrun is detected, the process is terminated as quickly as possible to minimize the chance that malicious code is executed.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="8d6c9-132">especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="8d6c9-132">C# language specification</span></span>

<span data-ttu-id="8d6c9-133">Para obter mais informações, consulte a seção de [alocação de pilha](~/_csharplang/spec/unsafe-code.md#stack-allocation) da [especificação da linguagem C#](~/_csharplang/spec/introduction.md) e a nota de proposta de recurso [permitir `stackalloc` em contextos aninhados](~/_csharplang/proposals/csharp-8.0/nested-stackalloc.md) .</span><span class="sxs-lookup"><span data-stu-id="8d6c9-133">For more information, see the [Stack allocation](~/_csharplang/spec/unsafe-code.md#stack-allocation) section of the [C# language specification](~/_csharplang/spec/introduction.md) and the [Permit `stackalloc` in nested contexts](~/_csharplang/proposals/csharp-8.0/nested-stackalloc.md) feature proposal note.</span></span>

## <a name="see-also"></a><span data-ttu-id="8d6c9-134">Confira também</span><span class="sxs-lookup"><span data-stu-id="8d6c9-134">See also</span></span>

- [<span data-ttu-id="8d6c9-135">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="8d6c9-135">C# reference</span></span>](../index.md)
- [<span data-ttu-id="8d6c9-136">Operadores e expressões C#</span><span class="sxs-lookup"><span data-stu-id="8d6c9-136">C# operators and expressions</span></span>](index.md)
- [<span data-ttu-id="8d6c9-137">Operadores relacionados a ponteiro</span><span class="sxs-lookup"><span data-stu-id="8d6c9-137">Pointer related operators</span></span>](pointer-related-operators.md)
- [<span data-ttu-id="8d6c9-138">Tipos de ponteiro</span><span class="sxs-lookup"><span data-stu-id="8d6c9-138">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="8d6c9-139">Tipos relacionados a memória e extensão</span><span class="sxs-lookup"><span data-stu-id="8d6c9-139">Memory and span-related types</span></span>](../../../standard/memory-and-spans/index.md)
- [<span data-ttu-id="8d6c9-140">Dos e não stackalloc</span><span class="sxs-lookup"><span data-stu-id="8d6c9-140">Dos and Don'ts of stackalloc</span></span>](https://vcsjones.dev/2020/02/24/stackalloc/)
