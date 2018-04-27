### <a name="apps-published-with-clickonce-that-use-a-sha-256-code-signing-certificate-may-fail-on-windows-2003"></a>Os aplicativos publicados com ClickOnce que usam um certificado de autenticação de código SHA-256 podem falhar no Windows 2003

|   |   |
|---|---|
|Detalhes|O executável é assinado com SHA256. Antes, ele era assinado com SHA1, independentemente se o certificado de assinatura de código era SHA-1 ou SHA-256. Isso se aplica a:<ul><li>Todos os aplicativos compilados com o Visual Studio 2012 ou posterior.</li><li>Os aplicativos compilados com o Visual Studio 2010 ou anteriores em sistemas com o .NET Framework 4.5.</li></ul>Além disso, se o .NET Framework 4.5 ou posterior estiver presente, o manifesto do ClickOnce também será assinado com certificados SHA-256 para SHA-256, independentemente da versão do .NET Framework na qual ele foi compilado.|
|Sugestão|A mudança na assinatura do executável do ClickOnce afeta apenas os sistemas Windows Server 2003; eles exigem a instalação do KB 938397. A alteração na assinatura do manifesto com SHA-256, mesmo quando um aplicativo destina-se ao .NET Framework 4.0 ou versões anteriores, introduz uma dependência de tempo de execução no .NET Framework 4.5 ou versões posteriores.|
|Escopo|Microsoft Edge|
|Versão|4.5|
|Tipo|Redirecionando|

