---
title: System. buffers-.NET
ms.date: 12/05/2019
ms.technology: dotnet-standard
helpviewer_keywords:
- buffers [.NET]
- I/O [.NET], buffers
author: rick-anderson
ms.author: riande
ms.openlocfilehash: e42f165bfedec3b1fa54615ee7e2a2028f40aadb
ms.sourcegitcommit: 42ed59871db1f29a32b3d8e7abeb20e6eceeda7c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74960491"
---
# <a name="work-with-buffers-in-net"></a><span data-ttu-id="21d51-102">Trabalhar com buffers no .NET</span><span class="sxs-lookup"><span data-stu-id="21d51-102">Work with Buffers in .NET</span></span>

<span data-ttu-id="21d51-103">Este artigo fornece uma visão geral dos tipos que ajudam a ler dados que são executados em vários buffers.</span><span class="sxs-lookup"><span data-stu-id="21d51-103">This article provides an overview of types that help read data that runs across multiple buffers.</span></span> <span data-ttu-id="21d51-104">Eles são usados principalmente para dar suporte a objetos <xref:System.IO.Pipelines.PipeReader>.</span><span class="sxs-lookup"><span data-stu-id="21d51-104">They're primarily used to support <xref:System.IO.Pipelines.PipeReader> objects.</span></span>

## <a name="ibufferwritert"></a><span data-ttu-id="21d51-105">IBufferWriter\<T\></span><span class="sxs-lookup"><span data-stu-id="21d51-105">IBufferWriter\<T\></span></span>

<span data-ttu-id="21d51-106"><xref:System.Buffers.IBufferWriter%601?displayProperty=fullName> é um contrato de gravação síncrona em buffer.</span><span class="sxs-lookup"><span data-stu-id="21d51-106"><xref:System.Buffers.IBufferWriter%601?displayProperty=fullName> is a contract for synchronous buffered writing.</span></span> <span data-ttu-id="21d51-107">No nível mais baixo, a interface:</span><span class="sxs-lookup"><span data-stu-id="21d51-107">At the lowest level, the interface:</span></span>

- <span data-ttu-id="21d51-108">É básico e não difícil de usar.</span><span class="sxs-lookup"><span data-stu-id="21d51-108">Is basic and not difficult to use.</span></span>
- <span data-ttu-id="21d51-109">Permite o acesso a um <xref:System.Memory%601> ou <xref:System.Span%601>.</span><span class="sxs-lookup"><span data-stu-id="21d51-109">Allows access to a <xref:System.Memory%601> or <xref:System.Span%601>.</span></span> <span data-ttu-id="21d51-110">O `Memory<T>` ou `Span<T>` pode ser gravado e você pode determinar quantos itens de `T` foram gravados.</span><span class="sxs-lookup"><span data-stu-id="21d51-110">The `Memory<T>` or `Span<T>` can be written to and you can determine how many `T` items were written.</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet)]

<span data-ttu-id="21d51-111">O método anterior:</span><span class="sxs-lookup"><span data-stu-id="21d51-111">The preceding method:</span></span>

- <span data-ttu-id="21d51-112">Solicita um buffer de pelo menos 5 bytes do `IBufferWriter<byte>` usando `GetSpan(5)`.</span><span class="sxs-lookup"><span data-stu-id="21d51-112">Requests a buffer of at least 5 bytes from the `IBufferWriter<byte>` using `GetSpan(5)`.</span></span>
- <span data-ttu-id="21d51-113">Grava bytes para a cadeia de caracteres ASCII "Olá" para o `Span<byte>`retornado.</span><span class="sxs-lookup"><span data-stu-id="21d51-113">Writes bytes for the ASCII string "Hello" to the returned `Span<byte>`.</span></span>
- <span data-ttu-id="21d51-114">Chama <xref:System.Buffers.IBufferWriter%601> para indicar quantos bytes foram gravados no buffer.</span><span class="sxs-lookup"><span data-stu-id="21d51-114">Calls  <xref:System.Buffers.IBufferWriter%601> to indicate how many bytes were written to the buffer.</span></span>

