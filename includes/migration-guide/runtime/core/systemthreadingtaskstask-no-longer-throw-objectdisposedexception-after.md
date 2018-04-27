### <a name="systemthreadingtaskstask-no-longer-throw-objectdisposedexception-after-object-is-disposed"></a>System.Threading.Tasks.Task não gera mais ObjectDisposedException depois que o objeto é descartado

|   |   |
|---|---|
|Detalhes|Exceto por <xref:System.Threading.Tasks.Task.System%23IAsyncResult%23AsyncWaitHandle>, os métodos <xref:System.Threading.Tasks.Task?displayProperty=name>não geram mais uma exceção <xref:System.ObjectDisposedException?displayProperty=name> após o objeto ser descartado. Essa alteração permite o uso de tarefas em cache. Por exemplo, um método pode retornar uma tarefa em cache para representar uma operação já concluída em vez de alocar uma nova tarefa. Isso era impossível nas versões anteriores do .NET Framework porque qualquer consumidor da tarefa poderia descartá-los, o que a tornava inutilizável.|
|Sugestão|Lembre-se de que os métodos Task podem não gerar mais <xref:System.ObjectDisposedException?displayProperty=name> nos casos em que o objeto é descartado. Se um aplicativo dependia dessa exceção para saber que uma tarefa foi descartada, ele deverá ser atualizado para verificar explicitamente o status da tarefa usando <xref:System.Threading.Tasks.Task.Status>.|
|Escopo|Secundário|
|Versão|4.5|
|Tipo|Tempo de execução|

