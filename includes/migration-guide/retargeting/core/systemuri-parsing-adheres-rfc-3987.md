### <a name="systemuri-parsing-adheres-to-rfc-3987"></a>Análise de System.Uri adere à RFC 3987

|   |   |
|---|---|
|Detalhes|A análise de URI foi alterada de várias maneiras no .NET 4.5. No entanto, observe que essas alterações afetam apenas o código que se destinam ao NET 4.5. Se um binário for destinado ao .NET 4.0, o comportamento antigo será observado. As alterações na análise de URI no .NET 4.5 incluem:<ul><li>A análise de URI executará a normalização e a verificação de caracteres de acordo com as regras mais recentes de URI na RFC 3987.</li><li>O formulário C de normalização Unicode só será executado na parte de host do URI.</li><li>Agora, os URIs mailto: inválidos gerarão uma exceção.</li><li>Os pontos à direita no fim de um segmento de linha agora são preservados.</li><li>Os URIs <code>file://</code> não escapam o caractere <code>?</code>.</li><li>Os caracteres de controle Unicode <code>U+0080</code> a <code>U+009F</code> não são compatíveis.</li><li>Os caracteres de vírgula <code>,</code> ou <code>%2c</code> não fogem ao escape automaticamente.</li></ul>|
|Sugestão|Se a semântica de análise de URI antiga do .NET 4.0 for necessária (geralmente não é), ela poderá ser usada visando o .NET 4.0. Isso pode ser feito usando um <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=name> no assembly ou pela interface do usuário do sistema do projeto no Visual Studio, na página "propriedades do projeto".|
|Escopo|Principal|
|Versão|4.5|
|Tipo|Redirecionando|
|APIs afetadas|<ul><li><xref:System.Uri.%23ctor(System.String)?displayProperty=nameWithType></li><li><xref:System.Uri.%23ctor(System.String,System.Boolean)?displayProperty=nameWithType></li><li><xref:System.Uri.%23ctor(System.String,System.UriKind)?displayProperty=nameWithType></li><li><xref:System.Uri.%23ctor(System.Uri,System.String)?displayProperty=nameWithType></li><li><xref:System.Uri.TryCreate(System.String,System.UriKind,System.Uri@)?displayProperty=nameWithType></li><li><xref:System.Uri.TryCreate(System.Uri,System.String,System.Uri@)?displayProperty=nameWithType></li><li><xref:System.Uri.TryCreate(System.Uri,System.Uri,System.Uri@)?displayProperty=nameWithType></li></ul>|

