### <a name="concurrentqueuelttgttrypeek-can-return-an-erroneous-null-via-its-out-parameter"></a>ConcurrentQueue&lt;T&gt;.TryPeek pode retornar um nulo errado por meio de seus parâmetros de saída

|   |   |
|---|---|
|Detalhes|Em alguns cenários multithread, <xref:System.Collections.Concurrent.ConcurrentQueue%601.TryPeek(%600@)?displayProperty=name> pode retornar true, mas popular o parâmetro de saída com um valor nulo (em vez do valor correto, inspecionado).|
|Sugestão|Esse problema foi corrigido no .NET Framework 4.5.1. O upgrade para esse Framework resolverá o problema.|
|Escopo|Principal|
|Versão|4.5|
|Tipo|Tempo de execução|
|APIs afetadas|<ul><li><xref:System.Collections.Concurrent.ConcurrentQueue%601.TryPeek(%600@)?displayProperty=nameWithType></li></ul>|

