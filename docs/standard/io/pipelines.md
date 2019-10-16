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
# <a name="systemiopipelines-in-net"></a>System. IO. pipelines no .NET

<xref:System.IO.Pipelines> é uma nova biblioteca projetada para facilitar a execução de e/s de alto desempenho no .NET. É uma biblioteca direcionada .NET Standard que funciona em todas as implementações do .NET.

<a name="solve"></a>

## <a name="what-problem-does-systemiopipelines-solve"></a>Qual problema o System. IO. pipelines resolve
<!-- corner case doesn't MT (machine translate)   -->
Aplicativos que analisam dados de streaming são compostos por código clichê com muitos fluxos de código especializados e incomuns. O código de caso clichê e especial é complexo e difícil de manter.

o `System.IO.Pipelines` foi arquitetado para:

* Ter dados de streaming de análise de alto desempenho.
* Reduza a complexidade do código.

O código a seguir é típico para um servidor TCP que recebe mensagens delimitadas por linha (delimitadas por `'\n'`) de um cliente:

```csharp
async Task ProcessLinesAsync(NetworkStream stream)
{
    var buffer = new byte[1024];
    await stream.ReadAsync(buffer, 0, buffer.Length);
    
    // Process a single line from the buffer
    ProcessLine(buffer);
}
```

O código anterior tem vários problemas:

* A mensagem inteira (fim da linha) não pode ser recebida em uma única chamada para `ReadAsync`.
* Ele está ignorando o resultado de `stream.ReadAsync`. `stream.ReadAsync` retorna a quantidade de dados lidos.
* Ele não manipula o caso em que várias linhas são lidas em uma única chamada `ReadAsync`.
* Ele aloca uma matriz `byte` com cada leitura.

Para corrigir os problemas anteriores, as seguintes alterações são necessárias:

* Armazenar os dados de entrada em buffer até que uma nova linha seja encontrada.
* Analise todas as linhas retornadas no buffer.
* É possível que a linha seja maior que 1 KB (1024 bytes). O código precisa redimensionar o buffer de entrada até que o delimitador seja encontrado para ajustar a linha completa dentro do buffer.

  * Se o buffer for redimensionado, mais cópias de buffer serão feitas conforme as linhas mais longas aparecerem na entrada.
  * Para reduzir o espaço desperdiçado, compacte o buffer usado para ler as linhas.

* Considere o uso do pool de buffers para evitar a alocação repetida de memória.
* O código a seguir aborda alguns desses problemas:

[!code-csharp[](~/samples/snippets/csharp/pipelines/ProcessLinesAsync.cs?name=snippet)]

O código anterior é complexo e não aborda todos os problemas identificados. A rede de alto desempenho geralmente significa escrever código muito complexo para maximizar o desempenho. o `System.IO.Pipelines` foi criado para facilitar a gravação desse tipo de código.

## <a name="pipe"></a>Conexão

A classe <xref:System.IO.Pipelines.Pipe> pode ser usada para criar um par de `PipeWriter/PipeReader`. Todos os dados gravados no `PipeWriter` estão disponíveis no `PipeReader`:

[!code-csharp[](~/samples/snippets/csharp/pipelines/Pipe.cs?name=snippet2)]

<a name="pbu"></a>

### <a name="pipe-basic-usage"></a>Uso básico do pipe

[!code-csharp[](~/samples/snippets/csharp/pipelines/Pipe.cs?name=snippet)]

Há dois loops:

* `FillPipeAsync` lê do `Socket` e grava no `PipeWriter`.
* `ReadPipeAsync` lê do `PipeReader` e analisa as linhas de entrada.

Não há buffers explícitos alocados. Todo o gerenciamento de buffer é delegado para as implementações `PipeReader` e `PipeWriter`. A delegação do gerenciamento de buffer facilita o consumo do código para se concentrar exclusivamente na lógica de negócios.

No primeiro loop:

* <xref:System.IO.Pipelines.PipeWriter.GetMemory(System.Int32)?displayProperty=nameWithType> é chamado para obter memória do gravador subjacente.
* <xref:System.IO.Pipelines.PipeWriter.Advance(System.Int32)?displayProperty=nameWithType> é chamado para informar ao `PipeWriter` a quantidade de dados gravada no buffer.
* <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A?displayProperty=nameWithType> é chamado para disponibilizar os dados para o `PipeReader`.

