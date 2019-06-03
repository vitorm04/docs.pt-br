---
title: while – Referência de C#
ms.custom: seodec18
ms.date: 05/28/2018
f1_keywords:
- while_CSharpKeyword
- while
helpviewer_keywords:
- while keyword [C#]
ms.assetid: 72a0765c-6852-4aca-b327-4a11cb7f5c59
ms.openlocfilehash: 486936ae29552891c6a58913b6d5cf9a0d725a69
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66422486"
---
# <a name="while-c-reference"></a><span data-ttu-id="c758b-102">while (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="c758b-102">while (C# Reference)</span></span>

<span data-ttu-id="c758b-103">A instrução `while` executa uma instrução ou um bloco de instruções enquanto uma expressão booliana especificada é avaliada como `true`.</span><span class="sxs-lookup"><span data-stu-id="c758b-103">The `while` statement executes a statement or a block of statements while a specified Boolean expression evaluates to `true`.</span></span> <span data-ttu-id="c758b-104">Como essa expressão é avaliada antes de cada execução do loop, um loop `while` é executado zero ou mais vezes.</span><span class="sxs-lookup"><span data-stu-id="c758b-104">Because that expression is evaluated before each execution of the loop, a `while` loop executes zero or more times.</span></span> <span data-ttu-id="c758b-105">Isso difere do loop [do](do.md), que é executado uma ou mais vezes.</span><span class="sxs-lookup"><span data-stu-id="c758b-105">This differs from the [do](do.md) loop, which executes one or more times.</span></span>

<span data-ttu-id="c758b-106">A qualquer momento dentro do bloco de instruções `while`, interrompa o loop usando a instrução [break](break.md).</span><span class="sxs-lookup"><span data-stu-id="c758b-106">At any point within the `while` statement block, you can break out of the loop by using the [break](break.md) statement.</span></span>

<span data-ttu-id="c758b-107">Você pode seguir diretamente para a avaliação da expressão `while` usando a instrução [continue](continue.md).</span><span class="sxs-lookup"><span data-stu-id="c758b-107">You can step directly to the evaluation of the `while` expression by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="c758b-108">Se a expressão for avaliada como `true`, a execução continuará na primeira instrução do loop.</span><span class="sxs-lookup"><span data-stu-id="c758b-108">If the expression evaluates to `true`, execution continues at the first statement in the loop.</span></span> <span data-ttu-id="c758b-109">Caso contrário, a execução continuará na primeira instrução após o loop.</span><span class="sxs-lookup"><span data-stu-id="c758b-109">Otherwise, execution continues at the first statement after the loop.</span></span>

<span data-ttu-id="c758b-110">Você também pode sair de um loop `while` com a instrução [goto](goto.md), [return](return.md) ou [throw](throw.md).</span><span class="sxs-lookup"><span data-stu-id="c758b-110">You also can exit a `while` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

## <a name="example"></a><span data-ttu-id="c758b-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c758b-111">Example</span></span>

<span data-ttu-id="c758b-112">O exemplo a seguir mostra o uso da instrução `while`.</span><span class="sxs-lookup"><span data-stu-id="c758b-112">The following example shows the usage of the `while` statement.</span></span> <span data-ttu-id="c758b-113">Selecione **Executar** para executar o código de exemplo.</span><span class="sxs-lookup"><span data-stu-id="c758b-113">Select **Run** to run the example code.</span></span> <span data-ttu-id="c758b-114">Depois disso, você pode modificar o código e executá-lo novamente.</span><span class="sxs-lookup"><span data-stu-id="c758b-114">After that you can modify the code and run it again.</span></span>

[!code-csharp-interactive[while loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#3)]

## <a name="c-language-specification"></a><span data-ttu-id="c758b-115">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="c758b-115">C# language specification</span></span>

<span data-ttu-id="c758b-116">Para saber mais, confira a seção [A instrução while](~/_csharplang/spec/statements.md#the-while-statement) na [Especificação da linguagem C#](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="c758b-116">For more information, see [The while statement](~/_csharplang/spec/statements.md#the-while-statement) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c758b-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c758b-117">See also</span></span>

- [<span data-ttu-id="c758b-118">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="c758b-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="c758b-119">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="c758b-119">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="c758b-120">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="c758b-120">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="c758b-121">Instrução do</span><span class="sxs-lookup"><span data-stu-id="c758b-121">do statement</span></span>](do.md)
