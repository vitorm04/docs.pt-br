---
title: expressão stackalloc - Referência C#
ms.date: 03/13/2020
f1_keywords:
- stackalloc_CSharpKeyword
helpviewer_keywords:
- stackalloc expression [C#]
ms.openlocfilehash: 2e99ce8b1e44dfa040c1acac799a3a55b375bd91
ms.sourcegitcommit: 34dc3c0d0d0a1cc418abff259d9daa8078d00b81
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2020
ms.locfileid: "79546595"
---
# <a name="stackalloc-expression-c-reference"></a><span data-ttu-id="19b47-102">expressão stackalloc (referência C#)</span><span class="sxs-lookup"><span data-stu-id="19b47-102">stackalloc expression (C# reference)</span></span>

<span data-ttu-id="19b47-103">Uma `stackalloc` expressão aloca um bloco de memória na pilha.</span><span class="sxs-lookup"><span data-stu-id="19b47-103">A `stackalloc` expression allocates a block of memory on the stack.</span></span> <span data-ttu-id="19b47-104">Um bloco de memória alocado na pilha criado durante a execução do método é descartado automaticamente quando esse método é retornado.</span><span class="sxs-lookup"><span data-stu-id="19b47-104">A stack allocated memory block created during the method execution is automatically discarded when that method returns.</span></span> <span data-ttu-id="19b47-105">Você não pode liberar explicitamente `stackalloc`a memória alocada com .</span><span class="sxs-lookup"><span data-stu-id="19b47-105">You cannot explicitly free the memory allocated with `stackalloc`.</span></span> <span data-ttu-id="19b47-106">Um bloco de memória alocado em pilha não está sujeito à [coleta de lixo](../../../standard/garbage-collection/index.md) e não precisa ser fixado com uma [ `fixed` declaração](../keywords/fixed-statement.md).</span><span class="sxs-lookup"><span data-stu-id="19b47-106">A stack allocated memory block is not subject to [garbage collection](../../../standard/garbage-collection/index.md) and doesn't have to be pinned with a [`fixed` statement](../keywords/fixed-statement.md).</span></span>

<span data-ttu-id="19b47-107">Você pode atribuir o `stackalloc` resultado de uma expressão a uma variável de um dos seguintes tipos:</span><span class="sxs-lookup"><span data-stu-id="19b47-107">You can assign the result of a `stackalloc` expression to a variable of one of the following types:</span></span>

- <span data-ttu-id="19b47-108">Começando com C# 7.2, <xref:System.Span%601?displayProperty=nameWithType> ou <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>, como o exemplo a seguir mostra:</span><span class="sxs-lookup"><span data-stu-id="19b47-108">Beginning with C# 7.2, <xref:System.Span%601?displayProperty=nameWithType> or <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>, as the following example shows:</span></span>

  [!code-csharp[stackalloc span](snippets/StackallocOperator.cs#AssignToSpan)]

  <span data-ttu-id="19b47-109">Você não precisa usar um contexto [unsafe](../keywords/unsafe.md) quando atribui um bloco de memória alocado na pilha a uma variável <xref:System.Span%601> ou <xref:System.ReadOnlySpan%601>.</span><span class="sxs-lookup"><span data-stu-id="19b47-109">You don't have to use an [unsafe](../keywords/unsafe.md) context when you assign a stack allocated memory block to a <xref:System.Span%601> or <xref:System.ReadOnlySpan%601> variable.</span></span>

  <span data-ttu-id="19b47-110">Ao trabalhar com esses tipos, você pode usar uma expressão `stackalloc` em [condicional](conditional-operator.md) ou expressões de atribuição, como mostra o seguinte exemplo:</span><span class="sxs-lookup"><span data-stu-id="19b47-110">When you work with those types, you can use a `stackalloc` expression in [conditional](conditional-operator.md) or assignment expressions, as the following example shows:</span></span>

  [!code-csharp[stackalloc expression](snippets/StackallocOperator.cs#AsExpression)]

  <span data-ttu-id="19b47-111">Começando com C# 8.0, `stackalloc` você pode usar uma <xref:System.Span%601> <xref:System.ReadOnlySpan%601> expressão dentro de outras expressões sempre que uma ou variável for permitida, como mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="19b47-111">Beginning with C# 8.0, you can use a `stackalloc` expression inside other expressions whenever a <xref:System.Span%601> or <xref:System.ReadOnlySpan%601> variable is allowed, as the following example shows:</span></span>

  [!code-csharp[stackalloc in nested expressions](snippets/StackallocOperator.cs#Nested)]

  > [!NOTE]
  > <span data-ttu-id="19b47-112">É recomendável usar os tipos <xref:System.Span%601> ou <xref:System.ReadOnlySpan%601> sempre que possível para trabalhar com memória alocada na pilha.</span><span class="sxs-lookup"><span data-stu-id="19b47-112">We recommend using <xref:System.Span%601> or <xref:System.ReadOnlySpan%601> types to work with stack allocated memory whenever possible.</span></span>

- <span data-ttu-id="19b47-113">Um [tipo de ponteiro](../../programming-guide/unsafe-code-pointers/pointer-types.md), como mostra o seguinte exemplo:</span><span class="sxs-lookup"><span data-stu-id="19b47-113">A [pointer type](../../programming-guide/unsafe-code-pointers/pointer-types.md), as the following example shows:</span></span>

  [!code-csharp[stackalloc pointer](snippets/StackallocOperator.cs#AssignToPointer)]

  <span data-ttu-id="19b47-114">Como mostra o exemplo anterior, você precisa usar um contexto `unsafe` ao trabalhar com tipos de ponteiro.</span><span class="sxs-lookup"><span data-stu-id="19b47-114">As the preceding example shows, you must use an `unsafe` context when you work with pointer types.</span></span>

  <span data-ttu-id="19b47-115">No caso de tipos de ponteiros, você pode usar uma `stackalloc` expressão apenas em uma declaração de variável local para inicializar a variável.</span><span class="sxs-lookup"><span data-stu-id="19b47-115">In the case of pointer types, you can use a `stackalloc` expression only in a local variable declaration to initialize the variable.</span></span>

<span data-ttu-id="19b47-116">A quantidade de memória disponível na pilha é limitada.</span><span class="sxs-lookup"><span data-stu-id="19b47-116">The amount of memory available on the stack is limited.</span></span> <span data-ttu-id="19b47-117">Se você alocar muita memória na <xref:System.StackOverflowException> pilha, um é jogado.</span><span class="sxs-lookup"><span data-stu-id="19b47-117">If you allocate too much memory on the stack, a <xref:System.StackOverflowException> is thrown.</span></span> <span data-ttu-id="19b47-118">Para evitar isso, siga as regras abaixo:</span><span class="sxs-lookup"><span data-stu-id="19b47-118">To avoid that, follow the rules below:</span></span>

- <span data-ttu-id="19b47-119">Limitar a quantidade de `stackalloc`memória que você aloca com:</span><span class="sxs-lookup"><span data-stu-id="19b47-119">Limit the amount of memory you allocate with `stackalloc`:</span></span>

  [!code-csharp[limit stackalloc](snippets/StackallocOperator.cs#LimitStackalloc)]

  <span data-ttu-id="19b47-120">Como a quantidade de memória disponível na pilha depende do ambiente em que o código é executado, seja conservador quando definir o valor limite real.</span><span class="sxs-lookup"><span data-stu-id="19b47-120">Because the amount of memory available on the stack depends on the environment in which the code is executed, be conservative when you define the actual limit value.</span></span>

- <span data-ttu-id="19b47-121">Evite `stackalloc` usar loops internos.</span><span class="sxs-lookup"><span data-stu-id="19b47-121">Avoid using `stackalloc` inside loops.</span></span> <span data-ttu-id="19b47-122">Aloque o bloco de memória fora de um loop e reutilize-o dentro do loop.</span><span class="sxs-lookup"><span data-stu-id="19b47-122">Allocate the memory block outside a loop and reuse it inside the loop.</span></span>

<span data-ttu-id="19b47-123">O conteúdo da memória recém-alocada é indefinido.</span><span class="sxs-lookup"><span data-stu-id="19b47-123">The content of the newly allocated memory is undefined.</span></span> <span data-ttu-id="19b47-124">Você deve inicializá-lo antes do uso.</span><span class="sxs-lookup"><span data-stu-id="19b47-124">You should initialize it before the use.</span></span> <span data-ttu-id="19b47-125">Por exemplo, você <xref:System.Span%601.Clear%2A?displayProperty=nameWithType> pode usar o método que define todos `T`os itens para o valor padrão do tipo .</span><span class="sxs-lookup"><span data-stu-id="19b47-125">For example, you can use the <xref:System.Span%601.Clear%2A?displayProperty=nameWithType> method that sets all the items to the default value of type `T`.</span></span>

<span data-ttu-id="19b47-126">Começando com C# 7.3, você pode usar a sintaxe inicializadora de matriz para definir o conteúdo da memória recém-alocada.</span><span class="sxs-lookup"><span data-stu-id="19b47-126">Beginning with C# 7.3, you can use array initializer syntax to define the content of the newly allocated memory.</span></span> <span data-ttu-id="19b47-127">O seguinte exemplo demonstra várias maneiras de fazer isso:</span><span class="sxs-lookup"><span data-stu-id="19b47-127">The following example demonstrates various ways to do that:</span></span>

[!code-csharp[stackalloc initialization](snippets/StackallocOperator.cs#StackallocInit)]

<span data-ttu-id="19b47-128">Na `stackalloc T[E]`expressão, `T` deve ser um `E` tipo não [gerenciado](../builtin-types/unmanaged-types.md) e deve avaliar para um valor [int](../builtin-types/integral-numeric-types.md) não negativo.</span><span class="sxs-lookup"><span data-stu-id="19b47-128">In expression `stackalloc T[E]`, `T` must be an [unmanaged type](../builtin-types/unmanaged-types.md) and `E` must evaluate to a non-negative [int](../builtin-types/integral-numeric-types.md) value.</span></span>

## <a name="security"></a><span data-ttu-id="19b47-129">Segurança</span><span class="sxs-lookup"><span data-stu-id="19b47-129">Security</span></span>

<span data-ttu-id="19b47-130">O uso de `stackalloc` habilita automaticamente os recursos de detecção de estouro de buffer no CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="19b47-130">The use of `stackalloc` automatically enables buffer overrun detection features in the common language runtime (CLR).</span></span> <span data-ttu-id="19b47-131">Se for detectada uma estouro de buffer, o processo será encerrado assim que possível para minimizar a chance de o código mal-intencionado ser executado.</span><span class="sxs-lookup"><span data-stu-id="19b47-131">If a buffer overrun is detected, the process is terminated as quickly as possible to minimize the chance that malicious code is executed.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="19b47-132">especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="19b47-132">C# language specification</span></span>

<span data-ttu-id="19b47-133">Para obter mais informações, consulte a seção [de alocação Stack](~/_csharplang/spec/unsafe-code.md#stack-allocation) da especificação do [idioma C#](~/_csharplang/spec/introduction.md) e a Nota de recurso [ `stackalloc` Permitir em contextos aninhados.](~/_csharplang/proposals/csharp-8.0/nested-stackalloc.md)</span><span class="sxs-lookup"><span data-stu-id="19b47-133">For more information, see the [Stack allocation](~/_csharplang/spec/unsafe-code.md#stack-allocation) section of the [C# language specification](~/_csharplang/spec/introduction.md) and the [Permit `stackalloc` in nested contexts](~/_csharplang/proposals/csharp-8.0/nested-stackalloc.md) feature proposal note.</span></span>

## <a name="see-also"></a><span data-ttu-id="19b47-134">Confira também</span><span class="sxs-lookup"><span data-stu-id="19b47-134">See also</span></span>

- [<span data-ttu-id="19b47-135">Referência do C#</span><span class="sxs-lookup"><span data-stu-id="19b47-135">C# reference</span></span>](../index.md)
- [<span data-ttu-id="19b47-136">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="19b47-136">C# operators</span></span>](index.md)
- [<span data-ttu-id="19b47-137">Operadores relacionados a ponteiro</span><span class="sxs-lookup"><span data-stu-id="19b47-137">Pointer related operators</span></span>](pointer-related-operators.md)
- [<span data-ttu-id="19b47-138">Tipos de Ponteiro</span><span class="sxs-lookup"><span data-stu-id="19b47-138">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="19b47-139">Tipos relacionados a memória e extensão</span><span class="sxs-lookup"><span data-stu-id="19b47-139">Memory and span-related types</span></span>](../../../standard/memory-and-spans/index.md)
- [<span data-ttu-id="19b47-140">Dos e Don'ts de stackalloc</span><span class="sxs-lookup"><span data-stu-id="19b47-140">Dos and Don'ts of stackalloc</span></span>](https://vcsjones.dev/2020/02/24/stackalloc/)
