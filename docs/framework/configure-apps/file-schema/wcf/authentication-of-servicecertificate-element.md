---
title: '&lt;autenticação&gt; do elemento &lt;serviceCertificate&gt;'
ms.date: 03/30/2017
ms.assetid: 733b67b4-08a1-4d25-9741-10046f9357ef
ms.openlocfilehash: 9ef17c8bedf6bcef21a7c59d98a86bb20ad2da80
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltauthenticationgt-of-ltservicecertificategt-element"></a>&lt;autenticação&gt; do elemento &lt;serviceCertificate&gt;
Especifica as configurações usadas pelo proxy do cliente para autenticar certificados de serviço que são obtidos usando negociação SSL/TLS.  
  
 \<system.ServiceModel>  
\<comportamentos >  
seção endpointBehaviors  
\<comportamento >  
\<clientCredentials>  
\<serviceCertificate >  
\<autenticação >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<authentication customCertificateValidatorType="String" certificateValidationMode="None/PeerTrust/ChainTrust/PeerOrChainTrust/Custom"  
revocationMode="NoCheck/Online/Offline"   
trustedStoreLocation="LocalMachine/CurrentUser" />  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem os elementos pai de atributos e elementos filho  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|customCertificateValidatorType|Cadeia. Um tipo e assembly usados para validar um tipo personalizado.|  
|certificateValidationMode|Especifica um dos três modos usados para validar credenciais. Se definido como `Custom`, em seguida, customCertificateValidator também deve ser fornecido. O padrão é `ChainTrust`.|  
|revocationMode|Um dos modos usados para verificar por listas de certificados revogados (CRL). O padrão é `Online`.|  
|trustedStoreLocation|Um dos locais de armazenamento de sistema de dois: `LocalMachine` ou `CurrentUser`. Esse valor é usado quando um certificado de serviço é negociado ao cliente. A validação é executada em relação a **pessoas confiáveis** armazenar no local de armazenamento especificado. O padrão é `CurrentUser`.|  
  
## <a name="customcertificatevalidator-attribute"></a>customCertificateValidator atributo  
  
|Valor|Descrição|  
|-----------|-----------------|  
|Cadeia de Caracteres|Especifica o nome do tipo e assembly e outros dados usados para localizar o tipo.|  
  
## <a name="certificatevalidationmode-attribute"></a>certificateValidationMode atributo  
  
|Valor|Descrição|  
|-----------|-----------------|  
|Enumeração|Um dos seguintes valores: None, PeerTrust, ChainTrust, PeerOrChainTrust, personalizado.<br /><br /> Para obter mais informações, consulte [trabalhar com certificados](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).|  
  
## <a name="revocationmode-attribute"></a>revocationMode atributo  
  
|Valor|Descrição|  
|-----------|-----------------|  
|Enumeração|Um dos seguintes valores: NoCheck, Online, Offline.<br /><br /> Para obter mais informações, consulte [trabalhar com certificados](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).|  
  
## <a name="trustedstorelocation-attribute"></a>trustedStoreLocation atributo  
  
|Valor|Descrição|  
|-----------|-----------------|  
|Enumeração|Um dos valores seguintes: LocalMachine ou CurrentUser. O padrão é CurrentUser. Se o aplicativo cliente é executado sob uma conta de sistema, em seguida, o certificado é geralmente em LocalMachine. Se o aplicativo cliente é executado sob uma conta de usuário, em seguida, o certificado é geralmente em CurrentUser.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<serviceCertificate >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md)|Especifica um certificado a ser usado ao autenticar um serviço para o cliente.|  
  
## <a name="remarks"></a>Comentários  
 O `certificateValidationMode` atributo desse elemento de configuração especifica o nível de confiança usado para autenticar certificados. Por padrão, o nível é definido como `ChainTrust`, que especifica que cada certificado deve ser encontrado em uma hierarquia de certificados terminam em uma autoridade de certificação confiável na parte superior da cadeia. Este é o modo mais seguro. Você também pode definir o valor `PeerOrChainTrust`, que especifica que os certificados emitidos por conta própria (confiança ponto a ponto) são aceitos, bem como certificados que estão em uma cadeia confiável. Esse valor é usado durante o desenvolvimento e depuração clientes e serviços, pois os certificados emitidos por conta própria não precisam ser adquiridos de uma autoridade confiável. Ao implantar um cliente, use o `ChainTrust` valor em vez disso. Você também pode definir o valor `Custom` ou `None`. Para usar o valor `Custom`, você também deverá definir o atributo `customCertificateValidator` para um assembly e um tipo usados para validar o certificado. Para criar seu próprios validador personalizado, você deve herdar da classe abstrata X509CertificateValidator. Para obter mais informações, consulte [como: criar um serviço que utiliza um validador de certificado personalizado](../../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).  
  
 O `revocationMode` atributo especifica como os certificados são verificados para revogação. O padrão é `online` que indica que certificados serão verificados automaticamente para revogação. Para obter mais informações, consulte [trabalhar com certificados](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir executa duas tarefas. Especifica um certificado de serviço para o cliente usar ao se comunicar com pontos de extremidade cujo nome de domínio é www.contoso.com através do protocolo HTTP pela primeira vez. Em segundo lugar, ele especifica o local de modo e repositório de revogação usado durante a autenticação.  
  
```xml  
<serviceCertificate>  
  <defaultCertificate findValue="www.contoso.com"   
                      storeLocation="LocalMachine"  
                      storeName="TrustedPeople"   
                      x509FindType="FindByIssuerDistinguishedName" />  
  <scopedCertificates>  
     <add targetUri="http://www.contoso.com"   
          findValue="www.contoso.com" storeLocation="LocalMachine"  
                  storeName="Root" x509FindType="FindByIssuerName" />  
  </scopedCertificates>  
  <authentication revocationMode="Online"   
   trustedStoreLocation="LocalMachine" />  
</serviceCertificate>  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.Authentication%2A>  
 <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication>  
 [Comportamentos de segurança](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [Trabalhando com certificados](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [Como criar um serviço que utiliza um validador de certificado personalizado](../../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)  
 [\<authentication>](../../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md)  
 [Protegendo clientes](../../../../../docs/framework/wcf/securing-clients.md)  
 [Protegendo serviços e clientes](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
