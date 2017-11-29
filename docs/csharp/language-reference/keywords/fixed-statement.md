---
title: "Instrução fixed (Referência de C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- fixed_CSharpKeyword
- fixed
helpviewer_keywords: fixed keyword [C#]
ms.assetid: 7ea6db08-ad49-4a7a-b934-d8c4acad1c3a
caps.latest.revision: "24"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 13633e71c863b075eede41c9a18419d65350bdb0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="fixed-statement-c-reference"></a><span data-ttu-id="e7a8b-102">Instrução fixed (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="e7a8b-102">fixed Statement (C# Reference)</span></span>
<span data-ttu-id="e7a8b-103">A instrução `fixed` impede que o coletor de lixo faça a realocação de uma variável móvel.</span><span class="sxs-lookup"><span data-stu-id="e7a8b-103">The `fixed` statement prevents the garbage collector from relocating a movable variable.</span></span> <span data-ttu-id="e7a8b-104">A instrução `fixed` é permitida somente em um contexto [não seguro](../../../csharp/language-reference/keywords/unsafe.md).</span><span class="sxs-lookup"><span data-stu-id="e7a8b-104">The `fixed` statement is only permitted in an [unsafe](../../../csharp/language-reference/keywords/unsafe.md) context.</span></span> <span data-ttu-id="e7a8b-105">A `Fixed` também pode ser usada para criar [buffers de tamanho fixo](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md).</span><span class="sxs-lookup"><span data-stu-id="e7a8b-105">`Fixed` can also be used to create [fixed size buffers](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md).</span></span>  
  
 <span data-ttu-id="e7a8b-106">A instrução `fixed` define um ponteiro para uma variável gerenciada e "fixa" essa variável durante a execução da instrução.</span><span class="sxs-lookup"><span data-stu-id="e7a8b-106">The `fixed` statement sets a pointer to a managed variable and "pins" that variable during the execution of the statement.</span></span> <span data-ttu-id="e7a8b-107">Sem a `fixed`, os ponteiros para variáveis gerenciadas móveis seriam de pouca utilidade, pois a coleta de lixo poderia realocar as variáveis de forma imprevisível.</span><span class="sxs-lookup"><span data-stu-id="e7a8b-107">Without `fixed`, pointers to movable managed variables would be of little use since garbage collection could relocate the variables unpredictably.</span></span> <span data-ttu-id="e7a8b-108">O compilador do C# só permite que você atribua um ponteiro a uma variável gerenciada em uma instrução `fixed`.</span><span class="sxs-lookup"><span data-stu-id="e7a8b-108">The C# compiler only lets you assign a pointer to a managed variable in a `fixed` statement.</span></span>  
  
 [!code-csharp[csrefKeywordsFixedLock#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/fixed-statement_1.cs)]  
  
 <span data-ttu-id="e7a8b-109">Você pode inicializar um ponteiro usando uma matriz, uma cadeia de caracteres, um buffer de tamanho fixo ou o endereço de uma variável.</span><span class="sxs-lookup"><span data-stu-id="e7a8b-109">You can initialize a pointer by using an array, a string, a fixed-size buffer, or the address of a variable.</span></span> <span data-ttu-id="e7a8b-110">O exemplo a seguir ilustra o uso de endereços de variáveis, matrizes e sequências de caracteres.</span><span class="sxs-lookup"><span data-stu-id="e7a8b-110">The following example illustrates the use of variable addresses, arrays, and strings.</span></span> <span data-ttu-id="e7a8b-111">Para obter mais informações sobre buffers de tamanho fixo, consulte [Buffers de tamanho fixo](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md).</span><span class="sxs-lookup"><span data-stu-id="e7a8b-111">For more information about fixed-size buffers, see [Fixed Size Buffers](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md).</span></span>  
  
 [!code-csharp[csrefKeywordsFixedLock#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/fixed-statement_2.cs)]  
  
 <span data-ttu-id="e7a8b-112">Você pode inicializar vários ponteiros, desde que eles sejam todos do mesmo tipo.</span><span class="sxs-lookup"><span data-stu-id="e7a8b-112">You can initialize multiple pointers, as long as they are all of the same type.</span></span>  
  
```csharp
fixed (byte* ps = srcarray, pd = dstarray) {...}  
```
  
 <span data-ttu-id="e7a8b-113">Para inicializar ponteiros de tipos diferentes, basta aninhar instruções `fixed`, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="e7a8b-113">To initialize pointers of different types, simply nest `fixed` statements, as shown in the following example.</span></span>  
  
 [!code-csharp[csrefKeywordsFixedLock#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/fixed-statement_3.cs)]  
  
 <span data-ttu-id="e7a8b-114">Depois que o código na instrução é executado, todas as variáveis fixadas são desafixadas e ficam sujeiras à coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="e7a8b-114">After the code in the statement is executed, any pinned variables are unpinned and subject to garbage collection.</span></span> <span data-ttu-id="e7a8b-115">Portanto, não aponte para essas variáveis fora da instrução `fixed`.</span><span class="sxs-lookup"><span data-stu-id="e7a8b-115">Therefore, do not point to those variables outside the `fixed` statement.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e7a8b-116">Os ponteiros inicializados em instruções fixas não podem ser modificados.</span><span class="sxs-lookup"><span data-stu-id="e7a8b-116">Pointers initialized in fixed statements cannot be modified.</span></span>  
  
 <span data-ttu-id="e7a8b-117">No modo não seguro, é possível alocar memória na pilha, local que não está sujeito à coleta de lixo e, portanto, não precisa ser fixado.</span><span class="sxs-lookup"><span data-stu-id="e7a8b-117">In unsafe mode, you can allocate memory on the stack, where it is not subject to garbage collection and therefore does not need to be pinned.</span></span> <span data-ttu-id="e7a8b-118">Para saber mais, confira [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md).</span><span class="sxs-lookup"><span data-stu-id="e7a8b-118">For more information, see [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e7a8b-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e7a8b-119">Example</span></span>  
 [!code-csharp[csrefKeywordsFixedLock#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/fixed-statement_4.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="e7a8b-120">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="e7a8b-120">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e7a8b-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e7a8b-121">See Also</span></span>  
 [<span data-ttu-id="e7a8b-122">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="e7a8b-122">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="e7a8b-123">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="e7a8b-123">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="e7a8b-124">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="e7a8b-124">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="e7a8b-125">unsafe</span><span class="sxs-lookup"><span data-stu-id="e7a8b-125">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
 [<span data-ttu-id="e7a8b-126">Buffers de tamanho fixo</span><span class="sxs-lookup"><span data-stu-id="e7a8b-126">Fixed Size Buffers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md)
