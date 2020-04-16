---
title: Associações de interoperabilidade fornecidas pelo sistema oferece suporte para protocolos de serviços Web
ms.date: 03/30/2017
helpviewer_keywords:
- WS-protocols
- Web services protocols
- Windows Communication Foundation, Web service protocols
ms.assetid: 1f7fc4ff-30fe-4e46-adda-91caad3b06c6
ms.openlocfilehash: 25efda74d205a36332a801e91ddc508796f7df5d
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463983"
---
# <a name="web-services-protocols-supported-by-system-provided-interoperability-bindings"></a>Associações de interoperabilidade fornecidas pelo sistema oferece suporte para protocolos de serviços Web
O Windows Communication Foundation (WCF) foi construído para interoperar com serviços web que suportam um conjunto de especificações conhecidas como especificações de serviços Web. Para simplificar a configuração do serviço para práticas recomendadas de interoperabilidade, o <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType> <xref:System.ServiceModel.WSHttpBinding?displayProperty=nameWithType>WCF <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType>introduz três vinculações interoperáveis fornecidas pelo sistema: , e . Para interoperabilidade com as normas da Organização para o Avanço das Normas de Informação Estruturada (OASIS), o WCF inclui uma vinculação interoperável fornecida pelo sistema: <xref:System.ServiceModel.WS2007HttpBinding?displayProperty=nameWithType>. Para publicação de metadados, o WCF inclui duas vinculações interoperáveis fornecidas pelo sistema: [ \<mexHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpbinding.md) e [ \<mexHttpsBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpsbinding.md). Este tópico lista especificações que o suporte de vinculações interoperáveis fornecidas pelo sistema.  
  
## <a name="web-services-protocols-supported-by-basichttpbinding-wshttpbinding-ws2007httpbinding-and-wsdualhttpbinding-bindings"></a>Protocolos de serviços web suportados por basicHttpBinding, wsHttpBinding, ws2007HttpBinding e wsDualHttpBinding Bindings Bindings  
  
### <a name="all-bindings"></a>Todas as vinculações  
 As [ \<>vinculações básicashttpBinding, ](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) [ \<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)e [ \<ws2007HttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md) vinculação suportam os seguintes protocolos.  
  
> [!NOTE]
> Para obter informações sobre vinculações usadas para publicar metadados, consulte a seção "Vinculações de metadados fornecidas pelo sistema" mais tarde neste tópico.  
  
