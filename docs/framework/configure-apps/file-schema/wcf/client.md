---
title: '&lt;client&gt;'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.ServiceModel/client
- http://schemas.microsoft.com/.NetConfiguration/v2.0#client
ms.assetid: bf0f7031-76c8-4e7e-a6c6-9ad9119134be
ms.openlocfilehash: 32fcd9792f674d4ded466f26641690c8ae4328b9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54540397"
---
# <a name="ltclientgt"></a>&lt;client&gt;
O `client` elemento define uma lista de pontos de extremidade que um cliente pode se conectar ao.  
  
 \<system.ServiceModel>  
\<client>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<system.serviceModel>
  <client>
    <endpoint>
    </endpoint>
    <metadata>
    </metadata>
  </client>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
 Nenhum  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<endpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-of-client.md)|Contém uma coleção de elementos de ponto de extremidade, que especificam os pontos de extremidade que esse cliente pode se conectar ao.|  
|[\<metadata>](../../../../../docs/framework/configure-apps/file-schema/wcf/metadata.md)|Contém configurações para metadados de processamento.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<system.serviceModel>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|O elemento raiz de todos os elementos de configuração do Windows Communication Foundation (WCF).|  
  
## <a name="remarks"></a>Comentários  
 O `client` seção define uma lista de pontos de extremidade que um cliente pode se conectar ao. Cada ponto de extremidade listado na seção cliente define sua própria associação, o comportamento e o contrato. Ele é identificado exclusivamente pela combinação da `name` e `contract` atributos. Especifica o código do cliente a `name` para se conectar a um ponto de extremidade para o serviço que implementa o cliente. Se o `name` atributo for omitido, o ponto de extremidade atua como o ponto de extremidade padrão para o contrato ele implementa.  
  
 Além disso, esta seção também especifica configurações para metadados de processamento.  
  
## <a name="example"></a>Exemplo  
  
```xml  
<client>
  <endpoint address="/HelloWorld/"
            bindingConfiguration="usingDefaults"
            name="MyBinding"
            binding="customBinding"
            contract="HelloWorld">
    <addressProperties actingAs="http://www.microsoft.com/TestActor"
                       identityData="BasicReadWrite"
                       identityType="Spn"
                       isAddressPrivate="false">
  </endpoint>
</client>
```  
  
## <a name="see-also"></a>Consulte também
- <xref:System.ServiceModel.Configuration.ClientSection>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- [Configuração de cliente do WCF](../../../../../docs/framework/wcf/feature-details/client-configuration.md)
- [Clientes](../../../../../docs/framework/wcf/feature-details/clients.md)
