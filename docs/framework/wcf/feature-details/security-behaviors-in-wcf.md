---
title: Comportamentos de segurança no WCF
ms.date: 03/30/2017
ms.assetid: 513232c0-39fd-4409-bda6-5ebd5e0ea7b0
ms.openlocfilehash: f56bbd66aa61b8db9d6e720fb3a67ddbbf5e267e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184534"
---
# <a name="security-behaviors-in-wcf"></a>Comportamentos de segurança no WCF
No Windows Communication Foundation (WCF), os comportamentos modificam o comportamento de tempo de execução no nível de serviço ou no nível de ponto final. (Para obter mais informações sobre comportamentos em geral, consulte [Especificar comportamento de tempo de execução de serviço](../../../../docs/framework/wcf/specifying-service-run-time-behavior.md).) *Os comportamentos de segurança* permitem o controle sobre credenciais, autenticação, autorização e registros de auditoria. Você pode usar comportamentos tanto pela programação quanto pela configuração. Este tópico se concentra na configuração dos seguintes comportamentos relacionados às funções de segurança:  
  
- serviceCredenciais>. [ \< ](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)  
  
- clientCredentials>. [ \< ](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)  
  
- [>de>de serviços . \< ](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md)  
  
- serviçoSecurityAudit>. [ \< ](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md)  
  
- serviceMetadata>, que também permite especificar um ponto final seguro que os clientes podem acessar para metadados. [ \< ](../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md)  
  
## <a name="setting-credentials-with-behaviors"></a>Definindo credenciais com comportamentos  
 Use os [ \<serviceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) e [ \<clientCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) para definir valores de credenciais para um serviço ou cliente. A configuração de vinculação subjacente determina se uma credencial deve ser definida. Por exemplo, se o modo `None`de segurança estiver definido para, tanto clientes quanto serviços não autenticam uns aos outros e não exigem credenciais de qualquer tipo.  
  
 Por outro lado, a vinculação do serviço pode exigir um tipo de credencial do cliente. Nesse caso, você pode ter que definir um valor de credencial usando um comportamento. (Para obter mais informações sobre os possíveis tipos de credenciais, consulte [Selecionar um tipo de credencial](../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md).) Em alguns casos, como quando as credenciais do Windows são usadas para autenticar, o ambiente estabelece automaticamente o valor real da credencial e você não precisa definir explicitamente o valor de credencial (a menos que você queira especificar um conjunto diferente de credenciais).  
  
 Todas as credenciais de serviço são encontradas como elementos infantis do [ \<serviçoComportamentos>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md). O exemplo a seguir mostra um certificado usado como credencial de serviço.  
  
```xml  
<configuration>  
 <system.serviceModel>  
  <behaviors>  
   <serviceBehaviors>  
    <behavior name="ServiceBehavior1">  
     <serviceCredentials>  
      <serviceCertificate findValue="000000000000000000000000000"
                          storeLocation="CurrentUser"  
      storeName="Root" x509FindType="FindByThumbprint" />  
     </serviceCredentials>  
    </behavior>  
   </serviceBehaviors>  
  </behaviors>  
 </system.serviceModel>  
</configuration>  
```  
  
## <a name="service-credentials"></a>Credenciais de serviço  
 O [ \<serviceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) contém quatro elementos infantis. Os elementos e seus usos são discutidos nas seções a seguir.  
  
### <a name="servicecertificate-element"></a>\<elemento de> de certificado de serviço  
 Use esse elemento para especificar um certificado X.509 que é usado para autenticar o serviço aos clientes usando o modo de segurança de mensagem. Se você estiver usando um certificado que é renovado periodicamente, então sua impressão digital muda. Nesse caso, use o nome `X509FindType` do assunto como porque o certificado pode ser reemitido com o mesmo nome de assunto.  
  
 Para obter mais informações sobre o uso do elemento, consulte [Como: Especificar valores de credencial do cliente](../../../../docs/framework/wcf/how-to-specify-client-credential-values.md).  
  
