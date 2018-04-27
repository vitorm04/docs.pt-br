### <a name="ribbongroup-background-is-set-to-transparent-in-localized-builds"></a>Tela de fundo RibbonGroup é definida como transparente em builds localizados

|   |   |
|---|---|
|Detalhes|A tela de fundo <xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=name> em builds localizados sempre foi pintada com um pincel Transparente, o que resultava em uma experiência de interface do usuário ruim. Isso foi corrigido no WPF do .NET 4.7 por meio da atualização dos recursos localizados para <xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=name>, que, por sua vez, garante que o pincel correto seja selecionado.|
|Sugestão|Atualizar para .NET 4.7|
|Escopo|Microsoft Edge|
|Versão|4.6.2|
|Tipo|Tempo de execução|

