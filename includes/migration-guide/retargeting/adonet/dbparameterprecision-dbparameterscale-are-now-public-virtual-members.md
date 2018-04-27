### <a name="dbparameterprecision-and-dbparameterscale-are-now-public-virtual-members"></a>DbParameter.Precision e DbParameter.Scale agora são membros virtuais públicos

|   |   |
|---|---|
|Detalhes|<xref:System.Data.Common.DbParameter.Precision> e <xref:System.Data.Common.DbParameter.Scale> são implementados como propriedades virtuais públicas. Elas substituem as implementações de interface explícitas correspondentes, <xref:System.Data.Common.DbParameter.System%23Data%23IDbDataParameter%23Precision> e <xref:System.Data.Common.DbParameter.System%23Data%23IDbDataParameter%23Scale>.|
|Sugestão|Ao recompilar um provedor de banco de dados ADO.NET, essas diferenças exigirão que a palavra-chave "override" seja aplicada às propriedades Precision e Scale. Isso é necessário somente na recompilação dos componentes; binários existentes continuarão funcionando.|
|Escopo|Secundário|
|Versão|4.5.1|
|Tipo|Redirecionando|
|APIs afetadas|<ul><li><xref:System.Data.Common.DbParameter.Precision?displayProperty=nameWithType></li><li><xref:System.Data.Common.DbParameter.Scale?displayProperty=nameWithType></li></ul>|