<span data-ttu-id="21d51-115">Esse método de gravação usa o `Memory<T>`/buffer `Span<T>` fornecido pelo `IBufferWriter<T>`.</span><span class="sxs-lookup"><span data-stu-id="21d51-115">This method of writing uses the `Memory<T>`/`Span<T>` buffer provided by the `IBufferWriter<T>`.</span></span> <span data-ttu-id="21d51-116">Como alternativa, o método de extensão <xref:System.Buffers.BuffersExtensions.Write%2A> pode ser usado para copiar um buffer existente para o `IBufferWriter<T>`.</span><span class="sxs-lookup"><span data-stu-id="21d51-116">Alternatively, the <xref:System.Buffers.BuffersExtensions.Write%2A> extension method can be used to copy an existing buffer to the `IBufferWriter<T>`.</span></span> <span data-ttu-id="21d51-117">`Write` faz o trabalho de chamar `GetSpan`/`Advance` conforme apropriado, portanto, não há necessidade de chamar `Advance` após escrever:</span><span class="sxs-lookup"><span data-stu-id="21d51-117">`Write` does the work of calling `GetSpan`/`Advance` as appropriate, so there's no need to call `Advance` after writing:</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet2)]

<span data-ttu-id="21d51-118"><xref:System.Buffers.ArrayBufferWriter%601> é uma implementação de `IBufferWriter<T>` cujo armazenamento de backup é uma única matriz contígua.</span><span class="sxs-lookup"><span data-stu-id="21d51-118"><xref:System.Buffers.ArrayBufferWriter%601> is an implementation of `IBufferWriter<T>` whose backing store is a single contiguous array.</span></span>

### <a name="ibufferwriter-common-problems"></a><span data-ttu-id="21d51-119">Problemas comuns do IBufferWriter</span><span class="sxs-lookup"><span data-stu-id="21d51-119">IBufferWriter common problems</span></span>

- <span data-ttu-id="21d51-120">`GetSpan` e `GetMemory` retornam um buffer com pelo menos a quantidade solicitada de memória.</span><span class="sxs-lookup"><span data-stu-id="21d51-120">`GetSpan` and `GetMemory` return a buffer with at least the requested amount of memory.</span></span> <span data-ttu-id="21d51-121">Não presuma os tamanhos de buffer exatos.</span><span class="sxs-lookup"><span data-stu-id="21d51-121">Don't assume exact buffer sizes.</span></span>
- <span data-ttu-id="21d51-122">Não há nenhuma garantia de que as chamadas sucessivas retornarão o mesmo buffer ou o buffer de mesmo tamanho.</span><span class="sxs-lookup"><span data-stu-id="21d51-122">There's no guarantee that successive calls will return the same buffer or the same-sized buffer.</span></span>
- <span data-ttu-id="21d51-123">Um novo buffer deve ser solicitado depois de chamar `Advance` para continuar gravando mais dados.</span><span class="sxs-lookup"><span data-stu-id="21d51-123">A new buffer must be requested after calling `Advance` to continue writing more data.</span></span> <span data-ttu-id="21d51-124">Um buffer adquirido anteriormente não pode ser gravado depois que `Advance` foi chamado.</span><span class="sxs-lookup"><span data-stu-id="21d51-124">A previously acquired buffer cannot be written to after `Advance` has been called.</span></span>

## <a name="readonlysequencet"></a><span data-ttu-id="21d51-125">ReadOnlySequence\<T\></span><span class="sxs-lookup"><span data-stu-id="21d51-125">ReadOnlySequence\<T\></span></span>

![ReadOnlySequence mostrando a memória no pipe e abaixo da posição da sequência de memória somente leitura](media/buffers/ro-sequence.png)

<span data-ttu-id="21d51-127"><xref:System.Buffers.ReadOnlySequence%601> é uma struct que pode representar uma sequência contígua ou não contígua de `T`.</span><span class="sxs-lookup"><span data-stu-id="21d51-127"><xref:System.Buffers.ReadOnlySequence%601> is a struct that can represent a contiguous or noncontiguous sequence of `T`.</span></span> <span data-ttu-id="21d51-128">Ele pode ser construído a partir de:</span><span class="sxs-lookup"><span data-stu-id="21d51-128">It can be constructed from:</span></span>

1. <span data-ttu-id="21d51-129">Um `T[]`</span><span class="sxs-lookup"><span data-stu-id="21d51-129">A `T[]`</span></span>
1. <span data-ttu-id="21d51-130">Um `ReadOnlyMemory<T>`</span><span class="sxs-lookup"><span data-stu-id="21d51-130">A `ReadOnlyMemory<T>`</span></span>
1. <span data-ttu-id="21d51-131">Um par de <xref:System.Buffers.ReadOnlySequenceSegment%601> de nó de lista vinculada e índice para representar a posição inicial e final da sequência.</span><span class="sxs-lookup"><span data-stu-id="21d51-131">A pair of linked list node <xref:System.Buffers.ReadOnlySequenceSegment%601> and index to represent the start and end position of the sequence.</span></span>

