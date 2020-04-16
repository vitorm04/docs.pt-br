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
# <a name="systemiopipelines-in-net"></a>Pipelines system.IO.em .NET

<xref:System.IO.Pipelines>é uma nova biblioteca projetada para facilitar a realização de I/O de alto desempenho em .NET. É uma biblioteca direcionada ao .NET Standard que funciona em todas as implementações .NET.

<a name="solve"></a>

## <a name="what-problem-does-systemiopipelines-solve"></a>Que problema o System.IO.Pipelines resolve

<!-- corner case doesn't MT (machine translate)   -->
Os aplicativos que analisam os dados de streaming são compostos de código de caldeira com muitos fluxos de código especializados e incomuns. A caldeira e o código de caso especial são complexos e difíceis de manter.

`System.IO.Pipelines`foi arquitetado para:

* Tenha dados de streaming de análise de alto desempenho.
* Reduza a complexidade do código.

O código a seguir é típico de um servidor TCP que `'\n'`recebe mensagens delimitadas de linha (delimitadas por ) de um cliente:

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

* A mensagem inteira (fim da linha) pode `ReadAsync`não ser recebida em uma única chamada para .
* Está ignorando o resultado `stream.ReadAsync`de. `stream.ReadAsync`retorna quantos dados foram lidos.
* Ele não lida com o caso em que `ReadAsync` várias linhas são lidas em uma única chamada.
* Ele aloca `byte` uma matriz a cada leitura.

Para corrigir os problemas anteriores, são necessárias as seguintes alterações:

* Tampe os dados de entrada até que uma nova linha seja encontrada.
* Analise todas as linhas devolvidas no buffer.
* É possível que a linha seja maior que 1 KB (1024 bytes). O código precisa redimensionar o buffer de entrada até que o delimitador seja encontrado para encaixar a linha completa dentro do buffer.

  * Se o buffer for redimensionado, mais cópias de buffer serão feitas à medida que linhas mais longas aparecerem na entrada.
  * Para reduzir o espaço desperdiçado, compacte o buffer usado para leitura de linhas.

* Considere usar o buffer pooling para evitar alocar a memória repetidamente.
* O código a seguir aborda alguns desses problemas:

[!code-csharp[](~/samples/snippets/csharp/pipelines/ProcessLinesAsync.cs?name=snippet)]

O código anterior é complexo e não resolve todos os problemas identificados. Rede de alto desempenho geralmente significa escrever código muito complexo para maximizar o desempenho. `System.IO.Pipelines`foi projetado para facilitar a escrita deste tipo de código.

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

## <a name="pipe"></a>Pipe

A <xref:System.IO.Pipelines.Pipe> classe pode ser `PipeWriter/PipeReader` usada para criar um par. Todos os dados `PipeWriter` gravados `PipeReader`no está disponível no:

[!code-csharp[](~/samples/snippets/csharp/pipelines/Pipe.cs?name=snippet2)]

<a name="pbu"></a>

### <a name="pipe-basic-usage"></a>Uso básico do tubo

[!code-csharp[](~/samples/snippets/csharp/pipelines/Pipe.cs?name=snippet)]

Há dois loops:

* `FillPipeAsync`lê do `Socket` e escreve `PipeWriter`para o .
* `ReadPipeAsync`lê a `PipeReader` partir das linhas de entrada e analisa.

Não há buffers explícitos alocados. Toda a gestão de `PipeReader` `PipeWriter` buffer é delegada para as implementações. Delegar o gerenciamento de buffer satisfaz que o consumo de código se concentre apenas na lógica do negócio.

No primeiro loop:

* <xref:System.IO.Pipelines.PipeWriter.GetMemory(System.Int32)?displayProperty=nameWithType>é chamado para obter memória do escritor subjacente.
* <xref:System.IO.Pipelines.PipeWriter.Advance(System.Int32)?displayProperty=nameWithType>é chamado para `PipeWriter` dizer quantos dados foram escritos para o buffer.
* <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A?displayProperty=nameWithType>é chamado para disponibilizar os `PipeReader`dados para o .

No segundo loop, `PipeReader` o consome os `PipeWriter`buffers escritos por . Os buffers vêm do soquete. A chamada `PipeReader.ReadAsync`para:

