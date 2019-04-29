---
title: Associações de interoperabilidade fornecidas pelo sistema oferece suporte para protocolos de serviços Web
ms.date: 03/30/2017
helpviewer_keywords:
- WS-protocols
- Web services protocols
- Windows Communication Foundation, Web service protocols
ms.assetid: 1f7fc4ff-30fe-4e46-adda-91caad3b06c6
ms.openlocfilehash: caf9a66e8c42fb80955539aa9d3eb32179309004
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61929682"
---
# <a name="web-services-protocols-supported-by-system-provided-interoperability-bindings"></a>Associações de interoperabilidade fornecidas pelo sistema oferece suporte para protocolos de serviços Web
Windows Communication Foundation (WCF) foi criada para interoperar com serviços da Web que dão suporte a um conjunto de especificações, conhecido como especificações de serviços da Web. Para simplificar a configuração de serviço para as práticas recomendadas de interoperabilidade, o WCF apresenta três associações fornecidas pelo sistema interoperáveis: <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType>, <xref:System.ServiceModel.WSHttpBinding?displayProperty=nameWithType>, e <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType>. Para interoperabilidade com a organização para os padrões de avanço dos Structured Information Standards (OASIS), o WCF inclui uma associação fornecida pelo sistema interoperável: <xref:System.ServiceModel.WS2007HttpBinding?displayProperty=nameWithType>. Para a publicação de metadados, o WCF inclui duas associações fornecidas pelo sistema interoperáveis: [ \<mexHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpbinding.md) e [ \<mexHttpsBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpsbinding.md). Este tópico lista as especificações que dão suporte a associações de interoperabilidade fornecidas pelo sistema.  
  
## <a name="web-services-protocols-supported-by-basichttpbinding-wshttpbinding-ws2007httpbinding-and-wsdualhttpbinding-bindings"></a>Web Services protocolos com suporte pelas associações basicHttpBinding, wsHttpBinding, ws2007HttpBinding e wsDualHttpBinding  
  
### <a name="all-bindings"></a>Todas as associações  
 O [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md), [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), e [ \<ws2007HttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md) suporte a associações de os seguintes protocolos.  
  
> [!NOTE]
>  Para obter informações sobre associações usado para publicar metadados, consulte a seção "Ligações de metadados System-Provided" mais adiante neste tópico.  
  
