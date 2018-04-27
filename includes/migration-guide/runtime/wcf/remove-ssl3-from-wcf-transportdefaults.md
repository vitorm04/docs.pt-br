### <a name="remove-ssl3-from-the-wcf-transportdefaults"></a>Remoção de Ssl3 de TransportDefaults do WCF

|   |   |
|---|---|
|Detalhes|Ao usar NetTcp com segurança de transporte e um tipo de credencial de certificado, o SSL 3 não é mais um protocolo padrão usado para negociar uma conexão segura. Na maioria dos casos, não deve haver impacto nos aplicativos existentes, pois o TLS 1.0 sempre esteve incluído na lista de protocolos para NetTcp. Todos os clientes existentes devem ser capazes de negociar uma conexão usando, no mínimo, o TLS 1.0.|
|Sugestão|Se Ssl3 for exigido, use um dos seguintes mecanismos de configuração para adicioná-lo à lista de protocolos negociados.<ul><li><xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols></li><li><xref:System.ServiceModel.TcpTransportSecurity.SslProtocols></li><li>[<](~/docs/framework/configure-apps/file-schema/wcf/transport-of-nettcpbinding.md)</li><li>[&lt;sslStreamSecurity&gt; section of &lt;customBinding&gt;]~/docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md)</li></ul>|
|Escopo|Microsoft Edge|
|Versão|4.6.2|
|Tipo|Tempo de execução|
|APIs afetadas|<ul><li><xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols?displayProperty=nameWithType></li><li><xref:System.ServiceModel.TcpTransportSecurity.SslProtocols?displayProperty=nameWithType></li></ul>|

