---
title: Pipelines de e/s-.NET
description: Saiba como usar pipelines de e/s com eficiência no .NET e evitar problemas em seu código.
ms.date: 10/01/2019
ms.technology: dotnet-standard
helpviewer_keywords:
- Pipelines
- Pipelines I/O
- I/O [.NET], Pipelines
author: rick-anderson
ms.author: riande
ms.openlocfilehash: 53d7bbf214a71daff9372efcd5978f34c066c657
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319999"
---
# <a name="systemiopipelines-in-net"></a><span data-ttu-id="be457-103">System. IO. pipelines no .NET</span><span class="sxs-lookup"><span data-stu-id="be457-103">System.IO.Pipelines in .NET</span></span>

<span data-ttu-id="be457-104"><xref:System.IO.Pipelines> é uma nova biblioteca projetada para facilitar a execução de e/s de alto desempenho no .NET.</span><span class="sxs-lookup"><span data-stu-id="be457-104"><xref:System.IO.Pipelines> is a new library that is designed to make it easier to do high-performance I/O in .NET.</span></span> <span data-ttu-id="be457-105">É uma biblioteca direcionada .NET Standard que funciona em todas as implementações do .NET.</span><span class="sxs-lookup"><span data-stu-id="be457-105">It’s a library targeting .NET Standard that works on all .NET implementations.</span></span>

<a name="solve"></a>

## <a name="what-problem-does-systemiopipelines-solve"></a><span data-ttu-id="be457-106">Qual problema o System. IO. pipelines resolve</span><span class="sxs-lookup"><span data-stu-id="be457-106">What problem does System.IO.Pipelines solve</span></span>
<!-- corner case doesn't MT (machine translate)   -->
<span data-ttu-id="be457-107">Aplicativos que analisam dados de streaming são compostos por código clichê com muitos fluxos de código especializados e incomuns.</span><span class="sxs-lookup"><span data-stu-id="be457-107">Apps that parse streaming data are composed of boilerplate code having many specialized and unusual code flows.</span></span> <span data-ttu-id="be457-108">O código de caso clichê e especial é complexo e difícil de manter.</span><span class="sxs-lookup"><span data-stu-id="be457-108">The boilerplate and special case code is complex and difficult to maintain.</span></span>

<span data-ttu-id="be457-109">o `System.IO.Pipelines` foi arquitetado para:</span><span class="sxs-lookup"><span data-stu-id="be457-109">`System.IO.Pipelines` was architected to:</span></span>

* <span data-ttu-id="be457-110">Ter dados de streaming de análise de alto desempenho.</span><span class="sxs-lookup"><span data-stu-id="be457-110">Have high performance parsing streaming data.</span></span>
* <span data-ttu-id="be457-111">Reduza a complexidade do código.</span><span class="sxs-lookup"><span data-stu-id="be457-111">Reduce code complexity.</span></span>

<span data-ttu-id="be457-112">O código a seguir é típico para um servidor TCP que recebe mensagens delimitadas por linha (delimitadas por `'\n'`) de um cliente:</span><span class="sxs-lookup"><span data-stu-id="be457-112">The following code is typical for a TCP server that receives line-delimited messages (delimited by `'\n'`) from a client:</span></span>

```csharp
async Task ProcessLinesAsync(NetworkStream stream)
{
    var buffer = new byte[1024];
    await stream.ReadAsync(buffer, 0, buffer.Length);
    
    // Process a single line from the buffer
    ProcessLine(buffer);
}
```

<span data-ttu-id="be457-113">O código anterior tem vários problemas:</span><span class="sxs-lookup"><span data-stu-id="be457-113">The preceding code has several problems:</span></span>

* <span data-ttu-id="be457-114">A mensagem inteira (fim da linha) não pode ser recebida em uma única chamada para `ReadAsync`.</span><span class="sxs-lookup"><span data-stu-id="be457-114">The entire message (end of line) might not be received in a single call to `ReadAsync`.</span></span>
* <span data-ttu-id="be457-115">Ele está ignorando o resultado de `stream.ReadAsync`.</span><span class="sxs-lookup"><span data-stu-id="be457-115">It's ignoring the result of `stream.ReadAsync`.</span></span> <span data-ttu-id="be457-116">`stream.ReadAsync` retorna a quantidade de dados lidos.</span><span class="sxs-lookup"><span data-stu-id="be457-116">`stream.ReadAsync` returns how much data was read.</span></span>
* <span data-ttu-id="be457-117">Ele não manipula o caso em que várias linhas são lidas em uma única chamada `ReadAsync`.</span><span class="sxs-lookup"><span data-stu-id="be457-117">It doesn't handle the case where multiple lines are read in a single `ReadAsync` call.</span></span>
* <span data-ttu-id="be457-118">Ele aloca uma matriz `byte` com cada leitura.</span><span class="sxs-lookup"><span data-stu-id="be457-118">It allocates a `byte` array with each read.</span></span>

<span data-ttu-id="be457-119">Para corrigir os problemas anteriores, as seguintes alterações são necessárias:</span><span class="sxs-lookup"><span data-stu-id="be457-119">To fix the preceding problems, the following changes are required:</span></span>

* <span data-ttu-id="be457-120">Armazenar os dados de entrada em buffer até que uma nova linha seja encontrada.</span><span class="sxs-lookup"><span data-stu-id="be457-120">Buffer the incoming data until a new line is found.</span></span>
* <span data-ttu-id="be457-121">Analise todas as linhas retornadas no buffer.</span><span class="sxs-lookup"><span data-stu-id="be457-121">Parse all the lines returned in the buffer.</span></span>
* <span data-ttu-id="be457-122">É possível que a linha seja maior que 1 KB (1024 bytes).</span><span class="sxs-lookup"><span data-stu-id="be457-122">It's possible that the line is bigger than 1 KB (1024 bytes).</span></span> <span data-ttu-id="be457-123">O código precisa redimensionar o buffer de entrada até que o delimitador seja encontrado para ajustar a linha completa dentro do buffer.</span><span class="sxs-lookup"><span data-stu-id="be457-123">The code needs to resize the input buffer until the delimiter is found in order to fit the complete line inside the buffer.</span></span>

  * <span data-ttu-id="be457-124">Se o buffer for redimensionado, mais cópias de buffer serão feitas conforme as linhas mais longas aparecerem na entrada.</span><span class="sxs-lookup"><span data-stu-id="be457-124">If the buffer is resized, more buffer copies are made as longer lines appear in the input.</span></span>
  * <span data-ttu-id="be457-125">Para reduzir o espaço desperdiçado, compacte o buffer usado para ler as linhas.</span><span class="sxs-lookup"><span data-stu-id="be457-125">To reduce wasted space, compact the buffer used for reading lines.</span></span>

* <span data-ttu-id="be457-126">Considere o uso do pool de buffers para evitar a alocação repetida de memória.</span><span class="sxs-lookup"><span data-stu-id="be457-126">Consider using buffer pooling to avoid allocating memory repeatedly.</span></span>
* <span data-ttu-id="be457-127">O código a seguir aborda alguns desses problemas:</span><span class="sxs-lookup"><span data-stu-id="be457-127">The following code addresses some of these problems:</span></span>

[!code-csharp[](~/samples/snippets/csharp/pipelines/ProcessLinesAsync.cs?name=snippet)]

