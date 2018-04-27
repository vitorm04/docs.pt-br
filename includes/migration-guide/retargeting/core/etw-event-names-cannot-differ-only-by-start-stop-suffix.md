### <a name="etw-event-names-cannot-differ-only-by-a-start-or-stop-suffix"></a>Nomes de evento ETW não podem ser diferentes apenas por um sufixo "Start" ou "Stop"

|   |   |
|---|---|
|Detalhes|No .NET Framework 4.6 e 4.6.1, o tempo de execução gera uma <xref:System.ArgumentException> quando dois nomes de evento ETW (Rastreamento de Eventos para Windows) diferem somente por um sufixo &quot;Start&quot; ou &quot;Stop&quot; (como quando um evento é denominado <code>LogUser</code> e outro é denominado <code>LogUserStart</code>). Nesse caso, o tempo de execução não pode construir a origem do evento, que não pode emitir nenhum log.|
|Sugestão|Para evitar a exceção, certifique-se de que nenhum dos dois nomes de eventos difiram somente por um sufixo &quot;Start&quot; ou &quot;Stop&quot;. Esse requisito foi removido a partir do .NET Framework 4.6.2. O tempo de execução pode resolver a ambiguidade de nomes de evento que diferem somente pelos sufixos &quot;Start&quot; e &quot;Stop&quot;.|
|Escopo|Microsoft Edge|
|Versão|4.6|
|Tipo|Redirecionando|

