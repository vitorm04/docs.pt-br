### <a name="httpruntimeappdomainapppath-throws-a-nullreferenceexception"></a>HttpRuntime.AppDomainAppPath gera NullReferenceException

|   |   |
|---|---|
|Detalhes|No .NET Framework 4.6.2, o tempo de execução gera <code>T:System.NullReferenceException</code> ao recuperar um valor <code>P:System.Web.HttpRuntime.AppDomainAppPath</code> que inclui caracteres nulos. No .NET Framework 4.6.1 e versões anteriores, o tempo de execução gera <code>T:System.ArgumentNullException</code>.|
|Sugestão|Você pode fazer o seguinte para responder a essa alteração:<ul><li>Identifique o <code>T:System.NullReferenceException</code> se o aplicativo estiver sendo executado no .NET Framework 4.6.2.</li><li>Atualize para o .NET Framework 4.7, que restaura o comportamento anterior e gera <code>T:System.ArgumentNullException</code>.</li></ul>|
|Escopo|Microsoft Edge|
|Versão|4.6.2|
|Tipo|Redirecionando|
|APIs afetadas|<ul><li><xref:System.Web.HttpRuntime.AppDomainAppPath?displayProperty=nameWithType></li></ul>|