* Retorna <xref:System.IO.Pipelines.ReadResult> um que contém duas informações importantes:

  * Os dados que foram lidos na forma de `ReadOnlySequence<byte>`.
  * Um booleano `IsCompleted` que indica se o fim dos dados (EOF) foi atingido.

Depois de encontrar o delimitador final da linha (EOL) e analisar a linha:

* A lógica processa o buffer para pular o que já está processado.
* `PipeReader.AdvanceTo`é chamado para `PipeReader` dizer quantos dados foram consumidos e examinados.

Os loops de leitor `Complete`e escritor terminam chamando . `Complete`permite que o tubo subjacente libere a memória que ele alocou.

### <a name="backpressure-and-flow-control"></a>Backpressure e controle de fluxo

Idealmente, a leitura e o trabalho de análise em conjunto:

* O segmento de escrita consome dados da rede e os coloca em buffers.
* O segmento de análise é responsável pela construção das estruturas de dados apropriadas.

Normalmente, a análise leva mais tempo do que apenas copiar blocos de dados da rede:

* O fio de leitura fica à frente do fio de análise.
* O segmento de leitura tem que diminuir ou alocar mais memória para armazenar os dados para o segmento de análise.

Para um desempenho ideal, há um equilíbrio entre pausas frequentes e alocação de mais memória.

Para resolver o problema `Pipe` anterior, o tem duas configurações para controlar o fluxo de dados:

* <xref:System.IO.Pipelines.PipeOptions.PauseWriterThreshold>: Determina quantos dados devem ser <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A> protegidos antes das chamadas pausarem.
* <xref:System.IO.Pipelines.PipeOptions.ResumeWriterThreshold>: Determina quantos dados o leitor tem `PipeWriter.FlushAsync` que observar antes das chamadas para retomar.

![Diagrama com resumeWriterThreshold e PauseWriterThreshold](./media/pipelines/resume-pause.png)

<xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A?displayProperty=nameWithType>:

* Retorna um `ValueTask<FlushResult>` incompleto quando a `Pipe` quantidade `PauseWriterThreshold`de dados nas cruzes .
* Completa `ValueTask<FlushResult>` quando se torna `ResumeWriterThreshold`mais baixo do que .

Dois valores são usados para prevenir o ciclismo rápido, o que pode ocorrer se um valor for usado.

### <a name="examples"></a>Exemplos

```csharp
// The Pipe will start returning incomplete tasks from FlushAsync until
// the reader examines at least 5 bytes.
var options = new PipeOptions(pauseWriterThreshold: 10, resumeWriterThreshold: 5);
var pipe = new Pipe(options);
```

### <a name="pipescheduler"></a>PipeScheduler

Normalmente, `async` ao `await`usar e, o código assíncrono é retomado em um <xref:System.Threading.Tasks.TaskScheduler> ou na corrente <xref:System.Threading.SynchronizationContext>.

Ao fazer I/O, é importante ter controle fino sobre onde a I/O é realizada. Este controle permite tirar vantagem dos caches da CPU de forma eficaz. O cache eficiente é fundamental para aplicativos de alto desempenho, como servidores web. <xref:System.IO.Pipelines.PipeScheduler>fornece controle sobre onde os retornos assíncronos são executados. Por padrão:

* A <xref:System.Threading.SynchronizationContext> corrente é usada.
* Se não `SynchronizationContext`houver, ele usa o pool de segmentos para executar retornos de chamadas.

[!code-csharp[](~/samples/snippets/csharp/pipelines/Program.cs?name=snippet)]

[PipeScheduler.ThreadPool](xref:System.IO.Pipelines.PipeScheduler.ThreadPool) é <xref:System.IO.Pipelines.PipeScheduler> a implementação que faz filas de retorno saqueado no pool de segmentos. `PipeScheduler.ThreadPool`é o padrão e geralmente a melhor escolha. [PipeScheduler.Inline](xref:System.IO.Pipelines.PipeScheduler.Inline) pode causar consequências não intencionais, como impasses.

### <a name="pipe-reset"></a>Reset de tubulação

É freqüentemente eficiente reutilizar `Pipe` o objeto. Para reiniciar o tubo, <xref:System.IO.Pipelines.PipeReader> <xref:System.IO.Pipelines.Pipe.Reset%2A> ligue `PipeReader` `PipeWriter` quando ambos estiverem completos.

