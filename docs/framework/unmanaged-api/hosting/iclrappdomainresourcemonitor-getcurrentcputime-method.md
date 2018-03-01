---
title: "Método ICLRAppDomainResourceMonitor::GetCurrentCpuTime"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICLRAppDomainResourceMonitor.GetCurrentCpuTime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAppDomainResourceMonitor::GetCurrentCpuTime
helpviewer_keywords:
- ICLRAppDomainResourceMonitor::GetCurrentCpuTime method [.NET Framework hosting]
- GetCurrentCpuTime method [.NET Framework hosting]
ms.assetid: ebc9cc33-fcd6-4cae-9ecb-ea21c51874e6
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2781cfb1e23db02ab8192c78bd0a3e585ee28b2b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrappdomainresourcemonitorgetcurrentcputime-method"></a>Método ICLRAppDomainResourceMonitor::GetCurrentCpuTime
Obtém o tempo total do processador que foi usado por todos os threads em execução no domínio de aplicativo atual, desde que o domínio de aplicativo foi criado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetCurrentCpuTime([in]  DWORD dwAppDomainId,  
                          [out] ULONGLONG* pMilliseconds);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `dwAppDomainId`  
 [in] A ID do domínio do aplicativo solicitado.  
  
 `pMilliseconds`  
 [out] Um ponteiro para o tempo total do processador que foi usado por todos os threads em execução no domínio de aplicativo atual desde que o domínio de aplicativo foi criado. Esse parâmetro pode ser `null`.  
  
## <a name="return-value"></a>Valor de retorno  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|O método foi concluído com êxito.|  
|COR_E_APPDOMAINUNLOADED|O domínio de aplicativo foi descarregado ou não existe.|  
|E_FAIL|Monitoramento de recursos do domínio de aplicativo não está habilitado.<br /><br /> -ou-<br /><br /> Todas as outras falhas.|  
  
## <a name="remarks"></a>Comentários  
 Esse método é o equivalente não gerenciado a gerenciado <xref:System.AppDomain.MonitoringTotalProcessorTime%2A?displayProperty=nameWithType> propriedade.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MetaHost.h  
  
 **Biblioteca:** incluído como um recurso no MSCOREE  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICLRAppDomainResourceMonitor](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)  
 [Hospedagem de Interfaces](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [Monitoramento de recursos de domínio do aplicativo](../../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md)  
 [Hospedagem](../../../../docs/framework/unmanaged-api/hosting/index.md)
