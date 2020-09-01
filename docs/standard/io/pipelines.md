---
title: Pipelines de e/s-.NET
description: Saiba como usar pipelines de e/s com eficiência no .NET e evitar problemas em seu código.
ms.date: 08/27/2020
ms.technology: dotnet-standard
helpviewer_keywords:
- Pipelines
- Pipelines I/O
- I/O [.NET], Pipelines
author: rick-anderson
ms.author: riande
ms.openlocfilehash: a24d7f5c22c936cd3fd3fdc51f0f3ace56386574
ms.sourcegitcommit: e0803b8975d3eb12e735a5d07637020dd6dac5ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2020
ms.locfileid: "89271978"
---
# <a name="systemiopipelines-in-net"></a><span data-ttu-id="96a09-103">System. IO. pipelines no .NET</span><span class="sxs-lookup"><span data-stu-id="96a09-103">System.IO.Pipelines in .NET</span></span>

<span data-ttu-id="96a09-104"><xref:System.IO.Pipelines> é uma nova biblioteca criada para facilitar a execução de e/s de alto desempenho no .NET.</span><span class="sxs-lookup"><span data-stu-id="96a09-104"><xref:System.IO.Pipelines> is a new library that is designed to make it easier to do high-performance I/O in .NET.</span></span> <span data-ttu-id="96a09-105">É uma biblioteca direcionada .NET Standard que funciona em todas as implementações do .NET.</span><span class="sxs-lookup"><span data-stu-id="96a09-105">It's a library targeting .NET Standard that works on all .NET implementations.</span></span>

<a name="solve"></a>

## <a name="what-problem-does-systemiopipelines-solve"></a><span data-ttu-id="96a09-106">Qual problema o System. IO. pipelines resolve</span><span class="sxs-lookup"><span data-stu-id="96a09-106">What problem does System.IO.Pipelines solve</span></span>

<!-- corner case doesn't MT (machine translate)   -->
<span data-ttu-id="96a09-107">Aplicativos que analisam dados de streaming são compostos por código clichê com muitos fluxos de código especializados e incomuns.</span><span class="sxs-lookup"><span data-stu-id="96a09-107">Apps that parse streaming data are composed of boilerplate code having many specialized and unusual code flows.</span></span> <span data-ttu-id="96a09-108">O código de caso clichê e especial é complexo e difícil de manter.</span><span class="sxs-lookup"><span data-stu-id="96a09-108">The boilerplate and special case code is complex and difficult to maintain.</span></span>

<span data-ttu-id="96a09-109">`System.IO.Pipelines` foi arquitetado para:</span><span class="sxs-lookup"><span data-stu-id="96a09-109">`System.IO.Pipelines` was architected to:</span></span>

* <span data-ttu-id="96a09-110">Ter dados de streaming de análise de alto desempenho.</span><span class="sxs-lookup"><span data-stu-id="96a09-110">Have high performance parsing streaming data.</span></span>
* <span data-ttu-id="96a09-111">Reduza a complexidade do código.</span><span class="sxs-lookup"><span data-stu-id="96a09-111">Reduce code complexity.</span></span>

<span data-ttu-id="96a09-112">O código a seguir é típico para um servidor TCP que recebe mensagens delimitadas por linha (delimitadas por `'\n'` ) de um cliente:</span><span class="sxs-lookup"><span data-stu-id="96a09-112">The following code is typical for a TCP server that receives line-delimited messages (delimited by `'\n'`) from a client:</span></span>

```csharp
async Task ProcessLinesAsync(NetworkStream stream)
{
    var buffer = new byte[1024];
    await stream.ReadAsync(buffer, 0, buffer.Length);

    // Process a single line from the buffer
    ProcessLine(buffer);
}
```

<span data-ttu-id="96a09-113">O código anterior tem vários problemas:</span><span class="sxs-lookup"><span data-stu-id="96a09-113">The preceding code has several problems:</span></span>

* <span data-ttu-id="96a09-114">A mensagem inteira (fim da linha) não pode ser recebida em uma única chamada para `ReadAsync` .</span><span class="sxs-lookup"><span data-stu-id="96a09-114">The entire message (end of line) might not be received in a single call to `ReadAsync`.</span></span>
* <span data-ttu-id="96a09-115">Ele está ignorando o resultado de `stream.ReadAsync` .</span><span class="sxs-lookup"><span data-stu-id="96a09-115">It's ignoring the result of `stream.ReadAsync`.</span></span> <span data-ttu-id="96a09-116">`stream.ReadAsync` Retorna o número de dados lidos.</span><span class="sxs-lookup"><span data-stu-id="96a09-116">`stream.ReadAsync` returns how much data was read.</span></span>
* <span data-ttu-id="96a09-117">Ele não manipula o caso em que várias linhas são lidas em uma única `ReadAsync` chamada.</span><span class="sxs-lookup"><span data-stu-id="96a09-117">It doesn't handle the case where multiple lines are read in a single `ReadAsync` call.</span></span>
* <span data-ttu-id="96a09-118">Ele aloca uma `byte` matriz com cada leitura.</span><span class="sxs-lookup"><span data-stu-id="96a09-118">It allocates a `byte` array with each read.</span></span>

<span data-ttu-id="96a09-119">Para corrigir os problemas anteriores, as seguintes alterações são necessárias:</span><span class="sxs-lookup"><span data-stu-id="96a09-119">To fix the preceding problems, the following changes are required:</span></span>

* <span data-ttu-id="96a09-120">Armazenar os dados de entrada em buffer até que uma nova linha seja encontrada.</span><span class="sxs-lookup"><span data-stu-id="96a09-120">Buffer the incoming data until a new line is found.</span></span>
* <span data-ttu-id="96a09-121">Analise todas as linhas retornadas no buffer.</span><span class="sxs-lookup"><span data-stu-id="96a09-121">Parse all the lines returned in the buffer.</span></span>
* <span data-ttu-id="96a09-122">É possível que a linha seja maior que 1 KB (1024 bytes).</span><span class="sxs-lookup"><span data-stu-id="96a09-122">It's possible that the line is bigger than 1 KB (1024 bytes).</span></span> <span data-ttu-id="96a09-123">O código precisa redimensionar o buffer de entrada até que o delimitador seja encontrado para ajustar a linha completa dentro do buffer.</span><span class="sxs-lookup"><span data-stu-id="96a09-123">The code needs to resize the input buffer until the delimiter is found in order to fit the complete line inside the buffer.</span></span>

  * <span data-ttu-id="96a09-124">Se o buffer for redimensionado, mais cópias de buffer serão feitas conforme as linhas mais longas aparecerem na entrada.</span><span class="sxs-lookup"><span data-stu-id="96a09-124">If the buffer is resized, more buffer copies are made as longer lines appear in the input.</span></span>
  * <span data-ttu-id="96a09-125">Para reduzir o espaço desperdiçado, compacte o buffer usado para ler as linhas.</span><span class="sxs-lookup"><span data-stu-id="96a09-125">To reduce wasted space, compact the buffer used for reading lines.</span></span>

* <span data-ttu-id="96a09-126">Considere o uso do pool de buffers para evitar a alocação repetida de memória.</span><span class="sxs-lookup"><span data-stu-id="96a09-126">Consider using buffer pooling to avoid allocating memory repeatedly.</span></span>
* <span data-ttu-id="96a09-127">O código a seguir aborda alguns desses problemas:</span><span class="sxs-lookup"><span data-stu-id="96a09-127">The following code addresses some of these problems:</span></span>

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/ProcessLinesAsync.cs" id="snippet":::

<span data-ttu-id="96a09-128">O código anterior é complexo e não aborda todos os problemas identificados.</span><span class="sxs-lookup"><span data-stu-id="96a09-128">The previous code is complex and doesn't address all the problems identified.</span></span> <span data-ttu-id="96a09-129">A rede de alto desempenho geralmente significa escrever código muito complexo para maximizar o desempenho.</span><span class="sxs-lookup"><span data-stu-id="96a09-129">High-performance networking usually means writing very complex code to maximize performance.</span></span> <span data-ttu-id="96a09-130">`System.IO.Pipelines` foi projetado para tornar mais fácil a criação desse tipo de código.</span><span class="sxs-lookup"><span data-stu-id="96a09-130">`System.IO.Pipelines` was designed to make writing this type of code easier.</span></span>

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

## <a name="pipe"></a><span data-ttu-id="96a09-131">Pipe</span><span class="sxs-lookup"><span data-stu-id="96a09-131">Pipe</span></span>

