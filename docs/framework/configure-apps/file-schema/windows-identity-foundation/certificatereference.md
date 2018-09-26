---
title: '&lt;CertificateReference&gt;'
ms.date: 03/30/2017
ms.assetid: 2ac8bc14-e9f1-48fb-b662-f5991558fbe4
author: BrucePerlerMS
ms.openlocfilehash: e04dc90134aadfb8af7b0800c7144963d267f513
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47206885"
---
# <a name="ltcertificatereferencegt"></a>&lt;CertificateReference&gt;
Especifica configurações que são usadas para encontrar e validar um certificado x. 509 em um repositório de certificados.  
  
 \<IdentityModel >  
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
|storeLocation|Um <xref:System.Security.Cryptography.X509Certificates.StoreLocation> valor que especifica o local do repositório de certificados X.509. O valor padrão é "LocalMachine". Opcional.|  
|x509FindType|Um <xref:System.Security.Cryptography.X509Certificates.X509FindType> valor que especifica o tipo de pesquisa a ser executado. O padrão é "FindBySubjectDistinguishedName". Opcional.|  
|findValue|O valor a ser pesquisado no repositório de certificados X.509. Opcional.|  
|isChainIncluded|Especifica se a validação deve ser executada usando a cadeia de certificados. O padrão é "true"; validação é executada usando a cadeia de certificados. Opcional.|  
  
### <a name="child-elements"></a>Elementos filho  
 Nenhum  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<serviceCertificate >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/servicecertificate.md)|Configura o certificado que é usado para criptografar e descriptografar tokens.|  
  
## <a name="remarks"></a>Comentários  
 O `<certificateReference>` elemento Especifica configurações que são usadas para encontrar e validar um certificado x. 509 em um repositório de certificados. Quando ele é especificado como o elemento filho a `<serviceCertficate>` elemento, ele especifica as configurações de local e a verificação do certificado X.509 que é usado para criptografar e descriptografar tokens. O `<certificateReference>` elemento é representado pelo <xref:System.ServiceModel.Configuration.CertificateReferenceElement> classe.
