---
title: '&lt;adicionar&gt; &lt;backupList&gt;'
ms.date: 03/30/2017
ms.assetid: bc5939fc-314a-4ea4-a533-c96958da7173
ms.openlocfilehash: 7e7361b24c0444b5f3d51a6f5bf079d5eb2dee18
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32745546"
---
# <a name="ltaddgt-of-ltbackuplistgt"></a>&lt;adicionar&gt; &lt;backupList&gt;
Representa um elemento de configuração que define um elemento de ponto de extremidade de backup.  
  
 \<system.serviceModel>  
\<roteamento >  
\<backupLists >  
\<backupList >  
\<add>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
   <routing>  <backupLists>    <backupList name="String">      <add endpointName="String" />    </backupList>    </backupLists></routing>  
```  
  
```csharp  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|name|Uma cadeia de caracteres que especifica o nome do ponto de extremidade de backup.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<roteamento >](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|Contém uma lista de pontos de extremidade que você deseja que o serviço de roteamento para usar no caso do ponto de extremidade primário não pode ser alcançado.|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Routing.Configuration.BackupEndpointElement?displayProperty=nameWithType> 