|Categoria|Protocolo|Especificação e Uso|  
|--------------|--------------|-----------------------------|  
|Transporte|HTTP 1.1|[HTTP 1.1](https://www.ietf.org/rfc/rfc2616.txt)<br /><br /> `BasicHttpBinding`, `WSHttpBinding`e `WS2007HttpBinding` usar os transportes HTTP e HTTPS.|  
|Mensagens|Mtom|[Mtom](https://www.w3.org/TR/soap12-mtom/)<br /><br /> `basicHttpBinding`, `wsHttpBinding`e `ws2007HttpBinding` apoiar o Mecanismo de Otimização da Transmissão de Mensagens (MTOM). Não usado por padrão. Para usar o MTOM, defina o atributo `messageEncoding` como `"Mtom"`.<br /><br /> Exemplo:<br /><br /> `<wsHttpBinding> <binding messageEncoding="Mtom"/> </wsHttpBinding>`|  
|Metadados|WSDL 1.1|[WSDL 1.1](https://www.w3.org/TR/wsdl/)<br /><br /> O WCF usa o WSDL (Web Services Description Language, linguagem de descrição de serviços web) para descrever serviços.|  
|Metadados|Política ws|[Política ws](https://www.w3.org/Submission/WS-Policy/)<br /><br /> O WCF usa a especificação WS-Policy juntamente com afirmações específicas de domínio para descrever requisitos e recursos de serviço.|  
|Metadados|Política WS 1.5|[Política WS 1.5](https://www.w3.org/TR/2007/CR-ws-policy-20070605/)<br /><br /> O WCF usa a especificação WS-Policy juntamente com afirmações específicas de domínio para descrever requisitos e recursos de serviço.|  
|Metadados|WS-PolicyAttachment|[WS-PolicyAttachment](http://specs.xmlsoap.org/ws/2004/09/policy/ws-policyattachment.pdf)<br /><br /> O WCF implementa o WS-PolicyAttachment para anexar expressões de diretiva em vários escopos no Web Services Description Language (WSDL).|  
|Metadados|WS-MetadataExchange|[WS-MetadataExchange](http://specs.xmlsoap.org/ws/2004/09/mex/WS-MetadataExchange.pdf)<br /><br /> O WCF implementa o WS-MetadataExchange para recuperar o Esquema XML, o WSDL e a Política WS.|  
  
### <a name="basichttpbinding"></a>basicHttpBinding  
  
|Categoria|Protocolo|Especificação e Uso|  
|--------------|--------------|-----------------------------|  
|Mensagens|SABÃO 1.1|[SABÃO 1.1](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/)<br /><br /> De acordo com o Perfil Básico `basicHttpBinding` 1.1, o elemento implementa o protocolo de mensagem SOAP 1.1.|  
|Segurança|Segurança de mensagem wss soap 1.0|[Segurança de mensagem wss soap 1.0](http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0.pdf)<br /><br /> De acordo com o Perfil `basicHttpBinding` básico de segurança, o elemento implementa a especificação SOAP Message Security 1.0 (Web Services Security 1.0) para nome de usuário/senha e segurança baseada em X.509.<br /><br /> `<basicHttpBinding> <binding name="Binding1"> <security mode="TransportWithMessageCredential &#124;                     "Message" .../> </binding> </basicHttpBinding>`|  
|Segurança|WSS SOAP Message Security UsernameToken Profile 1.0|[WSS SOAP Message Security UsernameToken Profile 1.0](http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0.pdf)<br /><br /> `<basicHttpBinding> <binding name="Binding1"> <security mode="TransportWithMessageCredential"> <transport clientCredentialType="Basic"/> </security> </basicHttpBinding>`|  
|Segurança|WSS SOAP Message Security X.509 Certificate Token Profile 1.0|[WSS SOAP Message Security X.509 Certificate Token Profile 1.0](http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-x509-token-profile-1.0.pdf)<br /><br /> `<basicHttpBinding>   <security mode="Message"> <message clientCredentialType="Certificate"/> </security> </basicHttpBinding>`|  
  
### <a name="wshttpbinding-ws2007httpbinding-and-wsdualhttpbinding"></a>wsHttpBinding, ws2007HttpBinding e wsDualHttpBinding  
  
|Categoria|Protocolo|Especificação e Uso|  
|--------------|--------------|-----------------------------|  
|Mensagens|SABÃO 1.2|[Instruções elementares](https://www.w3.org/TR/soap12-part0/)<br /><br /> [Estrutura de mensagens](https://www.w3.org/TR/2007/REC-soap12-part1-20070427/)<br /><br /> [Adjuntos (incluindo vinculação HTTP)](https://www.w3.org/TR/soap12-part2/)|  
|Mensagens|WS-Addressing 2005/08|[Serviços web abordando 1.0 - Núcleo](https://www.w3.org/TR/ws-addr-core/)<br /><br /> [Serviços Web abordando 1.0 - SOAP](https://www.w3.org/TR/ws-addr-soap/)<br /><br /> A `wsHttpBinding` `ws2007HttpBinding`, `wsDualHttpBinding` e implementar a recomendação WS-Addressing do World Wide Web Consortium (W3C) para permitir mensagens assíncronas, correlação de mensagens e mecanismos de endereçamento neutros em transporte.<br /><br /> O WCF não suporta criptografia de cabeçalhos de endereçamento do WS, embora isso seja permitido pelas especificações WS-*.|  
|Mensagens|WS-Addressing 1.0 - Metadados|[WS-Endereçando metadados 1.0](https://www.w3.org/2007/05/addressing/metadata/) O suporte para este protocolo é habilitado definindo a versão de diretiva no comportamento serviceMetadata - com a versão de policy definida como 1.2 (o padrão), a descrição wsdl é compatível com wsdl endereçamento do WS, com a versão de policy definida como 1.5, a descrição wsdl está em conformidade com metadados que endereçam ws.<br /><br /> O WCF não suporta criptografia de cabeçalhos de endereçamento do WS, embora isso seja permitido pelas especificações WS-*.|  
|Segurança|Segurança de mensagem wss soap 1.0|[Segurança de mensagem wss soap 1.0](http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0.pdf)<br /><br /> Use quando `securityMode` o atributo estiver definido como "wsSecurityOverHttp" (padrão) e os parâmetros forem configurados usando um `wsSecurity` elemento filho.<br /><br /> `<wsHttpBinding>   <binding name="myBinding">      <security mode="Message" .../>   </binding> </wsHttpBinding>`|  
|Segurança|WSS SOAP Message Security UsernameToken Profile 1.1|[WSS SOAP Message Security UsernameToken Profile 1.0](https://www.oasis-open.org/committees/download.php/16782/wss-v1.1-spec-os-UsernameTokenProfile.pdf)<br /><br /> Use quando `wsSecurity` o `authenticationMode` atributo do elemento estiver definido como "Nome de usuário".<br /><br /> `<wsHttpBinding>   <binding name="MyBinding">     <security mode="Message>       <message           clientCredentialType="UserName        negotiateServiceCredential="false"        establishSecurityContext="false"/>     </security> </binding> </wsHttpBinding>`|  
|Segurança|WSS SOAP Message Security X.509 Certificate Token Profile 1.1|[WSS SOAP Message Security X.509 Certificate Token Profile 1.1](https://www.oasis-open.org/committees/download.php/16785/wss-v1.1-spec-os-x509TokenProfile.pdf)<br /><br /> Use para proteção `wsSecurity` de `authenticationMode` mensagens quando o atributo do elemento estiver definido como "Nome de usuário", "Certificado" ou "Nenhum". Além disso, use isso para `wsSecurity` autenticação `authenticationMode` do cliente quando o atributo do elemento estiver definido como "Certificado".<br /><br /> `<wsHttpBinding>   <binding name="MyBinding">     <security mode="Message>       <message           clientCredentialType="Certificate"        negotiateServiceCredential="false"        establishSecurityContext="false"/>     </security>   </binding> </wsHttpBinding>`|  
|Segurança|WSS SOAP Message Security Kerberos Token Profile 1.1|[WSS SOAP Message Security Kerberos Token Profile 1.1](https://www.oasis-open.org/committees/download.php/16788/wss-v1.1-spec-os-KerberosTokenProfile.pdf)<br /><br /> Use para autenticação e `wsSecurity` proteção `authenticationMode` de mensagens quando o atributo do elemento estiver definido como "Windows".<br /><br /> `<wsHttpBinding>   <binding name="MyBinding">     <security mode="Message>       <message           clientCredentialType="Windows"        negotiateServiceCredential="false"        establishSecurityContext="false"/>     </security>   </binding> </wsHttpBinding>`|  
|Segurança|WS-SecureConversation|[WS-SecureConversation](http://specs.xmlsoap.org/ws/2005/02/sc/ws-secureconversation.pdf)<br /><br /> Use para fornecer uma `security/@mode` sessão segura quando o atributo estiver definido como "Mensagem" e o atributo `message/@establishSecurityContext` estiver definido como "verdadeiro" (padrão).|  
|Segurança|WS-Trust|[WS-Trust](http://specs.xmlsoap.org/ws/2005/02/trust/ws-trust.pdf)<br /><br /> Usado por WS-SecureConversation (veja acima).|  
|Mensagens confiáveis|WS-ReliableMessaging|[WS-ReliableMessaging](http://specs.xmlsoap.org/ws/2005/02/rm/ws-reliablemessaging.pdf)<br /><br /> Use quando a vinculação `reliableSession`estiver configurada para usar .<br /><br /> `<wsHttpBinding>  <binding name="myBinding">    <reliableSession/>   </binding> </wsHttpBinding>`|  
|Transactions|WS-AtomicTransaction|[WS-AtomicTransaction](http://specs.xmlsoap.org/ws/2004/10/wsat/wsat.pdf)<br /><br /> Uso para comunicação entre gerentes de transações. Clientes e serviços wcf sempre usam gerentes de transações locais.|  
|Transactions|Coordenação ws|[Coordenação ws](https://docs.microsoft.com/previous-versions/ms951231(v=msdn.10))<br /><br /> Use para fluir o `flowTransactions` contexto da transação quando o atributo estiver definido como "Permitido" ou "Obrigatório".<br /><br /> `<wsHttpBinding>   <binding transactionFlow="true"/> </wsHttpBinding>`|  
  
## <a name="wsfederationhttpbinding-and-ws2007federationhttpbinding"></a>wsFederationHttpBinding e ws2007FederationHttpBinding  
 Os [ \<elementos wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) e [ \<ws2007FederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/ws2007federationhttpbinding.md) são introduzidos para fornecer suporte a cenários federados, onde um terceiro emite um token usado para autenticar um cliente. Além dos protocolos utilizados por `wsHttpBinding`alavancas: `wsFederationHttpBinding`  
  
- `WS-Trust`para emissão de tokens.  
  
- WSS Security Assertions Markup Language (SAML) Token Profile 1.0 e 1.1 para o formato de token mais comumente emitido.  
  
 Exemplo:  
  
```xml  
<wsFederationHttpBinding>  
  <binding name="myBinding">  
     <security mode="Message">  
       <message issuedKeyType="Symmetric"
                issuedTokenType="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1">  
         <issuerMetadata address =
         'http://localhost/FederationSample/HomeRealmSTS/STS.svc/mex'/>  
       </message>  
     </security>  
  </binding>  
</wsFederationHttpBinding>  
```  
  
 Para obter mais informações, consulte [Federação](../../../../docs/framework/wcf/feature-details/federation.md) .  
  
## <a name="system-provided-metadata-bindings"></a>Vinculações de metadados fornecidas pelo sistema  
 As tabelas a seguir descrevem os protocolos suportados pelas vinculações de <xref:System.ServiceModel.Description.MetadataExchangeBindings?displayProperty=nameWithType> metadados interoperáveis fornecidas pelo sistema expostas pela classe.  
  
### <a name="mexhttpbinding"></a>mexHttpBinding  
 A vinculação [ \<mexHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpbinding.md) suporta os seguintes protocolos. Para obter mais informações sobre o uso dessa vinculação, consulte ['Publishing Metadata '](../../../../docs/framework/wcf/feature-details/publishing-metadata.md)  
  
|Categoria|Protocolo|Especificação e Uso|  
|--------------|--------------|-----------------------------|  
|Transporte|HTTP 1.1|[HTTP 1.1](https://www.ietf.org/rfc/rfc2616.txt)|  
|Mensagens|SABÃO 1.2|[Instruções elementares](https://www.w3.org/TR/soap12-part0/)<br /><br /> [Estrutura de mensagens](https://www.w3.org/TR/2007/REC-soap12-part1-20070427/)<br /><br /> [Adjuntos (incluindo vinculação HTTP)](https://www.w3.org/TR/soap12-part2/)|  
|Mensagens|WS-Addressing 2005/08|[Serviços web abordando 1.0 - Núcleo](https://www.w3.org/TR/ws-addr-core/)<br /><br /> [Serviços Web abordando 1.0 - SOAP](https://www.w3.org/TR/ws-addr-soap/)|  
|Metadados|WS-MetadataExchange|[WS-MetadataExchange](http://specs.xmlsoap.org/ws/2004/09/mex/WS-MetadataExchange.pdf)<br /><br /> O WCF implementa o WS-MetadataExchange para recuperar o Esquema XML, o WSDL e a Política WS.|  
  
### <a name="mexhttpsbinding"></a>mexHttpsBinding  
 mexHttpsBinding>suporta os seguintes protocolos. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpsbinding.md) Para obter mais informações sobre o uso dessa vinculação, consulte ['Publishing Metadata '](../../../../docs/framework/wcf/feature-details/publishing-metadata.md)  
  
|Categoria|Protocolo|Especificação e Uso|  
|--------------|--------------|-----------------------------|  
|Transporte|HTTP 1.1|[HTTP 1.1](https://www.ietf.org/rfc/rfc2616.txt)<br /><br /> A segurança do transporte está ativada.|  
|Mensagens|SABÃO 1.2|[Instruções elementares](https://www.w3.org/TR/soap12-part0/)<br /><br /> [Estrutura de mensagens](https://www.w3.org/TR/2007/REC-soap12-part1-20070427/)<br /><br /> [Adjuntos (incluindo vinculação HTTP)](https://www.w3.org/TR/soap12-part2/)|  
|Mensagens|WS-Addressing 2005/08|[Serviços web abordando 1.0 - Núcleo](https://www.w3.org/TR/ws-addr-core/)<br /><br /> [Serviços Web abordando 1.0 - SOAP](https://www.w3.org/TR/ws-addr-soap/)|  
|Metadados|WS-MetadataExchange|[WS-MetadataExchange](http://specs.xmlsoap.org/ws/2004/09/mex/WS-MetadataExchange.pdf)<br /><br /> O WCF implementa o WS-MetadataExchange para recuperar o Esquema XML, o WSDL e a Política WS.|  
  
## <a name="see-also"></a>Confira também

- [Associações fornecidas pelo sistema](../../../../docs/framework/wcf/system-provided-bindings.md)
- [\<>básicahttpBinding](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)
- [\<wshttpbinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)
- [\<wsDualhttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)
- [\<mexHttpsBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpsbinding.md)
- [\<mexhttpbinding>](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpbinding.md)
