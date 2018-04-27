### <a name="gridviews-with-allowcustompaging-set-to-true-may-fire-the-pageindexchanging-event-when-leaving-the-final-page-of-the-view"></a>GridViews com AllowCustomPaging definido como verdadeiro pode acionar o evento PageIndexChanging ao deixar a página final do modo de exibição

|   |   |
|---|---|
|Detalhes|Um bug no .NET Framework 4.5 faz com que <xref:System.Web.UI.WebControls.GridView.PageIndexChanging?displayProperty=name>, às vezes, não seja acionado para <xref:System.Web.UI.WebControls.GridView?displayProperty=name>s com <xref:System.Web.UI.WebControls.GridView.AllowCustomPaging?displayProperty=name> habilitado.|
|Sugestão|Esse problema foi corrigido no .NET Framework 4.6 e pode ser resolvido com o upgrade para essa versão do .NET Framework. Como solução alternativa, o aplicativo pode fazer um BindGrid explícito em qualquer <code>Page_Load</code> que respeite essas condições (o <xref:System.Web.UI.WebControls.GridView?displayProperty=name> está na última página e Last<xref:System.Web.UI.WebControls.GridView.PageSize?displayProperty=name> é diferente de <xref:System.Web.UI.WebControls.GridView.PageSize?displayProperty=name>). Como alternativa, o aplicativo pode ser modificado para permitir a paginação (em vez da paginação personalizada), uma vez que esse cenário não demonstra o problema.|
|Escopo|Secundário|
|Versão|4.5|
|Tipo|Tempo de execução|
|APIs afetadas|<ul><li><xref:System.Web.UI.WebControls.GridView.AllowCustomPaging?displayProperty=nameWithType></li></ul>|

