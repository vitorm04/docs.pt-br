---
title: <workflowInstanceQueries> do WCF
ms.date: 03/30/2017
ms.assetid: b0852f77-16e4-4d55-8eb7-a19feb0e8fc4
ms.openlocfilehash: 89e122b87743a81a80ce63b382ae235c1c4863bc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61790514"
---
# <a name="workflowinstancequeries-of-wcf"></a>\<workflowInstanceQueries > do WCF

Representa uma coleção de elementos de configuração que controlam alterações de ciclo de vida de instância de fluxo de trabalho como um evento iniciado ou concluído.  
  
Para obter mais informações sobre consultas de perfil de controle, consulte [perfis de acompanhamento](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)  
  
\<system.serviceModel>  
\<tracking>  
\<profiles>  
\<trackingProfile>  
\<workflow>  
\<workflowInstanceQueries>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <workflowInstanceQueries>
          <workflowInstanceQuery>
            <states>
              <state name="Name" />
            </states>
          </workflowInstanceQuery>
        </workflowInstanceQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos

As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  

nenhuma.  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<workflowInstanceQuery>](workflowinstancequery-of-wcf.md)|Uma consulta que é usada para controlar as alterações de ciclo de vida de instância de fluxo de trabalho.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<workflow>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|Um elemento de configuração que contém todas as consultas para um fluxo de trabalho específico identificado pela [activityDefinitionId](xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId) propriedade.|  
  
## <a name="remarks"></a>Comentários

<xref:System.Activities.Tracking.WorkflowInstanceQuery> é usado para assinar seguintes a <xref:System.Activities.Tracking.TrackingRecord> os objetos:  
  
- <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a>Exemplo  

A configuração a seguir assina o fluxo de trabalho em nível de instância registros de controle para o `Started` estado da instância usando esta consulta.  
  
```xml  
<workflowInstanceQueries>
  <workflowInstanceQuery>
    <states>
      <state name="Started" />
    </states>
  </workflowInstanceQuery>
</workflowInstanceQueries>
```  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [Acompanhamento e rastreamento de fluxo de trabalho](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [Acompanhando perfis](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
