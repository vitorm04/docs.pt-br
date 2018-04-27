### <a name="the-replace-method-in-odata-urls-is-disabled-by-default"></a>O método Replace nas URLs do OData é desabilitado por padrão

|   |   |
|---|---|
|Detalhes|A partir do .NET Framework 4.5, o método Replace em URLs do OData é desabilitado por padrão. Quando o Replace do OData está desabilitado (agora por padrão), qualquer solicitação de usuário, incluindo funções de substituição (que são incomuns), falha.|
|Sugestão|Se o método de substituição for necessário (o que é incomum), ele poderá ser reabilitado por meio das configurações (<xref:System.Data.Services.Configuration.DataServicesFeaturesSection.ReplaceFunction?displayProperty=name>). No entanto, um método de substituição habilitado pode dar abertura para vulnerabilidades de segurança, devendo ser usado somente depois de análise cuidadosa.|
|Escopo|Microsoft Edge|
|Versão|4.5|
|Tipo|Tempo de execução|
|APIs afetadas|<ul><li><xref:System.Data.Services.DataService%601?displayProperty=nameWithType></li></ul>|

