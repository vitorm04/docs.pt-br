---
title: Associações de interoperabilidade fornecidas pelo sistema oferece suporte para protocolos de serviços Web
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WS-protocols
- Web services protocols
- Windows Communication Foundation, Web service protocols
ms.assetid: 1f7fc4ff-30fe-4e46-adda-91caad3b06c6
caps.latest.revision: 39
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 754915d5ba596b5121c47be3533ee679b4f9594b
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2018
---
# <a name="web-services-protocols-supported-by-system-provided-interoperability-bindings"></a>Associações de interoperabilidade fornecidas pelo sistema oferece suporte para protocolos de serviços Web
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] é criado para interoperar com serviços da Web que oferecem suporte a um conjunto de especificações conhecido como especificações de serviços da Web. Para simplificar a configuração de serviço para práticas recomendadas de interoperabilidade, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] apresenta três associações fornecidas pelo sistema interoperáveis: <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType>, <xref:System.ServiceModel.WSHttpBinding?displayProperty=nameWithType>, e <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType>. Para interoperabilidade com a organização para os padrões de avanço de Structured Information Standards (OASIS), [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] inclui uma associação fornecida pelo sistema interoperável: <xref:System.ServiceModel.WS2007HttpBinding?displayProperty=nameWithType>. Para publicação de metadados, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] inclui duas associações fornecidas pelo sistema interoperáveis: [ \<mexHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpbinding.md) e [ \<mexHttpsBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpsbinding.md). Este tópico lista as especificações que dão suporte a associações de interoperabilidade fornecidas pelo sistema.  
  
## <a name="web-services-protocols-supported-by-basichttpbinding-wshttpbinding-ws2007httpbinding-and-wsdualhttpbinding-bindings"></a>Web Services dá suporte para protocolos associações basicHttpBinding, wsHttpBinding, ws2007HttpBinding e wsDualHttpBinding  
  
### <a name="all-bindings"></a>Todas as associações  
 O [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md), [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), e [ \<ws2007HttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md) suporte a associações de protocolos a seguir.  
  
> [!NOTE]
>  Para obter informações sobre associações usado para publicar metadados, consulte a seção "Associações de metadados System-Provided" mais adiante neste tópico.  
  
