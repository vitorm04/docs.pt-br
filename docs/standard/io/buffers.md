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
# <a name="work-with-buffers-in-net"></a><span data-ttu-id="1fc23-102">Trabalhe com Buffers em .NET</span><span class="sxs-lookup"><span data-stu-id="1fc23-102">Work with Buffers in .NET</span></span>

<span data-ttu-id="1fc23-103">Este artigo fornece uma visão geral dos tipos que ajudam a ler dados que são executados em vários buffers.</span><span class="sxs-lookup"><span data-stu-id="1fc23-103">This article provides an overview of types that help read data that runs across multiple buffers.</span></span> <span data-ttu-id="1fc23-104">Eles são usados principalmente <xref:System.IO.Pipelines.PipeReader> para apoiar objetos.</span><span class="sxs-lookup"><span data-stu-id="1fc23-104">They're primarily used to support <xref:System.IO.Pipelines.PipeReader> objects.</span></span>

## <a name="ibufferwritert"></a><span data-ttu-id="1fc23-105">IBufferWriter\<T\></span><span class="sxs-lookup"><span data-stu-id="1fc23-105">IBufferWriter\<T\></span></span>

<span data-ttu-id="1fc23-106"><xref:System.Buffers.IBufferWriter%601?displayProperty=fullName>é um contrato para escrita tampão síncrona.</span><span class="sxs-lookup"><span data-stu-id="1fc23-106"><xref:System.Buffers.IBufferWriter%601?displayProperty=fullName> is a contract for synchronous buffered writing.</span></span> <span data-ttu-id="1fc23-107">No nível mais baixo, a interface:</span><span class="sxs-lookup"><span data-stu-id="1fc23-107">At the lowest level, the interface:</span></span>

- <span data-ttu-id="1fc23-108">É básico e não é difícil de usar.</span><span class="sxs-lookup"><span data-stu-id="1fc23-108">Is basic and not difficult to use.</span></span>
- <span data-ttu-id="1fc23-109">Permite acesso <xref:System.Memory%601> a <xref:System.Span%601>um ou .</span><span class="sxs-lookup"><span data-stu-id="1fc23-109">Allows access to a <xref:System.Memory%601> or <xref:System.Span%601>.</span></span> <span data-ttu-id="1fc23-110">O `Memory<T>` `Span<T>` ou pode ser escrito e `T` você pode determinar quantos itens foram escritos.</span><span class="sxs-lookup"><span data-stu-id="1fc23-110">The `Memory<T>` or `Span<T>` can be written to and you can determine how many `T` items were written.</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet)]

<span data-ttu-id="1fc23-111">O método anterior:</span><span class="sxs-lookup"><span data-stu-id="1fc23-111">The preceding method:</span></span>

- <span data-ttu-id="1fc23-112">Solicita um buffer de pelo menos `IBufferWriter<byte>` 5 `GetSpan(5)`bytes do uso .</span><span class="sxs-lookup"><span data-stu-id="1fc23-112">Requests a buffer of at least 5 bytes from the `IBufferWriter<byte>` using `GetSpan(5)`.</span></span>
- <span data-ttu-id="1fc23-113">Escreve bytes para a seqüência ASCII `Span<byte>`"Hello" para o retornado .</span><span class="sxs-lookup"><span data-stu-id="1fc23-113">Writes bytes for the ASCII string "Hello" to the returned `Span<byte>`.</span></span>
- <span data-ttu-id="1fc23-114">Chamadas <xref:System.Buffers.IBufferWriter%601> para indicar quantos bytes foram escritos para o buffer.</span><span class="sxs-lookup"><span data-stu-id="1fc23-114">Calls  <xref:System.Buffers.IBufferWriter%601> to indicate how many bytes were written to the buffer.</span></span>

<span data-ttu-id="1fc23-115">Este método de `Memory<T>` / `Span<T>` escrita usa o `IBufferWriter<T>`buffer fornecido pelo .</span><span class="sxs-lookup"><span data-stu-id="1fc23-115">This method of writing uses the `Memory<T>`/`Span<T>` buffer provided by the `IBufferWriter<T>`.</span></span> <span data-ttu-id="1fc23-116">Alternativamente, <xref:System.Buffers.BuffersExtensions.Write%2A> o método de extensão pode ser `IBufferWriter<T>`usado para copiar um buffer existente para o .</span><span class="sxs-lookup"><span data-stu-id="1fc23-116">Alternatively, the <xref:System.Buffers.BuffersExtensions.Write%2A> extension method can be used to copy an existing buffer to the `IBufferWriter<T>`.</span></span> <span data-ttu-id="1fc23-117">`Write`faz o trabalho `GetSpan` / `Advance` de chamar conforme apropriado, então `Advance` não há necessidade de ligar depois de escrever:</span><span class="sxs-lookup"><span data-stu-id="1fc23-117">`Write` does the work of calling `GetSpan`/`Advance` as appropriate, so there's no need to call `Advance` after writing:</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet2)]

