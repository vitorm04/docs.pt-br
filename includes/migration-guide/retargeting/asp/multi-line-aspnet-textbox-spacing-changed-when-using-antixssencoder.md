### <a name="multi-line-aspnet-textbox-spacing-changed-when-using-antixssencoder"></a>O espaçamento de TextBox do ASP.Net de várias linhas é alterado quando se usa AntiXSSEncoder

|   |   |
|---|---|
|Detalhes|No .NET Framework 4.0, linhas extras eram inseridas entre as linhas de uma caixa de texto de várias linhas no postback, se usando o <xref:System.Web.Security.AntiXss.AntiXssEncoder?displayProperty=name>. No .NET Framework 4.5, essas quebras de linhas extras não são incluídas, mas somente se o aplicativo Web for direcionado ao .NET 4.5|
|Sugestão|Lembre-se de que os aplicativos web 4.0 redirecionados para o .NET Framework 4.5 podem ter caixas de texto multilinha melhoradas para não inserir quebras de linha extras. Se isso não for desejável, o aplicativo poderá ter o comportamento antigo durante a execução no .NET Framework 4.5 visando o .NET Framework 4.0.|
|Escopo|Secundário|
|Versão|4.5|
|Tipo|Redirecionando|