|Categoria|Protocolo|Especificação e uso|  
|--------------|--------------|-----------------------------|  
|Transporte|HTTP 1.1|[HTTP 1.1](https://go.microsoft.com/fwlink/?LinkId=84048)<br /><br /> `BasicHttpBinding`, `WSHttpBinding`, e `WS2007HttpBinding` usam os transportes HTTP e HTTPS.|  
|Mensagens|MTOM|[MTOM](https://go.microsoft.com/fwlink/?LinkId=95326)<br /><br /> `basicHttpBinding`, `wsHttpBinding`, e `ws2007HttpBinding` suporte MTOM Message Transmission Optimization Mechanism (). Não é usado por padrão. Para usar MTOM, defina as `messageEncoding` atributo `"Mtom"`.<br /><br /> Exemplo:<br /><br /> `<wsHttpBinding> <binding messageEncoding="Mtom"/> </wsHttpBinding>`|  
|Metadados|WSDL 1.1|[WSDL 1.1](https://go.microsoft.com/fwlink/?LinkId=94859)<br /><br /> Para descrever serviços, o WCF usa descrição linguagem WSDL (Web Services).|  
|Metadados|WS-Policy|[WS-Policy](https://go.microsoft.com/fwlink/?LinkId=94864)<br /><br /> WCF usa a especificação de WS-Policy junto com as declarações específicas de domínio para descrever os recursos e requisitos de serviço.|  
|Metadados|WS-Policy 1.5|[WS-Policy 1.5](https://go.microsoft.com/fwlink/?LinkId=95327)<br /><br /> WCF usa a especificação de WS-Policy junto com as declarações específicas de domínio para descrever os recursos e requisitos de serviço.|  
|Metadados|WS-PolicyAttachment|[WS-PolicyAttachment](https://go.microsoft.com/fwlink/?LinkId=95328)<br /><br /> O WCF implementa um mecanismo WS-PolicyAttachment para anexar as expressões de diretriz em vários escopos na descrição de linguagem WSDL (Web Services).|  
|Metadados|WS-MetadataExchange|[WS-MetadataExchange](https://go.microsoft.com/fwlink/?LinkId=94868)<br /><br /> O WCF implementa o WS-MetadataExchange para recuperar o esquema XML, WSDL e WS-Policy.|  
  
### <a name="basichttpbinding"></a>basicHttpBinding  
  
|Categoria|Protocolo|Especificação e uso|  
|--------------|--------------|-----------------------------|  
|Mensagens|SOAP 1.1|[SOAP 1.1](https://go.microsoft.com/fwlink/?LinkId=90520)<br /><br /> De acordo com a Basic Profile 1.1, o `basicHttpBinding` elemento implementa o protocolo SOAP 1.1.|  
|Segurança|Segurança de mensagem SOAP do WSS 1.0|[Segurança de mensagem SOAP do WSS 1.0](https://go.microsoft.com/fwlink/?LinkId=94684)<br /><br /> Acordo com o Basic Security Profile o `basicHttpBinding` elemento implementa a especificação de segurança de mensagem SOAP de Web Services Security (WSS) 1.0 para o nome de usuário/senha e segurança baseada em x. 509.<br /><br /> `<basicHttpBinding> <binding name="Binding1"> <security mode="TransportWithMessageCredential &#124;                     "Message" .../> </binding> </basicHttpBinding>`|  
|Segurança|Segurança de mensagem do WSS SOAP UsernameToken Profile 1.0|[Segurança de mensagem do WSS SOAP UsernameToken Profile 1.0](https://go.microsoft.com/fwlink/?LinkId=95334)<br /><br /> `<basicHttpBinding> <binding name="Binding1"> <security mode="TransportWithMessageCredential"> <transport clientCredentialType="Basic"/> </security> </basicHttpBinding>`|  
|Segurança|O WSS SOAP mensagem segurança x. 509 certificado Token Profile 1.0|[O WSS SOAP mensagem segurança x. 509 certificado Token Profile 1.0](https://go.microsoft.com/fwlink/?LinkId=95335)<br /><br /> `<basicHttpBinding>   <security mode="Message"> <message clientCredentialType="Certificate"/> </security> </basicHttpBinding>`|  
  
### <a name="wshttpbinding-ws2007httpbinding-and-wsdualhttpbinding"></a>wsHttpBinding, ws2007HttpBinding e wsDualHttpBinding  
  
|Categoria|Protocolo|Especificação e uso|  
|--------------|--------------|-----------------------------|  
|Mensagens|SOAP 1.2|[Primer](https://go.microsoft.com/fwlink/?LinkId=48282)<br /><br /> [Estrutura de mensagens](https://go.microsoft.com/fwlink/?LinkId=94664)<br /><br /> [Adjuncts (incluindo associação HTTP)](https://go.microsoft.com/fwlink/?LinkId=95329)|  
|Mensagens|2005 do WS-Addressing/08|[1.0 - Core endereçamento de serviços da Web](https://go.microsoft.com/fwlink/?LinkId=90574)<br /><br /> [1.0 - SOAP endereçamento de serviços da Web](https://go.microsoft.com/fwlink/?LinkId=95330)<br /><br /> O `wsHttpBinding`, `ws2007HttpBinding`, e `wsDualHttpBinding` implementar a recomendação do World Wide Web Consortium (W3C) WS-Addressing para habilitar o sistema de mensagens assíncrono, correlação de mensagem e mecanismos de endereçamento de transporte neutro.<br /><br /> O WCF não oferece suporte a criptografia de cabeçalhos de WS-Addressing Embora isso é permitido por WS-* especificações.|  
|Mensagens|WS-Addressing 1.0 - metadados|[WS-Addressing 1.0 metadados](https://www.w3.org/2007/05/addressing/metadata) suporte para esse protocolo é habilitado definindo a versão da diretiva de comportamento de ServiceMetadata - com policyversion="1.0 definido como 1.2 (o padrão), a descrição de wsdl está em conformidade com wsdl WS-Addressing, com policyversion="1.0 definido para 1.5, a descrição de wsdl está em conformidade com os metadados de ws-addressing.<br /><br /> O WCF não oferece suporte a criptografia de cabeçalhos de WS-Addressing Embora isso é permitido por WS-* especificações.|  
|Segurança|Segurança de mensagem SOAP do WSS 1.0|[Segurança de mensagem SOAP do WSS 1.0](https://go.microsoft.com/fwlink/?LinkId=94684)<br /><br /> Usado quando o `securityMode` atributo é definido como "wsSecurityOverHttp" (padrão) e os parâmetros são configurados usando um `wsSecurity` elemento filho.<br /><br /> `<wsHttpBinding>   <binding name="myBinding">      <security mode="Message" .../>   </binding> </wsHttpBinding>`|  
|Segurança|Segurança de mensagem do WSS SOAP UsernameToken Profile 1.1|[Segurança de mensagem do WSS SOAP UsernameToken Profile 1.0](https://go.microsoft.com/fwlink/?LinkId=95331)<br /><br /> Usado quando o `wsSecurity` do elemento `authenticationMode` atributo é definido como "Username".<br /><br /> `<wsHttpBinding>   <binding name="MyBinding">     <security mode="Message>       <message           clientCredentialType="UserName        negotiateServiceCredential="false"        establishSecurityContext="false"/>     </security> </binding> </wsHttpBinding>`|  
|Segurança|O WSS SOAP mensagem segurança x. 509 certificado Token Profile 1.1|[O WSS SOAP mensagem segurança x. 509 certificado Token Profile 1.1](https://go.microsoft.com/fwlink/?LinkId=95332)<br /><br /> Use para proteção de mensagem quando o `wsSecurity` do elemento `authenticationMode` atributo é definido como "Username", "Certificado" ou "None". Além disso, usar isso para autenticação de cliente quando o `wsSecurity` do elemento `authenticationMode` atributo é definido como "Certificado".<br /><br /> `<wsHttpBinding>   <binding name="MyBinding">     <security mode="Message>       <message           clientCredentialType="Certificate"        negotiateServiceCredential="false"        establishSecurityContext="false"/>     </security>   </binding> </wsHttpBinding>`|  
|Segurança|Perfil de Token Kerberos de segurança mensagem WSS SOAP 1.1|[Perfil de Token Kerberos de segurança mensagem WSS SOAP 1.1](https://go.microsoft.com/fwlink/?LinkId=95333)<br /><br /> Use para a proteção de autenticação e a mensagem quando o `wsSecurity` do elemento `authenticationMode` atributo é definido como "Windows".<br /><br /> `<wsHttpBinding>   <binding name="MyBinding">     <security mode="Message>       <message           clientCredentialType="Windows"        negotiateServiceCredential="false"        establishSecurityContext="false"/>     </security>   </binding> </wsHttpBinding>`|  
|Segurança|WS-SecureConversation|[WS-SecureConversation](https://go.microsoft.com/fwlink/?LinkId=95317)<br /><br /> Use para fornecer uma sessão segura quando o `security/@mode` atributo é definido como "Message" e o `message/@establishSecurityContext` atributo é definido como "true" (padrão).|  
|Segurança|WS-Trust|[WS-Trust](https://go.microsoft.com/fwlink/?LinkId=95318)<br /><br /> Usado por WS-SecureConversation (veja acima).|  
|Mensagens confiáveis|WS-ReliableMessaging|[WS-ReliableMessaging](https://go.microsoft.com/fwlink/?LinkId=95322)<br /><br /> Use quando a associação está configurada para usar `reliableSession`.<br /><br /> `<wsHttpBinding>  <binding name="myBinding">    <reliableSession/>   </binding> </wsHttpBinding>`|  
|Transações|WS-AtomicTransaction|[WS-AtomicTransaction](https://go.microsoft.com/fwlink/?LinkId=95323)<br /><br /> Use para comunicação entre os gerenciadores de transações. Serviços e clientes do WCF sempre usam gerenciadores de transações locais.|  
|Transações|WS-Coordination|[WS-Coordination](https://go.microsoft.com/fwlink/?LinkId=95324)<br /><br /> Usar o fluxo do contexto de transação quando o `flowTransactions` atributo é definido como "Autorizado" ou "Required".<br /><br /> `<wsHttpBinding>   <binding transactionFlow="true"/> </wsHttpBinding>`|  
  
## <a name="wsfederationhttpbinding-and-ws2007federationhttpbinding"></a>wsFederationHttpBinding e ws2007FederationHttpBinding  
 O [ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) e [ \<ws2007FederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/ws2007federationhttpbinding.md) elementos são apresentados para fornecer suporte para cenários federados, onde um terceiro terceiros emite um token usado para autenticar um cliente. Além dos protocolos usados pelo `wsHttpBinding`, `wsFederationHttpBinding` utiliza:  
  
- `WS-Trust` para emissão de token.  
  
- WSS asserções marcação linguagem SAML (Security) Token Profile 1.0 e 1.1 para a maioria comumente emitido o formato do token.  
  
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
  
 Para obter mais informações, consulte [federação](../../../../docs/framework/wcf/feature-details/federation.md) .  
  
## <a name="system-provided-metadata-bindings"></a>Associações de metadados fornecidos pelo sistema  
 As tabelas a seguir descrevem os protocolos suportados pelas associações fornecidas pelo sistema metadados interoperável expostas pelo <xref:System.ServiceModel.Description.MetadataExchangeBindings?displayProperty=nameWithType> classe.  
  
### <a name="mexhttpbinding"></a>mexHttpBinding  
 O [ \<mexHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpbinding.md) associação dá suporte aos protocolos a seguir. Para obter mais informações sobre como usar essa associação, consulte [metadados de publicação](../../../../docs/framework/wcf/feature-details/publishing-metadata.md).  
  
|Categoria|Protocolo|Especificação e uso|  
|--------------|--------------|-----------------------------|  
|Transporte|HTTP 1.1|[HTTP 1.1](https://go.microsoft.com/fwlink/?LinkId=84048)|  
|Mensagens|SOAP 1.2|[Primer](https://go.microsoft.com/fwlink/?LinkId=48282)<br /><br /> [Estrutura de mensagens](https://go.microsoft.com/fwlink/?LinkId=94664)<br /><br /> [Adjuncts (incluindo associação HTTP)](https://go.microsoft.com/fwlink/?LinkId=95329)|  
|Mensagens|2005 do WS-Addressing/08|[1.0 - Core endereçamento de serviços da Web](https://go.microsoft.com/fwlink/?LinkId=90574)<br /><br /> [1.0 - SOAP endereçamento de serviços da Web](https://go.microsoft.com/fwlink/?LinkId=95330)|  
|Metadados|WS-MetadataExchange|[WS-MetadataExchange](https://go.microsoft.com/fwlink/?LinkId=94868)<br /><br /> O WCF implementa o WS-MetadataExchange para recuperar o esquema XML, WSDL e WS-Policy.|  
  
### <a name="mexhttpsbinding"></a>mexHttpsBinding  
 [\<mexHttpsBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpsbinding.md) dá suporte a protocolos a seguir. Para obter mais informações sobre como usar essa associação, consulte [metadados de publicação](../../../../docs/framework/wcf/feature-details/publishing-metadata.md).  
  
|Categoria|Protocolo|Especificação e uso|  
|--------------|--------------|-----------------------------|  
|Transporte|HTTP 1.1|[HTTP 1.1](https://go.microsoft.com/fwlink/?LinkId=84048)<br /><br /> Segurança de transporte está habilitada.|  
|Mensagens|SOAP 1.2|[Primer](https://go.microsoft.com/fwlink/?LinkId=48282)<br /><br /> [Estrutura de mensagens](https://go.microsoft.com/fwlink/?LinkId=94664)<br /><br /> [Adjuncts (incluindo associação HTTP)](https://go.microsoft.com/fwlink/?LinkId=95329)|  
|Mensagens|2005 do WS-Addressing/08|[1.0 - Core endereçamento de serviços da Web](https://go.microsoft.com/fwlink/?LinkId=90574)<br /><br /> [1.0 - SOAP endereçamento de serviços da Web](https://go.microsoft.com/fwlink/?LinkId=95330)|  
|Metadados|WS-MetadataExchange|[WS-MetadataExchange](https://go.microsoft.com/fwlink/?LinkId=94868)<br /><br /> O WCF implementa o WS-MetadataExchange para recuperar o esquema XML, WSDL e WS-Policy.|  
  
## <a name="see-also"></a>Consulte também

- [Associações fornecidas pelo sistema](../../../../docs/framework/wcf/system-provided-bindings.md)
- [\<basicHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)
- [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)
- [\<wsDualHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)
- [\<mexHttpsBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpsbinding.md)
- [\<mexHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpbinding.md)
