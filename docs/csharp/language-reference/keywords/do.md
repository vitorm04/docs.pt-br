---
title: "do (Referência de C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- do_CSharpKeyword
- do
helpviewer_keywords: do keyword [C#]
ms.assetid: 50725f79-9ba6-4898-aa78-6e331568a1bb
caps.latest.revision: "22"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d24078d3fb985f643fb66aa456900d03d2ff3fce
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="do-c-reference"></a><span data-ttu-id="08e84-102">do (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="08e84-102">do (C# Reference)</span></span>
<span data-ttu-id="08e84-103">A instrução `do` executa uma instrução ou um bloco de instruções repetidamente até que uma expressão especificada seja avaliada como `false`.</span><span class="sxs-lookup"><span data-stu-id="08e84-103">The `do` statement executes a statement or a block of statements repeatedly until a specified expression evaluates to `false`.</span></span> <span data-ttu-id="08e84-104">O corpo do loop deve ser colocado entre chaves, `{}`, a menos que ele consista em uma única instrução.</span><span class="sxs-lookup"><span data-stu-id="08e84-104">The body of the loop must be enclosed in braces, `{}`, unless it consists of a single statement.</span></span> <span data-ttu-id="08e84-105">Nesse caso, as chaves são opcionais.</span><span class="sxs-lookup"><span data-stu-id="08e84-105">In that case, the braces are optional.</span></span>  
  
## <a name="example"></a><span data-ttu-id="08e84-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="08e84-106">Example</span></span>  
 <span data-ttu-id="08e84-107">No exemplo a seguir, as instruções de loop `do-while` são executadas desde que a variável `x` seja menor que 5.</span><span class="sxs-lookup"><span data-stu-id="08e84-107">In the following example, the `do-while` loop statements execute as long as the variable `x` is less than 5.</span></span>  
  
 [!code-csharp[csrefKeywordsIteration#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/do_1.cs)]  
  
 <span data-ttu-id="08e84-108">Diferente da instrução [while](../../../csharp/language-reference/keywords/while.md), um loop `do-while` é executado uma vez antes que a expressão condicional seja avaliada.</span><span class="sxs-lookup"><span data-stu-id="08e84-108">Unlike the [while](../../../csharp/language-reference/keywords/while.md) statement, a `do-while` loop is executed one time before the conditional expression is evaluated.</span></span>  
  
 <span data-ttu-id="08e84-109">Em qualquer momento no bloco `do-while`, você pode interromper o loop usando a instrução [break](../../../csharp/language-reference/keywords/break.md).</span><span class="sxs-lookup"><span data-stu-id="08e84-109">At any point in the `do-while` block, you can break out of the loop using the [break](../../../csharp/language-reference/keywords/break.md) statement.</span></span> <span data-ttu-id="08e84-110">Você pode entrar diretamente na instrução de avaliação de expressão `while` usando a instrução [continue](../../../csharp/language-reference/keywords/continue.md).</span><span class="sxs-lookup"><span data-stu-id="08e84-110">You can step directly to the `while` expression evaluation statement by using the [continue](../../../csharp/language-reference/keywords/continue.md) statement.</span></span> <span data-ttu-id="08e84-111">Se a expressão `while` for avaliada como verdadeira, a execução continuará na primeira instrução no loop.</span><span class="sxs-lookup"><span data-stu-id="08e84-111">If the `while` expression evaluates to true, execution continues at the first statement in the loop.</span></span> <span data-ttu-id="08e84-112">Se a expressão for avaliada como falsa, a execução continuará na primeira instrução após o loop `do-while`.</span><span class="sxs-lookup"><span data-stu-id="08e84-112">If the expression evaluates to false, execution continues at the first statement after the `do-while` loop.</span></span>  
  
 <span data-ttu-id="08e84-113">Um loop `do-while` também pode ser encerrado pelas instruções [goto](../../../csharp/language-reference/keywords/goto.md), [retorn](../../../csharp/language-reference/keywords/return.md) ou [throw](../../../csharp/language-reference/keywords/throw.md).</span><span class="sxs-lookup"><span data-stu-id="08e84-113">A `do-while` loop can also be exited by the [goto](../../../csharp/language-reference/keywords/goto.md), [return](../../../csharp/language-reference/keywords/return.md), or [throw](../../../csharp/language-reference/keywords/throw.md) statements.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="08e84-114">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="08e84-114">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="08e84-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="08e84-115">See Also</span></span>  
 [<span data-ttu-id="08e84-116">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="08e84-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="08e84-117">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="08e84-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="08e84-118">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="08e84-118">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="08e84-119">Instrução do-while (C++)</span><span class="sxs-lookup"><span data-stu-id="08e84-119">do-while Statement (C++)</span></span>](/cpp/cpp/do-while-statement-cpp)  
 [<span data-ttu-id="08e84-120">Instruções de iteração</span><span class="sxs-lookup"><span data-stu-id="08e84-120">Iteration Statements</span></span>](../../../csharp/language-reference/keywords/iteration-statements.md)
