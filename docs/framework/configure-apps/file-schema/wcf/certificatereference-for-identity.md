---
title: <certificateReference> para <identity>
ms.date: 03/30/2017
ms.assetid: ac359c65-c22d-42d2-97de-db53b77cebdb
ms.openlocfilehash: 3b7779ac00c2fca6300c12ac18ff2d5f6b868424
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59138801"
---
# <a name="certificatereference-for-identity"></a>\<certificateReference > para \<identidade >
Especifica configurações para validação de certificado X.509. Um cliente seguro do Windows Communication Foundation (WCF) que se conecta a um ponto de extremidade com esta identidade verifica que as declarações apresentadas pelo servidor contêm a declaração de identidade usada para construir essa identidade.  
  
 \<identity>  
\<certificateReference>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<certificateReference findValue="String"
                      isChainIncluded="Boolean"
                      storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                      storeLocation="LocalMachine/CurrentUser"
                      X509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier">
</certificateReference>
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|findValue|Especifica o valor a ser pesquisado no repositório de certificados x. 509. O tipo contido nesse atributo deve satisfazer os requisitos de especificado `X509FindType` valor. O padrão é uma cadeia de caracteres vazia.|  
|isChainIncluded|Um valor booliano que especifica se a validação é feita usando uma cadeia de certificados.|  
|storeLocation|Especifica o local do repositório de certificados que o cliente pode usar para validar o certificado do servidor.<br /><br /> Os valores válidos incluem o seguinte:<br /><br /> -LocalMachine: O repositório de certificados atribuído ao computador local.<br />-CurrentUser: O repositório de certificados atribuído ao usuário atual.<br /><br /> O valor padrão é LocalMachine.<br /><br /> Esse atributo é do tipo <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.|  
|storeName|Especifica o nome do repositório de certificados X.509 a ser aberto.<br /><br /> Os valores válidos incluem o seguinte:<br /><br /> -Catálogo de endereços: Repositório de certificados para outros usuários.<br />-AuthRoot: Repositório de certificados para autoridades de certificação de terceiros (CAs).<br />-CertificateAuthority: Repositório de certificados para autoridades de certificação intermediárias.<br />– Não permitido: Repositório de certificados para certificados revogados.<br />-Minha: Repositório de certificados para certificados pessoais.<br />-Raiz: Repositório de certificados para autoridades de certificação de raiz confiável.<br />-TrustedPeople: Repositório de certificados para recursos e pessoas diretamente confiáveis.<br />-   TrustedPublisher: Repositório de certificados para editores diretamente confiáveis.<br /><br /> O valor padrão é meu.<br /><br /> Esse atributo é do tipo <xref:System.Security.Cryptography.X509Certificates.StoreName>.|  
|X509FindType|Especifica o tipo de pesquisa X.509 a ser executado. O tipo contido a `findValue` atributo deve satisfazer os requisitos do X509FindType especificado.<br /><br /> Os valores válidos incluem o seguinte:<br /><br /> -   FindByThumbPrint<br />-FindBySubjectName<br />-FindBySubjectDistinguishedName<br />-FindByIssuerName<br />-FindByIssuerDistinguishedName<br />-   FindBySerialNumber<br />-   FindByTimeValid<br />-   FindByTimeNotYetValid<br />-   FindByTemplateName<br />-   FindByApplicationPolicy<br />-   FindByCertificatePolicy<br />-FindByExtension<br />-   FindByKeyUsage<br />-   FindBySubjectKeyIdentifier<br /><br /> O valor padrão é FindBySubjectDistinguishedName.<br /><br /> Esse atributo é do tipo <xref:System.Security.Cryptography.X509Certificates.X509FindType>.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<identity>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|Especifica configurações que habilitam a autenticação de um ponto de extremidade por outros pontos de extremidade trocando mensagens com ele.|  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Configuration.CertificateReferenceElement>
- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
