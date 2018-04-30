---
title: stackalloc (Referência de C#)
ms.date: 04/12/2018
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- stackalloc_CSharpKeyword
- stackalloc
helpviewer_keywords:
- stackalloc keyword [C#]
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c4cde254bb6a5601d10619c4a3bd2f00f1f146d3
ms.sourcegitcommit: 9a4fe1a1c37b26532654b4bbe22d702237950009
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="stackalloc-c-reference"></a><span data-ttu-id="52ea3-102">stackalloc (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="52ea3-102">stackalloc (C# Reference)</span></span>
<span data-ttu-id="52ea3-103">A palavra-chave `stackalloc` é usada em um contexto de código não seguro para alocar um bloco de memória na pilha.</span><span class="sxs-lookup"><span data-stu-id="52ea3-103">The `stackalloc` keyword is used in an unsafe code context to allocate a block of memory on the stack.</span></span>

```csharp
int* block = stackalloc int[100];
```

## <a name="remarks"></a><span data-ttu-id="52ea3-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="52ea3-104">Remarks</span></span>

<span data-ttu-id="52ea3-105">A palavra-chave é válida somente em inicializadores de variável locais.</span><span class="sxs-lookup"><span data-stu-id="52ea3-105">The keyword is valid only in local variable initializers.</span></span> <span data-ttu-id="52ea3-106">O código a seguir gera erros de compilador.</span><span class="sxs-lookup"><span data-stu-id="52ea3-106">The following code causes compiler errors.</span></span>

```csharp
int* block;
// The following assignment statement causes compiler errors. You
// can use stackalloc only when declaring and initializing a local
// variable.
block = stackalloc int[100];
```

<span data-ttu-id="52ea3-107">A partir do C# 7.3, é possível usar a sintaxe do inicializador de matriz para matrizes de `stackalloc`.</span><span class="sxs-lookup"><span data-stu-id="52ea3-107">Beginning with C# 7.3, you can use array initializer syntax for `stackalloc` arrays.</span></span> <span data-ttu-id="52ea3-108">Todas as declarações a seguir declaram uma matriz com três elementos cujos valores são os inteiros `1`, `2` e `3`:</span><span class="sxs-lookup"><span data-stu-id="52ea3-108">All the following declarations declare an array with three elements whose values are the integers `1`, `2`, and `3`:</span></span>

```csharp
// Valid starting with C# 7.3
int* first = stackalloc int[3] { 1, 2, 3 };
int* second = stackalloc int[] { 1, 2, 3 };
int* third = stackalloc[] { 1, 2, 3 };
```

<span data-ttu-id="52ea3-109">Como tipos de ponteiro estão envolvidos, `stackalloc` requer o contexto [não seguro](unsafe.md).</span><span class="sxs-lookup"><span data-stu-id="52ea3-109">Because pointer types are involved, `stackalloc` requires an [unsafe](unsafe.md) context.</span></span> <span data-ttu-id="52ea3-110">Para obter mais informações, consulte [Código não seguro e ponteiros](../../programming-guide/unsafe-code-pointers/index.md)</span><span class="sxs-lookup"><span data-stu-id="52ea3-110">For more information, see [Unsafe Code and Pointers](../../programming-guide/unsafe-code-pointers/index.md)</span></span> 

<span data-ttu-id="52ea3-111">`stackalloc` é como [_alloca](/cpp/c-runtime-library/reference/alloca) na biblioteca de tempo de execução C.</span><span class="sxs-lookup"><span data-stu-id="52ea3-111">`stackalloc` is like [_alloca](/cpp/c-runtime-library/reference/alloca) in the C run-time library.</span></span>

## <a name="examples"></a><span data-ttu-id="52ea3-112">Exemplos</span><span class="sxs-lookup"><span data-stu-id="52ea3-112">Examples</span></span>

<span data-ttu-id="52ea3-113">O exemplo a seguir calcula e exibe os 20 primeiros números na sequência de Fibonacci.</span><span class="sxs-lookup"><span data-stu-id="52ea3-113">The following example calculates and displays the first 20 numbers in the Fibonacci sequence.</span></span> <span data-ttu-id="52ea3-114">Cada número é a soma dos dois números anteriores.</span><span class="sxs-lookup"><span data-stu-id="52ea3-114">Each number is the sum of the previous two numbers.</span></span> <span data-ttu-id="52ea3-115">No código, um bloco de memória de tamanho suficiente para conter 20 elementos do tipo `int` é alocado na pilha, não no heap.</span><span class="sxs-lookup"><span data-stu-id="52ea3-115">In the code, a block of memory of sufficient size to contain 20 elements of type `int` is allocated on the stack, not the heap.</span></span> <span data-ttu-id="52ea3-116">O endereço do bloco é armazenado no ponteiro `fib`.</span><span class="sxs-lookup"><span data-stu-id="52ea3-116">The address of the block is stored in the pointer `fib`.</span></span> <span data-ttu-id="52ea3-117">Essa memória não está sujeita à coleta de lixo e, portanto, não precisa ser fixado (usando [fixed](fixed-statement.md)).</span><span class="sxs-lookup"><span data-stu-id="52ea3-117">This memory is not subject to garbage collection and therefore does not have to be pinned (by using [fixed](fixed-statement.md)).</span></span> <span data-ttu-id="52ea3-118">O tempo de vida do bloco de memória é limitado ao tempo de vida do método que o define.</span><span class="sxs-lookup"><span data-stu-id="52ea3-118">The lifetime of the memory block is limited to the lifetime of the method that defines it.</span></span> <span data-ttu-id="52ea3-119">Você não pode liberar a memória antes de o método retornar.</span><span class="sxs-lookup"><span data-stu-id="52ea3-119">You cannot free the memory before the method returns.</span></span>

[!code-csharp[csrefKeywordsOperator#15](../../../../samples/snippets/csharp/keywords/StackAllocExamples.cs#1)]

<span data-ttu-id="52ea3-120">O exemplo a seguir inicializa uma matriz `stackalloc` de inteiros em uma máscara de bits com um bit definido em cada elemento.</span><span class="sxs-lookup"><span data-stu-id="52ea3-120">The following example initializes a `stackalloc` array of integers to a bit mask with one bit set in each element.</span></span> <span data-ttu-id="52ea3-121">Isso demonstra a nova sintaxe do inicializador disponível a partir do C# 7.3:</span><span class="sxs-lookup"><span data-stu-id="52ea3-121">This demonstrates the new initializer syntax available starting in C# 7.3:</span></span>

[!code-csharp[csrefKeywordsOperator#15](../../../../samples/snippets/csharp/keywords/StackAllocExamples.cs#2)]

## <a name="security"></a><span data-ttu-id="52ea3-122">Segurança</span><span class="sxs-lookup"><span data-stu-id="52ea3-122">Security</span></span>

<span data-ttu-id="52ea3-123">O código não seguro é menos seguro do que as alternativas seguras.</span><span class="sxs-lookup"><span data-stu-id="52ea3-123">Unsafe code is less secure than safe alternatives.</span></span> <span data-ttu-id="52ea3-124">No entanto, o uso de `stackalloc` habilita automaticamente os recursos de detecção de estouro de buffer no CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="52ea3-124">However, the use of `stackalloc` automatically enables buffer overrun detection features in the common language runtime (CLR).</span></span> <span data-ttu-id="52ea3-125">Se for detectada uma estouro de buffer, o processo será encerrado assim que possível para minimizar a chance de o código mal-intencionado ser executado.</span><span class="sxs-lookup"><span data-stu-id="52ea3-125">If a buffer overrun is detected, the process is terminated as quickly as possible to minimize the chance that malicious code is executed.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="52ea3-126">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="52ea3-126">C# Language Specification</span></span>
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="52ea3-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="52ea3-127">See Also</span></span>
 [<span data-ttu-id="52ea3-128">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="52ea3-128">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="52ea3-129">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="52ea3-129">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="52ea3-130">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="52ea3-130">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="52ea3-131">Palavras-chave do operador</span><span class="sxs-lookup"><span data-stu-id="52ea3-131">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)  
 [<span data-ttu-id="52ea3-132">Código não seguro e ponteiros</span><span class="sxs-lookup"><span data-stu-id="52ea3-132">Unsafe Code and Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/index.md)
