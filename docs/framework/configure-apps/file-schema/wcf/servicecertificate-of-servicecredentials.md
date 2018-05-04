---
title: '&lt;serviceCertificate&gt; de &lt;serviceCredentials&gt;'
ms.date: 03/30/2017
ms.assetid: 597ae6d5-4938-4950-9f5e-b2280e816182
ms.openlocfilehash: 3bd6d392b15c37e22fd2a3639c99396e0e3d1749
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltservicecertificategt-of-ltservicecredentialsgt"></a>&lt;serviceCertificate&gt; de &lt;serviceCredentials&gt;
Especifique um certificado x. 509 que será usado para autenticar o serviço para clientes usando o modo de segurança de mensagem.  
  
 \<system.ServiceModel>  
\<comportamentos >  
\<serviceBehaviors >  
\<comportamento >  
\<serviceCredentials>  
\<serviceCertificate >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<serviceCertificate findValue="String"   
    storeLocation="LocalMachine/CurrentUser"  
    storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"  
x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"  
/>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`findValue`|Uma cadeia de caracteres que contém o valor para pesquisar no repositório de certificados x. 509. O tipo contido no atributo deve satisfazer os requisitos do X509FindType especificado. O padrão é uma cadeia de caracteres vazia.|  
|`storeLocation`|Especifica o local do repositório de certificados x. 509 que o cliente usa para validar o certificado do servidor. Os valores válidos incluem o seguinte:<br /><br /> -LocalMachine: o repositório de certificados atribuído ao computador local.<br />-CurrentUser: o repositório de certificados atribuído ao usuário atual.<br /><br /> O padrão é LocalMachine.|  
|`storeName`|Especifica o nome do repositório de certificados X.509 a ser aberto. Os valores válidos incluem o seguinte:<br /><br /> -Catálogo de endereços: O repositório de certificados para outros usuários.<br />-AuthRoot: Repositório de autoridades de certificação de terceiros (ACS) do certificado.<br />-CertificatAuthority: O repositório de certificados para autoridades de certificação intermediárias (CAs).<br />-Proibido: Repositório de certificados revogados de certificados.<br />-My: Repositório de certificados pessoais do certificado.<br />-Raiz: Repositório de certificados (autoridades de certificação de raiz confiável).<br />-TrustedPeople: Repositório de certificados pessoas confiáveis diretamente e recursos.<br />-TrustedPublisher: Repositório de certificados para editores diretamente confiáveis.<br /><br /> O padrão é meu.|  
|`x509FindType`|Define o tipo de pesquisa de X.509 a ser executada. Os valores válidos incluem o seguinte:<br /><br /> -FindByThumbprint<br />-FindBySubjectName<br />-FindBySubjectDistinguishedName<br />-FindByIssuerName<br />-FindByIssuerDistinguishedName<br />-FindBySerialNumber<br />-FindByTimeValid<br />-   FindByTimeNotYetValid<br />-FindByTemplateName<br />-FindByApplicationPolicy<br />-FindByCertificatePolicy<br />-FindByExtension<br />-FindByKeyUsage<br />-FindBySubjectKeyIdentifier<br /><br /> O tipo contido o `findValue` atributo deve satisfazer os requisitos do X509FindType especificado.<br /><br /> O valor padrão é FindBySubjectDistinguishedName.|  
  
### <a name="child-elements"></a>Elementos filho  
 Nenhum  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<serviceCredentials>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|Especifica a credencial a ser usada na autenticação de serviço, e a validação de credencial de cliente as configurações relacionadas.|  
  
## <a name="remarks"></a>Comentários  
 Use esse elemento para especificar um certificado x. 509 que será usado para autenticar o serviço para clientes usando o modo de segurança de mensagem. Se você estiver usando um certificado que será renovado periodicamente, sua impressão digital será alterado. Nesse caso, use o nome da entidade como o `x509FindType` porque o certificado pode ser reemitido com o mesmo nome de assunto.  
  
 Para obter mais informações sobre como usar o elemento, consulte [como: especificar valores de credencial de cliente](../../../../../docs/framework/wcf/how-to-specify-client-credential-values.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>  
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.ServiceCertificate%2A>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential>  
 <xref:System.ServiceModel.Description.ServiceCredentials.ServiceCertificate%2A>  
 [Como especificar valores de credenciais do cliente](../../../../../docs/framework/wcf/how-to-specify-client-credential-values.md)  
 [Comportamentos de segurança](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
