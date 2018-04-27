### <a name="item-scrolling-a-flat-list-with-items-of-different-pixel-height"></a>Rolagem de itens em uma lista simples de itens com diferentes alturas em pixels

|   |   |
|---|---|
|Detalhes|Quando um <xref:System.Windows.Controls.ItemsControl?displayProperty=name> exibe uma coleção usando virtualização (<code>IsVirtualizing=true</code>) e rolagem de itens (<code>ScrollUnit=Item</code>) e quando o controle rola para exibir um item cuja altura em pixels é diferente de seus vizinhos, o <xref:System.Windows.Controls.VirtualizingStackPanel?displayProperty=name> itera em todos os itens na coleção. A interface do usuário não responde durante essa iteração. Se a coleção for grande, isso poderá ser visto como um travamento. A iteração ocorre em outras circunstâncias, mesmo em versões anteriores do .Net. Por exemplo, isso ocorre na rolagem de pixels (<code>ScrollUnit=Pixel</code>) ao encontrar um item com uma altura de pixels diferente e na rolagem de itens de dados hierárquicos (como em um <xref:System.Windows.Controls.TreeView?displayProperty=name> ou um <xref:System.Windows.Controls.ItemsControl?displayProperty=name> com o agrupamento habilitado) ao encontrar um item com um número de itens descendentes diferentes de seus vizinhos. No caso em que há rolagem de itens e diferentes alturas em pixels, a iteração foi introduzida no .Net 4.6.1 para corrigir bugs no layout de dados hierárquicos.  Ela não será necessária se os dados forem simples (sem hierarquia) e o .Net 4.6.2 não faz isso nesse caso.|
|Sugestão|Se a iteração ocorrer no .Net 4.6.1, mas não em versões anteriores – isto é, se <xref:System.Windows.Controls.ItemsControl?displayProperty=name> for uma lista plana de rolagem por item com itens de diferentes alturas de pixel – haverá duas correções:<ol><li>Instalar o .NET 4.6.2.</li><li>Instalar o hotfix HR 1605 para o .net 4.6.1.</li></ol>|
|Escopo|Secundário|
|Versão|4.6.1|
|Tipo|Tempo de execução|
|APIs afetadas|<ul><li><xref:System.Windows.Controls.VirtualizingStackPanel?displayProperty=nameWithType></li></ul>|

