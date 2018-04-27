### <a name="enumerableemptylttresultgt-always-returns-cached-instance"></a>Enumerable.Empty&lt;TResult&gt; sempre retorna instância em cache

|   |   |
|---|---|
|Detalhes|A partir do .NET 4.5, <xref:System.Linq.Enumerable.Empty%60%601> sempre retorna uma instância <xref:System.Collections.Generic.IEnumerable%601> interna em cache. Antigamente, <xref:System.Linq.Enumerable.Empty%60%601> armazenava em cache um <xref:System.Collections.Generic.IEnumerable%601> vazio no momento em que a API era chamada, o que significa que, em algumas condições nas quais <xref:System.Linq.Enumerable.Empty%60%601> era chamado de forma rápida e simultânea, diferentes instâncias do tipo poderiam ser retornadas para diferentes chamadas à API.|
|Sugestão|Como o comportamento anterior não era determinístico, é improvável que o código dependesse dele. No entanto, na improbabilidade de que enumeráveis vazios estivessem sendo comparados e, às vezes, esperados que fosse diferentes, matrizes vazias explícitas deviam ser criadas (<code>new T[0]</code>) em vez de usar <xref:System.Linq.Enumerable.Empty%60%601>.|
|Escopo|Microsoft Edge|
|Versão|4.5|
|Tipo|Tempo de execução|
|APIs afetadas|<ul><li><xref:System.Linq.Enumerable.Empty%60%601?displayProperty=nameWithType></li></ul>|

