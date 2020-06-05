---
title: Instrução foreach do C#
ms.date: 06/03/2020
f1_keywords:
- foreach
- foreach_CSharpKeyword
helpviewer_keywords:
- foreach keyword [C#]
- foreach statement [C#]
- in keyword [C#]
ms.assetid: 5a9c5ddc-5fd3-457a-9bb6-9abffcd874ec
ms.openlocfilehash: 1645a246c9feee2a92c0d4e4bbeda47f0afde7d9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401882"
---
# <a name="foreach-in-c-reference"></a>foreach, in (Referência em C#)

A instrução `foreach` executa uma instrução ou um bloco de instruções para cada elemento em uma instância do tipo que implementa a interface <xref:System.Collections.IEnumerable?displayProperty=nameWithType> ou <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>. A `foreach` instrução não está limitada a esses tipos e pode ser aplicada a uma instância de qualquer tipo que satisfaça as seguintes condições:

- incluir um método `GetEnumerator` público sem parâmetros, cujo tipo de retorno é um tipo de classe, estrutura ou interface,
- o tipo de retorno do método `GetEnumerator` tem a propriedade `Current` pública e o método `MoveNext` público sem parâmetros, cujo tipo de retorno é <xref:System.Boolean>.

Na maioria dos usos, `foreach` itera uma `IEnumerable<T>` expressão em que cada elemento é do tipo `T` . No entanto, os elementos podem ser qualquer tipo que tenha uma conversão implícita ou explícita do tipo da `Current` propriedade. Se a `Current` Propriedade retornar `SomeType` , o tipo dos elementos poderá ser:

- Qualquer uma das classes base do `SomeType` .
- Qualquer uma das interfaces implementadas pelo `SomeType` .

Além disso, se `SomeType` for um `class` ou um `interface` e não `sealed` , o tipo de elementos pode incluir:

- Qualquer tipo derivado de `SomeType` .
- Qualquer interface arbitrária. Qualquer interface é permitida porque qualquer interface pode ser implementada por uma classe derivada de ou implementando `SomeType` .

Você pode declarar a variável de iteração usando qualquer tipo que corresponda às regras anteriores. Se a conversão de `SomeType` para o tipo da variável de iteração exigir uma conversão explícita, essa operação poderá gerar um <xref:System.InvalidCastException> quando a conversão falhar.

A partir do C# 7,3, se a propriedade do enumerador `Current` retornar um [valor de retorno de referência](ref.md#reference-return-values) ( `ref T` em que `T` é o tipo do elemento de coleção), você poderá declarar a variável de iteração com o `ref` `ref readonly` modificador ou.

A partir do C# 8,0, o `await` operador pode ser aplicado à `foreach` instrução quando o tipo de coleção implementa a <xref:System.Collections.Generic.IAsyncEnumerable%601> interface. Cada iteração do loop pode ser suspensa enquanto o próximo elemento é recuperado de forma assíncrona. Por padrão, os elementos de fluxo são processados no contexto capturado. Se você quiser desabilitar a captura do contexto, use o <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait%2A?displayProperty=nameWithType> método de extensão. Para obter mais informações sobre contextos de sincronização e como capturar o contexto atual, consulte o artigo sobre como [consumir o padrão assíncrono baseado em tarefa](../../../standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md).

Em qualquer ponto dentro do bloco de instrução `foreach`, você pode sair do loop usando a instrução [break](break.md) ou seguir para a próxima iteração no loop usando a instrução [continue](continue.md). Você também pode sair de um `foreach` loop pelas instruções [goto](goto.md), [Return](return.md)ou [throw](throw.md) .

Se a instrução `foreach` for aplicada a `null`, uma <xref:System.NullReferenceException> será gerada. Se a coleção de origem da `foreach` instrução estiver vazia, o corpo do `foreach` loop não será executado e ignorado.

## <a name="examples"></a>Exemplos

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

O exemplo a seguir mostra o uso da instrução `foreach` com uma instância do tipo <xref:System.Collections.Generic.List%601> que implementa a interface <xref:System.Collections.Generic.IEnumerable%601>:

:::code language="csharp" source="snippets/IterationKeywordsExamples.cs" id="1" interactive="try-dotnet-method" :::

O exemplo a seguir usa a instrução `foreach` com uma instância do tipo <xref:System.Span%601?displayProperty=nameWithType>, que não implementa nenhuma interface:

:::code language="csharp" source="snippets/IterationKeywordsExamples.cs" id="2" :::

O exemplo a seguir usa uma variável de iteração `ref` para definir o valor de cada item em uma matriz stackalloc. A versão `ref readonly` itera a coleção para imprimir todos os valores. A declaração `readonly` usa uma declaração de variável local implícita. Declarações de variável implícita podem ser usadas com declarações `ref` ou `ref readonly`, assim como declarações de variável tipadas explicitamente.

:::code language="csharp" source="snippets/IterationKeywordsExamples.cs" id="RefSpan" :::

O exemplo a seguir usa `await foreach` para iterar uma coleção que gera cada elemento de forma assíncrona:

:::code language="csharp" source="snippets/IterationKeywordsExamples.cs" id="AwaitForeach"  :::

## <a name="c-language-specification"></a>especificação da linguagem C#

Para obter mais informações, confira a seção [A instrução foreach](~/_csharplang/spec/statements.md#the-foreach-statement) na [Especificação da linguagem C#](/dotnet/csharp/language-reference/language-specification/introduction).

## <a name="see-also"></a>Confira também

- [Referência do C#](../index.md)
- [Guia de programação C#](../../programming-guide/index.md)
- [Palavras-chave do C#](index.md)
- [Usando foreach com matrizes](../../programming-guide/arrays/using-foreach-with-arrays.md)
- [Instrução for](for.md)
