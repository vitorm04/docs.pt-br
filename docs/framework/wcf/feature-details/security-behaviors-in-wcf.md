---
title: Comportamentos de segurança no WCF
ms.date: 03/30/2017
ms.assetid: 513232c0-39fd-4409-bda6-5ebd5e0ea7b0
ms.openlocfilehash: 12ae9bb90752fe3ee76404948693c501fc42efe6
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76730946"
---
# <a name="security-behaviors-in-wcf"></a>Comportamentos de segurança no WCF
No Windows Communication Foundation (WCF), os comportamentos modificam o comportamento de tempo de execução no nível de serviço ou no nível do ponto de extremidade. (Para obter mais informações sobre comportamentos em geral, consulte [especificando o comportamento de tempo de execução do serviço](../../../../docs/framework/wcf/specifying-service-run-time-behavior.md).) Os *comportamentos de segurança* permitem o controle sobre credenciais, autenticação, autorização e logs de auditoria. Você pode usar comportamentos por programação ou por meio de configuração. Este tópico se concentra na configuração dos seguintes comportamentos relacionados às funções de segurança:  
  
- [\<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md).  
  
- [\<clientcredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md).  
  
- [> de\<de autorização](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md).  
  
- [\<serviceSecurityAudit >](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md).  
  
- [\<> de metadados](../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md), que também permite especificar um ponto de extremidade seguro que os clientes podem acessar para metadados.  
  
## <a name="setting-credentials-with-behaviors"></a>Definindo credenciais com comportamentos  
 Use o [\<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) e [\<ClientCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) para definir valores de credencial para um serviço ou cliente. A configuração de associação subjacente determina se uma credencial deve ser definida. Por exemplo, se o modo de segurança for definido como `None`, os clientes e serviços não se autenticarão e não exigirão nenhuma credencial de nenhum tipo.  
  
 Por outro lado, a associação de serviço pode exigir um tipo de credencial de cliente. Nesse caso, talvez seja necessário definir um valor de credencial usando um comportamento. (Para obter mais informações sobre os possíveis tipos de credenciais, consulte [selecionando um tipo de credencial](../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md).) Em alguns casos, como quando as credenciais do Windows são usadas para autenticação, o ambiente estabelece automaticamente o valor real da credencial e você não precisa definir explicitamente o valor da credencial (a menos que você queira especificar um conjunto diferente de credenciais).  
  
 Todas as credenciais de serviço são encontradas como elementos filho do [> de\<](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md)de serviços. O exemplo a seguir mostra um certificado usado como uma credencial de serviço.  
  
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
 O [\<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) contém quatro elementos filho. Os elementos e seus usos são discutidos nas seções a seguir.  
  
### <a name="servicecertificate-element"></a>Elemento de > de \<de certificados  
 Use este elemento para especificar um certificado X. 509 que é usado para autenticar o serviço para clientes usando o modo de segurança de mensagem. Se você estiver usando um certificado que é renovado periodicamente, sua impressão digital será alterada. Nesse caso, use o nome da entidade como o `X509FindType` porque o certificado pode ser reemitido com o mesmo nome de entidade.  
  
 Para obter mais informações sobre como usar o elemento, consulte [como especificar valores de credencial do cliente](../../../../docs/framework/wcf/how-to-specify-client-credential-values.md).  
  
### <a name="certificate-of-clientcertificate-element"></a>\<> de certificado do elemento \<clientCertificate >  
 Use o elemento [\<> de certificado](../../../../docs/framework/configure-apps/file-schema/wcf/certificate-of-clientcertificate-element.md) quando o serviço precisar ter o certificado do cliente com antecedência para se comunicar com segurança com o cliente. Isso ocorre ao usar o padrão de comunicação duplex. No padrão de solicitação-resposta mais comum, o cliente inclui seu certificado na solicitação, que o serviço usa para proteger sua resposta de volta para o cliente. No entanto, o padrão de comunicação duplex não tem solicitações e respostas. O serviço não pode inferir o certificado do cliente da comunicação e, portanto, o serviço requer o certificado do cliente com antecedência para proteger as mensagens para o cliente. Você deve obter o certificado do cliente em um modo fora de banda e especificar o certificado usando esse elemento. Para obter mais informações sobre os serviços duplex, consulte [como: criar um contrato duplex](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).  
  
