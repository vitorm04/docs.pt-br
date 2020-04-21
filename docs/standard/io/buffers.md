---
title: System.Buffers - .NET
ms.date: 12/05/2019
ms.technology: dotnet-standard
helpviewer_keywords:
- buffers [.NET]
- I/O [.NET], buffers
author: rick-anderson
ms.author: riande
ms.openlocfilehash: d113def0182dc6a5bcea6c18b2d0e4b475946e31
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81739616"
---
# <a name="work-with-buffers-in-net"></a>Trabalhe com Buffers em .NET

Este artigo fornece uma visão geral dos tipos que ajudam a ler dados que são executados em vários buffers. Eles são usados principalmente <xref:System.IO.Pipelines.PipeReader> para apoiar objetos.

## <a name="ibufferwritert"></a>IBufferWriter\<T\>

<xref:System.Buffers.IBufferWriter%601?displayProperty=fullName>é um contrato para escrita tampão síncrona. No nível mais baixo, a interface:

- É básico e não é difícil de usar.
- Permite acesso <xref:System.Memory%601> a <xref:System.Span%601>um ou . O `Memory<T>` `Span<T>` ou pode ser escrito e `T` você pode determinar quantos itens foram escritos.

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet)]

O método anterior:

- Solicita um buffer de pelo menos `IBufferWriter<byte>` 5 `GetSpan(5)`bytes do uso .
- Escreve bytes para a seqüência ASCII `Span<byte>`"Hello" para o retornado .
- Chamadas <xref:System.Buffers.IBufferWriter%601> para indicar quantos bytes foram escritos para o buffer.

Este método de `Memory<T>` / `Span<T>` escrita usa o `IBufferWriter<T>`buffer fornecido pelo . Alternativamente, <xref:System.Buffers.BuffersExtensions.Write%2A> o método de extensão pode ser `IBufferWriter<T>`usado para copiar um buffer existente para o . `Write`faz o trabalho `GetSpan` / `Advance` de chamar conforme apropriado, então `Advance` não há necessidade de ligar depois de escrever:

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet2)]

<xref:System.Buffers.ArrayBufferWriter%601>é uma `IBufferWriter<T>` implementação de cuja loja de apoio é uma única matriz contígua.

### <a name="ibufferwriter-common-problems"></a>IBufferWriter problemas comuns

- `GetSpan`e `GetMemory` retornar um buffer com pelo menos a quantidade solicitada de memória. Não assuma tamanhos exatos de buffer.
- Não há garantia de que as chamadas sucessivas retornarão o mesmo buffer ou o buffer do mesmo tamanho.
- Um novo buffer deve ser `Advance` solicitado após a chamada para continuar a escrever mais dados. Um buffer adquirido anteriormente não `Advance` pode ser escrito depois de ter sido chamado.

## <a name="readonlysequencet"></a>ReadOnlySequence\<T\>

![ReadOnlySequence mostrando memória no tubo e abaixo dessa posição de seqüência de memória somente leitura](media/buffers/ro-sequence.png)

<xref:System.Buffers.ReadOnlySequence%601>é uma estrutura que pode representar uma seqüência contígua ou não contígua de `T`. Pode ser construído a partir de:

1. Uma `T[]`
1. Uma `ReadOnlyMemory<T>`
1. Um par de nó <xref:System.Buffers.ReadOnlySequenceSegment%601> de lista vinculado e índice para representar a posição inicial e final da seqüência.

A terceira representação é a mais interessante, pois tem `ReadOnlySequence<T>`implicações de desempenho em várias operações no:

|Representação|Operação|Complexidade|
---|---|---|
|`T[]`/`ReadOnlyMemory<T>`|`Length`|`O(1)`|
|`T[]`/`ReadOnlyMemory<T>`|`GetPosition(long)`|`O(1)`|
|`T[]`/`ReadOnlyMemory<T>`|`Slice(int, int)`|`O(1)`|
|`T[]`/`ReadOnlyMemory<T>`|`Slice(SequencePostion,  SequencePostion)`|`O(1)`|
|`ReadOnlySequenceSegment<T>`|`Length`|`O(1)`|
|`ReadOnlySequenceSegment<T>`|`GetPosition(long)`|`O(number of segments)`|
|`ReadOnlySequenceSegment<T>`|`Slice(int, int)`|`O(number of segments)`|
|`ReadOnlySequenceSegment<T>`|`Slice(SequencePostion, SequencePostion)`|`O(1)`|

