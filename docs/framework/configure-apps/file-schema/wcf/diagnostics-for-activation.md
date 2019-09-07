---
title: <diagnostics>para ativação
ms.date: 03/30/2017
ms.assetid: 1486e0eb-fe2a-46c3-b584-c924889477dd
ms.openlocfilehash: 33b2cd4c5ae1b4076892a61aa7e2b927efa1ddc1
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400406"
---
# <a name="diagnostics-for-activation"></a>\<> de diagnóstico para ativação
Configura as funcionalidades de diagnóstico do ouvinte Windows Communication Foundation (WCF).  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<sistema. serviceModel. Activation >** ](system-servicemodel-activation.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<> de diagnóstico**  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<configuration>
  <system.serviceModel.activation>
    <diagnostics performanceCountersEnabled="Boolean" />
  </system.serviceModel.activation>
</configuration>
```  
  
## <a name="type"></a>Tipo  
 `Type`  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`performanceCountersEnabled`|Um valor booliano que indica se os contadores de desempenho estão habilitados para fins de diagnóstico.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<system.serviceModel.activation>](system-servicemodel-activation.md)|Contém definições de configuração para o processo de ouvinte SMSvcHost. exe.|  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Activation.Configuration.DiagnosticSection>