<span data-ttu-id="1fc23-118"><xref:System.Buffers.ArrayBufferWriter%601>é uma `IBufferWriter<T>` implementação de cuja loja de apoio é uma única matriz contígua.</span><span class="sxs-lookup"><span data-stu-id="1fc23-118"><xref:System.Buffers.ArrayBufferWriter%601> is an implementation of `IBufferWriter<T>` whose backing store is a single contiguous array.</span></span>

### <a name="ibufferwriter-common-problems"></a><span data-ttu-id="1fc23-119">IBufferWriter problemas comuns</span><span class="sxs-lookup"><span data-stu-id="1fc23-119">IBufferWriter common problems</span></span>

- <span data-ttu-id="1fc23-120">`GetSpan`e `GetMemory` retornar um buffer com pelo menos a quantidade solicitada de memória.</span><span class="sxs-lookup"><span data-stu-id="1fc23-120">`GetSpan` and `GetMemory` return a buffer with at least the requested amount of memory.</span></span> <span data-ttu-id="1fc23-121">Não assuma tamanhos exatos de buffer.</span><span class="sxs-lookup"><span data-stu-id="1fc23-121">Don't assume exact buffer sizes.</span></span>
- <span data-ttu-id="1fc23-122">Não há garantia de que as chamadas sucessivas retornarão o mesmo buffer ou o buffer do mesmo tamanho.</span><span class="sxs-lookup"><span data-stu-id="1fc23-122">There's no guarantee that successive calls will return the same buffer or the same-sized buffer.</span></span>
- <span data-ttu-id="1fc23-123">Um novo buffer deve ser `Advance` solicitado após a chamada para continuar a escrever mais dados.</span><span class="sxs-lookup"><span data-stu-id="1fc23-123">A new buffer must be requested after calling `Advance` to continue writing more data.</span></span> <span data-ttu-id="1fc23-124">Um buffer adquirido anteriormente não `Advance` pode ser escrito depois de ter sido chamado.</span><span class="sxs-lookup"><span data-stu-id="1fc23-124">A previously acquired buffer cannot be written to after `Advance` has been called.</span></span>

## <a name="readonlysequencet"></a><span data-ttu-id="1fc23-125">ReadOnlySequence\<T\></span><span class="sxs-lookup"><span data-stu-id="1fc23-125">ReadOnlySequence\<T\></span></span>

![ReadOnlySequence mostrando memória no tubo e abaixo dessa posição de seqüência de memória somente leitura](media/buffers/ro-sequence.png)

<span data-ttu-id="1fc23-127"><xref:System.Buffers.ReadOnlySequence%601>é uma estrutura que pode representar uma seqüência contígua ou não contígua de `T`.</span><span class="sxs-lookup"><span data-stu-id="1fc23-127"><xref:System.Buffers.ReadOnlySequence%601> is a struct that can represent a contiguous or noncontiguous sequence of `T`.</span></span> <span data-ttu-id="1fc23-128">Pode ser construído a partir de:</span><span class="sxs-lookup"><span data-stu-id="1fc23-128">It can be constructed from:</span></span>

1. <span data-ttu-id="1fc23-129">Uma `T[]`</span><span class="sxs-lookup"><span data-stu-id="1fc23-129">A `T[]`</span></span>
1. <span data-ttu-id="1fc23-130">Uma `ReadOnlyMemory<T>`</span><span class="sxs-lookup"><span data-stu-id="1fc23-130">A `ReadOnlyMemory<T>`</span></span>
1. <span data-ttu-id="1fc23-131">Um par de nó <xref:System.Buffers.ReadOnlySequenceSegment%601> de lista vinculado e índice para representar a posição inicial e final da seqüência.</span><span class="sxs-lookup"><span data-stu-id="1fc23-131">A pair of linked list node <xref:System.Buffers.ReadOnlySequenceSegment%601> and index to represent the start and end position of the sequence.</span></span>

<span data-ttu-id="1fc23-132">A terceira representação é a mais interessante, pois tem `ReadOnlySequence<T>`implicações de desempenho em várias operações no:</span><span class="sxs-lookup"><span data-stu-id="1fc23-132">The third representation is the most interesting one as it has performance implications on various operations on the `ReadOnlySequence<T>`:</span></span>

