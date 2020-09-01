---
description: while – Referência de C#
title: while – Referência de C#
ms.date: 05/28/2018
f1_keywords:
- while_CSharpKeyword
- while
helpviewer_keywords:
- while keyword [C#]
ms.assetid: 72a0765c-6852-4aca-b327-4a11cb7f5c59
ms.openlocfilehash: 97299f9ac6f2cdd6bbddf831b3ee2ad711935fbe
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89141862"
---
# <a name="while-c-reference"></a><span data-ttu-id="9b235-103">while (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="9b235-103">while (C# Reference)</span></span>

<span data-ttu-id="9b235-104">A instrução `while` executa uma instrução ou um bloco de instruções enquanto uma expressão booliana especificada é avaliada como `true`.</span><span class="sxs-lookup"><span data-stu-id="9b235-104">The `while` statement executes a statement or a block of statements while a specified Boolean expression evaluates to `true`.</span></span> <span data-ttu-id="9b235-105">Como essa expressão é avaliada antes de cada execução do loop, um loop `while` é executado zero ou mais vezes.</span><span class="sxs-lookup"><span data-stu-id="9b235-105">Because that expression is evaluated before each execution of the loop, a `while` loop executes zero or more times.</span></span> <span data-ttu-id="9b235-106">Isso difere do loop [do](do.md), que é executado uma ou mais vezes.</span><span class="sxs-lookup"><span data-stu-id="9b235-106">This differs from the [do](do.md) loop, which executes one or more times.</span></span>

<span data-ttu-id="9b235-107">A qualquer momento dentro do bloco de instruções `while`, interrompa o loop usando a instrução [break](break.md).</span><span class="sxs-lookup"><span data-stu-id="9b235-107">At any point within the `while` statement block, you can break out of the loop by using the [break](break.md) statement.</span></span>

<span data-ttu-id="9b235-108">Você pode seguir diretamente para a avaliação da expressão `while` usando a instrução [continue](continue.md).</span><span class="sxs-lookup"><span data-stu-id="9b235-108">You can step directly to the evaluation of the `while` expression by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="9b235-109">Se a expressão for avaliada como `true`, a execução continuará na primeira instrução do loop.</span><span class="sxs-lookup"><span data-stu-id="9b235-109">If the expression evaluates to `true`, execution continues at the first statement in the loop.</span></span> <span data-ttu-id="9b235-110">Caso contrário, a execução continuará na primeira instrução após o loop.</span><span class="sxs-lookup"><span data-stu-id="9b235-110">Otherwise, execution continues at the first statement after the loop.</span></span>

<span data-ttu-id="9b235-111">Você também pode sair de um `while` loop pelas instruções [goto](goto.md), [Return](return.md)ou [throw](throw.md) .</span><span class="sxs-lookup"><span data-stu-id="9b235-111">You can also exit a `while` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

## <a name="example"></a><span data-ttu-id="9b235-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9b235-112">Example</span></span>

<span data-ttu-id="9b235-113">O exemplo a seguir mostra o uso da instrução `while`.</span><span class="sxs-lookup"><span data-stu-id="9b235-113">The following example shows the usage of the `while` statement.</span></span> <span data-ttu-id="9b235-114">Selecione **Executar** para executar o código de exemplo.</span><span class="sxs-lookup"><span data-stu-id="9b235-114">Select **Run** to run the example code.</span></span> <span data-ttu-id="9b235-115">Depois disso, você pode modificar o código e executá-lo novamente.</span><span class="sxs-lookup"><span data-stu-id="9b235-115">After that you can modify the code and run it again.</span></span>

[!code-csharp-interactive[while loop example](snippets/IterationKeywordsExamples.cs#3)]

## <a name="c-language-specification"></a><span data-ttu-id="9b235-116">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="9b235-116">C# language specification</span></span>

<span data-ttu-id="9b235-117">Para saber mais, confira a seção [A instrução while](~/_csharplang/spec/statements.md#the-while-statement) na [Especificação da linguagem C#](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="9b235-117">For more information, see [The while statement](~/_csharplang/spec/statements.md#the-while-statement) section of the [C# language specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span>

## <a name="see-also"></a><span data-ttu-id="9b235-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="9b235-118">See also</span></span>

- [<span data-ttu-id="9b235-119">Referência do C#</span><span class="sxs-lookup"><span data-stu-id="9b235-119">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="9b235-120">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="9b235-120">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="9b235-121">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="9b235-121">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="9b235-122">instrução do</span><span class="sxs-lookup"><span data-stu-id="9b235-122">do statement</span></span>](do.md)
