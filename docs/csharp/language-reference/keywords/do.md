---
title: do – Referência de C#
ms.date: 05/28/2018
f1_keywords:
- do_CSharpKeyword
- do
helpviewer_keywords:
- do keyword [C#]
ms.assetid: 50725f79-9ba6-4898-aa78-6e331568a1bb
ms.openlocfilehash: 1d4323366e567dab4b27b07803d0c06e731611ce
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81738901"
---
# <a name="do-c-reference"></a>do (Referência de C#)

A instrução `do` executa uma instrução ou um bloco de instruções enquanto uma expressão booliana especificada é avaliada como `true`. Como essa expressão é avaliada após cada execução do loop, um loop `do-while` é executado uma ou mais vezes. Isso é diferente do loop [while](while.md), que é executado zero ou mais vezes.

A qualquer momento dentro do bloco de instruções `do`, interrompa o loop usando a instrução [break](break.md).

Você pode seguir diretamente para a avaliação da expressão `while` usando a instrução [continue](continue.md). Se a expressão for avaliada como `true`, a execução continuará na primeira instrução do loop. Caso contrário, a execução continuará na primeira instrução após o loop.

Você também pode `do-while` sair de um loop pelas declarações [goto](goto.md), [return](return.md)ou [throw.](throw.md)

## <a name="example"></a>Exemplo

O exemplo a seguir mostra o uso da instrução `do`. Selecione **Executar** para executar o código de exemplo. Depois disso, você pode modificar o código e executá-lo novamente.

[!code-csharp-interactive[do loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#4)]

## <a name="c-language-specification"></a>especificação da linguagem C#

Para saber mais, confira a seção [A instrução do](~/_csharplang/spec/statements.md#the-do-statement) na [Especificação da linguagem C#](/dotnet/csharp/language-reference/language-specification/introduction).

## <a name="see-also"></a>Confira também

- [C# Referência](../index.md)
- [C# Guia de Programação](../../programming-guide/index.md)
- [C# Palavras-chave](index.md)
- [enquanto declaração](while.md)