|<span data-ttu-id="1fc23-133">Representação</span><span class="sxs-lookup"><span data-stu-id="1fc23-133">Representation</span></span>|<span data-ttu-id="1fc23-134">Operação</span><span class="sxs-lookup"><span data-stu-id="1fc23-134">Operation</span></span>|<span data-ttu-id="1fc23-135">Complexidade</span><span class="sxs-lookup"><span data-stu-id="1fc23-135">Complexity</span></span>|
---|---|---|
|`T[]`/`ReadOnlyMemory<T>`|`Length`|`O(1)`|
|`T[]`/`ReadOnlyMemory<T>`|`GetPosition(long)`|`O(1)`|
|`T[]`/`ReadOnlyMemory<T>`|`Slice(int, int)`|`O(1)`|
|`T[]`/`ReadOnlyMemory<T>`|`Slice(SequencePostion,  SequencePostion)`|`O(1)`|
|`ReadOnlySequenceSegment<T>`|`Length`|`O(1)`|
|`ReadOnlySequenceSegment<T>`|`GetPosition(long)`|`O(number of segments)`|
|`ReadOnlySequenceSegment<T>`|`Slice(int, int)`|`O(number of segments)`|
|`ReadOnlySequenceSegment<T>`|`Slice(SequencePostion, SequencePostion)`|`O(1)`|

<span data-ttu-id="1fc23-136">Por causa dessa representação `ReadOnlySequence<T>` mista, o `SequencePosition` expõe índices como em vez de um inteiro.</span><span class="sxs-lookup"><span data-stu-id="1fc23-136">Because of this mixed representation, the `ReadOnlySequence<T>` exposes indexes as `SequencePosition` instead of an integer.</span></span> <span data-ttu-id="1fc23-137">A: `SequencePosition`</span><span class="sxs-lookup"><span data-stu-id="1fc23-137">A `SequencePosition`:</span></span>

- <span data-ttu-id="1fc23-138">É um valor opaco que representa `ReadOnlySequence<T>` um índice no local de origem.</span><span class="sxs-lookup"><span data-stu-id="1fc23-138">Is an opaque value that represents an index into the `ReadOnlySequence<T>` where it originated.</span></span>
- <span data-ttu-id="1fc23-139">Consiste em duas partes, um inteiro e um objeto.</span><span class="sxs-lookup"><span data-stu-id="1fc23-139">Consists of two parts, an integer and an object.</span></span> <span data-ttu-id="1fc23-140">O que esses dois valores `ReadOnlySequence<T>`representam estão vinculados à implementação de .</span><span class="sxs-lookup"><span data-stu-id="1fc23-140">What these two values represent are tied to the implementation of `ReadOnlySequence<T>`.</span></span>

### <a name="access-data"></a><span data-ttu-id="1fc23-141">Acessar dados</span><span class="sxs-lookup"><span data-stu-id="1fc23-141">Access data</span></span>

<span data-ttu-id="1fc23-142">Os `ReadOnlySequence<T>` dados expõem como um `ReadOnlyMemory<T>`enumerado de .</span><span class="sxs-lookup"><span data-stu-id="1fc23-142">The `ReadOnlySequence<T>` exposes data as an enumerable of `ReadOnlyMemory<T>`.</span></span> <span data-ttu-id="1fc23-143">A enumeração de cada um dos segmentos pode ser feita usando um foreach básico:</span><span class="sxs-lookup"><span data-stu-id="1fc23-143">Enumerating each of the segments can be done using a basic foreach:</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet3)]

<span data-ttu-id="1fc23-144">O método anterior pesquisa cada segmento em busca de um byte específico.</span><span class="sxs-lookup"><span data-stu-id="1fc23-144">The preceding method searches each segment for a specific byte.</span></span> <span data-ttu-id="1fc23-145">Se você precisa acompanhar cada `SequencePosition`segmento, <xref:System.Buffers.ReadOnlySequence%601.TryGet%2A?displayProperty=nameWithType> é mais apropriado.</span><span class="sxs-lookup"><span data-stu-id="1fc23-145">If you need to keep track of each segment's `SequencePosition`, <xref:System.Buffers.ReadOnlySequence%601.TryGet%2A?displayProperty=nameWithType> is more appropriate.</span></span> <span data-ttu-id="1fc23-146">A próxima amostra altera o `SequencePosition` código anterior para retornar um em vez de um inteiro.</span><span class="sxs-lookup"><span data-stu-id="1fc23-146">The next sample changes the preceding code to return a `SequencePosition` instead of an integer.</span></span> <span data-ttu-id="1fc23-147">A devolução de um `SequencePosition` tem o benefício de permitir que o chamador evite uma segunda varredura para obter os dados em um índice específico.</span><span class="sxs-lookup"><span data-stu-id="1fc23-147">Returning a `SequencePosition` has the benefit of allowing the caller to avoid a second scan to get the data at a specific index.</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet4)]

