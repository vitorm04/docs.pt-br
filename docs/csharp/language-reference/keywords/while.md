---
title: "while (Referência de C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- while_CSharpKeyword
- while
dev_langs:
- CSharp
helpviewer_keywords:
- while keyword [C#]
ms.assetid: 72a0765c-6852-4aca-b327-4a11cb7f5c59
caps.latest.revision: 22
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
ms.openlocfilehash: ed531c83dba02b38576bf8354b1ff92f075048bc
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="while-c-reference"></a><span data-ttu-id="35cf9-102">while (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="35cf9-102">while (C# Reference)</span></span>
<span data-ttu-id="35cf9-103">A instrução `while` executa uma instrução ou um bloco de instruções até que uma expressão especificada seja avaliada como `false`.</span><span class="sxs-lookup"><span data-stu-id="35cf9-103">The `while` statement executes a statement or a block of statements until a specified expression evaluates to `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="35cf9-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="35cf9-104">Example</span></span>  
 <span data-ttu-id="35cf9-105">[!code-cs[csrefKeywordsIteration#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/while_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="35cf9-105">[!code-cs[csrefKeywordsIteration#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/while_1.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="35cf9-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="35cf9-106">Example</span></span>  
 <span data-ttu-id="35cf9-107">[!code-cs[csrefKeywordsIteration#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/while_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="35cf9-107">[!code-cs[csrefKeywordsIteration#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/while_2.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="35cf9-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="35cf9-108">Example</span></span>  
 <span data-ttu-id="35cf9-109">Uma vez que o teste da expressão `while` ocorre antes de cada execução do loop, um loop `while` é executado zero ou mais vezes.</span><span class="sxs-lookup"><span data-stu-id="35cf9-109">Because the test of the `while` expression takes place before each execution of the loop, a `while` loop executes zero or more times.</span></span> <span data-ttu-id="35cf9-110">Isso difere do loop [do](../../../csharp/language-reference/keywords/do.md), que é executado uma ou mais vezes.</span><span class="sxs-lookup"><span data-stu-id="35cf9-110">This differs from the [do](../../../csharp/language-reference/keywords/do.md) loop, which executes one or more times.</span></span>  
  
 <span data-ttu-id="35cf9-111">Um loop `while` pode ser finalizado quando uma instrução [break](../../../csharp/language-reference/keywords/break.md), [goto](../../../csharp/language-reference/keywords/goto.md), [return](../../../csharp/language-reference/keywords/return.md) ou [throw](../../../csharp/language-reference/keywords/throw.md) transfere o controle para fora do loop.</span><span class="sxs-lookup"><span data-stu-id="35cf9-111">A `while` loop can be terminated when a [break](../../../csharp/language-reference/keywords/break.md), [goto](../../../csharp/language-reference/keywords/goto.md), [return](../../../csharp/language-reference/keywords/return.md), or [throw](../../../csharp/language-reference/keywords/throw.md) statement transfers control outside the loop.</span></span> <span data-ttu-id="35cf9-112">Para passar o controle para a próxima iteração sem sair do loop, use a instrução [continue](../../../csharp/language-reference/keywords/continue.md).</span><span class="sxs-lookup"><span data-stu-id="35cf9-112">To pass control to the next iteration without exiting the loop, use the [continue](../../../csharp/language-reference/keywords/continue.md) statement.</span></span> <span data-ttu-id="35cf9-113">Observe a diferença na saída nos três exemplos anteriores, dependendo de onde `int n` é incrementado.</span><span class="sxs-lookup"><span data-stu-id="35cf9-113">Notice the difference in output in the three previous examples, depending on where `int n` is incremented.</span></span> <span data-ttu-id="35cf9-114">No exemplo abaixo, nenhuma saída é gerada.</span><span class="sxs-lookup"><span data-stu-id="35cf9-114">In the example below no output is generated.</span></span>  
  
 <span data-ttu-id="35cf9-115">[!code-cs[csrefKeywordsIteration#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/while_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="35cf9-115">[!code-cs[csrefKeywordsIteration#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/while_3.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="35cf9-116">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="35cf9-116">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="35cf9-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="35cf9-117">See Also</span></span>  
 <span data-ttu-id="35cf9-118">[Referência de C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="35cf9-118">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="35cf9-119">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="35cf9-119">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="35cf9-120">[Palavras-chave de C#](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="35cf9-120">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="35cf9-121">[Instrução while (C++)](/cpp/cpp/while-statement-cpp) </span><span class="sxs-lookup"><span data-stu-id="35cf9-121">[while Statement (C++)](/cpp/cpp/while-statement-cpp) </span></span>  
 [<span data-ttu-id="35cf9-122">Instruções de iteração</span><span class="sxs-lookup"><span data-stu-id="35cf9-122">Iteration Statements</span></span>](../../../csharp/language-reference/keywords/iteration-statements.md)

