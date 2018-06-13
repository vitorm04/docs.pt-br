---
title: '&lt;callbackTimeouts&gt;'
ms.date: 03/30/2017
ms.assetid: d7fcfc5f-6d35-491e-8fa6-2f964c1e792f
ms.openlocfilehash: 48da0351d162a2143a26cc5b9eaa05b731358639
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32749560"
---
# <a name="ltcallbacktimeoutsgt"></a>&lt;callbackTimeouts&gt;
Especifica o valor de tempo limite ao fluir transações de servidor para chmada um cenário de contrato de retorno de chamada dúplex.  
  
 \<system.ServiceModel>  
\<comportamentos >  
\<endpointBehaviors>  
\<comportamento >  
\<callbackTimeOuts >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<callbackTimeOuts transactionTimeout="TimeSpan" />  
```  
  
## <a name="type"></a>Tipo  
 `Type`  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`transactionTimeout`|Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo em que as transações devem ser completadas ou automaticamente encerrada. O padrão é "00: 00:00".|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<comportamento >](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Especifica um comportamento de ponto de extremidade.|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Configuration.CallbackTimeoutsElement>
