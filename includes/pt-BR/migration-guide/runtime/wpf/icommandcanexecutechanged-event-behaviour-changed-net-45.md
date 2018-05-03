### <a name="icommandcanexecutechanged-event-behaviour-changed-in-net-45"></a>O comportamento do evento ICommand.CanExecuteChanged foi alterado no .NET 4.5

|   |   |
|---|---|
|Detalhes|No .NET Framework 4.5, um <xref:System.Windows.Input.ICommand.CanExecuteChanged?displayProperty=name> era ignorado, a menos que o remetente do evento fosse o mesmo objeto que o objeto que acionou o evento. Esse bug foi corrigido nas atualizações de manutenção do .NET Framework 4.5.|
|Sugestão|Esse bug foi corrigido nas versões de serviço do .NET Framework 4.5, de modo que ele pode ser evitado garantindo que o .NET Framework seja atualizado ou fazendo upgrade para o .NET Framework 4.5.1. Como alternativa, o código do aplicativo que usa <xref:System.Windows.Input.ICommand?displayProperty=name> pode ser modificado para garantir que o remetente, ao acionar um comando <xref:System.Windows.Input.ICommand.CanExecuteChanged?displayProperty=name>, seja o mesmo que o objeto que aciona o evento.|
|Escopo|Secundário|
|Versão|4.5|
|Tipo|Tempo de execução|
|APIs afetadas|<ul><li><xref:System.Windows.Input.ICommand.CanExecuteChanged?displayProperty=nameWithType></li></ul>|
|Analisadores|<ul><li>CD0084</li></ul>|

