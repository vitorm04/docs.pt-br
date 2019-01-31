---
title: <persistenceProvider>
ms.date: 03/30/2017
ms.assetid: a37049c5-a7ea-4519-94f2-912eeb010380
ms.openlocfilehash: 054991687a54ecbf95cc18f58717a4ed3e36f050
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55260795"
---
# <a name="persistenceprovider"></a>\<persistenceProvider>
Especifica o tipo de implementação do provedor de persistência a usar, bem como o tempo limite a ser usado para operações de persistência.  
  
 \<system.ServiceModel>  
\<comportamentos >  
\<serviceBehaviors>  
\<behavior>  
\<persistenceProvider>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<persistenceProvider persistenceOperationTimeout="TimeSpan"
                     type="String" />
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|persistenceOperationTimeout|Um <xref:System.TimeSpan> valor que especifica o tempo limite usado para operações de persistência. O padrão é "00: 00:30".|  
|tipo|Uma cadeia de caracteres que especifica o tipo da fábrica de provedor de persistência a usar.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<behavior>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Especifica um elemento de comportamento.|  
  
## <a name="remarks"></a>Comentários  
 Esse elemento Especifica o provedor de persistência a ser usado para serializar o estado de um serviço WCF. Ele deve ser usado junto com o `wsHttpContextBinding` que passa informações de estado em cabeçalhos HTTP.  
  
## <a name="see-also"></a>Consulte também
- <xref:System.ServiceModel.Configuration.PersistenceProviderElement>
- <xref:System.ServiceModel.Persistence.PersistenceProvider>
