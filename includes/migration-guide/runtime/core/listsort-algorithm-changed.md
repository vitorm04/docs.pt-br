### <a name="listsort-algorithm-changed"></a>O algoritmo List.Sort foi alterado

|   |   |
|---|---|
|Detalhes|A partir do .NET Framework 4.5, o algoritmo de classificação de <xref:System.Collections.Generic.List%601?displayProperty=name> foi alterado (para ser uma classificação introspectiva em vez de uma classificação rápida). A classificação de <xref:System.Collections.Generic.List%601?displayProperty=name> nunca foi estável, mas essa alteração pode fazer com que cenários diferentes sejam classificados de maneiras instáveis. Isso significa apenas que itens equivalentes podem ser classificados em ordens diferentes em chamadas posteriores da API.|
|Sugestão|Como o algoritmo de classificação antigo também era instável (embora de maneiras ligeiramente diferentes), não deve haver nenhum código que dependa de itens equivalentes sempre serem classificados em uma ordem específica. Se houver casos de códigos que dependem disso e que tinham sorte com o comportamento antigo, esses códigos deverão ser atualizados para usar um comparador que classifique de forma determinista os itens na ordem desejada.|
|Escopo|Transparente|
|Versão|4.5|
|Tipo|Tempo de execução|
|APIs afetadas|<ul><li><xref:System.Collections.Generic.List%601.Sort?displayProperty=nameWithType></li><li><xref:System.Collections.Generic.List%601.Sort(System.Collections.Generic.IComparer{%600})?displayProperty=nameWithType></li><li><xref:System.Collections.Generic.List%601.Sort(System.Comparison{%600})?displayProperty=nameWithType></li><li><xref:System.Collections.Generic.List%601.Sort(System.Int32,System.Int32,System.Collections.Generic.IComparer{%600})?displayProperty=nameWithType></li></ul>|

