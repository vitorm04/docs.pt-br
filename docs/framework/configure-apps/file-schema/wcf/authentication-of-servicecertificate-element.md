---
title: <authentication> de <serviceCertificate> elemento
ms.date: 03/30/2017
ms.assetid: 733b67b4-08a1-4d25-9741-10046f9357ef
ms.openlocfilehash: 8288e530d0164b41a6cf53cc39385a2d29fdb091
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55255166"
---
# <a name="authentication-of-servicecertificate-element"></a>\<autenticação > de \<serviceCertificate > elemento
Especifica as configurações usadas pelo proxy do cliente para autenticar certificados de serviço que são obtidos usando negociação SSL/TLS.  
  
 \<system.ServiceModel>  
\<comportamentos >  
seção endpointBehaviors  
\<behavior>  
\<clientCredentials>  
\<serviceCertificate>  
\<autenticação >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<authentication customCertificateValidatorType="String"
                certificateValidationMode="None/PeerTrust/ChainTrust/PeerOrChainTrust/Custom"
                revocationMode="NoCheck/Online/Offline"
                trustedStoreLocation="LocalMachine/CurrentUser" />
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|customCertificateValidatorType|Cadeia. Um tipo e assembly usados para validar um tipo personalizado.|  
|certificateValidationMode|Especifica um dos três modos usados para validar as credenciais. Se definido como `Custom`, em seguida, também deverá ser fornecido um customCertificateValidator. O padrão é `ChainTrust`.|  
|revocationMode|Um dos modos usados para verificar por listas de certificados revogados (CRL). O padrão é `Online`.|  
|trustedStoreLocation|Um dos locais de armazenamento de sistema de dois: `LocalMachine` ou `CurrentUser`. Esse valor é usado quando um certificado de serviço é negociado ao cliente. Validação é executada em relação a **pessoas confiáveis** armazenar no local de repositório especificado. O padrão é `CurrentUser`.|  
  
## <a name="customcertificatevalidator-attribute"></a>customCertificateValidator atributo  
  
|Valor|Descrição|  
|-----------|-----------------|  
|Cadeia de Caracteres|Especifica o nome do tipo e assembly e outros dados usados para localizar o tipo.|  
  
## <a name="certificatevalidationmode-attribute"></a>certificateValidationMode atributo  
  
|Valor|Descrição|  
|-----------|-----------------|  
|Enumeração|Um dos seguintes valores: Nenhum, PeerTrust, ChainTrust, PeerOrChainTrust, personalizado.<br /><br /> Para obter mais informações, consulte [trabalhando com certificados](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).|  
  
## <a name="revocationmode-attribute"></a>revocationMode atributo  
  
|Valor|Descrição|  
|-----------|-----------------|  
|Enumeração|Um dos seguintes valores: NoCheck, Online, Offline.<br /><br /> Para obter mais informações, consulte [trabalhando com certificados](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).|  
  
## <a name="trustedstorelocation-attribute"></a>trustedStoreLocation atributo  
  
|Valor|Descrição|  
|-----------|-----------------|  
|Enumeração|Um dos seguintes valores: LocalMachine ou CurrentUser. O padrão é CurrentUser. Se o aplicativo cliente é executado sob uma conta do sistema, em seguida, o certificado é normalmente em LocalMachine. Se o aplicativo cliente está em execução em uma conta de usuário, em seguida, o certificado é normalmente em CurrentUser.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<serviceCertificate>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md)|Especifica um certificado a ser usado ao autenticar um serviço para o cliente.|  
  
## <a name="remarks"></a>Comentários  
 O `certificateValidationMode` atributo desse elemento de configuração especifica o nível de confiança usado para autenticar certificados. Por padrão, o nível é definido como `ChainTrust`, que especifica que cada certificado deve ser localizado em uma hierarquia de certificados terminam em uma autoridade de certificação confiável na parte superior da cadeia. Este é o modo mais seguro. Você também pode definir o valor `PeerOrChainTrust`, que especifica que os certificados emitidos por conta própria (confiança de par) são aceitos, bem como certificados que estão em uma cadeia confiável. Esse valor é usado ao desenvolver e depurar clientes e serviços, porque os certificados emitidos por conta própria não precisam ser adquiridos de uma autoridade confiável. Ao implantar um cliente, use o `ChainTrust` valor em vez disso. Você também pode definir o valor `Custom` ou `None`. Para usar o valor `Custom`, você também deverá definir o atributo `customCertificateValidator` para um assembly e um tipo usados para validar o certificado. Para criar seu próprio validador personalizado, você deve herdar da classe abstrata X509CertificateValidator. Para obter mais informações, confira [Como: Criar um serviço que utiliza um validador de certificado personalizado](../../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).  
  
 O `revocationMode` atributo especifica como os certificados são verificados para revogação. O padrão é `online` que indica que certificados serão verificados automaticamente para revogação. Para obter mais informações, consulte [trabalhando com certificados](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir executa duas tarefas. Especifica um certificado de serviço para o cliente a ser usado ao se comunicar com pontos de extremidade cujo nome de domínio é primeiro `www.contoso.com` através do protocolo HTTP. Em segundo lugar, ele especifica o local de modo e o repositório de revogação usado durante a autenticação.  
  
```xml  
<serviceCertificate>
  <defaultCertificate findValue="www.contoso.com"
                      storeLocation="LocalMachine"
                      storeName="TrustedPeople"
                      x509FindType="FindByIssuerDistinguishedName" />
  <scopedCertificates>
     <add targetUri="http://www.contoso.com"
          findValue="www.contoso.com"
          storeLocation="LocalMachine"
          storeName="Root"
          x509FindType="FindByIssuerName" />
  </scopedCertificates>
  <authentication revocationMode="Online"
                  trustedStoreLocation="LocalMachine" />
</serviceCertificate>
```  
  
## <a name="see-also"></a>Consulte também
- <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.Authentication%2A>
- <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication>
- [Comportamentos de segurança](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [Trabalhando com certificados](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [Como: Criar um serviço que utiliza um validador de certificado personalizado](../../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)
- [\<authentication>](../../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md)
- [Protegendo clientes](../../../../../docs/framework/wcf/securing-clients.md)
- [Protegendo serviços e clientes](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