<span data-ttu-id="1fc23-148">A combinação `SequencePosition` `TryGet` e age como um enumerador.</span><span class="sxs-lookup"><span data-stu-id="1fc23-148">The combination of `SequencePosition` and `TryGet` acts like an enumerator.</span></span> <span data-ttu-id="1fc23-149">O campo de posição é modificado no início de cada iteração para ser iniciada de cada segmento dentro do `ReadOnlySequence<T>`.</span><span class="sxs-lookup"><span data-stu-id="1fc23-149">The position field is modified at the start of each iteration to be start of each segment within the `ReadOnlySequence<T>`.</span></span>

<span data-ttu-id="1fc23-150">O método precedente existe como `ReadOnlySequence<T>`um método de extensão em .</span><span class="sxs-lookup"><span data-stu-id="1fc23-150">The preceding method exists as an extension method on `ReadOnlySequence<T>`.</span></span> <span data-ttu-id="1fc23-151"><xref:System.Buffers.BuffersExtensions.PositionOf%2A>pode ser usado para simplificar o código anterior:</span><span class="sxs-lookup"><span data-stu-id="1fc23-151"><xref:System.Buffers.BuffersExtensions.PositionOf%2A> can be used to simplify the preceding code:</span></span>

```csharp
SequencePosition? FindIndexOf(in ReadOnlySequence<byte> buffer, byte data) => buffer.PositionOf(data);
```

#### <a name="process-a-readonlysequencet"></a><span data-ttu-id="1fc23-152">Processe um\<ReadOnlySequence T\></span><span class="sxs-lookup"><span data-stu-id="1fc23-152">Process a ReadOnlySequence\<T\></span></span>

<span data-ttu-id="1fc23-153">O processamento `ReadOnlySequence<T>` de um pode ser desafiador, uma vez que os dados podem ser divididos em vários segmentos dentro da seqüência.</span><span class="sxs-lookup"><span data-stu-id="1fc23-153">Processing a `ReadOnlySequence<T>` can be challenging since data may be split across multiple segments within the sequence.</span></span> <span data-ttu-id="1fc23-154">Para obter o melhor desempenho, divida o código em dois caminhos:</span><span class="sxs-lookup"><span data-stu-id="1fc23-154">For the best performance, split code into two paths:</span></span>

- <span data-ttu-id="1fc23-155">Um caminho rápido que lida com o caso de um único segmento.</span><span class="sxs-lookup"><span data-stu-id="1fc23-155">A fast path that deals with the single segment case.</span></span>
- <span data-ttu-id="1fc23-156">Um caminho lento que lida com os dados divididos entre segmentos.</span><span class="sxs-lookup"><span data-stu-id="1fc23-156">A slow path that deals with the data split across segments.</span></span>

<span data-ttu-id="1fc23-157">Existem algumas abordagens que podem ser usadas para processar dados em seqüências multisegmentadas:</span><span class="sxs-lookup"><span data-stu-id="1fc23-157">There are a few approaches that can be used to process data in multi-segmented sequences:</span></span>

