### <a name="listboxitem-isselected-binding-issue-with-observablecollectionlttgtmove"></a>Problema de associação de ListBoxItem IsSelected com ObservableCollection&lt;T&gt;.Move

|   |   |
|---|---|
|Detalhes|Chamar <xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)> ou <xref:System.Collections.ObjectModel.ObservableCollection%601.MoveItem(System.Int32,System.Int32)> em uma coleção associada a um <xref:System.Windows.Controls.ListBox?displayProperty=name> com itens selecionados pode gerar comportamento imprevisível em seleções ou cancelamentos de seleção futuros de itens <xref:System.Windows.Controls.ListBox?displayProperty=name>.|
|Sugestão|Chamar <xref:System.Collections.ObjectModel.Collection%601.Remove(%600)?displayProperty=name> e <xref:System.Collections.ObjectModel.Collection%601.Insert(System.Int32,%600)?displayProperty=name> em vez de <xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)> é uma solução alternativa para esse problema. Como alternativa, esse problema foi corrigido no .NET Framework 4.6 e pode ser resolvido com o upgrade para essa versão do .NET Framework.|
|Escopo|Secundário|
|Versão|4.5|
|Tipo|Tempo de execução|
|APIs afetadas|<ul><li><xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)?displayProperty=nameWithType></li><li><xref:System.Collections.ObjectModel.ObservableCollection%601.MoveItem(System.Int32,System.Int32)?displayProperty=nameWithType></li></ul>|

