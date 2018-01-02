---
title: '&lt;ponto de extremidade&gt; do &lt;cliente&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: de6238ae-bbf8-48e9-a1b5-e24c0bea8afa
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 351f49c346cb8126cdd9d540a4db382bf5f4e721
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltendpointgt-of-ltclientgt"></a>&lt;ponto de extremidade&gt; do &lt;cliente&gt;
Especifica o contrato, associação e propriedades de endereço do ponto de extremidade de canal, que é usado pelos clientes para se conectar a pontos de extremidade de serviço no servidor.  
  
 \<sistema. ServiceModel >  
\<cliente >  
\<ponto de extremidade >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<endpoint address="String"  
   behaviorConfiguration="String"  
   binding="String"  
   bindingConfiguration="String"  
   contract="String"   endpointConfiguration="String"   kind="String"  
   name="String"  
</endpoint>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|endereço|Atributo de cadeia de caracteres obrigatória.<br /><br /> Especifica o endereço do ponto de extremidade. O padrão é uma cadeia de caracteres vazia. O endereço deve ser um URI absoluto.|  
|behaviorConfiguration|Uma cadeia de caracteres que contém o nome do comportamento do comportamento a ser usado para instanciar o ponto de extremidade. O nome do comportamento deve estar no escopo no ponto em que o serviço está definido. O padrão é uma cadeia de caracteres vazia.|  
|associação|Atributo de cadeia de caracteres obrigatória.<br /><br /> Uma cadeia de caracteres que indica o tipo de associação a ser usada. O tipo deve ter uma seção de configuração registrado para ser referenciado. O tipo é registrado pelo nome da seção, em vez de pelo nome do tipo de associação.|  
|bindingConfiguration|Opcional. Uma cadeia de caracteres que contém o nome da configuração de associação a ser usado quando o ponto de extremidade é instanciado. A configuração de associação deve estar no escopo no ponto de que extremidade é definida. O padrão é uma cadeia de caracteres vazia.<br /><br /> Este atributo é usado em conjunto com `binding` para fazer referência a uma configuração de associação específica no arquivo de configuração. Defina esse atributo, se você está tentando usar uma associação personalizada. Caso contrário, uma exceção pode ser lançada.|  
|contrato|Atributo de cadeia de caracteres obrigatória.<br /><br /> Uma cadeia de caracteres que indica qual contrato este ponto de extremidade está expondo. O assembly deve implementar o tipo de contrato.|  
|endpointConfiguration|Uma cadeia de caracteres que especifica o nome do ponto de extremidade padrão que é definido pelo `kind` atributo, o que faz referência às informações adicionais de configuração do ponto de extremidade padrão. O mesmo nome deve ser definido na `<standardEndpoints>` seção.|  
|tipo|Uma cadeia de caracteres que especifica o tipo de ponto de extremidade padrão aplicado. O tipo deve ser registrado na seção `<extensions>` ou em machine.config. Se nada for especificado, um ponto de extremidade de canal comum será criado.|  
|name|Atributo de cadeia de caracteres opcional. Este atributo identifica exclusivamente um ponto de extremidade para um dado contrato. Você pode definir vários clientes para um determinado tipo de contrato. Cada definição deve ser diferenciada por um nome exclusivo. Se esse atributo for omitido, o ponto de extremidade correspondente é usado como o ponto de extremidade padrão associado ao tipo de contrato especificado. O padrão é uma cadeia de caracteres vazia.<br /><br /> O `name` atributo de uma associação é usado para exportação de definição através de WSDL.|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<cabeçalhos >](../../../../../docs/framework/configure-apps/file-schema/wcf/headers.md)|Uma coleção de cabeçalhos de endereço.|  
|[\<identidade >](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|Uma identidade que permite a autenticação de um ponto de extremidade por outros pontos de extremidade de troca de mensagens com ele.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<cliente >](../../../../../docs/framework/configure-apps/file-schema/wcf/client.md)|Uma seção de configuração que define uma lista de pontos de extremidade que um cliente pode se conectar ao.|  
  
## <a name="example"></a>Exemplo  
 Este é um exemplo de uma configuração de ponto de extremidade de canal.  
  
```xml  
<endpoint address="/HelloWorld/"  
    bindingConfiguration="usingDefaults"  
    name="MyBinding"  
    binding="customBinding"  
    contract="HelloWorld">  
</endpoint>  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Configuration.ChannelEndpointElement>  
 <xref:System.ServiceModel.Configuration.ClientSection>  
 <xref:System.ServiceModel.Configuration.ChannelEndpointElementCollection>  
 <xref:System.ServiceModel.Configuration.ClientSection.Endpoints%2A>  
 <xref:System.ServiceModel.Configuration.ChannelEndpointElement>  
 [Configuração de cliente do WCF](../../../../../docs/framework/wcf/feature-details/client-configuration.md)  
 [Clientes](../../../../../docs/framework/wcf/feature-details/clients.md)
