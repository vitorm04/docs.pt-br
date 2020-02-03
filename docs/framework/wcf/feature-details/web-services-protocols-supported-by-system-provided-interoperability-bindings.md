---
title: Associações de interoperabilidade fornecidas pelo sistema oferece suporte para protocolos de serviços Web
ms.date: 03/30/2017
helpviewer_keywords:
- WS-protocols
- Web services protocols
- Windows Communication Foundation, Web service protocols
ms.assetid: 1f7fc4ff-30fe-4e46-adda-91caad3b06c6
ms.openlocfilehash: 80fa0e501f425bd5b917059e90f2811f075db651
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746901"
---
# <a name="web-services-protocols-supported-by-system-provided-interoperability-bindings"></a>Associações de interoperabilidade fornecidas pelo sistema oferece suporte para protocolos de serviços Web
O Windows Communication Foundation (WCF) foi criado para interoperar com serviços Web que dão suporte a um conjunto de especificações conhecidas como especificações de serviços da Web. Para simplificar a configuração de serviço para práticas recomendadas de interoperabilidade, o WCF apresenta três associações interoperáveis fornecidas pelo sistema: <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType>, <xref:System.ServiceModel.WSHttpBinding?displayProperty=nameWithType>e <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType>. Para interoperabilidade com a organização para o avanço de padrões de OASIS (padrões de informações estruturadas), o WCF inclui uma associação do sistema interoperável: <xref:System.ServiceModel.WS2007HttpBinding?displayProperty=nameWithType>. Para a publicação de metadados, o WCF inclui duas associações interoperáveis fornecidas pelo sistema: [\<mexHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpbinding.md) e [\<> de mexHttpsBinding](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpsbinding.md). Este tópico lista as especificações com suporte de associações interoperáveis fornecidas pelo sistema.  
  
## <a name="web-services-protocols-supported-by-basichttpbinding-wshttpbinding-ws2007httpbinding-and-wsdualhttpbinding-bindings"></a>Protocolos de serviços Web com suporte pelas associações basicHttpBinding, wsHttpBinding, ws2007HttpBinding e wsDualHttpBinding  
  
### <a name="all-bindings"></a>Todas as associações  
 As associações [\<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md), [\<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)e [\<ws2007HttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md) dão suporte aos seguintes protocolos.  
  
> [!NOTE]
> Para obter informações sobre associações usadas para publicar metadados, consulte a seção "associações de metadados fornecidas pelo sistema" mais adiante neste tópico.  
  
