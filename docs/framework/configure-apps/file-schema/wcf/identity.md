---
title: '&lt;identity&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c1d2ae56-e231-4a07-9c3f-9f13381dc0d8
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 95b2ac18f6c04ad7ba31a8b1579506ac5c3b51ab
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="ltidentitygt"></a>&lt;identity&gt;
O elemento de identidade permite que um desenvolvedor de cliente especificar em tempo de design a identidade esperada do serviço. No processo de handshake entre o cliente e o serviço, o [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] infraestrutura garantirá que a identidade do serviço esperado corresponde aos valores desse elemento e, portanto, pode ser autenticada. Para obter mais informações, consulte [autenticação e identidade de serviço](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).  
  
 \<sistema. ServiceModel >  
\<cliente >  
\<ponto de extremidade >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<identity>  
    <certificate encodedValue="String"/>  
    <certificateReference findValue="String"   
       isChainIncluded="Boolean"  
       storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"storeName="  
       storeLocation="LocalMachine/CurrentUser"  
       X509FindType= Enumeration./>  
    <dns value="String"/>  
    <rsa value="String"/>  
    <servicePrincipalName value="String"/>  
    <usePrincipalName value="String"/>  
</identity>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
 nenhuma.  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|certificado|Especifica as configurações de um certificado x. 509. Esse elemento é do tipo <xref:System.ServiceModel.Configuration.CertificateElement>. Ele contém um atributo `encodedValue` que é uma cadeia de caracteres que especifica o valor codificado por esse certificado.|  
|certificateReference|Especifica configurações para validação do certificado x. 509. Esse elemento é do tipo <xref:System.ServiceModel.Configuration.CertificateReferenceElement>.|  
|dns|Especifica o DNS de um certificado x. 509 usado para autenticar um serviço. Esse elemento contém um atributo `value` que é uma cadeia de caracteres e contém a identidade real.|  
|rsa|Especifica o valor do campo RSA de um certificado x. 509 usado para autenticar um serviço para um cliente. Esse elemento contém um atributo `value` que é uma cadeia de caracteres e contém a identidade real|  
|servicePrincipalName|Especifica uma identidade de nome principal (SPN) do servidor, que é o nome de entidade de segurança usado por um cliente para identificar exclusivamente uma instância de um serviço. Esse elemento contém um atributo `value` que é uma cadeia de caracteres e contém o nome real da entidade. Esse elemento é do tipo <xref:System.ServiceModel.Configuration.ServicePrincipalNameElement>.|  
|userPrincipalName|Especifica uma identidade de nome principal (UPN) do usuário, que é o tipo de nome de logon de um usuário em uma rede. Nome principal do usuário consiste do nome do objeto de usuário usado no Active Directory, seguido do símbolo de arroba (@) e, em seguida, em geral, o sistema de nome de domínio pai domínio. Por exemplo, Jeff na árvore de domínio Fabrikam.com pode ter o nome principal do usuário [ jeff@fabrikam.com ](mailto:jeffsmith@fabrikam.com).  Esse elemento contém um atributo `value` que é uma cadeia de caracteres e contém o nome real da entidade. Esse elemento é do tipo <xref:System.ServiceModel.Configuration.UserPrincipalNameElement>.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<personalizado >](../../../../../docs/framework/configure-apps/file-schema/wcf/custom.md)|Especifica um resolvedor de pares personalizado para um netPeerTcpBinding.|  
|[\<ponto de extremidade >](http://msdn.microsoft.com/en-us/13aa23b7-2f08-4add-8dbf-a99f8127c017)|Configura os diferentes tipos de pontos de extremidade.|  
|[\<emissor >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuer.md)|Especifica o serviço de Token de segurança (STS) para o serviço federado.|  
|[\<issuerMetadata >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuermetadata.md)|Especifica o ponto de extremidade de metadados para o Token de segurança Service (STS) de um serviço federado.|  
|[\<issuedTokenParameters >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md)|Define os parâmetros de um token emitido em uma associação personalizada.|  
|[\<localIssuer >](../../../../../docs/framework/configure-apps/file-schema/wcf/localissuer.md)|Especifica um local Security Token Service (STS).|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Configuration.IdentityElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.EndpointAddress.Identity%2A>  
 [Autenticação e identidade de serviço](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [Pontos de extremidade: Endereços, associações e contratos](../../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
