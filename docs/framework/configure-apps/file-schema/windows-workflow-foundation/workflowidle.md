---
title: <workflowIdle>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: b2ef703c-3e01-4213-9d2e-c14c7dba94d2
ms.openlocfilehash: 1d8ddaf5d69d87ff6112b5cbb285f0ccfda724e2
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397531"
---
# <a name="workflowidle"></a>\<> workflowIdle
Um comportamento de serviço que controla quando instâncias de fluxo de trabalho ocioso são descarregadas e persistidas.  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<sistema. > ServiceModel**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportamentos >** ](behaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de portais**](servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportamento**](behavior-of-servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> workflowIdle**  
  
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
|timeToPersist|Um valor TimeSpan que especifica a duração entre a hora em que o fluxo de trabalho se torna ocioso e é persistido. O valor padrão é TimeSpan. MaxValue.<br /><br /> A duração começa a decorrer quando a instância de fluxo de trabalho fica ociosa. Esse atributo será útil se você quiser persistir uma instância de fluxo de trabalho de forma mais agressiva enquanto mantém a instância na memória o mais longo possível. Esse atributo só será válido se seu valor for menor que o atributo **TimeToUnload** . Se for maior, ela será ignorada. Se esse atributo decorrer antes do valor especificado pelo atributo **TimeToUnload** , a persistência deverá ser concluída antes que o fluxo de trabalho seja descarregado. Isso significa que a operação pode ser atrasada até que o fluxo de trabalho é mantido. A camada de persistência é responsável por gerenciar quaisquer tentativas de erros transitórios e apenas lança exceções em erros não recuperáveis. Portanto, todas as exceções geradas durante a persistência são tratadas como fatal e a instância de fluxo de trabalho será anulada.|  
|timeToUnload|Um valor de Timespan que especifica a duração entre o momento em que o fluxo de trabalho fica ocioso e é descarregado. O valor padrão é 1 minuto.<br /><br /> Descarregar um fluxo de trabalho significa que ele também é mantido. Se esse atributo for definido como zero, a instância do fluxo de trabalho será persistida e descarregada imediatamente depois que o fluxo de trabalho se tornar ocioso. Definir esse atributo como TimeSpan. MaxValue desabilita efetivamente a operação de descarregamento. Instâncias de fluxo de trabalho ocioso nunca são descarregadas.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<comportamento > de \<percomportamentos >](behavior-of-servicebehaviors-of-workflow.md)|Especifica um elemento de comportamento.|  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowIdleElement>
