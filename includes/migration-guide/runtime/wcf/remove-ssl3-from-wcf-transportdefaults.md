---
ms.openlocfilehash: 37d771305bb0a4a38eeac9713e8667d158962174
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/01/2019
ms.locfileid: "57788789"
---
### <a name="remove-ssl3-from-the-wcf-transportdefaults"></a>Remoção de Ssl3 de TransportDefaults do WCF

|   |   |
|---|---|
|Detalhes|Ao usar NetTcp com segurança de transporte e um tipo de credencial de certificado, o SSL 3 não é mais um protocolo padrão usado para negociar uma conexão segura. Na maioria dos casos, não deve haver impacto nos aplicativos existentes, pois o TLS 1.0 sempre esteve incluído na lista de protocolos para NetTcp. Todos os clientes existentes devem ser capazes de negociar uma conexão usando, no mínimo, o TLS 1.0.|
|Sugestão|Se Ssl3 for exigido, use um dos seguintes mecanismos de configuração para adicioná-lo à lista de protocolos negociados.<ul><li><xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols></li><li><xref:System.ServiceModel.TcpTransportSecurity.SslProtocols></li><li>[\<transporte > de \<netTcpBinding >](~/docs/framework/configure-apps/file-schema/wcf/transport-of-nettcpbinding.md)</li><li>[Seção &lt;sslStreamSecurity>&gt; de &lt;&gt;customBinding>](~/docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md)</li></ul>|
|Escopo|Microsoft Edge|
|Versão|4.6.2|
|Tipo|Tempo de execução|
|APIs afetadas|<ul><li><xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols?displayProperty=nameWithType></li><li><xref:System.ServiceModel.TcpTransportSecurity.SslProtocols?displayProperty=nameWithType></li></ul>|

