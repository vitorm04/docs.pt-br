### <a name="path-colon-checks-are-stricter"></a>Verificações de dois-pontos em caminhos estão mais rigorosas

|   |   |
|---|---|
|Detalhes|No .NET Framework 4.6.2, uma série de alterações foram feitas para dar suporte aos caminhos incompatíveis anteriormente (em termos de comprimento e formato). As verificações de sintaxe do separador de unidades (dois-pontos) correto foram aperfeiçoadas, o que teve como efeito colateral o bloqueio de alguns caminhos de URI em algumas APIs de Caminho selecionadas em que eles costumavam ser aceitos.|
|Sugestão|Ao passar um URI para as APIs afetadas, modifique a cadeia de caracteres para um caminho correto antes.<ul><li>Remova o esquema das URLs manualmente (por exemplo, remova <code>file://</code> das URLs).</li><li>Passe o URI para a classe <xref:System.Uri> e use <xref:System.Uri.LocalPath>.</li></ul>Como alternativa, é possível recusar a normalização do novo caminho definindo a opção AppContext <code>Switch.System.IO.UseLegacyPathHandling</code> como true.|
|Escopo|Microsoft Edge|
|Versão|4.6.2|
|Tipo|Redirecionando|
|APIs afetadas|<ul><li><xref:System.IO.Path.GetDirectoryName(System.String)?displayProperty=nameWithType></li><li><xref:System.IO.Path.GetPathRoot(System.String)?displayProperty=nameWithType></li></ul>|