<span data-ttu-id="be457-128">O código anterior é complexo e não aborda todos os problemas identificados.</span><span class="sxs-lookup"><span data-stu-id="be457-128">The previous code is complex and doesn't address all the problems identified.</span></span> <span data-ttu-id="be457-129">A rede de alto desempenho geralmente significa escrever código muito complexo para maximizar o desempenho.</span><span class="sxs-lookup"><span data-stu-id="be457-129">High-performance networking usually means writing very complex code to maximize performance.</span></span> <span data-ttu-id="be457-130">o `System.IO.Pipelines` foi criado para facilitar a gravação desse tipo de código.</span><span class="sxs-lookup"><span data-stu-id="be457-130">`System.IO.Pipelines` was designed to make writing this type of code easier.</span></span>

## <a name="pipe"></a><span data-ttu-id="be457-131">Conexão</span><span class="sxs-lookup"><span data-stu-id="be457-131">Pipe</span></span>

<span data-ttu-id="be457-132">A classe <xref:System.IO.Pipelines.Pipe> pode ser usada para criar um par de `PipeWriter/PipeReader`.</span><span class="sxs-lookup"><span data-stu-id="be457-132">The <xref:System.IO.Pipelines.Pipe> class can be used to create a `PipeWriter/PipeReader` pair.</span></span> <span data-ttu-id="be457-133">Todos os dados gravados no `PipeWriter` estão disponíveis no `PipeReader`:</span><span class="sxs-lookup"><span data-stu-id="be457-133">All data written into the `PipeWriter` is available in the `PipeReader`:</span></span>

[!code-csharp[](~/samples/snippets/csharp/pipelines/Pipe.cs?name=snippet2)]

<a name="pbu"></a>

### <a name="pipe-basic-usage"></a><span data-ttu-id="be457-134">Uso básico do pipe</span><span class="sxs-lookup"><span data-stu-id="be457-134">Pipe basic usage</span></span>

[!code-csharp[](~/samples/snippets/csharp/pipelines/Pipe.cs?name=snippet)]

<span data-ttu-id="be457-135">Há dois loops:</span><span class="sxs-lookup"><span data-stu-id="be457-135">There are two loops:</span></span>

* <span data-ttu-id="be457-136">`FillPipeAsync` lê do `Socket` e grava no `PipeWriter`.</span><span class="sxs-lookup"><span data-stu-id="be457-136">`FillPipeAsync` reads from the `Socket` and writes to the `PipeWriter`.</span></span>
* <span data-ttu-id="be457-137">`ReadPipeAsync` lê do `PipeReader` e analisa as linhas de entrada.</span><span class="sxs-lookup"><span data-stu-id="be457-137">`ReadPipeAsync` reads from the `PipeReader` and parses incoming lines.</span></span>

<span data-ttu-id="be457-138">Não há buffers explícitos alocados.</span><span class="sxs-lookup"><span data-stu-id="be457-138">There are no explicit buffers allocated.</span></span> <span data-ttu-id="be457-139">Todo o gerenciamento de buffer é delegado para as implementações `PipeReader` e `PipeWriter`.</span><span class="sxs-lookup"><span data-stu-id="be457-139">All buffer management is delegated to the `PipeReader` and `PipeWriter` implementations.</span></span> <span data-ttu-id="be457-140">A delegação do gerenciamento de buffer facilita o consumo do código para se concentrar exclusivamente na lógica de negócios.</span><span class="sxs-lookup"><span data-stu-id="be457-140">Delegating buffer management makes it easier for consuming code to focus solely on the business logic.</span></span>

<span data-ttu-id="be457-141">No primeiro loop:</span><span class="sxs-lookup"><span data-stu-id="be457-141">In the first loop:</span></span>

* <span data-ttu-id="be457-142"><xref:System.IO.Pipelines.PipeWriter.GetMemory(System.Int32)?displayProperty=nameWithType> é chamado para obter memória do gravador subjacente.</span><span class="sxs-lookup"><span data-stu-id="be457-142"><xref:System.IO.Pipelines.PipeWriter.GetMemory(System.Int32)?displayProperty=nameWithType> is called to get memory from the underlying writer.</span></span>
* <span data-ttu-id="be457-143"><xref:System.IO.Pipelines.PipeWriter.Advance(System.Int32)?displayProperty=nameWithType> é chamado para informar ao `PipeWriter` a quantidade de dados gravada no buffer.</span><span class="sxs-lookup"><span data-stu-id="be457-143"><xref:System.IO.Pipelines.PipeWriter.Advance(System.Int32)?displayProperty=nameWithType> is called to tell the `PipeWriter` how much data was written to the buffer.</span></span>
* <span data-ttu-id="be457-144"><xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A?displayProperty=nameWithType> é chamado para disponibilizar os dados para o `PipeReader`.</span><span class="sxs-lookup"><span data-stu-id="be457-144"><xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A?displayProperty=nameWithType> is called to make the data available to the `PipeReader`.</span></span>

<span data-ttu-id="be457-145">No segundo loop, o `PipeReader` consome os buffers gravados por `PipeWriter`.</span><span class="sxs-lookup"><span data-stu-id="be457-145">In the second loop, the `PipeReader` consumes the buffers written by `PipeWriter`.</span></span> <span data-ttu-id="be457-146">Os buffers são provenientes do soquete.</span><span class="sxs-lookup"><span data-stu-id="be457-146">The buffers come from the socket.</span></span> <span data-ttu-id="be457-147">A chamada para `PipeReader.ReadAsync`:</span><span class="sxs-lookup"><span data-stu-id="be457-147">The call to `PipeReader.ReadAsync`:</span></span>

* <span data-ttu-id="be457-148">Retorna um <xref:System.IO.Pipelines.ReadResult> que contém duas partes importantes de informações:</span><span class="sxs-lookup"><span data-stu-id="be457-148">Returns a <xref:System.IO.Pipelines.ReadResult> that contains two important pieces of information:</span></span>

  * <span data-ttu-id="be457-149">Os dados que foram lidos na forma de `ReadOnlySequence<byte>`.</span><span class="sxs-lookup"><span data-stu-id="be457-149">The data that was read in the form of `ReadOnlySequence<byte>`.</span></span>
  * <span data-ttu-id="be457-150">Um booliano `IsCompleted` que indica se o fim dos dados (EOF) foi atingido.</span><span class="sxs-lookup"><span data-stu-id="be457-150">A boolean `IsCompleted` that indicates if the end of data (EOF) has been reached.</span></span> 

<span data-ttu-id="be457-151">Depois de encontrar o delimitador de fim de linha (EOL) e analisar a linha:</span><span class="sxs-lookup"><span data-stu-id="be457-151">After finding the end of line (EOL) delimiter and parsing the line:</span></span>

* <span data-ttu-id="be457-152">A lógica processa o buffer para ignorar o que já foi processado.</span><span class="sxs-lookup"><span data-stu-id="be457-152">The logic processes the buffer to skip what's already processed.</span></span>
* <span data-ttu-id="be457-153">`PipeReader.AdvanceTo` é chamado para informar ao `PipeReader` a quantidade de dados consumida e examinada.</span><span class="sxs-lookup"><span data-stu-id="be457-153">`PipeReader.AdvanceTo` is called to tell the `PipeReader` how much data has been consumed and examined.</span></span>

<span data-ttu-id="be457-154">Os loops de leitor e gravador terminam chamando `Complete`.</span><span class="sxs-lookup"><span data-stu-id="be457-154">The reader and writer loops end by calling `Complete`.</span></span> <span data-ttu-id="be457-155">`Complete` permite que o pipe subjacente libere a memória alocada.</span><span class="sxs-lookup"><span data-stu-id="be457-155">`Complete` lets the underlying Pipe release the memory it allocated.</span></span>

