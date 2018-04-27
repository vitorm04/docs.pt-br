### <a name="itemsclear-does-not-remove-duplicates-from-selecteditems"></a>Items.Clear não remove duplicatas de SelectedItems

|   |   |
|---|---|
|Detalhes|Suponha que um Seletor (com seleção múltipla habilitada) tenha duplicatas em sua coleção <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=name> – o mesmo item é exibido mais de uma vez.  A remoção desses itens da fonte de dados (por exemplo, chamando Items.Clear) falha ao removê-los de <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=name>; somente a primeira instância é removida. Além disso, o uso subsequente de <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=name> (por exemplo, SelectedItems.Clear()) pode encontrar problemas, como <xref:System.ArgumentException?displayProperty=name>, pois <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=name> contém itens que não estão mais na fonte de dados.|
|Sugestão|Se possível, atualize para o .NET 4.6.2.|
|Escopo|Secundário|
|Versão|4.5|
|Tipo|Tempo de execução|
|APIs afetadas|<ul><li><xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=nameWithType></li></ul>|