### <a name="authentication-of-clientcertificate-element"></a>\<> de autenticação do elemento \<clientCertificate >  
 O elemento de [> de autenticação\<](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md) permite que você personalize como os clientes são autenticados. Você pode definir o atributo `CertificateValidationMode` como `None`, `ChainTrust`, `PeerOrChainTrust`, `PeerTrust`ou `Custom`. Por padrão, o nível é definido como `ChainTrust`, que especifica que cada certificado deve ser encontrado em uma hierarquia de certificados que terminam em uma *autoridade raiz* na parte superior da cadeia. Esse é o modo mais seguro. Você também pode definir o valor como `PeerOrChainTrust`, que especifica que os certificados emitidos por conta própria (peer Trust) são aceitos, bem como certificados que estão em uma cadeia confiável. Esse valor é usado ao desenvolver e depurar clientes e serviços porque certificados emitidos por conta própria não precisam ser comprados de uma autoridade confiável. Ao implantar um cliente, use o valor `ChainTrust` em vez disso. Você também pode definir o valor para `Custom`. Quando definido como o valor `Custom`, você também deve definir o atributo `CustomCertificateValidatorType` como um assembly e o tipo usado para validar o certificado. Para criar seu próprio validador personalizado, você deve herdar da classe abstrata <xref:System.IdentityModel.Selectors.X509CertificateValidator>.  
  
### <a name="issuedtokenauthentication-element"></a>\<elemento de > issuedTokenAuthentication  
 O cenário de token emitido tem três estágios. No primeiro estágio, um cliente que está tentando acessar um serviço é referenciado como um *serviço de token seguro* (STS). Em seguida, o STS autentica o cliente e subsequentemente emite um token do cliente, normalmente um token SAML (Security Assertion Markup Language). O cliente retorna ao serviço com o token. O serviço examina o token de dados que permite que o serviço autentique o token e, portanto, o cliente. Para autenticar o token, o certificado que o serviço de token seguro usa deve ser conhecido pelo serviço. O elemento [\<issuedTokenAuthentication >](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md) é o repositório de qualquer certificado de serviço de token seguro. Para adicionar certificados, use o [\<knownCertificates >](../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md). Insira um [\<adicionar >](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md) para cada certificado, conforme mostrado no exemplo a seguir.  
  
```xml  
<issuedTokenAuthentication>  
   <knownCertificates>  
      <add findValue="www.contoso.com"   
           storeLocation="LocalMachine" storeName="My"   
           X509FindType="FindBySubjectName" />  
    </knownCertificates>  
</issuedTokenAuthentication>  
```  
  
 Por padrão, os certificados devem ser obtidos de um serviço de token seguro. Esses certificados "conhecidos" garantem que somente clientes legítimos possam acessar um serviço.  
  
 Você deve usar a coleção [\<allowedAudienceUris >](../../../../docs/framework/configure-apps/file-schema/wcf/allowedaudienceuris.md) em um aplicativo federado que utiliza um *serviço de token seguro* (STS) que emite `SamlSecurityToken` tokens de segurança. Quando o STS emite o token de segurança, ele pode especificar o URI dos serviços Web para os quais o token de segurança é destinado adicionando um `SamlAudienceRestrictionCondition` ao token de segurança. Isso permite que o `SamlSecurityTokenAuthenticator` para o serviço Web de destinatário Verifique se o token de segurança emitido destina-se a esse serviço Web, especificando que essa verificação deve acontecer fazendo o seguinte:  
  
- Defina o atributo `audienceUriMode` de [\<issuedTokenAuthentication >](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md) como `Always` ou `BearerKeyOnly`.  
  
- Especifique o conjunto de URIs válidos adicionando os URIs a esta coleção. Para fazer isso, insira um [\<adicionar >](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-allowedaudienceuris.md) para cada URI  
  
 Para obter mais informações, consulte <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.  
  
 Para obter mais informações sobre como usar esse elemento de configuração, consulte [How to: Configure Credentials on a serviço de Federação](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).  
  
