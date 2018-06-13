---
title: '&lt;certificateReference&gt; para &lt;identidade&gt;'
ms.date: 03/30/2017
ms.assetid: ac359c65-c22d-42d2-97de-db53b77cebdb
ms.openlocfilehash: 7c2ac27d547cdea959cca2ca4a0ffc9c9282c20d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32747636"
---
# <a name="ltcertificatereferencegt-for-ltidentitygt"></a>&lt;certificateReference&gt; para &lt;identidade&gt;
Especifica configurações para validação do certificado x. 509. Um cliente seguro do Windows Communication Foundation (WCF) que se conecta a um ponto de extremidade com esta identidade verifica que as declarações apresentadas pelo servidor contém a declaração de identidade usada para construir essa identidade.  
  
 \<identidade >  
\<certificateReference >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<certificateReference   
        findValue="String"   
    isChainIncluded="Boolean"  
    storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"storeName="  
  
    storeLocation="LocalMachine/CurrentUser"  
  
X509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"  
</certificateReference>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|findValue|Especifica o valor para pesquisar no repositório de certificados x. 509. O tipo contido esse atributo deve satisfazer os requisitos de especificado `X509FindType` valor. O padrão é uma cadeia de caracteres vazia.|  
|isChainIncluded|Um valor booleano que especifica se a validação é feita usando uma cadeia de certificados.|  
|storeLocation|Especifica o local do repositório de certificados que o cliente pode usar para validar o certificado do servidor.<br /><br /> Os valores válidos incluem o seguinte:<br /><br /> -LocalMachine: O repositório de certificados atribuído ao computador local.<br />-CurrentUser: O repositório de certificados atribuído ao usuário atual.<br /><br /> O valor padrão é LocalMachine.<br /><br /> Esse atributo é do tipo <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.|  
|storeName|Especifica o nome do repositório de certificados X.509 a ser aberto.<br /><br /> Os valores válidos incluem o seguinte:<br /><br /> -Catálogo de endereços: O repositório de certificados para outros usuários.<br />-AuthRoot: Repositório de autoridades de certificação de terceiros (ACS) do certificado.<br />-CertificateAuthority: Repositório de certificados de autoridades de certificação intermediárias.<br />-Proibido: Repositório de certificados revogados de certificados.<br />-My: Repositório de certificados pessoais do certificado.<br />-Root: Repositório de autoridades de certificação de raiz confiável do certificado.<br />-TrustedPeople: Repositório de certificados pessoas confiáveis diretamente e recursos.<br />-TrustedPublisher: Repositório de certificados para editores diretamente confiáveis.<br /><br /> O valor padrão é meu.<br /><br /> Esse atributo é do tipo <xref:System.Security.Cryptography.X509Certificates.StoreName>.|  
|X509FindType|Especifica o tipo de pesquisa x. 509 a ser executado. O tipo contido o `findValue` atributo deve satisfazer os requisitos do X509FindType especificado.<br /><br /> Os valores válidos incluem o seguinte:<br /><br /> -   FindByThumbPrint<br />-FindBySubjectName<br />-FindBySubjectDistinguishedName<br />-FindByIssuerName<br />-FindByIssuerDistinguishedName<br />-FindBySerialNumber<br />-FindByTimeValid<br />-   FindByTimeNotYetValid<br />-FindByTemplateName<br />-FindByApplicationPolicy<br />-FindByCertificatePolicy<br />-FindByExtension<br />-FindByKeyUsage<br />-FindBySubjectKeyIdentifier<br /><br /> O valor padrão é FindBySubjectDistinguishedName.<br /><br /> Esse atributo é do tipo <xref:System.Security.Cryptography.X509Certificates.X509FindType>.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<identity>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|Especifica configurações que permitem a autenticação de um ponto de extremidade por outros pontos de extremidade de troca de mensagens com ele.|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Configuration.CertificateReferenceElement>  
 <xref:System.ServiceModel.Configuration.IdentityElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.EndpointAddress.Identity%2A>
