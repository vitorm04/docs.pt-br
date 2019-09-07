---
title: <clientCertificate>do <clientCredentials> elemento
ms.date: 03/30/2017
ms.assetid: 3b3fa000-3434-4142-a178-11903bdd2c5d
ms.openlocfilehash: fb95ef3168378227e41e55c6fd5e5b772cb7ad0f
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400512"
---
# <a name="clientcertificate-of-clientcredentials-element"></a>\<clientCertificate > do \<elemento ClientCredentials >
Define um certificado X. 509 usado para autenticar um cliente para um serviço.  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportamentos >** ](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> endpointBehaviors**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportamento**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<clientCredentials >** ](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> clientCertificate**  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<clientCertificate findValue="String"
                   storeLocation="LocalMachine/CurrentUser"
                   storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                   X509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`findValue`|Uma cadeia de caracteres que contém o valor a ser procurado no repositório de certificados X. 509. O tipo contido no atributo deve atender aos requisitos do valor do `X509FindType` atributo. O padrão é uma cadeia de caracteres vazia.|  
|`storeLocation`|Especifica o local do certificado X. 509 que o cliente usa para se autenticar no serviço. Os valores válidos incluem o seguinte:<br /><br /> -LocalMachine: o repositório de certificados atribuído ao computador local.<br />-CurrentUser: o repositório de certificados atribuído ao usuário atual.<br /><br /> O padrão é LocalMachine. Esse atributo é do tipo <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.|  
|`storeName`|Especifica o nome do repositório de certificados X. 509 a ser pesquisado. Os valores válidos incluem o seguinte:<br /><br /> Catálogo Repositório de certificados para outros usuários.<br />- AuthRoot: Repositório de certificados para CAs (autoridades de certificação) de terceiros.<br />CertificateAuthority Repositório de certificados para CAs (autoridades de certificação) intermediárias.<br />Permitida Repositório de certificados para certificados revogados.<br />Pasta Repositório de certificados para certificados pessoais.<br />Básica Repositório de certificados para autoridades de certificação raiz confiáveis (CAs).<br />TrustedPeople Repositório de certificados para pessoas e recursos diretamente confiáveis.<br />- TrustedPublisher: Repositório de certificados para editores diretamente confiáveis.<br /><br /> O padrão é My. Esse atributo é do tipo <xref:System.Security.Cryptography.X509Certificates.StoreName>.|  
|X509FindType|Define o tipo de pesquisa de X.509 a ser executada. O tipo contido no `findValue` atributo deve atender aos requisitos deste atributo. Os valores válidos incluem o seguinte:<br /><br /> -   FindByThumbPrint<br />-FindBySubjectName<br />- FindBySubjectDistinguishedName<br />- FindByIssuerName<br />- FindByIssuerDistinguishedName<br />-   FindBySerialNumber<br />- FindByTimeValid<br />-   FindByTimeNotYetValid<br />-   FindByTemplateName<br />- FindByApplicationPolicy<br />- FindByCertificatePolicy<br />- FindByExtension<br />-   FindByKeyUsage<br />-   FindBySubjectKeyIdentifier<br /><br /> O valor padrão é FindBySubjectDistinguishedName. Esse atributo é do tipo <xref:System.Security.Cryptography.X509Certificates.X509FindType>.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<clientCredentials>](clientcredentials.md)|Especifica as credenciais usadas para autenticar o cliente para um serviço.|  
  
## <a name="remarks"></a>Comentários  
 Este elemento de configuração especifica o certificado usado para autenticar o cliente com este elemento. Para obter mais informações, confira [Como: Especifique os valores](../../../wcf/how-to-specify-client-credential-values.md)de credencial do cliente.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.ClientCertificate%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.ClientCertificate%2A>
- <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>
- <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential>
- [Comportamentos de segurança](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [Como: Especificar valores de credenciais de cliente](../../../wcf/how-to-specify-client-credential-values.md)
- [Protegendo clientes](../../../wcf/securing-clients.md)
- [Trabalhando com certificados](../../../wcf/feature-details/working-with-certificates.md)
- [Protegendo serviços e clientes](../../../wcf/feature-details/securing-services-and-clients.md)
