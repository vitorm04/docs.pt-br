### <a name="wcf-binding-with-the-transportwithmessagecredential-security-mode"></a>Associação do WCF com o modo de segurança TransportWithMessageCredential

|   |   |
|---|---|
|Detalhes|A partir do .NET Framework 4.6.1, a associação do WCF que usar o modo de segurança TransportWithMessageCredential poderá ser configurada para receber mensagens com cabeçalho &quot;para&quot; não assinados para chaves de segurança assimétricas. Por padrão, cabeçalho &quot;para&quot; não assinados continuarão a ser rejeitados no .NET 4.6.1. Eles só serão aceitos se um aplicativo aceitar esse novo modo de operação usando a opção de configuração Switch.System.ServiceModel.AllowUnsignedToHeader. Como esse é um recurso de aceitação, ele não deve afetar o comportamento dos aplicativos existentes.|
|Sugestão|Como esse é um recurso de aceitação, ele não deve afetar o comportamento dos aplicativos existentes. Para controlar se o novo comportamento está sendo usado ou não, use a seguinte configuração:<pre><code class="language-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.AllowUnsignedToHeader=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Escopo|Transparente|
|Versão|4.6.1|
|Tipo|Redirecionando|
|APIs afetadas|<ul><li><xref:System.ServiceModel.BasicHttpSecurityMode.TransportWithMessageCredential?displayProperty=nameWithType></li><li><xref:System.ServiceModel.BasicHttpsSecurityMode.TransportWithMessageCredential?displayProperty=nameWithType></li><li><xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential?displayProperty=nameWithType></li><li><xref:System.ServiceModel.WSFederationHttpSecurityMode.TransportWithMessageCredential?displayProperty=nameWithType></li></ul>|