#### <a name="allowing-anonymous-cardspace-users"></a>Permitindo usuários anônimos do CardSpace  
 A definição do atributo `AllowUntrustedRsaIssuers` do elemento `<IssuedTokenAuthentication>` como `true` permite explicitamente que qualquer cliente apresente um token emitido por conta própria assinado com um par de chaves de RSA arbitrário. O emissor não é *confiável* porque a chave não tem dados de emissor associados a ele. Um usuário do CardSpace pode criar um cartão emitido por conta própria, que inclui declarações de identidade autofornecidas. Use essa funcionalidade com cuidado. Para usar esse recurso, considere a chave pública RSA como uma senha mais segura que deve ser armazenada em um banco de dados junto com um nome de usuário. Antes de permitir que um cliente acesse o serviço, verifique a chave pública RSA apresentada pelo cliente comparando-a com a chave pública armazenada para o nome de usuário apresentado. Isso pressupõe que você estabeleceu um processo de registro pelo qual os usuários podem registrar seus nomes de usuário e associá-los às chaves públicas autoemitidas da RSA.  
  
## <a name="client-credentials"></a>Credenciais do cliente  
 As credenciais do cliente são usadas para autenticar o cliente para serviços em casos em que a autenticação mútua é necessária. Você pode usar a seção para especificar certificados de serviço para cenários em que o cliente deve proteger mensagens para um serviço com o certificado do serviço.  
  
 Você também pode configurar um cliente como parte de um cenário de Federação para usar tokens emitidos de um serviço de token seguro ou um emissor local de tokens. Para obter mais informações sobre cenários federados, consulte [Federação e tokens emitidos](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md). Todas as credenciais do cliente são encontradas no [>\<EndpointBehaviors](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md), conforme mostrado no código a seguir.  
  
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
  
#### <a name="clientcertificate-element"></a>\<elemento de > clientCertificate  
 Defina o certificado usado para autenticar o cliente com este elemento. Para obter mais informações, consulte [como especificar valores de credenciais de cliente](../../../../docs/framework/wcf/how-to-specify-client-credential-values.md).  
  
#### <a name="httpdigest"></a>\<httpDigest >  
 Esse recurso deve ser habilitado com Active Directory no Windows e no Serviços de Informações da Internet (IIS). Para obter mais informações, consulte [autenticação Digest no IIS 6,0](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc782661(v=ws.10)).  
  
#### <a name="issuedtoken-element"></a>\<elemento de > issuedToken  
 O [\<issuedToken >](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md) contém os elementos usados para configurar um emissor local de tokens ou os comportamentos usados com um serviço de token de segurança. Para obter instruções sobre como configurar um cliente para usar um emissor local, consulte [como: configurar um emissor local](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).  
  
#### <a name="localissueraddress"></a>\<localIssuerAddress >  
 Especifica um endereço de serviço de token de segurança padrão. Isso é usado quando o <xref:System.ServiceModel.WSFederationHttpBinding> não fornece uma URL para o serviço de token de segurança ou quando o endereço do emissor de uma associação federada é `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` ou `null`. Nesses casos, o <xref:System.ServiceModel.Description.ClientCredentials> deve ser configurado com o endereço do emissor local e a associação a ser usada para se comunicar com esse emissor.  
  
#### <a name="issuerchannelbehaviors"></a>\<issuerChannelBehaviors >  
 Use o [\<issuerChannelBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md) para adicionar os comportamentos de cliente do WCF usados ao se comunicar com um serviço de token de segurança. Defina comportamentos do cliente na seção [\<endpointBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md) . Para usar um comportamento definido, adicione um elemento <`add`> ao elemento `<issuerChannelBehaviors>` com dois atributos. Defina o `issuerAddress` como a URL do serviço de token de segurança e defina o atributo `behaviorConfiguration` como o nome do comportamento de ponto de extremidade definido, conforme mostrado no exemplo a seguir.  
  
```xml  
<clientCredentials>  
   <issuedToken>  
      <issuerChannelBehaviors>  
         <add issuerAddress="http://www.contoso.com"  
               behaviorConfiguration="clientBehavior1" />     
```  
  
