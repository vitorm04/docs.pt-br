---
title: <add> de <issuerChannelBehaviors>
ms.date: 03/30/2017
ms.assetid: 50710506-e28f-45dd-ab7e-bff6f44173db
ms.openlocfilehash: 325d6b8111115384b18547bd11ccec8a4a8af711
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920119"
---
# <a name="add-of-issuerchannelbehaviors"></a>\<Adicionar > de \<issuerChannelBehaviors >

Adiciona um comportamento de ponto de extremidade a ser usado ao se comunicar com um STS.

> [!NOTE]
> Se qualquer comportamento de ponto de extremidade contiver um elemento de [ \<> ClientCredentials](clientcredentials.md) , uma exceção será lançada.

\<system.ServiceModel>\
\<comportamentos > \
comportamento da \<seção EndpointBehaviors > \
\<clientCredentials>\
\<issuedToken>\
\<Elemento de > issuerChannelBehaviors \
\<add>

## <a name="syntax"></a>Sintaxe

```xml
<add issuerAddress="string"
     behaviorConfiguration="string" />
```

## <a name="attributes-and-elements"></a>Atributos e elementos

As seções a seguir descrevem atributos, elementos filho e elementos pai

### <a name="attributes"></a>Atributos

|Atributo|Descrição|
|---------------|-----------------|
|issuerAddress|O URI do emissor do token de segurança com o qual se comunicar.|
|behaviorConfiguration|O nome de um comportamento de ponto de extremidade definido no mesmo arquivo de configuração.|

### <a name="child-elements"></a>Elementos filho

nenhuma.

### <a name="parent-elements"></a>Elementos pai

|Elemento|Descrição|
|-------------|-----------------|
|[\<issuerChannelBehaviors>](issuerchannelbehaviors-element.md)|Contém uma coleção de comportamentos de ponto de extremidade de cliente do Windows Communication Foundation (WCF) a ser usada ao se comunicar com os serviços de token de serviço especificados.|

## <a name="remarks"></a>Comentários

`issuerAddress`contém o URI do serviço de token de segurança com o qual o cliente deseja se comunicar. `behaviorConfiguration`aponta para um comportamento de ponto de extremidade que o aplicativo usa nos canais criados por Windows Communication Foundation (WCF) para obter os tokens emitidos dos serviços de token de segurança.

## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>
- [Autenticação e identidade de serviço](../../../wcf/feature-details/service-identity-and-authentication.md)
- [Comportamentos de segurança](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [Federação e tokens emitidos](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [Protegendo serviços e clientes](../../../wcf/feature-details/securing-services-and-clients.md)
- [Protegendo clientes](../../../wcf/securing-clients.md)
- [Como: Criar um cliente federado](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [Como: Configurar um emissor local](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [Federação e tokens emitidos](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [\<issuerChannelBehaviors>](issuerchannelbehaviors-element.md)
