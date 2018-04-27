### <a name="deserialization-of-mailmessage-objects-serialized-under-the-net-framework-45-may-fail"></a>Desserialização de objetos MailMessage serializados no .NET Framework 4.5 pode falhar

|   |   |
|---|---|
|Detalhes|A partir do .NET Framework 4.5, os objetos <xref:System.Web.Mail.MailMessage> podem incluir caracteres não ASCII. No .NET Framework 4, somente caracteres ASCII têm suporte. Os objetos <xref:System.Web.Mail.MailMessage> que contêm caracteres não ASCII e são serializados no .NET Framework 4.5 ou versões posteriores não podem ser desserializados no .NET Framework 4.|
|Sugestão|Verifique se o seu código fornece tratamento de exceção ao desserializar um objeto <xref:System.Web.Mail.MailMessage>.|
|Escopo|Secundário|
|Versão|4.5|
|Tipo|Tempo de execução|
|APIs afetadas|<ul><li><xref:System.Web.Mail.MailMessage?displayProperty=nameWithType></li></ul>|