Por causa dessa representação `ReadOnlySequence<T>` mista, o `SequencePosition` expõe índices como em vez de um inteiro. A: `SequencePosition`

- É um valor opaco que representa `ReadOnlySequence<T>` um índice no local de origem.
- Consiste em duas partes, um inteiro e um objeto. O que esses dois valores `ReadOnlySequence<T>`representam estão vinculados à implementação de .

### <a name="access-data"></a>Acessar dados

Os `ReadOnlySequence<T>` dados expõem como um `ReadOnlyMemory<T>`enumerado de . A enumeração de cada um dos segmentos pode ser feita usando um foreach básico:

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet3)]

O método anterior pesquisa cada segmento em busca de um byte específico. Se você precisa acompanhar cada `SequencePosition`segmento, <xref:System.Buffers.ReadOnlySequence%601.TryGet%2A?displayProperty=nameWithType> é mais apropriado. A próxima amostra altera o `SequencePosition` código anterior para retornar um em vez de um inteiro. A devolução de um `SequencePosition` tem o benefício de permitir que o chamador evite uma segunda varredura para obter os dados em um índice específico.

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet4)]

A combinação `SequencePosition` `TryGet` e age como um enumerador. O campo de posição é modificado no início de cada iteração para ser iniciada de cada segmento dentro do `ReadOnlySequence<T>`.

O método precedente existe como `ReadOnlySequence<T>`um método de extensão em . <xref:System.Buffers.BuffersExtensions.PositionOf%2A>pode ser usado para simplificar o código anterior:

```csharp
SequencePosition? FindIndexOf(in ReadOnlySequence<byte> buffer, byte data) => buffer.PositionOf(data);
```

#### <a name="process-a-readonlysequencet"></a>Processe um\<ReadOnlySequence T\>

O processamento `ReadOnlySequence<T>` de um pode ser desafiador, uma vez que os dados podem ser divididos em vários segmentos dentro da seqüência. Para obter o melhor desempenho, divida o código em dois caminhos:

- Um caminho rápido que lida com o caso de um único segmento.
- Um caminho lento que lida com os dados divididos entre segmentos.

Existem algumas abordagens que podem ser usadas para processar dados em seqüências multisegmentadas:

- Use [`SequenceReader<T>`](#sequencereadert)o .
- Analisar os dados segmento por segmento, acompanhando o `SequencePosition` índice dentro do segmento analisado. Isso evita alocações desnecessárias, mas pode ser ineficiente, especialmente para pequenos buffers.
- Copie `ReadOnlySequence<T>` o para uma matriz contígua e trate-o como um único buffer:
  - Se o tamanho `ReadOnlySequence<T>` do for pequeno, pode ser razoável copiar os dados em um buffer alocado em pilha usando o operador [stackalloc.](../../csharp/language-reference/operators/stackalloc.md)
  - Copie `ReadOnlySequence<T>` o em uma <xref:System.Buffers.ArrayPool%601.Shared%2A?displayProperty=nameWithType>matriz agrupada usando .
  - Use [`ReadOnlySequence<T>.ToArray()`](xref:System.Buffers.BuffersExtensions.ToArray%2A). Isso não é recomendado em caminhos quentes, `T[]` pois aloca um novo na pilha.

Os exemplos a seguir demonstram alguns casos comuns para processamento: `ReadOnlySequence<byte>`

##### <a name="process-binary-data"></a>Dados binários de processo

O exemplo a seguir analisa um comprimento inteiro de 4 bytes `ReadOnlySequence<byte>`grande-endiano desde o início do .

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet5)]

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

##### <a name="process-text-data"></a>Dados de texto de processo

O exemplo a seguir:

- Encontra a primeira`\r\n`linha nova `ReadOnlySequence<byte>` ( ) no e retorna-a através do parâmetro 'line' out.
- Apara essa linha, `\r\n` excluindo o buffer de entrada.

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet6)]

##### <a name="empty-segments"></a>Segmentos vazios

É válido armazenar segmentos vazios `ReadOnlySequence<T>`dentro de um . Segmentos vazios podem ocorrer enquanto enumeram segmentos explicitamente:

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet7)]

O código anterior `ReadOnlySequence<byte>` cria um com segmentos vazios e mostra como esses segmentos vazios afetam as várias APIs:

- `ReadOnlySequence<T>.Slice`com `SequencePosition` um apontamento para um segmento vazio preserva esse segmento.
- `ReadOnlySequence<T>.Slice`com um int pula sobre os segmentos vazios.
- Enumerar `ReadOnlySequence<T>` os enumera os segmentos vazios.

