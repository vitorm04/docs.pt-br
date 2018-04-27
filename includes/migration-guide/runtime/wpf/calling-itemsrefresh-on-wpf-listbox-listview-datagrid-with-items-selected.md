### <a name="calling-itemsrefresh-on-a-wpf-listbox-listview-or-datagrid-with-items-selected-can-cause-duplicate-items-to-appear-in-the-element"></a>Chamar Items.Refresh em uma ListBox, ListView ou DataGrid do WPF com itens selecionados pode exibir itens duplicados no elemento

|   |   |
|---|---|
|Detalhes|No .NET Framework 4.5, chamar ListBox.Items.Refresh do código enquanto itens estiverem selecionados em uma <xref:System.Windows.Controls.ListBox?displayProperty=name> pode fazer com que os itens selecionados sejam duplicados na lista. Ocorre um problema semelhante com <xref:System.Windows.Controls.ListView?displayProperty=name> e <xref:System.Windows.Controls.DataGrid?displayProperty=name>. Isso foi corrigido no .NET Framework 4.6.|
|Sugestão|Esse problema pode ser contornado de forma programática cancelando a seleção dos itens antes de chamar <xref:System.Windows.Data.CollectionView.Refresh?displayProperty=name> e selecionando-os novamente após a conclusão da chamada. Como alternativa, esse problema foi corrigido no .NET Framework 4.6 e pode ser resolvido com o upgrade para essa versão do .NET Framework.|
|Escopo|Secundário|
|Versão|4.5|
|Tipo|Tempo de execução|
|APIs afetadas|<ul><li><xref:System.Windows.Data.CollectionView.Refresh?displayProperty=nameWithType></li></ul>|

