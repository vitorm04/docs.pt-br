### <a name="binding-a-wpf-selector-property-such-as-selecteditem-to-a-static-property-does-not-work"></a>Associar uma propriedade de seletor WPF (como 'SelectedItem') a uma propriedade estática não funciona

|   |   |
|---|---|
|Detalhes|No .NET Framework 4.5, propriedades do Seletor de WPF (como &#39;SelectedItem&#39; em <xref:System.Windows.Controls.ListBox?displayProperty=name> ou <xref:System.Windows.Controls.DataGrid?displayProperty=name>) que está associada a dados a propriedades estáticas não são atualizadas corretamente quando a propriedade associada é atualizada.|
|Sugestão|Esse comportamento foi revertido em uma atualização de serviço para o .NET Framework 4.5. Atualize o .NET Framework 4.5 ou faça upgrade para o .NET Framework 4.5.1 ou posterior para corrigir esse problema.|
|Escopo|Secundário|
|Versão|4.5|
|Tipo|Tempo de execução|

