---
title: '&lt;certificado&gt; de &lt;par&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 48b69142-c957-4305-a042-c9d0c9a55c0e
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f46ebab92cbca616b06db5be6dc155a44558aa7e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltcertificategt-of-ltpeergt"></a>&lt;certificado&gt; de &lt;par&gt;
Especifica um certificado usado por um colega.  
  
 \<sistema. ServiceModel >  
\<comportamentos >  
\<serviceBehaviors >  
\<comportamento >  
\<serviceCredentials >  
\<par >  
\<certificado >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<certificate findValue = "String"   
storeLocation = "CurrentUser/LocalMachine"  
storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"  
X509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"  
/>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`findValue`|Uma cadeia de caracteres que contém o valor para pesquisar no repositório de certificados x. 509. O tipo contido no atributo deve satisfazer os requisitos de especificado `x509FindType`. O padrão é uma cadeia de caracteres vazia.|  
|`storeLocation`|Especifica o local do repositório de certificados x. 509 que o cliente usa para validar o certificado do par. Os valores válidos incluem o seguinte:<br /><br /> -LocalMachine: o repositório de certificados atribuído ao computador local.<br />-CurrentUser: o repositório de certificados atribuído ao usuário atual.<br /><br /> O padrão é LocalMachine.|  
|`storeName`|Especifica o nome do repositório de certificados X.509 a ser aberto. Os valores válidos incluem o seguinte:<br /><br /> -Catálogo de endereços: O repositório de certificados para outros usuários.<br />-AuthRoot: Repositório de terceiros para autoridades de certificação (CAs) do certificado.<br />-CertificateAuthority: Repositório de certificados intermediários para autoridades de certificação (CAs).<br />-Proibido: Repositório de certificados revogados de certificados.<br />-My: Repositório de certificados pessoais do certificado.<br />-Raiz: O repositório de certificados raiz confiável para autoridades de certificação (CAs).<br />-TrustedPeople: Repositório de certificados pessoas confiáveis diretamente e recursos.<br />-TrustedPublisher: Repositório de certificados de editores confiáveis diretamente.<br /><br /> O padrão é meu.|  
|`X509FindType`|Define o tipo de pesquisa x. 509 a ser executado. Os valores válidos incluem o seguinte:<br /><br /> -FindByThumbPrint<br />-FindBySubjectName<br />-FindBySubjectDistinguishedName<br />-FindByIssuerName<br />-FindByIssuerDistinguishedName<br />-FindBySerialNumber<br />-FindByTimeValid<br />-FindByTimeNotYetValid<br />-FindByTemplateName<br />-FindByApplicationPolicy<br />-FindByCertificatePolicy<br />-FindByExtension<br />-FindByKeyUsage<br />-FindBySubjectKeyIdentifier<br /><br /> O tipo contido o `findValue` atributo deve satisfazer os requisitos de especificado `X509FindType`.<br /><br /> O valor padrão é FindBySubjectDistinguishedName.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<par >](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-servicecredentials.md)|Especifica as credenciais atuais de um nó ponto a ponto.|  
  
## <a name="remarks"></a>Comentários  
 Este elemento de configuração contém um `X509Certificate2` instância usada ao autenticar vizinhos na malha de pontos.  
  
 Para obter mais informações sobre programação ponto a ponto, consulte [rede ponto a ponto](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement.Certificate%2A>  
 <xref:System.ServiceModel.Configuration.X509PeerCertificateElement>  
 <xref:System.ServiceModel.Security.PeerCredential.Certificate%2A>  
 <xref:System.ServiceModel.Security.PeerCredential>  
 [Trabalhando com certificados](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [Rede ponto a ponto](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)  
 [Autenticação de mensagens de canal par](http://msdn.microsoft.com/en-us/80e73386-514e-4c30-9e4a-b9ca8c173a95)  
 [Autenticação personalizada de canal par](http://msdn.microsoft.com/en-us/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)  
 [Protegendo aplicativos de canal par](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)  
 [Protegendo serviços e clientes](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
