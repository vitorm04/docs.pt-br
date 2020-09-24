---
title: <wsdlImporter>
ms.date: 03/30/2017
ms.assetid: 986b2165-8430-4dba-b1b8-00396841bb96
ms.openlocfilehash: 82704aa40b508f1b1e2237c9768a7b7599c5c87e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91158585"
---
# \<wsdlImporter>

Especifica todos os importadores WSDL que importa metadados do WSDL (Web Services Description Language) 1,1 com anexos de WS-Policy.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<metadata>**](metadata.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsdlImporters>**](wsdlimporters.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<wsdlImporter>**  
  
## <a name="syntax"></a>Syntax  
  
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

 Nenhum.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<wsdlImporters>](wsdlimporters.md)|Especifica todos os importadores WSDL que importa metadados do WSDL (Web Services Description Language) 1,1 com anexos de WS-Policy.|  
  
## <a name="remarks"></a>Comentários  

 Um importador WSDL é usado para importar metadados, bem como converter essas informações em várias classes que representam informações de contrato e de ponto de extremidade. Ele pode importar seletivamente informações de contrato e de ponto de extremidade e propriedades que expõem quaisquer erros de importação e aceitam informações de tipo relevantes para o processo de importação e conversão. Ele também dá suporte à importação de informações de associação e propriedades que fornecem acesso a documentos de política, documentos WSDL, extensões WSDL e documentos de esquema XML.  
  
## <a name="see-also"></a>Confira também

- <xref:System.ServiceModel.Configuration.WsdlImporterElement>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- <xref:System.ServiceModel.Configuration.WsdlImporterElementCollection>
- <xref:System.ServiceModel.Description.MetadataImporter>
- <xref:System.ServiceModel.Description.WsdlImporter>
- [Configuração de cliente do WCF](../../../wcf/feature-details/client-configuration.md)
- [Clientes](../../../wcf/feature-details/clients.md)
