---
title: '&lt;policyImporter&gt;'
ms.date: 03/30/2017
ms.assetid: b0d03456-546f-44bb-ab12-1b2ce7f98fca
ms.openlocfilehash: 7483a95accef0a4bc956d919087379363b4762ca
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32753021"
---
# <a name="ltpolicyimportergt"></a>&lt;policyImporter&gt;
Especifica um importador de política que controla a importação de declarações de políticas personalizadas sobre associações.  
  
 \<system.ServiceModel>  
\<client>  
\<metadados >  
\<policyImporters >  
\<policyImporter >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<metadata>  
   <policyImporters>  
      <policyImporter type="string" />  
   </policyImporters>  
</metadata>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`type`|O tipo de elemento.|  
  
### <a name="child-elements"></a>Elementos filho  
 Nenhum  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<policyImporters >](../../../../../docs/framework/configure-apps/file-schema/wcf/policyimporters.md)|Especifica todos os importadores de políticas que controlam a importação de declarações de políticas personalizadas sobre associações.|  
  
## <a name="remarks"></a>Comentários  
 Um importador de política é usado para declarações de políticas personalizadas sobre associação de recursos de pesquisa, bem como anexar um elemento de associação personalizada que implementa os recursos que requer a asserção.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Configuration.PolicyImporterElementCollection>  
 <xref:System.ServiceModel.Configuration.PolicyImporterElement>  
 <xref:System.ServiceModel.Configuration.MetadataElement>  
 <xref:System.ServiceModel.Description.MetadataImporter>  
 [Configuração de cliente do WCF](../../../../../docs/framework/wcf/feature-details/client-configuration.md)  
 [Clientes](../../../../../docs/framework/wcf/feature-details/clients.md)