### <a name="backpressure-and-flow-control"></a><span data-ttu-id="be457-156">Controle de fluxo e de pressão</span><span class="sxs-lookup"><span data-stu-id="be457-156">Backpressure and flow control</span></span>

<span data-ttu-id="be457-157">Idealmente, a leitura e a análise funcionam em conjunto:</span><span class="sxs-lookup"><span data-stu-id="be457-157">Ideally, reading and parsing work together:</span></span>

* <span data-ttu-id="be457-158">O thread de gravação consome dados da rede e os coloca em buffers.</span><span class="sxs-lookup"><span data-stu-id="be457-158">The writing thread consumes data from the network and puts it in buffers.</span></span>
* <span data-ttu-id="be457-159">O thread de análise é responsável por construir as estruturas de dados apropriadas.</span><span class="sxs-lookup"><span data-stu-id="be457-159">The parsing thread is responsible for constructing the appropriate data structures.</span></span>

<span data-ttu-id="be457-160">Normalmente, a análise leva mais tempo do que apenas copiar blocos de dados da rede:</span><span class="sxs-lookup"><span data-stu-id="be457-160">Typically, parsing takes more time than just copying blocks of data from the network:</span></span>

* <span data-ttu-id="be457-161">O thread de leitura fica à frente do thread de análise.</span><span class="sxs-lookup"><span data-stu-id="be457-161">The reading thread gets ahead of the parsing thread.</span></span>
* <span data-ttu-id="be457-162">O thread de leitura precisa diminuir ou alocar mais memória para armazenar os dados para o thread de análise.</span><span class="sxs-lookup"><span data-stu-id="be457-162">The reading thread has to either slow down or allocate more memory to store the data for the parsing thread.</span></span>

<span data-ttu-id="be457-163">Para um desempenho ideal, há um equilíbrio entre pausas frequentes e alocação de mais memória.</span><span class="sxs-lookup"><span data-stu-id="be457-163">For optimal performance, there's a balance between frequent pauses and allocating more memory.</span></span>

<span data-ttu-id="be457-164">Para resolver o problema anterior, o `Pipe` tem duas configurações para controlar o fluxo de dados:</span><span class="sxs-lookup"><span data-stu-id="be457-164">To solve the preceding problem, the `Pipe` has two settings to control the flow of data:</span></span>

* <span data-ttu-id="be457-165"><xref:System.IO.Pipelines.PipeOptions.PauseWriterThreshold>: determina a quantidade de dados que deve ser armazenada em buffer antes de chamadas para <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A> pausa.</span><span class="sxs-lookup"><span data-stu-id="be457-165"><xref:System.IO.Pipelines.PipeOptions.PauseWriterThreshold>: Determines how much data should be buffered before calls to <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A> pause.</span></span>
* <span data-ttu-id="be457-166"><xref:System.IO.Pipelines.PipeOptions.ResumeWriterThreshold>: determina a quantidade de dados que o leitor deve observar antes de chamadas para a retomada de `PipeWriter.FlushAsync`.</span><span class="sxs-lookup"><span data-stu-id="be457-166"><xref:System.IO.Pipelines.PipeOptions.ResumeWriterThreshold>: Determines how much data the reader has to observe before calls to `PipeWriter.FlushAsync` resume.</span></span>

![Diagrama com ResumeWriterThreshold e PauseWriterThreshold](./media/pipelines/resume-pause.png)

<span data-ttu-id="be457-168"><xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="be457-168"><xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A?displayProperty=nameWithType>:</span></span>

* <span data-ttu-id="be457-169">Retorna um `ValueTask<FlushResult>` incompleto quando a quantidade de dados no `Pipe` cruza `PauseWriterThreshold`.</span><span class="sxs-lookup"><span data-stu-id="be457-169">Returns an incomplete `ValueTask<FlushResult>` when the amount of data in the `Pipe` crosses `PauseWriterThreshold`.</span></span>
* <span data-ttu-id="be457-170">Conclui `ValueTask<FlushResult>` quando se torna inferior a `ResumeWriterThreshold`.</span><span class="sxs-lookup"><span data-stu-id="be457-170">Completes `ValueTask<FlushResult>` when it becomes lower than `ResumeWriterThreshold`.</span></span>

<span data-ttu-id="be457-171">Dois valores são usados para evitar o ciclo rápido, que pode ocorrer se um valor for usado.</span><span class="sxs-lookup"><span data-stu-id="be457-171">Two values are used to prevent rapid cycling, which can occur if one value is used.</span></span>

### <a name="examples"></a><span data-ttu-id="be457-172">Exemplos</span><span class="sxs-lookup"><span data-stu-id="be457-172">Examples</span></span>

```csharp
// The Pipe will start returning incomplete tasks from FlushAsync until
// the reader examines at least 5 bytes.
var options = new PipeOptions(pauseWriterThreshold: 10, resumeWriterThreshold: 5);
var pipe = new Pipe(options);
```

### <a name="pipescheduler"></a><span data-ttu-id="be457-173">PipeScheduler</span><span class="sxs-lookup"><span data-stu-id="be457-173">PipeScheduler</span></span>

<span data-ttu-id="be457-174">Normalmente, ao usar `async` e `await`, o código assíncrono é retomado em um <xref:System.Threading.Tasks.TaskScheduler> ou no <xref:System.Threading.SynchronizationContext> atual.</span><span class="sxs-lookup"><span data-stu-id="be457-174">Typically when using `async` and `await`, asynchronous code resumes on either on a <xref:System.Threading.Tasks.TaskScheduler> or on the current  <xref:System.Threading.SynchronizationContext>.</span></span>

<span data-ttu-id="be457-175">Ao fazer e/s, é importante ter um controle refinado sobre onde a e/s é executada.</span><span class="sxs-lookup"><span data-stu-id="be457-175">When doing I/O, it's important to have fine-grained control over where the I/O is performed.</span></span> <span data-ttu-id="be457-176">Esse controle permite aproveitar os caches de CPU com eficiência.</span><span class="sxs-lookup"><span data-stu-id="be457-176">This control allows taking advantage of CPU caches effectively.</span></span> <span data-ttu-id="be457-177">O cache eficiente é essencial para aplicativos de alto desempenho, como servidores Web.</span><span class="sxs-lookup"><span data-stu-id="be457-177">Efficient caching is critical for high-performance apps like web servers.</span></span> <span data-ttu-id="be457-178"><xref:System.IO.Pipelines.PipeScheduler> fornece controle sobre o local em que os retornos de chamada assíncronos são executados.</span><span class="sxs-lookup"><span data-stu-id="be457-178"><xref:System.IO.Pipelines.PipeScheduler> provides control over where asynchronous callbacks run.</span></span> <span data-ttu-id="be457-179">Por padrão:</span><span class="sxs-lookup"><span data-stu-id="be457-179">By default:</span></span>

* <span data-ttu-id="be457-180">O <xref:System.Threading.SynchronizationContext> atual é usado.</span><span class="sxs-lookup"><span data-stu-id="be457-180">The current <xref:System.Threading.SynchronizationContext> is used.</span></span>
* <span data-ttu-id="be457-181">Se não houver `SynchronizationContext`, ele usará o pool de threads para executar retornos de chamada.</span><span class="sxs-lookup"><span data-stu-id="be457-181">If there's no `SynchronizationContext`, it uses the thread pool to run callbacks.</span></span>

