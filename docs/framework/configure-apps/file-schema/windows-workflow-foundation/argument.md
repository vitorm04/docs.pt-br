---
title: '&lt;argumento&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: a7144d53-8023-4e90-971f-895e016fd58a
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9537a7443617cbe62f1b4ed1f424260559f4071b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltargumentgt"></a>&lt;argumento&gt;
Um elemento de configuração que representa um argumento associado a uma consulta de estado de atividade.  
  
 Para obter mais informações sobre consultas de perfil de controle, consulte [perfis controle](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).  
  
\<System. ServiceModel >  
\<controle >  
\<trackingProfile >  
\<fluxo de trabalho >  
\<activityStateQueries >  
\<activityStateQuery >  
\<argumentos >  
\<argumento >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityStateQueries>
        <activityStateQuery activityName="String" />
        <arguments>
          <argument name="String"/>
        </arguments>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|name|Uma cadeia de caracteres que especifica o nome do argumento.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<argumentos >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md)|Uma coleção de argumentos associados a essa consulta de atividade.|  
  
## <a name="remarks"></a>Comentários  
 Um recurso exclusivo de um ActivityStateQuery é a capacidade de extrair dados para controlar a execução de um fluxo de trabalho. Isso fornece contexto adicional ao acessar o rastreamento registra pós execução. Você pode usar o [ \<argumentos >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [ \<estados >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) e [ \<estados >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elementos para extrair qualquer variável ou argumento de qualquer atividade em um fluxo de trabalho. O exemplo a seguir mostra uma consulta de estado de atividade que extrai os argumentos e variáveis quando a atividade `Closed` registro de rastreamento é emitido. Variáveis e argumentos pode ser extraídos apenas com um ActivityStateRecord e, portanto, se inscreveu em um controle de perfil usando [ \<activityStateQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).  
  
```xml  
<activityStateQuery activityName="SendEmailActivity">  
  <states>  
    <state name="Closed"/>  
  </states>  
  <variables>  
    <variable name="FromAddress"/>  
  </variables>  
  <arguments>  
    <argument name="Result"/>  
  </arguments>  
</activityStateQuery>  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.ArgumentElement?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>       
 [Acompanhamento e rastreamento de fluxo de trabalho](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [Acompanhando perfis](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
