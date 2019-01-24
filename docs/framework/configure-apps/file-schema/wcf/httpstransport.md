---
title: '&lt;httpsTransport&gt;'
ms.date: 03/30/2017
ms.assetid: f6ed4bc0-7e38-4348-9259-30bf61eb9435
ms.openlocfilehash: 8a2c76fd6d657a4b86909469296e3b4c6b47a926
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54624568"
---
# <a name="lthttpstransportgt"></a>&lt;httpsTransport&gt;
Especifica um transporte HTTP para transmissão de mensagens SOAP para uma associação personalizada.  
  
 \<system.serviceModel>  
\<bindings>  
\<customBinding>  
\<binding>  
\<httpsTransport>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<httpsTransport allowCookies="Boolean"
                authenticationScheme="Digest/Negotiate/Ntlm/Basic/Anonymous"
                bypassProxyOnLocal="Boolean"
                hostnameComparisonMode="StrongWildcard/Exact/WeakWildcard"
                manualAddressing="Boolean"
                maxBufferPoolSize="Integer"
                maxBufferSize="Integer"
                maxReceivedMessageSize="Integer"
                proxyAddress="Uri"
                proxyAuthenticationScheme="None/Digest/Negotiate/Ntlm/Basic/Anonymous"
                realm="String"
                requireClientCertificate="Boolean"
                transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse"
                unsafeConnectionNtlmAuthentication="Boolean"
                useDefaultWebProxy="Boolean" />
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|allowCookies|Um valor booliano que especifica se o cliente aceita cookies e propaga-os em solicitações futuras. O padrão é `false`.<br /><br /> Você pode usar esse atributo quando você interage com os serviços Web ASMX que usam cookies. Dessa forma, você pode ter certeza de que os cookies retornados do servidor são copiados automaticamente para todas as solicitações futuras de cliente para o serviço.|  
|authenticationScheme|Especifica o protocolo usado para autenticar solicitações de cliente sendo processadas por um ouvinte HTTP. Os valores válidos incluem o seguinte:<br /><br /> -Resumo: Especifica a autenticação Digest.<br />-Negotiate: Negocia com o cliente para determinar o esquema de autenticação. Se o cliente e o servidor oferecem suporte ao Kerberos, ele é usado; caso contrário, o NTLM é usado.<br />-   Ntlm: Especifica autenticação NTLM.<br />-Básico: Especifica autenticação básica.<br />-Anônimo: Especifica autenticação anônima.<br /><br /> O padrão é anônimo. Esse atributo é do tipo <xref:System.Net.AuthenticationSchemes>. Esse atributo só pode ser definido uma vez.|  
|bypassProxyOnLocal|Um valor booliano que indica se deve ignorar o servidor proxy para endereços locais. O padrão é `false`.<br /><br /> Um endereço local é aquele que está na rede local ou da intranet.<br /><br /> Windows Communication Foundation (WCF) sempre ignora o proxy se o endereço do serviço começa com `http://localhost`.<br /><br /> Se você deseja que os clientes para passar por um proxy ao conversar com os serviços no mesmo computador, você deve usar o nome de host em vez do localhost.|  
|hostnameComparisonMode|Especifica o modo de comparação de nome de host HTTP usado para analisar URIs. Os valores válidos são,<br /><br /> -StrongWildcard: ("+") corresponde a todos os possíveis nomes de host no contexto do esquema especificado, porta e o URI relativo.<br />-Exato: sem curingas<br />-WeakWildcard: ("\*") corresponde ao nome de host de todos os possíveis no contexto do esquema especificado, porta e UIR relativa que não foram correspondidas explicitamente ou por meio do mecanismo de curinga forte.<br /><br /> O padrão é StrongWildcard. Esse atributo é do tipo `System.ServiceModel.HostnameComparison`.|  
|manualAddressing|Um valor booliano que permite ao usuário assumir o controle do endereçamento de mensagem. Essa propriedade normalmente é usada em cenários de roteador, onde o aplicativo determina que uma de vários destinos para enviar uma mensagem.<br /><br /> Quando definido como `true`, o canal pressupõe que a mensagem já foi abordada e não adiciona qualquer informação adicional a ele. O usuário pode, em seguida, abordar todas as mensagens individualmente.<br /><br /> Quando definido como `false`, o mecanismo de endereçamento padrão Windows Communication Foundation (WCF) cria automaticamente os endereços para todas as mensagens.<br /><br /> O padrão é `false`.|  
|maxBufferPoolSize|Um inteiro positivo que especifica o tamanho máximo do pool de buffers. O padrão é 524288.<br /><br /> Muitas partes do WCF usam buffers. Criação e destruição de buffers de cada vez que elas são usadas são caro e coleta de lixo para buffers também é dispendiosa. Com os pools de buffer, usar um buffer do pool, usá-lo e retorná-lo ao pool quando terminar. Portanto, a sobrecarga na criação e destruição de buffers é evitada.|  
|maxBufferSize|Um inteiro positivo que especifica o tamanho máximo do buffer. O padrão é 524288|  
|maxReceivedMessageSize|Um inteiro positivo que especifica o tamanho de mensagem máximo permitido que pode ser recebido. O padrão é 65536.|  
|proxyAddress|Um URI que especifica o endereço do proxy HTTP. Se `useSystemWebProxy` está `true`, essa configuração deve ser `null`. O padrão é `null`.|  
|proxyAuthenticationScheme|Especifica o protocolo usado para autenticar solicitações de cliente sendo processadas por um proxy HTTP. Os valores válidos incluem o seguinte:<br /><br /> -None: Nenhuma autenticação é executada.<br />-Resumo: Especifica a autenticação Digest.<br />-Negotiate: Negocia com o cliente para determinar o esquema de autenticação. Se o cliente e o servidor oferecem suporte ao Kerberos, ele é usado; caso contrário, o NTLM é usado.<br />-   Ntlm: Especifica autenticação NTLM.<br />-Básico: Especifica autenticação básica.<br />-Anônimo: Especifica autenticação anônima.<br /><br /> O padrão é anônimo. Esse atributo é do tipo <xref:System.Net.AuthenticationSchemes>. Observe que `IntegratedWindowsAuthentication` não tem suporte.|  
|território|Uma cadeia de caracteres que especifica o domínio a ser usado no proxy/servidor. O padrão é uma cadeia de caracteres vazia.<br /><br /> Servidores usam realms para dividir os recursos protegidos. Cada partição pode ter seu próprio banco de dados de esquema e/ou autorização de autenticação. Realms são usados somente para basic e autenticação digest. Depois que um cliente é autenticado com êxito, a autenticação é válida para todos os recursos de um determinado território. Para obter uma descrição detalhada de territórios, consulte RFC 2617 na [site do IETF](https://www.ietf.org).|  
|requireClientCertificate|Um valor booliano que especifica se o servidor exige que o cliente forneça um certificado de cliente como parte do handshake HTTPS. O padrão é `false`.|  
|transferMode|Especifica se as mensagens são armazenadas em buffer ou transmitidas ou uma solicitação ou resposta. Os valores válidos incluem o seguinte:<br /><br /> -Armazenada em buffer: As mensagens de solicitação e resposta são armazenados em buffer.<br />-Transmitidos: As mensagens de solicitação e resposta são transmitidas.<br />-   StreamedRequest: A mensagem de solicitação é transmitida e a mensagem de resposta é armazenada em buffer.<br />-   StreamedResponse: A mensagem de solicitação é armazenada em buffer e a mensagem de resposta é transmitida.<br /><br /> O padrão é armazenada em buffer. Esse atributo é do tipo <xref:System.ServiceModel.TransferMode>.|  
|unsafeConnectionNtlmAuthentication|Um valor booliano que especifica se o compartilhamento de Conexão não segura está habilitada no servidor. O padrão é `false`. Se estiver habilitado, a autenticação NTLM será executada uma vez em cada conexão TCP.|  
|useDefaultWebProxy|Um valor booliano que especifica se as configurações de proxy de todo o computador são usadas em vez de configurações específicas do usuário. O padrão é `true`.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<binding>](../../../../../docs/framework/misc/binding.md)|Define todos os recursos de associação de associação personalizada.|  
  
## <a name="remarks"></a>Comentários  
 O `httpsTransport` elemento é o ponto de partida para criar uma associação personalizada que implementa o protocolo de transporte HTTPS. HTTPS é o transporte primário usado para fins de interoperabilidade segura. Há suporte pelo Windows Communication Foundation (WCF) para garantir a interoperabilidade com outras pilhas de serviços da Web para HTTPS.  
  
## <a name="see-also"></a>Consulte também
- <xref:System.ServiceModel.Configuration.HttpsTransportElement>
- <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Transportes](../../../../../docs/framework/wcf/feature-details/transports.md)
- [Escolhendo um transporte](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)
- [Associações](../../../../../docs/framework/wcf/bindings.md)
- [Estendendo associações](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [Associações personalizadas](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [\<customBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
