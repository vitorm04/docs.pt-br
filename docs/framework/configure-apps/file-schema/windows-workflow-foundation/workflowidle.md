---
title: <workflowIdle>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: b2ef703c-3e01-4213-9d2e-c14c7dba94d2
ms.openlocfilehash: 1dc186f5899935dab43c0d33894e659c4b19748c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59201111"
---
# <a name="workflowidle"></a>\<workflowIdle>
Um comportamento de serviço que controla quando instâncias de fluxo de trabalho ocioso são descarregadas e persistidas.  
  
\<system.ServiceModel>  
\<comportamentos >  
\<serviceBehaviors>  
\<behavior>  
\<workflowIdle>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowIdle timeToPersist="TimeSpan" 
                    timeToUnload="TimeSpan" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|timeToPersist|Um valor de Timespan que especifica a duração entre a hora em que o fluxo de trabalho fica ocioso e é mantido. O valor padrão é TimeSpan. MaxValue.<br /><br /> A duração começa a decorrer quando a instância de fluxo de trabalho fica ociosa. Esse atributo é útil se você quiser manter uma instância de fluxo de trabalho mais agressivamente enquanto mantém a instância na memória por mais tempo. Esse atributo só será válido se seu valor é menor do que o **timeToUnload** atributo. Se for maior, ela será ignorada. Se esse atributo decorrer antes do valor especificado pela **timeToUnload** atributo, persistência deve ser concluída antes que o fluxo de trabalho é descarregado. Isso significa que a operação pode ser atrasada até que o fluxo de trabalho é mantido. A camada de persistência é responsável por gerenciar quaisquer tentativas de erros transitórios e apenas lança exceções em erros não recuperáveis. Portanto, todas as exceções geradas durante a persistência são tratadas como fatal e a instância de fluxo de trabalho será anulada.|  
|timeToUnload|Um valor de Timespan que especifica a duração entre o momento em que o fluxo de trabalho fica ocioso e é descarregado. O valor padrão é 1 minuto.<br /><br /> Descarregar um fluxo de trabalho significa que ele também é mantido. Se esse atributo é definido como zero, a instância de fluxo de trabalho é mantida e descarregada imediatamente após o fluxo de trabalho fica ocioso. Definir esse atributo como TimeSpan efetivamente desabilita a operação. Instâncias de fluxo de trabalho ocioso nunca são descarregadas.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<comportamento > de \<serviceBehaviors >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|Especifica um elemento de comportamento.|  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowIdleElement>