No segundo loop, o `PipeReader` consome os buffers gravados por `PipeWriter`. Os buffers são provenientes do soquete. A chamada para `PipeReader.ReadAsync`:

* Retorna um <xref:System.IO.Pipelines.ReadResult> que contém duas partes importantes de informações:

  * Os dados que foram lidos na forma de `ReadOnlySequence<byte>`.
  * Um booliano `IsCompleted` que indica se o fim dos dados (EOF) foi atingido. 

Depois de encontrar o delimitador de fim de linha (EOL) e analisar a linha:

* A lógica processa o buffer para ignorar o que já foi processado.
* `PipeReader.AdvanceTo` é chamado para informar ao `PipeReader` a quantidade de dados consumida e examinada.

Os loops de leitor e gravador terminam chamando `Complete`. `Complete` permite que o pipe subjacente libere a memória alocada.

### <a name="backpressure-and-flow-control"></a>Controle de fluxo e de pressão

Idealmente, a leitura e a análise funcionam em conjunto:

* O thread de gravação consome dados da rede e os coloca em buffers.
* O thread de análise é responsável por construir as estruturas de dados apropriadas.

Normalmente, a análise leva mais tempo do que apenas copiar blocos de dados da rede:

* O thread de leitura fica à frente do thread de análise.
* O thread de leitura precisa diminuir ou alocar mais memória para armazenar os dados para o thread de análise.

Para um desempenho ideal, há um equilíbrio entre pausas frequentes e alocação de mais memória.

Para resolver o problema anterior, o `Pipe` tem duas configurações para controlar o fluxo de dados:

* <xref:System.IO.Pipelines.PipeOptions.PauseWriterThreshold>: determina a quantidade de dados que deve ser armazenada em buffer antes de chamadas para <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A> pausa.
* <xref:System.IO.Pipelines.PipeOptions.ResumeWriterThreshold>: determina a quantidade de dados que o leitor deve observar antes de chamadas para a retomada de `PipeWriter.FlushAsync`.

![Diagrama com ResumeWriterThreshold e PauseWriterThreshold](./media/pipelines/resume-pause.png)

<xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A?displayProperty=nameWithType>:

* Retorna um `ValueTask<FlushResult>` incompleto quando a quantidade de dados no `Pipe` cruza `PauseWriterThreshold`.
* Conclui `ValueTask<FlushResult>` quando se torna inferior a `ResumeWriterThreshold`.

Dois valores são usados para evitar o ciclo rápido, que pode ocorrer se um valor for usado.

### <a name="examples"></a>Exemplos

```csharp
// The Pipe will start returning incomplete tasks from FlushAsync until
// the reader examines at least 5 bytes.
var options = new PipeOptions(pauseWriterThreshold: 10, resumeWriterThreshold: 5);
var pipe = new Pipe(options);
```

### <a name="pipescheduler"></a>PipeScheduler

Normalmente, ao usar `async` e `await`, o código assíncrono é retomado em um <xref:System.Threading.Tasks.TaskScheduler> ou no <xref:System.Threading.SynchronizationContext> atual.

Ao fazer e/s, é importante ter um controle refinado sobre onde a e/s é executada. Esse controle permite aproveitar os caches de CPU com eficiência. O cache eficiente é essencial para aplicativos de alto desempenho, como servidores Web. <xref:System.IO.Pipelines.PipeScheduler> fornece controle sobre o local em que os retornos de chamada assíncronos são executados. Por padrão:

* O <xref:System.Threading.SynchronizationContext> atual é usado.
* Se não houver `SynchronizationContext`, ele usará o pool de threads para executar retornos de chamada.

[!code-csharp[](~/samples/snippets/csharp/pipelines/Program.cs?name=snippet)]

[PipeScheduler. ThreadPool](xref:System.IO.Pipelines.PipeScheduler.ThreadPool) é a implementação <xref:System.IO.Pipelines.PipeScheduler> que enfileira os retornos de chamada para o pool de threads. `PipeScheduler.ThreadPool` é o padrão e geralmente é a melhor opção. [PipeScheduler. Inline](xref:System.IO.Pipelines.PipeScheduler.Inline) pode causar consequências indesejadas, como deadlocks.

### <a name="pipe-reset"></a>Redefinição de pipe

