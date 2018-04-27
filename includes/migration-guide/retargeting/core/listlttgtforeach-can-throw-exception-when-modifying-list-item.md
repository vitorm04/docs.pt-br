### <a name="listlttgtforeach-can-throw-exception-when-modifying-list-item"></a>List&lt;T&gt;.ForEach agora gera exceção durante a modificação de item de lista

|   |   |
|---|---|
|Detalhes|A partir do .NET 4.5, o enumerador <xref:System.Collections.Generic.List%601.ForEach(System.Action{%600})> gerará uma exceção <xref:System.InvalidOperationException?displayProperty=name> se um elemento na coleção de chamada for modificado. Anteriormente, isso não geraria uma exceção, mas podia levar a condições de corrida.|
|Sugestão|De modo ideal, o código deve ser corrigido para não modificar listas durante a enumeração de seus elementos, pois essa nunca é uma operação segura. Porém, para reverter para o comportamento anterior, um aplicativo pode ser direcionado para o .NET 4.0.|
|Escopo|Microsoft Edge|
|Versão|4.5|
|Tipo|Redirecionando|
|APIs afetadas|<ul><li><xref:System.Collections.Generic.List%601.ForEach(System.Action{%600})?displayProperty=nameWithType></li></ul>|

