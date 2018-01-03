---
title: '&lt;estado&gt; do WCF, &lt;workflowInstanceQuery&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 40f21055-766c-4be9-86c4-d1d899007098
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: edb6cc424be51e03b3c34182a2b456a9658e2bc7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltstategt-of-wcf-ltworkflowinstancequerygt"></a>&lt;estado&gt; do WCF, &lt;workflowInstanceQuery&gt;
Representa uma coleção de estados inscritos da instância do fluxo de trabalho controladas quando os registros de rastreamento são criados.  
  
 Para obter mais informações sobre consultas de perfil de controle, consulte [perfis de controle](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)  
  
 \<System. ServiceModel >  
\<controle >  
\<trackingProfile >  
\<fluxo de trabalho >  
\<workflowInstanceQueries >  
\<workflowInstanceQuery >  
\<estados >  
\<estado >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <workflowInstanceQueries>             <workflowInstanceQuery>                <states>                   <state name="Name"/>                </states>            </workflowInstanceQuery>         </workflowInstanceQueries>       </workflow>   </trackingProfile></tracking>  
```
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|name|Uma cadeia de caracteres que especifica um estado inscrito da instância do fluxo de trabalho controladas quando o registro de rastreamento é criado.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<estados >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|Uma coleção de estados inscritos da instância do fluxo de trabalho controladas quando os registros de rastreamento são criados.|  
  
## <a name="remarks"></a>Comentários  
 Os registros retornados são filtrados por estados nesta coleção.  
  
 Estado de possíveis valores é descritos na tabela a seguir.  
  
|Estado|Descrição|  
|-----------|-----------------|  
|Anulado|A instância de fluxo de trabalho será anulada.|  
|Concluído|A instância de fluxo de trabalho for concluída.|  
|Deleted|A instância de fluxo de trabalho é excluída.|  
|Ocioso|A instância de fluxo de trabalho está ociosa.|  
|Persistentes|A instância de fluxo de trabalho é mantida.|  
|Retomada|A instância de fluxo de trabalho é retomada.|  
|Introdução|A instância de fluxo de trabalho é iniciada.|  
|UnhandledException|A instância de fluxo de trabalho encontrou uma exceção sem tratamento.|  
|Descarregado|A instância de fluxo de trabalho é descarregada.|  
|Cancelado|A instância de fluxo de trabalho é cancelada.|  
|Suspenso|A instância de fluxo de trabalho é suspensa.|  
|Encerrada|A instância de fluxo de trabalho é encerrada.|  
|Não suspenso|A instância de fluxo de trabalho é unsuspended.|  
  
## <a name="example"></a>Exemplo  
 A configuração a seguir assina o fluxo de trabalho em nível de instância registros de controle para o `Started` estado da instância usando esta consulta.  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>       
 <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElement?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>       
 [Acompanhamento e rastreamento de fluxo de trabalho](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [Acompanhando perfis](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
