---
title: '&lt;callbackTimeouts&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d7fcfc5f-6d35-491e-8fa6-2f964c1e792f
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e86b69b7d633fd99728936070e94da964e16de58
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="ltcallbacktimeoutsgt"></a>&lt;callbackTimeouts&gt;
Especifica o valor de tempo limite ao fluir transações de servidor para chmada um cenário de contrato de retorno de chamada dúplex.  
  
 \<sistema. ServiceModel >  
\<comportamentos >  
\<endpointBehaviors >  
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
