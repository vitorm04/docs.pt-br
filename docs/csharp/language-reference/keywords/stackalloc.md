---
title: "stackalloc (Referência de C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- stackalloc_CSharpKeyword
- stackalloc
dev_langs:
- CSharp
helpviewer_keywords:
- stackalloc keyword [C#]
ms.assetid: adc04c28-3ed2-4326-807a-7545df92b852
caps.latest.revision: 27
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 53d61cfdcf4d356a28881c57ad923017c2b479ae
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="stackalloc-c-reference"></a><span data-ttu-id="313aa-102">stackalloc (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="313aa-102">stackalloc (C# Reference)</span></span>
<span data-ttu-id="313aa-103">A palavra-chave `stackalloc` é usada em um contexto de código não seguro para alocar um bloco de memória na pilha.</span><span class="sxs-lookup"><span data-stu-id="313aa-103">The `stackalloc` keyword is used in an unsafe code context to allocate a block of memory on the stack.</span></span>  
  
```  
int* block = stackalloc int[100];  
```  
  
## <a name="remarks"></a><span data-ttu-id="313aa-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="313aa-104">Remarks</span></span>  
 <span data-ttu-id="313aa-105">A palavra-chave é válida somente em inicializadores de variável locais.</span><span class="sxs-lookup"><span data-stu-id="313aa-105">The keyword is valid only in local variable initializers.</span></span> <span data-ttu-id="313aa-106">O código a seguir gera erros de compilador.</span><span class="sxs-lookup"><span data-stu-id="313aa-106">The following code causes compiler errors.</span></span>  
  
```  
int* block;  
// The following assignment statement causes compiler errors. You  
// can use stackalloc only when declaring and initializing a local   
// variable.  
block = stackalloc int[100];  
```  
  
 <span data-ttu-id="313aa-107">Como os tipos de ponteiro estão envolvidos, `stackalloc` requer o contexto [unsafe](../../../csharp/language-reference/keywords/unsafe.md).</span><span class="sxs-lookup"><span data-stu-id="313aa-107">Because pointer types are involved, `stackalloc` requires [unsafe](../../../csharp/language-reference/keywords/unsafe.md) context.</span></span> <span data-ttu-id="313aa-108">Para obter mais informações, consulte [Código não seguro e ponteiros](../../../csharp/programming-guide/unsafe-code-pointers/index.md).</span><span class="sxs-lookup"><span data-stu-id="313aa-108">For more information, see [Unsafe Code and Pointers](../../../csharp/programming-guide/unsafe-code-pointers/index.md).</span></span>  
  
 <span data-ttu-id="313aa-109">`stackalloc` é como [_alloca](/cpp/c-runtime-library/reference/alloca) na biblioteca de tempo de execução C.</span><span class="sxs-lookup"><span data-stu-id="313aa-109">`stackalloc` is like [_alloca](/cpp/c-runtime-library/reference/alloca) in the C run-time library.</span></span>  
  
 <span data-ttu-id="313aa-110">O exemplo a seguir calcula e exibe os 20 primeiros números na sequência de Fibonacci.</span><span class="sxs-lookup"><span data-stu-id="313aa-110">The following example calculates and displays the first 20 numbers in the Fibonacci sequence.</span></span> <span data-ttu-id="313aa-111">Cada número é a soma dos dois números anteriores.</span><span class="sxs-lookup"><span data-stu-id="313aa-111">Each number is the sum of the previous two numbers.</span></span> <span data-ttu-id="313aa-112">No código, um bloco de memória de tamanho suficiente para conter 20 elementos do tipo `int` é alocado na pilha, não no heap.</span><span class="sxs-lookup"><span data-stu-id="313aa-112">In the code, a block of memory of sufficient size to contain 20 elements of type `int` is allocated on the stack, not the heap.</span></span> <span data-ttu-id="313aa-113">O endereço do bloco é armazenado no ponteiro `fib`.</span><span class="sxs-lookup"><span data-stu-id="313aa-113">The address of the block is stored in the pointer `fib`.</span></span> <span data-ttu-id="313aa-114">Essa memória não está sujeita à coleta de lixo e, portanto, não precisa ser fixado (usando [fixed](../../../csharp/language-reference/keywords/fixed-statement.md)).</span><span class="sxs-lookup"><span data-stu-id="313aa-114">This memory is not subject to garbage collection and therefore does not have to be pinned (by using [fixed](../../../csharp/language-reference/keywords/fixed-statement.md)).</span></span> <span data-ttu-id="313aa-115">O tempo de vida do bloco de memória é limitado ao tempo de vida do método que o define.</span><span class="sxs-lookup"><span data-stu-id="313aa-115">The lifetime of the memory block is limited to the lifetime of the method that defines it.</span></span> <span data-ttu-id="313aa-116">Você não pode liberar a memória antes de o método retornar.</span><span class="sxs-lookup"><span data-stu-id="313aa-116">You cannot free the memory before the method returns.</span></span>  
  
## <a name="example"></a><span data-ttu-id="313aa-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="313aa-117">Example</span></span>  
 <span data-ttu-id="313aa-118">[!code-cs[csrefKeywordsOperator#15](../../../csharp/language-reference/keywords/codesnippet/CSharp/stackalloc_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="313aa-118">[!code-cs[csrefKeywordsOperator#15](../../../csharp/language-reference/keywords/codesnippet/CSharp/stackalloc_1.cs)]</span></span>  
  
## <a name="security"></a><span data-ttu-id="313aa-119">Segurança</span><span class="sxs-lookup"><span data-stu-id="313aa-119">Security</span></span>  
 <span data-ttu-id="313aa-120">O código não seguro é menos seguro do que as alternativas seguras.</span><span class="sxs-lookup"><span data-stu-id="313aa-120">Unsafe code is less secure than safe alternatives.</span></span> <span data-ttu-id="313aa-121">No entanto, o uso de `stackalloc` habilita automaticamente os recursos de detecção de estouro de buffer no CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="313aa-121">However, the use of `stackalloc` automatically enables buffer overrun detection features in the common language runtime (CLR).</span></span> <span data-ttu-id="313aa-122">Se for detectada uma estouro de buffer, o processo será encerrado assim que possível para minimizar a chance de o código mal-intencionado ser executado.</span><span class="sxs-lookup"><span data-stu-id="313aa-122">If a buffer overrun is detected, the process is terminated as quickly as possible to minimize the chance that malicious code is executed.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="313aa-123">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="313aa-123">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="313aa-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="313aa-124">See Also</span></span>  
 <span data-ttu-id="313aa-125">[Referência de C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="313aa-125">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="313aa-126">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="313aa-126">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="313aa-127">[Palavras-chave de C#](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="313aa-127">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="313aa-128">[Palavras-chave do operador](../../../csharp/language-reference/keywords/operator-keywords.md) </span><span class="sxs-lookup"><span data-stu-id="313aa-128">[Operator Keywords](../../../csharp/language-reference/keywords/operator-keywords.md) </span></span>  
 [<span data-ttu-id="313aa-129">Código não seguro e ponteiros</span><span class="sxs-lookup"><span data-stu-id="313aa-129">Unsafe Code and Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/index.md)