### <a name="certificate-of-clientcertificate-element"></a>\<> de \<certificado do clienteCertificate> Element  
 Use [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/certificate-of-clientcertificate-element.md) o certificado>elemento quando o serviço deve ter o certificado do cliente com antecedência para se comunicar com segurança com o cliente. Isso ocorre ao usar o padrão de comunicação duplex. No padrão de solicitação-resposta mais típico, o cliente inclui seu certificado na solicitação, que o serviço usa para garantir sua resposta de volta ao cliente. O padrão de comunicação duplex, no entanto, não tem pedidos e respostas. O serviço não pode inferir o certificado do cliente a partir da comunicação e, portanto, o serviço requer o certificado do cliente com antecedência para garantir as mensagens ao cliente. Você deve obter o certificado do cliente de forma fora de banda e especificar o certificado usando esse elemento. Para obter mais informações sobre serviços duplex, consulte [Como: Criar um contrato duplex](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).  
  
### <a name="authentication-of-clientcertificate-element"></a>\<> de \<autenticação do clienteCertificate> Element  
 O elemento [ \<de autenticação>](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md) permite personalizar como os clientes são autenticados. Você pode `CertificateValidationMode` definir `None`o `ChainTrust` `PeerOrChainTrust`atributo para , , , `PeerTrust`ou `Custom`. Por padrão, o nível `ChainTrust`é definido para , o que especifica que cada certificado deve ser encontrado em uma hierarquia de certificados que terminam em uma *autoridade raiz* no topo da cadeia. Este é o modo mais seguro. Você também pode definir `PeerOrChainTrust`o valor para , o que especifica que certificados auto-emitidos (peer trust) são aceitos, bem como certificados que estão em uma cadeia confiável. Esse valor é usado ao desenvolver e depurar clientes e serviços porque os certificados auto-emitidos não precisam ser comprados de uma autoridade confiável. Ao implantar um cliente, `ChainTrust` use o valor em vez disso. Você também pode definir `Custom`o valor para . Quando definido `Custom` como valor, você `CustomCertificateValidatorType` também deve definir o atributo para um conjunto e tipo usado para validar o certificado. Para criar seu próprio validador personalizado, <xref:System.IdentityModel.Selectors.X509CertificateValidator> você deve herdar da classe abstrata.  
  
### <a name="issuedtokenauthentication-element"></a>\<elemento de> de autenticação deToken emitido  
 O cenário de token emitido tem três etapas. Na primeira etapa, um cliente que tenta acessar um serviço é encaminhado para um *serviço de token seguro* (STS). O STS então autentica o cliente e, posteriormente, emite um token para o cliente, tipicamente um token SAML (Security Assertions Markup Language). Em seguida, o cliente retorna ao serviço com o token. O serviço examina o token para dados que permitem que o serviço autentique o token e, portanto, o cliente. Para autenticar o token, o certificado que o serviço de token seguro usa deve ser conhecido pelo serviço. O elemento [ \<de>de autenticação Token emitido](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md) é o repositório de quaisquer certificados de serviço de token seguro. Para adicionar certificados, use os [ \<>conhecidos . ](../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md) Insira um [ \<>adição](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md) para cada certificado, conforme mostrado no exemplo a seguir.  
  
```xml  
<issuedTokenAuthentication>  
   <knownCertificates>  
      <add findValue="www.contoso.com"
           storeLocation="LocalMachine" storeName="My"
           X509FindType="FindBySubjectName" />  
    </knownCertificates>  
</issuedTokenAuthentication>  
```  
  
 Por padrão, os certificados devem ser obtidos a partir de um serviço de token seguro. Esses certificados "conhecidos" garantem que apenas clientes legítimos possam acessar um serviço.  
  
 Você deve usar a `SamlSecurityToken` *secure token service* [ \<coleção allowedAudienceUris>](../../../../docs/framework/configure-apps/file-schema/wcf/allowedaudienceuris.md) em um aplicativo federado que utiliza um serviço de token seguro (STS) que emite tokens de segurança. Quando o STS emite o token de segurança, ele pode especificar o URI `SamlAudienceRestrictionCondition` dos serviços da Web para os quais o token de segurança é destinado adicionando um ao token de segurança. Isso permite `SamlSecurityTokenAuthenticator` que o serviço web do destinatário verifique se o token de segurança emitido é destinado a este serviço web, especificando que essa verificação deve acontecer fazendo o seguinte:  
  
