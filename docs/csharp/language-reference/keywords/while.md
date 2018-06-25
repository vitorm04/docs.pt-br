---
title: while (Referência de C#)
ms.date: 05/28/2018
f1_keywords:
- while_CSharpKeyword
- while
helpviewer_keywords:
- while keyword [C#]
ms.assetid: 72a0765c-6852-4aca-b327-4a11cb7f5c59
ms.openlocfilehash: c082107472ac53d05b3b43dd4d9d8afc508a16cb
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34565859"
---
# <a name="while-c-reference"></a><span data-ttu-id="730ac-102">while (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="730ac-102">while (C# Reference)</span></span>

<span data-ttu-id="730ac-103">A instrução `while` executa uma instrução ou um bloco de instruções enquanto uma expressão booliana especificada é avaliada como `true`.</span><span class="sxs-lookup"><span data-stu-id="730ac-103">The `while` statement executes a statement or a block of statements while a specified boolean expression evaluates to `true`.</span></span> <span data-ttu-id="730ac-104">Como essa expressão é avaliada antes de cada execução do loop, um loop `while` é executado zero ou mais vezes.</span><span class="sxs-lookup"><span data-stu-id="730ac-104">Because that expression is evaluated before each execution of the loop, a `while` loop executes zero or more times.</span></span> <span data-ttu-id="730ac-105">Isso difere do loop [do](do.md), que é executado uma ou mais vezes.</span><span class="sxs-lookup"><span data-stu-id="730ac-105">This differs from the [do](do.md) loop, which executes one or more times.</span></span>

<span data-ttu-id="730ac-106">A qualquer momento dentro do bloco de instruções `while`, interrompa o loop usando a instrução [break](break.md).</span><span class="sxs-lookup"><span data-stu-id="730ac-106">At any point within the `while` statement block, you can break out of the loop by using the [break](break.md) statement.</span></span>

<span data-ttu-id="730ac-107">Você pode seguir diretamente para a avaliação da expressão `while` usando a instrução [continue](continue.md).</span><span class="sxs-lookup"><span data-stu-id="730ac-107">You can step directly to the evaluation of the `while` expression by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="730ac-108">Se a expressão for avaliada como `true`, a execução continuará na primeira instrução do loop.</span><span class="sxs-lookup"><span data-stu-id="730ac-108">If the expression evaluates to `true`, execution continues at the first statement in the loop.</span></span> <span data-ttu-id="730ac-109">Caso contrário, a execução continuará na primeira instrução após o loop.</span><span class="sxs-lookup"><span data-stu-id="730ac-109">Otherwise, execution continues at the first statement after the loop.</span></span>

<span data-ttu-id="730ac-110">Você também pode sair de um loop `while` com a instrução [goto](goto.md), [return](return.md) ou [throw](throw.md).</span><span class="sxs-lookup"><span data-stu-id="730ac-110">You also can exit a `while` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

## <a name="example"></a><span data-ttu-id="730ac-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="730ac-111">Example</span></span>

<span data-ttu-id="730ac-112">O exemplo a seguir mostra o uso da instrução `while`.</span><span class="sxs-lookup"><span data-stu-id="730ac-112">The following example shows the usage of the `while` statement.</span></span> <span data-ttu-id="730ac-113">Selecione **Executar** para executar o código de exemplo.</span><span class="sxs-lookup"><span data-stu-id="730ac-113">Select **Run** to run the example code.</span></span> <span data-ttu-id="730ac-114">Depois disso, você pode modificar o código e executá-lo novamente.</span><span class="sxs-lookup"><span data-stu-id="730ac-114">After that you can modify the code and run it again.</span></span>

[!code-csharp-interactive[while loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#3)]

## <a name="c-language-specification"></a><span data-ttu-id="730ac-115">especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="730ac-115">C# language specification</span></span>

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="730ac-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="730ac-116">See also</span></span>

 [<span data-ttu-id="730ac-117">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="730ac-117">C# Reference</span></span>](../index.md)  
 [<span data-ttu-id="730ac-118">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="730ac-118">C# Programming Guide</span></span>](../../programming-guide/index.md)  
 [<span data-ttu-id="730ac-119">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="730ac-119">C# Keywords</span></span>](index.md)  
 [<span data-ttu-id="730ac-120">Instrução while (C++)</span><span class="sxs-lookup"><span data-stu-id="730ac-120">while Statement (C++)</span></span>](/cpp/cpp/while-statement-cpp)  
 [<span data-ttu-id="730ac-121">Instruções de iteração</span><span class="sxs-lookup"><span data-stu-id="730ac-121">Iteration Statements</span></span>](iteration-statements.md)  
 [<span data-ttu-id="730ac-122">Instrução do</span><span class="sxs-lookup"><span data-stu-id="730ac-122">do statement</span></span>](do.md)  
