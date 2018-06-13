---
title: '&lt;userPrincipalName&gt;'
ms.date: 03/30/2017
ms.assetid: 68032f69-149e-4613-bae4-18314d4fd294
ms.openlocfilehash: 1bb0c8ac4cbe11cdfa31beb16b00b3863acabf92
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33358671"
---
# <a name="ltuserprincipalnamegt"></a>&lt;userPrincipalName&gt;
Especifica o usuário nome Principal (UPN) de um serviço para ser autenticado pelo cliente.  
  
 Para obter mais informações sobre como configurar o UPN, consulte [autenticação e identidade de serviço](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).  
  
\<identidade >  
\<userPrincipalName>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<userPrincipalName value="String" />  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem os elementos pai de atributos e elementos filho  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|Valor |Um nome de conta de usuário (também conhecido como o nome de logon do usuário) e um nome de domínio identificando o domínio no qual a conta de usuário está localizada. Este é o uso padrão para fazer logon em um domínio do Windows. O formato é: someone@example.com (como um endereço de email).|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<identity>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|Especifica a identidade do serviço para ser autenticado pelo cliente.|  
  
## <a name="remarks"></a>Comentários  
 Um cliente seguro do Windows Communication Foundation (WCF) que se conecta a um ponto de extremidade com esta identidade usa o UPN ao executar a autenticação de SSPI com o ponto de extremidade.  
  
## <a name="example"></a>Exemplo  
 O código de configuração a seguir especifica o UPN do serviço para ser autenticado pelo cliente.  
  
```xml  
<identity>  
  <userPrincipalName value="someone@cohowinery.com" />  
</identity>  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Configuration.IdentityElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.EndpointAddress.Identity%2A>  
 <xref:System.ServiceModel.UpnEndpointIdentity>  
 [Autenticação e identidade de serviço](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [\<identity>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