- Defina `audienceUriMode` o atributo do [ \<>Deautenticação Token emitido](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md) para `Always` ou `BearerKeyOnly`.  
  
- Especifique o conjunto de URIs válidos, adicionando as URIs a esta coleção. Para fazer isso, [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-allowedaudienceuris.md) insira um>adicional para cada URI  
  
 Para obter mais informações, consulte <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.  
  
 Para obter mais informações sobre como usar esse elemento de configuração, consulte [Como: Configurar credenciais em um serviço da Federação](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).  
  
#### <a name="allowing-anonymous-cardspace-users"></a>Permitindo usuários anônimos do CardSpace  
 Definir `AllowUntrustedRsaIssuers` o atributo do `<IssuedTokenAuthentication>` elemento para `true` explicitamente permite que qualquer cliente apresente um token auto-emitido assinado com um par de chaves RSA arbitrário. O emissor *não é confiável* porque a chave não tem dados de emissor associados a ele. Um usuário do CardSpace pode criar um cartão auto-emitido que inclui alegações de identidade auto-fornecidas. Use essa capacidade com cautela. Para usar esse recurso, pense na chave pública RSA como uma senha mais segura que deve ser armazenada em um banco de dados juntamente com um nome de usuário. Antes de permitir que um cliente acesse o serviço, verifique a chave pública RSA apresentada pelo cliente, comparando-a com a chave pública armazenada para o nome de usuário apresentado. Isso pressupõe que você estabeleceu um processo de registro pelo qual os usuários podem registrar seus nomes de usuário e associá-los com as chaves públicas RSA auto-emitidas.  
  
## <a name="client-credentials"></a>Credenciais do cliente  
 As credenciais do cliente são usadas para autenticar o cliente em serviços nos casos em que a autenticação mútua é necessária. Você pode usar a seção para especificar certificados de serviço para cenários onde o cliente deve proteger mensagens para um serviço com o certificado do serviço.  
  
 Você também pode configurar um cliente como parte de um cenário de federação para usar tokens emitidos a partir de um serviço de token seguro ou de um emissor local de tokens. Para obter mais informações sobre cenários federados, consulte [Federação e Tokens Emitidos](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md). Todas as credenciais do cliente são encontradas o [ \<ponto finalComportamentos>, ](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md)conforme mostrado no código a seguir.  
  
```xml  
<behaviors>  
 <endpointBehaviors>  
  <behavior name="EndpointBehavior1">  
   <clientCredentials>  
    <clientCertificate findValue="cn=www.contoso.com"
        storeLocation="LocalMachine"  
        storeName="AuthRoot" x509FindType="FindBySubjectName" />  
    <serviceCertificate>  
     <defaultCertificate findValue="www.cohowinery.com"
                    storeLocation="LocalMachine"  
                    storeName="Root" x509FindType="FindByIssuerName" />  
    <authentication revocationMode="Online"  
                    trustedStoreLocation="LocalMachine" />  
    </serviceCertificate>  
   </clientCredentials>  
  </behavior>  
 </endpointBehaviors>  
```  
  
#### <a name="clientcertificate-element"></a>\<elemento> de certificado de cliente  
 Defina o certificado usado para autenticar o cliente com este elemento. Para obter mais informações, consulte [Como: Especificar valores de credencial do cliente](../../../../docs/framework/wcf/how-to-specify-client-credential-values.md).  
  
