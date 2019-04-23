---
title: <diagnostics> para a ativação
ms.date: 03/30/2017
ms.assetid: 1486e0eb-fe2a-46c3-b584-c924889477dd
ms.openlocfilehash: 30456963a7d74a93e39bb1fddc0910daae97f039
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59203802"
---
# <a name="diagnostics-for-activation"></a>\<diagnóstico > para ativação
Configura as funcionalidades de diagnóstico do ouvinte do Windows Communication Foundation (WCF).  
  
 \<system.serviceModel.activation>  
\<diagnóstico >  
  
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
|[\<system.serviceModel.activation>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel-activation.md)|Contém definições de configuração para o processo de escuta SMSvcHost.exe.|  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Activation.Configuration.DiagnosticSection>
