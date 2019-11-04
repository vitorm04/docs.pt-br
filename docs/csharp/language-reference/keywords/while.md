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
ms.openlocfilehash: ab0a8ba0b724757b4f239daf1d3319b989c4531a
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73421910"
---
# <a name="while-c-reference"></a>while (Referência de C#)

A instrução `while` executa uma instrução ou um bloco de instruções enquanto uma expressão booliana especificada é avaliada como `true`. Como essa expressão é avaliada antes de cada execução do loop, um loop `while` é executado zero ou mais vezes. Isso difere do loop [do](do.md), que é executado uma ou mais vezes.

A qualquer momento dentro do bloco de instruções `while`, interrompa o loop usando a instrução [break](break.md).

Você pode seguir diretamente para a avaliação da expressão `while` usando a instrução [continue](continue.md). Se a expressão for avaliada como `true`, a execução continuará na primeira instrução do loop. Caso contrário, a execução continuará na primeira instrução após o loop.

Você também pode sair de um loop `while` com a instrução [goto](goto.md), [return](return.md) ou [throw](throw.md).

## <a name="example"></a>Exemplo

O exemplo a seguir mostra o uso da instrução `while`. Selecione **Executar** para executar o código de exemplo. Depois disso, você pode modificar o código e executá-lo novamente.

[!code-csharp-interactive[while loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#3)]

## <a name="c-language-specification"></a>Especificação da linguagem C#

Para saber mais, confira a seção [A instrução while](~/_csharplang/spec/statements.md#the-while-statement) na [Especificação da linguagem C#](/dotnet/csharp/language-reference/language-specification/introduction).

## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)
- [Guia de Programação em C#](../../programming-guide/index.md)
- [Palavras-chave do C#](index.md)
- [Instrução do](do.md)