[!code-csharp[](~/samples/snippets/csharp/pipelines/Program.cs?name=snippet)]

<span data-ttu-id="be457-182">[PipeScheduler. ThreadPool](xref:System.IO.Pipelines.PipeScheduler.ThreadPool) é a implementação <xref:System.IO.Pipelines.PipeScheduler> que enfileira os retornos de chamada para o pool de threads.</span><span class="sxs-lookup"><span data-stu-id="be457-182">[PipeScheduler.ThreadPool](xref:System.IO.Pipelines.PipeScheduler.ThreadPool) is the <xref:System.IO.Pipelines.PipeScheduler> implementation that queues callbacks to the thread pool.</span></span> <span data-ttu-id="be457-183">`PipeScheduler.ThreadPool` é o padrão e geralmente é a melhor opção.</span><span class="sxs-lookup"><span data-stu-id="be457-183">`PipeScheduler.ThreadPool` is the default and generally the best choice.</span></span> <span data-ttu-id="be457-184">[PipeScheduler. Inline](xref:System.IO.Pipelines.PipeScheduler.Inline) pode causar consequências indesejadas, como deadlocks.</span><span class="sxs-lookup"><span data-stu-id="be457-184">[PipeScheduler.Inline](xref:System.IO.Pipelines.PipeScheduler.Inline) can cause unintended consequences such as deadlocks.</span></span>

### <a name="pipe-reset"></a><span data-ttu-id="be457-185">Redefinição de pipe</span><span class="sxs-lookup"><span data-stu-id="be457-185">Pipe reset</span></span>

<span data-ttu-id="be457-186">Com frequência, é eficiente reutilizar o objeto `Pipe`.</span><span class="sxs-lookup"><span data-stu-id="be457-186">It's frequently efficient to reuse the `Pipe` object.</span></span> <span data-ttu-id="be457-187">Para redefinir o pipe, chame <xref:System.IO.Pipelines.PipeReader> <xref:System.IO.Pipelines.Pipe.Reset%2A> quando o `PipeReader` e `PipeWriter` estiverem concluídos.</span><span class="sxs-lookup"><span data-stu-id="be457-187">To reset the pipe, call <xref:System.IO.Pipelines.PipeReader> <xref:System.IO.Pipelines.Pipe.Reset%2A> when both the `PipeReader` and `PipeWriter` are complete.</span></span>

## <a name="pipereader"></a><span data-ttu-id="be457-188">PipeReader</span><span class="sxs-lookup"><span data-stu-id="be457-188">PipeReader</span></span>

<span data-ttu-id="be457-189"><xref:System.IO.Pipelines.PipeReader> gerencia a memória em nome do chamador.</span><span class="sxs-lookup"><span data-stu-id="be457-189"><xref:System.IO.Pipelines.PipeReader> manages memory on the caller's behalf.</span></span> <span data-ttu-id="be457-190">**Sempre** chame <xref:System.IO.Pipelines.PipeReader.AdvanceTo%2A?displayProperty=nameWithType> depois de chamar <xref:System.IO.Pipelines.PipeReader.ReadAsync%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="be457-190">**Always** call <xref:System.IO.Pipelines.PipeReader.AdvanceTo%2A?displayProperty=nameWithType> after calling <xref:System.IO.Pipelines.PipeReader.ReadAsync%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="be457-191">Isso permite que o `PipeReader` saiba quando o chamador é concluído com a memória para que possa ser acompanhado.</span><span class="sxs-lookup"><span data-stu-id="be457-191">This lets the `PipeReader` know when the caller is done with the memory so that it can be tracked.</span></span> <span data-ttu-id="be457-192">O `ReadOnlySequence<byte>` retornado de `PipeReader.ReadAsync` é válido somente até que a chamada seja a `PipeReader.AdvanceTo`.</span><span class="sxs-lookup"><span data-stu-id="be457-192">The `ReadOnlySequence<byte>` returned from `PipeReader.ReadAsync` is only valid until the call the `PipeReader.AdvanceTo`.</span></span> <span data-ttu-id="be457-193">É ilegal usar `ReadOnlySequence<byte>` depois de chamar `PipeReader.AdvanceTo`.</span><span class="sxs-lookup"><span data-stu-id="be457-193">It's illegal to use `ReadOnlySequence<byte>` after calling `PipeReader.AdvanceTo`.</span></span>

<span data-ttu-id="be457-194">`PipeReader.AdvanceTo` usa dois argumentos <xref:System.SequencePosition>:</span><span class="sxs-lookup"><span data-stu-id="be457-194">`PipeReader.AdvanceTo` takes two <xref:System.SequencePosition> arguments:</span></span>

* <span data-ttu-id="be457-195">O primeiro argumento determina a quantidade de memória consumida.</span><span class="sxs-lookup"><span data-stu-id="be457-195">The first argument determines how much memory was consumed.</span></span>
* <span data-ttu-id="be457-196">O segundo argumento determina o quanto do buffer foi observado.</span><span class="sxs-lookup"><span data-stu-id="be457-196">The second argument determines how much of the buffer was observed.</span></span>

<span data-ttu-id="be457-197">Marcar dados como consumidos significa que o pipe pode retornar a memória para o pool de buffers subjacente.</span><span class="sxs-lookup"><span data-stu-id="be457-197">Marking data as consumed means that the pipe can return the memory to the underlying buffer pool.</span></span> <span data-ttu-id="be457-198">Marcar dados como observados controla o que a próxima chamada para `PipeReader.ReadAsync` faz.</span><span class="sxs-lookup"><span data-stu-id="be457-198">Marking data as observed controls what the next call to `PipeReader.ReadAsync` does.</span></span> <span data-ttu-id="be457-199">Marcar tudo como observado significa que a próxima chamada para `PipeReader.ReadAsync` não retornará até que haja mais dados gravados no pipe.</span><span class="sxs-lookup"><span data-stu-id="be457-199">Marking everything as observed means that the next call to `PipeReader.ReadAsync` won't return until there's more data written to the pipe.</span></span> <span data-ttu-id="be457-200">Qualquer outro valor fará com que a próxima chamada para `PipeReader.ReadAsync` retorne imediatamente com os dados observados *e* não observados, mas os dados que já foram consumidos.</span><span class="sxs-lookup"><span data-stu-id="be457-200">Any other value will make the next call to `PipeReader.ReadAsync` return immediately with the observed *and* unobserved data, but data that has already been consumed.</span></span>

### <a name="read-streaming-data-scenarios"></a><span data-ttu-id="be457-201">Ler cenários de dados de streaming</span><span class="sxs-lookup"><span data-stu-id="be457-201">Read streaming data scenarios</span></span>

<span data-ttu-id="be457-202">Há alguns padrões típicos que surgem ao tentar ler dados de streaming:</span><span class="sxs-lookup"><span data-stu-id="be457-202">There are a couple of typical patterns that emerge when trying to read streaming data:</span></span>

* <span data-ttu-id="be457-203">Dado um fluxo de dados, analise uma única mensagem.</span><span class="sxs-lookup"><span data-stu-id="be457-203">Given a stream of data, parse a single message.</span></span>
* <span data-ttu-id="be457-204">Dado um fluxo de dados, analise todas as mensagens disponíveis.</span><span class="sxs-lookup"><span data-stu-id="be457-204">Given a stream of data, parse all available messages.</span></span>

