---
title: <behaviors> fluxo de trabalho
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 3c6017b6-0c4f-4192-bd67-9515f5d1ec82
ms.openlocfilehash: b7c5cf93a82ac88c25f9c478ad52cf41eb6f6d65
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59129201"
---
# <a name="behaviors-of-workflow"></a>\<comportamentos > de fluxo de trabalho
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
|[\<serviceBehaviors>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/servicebehaviors-of-workflow.md)|Esta seção de configuração representa todos os comportamentos definidos para um serviço de fluxo de trabalho específico.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<system.serviceModel>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|O elemento raiz de todos os elementos de configuração do fluxo de trabalho.|  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Configuration.BehaviorsSection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElement>
- [Configurando e estendendo o tempo de execução com comportamentos](../../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
