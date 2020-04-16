---
title: Oleodutos de I/O - .NET
description: Aprenda a usar eficientemente os pipelines de I/O em .NET e evite problemas em seu código.
ms.date: 10/01/2019
ms.technology: dotnet-standard
helpviewer_keywords:
- Pipelines
- Pipelines I/O
- I/O [.NET], Pipelines
author: rick-anderson
ms.author: riande
ms.openlocfilehash: 8822e731ae805e83d4072c5bd78dff3fcf9a31a1
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81462516"
---
# <a name="systemiopipelines-in-net"></a><span data-ttu-id="d3966-103">Pipelines system.IO.em .NET</span><span class="sxs-lookup"><span data-stu-id="d3966-103">System.IO.Pipelines in .NET</span></span>

<span data-ttu-id="d3966-104"><xref:System.IO.Pipelines>é uma nova biblioteca projetada para facilitar a realização de I/O de alto desempenho em .NET.</span><span class="sxs-lookup"><span data-stu-id="d3966-104"><xref:System.IO.Pipelines> is a new library that is designed to make it easier to do high-performance I/O in .NET.</span></span> <span data-ttu-id="d3966-105">É uma biblioteca direcionada ao .NET Standard que funciona em todas as implementações .NET.</span><span class="sxs-lookup"><span data-stu-id="d3966-105">It’s a library targeting .NET Standard that works on all .NET implementations.</span></span>

<a name="solve"></a>

## <a name="what-problem-does-systemiopipelines-solve"></a><span data-ttu-id="d3966-106">Que problema o System.IO.Pipelines resolve</span><span class="sxs-lookup"><span data-stu-id="d3966-106">What problem does System.IO.Pipelines solve</span></span>

<!-- corner case doesn't MT (machine translate)   -->
<span data-ttu-id="d3966-107">Os aplicativos que analisam os dados de streaming são compostos de código de caldeira com muitos fluxos de código especializados e incomuns.</span><span class="sxs-lookup"><span data-stu-id="d3966-107">Apps that parse streaming data are composed of boilerplate code having many specialized and unusual code flows.</span></span> <span data-ttu-id="d3966-108">A caldeira e o código de caso especial são complexos e difíceis de manter.</span><span class="sxs-lookup"><span data-stu-id="d3966-108">The boilerplate and special case code is complex and difficult to maintain.</span></span>

<span data-ttu-id="d3966-109">`System.IO.Pipelines`foi arquitetado para:</span><span class="sxs-lookup"><span data-stu-id="d3966-109">`System.IO.Pipelines` was architected to:</span></span>

* <span data-ttu-id="d3966-110">Tenha dados de streaming de análise de alto desempenho.</span><span class="sxs-lookup"><span data-stu-id="d3966-110">Have high performance parsing streaming data.</span></span>
* <span data-ttu-id="d3966-111">Reduza a complexidade do código.</span><span class="sxs-lookup"><span data-stu-id="d3966-111">Reduce code complexity.</span></span>

<span data-ttu-id="d3966-112">O código a seguir é típico de um servidor TCP que `'\n'`recebe mensagens delimitadas de linha (delimitadas por ) de um cliente:</span><span class="sxs-lookup"><span data-stu-id="d3966-112">The following code is typical for a TCP server that receives line-delimited messages (delimited by `'\n'`) from a client:</span></span>

```csharp
async Task ProcessLinesAsync(NetworkStream stream)
{
    var buffer = new byte[1024];
    await stream.ReadAsync(buffer, 0, buffer.Length);

    // Process a single line from the buffer
    ProcessLine(buffer);
}
```

<span data-ttu-id="d3966-113">O código anterior tem vários problemas:</span><span class="sxs-lookup"><span data-stu-id="d3966-113">The preceding code has several problems:</span></span>

* <span data-ttu-id="d3966-114">A mensagem inteira (fim da linha) pode `ReadAsync`não ser recebida em uma única chamada para .</span><span class="sxs-lookup"><span data-stu-id="d3966-114">The entire message (end of line) might not be received in a single call to `ReadAsync`.</span></span>
* <span data-ttu-id="d3966-115">Está ignorando o resultado `stream.ReadAsync`de.</span><span class="sxs-lookup"><span data-stu-id="d3966-115">It's ignoring the result of `stream.ReadAsync`.</span></span> <span data-ttu-id="d3966-116">`stream.ReadAsync`retorna quantos dados foram lidos.</span><span class="sxs-lookup"><span data-stu-id="d3966-116">`stream.ReadAsync` returns how much data was read.</span></span>
* <span data-ttu-id="d3966-117">Ele não lida com o caso em que `ReadAsync` várias linhas são lidas em uma única chamada.</span><span class="sxs-lookup"><span data-stu-id="d3966-117">It doesn't handle the case where multiple lines are read in a single `ReadAsync` call.</span></span>
* <span data-ttu-id="d3966-118">Ele aloca `byte` uma matriz a cada leitura.</span><span class="sxs-lookup"><span data-stu-id="d3966-118">It allocates a `byte` array with each read.</span></span>

<span data-ttu-id="d3966-119">Para corrigir os problemas anteriores, são necessárias as seguintes alterações:</span><span class="sxs-lookup"><span data-stu-id="d3966-119">To fix the preceding problems, the following changes are required:</span></span>

* <span data-ttu-id="d3966-120">Tampe os dados de entrada até que uma nova linha seja encontrada.</span><span class="sxs-lookup"><span data-stu-id="d3966-120">Buffer the incoming data until a new line is found.</span></span>
* <span data-ttu-id="d3966-121">Analise todas as linhas devolvidas no buffer.</span><span class="sxs-lookup"><span data-stu-id="d3966-121">Parse all the lines returned in the buffer.</span></span>
* <span data-ttu-id="d3966-122">É possível que a linha seja maior que 1 KB (1024 bytes).</span><span class="sxs-lookup"><span data-stu-id="d3966-122">It's possible that the line is bigger than 1 KB (1024 bytes).</span></span> <span data-ttu-id="d3966-123">O código precisa redimensionar o buffer de entrada até que o delimitador seja encontrado para encaixar a linha completa dentro do buffer.</span><span class="sxs-lookup"><span data-stu-id="d3966-123">The code needs to resize the input buffer until the delimiter is found in order to fit the complete line inside the buffer.</span></span>

  * <span data-ttu-id="d3966-124">Se o buffer for redimensionado, mais cópias de buffer serão feitas à medida que linhas mais longas aparecerem na entrada.</span><span class="sxs-lookup"><span data-stu-id="d3966-124">If the buffer is resized, more buffer copies are made as longer lines appear in the input.</span></span>
  * <span data-ttu-id="d3966-125">Para reduzir o espaço desperdiçado, compacte o buffer usado para leitura de linhas.</span><span class="sxs-lookup"><span data-stu-id="d3966-125">To reduce wasted space, compact the buffer used for reading lines.</span></span>

* <span data-ttu-id="d3966-126">Considere usar o buffer pooling para evitar alocar a memória repetidamente.</span><span class="sxs-lookup"><span data-stu-id="d3966-126">Consider using buffer pooling to avoid allocating memory repeatedly.</span></span>
* <span data-ttu-id="d3966-127">O código a seguir aborda alguns desses problemas:</span><span class="sxs-lookup"><span data-stu-id="d3966-127">The following code addresses some of these problems:</span></span>

[!code-csharp[](~/samples/snippets/csharp/pipelines/ProcessLinesAsync.cs?name=snippet)]

