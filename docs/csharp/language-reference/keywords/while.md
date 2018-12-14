---
title: while (Referência de C#)
ms.date: 05/28/2018
f1_keywords:
- while_CSharpKeyword
- while
helpviewer_keywords:
- while keyword [C#]
ms.assetid: 72a0765c-6852-4aca-b327-4a11cb7f5c59
ms.openlocfilehash: f465bc98c0348c3b3522c062cf3be5ed90ee414a
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53143500"
---
# <a name="while-c-reference"></a><span data-ttu-id="acda5-102">while (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="acda5-102">while (C# Reference)</span></span>

<span data-ttu-id="acda5-103">A instrução `while` executa uma instrução ou um bloco de instruções enquanto uma expressão booliana especificada é avaliada como `true`.</span><span class="sxs-lookup"><span data-stu-id="acda5-103">The `while` statement executes a statement or a block of statements while a specified Boolean expression evaluates to `true`.</span></span> <span data-ttu-id="acda5-104">Como essa expressão é avaliada antes de cada execução do loop, um loop `while` é executado zero ou mais vezes.</span><span class="sxs-lookup"><span data-stu-id="acda5-104">Because that expression is evaluated before each execution of the loop, a `while` loop executes zero or more times.</span></span> <span data-ttu-id="acda5-105">Isso difere do loop [do](do.md), que é executado uma ou mais vezes.</span><span class="sxs-lookup"><span data-stu-id="acda5-105">This differs from the [do](do.md) loop, which executes one or more times.</span></span>

<span data-ttu-id="acda5-106">A qualquer momento dentro do bloco de instruções `while`, interrompa o loop usando a instrução [break](break.md).</span><span class="sxs-lookup"><span data-stu-id="acda5-106">At any point within the `while` statement block, you can break out of the loop by using the [break](break.md) statement.</span></span>

<span data-ttu-id="acda5-107">Você pode seguir diretamente para a avaliação da expressão `while` usando a instrução [continue](continue.md).</span><span class="sxs-lookup"><span data-stu-id="acda5-107">You can step directly to the evaluation of the `while` expression by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="acda5-108">Se a expressão for avaliada como `true`, a execução continuará na primeira instrução do loop.</span><span class="sxs-lookup"><span data-stu-id="acda5-108">If the expression evaluates to `true`, execution continues at the first statement in the loop.</span></span> <span data-ttu-id="acda5-109">Caso contrário, a execução continuará na primeira instrução após o loop.</span><span class="sxs-lookup"><span data-stu-id="acda5-109">Otherwise, execution continues at the first statement after the loop.</span></span>

<span data-ttu-id="acda5-110">Você também pode sair de um loop `while` com a instrução [goto](goto.md), [return](return.md) ou [throw](throw.md).</span><span class="sxs-lookup"><span data-stu-id="acda5-110">You also can exit a `while` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

## <a name="example"></a><span data-ttu-id="acda5-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="acda5-111">Example</span></span>

<span data-ttu-id="acda5-112">O exemplo a seguir mostra o uso da instrução `while`.</span><span class="sxs-lookup"><span data-stu-id="acda5-112">The following example shows the usage of the `while` statement.</span></span> <span data-ttu-id="acda5-113">Selecione **Executar** para executar o código de exemplo.</span><span class="sxs-lookup"><span data-stu-id="acda5-113">Select **Run** to run the example code.</span></span> <span data-ttu-id="acda5-114">Depois disso, você pode modificar o código e executá-lo novamente.</span><span class="sxs-lookup"><span data-stu-id="acda5-114">After that you can modify the code and run it again.</span></span>

[!code-csharp-interactive[while loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#3)]

## <a name="c-language-specification"></a><span data-ttu-id="acda5-115">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="acda5-115">C# language specification</span></span>

<span data-ttu-id="acda5-116">Para saber mais, confira a seção [A instrução while](~/_csharplang/spec/statements.md#the-while-statement) na [Especificação da linguagem C#](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="acda5-116">For more information, see [The while statement](~/_csharplang/spec/statements.md#the-while-statement) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="acda5-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="acda5-117">See also</span></span>

- [<span data-ttu-id="acda5-118">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="acda5-118">C# Reference</span></span>](../index.md)  
- [<span data-ttu-id="acda5-119">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="acda5-119">C# Programming Guide</span></span>](../../programming-guide/index.md)  
- [<span data-ttu-id="acda5-120">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="acda5-120">C# Keywords</span></span>](index.md)  
- [<span data-ttu-id="acda5-121">Instruções de iteração</span><span class="sxs-lookup"><span data-stu-id="acda5-121">Iteration Statements</span></span>](iteration-statements.md)  
- [<span data-ttu-id="acda5-122">Instrução do</span><span class="sxs-lookup"><span data-stu-id="acda5-122">do statement</span></span>](do.md)  
