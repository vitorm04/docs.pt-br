---
title: do – Referência de C#
ms.custom: seodec18
ms.date: 05/28/2018
f1_keywords:
- do_CSharpKeyword
- do
helpviewer_keywords:
- do keyword [C#]
ms.assetid: 50725f79-9ba6-4898-aa78-6e331568a1bb
ms.openlocfilehash: 5566965e77feb9d46584146829284e9e0be71539
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66422046"
---
# <a name="do-c-reference"></a><span data-ttu-id="1afd7-102">do (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="1afd7-102">do (C# Reference)</span></span>

<span data-ttu-id="1afd7-103">A instrução `do` executa uma instrução ou um bloco de instruções enquanto uma expressão booliana especificada é avaliada como `true`.</span><span class="sxs-lookup"><span data-stu-id="1afd7-103">The `do` statement executes a statement or a block of statements while a specified Boolean expression evaluates to `true`.</span></span> <span data-ttu-id="1afd7-104">Como essa expressão é avaliada após cada execução do loop, um loop `do-while` é executado uma ou mais vezes.</span><span class="sxs-lookup"><span data-stu-id="1afd7-104">Because that expression is evaluated after each execution of the loop, a `do-while` loop executes one or more times.</span></span> <span data-ttu-id="1afd7-105">Isso é diferente do loop [while](while.md), que é executado zero ou mais vezes.</span><span class="sxs-lookup"><span data-stu-id="1afd7-105">This differs from the [while](while.md) loop, which executes zero or more times.</span></span>

<span data-ttu-id="1afd7-106">A qualquer momento dentro do bloco de instruções `do`, interrompa o loop usando a instrução [break](break.md).</span><span class="sxs-lookup"><span data-stu-id="1afd7-106">At any point within the `do` statement block, you can break out of the loop by using the [break](break.md) statement.</span></span>

<span data-ttu-id="1afd7-107">Você pode seguir diretamente para a avaliação da expressão `while` usando a instrução [continue](continue.md).</span><span class="sxs-lookup"><span data-stu-id="1afd7-107">You can step directly to the evaluation of the `while` expression by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="1afd7-108">Se a expressão for avaliada como `true`, a execução continuará na primeira instrução do loop.</span><span class="sxs-lookup"><span data-stu-id="1afd7-108">If the expression evaluates to `true`, execution continues at the first statement in the loop.</span></span> <span data-ttu-id="1afd7-109">Caso contrário, a execução continuará na primeira instrução após o loop.</span><span class="sxs-lookup"><span data-stu-id="1afd7-109">Otherwise, execution continues at the first statement after the loop.</span></span>

<span data-ttu-id="1afd7-110">Você também pode sair de um loop `do-while` com a instrução [goto](goto.md), [return](return.md) ou [throw](throw.md).</span><span class="sxs-lookup"><span data-stu-id="1afd7-110">You also can exit a `do-while` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

## <a name="example"></a><span data-ttu-id="1afd7-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1afd7-111">Example</span></span>

<span data-ttu-id="1afd7-112">O exemplo a seguir mostra o uso da instrução `do`.</span><span class="sxs-lookup"><span data-stu-id="1afd7-112">The following example shows the usage of the `do` statement.</span></span> <span data-ttu-id="1afd7-113">Selecione **Executar** para executar o código de exemplo.</span><span class="sxs-lookup"><span data-stu-id="1afd7-113">Select **Run** to run the example code.</span></span> <span data-ttu-id="1afd7-114">Depois disso, você pode modificar o código e executá-lo novamente.</span><span class="sxs-lookup"><span data-stu-id="1afd7-114">After that you can modify the code and run it again.</span></span>

[!code-csharp-interactive[do loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#4)]

## <a name="c-language-specification"></a><span data-ttu-id="1afd7-115">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="1afd7-115">C# language specification</span></span>

<span data-ttu-id="1afd7-116">Para saber mais, confira a seção [A instrução do](~/_csharplang/spec/statements.md#the-do-statement) na [Especificação da linguagem C#](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="1afd7-116">For more information, see [The do statement](~/_csharplang/spec/statements.md#the-do-statement) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1afd7-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1afd7-117">See also</span></span>

- [<span data-ttu-id="1afd7-118">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="1afd7-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="1afd7-119">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="1afd7-119">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="1afd7-120">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="1afd7-120">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="1afd7-121">instrução while</span><span class="sxs-lookup"><span data-stu-id="1afd7-121">while statement</span></span>](while.md)