- <span data-ttu-id="1fc23-158">Use [`SequenceReader<T>`](#sequencereadert)o .</span><span class="sxs-lookup"><span data-stu-id="1fc23-158">Use the [`SequenceReader<T>`](#sequencereadert).</span></span>
- <span data-ttu-id="1fc23-159">Analisar os dados segmento por segmento, acompanhando o `SequencePosition` índice dentro do segmento analisado.</span><span class="sxs-lookup"><span data-stu-id="1fc23-159">Parse data segment by segment, keeping track of the `SequencePosition` and index within the segment parsed.</span></span> <span data-ttu-id="1fc23-160">Isso evita alocações desnecessárias, mas pode ser ineficiente, especialmente para pequenos buffers.</span><span class="sxs-lookup"><span data-stu-id="1fc23-160">This avoids unnecessary allocations but may be inefficient, especially for small buffers.</span></span>
- <span data-ttu-id="1fc23-161">Copie `ReadOnlySequence<T>` o para uma matriz contígua e trate-o como um único buffer:</span><span class="sxs-lookup"><span data-stu-id="1fc23-161">Copy the `ReadOnlySequence<T>` to a contiguous array and treat it like a single buffer:</span></span>
  - <span data-ttu-id="1fc23-162">Se o tamanho `ReadOnlySequence<T>` do for pequeno, pode ser razoável copiar os dados em um buffer alocado em pilha usando o operador [stackalloc.](../../csharp/language-reference/operators/stackalloc.md)</span><span class="sxs-lookup"><span data-stu-id="1fc23-162">If the size of the `ReadOnlySequence<T>` is small, it may be reasonable to copy the data into a stack-allocated buffer using the [stackalloc](../../csharp/language-reference/operators/stackalloc.md) operator.</span></span>
  - <span data-ttu-id="1fc23-163">Copie `ReadOnlySequence<T>` o em uma <xref:System.Buffers.ArrayPool%601.Shared%2A?displayProperty=nameWithType>matriz agrupada usando .</span><span class="sxs-lookup"><span data-stu-id="1fc23-163">Copy the `ReadOnlySequence<T>` into a pooled array using <xref:System.Buffers.ArrayPool%601.Shared%2A?displayProperty=nameWithType>.</span></span>
  - <span data-ttu-id="1fc23-164">Use [`ReadOnlySequence<T>.ToArray()`](xref:System.Buffers.BuffersExtensions.ToArray%2A).</span><span class="sxs-lookup"><span data-stu-id="1fc23-164">Use [`ReadOnlySequence<T>.ToArray()`](xref:System.Buffers.BuffersExtensions.ToArray%2A).</span></span> <span data-ttu-id="1fc23-165">Isso não é recomendado em caminhos quentes, `T[]` pois aloca um novo na pilha.</span><span class="sxs-lookup"><span data-stu-id="1fc23-165">This isn't recommended in hot paths as it allocates a new `T[]` on the heap.</span></span>

<span data-ttu-id="1fc23-166">Os exemplos a seguir demonstram alguns casos comuns para processamento: `ReadOnlySequence<byte>`</span><span class="sxs-lookup"><span data-stu-id="1fc23-166">The following examples demonstrate some common cases for processing `ReadOnlySequence<byte>`:</span></span>

##### <a name="process-binary-data"></a><span data-ttu-id="1fc23-167">Dados binários de processo</span><span class="sxs-lookup"><span data-stu-id="1fc23-167">Process binary data</span></span>

<span data-ttu-id="1fc23-168">O exemplo a seguir analisa um comprimento inteiro de 4 bytes `ReadOnlySequence<byte>`grande-endiano desde o início do .</span><span class="sxs-lookup"><span data-stu-id="1fc23-168">The following example parses a 4-byte big-endian integer length from the start of the `ReadOnlySequence<byte>`.</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet5)]

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

##### <a name="process-text-data"></a><span data-ttu-id="1fc23-169">Dados de texto de processo</span><span class="sxs-lookup"><span data-stu-id="1fc23-169">Process text data</span></span>

<span data-ttu-id="1fc23-170">O exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="1fc23-170">The following example:</span></span>

- <span data-ttu-id="1fc23-171">Encontra a primeira`\r\n`linha nova `ReadOnlySequence<byte>` ( ) no e retorna-a através do parâmetro 'line' out.</span><span class="sxs-lookup"><span data-stu-id="1fc23-171">Finds the first newline (`\r\n`) in the `ReadOnlySequence<byte>` and returns it via the out 'line' parameter.</span></span>
- <span data-ttu-id="1fc23-172">Apara essa linha, `\r\n` excluindo o buffer de entrada.</span><span class="sxs-lookup"><span data-stu-id="1fc23-172">Trims that line, excluding the `\r\n` from the input buffer.</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet6)]

##### <a name="empty-segments"></a><span data-ttu-id="1fc23-173">Segmentos vazios</span><span class="sxs-lookup"><span data-stu-id="1fc23-173">Empty segments</span></span>

<span data-ttu-id="1fc23-174">É válido armazenar segmentos vazios `ReadOnlySequence<T>`dentro de um .</span><span class="sxs-lookup"><span data-stu-id="1fc23-174">It's valid to store empty segments inside of a `ReadOnlySequence<T>`.</span></span> <span data-ttu-id="1fc23-175">Segmentos vazios podem ocorrer enquanto enumeram segmentos explicitamente:</span><span class="sxs-lookup"><span data-stu-id="1fc23-175">Empty segments may occur while enumerating segments explicitly:</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet7)]

