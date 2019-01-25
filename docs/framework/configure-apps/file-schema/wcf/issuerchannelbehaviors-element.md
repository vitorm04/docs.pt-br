---
title: Elemento &lt;issuerChannelBehaviors&gt;
ms.date: 03/30/2017
ms.assetid: f7378673-8e9b-45b2-98d1-cf5dccdd8c40
ms.openlocfilehash: b77d0ce79557dff4b5a243da4d24703ed45fde07
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54677102"
---
# <a name="ltissuerchannelbehaviorsgt-element"></a>Elemento &lt;issuerChannelBehaviors&gt;
Contém uma coleção de comportamentos de ponto de extremidade do cliente do Windows Communication Foundation (WCF) (definido na configuração) para ser usado ao se comunicar com os serviços de Token de serviço especificados. Os comportamentos definidos não podem incluir nenhum [ \<clientCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) elementos.  
  
 \<system.ServiceModel>  
\<comportamentos >  
seção endpointBehaviors  
\<behavior>  
\<clientCredentials>  
\<issuedToken>  
\<issuerChannelBehaviors>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<issuerChannelBehaviors>
  <add behaviorConfiguraton="string"
       issuerAddress="string" />
</issuerChannelBehaviors>
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
 nenhuma.  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-issuerchannelbehaviors.md)|Adiciona um comportamento à coleção.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<issuedToken>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md)|Especifica um token personalizado usado para autenticar um cliente a um serviço.|  
  
## <a name="remarks"></a>Comentários  
 Use esse elemento quando qualquer comportamentos (diferente de comportamentos que incluem `<clientCredentials>` elementos) deve ser usado para se comunicar com um serviço. Por exemplo, se um [ \<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) elemento de comportamento deve ser incluído.  
  
## <a name="see-also"></a>Consulte também
- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>
- [Autenticação e identidade de serviço](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [Comportamentos de segurança](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [Federação e tokens emitidos](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [Protegendo serviços e clientes](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [Protegendo clientes](../../../../../docs/framework/wcf/securing-clients.md)
- [Como: Criar um cliente federado](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)
- [Como: Configurar um emissor Local](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)
- [Federação e tokens emitidos](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