<span data-ttu-id="21d51-132">A terceira representação é a mais interessante, uma vez que tem implicações de desempenho em várias operações no `ReadOnlySequence<T>`:</span><span class="sxs-lookup"><span data-stu-id="21d51-132">The third representation is the most interesting one as it has performance implications on various operations on the `ReadOnlySequence<T>`:</span></span>

|<span data-ttu-id="21d51-133">Representação</span><span class="sxs-lookup"><span data-stu-id="21d51-133">Representation</span></span>|<span data-ttu-id="21d51-134">Operação</span><span class="sxs-lookup"><span data-stu-id="21d51-134">Operation</span></span>|<span data-ttu-id="21d51-135">Complexidade</span><span class="sxs-lookup"><span data-stu-id="21d51-135">Complexity</span></span>|
---|---|---|
|`T[]`/`ReadOnlyMemory<T>`|`Length`|`O(1)`|
|`T[]`/`ReadOnlyMemory<T>`|`GetPosition(long)`|`O(1)`|
|`T[]`/`ReadOnlyMemory<T>`|`Slice(int, int)`|`O(1)`|
|`T[]`/`ReadOnlyMemory<T>`|`Slice(SequencePostion,  SequencePostion)`|`O(1)`|
|`ReadOnlySequenceSegment<T>`|`Length`|`O(1)`|
|`ReadOnlySequenceSegment<T>`|`GetPosition(long)`|`O(number of segments)`|
|`ReadOnlySequenceSegment<T>`|`Slice(int, int)`|`O(number of segments)`|
|`ReadOnlySequenceSegment<T>`|`Slice(SequencePostion, SequencePostion)`|`O(1)`|

<span data-ttu-id="21d51-136">Devido a essa representação mista, o `ReadOnlySequence<T>` expõe índices como `SequencePosition` em vez de um inteiro.</span><span class="sxs-lookup"><span data-stu-id="21d51-136">Because of this mixed representation, the `ReadOnlySequence<T>` exposes indexes as `SequencePosition` instead of an integer.</span></span> <span data-ttu-id="21d51-137">Um `SequencePosition`:</span><span class="sxs-lookup"><span data-stu-id="21d51-137">A `SequencePosition`:</span></span>

- <span data-ttu-id="21d51-138">É um valor opaco que representa um índice no `ReadOnlySequence<T>` onde ele foi originado.</span><span class="sxs-lookup"><span data-stu-id="21d51-138">Is an opaque value that represents an index into the `ReadOnlySequence<T>` where it originated.</span></span>
- <span data-ttu-id="21d51-139">Consiste em duas partes, um inteiro e um objeto.</span><span class="sxs-lookup"><span data-stu-id="21d51-139">Consists of two parts, an integer and an object.</span></span> <span data-ttu-id="21d51-140">O que esses dois valores representam são vinculados à implementação de `ReadOnlySequence<T>`.</span><span class="sxs-lookup"><span data-stu-id="21d51-140">What these two values represent are tied to the implementation of `ReadOnlySequence<T>`.</span></span>

### <a name="access-data"></a><span data-ttu-id="21d51-141">Acessar dados</span><span class="sxs-lookup"><span data-stu-id="21d51-141">Access data</span></span>

<span data-ttu-id="21d51-142">O `ReadOnlySequence<T>` expõe dados como um enumerável de `ReadOnlyMemory<T>`.</span><span class="sxs-lookup"><span data-stu-id="21d51-142">The `ReadOnlySequence<T>` exposes data as an enumerable of `ReadOnlyMemory<T>`.</span></span> <span data-ttu-id="21d51-143">A enumeração de cada um dos segmentos pode ser feita usando um foreach básico:</span><span class="sxs-lookup"><span data-stu-id="21d51-143">Enumerating each of the segments can be done using a basic foreach:</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet3)]