<span data-ttu-id="d3966-128">O código anterior é complexo e não resolve todos os problemas identificados.</span><span class="sxs-lookup"><span data-stu-id="d3966-128">The previous code is complex and doesn't address all the problems identified.</span></span> <span data-ttu-id="d3966-129">Rede de alto desempenho geralmente significa escrever código muito complexo para maximizar o desempenho.</span><span class="sxs-lookup"><span data-stu-id="d3966-129">High-performance networking usually means writing very complex code to maximize performance.</span></span> <span data-ttu-id="d3966-130">`System.IO.Pipelines`foi projetado para facilitar a escrita deste tipo de código.</span><span class="sxs-lookup"><span data-stu-id="d3966-130">`System.IO.Pipelines` was designed to make writing this type of code easier.</span></span>

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

## <a name="pipe"></a><span data-ttu-id="d3966-131">Pipe</span><span class="sxs-lookup"><span data-stu-id="d3966-131">Pipe</span></span>

<span data-ttu-id="d3966-132">A <xref:System.IO.Pipelines.Pipe> classe pode ser `PipeWriter/PipeReader` usada para criar um par.</span><span class="sxs-lookup"><span data-stu-id="d3966-132">The <xref:System.IO.Pipelines.Pipe> class can be used to create a `PipeWriter/PipeReader` pair.</span></span> <span data-ttu-id="d3966-133">Todos os dados `PipeWriter` gravados `PipeReader`no está disponível no:</span><span class="sxs-lookup"><span data-stu-id="d3966-133">All data written into the `PipeWriter` is available in the `PipeReader`:</span></span>

[!code-csharp[](~/samples/snippets/csharp/pipelines/Pipe.cs?name=snippet2)]

<a name="pbu"></a>

### <a name="pipe-basic-usage"></a><span data-ttu-id="d3966-134">Uso básico do tubo</span><span class="sxs-lookup"><span data-stu-id="d3966-134">Pipe basic usage</span></span>

[!code-csharp[](~/samples/snippets/csharp/pipelines/Pipe.cs?name=snippet)]

<span data-ttu-id="d3966-135">Há dois loops:</span><span class="sxs-lookup"><span data-stu-id="d3966-135">There are two loops:</span></span>

* <span data-ttu-id="d3966-136">`FillPipeAsync`lê do `Socket` e escreve `PipeWriter`para o .</span><span class="sxs-lookup"><span data-stu-id="d3966-136">`FillPipeAsync` reads from the `Socket` and writes to the `PipeWriter`.</span></span>
* <span data-ttu-id="d3966-137">`ReadPipeAsync`lê a `PipeReader` partir das linhas de entrada e analisa.</span><span class="sxs-lookup"><span data-stu-id="d3966-137">`ReadPipeAsync` reads from the `PipeReader` and parses incoming lines.</span></span>

<span data-ttu-id="d3966-138">Não há buffers explícitos alocados.</span><span class="sxs-lookup"><span data-stu-id="d3966-138">There are no explicit buffers allocated.</span></span> <span data-ttu-id="d3966-139">Toda a gestão de `PipeReader` `PipeWriter` buffer é delegada para as implementações.</span><span class="sxs-lookup"><span data-stu-id="d3966-139">All buffer management is delegated to the `PipeReader` and `PipeWriter` implementations.</span></span> <span data-ttu-id="d3966-140">Delegar o gerenciamento de buffer satisfaz que o consumo de código se concentre apenas na lógica do negócio.</span><span class="sxs-lookup"><span data-stu-id="d3966-140">Delegating buffer management makes it easier for consuming code to focus solely on the business logic.</span></span>

<span data-ttu-id="d3966-141">No primeiro loop:</span><span class="sxs-lookup"><span data-stu-id="d3966-141">In the first loop:</span></span>

* <span data-ttu-id="d3966-142"><xref:System.IO.Pipelines.PipeWriter.GetMemory(System.Int32)?displayProperty=nameWithType>é chamado para obter memória do escritor subjacente.</span><span class="sxs-lookup"><span data-stu-id="d3966-142"><xref:System.IO.Pipelines.PipeWriter.GetMemory(System.Int32)?displayProperty=nameWithType> is called to get memory from the underlying writer.</span></span>
* <span data-ttu-id="d3966-143"><xref:System.IO.Pipelines.PipeWriter.Advance(System.Int32)?displayProperty=nameWithType>é chamado para `PipeWriter` dizer quantos dados foram escritos para o buffer.</span><span class="sxs-lookup"><span data-stu-id="d3966-143"><xref:System.IO.Pipelines.PipeWriter.Advance(System.Int32)?displayProperty=nameWithType> is called to tell the `PipeWriter` how much data was written to the buffer.</span></span>
* <span data-ttu-id="d3966-144"><xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A?displayProperty=nameWithType>é chamado para disponibilizar os `PipeReader`dados para o .</span><span class="sxs-lookup"><span data-stu-id="d3966-144"><xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A?displayProperty=nameWithType> is called to make the data available to the `PipeReader`.</span></span>

<span data-ttu-id="d3966-145">No segundo loop, `PipeReader` o consome os `PipeWriter`buffers escritos por .</span><span class="sxs-lookup"><span data-stu-id="d3966-145">In the second loop, the `PipeReader` consumes the buffers written by `PipeWriter`.</span></span> <span data-ttu-id="d3966-146">Os buffers vêm do soquete.</span><span class="sxs-lookup"><span data-stu-id="d3966-146">The buffers come from the socket.</span></span> <span data-ttu-id="d3966-147">A chamada `PipeReader.ReadAsync`para:</span><span class="sxs-lookup"><span data-stu-id="d3966-147">The call to `PipeReader.ReadAsync`:</span></span>

* <span data-ttu-id="d3966-148">Retorna <xref:System.IO.Pipelines.ReadResult> um que contém duas informações importantes:</span><span class="sxs-lookup"><span data-stu-id="d3966-148">Returns a <xref:System.IO.Pipelines.ReadResult> that contains two important pieces of information:</span></span>

  * <span data-ttu-id="d3966-149">Os dados que foram lidos na forma de `ReadOnlySequence<byte>`.</span><span class="sxs-lookup"><span data-stu-id="d3966-149">The data that was read in the form of `ReadOnlySequence<byte>`.</span></span>
  * <span data-ttu-id="d3966-150">Um booleano `IsCompleted` que indica se o fim dos dados (EOF) foi atingido.</span><span class="sxs-lookup"><span data-stu-id="d3966-150">A boolean `IsCompleted` that indicates if the end of data (EOF) has been reached.</span></span>

<span data-ttu-id="d3966-151">Depois de encontrar o delimitador final da linha (EOL) e analisar a linha:</span><span class="sxs-lookup"><span data-stu-id="d3966-151">After finding the end of line (EOL) delimiter and parsing the line:</span></span>

* <span data-ttu-id="d3966-152">A lógica processa o buffer para pular o que já está processado.</span><span class="sxs-lookup"><span data-stu-id="d3966-152">The logic processes the buffer to skip what's already processed.</span></span>
* <span data-ttu-id="d3966-153">`PipeReader.AdvanceTo`é chamado para `PipeReader` dizer quantos dados foram consumidos e examinados.</span><span class="sxs-lookup"><span data-stu-id="d3966-153">`PipeReader.AdvanceTo` is called to tell the `PipeReader` how much data has been consumed and examined.</span></span>

<span data-ttu-id="d3966-154">Os loops de leitor `Complete`e escritor terminam chamando .</span><span class="sxs-lookup"><span data-stu-id="d3966-154">The reader and writer loops end by calling `Complete`.</span></span> <span data-ttu-id="d3966-155">`Complete`permite que o tubo subjacente libere a memória que ele alocou.</span><span class="sxs-lookup"><span data-stu-id="d3966-155">`Complete` lets the underlying Pipe release the memory it allocated.</span></span>

