### <a name="objectcontexttranslate-and-objectcontextexecutestorequery-now-support-enum-type"></a>ObjectContext.Translate e ObjectContext.ExecuteStoreQuery agora dão suporte ao tipo de enumeração

|   |   |
|---|---|
|Detalhes|No .NET 4.0, o parâmetro genérico <code>T</code> de <code>ObjectContext.Translate</code> e os métodos <code>ObjectContext.ExecuteStoreQuery</code> não podiam ser uma enumeração. Agora há suporte para esse cenário.|
|Sugestão|Se Translate ou ExecuteStoreQuery era chamado em um tipo de enumeração no .NET 4.0, era retornado "0". Se esse comportamento fosse desejável, as chamadas deveriam ser substituídas por uma constante 0 (ou o equivalente de enumeração dele).|
|Escopo|Microsoft Edge|
|Versão|4.5|
|Tipo|Tempo de execução|
|APIs afetadas|<ul><li><xref:System.Data.Objects.ObjectContext.Translate%60%601(System.Data.Common.DbDataReader)?displayProperty=nameWithType></li><li><xref:System.Data.Objects.ObjectContext.Translate%60%601(System.Data.Common.DbDataReader,System.String,System.Data.Objects.MergeOption)?displayProperty=nameWithType></li><li><xref:System.Data.Objects.ObjectContext.ExecuteStoreQuery%60%601(System.String,System.Object[])?displayProperty=nameWithType></li><li><xref:System.Data.Objects.ObjectContext.ExecuteStoreQuery%60%601(System.String,System.String,System.Data.Objects.MergeOption,System.Object[])?displayProperty=nameWithType></li></ul>|

