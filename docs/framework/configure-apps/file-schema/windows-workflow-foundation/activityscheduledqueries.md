---
title: '&lt;activityScheduledQueries&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: ca6e82f1-54f2-48d6-899c-9873065b5547
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 048b141d54a0fded8e3a5771c0f6c37bef9f7e30
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltactivityscheduledqueriesgt"></a>&lt;activityScheduledQueries&gt;
Representa uma coleção de consultas que são usados para controlar uma atividade agendada para execução por uma atividade pai. A consulta é necessária para um participante de rastreamento assinar os registros de atividade agendada.  
  
 Para obter mais informações sobre consultas de perfil de controle, consulte [perfis de controle](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)  
  
\<System. ServiceModel >  
\<controle >  
\<trackingProfile >  
\<fluxo de trabalho >  
\<activityScheduledQueries >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityScheduledQueries>
        <activityScheduledQuery activityName="String" 
                                childActivityName="String" />
      </activityScheduledQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
 nenhuma.  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<activityScheduledQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activityscheduledquery.md)|Uma consulta que é usada para controlar uma atividade agendada para execução por uma atividade pai.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<fluxo de trabalho >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|Um elemento de configuração que contém todas as consultas para um fluxo de trabalho específico identificado pelo **activityDefinitionId** propriedade.|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType>       
 [Acompanhamento e rastreamento de fluxo de trabalho](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [Acompanhando perfis](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
