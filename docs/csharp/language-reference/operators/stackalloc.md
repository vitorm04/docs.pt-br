---
title: Operador stackalloc – referência do C#
ms.date: 09/20/2019
f1_keywords:
- stackalloc_CSharpKeyword
helpviewer_keywords:
- stackalloc operator [C#]
ms.openlocfilehash: 9c9767e0c9945a9589d049fa7abba192cb928ad5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78846241"
---
# <a name="stackalloc-operator-c-reference"></a><span data-ttu-id="61443-102">Operador stackalloc (referência do C#)</span><span class="sxs-lookup"><span data-stu-id="61443-102">stackalloc operator (C# reference)</span></span>

<span data-ttu-id="61443-103">O operador `stackalloc` aloca um bloco de memória na pilha.</span><span class="sxs-lookup"><span data-stu-id="61443-103">The `stackalloc` operator allocates a block of memory on the stack.</span></span> <span data-ttu-id="61443-104">Um bloco de memória alocado na pilha criado durante a execução do método é descartado automaticamente quando esse método é retornado.</span><span class="sxs-lookup"><span data-stu-id="61443-104">A stack allocated memory block created during the method execution is automatically discarded when that method returns.</span></span> <span data-ttu-id="61443-105">Não é possível liberar explicitamente a memória alocada com o operador `stackalloc`.</span><span class="sxs-lookup"><span data-stu-id="61443-105">You cannot explicitly free memory allocated with the `stackalloc` operator.</span></span> <span data-ttu-id="61443-106">Um bloco de memória alocado em pilha não está sujeito à [coleta de lixo](../../../standard/garbage-collection/index.md) e não precisa ser fixado com uma [ `fixed` declaração](../keywords/fixed-statement.md).</span><span class="sxs-lookup"><span data-stu-id="61443-106">A stack allocated memory block is not subject to [garbage collection](../../../standard/garbage-collection/index.md) and doesn't have to be pinned with a [`fixed` statement](../keywords/fixed-statement.md).</span></span>

<span data-ttu-id="61443-107">Você pode atribuir o resultado do operador `stackalloc` a uma variável de um dos seguintes tipos:</span><span class="sxs-lookup"><span data-stu-id="61443-107">You can assign the result of the `stackalloc` operator to a variable of one of the following types:</span></span>

- <span data-ttu-id="61443-108">Começando com C# 7.2, <xref:System.Span%601?displayProperty=nameWithType> ou <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>, como o exemplo a seguir mostra:</span><span class="sxs-lookup"><span data-stu-id="61443-108">Beginning with C# 7.2, <xref:System.Span%601?displayProperty=nameWithType> or <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>, as the following example shows:</span></span>

  [!code-csharp[stackalloc span](snippets/StackallocOperator.cs#AssignToSpan)]

  <span data-ttu-id="61443-109">Você não precisa usar um contexto [unsafe](../keywords/unsafe.md) quando atribui um bloco de memória alocado na pilha a uma variável <xref:System.Span%601> ou <xref:System.ReadOnlySpan%601>.</span><span class="sxs-lookup"><span data-stu-id="61443-109">You don't have to use an [unsafe](../keywords/unsafe.md) context when you assign a stack allocated memory block to a <xref:System.Span%601> or <xref:System.ReadOnlySpan%601> variable.</span></span>

  <span data-ttu-id="61443-110">Ao trabalhar com esses tipos, você pode usar uma expressão `stackalloc` em [condicional](conditional-operator.md) ou expressões de atribuição, como mostra o seguinte exemplo:</span><span class="sxs-lookup"><span data-stu-id="61443-110">When you work with those types, you can use a `stackalloc` expression in [conditional](conditional-operator.md) or assignment expressions, as the following example shows:</span></span>

  [!code-csharp[stackalloc expression](snippets/StackallocOperator.cs#AsExpression)]

  <span data-ttu-id="61443-111">Começando com C# 8.0, `stackalloc` você pode usar uma <xref:System.Span%601> <xref:System.ReadOnlySpan%601> expressão dentro de outras expressões sempre que uma ou variável for permitida, como mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="61443-111">Beginning with C# 8.0, you can use a `stackalloc` expression inside other expressions whenever a <xref:System.Span%601> or <xref:System.ReadOnlySpan%601> variable is allowed, as the following example shows:</span></span>

  [!code-csharp[stackalloc in nested expressions](snippets/StackallocOperator.cs#Nested)]

  > [!NOTE]
  > <span data-ttu-id="61443-112">É recomendável usar os tipos <xref:System.Span%601> ou <xref:System.ReadOnlySpan%601> sempre que possível para trabalhar com memória alocada na pilha.</span><span class="sxs-lookup"><span data-stu-id="61443-112">We recommend using <xref:System.Span%601> or <xref:System.ReadOnlySpan%601> types to work with stack allocated memory whenever possible.</span></span>

- <span data-ttu-id="61443-113">Um [tipo de ponteiro](../../programming-guide/unsafe-code-pointers/pointer-types.md), como mostra o seguinte exemplo:</span><span class="sxs-lookup"><span data-stu-id="61443-113">A [pointer type](../../programming-guide/unsafe-code-pointers/pointer-types.md), as the following example shows:</span></span>

  [!code-csharp[stackalloc pointer](snippets/StackallocOperator.cs#AssignToPointer)]

  <span data-ttu-id="61443-114">Como mostra o exemplo anterior, você precisa usar um contexto `unsafe` ao trabalhar com tipos de ponteiro.</span><span class="sxs-lookup"><span data-stu-id="61443-114">As the preceding example shows, you must use an `unsafe` context when you work with pointer types.</span></span>

  <span data-ttu-id="61443-115">No caso de tipos de ponteiros, você pode usar uma `stackalloc` expressão apenas em uma declaração de variável local para inicializar a variável.</span><span class="sxs-lookup"><span data-stu-id="61443-115">In the case of pointer types, you can use a `stackalloc` expression only in a local variable declaration to initialize the variable.</span></span>

<span data-ttu-id="61443-116">O conteúdo da memória recém-alocada é indefinido.</span><span class="sxs-lookup"><span data-stu-id="61443-116">The content of the newly allocated memory is undefined.</span></span> <span data-ttu-id="61443-117">Começando com C# 7.3, você pode usar a sintaxe inicializadora de matriz para definir o conteúdo da memória recém-alocada.</span><span class="sxs-lookup"><span data-stu-id="61443-117">Beginning with C# 7.3, you can use array initializer syntax to define the content of the newly allocated memory.</span></span> <span data-ttu-id="61443-118">O seguinte exemplo demonstra várias maneiras de fazer isso:</span><span class="sxs-lookup"><span data-stu-id="61443-118">The following example demonstrates various ways to do that:</span></span>

[!code-csharp[stackalloc initialization](snippets/StackallocOperator.cs#StackallocInit)]

<span data-ttu-id="61443-119">Na `stackalloc T[E]`expressão, `T` deve ser um `E` tipo não [gerenciado](../builtin-types/unmanaged-types.md) e deve ser uma expressão de tipo [int](../builtin-types/integral-numeric-types.md).</span><span class="sxs-lookup"><span data-stu-id="61443-119">In expression `stackalloc T[E]`, `T` must be an [unmanaged type](../builtin-types/unmanaged-types.md) and `E` must be an expression of type [int](../builtin-types/integral-numeric-types.md).</span></span>

## <a name="security"></a><span data-ttu-id="61443-120">Segurança</span><span class="sxs-lookup"><span data-stu-id="61443-120">Security</span></span>

<span data-ttu-id="61443-121">O uso de `stackalloc` habilita automaticamente os recursos de detecção de estouro de buffer no CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="61443-121">The use of `stackalloc` automatically enables buffer overrun detection features in the common language runtime (CLR).</span></span> <span data-ttu-id="61443-122">Se for detectada uma estouro de buffer, o processo será encerrado assim que possível para minimizar a chance de o código mal-intencionado ser executado.</span><span class="sxs-lookup"><span data-stu-id="61443-122">If a buffer overrun is detected, the process is terminated as quickly as possible to minimize the chance that malicious code is executed.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="61443-123">especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="61443-123">C# language specification</span></span>

<span data-ttu-id="61443-124">Para obter mais informações, consulte a seção [de alocação Stack](~/_csharplang/spec/unsafe-code.md#stack-allocation) da especificação do [idioma C#](~/_csharplang/spec/introduction.md) e a Nota de recurso [ `stackalloc` Permitir em contextos aninhados.](~/_csharplang/proposals/csharp-8.0/nested-stackalloc.md)</span><span class="sxs-lookup"><span data-stu-id="61443-124">For more information, see the [Stack allocation](~/_csharplang/spec/unsafe-code.md#stack-allocation) section of the [C# language specification](~/_csharplang/spec/introduction.md) and the [Permit `stackalloc` in nested contexts](~/_csharplang/proposals/csharp-8.0/nested-stackalloc.md) feature proposal note.</span></span>

## <a name="see-also"></a><span data-ttu-id="61443-125">Confira também</span><span class="sxs-lookup"><span data-stu-id="61443-125">See also</span></span>

- [<span data-ttu-id="61443-126">Referência do C#</span><span class="sxs-lookup"><span data-stu-id="61443-126">C# reference</span></span>](../index.md)
- [<span data-ttu-id="61443-127">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="61443-127">C# operators</span></span>](index.md)
- [<span data-ttu-id="61443-128">Operadores relacionados a ponteiro</span><span class="sxs-lookup"><span data-stu-id="61443-128">Pointer related operators</span></span>](pointer-related-operators.md)
- [<span data-ttu-id="61443-129">Tipos de Ponteiro</span><span class="sxs-lookup"><span data-stu-id="61443-129">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="61443-130">Tipos relacionados a memória e extensão</span><span class="sxs-lookup"><span data-stu-id="61443-130">Memory and span-related types</span></span>](../../../standard/memory-and-spans/index.md)
