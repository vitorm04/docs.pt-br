---
title: Palavra-chave stackalloc – Referência de C#
ms.custom: seodec18
ms.date: 04/12/2018
f1_keywords:
- stackalloc_CSharpKeyword
- stackalloc
helpviewer_keywords:
- stackalloc keyword [C#]
ms.openlocfilehash: 61a27e777a1919a2a6fc5140a311835a8f3daba9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59480801"
---
# <a name="stackalloc-c-reference"></a><span data-ttu-id="d7c27-102">stackalloc (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="d7c27-102">stackalloc (C# Reference)</span></span>

<span data-ttu-id="d7c27-103">A palavra-chave `stackalloc` é usada para alocar um bloco de memória na pilha.</span><span class="sxs-lookup"><span data-stu-id="d7c27-103">The `stackalloc` keyword is used to allocate a block of memory on the stack.</span></span>

```csharp
Span<int> block = stackalloc int[100];
```

<span data-ttu-id="d7c27-104">Atribuir o bloco alocado a um <xref:System.Span%601?displayName=nameWithType> em vez de um `int*` permite alocações de pilha em um bloco seguro.</span><span class="sxs-lookup"><span data-stu-id="d7c27-104">Assigning the allocated block to a <xref:System.Span%601?displayName=nameWithType> instead of an `int*` allows stack allocations in a safe block.</span></span> <span data-ttu-id="d7c27-105">O contexto `unsafe` não é obrigatório.</span><span class="sxs-lookup"><span data-stu-id="d7c27-105">The `unsafe` context is not required.</span></span>

## <a name="remarks"></a><span data-ttu-id="d7c27-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="d7c27-106">Remarks</span></span>

<span data-ttu-id="d7c27-107">A palavra-chave é válida somente em inicializadores de variável locais.</span><span class="sxs-lookup"><span data-stu-id="d7c27-107">The keyword is valid only in local variable initializers.</span></span> <span data-ttu-id="d7c27-108">O código a seguir gera erros de compilador.</span><span class="sxs-lookup"><span data-stu-id="d7c27-108">The following code causes compiler errors.</span></span>

```csharp
int* block;
// The following assignment statement causes compiler errors. You
// can use stackalloc only when declaring and initializing a local
// variable.
block = stackalloc int[100];
Span<int> span;
// The following assignment statement causes compiler errors. You
// can use stackalloc only when declaring and initializing a local
// variable.
span = stackalloc int[100];
```

<span data-ttu-id="d7c27-109">A partir do C# 7.3, é possível usar a sintaxe do inicializador de matriz para matrizes de `stackalloc`.</span><span class="sxs-lookup"><span data-stu-id="d7c27-109">Beginning with C# 7.3, you can use array initializer syntax for `stackalloc` arrays.</span></span> <span data-ttu-id="d7c27-110">Todas as declarações a seguir declaram uma matriz com três elementos cujos valores são os inteiros `1`, `2` e `3`.</span><span class="sxs-lookup"><span data-stu-id="d7c27-110">All the following declarations declare an array with three elements whose values are the integers `1`, `2`, and `3`.</span></span> <span data-ttu-id="d7c27-111">A segunda inicialização atribui a memória a um <xref:System.ReadOnlySpan%601>, indicando que a memória não pode ser modificada.</span><span class="sxs-lookup"><span data-stu-id="d7c27-111">The second initialization assigns the memory to a <xref:System.ReadOnlySpan%601>, indicating that the memory cannot be modified.</span></span>

```csharp
// Valid starting with C# 7.3
Span<int> first = stackalloc int[3] { 1, 2, 3 };
ReadOnlySpan<int> second = stackalloc int[] { 1, 2, 3 };
Span<int> third = stackalloc[] { 1, 2, 3 };
```

<span data-ttu-id="d7c27-112">Quando tipos de ponteiro estão envolvidos, `stackalloc` requer um contexto [não seguro](unsafe.md).</span><span class="sxs-lookup"><span data-stu-id="d7c27-112">When pointer types are involved, `stackalloc` requires an [unsafe](unsafe.md) context.</span></span> <span data-ttu-id="d7c27-113">Para obter mais informações, consulte [Código não seguro e ponteiros](../../programming-guide/unsafe-code-pointers/index.md).</span><span class="sxs-lookup"><span data-stu-id="d7c27-113">For more information, see [Unsafe Code and Pointers](../../programming-guide/unsafe-code-pointers/index.md).</span></span>

<span data-ttu-id="d7c27-114">`stackalloc` é como [_alloca](/cpp/c-runtime-library/reference/alloca) na biblioteca de tempo de execução C.</span><span class="sxs-lookup"><span data-stu-id="d7c27-114">`stackalloc` is like [_alloca](/cpp/c-runtime-library/reference/alloca) in the C run-time library.</span></span>

## <a name="examples"></a><span data-ttu-id="d7c27-115">Exemplos</span><span class="sxs-lookup"><span data-stu-id="d7c27-115">Examples</span></span>

<span data-ttu-id="d7c27-116">O exemplo a seguir calcula e exibe os 20 primeiros números na sequência de Fibonacci.</span><span class="sxs-lookup"><span data-stu-id="d7c27-116">The following example calculates and displays the first 20 numbers in the Fibonacci sequence.</span></span> <span data-ttu-id="d7c27-117">Cada número é a soma dos dois números anteriores.</span><span class="sxs-lookup"><span data-stu-id="d7c27-117">Each number is the sum of the previous two numbers.</span></span> <span data-ttu-id="d7c27-118">No código, um bloco de memória de tamanho suficiente para conter 20 elementos do tipo `int` é alocado na pilha, não no heap.</span><span class="sxs-lookup"><span data-stu-id="d7c27-118">In the code, a block of memory of sufficient size to contain 20 elements of type `int` is allocated on the stack, not the heap.</span></span> <span data-ttu-id="d7c27-119">O endereço do bloco é armazenado no `Span` `fib`.</span><span class="sxs-lookup"><span data-stu-id="d7c27-119">The address of the block is stored in the `Span` `fib`.</span></span> <span data-ttu-id="d7c27-120">Essa memória não está sujeita à coleta de lixo e, portanto, não precisa ser fixado (usando [fixed](fixed-statement.md)).</span><span class="sxs-lookup"><span data-stu-id="d7c27-120">This memory is not subject to garbage collection and therefore does not have to be pinned (by using [fixed](fixed-statement.md)).</span></span> <span data-ttu-id="d7c27-121">O tempo de vida do bloco de memória é limitado ao tempo de vida do método que o define.</span><span class="sxs-lookup"><span data-stu-id="d7c27-121">The lifetime of the memory block is limited to the lifetime of the method that defines it.</span></span> <span data-ttu-id="d7c27-122">Você não pode liberar a memória antes de o método retornar.</span><span class="sxs-lookup"><span data-stu-id="d7c27-122">You cannot free the memory before the method returns.</span></span>

[!code-csharp[csrefKeywordsOperator#15](~/samples/snippets/csharp/keywords/StackAllocExamples.cs#1)]

<span data-ttu-id="d7c27-123">O exemplo a seguir inicializa uma matriz `stackalloc` de inteiros em uma máscara de bits com um bit definido em cada elemento.</span><span class="sxs-lookup"><span data-stu-id="d7c27-123">The following example initializes a `stackalloc` array of integers to a bit mask with one bit set in each element.</span></span> <span data-ttu-id="d7c27-124">Isso demonstra a nova sintaxe do inicializador disponível a partir do C# 7.3:</span><span class="sxs-lookup"><span data-stu-id="d7c27-124">This demonstrates the new initializer syntax available starting in C# 7.3:</span></span>

[!code-csharp[csrefKeywordsOperator#15](~/samples/snippets/csharp/keywords/StackAllocExamples.cs#2)]

## <a name="security"></a><span data-ttu-id="d7c27-125">Segurança</span><span class="sxs-lookup"><span data-stu-id="d7c27-125">Security</span></span>

<span data-ttu-id="d7c27-126">Você deve usar <xref:System.Span%601> ou <xref:System.ReadOnlySpan%601> quando possível porque códigos não gerenciados são menos seguros do que alternativas seguras.</span><span class="sxs-lookup"><span data-stu-id="d7c27-126">You should use <xref:System.Span%601> or <xref:System.ReadOnlySpan%601> when possible because unsafe code is less secure than safe alternatives.</span></span> <span data-ttu-id="d7c27-127">Mesmo quando usado com ponteiros, o uso de `stackalloc` habilita automaticamente os recursos de detecção de estouro de buffer no CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="d7c27-127">Even when used with pointers, the use of `stackalloc` automatically enables buffer overrun detection features in the common language runtime (CLR).</span></span> <span data-ttu-id="d7c27-128">Se for detectada uma estouro de buffer, o processo será encerrado assim que possível para minimizar a chance de o código mal-intencionado ser executado.</span><span class="sxs-lookup"><span data-stu-id="d7c27-128">If a buffer overrun is detected, the process is terminated as quickly as possible to minimize the chance that malicious code is executed.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="d7c27-129">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="d7c27-129">C# language specification</span></span>

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="d7c27-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d7c27-130">See also</span></span>

- [<span data-ttu-id="d7c27-131">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="d7c27-131">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="d7c27-132">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="d7c27-132">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="d7c27-133">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="d7c27-133">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="d7c27-134">Palavras-chave do operador</span><span class="sxs-lookup"><span data-stu-id="d7c27-134">Operator Keywords</span></span>](operator-keywords.md)
- [<span data-ttu-id="d7c27-135">Código não seguro e ponteiros</span><span class="sxs-lookup"><span data-stu-id="d7c27-135">Unsafe Code and Pointers</span></span>](../../programming-guide/unsafe-code-pointers/index.md)
