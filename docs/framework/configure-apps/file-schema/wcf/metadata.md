---
title: <metadata>
ms.date: 03/30/2017
ms.assetid: d09653eb-e355-4c73-b87b-28f93d56480d
ms.openlocfilehash: c0c9848d073c799e1f97dd79b375848dfab71e99
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59191478"
---
# <a name="metadata"></a>\<metadata>
Especifica como os metadados de serviço podem ser processados.  
  
 \<system.ServiceModel>  
\<client>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<system.serviceModel>
  <client>
    <metadata>
      <policyImporters>
        <policyImporter type="string" />
      </policyImporters>
      <wsdlImporters>
        <wsdlImporter type="string" />
      </wsdlImporters>
    </metadata>
  </client>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
 nenhuma.  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<policyImporters>](../../../../../docs/framework/configure-apps/file-schema/wcf/policyimporters.md)|Especifica todos os importadores de políticas que controlam a importação de declarações de política personalizada sobre associações. Um importador de política é usado para pesquisar as declarações de política personalizadas sobre recursos de associação, bem como anexar a um elemento de associação personalizado que implementa os recursos que exige que a asserção.|  
|[\<wsdlImporters>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdlimporters.md)|Especifica todos os importadores WSDL que importam metadados de descrição linguagem WSDL (Web Services) 1.1 com anexos WS-Policy. Um importador WSDL é usado para importar metadados, bem como converter essa informações em várias classes que representam o contrato e informações de ponto de extremidade. Ele seletivamente pode importar informações de contrato e o ponto de extremidade e propriedades que expõem os erros de importação e aceitar informações relevantes para o processo de importação e a conversão do tipo. Ele também dá suporte a importação de informações de associação e propriedades que fornecem acesso a todos os documentos de política, documentos WSDL, extensões WSDL e documentos de esquema XML.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<client>](../../../../../docs/framework/configure-apps/file-schema/wcf/client.md)|A seção de cliente define uma lista de pontos de extremidade que um cliente pode se conectar ao.|  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Configuration.MetadataElement>
- <xref:System.ServiceModel.Configuration.PolicyImporterElementCollection>
- <xref:System.ServiceModel.Configuration.WsdlImporterElementCollection>
- <xref:System.ServiceModel.Description.MetadataImporter>
- <xref:System.ServiceModel.Description.WsdlImporter>
- [Configuração de cliente do WCF](../../../../../docs/framework/wcf/feature-details/client-configuration.md)
- [Clientes](../../../../../docs/framework/wcf/feature-details/clients.md)