<span data-ttu-id="96a09-132">A <xref:System.IO.Pipelines.Pipe> classe pode ser usada para criar um `PipeWriter/PipeReader` par.</span><span class="sxs-lookup"><span data-stu-id="96a09-132">The <xref:System.IO.Pipelines.Pipe> class can be used to create a `PipeWriter/PipeReader` pair.</span></span> <span data-ttu-id="96a09-133">Todos os dados gravados no `PipeWriter` estão disponíveis no `PipeReader` :</span><span class="sxs-lookup"><span data-stu-id="96a09-133">All data written into the `PipeWriter` is available in the `PipeReader`:</span></span>

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/Pipe.cs" id="snippet2":::

<a name="pbu"></a>

### <a name="pipe-basic-usage"></a><span data-ttu-id="96a09-134">Uso básico do pipe</span><span class="sxs-lookup"><span data-stu-id="96a09-134">Pipe basic usage</span></span>

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/Pipe.cs" id="snippet":::

<span data-ttu-id="96a09-135">Há dois loops:</span><span class="sxs-lookup"><span data-stu-id="96a09-135">There are two loops:</span></span>

* <span data-ttu-id="96a09-136">`FillPipeAsync` lê do `Socket` e grava no `PipeWriter` .</span><span class="sxs-lookup"><span data-stu-id="96a09-136">`FillPipeAsync` reads from the `Socket` and writes to the `PipeWriter`.</span></span>
* <span data-ttu-id="96a09-137">`ReadPipeAsync` lê de `PipeReader` e analisa as linhas de entrada.</span><span class="sxs-lookup"><span data-stu-id="96a09-137">`ReadPipeAsync` reads from the `PipeReader` and parses incoming lines.</span></span>

<span data-ttu-id="96a09-138">Não há buffers explícitos alocados.</span><span class="sxs-lookup"><span data-stu-id="96a09-138">There are no explicit buffers allocated.</span></span> <span data-ttu-id="96a09-139">Todo o gerenciamento de buffer é delegado às `PipeReader` `PipeWriter` implementações e.</span><span class="sxs-lookup"><span data-stu-id="96a09-139">All buffer management is delegated to the `PipeReader` and `PipeWriter` implementations.</span></span> <span data-ttu-id="96a09-140">A delegação do gerenciamento de buffer facilita o consumo do código para se concentrar exclusivamente na lógica de negócios.</span><span class="sxs-lookup"><span data-stu-id="96a09-140">Delegating buffer management makes it easier for consuming code to focus solely on the business logic.</span></span>

<span data-ttu-id="96a09-141">No primeiro loop:</span><span class="sxs-lookup"><span data-stu-id="96a09-141">In the first loop:</span></span>

* <span data-ttu-id="96a09-142"><xref:System.IO.Pipelines.PipeWriter.GetMemory(System.Int32)?displayProperty=nameWithType> é chamado para obter memória do gravador subjacente.</span><span class="sxs-lookup"><span data-stu-id="96a09-142"><xref:System.IO.Pipelines.PipeWriter.GetMemory(System.Int32)?displayProperty=nameWithType> is called to get memory from the underlying writer.</span></span>
* <span data-ttu-id="96a09-143"><xref:System.IO.Pipelines.PipeWriter.Advance(System.Int32)?displayProperty=nameWithType> é chamado para informar a `PipeWriter` quantidade de dados gravados no buffer.</span><span class="sxs-lookup"><span data-stu-id="96a09-143"><xref:System.IO.Pipelines.PipeWriter.Advance(System.Int32)?displayProperty=nameWithType> is called to tell the `PipeWriter` how much data was written to the buffer.</span></span>
* <span data-ttu-id="96a09-144"><xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A?displayProperty=nameWithType> é chamado para disponibilizar os dados para o `PipeReader` .</span><span class="sxs-lookup"><span data-stu-id="96a09-144"><xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A?displayProperty=nameWithType> is called to make the data available to the `PipeReader`.</span></span>

<span data-ttu-id="96a09-145">No segundo loop, o `PipeReader` consome os buffers gravados pelo `PipeWriter` .</span><span class="sxs-lookup"><span data-stu-id="96a09-145">In the second loop, the `PipeReader` consumes the buffers written by `PipeWriter`.</span></span> <span data-ttu-id="96a09-146">Os buffers são provenientes do soquete.</span><span class="sxs-lookup"><span data-stu-id="96a09-146">The buffers come from the socket.</span></span> <span data-ttu-id="96a09-147">A chamada para `PipeReader.ReadAsync` :</span><span class="sxs-lookup"><span data-stu-id="96a09-147">The call to `PipeReader.ReadAsync`:</span></span>

* <span data-ttu-id="96a09-148">Retorna um <xref:System.IO.Pipelines.ReadResult> que contém duas partes importantes de informações:</span><span class="sxs-lookup"><span data-stu-id="96a09-148">Returns a <xref:System.IO.Pipelines.ReadResult> that contains two important pieces of information:</span></span>

  * <span data-ttu-id="96a09-149">Os dados que foram lidos na forma de `ReadOnlySequence<byte>` .</span><span class="sxs-lookup"><span data-stu-id="96a09-149">The data that was read in the form of `ReadOnlySequence<byte>`.</span></span>
  * <span data-ttu-id="96a09-150">Um booliano `IsCompleted` que indica se o fim de dados (EOF) foi atingido.</span><span class="sxs-lookup"><span data-stu-id="96a09-150">A boolean `IsCompleted` that indicates if the end of data (EOF) has been reached.</span></span>

<span data-ttu-id="96a09-151">Depois de encontrar o delimitador de fim de linha (EOL) e analisar a linha:</span><span class="sxs-lookup"><span data-stu-id="96a09-151">After finding the end of line (EOL) delimiter and parsing the line:</span></span>

* <span data-ttu-id="96a09-152">A lógica processa o buffer para ignorar o que já foi processado.</span><span class="sxs-lookup"><span data-stu-id="96a09-152">The logic processes the buffer to skip what's already processed.</span></span>
* <span data-ttu-id="96a09-153">`PipeReader.AdvanceTo` é chamado para informar a `PipeReader` quantidade de dados consumidos e examinados.</span><span class="sxs-lookup"><span data-stu-id="96a09-153">`PipeReader.AdvanceTo` is called to tell the `PipeReader` how much data has been consumed and examined.</span></span>

<span data-ttu-id="96a09-154">Os loops de leitor e gravador terminam chamando `Complete` .</span><span class="sxs-lookup"><span data-stu-id="96a09-154">The reader and writer loops end by calling `Complete`.</span></span> <span data-ttu-id="96a09-155">`Complete` permite que o pipe subjacente libere a memória alocada.</span><span class="sxs-lookup"><span data-stu-id="96a09-155">`Complete` lets the underlying Pipe release the memory it allocated.</span></span>

### <a name="backpressure-and-flow-control"></a><span data-ttu-id="96a09-156">Controle de fluxo e de pressão</span><span class="sxs-lookup"><span data-stu-id="96a09-156">Backpressure and flow control</span></span>

<span data-ttu-id="96a09-157">Idealmente, a leitura e a análise funcionam em conjunto:</span><span class="sxs-lookup"><span data-stu-id="96a09-157">Ideally, reading and parsing work together:</span></span>

* <span data-ttu-id="96a09-158">O thread de gravação consome dados da rede e os coloca em buffers.</span><span class="sxs-lookup"><span data-stu-id="96a09-158">The writing thread consumes data from the network and puts it in buffers.</span></span>
* <span data-ttu-id="96a09-159">O thread de análise é responsável por construir as estruturas de dados apropriadas.</span><span class="sxs-lookup"><span data-stu-id="96a09-159">The parsing thread is responsible for constructing the appropriate data structures.</span></span>

<span data-ttu-id="96a09-160">Normalmente, a análise leva mais tempo do que apenas copiar blocos de dados da rede:</span><span class="sxs-lookup"><span data-stu-id="96a09-160">Typically, parsing takes more time than just copying blocks of data from the network:</span></span>

* <span data-ttu-id="96a09-161">O thread de leitura fica à frente do thread de análise.</span><span class="sxs-lookup"><span data-stu-id="96a09-161">The reading thread gets ahead of the parsing thread.</span></span>
* <span data-ttu-id="96a09-162">O thread de leitura precisa diminuir ou alocar mais memória para armazenar os dados para o thread de análise.</span><span class="sxs-lookup"><span data-stu-id="96a09-162">The reading thread has to either slow down or allocate more memory to store the data for the parsing thread.</span></span>

