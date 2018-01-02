---
title: '&lt;certificateReference&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2ac8bc14-e9f1-48fb-b662-f5991558fbe4
caps.latest.revision: "4"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: fd0d4742a162000d438851cef9c00e21368b7ba1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltcertificatereferencegt"></a>&lt;certificateReference&gt;
Especifica configurações que são usadas para encontrar e validar um certificado x. 509 em um repositório de certificados.  
  
 \<System >  
\<federationConfiguration >  
\<serviceCertificate >  
\<certificateReference >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <serviceCertificate>  
      <certificateReference   
        storeName="AddressBook||AuthRoot||CertificateAuthority||Disallowed||My||Root||TrustedPeople||TrustedPublisher"  
        storeLocation="CurrentUser||LocalMachine"  
        x509FindType="FindByThumbprint||FindBySubjectName||FindBySubjectDistinguishedName||FindByIssuerName||FindByIssuerDistinguishedName||FindBySerialNumber||FindByTimeValid||FindByTimeNotYetValid||FindByTimeExpired||FindByTemplateName||FindByApplicationPolicy||FindByCertificatePolicy||FindByExtension||FindByKeyUsage||FindBySubjectKeyIdentifier"  
        findValue=xs:String  
        isChainIncluded=xs:Boolean >  
      </certificateReference>  
    </serviceCertificate>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|storeName|O nome do repositório de certificados X.509. O padrão é "My". Opcional.|  
|storeLocation|Um <xref:System.Security.Cryptography.X509Certificates.StoreLocation> valor que especifica o local do repositório de certificados x. 509. O valor padrão é "LocalMachine". Opcional.|  
|X509FindType|Um <xref:System.Security.Cryptography.X509Certificates.X509FindType> valor que especifica o tipo de pesquisa a ser executado. O padrão é "FindBySubjectDistinguishedName". Opcional.|  
|findValue|O valor a ser pesquisado no repositório de certificados X.509. Opcional.|  
|isChainIncluded|Especifica se a validação deve ser executada usando a cadeia de certificados. O padrão é "true"; a validação é executada usando a cadeia de certificados. Opcional.|  
  
### <a name="child-elements"></a>Elementos filho  
 Nenhum  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<serviceCertificate >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/servicecertificate.md)|Configura o certificado usado para criptografar e descriptografar tokens.|  
  
## <a name="remarks"></a>Comentários  
 O `<certificateReference>` elemento Especifica configurações que são usadas para localizar e validar um certificado x. 509 em um repositório de certificados. Quando ele é especificado como o elemento filho de `<serviceCertficate>` elemento, especifica as configurações de local e a verificação do certificado x. 509 que é usada para criptografar e descriptografar tokens. O `<certificateReference>` elemento é representado pela <xref:System.ServiceModel.Configuration.CertificateReferenceElement> classe.