Com frequência, é eficiente reutilizar o objeto `Pipe`. Para redefinir o pipe, chame <xref:System.IO.Pipelines.PipeReader> <xref:System.IO.Pipelines.Pipe.Reset%2A> quando o `PipeReader` e `PipeWriter` estiverem concluídos.

## <a name="pipereader"></a>PipeReader

<xref:System.IO.Pipelines.PipeReader> gerencia a memória em nome do chamador. **Sempre** chame <xref:System.IO.Pipelines.PipeReader.AdvanceTo%2A?displayProperty=nameWithType> depois de chamar <xref:System.IO.Pipelines.PipeReader.ReadAsync%2A?displayProperty=nameWithType>. Isso permite que o `PipeReader` saiba quando o chamador é concluído com a memória para que possa ser acompanhado. O `ReadOnlySequence<byte>` retornado de `PipeReader.ReadAsync` é válido somente até que a chamada seja a `PipeReader.AdvanceTo`. É ilegal usar `ReadOnlySequence<byte>` depois de chamar `PipeReader.AdvanceTo`.

`PipeReader.AdvanceTo` usa dois argumentos <xref:System.SequencePosition>:

* O primeiro argumento determina a quantidade de memória consumida.
* O segundo argumento determina o quanto do buffer foi observado.

Marcar dados como consumidos significa que o pipe pode retornar a memória para o pool de buffers subjacente. Marcar dados como observados controla o que a próxima chamada para `PipeReader.ReadAsync` faz. Marcar tudo como observado significa que a próxima chamada para `PipeReader.ReadAsync` não retornará até que haja mais dados gravados no pipe. Qualquer outro valor fará com que a próxima chamada para `PipeReader.ReadAsync` retorne imediatamente com os dados observados *e* não observados, mas os dados que já foram consumidos.

### <a name="read-streaming-data-scenarios"></a>Ler cenários de dados de streaming

Há alguns padrões típicos que surgem ao tentar ler dados de streaming:

* Dado um fluxo de dados, analise uma única mensagem.
* Dado um fluxo de dados, analise todas as mensagens disponíveis.

Os exemplos a seguir usam o método `TryParseMessage` para analisar mensagens de um `ReadOnlySequence<byte>`. `TryParseMessage` analisa uma única mensagem e atualiza o buffer de entrada para cortar a mensagem analisada do buffer. `TryParseMessage` não faz parte do .NET, é um método escrito pelo usuário usado nas seções a seguir.

```csharp
bool TryParseMessage(ref ReadOnlySequence<byte> buffer, out Message message);
```

### <a name="read-a-single-message"></a>Ler uma única mensagem

O código a seguir lê uma única mensagem de um `PipeReader` e a retorna ao chamador.

[!code-csharp[ReadSingleMsg](~/samples/snippets/csharp/pipelines/ReadSingleMsg.cs?name=snippet)]

O código anterior:

* Analisa uma única mensagem.
* Atualiza o `SequencePosition` consumido e examinado `SequencePosition` para apontar para o início do buffer de entrada cortado.

Os dois argumentos `SequencePosition` são atualizados porque `TryParseMessage` remove a mensagem analisada do buffer de entrada. Geralmente, ao analisar uma única mensagem do buffer, a posição examinada deve ser uma das seguintes:

* O fim da mensagem.
* O final do buffer recebido se nenhuma mensagem for encontrada.

