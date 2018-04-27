### <a name="deadlock-may-result-when-using-reentrant-services"></a>Uso de serviços Reentrantes pode resultar em deadlock

|   |   |
|---|---|
|Detalhes|Um deadlock pode resultar em um serviço Reentrante, o que restringe as instâncias do serviço para um thread de execução de cada vez. Os serviços que podem apresentar esse problema terão o <xref:System.ServiceModel.ServiceBehaviorAttribute> a seguir no código:<pre><code class="language-csharp">[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Reentrant)]&#13;&#10;</code></pre>|
|Sugestão|Para solucionar esse problema, você pode fazer o seguinte:<ul><li>Definir o modo de simultaneidade do serviço como <xref:System.ServiceModel.ConcurrencyMode.Single?displayProperty=nameWithType> ou &lt;System.ServiceModel.ConcurrencyMode.Multiple?displayProperty=nameWithType&gt;. Por exemplo:</li></ul><pre><code class="language-csharp">[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Single)]&#13;&#10;</code></pre><ul><li>Instalar a atualização mais recente do .NET Framework 4.6.2 ou atualizar para uma versão posterior do .NET Framework. Isso desabilita o fluxo do <xref:System.Threading.ExecutionContext> em <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType>. Esse comportamento é configurável; é equivalente a adicionar a seguinte configuração de aplicativo ao arquivo de configuração:</li></ul><pre><code class="language-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;Switch.System.ServiceModel.DisableOperationContextAsyncFlow&quot; value=&quot;true&quot; /&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;&#13;&#10;The value of &#39;Switch.System.ServiceModel.DisableOperationContextAsyncFlow&#39; should never be set to &#39;false&#39; for Rentrant services.&#13;&#10;</code></pre>|
|Escopo|Secundário|
|Versão|4.6.2|
|Tipo|Redirecionando|
|APIs afetadas|<ul><li><xref:System.ServiceModel.ServiceBehaviorAttribute?displayProperty=nameWithType></li><li><xref:System.ServiceModel.ConcurrencyMode.Reentrant?displayProperty=nameWithType></li></ul>|

