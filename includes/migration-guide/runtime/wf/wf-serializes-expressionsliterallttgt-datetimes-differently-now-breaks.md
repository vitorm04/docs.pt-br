### <a name="wf-serializes-expressionsliterallttgt-datetimes-differently-now-breaks-custom-xaml-parsers"></a>O WF agora serializa Expressions.Literal&lt;T&gt; DateTimes de modo diferente (interrompe analisadores XAML personalizados)

|   |   |
|---|---|
|Detalhes|O objeto <xref:System.Windows.Markup.ValueSerializer> associado converterá um objeto <xref:System.DateTime?displayProperty=name> ou <xref:System.DateTimeOffset?displayProperty=name> cujos componentes Second e <xref:System.DateTime.Millisecond?displayProperty=name> são diferentes de zero e (para um valor de <xref:System.DateTime?displayProperty=name>) cuja propriedade <xref:System.DateTime.Kind> não é Unspecified para a sintaxe de elemento de propriedade em vez de uma cadeia de caracteres. Essa alteração permite que os valores <xref:System.DateTime?displayProperty=name> e <xref:System.DateTimeOffset?displayProperty=name> completem um ciclo. Os analisadores XAML personalizados que assumem que a entrada XAML está na sintaxe de atributo não funcionará corretamente.|
|Sugestão|Essa alteração permite que os valores <xref:System.DateTime?displayProperty=name> e <xref:System.DateTimeOffset?displayProperty=name> completem um ciclo. Os analisadores XAML personalizados que assumem que a entrada XAML está na sintaxe de atributo não funcionará corretamente.|
|Escopo|Microsoft Edge|
|Versão|4.5|
|Tipo|Tempo de execução|

