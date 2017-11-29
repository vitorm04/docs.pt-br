---
title: "while (Referência de C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- while_CSharpKeyword
- while
helpviewer_keywords: while keyword [C#]
ms.assetid: 72a0765c-6852-4aca-b327-4a11cb7f5c59
caps.latest.revision: "22"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 420b409689d877c3e1ac744e8d7a65500cf8f964
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="while-c-reference"></a><span data-ttu-id="45cce-102">while (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="45cce-102">while (C# Reference)</span></span>
<span data-ttu-id="45cce-103">A instrução `while` executa uma instrução ou um bloco de instruções até que uma expressão especificada seja avaliada como `false`.</span><span class="sxs-lookup"><span data-stu-id="45cce-103">The `while` statement executes a statement or a block of statements until a specified expression evaluates to `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="45cce-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="45cce-104">Example</span></span>  
 [!code-csharp[csrefKeywordsIteration#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/while_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="45cce-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="45cce-105">Example</span></span>  
 [!code-csharp[csrefKeywordsIteration#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/while_2.cs)]  
  
## <a name="example"></a><span data-ttu-id="45cce-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="45cce-106">Example</span></span>  
 <span data-ttu-id="45cce-107">Uma vez que o teste da expressão `while` ocorre antes de cada execução do loop, um loop `while` é executado zero ou mais vezes.</span><span class="sxs-lookup"><span data-stu-id="45cce-107">Because the test of the `while` expression takes place before each execution of the loop, a `while` loop executes zero or more times.</span></span> <span data-ttu-id="45cce-108">Isso difere do loop [do](../../../csharp/language-reference/keywords/do.md), que é executado uma ou mais vezes.</span><span class="sxs-lookup"><span data-stu-id="45cce-108">This differs from the [do](../../../csharp/language-reference/keywords/do.md) loop, which executes one or more times.</span></span>  
  
 <span data-ttu-id="45cce-109">Um loop `while` pode ser finalizado quando uma instrução [break](../../../csharp/language-reference/keywords/break.md), [goto](../../../csharp/language-reference/keywords/goto.md), [return](../../../csharp/language-reference/keywords/return.md) ou [throw](../../../csharp/language-reference/keywords/throw.md) transfere o controle para fora do loop.</span><span class="sxs-lookup"><span data-stu-id="45cce-109">A `while` loop can be terminated when a [break](../../../csharp/language-reference/keywords/break.md), [goto](../../../csharp/language-reference/keywords/goto.md), [return](../../../csharp/language-reference/keywords/return.md), or [throw](../../../csharp/language-reference/keywords/throw.md) statement transfers control outside the loop.</span></span> <span data-ttu-id="45cce-110">Para passar o controle para a próxima iteração sem sair do loop, use a instrução [continue](../../../csharp/language-reference/keywords/continue.md).</span><span class="sxs-lookup"><span data-stu-id="45cce-110">To pass control to the next iteration without exiting the loop, use the [continue](../../../csharp/language-reference/keywords/continue.md) statement.</span></span> <span data-ttu-id="45cce-111">Observe a diferença na saída nos três exemplos anteriores, dependendo de onde `int n` é incrementado.</span><span class="sxs-lookup"><span data-stu-id="45cce-111">Notice the difference in output in the three previous examples, depending on where `int n` is incremented.</span></span> <span data-ttu-id="45cce-112">No exemplo abaixo, nenhuma saída é gerada.</span><span class="sxs-lookup"><span data-stu-id="45cce-112">In the example below no output is generated.</span></span>  
  
 [!code-csharp[csrefKeywordsIteration#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/while_3.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="45cce-113">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="45cce-113">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="45cce-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="45cce-114">See Also</span></span>  
 [<span data-ttu-id="45cce-115">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="45cce-115">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="45cce-116">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="45cce-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="45cce-117">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="45cce-117">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="45cce-118">Instrução while (C++)</span><span class="sxs-lookup"><span data-stu-id="45cce-118">while Statement (C++)</span></span>](/cpp/cpp/while-statement-cpp)  
 [<span data-ttu-id="45cce-119">Instruções de iteração</span><span class="sxs-lookup"><span data-stu-id="45cce-119">Iteration Statements</span></span>](../../../csharp/language-reference/keywords/iteration-statements.md)