<span data-ttu-id="be457-205">Os exemplos a seguir usam o método `TryParseMessage` para analisar mensagens de um `ReadOnlySequence<byte>`.</span><span class="sxs-lookup"><span data-stu-id="be457-205">The following examples use the `TryParseMessage` method for parsing messages from a `ReadOnlySequence<byte>`.</span></span> <span data-ttu-id="be457-206">`TryParseMessage` analisa uma única mensagem e atualiza o buffer de entrada para cortar a mensagem analisada do buffer.</span><span class="sxs-lookup"><span data-stu-id="be457-206">`TryParseMessage` parses a single message and update the input buffer to trim the parsed message from the buffer.</span></span> <span data-ttu-id="be457-207">`TryParseMessage` não faz parte do .NET, é um método escrito pelo usuário usado nas seções a seguir.</span><span class="sxs-lookup"><span data-stu-id="be457-207">`TryParseMessage` is not part of .NET, it's a user written method used in the following sections.</span></span>

```csharp
bool TryParseMessage(ref ReadOnlySequence<byte> buffer, out Message message);
```

### <a name="read-a-single-message"></a><span data-ttu-id="be457-208">Ler uma única mensagem</span><span class="sxs-lookup"><span data-stu-id="be457-208">Read a single message</span></span>

<span data-ttu-id="be457-209">O código a seguir lê uma única mensagem de um `PipeReader` e a retorna ao chamador.</span><span class="sxs-lookup"><span data-stu-id="be457-209">The following code reads a single message from a `PipeReader` and returns it to the caller.</span></span>

[!code-csharp[ReadSingleMsg](~/samples/snippets/csharp/pipelines/ReadSingleMsg.cs?name=snippet)]

<span data-ttu-id="be457-210">O código anterior:</span><span class="sxs-lookup"><span data-stu-id="be457-210">The preceding code:</span></span>

* <span data-ttu-id="be457-211">Analisa uma única mensagem.</span><span class="sxs-lookup"><span data-stu-id="be457-211">Parses a single message.</span></span>
* <span data-ttu-id="be457-212">Atualiza o `SequencePosition` consumido e examinado `SequencePosition` para apontar para o início do buffer de entrada cortado.</span><span class="sxs-lookup"><span data-stu-id="be457-212">Updates the consumed `SequencePosition` and examined `SequencePosition` to point to the start of the trimmed input buffer.</span></span>

<span data-ttu-id="be457-213">Os dois argumentos `SequencePosition` são atualizados porque `TryParseMessage` remove a mensagem analisada do buffer de entrada.</span><span class="sxs-lookup"><span data-stu-id="be457-213">The two `SequencePosition` arguments are updated because `TryParseMessage` removes the parsed message from the input buffer.</span></span> <span data-ttu-id="be457-214">Geralmente, ao analisar uma única mensagem do buffer, a posição examinada deve ser uma das seguintes:</span><span class="sxs-lookup"><span data-stu-id="be457-214">Generally, when parsing a single message from the buffer, the examined position should be one of the following:</span></span>

* <span data-ttu-id="be457-215">O fim da mensagem.</span><span class="sxs-lookup"><span data-stu-id="be457-215">The end of the message.</span></span>
* <span data-ttu-id="be457-216">O final do buffer recebido se nenhuma mensagem for encontrada.</span><span class="sxs-lookup"><span data-stu-id="be457-216">The end of the received buffer if no message was found.</span></span>

