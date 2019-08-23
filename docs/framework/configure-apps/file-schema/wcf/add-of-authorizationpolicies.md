---
title: <add> de <authorizationPolicies>
ms.date: 03/30/2017
ms.assetid: 613a03d8-4384-4556-bce2-8c23286c0bb0
ms.openlocfilehash: 65398c5afa9750f215c95899bb6004cae671123a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920269"
---
# <a name="add-of-authorizationpolicies"></a>\<Adicionar > de \<authorizationPolicies >
Especifica uma política de autorização para transformação de declaração.  
  
 \<system.ServiceModel>  
\<comportamentos >  
\<> de comportamento  
\<serviceAuthorization>  
\<authorizationPolicies>  
\<add>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<authorizationPolicies>
  <add policyType="String" />
</authorizationPolicies>
```  
  
## <a name="type"></a>Tipo  
 `Type`  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`policyType`|Um atributo de cadeia de caracteres necessário.<br /><br /> O modelo de controle de acesso do Windows Communication Foundation (WCF) dá suporte ao provisionamento de um conjunto de políticas de autorização como tipos. Esse atributo especifica uma política de autorização, que permite a transformação de um conjunto de declarações de entrada em outro conjunto de declarações. Controle de acesso pode ser concedido ou negado com base nisso.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<authorizationPolicies>](authorizationpolicies.md)|Especifica uma coleção de tipos de política de autorização.|  
  
## <a name="remarks"></a>Comentários  
 Cada política de autorização contém um único `policyType` atributo necessário que é uma cadeia de caracteres. O atributo especifica uma política de autorização, que permite a transformação de um conjunto de declarações de entrada em outro conjunto de declarações. Controle de acesso pode ser concedido ou negado com base nisso. Para obter mais informações sobre como funciona uma diretiva de autorização <xref:System.IdentityModel.Policy.IAuthorizationPolicy> , consulte e [política de autorização](../../../wcf/samples/authorization-policy.md).  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
- <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>
- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement.AuthorizationPolicies%2A>
- <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElementCollection>
- <xref:System.IdentityModel.Policy.IAuthorizationPolicy>
- [Autorizando o acesso a operações de serviço](../../../wcf/samples/authorizing-access-to-service-operations.md)
- [Como: Criar um Gerenciador de autorização personalizado para um serviço](../../../wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)
- [\<add>](add-of-authorizationpolicies.md)
- [Política de autorização](../../../wcf/samples/authorization-policy.md)
