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
ms.openlocfilehash: 2cf58e2edc5685032c2b9e590bc456e3a4e4d79b
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65633068"
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

Para saber mais, confira a seção [A instrução while](~/_csharplang/spec/statements.md#the-while-statement) na [Especificação da linguagem C#](../language-specification/index.md).

## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)
- [Guia de Programação em C#](../../programming-guide/index.md)
- [Palavras-chave do C#](index.md)
- [Instruções de iteração](iteration-statements.md)
- [Instrução do](do.md)
