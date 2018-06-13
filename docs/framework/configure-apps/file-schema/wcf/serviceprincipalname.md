---
title: '&lt;ServicePrincipalName&gt;'
ms.date: 03/30/2017
ms.assetid: 3f3b85d3-20f2-4cd8-8a6a-ee18befbd165
ms.openlocfilehash: e5c1f5a6986d57d20180560b12f5c7c5540a590d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32750720"
---
# <a name="ltserviceprincipalnamegt"></a>&lt;ServicePrincipalName&gt;
Especifica a identidade de um serviço por seu serviço Nome Principal (SPN).  
  
 Para obter mais informações sobre como configurar o SPN, consulte [autenticação e identidade de serviço](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).  
  
 \<identidade >  
\<servicePrincipalName >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<servicePrincipalName value = "String" />  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem os elementos pai de atributos e elementos filho  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|Valor |O nome pelo qual um cliente identifica exclusivamente uma instância de um serviço. Se você instalar várias instâncias de um serviço em computadores em uma floresta, cada instância deve ter seu próprio SPN. Uma instância de determinado serviço pode ter vários SPNs se houver vários nomes que os clientes podem usar para autenticação.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<identity>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|Especifica a identidade do serviço para ser autenticado pelo cliente.|  
  
## <a name="remarks"></a>Comentários  
 Um cliente seguro do Windows Communication Foundation (WCF) que se conecta a um ponto de extremidade com esta identidade usa o SPN ao executar a autenticação de SSPI com o ponto de extremidade.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Configuration.IdentityElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.EndpointAddress.Identity%2A>  
 <xref:System.ServiceModel.SpnEndpointIdentity>  
 [Autenticação e identidade de serviço](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [\<identity>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
