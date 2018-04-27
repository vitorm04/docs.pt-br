### <a name="targetframeworkname-for-default-app-domain-no-longer-defaults-to-null-if-not-set"></a>TargetFrameworkName para o domínio de aplicativo padrão não será mais padronizado como nulo se não for definido

|   |   |
|---|---|
|Detalhes|O <xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=name> era nulo anteriormente no domínio de aplicativo padrão, a menos que fosse explicitamente definido. A partir da 4.6, a propriedade <xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=name> para o domínio de aplicativo padrão terá um valor padrão derivado do TargetFrameworkAttribute (se um estiver presente). Os domínios de aplicativo não padrão continuarão herdando o respectivo <xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=name> do domínio de aplicativo padrão (que não será padronizado para nulo na 4.6), a menos que sejam explicitamente substituídos.|
|Sugestão|O código deve ser atualizado para não depender do <xref:System.AppDomainSetup.TargetFrameworkName> que padroniza para nulo. Se for necessário que essa propriedade continue sendo avaliada como nula, ela poderá ser explicitamente definida para esse valor.|
|Escopo|Microsoft Edge|
|Versão|4.6|
|Tipo|Tempo de execução|
|APIs afetadas|<ul><li><xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=nameWithType></li></ul>|

