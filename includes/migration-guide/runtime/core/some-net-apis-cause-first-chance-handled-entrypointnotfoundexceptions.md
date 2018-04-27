### <a name="some-net-apis-cause-first-chance-handled-entrypointnotfoundexceptions"></a>Algumas APIs .NET causam EntryPointNotFoundExceptions de primeira chance

|   |   |
|---|---|
|Detalhes|No .NET Framework 4.5, um pequeno número de métodos .NET começou a gerar <xref:System.EntryPointNotFoundException?displayProperty=name>s de primeira chance. Essas exceções eram tratadas dentro do .NET Framework, mas poderiam interromper a automação de teste que não esperava as exceções de primeira chance. Essas mesmas APIs interrompem alguns cenários ApiVerifier quando HighVersionLie é habilitado.|
|Sugestão|Esse bug pode ser evitado com a o upgrade para o .NET Framework 4.5.1. Como alternativa, a automação de teste pode ser atualizada para não interromper <xref:System.EntryPointNotFoundException?displayProperty=name> de primeira chance.|
|Escopo|Microsoft Edge|
|Versão|4.5|
|Tipo|Tempo de execução|
|APIs afetadas|<ul><li><xref:System.Diagnostics.Debug.Assert(System.Boolean)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Debug.Assert(System.Boolean,System.String)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Debug.Assert(System.Boolean,System.String,System.String)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Debug.Assert(System.Boolean,System.String,System.String,System.Object[])?displayProperty=nameWithType></li><li><xref:System.Xml.Serialization.XmlSerializer.%23ctor(System.Type)?displayProperty=nameWithType></li></ul>|

