---
title: Associações de interoperabilidade fornecidas pelo sistema oferece suporte para protocolos de serviços Web
ms.date: 03/30/2017
helpviewer_keywords:
- WS-protocols
- Web services protocols
- Windows Communication Foundation, Web service protocols
ms.assetid: 1f7fc4ff-30fe-4e46-adda-91caad3b06c6
ms.openlocfilehash: 963325604f66ddd4f8470933584b7880c86403bc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69951566"
---
# <a name="web-services-protocols-supported-by-system-provided-interoperability-bindings"></a>Associações de interoperabilidade fornecidas pelo sistema oferece suporte para protocolos de serviços Web
O Windows Communication Foundation (WCF) foi criado para interoperar com serviços Web que dão suporte a um conjunto de especificações conhecidas como especificações de serviços da Web. Para simplificar a configuração de serviço para práticas recomendadas de interoperabilidade, o WCF apresenta três associações <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType>interoperáveis <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType>fornecidas pelo sistema:, <xref:System.ServiceModel.WSHttpBinding?displayProperty=nameWithType>e. Para a interoperabilidade com a organização para o avanço de padrões de OASIS (padrões de informações estruturadas), o WCF inclui uma <xref:System.ServiceModel.WS2007HttpBinding?displayProperty=nameWithType>Associação de sistema interoperável fornecida por sistemas:. Para a publicação de metadados, o WCF inclui duas associações interoperáveis fornecidas pelo sistema: [ \<mexHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpbinding.md) e [ \<mexHttpsBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpsbinding.md). Este tópico lista as especificações com suporte de associações interoperáveis fornecidas pelo sistema.  
  
## <a name="web-services-protocols-supported-by-basichttpbinding-wshttpbinding-ws2007httpbinding-and-wsdualhttpbinding-bindings"></a>Protocolos de serviços Web com suporte pelas associações basicHttpBinding, wsHttpBinding, ws2007HttpBinding e wsDualHttpBinding  
  
### <a name="all-bindings"></a>Todas as associações  
 [ As\<associações BasicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md), [ \<WSHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)e [ \<ws2007HttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md) dão suporte aos seguintes protocolos.  
  
> [!NOTE]
> Para obter informações sobre associações usadas para publicar metadados, consulte a seção "associações de metadados fornecidas pelo sistema" mais adiante neste tópico.  
  
