### <a name="contentdisposition-datetimes-returns-slightly-different-string"></a>ContentDisposition DateTimes retorna cadeia de caracteres ligeiramente diferente

|   |   |
|---|---|
|Detalhes|As representações de cadeia de caracteres de <xref:System.Net.Mime.ContentDisposition?displayProperty=name> foram atualizadas, a partir da versão 4.6, para sempre representarem o componente de hora de um <xref:System.DateTime?displayProperty=name> com dois dígitos. Isso está em conformidade com a [RFC822](http://www.ietf.org/rfc/rfc0822.txt) e [RFC2822](http://www.ietf.org/rfc/rfc2822.txt). Isso faz com que <xref:System.Net.Mime.ContentDisposition.ToString> retorne uma cadeia de caracteres ligeiramente diferente na versão 4.6 em cenários em que um dos elementos de tempo da disposição era anterior a 10:00 AM. Observe que ContentDispositions, às vezes, são serializados por meio de conversão em cadeias de caracteres, de modo que quaisquer operações <xref:System.Net.Mime.ContentDisposition.ToString>, serialização ou chamadas GetHashCode devem ser revisadas.|
|Sugestão|Não espere que essas representações de cadeia de caracteres de ContentDispositions de diferentes versões do .NET Framework sejam corretamente comparadas umas com as outras. Converta as cadeias de caracteres de volta em ContentDispositions, se possível, antes de realizar uma comparação.|
|Escopo|Secundário|
|Versão|4.6|
|Tipo|Tempo de execução|
|APIs afetadas|<ul><li><xref:System.Net.Mime.ContentDisposition.ToString?displayProperty=nameWithType></li><li><xref:System.Net.Mime.ContentDisposition.GetHashCode?displayProperty=nameWithType></li></ul>|

