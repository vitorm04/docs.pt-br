### <a name="vbnet-no-longer-supports-partial-namespace-qualification-for-systemwindows-apis"></a>VB.NET não é mais compatível com a qualificação do namespace parcial para APIs System.Windows

|   |   |
|---|---|
|Detalhes|A partir do .NET 4.5.2, os projetos VB.NET não podem especificar as APIs System.Windows com namespaces parcialmente qualificados. Por exemplo, fazer referência a <code>Windows.Forms.DialogResult</code> falhará. Em vez disso, o código deve fazer referência ao nome totalmente qualificado (<xref:System.Windows.Forms.DialogResult>) ou importar o namespace específico e simplesmente fazer referência a <xref:System.Windows.Forms.DialogResult?displayProperty=name>.|
|Sugestão|O código deve ser atualizado para fazer referência as APIs <code>System.Windows</code> com nomes simples (e importando o namespace relevante) ou com nomes totalmente qualificados.|
|Escopo|Secundário|
|Versão|4.5.2|
|Tipo|Redirecionando|