#### <a name="servicecertificate-element"></a>Elemento de > de \<de certificados  
 Use este elemento para controlar a autenticação de certificados de serviço.  
  
 O elemento [>\<DefaultCertificate](../../../../docs/framework/configure-apps/file-schema/wcf/defaultcertificate-element.md) pode armazenar um único certificado usado quando o serviço especifica que não há nenhum certificado.  
  
 Use o [>\<scopedCertificates](../../../../docs/framework/configure-apps/file-schema/wcf/scopedcertificates-element.md) e [\<Adicionar >](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-scopedcertificates-element.md) para definir certificados de serviço associados a serviços específicos. O elemento `<add>` inclui um atributo `targetUri` que é usado para associar o certificado ao serviço.  
  
 O elemento de [> de autenticação\<](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md) especifica o nível de confiança usado para autenticar certificados. Por padrão, o nível é definido como "ChainTrust", que especifica que cada certificado deve ser encontrado em uma hierarquia de certificados que terminam em uma autoridade de certificação confiável na parte superior da cadeia. Esse é o modo mais seguro. Você também pode definir o valor como "PeerOrChainTrust", que especifica que os certificados emitidos por conta própria (peer Trust) são aceitos, bem como os certificados que estão em uma cadeia confiável. Esse valor é usado ao desenvolver e depurar clientes e serviços porque certificados emitidos por conta própria não precisam ser comprados de uma autoridade confiável. Ao implantar um cliente, use o valor "ChainTrust" em seu lugar. Você também pode definir o valor como "Custom" ou "None". Para usar o valor "Custom", você também deve definir o atributo `CustomCertificateValidatorType` como um assembly e o tipo usado para validar o certificado. Para criar seu próprio validador personalizado, você deve herdar da classe abstrata <xref:System.IdentityModel.Selectors.X509CertificateValidator>. Para obter mais informações, consulte [como: criar um serviço que emprega um validador de certificado personalizado](../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).  
  
 O elemento de [> de autenticação\<](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md) inclui um atributo `RevocationMode` que especifica como os certificados são verificados quanto à revogação. O padrão é "online", que indica que os certificados são verificados automaticamente para revogação. Para obter mais informações, consulte [trabalhando com certificados](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).  
  
## <a name="serviceauthorization"></a>ServiceAuthorization  
 O elemento de [> de\<](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) de autenticação contém elementos que afetam a autorização, os provedores de funções personalizados e a representação.  
  
 A classe <xref:System.Security.Permissions.PrincipalPermissionAttribute> é aplicada a um método de serviço. O atributo especifica os grupos de usuários a serem usados ao autorizar o uso de um método protegido. O valor padrão é "UseWindowsGroups" e especifica que os grupos do Windows, como "administradores" ou "usuários", são pesquisados em busca de uma identidade que tenta acessar um recurso. Você também pode especificar "UseAspNetRoles" para usar um provedor de função personalizado configurado no elemento <`system.web` >, conforme mostrado no código a seguir.  
  
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
  
 O código a seguir mostra o `roleProviderName` usado com o atributo `principalPermissionMode`.  
  
```xml  
<behaviors>  
 <behavior name="ServiceBehaviour">          
  <serviceAuthorization principalPermissionMode ="UseAspNetRoles"   
                        roleProviderName ="SqlProvider" />  
</behavior>   
   <!-- Other configuration code not shown. -->  
</behaviors>  
```  
  
## <a name="configuring-security-audits"></a>Configurando auditorias de segurança  
 Use o [\<serviceSecurityAudit >](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md) para especificar o log gravado e quais tipos de eventos registrar. Para obter mais informações, consulte [auditoria](../../../../docs/framework/wcf/feature-details/auditing-security-events.md).  
  
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
  
## <a name="secure-metadata-exchange"></a>Proteger a troca de metadados  
 A exportação de metadados para clientes é conveniente para desenvolvedores de serviço e cliente, pois permite downloads de configuração e código de cliente. Para reduzir a exposição de um serviço a usuários mal-intencionados, é possível proteger a transferência usando o mecanismo SSL sobre HTTP (HTTPS). Para fazer isso, primeiro você deve associar um certificado X. 509 adequado a uma porta específica no computador que está hospedando o serviço. (Para obter mais informações, consulte [trabalhando com certificados](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).) Em segundo lugar, adicione um [> de\<de metadados](../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md) à configuração de serviço e defina o atributo `HttpsGetEnabled` como `true`. Por fim, defina o atributo `HttpsGetUrl` como a URL do ponto de extremidade de metadados de serviço, conforme mostrado no exemplo a seguir.  
  
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
  
## <a name="see-also"></a>Consulte também

- [Auditoria](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)
- [Modelo de segurança para o Windows Server app Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))