|Categoria|Protocol|Especificação e uso|  
|--------------|--------------|-----------------------------|  
|Porta|HTTP 1,1|[HTTP 1,1](https://go.microsoft.com/fwlink/?LinkId=84048)<br /><br /> `BasicHttpBinding`, `WSHttpBinding` e`WS2007HttpBinding` usam os transportes http e HTTPS.|  
|Mensagens|MTOM|[MTOM](https://go.microsoft.com/fwlink/?LinkId=95326)<br /><br /> `basicHttpBinding`, `wsHttpBinding` e`ws2007HttpBinding` dão suporte ao mecanismo de otimização de transmissão de mensagens (MTOM). Não usado por padrão. Para usar o MTOM, defina `messageEncoding` o atributo `"Mtom"`como.<br /><br /> Exemplo:<br /><br /> `<wsHttpBinding> <binding messageEncoding="Mtom"/> </wsHttpBinding>`|  
|Metadados|WSDL 1,1|[WSDL 1,1](https://go.microsoft.com/fwlink/?LinkId=94859)<br /><br /> O WCF usa WSDL (Web Services Description Language) para descrever os serviços.|  
|Metadados|WS-Policy|[WS-Policy](https://go.microsoft.com/fwlink/?LinkId=94864)<br /><br /> O WCF usa a especificação WS-Policy juntamente com declarações específicas de domínio para descrever os requisitos de serviço e os recursos.|  
|Metadados|WS-Policy 1,5|[WS-Policy 1,5](https://go.microsoft.com/fwlink/?LinkId=95327)<br /><br /> O WCF usa a especificação WS-Policy juntamente com declarações específicas de domínio para descrever os requisitos de serviço e os recursos.|  
|Metadados|WS-PolicyAttachment|[WS-PolicyAttachment](https://go.microsoft.com/fwlink/?LinkId=95328)<br /><br /> O WCF implementa o WS-PolicyAttachment para anexar expressões de política em vários escopos no WSDL (Web Services Description Language).|  
|Metadados|WS-MetadataExchange|[WS-MetadataExchange](https://go.microsoft.com/fwlink/?LinkId=94868)<br /><br /> O WCF implementa o WS-MetadataExchange para recuperar o esquema XML, o WSDL e o WS-Policy.|  
  
### <a name="basichttpbinding"></a>basicHttpBinding  
  
|Categoria|Protocol|Especificação e uso|  
|--------------|--------------|-----------------------------|  
|Mensagens|SOAP 1,1|[SOAP 1,1](https://go.microsoft.com/fwlink/?LinkId=90520)<br /><br /> De acordo com o perfil básico 1,1, `basicHttpBinding` o elemento implementa o protocolo de mensagem SOAP 1,1.|  
|Segurança|Segurança de mensagem SOAP do WSS 1,0|[Segurança de mensagem SOAP do WSS 1,0](https://go.microsoft.com/fwlink/?LinkId=94684)<br /><br /> De acordo com o perfil de segurança básico, `basicHttpBinding` o elemento implementa a especificação de especificação Web Services Security (WSS) SOAP Message Security 1,0 para o nome de usuário/senha e a segurança baseada em X. 509.<br /><br /> `<basicHttpBinding> <binding name="Binding1"> <security mode="TransportWithMessageCredential &#124;                     "Message" .../> </binding> </basicHttpBinding>`|  
|Segurança|Perfil do UsernameToken de segurança de mensagem SOAP do WSS 1,0|[Perfil do UsernameToken de segurança de mensagem SOAP do WSS 1,0](https://go.microsoft.com/fwlink/?LinkId=95334)<br /><br /> `<basicHttpBinding> <binding name="Binding1"> <security mode="TransportWithMessageCredential"> <transport clientCredentialType="Basic"/> </security> </basicHttpBinding>`|  
|Segurança|Segurança de mensagem SOAP do WSS X. 509 perfil de token de certificado 1,0|[Segurança de mensagem SOAP do WSS X. 509 perfil de token de certificado 1,0](https://go.microsoft.com/fwlink/?LinkId=95335)<br /><br /> `<basicHttpBinding>   <security mode="Message"> <message clientCredentialType="Certificate"/> </security> </basicHttpBinding>`|  
  
### <a name="wshttpbinding-ws2007httpbinding-and-wsdualhttpbinding"></a>wsHttpBinding, ws2007HttpBinding e wsDualHttpBinding  
  
|Categoria|Protocol|Especificação e uso|  
|--------------|--------------|-----------------------------|  
|Mensagens|SOAP 1,2|[Primer](https://go.microsoft.com/fwlink/?LinkId=48282)<br /><br /> [Estrutura de mensagens](https://go.microsoft.com/fwlink/?LinkId=94664)<br /><br /> [Adjuncts (incluindo associação HTTP)](https://go.microsoft.com/fwlink/?LinkId=95329)|  
|Mensagens|WS-Addressing 2005/08|[Endereçamento de serviços da Web 1,0-Core](https://go.microsoft.com/fwlink/?LinkId=90574)<br /><br /> [Endereçamento de serviços da Web 1,0-SOAP](https://go.microsoft.com/fwlink/?LinkId=95330)<br /><br /> O `wsHttpBinding`, `ws2007HttpBinding`o e`wsDualHttpBinding` o implementam a recomendação de WS-Addressing do World Wide Web Consortium (W3C) para habilitar mensagens assíncronas, correlação de mensagens e mecanismos de endereçamento de transporte neutro.<br /><br /> O WCF não dá suporte à criptografia de cabeçalhos de WS-Addressing, embora isso seja permitido pelas especificações WS-*.|  
|Mensagens|WS-Addressing 1,0-Metadata|[Metadados 1,0 do WS-Addressing](https://www.w3.org/2007/05/addressing/metadata) O suporte para esse protocolo é habilitado pela definição da versão da política no comportamento de metadados-com PolicyVersion definido como 1,2 (o padrão), a descrição do WSDL é compatível com o WSDL do WS-Addressing, com PolicyVersion definido como 1,5, a descrição do WSDL é em conformidade com os metadados do WS-Addressing.<br /><br /> O WCF não dá suporte à criptografia de cabeçalhos de WS-Addressing, embora isso seja permitido pelas especificações WS-*.|  
|Segurança|Segurança de mensagem SOAP do WSS 1,0|[Segurança de mensagem SOAP do WSS 1,0](https://go.microsoft.com/fwlink/?LinkId=94684)<br /><br /> Use quando o `securityMode` atributo for definido como "wsSecurityOverHttp" (padrão) e os parâmetros forem configurados usando um `wsSecurity` elemento filho.<br /><br /> `<wsHttpBinding>   <binding name="myBinding">      <security mode="Message" .../>   </binding> </wsHttpBinding>`|  
|Segurança|Perfil do UsernameToken de segurança de mensagem SOAP do WSS 1,1|[Perfil do UsernameToken de segurança de mensagem SOAP do WSS 1,0](https://go.microsoft.com/fwlink/?LinkId=95331)<br /><br /> Use quando o `wsSecurity` atributo do `authenticationMode` elemento estiver definido como "username".<br /><br /> `<wsHttpBinding>   <binding name="MyBinding">     <security mode="Message>       <message           clientCredentialType="UserName        negotiateServiceCredential="false"        establishSecurityContext="false"/>     </security> </binding> </wsHttpBinding>`|  
|Segurança|Segurança de mensagem SOAP do WSS X. 509 perfil de token de certificado 1,1|[Segurança de mensagem SOAP do WSS X. 509 perfil de token de certificado 1,1](https://go.microsoft.com/fwlink/?LinkId=95332)<br /><br /> Use para proteção de mensagem quando `wsSecurity` o atributo `authenticationMode` do elemento estiver definido como "username", "Certificate" ou "None". Além disso, use isso para autenticação de cliente `wsSecurity` quando o `authenticationMode` atributo do elemento estiver definido como "certificado".<br /><br /> `<wsHttpBinding>   <binding name="MyBinding">     <security mode="Message>       <message           clientCredentialType="Certificate"        negotiateServiceCredential="false"        establishSecurityContext="false"/>     </security>   </binding> </wsHttpBinding>`|  
|Segurança|Perfil de token Kerberos de segurança de mensagem SOAP do WSS 1,1|[Perfil de token Kerberos de segurança de mensagem SOAP do WSS 1,1](https://go.microsoft.com/fwlink/?LinkId=95333)<br /><br /> Use para autenticação e proteção de mensagem quando `wsSecurity` o atributo `authenticationMode` do elemento estiver definido como "Windows".<br /><br /> `<wsHttpBinding>   <binding name="MyBinding">     <security mode="Message>       <message           clientCredentialType="Windows"        negotiateServiceCredential="false"        establishSecurityContext="false"/>     </security>   </binding> </wsHttpBinding>`|  
|Segurança|WS-SecureConversation|[WS-SecureConversation](https://go.microsoft.com/fwlink/?LinkId=95317)<br /><br /> Use para fornecer uma sessão segura quando o `security/@mode` atributo for definido como "Message" e o `message/@establishSecurityContext` atributo for definido como "true" (padrão).|  
|Segurança|WS-Trust|[WS-Trust](https://go.microsoft.com/fwlink/?LinkId=95318)<br /><br /> Usado pelo WS-SecureConversation (veja acima).|  
|Mensagens confiáveis|WS-ReliableMessaging|[WS-ReliableMessaging](https://go.microsoft.com/fwlink/?LinkId=95322)<br /><br /> Use quando a associação estiver configurada `reliableSession`para usar.<br /><br /> `<wsHttpBinding>  <binding name="myBinding">    <reliableSession/>   </binding> </wsHttpBinding>`|  
|Transações|WS-AtomicTransaction|[WS-AtomicTransaction](https://go.microsoft.com/fwlink/?LinkId=95323)<br /><br /> Use para comunicação entre gerenciadores de transações. Os clientes e serviços WCF sempre usam gerenciadores de transações locais.|  
|Transações|WS-Coordination|[WS-Coordination](https://go.microsoft.com/fwlink/?LinkId=95324)<br /><br /> Use para fluir o contexto da transação `flowTransactions` quando o atributo estiver definido como "Allowed" ou "required".<br /><br /> `<wsHttpBinding>   <binding transactionFlow="true"/> </wsHttpBinding>`|  
  
## <a name="wsfederationhttpbinding-and-ws2007federationhttpbinding"></a>wsFederationHttpBinding e ws2007FederationHttpBinding  
 [ Os\<elementos WSFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) e [ \<ws2007FederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/ws2007federationhttpbinding.md) são introduzidos para oferecer suporte a cenários federados, em que um terceiro emite um token usado para autenticar um cliente. Além dos protocolos usados pelo `wsHttpBinding`, `wsFederationHttpBinding` aproveita:  
  
- `WS-Trust`para emissão de tokens.  
  
- Perfil de token SAML (declaração de asserções de segurança) do WSS 1,0 e 1,1 para o formato de token emitido com mais frequência.  
  
 Exemplo:  
  
```xml  
<wsFederationHttpBinding>  
  <binding name="myBinding">  
     <security mode="Message">  
       <message issuedKeyType="Symmetric"   
                issuedTokenType="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1">  
         <issuerMetadata address =   
         'http://localhost/FederationSample/HomeRealmSTS/STS.svc/mex'>  
       </message>  
     </security>  
  </binding>  
</wsFederationHttpBinding>  
```  
  
 Para obter mais informações, consulte [Federação](../../../../docs/framework/wcf/feature-details/federation.md) .  
  
## <a name="system-provided-metadata-bindings"></a>Associações de metadados fornecidas pelo sistema  
 As tabelas a seguir descrevem os protocolos compatíveis com as associações de metadados interoperáveis fornecidas pelo sistema expostas pela <xref:System.ServiceModel.Description.MetadataExchangeBindings?displayProperty=nameWithType> classe.  
  
### <a name="mexhttpbinding"></a>mexHttpBinding  
 A associação de [ \<> mexHttpBinding](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpbinding.md) dá suporte aos seguintes protocolos. Para obter mais informações sobre como usar essa associação, consulte [publicando metadados](../../../../docs/framework/wcf/feature-details/publishing-metadata.md).  
  
|Categoria|Protocol|Especificação e uso|  
|--------------|--------------|-----------------------------|  
|Porta|HTTP 1,1|[HTTP 1,1](https://go.microsoft.com/fwlink/?LinkId=84048)|  
|Mensagens|SOAP 1,2|[Primer](https://go.microsoft.com/fwlink/?LinkId=48282)<br /><br /> [Estrutura de mensagens](https://go.microsoft.com/fwlink/?LinkId=94664)<br /><br /> [Adjuncts (incluindo associação HTTP)](https://go.microsoft.com/fwlink/?LinkId=95329)|  
|Mensagens|WS-Addressing 2005/08|[Endereçamento de serviços da Web 1,0-Core](https://go.microsoft.com/fwlink/?LinkId=90574)<br /><br /> [Endereçamento de serviços da Web 1,0-SOAP](https://go.microsoft.com/fwlink/?LinkId=95330)|  
|Metadados|WS-MetadataExchange|[WS-MetadataExchange](https://go.microsoft.com/fwlink/?LinkId=94868)<br /><br /> O WCF implementa o WS-MetadataExchange para recuperar o esquema XML, o WSDL e o WS-Policy.|  
  
### <a name="mexhttpsbinding"></a>mexHttpsBinding  
 mexHttpsBinding > dá suporte aos seguintes protocolos. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpsbinding.md) Para obter mais informações sobre como usar essa associação, consulte [publicando metadados](../../../../docs/framework/wcf/feature-details/publishing-metadata.md).  
  
|Categoria|Protocol|Especificação e uso|  
|--------------|--------------|-----------------------------|  
|Porta|HTTP 1,1|[HTTP 1,1](https://go.microsoft.com/fwlink/?LinkId=84048)<br /><br /> A segurança de transporte está habilitada.|  
|Mensagens|SOAP 1,2|[Primer](https://go.microsoft.com/fwlink/?LinkId=48282)<br /><br /> [Estrutura de mensagens](https://go.microsoft.com/fwlink/?LinkId=94664)<br /><br /> [Adjuncts (incluindo associação HTTP)](https://go.microsoft.com/fwlink/?LinkId=95329)|  
|Mensagens|WS-Addressing 2005/08|[Endereçamento de serviços da Web 1,0-Core](https://go.microsoft.com/fwlink/?LinkId=90574)<br /><br /> [Endereçamento de serviços da Web 1,0-SOAP](https://go.microsoft.com/fwlink/?LinkId=95330)|  
|Metadados|WS-MetadataExchange|[WS-MetadataExchange](https://go.microsoft.com/fwlink/?LinkId=94868)<br /><br /> O WCF implementa o WS-MetadataExchange para recuperar o esquema XML, o WSDL e o WS-Policy.|  
  
## <a name="see-also"></a>Consulte também

- [Associações fornecidas pelo sistema](../../../../docs/framework/wcf/system-provided-bindings.md)
- [\<basicHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)
- [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)
- [\<wsDualHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)
- [\<mexHttpsBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpsbinding.md)
- [\<mexHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpbinding.md)
