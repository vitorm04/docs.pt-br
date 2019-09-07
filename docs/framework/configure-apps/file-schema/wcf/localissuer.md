---
title: <localIssuer>
ms.date: 03/30/2017
ms.assetid: 26bdd0df-0e7d-4b9e-bbeb-f28c53769385
ms.openlocfilehash: 055b7b49d1f775d49ac20de18c18ca0433716a23
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397856"
---
# <a name="localissuer"></a>\<localIssuer>
Especifica o endereço e a associação do emissor local a ser usado para obter um token de segurança.  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportamentos >** ](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> endpointBehaviors**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportamento**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<clientCredentials >** ](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> issuedToken**](issuedtoken.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> localIssuer**  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<localIssuer address="String"
             binding="String"
             bindingConfiguration="String" />
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|endereço|Cadeia de caracteres obrigatória. Especifica o URI do emissor local.|  
|associação|Cadeia de caracteres opcional. Uma das associações fornecidas pelo sistema. Para obter uma lista, consulte [associações fornecidas pelo sistema](../../../wcf/system-provided-bindings.md).|  
|bindingConfiguration|Cadeia de caracteres opcional. Especifica uma configuração de associação encontrada no arquivo de configuração.|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<identity>](identity.md)|Especifica informações de identidade para o emissor local.|  
|[\<headers>](headers-element.md)|Uma coleção de cabeçalhos de endereço que são necessários para resolver corretamente o emissor local. Você pode usar a `add` palavra-chave para adicionar um cabeçalho a essa coleção.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<issuedToken>](issuedtoken.md)|Especifica um token personalizado usado para autenticar um cliente para um serviço.|  
  
## <a name="remarks"></a>Comentários  
 Ao obter um token emitido de um serviço de token de segurança (STS), o aplicativo cliente deve ser configurado com o endereço e a associação a serem usados para se comunicar com o STS. Quando o <xref:System.ServiceModel.WSFederationHttpBinding> não fornece uma URL para o serviço de token de segurança, ou quando o endereço do emissor de uma associação federada `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` é `null`ou, o canal de Windows Communication Foundation do cliente (WCF) usa os valores especificados por `address` e`binding` para se comunicar com o STS para obter o token emitido. Para obter mais informações sobre como configurar um emissor local, [consulte Como: Configure um emissor](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)local.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir define `address`os `binding`atributos, `bindingConfiguration` e de um `localIssuer` elemento.  
  
```xml  
<system.serviceModel>
  <behaviors>
    <endpointBehaviors>
      <behavior name="MyEndpointBehavior">
        <clientCredentials>
          <issuedToken cacheIssuedTokens="false"
                       defaultKeyEntropyMode="ClientEntropy">
            <localIssuer address="net.tcp://cohowinery/tokens"
                         binding="netTcpBinding"
                         bindingConfiguration="myTcpBindingConfig" />
          </issuedToken>
        </clientCredentials>
      </behavior>
    </endpointBehaviors>
  </behaviors>
</system.serviceModel>
```  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.LocalIssuer%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential>
- [Comportamentos de segurança](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [Como: Configurar um emissor local](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [Autenticação e identidade de serviço](../../../wcf/feature-details/service-identity-and-authentication.md)
- [Comportamentos de segurança](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [Federação e tokens emitidos](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [Protegendo serviços e clientes](../../../wcf/feature-details/securing-services-and-clients.md)
- [Protegendo clientes](../../../wcf/securing-clients.md)
- [Como: Criar um cliente federado](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [Federação e tokens emitidos](../../../wcf/feature-details/federation-and-issued-tokens.md)