### <a name="backpressure-and-flow-control"></a><span data-ttu-id="d3966-156">Backpressure e controle de fluxo</span><span class="sxs-lookup"><span data-stu-id="d3966-156">Backpressure and flow control</span></span>

<span data-ttu-id="d3966-157">Idealmente, a leitura e o trabalho de análise em conjunto:</span><span class="sxs-lookup"><span data-stu-id="d3966-157">Ideally, reading and parsing work together:</span></span>

* <span data-ttu-id="d3966-158">O segmento de escrita consome dados da rede e os coloca em buffers.</span><span class="sxs-lookup"><span data-stu-id="d3966-158">The writing thread consumes data from the network and puts it in buffers.</span></span>
* <span data-ttu-id="d3966-159">O segmento de análise é responsável pela construção das estruturas de dados apropriadas.</span><span class="sxs-lookup"><span data-stu-id="d3966-159">The parsing thread is responsible for constructing the appropriate data structures.</span></span>

<span data-ttu-id="d3966-160">Normalmente, a análise leva mais tempo do que apenas copiar blocos de dados da rede:</span><span class="sxs-lookup"><span data-stu-id="d3966-160">Typically, parsing takes more time than just copying blocks of data from the network:</span></span>

* <span data-ttu-id="d3966-161">O fio de leitura fica à frente do fio de análise.</span><span class="sxs-lookup"><span data-stu-id="d3966-161">The reading thread gets ahead of the parsing thread.</span></span>
* <span data-ttu-id="d3966-162">O segmento de leitura tem que diminuir ou alocar mais memória para armazenar os dados para o segmento de análise.</span><span class="sxs-lookup"><span data-stu-id="d3966-162">The reading thread has to either slow down or allocate more memory to store the data for the parsing thread.</span></span>

<span data-ttu-id="d3966-163">Para um desempenho ideal, há um equilíbrio entre pausas frequentes e alocação de mais memória.</span><span class="sxs-lookup"><span data-stu-id="d3966-163">For optimal performance, there's a balance between frequent pauses and allocating more memory.</span></span>

<span data-ttu-id="d3966-164">Para resolver o problema `Pipe` anterior, o tem duas configurações para controlar o fluxo de dados:</span><span class="sxs-lookup"><span data-stu-id="d3966-164">To solve the preceding problem, the `Pipe` has two settings to control the flow of data:</span></span>

* <span data-ttu-id="d3966-165"><xref:System.IO.Pipelines.PipeOptions.PauseWriterThreshold>: Determina quantos dados devem ser <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A> protegidos antes das chamadas pausarem.</span><span class="sxs-lookup"><span data-stu-id="d3966-165"><xref:System.IO.Pipelines.PipeOptions.PauseWriterThreshold>: Determines how much data should be buffered before calls to <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A> pause.</span></span>
* <span data-ttu-id="d3966-166"><xref:System.IO.Pipelines.PipeOptions.ResumeWriterThreshold>: Determina quantos dados o leitor tem `PipeWriter.FlushAsync` que observar antes das chamadas para retomar.</span><span class="sxs-lookup"><span data-stu-id="d3966-166"><xref:System.IO.Pipelines.PipeOptions.ResumeWriterThreshold>: Determines how much data the reader has to observe before calls to `PipeWriter.FlushAsync` resume.</span></span>

![Diagrama com resumeWriterThreshold e PauseWriterThreshold](./media/pipelines/resume-pause.png)

<span data-ttu-id="d3966-168"><xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="d3966-168"><xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A?displayProperty=nameWithType>:</span></span>

* <span data-ttu-id="d3966-169">Retorna um `ValueTask<FlushResult>` incompleto quando a `Pipe` quantidade `PauseWriterThreshold`de dados nas cruzes .</span><span class="sxs-lookup"><span data-stu-id="d3966-169">Returns an incomplete `ValueTask<FlushResult>` when the amount of data in the `Pipe` crosses `PauseWriterThreshold`.</span></span>
* <span data-ttu-id="d3966-170">Completa `ValueTask<FlushResult>` quando se torna `ResumeWriterThreshold`mais baixo do que .</span><span class="sxs-lookup"><span data-stu-id="d3966-170">Completes `ValueTask<FlushResult>` when it becomes lower than `ResumeWriterThreshold`.</span></span>

<span data-ttu-id="d3966-171">Dois valores são usados para prevenir o ciclismo rápido, o que pode ocorrer se um valor for usado.</span><span class="sxs-lookup"><span data-stu-id="d3966-171">Two values are used to prevent rapid cycling, which can occur if one value is used.</span></span>

### <a name="examples"></a><span data-ttu-id="d3966-172">Exemplos</span><span class="sxs-lookup"><span data-stu-id="d3966-172">Examples</span></span>

```csharp
// The Pipe will start returning incomplete tasks from FlushAsync until
// the reader examines at least 5 bytes.
var options = new PipeOptions(pauseWriterThreshold: 10, resumeWriterThreshold: 5);
var pipe = new Pipe(options);
```

### <a name="pipescheduler"></a><span data-ttu-id="d3966-173">PipeScheduler</span><span class="sxs-lookup"><span data-stu-id="d3966-173">PipeScheduler</span></span>

<span data-ttu-id="d3966-174">Normalmente, `async` ao `await`usar e, o código assíncrono é retomado em um <xref:System.Threading.Tasks.TaskScheduler> ou na corrente <xref:System.Threading.SynchronizationContext>.</span><span class="sxs-lookup"><span data-stu-id="d3966-174">Typically when using `async` and `await`, asynchronous code resumes on either on a <xref:System.Threading.Tasks.TaskScheduler> or on the current  <xref:System.Threading.SynchronizationContext>.</span></span>

<span data-ttu-id="d3966-175">Ao fazer I/O, é importante ter controle fino sobre onde a I/O é realizada.</span><span class="sxs-lookup"><span data-stu-id="d3966-175">When doing I/O, it's important to have fine-grained control over where the I/O is performed.</span></span> <span data-ttu-id="d3966-176">Este controle permite tirar vantagem dos caches da CPU de forma eficaz.</span><span class="sxs-lookup"><span data-stu-id="d3966-176">This control allows taking advantage of CPU caches effectively.</span></span> <span data-ttu-id="d3966-177">O cache eficiente é fundamental para aplicativos de alto desempenho, como servidores web.</span><span class="sxs-lookup"><span data-stu-id="d3966-177">Efficient caching is critical for high-performance apps like web servers.</span></span> <span data-ttu-id="d3966-178"><xref:System.IO.Pipelines.PipeScheduler>fornece controle sobre onde os retornos assíncronos são executados.</span><span class="sxs-lookup"><span data-stu-id="d3966-178"><xref:System.IO.Pipelines.PipeScheduler> provides control over where asynchronous callbacks run.</span></span> <span data-ttu-id="d3966-179">Por padrão:</span><span class="sxs-lookup"><span data-stu-id="d3966-179">By default:</span></span>

* <span data-ttu-id="d3966-180">A <xref:System.Threading.SynchronizationContext> corrente é usada.</span><span class="sxs-lookup"><span data-stu-id="d3966-180">The current <xref:System.Threading.SynchronizationContext> is used.</span></span>
* <span data-ttu-id="d3966-181">Se não `SynchronizationContext`houver, ele usa o pool de segmentos para executar retornos de chamadas.</span><span class="sxs-lookup"><span data-stu-id="d3966-181">If there's no `SynchronizationContext`, it uses the thread pool to run callbacks.</span></span>