#### <a name="httpdigest"></a>\<httpDigest>  
 Esse recurso deve ser ativado com o Active Directory no Windows e no Internet Information Services (IIS). Para obter mais informações, consulte [Autenticação Digest no IIS 6.0](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc782661(v=ws.10)).  
  
#### <a name="issuedtoken-element"></a>\<elemento> emitidoToken  
 O [ \<>Token emitido](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md) contém os elementos usados para configurar um emissor local de tokens ou comportamentos usados com um serviço de token de segurança. Para obter instruções sobre como configurar um cliente para usar um emissor local, consulte [Como: Configurar um emissor local](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).  
  
#### <a name="localissueraddress"></a>\<> localIssuerAddress  
 Especifica um endereço de serviço de token de segurança padrão. Isso é usado <xref:System.ServiceModel.WSFederationHttpBinding> quando o url não fornece uma URL para o serviço de token de segurança ou quando o endereço do emissor de uma vinculação federada é `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` ou `null`. Nesses casos, <xref:System.ServiceModel.Description.ClientCredentials> o deve ser configurado com o endereço do emissor local e a vinculação para usar para se comunicar com aquele emissor.  
  
#### <a name="issuerchannelbehaviors"></a>\<emissorChannelBehaviors>  
 Use o [ \<emissorChannelBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md) para adicionar comportamentos de cliente WCF usados ao se comunicar com um serviço de token de segurança. Defina comportamentos do cliente no [ \<endpointComportamentos>](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md) seção. Para usar um comportamento definido, adicione um elemento> <`add` ao elemento com dois atributos. `<issuerChannelBehaviors>` Defina `issuerAddress` a URL do serviço de token de segurança e defina o atributo `behaviorConfiguration` para o nome do comportamento de ponto final definido, conforme mostrado no exemplo a seguir.  
  
```xml  
<clientCredentials>  
   <issuedToken>  
      <issuerChannelBehaviors>  
         <add issuerAddress="http://www.contoso.com"  
               behaviorConfiguration="clientBehavior1" />
```  
  
#### <a name="servicecertificate-element"></a>\<elemento de> de certificado de serviço  
 Use este elemento para controlar a autenticação de certificados de serviço.  
  
 O elemento [ \<>de certificado padrão](../../../../docs/framework/configure-apps/file-schema/wcf/defaultcertificate-element.md) pode armazenar um único certificado usado quando o serviço especifica nenhum certificado.  
  
 Use os [ \<certificados escopo>](../../../../docs/framework/configure-apps/file-schema/wcf/scopedcertificates-element.md) e [ \<adicione>](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-scopedcertificates-element.md) para definir certificados de serviço associados a serviços específicos. O `<add>` elemento inclui `targetUri` um atributo que é usado para associar o certificado ao serviço.  
  
 O elemento [ \<>de autenticação](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md) especifica o nível de confiança usado para autenticar certificados. Por padrão, o nível é definido como "ChainTrust", que especifica que cada certificado deve ser encontrado em uma hierarquia de certificados que terminam em uma autoridade de certificação confiável no topo da cadeia. Este é o modo mais seguro. Você também pode definir o valor como "PeerOrChainTrust", que especifica que certificados auto-emitidos (peer trust) são aceitos, bem como certificados que estão em uma cadeia confiável. Esse valor é usado ao desenvolver e depurar clientes e serviços porque os certificados auto-emitidos não precisam ser comprados de uma autoridade confiável. Ao implantar um cliente, use o valor "ChainTrust". Você também pode definir o valor como "Personalizado" ou "Nenhum". Para usar o valor "Personalizado", você `CustomCertificateValidatorType` também deve definir o atributo para um conjunto e tipo usado para validar o certificado. Para criar seu próprio validador personalizado, <xref:System.IdentityModel.Selectors.X509CertificateValidator> você deve herdar da classe abstrata. Para obter mais informações, [consulte Como: Criar um serviço que emprega um validador de certificadopersonalizado](../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).  
  
 O [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md) elemento>de `RevocationMode` autenticação inclui um atributo que especifica como os certificados são verificados para revogação. O padrão é "online", o que indica que os certificados são automaticamente verificados para revogação. Para obter mais informações, consulte [Trabalhando com Certificados](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).  
  
