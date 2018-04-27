### <a name="clickonce-supports-sha-256-on-40-targeted-apps"></a>ClickOnce é compatível com SHA-256 em aplicativos destinados ao 4.0

|   |   |
|---|---|
|Detalhes|Anteriormente, um aplicativo ClickOnce com um certificado assinado com SHA-256 exigiria .NET 4.5 ou versões posteriores para estar presente, mesmo que o aplicativo se destinasse ao 4.0. Agora, os aplicativos ClickOnce destinados ao 4.0 podem ser executados no 4.0, mesmo se assinados com SHA-256.|
|Sugestão|Essa alteração elimina essa dependência e permite que certificados SHA-256 sejam usados para assinar aplicativos ClickOnce destinados ao .NET Framework 4 e versões anteriores.|
|Escopo|Secundário|
|Versão|4.6|
|Tipo|Redirecionando|

