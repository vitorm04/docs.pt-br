---
title: '&lt;comportamentos&gt; de fluxo de trabalho'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 3c6017b6-0c4f-4192-bd67-9515f5d1ec82
ms.openlocfilehash: 762fd1ff0de7980848ac3921706f406932c7f35d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32767304"
---
# <a name="ltbehaviorsgt-of-workflow"></a>&lt;comportamentos&gt; de fluxo de trabalho
Esse elemento contém o **serviceBehaviors** coleção.  Cada elemento na coleção define elementos de comportamento consumidos pelos serviços de fluxo de trabalho. Cada elemento de comportamento é identificado por seu exclusivo **nome** atributo.  
  
 \<system.ServiceModel>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
  </serviceBehaviors>  
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
 Nenhum  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<serviceBehaviors >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/servicebehaviors-of-workflow.md)|Esta seção de configuração representa todos os comportamentos definidos para um serviço de fluxo de trabalho específico.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<system.serviceModel>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|O elemento raiz de todos os elementos de configuração do fluxo de trabalho.|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Configuration.BehaviorsSection>  
 <xref:System.ServiceModel.Configuration.ServiceBehaviorElementCollection>  
 <xref:System.ServiceModel.Configuration.ServiceBehaviorElement>  
 [Configurando e estendendo o tempo de execução com comportamentos](../../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