|Categoria|Protocolo|Especificação e uso|  
|--------------|--------------|-----------------------------|  
|Transporte|HTTP 1.1|[HTTP 1.1](http://go.microsoft.com/fwlink/?LinkId=84048)<br /><br /> `BasicHttpBinding`, `WSHttpBinding`, e `WS2007HttpBinding` usar os transportes HTTP e HTTPS.|  
|Mensagens|MTOM|[MTOM](http://go.microsoft.com/fwlink/?LinkId=95326)<br /><br /> `basicHttpBinding`, `wsHttpBinding`, e `ws2007HttpBinding` suporte do mecanismo de otimização de transmissão mensagem (MTOM). Não é usado por padrão. Para usar MTOM, defina o `messageEncoding` atributo `"Mtom"`.<br /><br /> Exemplo:<br /><br /> `<wsHttpBinding> <binding messageEncoding="Mtom"/> </wsHttpBinding>`|  
|Metadados|WSDL 1.1|[WSDL 1.1](http://go.microsoft.com/fwlink/?LinkId=94859)<br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usa o WSDL Web Services Description Language () para descrever serviços.|  
|Metadados|WS-Policy|[WS-Policy](http://go.microsoft.com/fwlink/?LinkId=94864)<br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usa a especificação WS-Policy junto com declarações específicas de domínio para descrever os recursos e requisitos de serviço.|  
|Metadados|WS-Policy 1.5|[WS-Policy 1.5](http://go.microsoft.com/fwlink/?LinkId=95327)<br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usa a especificação WS-Policy junto com declarações específicas de domínio para descrever os recursos e requisitos de serviço.|  
|Metadados|WS-PolicyAttachment|[WS-PolicyAttachment](http://go.microsoft.com/fwlink/?LinkId=95328)<br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] implementa um mecanismo WS-PolicyAttachment para anexar a expressões de política em vários escopos no WSDL Web Services Description Language ().|  
|Metadados|WS-MetadataExchange|[WS-MetadataExchange](http://go.microsoft.com/fwlink/?LinkId=94868)<br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] implementa o WS-MetadataExchange para recuperar o esquema XML, WSDL e WS-Policy.|  
  
### <a name="basichttpbinding"></a>basicHttpBinding  
  
|Categoria|Protocolo|Especificação e uso|  
|--------------|--------------|-----------------------------|  
|Mensagens|SOAP 1.1|[SOAP 1.1](http://go.microsoft.com/fwlink/?LinkId=90520)<br /><br /> De acordo com o Basic Profile 1.1, o `basicHttpBinding` elemento implementa o protocolo de mensagem SOAP 1.1.|  
|Segurança|Segurança de mensagens SOAP do WSS 1.0|[Segurança de mensagens SOAP do WSS 1.0](http://go.microsoft.com/fwlink/?LinkId=94684)<br /><br /> O perfil básico de segurança, de acordo com o `basicHttpBinding` elemento implementa a especificação de segurança de mensagens SOAP de segurança de serviços da Web (WSS) 1.0 para o nome de usuário/senha e segurança com base em x. 509.<br /><br /> `<basicHttpBinding> <binding name="Binding1"> <security mode="TransportWithMessageCredential &#124;                     "Message" .../> </binding> </basicHttpBinding>`|  
|Segurança|Segurança de mensagem do WSS SOAP UsernameToken perfil 1.0|[Segurança de mensagem do WSS SOAP UsernameToken perfil 1.0](http://go.microsoft.com/fwlink/?LinkId=95334)<br /><br /> `<basicHttpBinding> <binding name="Binding1"> <security mode="TransportWithMessageCredential"> <transport clientCredentialType="Basic"/> </security> </basicHttpBinding>`|  
|Segurança|WSS SOAP mensagem segurança x. 509 Token perfil de certificado 1.0|[WSS SOAP mensagem segurança x. 509 Token perfil de certificado 1.0](http://go.microsoft.com/fwlink/?LinkId=95335)<br /><br /> `<basicHttpBinding>   <security mode="Message"> <message clientCredentialType="Certificate"/> </security> </basicHttpBinding>`|  
  
### <a name="wshttpbinding-ws2007httpbinding-and-wsdualhttpbinding"></a>wsHttpBinding, ws2007HttpBinding e wsDualHttpBinding  
  
|Categoria|Protocolo|Especificação e uso|  
|--------------|--------------|-----------------------------|  
|Mensagens|SOAP 1.2|[Livro de instruções](http://go.microsoft.com/fwlink/?LinkId=48282)<br /><br /> [Estrutura de mensagens](http://go.microsoft.com/fwlink/?LinkId=94664)<br /><br /> [Adjuncts (incluindo a associação HTTP)](http://go.microsoft.com/fwlink/?LinkId=95329)|  
|Mensagens|08/2005 WS-Addressing.|[1.0 - Core endereçamento de serviços Web](http://go.microsoft.com/fwlink/?LinkId=90574)<br /><br /> [1.0 - SOAP endereçamento de serviços Web](http://go.microsoft.com/fwlink/?LinkId=95330)<br /><br /> O `wsHttpBinding`, `ws2007HttpBinding`, e `wsDualHttpBinding` implementar a recomendação de WS-Addressing World Wide Web Consortium (W3C) para habilitar o sistema de mensagens assíncronas, correlação de mensagem e mecanismos de transporte com neutralidade de endereçamento.<br /><br /> O WCF não dá suporte à criptografia de cabeçalhos WS-Addressing Embora isso é permitido por WS-* especificações.|  
|Mensagens|WS-Addressing 1.0 - metadados|[WS-Addressing 1.0 metadados](http://www.w3.org/2007/05/addressing/metadata) suporte para esse protocolo é habilitado ao definir a versão de política no comportamento ServiceMetadata - com policyversion definido como 1.2 (o padrão), a descrição de wsdl é compatível com o WS-Addressing wsdl, com policyversion definido para 1.5, a descrição de wsdl é compatível com metadados de ws-addressing.<br /><br /> O WCF não dá suporte à criptografia de cabeçalhos WS-Addressing Embora isso é permitido por WS-* especificações.|  
|Segurança|Segurança de mensagens SOAP do WSS 1.0|[Segurança de mensagens SOAP do WSS 1.0](http://go.microsoft.com/fwlink/?LinkId=94684)<br /><br /> Usado quando o `securityMode` atributo é definido como "wsSecurityOverHttp" (padrão) e os parâmetros são configurados usando um `wsSecurity` elemento filho.<br /><br /> `<wsHttpBinding>   <binding name="myBinding">      <security mode="Message" .../>   </binding> </wsHttpBinding>`|  
|Segurança|Segurança de mensagem do WSS SOAP UsernameToken Profile 1.1|[Segurança de mensagem do WSS SOAP UsernameToken perfil 1.0](http://go.microsoft.com/fwlink/?LinkId=95331)<br /><br /> Usado quando o `wsSecurity` do elemento `authenticationMode` atributo é definido como "Username".<br /><br /> `<wsHttpBinding>   <binding name="MyBinding">     <security mode="Message>       <message           clientCredentialType="UserName        negotiateServiceCredential="false"        establishSecurityContext="false"/>     </security> </binding> </wsHttpBinding>`|  
|Segurança|WSS SOAP mensagem segurança x. 509 Token perfil de certificado 1.1|[WSS SOAP mensagem segurança x. 509 Token perfil de certificado 1.1](http://go.microsoft.com/fwlink/?LinkId=95332)<br /><br /> Use para proteção de mensagem quando o `wsSecurity` do elemento `authenticationMode` atributo é definido como "Username", "Certificado" ou "None". Além disso, usar isso para autenticação de cliente quando o `wsSecurity` do elemento `authenticationMode` atributo é definido como "Certificado".<br /><br /> `<wsHttpBinding>   <binding name="MyBinding">     <security mode="Message>       <message           clientCredentialType="Certificate"        negotiateServiceCredential="false"        establishSecurityContext="false"/>     </security>   </binding> </wsHttpBinding>`|  
|Segurança|Perfil do Token Kerberos de segurança mensagem WSS SOAP 1.1|[Perfil do Token Kerberos de segurança mensagem WSS SOAP 1.1](http://go.microsoft.com/fwlink/?LinkId=95333)<br /><br /> Use para proteção de autenticação e de mensagem quando o `wsSecurity` do elemento `authenticationMode` atributo é definido como "Windows".<br /><br /> `<wsHttpBinding>   <binding name="MyBinding">     <security mode="Message>       <message           clientCredentialType="Windows"        negotiateServiceCredential="false"        establishSecurityContext="false"/>     </security>   </binding> </wsHttpBinding>`|  
|Segurança|WS-SecureConversation|[WS-SecureConversation](http://go.microsoft.com/fwlink/?LinkId=95317)<br /><br /> Use para fornecer uma sessão segura quando o `security/@mode` atributo é definido como "Mensagem" e o `message/@establishSecurityContext` atributo é definido como "true" (padrão).|  
|Segurança|WS-Trust|[WS-Trust](http://go.microsoft.com/fwlink/?LinkId=95318)<br /><br /> Usado por WS-SecureConversation (veja acima).|  
|Mensagens confiáveis|WS-ReliableMessaging|[WS-ReliableMessaging](http://go.microsoft.com/fwlink/?LinkId=95322)<br /><br /> Use quando a associação está configurada para usar `reliableSession`.<br /><br /> `<wsHttpBinding>  <binding name="myBinding">    <reliableSession/>   </binding> </wsHttpBinding>`|  
|Transações|WS-AtomicTransaction|[WS-AtomicTransaction](http://go.microsoft.com/fwlink/?LinkId=95323)<br /><br /> Usado para comunicação entre os gerenciadores de transações. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] clientes e serviços sempre usam gerenciadores de transações locais.|  
|Transações|Coordenação WS|[WS-Coordination](http://go.microsoft.com/fwlink/?LinkId=95324)<br /><br /> Usar o fluxo do contexto de transação quando o `flowTransactions` atributo é definido como "Permitido" ou "Necessário".<br /><br /> `<wsHttpBinding>   <binding transactionFlow="true"/> </wsHttpBinding>`|  
  
## <a name="wsfederationhttpbinding-and-ws2007federationhttpbinding"></a>wsFederationHttpBinding e ws2007FederationHttpBinding  
 O [ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) e [ \<ws2007FederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/ws2007federationhttpbinding.md) elementos são introduzidos para fornecer suporte para cenários federados, onde um terceiro parte emite um token usado para autenticar um cliente. Além de protocolos usados pelo `wsHttpBinding`, `wsFederationHttpBinding` aproveita:  
  
-   `WS-Trust` para emissão de tokens.  
  
-   WSS Security asserções Markup Language (SAML) Token perfil 1.0 e 1.1 para mais comumente emitido formato do token.  
  
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
 As tabelas a seguir descrevem os protocolos suportados pelas associações de metadados de interoperabilidade fornecidas pelo sistema expostas pelo <xref:System.ServiceModel.Description.MetadataExchangeBindings?displayProperty=nameWithType> classe.  
  
### <a name="mexhttpbinding"></a>mexHttpBinding  
 O [ \<mexHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpbinding.md) associação suporta os seguintes protocolos. [!INCLUDE[crabout](../../../../includes/crabout-md.md)] usando essa associação, consulte [metadados de publicação](../../../../docs/framework/wcf/feature-details/publishing-metadata.md).  
  
|Categoria|Protocolo|Especificação e uso|  
|--------------|--------------|-----------------------------|  
|Transporte|HTTP 1.1|[HTTP 1.1](http://go.microsoft.com/fwlink/?LinkId=84048)|  
|Mensagens|SOAP 1.2|[Livro de instruções](http://go.microsoft.com/fwlink/?LinkId=48282)<br /><br /> [Estrutura de mensagens](http://go.microsoft.com/fwlink/?LinkId=94664)<br /><br /> [Adjuncts (incluindo a associação HTTP)](http://go.microsoft.com/fwlink/?LinkId=95329)|  
|Mensagens|08/2005 WS-Addressing.|[1.0 - Core endereçamento de serviços Web](http://go.microsoft.com/fwlink/?LinkId=90574)<br /><br /> [1.0 - SOAP endereçamento de serviços Web](http://go.microsoft.com/fwlink/?LinkId=95330)|  
|Metadados|WS-MetadataExchange|[WS-MetadataExchange](http://go.microsoft.com/fwlink/?LinkId=94868)<br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] implementa o WS-MetadataExchange para recuperar o esquema XML, WSDL e WS-Policy.|  
  
### <a name="mexhttpsbinding"></a>mexHttpsBinding  
 [\<mexHttpsBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpsbinding.md) suporta os seguintes protocolos. [!INCLUDE[crabout](../../../../includes/crabout-md.md)] usando essa associação, consulte [metadados de publicação](../../../../docs/framework/wcf/feature-details/publishing-metadata.md).  
  
|Categoria|Protocolo|Especificação e uso|  
|--------------|--------------|-----------------------------|  
|Transporte|HTTP 1.1|[HTTP 1.1](http://go.microsoft.com/fwlink/?LinkId=84048)<br /><br /> Segurança de transporte está habilitada.|  
|Mensagens|SOAP 1.2|[Livro de instruções](http://go.microsoft.com/fwlink/?LinkId=48282)<br /><br /> [Estrutura de mensagens](http://go.microsoft.com/fwlink/?LinkId=94664)<br /><br /> [Adjuncts (incluindo a associação HTTP)](http://go.microsoft.com/fwlink/?LinkId=95329)|  
|Mensagens|08/2005 WS-Addressing.|[1.0 - Core endereçamento de serviços Web](http://go.microsoft.com/fwlink/?LinkId=90574)<br /><br /> [1.0 - SOAP endereçamento de serviços Web](http://go.microsoft.com/fwlink/?LinkId=95330)|  
|Metadados|WS-MetadataExchange|[WS-MetadataExchange](http://go.microsoft.com/fwlink/?LinkId=94868)<br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] implementa o WS-MetadataExchange para recuperar o esquema XML, WSDL e WS-Policy.|  
  
## <a name="see-also"></a>Consulte também  
 [Associações fornecidas pelo sistema](../../../../docs/framework/wcf/system-provided-bindings.md)  
 [\<basicHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)  
 [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)  
 [\<wsDualHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)  
 [\<mexHttpsBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpsbinding.md)  
 [\<mexHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpbinding.md)