## <a name="pipereader"></a>PipeReader

<xref:System.IO.Pipelines.PipeReader>gerencia a memória em nome do chamador. **Sempre** <xref:System.IO.Pipelines.PipeReader.AdvanceTo%2A?displayProperty=nameWithType> ligue <xref:System.IO.Pipelines.PipeReader.ReadAsync%2A?displayProperty=nameWithType>depois de ligar. Isso permite `PipeReader` saber quando o chamador é feito com a memória para que ele possa ser rastreado. O `ReadOnlySequence<byte>` retorno `PipeReader.ReadAsync` só é válido até `PipeReader.AdvanceTo`a chamada do . É ilegal usar `ReadOnlySequence<byte>` depois `PipeReader.AdvanceTo`de ligar.

`PipeReader.AdvanceTo`leva <xref:System.SequencePosition> dois argumentos:

* O primeiro argumento determina quanta memória foi consumida.
* O segundo argumento determina quanto do buffer foi observado.

Marcar dados como consumidos significa que o tubo pode retornar a memória para o pool de buffer subjacente. Marcar dados como observado controla o `PipeReader.ReadAsync` que a próxima chamada faz. Marcar tudo como observado significa que `PipeReader.ReadAsync` a próxima chamada não retornará até que haja mais dados escritos no tubo. Qualquer outro valor fará a `PipeReader.ReadAsync` próxima chamada para retornar imediatamente com os dados observados *e* não observados, mas não dados que já foram consumidos.

### <a name="read-streaming-data-scenarios"></a>Leia cenários de dados de streaming

Existem alguns padrões típicos que surgem ao tentar ler dados de streaming:

* Dado um fluxo de dados, analise uma única mensagem.
* Dado um fluxo de dados, analise todas as mensagens disponíveis.

Os exemplos a `TryParseMessage` seguir usam o método para `ReadOnlySequence<byte>`analisar mensagens de a . `TryParseMessage`analisa uma única mensagem e atualiza o buffer de entrada para aparar a mensagem analisado do buffer. `TryParseMessage`não faz parte do .NET, é um método escrito pelo usuário usado nas seguintes seções.

```csharp
bool TryParseMessage(ref ReadOnlySequence<byte> buffer, out Message message);
```

### <a name="read-a-single-message"></a>Leia uma única mensagem

O código a seguir lê `PipeReader` uma única mensagem de um e devolve-a ao chamador.

[!code-csharp[ReadSingleMsg](~/samples/snippets/csharp/pipelines/ReadSingleMsg.cs?name=snippet)]

O código anterior:

* Analisa uma única mensagem.
* Atualiza o `SequencePosition` consumido e `SequencePosition` examinado para apontar para o início do buffer de entrada aparado.

Os `SequencePosition` dois argumentos `TryParseMessage` são atualizados porque remove a mensagem analisado do buffer de entrada. Geralmente, ao analisar uma única mensagem do buffer, a posição examinada deve ser uma das seguintes:

* O fim da mensagem.
* O fim do buffer recebido se nenhuma mensagem foi encontrada.