<span data-ttu-id="96a09-163">Para um desempenho ideal, há um equilíbrio entre pausas frequentes e alocação de mais memória.</span><span class="sxs-lookup"><span data-stu-id="96a09-163">For optimal performance, there's a balance between frequent pauses and allocating more memory.</span></span>

<span data-ttu-id="96a09-164">Para resolver o problema anterior, o `Pipe` tem duas configurações para controlar o fluxo de dados:</span><span class="sxs-lookup"><span data-stu-id="96a09-164">To solve the preceding problem, the `Pipe` has two settings to control the flow of data:</span></span>

* <span data-ttu-id="96a09-165"><xref:System.IO.Pipelines.PipeOptions.PauseWriterThreshold>: Determina a quantidade de dados que deve ser armazenada em buffer antes das chamadas para <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A> Pausar.</span><span class="sxs-lookup"><span data-stu-id="96a09-165"><xref:System.IO.Pipelines.PipeOptions.PauseWriterThreshold>: Determines how much data should be buffered before calls to <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A> pause.</span></span>
* <span data-ttu-id="96a09-166"><xref:System.IO.Pipelines.PipeOptions.ResumeWriterThreshold>: Determina a quantidade de dados que o leitor deve observar antes de chamar a `PipeWriter.FlushAsync` retomada.</span><span class="sxs-lookup"><span data-stu-id="96a09-166"><xref:System.IO.Pipelines.PipeOptions.ResumeWriterThreshold>: Determines how much data the reader has to observe before calls to `PipeWriter.FlushAsync` resume.</span></span>

![Diagrama com ResumeWriterThreshold e PauseWriterThreshold](media/pipelines/resume-pause.png)

<span data-ttu-id="96a09-168"><xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="96a09-168"><xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A?displayProperty=nameWithType>:</span></span>

* <span data-ttu-id="96a09-169">Retorna um incompleto `ValueTask<FlushResult>` quando a quantidade de dados em `Pipe` cruza `PauseWriterThreshold` .</span><span class="sxs-lookup"><span data-stu-id="96a09-169">Returns an incomplete `ValueTask<FlushResult>` when the amount of data in the `Pipe` crosses `PauseWriterThreshold`.</span></span>
* <span data-ttu-id="96a09-170">É concluído `ValueTask<FlushResult>` quando se torna menor que `ResumeWriterThreshold` .</span><span class="sxs-lookup"><span data-stu-id="96a09-170">Completes `ValueTask<FlushResult>` when it becomes lower than `ResumeWriterThreshold`.</span></span>

<span data-ttu-id="96a09-171">Dois valores são usados para evitar o ciclo rápido, que pode ocorrer se um valor for usado.</span><span class="sxs-lookup"><span data-stu-id="96a09-171">Two values are used to prevent rapid cycling, which can occur if one value is used.</span></span>

### <a name="examples"></a><span data-ttu-id="96a09-172">Exemplos</span><span class="sxs-lookup"><span data-stu-id="96a09-172">Examples</span></span>

```csharp
// The Pipe will start returning incomplete tasks from FlushAsync until
// the reader examines at least 5 bytes.
var options = new PipeOptions(pauseWriterThreshold: 10, resumeWriterThreshold: 5);
var pipe = new Pipe(options);
```

### <a name="pipescheduler"></a><span data-ttu-id="96a09-173">PipeScheduler</span><span class="sxs-lookup"><span data-stu-id="96a09-173">PipeScheduler</span></span>

<span data-ttu-id="96a09-174">Normalmente, ao usar o `async` e `await` o, o código assíncrono continua em um <xref:System.Threading.Tasks.TaskScheduler> ou no atual <xref:System.Threading.SynchronizationContext> .</span><span class="sxs-lookup"><span data-stu-id="96a09-174">Typically when using `async` and `await`, asynchronous code resumes on either on a <xref:System.Threading.Tasks.TaskScheduler> or on the current <xref:System.Threading.SynchronizationContext>.</span></span>

<span data-ttu-id="96a09-175">Ao fazer e/s, é importante ter um controle refinado sobre onde a e/s é executada.</span><span class="sxs-lookup"><span data-stu-id="96a09-175">When doing I/O, it's important to have fine-grained control over where the I/O is performed.</span></span> <span data-ttu-id="96a09-176">Esse controle permite aproveitar os caches de CPU com eficiência.</span><span class="sxs-lookup"><span data-stu-id="96a09-176">This control allows taking advantage of CPU caches effectively.</span></span> <span data-ttu-id="96a09-177">O cache eficiente é essencial para aplicativos de alto desempenho, como servidores Web.</span><span class="sxs-lookup"><span data-stu-id="96a09-177">Efficient caching is critical for high-performance apps like web servers.</span></span> <span data-ttu-id="96a09-178"><xref:System.IO.Pipelines.PipeScheduler> fornece controle sobre onde os retornos de chamada assíncronos são executados.</span><span class="sxs-lookup"><span data-stu-id="96a09-178"><xref:System.IO.Pipelines.PipeScheduler> provides control over where asynchronous callbacks run.</span></span> <span data-ttu-id="96a09-179">Por padrão:</span><span class="sxs-lookup"><span data-stu-id="96a09-179">By default:</span></span>

* <span data-ttu-id="96a09-180">O atual <xref:System.Threading.SynchronizationContext> é usado.</span><span class="sxs-lookup"><span data-stu-id="96a09-180">The current <xref:System.Threading.SynchronizationContext> is used.</span></span>
* <span data-ttu-id="96a09-181">Se não houver `SynchronizationContext` , ele usará o pool de threads para executar retornos de chamada.</span><span class="sxs-lookup"><span data-stu-id="96a09-181">If there's no `SynchronizationContext`, it uses the thread pool to run callbacks.</span></span>

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/Program.cs" id="snippet":::

<span data-ttu-id="96a09-182">[PipeScheduler. ThreadPool](xref:System.IO.Pipelines.PipeScheduler.ThreadPool) é a <xref:System.IO.Pipelines.PipeScheduler> implementação que enfileira os retornos de chamada para o pool de threads.</span><span class="sxs-lookup"><span data-stu-id="96a09-182">[PipeScheduler.ThreadPool](xref:System.IO.Pipelines.PipeScheduler.ThreadPool) is the <xref:System.IO.Pipelines.PipeScheduler> implementation that queues callbacks to the thread pool.</span></span> <span data-ttu-id="96a09-183">`PipeScheduler.ThreadPool` é o padrão e geralmente é a melhor opção.</span><span class="sxs-lookup"><span data-stu-id="96a09-183">`PipeScheduler.ThreadPool` is the default and generally the best choice.</span></span> <span data-ttu-id="96a09-184">[PipeScheduler. Inline](xref:System.IO.Pipelines.PipeScheduler.Inline) pode causar consequências indesejadas, como deadlocks.</span><span class="sxs-lookup"><span data-stu-id="96a09-184">[PipeScheduler.Inline](xref:System.IO.Pipelines.PipeScheduler.Inline) can cause unintended consequences such as deadlocks.</span></span>

### <a name="pipe-reset"></a><span data-ttu-id="96a09-185">Redefinição de pipe</span><span class="sxs-lookup"><span data-stu-id="96a09-185">Pipe reset</span></span>

<span data-ttu-id="96a09-186">Com frequência, é eficiente reutilizar o `Pipe` objeto.</span><span class="sxs-lookup"><span data-stu-id="96a09-186">It's frequently efficient to reuse the `Pipe` object.</span></span> <span data-ttu-id="96a09-187">Para redefinir o pipe, chame <xref:System.IO.Pipelines.PipeReader> <xref:System.IO.Pipelines.Pipe.Reset%2A> quando o `PipeReader` e o `PipeWriter` estiverem concluídos.</span><span class="sxs-lookup"><span data-stu-id="96a09-187">To reset the pipe, call <xref:System.IO.Pipelines.PipeReader> <xref:System.IO.Pipelines.Pipe.Reset%2A> when both the `PipeReader` and `PipeWriter` are complete.</span></span>

## <a name="pipereader"></a><span data-ttu-id="96a09-188">PipeReader</span><span class="sxs-lookup"><span data-stu-id="96a09-188">PipeReader</span></span>