### <a name="potential-problems-with-readonlysequencet-and-sequenceposition"></a>Problemas potenciais\<com ReadOnlySequence T> e SequencePosition

Existem vários resultados incomuns `ReadOnlySequence<T>` / `SequencePosition` ao lidar `ReadOnlySpan<T>` / `ReadOnlyMemory<T>` / `T[]` / `int`com um versus um normal :

- `SequencePosition`é um marcador de `ReadOnlySequence<T>`posição para uma posição específica, não absoluta. Por ser relativa a `ReadOnlySequence<T>`um específico, não tem significado se `ReadOnlySequence<T>` usado fora do local de origem.
- A aritmética não pode `SequencePosition` ser `ReadOnlySequence<T>`executada sem o . Isso significa fazer `position++` coisas `ReadOnlySequence<T>.GetPosition(position, 1)`básicas como está escrito.
- `GetPosition(long)`**não suporta** índices negativos. Isso significa que é impossível obter o penúltimo personagem sem andar em todos os segmentos.
- Dois `SequencePosition` não podem ser comparados, dificultando:
  - Saiba se uma posição é maior ou menor que outra.
  - Escreva alguns algoritmos de análise.
- `ReadOnlySequence<T>`é maior do que uma referência de objeto e deve ser passado [por](../../csharp/language-reference/keywords/in-parameter-modifier.md) [ou ref,](../../csharp/language-reference/keywords/ref.md) sempre que possível. Passando `ReadOnlySequence<T>` `in` ou `ref` reduz cópias da [estrutura.](../../csharp/language-reference/builtin-types/struct.md)
- Segmentos vazios:
  - São válidos `ReadOnlySequence<T>`dentro de um .
  - Pode aparecer ao iterar usando o `ReadOnlySequence<T>.TryGet` método.
  - Pode aparecer cortando a `ReadOnlySequence<T>.Slice()` seqüência usando o método com `SequencePosition` objetos.

## <a name="sequencereadert"></a>SequenceReader\<T\>

<xref:System.Buffers.SequenceReader%601>:

- É um novo tipo que foi introduzido no .NET Core `ReadOnlySequence<T>`3.0 para simplificar o processamento de um .
- Unifica as diferenças entre `ReadOnlySequence<T>` um único `ReadOnlySequence<T>`segmento e um segmento múltiplo.
- Fornece ajudantes para leitura de`byte` dados `char`binários e de texto (e) que podem ou não ser divididos entre segmentos.

Existem métodos incorporados para lidar com o processamento de dados binários e delimitados. A seção a seguir demonstra como `SequenceReader<T>`esses mesmos métodos se parecem com:

### <a name="access-data"></a>Acessar dados

`SequenceReader<T>`tem métodos para enumerar `ReadOnlySequence<T>` dados dentro do diretamente. O código a seguir é `ReadOnlySequence<byte>` um `byte` exemplo de processamento de a a de cada vez:

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet8)]

O `CurrentSpan` expõe o segmento `Span`atual, que é semelhante ao que foi feito manualmente no método.

### <a name="use-position"></a>Posição de uso

O código a seguir `FindIndexOf` é `SequenceReader<T>`um exemplo de implementação do uso do :

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet9)]

### <a name="process-binary-data"></a>Dados binários de processo

O exemplo a seguir analisa um comprimento inteiro de 4 bytes `ReadOnlySequence<byte>`grande-endiano desde o início do .

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet11)]

### <a name="process-text-data"></a>Dados de texto de processo

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet10)]

### <a name="sequencereadert-common-problems"></a>Sequenclero\> T\<problemas comuns

- Por `SequenceReader<T>` ser uma estrutura mutável, deve ser sempre passada por [referência.](../../csharp/language-reference/keywords/ref.md)
- `SequenceReader<T>`é uma [estrutura ref para](../../csharp/language-reference/builtin-types/struct.md#ref-struct) que ele só possa ser usado em métodos síncronos e não pode ser armazenado em campos. Para obter mais informações, consulte [Escrever código C# seguro e eficiente](../../csharp/write-safe-efficient-code.md).
- `SequenceReader<T>`é otimizado para uso como um leitor somente para frente. `Rewind`destina-se a pequenos backups que não podem `Read` `Peek`ser `IsNext` endereçados utilizando outras , e APIs.
