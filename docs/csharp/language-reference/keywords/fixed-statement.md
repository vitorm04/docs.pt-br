---
title: Instrução fixed – Referência de C#
ms.date: 05/10/2018
f1_keywords:
- fixed_CSharpKeyword
- fixed
helpviewer_keywords:
- fixed keyword [C#]
ms.openlocfilehash: e527e8a54a739391d18b180532372b5b70f34d37
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713517"
---
# <a name="fixed-statement-c-reference"></a><span data-ttu-id="0dead-102">Instrução fixed (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="0dead-102">fixed Statement (C# Reference)</span></span>

<span data-ttu-id="0dead-103">A instrução `fixed` impede que o coletor de lixo faça a realocação de uma variável móvel.</span><span class="sxs-lookup"><span data-stu-id="0dead-103">The `fixed` statement prevents the garbage collector from relocating a movable variable.</span></span> <span data-ttu-id="0dead-104">A instrução `fixed` é permitida somente em um contexto [não seguro](unsafe.md).</span><span class="sxs-lookup"><span data-stu-id="0dead-104">The `fixed` statement is only permitted in an [unsafe](unsafe.md) context.</span></span> <span data-ttu-id="0dead-105">Você também pode usar a palavra-chave `fixed` para criar [buffers de tamanho fixo](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md).</span><span class="sxs-lookup"><span data-stu-id="0dead-105">You can also use the `fixed` keyword to create [fixed size buffers](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md).</span></span>

<span data-ttu-id="0dead-106">A instrução `fixed` define um ponteiro para uma variável gerenciada e "fixa" essa variável durante a execução da instrução.</span><span class="sxs-lookup"><span data-stu-id="0dead-106">The `fixed` statement sets a pointer to a managed variable and "pins" that variable during the execution of the statement.</span></span> <span data-ttu-id="0dead-107">Os ponteiros móveis gerenciados são úteis apenas em um contexto `fixed`.</span><span class="sxs-lookup"><span data-stu-id="0dead-107">Pointers to movable managed variables are useful only in a `fixed` context.</span></span> <span data-ttu-id="0dead-108">Sem um contexto `fixed`, a coleta de lixo poderia realocar as variáveis de forma imprevisível.</span><span class="sxs-lookup"><span data-stu-id="0dead-108">Without a `fixed` context, garbage collection could relocate the variables unpredictably.</span></span> <span data-ttu-id="0dead-109">O compilador do C# só permite que você atribua um ponteiro a uma variável gerenciada em uma instrução `fixed`.</span><span class="sxs-lookup"><span data-stu-id="0dead-109">The C# compiler only lets you assign a pointer to a managed variable in a `fixed` statement.</span></span>

[!code-csharp[Accessing fixed memory](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#1)]

<span data-ttu-id="0dead-110">Você pode inicializar um ponteiro usando uma matriz, uma cadeia de caracteres, um buffer de tamanho fixo ou o endereço de uma variável.</span><span class="sxs-lookup"><span data-stu-id="0dead-110">You can initialize a pointer by using an array, a string, a fixed-size buffer, or the address of a variable.</span></span> <span data-ttu-id="0dead-111">O exemplo a seguir ilustra o uso de endereços de variáveis, matrizes e sequências de caracteres:</span><span class="sxs-lookup"><span data-stu-id="0dead-111">The following example illustrates the use of variable addresses, arrays, and strings:</span></span>

[!code-csharp[Initializing fixed size buffers](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#2)]

<span data-ttu-id="0dead-112">Começando com o C# 7.3, a instrução `fixed` opera em tipos adicionais além de cadeias de caracteres, matrizes, buffers de tamanho fixo ou variáveis não gerenciadas.</span><span class="sxs-lookup"><span data-stu-id="0dead-112">Starting with C# 7.3, the `fixed` statement operates on additional types beyond arrays, strings, fixed size buffers, or unmanaged variables.</span></span> <span data-ttu-id="0dead-113">Qualquer tipo que implementa um método chamado `GetPinnableReference` pode ser anexado.</span><span class="sxs-lookup"><span data-stu-id="0dead-113">Any type that implements a method named `GetPinnableReference` can be pinned.</span></span> <span data-ttu-id="0dead-114">O `GetPinnableReference` deve retornar uma variável `ref` para um [tipo não gerenciado](../builtin-types/unmanaged-types.md).</span><span class="sxs-lookup"><span data-stu-id="0dead-114">The `GetPinnableReference` must return a `ref` variable of an [unmanaged type](../builtin-types/unmanaged-types.md).</span></span> <span data-ttu-id="0dead-115">Os tipos .NET <xref:System.Span%601?displayProperty=nameWithType> e <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> introduzidos no .NET Core 2.0 usam esse padrão e podem ser anexados.</span><span class="sxs-lookup"><span data-stu-id="0dead-115">The .NET types <xref:System.Span%601?displayProperty=nameWithType> and <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> introduced in .NET Core 2.0 make use of this pattern and can be pinned.</span></span> <span data-ttu-id="0dead-116">Isso é mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="0dead-116">This is shown in the following example:</span></span>

[!code-csharp[Accessing fixed memory](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#FixedSpan)]

<span data-ttu-id="0dead-117">Se você estiver criando tipos que devem participar desse padrão, consulte <xref:System.Span%601.GetPinnableReference?displayProperty=nameWithType> para obter um exemplo da implementação do padrão.</span><span class="sxs-lookup"><span data-stu-id="0dead-117">If you are creating types that should participate in this pattern, see <xref:System.Span%601.GetPinnableReference?displayProperty=nameWithType> for an example of implementing the pattern.</span></span>

<span data-ttu-id="0dead-118">Vários ponteiros podem ser inicializados em uma instrução quando eles são do mesmo tipo:</span><span class="sxs-lookup"><span data-stu-id="0dead-118">Multiple pointers can be initialized in one statement if they are all the same type:</span></span>

```csharp
fixed (byte* ps = srcarray, pd = dstarray) {...}
```

<span data-ttu-id="0dead-119">Para inicializar ponteiros de tipos diferentes, basta aninhar instruções `fixed`, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="0dead-119">To initialize pointers of different types, simply nest `fixed` statements, as shown in the following example.</span></span>

[!code-csharp[Initializing multiple pointers](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#3)]

<span data-ttu-id="0dead-120">Depois que o código na instrução é executado, todas as variáveis fixadas são desafixadas e ficam sujeiras à coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="0dead-120">After the code in the statement is executed, any pinned variables are unpinned and subject to garbage collection.</span></span> <span data-ttu-id="0dead-121">Portanto, não aponte para essas variáveis fora da instrução `fixed`.</span><span class="sxs-lookup"><span data-stu-id="0dead-121">Therefore, do not point to those variables outside the `fixed` statement.</span></span> <span data-ttu-id="0dead-122">As variáveis declaradas na instrução `fixed` estão no escopo dessa instrução, facilitando isto:</span><span class="sxs-lookup"><span data-stu-id="0dead-122">The variables declared in the `fixed` statement are scoped to that statement, making this easier:</span></span>

```csharp
fixed (byte* ps = srcarray, pd = dstarray)
{
   ...
}
// ps and pd are no longer in scope here.
```

<span data-ttu-id="0dead-123">Os ponteiros inicializados em instruções `fixed` são variáveis somente leitura.</span><span class="sxs-lookup"><span data-stu-id="0dead-123">Pointers initialized in `fixed` statements are readonly variables.</span></span> <span data-ttu-id="0dead-124">Se você quiser modificar o valor do ponteiro, será necessário declarar uma segunda variável de ponteiro e modificá-la.</span><span class="sxs-lookup"><span data-stu-id="0dead-124">If you want to modify the pointer value, you must declare a second pointer variable, and modify that.</span></span> <span data-ttu-id="0dead-125">A variável declarada na instrução `fixed` não pode ser modificada:</span><span class="sxs-lookup"><span data-stu-id="0dead-125">The variable declared in the `fixed` statement cannot be modified:</span></span>

```csharp
fixed (byte* ps = srcarray, pd = dstarray)
{
    byte* pSourceCopy = ps;
    pSourceCopy++; // point to the next element.
    ps++; // invalid: cannot modify ps, as it is declared in the fixed statement.
}
```

<span data-ttu-id="0dead-126">É possível alocar memória na pilha, local que não está sujeito à coleta de lixo e, portanto, não precisa ser fixado.</span><span class="sxs-lookup"><span data-stu-id="0dead-126">You can allocate memory on the stack, where it is not subject to garbage collection and therefore does not need to be pinned.</span></span> <span data-ttu-id="0dead-127">Para fazer isso, use o [ `stackalloc` operador](../operators/stackalloc.md).</span><span class="sxs-lookup"><span data-stu-id="0dead-127">To do that use the [`stackalloc` operator](../operators/stackalloc.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="0dead-128">especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="0dead-128">C# language specification</span></span>

<span data-ttu-id="0dead-129">Para saber mais, confira a seção [A instrução corrigida](~/_csharplang/spec/unsafe-code.md#the-fixed-statement) na [Especificação da linguagem C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="0dead-129">For more information, see [The fixed statement](~/_csharplang/spec/unsafe-code.md#the-fixed-statement) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0dead-130">Confira também</span><span class="sxs-lookup"><span data-stu-id="0dead-130">See also</span></span>

- [<span data-ttu-id="0dead-131">C# Referência</span><span class="sxs-lookup"><span data-stu-id="0dead-131">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="0dead-132">C# Guia de Programação</span><span class="sxs-lookup"><span data-stu-id="0dead-132">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="0dead-133">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="0dead-133">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="0dead-134">Inseguro</span><span class="sxs-lookup"><span data-stu-id="0dead-134">unsafe</span></span>](unsafe.md)
- [<span data-ttu-id="0dead-135">Tipos de Ponteiro</span><span class="sxs-lookup"><span data-stu-id="0dead-135">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="0dead-136">Buffers de tamanho fixo</span><span class="sxs-lookup"><span data-stu-id="0dead-136">Fixed Size Buffers</span></span>](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md)
