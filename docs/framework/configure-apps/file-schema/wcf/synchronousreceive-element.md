---
title: elemento &lt;synchronousReceive&gt;
ms.date: 03/30/2017
ms.assetid: cc070387-3d11-4b02-a952-bc08ad2df05a
ms.openlocfilehash: af1ca2ee1fe3c03c33f05e0c30c7b843b3720a36
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32753255"
---
# <a name="ltsynchronousreceivegt-element"></a>elemento &lt;synchronousReceive&gt;
Este elemento de configuração é usado para especificar o comportamento de tempo de execução para receber mensagens em um cliente ou serviço de aplicativo. Ele não tem atributos ou elementos filho.  
  
 \<system.ServiceModel>  
\<comportamentos >  
\<endpointBehaviors>  
\<comportamento >  
\<synchronousReceive >  
  
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
|[\<comportamento >](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Especifica um comportamento de ponto de extremidade.|  
  
## <a name="remarks"></a>Comentários  
 Use esse comportamento para instruir o ouvinte de canal para usar um síncrono receber, em vez do padrão assíncrono. Windows Communication Foundation (WCF) emite um novo thread para a bomba de cada canal aceito. Se houver muita canais, há a possibilidade de falta de threads.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Configuration.SynchronousReceiveElement>  
 <xref:System.ServiceModel.Description.SynchronousReceiveBehavior>