[!code-csharp[](~/samples/snippets/csharp/pipelines/Program.cs?name=snippet)]

<span data-ttu-id="d3966-182">[PipeScheduler.ThreadPool](xref:System.IO.Pipelines.PipeScheduler.ThreadPool) é <xref:System.IO.Pipelines.PipeScheduler> a implementação que faz filas de retorno saqueado no pool de segmentos.</span><span class="sxs-lookup"><span data-stu-id="d3966-182">[PipeScheduler.ThreadPool](xref:System.IO.Pipelines.PipeScheduler.ThreadPool) is the <xref:System.IO.Pipelines.PipeScheduler> implementation that queues callbacks to the thread pool.</span></span> <span data-ttu-id="d3966-183">`PipeScheduler.ThreadPool`é o padrão e geralmente a melhor escolha.</span><span class="sxs-lookup"><span data-stu-id="d3966-183">`PipeScheduler.ThreadPool` is the default and generally the best choice.</span></span> <span data-ttu-id="d3966-184">[PipeScheduler.Inline](xref:System.IO.Pipelines.PipeScheduler.Inline) pode causar consequências não intencionais, como impasses.</span><span class="sxs-lookup"><span data-stu-id="d3966-184">[PipeScheduler.Inline](xref:System.IO.Pipelines.PipeScheduler.Inline) can cause unintended consequences such as deadlocks.</span></span>

### <a name="pipe-reset"></a><span data-ttu-id="d3966-185">Reset de tubulação</span><span class="sxs-lookup"><span data-stu-id="d3966-185">Pipe reset</span></span>

<span data-ttu-id="d3966-186">É freqüentemente eficiente reutilizar `Pipe` o objeto.</span><span class="sxs-lookup"><span data-stu-id="d3966-186">It's frequently efficient to reuse the `Pipe` object.</span></span> <span data-ttu-id="d3966-187">Para reiniciar o tubo, <xref:System.IO.Pipelines.PipeReader> <xref:System.IO.Pipelines.Pipe.Reset%2A> ligue `PipeReader` `PipeWriter` quando ambos estiverem completos.</span><span class="sxs-lookup"><span data-stu-id="d3966-187">To reset the pipe, call <xref:System.IO.Pipelines.PipeReader> <xref:System.IO.Pipelines.Pipe.Reset%2A> when both the `PipeReader` and `PipeWriter` are complete.</span></span>

## <a name="pipereader"></a><span data-ttu-id="d3966-188">PipeReader</span><span class="sxs-lookup"><span data-stu-id="d3966-188">PipeReader</span></span>

<span data-ttu-id="d3966-189"><xref:System.IO.Pipelines.PipeReader>gerencia a memória em nome do chamador.</span><span class="sxs-lookup"><span data-stu-id="d3966-189"><xref:System.IO.Pipelines.PipeReader> manages memory on the caller's behalf.</span></span> <span data-ttu-id="d3966-190">**Sempre** <xref:System.IO.Pipelines.PipeReader.AdvanceTo%2A?displayProperty=nameWithType> ligue <xref:System.IO.Pipelines.PipeReader.ReadAsync%2A?displayProperty=nameWithType>depois de ligar.</span><span class="sxs-lookup"><span data-stu-id="d3966-190">**Always** call <xref:System.IO.Pipelines.PipeReader.AdvanceTo%2A?displayProperty=nameWithType> after calling <xref:System.IO.Pipelines.PipeReader.ReadAsync%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="d3966-191">Isso permite `PipeReader` saber quando o chamador é feito com a memória para que ele possa ser rastreado.</span><span class="sxs-lookup"><span data-stu-id="d3966-191">This lets the `PipeReader` know when the caller is done with the memory so that it can be tracked.</span></span> <span data-ttu-id="d3966-192">O `ReadOnlySequence<byte>` retorno `PipeReader.ReadAsync` só é válido até `PipeReader.AdvanceTo`a chamada do .</span><span class="sxs-lookup"><span data-stu-id="d3966-192">The `ReadOnlySequence<byte>` returned from `PipeReader.ReadAsync` is only valid until the call the `PipeReader.AdvanceTo`.</span></span> <span data-ttu-id="d3966-193">É ilegal usar `ReadOnlySequence<byte>` depois `PipeReader.AdvanceTo`de ligar.</span><span class="sxs-lookup"><span data-stu-id="d3966-193">It's illegal to use `ReadOnlySequence<byte>` after calling `PipeReader.AdvanceTo`.</span></span>

<span data-ttu-id="d3966-194">`PipeReader.AdvanceTo`leva <xref:System.SequencePosition> dois argumentos:</span><span class="sxs-lookup"><span data-stu-id="d3966-194">`PipeReader.AdvanceTo` takes two <xref:System.SequencePosition> arguments:</span></span>

* <span data-ttu-id="d3966-195">O primeiro argumento determina quanta memória foi consumida.</span><span class="sxs-lookup"><span data-stu-id="d3966-195">The first argument determines how much memory was consumed.</span></span>
* <span data-ttu-id="d3966-196">O segundo argumento determina quanto do buffer foi observado.</span><span class="sxs-lookup"><span data-stu-id="d3966-196">The second argument determines how much of the buffer was observed.</span></span>

<span data-ttu-id="d3966-197">Marcar dados como consumidos significa que o tubo pode retornar a memória para o pool de buffer subjacente.</span><span class="sxs-lookup"><span data-stu-id="d3966-197">Marking data as consumed means that the pipe can return the memory to the underlying buffer pool.</span></span> <span data-ttu-id="d3966-198">Marcar dados como observado controla o `PipeReader.ReadAsync` que a próxima chamada faz.</span><span class="sxs-lookup"><span data-stu-id="d3966-198">Marking data as observed controls what the next call to `PipeReader.ReadAsync` does.</span></span> <span data-ttu-id="d3966-199">Marcar tudo como observado significa que `PipeReader.ReadAsync` a próxima chamada não retornará até que haja mais dados escritos no tubo.</span><span class="sxs-lookup"><span data-stu-id="d3966-199">Marking everything as observed means that the next call to `PipeReader.ReadAsync` won't return until there's more data written to the pipe.</span></span> <span data-ttu-id="d3966-200">Qualquer outro valor fará a `PipeReader.ReadAsync` próxima chamada para retornar imediatamente com os dados observados *e* não observados, mas não dados que já foram consumidos.</span><span class="sxs-lookup"><span data-stu-id="d3966-200">Any other value will make the next call to `PipeReader.ReadAsync` return immediately with the observed *and* unobserved data, but not data that has already been consumed.</span></span>

### <a name="read-streaming-data-scenarios"></a><span data-ttu-id="d3966-201">Leia cenários de dados de streaming</span><span class="sxs-lookup"><span data-stu-id="d3966-201">Read streaming data scenarios</span></span>

<span data-ttu-id="d3966-202">Existem alguns padrões típicos que surgem ao tentar ler dados de streaming:</span><span class="sxs-lookup"><span data-stu-id="d3966-202">There are a couple of typical patterns that emerge when trying to read streaming data:</span></span>

* <span data-ttu-id="d3966-203">Dado um fluxo de dados, analise uma única mensagem.</span><span class="sxs-lookup"><span data-stu-id="d3966-203">Given a stream of data, parse a single message.</span></span>
* <span data-ttu-id="d3966-204">Dado um fluxo de dados, analise todas as mensagens disponíveis.</span><span class="sxs-lookup"><span data-stu-id="d3966-204">Given a stream of data, parse all available messages.</span></span>

