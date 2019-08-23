---
title: <issuedToken>
ms.date: 03/30/2017
ms.assetid: b6eae4b7-a6cd-4e1a-b0f6-f407022550b0
ms.openlocfilehash: 68e3a0802a10b14148188a81ee24ed901caa147f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925377"
---
# <a name="issuedtoken"></a>\<issuedToken>
Especifica um token personalizado usado para autenticar um cliente para um serviço.  
  
 \<system.ServiceModel>  
\<comportamentos >  
seção endpointBehaviors  
\<> de comportamento  
\<clientCredentials>  
\<issuedToken>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<issuedToken cacheIssuedTokens="Boolean"
             defaultKeyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy"
             issuedTokenRenewalThresholdPercentage = "0 to 100"
             issuerChannelBehaviors="String"
             localIssuerChannelBehaviors="String"
             maxIssuedTokenCachingTime="TimeSpan">
</issuedToken>
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`cacheIssuedTokens`|Atributo booliano opcional que especifica se os tokens são armazenados em cache. O padrão é `true`.|  
|`defaultKeyEntropyMode`|Atributo de cadeia de caracteres opcional que especifica quais valores aleatórios (entropias) são usados para operações de handshake. Os valores `ClientEntropy`incluem `ServerEntropy`, e `CombinedEntropy`, o padrão é `CombinedEntropy`. Esse atributo é do tipo <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>.|  
|`issuedTokenRenewalThresholdPercentage`|Atributo inteiro opcional que especifica a porcentagem de um período de tempo válido (fornecido pelo emissor do token) que pode passar antes de um token ser renovado. Os valores são de 0 a 100. O padrão é 60, que especifica 60% do tempo passado antes da tentativa de renovação.|  
|`issuerChannelBehaviors`|Atributo opcional que especifica os comportamentos de canal a serem usados ao se comunicar com o emissor.|  
|`localIssuerChannelBehaviors`|Atributo opcional que especifica os comportamentos de canal a serem usados ao se comunicar com o emissor local.|  
|`maxIssuedTokenCachingTime`|Atributo TimeSpan opcional que especifica a duração em que os tokens emitidos são armazenados em cache quando o emissor do token (um STS) não especifica uma hora. O padrão é "10675199.02:48:05.4775807".|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<localIssuer>](localissuer.md)|Especifica o endereço do emissor local do token e a associação usada para se comunicar com o ponto de extremidade.|  
|[\<issuerChannelBehaviors>](issuerchannelbehaviors-element.md)|Especifica os comportamentos de ponto de extremidade a serem usados ao contatar um emissor local.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<clientCredentials>](clientcredentials.md)|Especifica as credenciais usadas para autenticar um cliente para um serviço.|  
  
## <a name="remarks"></a>Comentários  
 Um token emitido é um tipo de credencial personalizado usado, por exemplo, ao autenticar com um serviço de token de segurança (STS) em um cenário federado. Por padrão, o token é um token SAML. Para obter mais informações, consulte [Federação e tokens emitidos](../../../wcf/feature-details/federation-and-issued-tokens.md). e a [Federação e](../../../wcf/feature-details/federation-and-issued-tokens.md)os tokens emitidos.  
  
 Esta seção contém os elementos usados para configurar um emissor local de tokens ou os comportamentos usados com um serviço de token de segurança. Para obter instruções sobre como configurar um cliente para usar um emissor local, [consulte Como: Configure um emissor](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)local.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.IssuedToken%2A>
- <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential>
- [Comportamentos de segurança](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [Protegendo serviços e clientes](../../../wcf/feature-details/securing-services-and-clients.md)
- [Federação e tokens emitidos](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [Protegendo clientes](../../../wcf/securing-clients.md)
- [Como: Criar um cliente federado](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [Como: Configurar um emissor local](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [Federação e tokens emitidos](../../../wcf/feature-details/federation-and-issued-tokens.md)
