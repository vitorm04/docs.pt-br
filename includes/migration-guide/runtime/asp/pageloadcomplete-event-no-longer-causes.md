### <a name="pageloadcomplete-event-no-longer-causes-systemwebuiwebcontrolsentitydatasource-control-to-invoke-data-binding"></a>O evento Page.LoadComplete não faz mais com que o controle System.Web.UI.WebControls.EntityDataSource invoque a associação de dados

|   |   |
|---|---|
|Detalhes|O evento <xref:System.Web.UI.Page.LoadComplete> não faz mais com que o controle <xref:System.Web.UI.WebControls.EntityDataSource?displayProperty=name> chame a associação de dados para alterações par criar/atualizar/excluir parâmetros. Essa alteração elimina um processamento irrelevante para o banco de dados, impede que os valores dos controles sejam redefinidos e gera um comportamento consistente com outros controles de dados, como <xref:System.Web.UI.WebControls.SqlDataSource?displayProperty=name> e <xref:System.Web.UI.WebControls.ObjectDataSource?displayProperty=name>. Essa alteração gera um comportamento diferente em um evento improvável no qual os aplicativos dependam da associação de dados no evento <xref:System.Web.UI.Page.LoadComplete>.|
|Sugestão|Se houver necessidade de vinculação de dados, invoque manualmente a associação de dados em um evento que seja anterior no post-back.|
|Escopo|Microsoft Edge|
|Versão|4.5|
|Tipo|Tempo de execução|