<span data-ttu-id="96a09-189"><xref:System.IO.Pipelines.PipeReader> gerencia a memória em nome do chamador.</span><span class="sxs-lookup"><span data-stu-id="96a09-189"><xref:System.IO.Pipelines.PipeReader> manages memory on the caller's behalf.</span></span> <span data-ttu-id="96a09-190">**Sempre** chamar <xref:System.IO.Pipelines.PipeReader.AdvanceTo%2A?displayProperty=nameWithType> após a chamada <xref:System.IO.Pipelines.PipeReader.ReadAsync%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="96a09-190">**Always** call <xref:System.IO.Pipelines.PipeReader.AdvanceTo%2A?displayProperty=nameWithType> after calling <xref:System.IO.Pipelines.PipeReader.ReadAsync%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="96a09-191">Isso permite `PipeReader` saber quando o chamador é feito com a memória para que possa ser acompanhado.</span><span class="sxs-lookup"><span data-stu-id="96a09-191">This lets the `PipeReader` know when the caller is done with the memory so that it can be tracked.</span></span> <span data-ttu-id="96a09-192">O `ReadOnlySequence<byte>` retornado de `PipeReader.ReadAsync` é válido somente até a chamada de `PipeReader.AdvanceTo` .</span><span class="sxs-lookup"><span data-stu-id="96a09-192">The `ReadOnlySequence<byte>` returned from `PipeReader.ReadAsync` is only valid until the call the `PipeReader.AdvanceTo`.</span></span> <span data-ttu-id="96a09-193">É ilegal usar depois de `ReadOnlySequence<byte>` chamar `PipeReader.AdvanceTo` .</span><span class="sxs-lookup"><span data-stu-id="96a09-193">It's illegal to use `ReadOnlySequence<byte>` after calling `PipeReader.AdvanceTo`.</span></span>

<span data-ttu-id="96a09-194">`PipeReader.AdvanceTo` usa dois <xref:System.SequencePosition> argumentos:</span><span class="sxs-lookup"><span data-stu-id="96a09-194">`PipeReader.AdvanceTo` takes two <xref:System.SequencePosition> arguments:</span></span>

* <span data-ttu-id="96a09-195">O primeiro argumento determina a quantidade de memória consumida.</span><span class="sxs-lookup"><span data-stu-id="96a09-195">The first argument determines how much memory was consumed.</span></span>
* <span data-ttu-id="96a09-196">O segundo argumento determina o quanto do buffer foi observado.</span><span class="sxs-lookup"><span data-stu-id="96a09-196">The second argument determines how much of the buffer was observed.</span></span>

<span data-ttu-id="96a09-197">Marcar dados como consumidos significa que o pipe pode retornar a memória para o pool de buffers subjacente.</span><span class="sxs-lookup"><span data-stu-id="96a09-197">Marking data as consumed means that the pipe can return the memory to the underlying buffer pool.</span></span> <span data-ttu-id="96a09-198">Marcar dados como observados controla o que a próxima chamada `PipeReader.ReadAsync` faz.</span><span class="sxs-lookup"><span data-stu-id="96a09-198">Marking data as observed controls what the next call to `PipeReader.ReadAsync` does.</span></span> <span data-ttu-id="96a09-199">Marcar tudo como observado significa que a próxima chamada para `PipeReader.ReadAsync` não retornará até que haja mais dados gravados no pipe.</span><span class="sxs-lookup"><span data-stu-id="96a09-199">Marking everything as observed means that the next call to `PipeReader.ReadAsync` won't return until there's more data written to the pipe.</span></span> <span data-ttu-id="96a09-200">Qualquer outro valor fará com que a próxima chamada seja `PipeReader.ReadAsync` retornada imediatamente com os dados observados *e* inobservados, mas não os dados que já foram consumidos.</span><span class="sxs-lookup"><span data-stu-id="96a09-200">Any other value will make the next call to `PipeReader.ReadAsync` return immediately with the observed *and* unobserved data, but not data that has already been consumed.</span></span>

### <a name="read-streaming-data-scenarios"></a><span data-ttu-id="96a09-201">Ler cenários de dados de streaming</span><span class="sxs-lookup"><span data-stu-id="96a09-201">Read streaming data scenarios</span></span>

<span data-ttu-id="96a09-202">Há alguns padrões típicos que surgem ao tentar ler dados de streaming:</span><span class="sxs-lookup"><span data-stu-id="96a09-202">There are a couple of typical patterns that emerge when trying to read streaming data:</span></span>

* <span data-ttu-id="96a09-203">Dado um fluxo de dados, analise uma única mensagem.</span><span class="sxs-lookup"><span data-stu-id="96a09-203">Given a stream of data, parse a single message.</span></span>
* <span data-ttu-id="96a09-204">Dado um fluxo de dados, analise todas as mensagens disponíveis.</span><span class="sxs-lookup"><span data-stu-id="96a09-204">Given a stream of data, parse all available messages.</span></span>

<span data-ttu-id="96a09-205">Os exemplos a seguir usam o `TryParseMessage` método para analisar mensagens de um `ReadOnlySequence<byte>` .</span><span class="sxs-lookup"><span data-stu-id="96a09-205">The following examples use the `TryParseMessage` method for parsing messages from a `ReadOnlySequence<byte>`.</span></span> <span data-ttu-id="96a09-206">`TryParseMessage` analisa uma única mensagem e atualiza o buffer de entrada para cortar a mensagem analisada do buffer.</span><span class="sxs-lookup"><span data-stu-id="96a09-206">`TryParseMessage` parses a single message and update the input buffer to trim the parsed message from the buffer.</span></span> <span data-ttu-id="96a09-207">`TryParseMessage` Não faz parte do .NET, é um método escrito pelo usuário usado nas seções a seguir.</span><span class="sxs-lookup"><span data-stu-id="96a09-207">`TryParseMessage` is not part of .NET, it's a user written method used in the following sections.</span></span>

```csharp
bool TryParseMessage(ref ReadOnlySequence<byte> buffer, out Message message);
```

### <a name="read-a-single-message"></a><span data-ttu-id="96a09-208">Ler uma única mensagem</span><span class="sxs-lookup"><span data-stu-id="96a09-208">Read a single message</span></span>

<span data-ttu-id="96a09-209">O código a seguir lê uma única mensagem de a `PipeReader` e retorna-a para o chamador.</span><span class="sxs-lookup"><span data-stu-id="96a09-209">The following code reads a single message from a `PipeReader` and returns it to the caller.</span></span>

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/ReadSingleMsg.cs" id="snippet":::

<span data-ttu-id="96a09-210">O código anterior:</span><span class="sxs-lookup"><span data-stu-id="96a09-210">The preceding code:</span></span>

* <span data-ttu-id="96a09-211">Analisa uma única mensagem.</span><span class="sxs-lookup"><span data-stu-id="96a09-211">Parses a single message.</span></span>
* <span data-ttu-id="96a09-212">Atualiza o consumido `SequencePosition` e examinado `SequencePosition` para apontar para o início do buffer de entrada cortado.</span><span class="sxs-lookup"><span data-stu-id="96a09-212">Updates the consumed `SequencePosition` and examined `SequencePosition` to point to the start of the trimmed input buffer.</span></span>

<span data-ttu-id="96a09-213">Os dois `SequencePosition` argumentos são atualizados porque `TryParseMessage` o Remove a mensagem analisada do buffer de entrada.</span><span class="sxs-lookup"><span data-stu-id="96a09-213">The two `SequencePosition` arguments are updated because `TryParseMessage` removes the parsed message from the input buffer.</span></span> <span data-ttu-id="96a09-214">Geralmente, ao analisar uma única mensagem do buffer, a posição examinada deve ser uma das seguintes:</span><span class="sxs-lookup"><span data-stu-id="96a09-214">Generally, when parsing a single message from the buffer, the examined position should be one of the following:</span></span>

* <span data-ttu-id="96a09-215">O fim da mensagem.</span><span class="sxs-lookup"><span data-stu-id="96a09-215">The end of the message.</span></span>
* <span data-ttu-id="96a09-216">O final do buffer recebido se nenhuma mensagem for encontrada.</span><span class="sxs-lookup"><span data-stu-id="96a09-216">The end of the received buffer if no message was found.</span></span>

