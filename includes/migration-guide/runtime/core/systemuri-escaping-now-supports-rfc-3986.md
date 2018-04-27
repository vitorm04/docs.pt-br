### <a name="systemuri-escaping-now-supports-rfc-3986"></a>O escape de System.Uri agora é compatível com RFC 3986

|   |   |
|---|---|
|Detalhes|O escape do URI mudou no .NET 4.5 para dar suporte à [RFC 3986](http://tools.ietf.org/html/rfc3986). As alterações específicas incluem:<ul><li><xref:System.Uri.EscapeDataString(System.String)?displayProperty=name> escapa caracteres reservados com base na RFC 3986.</li><li><xref:System.Uri.EscapeUriString(System.String)?displayProperty=name> não escapa caracteres reservados.</li><li><xref:System.Uri.UnescapeDataString(System.String)?displayProperty=name> não gerará uma exceção se encontrar uma sequência de escape inválida.</li><li>Os caracteres escapados não reservados não são escapados.</li></ul>|
|Sugestão|<ul><li>Atualize os aplicativos para não dependerem da geração de <xref:System.Uri.UnescapeDataString(System.String)?displayProperty=name> no caso de uma sequência de escape inválida. Essas sequências devem ser detectadas diretamente agora.</li><li>Da mesma forma, espere que o URI com escape e sem escape, bem como cadeias de caracteres de dados, possam variar do .NET 4.0 e .NET 4.5, não devendo ser comparados entre as versões do .NET diretamente. Em vez disso, eles devem ser analisados e normalizados em uma única versão do .NET antes que qualquer comparação seja feita.</li></ul>|
|Escopo|Secundário|
|Versão|4.5|
|Tipo|Tempo de execução|
|APIs afetadas|<ul><li><xref:System.Uri.EscapeDataString(System.String)?displayProperty=nameWithType></li><li><xref:System.Uri.EscapeUriString(System.String)?displayProperty=nameWithType></li><li><xref:System.Uri.UnescapeDataString(System.String)?displayProperty=nameWithType></li></ul>|

