### <a name="wpf-textbox-selected-text-appears-a-different-color-when-the-text-box-is-inactive"></a>O texto selecionado TextBox do WPF aparece em cor diferente quando a caixa de texto está inativa

|   |   |
|---|---|
|Detalhes|No .NET 4.5, quando um controle de caixa de texto do WPF estiver inativo (não tem foco), o texto selecionado dentro da caixa aparecerá em uma cor diferente de quando o controle estiver ativo.|
|Sugestão|É possível restaurar o comportamento anterior (.NET 4.0) definindo a propriedade <xref:System.Windows.FrameworkCompatibilityPreferences.AreInactiveSelectionHighlightBrushKeysSupported> como <code>false</code>.|
|Escopo|Microsoft Edge|
|Versão|4.5|
|Tipo|Tempo de execução|
|APIs afetadas|<ul><li><xref:System.Windows.Controls.TextBox?displayProperty=nameWithType></li></ul>|

