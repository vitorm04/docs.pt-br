### <a name="systemuriiswellformeduristring-method-returns-false-for-relative-uris-with-a-colon-char-in-first-segment"></a>Método System.Uri.IsWellFormedUriString retorna false para URIs com dois-pontos no primeiro segmento

|   |   |
|---|---|
|Detalhes|A partir do .NET Framework 4.5, <xref:System.Uri.IsWellFormedUriString(System.String,System.UriKind)> tratará URIs relativos com um <code>:</code> no primeiro segmento como malformados. Essa é uma alteração do comportamento de <xref:System.Uri.IsWellFormedUriString(System.String,System.UriKind)?displayProperty=name> no .NET Framework 4.0, realizada para manter a conformidade com a RFC3986.|
|Sugestão|Essa alteração (assim como várias outras alterações de URI) afetará somente os aplicativos do .NET Framework 4.5 ou versões posteriores. Para continuar usando o comportamento antigo, direcione o aplicativo para o .NET Framework 4.0. Como alternativa, verifique se há caracteres <code>:</code> no URI que você deseja remover para fins de validação antes de chamar <xref:System.Uri.IsWellFormedUriString(System.String,System.UriKind)?displayProperty=name> se quiser usar o comportamento antigo.|
|Escopo|Secundário|
|Versão|4.5|
|Tipo|Redirecionando|
|APIs afetadas|<ul><li><xref:System.Uri.IsWellFormedUriString(System.String,System.UriKind)?displayProperty=nameWithType></li></ul>|

