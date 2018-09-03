---
title: do (Referência de C#)
ms.date: 05/28/2018
f1_keywords:
- do_CSharpKeyword
- do
helpviewer_keywords:
- do keyword [C#]
ms.assetid: 50725f79-9ba6-4898-aa78-6e331568a1bb
ms.openlocfilehash: 89c13f5b547c13052e229ff6eb3a39ae5babce41
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43467199"
---
# <a name="do-c-reference"></a>do (Referência de C#)

A instrução `do` executa uma instrução ou um bloco de instruções enquanto uma expressão booliana especificada é avaliada como `true`. Como essa expressão é avaliada após cada execução do loop, um loop `do-while` é executado uma ou mais vezes. Isso é diferente do loop [while](while.md), que é executado zero ou mais vezes.

A qualquer momento dentro do bloco de instruções `do`, interrompa o loop usando a instrução [break](break.md).

Você pode seguir diretamente para a avaliação da expressão `while` usando a instrução [continue](continue.md). Se a expressão for avaliada como `true`, a execução continuará na primeira instrução do loop. Caso contrário, a execução continuará na primeira instrução após o loop.

Você também pode sair de um loop `do-while` com a instrução [goto](goto.md), [return](return.md) ou [throw](throw.md).

## <a name="example"></a>Exemplo

O exemplo a seguir mostra o uso da instrução `do`. Selecione **Executar** para executar o código de exemplo. Depois disso, você pode modificar o código e executá-lo novamente.

[!code-csharp-interactive[do loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#4)]

## <a name="c-language-specification"></a>especificação da linguagem C#

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)  
- [Guia de Programação em C#](../../programming-guide/index.md)  
- [Palavras-chave do C#](index.md)  
- [Instrução do-while (C++)](/cpp/cpp/do-while-statement-cpp)  
- [Instruções de iteração](iteration-statements.md)  
- [instrução while](while.md)  
