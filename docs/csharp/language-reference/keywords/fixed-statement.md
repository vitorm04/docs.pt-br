---
description: Instrução fixed – Referência de C#
title: Instrução fixed – Referência de C#
ms.date: 05/10/2018
f1_keywords:
- fixed_CSharpKeyword
- fixed
helpviewer_keywords:
- fixed keyword [C#]
ms.openlocfilehash: 05505916ab3837d2c433ec420d7928a8ee883fa8
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89139717"
---
# <a name="fixed-statement-c-reference"></a><span data-ttu-id="e2db2-103">Instrução fixed (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="e2db2-103">fixed Statement (C# Reference)</span></span>

<span data-ttu-id="e2db2-104">A instrução `fixed` impede que o coletor de lixo faça a realocação de uma variável móvel.</span><span class="sxs-lookup"><span data-stu-id="e2db2-104">The `fixed` statement prevents the garbage collector from relocating a movable variable.</span></span> <span data-ttu-id="e2db2-105">A instrução `fixed` é permitida somente em um contexto [não seguro](unsafe.md).</span><span class="sxs-lookup"><span data-stu-id="e2db2-105">The `fixed` statement is only permitted in an [unsafe](unsafe.md) context.</span></span> <span data-ttu-id="e2db2-106">Você também pode usar a palavra-chave `fixed` para criar [buffers de tamanho fixo](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md).</span><span class="sxs-lookup"><span data-stu-id="e2db2-106">You can also use the `fixed` keyword to create [fixed size buffers](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md).</span></span>

<span data-ttu-id="e2db2-107">A instrução `fixed` define um ponteiro para uma variável gerenciada e "fixa" essa variável durante a execução da instrução.</span><span class="sxs-lookup"><span data-stu-id="e2db2-107">The `fixed` statement sets a pointer to a managed variable and "pins" that variable during the execution of the statement.</span></span> <span data-ttu-id="e2db2-108">Os ponteiros móveis gerenciados são úteis apenas em um contexto `fixed`.</span><span class="sxs-lookup"><span data-stu-id="e2db2-108">Pointers to movable managed variables are useful only in a `fixed` context.</span></span> <span data-ttu-id="e2db2-109">Sem um contexto `fixed`, a coleta de lixo poderia realocar as variáveis de forma imprevisível.</span><span class="sxs-lookup"><span data-stu-id="e2db2-109">Without a `fixed` context, garbage collection could relocate the variables unpredictably.</span></span> <span data-ttu-id="e2db2-110">O compilador do C# só permite que você atribua um ponteiro a uma variável gerenciada em uma instrução `fixed`.</span><span class="sxs-lookup"><span data-stu-id="e2db2-110">The C# compiler only lets you assign a pointer to a managed variable in a `fixed` statement.</span></span>

[!code-csharp[Accessing fixed memory](snippets/FixedKeywordExamples.cs#1)]

<span data-ttu-id="e2db2-111">Você pode inicializar um ponteiro usando uma matriz, uma cadeia de caracteres, um buffer de tamanho fixo ou o endereço de uma variável.</span><span class="sxs-lookup"><span data-stu-id="e2db2-111">You can initialize a pointer by using an array, a string, a fixed-size buffer, or the address of a variable.</span></span> <span data-ttu-id="e2db2-112">O exemplo a seguir ilustra o uso de endereços de variáveis, matrizes e sequências de caracteres:</span><span class="sxs-lookup"><span data-stu-id="e2db2-112">The following example illustrates the use of variable addresses, arrays, and strings:</span></span>

[!code-csharp[Initializing fixed size buffers](snippets/FixedKeywordExamples.cs#2)]

<span data-ttu-id="e2db2-113">Começando com o C# 7.3, a instrução `fixed` opera em tipos adicionais além de cadeias de caracteres, matrizes, buffers de tamanho fixo ou variáveis não gerenciadas.</span><span class="sxs-lookup"><span data-stu-id="e2db2-113">Starting with C# 7.3, the `fixed` statement operates on additional types beyond arrays, strings, fixed size buffers, or unmanaged variables.</span></span> <span data-ttu-id="e2db2-114">Qualquer tipo que implementa um método chamado `GetPinnableReference` pode ser anexado.</span><span class="sxs-lookup"><span data-stu-id="e2db2-114">Any type that implements a method named `GetPinnableReference` can be pinned.</span></span> <span data-ttu-id="e2db2-115">O `GetPinnableReference` deve retornar uma variável `ref` para um [tipo não gerenciado](../builtin-types/unmanaged-types.md).</span><span class="sxs-lookup"><span data-stu-id="e2db2-115">The `GetPinnableReference` must return a `ref` variable of an [unmanaged type](../builtin-types/unmanaged-types.md).</span></span> <span data-ttu-id="e2db2-116">Os tipos .NET <xref:System.Span%601?displayProperty=nameWithType> e <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> introduzidos no .NET Core 2.0 usam esse padrão e podem ser anexados.</span><span class="sxs-lookup"><span data-stu-id="e2db2-116">The .NET types <xref:System.Span%601?displayProperty=nameWithType> and <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> introduced in .NET Core 2.0 make use of this pattern and can be pinned.</span></span> <span data-ttu-id="e2db2-117">Isso é mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="e2db2-117">This is shown in the following example:</span></span>

[!code-csharp[Accessing fixed memory](snippets/FixedKeywordExamples.cs#FixedSpan)]

<span data-ttu-id="e2db2-118">Se você estiver criando tipos que devem participar desse padrão, consulte <xref:System.Span%601.GetPinnableReference?displayProperty=nameWithType> para obter um exemplo da implementação do padrão.</span><span class="sxs-lookup"><span data-stu-id="e2db2-118">If you are creating types that should participate in this pattern, see <xref:System.Span%601.GetPinnableReference?displayProperty=nameWithType> for an example of implementing the pattern.</span></span>

<span data-ttu-id="e2db2-119">Vários ponteiros podem ser inicializados em uma instrução quando eles são do mesmo tipo:</span><span class="sxs-lookup"><span data-stu-id="e2db2-119">Multiple pointers can be initialized in one statement if they are all the same type:</span></span>

```csharp
fixed (byte* ps = srcarray, pd = dstarray) {...}
```

<span data-ttu-id="e2db2-120">Para inicializar ponteiros de tipos diferentes, basta aninhar instruções `fixed`, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="e2db2-120">To initialize pointers of different types, simply nest `fixed` statements, as shown in the following example.</span></span>

[!code-csharp[Initializing multiple pointers](snippets/FixedKeywordExamples.cs#3)]

<span data-ttu-id="e2db2-121">Depois que o código na instrução é executado, todas as variáveis fixadas são desafixadas e ficam sujeiras à coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="e2db2-121">After the code in the statement is executed, any pinned variables are unpinned and subject to garbage collection.</span></span> <span data-ttu-id="e2db2-122">Portanto, não aponte para essas variáveis fora da instrução `fixed`.</span><span class="sxs-lookup"><span data-stu-id="e2db2-122">Therefore, do not point to those variables outside the `fixed` statement.</span></span> <span data-ttu-id="e2db2-123">As variáveis declaradas na instrução `fixed` estão no escopo dessa instrução, facilitando isto:</span><span class="sxs-lookup"><span data-stu-id="e2db2-123">The variables declared in the `fixed` statement are scoped to that statement, making this easier:</span></span>

```csharp
fixed (byte* ps = srcarray, pd = dstarray)
{
   ...
}
// ps and pd are no longer in scope here.
```

<span data-ttu-id="e2db2-124">Os ponteiros inicializados em instruções `fixed` são variáveis somente leitura.</span><span class="sxs-lookup"><span data-stu-id="e2db2-124">Pointers initialized in `fixed` statements are readonly variables.</span></span> <span data-ttu-id="e2db2-125">Se você quiser modificar o valor do ponteiro, será necessário declarar uma segunda variável de ponteiro e modificá-la.</span><span class="sxs-lookup"><span data-stu-id="e2db2-125">If you want to modify the pointer value, you must declare a second pointer variable, and modify that.</span></span> <span data-ttu-id="e2db2-126">A variável declarada na instrução `fixed` não pode ser modificada:</span><span class="sxs-lookup"><span data-stu-id="e2db2-126">The variable declared in the `fixed` statement cannot be modified:</span></span>

```csharp
fixed (byte* ps = srcarray, pd = dstarray)
{
    byte* pSourceCopy = ps;
    pSourceCopy++; // point to the next element.
    ps++; // invalid: cannot modify ps, as it is declared in the fixed statement.
}
```

<span data-ttu-id="e2db2-127">É possível alocar memória na pilha, local que não está sujeito à coleta de lixo e, portanto, não precisa ser fixado.</span><span class="sxs-lookup"><span data-stu-id="e2db2-127">You can allocate memory on the stack, where it is not subject to garbage collection and therefore does not need to be pinned.</span></span> <span data-ttu-id="e2db2-128">Para fazer isso, use uma [ `stackalloc` expressão](../operators/stackalloc.md).</span><span class="sxs-lookup"><span data-stu-id="e2db2-128">To do that, use a [`stackalloc` expression](../operators/stackalloc.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="e2db2-129">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="e2db2-129">C# language specification</span></span>

<span data-ttu-id="e2db2-130">Para saber mais, confira a seção [A instrução corrigida](~/_csharplang/spec/unsafe-code.md#the-fixed-statement) na [Especificação da linguagem C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="e2db2-130">For more information, see [The fixed statement](~/_csharplang/spec/unsafe-code.md#the-fixed-statement) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e2db2-131">Confira também</span><span class="sxs-lookup"><span data-stu-id="e2db2-131">See also</span></span>

- [<span data-ttu-id="e2db2-132">Referência do C#</span><span class="sxs-lookup"><span data-stu-id="e2db2-132">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="e2db2-133">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="e2db2-133">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="e2db2-134">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="e2db2-134">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="e2db2-135">UNSAFE</span><span class="sxs-lookup"><span data-stu-id="e2db2-135">unsafe</span></span>](unsafe.md)
- [<span data-ttu-id="e2db2-136">Tipos de ponteiro</span><span class="sxs-lookup"><span data-stu-id="e2db2-136">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="e2db2-137">Buffers de tamanho fixo</span><span class="sxs-lookup"><span data-stu-id="e2db2-137">Fixed Size Buffers</span></span>](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md)