<span data-ttu-id="21d51-144">O método anterior pesquisa cada segmento em busca de um byte específico.</span><span class="sxs-lookup"><span data-stu-id="21d51-144">The preceding method searches each segment for a specific byte.</span></span> <span data-ttu-id="21d51-145">Se você precisar controlar a `SequencePosition`de cada segmento, <xref:System.Buffers.ReadOnlySequence%601.TryGet%2A?displayProperty=nameWithType> será mais apropriado.</span><span class="sxs-lookup"><span data-stu-id="21d51-145">If you need to keep track of each segment's `SequencePosition`, <xref:System.Buffers.ReadOnlySequence%601.TryGet%2A?displayProperty=nameWithType> is more appropriate.</span></span> <span data-ttu-id="21d51-146">O exemplo a seguir altera o código anterior para retornar um `SequencePosition` em vez de um inteiro.</span><span class="sxs-lookup"><span data-stu-id="21d51-146">The next sample changes the preceding code to return a `SequencePosition` instead of an integer.</span></span> <span data-ttu-id="21d51-147">Retornar um `SequencePosition` tem a vantagem de permitir que o chamador Evite uma segunda verificação para obter os dados em um índice específico.</span><span class="sxs-lookup"><span data-stu-id="21d51-147">Returning a `SequencePosition` has the benefit of allowing the caller to avoid a second scan to get the data at a specific index.</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet4)]

<span data-ttu-id="21d51-148">A combinação de `SequencePosition` e `TryGet` atua como um enumerador.</span><span class="sxs-lookup"><span data-stu-id="21d51-148">The combination of `SequencePosition` and `TryGet` acts like an enumerator.</span></span> <span data-ttu-id="21d51-149">O campo posição é modificado no início de cada iteração para ser iniciado de cada segmento dentro do `ReadOnlySequence<T>`.</span><span class="sxs-lookup"><span data-stu-id="21d51-149">The position field is modified at the start of each iteration to be start of each segment within the `ReadOnlySequence<T>`.</span></span>

<span data-ttu-id="21d51-150">O método anterior existe como um método de extensão em `ReadOnlySequence<T>`.</span><span class="sxs-lookup"><span data-stu-id="21d51-150">The preceding method exists as an extension method on `ReadOnlySequence<T>`.</span></span> <span data-ttu-id="21d51-151"><xref:System.Buffers.BuffersExtensions.PositionOf%2A> pode ser usado para simplificar o código anterior:</span><span class="sxs-lookup"><span data-stu-id="21d51-151"><xref:System.Buffers.BuffersExtensions.PositionOf%2A> can be used to simplify the preceding code:</span></span>

```csharp
SequencePosition? FindIndexOf(in ReadOnlySequence<byte> buffer, byte data) => buffer.PositionOf(data);
```

#### <a name="process-a-readonlysequencet"></a><span data-ttu-id="21d51-152">Processar um ReadOnlySequence\<T\></span><span class="sxs-lookup"><span data-stu-id="21d51-152">Process a ReadOnlySequence\<T\></span></span>

<span data-ttu-id="21d51-153">O processamento de um `ReadOnlySequence<T>` pode ser desafiador, pois os dados podem ser divididos em vários segmentos dentro da sequência.</span><span class="sxs-lookup"><span data-stu-id="21d51-153">Processing a `ReadOnlySequence<T>` can be challenging since data may be split across multiple segments within the sequence.</span></span> <span data-ttu-id="21d51-154">Para obter o melhor desempenho, divida o código em dois caminhos:</span><span class="sxs-lookup"><span data-stu-id="21d51-154">For the best performance, split code into two paths:</span></span>

- <span data-ttu-id="21d51-155">Um caminho rápido que lida com o caso de segmento único.</span><span class="sxs-lookup"><span data-stu-id="21d51-155">A fast path that deals with the single segment case.</span></span>
- <span data-ttu-id="21d51-156">Um caminho lento que lida com os dados divididos entre segmentos.</span><span class="sxs-lookup"><span data-stu-id="21d51-156">A slow path that deals with the data split across segments.</span></span>

<span data-ttu-id="21d51-157">Há algumas abordagens que podem ser usadas para processar dados em sequências com vários segmentos:</span><span class="sxs-lookup"><span data-stu-id="21d51-157">There are a few approaches that can be used to process data in multi-segmented sequences:</span></span>

