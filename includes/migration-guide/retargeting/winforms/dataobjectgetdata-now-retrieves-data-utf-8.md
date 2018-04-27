### <a name="dataobjectgetdata-now-retrieves-data-as-utf-8"></a>DataObject.GetData agora recupera dados como UTF-8

|   |   |
|---|---|
|Detalhes|Para aplicativos destinados ao .NET Framework 4 ou que são executados no .NET Framework 4.5.1 ou em versões mais recentes, <code>DataObject.GetData</code> recupera dados formatados em HTML como uma cadeia de caracteres ASCII. Como resultado, caracteres não ASCII (caracteres cujos códigos ASCII são maiores que 0x7F) são representados por dois caracteres aleatórios. Para aplicativos que são destinados ao .NET Framework 4.5 ou posterior e são executados no .NET Framework 4.5.2, <code>DataObject.GetData</code> recupera dados formatados em HTML como UTF-8, que representa caracteres maiores que 0x7F corretamente.|
|Sugestão|Se você implementou uma solução alternativa para o problema de codificação com cadeias de caracteres formatadas em HTML (por exemplo, codificando explicitamente a cadeia de caracteres HTML recuperada da área de transferência enviando-a para <xref:System.Text.UTF8Encoding.GetString(System.Byte[],System.Int32,System.Int32)?displayProperty=name>) e estiver redirecionando seu aplicativo da versão 4 para a versão 4.5, essa solução deverá ser removida. Se o comportamento antigo for necessário por algum motivo, o aplicativo poderá ser destinado ao .NET Framework 4.0 para obtê-lo.|
|Escopo|Microsoft Edge|
|Versão|4.5.2|
|Tipo|Redirecionando|
|APIs afetadas|<ul><li><xref:System.Windows.DataObject.GetData(System.String)?displayProperty=nameWithType></li><li><xref:System.Windows.DataObject.GetData(System.Type)?displayProperty=nameWithType></li><li><xref:System.Windows.DataObject.GetData(System.String,System.Boolean)?displayProperty=nameWithType></li></ul>|