|Categoria|Protocolo|Especificação e uso|  
|--------------|--------------|-----------------------------|  
|Transporte|HTTP 1.1|[HTTP 1,1](https://www.ietf.org/rfc/rfc2616.txt)<br /><br /> `BasicHttpBinding`, `WSHttpBinding`e `WS2007HttpBinding` usar os transportes HTTP e HTTPS.|  
|Mensagens|MTOM|[MTOM](https://www.w3.org/TR/soap12-mtom/)<br /><br /> `basicHttpBinding`, `wsHttpBinding`e `ws2007HttpBinding` oferecem suporte ao mecanismo de otimização de transmissão de mensagens (MTOM). Não usado por padrão. Para usar o MTOM, defina o atributo `messageEncoding` como `"Mtom"`.<br /><br /> Exemplo:<br /><br /> `<wsHttpBinding> <binding messageEncoding="Mtom"/> </wsHttpBinding>`|  
|Metadados|WSDL 1,1|[WSDL 1,1](https://www.w3.org/TR/wsdl/)<br /><br /> O WCF usa WSDL (Web Services Description Language) para descrever os serviços.|  
|Metadados|WS-Policy|[WS-Policy](https://www.w3.org/Submission/WS-Policy/)<br /><br /> O WCF usa a especificação WS-Policy juntamente com declarações específicas de domínio para descrever os requisitos de serviço e os recursos.|  
|Metadados|WS-Policy 1,5|[WS-Policy 1,5](https://www.w3.org/TR/2007/CR-ws-policy-20070605/)<br /><br /> O WCF usa a especificação WS-Policy juntamente com declarações específicas de domínio para descrever os requisitos de serviço e os recursos.|  
|Metadados|WS-PolicyAttachment|[WS-PolicyAttachment](http://specs.xmlsoap.org/ws/2004/09/policy/ws-policyattachment.pdf)<br /><br /> O WCF implementa o WS-PolicyAttachment para anexar expressões de política em vários escopos no WSDL (Web Services Description Language).|  
|Metadados|WS-MetadataExchange|[WS-MetadataExchange](http://specs.xmlsoap.org/ws/2004/09/mex/WS-MetadataExchange.pdf)<br /><br /> O WCF implementa o WS-MetadataExchange para recuperar o esquema XML, o WSDL e o WS-Policy.|  
  
### <a name="basichttpbinding"></a>basicHttpBinding  
  
|Categoria|Protocolo|Especificação e uso|  
|--------------|--------------|-----------------------------|  
|Mensagens|SOAP 1,1|[SOAP 1,1](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/)<br /><br /> De acordo com o perfil básico 1,1, o elemento `basicHttpBinding` implementa o protocolo de mensagem SOAP 1,1.|  
|Segurança|Segurança de mensagem SOAP do WSS 1,0|[Segurança de mensagem SOAP do WSS 1,0](http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0.pdf)<br /><br /> De acordo com o perfil de segurança básico, o elemento `basicHttpBinding` implementa a especificação de segurança de mensagem SOAP do especificação Web Services Security (WSS) 1,0 para o nome de usuário/senha e a segurança baseada em X. 509.<br /><br /> `<basicHttpBinding> <binding name="Binding1"> <security mode="TransportWithMessageCredential &#124;                     "Message" .../> </binding> </basicHttpBinding>`|  
|Segurança|Perfil do UsernameToken de segurança de mensagem SOAP do WSS 1,0|[Perfil do UsernameToken de segurança de mensagem SOAP do WSS 1,0](http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0.pdf)<br /><br /> `<basicHttpBinding> <binding name="Binding1"> <security mode="TransportWithMessageCredential"> <transport clientCredentialType="Basic"/> </security> </basicHttpBinding>`|  
|Segurança|Segurança de mensagem SOAP do WSS X. 509 perfil de token de certificado 1,0|[Segurança de mensagem SOAP do WSS X. 509 perfil de token de certificado 1,0](http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-x509-token-profile-1.0.pdf)<br /><br /> `<basicHttpBinding>   <security mode="Message"> <message clientCredentialType="Certificate"/> </security> </basicHttpBinding>`|  
  
### <a name="wshttpbinding-ws2007httpbinding-and-wsdualhttpbinding"></a>wsHttpBinding, ws2007HttpBinding e wsDualHttpBinding  
  
|Categoria|Protocolo|Especificação e uso|  
|--------------|--------------|-----------------------------|  
|Mensagens|SOAP 1,2|[Instruções elementares](https://www.w3.org/TR/soap12-part0/)<br /><br /> [Estrutura de mensagens](https://www.w3.org/TR/2007/REC-soap12-part1-20070427/)<br /><br /> [Adjuncts (incluindo associação HTTP)](https://www.w3.org/TR/soap12-part2/)|  
|Mensagens|WS-Addressing 2005/08|[Endereçamento de serviços da Web 1,0-Core](https://www.w3.org/TR/ws-addr-core/)<br /><br /> [Endereçamento de serviços da Web 1,0-SOAP](https://www.w3.org/TR/ws-addr-soap/)<br /><br /> O `wsHttpBinding`, `ws2007HttpBinding`e `wsDualHttpBinding` implementam a recomendação WS-Addressing do World Wide Web Consortium (W3C) para habilitar o sistema de mensagens assíncronas, a correlação de mensagens e os mecanismos de endereçamento de transporte neutro.<br /><br /> O WCF não dá suporte à criptografia de cabeçalhos de WS-Addressing, embora isso seja permitido pelas especificações WS-*.|  
|Mensagens|WS-Addressing 1,0-Metadata|[Metadados 1,0 do WS-Addressing](https://www.w3.org/2007/05/addressing/metadata/) O suporte para esse protocolo é habilitado pela definição da versão da política no comportamento de metadados-com PolicyVersion definido como 1,2 (o padrão), a descrição do WSDL é compatível com o WSDL do WS-Addressing, com PolicyVersion definido como 1,5, a descrição do WSDL é compatível com os metadados do WS-Addressing.<br /><br /> O WCF não dá suporte à criptografia de cabeçalhos de WS-Addressing, embora isso seja permitido pelas especificações WS-*.|  
|Segurança|Segurança de mensagem SOAP do WSS 1,0|[Segurança de mensagem SOAP do WSS 1,0](http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0.pdf)<br /><br /> Use quando o atributo `securityMode` estiver definido como "wsSecurityOverHttp" (padrão) e os parâmetros forem configurados usando um elemento filho `wsSecurity`.<br /><br /> `<wsHttpBinding>   <binding name="myBinding">      <security mode="Message" .../>   </binding> </wsHttpBinding>`|  
|Segurança|Perfil do UsernameToken de segurança de mensagem SOAP do WSS 1,1|[Perfil do UsernameToken de segurança de mensagem SOAP do WSS 1,0](https://www.oasis-open.org/committees/download.php/16782/wss-v1.1-spec-os-UsernameTokenProfile.pdf)<br /><br /> Use quando o atributo `authenticationMode` do elemento de `wsSecurity` estiver definido como "username".<br /><br /> `<wsHttpBinding>   <binding name="MyBinding">     <security mode="Message>       <message           clientCredentialType="UserName        negotiateServiceCredential="false"        establishSecurityContext="false"/>     </security> </binding> </wsHttpBinding>`|  
|Segurança|Segurança de mensagem SOAP do WSS X. 509 perfil de token de certificado 1,1|[Segurança de mensagem SOAP do WSS X. 509 perfil de token de certificado 1,1](https://www.oasis-open.org/committees/download.php/16785/wss-v1.1-spec-os-x509TokenProfile.pdf)<br /><br /> Use para proteção de mensagem quando o atributo `authenticationMode` do elemento de `wsSecurity` estiver definido como "username", "Certificate" ou "None". Além disso, use isso para autenticação de cliente quando o atributo `authenticationMode` do elemento `wsSecurity` estiver definido como "certificado".<br /><br /> `<wsHttpBinding>   <binding name="MyBinding">     <security mode="Message>       <message           clientCredentialType="Certificate"        negotiateServiceCredential="false"        establishSecurityContext="false"/>     </security>   </binding> </wsHttpBinding>`|  
|Segurança|Perfil de token Kerberos de segurança de mensagem SOAP do WSS 1,1|[Perfil de token Kerberos de segurança de mensagem SOAP do WSS 1,1](https://www.oasis-open.org/committees/download.php/16788/wss-v1.1-spec-os-KerberosTokenProfile.pdf)<br /><br /> Use para autenticação e proteção de mensagem quando o atributo `authenticationMode` do elemento de `wsSecurity` estiver definido como "Windows".<br /><br /> `<wsHttpBinding>   <binding name="MyBinding">     <security mode="Message>       <message           clientCredentialType="Windows"        negotiateServiceCredential="false"        establishSecurityContext="false"/>     </security>   </binding> </wsHttpBinding>`|  
|Segurança|WS-SecureConversation|[WS-SecureConversation](http://specs.xmlsoap.org/ws/2005/02/sc/ws-secureconversation.pdf)<br /><br /> Use para fornecer uma sessão segura quando o atributo `security/@mode` for definido como "Message" e o atributo `message/@establishSecurityContext` estiver definido como "true" (padrão).|  
|Segurança|WS-Trust|[WS-Trust](http://specs.xmlsoap.org/ws/2005/02/trust/ws-trust.pdf)<br /><br /> Usado pelo WS-SecureConversation (veja acima).|  
|Mensagens confiáveis|WS-ReliableMessaging|[WS-ReliableMessaging](http://specs.xmlsoap.org/ws/2005/02/rm/ws-reliablemessaging.pdf)<br /><br /> Use quando a associação estiver configurada para usar `reliableSession`.<br /><br /> `<wsHttpBinding>  <binding name="myBinding">    <reliableSession/>   </binding> </wsHttpBinding>`|  
|Transações|WS-AtomicTransaction|[WS-AtomicTransaction](http://specs.xmlsoap.org/ws/2004/10/wsat/wsat.pdf)<br /><br /> Use para comunicação entre gerenciadores de transações. Os clientes e serviços WCF sempre usam gerenciadores de transações locais.|  
|Transações|WS-Coordination|[WS-Coordination](https://docs.microsoft.com/previous-versions/ms951231(v=msdn.10))<br /><br /> Use para fluir o contexto da transação quando o atributo `flowTransactions` estiver definido como "Allowed" ou "required".<br /><br /> `<wsHttpBinding>   <binding transactionFlow="true"/> </wsHttpBinding>`|  
  
## <a name="wsfederationhttpbinding-and-ws2007federationhttpbinding"></a>wsFederationHttpBinding e ws2007FederationHttpBinding  
 Os elementos [\<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) e [\<> do ws2007FederationHttpBinding](../../../../docs/framework/configure-apps/file-schema/wcf/ws2007federationhttpbinding.md) são introduzidos para oferecer suporte a cenários federados, em que um terceiro emite um token usado para autenticar um cliente. Além dos protocolos usados pelo `wsHttpBinding`, o `wsFederationHttpBinding` aproveita:  
  
- `WS-Trust` para emissão de tokens.  
  
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
 As tabelas a seguir descrevem os protocolos compatíveis com as associações de metadados interoperáveis fornecidas pelo sistema expostas pela classe <xref:System.ServiceModel.Description.MetadataExchangeBindings?displayProperty=nameWithType>.  
  
### <a name="mexhttpbinding"></a>mexHttpBinding  
 A associação de [>\<mexHttpBinding](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpbinding.md) dá suporte aos seguintes protocolos. Para obter mais informações sobre como usar essa associação, consulte [publicando metadados](../../../../docs/framework/wcf/feature-details/publishing-metadata.md).  
  
|Categoria|Protocolo|Especificação e uso|  
|--------------|--------------|-----------------------------|  
|Transporte|HTTP 1.1|[HTTP 1,1](https://www.ietf.org/rfc/rfc2616.txt)|  
|Mensagens|SOAP 1,2|[Instruções elementares](https://www.w3.org/TR/soap12-part0/)<br /><br /> [Estrutura de mensagens](https://www.w3.org/TR/2007/REC-soap12-part1-20070427/)<br /><br /> [Adjuncts (incluindo associação HTTP)](https://www.w3.org/TR/soap12-part2/)|  
|Mensagens|WS-Addressing 2005/08|[Endereçamento de serviços da Web 1,0-Core](https://www.w3.org/TR/ws-addr-core/)<br /><br /> [Endereçamento de serviços da Web 1,0-SOAP](https://www.w3.org/TR/ws-addr-soap/)|  
|Metadados|WS-MetadataExchange|[WS-MetadataExchange](http://specs.xmlsoap.org/ws/2004/09/mex/WS-MetadataExchange.pdf)<br /><br /> O WCF implementa o WS-MetadataExchange para recuperar o esquema XML, o WSDL e o WS-Policy.|  
  
### <a name="mexhttpsbinding"></a>mexHttpsBinding  
 [\<mexHttpsBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpsbinding.md) dá suporte aos seguintes protocolos. Para obter mais informações sobre como usar essa associação, consulte [publicando metadados](../../../../docs/framework/wcf/feature-details/publishing-metadata.md).  
  
|Categoria|Protocolo|Especificação e uso|  
|--------------|--------------|-----------------------------|  
|Transporte|HTTP 1.1|[HTTP 1,1](https://www.ietf.org/rfc/rfc2616.txt)<br /><br /> A segurança de transporte está habilitada.|  
|Mensagens|SOAP 1,2|[Instruções elementares](https://www.w3.org/TR/soap12-part0/)<br /><br /> [Estrutura de mensagens](https://www.w3.org/TR/2007/REC-soap12-part1-20070427/)<br /><br /> [Adjuncts (incluindo associação HTTP)](https://www.w3.org/TR/soap12-part2/)|  
|Mensagens|WS-Addressing 2005/08|[Endereçamento de serviços da Web 1,0-Core](https://www.w3.org/TR/ws-addr-core/)<br /><br /> [Endereçamento de serviços da Web 1,0-SOAP](https://www.w3.org/TR/ws-addr-soap/)|  
|Metadados|WS-MetadataExchange|[WS-MetadataExchange](http://specs.xmlsoap.org/ws/2004/09/mex/WS-MetadataExchange.pdf)<br /><br /> O WCF implementa o WS-MetadataExchange para recuperar o esquema XML, o WSDL e o WS-Policy.|  
  
## <a name="see-also"></a>Consulte também

- [Associações fornecidas pelo sistema](../../../../docs/framework/wcf/system-provided-bindings.md)
- [\<basicHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)
- [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)
- [\<wsDualHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)
- [\<mexHttpsBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpsbinding.md)
- [\<mexHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpbinding.md)