<span data-ttu-id="1fc23-176">O código anterior `ReadOnlySequence<byte>` cria um com segmentos vazios e mostra como esses segmentos vazios afetam as várias APIs:</span><span class="sxs-lookup"><span data-stu-id="1fc23-176">The preceding code creates a `ReadOnlySequence<byte>` with empty segments and shows how those empty segments affect the various APIs:</span></span>

- <span data-ttu-id="1fc23-177">`ReadOnlySequence<T>.Slice`com `SequencePosition` um apontamento para um segmento vazio preserva esse segmento.</span><span class="sxs-lookup"><span data-stu-id="1fc23-177">`ReadOnlySequence<T>.Slice` with a `SequencePosition` pointing to an empty segment preserves that segment.</span></span>
- <span data-ttu-id="1fc23-178">`ReadOnlySequence<T>.Slice`com um int pula sobre os segmentos vazios.</span><span class="sxs-lookup"><span data-stu-id="1fc23-178">`ReadOnlySequence<T>.Slice` with an int skips over the empty segments.</span></span>
- <span data-ttu-id="1fc23-179">Enumerar `ReadOnlySequence<T>` os enumera os segmentos vazios.</span><span class="sxs-lookup"><span data-stu-id="1fc23-179">Enumerating the `ReadOnlySequence<T>` enumerates the empty segments.</span></span>

### <a name="potential-problems-with-readonlysequencet-and-sequenceposition"></a><span data-ttu-id="1fc23-180">Problemas potenciais\<com ReadOnlySequence T> e SequencePosition</span><span class="sxs-lookup"><span data-stu-id="1fc23-180">Potential problems with ReadOnlySequence\<T> and SequencePosition</span></span>

<span data-ttu-id="1fc23-181">Existem vários resultados incomuns `ReadOnlySequence<T>` / `SequencePosition` ao lidar `ReadOnlySpan<T>` / `ReadOnlyMemory<T>` / `T[]` / `int`com um versus um normal :</span><span class="sxs-lookup"><span data-stu-id="1fc23-181">There are several unusual outcomes when dealing with a `ReadOnlySequence<T>`/`SequencePosition` vs. a normal `ReadOnlySpan<T>`/`ReadOnlyMemory<T>`/`T[]`/`int`:</span></span>

- <span data-ttu-id="1fc23-182">`SequencePosition`é um marcador de `ReadOnlySequence<T>`posição para uma posição específica, não absoluta.</span><span class="sxs-lookup"><span data-stu-id="1fc23-182">`SequencePosition` is a position marker for a specific `ReadOnlySequence<T>`, not an absolute position.</span></span> <span data-ttu-id="1fc23-183">Por ser relativa a `ReadOnlySequence<T>`um específico, não tem significado se `ReadOnlySequence<T>` usado fora do local de origem.</span><span class="sxs-lookup"><span data-stu-id="1fc23-183">Because it's relative to a specific `ReadOnlySequence<T>`, it doesn't have meaning if used outside of the `ReadOnlySequence<T>` where it originated.</span></span>
- <span data-ttu-id="1fc23-184">A aritmética não pode `SequencePosition` ser `ReadOnlySequence<T>`executada sem o .</span><span class="sxs-lookup"><span data-stu-id="1fc23-184">Arithmetic can't be performed on `SequencePosition` without the `ReadOnlySequence<T>`.</span></span> <span data-ttu-id="1fc23-185">Isso significa fazer `position++` coisas `ReadOnlySequence<T>.GetPosition(position, 1)`básicas como está escrito.</span><span class="sxs-lookup"><span data-stu-id="1fc23-185">That means doing basic things like `position++` is written `ReadOnlySequence<T>.GetPosition(position, 1)`.</span></span>
- <span data-ttu-id="1fc23-186">`GetPosition(long)`**não suporta** índices negativos.</span><span class="sxs-lookup"><span data-stu-id="1fc23-186">`GetPosition(long)` does **not** support negative indexes.</span></span> <span data-ttu-id="1fc23-187">Isso significa que é impossível obter o penúltimo personagem sem andar em todos os segmentos.</span><span class="sxs-lookup"><span data-stu-id="1fc23-187">That means it's impossible to get the second to last character without walking all segments.</span></span>
- <span data-ttu-id="1fc23-188">Dois `SequencePosition` não podem ser comparados, dificultando:</span><span class="sxs-lookup"><span data-stu-id="1fc23-188">Two `SequencePosition` can't be compared, making it difficult to:</span></span>
  - <span data-ttu-id="1fc23-189">Saiba se uma posição é maior ou menor que outra.</span><span class="sxs-lookup"><span data-stu-id="1fc23-189">Know if one position is greater than or less than another position.</span></span>
  - <span data-ttu-id="1fc23-190">Escreva alguns algoritmos de análise.</span><span class="sxs-lookup"><span data-stu-id="1fc23-190">Write some parsing algorithms.</span></span>
