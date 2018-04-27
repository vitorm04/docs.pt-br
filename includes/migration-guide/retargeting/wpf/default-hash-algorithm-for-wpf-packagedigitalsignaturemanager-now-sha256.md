### <a name="the-default-hash-algorithm-for-wpf-packagedigitalsignaturemanager-is-now-sha256"></a>O algoritmo de hash padrão para o PackageDigitalSignatureManager do WPF agora é SHA256

|   |   |
|---|---|
|Detalhes|O <code>System.IO.Packaging.PackageDigitalSignatureManager</code> fornece funcionalidade para assinaturas digitais em relação a pacotes do WPF.  No .NET Framework 4.7 e em versões anteriores, o algoritmo padrão (<xref:System.IO.Packaging.PackageDigitalSignatureManager.DefaultHashAlgorithm?displayProperty=nameWithType>) usado para assinar partes de um pacote era SHA1.  Devido a questões de segurança recentes com SHA1, esse padrão foi alterado para o SHA256 a partir do .NET Framework 4.7.1.  Esta alteração afeta a assinatura de todos os pacotes, incluindo documentos XPS.|
|Sugestão|Um desenvolvedor que deseja usar esta alteração enquanto tem como destino uma versão do framework abaixo do .NET 4.7.1 ou um desenvolvedor que precisa da funcionalidade anterior enquanto tem como destino o .NET 4.7.1 ou posterior pode define o seguinte sinalizador de AppContext adequadamente.  O valor true fará com que SHA1 seja usado como algoritmo padrão; false fará com que SHA256 seja usado.<pre><code class="language-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.MS.Internal.UseSha1AsDefaultHashAlgorithmForDigitalSignatures=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Escopo|Microsoft Edge|
|Versão|4.7.1|
|Tipo|Redirecionando|
|APIs afetadas|<ul><li><xref:System.IO.Packaging.PackageDigitalSignatureManager.DefaultHashAlgorithm?displayProperty=nameWithType></li></ul>|

