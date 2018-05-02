---
title: Instrução fixed (Referência de C#)
ms.date: 04/20/2018
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- fixed_CSharpKeyword
- fixed
helpviewer_keywords:
- fixed keyword [C#]
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 5dd117461f792ec7a10b740fbad277de52d05623
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="fixed-statement-c-reference"></a><span data-ttu-id="0d7c4-102">Instrução fixed (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="0d7c4-102">fixed Statement (C# Reference)</span></span>

<span data-ttu-id="0d7c4-103">A instrução `fixed` impede que o coletor de lixo faça a realocação de uma variável móvel.</span><span class="sxs-lookup"><span data-stu-id="0d7c4-103">The `fixed` statement prevents the garbage collector from relocating a movable variable.</span></span> <span data-ttu-id="0d7c4-104">A instrução `fixed` é permitida somente em um contexto [não seguro](unsafe.md).</span><span class="sxs-lookup"><span data-stu-id="0d7c4-104">The `fixed` statement is only permitted in an [unsafe](unsafe.md) context.</span></span> <span data-ttu-id="0d7c4-105">A `Fixed` também pode ser usada para criar [buffers de tamanho fixo](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md).</span><span class="sxs-lookup"><span data-stu-id="0d7c4-105">`Fixed` can also be used to create [fixed size buffers](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md).</span></span>

<span data-ttu-id="0d7c4-106">A instrução `fixed` define um ponteiro para uma variável gerenciada e "fixa" essa variável durante a execução da instrução.</span><span class="sxs-lookup"><span data-stu-id="0d7c4-106">The `fixed` statement sets a pointer to a managed variable and "pins" that variable during the execution of the statement.</span></span> <span data-ttu-id="0d7c4-107">Os ponteiros móveis gerenciados são úteis apenas em um contexto `fixed`.</span><span class="sxs-lookup"><span data-stu-id="0d7c4-107">Pointers to movable managed variables are useful only in a `fixed` context.</span></span> <span data-ttu-id="0d7c4-108">Sem um contexto `fixed`, a coleta de lixo poderia realocar as variáveis de forma imprevisível.</span><span class="sxs-lookup"><span data-stu-id="0d7c4-108">Without a `fixed` context, garbage collection could relocate the variables unpredictably.</span></span> <span data-ttu-id="0d7c4-109">O compilador do C# só permite que você atribua um ponteiro a uma variável gerenciada em uma instrução `fixed`.</span><span class="sxs-lookup"><span data-stu-id="0d7c4-109">The C# compiler only lets you assign a pointer to a managed variable in a `fixed` statement.</span></span>

[!code-csharp[Accessing fixed memory](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#1)]

<span data-ttu-id="0d7c4-110">Você pode inicializar um ponteiro usando uma matriz, uma cadeia de caracteres, um buffer de tamanho fixo ou o endereço de uma variável.</span><span class="sxs-lookup"><span data-stu-id="0d7c4-110">You can initialize a pointer by using an array, a string, a fixed-size buffer, or the address of a variable.</span></span> <span data-ttu-id="0d7c4-111">O exemplo a seguir ilustra o uso de endereços de variáveis, matrizes e sequências de caracteres.</span><span class="sxs-lookup"><span data-stu-id="0d7c4-111">The following example illustrates the use of variable addresses, arrays, and strings.</span></span> <span data-ttu-id="0d7c4-112">Para obter mais informações sobre buffers de tamanho fixo, consulte [Buffers de tamanho fixo](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md).</span><span class="sxs-lookup"><span data-stu-id="0d7c4-112">For more information about fixed-size buffers, see [Fixed Size Buffers](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md).</span></span>

[!code-csharp[Initializing fixed size buffers](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#2)]

<span data-ttu-id="0d7c4-113">Vários ponteiros podem ser inicializados em uma instrução quando eles são do mesmo tipo:</span><span class="sxs-lookup"><span data-stu-id="0d7c4-113">Multiple pointers can be initialized in one statement if they are all the same type:</span></span>

```csharp
fixed (byte* ps = srcarray, pd = dstarray) {...}
```

<span data-ttu-id="0d7c4-114">Para inicializar ponteiros de tipos diferentes, basta aninhar instruções `fixed`, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="0d7c4-114">To initialize pointers of different types, simply nest `fixed` statements, as shown in the following example.</span></span>

[!code-csharp[Initializing multiple pointers](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#3)]

<span data-ttu-id="0d7c4-115">Depois que o código na instrução é executado, todas as variáveis fixadas são desafixadas e ficam sujeiras à coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="0d7c4-115">After the code in the statement is executed, any pinned variables are unpinned and subject to garbage collection.</span></span> <span data-ttu-id="0d7c4-116">Portanto, não aponte para essas variáveis fora da instrução `fixed`.</span><span class="sxs-lookup"><span data-stu-id="0d7c4-116">Therefore, do not point to those variables outside the `fixed` statement.</span></span> <span data-ttu-id="0d7c4-117">As variáveis declaradas na instrução `fixed` estão no escopo dessa instrução, facilitando isto:</span><span class="sxs-lookup"><span data-stu-id="0d7c4-117">The variables declared in the `fixed` statement are scoped to that statement, making this easier:</span></span>

```csharp
fixed (byte* ps = srcarray, pd = dstarray)
{
   ...
}
// ps and pd are no longer in scope here.
```

<span data-ttu-id="0d7c4-118">Os ponteiros inicializados em instruções `fixed` são variáveis somente leitura.</span><span class="sxs-lookup"><span data-stu-id="0d7c4-118">Pointers initialized in `fixed` statements are readonly variables.</span></span> <span data-ttu-id="0d7c4-119">Se você quiser modificar o valor do ponteiro, será necessário declarar uma segunda variável de ponteiro e modificá-la.</span><span class="sxs-lookup"><span data-stu-id="0d7c4-119">If you want to modify the pointer value, you must declare a second pointer variable, and modify that.</span></span> <span data-ttu-id="0d7c4-120">A variável declarada na instrução `fixed` não pode ser modificada:</span><span class="sxs-lookup"><span data-stu-id="0d7c4-120">The variable declared in the `fixed` statement cannot be modified:</span></span>

```csharp
fixed (byte* ps = srcarray, pd = dstarray)
{
    byte* pSourceCopy = ps;
    pSourceCopy++; // point to the next element.
    ps++; // invalid: cannot modify ps, as it is declared in the fixed statement.
}
```


<span data-ttu-id="0d7c4-121">No modo não seguro, é possível alocar memória na pilha, local que não está sujeito à coleta de lixo e, portanto, não precisa ser fixado.</span><span class="sxs-lookup"><span data-stu-id="0d7c4-121">In unsafe mode, you can allocate memory on the stack, where it is not subject to garbage collection and therefore does not need to be pinned.</span></span> <span data-ttu-id="0d7c4-122">Para saber mais, confira [stackalloc](stackalloc.md).</span><span class="sxs-lookup"><span data-stu-id="0d7c4-122">For more information, see [stackalloc](stackalloc.md).</span></span>

[!code-csharp[Initializing multiple pointers](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#4)]

## <a name="c-language-specification"></a><span data-ttu-id="0d7c4-123">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="0d7c4-123">C# Language Specification</span></span>

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="0d7c4-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0d7c4-124">See Also</span></span>

 [<span data-ttu-id="0d7c4-125">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="0d7c4-125">C# Reference</span></span>](../index.md)  
 [<span data-ttu-id="0d7c4-126">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="0d7c4-126">C# Programming Guide</span></span>](../../programming-guide/index.md)  
 [<span data-ttu-id="0d7c4-127">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="0d7c4-127">C# Keywords</span></span>](index.md)  
 [<span data-ttu-id="0d7c4-128">unsafe</span><span class="sxs-lookup"><span data-stu-id="0d7c4-128">unsafe</span></span>](unsafe.md)  
 [<span data-ttu-id="0d7c4-129">Buffers de tamanho fixo</span><span class="sxs-lookup"><span data-stu-id="0d7c4-129">Fixed Size Buffers</span></span>](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md)