- <span data-ttu-id="21d51-158">Use o [`SequenceReader<T>`](#sequencereadert).</span><span class="sxs-lookup"><span data-stu-id="21d51-158">Use the [`SequenceReader<T>`](#sequencereadert).</span></span>
- <span data-ttu-id="21d51-159">Analisar o segmento de dados por segmento, controlando o `SequencePosition` e o índice dentro do segmento analisado.</span><span class="sxs-lookup"><span data-stu-id="21d51-159">Parse data segment by segment, keeping track of the `SequencePosition` and index within the segment parsed.</span></span> <span data-ttu-id="21d51-160">Isso evita as alocações desnecessárias, mas pode ser ineficiente, especialmente para buffers pequenos.</span><span class="sxs-lookup"><span data-stu-id="21d51-160">This avoids unnecessary allocations but may be inefficient, especially for small buffers.</span></span>
- <span data-ttu-id="21d51-161">Copie o `ReadOnlySequence<T>` para uma matriz contígua e trate-o como um único buffer:</span><span class="sxs-lookup"><span data-stu-id="21d51-161">Copy the `ReadOnlySequence<T>` to a contiguous array and treat it like a single buffer:</span></span>
  - <span data-ttu-id="21d51-162">Se o tamanho da `ReadOnlySequence<T>` for pequeno, talvez seja razoável copiar os dados em um buffer alocado de pilha usando o operador [stackalloc](../../csharp/language-reference/operators/stackalloc.md) .</span><span class="sxs-lookup"><span data-stu-id="21d51-162">If the size of the `ReadOnlySequence<T>` is small, it may be reasonable to copy the data into a stack-allocated buffer using the [stackalloc](../../csharp/language-reference/operators/stackalloc.md) operator.</span></span>
  - <span data-ttu-id="21d51-163">Copie o `ReadOnlySequence<T>` em uma matriz em pool usando <xref:System.Buffers.ArrayPool%601.Shared%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="21d51-163">Copy the `ReadOnlySequence<T>` into a pooled array using <xref:System.Buffers.ArrayPool%601.Shared%2A?displayProperty=nameWithType>.</span></span>
  - <span data-ttu-id="21d51-164">Use [`ReadOnlySequence<T>.ToArray()`](xref:System.Buffers.BuffersExtensions.ToArray%2A).</span><span class="sxs-lookup"><span data-stu-id="21d51-164">Use [`ReadOnlySequence<T>.ToArray()`](xref:System.Buffers.BuffersExtensions.ToArray%2A).</span></span> <span data-ttu-id="21d51-165">Isso não é recomendado em caminhos ativos, pois aloca um novo `T[]` no heap.</span><span class="sxs-lookup"><span data-stu-id="21d51-165">This isn't recommended in hot paths as it allocates a new `T[]` on the heap.</span></span>

<span data-ttu-id="21d51-166">Os exemplos a seguir demonstram alguns casos comuns de processamento `ReadOnlySequence<byte>`:</span><span class="sxs-lookup"><span data-stu-id="21d51-166">The following examples demonstrate some common cases for processing `ReadOnlySequence<byte>`:</span></span>

##### <a name="process-binary-data"></a><span data-ttu-id="21d51-167">Processar dados binários</span><span class="sxs-lookup"><span data-stu-id="21d51-167">Process binary data</span></span>

<span data-ttu-id="21d51-168">O exemplo a seguir analisa um tamanho inteiro big-endian de 4 bytes desde o início do `ReadOnlySequence<byte>`.</span><span class="sxs-lookup"><span data-stu-id="21d51-168">The following example parses a 4-byte big-endian integer length from the start of the `ReadOnlySequence<byte>`.</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet5)]

##### <a name="process-text-data"></a><span data-ttu-id="21d51-169">Processar dados de texto</span><span class="sxs-lookup"><span data-stu-id="21d51-169">Process text data</span></span>

<span data-ttu-id="21d51-170">O exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="21d51-170">The following example:</span></span>

- <span data-ttu-id="21d51-171">Localiza a primeira nova linha (`\r\n`) na `ReadOnlySequence<byte>` e a retorna por meio do parâmetro ' line ' out.</span><span class="sxs-lookup"><span data-stu-id="21d51-171">Finds the first newline (`\r\n`) in the `ReadOnlySequence<byte>` and returns it via the out 'line' parameter.</span></span>
- <span data-ttu-id="21d51-172">Corta essa linha, excluindo a `\r\n` do buffer de entrada.</span><span class="sxs-lookup"><span data-stu-id="21d51-172">Trims that line, excluding the `\r\n` from the input buffer.</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet6)]

##### <a name="empty-segments"></a><span data-ttu-id="21d51-173">Segmentos vazios</span><span class="sxs-lookup"><span data-stu-id="21d51-173">Empty segments</span></span>

<span data-ttu-id="21d51-174">É válido armazenar segmentos vazios dentro de um `ReadOnlySequence<T>`.</span><span class="sxs-lookup"><span data-stu-id="21d51-174">It's valid to store empty segments inside of a `ReadOnlySequence<T>`.</span></span> <span data-ttu-id="21d51-175">Segmentos vazios podem ocorrer ao enumerar segmentos explicitamente:</span><span class="sxs-lookup"><span data-stu-id="21d51-175">Empty segments may occur while enumerating segments explicitly:</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet7)]

