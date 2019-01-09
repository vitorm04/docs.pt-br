---
title: '&lt;serviceCertificate&gt; de &lt;serviceCredentials&gt;'
ms.date: 03/30/2017
ms.assetid: 597ae6d5-4938-4950-9f5e-b2280e816182
ms.openlocfilehash: dfaf02eeaf6de781af70c21321a042de5eff74a5
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54146024"
---
# <a name="ltservicecertificategt-of-ltservicecredentialsgt"></a>&lt;serviceCertificate&gt; de &lt;serviceCredentials&gt;
Especifique um certificado X.509 que será usado para autenticar o serviço para os clientes que usam o modo de segurança de mensagem.  
  
 \<system.ServiceModel>  
\<comportamentos >  
\<serviceBehaviors >  
\<comportamento de >  
\<serviceCredentials>  
\<serviceCertificate >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<serviceCertificate findValue="String"
                    storeLocation="LocalMachine/CurrentUser"
                    storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                    x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`findValue`|Uma cadeia de caracteres que contém o valor a ser pesquisado no repositório de certificados x. 509. O tipo contido no atributo deve satisfazer os requisitos do X509FindType especificado. O padrão é uma cadeia de caracteres vazia.|  
|`storeLocation`|Especifica o local do repositório de certificados X.509 que o cliente usa para validar o certificado do servidor contra. Os valores válidos incluem o seguinte:<br /><br /> -LocalMachine: o repositório de certificados atribuído ao computador local.<br />-CurrentUser: o repositório de certificados atribuído ao usuário atual.<br /><br /> O padrão é LocalMachine.|  
|`storeName`|Especifica o nome do repositório de certificados X.509 a ser aberto. Os valores válidos incluem o seguinte:<br /><br /> -Catálogo de endereços: Repositório de certificados para outros usuários.<br />-AuthRoot: Repositório de certificados para autoridades de certificação de terceiros (CAs).<br />-CertificatAuthority: Repositório de certificados para autoridades de certificação intermediárias (CAs).<br />– Não permitido: Repositório de certificados para certificados revogados.<br />-Minha: Repositório de certificados para certificados pessoais.<br />-Raiz: Repositório de certificados para autoridades de certificação raiz confiável (CAs).<br />-TrustedPeople: Repositório de certificados para recursos e pessoas diretamente confiáveis.<br />-TrustedPublisher: Repositório de certificados para editores diretamente confiáveis.<br /><br /> O padrão é meu.|  
|`x509FindType`|Define o tipo de pesquisa de X.509 a ser executada. Os valores válidos incluem o seguinte:<br /><br /> -FindByThumbprint<br />-FindBySubjectName<br />-FindBySubjectDistinguishedName<br />-FindByIssuerName<br />-FindByIssuerDistinguishedName<br />-FindBySerialNumber<br />-FindByTimeValid<br />-   FindByTimeNotYetValid<br />-FindByTemplateName<br />-FindByApplicationPolicy<br />-FindByCertificatePolicy<br />-FindByExtension<br />-FindByKeyUsage<br />-FindBySubjectKeyIdentifier<br /><br /> O tipo contido a `findValue` atributo deve satisfazer os requisitos do X509FindType especificado.<br /><br /> O valor padrão é FindBySubjectDistinguishedName.|  
  
### <a name="child-elements"></a>Elementos filho  
 Nenhum  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<serviceCredentials>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|Especifica a credencial a ser usada na autenticação de serviço, e configurações relacionadas à validação de credenciais do cliente.|  
  
## <a name="remarks"></a>Comentários  
 Use esse elemento para especificar um certificado X.509 que será usado para autenticar o serviço para os clientes que usam o modo de segurança de mensagem. Se você estiver usando um certificado que será renovado periodicamente, sua impressão digital será alterado. Nesse caso, use o nome da entidade como o `x509FindType` porque o certificado pode ser reemitido com o mesmo nome de assunto.  
  
 Para obter mais informações sobre como usar o elemento, consulte [como: Especificar valores de credenciais de cliente](../../../../../docs/framework/wcf/how-to-specify-client-credential-values.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>  
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.ServiceCertificate%2A>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential>  
 <xref:System.ServiceModel.Description.ServiceCredentials.ServiceCertificate%2A>  
 [Como: Especificar valores de credenciais de cliente](../../../../../docs/framework/wcf/how-to-specify-client-credential-values.md)  
 [Comportamentos de segurança](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
