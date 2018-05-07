---
title: '&lt;httpTransport&gt;'
ms.date: 03/30/2017
ms.assetid: 8b30c065-b32a-4fa3-8eb4-5537a9c6b897
ms.openlocfilehash: 77400348e9adc31d8121fc75f46d75d757af270f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="lthttptransportgt"></a>&lt;httpTransport&gt;
Especifica um transporte HTTP para transmissão de mensagens SOAP para uma associação personalizada.  
  
 \<system.serviceModel>  
\<associações >  
\<customBinding>  
\<associação >  
\<httpTransport>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<httpTransport  
    allowCookies=Boolean"  
    authenticationScheme="Digest/Negotiate/Ntlm/Basic/Anonymous"  
    bypassProxyOnLocal=Boolean"  
    hostnameComparisonMode="StrongWildcard/Exact/WeakWildcard"  
    keepAliveEnabled="Boolean"  
    maxBufferSize="Integer"  
    proxyAddress="Uri"  
    proxyAuthenticationScheme="None/Digest/Negotiate/Ntlm/Basic/Anonymous"  
IntegratedWindowsAuthentication: Specifies Windows authentication"  
    realm="String"  
    transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse"  
        unsafeConnectionNtlmAuthentication="Boolean"  
        useDefaultWebProxy="Boolean" />  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|allowCookies|Um valor booleano que especifica se o cliente aceita cookies e os propaga em solicitações futuras. O padrão é `false`.<br /><br /> Você pode usar esse atributo quando você interage com os serviços Web ASMX que usam cookies. Dessa forma, você poderá ter certeza de que os cookies retornados do servidor são copiados automaticamente para todas as solicitações de cliente futuras desse serviço.|  
|authenticationScheme|Especifica o protocolo usado para autenticar solicitações de cliente processadas por um ouvinte HTTP. Os valores válidos incluem o seguinte:<br /><br /> -Digest: Especifica a autenticação digest.<br />-Negotiate: Negocia com o cliente para determinar o esquema de autenticação. Se o cliente e o servidor oferecem suporte ao Kerberos, ele é usado; caso contrário, o NTLM é usado.<br />-Ntlm: Especifica a autenticação NTLM.<br />-Básico: Especifica a autenticação básica.<br />-Anônimo: Especifica a autenticação anônima.<br /><br /> O padrão é anônimo. Esse atributo é do tipo <xref:System.Net.AuthenticationSchemes>. Esse atributo só pode ser definido uma vez.|  
|bypassProxyOnLocal|Um valor booliano que indica se deve ignorar o servidor proxy para endereços locais. O padrão é `false`.<br /><br /> Um endereço local é aquele que está na rede local ou intranet.<br /><br /> Windows Communication Foundation (WCF) sempre ignora o proxy se o endereço do serviço começa com http://localhost.<br /><br /> Se você deseja que os clientes passar por um proxy ao conversar com serviços no mesmo computador, você deve usar o nome de host em vez de localhost.|  
|hostnameComparisonMode|Especifica o modo de comparação de nome de host HTTP usado para analisar URIs. Os valores válidos são,<br /><br /> -StrongWildcard: ("+") corresponde a todos os possíveis nomes de host no contexto do esquema especificado, porta e URI relativo.<br />-Exato: sem curingas<br />-WeakWildcard: ("*") corresponde a todas as possíveis hostname no contexto do esquema especificado, porta e UIR relativo que não foram correspondidas explicitamente ou por meio do mecanismo de curinga forte.<br /><br /> O padrão é StrongWildcard. Esse atributo é do tipo `System.ServiceModel.HostnameComparisonMode`.|  
|keepAliveEnabled|Um valor booleano que especifica se deve fazer uma conexão persistente para o recurso de internet.|  
|maxBufferSize|Um inteiro positivo que especifica o tamanho máximo do buffer. O padrão é 524288|  
|proxyAddress|Um URI que especifica o endereço do proxy HTTP. Se `useSystemWebProxy` é `true`, essa configuração deve ser `null`. O padrão é `null`.|  
|proxyAuthenticationScheme|Especifica o protocolo usado para autenticar solicitações de cliente processadas por um proxy HTTP. Os valores válidos incluem o seguinte:<br /><br /> -Nenhum: Nenhuma autenticação é realizada.<br />-Digest: Especifica a autenticação digest.<br />-Negotiate: Negocia com o cliente para determinar o esquema de autenticação. Se o cliente e o servidor oferecem suporte ao Kerberos, ele é usado; caso contrário, o NTLM é usado.<br />-Ntlm: Especifica a autenticação NTLM.<br />-Básico: Especifica a autenticação básica.<br />-Anônimo: Especifica a autenticação anônima.<br />-IntegratedWindowsAuthentication: Especifica a autenticação do Windows.<br /><br /> O padrão é anônimo. Esse atributo é do tipo <xref:System.Net.AuthenticationSchemes>.|  
|território|Uma cadeia de caracteres que especifica o domínio a ser usado no proxy/servidor. O padrão é uma cadeia de caracteres vazia.<br /><br /> Servidores usam realms para particionar a recursos protegidos. Cada partição pode ter seu próprio banco de dados de esquema e/ou autorização de autenticação. Territórios são usados apenas para basic e a autenticação digest. Depois que um cliente é autenticado com êxito, a autenticação é válida para todos os recursos de um determinado território. Para obter uma descrição detalhada de territórios, consulte RFC 2617 no http://www.ietf.org.|  
|transferMode|Especifica se as mensagens são armazenados em buffer ou transmitidas ou uma solicitação ou resposta. Os valores válidos incluem o seguinte:<br /><br /> -Buffer: As mensagens de solicitação e resposta são armazenados em buffer.<br />-Streaming: As mensagens de solicitação e resposta são transmitidas.<br />-StreamedRequest: A mensagem de solicitação é transmitida e a mensagem de resposta é armazenada em buffer.<br />-StreamedResponse: A mensagem de solicitação é armazenado em buffer e a mensagem de resposta é transmitida.<br /><br /> O padrão é armazenado em buffer. Esse atributo é do tipo <xref:System.ServiceModel.TransferMode> .|  
|unsafeConnectionNtlmAuthentication|Um valor booleano que especifica se o compartilhamento de Conexão não segura está habilitada no servidor. O padrão é `false`. Se estiver habilitado, a autenticação NTLM será executada uma vez em cada conexão TCP.|  
|useDefaultWebProxy|Um valor booleano que especifica se as configurações de proxy de todo o computador são usadas em vez de configurações específicas do usuário. O padrão é `true`.|  
  
### <a name="child-elements"></a>Elementos filho  
 Nenhum  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<associação >](../../../../../docs/framework/misc/binding.md)|Define todos os recursos de associação da associação personalizada.|  
  
## <a name="remarks"></a>Comentários  
 O `httpTransport` elemento é o ponto de partida para criar uma associação personalizada que implementa o protocolo de transporte HTTP. O HTTP é o transporte primário usado para fins de interoperabilidade. Esse transporte é suportado pelo Windows Communication Foundation (WCF) para garantir a interoperabilidade com outros pilhas de serviços não WCF Web.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Configuration.HttpTransportElement>  
 <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
 <xref:System.ServiceModel.Channels.TransportBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [Transportes](../../../../../docs/framework/wcf/feature-details/transports.md)  
 [Escolhendo um transporte](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 [Associações](../../../../../docs/framework/wcf/bindings.md)  
 [Estendendo associações](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [Associações personalizadas](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
