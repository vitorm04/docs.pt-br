---
title: <issuedTokenAuthentication> De <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: 5c2e288f-f603-4d13-839a-0fd6d1981bec
ms.openlocfilehash: c195791250831897b8bc9d09782d17609272e146
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55260275"
---
# <a name="issuedtokenauthentication-of-servicecredentials"></a>\<issuedTokenAuthentication > de \<serviceCredentials >
Especifica um token personalizado emitido como uma credencial de serviço.  
  
 \<system.ServiceModel>  
\<comportamentos >  
\<serviceBehaviors>  
\<behavior>  
\<serviceCredentials>  
\<issuedTokenAuthentication>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<issuedTokenAuthentication allowUntrustedRsaIssuers="Boolean"
                           audienceUriMode="Always/BearerKeyOnly/Never"
                           customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                           certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                           revocationMode="NoCheck/Online/Offline"
                           samlSerializer="String"
                           trustedStoreLocation="CurrentUser/LocalMachine">
  <allowedAudienceUris>
    <add allowedAudienceUri="String" />
  </allowedAudienceUris>
  <knownCertificates>
    <add findValue="String"
         storeLocation="CurrentUser/LocalMachine"
         storeName=" CurrentUser/LocalMachine"
         x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
  </knownCertificates>
</issuedTokenAuthentication>
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`allowedAudienceUris`|Obtém o conjunto de URIs de destino para o qual o <xref:System.IdentityModel.Tokens.SamlSecurityToken> token de segurança pode ser direcionado para ser considerado válido por um <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instância. Para obter mais informações sobre como usar esse atributo, consulte <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>.|  
|`allowUntrustedRsaIssuers`|Um valor booliano que especifica se emissores de certificados RSA não confiáveis são permitidos.<br /><br /> Os certificados são assinados por autoridades de certificação (CAs) para verificar autenticidade. Um emissor não confiável é uma autoridade de certificação não for especificada para ser confiável para assinar certificados.|  
|`audienceUriMode`|Obtém um valor que especifica se o <xref:System.IdentityModel.Tokens.SamlSecurityToken> do token de segurança <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> deve ser validado. Esse valor é do tipo <xref:System.IdentityModel.Selectors.AudienceUriMode>. Para obter mais informações sobre como usar esse atributo, consulte <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>.|  
|`certificateValidationMode`|Define o modo de validação de certificado. Um dos valores válidos de <xref:System.ServiceModel.Security.X509CertificateValidationMode>. Se definido como `Custom`, em seguida, um `customCertificateValidator` também deve ser fornecido. O padrão é `ChainTrust`.|  
|`customCertificateValidatorType`|Cadeia de caracteres opcional. Um tipo e assembly usados para validar um tipo personalizado. Esse atributo deve ser definido quando `certificateValidationMode` é definido como `Custom`.|  
|`revocationMode`|Define o modo de revogação que especifica se uma verificação de revogação ocorre e se ela é executada online ou offline. Esse atributo é do tipo <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.|  
|`samlSerializer`|Um atributo de cadeia de caracteres opcional que especifica o tipo de classe SamlSerializer que é usado para a credencial de serviço. O padrão é uma cadeia de caracteres vazia.|  
|`trustedStoreLocation`|Enumeração opcional. Um dos locais de armazenamento de sistema de dois: `LocalMachine` ou `CurrentUser`.|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`knownCertificates`|Especifica uma coleção de <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement> elementos que especifica os emissores confiáveis para a credencial de serviço.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<serviceCredentials>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|Especifica a credencial a ser usado na autenticação do serviço e as configurações de relacionadas à validação de credenciais do cliente.|  
  
## <a name="remarks"></a>Comentários  
 O cenário de token emitido tem três etapas. O primeiro estágio, um cliente tentar acessar um serviço é chamado um *serviço de token seguro*. O serviço de token seguro, em seguida, autentica o cliente e emite subsequentemente um token, normalmente um token de segurança asserções SAML (Markup Language) para o cliente. O cliente, em seguida, retorne para o serviço com o token. O serviço examina o token para os dados que permite que o serviço autenticar o token e, portanto, o cliente. Para autenticar o token, o certificado usa o serviço de token seguro deve ser conhecida para o serviço.  
  
 Esse elemento é o repositório para todos esses certificados de serviço de token seguro. Para adicionar certificados, use o [ \<knownCertificates >](../../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md). Inserir uma [ \<Adicionar >](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md) para cada certificado, conforme mostrado no exemplo a seguir.  
  
```xml  
<issuedTokenAuthentication>
  <knownCertificates>
    <add findValue="www.contoso.com"
         storeLocation="LocalMachine"
         storeName="My"
         X509FindType="FindBySubjectName" />
  </knownCertificates>
</issuedTokenAuthentication>
```  
  
 Por padrão, os certificados devem ser obtidos de um serviço de token seguro. Esses "conhecidos" certificados Certifique-se de que apenas legítimas os clientes podem acessar um serviço.  
  
 Para obter mais informações sobre como usar este elemento de configuração, consulte [como: Configurar credenciais em um serviço de Federação](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).  
  
## <a name="see-also"></a>Consulte também
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.IssuedTokenAuthentication%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>
- <xref:System.ServiceModel.Description.ServiceCredentials.IssuedTokenAuthentication%2A>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential>
- [Protegendo serviços e clientes](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [Como: Configurar credenciais em um serviço de Federação](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
