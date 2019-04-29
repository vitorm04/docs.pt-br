---
title: <wsdlImporter>
ms.date: 03/30/2017
ms.assetid: 986b2165-8430-4dba-b1b8-00396841bb96
ms.openlocfilehash: 1f34486296465b3ea0b5b05bd9492062c85ad8c8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61670242"
---
# <a name="wsdlimporter"></a>\<wsdlImporter>
Especifica todos os importadores WSDL que importa os metadados de descrição linguagem WSDL (Web Services) 1.1 com anexos WS-Policy.  
  
\<system.ServiceModel>  
\<client>  
\<metadata>  
\<wsdlImporters>  
\<wsdlImporter>  
  
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
|`type`|O tipo deste elemento.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<wsdlImporters>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdlimporters.md)|Especifica todos os importadores WSDL que importa os metadados de descrição linguagem WSDL (Web Services) 1.1 com anexos WS-Policy.|  
  
## <a name="remarks"></a>Comentários  
 Um importador WSDL é usado para importar metadados, bem como converter essa informações em várias classes que representam o contrato e informações de ponto de extremidade. Ele seletivamente pode importar informações de contrato e o ponto de extremidade e propriedades que expõem os erros de importação e aceitar informações relevantes para o processo de importação e a conversão do tipo. Ele também dá suporte a importação de informações de associação e propriedades que fornecem acesso a todos os documentos de política, documentos WSDL, extensões WSDL e documentos de esquema XML.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Configuration.WsdlImporterElement>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- <xref:System.ServiceModel.Configuration.WsdlImporterElementCollection>
- <xref:System.ServiceModel.Description.MetadataImporter>
- <xref:System.ServiceModel.Description.WsdlImporter>
- [Configuração de cliente do WCF](../../../../../docs/framework/wcf/feature-details/client-configuration.md)
- [Clientes](../../../../../docs/framework/wcf/feature-details/clients.md)