<span data-ttu-id="96a09-217">O caso de mensagem única tem o maior potencial para erros.</span><span class="sxs-lookup"><span data-stu-id="96a09-217">The single message case has the most potential for errors.</span></span> <span data-ttu-id="96a09-218">Passar os valores incorretos para *examinados* pode resultar em uma exceção de memória insuficiente ou um loop infinito.</span><span class="sxs-lookup"><span data-stu-id="96a09-218">Passing the wrong values to *examined* can result in an out of memory exception or an infinite loop.</span></span> <span data-ttu-id="96a09-219">Para obter mais informações, consulte a seção [problemas comuns do PipeReader](#gotchas) neste artigo.</span><span class="sxs-lookup"><span data-stu-id="96a09-219">For more information, see the [PipeReader common problems](#gotchas) section in this article.</span></span>

### <a name="reading-multiple-messages"></a><span data-ttu-id="96a09-220">Lendo várias mensagens</span><span class="sxs-lookup"><span data-stu-id="96a09-220">Reading multiple messages</span></span>

<span data-ttu-id="96a09-221">O código a seguir lê todas as mensagens de um `PipeReader` e chamadas `ProcessMessageAsync` em cada uma.</span><span class="sxs-lookup"><span data-stu-id="96a09-221">The following code reads all messages from a `PipeReader` and calls `ProcessMessageAsync` on each.</span></span>

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/MyConnection1.cs" id="snippet":::

### <a name="cancellation"></a><span data-ttu-id="96a09-222">Cancelamento</span><span class="sxs-lookup"><span data-stu-id="96a09-222">Cancellation</span></span>

<span data-ttu-id="96a09-223">`PipeReader.ReadAsync`:</span><span class="sxs-lookup"><span data-stu-id="96a09-223">`PipeReader.ReadAsync`:</span></span>

* <span data-ttu-id="96a09-224">Dá suporte à passagem de um <xref:System.Threading.CancellationToken> .</span><span class="sxs-lookup"><span data-stu-id="96a09-224">Supports passing a <xref:System.Threading.CancellationToken>.</span></span>
* <span data-ttu-id="96a09-225">Gera um <xref:System.OperationCanceledException> se o `CancellationToken` for cancelado enquanto houver uma leitura pendente.</span><span class="sxs-lookup"><span data-stu-id="96a09-225">Throws an <xref:System.OperationCanceledException> if the `CancellationToken` is canceled while there's a read pending.</span></span>
* <span data-ttu-id="96a09-226">O oferece suporte a uma maneira de cancelar a operação de leitura atual por meio do <xref:System.IO.Pipelines.PipeReader.CancelPendingRead%2A?displayProperty=nameWithType> , que evita a geração de uma exceção.</span><span class="sxs-lookup"><span data-stu-id="96a09-226">Supports a way to cancel the current read operation via <xref:System.IO.Pipelines.PipeReader.CancelPendingRead%2A?displayProperty=nameWithType>, which avoids raising an exception.</span></span> <span data-ttu-id="96a09-227">`PipeReader.CancelPendingRead`A chamada faz com que a chamada atual ou seguinte para `PipeReader.ReadAsync` retorne um <xref:System.IO.Pipelines.ReadResult> com `IsCanceled` definido como `true` .</span><span class="sxs-lookup"><span data-stu-id="96a09-227">Calling `PipeReader.CancelPendingRead` causes the current or next call to `PipeReader.ReadAsync` to return a <xref:System.IO.Pipelines.ReadResult> with `IsCanceled` set to `true`.</span></span> <span data-ttu-id="96a09-228">Isso pode ser útil para interromper o loop de leitura existente de forma não destrutiva e não excepcional.</span><span class="sxs-lookup"><span data-stu-id="96a09-228">This can be useful for halting the existing read loop in a non-destructive and non-exceptional way.</span></span>

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/MyConnection.cs" id="snippet":::

<a name="gotchas"></a>

### <a name="pipereader-common-problems"></a><span data-ttu-id="96a09-229">Problemas comuns do PipeReader</span><span class="sxs-lookup"><span data-stu-id="96a09-229">PipeReader common problems</span></span>

* <span data-ttu-id="96a09-230">Passar os valores incorretos para `consumed` ou `examined` pode resultar na leitura de dados já lidos.</span><span class="sxs-lookup"><span data-stu-id="96a09-230">Passing the wrong values to `consumed` or `examined` may result in reading already read data.</span></span>
* <span data-ttu-id="96a09-231">Passar `buffer.End` como examinado pode resultar em:</span><span class="sxs-lookup"><span data-stu-id="96a09-231">Passing `buffer.End` as examined may result in:</span></span>

  * <span data-ttu-id="96a09-232">Dados interrompidos</span><span class="sxs-lookup"><span data-stu-id="96a09-232">Stalled data</span></span>
  * <span data-ttu-id="96a09-233">Possivelmente uma exceção de memória insuficiente (OOM) se os dados não forem consumidos.</span><span class="sxs-lookup"><span data-stu-id="96a09-233">Possibly an eventual Out of Memory (OOM) exception if data isn't consumed.</span></span> <span data-ttu-id="96a09-234">Por exemplo, `PipeReader.AdvanceTo(position, buffer.End)` ao processar uma única mensagem por vez do buffer.</span><span class="sxs-lookup"><span data-stu-id="96a09-234">For example, `PipeReader.AdvanceTo(position, buffer.End)` when processing a single message at a time from the buffer.</span></span>

* <span data-ttu-id="96a09-235">Passar os valores incorretos para `consumed` ou `examined` pode resultar em um loop infinito.</span><span class="sxs-lookup"><span data-stu-id="96a09-235">Passing the wrong values to `consumed` or `examined` may result in an infinite loop.</span></span> <span data-ttu-id="96a09-236">Por exemplo, `PipeReader.AdvanceTo(buffer.Start)` se não alterado, fará com que `buffer.Start` a próxima chamada a `PipeReader.ReadAsync` seja retornada imediatamente antes que novos dados cheguem.</span><span class="sxs-lookup"><span data-stu-id="96a09-236">For example, `PipeReader.AdvanceTo(buffer.Start)` if `buffer.Start` hasn't changed will cause the next call to `PipeReader.ReadAsync` to return immediately before new data arrives.</span></span>
* <span data-ttu-id="96a09-237">Passar os valores incorretos para `consumed` ou `examined` pode resultar em buffer infinito (OOM eventual).</span><span class="sxs-lookup"><span data-stu-id="96a09-237">Passing the wrong values to `consumed` or `examined` may result in infinite buffering (eventual OOM).</span></span>
* <span data-ttu-id="96a09-238">Usar o `ReadOnlySequence<byte>` após chamar `PipeReader.AdvanceTo` pode resultar em corrupção de memória (use depois de gratuito).</span><span class="sxs-lookup"><span data-stu-id="96a09-238">Using the `ReadOnlySequence<byte>` after calling `PipeReader.AdvanceTo` may result in memory corruption (use after free).</span></span>
* <span data-ttu-id="96a09-239">A falha na chamada `PipeReader.Complete/CompleteAsync` pode resultar em um vazamento de memória.</span><span class="sxs-lookup"><span data-stu-id="96a09-239">Failing to call `PipeReader.Complete/CompleteAsync` may result in a memory leak.</span></span>
* <span data-ttu-id="96a09-240">Verificar <xref:System.IO.Pipelines.ReadResult.IsCompleted?displayProperty=nameWithType> e sair da lógica de leitura antes de processar o buffer resulta em perda de dados.</span><span class="sxs-lookup"><span data-stu-id="96a09-240">Checking <xref:System.IO.Pipelines.ReadResult.IsCompleted?displayProperty=nameWithType> and exiting the reading logic before processing the buffer results in data loss.</span></span> <span data-ttu-id="96a09-241">A condição de saída do loop deve ser baseada em `ReadResult.Buffer.IsEmpty` e `ReadResult.IsCompleted` .</span><span class="sxs-lookup"><span data-stu-id="96a09-241">The loop exit condition should be based on `ReadResult.Buffer.IsEmpty` and `ReadResult.IsCompleted`.</span></span> <span data-ttu-id="96a09-242">Fazer isso incorretamente pode resultar em um loop infinito.</span><span class="sxs-lookup"><span data-stu-id="96a09-242">Doing this incorrectly could result in an infinite loop.</span></span>

#### <a name="problematic-code"></a><span data-ttu-id="96a09-243">Código problemático</span><span class="sxs-lookup"><span data-stu-id="96a09-243">Problematic code</span></span>

<span data-ttu-id="96a09-244">❌**Perda de dados**</span><span class="sxs-lookup"><span data-stu-id="96a09-244">❌ **Data loss**</span></span>

<span data-ttu-id="96a09-245">O `ReadResult` pode retornar o segmento final de dados quando `IsCompleted` é definido como `true` .</span><span class="sxs-lookup"><span data-stu-id="96a09-245">The `ReadResult` can return the final segment of data when `IsCompleted` is set to `true`.</span></span> <span data-ttu-id="96a09-246">Não ler os dados antes de sair do loop de leitura resultará em perda de dados.</span><span class="sxs-lookup"><span data-stu-id="96a09-246">Not reading that data before exiting the read loop will result in data loss.</span></span>

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/DoNotUse.cs" id="snippet":::

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

<span data-ttu-id="96a09-247">❌**Loop infinito**</span><span class="sxs-lookup"><span data-stu-id="96a09-247">❌ **Infinite loop**</span></span>

<span data-ttu-id="96a09-248">A lógica a seguir pode resultar em um loop infinito se o `Result.IsCompleted` for `true` , mas nunca há uma mensagem completa no buffer.</span><span class="sxs-lookup"><span data-stu-id="96a09-248">The following logic may result in an infinite loop if the `Result.IsCompleted` is `true` but there's never a complete message in the buffer.</span></span>

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/DoNotUse.cs" id="snippet2":::

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

<span data-ttu-id="96a09-249">Aqui está outra parte do código com o mesmo problema.</span><span class="sxs-lookup"><span data-stu-id="96a09-249">Here's another piece of code with the same problem.</span></span> <span data-ttu-id="96a09-250">Ele está verificando um buffer não vazio antes de verificar `ReadResult.IsCompleted` .</span><span class="sxs-lookup"><span data-stu-id="96a09-250">It's checking for a non-empty buffer before checking `ReadResult.IsCompleted`.</span></span> <span data-ttu-id="96a09-251">Como ele está em um `else if` , ele fará um loop contínuo se nunca houver uma mensagem completa no buffer.</span><span class="sxs-lookup"><span data-stu-id="96a09-251">Because it's in an `else if`, it will loop forever if there's never a complete message in the buffer.</span></span>

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/DoNotUse.cs" id="snippet3":::

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

<span data-ttu-id="96a09-252">❌**Falha inesperada**</span><span class="sxs-lookup"><span data-stu-id="96a09-252">❌ **Unexpected Hang**</span></span>

<span data-ttu-id="96a09-253">Chamar incondicionalmente `PipeReader.AdvanceTo` com `buffer.End` na `examined` posição pode resultar em suspensões durante a análise de uma única mensagem.</span><span class="sxs-lookup"><span data-stu-id="96a09-253">Unconditionally calling `PipeReader.AdvanceTo` with `buffer.End` in the `examined` position may result in hangs when parsing a single message.</span></span> <span data-ttu-id="96a09-254">A próxima chamada para `PipeReader.AdvanceTo` não retornará até:</span><span class="sxs-lookup"><span data-stu-id="96a09-254">The next call to `PipeReader.AdvanceTo` won't return until:</span></span>

* <span data-ttu-id="96a09-255">Há mais dados gravados no pipe.</span><span class="sxs-lookup"><span data-stu-id="96a09-255">There's more data written to the pipe.</span></span>
* <span data-ttu-id="96a09-256">E os novos dados não foram examinados anteriormente.</span><span class="sxs-lookup"><span data-stu-id="96a09-256">And the new data wasn't previously examined.</span></span>

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/DoNotUse.cs" id="snippet4":::

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

<span data-ttu-id="96a09-257">❌**Memória insuficiente (OOM)**</span><span class="sxs-lookup"><span data-stu-id="96a09-257">❌ **Out of Memory (OOM)**</span></span>

<span data-ttu-id="96a09-258">Com as condições a seguir, o código a seguir mantém o buffer até <xref:System.OutOfMemoryException> ocorrer:</span><span class="sxs-lookup"><span data-stu-id="96a09-258">With the following conditions, the following code keeps buffering until an <xref:System.OutOfMemoryException> occurs:</span></span>

* <span data-ttu-id="96a09-259">Não há tamanho máximo de mensagem.</span><span class="sxs-lookup"><span data-stu-id="96a09-259">There's no maximum message size.</span></span>
* <span data-ttu-id="96a09-260">Os dados retornados de `PipeReader` não fazem uma mensagem completa.</span><span class="sxs-lookup"><span data-stu-id="96a09-260">The data returned from the `PipeReader` doesn't make a complete message.</span></span> <span data-ttu-id="96a09-261">Por exemplo, ele não faz uma mensagem completa porque o outro lado está escrevendo uma mensagem grande (por exemplo, uma mensagem de 4 GB).</span><span class="sxs-lookup"><span data-stu-id="96a09-261">For example, it doesn't make a complete message because the other side is writing a large message (For example, a 4-GB message).</span></span>

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/DoNotUse.cs" id="snippet5":::

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

<span data-ttu-id="96a09-262">❌**Corrupção de memória**</span><span class="sxs-lookup"><span data-stu-id="96a09-262">❌ **Memory Corruption**</span></span>

<span data-ttu-id="96a09-263">Ao escrever auxiliares que lêem o buffer, qualquer carga retornada deve ser copiada antes de chamar `Advance` .</span><span class="sxs-lookup"><span data-stu-id="96a09-263">When writing helpers that read the buffer, any returned payload should be copied before calling `Advance`.</span></span> <span data-ttu-id="96a09-264">O exemplo a seguir retornará a memória que o `Pipe` foi descartada e pode reutilizá-lo para a próxima operação (leitura/gravação).</span><span class="sxs-lookup"><span data-stu-id="96a09-264">The following example will return memory that the `Pipe` has discarded and may reuse it for the next operation (read/write).</span></span>

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/DoNotUse.cs" id="snippetMessage":::

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/DoNotUse.cs" id="snippet6":::

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

## <a name="pipewriter"></a><span data-ttu-id="96a09-265">PipeWriter</span><span class="sxs-lookup"><span data-stu-id="96a09-265">PipeWriter</span></span>

<span data-ttu-id="96a09-266">O <xref:System.IO.Pipelines.PipeWriter> gerencia buffers para gravação em nome do chamador.</span><span class="sxs-lookup"><span data-stu-id="96a09-266">The <xref:System.IO.Pipelines.PipeWriter> manages buffers for writing on the caller's behalf.</span></span> <span data-ttu-id="96a09-267">`PipeWriter` implementa [`IBufferWriter<byte>`](xref:System.Buffers.IBufferWriter%601) .</span><span class="sxs-lookup"><span data-stu-id="96a09-267">`PipeWriter` implements [`IBufferWriter<byte>`](xref:System.Buffers.IBufferWriter%601).</span></span> <span data-ttu-id="96a09-268">`IBufferWriter<byte>` torna possível obter acesso a buffers para executar gravações sem cópias de buffer adicionais.</span><span class="sxs-lookup"><span data-stu-id="96a09-268">`IBufferWriter<byte>` makes it possible to get access to buffers to perform writes without additional buffer copies.</span></span>

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/MyPipeWriter.cs" id="snippet":::

<span data-ttu-id="96a09-269">O código anterior:</span><span class="sxs-lookup"><span data-stu-id="96a09-269">The previous code:</span></span>

* <span data-ttu-id="96a09-270">Solicita um buffer de pelo menos 5 bytes do `PipeWriter` uso do <xref:System.IO.Pipelines.PipeWriter.GetMemory%2A> .</span><span class="sxs-lookup"><span data-stu-id="96a09-270">Requests a buffer of at least 5 bytes from the `PipeWriter` using <xref:System.IO.Pipelines.PipeWriter.GetMemory%2A>.</span></span>
* <span data-ttu-id="96a09-271">Grava bytes para a cadeia de caracteres ASCII no `"Hello"` retornado `Memory<byte>` .</span><span class="sxs-lookup"><span data-stu-id="96a09-271">Writes bytes for the ASCII string `"Hello"` to the returned `Memory<byte>`.</span></span>
* <span data-ttu-id="96a09-272">Chama <xref:System.IO.Pipelines.PipeWriter.Advance%2A> para indicar quantos bytes foram gravados no buffer.</span><span class="sxs-lookup"><span data-stu-id="96a09-272">Calls <xref:System.IO.Pipelines.PipeWriter.Advance%2A> to indicate how many bytes were written to the buffer.</span></span>
* <span data-ttu-id="96a09-273">Libera o `PipeWriter` , que envia os bytes para o dispositivo subjacente.</span><span class="sxs-lookup"><span data-stu-id="96a09-273">Flushes the `PipeWriter`, which sends the bytes to the underlying device.</span></span>

<span data-ttu-id="96a09-274">O método anterior de gravação usa os buffers fornecidos pelo `PipeWriter` .</span><span class="sxs-lookup"><span data-stu-id="96a09-274">The previous method of writing uses the buffers provided by the `PipeWriter`.</span></span> <span data-ttu-id="96a09-275">Como alternativa, <xref:System.IO.Pipelines.PipeWriter.WriteAsync%2A?displayProperty=nameWithType> :</span><span class="sxs-lookup"><span data-stu-id="96a09-275">Alternatively, <xref:System.IO.Pipelines.PipeWriter.WriteAsync%2A?displayProperty=nameWithType>:</span></span>

* <span data-ttu-id="96a09-276">Copia o buffer existente para o `PipeWriter` .</span><span class="sxs-lookup"><span data-stu-id="96a09-276">Copies the existing buffer to the `PipeWriter`.</span></span>
* <span data-ttu-id="96a09-277">Chamadas `GetSpan` , `Advance` conforme apropriado e chamadas <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A> .</span><span class="sxs-lookup"><span data-stu-id="96a09-277">Calls `GetSpan`, `Advance` as appropriate and calls <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A>.</span></span>

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/MyPipeWriter.cs" id="snippet2":::

### <a name="cancellation"></a><span data-ttu-id="96a09-278">Cancelamento</span><span class="sxs-lookup"><span data-stu-id="96a09-278">Cancellation</span></span>

<span data-ttu-id="96a09-279"><xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A> dá suporte à passagem de um <xref:System.Threading.CancellationToken> .</span><span class="sxs-lookup"><span data-stu-id="96a09-279"><xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A> supports passing a <xref:System.Threading.CancellationToken>.</span></span> <span data-ttu-id="96a09-280">Passar um `CancellationToken` resultado em um `OperationCanceledException` se o token for cancelado enquanto houver uma liberação pendente.</span><span class="sxs-lookup"><span data-stu-id="96a09-280">Passing a `CancellationToken` results in an `OperationCanceledException` if the token is canceled while there's a flush pending.</span></span> <span data-ttu-id="96a09-281">`PipeWriter.FlushAsync` dá suporte a uma maneira de cancelar a operação de liberação atual por meio <xref:System.IO.Pipelines.PipeWriter.CancelPendingFlush%2A?displayProperty=nameWithType> de sem gerar uma exceção.</span><span class="sxs-lookup"><span data-stu-id="96a09-281">`PipeWriter.FlushAsync` supports a way to cancel the current flush operation via <xref:System.IO.Pipelines.PipeWriter.CancelPendingFlush%2A?displayProperty=nameWithType> without raising an exception.</span></span> <span data-ttu-id="96a09-282">`PipeWriter.CancelPendingFlush`A chamada faz com que a chamada atual ou próxima chame `PipeWriter.FlushAsync` ou `PipeWriter.WriteAsync` retorne um <xref:System.IO.Pipelines.FlushResult> com `IsCanceled` definido como `true` .</span><span class="sxs-lookup"><span data-stu-id="96a09-282">Calling `PipeWriter.CancelPendingFlush` causes the current or next call to `PipeWriter.FlushAsync` or `PipeWriter.WriteAsync` to return a <xref:System.IO.Pipelines.FlushResult> with `IsCanceled` set to `true`.</span></span> <span data-ttu-id="96a09-283">Isso pode ser útil para interromper a liberação de rendimento de forma não destrutiva e não excepcional.</span><span class="sxs-lookup"><span data-stu-id="96a09-283">This can be useful for halting the yielding flush in a non-destructive and non-exceptional way.</span></span>

<a name="pwcp"></a>

### <a name="pipewriter-common-problems"></a><span data-ttu-id="96a09-284">Problemas comuns do PipeWriter</span><span class="sxs-lookup"><span data-stu-id="96a09-284">PipeWriter common problems</span></span>

* <span data-ttu-id="96a09-285"><xref:System.IO.Pipelines.PipeWriter.GetSpan%2A> e <xref:System.IO.Pipelines.PipeWriter.GetMemory%2A> retornam um buffer com pelo menos a quantidade solicitada de memória.</span><span class="sxs-lookup"><span data-stu-id="96a09-285"><xref:System.IO.Pipelines.PipeWriter.GetSpan%2A> and <xref:System.IO.Pipelines.PipeWriter.GetMemory%2A> return a buffer with at least the requested amount of memory.</span></span> <span data-ttu-id="96a09-286">**Não** presuma os tamanhos de buffer exatos.</span><span class="sxs-lookup"><span data-stu-id="96a09-286">**Don't** assume exact buffer sizes.</span></span>
* <span data-ttu-id="96a09-287">Não há nenhuma garantia de que as chamadas sucessivas retornarão o mesmo buffer ou o buffer de mesmo tamanho.</span><span class="sxs-lookup"><span data-stu-id="96a09-287">There's no guarantee that successive calls will return the same buffer or the same-sized buffer.</span></span>
* <span data-ttu-id="96a09-288">Um novo buffer deve ser solicitado após <xref:System.IO.Pipelines.PipeWriter.Advance%2A> a chamada para continuar gravando mais dados.</span><span class="sxs-lookup"><span data-stu-id="96a09-288">A new buffer must be requested after calling <xref:System.IO.Pipelines.PipeWriter.Advance%2A> to continue writing more data.</span></span> <span data-ttu-id="96a09-289">Não é possível gravar no buffer adquirido anteriormente.</span><span class="sxs-lookup"><span data-stu-id="96a09-289">The previously acquired buffer can't be written to.</span></span>
* <span data-ttu-id="96a09-290">Chamar `GetMemory` ou `GetSpan` embora haja uma chamada incompleta para `FlushAsync` não é seguro.</span><span class="sxs-lookup"><span data-stu-id="96a09-290">Calling `GetMemory` or `GetSpan` while there's an incomplete call to `FlushAsync` isn't safe.</span></span>
* <span data-ttu-id="96a09-291">Chamar `Complete` ou `CompleteAsync` embora haja dados não liberados pode resultar em corrupção de memória.</span><span class="sxs-lookup"><span data-stu-id="96a09-291">Calling `Complete` or `CompleteAsync` while there's unflushed data can result in memory corruption.</span></span>

## <a name="iduplexpipe"></a><span data-ttu-id="96a09-292">IDuplexPipe</span><span class="sxs-lookup"><span data-stu-id="96a09-292">IDuplexPipe</span></span>

<span data-ttu-id="96a09-293">O <xref:System.IO.Pipelines.IDuplexPipe> é um contrato para tipos que dão suporte à leitura e gravação.</span><span class="sxs-lookup"><span data-stu-id="96a09-293">The <xref:System.IO.Pipelines.IDuplexPipe> is a contract for types that support both reading and writing.</span></span> <span data-ttu-id="96a09-294">Por exemplo, uma conexão de rede seria representada por um `IDuplexPipe` .</span><span class="sxs-lookup"><span data-stu-id="96a09-294">For example, a network connection would be represented by an `IDuplexPipe`.</span></span>

 <span data-ttu-id="96a09-295">Ao contrário de `Pipe` , que contém um `PipeReader` e um `PipeWriter` , `IDuplexPipe` representa um único lado de uma conexão Full duplex.</span><span class="sxs-lookup"><span data-stu-id="96a09-295">Unlike `Pipe`, which contains a `PipeReader` and a `PipeWriter`, `IDuplexPipe` represents a single side of a full duplex connection.</span></span> <span data-ttu-id="96a09-296">Isso significa que o que é gravado no `PipeWriter` não será lido no `PipeReader` .</span><span class="sxs-lookup"><span data-stu-id="96a09-296">That means what is written to the `PipeWriter` will not be read from the `PipeReader`.</span></span>

## <a name="streams"></a><span data-ttu-id="96a09-297">Fluxos</span><span class="sxs-lookup"><span data-stu-id="96a09-297">Streams</span></span>

<span data-ttu-id="96a09-298">Ao ler ou gravar dados de fluxo, você normalmente lê dados usando um desserializador e grava dados usando um serializador.</span><span class="sxs-lookup"><span data-stu-id="96a09-298">When reading or writing stream data, you typically read data using a de-serializer and write data using a serializer.</span></span> <span data-ttu-id="96a09-299">A maioria dessas APIs de leitura e gravação de fluxo tem um `Stream` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="96a09-299">Most of these read and write stream APIs have a `Stream` parameter.</span></span> <span data-ttu-id="96a09-300">Para facilitar a integração com essas APIs existentes `PipeReader` e `PipeWriter` expor um <xref:System.IO.Pipelines.PipeReader.AsStream%2A> método.</span><span class="sxs-lookup"><span data-stu-id="96a09-300">To make it easier to integrate with these existing APIs, `PipeReader` and `PipeWriter` expose an <xref:System.IO.Pipelines.PipeReader.AsStream%2A> method.</span></span> <span data-ttu-id="96a09-301"><xref:System.IO.Pipelines.PipeWriter.AsStream%2A> Retorna uma `Stream` implementação em relação ao `PipeReader` ou ao `PipeWriter` .</span><span class="sxs-lookup"><span data-stu-id="96a09-301"><xref:System.IO.Pipelines.PipeWriter.AsStream%2A> returns a `Stream` implementation around the `PipeReader` or `PipeWriter`.</span></span>

### <a name="stream-example"></a><span data-ttu-id="96a09-302">Exemplo de fluxo</span><span class="sxs-lookup"><span data-stu-id="96a09-302">Stream example</span></span>

<span data-ttu-id="96a09-303">`PipeReader``PipeWriter`as instâncias e podem ser criadas usando os métodos estáticos de `Create` acordo com um <xref:System.IO.Stream> objeto e as opções de criação correspondentes opcionais.</span><span class="sxs-lookup"><span data-stu-id="96a09-303">`PipeReader` and `PipeWriter` instances can be created using the static `Create` methods given a <xref:System.IO.Stream> object and optional corresponding creation options.</span></span>

<span data-ttu-id="96a09-304">O <xref:System.IO.Pipelines.StreamPipeReaderOptions> Permitir controle sobre a criação da `PipeReader` instância com os seguintes parâmetros:</span><span class="sxs-lookup"><span data-stu-id="96a09-304">The <xref:System.IO.Pipelines.StreamPipeReaderOptions> allow for control over the creation of the `PipeReader` instance with the following parameters:</span></span>

- <span data-ttu-id="96a09-305"><xref:System.IO.Pipelines.StreamPipeReaderOptions.BufferSize?displayProperty=nameWithType> é o tamanho mínimo do buffer em bytes usado ao aluguel a memória do pool e usa como padrão `4096` .</span><span class="sxs-lookup"><span data-stu-id="96a09-305"><xref:System.IO.Pipelines.StreamPipeReaderOptions.BufferSize?displayProperty=nameWithType> is the minimum buffer size in bytes used when renting memory from the pool, and defaults to `4096`.</span></span>
- <span data-ttu-id="96a09-306"><xref:System.IO.Pipelines.StreamPipeReaderOptions.LeaveOpen?displayProperty=nameWithType> sinalizador determina se o fluxo subjacente é deixado aberto após a `PipeReader` conclusão e o padrão é `false` .</span><span class="sxs-lookup"><span data-stu-id="96a09-306"><xref:System.IO.Pipelines.StreamPipeReaderOptions.LeaveOpen?displayProperty=nameWithType> flag determines whether or not the underlying stream is left open after the `PipeReader` completes, and defaults to `false`.</span></span>
- <span data-ttu-id="96a09-307"><xref:System.IO.Pipelines.StreamPipeReaderOptions.MinimumReadSize?displayProperty=nameWithType> representa o limite de bytes restantes no buffer antes de um novo buffer ser alocado e o padrão é `1024` .</span><span class="sxs-lookup"><span data-stu-id="96a09-307"><xref:System.IO.Pipelines.StreamPipeReaderOptions.MinimumReadSize?displayProperty=nameWithType> represents the threshold of remaining bytes in the buffer before a new buffer is allocated, and defaults to `1024`.</span></span>
- <span data-ttu-id="96a09-308"><xref:System.IO.Pipelines.StreamPipeReaderOptions.Pool?displayProperty=nameWithType> é `MemoryPool<byte>` usado ao alocar memória e usa como padrão `null` .</span><span class="sxs-lookup"><span data-stu-id="96a09-308"><xref:System.IO.Pipelines.StreamPipeReaderOptions.Pool?displayProperty=nameWithType> is the `MemoryPool<byte>` used when allocating memory, and defaults to `null`.</span></span>

<span data-ttu-id="96a09-309">O <xref:System.IO.Pipelines.StreamPipeWriterOptions> Permitir controle sobre a criação da `PipeWriter` instância com os seguintes parâmetros:</span><span class="sxs-lookup"><span data-stu-id="96a09-309">The <xref:System.IO.Pipelines.StreamPipeWriterOptions> allow for control over the creation of the `PipeWriter` instance with the following parameters:</span></span>

- <span data-ttu-id="96a09-310"><xref:System.IO.Pipelines.StreamPipeWriterOptions.LeaveOpen?displayProperty=nameWithType> sinalizador determina se o fluxo subjacente é deixado aberto após a `PipeWriter` conclusão e o padrão é `false` .</span><span class="sxs-lookup"><span data-stu-id="96a09-310"><xref:System.IO.Pipelines.StreamPipeWriterOptions.LeaveOpen?displayProperty=nameWithType> flag determines whether or not the underlying stream is left open after the `PipeWriter` completes, and defaults to `false`.</span></span>
- <span data-ttu-id="96a09-311"><xref:System.IO.Pipelines.StreamPipeWriterOptions.MinimumBufferSize?displayProperty=nameWithType> representa o tamanho mínimo do buffer a ser usado ao aluguel a memória do <xref:System.IO.Pipelines.StreamPipeWriterOptions.Pool> e o padrão é `4096` .</span><span class="sxs-lookup"><span data-stu-id="96a09-311"><xref:System.IO.Pipelines.StreamPipeWriterOptions.MinimumBufferSize?displayProperty=nameWithType> represents the minimum buffer size to use when renting memory from the <xref:System.IO.Pipelines.StreamPipeWriterOptions.Pool>, and defaults to `4096`.</span></span>
- <span data-ttu-id="96a09-312"><xref:System.IO.Pipelines.StreamPipeWriterOptions.Pool?displayProperty=nameWithType> é `MemoryPool<byte>` usado ao alocar memória e usa como padrão `null` .</span><span class="sxs-lookup"><span data-stu-id="96a09-312"><xref:System.IO.Pipelines.StreamPipeWriterOptions.Pool?displayProperty=nameWithType> is the `MemoryPool<byte>` used when allocating memory, and defaults to `null`.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="96a09-313">Ao criar `PipeReader` e `PipeWriter` instâncias usando os `Create` métodos, você precisa considerar o `Stream` tempo de vida do objeto.</span><span class="sxs-lookup"><span data-stu-id="96a09-313">When creating `PipeReader` and `PipeWriter` instances using the `Create` methods, you need to consider the `Stream` object lifetime.</span></span> <span data-ttu-id="96a09-314">Se você precisar de acesso ao fluxo depois que o leitor ou o gravador for feito com ele, você precisará definir o `LeaveOpen` sinalizador como `true` nas opções de criação.</span><span class="sxs-lookup"><span data-stu-id="96a09-314">If you need access to the stream after the reader or writer is done with it, you'll need to set the `LeaveOpen` flag to `true` on the creation options.</span></span> <span data-ttu-id="96a09-315">Caso contrário, o fluxo será fechado.</span><span class="sxs-lookup"><span data-stu-id="96a09-315">Otherwise, the stream will be closed.</span></span>

<span data-ttu-id="96a09-316">O código a seguir demonstra a criação `PipeReader` de `PipeWriter` instâncias e usando os `Create` métodos de um fluxo.</span><span class="sxs-lookup"><span data-stu-id="96a09-316">The following code demonstrates the creation of `PipeReader` and `PipeWriter` instances using the `Create` methods from a stream.</span></span>

:::code language="csharp" source="snippets/pipelines/Program.cs":::

<span data-ttu-id="96a09-317">O aplicativo usa um <xref:System.IO.StreamReader> para ler o arquivo de *lorem-ipsum.txt* como um fluxo.</span><span class="sxs-lookup"><span data-stu-id="96a09-317">The application uses a <xref:System.IO.StreamReader> to read the *lorem-ipsum.txt* file as a stream.</span></span> <span data-ttu-id="96a09-318">O <xref:System.IO.FileStream> é passado para <xref:System.IO.Pipelines.PipeReader.Create%2A?displayProperty=nameWithType> , que instancia um `PipeReader` objeto.</span><span class="sxs-lookup"><span data-stu-id="96a09-318">The <xref:System.IO.FileStream> is passed to <xref:System.IO.Pipelines.PipeReader.Create%2A?displayProperty=nameWithType>, which instantiates a `PipeReader` object.</span></span> <span data-ttu-id="96a09-319">Em seguida, o aplicativo de console passa seu fluxo de saída padrão para o <xref:System.IO.Pipelines.PipeWriter.Create%2A?displayProperty=nameWithType> usando <xref:System.Console.OpenStandardOutput?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="96a09-319">The console application then passes its standard output stream to <xref:System.IO.Pipelines.PipeWriter.Create%2A?displayProperty=nameWithType> using <xref:System.Console.OpenStandardOutput?displayProperty=nameWithType>.</span></span> <span data-ttu-id="96a09-320">O exemplo dá suporte ao [cancelamento](#cancellation).</span><span class="sxs-lookup"><span data-stu-id="96a09-320">The example supports [cancellation](#cancellation).</span></span>
