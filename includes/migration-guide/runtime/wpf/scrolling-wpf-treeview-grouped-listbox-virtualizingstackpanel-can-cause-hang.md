### <a name="scrolling-a-wpf-treeview-or-grouped-listbox-in-a-virtualizingstackpanel-can-cause-a-hang"></a>Rolar em uma TreeView ou ListBox agrupada no WPF em um VirtualizingStackPanel pode causar travamento

|   |   |
|---|---|
|Detalhes|No .NET Framework v4.5, rolar em uma <xref:System.Windows.Controls.TreeView?displayProperty=name> do WPF em um painel de pilha virtualizado poderá causar travamentos se houver margens no visor (entre os itens na <xref:System.Windows.Controls.TreeView?displayProperty=name>, por exemplo, ou em um elemento ItemsPresenter). Além disso, em alguns casos, itens de tamanhos diferentes no modo de exibição podem causar instabilidade, mesmo se não houver margens.|
|Sugestão|Esse bug pode ser evitado com a o upgrade para o .NET Framework 4.5.1. Como alternativa, as margens poderão ser removidas das coleções de exibições (como <xref:System.Windows.Controls.TreeView?displayProperty=name>s) em painéis de pilha virtualizados se todos os itens contidos forem do mesmo tamanho.|
|Escopo|Principal|
|Versão|4.5|
|Tipo|Tempo de execução|
|APIs afetadas|<ul><li><xref:System.Windows.Controls.VirtualizingStackPanel.SetIsVirtualizing(System.Windows.DependencyObject,System.Boolean)?displayProperty=nameWithType></li></ul>|

