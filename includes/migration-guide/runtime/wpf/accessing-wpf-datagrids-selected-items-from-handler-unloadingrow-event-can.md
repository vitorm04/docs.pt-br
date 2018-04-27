### <a name="accessing-a-wpf-datagrids-selected-items-from-a-handler-of-the-datagrids-unloadingrow-event-can-cause-a-nullreferenceexception"></a>Acessar os itens selecionados de um DataGrid do WPF em um manipulador do evento UnloadingRow do DataGrid pode gerar NullReferenceException

|   |   |
|---|---|
|Detalhes|Por causa de um bug no .NET Framework 4.5, os manipuladores de eventos <xref:System.Windows.Controls.DataGrid> que envolvem a remoção de uma linha podem gerar <xref:System.NullReferenceException?displayProperty=name> se acessarem as propriedades <xref:System.Windows.Controls.Primitives.Selector.SelectedItem?displayProperty=name> ou <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=name> de <xref:System.Windows.Controls.DataGrid>.|
|Sugestão|Esse problema foi corrigido no .NET Framework 4.6 e pode ser resolvido com o upgrade para essa versão do .NET Framework.|
|Escopo|Secundário|
|Versão|4.5|
|Tipo|Tempo de execução|
|APIs afetadas|<ul><li><xref:System.Windows.Controls.DataGrid.UnloadingRow?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.DataGrid.UnloadingRowDetails?displayProperty=nameWithType></li></ul>|

