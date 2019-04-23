---
title: <backupList>
ms.date: 03/30/2017
ms.assetid: a3d9d1f9-4a53-45e9-a880-86c8bee0b833
ms.openlocfilehash: b0a6c604b5741c1355c35fca510cd10544dab9f3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59135727"
---
# <a name="backuplist"></a>\<backupList>
Representa uma seção de configuração para definir uma lista de backup que enumera um conjunto de pontos de extremidade que você gostaria que o serviço de roteamento use caso o ponto de extremidade primário não pode ser alcançado. Se o primeiro ponto de extremidade na lista estiver inativo, o serviço de roteamento irá automaticamente failover para o próximo na lista.  Isso lhe dá uma maneira rápida de adicionar confiabilidade para seu aplicativo sem ter que ensinar o aplicativo cliente como lidar com padrões complexos ou onde todos os seus serviços são implantados.  
  
 \<system.serviceModel>  
\<routing>  
\<backupLists>  
\<backupList>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<routing>
  <backupLists>
    <backupList name="String">
      <add endpointName="String" />
    </backupList>
  </backupLists>
</routing>
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|name|Uma cadeia de caracteres que especifica o nome usado para identificar esta lista de ponto de extremidade.|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<filter>](../../../../../docs/framework/configure-apps/file-schema/wcf/filter.md)||  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<routing>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|Uma lista de pontos de extremidade de backup.|  
  
## <a name="remarks"></a>Comentários  
 Esta seção contém uma coleção ordenada de pontos de extremidade que uma mensagem será transmitida no caso de uma exceção de comunicação ao enviar para o ponto de extremidade primário.  
  
 Se um envio para o ponto de extremidade primário é listado na `endpointName` atributo de [ \<Adicionar >](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-entries.md) falhar com uma exceção de comunicação, o serviço de roteamento tentará enviar a mensagem para o primeiro ponto de extremidade neste seção de configuração. Se isso também falhar com uma exceção de comunicação, o serviço de roteamento tentará enviar a mensagem para a próxima mensagem contida nesta seção até que a tentativa de envio for bem-sucedido, retornará uma falha que não seja uma exceção de comunicação ou todos os pontos de extremidade no coleção ter retornou uma falha.  
  
 No exemplo a seguir, se um envio para o ponto de extremidade primário chamado "Destino" retorna uma exceção de comunicação, o serviço tentará enviar a mensagem para "alternateServiceQueue". Se essa tentativa também retorna uma exceção de comunicação, o serviço de roteamento tentará enviar a mensagem para o próximo ponto de extremidade na coleção.  
  
```xml  
<filterTables>
  <filterTable name="filterTable1">
    <add filterName="MatchAllFilter1"
         endpointName="Destination"
         backupList="backupEndpointList" />
  </filterTable>
</filterTables>
<backupLists>
  <backupList name="backupEndpointList">
    <add endpointName="backupServiceQueue" />
    <add endpointName="alternateServiceQueue" />
  </backupList>
</backupLists>
```  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection?displayProperty=nameWithType>
