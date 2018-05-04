---
title: '&lt;adicionar&gt; &lt;knownCertificates&gt;'
ms.date: 03/30/2017
ms.assetid: 128aaabe-3f1a-4c3b-b59f-898d0f02910f
ms.openlocfilehash: 0192c14d5ebc0c84859878b35770e03843b2dd50
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltaddgt-of-ltknowncertificatesgt"></a>&lt;adicionar&gt; &lt;knownCertificates&gt;
Adiciona um certificado x. 509 à coleção de certificados conhecidos.  
  
 \<system.ServiceModel>  
\<comportamentos >  
\<serviceBehaviors >  
\<comportamento >  
\<serviceCredentials>  
\<issuedTokenAuthentication >  
\<knownCertificates >  
\<add>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<knownCertificates>   
   <add findValue="String"  
      storeLocation="CurrentUser/LocalMachine"  
      storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"  
      x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"/>  
</knownCertificates>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|findValue|Cadeia. O valor a ser procurado.|  
|storeLocation|Enumeração. Um dos dois locais de repositório para pesquisar.|  
|storeName|Enumeração. Um dos repositórios de sistema para pesquisar.|  
|X509FindType|Enumeração. Um dos campos de certificado a ser pesquisado.|  
  
## <a name="findvalue-attribute"></a>findValue atributo  
  
|Valor|Descrição|  
|-----------|-----------------|  
|Cadeia de Caracteres|O valor depende do campo (especificado pelo atributo X509FindType) que está sendo pesquisado. Por exemplo, se você está procurando uma impressão digital, o valor deve ser uma cadeia de caracteres de números hexadecimais.|  
  
## <a name="x509findtype-attribute"></a>Atributo x509FindType  
  
|Valor|Descrição|  
|-----------|-----------------|  
|Enumeração|Os valores incluem: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.|  
  
## <a name="storelocation-attribute"></a>storeLocation atributo  
  
|Valor|Descrição|  
|-----------|-----------------|  
|Enumeração|CurrentUser ou LocalMachine.|  
  
## <a name="storename-attribute"></a>Atributo da storeName  
  
|Valor|Descrição|  
|-----------|-----------------|  
|Enumeração|Os valores incluem: catálogo de endereços, AuthRoot, CertificateAuthority, não permitidas, My, raiz, TrustedPeople e TrustedPublisher.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<knownCertificates >](../../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md)|Representa uma coleção de certificados x. 509 que são fornecidos por um Token de segurança Service (STS) para validação dos tokens de segurança.|  
  
## <a name="remarks"></a>Comentários  
 O cenário de token emitido tem três etapas. O primeiro estágio, um cliente tentar acessar um serviço é chamado um *do serviço de token seguro*. O serviço de token seguro, em seguida, autentica o cliente e subsequentemente emite para o cliente um token, normalmente um token de segurança asserções SAML (Markup Language). O cliente, em seguida, retorne para o serviço com o token. O serviço examina o token de dados que permite que o serviço autenticar o token e, portanto, o cliente. Para autenticar o token, o certificado usa o serviço de token seguro deve ser conhecida para o serviço.  
  
 O [ \<issuedTokenAuthentication >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md) elemento é o repositório de todos esses certificados de serviço de token seguro. Para adicionar certificados, use o [ \<knownCertificates >](../../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md). Inserir uma [ \<Adicionar > elemento \<knownCertificates > elemento](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md) para cada certificado, conforme mostrado no exemplo a seguir.  
  
```xml  
<issuedTokenAuthentication>  
   <knownCertificates>  
      <add findValue="www.contoso.com"   
           storeLocation="LocalMachine" storeName="My"   
           X509FindType="FindBySubjectName" />  
    </knownCertificates>  
</issuedTokenAuthentication>  
```  
  
 Por padrão, os certificados devem ser obtidos de um serviço de token seguro. Esses "conhecidos" certificados Certifique-se de que apenas legítimas clientes podem acessar um serviço.  
  
 Para examinar as condições exigidas para um cliente seja autenticado por um serviço federado, bem como para obter mais informações sobre este elemento de configuração, consulte [como: configurar credenciais em um serviço de Federação](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md). Para obter mais informações sobre cenários federados, consulte [federação e Tokens emitidos](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir adiciona um certificado no repositório de todos os certificados STS.  
  
```xml  
<serviceBehaviors>  
 <behavior name="myServiceBehavior">  
  <serviceCredentials>  
   <issuedTokenAuthentication>  
    <knownCertificates>  
     <add findValue="www.contoso.com" storeLocation="LocalMachine"   
           storeName="CertificateAuthority"  
           x509FindType="FindByIssuerName" />  
     </knownCertificates>  
    </issuedTokenAuthentication>  
   </serviceCredentials>  
  </behavior>  
 </serviceBehaviors>  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.KnownCertificates%2A>  
 <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElementCollection>  
 <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement>  
 <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A>  
 [\<knownCertificates >](../../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md)  
 [Trabalhando com certificados](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [Federação e tokens emitidos](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [Como configurar as credenciais em um Serviço de Federação](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)  
 [Protegendo serviços e clientes](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