O caso de mensagem única tem o maior potencial para erros. Passar os valores errados para *examinados* pode resultar em uma exceção fora da memória ou um loop infinito. Para obter mais informações, consulte a seção [problemas comuns do PipeReader](#gotchas) neste artigo.

### <a name="reading-multiple-messages"></a>Lendo várias mensagens

O código a seguir lê `PipeReader` todas `ProcessMessageAsync` as mensagens de a e chama cada um.

[!code-csharp[MyConnection1](~/samples/snippets/csharp/pipelines/MyConnection1.cs?name=snippet)]

### <a name="cancellation"></a>Cancelamento

`PipeReader.ReadAsync`:

* Suporta passar <xref:System.Threading.CancellationToken>um .
* Joga <xref:System.OperationCanceledException> um `CancellationToken` se o for cancelado enquanto há uma leitura pendente.
* Apoia uma maneira de cancelar a <xref:System.IO.Pipelines.PipeReader.CancelPendingRead%2A?displayProperty=nameWithType>operação de leitura atual via , o que evita aumentar uma exceção. A `PipeReader.CancelPendingRead` chamada faz com `PipeReader.ReadAsync` que a <xref:System.IO.Pipelines.ReadResult> `IsCanceled` chamada `true`atual ou próxima retorne a um com set para . Isso pode ser útil para parar o loop de leitura existente de uma forma não destrutiva e não excepcional.

[!code-csharp[MyConnection](~/samples/snippets/csharp/pipelines/MyConnection.cs?name=snippet)]

<a name="gotchas"></a>

### <a name="pipereader-common-problems"></a>Problemas comuns do PipeReader

* Passar os valores errados para `consumed` ou `examined` pode resultar na leitura de dados já lidos.
* Passar `buffer.End` como examinado pode resultar em:

  * Dados paralisados
  * Possivelmente uma eventual exceção fora da memória (OOM) se os dados não forem consumidos. Por exemplo, `PipeReader.AdvanceTo(position, buffer.End)` ao processar uma única mensagem de cada vez a partir do buffer.

* Passar os valores errados para `consumed` ou `examined` pode resultar em um loop infinito. Por `PipeReader.AdvanceTo(buffer.Start)` exemplo, `buffer.Start` se não tiver sido alterado `PipeReader.ReadAsync` fará com que a próxima chamada retorne imediatamente antes que novos dados cheguem.
* Passar os valores errados para `consumed` ou `examined` pode resultar em buffering infinito (eventual OOM).
* O `ReadOnlySequence<byte>` uso `PipeReader.AdvanceTo` da chamada pós-chamada pode resultar em corrupção de memória (uso após a liberdade).
* Não ligar `PipeReader.Complete/CompleteAsync` pode resultar em um vazamento de memória.
* Verificar <xref:System.IO.Pipelines.ReadResult.IsCompleted?displayProperty=nameWithType> e sair da lógica de leitura antes de processar o buffer resulta em perda de dados. A condição de saída `ReadResult.Buffer.IsEmpty` do `ReadResult.IsCompleted`loop deve ser baseada em e . Fazer isso incorretamente pode resultar em um loop infinito.

#### <a name="problematic-code"></a>Código problemático

❌**Perda de dados**

O `ReadResult` pode retornar o segmento `IsCompleted` final `true`de dados quando é definido para . Não ler esses dados antes de sair do loop de leitura resultará em perda de dados.

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#1](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

❌**Loop infinito**

A seguinte lógica pode resultar em `Result.IsCompleted` `true` um loop infinito se for, mas nunca há uma mensagem completa no buffer.

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#2](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet2)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

Aqui está outro código com o mesmo problema. Está verificando se há um buffer não `ReadResult.IsCompleted`vazio antes de verificar . Porque ele está `else if`em um , ele vai loop para sempre se nunca há uma mensagem completa no buffer.

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#3](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet3)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

❌**Hang inesperado**

Chamar `PipeReader.AdvanceTo` incondicionalmente com `buffer.End` na `examined` posição pode resultar em travamentos ao analisar uma única mensagem. A próxima `PipeReader.AdvanceTo` chamada não retornará até:

* Há mais dados escritos no tubo.
* E os novos dados não foram examinados anteriormente.

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#4](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet4)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

❌**Fora da memória (OOM)**

Com as seguintes condições, o seguinte <xref:System.OutOfMemoryException> código continua a ser tamponado até que ocorra um:

* Não há tamanho máximo de mensagem.
* Os dados devolvidos `PipeReader` do não fazem uma mensagem completa. Por exemplo, ele não faz uma mensagem completa porque o outro lado está escrevendo uma mensagem grande (por exemplo, uma mensagem de 4 GB).

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#5](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet5)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

❌**Corrupção de memória**

Ao escrever ajudantes que lêem o buffer, qualquer carga `Advance`de carga retornada deve ser copiada antes de ligar . O exemplo a seguir `Pipe` retornará a memória que o tem descartado e poderá reutilizá-la para a próxima operação (ler/gravar).

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#Message](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippetMessage)]

[!code-csharp[DoNotUse#6](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet6)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

## <a name="pipewriter"></a>PipeWriter

Os <xref:System.IO.Pipelines.PipeWriter> buffers gerenciapara escrever em nome do chamador. `PipeWriter`implementos [`IBufferWriter<byte>`](xref:System.Buffers.IBufferWriter%601). `IBufferWriter<byte>`torna possível ter acesso a buffers para executar gravações sem cópias de buffer adicionais.

[!code-csharp[MyPipeWriter](~/samples/snippets/csharp/pipelines/MyPipeWriter.cs?name=snippet)]

O código anterior:

* Solicita um buffer de pelo menos `PipeWriter` 5 <xref:System.IO.Pipelines.PipeWriter.GetMemory%2A>bytes do uso .
* Escreve bytes para a `"Hello"` seqüência `Memory<byte>`ASCII para o retornado .
* Chamadas <xref:System.IO.Pipelines.PipeWriter.Advance%2A> para indicar quantos bytes foram escritos para o buffer.
* Lava o `PipeWriter`, que envia os bytes para o dispositivo subjacente.

O método anterior de escrita usa os `PipeWriter`buffers fornecidos pelo . Alternativamente, <xref:System.IO.Pipelines.PipeWriter.WriteAsync%2A?displayProperty=nameWithType>:

* Copia o buffer existente `PipeWriter`para o .
* `GetSpan`Chamadas, `Advance` conforme apropriado <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A>e chamadas.

[!code-csharp[MyPipeWriter#2](~/samples/snippets/csharp/pipelines/MyPipeWriter.cs?name=snippet2)]

### <a name="cancellation"></a>Cancelamento

<xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A>suporta passar <xref:System.Threading.CancellationToken>um . Passando `CancellationToken` um resultado `OperationCanceledException` em um se o token é cancelado enquanto há um flush pendente. `PipeWriter.FlushAsync`suporta uma maneira de cancelar a <xref:System.IO.Pipelines.PipeWriter.CancelPendingFlush%2A?displayProperty=nameWithType> operação de flush atual via sem levantar uma exceção. A `PipeWriter.CancelPendingFlush` chamada faz com `PipeWriter.FlushAsync` que `PipeWriter.WriteAsync` a <xref:System.IO.Pipelines.FlushResult> chamada `IsCanceled` atual `true`ou próxima para ou para retornar um com set para . Isso pode ser útil para parar o flush de rendimento de uma forma não destrutiva e não excepcional.

<a name="pwcp"></a>

### <a name="pipewriter-common-problems"></a>Problemas comuns do PipeWriter

* <xref:System.IO.Pipelines.PipeWriter.GetSpan%2A>e <xref:System.IO.Pipelines.PipeWriter.GetMemory%2A> retornar um buffer com pelo menos a quantidade solicitada de memória. **Não assuma** tamanhos exatos de buffer.
* Não há garantia de que as chamadas sucessivas retornarão o mesmo buffer ou o buffer do mesmo tamanho.
* Um novo buffer deve ser <xref:System.IO.Pipelines.PipeWriter.Advance%2A> solicitado após a chamada para continuar a escrever mais dados. O buffer adquirido anteriormente não pode ser escrito para.
* Ligar `GetMemory` `GetSpan` ou enquanto houver uma `FlushAsync` chamada incompleta não é seguro.
* Ligar `Complete` `CompleteAsync` ou enquanto houver dados não lavados pode resultar em corrupção de memória.

## <a name="iduplexpipe"></a>IDuplexPipe

O <xref:System.IO.Pipelines.IDuplexPipe> é um contrato para tipos que suportam tanto a leitura quanto a escrita. Por exemplo, uma conexão de `IDuplexPipe`rede seria representada por um .

 Ao `Pipe` contrário `PipeReader` do `PipeWriter`que `IDuplexPipe` contém a e a, representa um único lado de uma conexão duplex completa. Isso significa que o `PipeWriter` que está escrito `PipeReader`para o não será lido a partir do .

## <a name="streams"></a>Fluxos

Ao ler ou escrever dados de fluxo, você normalmente lê dados usando um desserializador e escreve dados usando um serializador. A maioria dessas APIs de `Stream` fluxo de leitura e gravação tem um parâmetro. Para facilitar a integração com essas `PipeReader` APIs existentes e `PipeWriter` expor uma <xref:System.IO.Pipelines.PipeReader.AsStream%2A>.  <xref:System.IO.Pipelines.PipeWriter.AsStream%2A>retorna `Stream` uma implementação em torno do `PipeReader` ou `PipeWriter`.
