### <a name="adonet-now-attempts-to-automatically-reconnect-broken-sql-connections"></a>Agora, ADO.NET tentará reconectar automaticamente conexões SQL interrompidas

|   |   |
|---|---|
|Detalhes|A partir do .NET Framework 4.5.1, o .NET Framework tentará reconectar automaticamente conexões SQL interrompidas. Embora, normalmente, isso torne os aplicativos mais confiáveis, há casos de borda em que um aplicativo precisa saber que a conexão foi perdida para tomar medidas sobre a reconexão.|
|Sugestão|Se esse recurso for indesejável devido a preocupações de compatibilidade, ele poderá ser desabilitado por meio da configuração da propriedade <xref:System.Data.SqlClient.SqlConnectionStringBuilder.ConnectRetryCount?displayProperty=name> de uma cadeia de conexão (ou <xref:System.Data.SqlClient.SqlConnectionStringBuilder?displayProperty=name>) para 0.|
|Escopo|Microsoft Edge|
|Versão|4.5.1|
|Tipo|Tempo de execução|
|APIs afetadas|<ul><li><xref:System.Data.IDbConnection.ConnectionString?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnection.ConnectionString?displayProperty=nameWithType></li><li><xref:System.Configuration.ConnectionStringSettings.ConnectionString?displayProperty=nameWithType></li><li><xref:System.Data.Common.DbConnection.ConnectionString?displayProperty=nameWithType></li><li><xref:System.Data.Common.DbConnectionStringBuilder.ConnectionString?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnectionStringBuilder.%23ctor?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnectionStringBuilder.%23ctor(System.String)?displayProperty=nameWithType></li><li><xref:System.Data.Common.DbConnectionStringBuilder.%23ctor?displayProperty=nameWithType></li><li><xref:System.Data.Common.DbConnectionStringBuilder.%23ctor(System.Boolean)?displayProperty=nameWithType></li></ul>|

