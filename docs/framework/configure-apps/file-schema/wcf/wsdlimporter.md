---
title: '&lt;wsdlImporter&gt;'
ms.date: 03/30/2017
ms.assetid: 986b2165-8430-4dba-b1b8-00396841bb96
ms.openlocfilehash: 33c2b0e4286ce746f745e4aebe10fd4bbd96810f
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32754896"
---
# <a name="ltwsdlimportergt"></a>&lt;wsdlImporter&gt;
Especifica todos os importadores WSDL que importa os metadados de WSDL Web Services Description Language () 1.1 com anexos de WS-Policy.  
  
\<system.ServiceModel>  
\<client>  
\<metadados >  
\<wsdlImporters >  
\<wsdlImporter >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<metadata>  
  <wsdlImporters>  
    <wsdlImporter type="string" />  
  </wsdlImporters>  
</metadata>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`type`|O tipo de elemento.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<wsdlImporters >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdlimporters.md)|Especifica todos os importadores WSDL que importa os metadados de WSDL Web Services Description Language () 1.1 com anexos de WS-Policy.|  
  
## <a name="remarks"></a>Comentários  
 O importador de WSDL é usado para importar metadados, bem como converter que informações em várias classes que representam o contrato e informações de ponto de extremidade. Seletivamente pode importar informações de contrato e o ponto de extremidade e propriedades que expõem os erros de importação e aceitam informações relevantes para o processo de importação e a conversão do tipo. Ele também oferece suporte a importação de informações de associação e propriedades que fornecem acesso a todos os documentos de política, documentos WSDL, extensões WSDL e documentos de esquema XML.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Configuration.WsdlImporterElement>  
 <xref:System.ServiceModel.Configuration.MetadataElement>  
 <xref:System.ServiceModel.Configuration.WsdlImporterElementCollection>  
 <xref:System.ServiceModel.Description.MetadataImporter>  
 <xref:System.ServiceModel.Description.WsdlImporter>  
 [Configuração de cliente do WCF](../../../../../docs/framework/wcf/feature-details/client-configuration.md)  
 [Clientes](../../../../../docs/framework/wcf/feature-details/clients.md)