<span data-ttu-id="21d51-176">O código anterior cria uma `ReadOnlySequence<byte>` com segmentos vazios e mostra como esses segmentos vazios afetam as várias APIs:</span><span class="sxs-lookup"><span data-stu-id="21d51-176">The preceding code creates a `ReadOnlySequence<byte>` with empty segments and shows how those empty segments affect the various APIs:</span></span>

- <span data-ttu-id="21d51-177">`ReadOnlySequence<T>.Slice` com uma `SequencePosition` apontando para um segmento vazio preserva esse segmento.</span><span class="sxs-lookup"><span data-stu-id="21d51-177">`ReadOnlySequence<T>.Slice` with a `SequencePosition` pointing to an empty segment preserves that segment.</span></span>
- <span data-ttu-id="21d51-178">`ReadOnlySequence<T>.Slice` com um int ignora os segmentos vazios.</span><span class="sxs-lookup"><span data-stu-id="21d51-178">`ReadOnlySequence<T>.Slice` with an int skips over the empty segments.</span></span>
- <span data-ttu-id="21d51-179">Enumerar o `ReadOnlySequence<T>` enumera os segmentos vazios.</span><span class="sxs-lookup"><span data-stu-id="21d51-179">Enumerating the `ReadOnlySequence<T>` enumerates the empty segments.</span></span>

### <a name="potential-problems-with-readonlysequencet-and-sequenceposition"></a><span data-ttu-id="21d51-180">Problemas potenciais com ReadOnlySequence\<T > e SequencePosition</span><span class="sxs-lookup"><span data-stu-id="21d51-180">Potential problems with ReadOnlySequence\<T> and SequencePosition</span></span>

<span data-ttu-id="21d51-181">Há vários resultados incomuns ao lidar com um `ReadOnlySequence<T>`/`SequencePosition` vs. um `ReadOnlySpan<T>`normal /`ReadOnlyMemory<T>`/`T[]`/:</span><span class="sxs-lookup"><span data-stu-id="21d51-181">There are several unusual outcomes when dealing with a `ReadOnlySequence<T>`/`SequencePosition` vs. a normal `ReadOnlySpan<T>`/`ReadOnlyMemory<T>`/`T[]`/`int`:</span></span>

- <span data-ttu-id="21d51-182">`SequencePosition` é um marcador de posição para uma `ReadOnlySequence<T>`específica, não uma posição absoluta.</span><span class="sxs-lookup"><span data-stu-id="21d51-182">`SequencePosition` is a position marker for a specific `ReadOnlySequence<T>`, not an absolute position.</span></span> <span data-ttu-id="21d51-183">Como ele é relativo a um `ReadOnlySequence<T>`específico, ele não tem significado se for usado fora do `ReadOnlySequence<T>` de origem.</span><span class="sxs-lookup"><span data-stu-id="21d51-183">Because it's relative to a specific `ReadOnlySequence<T>`, it doesn't have meaning if used outside of the `ReadOnlySequence<T>` where it originated.</span></span>
- <span data-ttu-id="21d51-184">A aritmética não pode ser executada em `SequencePosition` sem o `ReadOnlySequence<T>`.</span><span class="sxs-lookup"><span data-stu-id="21d51-184">Arithmetic can't be performed on `SequencePosition` without the `ReadOnlySequence<T>`.</span></span> <span data-ttu-id="21d51-185">Isso significa fazer coisas básicas como `position++` é escrito `ReadOnlySequence<T>.GetPosition(position, 1)`.</span><span class="sxs-lookup"><span data-stu-id="21d51-185">That means doing basic things like `position++` is written `ReadOnlySequence<T>.GetPosition(position, 1)`.</span></span>
- <span data-ttu-id="21d51-186">`GetPosition(long)` não **dá suporte a** índices negativos.</span><span class="sxs-lookup"><span data-stu-id="21d51-186">`GetPosition(long)` does **not** support negative indexes.</span></span> <span data-ttu-id="21d51-187">Isso significa que é impossível obter o segundo para o último caractere sem percorrer todos os segmentos.</span><span class="sxs-lookup"><span data-stu-id="21d51-187">That means it's impossible to get the second to last character without walking all segments.</span></span>
- <span data-ttu-id="21d51-188">Dois `SequencePosition` não podem ser comparados, dificultando:</span><span class="sxs-lookup"><span data-stu-id="21d51-188">Two `SequencePosition` can't be compared, making it difficult to:</span></span>
  - <span data-ttu-id="21d51-189">Saiba se uma posição é maior ou menor que outra posição.</span><span class="sxs-lookup"><span data-stu-id="21d51-189">Know if one position is greater than or less than another position.</span></span>
  - <span data-ttu-id="21d51-190">Escreva alguns algoritmos de análise.</span><span class="sxs-lookup"><span data-stu-id="21d51-190">Write some parsing algorithms.</span></span>
