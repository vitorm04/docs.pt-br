### <a name="eventlistener-truncates-strings-with-embedded-nulls"></a>EventListener trunca cadeias de caracteres com nulos inseridos

|   |   |
|---|---|
|Detalhes|<xref:System.Diagnostics.Tracing.EventListener?displayProperty=name> trunca cadeias de caracteres com nulos inseridos. Os caracteres nulos não são compatíveis com a classe <xref:System.Diagnostics.Tracing.EventSource?displayProperty=name>. A alteração afeta apenas os aplicativos que usam <xref:System.Diagnostics.Tracing.EventListener?displayProperty=name> para ler dados <xref:System.Diagnostics.Tracing.EventSource?displayProperty=name> no processo e que usam caracteres nulos como delimitadores.|
|Sugestão|Os dados <xref:System.Diagnostics.Tracing.EventSource?displayProperty=name> devem ser atualizados, se possível, para não usar caracteres nulos inseridos.|
|Escopo|Microsoft Edge|
|Versão|4.5.1|
|Tipo|Tempo de execução|
|APIs afetadas|<ul><li><xref:System.Diagnostics.Tracing.EventListener.%23ctor?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel,System.Diagnostics.Tracing.EventKeywords)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel,System.Diagnostics.Tracing.EventKeywords,System.Collections.Generic.IDictionary{System.String,System.String})?displayProperty=nameWithType></li></ul>|

