### <a name="change-in-behavior-for-taskwaitall-methods-with-time-out-arguments"></a>Mudança no comportamento de métodos Task.WaitAll com argumentos de tempo limite

|   |   |
|---|---|
|Detalhes|O comportamento de Task.WaitAll ficou mais consistente no .NET 4.5. No .NET Framework 4, esses métodos se comportavam de forma inconsistente. Quando o tempo limite expirou, se uma ou mais tarefas foram concluídas ou canceladas antes da chamada de método, o método lançou uma exceção <xref:System.AggregateException?displayProperty=name>. Quando o tempo limite expirava, se nenhuma tarefa tivesse sido concluída ou cancelada antes da chamada de método, mas uma ou mais tarefas tivessem entrado nesses estados após a chamada de método, o método retornava false.<br/><br/>No .NET Framework 4.5, essas sobrecargas de método agora retornam false se alguma tarefa ainda está em execução quando o intervalo de tempo limite expira e geram uma exceção <xref:System.AggregateException?displayProperty=name> somente se uma tarefa de entrada é cancelada (não importa se antes ou depois da chamada de método) e nenhuma outra tarefa ainda está em execução.|
|Sugestão|Se um <xref:System.AggregateException?displayProperty=name> estava sendo capturado como um meio de detectar uma tarefa que foi cancelada antes da chamada WaitAll ser invocada, esse código deverá fazer a mesma detecção por meio da propriedade IsCanceled (por exemplo: .Any(t =&gt; t.IsCanceled)), uma vez que o .NET 4.6 acionará esse caso apenas se todas as tarefas esperadas forem concluídas antes do tempo limite.|
|Escopo|Secundário|
|Versão|4.5|
|Tipo|Tempo de execução|
|APIs afetadas|<ul><li><xref:System.Threading.Tasks.Task.WaitAll(System.Threading.Tasks.Task[],System.Int32)?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.WaitAll(System.Threading.Tasks.Task[],System.Int32,System.Threading.CancellationToken)?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.WaitAll(System.Threading.Tasks.Task[],System.TimeSpan)?displayProperty=nameWithType></li></ul>|

