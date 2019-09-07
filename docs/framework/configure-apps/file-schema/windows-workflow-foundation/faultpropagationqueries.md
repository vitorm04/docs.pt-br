---
title: <faultPropagationQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 00ff90ae-ebe0-4c85-a93f-61557288d0a3
ms.openlocfilehash: bc0cc5fd027da45994269b149b72496fa03becef
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398727"
---
# <a name="faultpropagationqueries"></a>\<faultPropagationQueries>
Representa uma coleção de consultas que são usadas para rastrear a manipulação de falhas que ocorrem em uma atividade.  Esse evento ocorre toda vez que um FaultHandler processa uma falha. Você deve usar essa consulta para controlar o tratamento de falhas que ocorrem dentro de uma atividade. A consulta é necessária para um participante de rastreamento assinar os registros de propagação de falhas.  
  
 Para obter mais informações sobre consultas de perfil de rastreamento, consulte [perfis de rastreamento](../../../windows-workflow-foundation/tracking-profiles.md).  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<sistema. > ServiceModel**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<acompanhamento de >** ](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> trackingProfile**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de fluxo de trabalho**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> faultPropagationQueries** 
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <faultPropagationQueries>
        <faultPropagationQuery activityName="String" 
                               faultHandlerActivityName="String" />
      </faultPropagationQueries>
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
|[\<faultPropagationQuery>](faultpropagationquery.md)|Uma consulta que é usada para rastrear a manipulação de falhas que ocorrem em uma atividade.  Esse evento ocorre toda vez que um FaultHandler processa uma falha.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<workflow>](workflow.md)|Um elemento de configuração que contém todas as consultas para um fluxo de trabalho específico identificado pela propriedade **activityDefinitionId** .|  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [Acompanhamento e rastreamento de fluxo de trabalho](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [Acompanhando perfis](../../../windows-workflow-foundation/tracking-profiles.md)
