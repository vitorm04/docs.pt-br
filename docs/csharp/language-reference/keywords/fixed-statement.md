---
title: Instrução fixed (Referência de C#)
ms.date: 05/10/2018
f1_keywords:
- fixed_CSharpKeyword
- fixed
helpviewer_keywords:
- fixed keyword [C#]
ms.openlocfilehash: e26e7e7f15dd48cf029d5f67bf5ef0de3e19b7bb
ms.sourcegitcommit: 895c7602386a6dfe7ca4facce3d965b27e5c6e87
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2018
---
# <a name="fixed-statement-c-reference"></a><span data-ttu-id="0e2da-102">Instrução fixed (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="0e2da-102">fixed Statement (C# Reference)</span></span>

<span data-ttu-id="0e2da-103">A instrução `fixed` impede que o coletor de lixo faça a realocação de uma variável móvel.</span><span class="sxs-lookup"><span data-stu-id="0e2da-103">The `fixed` statement prevents the garbage collector from relocating a movable variable.</span></span> <span data-ttu-id="0e2da-104">A instrução `fixed` é permitida somente em um contexto [não seguro](unsafe.md).</span><span class="sxs-lookup"><span data-stu-id="0e2da-104">The `fixed` statement is only permitted in an [unsafe](unsafe.md) context.</span></span> <span data-ttu-id="0e2da-105">A `fixed` também pode ser usada para criar [buffers de tamanho fixo](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md).</span><span class="sxs-lookup"><span data-stu-id="0e2da-105">`fixed` can also be used to create [fixed size buffers](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md).</span></span>

<span data-ttu-id="0e2da-106">A instrução `fixed` define um ponteiro para uma variável gerenciada e "fixa" essa variável durante a execução da instrução.</span><span class="sxs-lookup"><span data-stu-id="0e2da-106">The `fixed` statement sets a pointer to a managed variable and "pins" that variable during the execution of the statement.</span></span> <span data-ttu-id="0e2da-107">Os ponteiros móveis gerenciados são úteis apenas em um contexto `fixed`.</span><span class="sxs-lookup"><span data-stu-id="0e2da-107">Pointers to movable managed variables are useful only in a `fixed` context.</span></span> <span data-ttu-id="0e2da-108">Sem um contexto `fixed`, a coleta de lixo poderia realocar as variáveis de forma imprevisível.</span><span class="sxs-lookup"><span data-stu-id="0e2da-108">Without a `fixed` context, garbage collection could relocate the variables unpredictably.</span></span> <span data-ttu-id="0e2da-109">O compilador do C# só permite que você atribua um ponteiro a uma variável gerenciada em uma instrução `fixed`.</span><span class="sxs-lookup"><span data-stu-id="0e2da-109">The C# compiler only lets you assign a pointer to a managed variable in a `fixed` statement.</span></span>

[!code-csharp[Accessing fixed memory](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#1)]

<span data-ttu-id="0e2da-110">Você pode inicializar um ponteiro usando uma matriz, uma cadeia de caracteres, um buffer de tamanho fixo ou o endereço de uma variável.</span><span class="sxs-lookup"><span data-stu-id="0e2da-110">You can initialize a pointer by using an array, a string, a fixed-size buffer, or the address of a variable.</span></span> <span data-ttu-id="0e2da-111">O exemplo a seguir ilustra o uso de endereços de variáveis, matrizes e sequências de caracteres.</span><span class="sxs-lookup"><span data-stu-id="0e2da-111">The following example illustrates the use of variable addresses, arrays, and strings.</span></span> <span data-ttu-id="0e2da-112">Para obter mais informações sobre buffers de tamanho fixo, consulte [Buffers de tamanho fixo](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md).</span><span class="sxs-lookup"><span data-stu-id="0e2da-112">For more information about fixed-size buffers, see [Fixed Size Buffers](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md).</span></span>

[!code-csharp[Initializing fixed size buffers](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#2)]

<span data-ttu-id="0e2da-113">Começando com o C# 7.3, a instrução `fixed` opera em tipos adicionais além de cadeias de caracteres, matrizes, buffers de tamanho fixo ou variáveis não gerenciadas.</span><span class="sxs-lookup"><span data-stu-id="0e2da-113">Starting with C# 7.3, the `fixed` statement operates on additional types beyond arrays, strings, fixed-size buffers, or unmanaged variables.</span></span> <span data-ttu-id="0e2da-114">Qualquer tipo que implementa um método chamado `DangerousGetPinnableReference` pode ser anexado.</span><span class="sxs-lookup"><span data-stu-id="0e2da-114">Any type that implements a method named `DangerousGetPinnableReference` can be pinned.</span></span> <span data-ttu-id="0e2da-115">O `DangerousGetPinnableReference` deve retornar uma variável `ref` para um tipo não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="0e2da-115">The `DangerousGetPinnableReference` must return a `ref` variable to an unmanaged type.</span></span> <span data-ttu-id="0e2da-116">Consulte o tópico sobre [tipos de ponteiro](../../programming-guide/unsafe-code-pointers/pointer-types.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="0e2da-116">See the topic on [pointer types](../../programming-guide/unsafe-code-pointers/pointer-types.md) for more information.</span></span> <span data-ttu-id="0e2da-117">Os tipos .NET <xref:System.Span%601?displayProperty=nameWithType> e <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> introduzidos no .NET Core 2.0 usam esse padrão e podem ser anexados.</span><span class="sxs-lookup"><span data-stu-id="0e2da-117">The .NET types <xref:System.Span%601?displayProperty=nameWithType> and <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> introduced in .NET Core 2.0 make use of this pattern and can be pinned.</span></span> <span data-ttu-id="0e2da-118">Isso é mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="0e2da-118">This is shown in the following example:</span></span>

[!code-csharp[Accessing fixed memory](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#FixedSpan)]

<span data-ttu-id="0e2da-119">Se você estiver criando tipos que devem participar desse padrão, consulte <xref:System.Span%601.DangerousGetPinnableReference?displayProperty=nameWithType> para obter um exemplo da implementação do padrão.</span><span class="sxs-lookup"><span data-stu-id="0e2da-119">If you are creating types that should participate in this pattern, see <xref:System.Span%601.DangerousGetPinnableReference?displayProperty=nameWithType> for an example of implementing the pattern.</span></span>

<span data-ttu-id="0e2da-120">Vários ponteiros podem ser inicializados em uma instrução quando eles são do mesmo tipo:</span><span class="sxs-lookup"><span data-stu-id="0e2da-120">Multiple pointers can be initialized in one statement if they are all the same type:</span></span>

```csharp
fixed (byte* ps = srcarray, pd = dstarray) {...}
```

<span data-ttu-id="0e2da-121">Para inicializar ponteiros de tipos diferentes, basta aninhar instruções `fixed`, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="0e2da-121">To initialize pointers of different types, simply nest `fixed` statements, as shown in the following example.</span></span>

[!code-csharp[Initializing multiple pointers](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#3)]

<span data-ttu-id="0e2da-122">Depois que o código na instrução é executado, todas as variáveis fixadas são desafixadas e ficam sujeiras à coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="0e2da-122">After the code in the statement is executed, any pinned variables are unpinned and subject to garbage collection.</span></span> <span data-ttu-id="0e2da-123">Portanto, não aponte para essas variáveis fora da instrução `fixed`.</span><span class="sxs-lookup"><span data-stu-id="0e2da-123">Therefore, do not point to those variables outside the `fixed` statement.</span></span> <span data-ttu-id="0e2da-124">As variáveis declaradas na instrução `fixed` estão no escopo dessa instrução, facilitando isto:</span><span class="sxs-lookup"><span data-stu-id="0e2da-124">The variables declared in the `fixed` statement are scoped to that statement, making this easier:</span></span>

```csharp
fixed (byte* ps = srcarray, pd = dstarray)
{
   ...
}
// ps and pd are no longer in scope here.
```

<span data-ttu-id="0e2da-125">Os ponteiros inicializados em instruções `fixed` são variáveis somente leitura.</span><span class="sxs-lookup"><span data-stu-id="0e2da-125">Pointers initialized in `fixed` statements are readonly variables.</span></span> <span data-ttu-id="0e2da-126">Se você quiser modificar o valor do ponteiro, será necessário declarar uma segunda variável de ponteiro e modificá-la.</span><span class="sxs-lookup"><span data-stu-id="0e2da-126">If you want to modify the pointer value, you must declare a second pointer variable, and modify that.</span></span> <span data-ttu-id="0e2da-127">A variável declarada na instrução `fixed` não pode ser modificada:</span><span class="sxs-lookup"><span data-stu-id="0e2da-127">The variable declared in the `fixed` statement cannot be modified:</span></span>

```csharp
fixed (byte* ps = srcarray, pd = dstarray)
{
    byte* pSourceCopy = ps;
    pSourceCopy++; // point to the next element.
    ps++; // invalid: cannot modify ps, as it is declared in the fixed statement.
}
```


<span data-ttu-id="0e2da-128">No modo não seguro, é possível alocar memória na pilha, local que não está sujeito à coleta de lixo e, portanto, não precisa ser fixado.</span><span class="sxs-lookup"><span data-stu-id="0e2da-128">In unsafe mode, you can allocate memory on the stack, where it is not subject to garbage collection and therefore does not need to be pinned.</span></span> <span data-ttu-id="0e2da-129">Para saber mais, confira [stackalloc](stackalloc.md).</span><span class="sxs-lookup"><span data-stu-id="0e2da-129">For more information, see [stackalloc](stackalloc.md).</span></span>

[!code-csharp[Initializing multiple pointers](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#4)]

## <a name="c-language-specification"></a><span data-ttu-id="0e2da-130">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="0e2da-130">C# Language Specification</span></span>

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="0e2da-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0e2da-131">See Also</span></span>

 [<span data-ttu-id="0e2da-132">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="0e2da-132">C# Reference</span></span>](../index.md)  
 [<span data-ttu-id="0e2da-133">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="0e2da-133">C# Programming Guide</span></span>](../../programming-guide/index.md)  
 [<span data-ttu-id="0e2da-134">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="0e2da-134">C# Keywords</span></span>](index.md)  
 [<span data-ttu-id="0e2da-135">unsafe</span><span class="sxs-lookup"><span data-stu-id="0e2da-135">unsafe</span></span>](unsafe.md)  
 [<span data-ttu-id="0e2da-136">Buffers de tamanho fixo</span><span class="sxs-lookup"><span data-stu-id="0e2da-136">Fixed Size Buffers</span></span>](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md)
