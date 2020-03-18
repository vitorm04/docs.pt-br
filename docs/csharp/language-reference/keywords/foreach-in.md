---
title: Instrução foreach do C#
ms.date: 05/17/2019
f1_keywords:
- foreach
- foreach_CSharpKeyword
helpviewer_keywords:
- foreach keyword [C#]
- foreach statement [C#]
- in keyword [C#]
ms.assetid: 5a9c5ddc-5fd3-457a-9bb6-9abffcd874ec
ms.openlocfilehash: dbe4f4e95c2b99f1be47885e39d51db81ba3a97d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173699"
---
# <a name="foreach-in-c-reference"></a>foreach, in (Referência em C#)

A instrução `foreach` executa uma instrução ou um bloco de instruções para cada elemento em uma instância do tipo que implementa a interface <xref:System.Collections.IEnumerable?displayProperty=nameWithType> ou <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>. A instrução `foreach` não está limitada a esses tipos e pode ser aplicada a uma instância de qualquer tipo que satisfaça as seguintes condições:

- incluir um método `GetEnumerator` público sem parâmetros, cujo tipo de retorno é um tipo de classe, estrutura ou interface,
- o tipo de retorno do método `GetEnumerator` tem a propriedade `Current` pública e o método `MoveNext` público sem parâmetros, cujo tipo de retorno é <xref:System.Boolean>.

Começando com C# 7.3, se a `Current` propriedade do enumerador`ref T` `T` retornar um valor de retorno [de referência](ref.md#reference-return-values) (onde está `ref` `ref readonly` o tipo do elemento de coleta), você pode declarar a variável de iteração com o ou modificador.

A partir de C# `await` 8.0, o `foreach` operador pode ser aplicado <xref:System.Collections.Generic.IAsyncEnumerable%601> à declaração quando o tipo de coleta implementa a interface. Cada iteração do loop pode ser suspensa enquanto o próximo elemento é recuperado assíncronamente. Por padrão, os elementos de fluxo são processados no contexto capturado. Se você quiser desativar a captura do <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait%2A?displayProperty=nameWithType> contexto, use o método de extensão. Para obter mais informações sobre contextos de sincronização e captura do contexto atual, consulte o artigo sobre [o consumo do padrão assíncrono baseado em tarefas](../../../standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md).

Em qualquer ponto dentro do bloco de instrução `foreach`, você pode sair do loop usando a instrução [break](break.md) ou seguir para a próxima iteração no loop usando a instrução [continue](continue.md). Você também pode sair de um loop `foreach` com a instrução [goto](goto.md), [return](return.md) ou [throw](throw.md).

Se a instrução `foreach` for aplicada a `null`, uma <xref:System.NullReferenceException> será gerada. Se a coleta `foreach` de origem da declaração `foreach` estiver vazia, o corpo do laço não é executado e pulado.

## <a name="examples"></a>Exemplos

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

O exemplo a seguir mostra o uso da instrução `foreach` com uma instância do tipo <xref:System.Collections.Generic.List%601> que implementa a interface <xref:System.Collections.Generic.IEnumerable%601>:

[!code-csharp-interactive[list example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#1)]

O exemplo a seguir usa a instrução `foreach` com uma instância do tipo <xref:System.Span%601?displayProperty=nameWithType>, que não implementa nenhuma interface:

[!code-csharp[span example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#2)]

O exemplo a seguir usa uma variável de iteração `ref` para definir o valor de cada item em uma matriz stackalloc. A versão `ref readonly` itera a coleção para imprimir todos os valores. A declaração `readonly` usa uma declaração de variável local implícita. Declarações de variável implícita podem ser usadas com declarações `ref` ou `ref readonly`, assim como declarações de variável tipadas explicitamente.

[!code-csharp[ref span example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#RefSpan)]

O exemplo `await foreach` a seguir usa para iterar uma coleção que gera cada elemento assíncronamente:

[!code-csharp[ref span example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#AwaitForeach)]

## <a name="c-language-specification"></a>especificação da linguagem C#

Para obter mais informações, confira a seção [A instrução foreach](~/_csharplang/spec/statements.md#the-foreach-statement) na [Especificação da linguagem C#](/dotnet/csharp/language-reference/language-specification/introduction).

## <a name="see-also"></a>Confira também

- [C# Referência](../index.md)
- [C# Guia de Programação](../../programming-guide/index.md)
- [Palavras-chave do C#](index.md)
- [Usar foreach com matrizes](../../programming-guide/arrays/using-foreach-with-arrays.md)
- [para declaração](for.md)
