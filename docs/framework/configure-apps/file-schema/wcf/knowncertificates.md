---
title: <knownCertificates>
ms.date: 03/30/2017
ms.assetid: 678e21b4-6493-47c3-8359-fcf0d37e2138
ms.openlocfilehash: 7ddb292b8f0ffe38133c7f142be751a87d2be11c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91150902"
---
# \<knownCertificates>

Representa uma coleção de certificados X. 509 que são fornecidos para autenticar credenciais de segurança emitidas de um serviço de token de segurança (STS).  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenAuthentication>**](issuedtokenauthentication-of-servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<knownCertificates>**  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<knownCertificates>
  <add findValue="String"
       storeLocation="CurrentUser/LocalMachine"
       storeName=" CurrentUser/LocalMachine"
       x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
</knownCertificates>
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  

 As seções a seguir descrevem atributos, elementos filho e elementos pai  
  
### <a name="attributes"></a>Atributos  

 Nenhum.  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<add>](add-of-knowncertificates.md)|Adiciona um certificado X. 509 à coleção.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md)|Especifica um token emitido como uma credencial de serviço.|  
  
## <a name="remarks"></a>Comentários  

 O cenário de token emitido tem três estágios. No primeiro estágio, um cliente que tenta acessar um serviço é chamado de um *serviço de token seguro*. O serviço de token seguro autentica o cliente e subsequentemente emite um token do cliente, normalmente um token SAML (Security Assertion Markup Language). O cliente retorna ao serviço com o token. O serviço examina o token de dados que permite que o serviço autentique o token e, portanto, o cliente. Para autenticar o token, o certificado que o serviço de token seguro usa deve ser conhecido pelo serviço.  
  
 O [\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md) elemento é o repositório para qualquer certificado de serviço de token seguro. Para adicionar certificados, use o [ \<knownCertificates> elemento](knowncertificates.md). Insira um [\<add>](add-of-knowncertificates.md) para cada certificado, conforme mostrado no exemplo a seguir.  
  
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
  
 Por padrão, os certificados devem ser obtidos de um serviço de token seguro. Esses certificados "conhecidos" garantem que somente clientes legítimos possam acessar um serviço.  
  
 Para revisar as condições necessárias para um cliente ser autenticado por um serviço federado, bem como mais informações sobre como usar esse elemento de configuração, consulte [como configurar credenciais em um serviço de Federação](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md). Para obter mais informações sobre cenários federados, consulte [Federação e tokens emitidos](../../../wcf/feature-details/federation-and-issued-tokens.md).  
  
 Para obter um exemplo que mostra como preencher a coleção na configuração, consulte [\<add>](add-of-knowncertificates.md) .  
  
## <a name="see-also"></a>Confira também

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.KnownCertificates%2A>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElementCollection>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A>
- [\<add>](add-of-knowncertificates.md)
- [\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md)
- [Comportamentos de segurança](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [Como: configurar credenciais em um serviço de federação](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
- [Trabalhando com certificados](../../../wcf/feature-details/working-with-certificates.md)
- [Federação e tokens emitidos](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [\<add>](add-of-knowncertificates.md)
- [Protegendo serviços e clientes](../../../wcf/feature-details/securing-services-and-clients.md)
