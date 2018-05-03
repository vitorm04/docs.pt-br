### <a name="typeisassignablefrom-returns-wrong-result-for-generic-variables-with-constraints"></a>Type.IsAssignableFrom retorna o resultado incorreto para variáveis genéricas com restrições

|   |   |
|---|---|
|Detalhes|No .NET Framework 4.5, <xref:System.Type.IsAssignableFrom(System.Type)> retornará <code>false</code> incorretamente em todos os casos para alguns tipos genéricos com restrições.|
|Sugestão|Esse problema foi corrigido em uma atualização de serviço. Atualize o .NET Framework 4.5 ou faça upgrade para o .NET Framework 4.5.1 ou posterior para corrigir esse problema. Como alternativa, evite usar IsAssignableFrom com tipos genéricos que tenham restrições em parâmetros genéricos. As APIs de reflexão podem ser usadas como uma solução alternativa.|
|Escopo|Secundário|
|Versão|4.5|
|Tipo|Tempo de execução|
|APIs afetadas|<ul><li><xref:System.Type.IsAssignableFrom(System.Type)?displayProperty=nameWithType></li></ul>|
|Analisadores|<ul><li>CD0089</li></ul>|

