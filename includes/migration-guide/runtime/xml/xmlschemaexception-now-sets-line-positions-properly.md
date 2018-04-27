### <a name="xmlschemaexception-now-sets-line-positions-properly"></a>XmlSchemaException agora define posições de linhas corretamente

|   |   |
|---|---|
|Detalhes|Se o valor <xref:System.Xml.Linq.LoadOptions.SetLineInfo> é passado para o método Load e um erro de validação ocorre, as propriedades <xref:System.Xml.Schema.XmlSchemaException.LineNumber> e <xref:System.Xml.Schema.XmlSchemaException.LinePosition> contêm agora a linha de informações.|
|Sugestão|O código de tratamento de exceção que supõe que <xref:System.Xml.Schema.XmlSchemaException.LineNumber> e <xref:System.Xml.Schema.XmlSchemaException.LinePosition> não serão definidas deverá ser atualizado, uma vez que essas propriedades agora serão definidas corretamente quando SetLineInfo for usado durante o carregamento de XML.|
|Escopo|Microsoft Edge|
|Versão|4.5|
|Tipo|Tempo de execução|
|APIs afetadas|<ul><li><xref:System.Xml.Linq.LoadOptions.SetLineInfo?displayProperty=nameWithType></li></ul>|