- <span data-ttu-id="1fc23-191">`ReadOnlySequence<T>`é maior do que uma referência de objeto e deve ser passado [por](../../csharp/language-reference/keywords/in-parameter-modifier.md) [ou ref,](../../csharp/language-reference/keywords/ref.md) sempre que possível.</span><span class="sxs-lookup"><span data-stu-id="1fc23-191">`ReadOnlySequence<T>` is bigger than an object reference and should be passed by [in](../../csharp/language-reference/keywords/in-parameter-modifier.md) or [ref](../../csharp/language-reference/keywords/ref.md) where possible.</span></span> <span data-ttu-id="1fc23-192">Passando `ReadOnlySequence<T>` `in` ou `ref` reduz cópias da [estrutura.](../../csharp/language-reference/builtin-types/struct.md)</span><span class="sxs-lookup"><span data-stu-id="1fc23-192">Passing `ReadOnlySequence<T>` by `in` or `ref` reduces copies of the [struct](../../csharp/language-reference/builtin-types/struct.md).</span></span>
- <span data-ttu-id="1fc23-193">Segmentos vazios:</span><span class="sxs-lookup"><span data-stu-id="1fc23-193">Empty segments:</span></span>
  - <span data-ttu-id="1fc23-194">São válidos `ReadOnlySequence<T>`dentro de um .</span><span class="sxs-lookup"><span data-stu-id="1fc23-194">Are valid within a `ReadOnlySequence<T>`.</span></span>
  - <span data-ttu-id="1fc23-195">Pode aparecer ao iterar usando o `ReadOnlySequence<T>.TryGet` método.</span><span class="sxs-lookup"><span data-stu-id="1fc23-195">Can appear when iterating using the `ReadOnlySequence<T>.TryGet` method.</span></span>
  - <span data-ttu-id="1fc23-196">Pode aparecer cortando a `ReadOnlySequence<T>.Slice()` seqüência usando o método com `SequencePosition` objetos.</span><span class="sxs-lookup"><span data-stu-id="1fc23-196">Can appear slicing the sequence using the `ReadOnlySequence<T>.Slice()` method with `SequencePosition` objects.</span></span>

## <a name="sequencereadert"></a><span data-ttu-id="1fc23-197">SequenceReader\<T\></span><span class="sxs-lookup"><span data-stu-id="1fc23-197">SequenceReader\<T\></span></span>

<span data-ttu-id="1fc23-198"><xref:System.Buffers.SequenceReader%601>:</span><span class="sxs-lookup"><span data-stu-id="1fc23-198"><xref:System.Buffers.SequenceReader%601>:</span></span>

- <span data-ttu-id="1fc23-199">É um novo tipo que foi introduzido no .NET Core `ReadOnlySequence<T>`3.0 para simplificar o processamento de um .</span><span class="sxs-lookup"><span data-stu-id="1fc23-199">Is a new type that was introduced in .NET Core 3.0 to simplify the processing of a `ReadOnlySequence<T>`.</span></span>
- <span data-ttu-id="1fc23-200">Unifica as diferenças entre `ReadOnlySequence<T>` um único `ReadOnlySequence<T>`segmento e um segmento múltiplo.</span><span class="sxs-lookup"><span data-stu-id="1fc23-200">Unifies the differences between a single segment `ReadOnlySequence<T>` and multi-segment `ReadOnlySequence<T>`.</span></span>
- <span data-ttu-id="1fc23-201">Fornece ajudantes para leitura de`byte` dados `char`binários e de texto (e) que podem ou não ser divididos entre segmentos.</span><span class="sxs-lookup"><span data-stu-id="1fc23-201">Provides helpers for reading binary and text data (`byte` and `char`) that may or may not be split across segments.</span></span>

<span data-ttu-id="1fc23-202">Existem métodos incorporados para lidar com o processamento de dados binários e delimitados.</span><span class="sxs-lookup"><span data-stu-id="1fc23-202">There are built-in methods for dealing with processing both binary and delimited data.</span></span> <span data-ttu-id="1fc23-203">A seção a seguir demonstra como `SequenceReader<T>`esses mesmos métodos se parecem com:</span><span class="sxs-lookup"><span data-stu-id="1fc23-203">The following section demonstrates what those same methods look like with the `SequenceReader<T>`:</span></span>

### <a name="access-data"></a><span data-ttu-id="1fc23-204">Acessar dados</span><span class="sxs-lookup"><span data-stu-id="1fc23-204">Access data</span></span>

