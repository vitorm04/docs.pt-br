### <a name="unexpected-invalidcastexception-from-invokemethod-activity-in-wf4"></a>InvalidCastException inesperado da atividade InvokeMethod em WF4

|   |   |
|---|---|
|Detalhes|Usar um <xref:System.Activities.Statements.InvokeMethod> direcionado a um método com um parâmetro anulável pode gerar um <xref:System.InvalidCastException?displayProperty=name>.|
|Sugestão|Esse comportamento foi revertido em uma versão de serviço do .NET Framework 4.5. Atualize o .NET Framework 4.5 ou faça upgrade para o .NET Framework 4.5.1 ou posterior para corrigir esse problema.|
|Escopo|Secundário|
|Versão|4.5|
|Tipo|Tempo de execução|
|APIs afetadas|<ul><li><xref:System.Activities.Statements.InvokeMethod.Parameters?displayProperty=nameWithType></li></ul>|
|Analisadores|<ul><li>CD0088</li></ul>|