O caso de mensagem única tem o maior potencial para erros. Passar os valores incorretos para *examinados* pode resultar em uma exceção de memória insuficiente ou um loop infinito. Para obter mais informações, consulte a seção [problemas comuns do PipeReader](#gotchas) neste artigo.

### <a name="reading-multiple-messages"></a>Lendo várias mensagens

O código a seguir lê todas as mensagens de um `PipeReader` e chama `ProcessMessageAsync` em cada.

[!code-csharp[MyConnection1](~/samples/snippets/csharp/pipelines/MyConnection1.cs?name=snippet)]

### <a name="cancellation"></a>Cancelamento

`PipeReader.ReadAsync`:

* Dá suporte à passagem de um <xref:System.Threading.CancellationToken>.
* Gera um <xref:System.OperationCanceledException> se o `CancellationToken` for cancelado enquanto houver uma leitura pendente.
* Dá suporte a uma maneira de cancelar a operação de leitura atual por meio de <xref:System.IO.Pipelines.PipeReader.CancelPendingRead%2A?displayProperty=nameWithType>, o que evita a geração de uma exceção. Chamar `PipeReader.CancelPendingRead` faz com que a chamada atual ou próxima para `PipeReader.ReadAsync` retorne um <xref:System.IO.Pipelines.ReadResult> com `IsCanceled` definido como `true`. Isso pode ser útil para interromper o loop de leitura existente de forma não destrutiva e não excepcional.

[!code-csharp[MyConnection](~/samples/snippets/csharp/pipelines/MyConnection.cs?name=snippet)]

<a name="gotchas"></a>

### <a name="pipereader-common-problems"></a>Problemas comuns do PipeReader

* Passar os valores errados para `consumed` ou `examined` pode resultar na leitura de dados já lidos.
* Passar `buffer.End` como examinado pode resultar em:

  * Dados interrompidos
  * Possivelmente uma exceção de memória insuficiente (OOM) se os dados não forem consumidos. Por exemplo, `PipeReader.AdvanceTo(position, buffer.End)` ao processar uma única mensagem por vez do buffer.

* Passar os valores errados para `consumed` ou `examined` pode resultar em um loop infinito. Por exemplo, `PipeReader.AdvanceTo(buffer.Start)` se `buffer.Start` não for alterado fará com que a próxima chamada para `PipeReader.ReadAsync` seja retornada imediatamente antes que novos dados cheguem.
* Passar os valores errados para `consumed` ou `examined` pode resultar em buffer infinito (OOM eventual).
* Usar o `ReadOnlySequence<byte>` após chamar `PipeReader.AdvanceTo` pode resultar em corrupção de memória (use depois de gratuito).
* A falha ao chamar `PipeReader.Complete/CompleteAsync` pode resultar em um vazamento de memória.
* Verificar <xref:System.IO.Pipelines.ReadResult.IsCompleted?displayProperty=nameWithType> e sair da lógica de leitura antes de processar o buffer resulta em perda de dados. A condição de saída do loop deve ser baseada em `ReadResult.Buffer.IsEmpty` e `ReadResult.IsCompleted`. Fazer isso incorretamente pode resultar em um loop infinito.

#### <a name="problematic-code"></a>Código problemático

**perda de dados** de ❌

O `ReadResult` pode retornar o segmento final de dados quando `IsCompleted` é definido como `true`. Não ler os dados antes de sair do loop de leitura resultará em perda de dados.

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#1](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

**loop infinito** ❌

A lógica a seguir pode resultar em um loop infinito se o `Result.IsCompleted` for `true`, mas nunca houver uma mensagem completa no buffer.

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#2](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet2)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

Aqui está outra parte do código com o mesmo problema. Ele está verificando um buffer não vazio antes de verificar `ReadResult.IsCompleted`. Como está em um `else if`, ele entrará em loop para sempre se nunca houver uma mensagem completa no buffer.

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#3](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet3)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

❌ **falha inesperada**

Chamar incondicionalmente `PipeReader.AdvanceTo` com `buffer.End` na posição `examined` pode resultar em travas ao analisar uma única mensagem. A próxima chamada para `PipeReader.AdvanceTo` não retornará até:

* Há mais dados gravados no pipe.
* E os novos dados não foram examinados anteriormente.

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#4](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet4)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

❌ **memória insuficiente (OOM)**

Com as condições a seguir, o código a seguir mantém o buffer até que um <xref:System.OutOfMemoryException> ocorra:

* Não há tamanho máximo de mensagem.
* Os dados retornados do `PipeReader` não fazem uma mensagem completa. Por exemplo, ele não faz uma mensagem completa porque o outro lado está escrevendo uma mensagem grande (por exemplo, uma mensagem de 4 GB).

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#5](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet5)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

**corrupção de memória** de ❌

Ao escrever auxiliares que lêem o buffer, qualquer carga retornada deve ser copiada antes de chamar `Advance`. O exemplo a seguir retornará a memória informando que o `Pipe` foi descartado e poderá reutilizá-lo para a próxima operação (leitura/gravação).

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#Message](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippetMessage)]

[!code-csharp[DoNotUse#6](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet6)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

## <a name="pipewriter"></a>PipeWriter

O <xref:System.IO.Pipelines.PipeWriter> gerencia buffers para gravação em nome do chamador. `PipeWriter` implementa [`IBufferWriter<byte>`](xref:System.Buffers.IBufferWriter`1). `IBufferWriter<byte>` torna possível obter acesso a buffers para executar gravações sem cópias de buffer adicionais.

[!code-csharp[MyPipeWriter](~/samples/snippets/csharp/pipelines/MyPipeWriter.cs?name=snippet)]

O código anterior:

* Solicita um buffer de pelo menos 5 bytes do `PipeWriter` usando <xref:System.IO.Pipelines.PipeWriter.GetSpan%2A>.
* Grava bytes para a cadeia de caracteres ASCII `"Hello"` no @no__t retornado-1.
* Chama <xref:System.IO.Pipelines.PipeWriter.Advance%2A> para indicar quantos bytes foram gravados no buffer.
* Libera o `PipeWriter`, que envia os bytes para o dispositivo subjacente.

O método anterior de gravação usa os buffers fornecidos pelo `PipeWriter`. Como alternativa, <xref:System.IO.Pipelines.PipeWriter.WriteAsync%2A?displayProperty=nameWithType>:

* Copia o buffer existente para o `PipeWriter`.
* Chama `GetSpan`, `Advance` conforme apropriado e chama <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A>.

[!code-csharp[MyPipeWriter#2](~/samples/snippets/csharp/pipelines/MyPipeWriter.cs?name=snippet2)]

### <a name="cancellation"></a>Cancelamento

<xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A> dá suporte à passagem de um <xref:System.Threading.CancellationToken>. Passar um `CancellationToken` resultará em um `OperationCanceledException` se o token for cancelado enquanto houver uma liberação pendente. `PipeWriter.FlushAsync` dá suporte a uma maneira de cancelar a operação de liberação atual por meio de <xref:System.IO.Pipelines.PipeWriter.CancelPendingFlush%2A?displayProperty=nameWithType> sem gerar uma exceção. Chamar `PipeWriter.CancelPendingFlush` faz com que a chamada atual ou seguinte para `PipeWriter.FlushAsync` ou `PipeWriter.WriteAsync` retorne um <xref:System.IO.Pipelines.FlushResult> com `IsCanceled` definido como `true`. Isso pode ser útil para interromper a liberação de rendimento de forma não destrutiva e não excepcional.

<a name="pwcp"></a>

### <a name="pipewriter-common-problems"></a>Problemas comuns do PipeWriter

* <xref:System.IO.Pipelines.PipeWriter.GetSpan%2A> e <xref:System.IO.Pipelines.PipeWriter.GetMemory%2A> retornam um buffer com pelo menos a quantidade solicitada de memória. **Não** presuma os tamanhos de buffer exatos.
* Não há nenhuma garantia de que as chamadas sucessivas retornarão o mesmo buffer ou o buffer de mesmo tamanho.
* Um novo buffer deve ser solicitado depois de chamar <xref:System.IO.Pipelines.PipeWriter.Advance%2A> para continuar gravando mais dados. Não é possível gravar no buffer adquirido anteriormente.
* Chamar `GetMemory` ou `GetSpan` enquanto houver uma chamada incompleta para `FlushAsync` não é seguro.
* Chamar `Complete` ou `CompleteAsync` enquanto houver dados não liberados pode resultar em corrupção de memória.

## <a name="iduplexpipe"></a>IDuplexPipe

O <xref:System.IO.Pipelines.IDuplexPipe> é um contrato para tipos que dão suporte à leitura e gravação. Por exemplo, uma conexão de rede seria representada por um `IDuplexPipe`.

 Ao contrário de `Pipe` que contém um `PipeReader` e um `PipeWriter`, `IDuplexPipe` representa um único lado de uma conexão Full duplex. Isso significa que o que é gravado no `PipeWriter` não será lido no `PipeReader`.

## <a name="streams"></a>Fluxos

Ao ler ou gravar dados de fluxo, você normalmente lê dados usando um desserializador e grava dados usando um serializador. A maioria dessas APIs de leitura e gravação de fluxo tem um parâmetro `Stream`. Para facilitar a integração com essas APIs existentes, `PipeReader` e `PipeWriter` expõem um <xref:System.IO.Pipelines.PipeReader.AsStream%2A>.  <xref:System.IO.Pipelines.PipeWriter.AsStream%2A> retorna uma implementação `Stream` em relação ao `PipeReader` ou `PipeWriter`.
