---
title: '&lt;faultPropagationQuery&gt; of WCF'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fabafbc8-3e45-4feb-8321-0725e9f4079c
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 650be6a52651f9f55a868d135fd7d0dfa84b967a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ltfaultpropagationquerygt-of-wcf"></a>&lt;faultPropagationQuery&gt; of WCF
Representa uma consulta que é usada para controlar o tratamento de falhas que ocorrem dentro de uma atividade.  Esse evento ocorre sempre que um FaultHandler processa uma falha. Você deve usar essa consulta para controlar o tratamento de falhas que ocorrem dentro de uma atividade. A consulta é necessária para um participante de rastreamento assinar os registros de propagação de falhas.  
  
 Para obter mais informações sobre consultas de perfil de controle, consulte [perfis controle](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).  
  
 \<System. ServiceModel >  
\<controle >  
\<trackingProfile >  
\<fluxo de trabalho >  
\<faultPropagationQueries >  
\<faultPropagationQuery >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <faultPropagationQueries>             <faultPropagationQuery activityName="String"                 faultHandlerActivityName="String"/>          </faultPropagationQueries>       </workflow>   </trackingProfile></tracking>  
```
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|Nome_da_atividade|Uma cadeia de caracteres que especifica o nome da atividade do manipulador falhas propagada a falha. O padrão é *, que indica que os registros de propagação de falha são retornados para todas as atividades.|  
|faultHandlerActivityName|Uma cadeia de caracteres que especifica o nome da atividade que foi a origem da falha.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<faultPropagationQueries >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationqueries.md)|Representa uma lista de elementos de configuração que são usados para controlar o tratamento de falhas que ocorrem dentro de uma atividade.  Esse evento ocorre sempre que um FaultHandler processa uma falha.|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>       
 [Acompanhamento e rastreamento de fluxo de trabalho](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [Acompanhando perfis](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
