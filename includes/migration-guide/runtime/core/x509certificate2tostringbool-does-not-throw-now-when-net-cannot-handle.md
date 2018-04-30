### <a name="x509certificate2tostringbool-does-not-throw-now-when-net-cannot-handle-the-certificate"></a>X509Certificate2.ToString(bool) agora não é gerado quando o .NET não pode tratar o certificado

|   |   |
|---|---|
|Detalhes|Anteriormente, esse método seria lançado se <code>true</code> fosse passado para o parâmetro verbose e se houvesse certificados instalados que não tivessem suporte do .NET Framework. Agora, o método será bem-sucedido e retornará uma cadeia de caracteres válida que omita as partes inacessíveis do certificado.|
|Sugestão|Qualquer código dependente do <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString(System.Boolean)> deve ser atualizado para esperar que a cadeia de caracteres retornada possa excluir alguns dados do certificado (como chave pública, chave privada e extensões) em alguns casos nos quais a API teria sido gerada anteriormente.|
|Escopo|Microsoft Edge|
|Versão|4.6|
|Tipo|Tempo de execução|
|APIs afetadas|<ul><li><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString(System.Boolean)?displayProperty=nameWithType></li></ul>|

