### <a name="htmltextwriter-does-not-render-br-element-correctly"></a>HtmlTextWriter não renderiza o elemento `<br/>` corretamente

|   |   |
|---|---|
|Detalhes|A partir do .NET Framework 4.6, chamar <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> e <xref:System.Web.UI.HtmlTextWriter.RenderEndTag> com um elemento <code>&lt;BR /&gt;</code> vai inserir corretamente apenas um <code>&lt;BR /&gt;</code> (em vez de dois)|
|Sugestão|Se um aplicativo depender da marca <code>&lt;BR /&gt;</code> extra, <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> deverá ser chamado uma segunda vez. Observe que essa alteração de comportamento afeta apenas aplicativos destinados ao .NET Framework 4.6 ou versões posteriores, de modo que outra opção é destinar a uma versão anterior do .NET Framework a fim de obter o comportamento antigo.|
|Escopo|Microsoft Edge|
|Versão|4.6|
|Tipo|Redirecionando|
|APIs afetadas|<ul><li><xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)?displayProperty=nameWithType></li><li><xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.Web.UI.HtmlTextWriterTag)?displayProperty=nameWithType></li></ul>|

