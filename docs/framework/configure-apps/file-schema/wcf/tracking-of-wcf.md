---
title: <tracking> do WCF
ms.date: 03/30/2017
ms.assetid: 70cfaf24-a91c-4e56-ac47-d2ed87a963b3
ms.openlocfilehash: ddaf6f7871b4d10961b615f74d1ed49dd76d379a
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55268243"
---
# <a name="tracking-of-wcf"></a>\<Acompanhamento > do WCF
Representa uma seção de configuração para definir configurações de controle para um serviço de fluxo de trabalho.  
  
 Para obter mais informações no controle de fluxo de trabalho e sua configuração, consulte [fluxo de trabalho, controle e rastreamento](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) e [Configurando o rastreamento para um fluxo de trabalho](../../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md).  
  
 \<system.serviceModel>  
\<tracking>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<system.serviceModel>
  <tracking>
    <participants>
      <add name="String"
           profileName="String"
           type="String" />
    </participants>
    <profiles>
      <trackingProfile name="String">
        <workflow activityDefinitionId="String">
          <activityScheduledQueries>
            <activityScheduledQuery activityName="String"
                                    childActivityName="String"/>
          </activityScheduledQueries>
          <activityStateQueries>
            <activityStateQuery activityName="String" />
            <arguments>
              <argument name="String"/>
            </arguments>
            <states>
              <state name="String"/>
            </states>
            <variables>
              <variable name="String"/>
            </variables>
          </activityStateQueries>
          <bookmarkResumptionQueries>
            <bookmarkResumptionQuery name="String" />
          </bookmarkResumptionQueries>
          <cancelRequestQueries>
            <cancelRequestQuery activityName="String"
                                childActivityName="String"/>
          </cancelRequestQueries>
          <customTrackingQueries>
            <customTrackingQuery activityName="String"
                                 name="String"/>
          </customTrackingQueries>
          <faultPropagationQueries>
            <faultPropagationQuery activityName="String"
                                   faultHandlerActivityName="String"/>
          </faultPropagationQueries>
          <workflowInstanceQueries>
            <workflowInstanceQuery>
              <states>
                <state name="String"/>
              </states>
            </workflowInstanceQuery>
          </workflowInstanceQueries>
        </workflow>
      </trackingProfile>
    </profiles>
  </tracking>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
 nenhuma.  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<participants>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/participants.md)|Uma coleção de elementos de configuração definindo os participantes que assinar a acompanhar registros. Os participantes de rastreamento contém a lógica para processar a carga de registros de rastreamento (por exemplo, eles poderiam optar por gravar em um arquivo).|  
|[\<trackingProfile>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/trackingprofile.md)|Um perfil de rastreamento para filtrar registros de rastreamento emitida de uma instância de fluxo de trabalho.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|sistema.ServiceModel|O elemento raiz de todos os elementos de configuração do fluxo de trabalho.|  
  
## <a name="remarks"></a>Comentários  
 Rastreamento fornece a capacidade de examinar a execução de um fluxo de trabalho. A infra-estrutura de controle de fluxo de trabalho implementa um fluxo de trabalho para emitir registros que refletem eventos chave durante a execução. Por exemplo, quando uma instância de fluxo de trabalho inicia ou termina registros de rastreamento são emitidos. Rastreamento também pode extrair dados relevantes de negócios associados as variáveis de fluxo de trabalho. Por exemplo, se o fluxo de trabalho representa um sistema de processamento de pedidos a identificação do pedido pode ser extraída juntamente com o registro de rastreamento. Em geral, habilitar o rastreamento de WF facilita diagnóstico ou análise comercial sobre uma execução de fluxo de trabalho.  
  
## <a name="see-also"></a>Consulte também
- <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection?displayProperty=nameWithType>
- [Acompanhamento e rastreamento de fluxo de trabalho](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
