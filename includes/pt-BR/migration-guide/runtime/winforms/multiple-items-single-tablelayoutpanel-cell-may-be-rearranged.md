### <a name="multiple-items-in-a-single-tablelayoutpanel-cell-may-be-rearranged"></a>Vários itens em uma única célula TableLayoutPanel podem ser reorganizados

|   |   |
|---|---|
|Detalhes|No .NET Framework 4.5, se vários itens forem colocados na mesma célula <xref:System.Windows.Forms.TableLayoutPanel?displayProperty=name>, eles poderão ser exibidos em uma ordem diferente daquela em que eram exibidos no .NET Framework 4.0.|
|Sugestão|Esse comportamento foi revertido em uma atualização de serviço para o .NET Framework 4.5. Atualize o .NET Framework 4.5 ou faça upgrade para o .NET Framework 4.5.1 ou posterior para corrigir esse problema. Como alternativa, evite o caso ambíguo de vários itens na mesma célula <xref:System.Windows.Forms.TableLayoutPanel?displayProperty=name>.|
|Escopo|Secundário|
|Versão|4.5|
|Tipo|Tempo de execução|
|APIs afetadas|<ul><li><xref:System.Windows.Forms.TableLayoutControlCollection.Add(System.Windows.Forms.Control%2CSystem.Int32%2CSystem.Int32)?displayProperty=nameWithType></li></ul>|
|Analisadores|<ul><li>CD0098</li></ul>|

