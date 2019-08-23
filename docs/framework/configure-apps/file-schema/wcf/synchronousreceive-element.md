---
title: Elemento <synchronousReceive>
ms.date: 03/30/2017
ms.assetid: cc070387-3d11-4b02-a952-bc08ad2df05a
ms.openlocfilehash: fa14d4606303b2d67cf5ef845d428bb086680204
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69938959"
---
# <a name="synchronousreceive-element"></a>\<elemento de > synchronousReceive
Este elemento de configuração é usado para especificar o comportamento de tempo de execução para receber mensagens em um serviço ou aplicativo cliente. Ele não tem nenhum atributo ou elemento filho.  
  
 \<system.ServiceModel>  
\<comportamentos >  
\<endpointBehaviors>  
\<> de comportamento  
\<synchronousReceive>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<synchronousReceive />
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
 nenhuma.  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<> de comportamento](behavior-of-endpointbehaviors.md)|Especifica um comportamento de ponto de extremidade.|  
  
## <a name="remarks"></a>Comentários  
 Use esse comportamento para instruir o ouvinte de canal a usar um recebimento síncrono, em vez do padrão, assíncrono. Windows Communication Foundation (WCF) emite um novo thread para bombeamento para cada canal aceito. Se houver muitos canais, haverá a possibilidade de ficar sem threads.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Configuration.SynchronousReceiveElement>
- <xref:System.ServiceModel.Description.SynchronousReceiveBehavior>