- <span data-ttu-id="21d51-191">`ReadOnlySequence<T>` é maior que uma referência de objeto e deve ser passada por [em](../../csharp/language-reference/keywords/in-parameter-modifier.md) ou [ref](../../csharp/language-reference/keywords/ref.md) sempre que possível.</span><span class="sxs-lookup"><span data-stu-id="21d51-191">`ReadOnlySequence<T>` is bigger than an object reference and should be passed by [in](../../csharp/language-reference/keywords/in-parameter-modifier.md) or [ref](../../csharp/language-reference/keywords/ref.md) where possible.</span></span> <span data-ttu-id="21d51-192">A passagem de `ReadOnlySequence<T>` por `in` ou `ref` reduz as cópias da [estrutura](../../csharp/language-reference/keywords/struct.md).</span><span class="sxs-lookup"><span data-stu-id="21d51-192">Passing `ReadOnlySequence<T>` by `in` or `ref` reduces copies of the [struct](../../csharp/language-reference/keywords/struct.md).</span></span>
- <span data-ttu-id="21d51-193">Segmentos vazios:</span><span class="sxs-lookup"><span data-stu-id="21d51-193">Empty segments:</span></span>
  - <span data-ttu-id="21d51-194">São válidos dentro de um `ReadOnlySequence<T>`.</span><span class="sxs-lookup"><span data-stu-id="21d51-194">Are valid within a `ReadOnlySequence<T>`.</span></span>
  - <span data-ttu-id="21d51-195">Pode aparecer ao iterar usando o método `ReadOnlySequence<T>.TryGet`.</span><span class="sxs-lookup"><span data-stu-id="21d51-195">Can appear when iterating using the `ReadOnlySequence<T>.TryGet` method.</span></span>
  - <span data-ttu-id="21d51-196">Pode aparecer de divisão da sequência usando o método `ReadOnlySequence<T>.Slice()` com `SequencePosition` objetos.</span><span class="sxs-lookup"><span data-stu-id="21d51-196">Can appear slicing the sequence using the `ReadOnlySequence<T>.Slice()` method with `SequencePosition` objects.</span></span>

## <a name="sequencereadert"></a><span data-ttu-id="21d51-197">SequenceReader\<T\></span><span class="sxs-lookup"><span data-stu-id="21d51-197">SequenceReader\<T\></span></span>

<span data-ttu-id="21d51-198"><xref:System.Buffers.SequenceReader%601>:</span><span class="sxs-lookup"><span data-stu-id="21d51-198"><xref:System.Buffers.SequenceReader%601>:</span></span>

- <span data-ttu-id="21d51-199">É um novo tipo que foi introduzido no .NET Core 3,0 para simplificar o processamento de um `ReadOnlySequence<T>`.</span><span class="sxs-lookup"><span data-stu-id="21d51-199">Is a new type that was introduced in .NET Core 3.0 to simplify the processing of a `ReadOnlySequence<T>`.</span></span>
- <span data-ttu-id="21d51-200">Unifica as diferenças entre um único segmento `ReadOnlySequence<T>` e `ReadOnlySequence<T>`de vários segmentos.</span><span class="sxs-lookup"><span data-stu-id="21d51-200">Unifies the differences between a single segment `ReadOnlySequence<T>` and multi-segment `ReadOnlySequence<T>`.</span></span>
- <span data-ttu-id="21d51-201">Fornece ajuda para a leitura de dados binários e de texto (`byte` e `char`) que podem ou não ser divididos entre segmentos.</span><span class="sxs-lookup"><span data-stu-id="21d51-201">Provides helpers for reading binary and text data (`byte` and `char`) that may or may not be split across segments.</span></span>

<span data-ttu-id="21d51-202">Há métodos internos para lidar com o processamento de dados binários e delimitados.</span><span class="sxs-lookup"><span data-stu-id="21d51-202">There are built-in methods for dealing with processing both binary and delimited data.</span></span> <span data-ttu-id="21d51-203">A seção a seguir demonstra como os mesmos métodos se parecem com o `SequenceReader<T>`:</span><span class="sxs-lookup"><span data-stu-id="21d51-203">The following section demonstrates what those same methods look like with the `SequenceReader<T>`:</span></span>

