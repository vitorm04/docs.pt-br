### <a name="webutilityhtmldecode-no-longer-decodes-invalid-input-sequences"></a>WebUtility.HtmlDecode não decodifica mais sequências de entrada inválidas

|   |   |
|---|---|
|Detalhes|Por padrão, os métodos de decodificação não decodificam mais uma sequência de entrada válida em uma cadeia de caracteres UTF-16 inválida. Em vez disso, eles retornam a entrada original.|
|Sugestão|A alteração na saída do decodificador deve importar somente se você armazenar dados binários em vez de dados UTF-16 em cadeias de caracteres. Para controlar explicitamente esse comportamento, defina o atributo <code>aspnet:AllowRelaxedUnicodeDecoding</code> do elemento [appSettings](~/docs/framework/configure-apps/file-schema/appsettings/index.md) como <code>true</code> para habilitar o comportamento herdado ou como <code>false</code> para habilitar o comportamento atual.|
|Escopo|Secundário|
|Versão|4.5|
|Tipo|Tempo de execução|
|APIs afetadas|<ul><li><xref:System.Net.WebUtility.HtmlDecode(System.String)?displayProperty=nameWithType></li><li><xref:System.Net.WebUtility.HtmlDecode(System.String,System.IO.TextWriter)?displayProperty=nameWithType></li><li><xref:System.Net.WebUtility.UrlDecode(System.String)?displayProperty=nameWithType></li></ul>|

