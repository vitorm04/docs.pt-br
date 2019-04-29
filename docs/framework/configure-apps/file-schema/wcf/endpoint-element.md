---
title: Elemento <endpoint>
ms.date: 03/30/2017
ms.assetid: 2fc8fedc-78d0-4e87-8142-fbfd26c15a4e
ms.openlocfilehash: 667086cda010daf51cb92116d636b9b526b4b34b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61673024"
---
# <a name="endpoint-element"></a>\<ponto de extremidade > elemento
Especifica a associação, contrato e propriedades de endereço de um ponto de extremidade de serviço, que é usado para expor serviços.  
  
 \<system.ServiceModel>  
\<service>  
\<endpoint>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<endpoint address="String"
          behaviorConfiguration="String"
          binding="String"
          bindingConfiguration="String"
          bindingName="String"
          bindingNamespace="String"
          contract="String"
          endpointConfiguration="String"
          isSystemEndpoint="Boolean"
          kind="String"
          listenUriMode="Explicit/Unique"
          listenUri="Uri">
</endpoint>
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|endereço|Uma cadeia de caracteres que contém o endereço do ponto de extremidade. O endereço pode ser especificado como um endereço absoluto ou relativo. Se um endereço relativo for fornecido, o host deve fornecer um endereço base apropriado para o esquema de transporte usado na associação. Se um endereço não estiver configurado, o endereço base é considerado o endereço do ponto de extremidade.<br /><br /> O padrão é uma cadeia de caracteres vazia.|  
|behaviorConfiguration|Uma cadeia de caracteres que contém o nome do comportamento a ser usado no ponto de extremidade.|  
|associação|Necessário o atributo de cadeia de caracteres que especifica o tipo de associação a ser usada. O tipo deve ter uma seção de configuração registrado para ser referenciado. O tipo é registrado pelo nome da seção, em vez de pelo nome do tipo da associação.|  
|bindingConfiguration|Uma cadeia de caracteres que especifica o nome de associação da associação a ser usada quando o ponto de extremidade é instanciado. O nome da associação deve estar no escopo no ponto de que extremidade é definido. O padrão é uma cadeia de caracteres vazia.<br /><br /> Esse atributo é usado em conjunto com `binding` para fazer referência a uma configuração de associação específica no arquivo de configuração. Defina esse atributo, se você está tentando usar uma associação personalizada. Caso contrário, uma exceção pode ser lançada.|  
|bindingName|Uma cadeia de caracteres que especifica o nome qualificado exclusivo da associação para exportação de definição por meio de WSDL. O padrão é uma cadeia de caracteres vazia.|  
|bindingNamespace|Uma cadeia de caracteres que especifica o nome qualificado do namespace da associação para a definição de exportação por meio de WSDL. O padrão é uma cadeia de caracteres vazia.|  
|contrato|Uma cadeia de caracteres que indica qual contrato este ponto de extremidade está expondo. O assembly deve implementar o tipo de contrato. Se uma implementação de serviço implementa um tipo de contrato único, em seguida, essa propriedade pode ser omitida. O padrão é uma cadeia de caracteres vazia.|  
|endpointConfiguration|Uma cadeia de caracteres que especifica o nome do ponto de extremidade padrão que é definido pelo `kind` atributo, o que faz referência às informações de configuração adicionais deste ponto de extremidade padrão. O mesmo nome deve ser definido no `<standardEndpoints>` seção.|  
|isSystemEndpoint|Um valor booliano que especifica se um ponto de extremidade é um ponto de extremidade de infraestrutura.|  
|Tipo|Uma cadeia de caracteres que especifica o tipo de ponto de extremidade padrão aplicado. O tipo deve ser registrado na seção `<extensions>` ou em machine.config. Se nada for especificado, um ponto de extremidade de serviço comum será criado.|  
|listenUriMode|Especifica como o transporte trata o `ListenUri` fornecido para o serviço escutar. Os valores válidos são<br /><br /> -Explícita<br />-Exclusivo<br /><br /> O valor padrão é explícito.|  
|listenUri|Uma cadeia de caracteres que especifica o URI no qual o ponto de extremidade de serviço escuta. O padrão é uma cadeia de caracteres vazia.|  
|name|Atributo opcional. Uma cadeia de caracteres que especifica o nome do ponto de extremidade de serviço. O valor padrão é a concatenação do nome de associação e o nome de descrição do contrato. Serviços podem ter vários pontos de extremidade, portanto, o ponto de extremidade `name` atributo é diferente do nome do serviço.|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<headers>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers.md)|Uma coleção de cabeçalhos de endereço.|  
|[\<identity>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|Uma identidade que permite a autenticação de um ponto de extremidade por outros pontos de extremidade trocando mensagens com ele.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<service>](../../../../../docs/framework/configure-apps/file-schema/wcf/service.md)|Uma seção de configuração que define uma lista de pontos de extremidade que um cliente pode se conectar ao.|  
  
## <a name="example"></a>Exemplo  
 Este é um exemplo de uma configuração de ponto de extremidade de serviço.  
  
```xml  
<endpoint address="/HelloWorld/"
          bindingConfiguration="usingDefaults"
          bindingName="MyBinding"
          binding="customBinding"
          contract="HelloWorld">
  <headers>
    <region xmlns="http://tempuri.org/">EastCoast</region>
    <member xmlns="http://tempuri.org/">Gold</member>
  </headers>
</endpoint>
```  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Configuration.ServiceEndpointElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.Description.ServiceEndpoint>
- [Pontos de extremidade: Endereços, associações e contratos](../../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
- [Como: Criar um ponto de extremidade de serviço na configuração](../../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)
