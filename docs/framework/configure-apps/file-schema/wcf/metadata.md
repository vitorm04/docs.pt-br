---
title: '&lt;Metadados&gt;'
ms.date: 03/30/2017
ms.assetid: d09653eb-e355-4c73-b87b-28f93d56480d
ms.openlocfilehash: 7e314ae56ed7a1b532bb8946fbb28802e72d3e20
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32747847"
---
# <a name="ltmetadatagt"></a>&lt;Metadados&gt;
Especifica como os metadados de serviço podem ser processado.  
  
 \<system.ServiceModel>  
\<client>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<system.serviceModel>  
    <client>  
        <metadata>  
                   <policyImporters>  
                          <policyImporter type="string" />  
                   </policyImporters  
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
|[\<policyImporters >](../../../../../docs/framework/configure-apps/file-schema/wcf/policyimporters.md)|Especifica todos os importadores de políticas que controlam a importação de declarações de políticas personalizadas sobre associações. Um importador de política é usado para declarações de políticas personalizadas sobre associação de recursos de pesquisa, bem como anexar um elemento de associação personalizada que implementa os recursos que requer a asserção.|  
|[\<wsdlImporters >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdlimporters.md)|Especifica todos os importadores WSDL que importam metadados de WSDL Web Services Description Language () 1.1 com anexos de WS-Policy. O importador de WSDL é usado para importar metadados, bem como converter que informações em várias classes que representam o contrato e informações de ponto de extremidade. Seletivamente pode importar informações de contrato e o ponto de extremidade e propriedades que expõem os erros de importação e aceitam informações relevantes para o processo de importação e a conversão do tipo. Ele também oferece suporte a importação de informações de associação e propriedades que fornecem acesso a todos os documentos de política, documentos WSDL, extensões WSDL e documentos de esquema XML.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<cliente >](../../../../../docs/framework/configure-apps/file-schema/wcf/client.md)|A seção de cliente define uma lista de pontos de extremidade que um cliente pode se conectar ao.|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Configuration.MetadataElement>  
 <xref:System.ServiceModel.Configuration.PolicyImporterElementCollection>  
 <xref:System.ServiceModel.Configuration.WsdlImporterElementCollection>  
 <xref:System.ServiceModel.Description.MetadataImporter>  
 <xref:System.ServiceModel.Description.WsdlImporter>  
 [Configuração de cliente do WCF](../../../../../docs/framework/wcf/feature-details/client-configuration.md)  
 [Clientes](../../../../../docs/framework/wcf/feature-details/clients.md)
