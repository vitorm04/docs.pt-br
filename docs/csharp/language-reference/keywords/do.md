---
title: do (Referência de C#)
ms.date: 05/28/2018
f1_keywords:
- do_CSharpKeyword
- do
helpviewer_keywords:
- do keyword [C#]
ms.assetid: 50725f79-9ba6-4898-aa78-6e331568a1bb
ms.openlocfilehash: b918b378623a239803fb4e0a65fcf82fd677b21f
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34566079"
---
# <a name="do-c-reference"></a><span data-ttu-id="ebfad-102">do (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="ebfad-102">do (C# Reference)</span></span>

<span data-ttu-id="ebfad-103">A instrução `do` executa uma instrução ou um bloco de instruções enquanto uma expressão booliana especificada é avaliada como `true`.</span><span class="sxs-lookup"><span data-stu-id="ebfad-103">The `do` statement executes a statement or a block of statements while a specified boolean expression evaluates to `true`.</span></span> <span data-ttu-id="ebfad-104">Como essa expressão é avaliada após cada execução do loop, um loop `do-while` é executado uma ou mais vezes.</span><span class="sxs-lookup"><span data-stu-id="ebfad-104">Because that expression is evaluated after each execution of the loop, a `do-while` loop executes one or more times.</span></span> <span data-ttu-id="ebfad-105">Isso é diferente do loop [while](while.md), que é executado zero ou mais vezes.</span><span class="sxs-lookup"><span data-stu-id="ebfad-105">This differs from the [while](while.md) loop, which executes zero or more times.</span></span>

<span data-ttu-id="ebfad-106">A qualquer momento dentro do bloco de instruções `do`, interrompa o loop usando a instrução [break](break.md).</span><span class="sxs-lookup"><span data-stu-id="ebfad-106">At any point within the `do` statement block, you can break out of the loop by using the [break](break.md) statement.</span></span>

<span data-ttu-id="ebfad-107">Você pode seguir diretamente para a avaliação da expressão `while` usando a instrução [continue](continue.md).</span><span class="sxs-lookup"><span data-stu-id="ebfad-107">You can step directly to the evaluation of the `while` expression by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="ebfad-108">Se a expressão for avaliada como `true`, a execução continuará na primeira instrução do loop.</span><span class="sxs-lookup"><span data-stu-id="ebfad-108">If the expression evaluates to `true`, execution continues at the first statement in the loop.</span></span> <span data-ttu-id="ebfad-109">Caso contrário, a execução continuará na primeira instrução após o loop.</span><span class="sxs-lookup"><span data-stu-id="ebfad-109">Otherwise, execution continues at the first statement after the loop.</span></span>

<span data-ttu-id="ebfad-110">Você também pode sair de um loop `do-while` com a instrução [goto](goto.md), [return](return.md) ou [throw](throw.md).</span><span class="sxs-lookup"><span data-stu-id="ebfad-110">You also can exit a `do-while` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

## <a name="example"></a><span data-ttu-id="ebfad-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ebfad-111">Example</span></span>

<span data-ttu-id="ebfad-112">O exemplo a seguir mostra o uso da instrução `do`.</span><span class="sxs-lookup"><span data-stu-id="ebfad-112">The following example shows the usage of the `do` statement.</span></span> <span data-ttu-id="ebfad-113">Selecione **Executar** para executar o código de exemplo.</span><span class="sxs-lookup"><span data-stu-id="ebfad-113">Select **Run** to run the example code.</span></span> <span data-ttu-id="ebfad-114">Depois disso, você pode modificar o código e executá-lo novamente.</span><span class="sxs-lookup"><span data-stu-id="ebfad-114">After that you can modify the code and run it again.</span></span>

[!code-csharp-interactive[do loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#4)]

## <a name="c-language-specification"></a><span data-ttu-id="ebfad-115">especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="ebfad-115">C# language specification</span></span>

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="ebfad-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ebfad-116">See also</span></span>

 [<span data-ttu-id="ebfad-117">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="ebfad-117">C# Reference</span></span>](../index.md)  
 [<span data-ttu-id="ebfad-118">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="ebfad-118">C# Programming Guide</span></span>](../../programming-guide/index.md)  
 [<span data-ttu-id="ebfad-119">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="ebfad-119">C# Keywords</span></span>](index.md)  
 [<span data-ttu-id="ebfad-120">Instrução do-while (C++)</span><span class="sxs-lookup"><span data-stu-id="ebfad-120">do-while Statement (C++)</span></span>](/cpp/cpp/do-while-statement-cpp)  
 [<span data-ttu-id="ebfad-121">Instruções de iteração</span><span class="sxs-lookup"><span data-stu-id="ebfad-121">Iteration Statements</span></span>](iteration-statements.md)  
 [<span data-ttu-id="ebfad-122">instrução while</span><span class="sxs-lookup"><span data-stu-id="ebfad-122">while statement</span></span>](while.md)  