<span data-ttu-id="be457-217">O caso de mensagem única tem o maior potencial para erros.</span><span class="sxs-lookup"><span data-stu-id="be457-217">The single message case has the most potential for errors.</span></span> <span data-ttu-id="be457-218">Passar os valores incorretos para *examinados* pode resultar em uma exceção de memória insuficiente ou um loop infinito.</span><span class="sxs-lookup"><span data-stu-id="be457-218">Passing the wrong values to *examined* can result in an out of memory exception or an infinite loop.</span></span> <span data-ttu-id="be457-219">Para obter mais informações, consulte a seção [problemas comuns do PipeReader](#gotchas) neste artigo.</span><span class="sxs-lookup"><span data-stu-id="be457-219">For more information, see the [PipeReader common problems](#gotchas) section in this article.</span></span>

### <a name="reading-multiple-messages"></a><span data-ttu-id="be457-220">Lendo várias mensagens</span><span class="sxs-lookup"><span data-stu-id="be457-220">Reading multiple messages</span></span>

<span data-ttu-id="be457-221">O código a seguir lê todas as mensagens de um `PipeReader` e chama `ProcessMessageAsync` em cada.</span><span class="sxs-lookup"><span data-stu-id="be457-221">The following code reads all messages from a `PipeReader` and calls `ProcessMessageAsync` on each.</span></span>

[!code-csharp[MyConnection1](~/samples/snippets/csharp/pipelines/MyConnection1.cs?name=snippet)]

### <a name="cancellation"></a><span data-ttu-id="be457-222">Cancelamento</span><span class="sxs-lookup"><span data-stu-id="be457-222">Cancellation</span></span>

<span data-ttu-id="be457-223">`PipeReader.ReadAsync`:</span><span class="sxs-lookup"><span data-stu-id="be457-223">`PipeReader.ReadAsync`:</span></span>

* <span data-ttu-id="be457-224">Dá suporte à passagem de um <xref:System.Threading.CancellationToken>.</span><span class="sxs-lookup"><span data-stu-id="be457-224">Supports passing a <xref:System.Threading.CancellationToken>.</span></span>
* <span data-ttu-id="be457-225">Gera um <xref:System.OperationCanceledException> se o `CancellationToken` for cancelado enquanto houver uma leitura pendente.</span><span class="sxs-lookup"><span data-stu-id="be457-225">Throws an <xref:System.OperationCanceledException> if the `CancellationToken` is canceled while there's a read pending.</span></span>
* <span data-ttu-id="be457-226">Dá suporte a uma maneira de cancelar a operação de leitura atual por meio de <xref:System.IO.Pipelines.PipeReader.CancelPendingRead%2A?displayProperty=nameWithType>, o que evita a geração de uma exceção.</span><span class="sxs-lookup"><span data-stu-id="be457-226">Supports a way to cancel the current read operation via <xref:System.IO.Pipelines.PipeReader.CancelPendingRead%2A?displayProperty=nameWithType>, which avoids raising an exception.</span></span> <span data-ttu-id="be457-227">Chamar `PipeReader.CancelPendingRead` faz com que a chamada atual ou próxima para `PipeReader.ReadAsync` retorne um <xref:System.IO.Pipelines.ReadResult> com `IsCanceled` definido como `true`.</span><span class="sxs-lookup"><span data-stu-id="be457-227">Calling `PipeReader.CancelPendingRead` causes the current or next call to `PipeReader.ReadAsync` to return a <xref:System.IO.Pipelines.ReadResult> with `IsCanceled` set to `true`.</span></span> <span data-ttu-id="be457-228">Isso pode ser útil para interromper o loop de leitura existente de forma não destrutiva e não excepcional.</span><span class="sxs-lookup"><span data-stu-id="be457-228">This can be useful for halting the existing read loop in a non-destructive and non-exceptional way.</span></span>

[!code-csharp[MyConnection](~/samples/snippets/csharp/pipelines/MyConnection.cs?name=snippet)]

<a name="gotchas"></a>

### <a name="pipereader-common-problems"></a><span data-ttu-id="be457-229">Problemas comuns do PipeReader</span><span class="sxs-lookup"><span data-stu-id="be457-229">PipeReader common problems</span></span>

* <span data-ttu-id="be457-230">Passar os valores errados para `consumed` ou `examined` pode resultar na leitura de dados já lidos.</span><span class="sxs-lookup"><span data-stu-id="be457-230">Passing the wrong values to `consumed` or `examined` may result in reading already read data.</span></span>
* <span data-ttu-id="be457-231">Passar `buffer.End` como examinado pode resultar em:</span><span class="sxs-lookup"><span data-stu-id="be457-231">Passing `buffer.End` as examined may result in:</span></span>

  * <span data-ttu-id="be457-232">Dados interrompidos</span><span class="sxs-lookup"><span data-stu-id="be457-232">Stalled data</span></span>
  * <span data-ttu-id="be457-233">Possivelmente uma exceção de memória insuficiente (OOM) se os dados não forem consumidos.</span><span class="sxs-lookup"><span data-stu-id="be457-233">Possibly an eventual Out of Memory (OOM) exception if data isn't consumed.</span></span> <span data-ttu-id="be457-234">Por exemplo, `PipeReader.AdvanceTo(position, buffer.End)` ao processar uma única mensagem por vez do buffer.</span><span class="sxs-lookup"><span data-stu-id="be457-234">For example, `PipeReader.AdvanceTo(position, buffer.End)` when processing a single message at a time from the buffer.</span></span>

* <span data-ttu-id="be457-235">Passar os valores errados para `consumed` ou `examined` pode resultar em um loop infinito.</span><span class="sxs-lookup"><span data-stu-id="be457-235">Passing the wrong values to `consumed` or `examined` may result in an infinite loop.</span></span> <span data-ttu-id="be457-236">Por exemplo, `PipeReader.AdvanceTo(buffer.Start)` se `buffer.Start` não for alterado fará com que a próxima chamada para `PipeReader.ReadAsync` seja retornada imediatamente antes que novos dados cheguem.</span><span class="sxs-lookup"><span data-stu-id="be457-236">For example, `PipeReader.AdvanceTo(buffer.Start)` if `buffer.Start` hasn't changed will cause the next call to `PipeReader.ReadAsync` to return immediately before new data arrives.</span></span>
* <span data-ttu-id="be457-237">Passar os valores errados para `consumed` ou `examined` pode resultar em buffer infinito (OOM eventual).</span><span class="sxs-lookup"><span data-stu-id="be457-237">Passing the wrong values to `consumed` or `examined` may result in infinite buffering (eventual OOM).</span></span>
* <span data-ttu-id="be457-238">Usar o `ReadOnlySequence<byte>` após chamar `PipeReader.AdvanceTo` pode resultar em corrupção de memória (use depois de gratuito).</span><span class="sxs-lookup"><span data-stu-id="be457-238">Using the `ReadOnlySequence<byte>` after calling `PipeReader.AdvanceTo` may result in memory corruption (use after free).</span></span>
* <span data-ttu-id="be457-239">A falha ao chamar `PipeReader.Complete/CompleteAsync` pode resultar em um vazamento de memória.</span><span class="sxs-lookup"><span data-stu-id="be457-239">Failing to call `PipeReader.Complete/CompleteAsync` may result in a memory leak.</span></span>
* <span data-ttu-id="be457-240">Verificar <xref:System.IO.Pipelines.ReadResult.IsCompleted?displayProperty=nameWithType> e sair da lógica de leitura antes de processar o buffer resulta em perda de dados.</span><span class="sxs-lookup"><span data-stu-id="be457-240">Checking <xref:System.IO.Pipelines.ReadResult.IsCompleted?displayProperty=nameWithType> and exiting the reading logic before processing the buffer results in data loss.</span></span> <span data-ttu-id="be457-241">A condição de saída do loop deve ser baseada em `ReadResult.Buffer.IsEmpty` e `ReadResult.IsCompleted`.</span><span class="sxs-lookup"><span data-stu-id="be457-241">The loop exit condition should be based on `ReadResult.Buffer.IsEmpty` and `ReadResult.IsCompleted`.</span></span> <span data-ttu-id="be457-242">Fazer isso incorretamente pode resultar em um loop infinito.</span><span class="sxs-lookup"><span data-stu-id="be457-242">Doing this incorrectly could result in an infinite loop.</span></span>

#### <a name="problematic-code"></a><span data-ttu-id="be457-243">Código problemático</span><span class="sxs-lookup"><span data-stu-id="be457-243">Problematic code</span></span>

<span data-ttu-id="be457-244">**perda de dados** de ❌</span><span class="sxs-lookup"><span data-stu-id="be457-244">❌ **Data loss**</span></span>

<span data-ttu-id="be457-245">O `ReadResult` pode retornar o segmento final de dados quando `IsCompleted` é definido como `true`.</span><span class="sxs-lookup"><span data-stu-id="be457-245">The `ReadResult` can return the final segment of data when `IsCompleted` is set to `true`.</span></span> <span data-ttu-id="be457-246">Não ler os dados antes de sair do loop de leitura resultará em perda de dados.</span><span class="sxs-lookup"><span data-stu-id="be457-246">Not reading that data before exiting the read loop will result in data loss.</span></span>

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#1](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

<span data-ttu-id="be457-247">**loop infinito** ❌</span><span class="sxs-lookup"><span data-stu-id="be457-247">❌ **Infinite loop**</span></span>

<span data-ttu-id="be457-248">A lógica a seguir pode resultar em um loop infinito se o `Result.IsCompleted` for `true`, mas nunca houver uma mensagem completa no buffer.</span><span class="sxs-lookup"><span data-stu-id="be457-248">The following logic may result in an infinite loop if the `Result.IsCompleted` is `true` but there's never a complete message in the buffer.</span></span>

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#2](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet2)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

<span data-ttu-id="be457-249">Aqui está outra parte do código com o mesmo problema.</span><span class="sxs-lookup"><span data-stu-id="be457-249">Here's another piece of code with the same problem.</span></span> <span data-ttu-id="be457-250">Ele está verificando um buffer não vazio antes de verificar `ReadResult.IsCompleted`.</span><span class="sxs-lookup"><span data-stu-id="be457-250">It's checking for a non-empty buffer before checking `ReadResult.IsCompleted`.</span></span> <span data-ttu-id="be457-251">Como está em um `else if`, ele entrará em loop para sempre se nunca houver uma mensagem completa no buffer.</span><span class="sxs-lookup"><span data-stu-id="be457-251">Because it's in an `else if`, it will loop forever if there's never a complete message in the buffer.</span></span>

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#3](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet3)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

<span data-ttu-id="be457-252">❌ **falha inesperada**</span><span class="sxs-lookup"><span data-stu-id="be457-252">❌ **Unexpected Hang**</span></span>

<span data-ttu-id="be457-253">Chamar incondicionalmente `PipeReader.AdvanceTo` com `buffer.End` na posição `examined` pode resultar em travas ao analisar uma única mensagem.</span><span class="sxs-lookup"><span data-stu-id="be457-253">Unconditionally calling `PipeReader.AdvanceTo` with `buffer.End` in the `examined` position may result in hangs when parsing a single message.</span></span> <span data-ttu-id="be457-254">A próxima chamada para `PipeReader.AdvanceTo` não retornará até:</span><span class="sxs-lookup"><span data-stu-id="be457-254">The next call to `PipeReader.AdvanceTo` won't return until:</span></span>

* <span data-ttu-id="be457-255">Há mais dados gravados no pipe.</span><span class="sxs-lookup"><span data-stu-id="be457-255">There's more data written to the pipe.</span></span>
* <span data-ttu-id="be457-256">E os novos dados não foram examinados anteriormente.</span><span class="sxs-lookup"><span data-stu-id="be457-256">And the new data wasn't previously examined.</span></span>

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#4](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet4)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

<span data-ttu-id="be457-257">❌ **memória insuficiente (OOM)**</span><span class="sxs-lookup"><span data-stu-id="be457-257">❌ **Out of Memory (OOM)**</span></span>

<span data-ttu-id="be457-258">Com as condições a seguir, o código a seguir mantém o buffer até que um <xref:System.OutOfMemoryException> ocorra:</span><span class="sxs-lookup"><span data-stu-id="be457-258">With the following conditions, the following code keeps buffering until an <xref:System.OutOfMemoryException> occurs:</span></span>

* <span data-ttu-id="be457-259">Não há tamanho máximo de mensagem.</span><span class="sxs-lookup"><span data-stu-id="be457-259">There's no maximum message size.</span></span>
* <span data-ttu-id="be457-260">Os dados retornados do `PipeReader` não fazem uma mensagem completa.</span><span class="sxs-lookup"><span data-stu-id="be457-260">The data returned from the `PipeReader` doesn't make a complete message.</span></span> <span data-ttu-id="be457-261">Por exemplo, ele não faz uma mensagem completa porque o outro lado está escrevendo uma mensagem grande (por exemplo, uma mensagem de 4 GB).</span><span class="sxs-lookup"><span data-stu-id="be457-261">For example, it doesn't make a complete message because the other side is writing a large message (For example, a 4-GB message).</span></span>

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#5](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet5)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

<span data-ttu-id="be457-262">**corrupção de memória** de ❌</span><span class="sxs-lookup"><span data-stu-id="be457-262">❌ **Memory Corruption**</span></span>

<span data-ttu-id="be457-263">Ao escrever auxiliares que lêem o buffer, qualquer carga retornada deve ser copiada antes de chamar `Advance`.</span><span class="sxs-lookup"><span data-stu-id="be457-263">When writing helpers that read the buffer, any returned payload should be copied before calling `Advance`.</span></span> <span data-ttu-id="be457-264">O exemplo a seguir retornará a memória informando que o `Pipe` foi descartado e poderá reutilizá-lo para a próxima operação (leitura/gravação).</span><span class="sxs-lookup"><span data-stu-id="be457-264">The following example will return memory that the `Pipe` has discarded and may reuse it for the next operation (read/write).</span></span>

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#Message](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippetMessage)]

[!code-csharp[DoNotUse#6](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet6)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

## <a name="pipewriter"></a><span data-ttu-id="be457-265">PipeWriter</span><span class="sxs-lookup"><span data-stu-id="be457-265">PipeWriter</span></span>

<span data-ttu-id="be457-266">O <xref:System.IO.Pipelines.PipeWriter> gerencia buffers para gravação em nome do chamador.</span><span class="sxs-lookup"><span data-stu-id="be457-266">The <xref:System.IO.Pipelines.PipeWriter> manages buffers for writing on the caller's behalf.</span></span> <span data-ttu-id="be457-267">`PipeWriter` implementa [`IBufferWriter<byte>`](xref:System.Buffers.IBufferWriter`1).</span><span class="sxs-lookup"><span data-stu-id="be457-267">`PipeWriter` implements [`IBufferWriter<byte>`](xref:System.Buffers.IBufferWriter`1).</span></span> <span data-ttu-id="be457-268">`IBufferWriter<byte>` torna possível obter acesso a buffers para executar gravações sem cópias de buffer adicionais.</span><span class="sxs-lookup"><span data-stu-id="be457-268">`IBufferWriter<byte>` makes it possible to get access to buffers to perform writes without additional buffer copies.</span></span>

[!code-csharp[MyPipeWriter](~/samples/snippets/csharp/pipelines/MyPipeWriter.cs?name=snippet)]

<span data-ttu-id="be457-269">O código anterior:</span><span class="sxs-lookup"><span data-stu-id="be457-269">The previous code:</span></span>

* <span data-ttu-id="be457-270">Solicita um buffer de pelo menos 5 bytes do `PipeWriter` usando <xref:System.IO.Pipelines.PipeWriter.GetSpan%2A>.</span><span class="sxs-lookup"><span data-stu-id="be457-270">Requests a buffer of at least 5 bytes from the `PipeWriter` using <xref:System.IO.Pipelines.PipeWriter.GetSpan%2A>.</span></span>
* <span data-ttu-id="be457-271">Grava bytes para a cadeia de caracteres ASCII `"Hello"` no @no__t retornado-1.</span><span class="sxs-lookup"><span data-stu-id="be457-271">Writes bytes for the ASCII string `"Hello"` to the returned `Span<byte>`.</span></span>
* <span data-ttu-id="be457-272">Chama <xref:System.IO.Pipelines.PipeWriter.Advance%2A> para indicar quantos bytes foram gravados no buffer.</span><span class="sxs-lookup"><span data-stu-id="be457-272">Calls <xref:System.IO.Pipelines.PipeWriter.Advance%2A> to indicate how many bytes were written to the buffer.</span></span>
* <span data-ttu-id="be457-273">Libera o `PipeWriter`, que envia os bytes para o dispositivo subjacente.</span><span class="sxs-lookup"><span data-stu-id="be457-273">Flushes the `PipeWriter`, which sends the bytes to the underlying device.</span></span>

<span data-ttu-id="be457-274">O método anterior de gravação usa os buffers fornecidos pelo `PipeWriter`.</span><span class="sxs-lookup"><span data-stu-id="be457-274">The previous method of writing uses the buffers provided by the `PipeWriter`.</span></span> <span data-ttu-id="be457-275">Como alternativa, <xref:System.IO.Pipelines.PipeWriter.WriteAsync%2A?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="be457-275">Alternatively, <xref:System.IO.Pipelines.PipeWriter.WriteAsync%2A?displayProperty=nameWithType>:</span></span>

* <span data-ttu-id="be457-276">Copia o buffer existente para o `PipeWriter`.</span><span class="sxs-lookup"><span data-stu-id="be457-276">Copies the existing buffer to the `PipeWriter`.</span></span>
* <span data-ttu-id="be457-277">Chama `GetSpan`, `Advance` conforme apropriado e chama <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A>.</span><span class="sxs-lookup"><span data-stu-id="be457-277">Calls `GetSpan`, `Advance` as appropriate and calls <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A>.</span></span>

[!code-csharp[MyPipeWriter#2](~/samples/snippets/csharp/pipelines/MyPipeWriter.cs?name=snippet2)]

### <a name="cancellation"></a><span data-ttu-id="be457-278">Cancelamento</span><span class="sxs-lookup"><span data-stu-id="be457-278">Cancellation</span></span>

<span data-ttu-id="be457-279"><xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A> dá suporte à passagem de um <xref:System.Threading.CancellationToken>.</span><span class="sxs-lookup"><span data-stu-id="be457-279"><xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A> supports passing a <xref:System.Threading.CancellationToken>.</span></span> <span data-ttu-id="be457-280">Passar um `CancellationToken` resultará em um `OperationCanceledException` se o token for cancelado enquanto houver uma liberação pendente.</span><span class="sxs-lookup"><span data-stu-id="be457-280">Passing a `CancellationToken` results in an `OperationCanceledException` if the token is canceled while there's a flush pending.</span></span> <span data-ttu-id="be457-281">`PipeWriter.FlushAsync` dá suporte a uma maneira de cancelar a operação de liberação atual por meio de <xref:System.IO.Pipelines.PipeWriter.CancelPendingFlush%2A?displayProperty=nameWithType> sem gerar uma exceção.</span><span class="sxs-lookup"><span data-stu-id="be457-281">`PipeWriter.FlushAsync` supports a way to cancel the current flush operation via <xref:System.IO.Pipelines.PipeWriter.CancelPendingFlush%2A?displayProperty=nameWithType> without raising an exception.</span></span> <span data-ttu-id="be457-282">Chamar `PipeWriter.CancelPendingFlush` faz com que a chamada atual ou seguinte para `PipeWriter.FlushAsync` ou `PipeWriter.WriteAsync` retorne um <xref:System.IO.Pipelines.FlushResult> com `IsCanceled` definido como `true`.</span><span class="sxs-lookup"><span data-stu-id="be457-282">Calling `PipeWriter.CancelPendingFlush` causes the current or next call to `PipeWriter.FlushAsync` or `PipeWriter.WriteAsync` to return a <xref:System.IO.Pipelines.FlushResult> with `IsCanceled` set to `true`.</span></span> <span data-ttu-id="be457-283">Isso pode ser útil para interromper a liberação de rendimento de forma não destrutiva e não excepcional.</span><span class="sxs-lookup"><span data-stu-id="be457-283">This can be useful for halting the yielding flush in a non-destructive and non-exceptional way.</span></span>

<a name="pwcp"></a>

### <a name="pipewriter-common-problems"></a><span data-ttu-id="be457-284">Problemas comuns do PipeWriter</span><span class="sxs-lookup"><span data-stu-id="be457-284">PipeWriter common problems</span></span>

* <span data-ttu-id="be457-285"><xref:System.IO.Pipelines.PipeWriter.GetSpan%2A> e <xref:System.IO.Pipelines.PipeWriter.GetMemory%2A> retornam um buffer com pelo menos a quantidade solicitada de memória.</span><span class="sxs-lookup"><span data-stu-id="be457-285"><xref:System.IO.Pipelines.PipeWriter.GetSpan%2A> and <xref:System.IO.Pipelines.PipeWriter.GetMemory%2A> return a buffer with at least the requested amount of memory.</span></span> <span data-ttu-id="be457-286">**Não** presuma os tamanhos de buffer exatos.</span><span class="sxs-lookup"><span data-stu-id="be457-286">**Don't** assume exact buffer sizes.</span></span>
* <span data-ttu-id="be457-287">Não há nenhuma garantia de que as chamadas sucessivas retornarão o mesmo buffer ou o buffer de mesmo tamanho.</span><span class="sxs-lookup"><span data-stu-id="be457-287">There's no guarantee that successive calls will return the same buffer or the same-sized buffer.</span></span>
* <span data-ttu-id="be457-288">Um novo buffer deve ser solicitado depois de chamar <xref:System.IO.Pipelines.PipeWriter.Advance%2A> para continuar gravando mais dados.</span><span class="sxs-lookup"><span data-stu-id="be457-288">A new buffer must be requested after calling <xref:System.IO.Pipelines.PipeWriter.Advance%2A> to continue writing more data.</span></span> <span data-ttu-id="be457-289">Não é possível gravar no buffer adquirido anteriormente.</span><span class="sxs-lookup"><span data-stu-id="be457-289">The previously acquired buffer can't be written to.</span></span>
* <span data-ttu-id="be457-290">Chamar `GetMemory` ou `GetSpan` enquanto houver uma chamada incompleta para `FlushAsync` não é seguro.</span><span class="sxs-lookup"><span data-stu-id="be457-290">Calling `GetMemory` or `GetSpan` while there's an incomplete call to `FlushAsync` isn't safe.</span></span>
* <span data-ttu-id="be457-291">Chamar `Complete` ou `CompleteAsync` enquanto houver dados não liberados pode resultar em corrupção de memória.</span><span class="sxs-lookup"><span data-stu-id="be457-291">Calling `Complete` or `CompleteAsync` while there's unflushed data can result in memory corruption.</span></span>

## <a name="iduplexpipe"></a><span data-ttu-id="be457-292">IDuplexPipe</span><span class="sxs-lookup"><span data-stu-id="be457-292">IDuplexPipe</span></span>

<span data-ttu-id="be457-293">O <xref:System.IO.Pipelines.IDuplexPipe> é um contrato para tipos que dão suporte à leitura e gravação.</span><span class="sxs-lookup"><span data-stu-id="be457-293">The <xref:System.IO.Pipelines.IDuplexPipe> is a contract for types that support both reading and writing.</span></span> <span data-ttu-id="be457-294">Por exemplo, uma conexão de rede seria representada por um `IDuplexPipe`.</span><span class="sxs-lookup"><span data-stu-id="be457-294">For example, a network connection would be represented by an `IDuplexPipe`.</span></span>

 <span data-ttu-id="be457-295">Ao contrário de `Pipe` que contém um `PipeReader` e um `PipeWriter`, `IDuplexPipe` representa um único lado de uma conexão Full duplex.</span><span class="sxs-lookup"><span data-stu-id="be457-295">Unlike `Pipe` which contains a `PipeReader` and a `PipeWriter`, `IDuplexPipe` represents a single side of a full duplex connection.</span></span> <span data-ttu-id="be457-296">Isso significa que o que é gravado no `PipeWriter` não será lido no `PipeReader`.</span><span class="sxs-lookup"><span data-stu-id="be457-296">That means what is written to the `PipeWriter` will not be read from the `PipeReader`.</span></span>

## <a name="streams"></a><span data-ttu-id="be457-297">Fluxos</span><span class="sxs-lookup"><span data-stu-id="be457-297">Streams</span></span>

<span data-ttu-id="be457-298">Ao ler ou gravar dados de fluxo, você normalmente lê dados usando um desserializador e grava dados usando um serializador.</span><span class="sxs-lookup"><span data-stu-id="be457-298">When reading or writing stream data, you typically read data using a de-serializer and write data using a serializer.</span></span> <span data-ttu-id="be457-299">A maioria dessas APIs de leitura e gravação de fluxo tem um parâmetro `Stream`.</span><span class="sxs-lookup"><span data-stu-id="be457-299">Most of these read and write stream APIs have a `Stream` parameter.</span></span> <span data-ttu-id="be457-300">Para facilitar a integração com essas APIs existentes, `PipeReader` e `PipeWriter` expõem um <xref:System.IO.Pipelines.PipeReader.AsStream%2A>.</span><span class="sxs-lookup"><span data-stu-id="be457-300">To make it easier to integrate with these existing APIs, `PipeReader` and `PipeWriter` expose an <xref:System.IO.Pipelines.PipeReader.AsStream%2A>.</span></span>  <span data-ttu-id="be457-301"><xref:System.IO.Pipelines.PipeWriter.AsStream%2A> retorna uma implementação `Stream` em relação ao `PipeReader` ou `PipeWriter`.</span><span class="sxs-lookup"><span data-stu-id="be457-301"><xref:System.IO.Pipelines.PipeWriter.AsStream%2A> returns a `Stream` implementation around the `PipeReader` or `PipeWriter`.</span></span>
