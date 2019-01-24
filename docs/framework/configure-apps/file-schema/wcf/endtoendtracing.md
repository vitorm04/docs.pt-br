---
title: '&lt;endToEndTracing&gt;'
ms.date: 03/30/2017
ms.assetid: 5034f5de-bb60-4157-9ad4-58aaade094e0
ms.openlocfilehash: c2f5e33eff4fdc6dfa85bcc10b59a7c1436cabb6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54519354"
---
# <a name="ltendtoendtracinggt"></a>&lt;endToEndTracing&gt;
Um elemento de configuração que permite que você habilitar e desabilitar diferentes aspectos de rastreamento de ponta a ponta durante a execução de um aplicativo de serviço.  
  
 \<system.ServiceModel>  
\<diagnóstico >  
\<endToEndTracing>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<system.serviceModel>
  <diagnostics>
    <endToEndTracing activityTracing="Boolean"
                     messageFlowTracing="Boolean"
                     propagateActivity="Boolean" />
  </diagnostics>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`activityTracing`|Um valor booliano que especifica se o rastreamento de atividades está habilitado.|  
|`messageFlowTracing`|Um valor booliano que especifica se o fluxo de mensagens de rastreamento no habilitada.|  
|`propagateActivity`|Um valor booliano que especifica se o atributo propagate é definido como true.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<diagnóstico >](../../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md)|Define as configurações do WCF para inspeção de tempo de execução e controle para o administrador.|  
  
## <a name="see-also"></a>Consulte também
- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.EndToEndTracing%2A>
- <xref:System.ServiceModel.Configuration.EndToEndTracingElement>
- [Rastreamento ponta a ponta](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing.md)
