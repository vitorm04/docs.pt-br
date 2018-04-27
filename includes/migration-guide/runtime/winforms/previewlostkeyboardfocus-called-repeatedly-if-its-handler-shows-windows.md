### <a name="previewlostkeyboardfocus-is-called-repeatedly-if-its-handler-shows-a-windows-forms-message-box"></a>PreviewLostKeyboardFocus será chamado repetidamente se seu manipulador mostrar uma caixa de mensagem do Windows Forms

|   |   |
|---|---|
|Detalhes|A partir do .NET Framework 4.5, chamar <code>System.Windows.Forms.MessageBox.Show</code> de um manipulador <xref:System.Windows.UIElement.PreviewLostKeyboardFocus> fará com que o manipulador seja acionado novamente quando a caixa de mensagem for fechada, possivelmente resultando em um loop infinito de caixas de mensagem.|
|Sugestão|Há duas opções para contornar esse problema.<ol><li>Ele pode ser evitado chamando <code>System.Windows.MessageBox.Show</code> em vez de <code>System.Windows.Forms.MessageBox.Show</code>.</li><li>Ele pode ser evitado mostrando a caixa de mensagem de um manipulador de eventos <xref:System.Windows.UIElement.LostKeyboardFocus> (em oposição a um manipulador de eventos <xref:System.Windows.UIElement.PreviewLostKeyboardFocus?displayProperty=name>).</li></ol>|
|Escopo|Microsoft Edge|
|Versão|4.5|
|Tipo|Tempo de execução|
|APIs afetadas|<ul><li><xref:System.Windows.ContentElement.PreviewLostKeyboardFocus?displayProperty=nameWithType></li><li><xref:System.Windows.IInputElement.PreviewLostKeyboardFocus?displayProperty=nameWithType></li><li><xref:System.Windows.UIElement.PreviewLostKeyboardFocus?displayProperty=nameWithType></li><li><xref:System.Windows.UIElement3D.PreviewLostKeyboardFocus?displayProperty=nameWithType></li></ul>|