<span data-ttu-id="d3966-205">Os exemplos a `TryParseMessage` seguir usam o método para `ReadOnlySequence<byte>`analisar mensagens de a .</span><span class="sxs-lookup"><span data-stu-id="d3966-205">The following examples use the `TryParseMessage` method for parsing messages from a `ReadOnlySequence<byte>`.</span></span> <span data-ttu-id="d3966-206">`TryParseMessage`analisa uma única mensagem e atualiza o buffer de entrada para aparar a mensagem analisado do buffer.</span><span class="sxs-lookup"><span data-stu-id="d3966-206">`TryParseMessage` parses a single message and update the input buffer to trim the parsed message from the buffer.</span></span> <span data-ttu-id="d3966-207">`TryParseMessage`não faz parte do .NET, é um método escrito pelo usuário usado nas seguintes seções.</span><span class="sxs-lookup"><span data-stu-id="d3966-207">`TryParseMessage` is not part of .NET, it's a user written method used in the following sections.</span></span>

```csharp
bool TryParseMessage(ref ReadOnlySequence<byte> buffer, out Message message);
```

### <a name="read-a-single-message"></a><span data-ttu-id="d3966-208">Leia uma única mensagem</span><span class="sxs-lookup"><span data-stu-id="d3966-208">Read a single message</span></span>

<span data-ttu-id="d3966-209">O código a seguir lê `PipeReader` uma única mensagem de um e devolve-a ao chamador.</span><span class="sxs-lookup"><span data-stu-id="d3966-209">The following code reads a single message from a `PipeReader` and returns it to the caller.</span></span>

[!code-csharp[ReadSingleMsg](~/samples/snippets/csharp/pipelines/ReadSingleMsg.cs?name=snippet)]

<span data-ttu-id="d3966-210">O código anterior:</span><span class="sxs-lookup"><span data-stu-id="d3966-210">The preceding code:</span></span>

* <span data-ttu-id="d3966-211">Analisa uma única mensagem.</span><span class="sxs-lookup"><span data-stu-id="d3966-211">Parses a single message.</span></span>
* <span data-ttu-id="d3966-212">Atualiza o `SequencePosition` consumido e `SequencePosition` examinado para apontar para o início do buffer de entrada aparado.</span><span class="sxs-lookup"><span data-stu-id="d3966-212">Updates the consumed `SequencePosition` and examined `SequencePosition` to point to the start of the trimmed input buffer.</span></span>

<span data-ttu-id="d3966-213">Os `SequencePosition` dois argumentos `TryParseMessage` são atualizados porque remove a mensagem analisado do buffer de entrada.</span><span class="sxs-lookup"><span data-stu-id="d3966-213">The two `SequencePosition` arguments are updated because `TryParseMessage` removes the parsed message from the input buffer.</span></span> <span data-ttu-id="d3966-214">Geralmente, ao analisar uma única mensagem do buffer, a posição examinada deve ser uma das seguintes:</span><span class="sxs-lookup"><span data-stu-id="d3966-214">Generally, when parsing a single message from the buffer, the examined position should be one of the following:</span></span>

* <span data-ttu-id="d3966-215">O fim da mensagem.</span><span class="sxs-lookup"><span data-stu-id="d3966-215">The end of the message.</span></span>
* <span data-ttu-id="d3966-216">O fim do buffer recebido se nenhuma mensagem foi encontrada.</span><span class="sxs-lookup"><span data-stu-id="d3966-216">The end of the received buffer if no message was found.</span></span>