<span data-ttu-id="1fc23-205">`SequenceReader<T>`tem métodos para enumerar `ReadOnlySequence<T>` dados dentro do diretamente.</span><span class="sxs-lookup"><span data-stu-id="1fc23-205">`SequenceReader<T>` has methods for enumerating data inside of the `ReadOnlySequence<T>` directly.</span></span> <span data-ttu-id="1fc23-206">O código a seguir é `ReadOnlySequence<byte>` um `byte` exemplo de processamento de a a de cada vez:</span><span class="sxs-lookup"><span data-stu-id="1fc23-206">The following code is an example of processing a `ReadOnlySequence<byte>` a `byte` at a time:</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet8)]

<span data-ttu-id="1fc23-207">O `CurrentSpan` expõe o segmento `Span`atual, que é semelhante ao que foi feito manualmente no método.</span><span class="sxs-lookup"><span data-stu-id="1fc23-207">The `CurrentSpan` exposes the current segment's `Span`, which is similar to what was done in the method manually.</span></span>

### <a name="use-position"></a><span data-ttu-id="1fc23-208">Posição de uso</span><span class="sxs-lookup"><span data-stu-id="1fc23-208">Use position</span></span>

<span data-ttu-id="1fc23-209">O código a seguir `FindIndexOf` é `SequenceReader<T>`um exemplo de implementação do uso do :</span><span class="sxs-lookup"><span data-stu-id="1fc23-209">The following code is an example implementation of `FindIndexOf` using the `SequenceReader<T>`:</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet9)]

### <a name="process-binary-data"></a><span data-ttu-id="1fc23-210">Dados binários de processo</span><span class="sxs-lookup"><span data-stu-id="1fc23-210">Process binary data</span></span>

<span data-ttu-id="1fc23-211">O exemplo a seguir analisa um comprimento inteiro de 4 bytes `ReadOnlySequence<byte>`grande-endiano desde o início do .</span><span class="sxs-lookup"><span data-stu-id="1fc23-211">The following example parses a 4-byte big-endian integer length from the start of the `ReadOnlySequence<byte>`.</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet11)]

### <a name="process-text-data"></a><span data-ttu-id="1fc23-212">Dados de texto de processo</span><span class="sxs-lookup"><span data-stu-id="1fc23-212">Process text data</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet10)]

### <a name="sequencereadert-common-problems"></a><span data-ttu-id="1fc23-213">Sequenclero\> T\<problemas comuns</span><span class="sxs-lookup"><span data-stu-id="1fc23-213">SequenceReader\<T\> common problems</span></span>

- <span data-ttu-id="1fc23-214">Por `SequenceReader<T>` ser uma estrutura mutável, deve ser sempre passada por [referência.](../../csharp/language-reference/keywords/ref.md)</span><span class="sxs-lookup"><span data-stu-id="1fc23-214">Because `SequenceReader<T>` is a mutable struct, it should always be passed by [reference](../../csharp/language-reference/keywords/ref.md).</span></span>
- <span data-ttu-id="1fc23-215">`SequenceReader<T>`é uma [estrutura ref para](../../csharp/language-reference/builtin-types/struct.md#ref-struct) que ele só possa ser usado em métodos síncronos e não pode ser armazenado em campos.</span><span class="sxs-lookup"><span data-stu-id="1fc23-215">`SequenceReader<T>` is a [ref struct](../../csharp/language-reference/builtin-types/struct.md#ref-struct) so it can only be used in synchronous methods and can't be stored in fields.</span></span> <span data-ttu-id="1fc23-216">Para obter mais informações, consulte [Escrever código C# seguro e eficiente](../../csharp/write-safe-efficient-code.md).</span><span class="sxs-lookup"><span data-stu-id="1fc23-216">For more information, see [Write safe and efficient C# code](../../csharp/write-safe-efficient-code.md).</span></span>
- <span data-ttu-id="1fc23-217">`SequenceReader<T>`é otimizado para uso como um leitor somente para frente.</span><span class="sxs-lookup"><span data-stu-id="1fc23-217">`SequenceReader<T>` is optimized for use as a forward-only reader.</span></span> <span data-ttu-id="1fc23-218">`Rewind`destina-se a pequenos backups que não podem `Read` `Peek`ser `IsNext` endereçados utilizando outras , e APIs.</span><span class="sxs-lookup"><span data-stu-id="1fc23-218">`Rewind` is intended for small backups that can't be addressed utilizing other `Read`, `Peek`, and `IsNext` APIs.</span></span>
