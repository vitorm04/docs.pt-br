### <a name="wpf-textbox-defaults-to-undo-limit-of-100"></a>O padrão da Caixa de Texto do WPF é o limite de 100 na ação desfazer

|   |   |
|---|---|
|Detalhes|No .NET 4.5, o limite padrão da ação desfazer para uma caixa de texto do WPF é 100 (ao contrário de ser ilimitado como no .NET 4.0)|
|Sugestão|Se um limite de 100 da ação desfazer for muito baixo, o limite poderá ser definido explicitamente com <xref:System.Windows.Controls.Primitives.TextBoxBase.UndoLimit>.|
|Escopo|Microsoft Edge|
|Versão|4.5|
|Tipo|Tempo de execução|
|APIs afetadas|<ul><li><xref:System.Windows.Controls.TextBox?displayProperty=nameWithType></li></ul>|

