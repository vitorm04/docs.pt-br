---
title: do – Referência de C#
ms.date: 05/28/2018
f1_keywords:
- do_CSharpKeyword
- do
helpviewer_keywords:
- do keyword [C#]
ms.assetid: 50725f79-9ba6-4898-aa78-6e331568a1bb
ms.openlocfilehash: 38224ce70c19ff67ad80b99d3da52155849f1341
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713596"
---
# <a name="do-c-reference"></a><span data-ttu-id="f5c7c-102">do (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="f5c7c-102">do (C# Reference)</span></span>

<span data-ttu-id="f5c7c-103">A instrução `do` executa uma instrução ou um bloco de instruções enquanto uma expressão booliana especificada é avaliada como `true`.</span><span class="sxs-lookup"><span data-stu-id="f5c7c-103">The `do` statement executes a statement or a block of statements while a specified Boolean expression evaluates to `true`.</span></span> <span data-ttu-id="f5c7c-104">Como essa expressão é avaliada após cada execução do loop, um loop `do-while` é executado uma ou mais vezes.</span><span class="sxs-lookup"><span data-stu-id="f5c7c-104">Because that expression is evaluated after each execution of the loop, a `do-while` loop executes one or more times.</span></span> <span data-ttu-id="f5c7c-105">Isso é diferente do loop [while](while.md), que é executado zero ou mais vezes.</span><span class="sxs-lookup"><span data-stu-id="f5c7c-105">This differs from the [while](while.md) loop, which executes zero or more times.</span></span>

<span data-ttu-id="f5c7c-106">A qualquer momento dentro do bloco de instruções `do`, interrompa o loop usando a instrução [break](break.md).</span><span class="sxs-lookup"><span data-stu-id="f5c7c-106">At any point within the `do` statement block, you can break out of the loop by using the [break](break.md) statement.</span></span>

<span data-ttu-id="f5c7c-107">Você pode seguir diretamente para a avaliação da expressão `while` usando a instrução [continue](continue.md).</span><span class="sxs-lookup"><span data-stu-id="f5c7c-107">You can step directly to the evaluation of the `while` expression by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="f5c7c-108">Se a expressão for avaliada como `true`, a execução continuará na primeira instrução do loop.</span><span class="sxs-lookup"><span data-stu-id="f5c7c-108">If the expression evaluates to `true`, execution continues at the first statement in the loop.</span></span> <span data-ttu-id="f5c7c-109">Caso contrário, a execução continuará na primeira instrução após o loop.</span><span class="sxs-lookup"><span data-stu-id="f5c7c-109">Otherwise, execution continues at the first statement after the loop.</span></span>

<span data-ttu-id="f5c7c-110">Você também pode sair de um loop `do-while` com a instrução [goto](goto.md), [return](return.md) ou [throw](throw.md).</span><span class="sxs-lookup"><span data-stu-id="f5c7c-110">You also can exit a `do-while` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

## <a name="example"></a><span data-ttu-id="f5c7c-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f5c7c-111">Example</span></span>

<span data-ttu-id="f5c7c-112">O exemplo a seguir mostra o uso da instrução `do`.</span><span class="sxs-lookup"><span data-stu-id="f5c7c-112">The following example shows the usage of the `do` statement.</span></span> <span data-ttu-id="f5c7c-113">Selecione **Executar** para executar o código de exemplo.</span><span class="sxs-lookup"><span data-stu-id="f5c7c-113">Select **Run** to run the example code.</span></span> <span data-ttu-id="f5c7c-114">Depois disso, você pode modificar o código e executá-lo novamente.</span><span class="sxs-lookup"><span data-stu-id="f5c7c-114">After that you can modify the code and run it again.</span></span>

[!code-csharp-interactive[do loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#4)]

## <a name="c-language-specification"></a><span data-ttu-id="f5c7c-115">especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="f5c7c-115">C# language specification</span></span>

<span data-ttu-id="f5c7c-116">Para saber mais, confira a seção [A instrução do](~/_csharplang/spec/statements.md#the-do-statement) na [Especificação da linguagem C#](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="f5c7c-116">For more information, see [The do statement](~/_csharplang/spec/statements.md#the-do-statement) section of the [C# language specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span>

## <a name="see-also"></a><span data-ttu-id="f5c7c-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="f5c7c-117">See also</span></span>

- [<span data-ttu-id="f5c7c-118">C# Referência</span><span class="sxs-lookup"><span data-stu-id="f5c7c-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="f5c7c-119">C# Guia de Programação</span><span class="sxs-lookup"><span data-stu-id="f5c7c-119">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="f5c7c-120">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="f5c7c-120">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="f5c7c-121">enquanto declaração</span><span class="sxs-lookup"><span data-stu-id="f5c7c-121">while statement</span></span>](while.md)
