---
title: "stackalloc (Referência de C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- stackalloc_CSharpKeyword
- stackalloc
helpviewer_keywords: stackalloc keyword [C#]
ms.assetid: adc04c28-3ed2-4326-807a-7545df92b852
caps.latest.revision: "27"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ad4453f889a344fcd44dfad44a30fef07380b6a3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="stackalloc-c-reference"></a><span data-ttu-id="4271e-102">stackalloc (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="4271e-102">stackalloc (C# Reference)</span></span>
<span data-ttu-id="4271e-103">A palavra-chave `stackalloc` é usada em um contexto de código não seguro para alocar um bloco de memória na pilha.</span><span class="sxs-lookup"><span data-stu-id="4271e-103">The `stackalloc` keyword is used in an unsafe code context to allocate a block of memory on the stack.</span></span>  
  
```  
int* block = stackalloc int[100];  
```  
  
## <a name="remarks"></a><span data-ttu-id="4271e-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="4271e-104">Remarks</span></span>  
 <span data-ttu-id="4271e-105">A palavra-chave é válida somente em inicializadores de variável locais.</span><span class="sxs-lookup"><span data-stu-id="4271e-105">The keyword is valid only in local variable initializers.</span></span> <span data-ttu-id="4271e-106">O código a seguir gera erros de compilador.</span><span class="sxs-lookup"><span data-stu-id="4271e-106">The following code causes compiler errors.</span></span>  
  
```  
int* block;  
// The following assignment statement causes compiler errors. You  
// can use stackalloc only when declaring and initializing a local   
// variable.  
block = stackalloc int[100];  
```  
  
 <span data-ttu-id="4271e-107">Como os tipos de ponteiro estão envolvidos, `stackalloc` requer o contexto [unsafe](../../../csharp/language-reference/keywords/unsafe.md).</span><span class="sxs-lookup"><span data-stu-id="4271e-107">Because pointer types are involved, `stackalloc` requires [unsafe](../../../csharp/language-reference/keywords/unsafe.md) context.</span></span> <span data-ttu-id="4271e-108">Para obter mais informações, consulte [Código não seguro e ponteiros](../../../csharp/programming-guide/unsafe-code-pointers/index.md).</span><span class="sxs-lookup"><span data-stu-id="4271e-108">For more information, see [Unsafe Code and Pointers](../../../csharp/programming-guide/unsafe-code-pointers/index.md).</span></span>  
  
 <span data-ttu-id="4271e-109">`stackalloc` é como [_alloca](/cpp/c-runtime-library/reference/alloca) na biblioteca de tempo de execução C.</span><span class="sxs-lookup"><span data-stu-id="4271e-109">`stackalloc` is like [_alloca](/cpp/c-runtime-library/reference/alloca) in the C run-time library.</span></span>  
  
 <span data-ttu-id="4271e-110">O exemplo a seguir calcula e exibe os 20 primeiros números na sequência de Fibonacci.</span><span class="sxs-lookup"><span data-stu-id="4271e-110">The following example calculates and displays the first 20 numbers in the Fibonacci sequence.</span></span> <span data-ttu-id="4271e-111">Cada número é a soma dos dois números anteriores.</span><span class="sxs-lookup"><span data-stu-id="4271e-111">Each number is the sum of the previous two numbers.</span></span> <span data-ttu-id="4271e-112">No código, um bloco de memória de tamanho suficiente para conter 20 elementos do tipo `int` é alocado na pilha, não no heap.</span><span class="sxs-lookup"><span data-stu-id="4271e-112">In the code, a block of memory of sufficient size to contain 20 elements of type `int` is allocated on the stack, not the heap.</span></span> <span data-ttu-id="4271e-113">O endereço do bloco é armazenado no ponteiro `fib`.</span><span class="sxs-lookup"><span data-stu-id="4271e-113">The address of the block is stored in the pointer `fib`.</span></span> <span data-ttu-id="4271e-114">Essa memória não está sujeita à coleta de lixo e, portanto, não precisa ser fixado (usando [fixed](../../../csharp/language-reference/keywords/fixed-statement.md)).</span><span class="sxs-lookup"><span data-stu-id="4271e-114">This memory is not subject to garbage collection and therefore does not have to be pinned (by using [fixed](../../../csharp/language-reference/keywords/fixed-statement.md)).</span></span> <span data-ttu-id="4271e-115">O tempo de vida do bloco de memória é limitado ao tempo de vida do método que o define.</span><span class="sxs-lookup"><span data-stu-id="4271e-115">The lifetime of the memory block is limited to the lifetime of the method that defines it.</span></span> <span data-ttu-id="4271e-116">Você não pode liberar a memória antes de o método retornar.</span><span class="sxs-lookup"><span data-stu-id="4271e-116">You cannot free the memory before the method returns.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4271e-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4271e-117">Example</span></span>  
 [!code-csharp[csrefKeywordsOperator#15](../../../csharp/language-reference/keywords/codesnippet/CSharp/stackalloc_1.cs)]  
  
## <a name="security"></a><span data-ttu-id="4271e-118">Segurança</span><span class="sxs-lookup"><span data-stu-id="4271e-118">Security</span></span>  
 <span data-ttu-id="4271e-119">O código não seguro é menos seguro do que as alternativas seguras.</span><span class="sxs-lookup"><span data-stu-id="4271e-119">Unsafe code is less secure than safe alternatives.</span></span> <span data-ttu-id="4271e-120">No entanto, o uso de `stackalloc` habilita automaticamente os recursos de detecção de estouro de buffer no CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="4271e-120">However, the use of `stackalloc` automatically enables buffer overrun detection features in the common language runtime (CLR).</span></span> <span data-ttu-id="4271e-121">Se for detectada uma estouro de buffer, o processo será encerrado assim que possível para minimizar a chance de o código mal-intencionado ser executado.</span><span class="sxs-lookup"><span data-stu-id="4271e-121">If a buffer overrun is detected, the process is terminated as quickly as possible to minimize the chance that malicious code is executed.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="4271e-122">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="4271e-122">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="4271e-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4271e-123">See Also</span></span>  
 [<span data-ttu-id="4271e-124">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="4271e-124">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="4271e-125">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="4271e-125">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="4271e-126">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="4271e-126">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="4271e-127">Palavras-chave do operador</span><span class="sxs-lookup"><span data-stu-id="4271e-127">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)  
 [<span data-ttu-id="4271e-128">Código não seguro e ponteiros</span><span class="sxs-lookup"><span data-stu-id="4271e-128">Unsafe Code and Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/index.md)