<span data-ttu-id="d3966-217">O caso de mensagem única tem o maior potencial para erros.</span><span class="sxs-lookup"><span data-stu-id="d3966-217">The single message case has the most potential for errors.</span></span> <span data-ttu-id="d3966-218">Passar os valores errados para *examinados* pode resultar em uma exceção fora da memória ou um loop infinito.</span><span class="sxs-lookup"><span data-stu-id="d3966-218">Passing the wrong values to *examined* can result in an out of memory exception or an infinite loop.</span></span> <span data-ttu-id="d3966-219">Para obter mais informações, consulte a seção [problemas comuns do PipeReader](#gotchas) neste artigo.</span><span class="sxs-lookup"><span data-stu-id="d3966-219">For more information, see the [PipeReader common problems](#gotchas) section in this article.</span></span>

### <a name="reading-multiple-messages"></a><span data-ttu-id="d3966-220">Lendo várias mensagens</span><span class="sxs-lookup"><span data-stu-id="d3966-220">Reading multiple messages</span></span>

<span data-ttu-id="d3966-221">O código a seguir lê `PipeReader` todas `ProcessMessageAsync` as mensagens de a e chama cada um.</span><span class="sxs-lookup"><span data-stu-id="d3966-221">The following code reads all messages from a `PipeReader` and calls `ProcessMessageAsync` on each.</span></span>

[!code-csharp[MyConnection1](~/samples/snippets/csharp/pipelines/MyConnection1.cs?name=snippet)]

### <a name="cancellation"></a><span data-ttu-id="d3966-222">Cancelamento</span><span class="sxs-lookup"><span data-stu-id="d3966-222">Cancellation</span></span>

<span data-ttu-id="d3966-223">`PipeReader.ReadAsync`:</span><span class="sxs-lookup"><span data-stu-id="d3966-223">`PipeReader.ReadAsync`:</span></span>

* <span data-ttu-id="d3966-224">Suporta passar <xref:System.Threading.CancellationToken>um .</span><span class="sxs-lookup"><span data-stu-id="d3966-224">Supports passing a <xref:System.Threading.CancellationToken>.</span></span>
* <span data-ttu-id="d3966-225">Joga <xref:System.OperationCanceledException> um `CancellationToken` se o for cancelado enquanto há uma leitura pendente.</span><span class="sxs-lookup"><span data-stu-id="d3966-225">Throws an <xref:System.OperationCanceledException> if the `CancellationToken` is canceled while there's a read pending.</span></span>
* <span data-ttu-id="d3966-226">Apoia uma maneira de cancelar a <xref:System.IO.Pipelines.PipeReader.CancelPendingRead%2A?displayProperty=nameWithType>operação de leitura atual via , o que evita aumentar uma exceção.</span><span class="sxs-lookup"><span data-stu-id="d3966-226">Supports a way to cancel the current read operation via <xref:System.IO.Pipelines.PipeReader.CancelPendingRead%2A?displayProperty=nameWithType>, which avoids raising an exception.</span></span> <span data-ttu-id="d3966-227">A `PipeReader.CancelPendingRead` chamada faz com `PipeReader.ReadAsync` que a <xref:System.IO.Pipelines.ReadResult> `IsCanceled` chamada `true`atual ou próxima retorne a um com set para .</span><span class="sxs-lookup"><span data-stu-id="d3966-227">Calling `PipeReader.CancelPendingRead` causes the current or next call to `PipeReader.ReadAsync` to return a <xref:System.IO.Pipelines.ReadResult> with `IsCanceled` set to `true`.</span></span> <span data-ttu-id="d3966-228">Isso pode ser útil para parar o loop de leitura existente de uma forma não destrutiva e não excepcional.</span><span class="sxs-lookup"><span data-stu-id="d3966-228">This can be useful for halting the existing read loop in a non-destructive and non-exceptional way.</span></span>

[!code-csharp[MyConnection](~/samples/snippets/csharp/pipelines/MyConnection.cs?name=snippet)]

<a name="gotchas"></a>

### <a name="pipereader-common-problems"></a><span data-ttu-id="d3966-229">Problemas comuns do PipeReader</span><span class="sxs-lookup"><span data-stu-id="d3966-229">PipeReader common problems</span></span>

* <span data-ttu-id="d3966-230">Passar os valores errados para `consumed` ou `examined` pode resultar na leitura de dados já lidos.</span><span class="sxs-lookup"><span data-stu-id="d3966-230">Passing the wrong values to `consumed` or `examined` may result in reading already read data.</span></span>
* <span data-ttu-id="d3966-231">Passar `buffer.End` como examinado pode resultar em:</span><span class="sxs-lookup"><span data-stu-id="d3966-231">Passing `buffer.End` as examined may result in:</span></span>

  * <span data-ttu-id="d3966-232">Dados paralisados</span><span class="sxs-lookup"><span data-stu-id="d3966-232">Stalled data</span></span>
  * <span data-ttu-id="d3966-233">Possivelmente uma eventual exceção fora da memória (OOM) se os dados não forem consumidos.</span><span class="sxs-lookup"><span data-stu-id="d3966-233">Possibly an eventual Out of Memory (OOM) exception if data isn't consumed.</span></span> <span data-ttu-id="d3966-234">Por exemplo, `PipeReader.AdvanceTo(position, buffer.End)` ao processar uma única mensagem de cada vez a partir do buffer.</span><span class="sxs-lookup"><span data-stu-id="d3966-234">For example, `PipeReader.AdvanceTo(position, buffer.End)` when processing a single message at a time from the buffer.</span></span>

* <span data-ttu-id="d3966-235">Passar os valores errados para `consumed` ou `examined` pode resultar em um loop infinito.</span><span class="sxs-lookup"><span data-stu-id="d3966-235">Passing the wrong values to `consumed` or `examined` may result in an infinite loop.</span></span> <span data-ttu-id="d3966-236">Por `PipeReader.AdvanceTo(buffer.Start)` exemplo, `buffer.Start` se não tiver sido alterado `PipeReader.ReadAsync` fará com que a próxima chamada retorne imediatamente antes que novos dados cheguem.</span><span class="sxs-lookup"><span data-stu-id="d3966-236">For example, `PipeReader.AdvanceTo(buffer.Start)` if `buffer.Start` hasn't changed will cause the next call to `PipeReader.ReadAsync` to return immediately before new data arrives.</span></span>
* <span data-ttu-id="d3966-237">Passar os valores errados para `consumed` ou `examined` pode resultar em buffering infinito (eventual OOM).</span><span class="sxs-lookup"><span data-stu-id="d3966-237">Passing the wrong values to `consumed` or `examined` may result in infinite buffering (eventual OOM).</span></span>
* <span data-ttu-id="d3966-238">O `ReadOnlySequence<byte>` uso `PipeReader.AdvanceTo` da chamada pós-chamada pode resultar em corrupção de memória (uso após a liberdade).</span><span class="sxs-lookup"><span data-stu-id="d3966-238">Using the `ReadOnlySequence<byte>` after calling `PipeReader.AdvanceTo` may result in memory corruption (use after free).</span></span>
* <span data-ttu-id="d3966-239">Não ligar `PipeReader.Complete/CompleteAsync` pode resultar em um vazamento de memória.</span><span class="sxs-lookup"><span data-stu-id="d3966-239">Failing to call `PipeReader.Complete/CompleteAsync` may result in a memory leak.</span></span>
* <span data-ttu-id="d3966-240">Verificar <xref:System.IO.Pipelines.ReadResult.IsCompleted?displayProperty=nameWithType> e sair da lógica de leitura antes de processar o buffer resulta em perda de dados.</span><span class="sxs-lookup"><span data-stu-id="d3966-240">Checking <xref:System.IO.Pipelines.ReadResult.IsCompleted?displayProperty=nameWithType> and exiting the reading logic before processing the buffer results in data loss.</span></span> <span data-ttu-id="d3966-241">A condição de saída `ReadResult.Buffer.IsEmpty` do `ReadResult.IsCompleted`loop deve ser baseada em e .</span><span class="sxs-lookup"><span data-stu-id="d3966-241">The loop exit condition should be based on `ReadResult.Buffer.IsEmpty` and `ReadResult.IsCompleted`.</span></span> <span data-ttu-id="d3966-242">Fazer isso incorretamente pode resultar em um loop infinito.</span><span class="sxs-lookup"><span data-stu-id="d3966-242">Doing this incorrectly could result in an infinite loop.</span></span>

#### <a name="problematic-code"></a><span data-ttu-id="d3966-243">Código problemático</span><span class="sxs-lookup"><span data-stu-id="d3966-243">Problematic code</span></span>

<span data-ttu-id="d3966-244">❌**Perda de dados**</span><span class="sxs-lookup"><span data-stu-id="d3966-244">❌ **Data loss**</span></span>

<span data-ttu-id="d3966-245">O `ReadResult` pode retornar o segmento `IsCompleted` final `true`de dados quando é definido para .</span><span class="sxs-lookup"><span data-stu-id="d3966-245">The `ReadResult` can return the final segment of data when `IsCompleted` is set to `true`.</span></span> <span data-ttu-id="d3966-246">Não ler esses dados antes de sair do loop de leitura resultará em perda de dados.</span><span class="sxs-lookup"><span data-stu-id="d3966-246">Not reading that data before exiting the read loop will result in data loss.</span></span>

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#1](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

<span data-ttu-id="d3966-247">❌**Loop infinito**</span><span class="sxs-lookup"><span data-stu-id="d3966-247">❌ **Infinite loop**</span></span>

<span data-ttu-id="d3966-248">A seguinte lógica pode resultar em `Result.IsCompleted` `true` um loop infinito se for, mas nunca há uma mensagem completa no buffer.</span><span class="sxs-lookup"><span data-stu-id="d3966-248">The following logic may result in an infinite loop if the `Result.IsCompleted` is `true` but there's never a complete message in the buffer.</span></span>

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#2](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet2)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

<span data-ttu-id="d3966-249">Aqui está outro código com o mesmo problema.</span><span class="sxs-lookup"><span data-stu-id="d3966-249">Here's another piece of code with the same problem.</span></span> <span data-ttu-id="d3966-250">Está verificando se há um buffer não `ReadResult.IsCompleted`vazio antes de verificar .</span><span class="sxs-lookup"><span data-stu-id="d3966-250">It's checking for a non-empty buffer before checking `ReadResult.IsCompleted`.</span></span> <span data-ttu-id="d3966-251">Porque ele está `else if`em um , ele vai loop para sempre se nunca há uma mensagem completa no buffer.</span><span class="sxs-lookup"><span data-stu-id="d3966-251">Because it's in an `else if`, it will loop forever if there's never a complete message in the buffer.</span></span>

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#3](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet3)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

<span data-ttu-id="d3966-252">❌**Hang inesperado**</span><span class="sxs-lookup"><span data-stu-id="d3966-252">❌ **Unexpected Hang**</span></span>

<span data-ttu-id="d3966-253">Chamar `PipeReader.AdvanceTo` incondicionalmente com `buffer.End` na `examined` posição pode resultar em travamentos ao analisar uma única mensagem.</span><span class="sxs-lookup"><span data-stu-id="d3966-253">Unconditionally calling `PipeReader.AdvanceTo` with `buffer.End` in the `examined` position may result in hangs when parsing a single message.</span></span> <span data-ttu-id="d3966-254">A próxima `PipeReader.AdvanceTo` chamada não retornará até:</span><span class="sxs-lookup"><span data-stu-id="d3966-254">The next call to `PipeReader.AdvanceTo` won't return until:</span></span>

* <span data-ttu-id="d3966-255">Há mais dados escritos no tubo.</span><span class="sxs-lookup"><span data-stu-id="d3966-255">There's more data written to the pipe.</span></span>
* <span data-ttu-id="d3966-256">E os novos dados não foram examinados anteriormente.</span><span class="sxs-lookup"><span data-stu-id="d3966-256">And the new data wasn't previously examined.</span></span>

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#4](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet4)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

<span data-ttu-id="d3966-257">❌**Fora da memória (OOM)**</span><span class="sxs-lookup"><span data-stu-id="d3966-257">❌ **Out of Memory (OOM)**</span></span>

<span data-ttu-id="d3966-258">Com as seguintes condições, o seguinte <xref:System.OutOfMemoryException> código continua a ser tamponado até que ocorra um:</span><span class="sxs-lookup"><span data-stu-id="d3966-258">With the following conditions, the following code keeps buffering until an <xref:System.OutOfMemoryException> occurs:</span></span>

* <span data-ttu-id="d3966-259">Não há tamanho máximo de mensagem.</span><span class="sxs-lookup"><span data-stu-id="d3966-259">There's no maximum message size.</span></span>
* <span data-ttu-id="d3966-260">Os dados devolvidos `PipeReader` do não fazem uma mensagem completa.</span><span class="sxs-lookup"><span data-stu-id="d3966-260">The data returned from the `PipeReader` doesn't make a complete message.</span></span> <span data-ttu-id="d3966-261">Por exemplo, ele não faz uma mensagem completa porque o outro lado está escrevendo uma mensagem grande (por exemplo, uma mensagem de 4 GB).</span><span class="sxs-lookup"><span data-stu-id="d3966-261">For example, it doesn't make a complete message because the other side is writing a large message (For example, a 4-GB message).</span></span>

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#5](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet5)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

<span data-ttu-id="d3966-262">❌**Corrupção de memória**</span><span class="sxs-lookup"><span data-stu-id="d3966-262">❌ **Memory Corruption**</span></span>

<span data-ttu-id="d3966-263">Ao escrever ajudantes que lêem o buffer, qualquer carga `Advance`de carga retornada deve ser copiada antes de ligar .</span><span class="sxs-lookup"><span data-stu-id="d3966-263">When writing helpers that read the buffer, any returned payload should be copied before calling `Advance`.</span></span> <span data-ttu-id="d3966-264">O exemplo a seguir `Pipe` retornará a memória que o tem descartado e poderá reutilizá-la para a próxima operação (ler/gravar).</span><span class="sxs-lookup"><span data-stu-id="d3966-264">The following example will return memory that the `Pipe` has discarded and may reuse it for the next operation (read/write).</span></span>

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#Message](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippetMessage)]

[!code-csharp[DoNotUse#6](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet6)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

## <a name="pipewriter"></a><span data-ttu-id="d3966-265">PipeWriter</span><span class="sxs-lookup"><span data-stu-id="d3966-265">PipeWriter</span></span>

<span data-ttu-id="d3966-266">Os <xref:System.IO.Pipelines.PipeWriter> buffers gerenciapara escrever em nome do chamador.</span><span class="sxs-lookup"><span data-stu-id="d3966-266">The <xref:System.IO.Pipelines.PipeWriter> manages buffers for writing on the caller's behalf.</span></span> <span data-ttu-id="d3966-267">`PipeWriter`implementos [`IBufferWriter<byte>`](xref:System.Buffers.IBufferWriter%601).</span><span class="sxs-lookup"><span data-stu-id="d3966-267">`PipeWriter` implements [`IBufferWriter<byte>`](xref:System.Buffers.IBufferWriter%601).</span></span> <span data-ttu-id="d3966-268">`IBufferWriter<byte>`torna possível ter acesso a buffers para executar gravações sem cópias de buffer adicionais.</span><span class="sxs-lookup"><span data-stu-id="d3966-268">`IBufferWriter<byte>` makes it possible to get access to buffers to perform writes without additional buffer copies.</span></span>

[!code-csharp[MyPipeWriter](~/samples/snippets/csharp/pipelines/MyPipeWriter.cs?name=snippet)]

<span data-ttu-id="d3966-269">O código anterior:</span><span class="sxs-lookup"><span data-stu-id="d3966-269">The previous code:</span></span>

* <span data-ttu-id="d3966-270">Solicita um buffer de pelo menos `PipeWriter` 5 <xref:System.IO.Pipelines.PipeWriter.GetMemory%2A>bytes do uso .</span><span class="sxs-lookup"><span data-stu-id="d3966-270">Requests a buffer of at least 5 bytes from the `PipeWriter` using <xref:System.IO.Pipelines.PipeWriter.GetMemory%2A>.</span></span>
* <span data-ttu-id="d3966-271">Escreve bytes para a `"Hello"` seqüência `Memory<byte>`ASCII para o retornado .</span><span class="sxs-lookup"><span data-stu-id="d3966-271">Writes bytes for the ASCII string `"Hello"` to the returned `Memory<byte>`.</span></span>
* <span data-ttu-id="d3966-272">Chamadas <xref:System.IO.Pipelines.PipeWriter.Advance%2A> para indicar quantos bytes foram escritos para o buffer.</span><span class="sxs-lookup"><span data-stu-id="d3966-272">Calls <xref:System.IO.Pipelines.PipeWriter.Advance%2A> to indicate how many bytes were written to the buffer.</span></span>
* <span data-ttu-id="d3966-273">Lava o `PipeWriter`, que envia os bytes para o dispositivo subjacente.</span><span class="sxs-lookup"><span data-stu-id="d3966-273">Flushes the `PipeWriter`, which sends the bytes to the underlying device.</span></span>

<span data-ttu-id="d3966-274">O método anterior de escrita usa os `PipeWriter`buffers fornecidos pelo .</span><span class="sxs-lookup"><span data-stu-id="d3966-274">The previous method of writing uses the buffers provided by the `PipeWriter`.</span></span> <span data-ttu-id="d3966-275">Alternativamente, <xref:System.IO.Pipelines.PipeWriter.WriteAsync%2A?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="d3966-275">Alternatively, <xref:System.IO.Pipelines.PipeWriter.WriteAsync%2A?displayProperty=nameWithType>:</span></span>

* <span data-ttu-id="d3966-276">Copia o buffer existente `PipeWriter`para o .</span><span class="sxs-lookup"><span data-stu-id="d3966-276">Copies the existing buffer to the `PipeWriter`.</span></span>
* <span data-ttu-id="d3966-277">`GetSpan`Chamadas, `Advance` conforme apropriado <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A>e chamadas.</span><span class="sxs-lookup"><span data-stu-id="d3966-277">Calls `GetSpan`, `Advance` as appropriate and calls <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A>.</span></span>

[!code-csharp[MyPipeWriter#2](~/samples/snippets/csharp/pipelines/MyPipeWriter.cs?name=snippet2)]

### <a name="cancellation"></a><span data-ttu-id="d3966-278">Cancelamento</span><span class="sxs-lookup"><span data-stu-id="d3966-278">Cancellation</span></span>

<span data-ttu-id="d3966-279"><xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A>suporta passar <xref:System.Threading.CancellationToken>um .</span><span class="sxs-lookup"><span data-stu-id="d3966-279"><xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A> supports passing a <xref:System.Threading.CancellationToken>.</span></span> <span data-ttu-id="d3966-280">Passando `CancellationToken` um resultado `OperationCanceledException` em um se o token é cancelado enquanto há um flush pendente.</span><span class="sxs-lookup"><span data-stu-id="d3966-280">Passing a `CancellationToken` results in an `OperationCanceledException` if the token is canceled while there's a flush pending.</span></span> <span data-ttu-id="d3966-281">`PipeWriter.FlushAsync`suporta uma maneira de cancelar a <xref:System.IO.Pipelines.PipeWriter.CancelPendingFlush%2A?displayProperty=nameWithType> operação de flush atual via sem levantar uma exceção.</span><span class="sxs-lookup"><span data-stu-id="d3966-281">`PipeWriter.FlushAsync` supports a way to cancel the current flush operation via <xref:System.IO.Pipelines.PipeWriter.CancelPendingFlush%2A?displayProperty=nameWithType> without raising an exception.</span></span> <span data-ttu-id="d3966-282">A `PipeWriter.CancelPendingFlush` chamada faz com `PipeWriter.FlushAsync` que `PipeWriter.WriteAsync` a <xref:System.IO.Pipelines.FlushResult> chamada `IsCanceled` atual `true`ou próxima para ou para retornar um com set para .</span><span class="sxs-lookup"><span data-stu-id="d3966-282">Calling `PipeWriter.CancelPendingFlush` causes the current or next call to `PipeWriter.FlushAsync` or `PipeWriter.WriteAsync` to return a <xref:System.IO.Pipelines.FlushResult> with `IsCanceled` set to `true`.</span></span> <span data-ttu-id="d3966-283">Isso pode ser útil para parar o flush de rendimento de uma forma não destrutiva e não excepcional.</span><span class="sxs-lookup"><span data-stu-id="d3966-283">This can be useful for halting the yielding flush in a non-destructive and non-exceptional way.</span></span>

<a name="pwcp"></a>

### <a name="pipewriter-common-problems"></a><span data-ttu-id="d3966-284">Problemas comuns do PipeWriter</span><span class="sxs-lookup"><span data-stu-id="d3966-284">PipeWriter common problems</span></span>

* <span data-ttu-id="d3966-285"><xref:System.IO.Pipelines.PipeWriter.GetSpan%2A>e <xref:System.IO.Pipelines.PipeWriter.GetMemory%2A> retornar um buffer com pelo menos a quantidade solicitada de memória.</span><span class="sxs-lookup"><span data-stu-id="d3966-285"><xref:System.IO.Pipelines.PipeWriter.GetSpan%2A> and <xref:System.IO.Pipelines.PipeWriter.GetMemory%2A> return a buffer with at least the requested amount of memory.</span></span> <span data-ttu-id="d3966-286">**Não assuma** tamanhos exatos de buffer.</span><span class="sxs-lookup"><span data-stu-id="d3966-286">**Don't** assume exact buffer sizes.</span></span>
* <span data-ttu-id="d3966-287">Não há garantia de que as chamadas sucessivas retornarão o mesmo buffer ou o buffer do mesmo tamanho.</span><span class="sxs-lookup"><span data-stu-id="d3966-287">There's no guarantee that successive calls will return the same buffer or the same-sized buffer.</span></span>
* <span data-ttu-id="d3966-288">Um novo buffer deve ser <xref:System.IO.Pipelines.PipeWriter.Advance%2A> solicitado após a chamada para continuar a escrever mais dados.</span><span class="sxs-lookup"><span data-stu-id="d3966-288">A new buffer must be requested after calling <xref:System.IO.Pipelines.PipeWriter.Advance%2A> to continue writing more data.</span></span> <span data-ttu-id="d3966-289">O buffer adquirido anteriormente não pode ser escrito para.</span><span class="sxs-lookup"><span data-stu-id="d3966-289">The previously acquired buffer can't be written to.</span></span>
* <span data-ttu-id="d3966-290">Ligar `GetMemory` `GetSpan` ou enquanto houver uma `FlushAsync` chamada incompleta não é seguro.</span><span class="sxs-lookup"><span data-stu-id="d3966-290">Calling `GetMemory` or `GetSpan` while there's an incomplete call to `FlushAsync` isn't safe.</span></span>
* <span data-ttu-id="d3966-291">Ligar `Complete` `CompleteAsync` ou enquanto houver dados não lavados pode resultar em corrupção de memória.</span><span class="sxs-lookup"><span data-stu-id="d3966-291">Calling `Complete` or `CompleteAsync` while there's unflushed data can result in memory corruption.</span></span>

## <a name="iduplexpipe"></a><span data-ttu-id="d3966-292">IDuplexPipe</span><span class="sxs-lookup"><span data-stu-id="d3966-292">IDuplexPipe</span></span>

<span data-ttu-id="d3966-293">O <xref:System.IO.Pipelines.IDuplexPipe> é um contrato para tipos que suportam tanto a leitura quanto a escrita.</span><span class="sxs-lookup"><span data-stu-id="d3966-293">The <xref:System.IO.Pipelines.IDuplexPipe> is a contract for types that support both reading and writing.</span></span> <span data-ttu-id="d3966-294">Por exemplo, uma conexão de `IDuplexPipe`rede seria representada por um .</span><span class="sxs-lookup"><span data-stu-id="d3966-294">For example, a network connection would be represented by an `IDuplexPipe`.</span></span>

 <span data-ttu-id="d3966-295">Ao `Pipe` contrário `PipeReader` do `PipeWriter`que `IDuplexPipe` contém a e a, representa um único lado de uma conexão duplex completa.</span><span class="sxs-lookup"><span data-stu-id="d3966-295">Unlike `Pipe` which contains a `PipeReader` and a `PipeWriter`, `IDuplexPipe` represents a single side of a full duplex connection.</span></span> <span data-ttu-id="d3966-296">Isso significa que o `PipeWriter` que está escrito `PipeReader`para o não será lido a partir do .</span><span class="sxs-lookup"><span data-stu-id="d3966-296">That means what is written to the `PipeWriter` will not be read from the `PipeReader`.</span></span>

## <a name="streams"></a><span data-ttu-id="d3966-297">Fluxos</span><span class="sxs-lookup"><span data-stu-id="d3966-297">Streams</span></span>

<span data-ttu-id="d3966-298">Ao ler ou escrever dados de fluxo, você normalmente lê dados usando um desserializador e escreve dados usando um serializador.</span><span class="sxs-lookup"><span data-stu-id="d3966-298">When reading or writing stream data, you typically read data using a de-serializer and write data using a serializer.</span></span> <span data-ttu-id="d3966-299">A maioria dessas APIs de `Stream` fluxo de leitura e gravação tem um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="d3966-299">Most of these read and write stream APIs have a `Stream` parameter.</span></span> <span data-ttu-id="d3966-300">Para facilitar a integração com essas `PipeReader` APIs existentes e `PipeWriter` expor uma <xref:System.IO.Pipelines.PipeReader.AsStream%2A>.</span><span class="sxs-lookup"><span data-stu-id="d3966-300">To make it easier to integrate with these existing APIs, `PipeReader` and `PipeWriter` expose an <xref:System.IO.Pipelines.PipeReader.AsStream%2A>.</span></span>  <span data-ttu-id="d3966-301"><xref:System.IO.Pipelines.PipeWriter.AsStream%2A>retorna `Stream` uma implementação em torno do `PipeReader` ou `PipeWriter`.</span><span class="sxs-lookup"><span data-stu-id="d3966-301"><xref:System.IO.Pipelines.PipeWriter.AsStream%2A> returns a `Stream` implementation around the `PipeReader` or `PipeWriter`.</span></span>
