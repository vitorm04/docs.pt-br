---
title: <customTrackingQuery>do WCF
ms.date: 03/30/2017
ms.assetid: 164446ae-8440-4b67-b217-6786cfae1e01
ms.openlocfilehash: b034727dc89b58794ec2834cb0ff39cd7e5f1dca
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919357"
---
# <a name="customtrackingquery-of-wcf"></a>\<customTrackingQuery > do WCF

Representa uma consulta que é usada para rastrear eventos que você define em suas atividades de código. A consulta é necessária para um participante de rastreamento assinar registros personalizados de rastreamento.

Para obter mais informações sobre consultas de perfil de rastreamento, consulte [perfis de rastreamento](../../../windows-workflow-foundation/tracking-profiles.md)  
  
\<system.serviceModel>  
\<acompanhamento de >  
\<perfis >  
\<trackingProfile>  
\<workflow>  
\<customTrackingQueries>  
\<customTrackingQuery>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <customTrackingQueries>
          <customTrackingQuery activityName="String"
                               name="String"/>
        </customTrackingQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  

As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`activityName`|Uma cadeia de caracteres que especifica o nome da atividade que gerou o registro de rastreamento.|  
|`name`|Uma cadeia de caracteres que especifica o nome do registro de controle personalizado que é emitido.|  
  
### <a name="child-elements"></a>Elementos filho

nenhuma.

### <a name="parent-elements"></a>Elementos pai

|Elemento|Descrição|  
|-------------|-----------------|  
|[\<customTrackingQueries>](customtrackingqueries-of-wcf.md)|Representa uma coleção de consultas que são usados para controlar os eventos que você define em suas atividades de código.|
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [Acompanhamento e rastreamento de fluxo de trabalho](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [Acompanhando perfis](../../../windows-workflow-foundation/tracking-profiles.md)
