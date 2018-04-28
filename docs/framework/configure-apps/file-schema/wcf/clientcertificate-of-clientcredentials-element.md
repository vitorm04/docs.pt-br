---
title: '&lt;clientCertificate&gt; de &lt;clientCredentials&gt; Element'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3b3fa000-3434-4142-a178-11903bdd2c5d
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9c5616aab5cb54e94a62370ad682eaa55eceb8ef
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2018
---
# <a name="ltclientcertificategt-of-ltclientcredentialsgt-element"></a>&lt;clientCertificate&gt; de &lt;clientCredentials&gt; Element
Define um certificado x. 509 usado para autenticar um cliente para um serviço.  
  
 \<system.ServiceModel>  
\<comportamentos >  
\<endpointBehaviors>  
\<comportamento >  
\<clientCredentials>  
\<clientCertificate >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<clientCertificate findValue="String"   
    storeLocation="LocalMachine/CurrentUser"  
    storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"  
X509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"  
/>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem os elementos pai de atributos e elementos filho  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`findValue`|Uma cadeia de caracteres que contém o valor para pesquisar no repositório de certificados x. 509. O tipo contido no atributo deve satisfazer os requisitos do `X509FindType` valor do atributo. O padrão é uma cadeia de caracteres vazia.|  
|`storeLocation`|Especifica o local do certificado x. 509 que o cliente usa para se autenticar para o serviço. Os valores válidos incluem o seguinte:<br /><br /> -LocalMachine: o repositório de certificados atribuído ao computador local.<br />-CurrentUser: o repositório de certificados atribuído ao usuário atual.<br /><br /> O padrão é LocalMachine. Esse atributo é do tipo <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.|  
|`storeName`|Especifica o nome do repositório de certificados x. 509 para pesquisar. Os valores válidos incluem o seguinte:<br /><br /> -Catálogo de endereços: O repositório de certificados para outros usuários.<br />-AuthRoot: Repositório de terceiros para autoridades de certificação (CAs) do certificado.<br />-CertificateAuthority: Repositório de certificados intermediários para autoridades de certificação (CAs).<br />-Proibido: Repositório de certificados revogados de certificados.<br />-My: Repositório de certificados pessoais do certificado.<br />-Raiz: O repositório de certificados raiz confiável para autoridades de certificação (CAs).<br />-TrustedPeople: Repositório de certificados pessoas confiáveis diretamente e recursos.<br />-TrustedPublisher: Repositório de certificados para editores diretamente confiáveis.<br /><br /> O padrão é meu. Esse atributo é do tipo <xref:System.Security.Cryptography.X509Certificates.StoreName>.|  
|X509FindType|Define o tipo de pesquisa de X.509 a ser executada. O tipo contido o `findValue` atributo deve satisfazer os requisitos desse atributo. Os valores válidos incluem o seguinte:<br /><br /> -   FindByThumbPrint<br />-FindBySubjectName<br />-FindBySubjectDistinguishedName<br />-FindByIssuerName<br />-FindByIssuerDistinguishedName<br />-FindBySerialNumber<br />-FindByTimeValid<br />-   FindByTimeNotYetValid<br />-FindByTemplateName<br />-FindByApplicationPolicy<br />-FindByCertificatePolicy<br />-FindByExtension<br />-FindByKeyUsage<br />-FindBySubjectKeyIdentifier<br /><br /> O valor padrão é FindBySubjectDistinguishedName. Esse atributo é do tipo <xref:System.Security.Cryptography.X509Certificates.X509FindType>.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<clientCredentials>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|Especifica as credenciais usadas para autenticar o cliente para um serviço.|  
  
## <a name="remarks"></a>Comentários  
 Este elemento de configuração especifica o certificado usado para autenticar o cliente com esse elemento. Para obter mais informações, consulte [como: especificar valores de credencial de cliente](../../../../../docs/framework/wcf/how-to-specify-client-credential-values.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement.ClientCertificate%2A>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Description.ClientCredentials.ClientCertificate%2A>  
 <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>  
 <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential>  
 [Comportamentos de segurança](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [Como especificar valores de credenciais do cliente](../../../../../docs/framework/wcf/how-to-specify-client-credential-values.md)  
 [Protegendo clientes](../../../../../docs/framework/wcf/securing-clients.md)  
 [Trabalhando com certificados](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [Protegendo serviços e clientes](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
