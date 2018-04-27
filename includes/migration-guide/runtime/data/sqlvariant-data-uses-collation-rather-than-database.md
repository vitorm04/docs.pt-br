### <a name="sqlvariant-data-uses-sqlvariant-collation-rather-than-database-collation"></a>Os dados do Sql_variant usam o agrupamento sql_variant em vez do agrupamento de banco de dados

|   |   |
|---|---|
|Detalhes|Os dados do <code>sql_variant</code> usam o agrupamento <code>sql_variant</code> em vez do agrupamento de banco de dados.|
|Sugestão|Essa alteração aborda o possível corrompimento de dados caso a conferência do banco de dados seja diferente da conferência <code>sql_variant</code>. Os aplicativos que dependem de dados corrompidos podem apresentar falhas.|
|Escopo|Transparente|
|Versão|4.5|
|Tipo|Tempo de execução|

