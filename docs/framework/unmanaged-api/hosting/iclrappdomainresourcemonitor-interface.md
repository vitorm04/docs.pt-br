---
title: Interface ICLRAppDomainResourceMonitor
ms.date: 03/30/2017
api_name:
- ICLRAppDomainResourceMonitor
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAppDomainResourceMonitor
helpviewer_keywords:
- ICLRAppDomainResourceMonitor interface [.NET Framework hosting]
ms.assetid: 72fa83a1-8997-41d7-b355-ab177a24a303
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dc2326c72c9a1c63c4740608e120ace5dc83ebee
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33434864"
---
# <a name="iclrappdomainresourcemonitor-interface"></a>Interface ICLRAppDomainResourceMonitor
Fornece métodos que Inspecione a memória e a utilização da CPU de um domínio de aplicativo.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método GetCurrentAllocated](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentallocated-method.md)|Obtém o tamanho total, em bytes, de todas as alocações de memória que foram feitas pelo domínio do aplicativo desde que ele foi criado, sem subtrair a memória foi coletado como lixo.|  
|[Método GetCurrentSurvived](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentsurvived-method.md)|Obtém o número de bytes que sobreviveram o última completo, bloqueio de coleta de lixo e que são referenciados pelo domínio do aplicativo atual.|  
|[Método GetCurrentCpuTime](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentcputime-method.md)|Obtém o tempo total do processador que foi usado por todos os threads em execução no domínio de aplicativo atual, desde que o domínio de aplicativo foi criado.|  
  
## <a name="remarks"></a>Comentários  
 O `ICLRAppDomainResourceMonitor` interface fornece funcionalidade semelhante para as seguintes propriedades gerenciadas:  
  
-   <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.MonitoringTotalProcessorTime%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.MonitoringTotalAllocatedMemorySize%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.MonitoringSurvivedProcessMemorySize%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.MonitoringSurvivedMemorySize%2A?displayProperty=nameWithType>  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MetaHost.h  
  
 **Biblioteca:** incluído como um recurso no MSCOREE  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [\<appDomainResourceMonitoring > elemento](../../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md)  
 [Monitoramento de recursos de domínio do aplicativo](../../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md)  
 [Hospedagem de Interfaces](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [Hospedagem](../../../../docs/framework/unmanaged-api/hosting/index.md)
