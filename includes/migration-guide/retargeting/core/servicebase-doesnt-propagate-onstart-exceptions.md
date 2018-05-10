### <a name="servicebase-doesnt-propagate-onstart-exceptions"></a>ServiceBase não propaga exceções de OnStart

|   |   |
|---|---|
|Detalhes|No .NET Framework 4.7 e nas versões anteriores, as exceções geradas durante a inicialização do serviço não são propagadas para o chamador de <xref:System.ServiceProcess.ServiceBase.Run%2A?displayProperty=nameWithType>.<br/>Começando com os aplicativos direcionados ao .NET Framework 4.7.1, o tempo de execução propaga exceções para <xref:System.ServiceProcess.ServiceBase.Run%2A?displayProperty=nameWithType> de serviços que falham ao iniciar.|
|Sugestão|Na inicialização do serviço, se houver uma exceção, essa exceção será propagada. Isso deve ajudar a diagnosticar casos em que os serviços falham ao iniciar. <br/>Se esse comportamento não for desejado, você poderá recusá-lo, adicionando o seguinte elemento <AppContextSwitchOverrides> à seção <runtime> do arquivo de configuração de aplicativo:<pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceProcess.DontThrowExceptionsOnStart=true&quot; /&gt;&#13;&#10;</code></pre>Se seu aplicativo for destinado a uma versão anterior à 4.7.1, mas você desejar ter esse comportamento, adicione o seguinte elemento <AppContextSwitchOverrides> à seção <runtime> do arquivo de configuração de aplicativo:<pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceProcess.DontThrowExceptionsOnStart=false&quot; /&gt;&#13;&#10;</code></pre>|
|Escopo|Secundário|
|Versão|4.7.1|
|Tipo|Redirecionando|
|APIs afetadas|<ul><li><xref:System.ServiceProcess.ServiceBase.Run(System.ServiceProcess.ServiceBase)?displayProperty=nameWithType></li><li><xref:System.ServiceProcess.ServiceBase.Run(System.ServiceProcess.ServiceBase[])?displayProperty=nameWithType></li></ul>|

