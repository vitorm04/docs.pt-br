---
description: do – Referência de C#
title: do – Referência de C#
ms.date: 05/28/2018
f1_keywords:
- do_CSharpKeyword
- do
helpviewer_keywords:
- do keyword [C#]
ms.assetid: 50725f79-9ba6-4898-aa78-6e331568a1bb
ms.openlocfilehash: 601231f23a58e8af8339a733677f0bbd92bb4ffc
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89126951"
---
# <a name="do-c-reference"></a><span data-ttu-id="43b77-103">do (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="43b77-103">do (C# Reference)</span></span>

<span data-ttu-id="43b77-104">A instrução `do` executa uma instrução ou um bloco de instruções enquanto uma expressão booliana especificada é avaliada como `true`.</span><span class="sxs-lookup"><span data-stu-id="43b77-104">The `do` statement executes a statement or a block of statements while a specified Boolean expression evaluates to `true`.</span></span> <span data-ttu-id="43b77-105">Como essa expressão é avaliada após cada execução do loop, um loop `do-while` é executado uma ou mais vezes.</span><span class="sxs-lookup"><span data-stu-id="43b77-105">Because that expression is evaluated after each execution of the loop, a `do-while` loop executes one or more times.</span></span> <span data-ttu-id="43b77-106">Isso é diferente do loop [while](while.md), que é executado zero ou mais vezes.</span><span class="sxs-lookup"><span data-stu-id="43b77-106">This differs from the [while](while.md) loop, which executes zero or more times.</span></span>

<span data-ttu-id="43b77-107">A qualquer momento dentro do bloco de instruções `do`, interrompa o loop usando a instrução [break](break.md).</span><span class="sxs-lookup"><span data-stu-id="43b77-107">At any point within the `do` statement block, you can break out of the loop by using the [break](break.md) statement.</span></span>

<span data-ttu-id="43b77-108">Você pode seguir diretamente para a avaliação da expressão `while` usando a instrução [continue](continue.md).</span><span class="sxs-lookup"><span data-stu-id="43b77-108">You can step directly to the evaluation of the `while` expression by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="43b77-109">Se a expressão for avaliada como `true`, a execução continuará na primeira instrução do loop.</span><span class="sxs-lookup"><span data-stu-id="43b77-109">If the expression evaluates to `true`, execution continues at the first statement in the loop.</span></span> <span data-ttu-id="43b77-110">Caso contrário, a execução continuará na primeira instrução após o loop.</span><span class="sxs-lookup"><span data-stu-id="43b77-110">Otherwise, execution continues at the first statement after the loop.</span></span>

<span data-ttu-id="43b77-111">Você também pode sair de um `do-while` loop pelas instruções [goto](goto.md), [Return](return.md)ou [throw](throw.md) .</span><span class="sxs-lookup"><span data-stu-id="43b77-111">You can also exit a `do-while` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

## <a name="example"></a><span data-ttu-id="43b77-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="43b77-112">Example</span></span>

<span data-ttu-id="43b77-113">O exemplo a seguir mostra o uso da instrução `do`.</span><span class="sxs-lookup"><span data-stu-id="43b77-113">The following example shows the usage of the `do` statement.</span></span> <span data-ttu-id="43b77-114">Selecione **Executar** para executar o código de exemplo.</span><span class="sxs-lookup"><span data-stu-id="43b77-114">Select **Run** to run the example code.</span></span> <span data-ttu-id="43b77-115">Depois disso, você pode modificar o código e executá-lo novamente.</span><span class="sxs-lookup"><span data-stu-id="43b77-115">After that you can modify the code and run it again.</span></span>

[!code-csharp-interactive[do loop example](snippets/IterationKeywordsExamples.cs#4)]

## <a name="c-language-specification"></a><span data-ttu-id="43b77-116">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="43b77-116">C# language specification</span></span>

<span data-ttu-id="43b77-117">Para saber mais, confira a seção [A instrução do](~/_csharplang/spec/statements.md#the-do-statement) na [Especificação da linguagem C#](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="43b77-117">For more information, see [The do statement](~/_csharplang/spec/statements.md#the-do-statement) section of the [C# language specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span>

## <a name="see-also"></a><span data-ttu-id="43b77-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="43b77-118">See also</span></span>

- [<span data-ttu-id="43b77-119">Referência do C#</span><span class="sxs-lookup"><span data-stu-id="43b77-119">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="43b77-120">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="43b77-120">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="43b77-121">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="43b77-121">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="43b77-122">Instrução while</span><span class="sxs-lookup"><span data-stu-id="43b77-122">while statement</span></span>](while.md)
