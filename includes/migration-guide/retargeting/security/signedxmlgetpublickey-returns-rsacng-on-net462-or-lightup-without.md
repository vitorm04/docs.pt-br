### <a name="signedxmlgetpublickey-returns-rsacng-on-net462-or-lightup-without-retargeting-change"></a>SignedXml.GetPublicKey retorna RSACng em net462 (ou lightup) sem redirecionar a alteração

|   |   |
|---|---|
|Detalhes|A partir do .NET Framework 4.6.2, o tipo concreto de objeto retornado pelo método <xref:System.Security.Cryptography.Xml.SignedXml.GetPublicKey%2A?displayProperty=nameWithType> foi alterado (sem um quirk) de uma implementação de CryptoServiceProvider para uma implementação de Cng. Isso ocorreu porque a implementação foi alterada: do uso de <code>certificate.PublicKey.Key</code> para o uso do <code>certificate.GetAnyPublicKey</code> interno, que encaminha para <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey%2A?displayProperty=nameWithType>.|
|Sugestão|Começando com aplicativos em execução no .NET Framework 4.7.1, é possível usar a implementação de CryptoServiceProvider usada por padrão no .NET Framework 4.6.1 e versões anteriores adicionando a seguinte opção de configuração à seção [tempo de execução](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) do arquivo de configuração do aplicativo:<pre><code class="language-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.System.Security.Cryptography.Xml.SignedXmlUseLegacyCertificatePrivateKey=true&quot; /&gt;&#13;&#10;</code></pre>|
|Escopo|Microsoft Edge|
|Versão|4.6.2|
|Tipo|Redirecionando|
|APIs afetadas|<ul><li><xref:System.Security.Cryptography.Xml.SignedXml.CheckSignatureReturningKey(System.Security.Cryptography.AsymmetricAlgorithm@)?displayProperty=nameWithType></li></ul>|

