### <a name="rsacngverifyhash-now-returns-false-for-any-verification-failure"></a>RSACng.VerifyHash agora retorna False para qualquer falha de verificação

|   |   |
|---|---|
|Detalhes|A partir do .NET Framework 4.6.2, esse método retornará <strong>False</strong> se a assinatura em si estiver incorretamente formatada. Agora, ele retornará false para qualquer falha de verificação. No .NET Framework 4.6 e 4.6.1, o método gera <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> se a assinatura em si está incorretamente formatada.|
|Sugestão|Qualquer código cuja execução dependa da identificação de <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> deverá ser executado se a validação falhar e o método retornar <strong>False</strong>.|
|Escopo|Secundário|
|Versão|4.6.2|
|Tipo|Tempo de execução|
|APIs afetadas|<ul><li><xref:System.Security.Cryptography.RSACng.VerifyHash(System.Byte[],System.Byte[],System.Security.Cryptography.HashAlgorithmName,System.Security.Cryptography.RSASignaturePadding)?displayProperty=nameWithType></li></ul>|

