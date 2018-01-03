---
title: elemento de &lt;ponto de extremidade&gt;
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2fc8fedc-78d0-4e87-8142-fbfd26c15a4e
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7175cf55df6bb735367effa8f806a472b9ce5ea6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltendpointgt-element"></a>elemento de &lt;ponto de extremidade&gt;
Especifica a associação, contrato e propriedades de endereço de um ponto de extremidade de serviço, que é usado para expor serviços.  
  
 \<sistema. ServiceModel >  
\<serviço >  
\<ponto de extremidade >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<endpoint address="String"  
   behaviorConfiguration="String"  
   binding="String"  
   bindingConfiguration="String"  
   bindingName="String"  
   bindingNamespace="String"  
   contract="String"  
   endpointConfiguration="String"   isSystemEndpoint="Boolean"   kind="String"   listenUriMode="Explicit/Unique"  
   listenUri="Uri"  
</endpoint>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|endereço|Uma cadeia de caracteres que contém o endereço do ponto de extremidade. O endereço pode ser especificado como um endereço absoluto ou relativo. Se for fornecido um endereço relativo, o host deve fornecer um endereço base apropriado para o esquema de transporte usado na associação. Se um endereço não estiver configurado, o endereço base é considerado o endereço do ponto de extremidade.<br /><br /> O padrão é uma cadeia de caracteres vazia.|  
|behaviorConfiguration|Uma cadeia de caracteres que contém o nome do comportamento a ser usado no ponto de extremidade.|  
|associação|Necessário um atributo de cadeia de caracteres que especifica o tipo de associação a ser usada. O tipo deve ter uma seção de configuração registrado para ser referenciado. O tipo é registrado por nome de seção, em vez do nome do tipo de associação.|  
|bindingConfiguration|Uma cadeia de caracteres que especifica o nome de associação da associação a ser usado quando o ponto de extremidade é instanciado. O nome da associação deve estar no escopo no ponto de que extremidade é definida. O padrão é uma cadeia de caracteres vazia.<br /><br /> Este atributo é usado em conjunto com `binding` para fazer referência a uma configuração de associação específica no arquivo de configuração. Defina esse atributo, se você está tentando usar uma associação personalizada. Caso contrário, uma exceção pode ser lançada.|  
|bindingName|Uma cadeia de caracteres que especifica o nome qualificado exclusivo da associação para exportação de definição através de WSDL. O padrão é uma cadeia de caracteres vazia.|  
|bindingNamespace|Exportar uma cadeia de caracteres que especifica o nome qualificado do namespace da associação de definição através de WSDL. O padrão é uma cadeia de caracteres vazia.|  
|contrato|Uma cadeia de caracteres que indica qual contrato este ponto de extremidade está expondo. O assembly deve implementar o tipo de contrato. Se uma implementação de serviço implementa um tipo de contrato único, essa propriedade pode ser omitida. O padrão é uma cadeia de caracteres vazia.|  
|endpointConfiguration|Uma cadeia de caracteres que especifica o nome do ponto de extremidade padrão que é definido pelo `kind` atributo, o que faz referência às informações adicionais de configuração do ponto de extremidade padrão. O mesmo nome deve ser definido na `<standardEndpoints>` seção.|  
|isSystemEndpoint|Um valor booleano que especifica se um ponto de extremidade é um ponto de extremidade de infraestrutura.|  
|tipo|Uma cadeia de caracteres que especifica o tipo de ponto de extremidade padrão aplicado. O tipo deve ser registrado na seção `<extensions>` ou em machine.config. Se nada for especificado, um ponto de extremidade de serviço comum será criado.|  
|listenUriMode|Especifica como o transporte trata o `ListenUri` fornecido para o serviço de escuta. Os valores válidos são<br /><br /> -Explícita<br />-Exclusivo<br /><br /> O valor padrão é Explicit.|  
|ListenUri|Uma cadeia de caracteres que especifica o URI no qual o ponto de extremidade de serviço escuta. O padrão é uma cadeia de caracteres vazia.|  
|name|Atributo opcional. Uma cadeia de caracteres que especifica o nome do ponto de extremidade de serviço. O valor padrão é a concatenação do nome de associação e o nome de descrição do contrato. Serviços podem ter vários pontos de extremidade, portanto o ponto de extremidade `name` atributo é diferente do nome do serviço.|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<cabeçalhos >](../../../../../docs/framework/configure-apps/file-schema/wcf/headers.md)|Uma coleção de cabeçalhos de endereço.|  
|[\<identidade >](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|Uma identidade que permite a autenticação de um ponto de extremidade por outros pontos de extremidade de troca de mensagens com ele.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<serviço >](../../../../../docs/framework/configure-apps/file-schema/wcf/service.md)|Uma seção de configuração que define uma lista de pontos de extremidade que um cliente pode se conectar ao.|  
  
## <a name="example"></a>Exemplo  
 Este é um exemplo de uma configuração de ponto de extremidade de serviço.  
  
```xml  
<endpoint   
    address="/HelloWorld/"  
    bindingConfiguration="usingDefaults"  
    bindingName="MyBinding"  
    binding="customBinding"  
    contract="HelloWorld">  
    <Headers>  
       <Region xmlns="http://tempuri.org/">EastCoast</Region>  
       <Member xmlns="http://tempuri.org/">Gold</Member>  
    </Headers>  
</endpoint>  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Configuration.ServiceEndpointElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.Description.ServiceEndpoint>  
 [Pontos de extremidade: endereços, associações e contratos](../../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)  
 [Como criar um ponto de extremidade de serviço na configuração](../../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)