### <a name="access-data"></a><span data-ttu-id="21d51-204">Acessar dados</span><span class="sxs-lookup"><span data-stu-id="21d51-204">Access data</span></span>

<span data-ttu-id="21d51-205">`SequenceReader<T>` tem métodos para enumerar dados dentro do `ReadOnlySequence<T>` diretamente.</span><span class="sxs-lookup"><span data-stu-id="21d51-205">`SequenceReader<T>` has methods for enumerating data inside of the `ReadOnlySequence<T>` directly.</span></span> <span data-ttu-id="21d51-206">O código a seguir é um exemplo de processamento de um `ReadOnlySequence<byte>` um `byte` de cada vez:</span><span class="sxs-lookup"><span data-stu-id="21d51-206">The following code is an example of processing a `ReadOnlySequence<byte>` a `byte` at a time:</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet8)]

<span data-ttu-id="21d51-207">O `CurrentSpan` expõe a `Span`do segmento atual, que é semelhante ao que foi feito no método manualmente.</span><span class="sxs-lookup"><span data-stu-id="21d51-207">The `CurrentSpan` exposes the current segment's `Span`, which is similar to what was done in the method manually.</span></span>

### <a name="use-position"></a><span data-ttu-id="21d51-208">Usar posição</span><span class="sxs-lookup"><span data-stu-id="21d51-208">Use position</span></span>

<span data-ttu-id="21d51-209">O código a seguir é uma implementação de exemplo de `FindIndexOf` usando o `SequenceReader<T>`:</span><span class="sxs-lookup"><span data-stu-id="21d51-209">The following code is an example implementation of `FindIndexOf` using the `SequenceReader<T>`:</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet9)]

### <a name="process-binary-data"></a><span data-ttu-id="21d51-210">Processar dados binários</span><span class="sxs-lookup"><span data-stu-id="21d51-210">Process binary data</span></span>

<span data-ttu-id="21d51-211">O exemplo a seguir analisa um tamanho inteiro big-endian de 4 bytes desde o início do `ReadOnlySequence<byte>`.</span><span class="sxs-lookup"><span data-stu-id="21d51-211">The following example parses a 4-byte big-endian integer length from the start of the `ReadOnlySequence<byte>`.</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet11)]

### <a name="process-text-data"></a><span data-ttu-id="21d51-212">Processar dados de texto</span><span class="sxs-lookup"><span data-stu-id="21d51-212">Process text data</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet10)]

### <a name="sequencereadert-common-problems"></a><span data-ttu-id="21d51-213">SequenceReader\<T\> problemas comuns</span><span class="sxs-lookup"><span data-stu-id="21d51-213">SequenceReader\<T\> common problems</span></span>

- <span data-ttu-id="21d51-214">Como `SequenceReader<T>` é uma struct mutável, ela sempre deve ser passada por [referência](../../csharp/language-reference/keywords/ref.md).</span><span class="sxs-lookup"><span data-stu-id="21d51-214">Because `SequenceReader<T>` is a mutable struct, it should always be passed by [reference](../../csharp/language-reference/keywords/ref.md).</span></span>
- <span data-ttu-id="21d51-215">`SequenceReader<T>` é uma [struct de referência](../../csharp/language-reference/keywords/ref.md#ref-struct-types) para que ela possa ser usada apenas em métodos síncronos e não possa ser armazenada em campos.</span><span class="sxs-lookup"><span data-stu-id="21d51-215">`SequenceReader<T>` is a [ref struct](../../csharp/language-reference/keywords/ref.md#ref-struct-types) so it can only be used in synchronous methods and can't be stored in fields.</span></span> <span data-ttu-id="21d51-216">Para obter mais informações, consulte [escrever código seguro C# e eficiente](../../csharp/write-safe-efficient-code.md).</span><span class="sxs-lookup"><span data-stu-id="21d51-216">For more information, see [Write safe and efficient C# code](../../csharp/write-safe-efficient-code.md).</span></span>
- <span data-ttu-id="21d51-217">`SequenceReader<T>` é otimizado para uso como um leitor somente de encaminhamento.</span><span class="sxs-lookup"><span data-stu-id="21d51-217">`SequenceReader<T>` is optimized for use as a forward-only reader.</span></span> <span data-ttu-id="21d51-218">o `Rewind` destina-se a backups pequenos que não podem ser resolvidos utilizando outras APIs `Read`, `Peek`e `IsNext`.</span><span class="sxs-lookup"><span data-stu-id="21d51-218">`Rewind` is intended for small backups that can't be addressed utilizing other `Read`, `Peek`, and `IsNext` APIs.</span></span>
