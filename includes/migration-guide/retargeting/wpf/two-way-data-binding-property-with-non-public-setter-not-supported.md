### <a name="two-way-data-binding-to-a-property-with-a-non-public-setter-is-not-supported"></a>Não há suporte para a associação de dados bidirecionais para uma propriedade com um setter não público

|   |   |
|---|---|
|Detalhes|A tentativa de associar dados a uma propriedade sem um setter público nunca foi um cenário com suporte. A partir do .NET Framework 4.5.1, esse cenário vai gerar uma <xref:System.InvalidOperationException?displayProperty=name>. Observe que essa nova exceção será gerada somente para aplicativos destinados especificamente ao .NET Framework 4.5.1. Se um aplicativo for destinado ao .NET Framework 4.5, a chamada será permitida. Se o aplicativo não for destinado a uma versão específica do .NET Framework, a associação será tratada como unidirecional.|
|Sugestão|O aplicativo deve ser atualizado para usar a associação unidirecional ou expor publicamente o setter da propriedade. Como alternativa, o direcionamento ao .NET Framework 4.5 fará com que o aplicativo demonstre o comportamento antigo.|
|Escopo|Secundário|
|Versão|4.5.1|
|Tipo|Redirecionando|
|APIs afetadas|<ul><li><xref:System.Windows.Data.BindingMode.TwoWay?displayProperty=nameWithType></li></ul>|

