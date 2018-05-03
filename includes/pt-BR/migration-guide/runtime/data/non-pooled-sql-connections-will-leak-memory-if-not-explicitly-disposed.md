### <a name="non-pooled-sql-connections-will-leak-memory-if-not-explicitly-disposed"></a>Conexões SQL não em pool causarão vazamento de memória se não forem explicitamente descartadas

|   |   |
|---|---|
|Detalhes|No .NET Framework 4.5, conexões SQL não em pool que não são explicitamente expostas (via Dispose, Close ou using) terão vazamento de memória|
|Sugestão|Esse problema foi corrigido uma atualização de manutenção do .NET Framework 4.5. Atualize o .NET Framework 4.5 ou faça upgrade para o .NET Framework 4.5.1 ou posterior para corrigir esse problema. Como alternativa, esse problema pode ser evitado usando o <xref:System.Data.SqlClient.SqlConnection?displayProperty=name> em um padrão &#39;using&#39; (que é uma prática recomendada) ou explicitamente chamando Dispose ou Close quando a conexão não é mais necessária.|
|Escopo|Microsoft Edge|
|Versão|4.5|
|Tipo|Tempo de execução|
|APIs afetadas|<ul><li><xref:System.Data.SqlClient.SqlConnection.%23ctor(System.String)?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnection.%23ctor(System.String%2CSystem.Data.SqlClient.SqlCredential)?displayProperty=nameWithType></li></ul>|

