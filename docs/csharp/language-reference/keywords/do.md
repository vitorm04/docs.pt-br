---
title: "do (Referência de C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- do_CSharpKeyword
- do
dev_langs:
- CSharp
helpviewer_keywords:
- do keyword [C#]
ms.assetid: 50725f79-9ba6-4898-aa78-6e331568a1bb
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
ms.openlocfilehash: 58a9361c440bc1b17c5ab929ff7b45ba71ce50a4
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="do-c-reference"></a><span data-ttu-id="9448b-102">do (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="9448b-102">do (C# Reference)</span></span>
<span data-ttu-id="9448b-103">A instrução `do` executa uma instrução ou um bloco de instruções repetidamente até que uma expressão especificada seja avaliada como `false`.</span><span class="sxs-lookup"><span data-stu-id="9448b-103">The `do` statement executes a statement or a block of statements repeatedly until a specified expression evaluates to `false`.</span></span> <span data-ttu-id="9448b-104">O corpo do loop deve ser colocado entre chaves, `{}`, a menos que ele consista em uma única instrução.</span><span class="sxs-lookup"><span data-stu-id="9448b-104">The body of the loop must be enclosed in braces, `{}`, unless it consists of a single statement.</span></span> <span data-ttu-id="9448b-105">Nesse caso, as chaves são opcionais.</span><span class="sxs-lookup"><span data-stu-id="9448b-105">In that case, the braces are optional.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9448b-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9448b-106">Example</span></span>  
 <span data-ttu-id="9448b-107">No exemplo a seguir, as instruções de loop `do-while` são executadas desde que a variável `x` seja menor que 5.</span><span class="sxs-lookup"><span data-stu-id="9448b-107">In the following example, the `do-while` loop statements execute as long as the variable `x` is less than 5.</span></span>  
  
 <span data-ttu-id="9448b-108">[!code-cs[csrefKeywordsIteration#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/do_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="9448b-108">[!code-cs[csrefKeywordsIteration#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/do_1.cs)]</span></span>  
  
 <span data-ttu-id="9448b-109">Diferente da instrução [while](../../../csharp/language-reference/keywords/while.md), um loop `do-while` é executado uma vez antes que a expressão condicional seja avaliada.</span><span class="sxs-lookup"><span data-stu-id="9448b-109">Unlike the [while](../../../csharp/language-reference/keywords/while.md) statement, a `do-while` loop is executed one time before the conditional expression is evaluated.</span></span>  
  
 <span data-ttu-id="9448b-110">Em qualquer momento no bloco `do-while`, você pode interromper o loop usando a instrução [break](../../../csharp/language-reference/keywords/break.md).</span><span class="sxs-lookup"><span data-stu-id="9448b-110">At any point in the `do-while` block, you can break out of the loop using the [break](../../../csharp/language-reference/keywords/break.md) statement.</span></span> <span data-ttu-id="9448b-111">Você pode entrar diretamente na instrução de avaliação de expressão `while` usando a instrução [continue](../../../csharp/language-reference/keywords/continue.md).</span><span class="sxs-lookup"><span data-stu-id="9448b-111">You can step directly to the `while` expression evaluation statement by using the [continue](../../../csharp/language-reference/keywords/continue.md) statement.</span></span> <span data-ttu-id="9448b-112">Se a expressão `while` for avaliada como verdadeira, a execução continuará na primeira instrução no loop.</span><span class="sxs-lookup"><span data-stu-id="9448b-112">If the `while` expression evaluates to true, execution continues at the first statement in the loop.</span></span> <span data-ttu-id="9448b-113">Se a expressão for avaliada como falsa, a execução continuará na primeira instrução após o loop `do-while`.</span><span class="sxs-lookup"><span data-stu-id="9448b-113">If the expression evaluates to false, execution continues at the first statement after the `do-while` loop.</span></span>  
  
 <span data-ttu-id="9448b-114">Um loop `do-while` também pode ser encerrado pelas instruções [goto](../../../csharp/language-reference/keywords/goto.md), [retorn](../../../csharp/language-reference/keywords/return.md) ou [throw](../../../csharp/language-reference/keywords/throw.md).</span><span class="sxs-lookup"><span data-stu-id="9448b-114">A `do-while` loop can also be exited by the [goto](../../../csharp/language-reference/keywords/goto.md), [return](../../../csharp/language-reference/keywords/return.md), or [throw](../../../csharp/language-reference/keywords/throw.md) statements.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="9448b-115">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="9448b-115">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9448b-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9448b-116">See Also</span></span>  
 <span data-ttu-id="9448b-117">[Referência de C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="9448b-117">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="9448b-118">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="9448b-118">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="9448b-119">[Palavras-chave de C#](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="9448b-119">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="9448b-120">[Instrução do-while (C++)](/cpp/cpp/do-while-statement-cpp) </span><span class="sxs-lookup"><span data-stu-id="9448b-120">[do-while Statement (C++)](/cpp/cpp/do-while-statement-cpp) </span></span>  
 [<span data-ttu-id="9448b-121">Instruções de iteração</span><span class="sxs-lookup"><span data-stu-id="9448b-121">Iteration Statements</span></span>](../../../csharp/language-reference/keywords/iteration-statements.md)

