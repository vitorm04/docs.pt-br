---
title: Elemento &lt;defaultCertificate&gt;
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f1ddf364-9a00-45d3-b989-ff381c154ce6
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4424b8b5e0389c0a0395550fddb71ac34e0fb987
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ltdefaultcertificategt-element"></a>Elemento &lt;defaultCertificate&gt;
Especifica um certificado x. 509 a ser usado quando um serviço ou STS não fornece um através de um protocolo de negociação.  
  
 \<sistema. ServiceModel >  
\<comportamentos >  
seção endpointBehaviors  
\<comportamento >  
\<clientCredentials >  
\<serviceCertificate >  
\<defaultCertificate >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<defaultCertificate findValue="String"   
storeLocation=" CurrentUser/LocalMachine"  
storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"   
x509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialiNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem os elementos pai de atributos e elementos filho  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|findValue|Cadeia. O valor a ser procurado.|  
|X509FindType|Enumeração. Um dos campos de certificado a ser pesquisado.|  
|storeLocation|Enumeração. Um sistema de dois locais de repositório para pesquisar.|  
|storeName|Enumeração. Um dos repositórios de sistema para pesquisar.|  
  
## <a name="findvalue-attribute"></a>findValue atributo  
  
|Valor|Descrição|  
|-----------|-----------------|  
|Cadeia de caracteres|O valor depende do campo (especificado pelo atributo X509FindType) que está sendo pesquisado. Por exemplo, se você está procurando uma impressão digital, o valor deve ser uma cadeia de caracteres de números hexadecimais.|  
  
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
|[\<serviceCertificate >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md)|Especifica um certificado a ser usado ao autenticar um serviço para o cliente.|  
  
## <a name="remarks"></a>Comentários  
 Para associações que usam a segurança de mensagens baseada em certificado, o certificado especificado por este elemento de configuração é usado para criptografar mensagens para o serviço e deve ser usada pelo serviço para assinar respostas ao cliente. Ele armazena um único certificado a ser usado quando nenhum certificado é especificado por um serviço.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir especifica um certificado a ser usado para pontos de extremidade cujo URI começa com http://www.contoso.com e um certificado a ser usado para todos os outros pontos de extremidade que não executam a negociação do certificado.  
  
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
 <xref:System.ServiceModel.Configuration.X509DefaultServiceCertificateElement>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.DefaultCertificate%2A>  
 [Trabalhar com certificados](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [\<autenticação >](../../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md)  
 [Securing Clients](../../../../../docs/framework/wcf/securing-clients.md) (Protegendo clientes)  
 [Protegendo serviços e clientes](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
