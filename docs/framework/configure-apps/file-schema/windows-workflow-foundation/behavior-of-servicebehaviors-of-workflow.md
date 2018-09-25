---
title: '&lt;comportamento&gt; dos &lt;serviceBehaviors&gt; de fluxo de trabalho'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 6a4b718a-1b40-4957-935a-f6122819ab3c
ms.openlocfilehash: 9b16aad6138d79d3dbff4994250f05d617d54140
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47109531"
---
# <a name="ltbehaviorgt-of-ltservicebehaviorsgt-of-workflow"></a>&lt;comportamento&gt; dos &lt;serviceBehaviors&gt; de fluxo de trabalho
O **comportamento** elemento contém uma coleção de configurações para o comportamento de um serviço. Cada comportamento é indexado por seus **nome**. Serviços podem vincular a cada comportamento por esse nome usando o **behaviorConfiguration** atributo da [ \<ponto de extremidade >](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) elemento. Isso permite que os pontos de extremidade compartilhem configurações comuns de comportamento sem redefinir as configurações.  
  
\<system.ServiceModel>  
\<comportamentos >  
\<serviceBehaviors >  
\<comportamento de >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<system.ServiceModel>  
  <behaviors>  
    <serviceBehaviors>  
      <behavior name="String">
        <bufferReceive maxPendingMessagesPerChannel="Integer" />
        <etwTracking profileName="String" />
        <sendMessageChannelCache allowUnsafeCaching="Boolean">
          <channelSettings idleTimeout="TimeSpan" 
                           leaseTimeout="TimeSpan" 
                           maxItemsInCache="Integer" />
          <factorySettings idleTimeout="TimeSpan" 
                           leaseTimeout="TimeSpan" 
                           maxItemsInCache="Integer" />
        </sendMessageChannelCache>
        <sqlWorkflowInstanceStore connectionStringName="String" 
                                  honstLockRenewalPeriod="TimeSpan" 
                                  instanceCompletionAction="DeleteNothing/DeleteAll" 
                                  instanceEncodingAction="None/GZip" 
                                  instanceLockedExceptionAction="NoRetry/BasicRetry/AggressiveRetry" 
                                  runnableInstancesDetectionPeriod="TimeSpan" />
        <workflowIdle timeToPersist="TimeSpan" 
                      timeToUnload="TimeSpan" />
        <workflowUnhandledException action="Abandon/AbandonAndSuspend/Cancel/Terminate" />
      </behavior>
    </serviceBehaviors>  
  </behaviors>  
</system.ServiceModel>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|name|Uma cadeia de caracteres exclusiva que contém o nome da configuração do comportamento. Esse valor é uma cadeia de caracteres definida pelo usuário que deve ser exclusiva, pois ele atua como a cadeia de caracteres de identificação para o elemento.|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<bufferReceive >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/bufferreceive.md)|Um comportamento de serviço que permite que um serviço a ser usado em buffer recebe o processamento, que permite que um serviço de fluxo de trabalho processar mensagens de fora de ordem.|  
|[\<roteamento >](../../../../../docs/framework/configure-apps/file-schema/wcf/routing-of-servicebehavior.md)|Um comportamento de serviço que permite que um serviço que utiliza o acompanhamento ETW use um <xref:System.Activities.Tracking.EtwTrackingParticipant>.|  
|[\<sendMessageChannelCache >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/sendmessagechannelcache.md)|Um comportamento de serviço que permite a personalização do cache do compartilhamento níveis, as configurações de cache da fábrica de canal e as configurações de cache do canal para fluxos de trabalho que enviam mensagens a pontos de extremidade de serviço usando atividades de mensagem de envio.|  
|[\<sqlWorkflowInstanceStore >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/sqlworkflowinstancestore.md)|Um comportamento de serviço que permite configurar o recurso <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>, que dá suporte a informações de estado persistentes para instâncias de serviço de fluxo de trabalho em um banco de dados do SQL Server 2005 ou do SQL Server 2008.|  
|[\<workflowIdle >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowidle.md)|Um comportamento de serviço que controla quando instâncias de fluxo de trabalho ocioso são descarregadas e persistidas.|  
|[\<workflowInstanceManagement >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowinstancemanagement.md)|Um comportamento de serviço que permite que você especifique as configurações que controlam como as instâncias de fluxo de trabalho são executadas, incluindo persistência, o comportamento de exceção sem tratamento e o comportamento ocioso.|  
|[\<workflowUnhandledException >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowunhandledexception.md)|Um comportamento de serviço que permite que você especifique a ação a ser executada quando ocorre uma exceção sem tratamento em um serviço de fluxo de trabalho.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<serviceBehaviors >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/servicebehaviors-of-workflow.md)|Uma coleção de elementos de comportamento de serviço.|