## <a name="serviceauthorization"></a>Autorização de serviço  
 O [ \<elemento serviceAuthorization>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) contém elementos que afetam a autorização, os provedores de função personalizados e a personificação.  
  
 A <xref:System.Security.Permissions.PrincipalPermissionAttribute> classe é aplicada a um método de serviço. O atributo especifica os grupos de usuários a serem usados ao autorizar o uso de um método protegido. O valor padrão é "UseWindowsGroups" e especifica que grupos do Windows, como "Administradores" ou "Usuários", são pesquisados por uma identidade que tenta acessar um recurso. Você também pode especificar UseAspNetRoles para usar um provedor `system.web` de funções personalizado configurado o elemento <>, conforme mostrado no código a seguir.  
  
```xml  
<system.web>  
  <membership defaultProvider="SqlProvider"
   userIsOnlineTimeWindow="15">  
     <providers>  
       <clear />  
       <add
          name="SqlProvider"
          type="System.Web.Security.SqlMembershipProvider"
          connectionStringName="SqlConn"  
          applicationName="MembershipProvider"  
          enablePasswordRetrieval="false"  
          enablePasswordReset="false"  
          requiresQuestionAndAnswer="false"  
          requiresUniqueEmail="true"  
          passwordFormat="Hashed" />  
     </providers>  
   </membership>  
  <!-- Other configuration code not shown.-->  
</system.web>  
```  
  
 O código a `roleProviderName` seguir `principalPermissionMode` mostra o usado com o atributo.  
  
```xml  
<behaviors>  
 <behavior name="ServiceBehaviour">
  <serviceAuthorization principalPermissionMode ="UseAspNetRoles"
                        roleProviderName ="SqlProvider" />  
</behavior>
   <!-- Other configuration code not shown. -->  
</behaviors>  
```  
  
## <a name="configuring-security-audits"></a>Configuração de auditorias de segurança  
 Use o [ \<serviceSecurityAudit>](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md) para especificar o registro gravado e quais tipos de eventos a registrar. Para obter mais informações, consulte [Auditoria](../../../../docs/framework/wcf/feature-details/auditing-security-events.md).  
  
```xml  
<system.serviceModel>  
<serviceBehaviors>  
  <behavior name="NewBehavior">  
    <serviceSecurityAudit auditLogLocation="Application"
             suppressAuditFailure="true"  
             serviceAuthorizationAuditLevel="Success"
             messageAuthenticationAuditLevel="Success" />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
## <a name="secure-metadata-exchange"></a>Troca de metadados seguro  
 Exportar metadados para clientes é conveniente para desenvolvedores de serviços e clientes, pois permite downloads de configuração e código do cliente. Para reduzir a exposição de um serviço a usuários mal-intencionados, é possível garantir a transferência usando o mecanismo SSL over HTTP (HTTPS). Para isso, você deve primeiro vincular um certificado X.509 adequado a uma porta específica no computador que está hospedando o serviço. (Para obter mais informações, consulte [Trabalhando com Certificados](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).) Em segundo lugar, adicione um `HttpsGetEnabled` `true` [ \<>serviceMetadata](../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md) à configuração do serviço e defina o atributo para . Finalmente, defina o atributo `HttpsGetUrl` para a URL do ponto final de metadados do serviço, como mostrado no exemplo a seguir.  
  
```xml  
<behaviors>  
 <serviceBehaviors>  
  <behavior name="NewBehavior">  
    <serviceMetadata httpsGetEnabled="true"
     httpsGetUrl="https://myComputerName/myEndpoint" />  
  </behavior>  
 </serviceBehaviors>  
</behaviors>  
```  
  
## <a name="see-also"></a>Confira também

- [Auditoria](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)
- [Modelo de segurança para a malha do aplicativo do Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))
